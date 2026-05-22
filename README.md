Deployment-oriented benchmark study of graph AI for cryptocurrency anti-money-laundering (AML) detection using the Elliptic and Elliptic2 public Bitcoin AML datasets.

This repository contains the research notebook, manuscript files, generated figures, result tables, and reproducibility artifacts for evaluating whether graph-based learning models outperform strong non-GNN baselines under realistic AML validation settings.

## Project Overview

Cryptocurrency AML is often treated as a graph-learning problem because suspicious activity unfolds through transaction networks. This project tests that assumption using two public benchmarks:

- **Elliptic**: transaction-node classification with temporal train-validation-test evaluation.
- **Elliptic2**: subgraph-level AML classification with repeated stratified robustness checks.

The study compares classical machine learning models, tree ensembles, graph-derived features, graph embeddings, neural baselines, and GNN variants using deployment-relevant metrics such as AUPRC, AUROC, Precision@K, Recall@K, calibration, operating points, and bootstrap uncertainty.

## Main Research Question

Do graph AI architectures provide a meaningful operational advantage over strong non-GNN baselines for cryptocurrency AML detection under temporal and cross-granularity evaluation?

## Selected Results

### Elliptic Transaction-Node Benchmark

On the temporal Elliptic test set, **Extra Trees** achieved the strongest overall performance:

- **AUPRC:** 0.570
- **AUROC:** 0.869
- **Accuracy:** 0.974
- **Precision:** 0.923
- **Recall:** 0.473
- **Recall@K:** 0.498

The strongest standard GNN baseline was **GraphSAGE**:

- **AUPRC:** 0.311
- **Recall@K:** 0.309

The strict-temporal GraphSAGE variant improved over standard GraphSAGE:

- **AUPRC:** 0.381
- **Recall@K:** 0.395

A paired bootstrap comparison showed that Extra Trees exceeded GraphSAGE by:

- **AUPRC difference:** +0.259
- **95% bootstrap interval:** [0.222, 0.297]

### Elliptic2 Subgraph Benchmark

On the full Elliptic2 subgraph benchmark, **Random Forest** achieved the strongest main-split AUPRC:

- **AUPRC:** 0.494
- **AUROC:** 0.923
- **Accuracy:** 0.982
- **Precision:** 0.929
- **Recall:** 0.219
- **Recall@K:** 0.595

Across repeated stratified splits, Random Forest remained the strongest model by mean AUPRC:

- **Mean AUPRC:** 0.488
- **Split-to-split interval:** [0.476, 0.500]

## Key Finding

The results show that strong tree ensembles remain highly competitive in cryptocurrency AML detection. On the Elliptic temporal benchmark, Extra Trees outperforms the evaluated GNN baselines by AUPRC. On the Elliptic2 subgraph benchmark, Random Forest is the strongest repeated-split model by mean AUPRC.

The project argues that graph AI models for AML should be stress-tested against strong tree-based baselines before architectural complexity is treated as deployment evidence.

## Repository Contents

- `graph-ai-for-cryptocurrency.ipynb`  
  Main Kaggle notebook containing preprocessing, feature construction, model training, evaluation, and figure generation.

- `main.tex`  
  BDCC-formatted LaTeX manuscript.

- `references.bib`  
  Bibliography file for the manuscript.

- `figures/`  
  Publication-ready figures generated from the notebook.

- `results/`  
  Model outputs, performance tables, bootstrap intervals, predictions, and diagnostic artifacts.

## Keywords

cryptocurrency AML, graph AI, graph neural networks, Elliptic dataset, Elliptic2 dataset, fraud detection, financial crime, RegTech, temporal validation, model governance
