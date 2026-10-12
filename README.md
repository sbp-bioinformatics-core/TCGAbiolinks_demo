# Accessing Cancer Genomics Datasets from NCI's Genomic Data Commons (GDC) Using TCGAbiolinks. 

---

[TCGAbiolinks](https://bioconductor.org/packages/3.23/bioc/vignettes/TCGAbiolinks/inst/doc/index.html) 
R package from Bioconductor project allows:

  - Open-source data retrieval from GDC
  - Data pre-processing
  - Standard analyses
  - Data visualization

For a demo of how to use TCGAbiolinks for downloading TCGA RNA-seq data, see
***Download_GDC_TCGAbiolinks.Rmd***.

---

### Downloaded data formats:

GDC data from gene expression experiments (RNA-seq) is downloaded as a 
[RangedSummarizedExperiment](https://www.bioconductor.org/packages/devel/bioc/vignettes/SummarizedExperiment/inst/doc/SummarizedExperiment.html)
which is a matrix-like container data structure with rows as features 
(e.g. genes for RNA-seq) and columns as samples:

#### Obtaining feature, sample, and assay information from RangedSummarizedExperiment object:
For a RangedSummarizedExperiment objects called "rnaseq_normals":

Obtaining colData (sample information):

`rnaseq_normals@colData`

Obtaining rowRanges (feature information in GRanges format):

`rnaseq_normals@rowRanges`

Obtaining a specific assay matrix (e.g. counts):

`assay(rnaseq_normals, "unstranded")`


#### Available assays in the RNA-seq RangedSummarizedExperiment: 

  - **unstranded** (total counts from both strands, from unstranded RNA-seq)
  - **stranded_first** 
  - **stranded_second**
  - **tpm_unstrand** (TPM)
  - **fpkm_unstrand** (FPKM)
  - **fpkm_uq_unstrand** (UQ normalized FPKM)