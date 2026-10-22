# Calculative Foundation 📐📊

A robust, object-oriented Python framework utilizing `NumPy` to perform fundamental linear algebra operations for multi-dimensional student score matrices (students $\times$ subjects).

---

## 🚀 Features & Modules

1. **Vector Fundamentals (`vector_fundamentals`)**: Computes Manhattan/Euclidean norms, dot products, vector angles, projections, and 3D cross products.
2. **Matrix Operations (`matrix_operations`)**: Handles matrix transpositions, products, determinants, and inverses.
3. **Eigen Decomposition (`eigen_decomposition`)**: Computes covariance matrices alongside sorted eigenvalues and eigenvectors for principal feature analysis.

---

## 🛠️ Installation

```bash
pip install numpy
```

---

## 📖 Usage Example

```python
import numpy as np

class CalculativeFoundation:
    def __init__(self, data_matrix):
        self.data_matrix = np.array(data_matrix, dtype=float)

    def vector_fundamentals(self, student_idx1, student_idx2, sub_indices_3d=None):
        v1 = self.data_matrix[student_idx1]
        v2 = self.data_matrix[student_idx2]
        
        norm1_v1 = np.linalg.norm(v1, ord=1)
        norm2_v1 = np.linalg.norm(v1, ord=2)
        
        dot_prod = np.dot(v1, v2)
        norm_product = np.linalg.norm(v1) * np.linalg.norm(v2)
        cos_angle = dot_prod / norm_product if norm_product != 0 else 0
        angle_rad = np.arccos(np.clip(cos_angle, -1.0, 1.0))
        angle_deg = np.degrees(angle_rad)
        
        projection = (np.dot(v1, v2) / np.dot(v2, v2)) * v2 if np.dot(v2, v2) != 0 else np.zeros_like(v2)
        
        cross_prod = None
        if sub_indices_3d is not None and len(sub_indices_3d) == 3:
            s1_3d = v1[sub_indices_3d]
            s2_3d = v2[sub_indices_3d]
            cross_prod = np.cross(s1_3d, s2_3d)

        return {
            "v1": v1, "v2": v2,
            "norm1_v1": norm1_v1, "norm2_v1": norm2_v1,
            "dot_product": dot_prod, "angle_degrees": angle_deg,
            "projection_v1_on_v2": projection, "cross_product_3d": cross_prod
        }
```

---

## 📊 Sample Outputs

```text
Norm-1 (Manhattan) of Student 0: 345.00
Norm-2 (Euclidean) of Student 0: 172.84
Dot Product between Student 0 & Student 2: 29538.00
Angle between vectors: 7.65 degrees
Vector Projection of Student 0 on Student 2: [87.419, 81.459, 94.373, 78.479]
Cross Product (3D subjects): [2154.0, -1211.0, -950.0]
```

---
# -Calculative-Foundation
