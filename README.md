# Linear Programming Model – Optimal Land Allocation for Crop Cultivation

This project models and solves a real-world **Linear Programming (LP)** problem to help the **National Farmers' Union** determine the optimal allocation of land to crops across 5 divisions in the Anuradhapura irrigation zone.

---

## 📌 Problem Statement

Maximize total profit from cultivating three crops (Black gram, Sesame, and Big Onion) across 5 divisions, under the following constraints:

- Land availability per division
- Total irrigation water limit (7400 acre-feet)
- Market sales limits
- A minimum production requirement for sesame
- Crop-specific water needs, yield, and profit rates

---

## ✅ Sets and Indices

- Divisions \( i \in \{1,2,3,4,5\} \)
  - 1: Thanthirimale  
  - 2: Pulmude  
  - 3: Rambewa  
  - 4: Tirappane  
  - 5: Rajanganaya

- Crops \( j \in \{G, S, O\} \)
  - G: Black gram  
  - S: Sesame  
  - O: Big onion

---

## 🔢 Parameters

| Crop \( j \) | Water (AF/acre) | Yield       | Market Limit | Profit (Rs/acre) |
|--------------|------------------|-------------|---------------|------------------|
| G (Black gram) | 1.6            | 50 bu/acre  | 110,000 bu    | 100,000          |
| S (Sesame)     | 2.9            | 1.5 t/acre  | 1,800 tons    | 60,000           |
| O (Big onion)  | 3.5            | 2.2 t/acre  | 2,200 tons    | 110,000          |

| Division \( i \) | Max Land (acres) | Water Limit (AF) |
|------------------|------------------|------------------|
| 1 (TMT)          | 2000             | 3200             |
| 2 (PLD)          | 2300             | 3400             |
| 3 (RMB)          | 600              | 800              |
| 4 (TRP)          | 1100             | 500              |
| 5 (RAJ)          | 500              | 600              |

---

## 📈 Objective Function

Maximize total profit:

\[
\max Z = \sum_{i=1}^{5} \left( 100000 \cdot x_{iG} + 60000 \cdot x_{iS} + 110000 \cdot x_{iO} \right)
\]

---

## 📋 Constraints

### 1. Land Constraints (∀ \( i \)):

\[
x_{iG} + x_{iS} + x_{iO} \leq \text{Land}_i
\]

### 2. Total Water Constraint (no extra water purchased):

\[
\sum_{i=1}^{5} (1.6x_{iG} + 2.9x_{iS} + 3.5x_{iO}) \leq 7400
\]

### 3. Market Demand Limits:

- Black gram:
\[
50 \cdot \sum_{i=1}^{5} x_{iG} \leq 110000
\]

- Sesame:
\[
1.5 \cdot \sum_{i=1}^{5} x_{iS} \leq 1800
\]

- Big onion:
\[
2.2 \cdot \sum_{i=1}^{5} x_{iO} \leq 2200
\]

### 4. Minimum Sesame Requirement:

\[
1.5 \cdot \sum_{i=1}^{5} x_{iS} \geq 800
\]

### 5. Non-negativity:

\[
x_{ij} \geq 0 \quad \forall i \in \{1..5\},\ j \in \{G, S, O\}
\]

---

## 🚀 Output

The solution provides:
- Acres to allocate per crop in each division
- Maximum profit under given constraints

---

## 🧮 Tools Used

- Python
- PuLP (Linear Programming Solver)
- Google Colab

---

## 📎 Notes

- This model **excludes** the optional 600 acre-feet extra water scenario. See `extra_water_version.ipynb` if included in repo.
- Feel free to reuse the model for agricultural planning or academic use.

---
