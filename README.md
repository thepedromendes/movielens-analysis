# MovieLens Recommender System

A end-to-end movie recommendation project built on the [MovieLens Small dataset](https://grouplens.org/datasets/movielens/latest/) (100,836 ratings · 9,742 movies · 610 users). The project compares interaction-based methods with content-based and semantic retrieval approaches, and includes an LLM-powered explanation module.

---

## Overview

Users on any movie platform rate only a tiny fraction of the catalogue. This creates an extremely sparse user–item matrix (≈98.3% empty) where predicting preferences for unseen movies is the central challenge. This project tackles that problem by building and comparing multiple recommendation strategies — from simple baselines to neural models and RAG-style semantic retrieval.

---

## Methods Covered

| Stage | Methods |
|---|---|
| Baseline | Popularity-based recommender |
| Interaction-based | Association Rules, User-based Collaborative Filtering, Matrix Factorization, Bayesian Personalised Ranking (BPR), Neural Collaborative Filtering (NCF) |
| Content & Semantic | Genre multi-hot encoding, tag-based semantic retrieval, RAG-oriented pipeline |
| Explainability | LLM-based recommendation explanation module |

---

## Evaluation

All models are evaluated using **Precision@3** and **Recall@3** — the most operationally relevant metrics for generating short recommendation lists. Rating prediction models also report RMSE and MAE as secondary diagnostics.

A consistent train/validation/test split is used across all models. Probing experiments are first run on a 20% user sample for fast iteration, then the best models are scaled to the full dataset.

---

## Repository Structure

```
├── movielens.ipynb              # Main analysis notebook
├── movielens.html               # Rendered HTML export of the notebook
├── movielens_presentation.pptx  # Project presentation slides
├── ml-latest-small/             # MovieLens dataset (not tracked in git)
│   ├── ratings.csv
│   ├── movies.csv
│   ├── tags.csv
│   └── links.csv
└── README.md
```

> **Note:** The `ml-latest-small/` dataset folder is excluded from version control. Download it directly from [GroupLens](https://grouplens.org/datasets/movielens/latest/) and place it in the project root before running the notebook.

---

## Getting Started

**1. Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/movielens-analysis.git
cd movielens-analysis
```

**2. Download the dataset**

Download the `ml-latest-small.zip` from [grouplens.org](https://grouplens.org/datasets/movielens/latest/), extract it, and place the `ml-latest-small/` folder in the project root.

**3. Install dependencies**
```bash
pip install numpy pandas scikit-learn mlxtend scipy matplotlib seaborn
```

**4. Run the notebook**
```bash
jupyter notebook movielens.ipynb
```

---

## Key Findings

- The user–item matrix has **98.3% sparsity** — the average user rated fewer than 2% of available movies.
- Ratings skew positive, with the most common score being 4.0, justifying a relevance threshold of `rating ≥ 4` for binary feedback models.
- Interaction-based models (BPR, NCF) outperform the popularity baseline on Precision@3 and Recall@3.
- Semantic retrieval methods complement interaction-based models by addressing cold-start scenarios where rating history is sparse or absent.

---

## Dataset

**MovieLens Small** — collected by GroupLens Research at the University of Minnesota.
Ratings span March 1996 to September 2018. Users are anonymised with no demographic information available.

> F. Maxwell Harper and Joseph A. Konstan. 2015. The MovieLens Datasets: History and Context. *ACM Transactions on Interactive Intelligent Systems (TiiS)* 5, 4: 1–19.
