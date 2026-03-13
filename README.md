# Scrna-seq-anaylsis-using-SCRAN-Normalization-method-
This repository contains a single-cell RNA-seq analysis workflow for Drosophila melanogaster implemented in R using the scran framework. The pipeline includes quality control, pre-clustering, deconvolution normalization, log normalization, highly variable gene detection, dimensionality reduction, clustering, and marker gene analysis . 

scRNA-seq Analysis Pipeline using scran (Drosophila melanogaster)

This repository presents a complete single-cell RNA-seq analysis workflow implemented in R using the Bioconductor scran framework. The analysis was performed on 10x Genomics scRNA-seq data from Drosophila melanogaster containing 17,473 genes across 3,000 cells, using the SingleCellExperiment structure for efficient data management.

Workflow Overview

The pipeline follows the standard scran-based normalization and clustering workflow:

Data Import → Quality Control → Pre-Clustering → Deconvolution Normalization → Log Normalization → Highly Variable Gene Detection → PCA → UMAP/t-SNE → Graph-Based Clustering → Marker Gene Identification

Results Summary
Quality Control

Per-cell QC metrics including library size (UMI counts) and detected gene counts were calculated to identify low-quality cells. Filtering and outlier detection removed empty droplets and noisy cells, resulting in a high-quality dataset of 1,560 cells suitable for downstream analysis.

Pre-Clustering

Cells were grouped into preliminary clusters using scran’s quickCluster() to support accurate normalization. This step grouped transcriptionally similar cells, ensuring stable size factor estimation during normalization.

Deconvolution Normalization

Normalization was performed using scran’s computeSumFactors(), which estimates cell-specific size factors through a deconvolution strategy. The calculated size factors ranged from 0.049 to 16.96, highlighting substantial variation in sequencing depth that was successfully corrected.

Log Normalization

Expression values were scaled and log-transformed to stabilize variance across cells. The normalized expression values ranged approximately from 2.24 to 5.81, indicating effective compression of extreme expression values and improved comparability across cells.

Highly Variable Gene Detection

Variance modeling identified 2,000 highly variable genes (HVGs) that capture the most significant biological variation across cells. These genes were used for downstream dimensionality reduction and clustering.

Dimensionality Reduction

Principal Component Analysis (PCA) revealed strong transcriptional heterogeneity across cells, with PC1 explaining ~31% of the total variance. Additional visualization using UMAP and t-SNE showed clear separation of cellular populations.

Graph-Based Clustering

Using Shared Nearest Neighbor (SNN) graph clustering, the dataset was partitioned into 10 transcriptionally distinct clusters, suggesting the presence of multiple cell types or cellular states.

Marker Gene Identification

Differential expression analysis identified cluster-specific marker genes, including genes such as FBgn0026084, FBgn0040747, and FBgn0023167. Marker detection achieved an approximate 7.21% marker discovery rate, indicating a subset of strongly discriminative genes defining specific clusters.

Computational Performance
Metric	Result
Dataset Size	1,560 cells × 17,473 genes
Runtime	~32.2 seconds
Peak R Memory Usage	~668 MB
System RAM	12.7 GB available
CPU	2 cores (Linux x86_64 environment)
Clusters Identified	10

The pipeline demonstrated efficient runtime, moderate memory usage, and stable performance, making it suitable for standard workstation environments without high-performance computing resources.

Conclusion

This analysis successfully demonstrates an efficient scran-based scRNA-seq workflow capable of processing raw 10x Genomics datasets, correcting sequencing depth variation through deconvolution normalization, and identifying transcriptionally distinct cellular populations. The results highlight the presence of ten heterogeneous cell clusters defined by specific marker genes, illustrating the effectiveness of the pipeline for exploring cellular diversity in single-cell transcriptomic data.

 
