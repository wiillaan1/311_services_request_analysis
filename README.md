# Manhattan 311 Complaint Analysis (2025)
**Course:** 5205 Machine Learning | **Dataset:** NYC Open Data — 311 Service Requests

---

## Project Overview

This project applies unsupervised learning methods to Manhattan 311 service request data from 2025. The analysis identifies major complaint themes, clusters ZIP codes into community profiles, and examines whether service response times differ systematically across these profiles.

**Research Questions:**
- RQ1: What major issue themes can be identified from Manhattan 311 complaint descriptors?
- RQ2: Do Manhattan ZIP codes exhibit distinct community problem profiles?
- RQ3: Are there systematic differences in case processing time across these profiles?

---

## Methods Used

| Method | Purpose |
|---|---|
| TF-IDF Vectorization | Text feature extraction from complaint descriptors |
| Latent Dirichlet Allocation (LDA) | Topic modeling to identify complaint themes (RQ1) |
| K-Means Clustering | ZIP-code level community profiling (RQ2) |
| PCA | Dimensionality reduction for cluster visualization |
| Kruskal-Wallis Test | Non-parametric response time comparison (RQ3) |
| Mann-Whitney U + Holm correction | Pairwise follow-up tests |

---

## Repository Structure

```
├── RQ1_Major_Complaint_Themes.ipynb
├── RQ2+3.ipynb
├── README.md             
└── 5205_final_report.docx  # Final written report
```

---

## Requirements

Install dependencies via pip:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn scipy nltk
```

Or via conda:

```bash
conda install pandas numpy scikit-learn matplotlib seaborn scipy nltk
```

---

## Data

Data is pulled directly from the **NYC Open Data Socrata API** within the notebook (dataset ID: `erm2-nwe9`). No local data file is needed — the notebook handles retrieval automatically.

- Scope: Manhattan, January–December 2025
- Sample size: ~18,743 records (random monthly sampling)
- Key fields: `complaint_type`, `descriptor`, `incident_zip`, `created_date`, `closed_date`

---

## How to Run

1. Clone or download this repository
2. Install the required libraries (see Requirements above)
3. Open `notebook.ipynb` in Jupyter
4. Run all cells from top to bottom

> **Note:** The API pull in the first section requires an internet connection. All subsequent cells use the loaded dataframe and can be re-run offline.

---

## Key Findings

- LDA identified **4 complaint themes**: Residential Noise & Street Disruption, Sanitation & Property Conditions, Building Noise & Vendor Issues, and Parking & Construction Violations
- K-Means grouped 40 Manhattan ZIP codes into **4 community profiles** aligned with these themes
- Response times split into **two tiers**: sanitation/parking clusters are ~2× slower than noise/building clusters (Kruskal-Wallis H = 41.09, p < 0.001)
