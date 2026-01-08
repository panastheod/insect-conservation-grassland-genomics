# Population Genomics Analysis Scripts

This repository contains scripts and parameter files supporting population genomic analyses conducted for the study "Ecotones promote, agriculture restricts: landscape-genomic patterns across three insects in a conservation grassland mosaic”. 

---

## Overview of the workflow

The analytical pipeline implemented in this repository includes:

1. **Quality filtering and adapter trimming**
   - Illumina paired-end RADseq reads were filtered and trimmed using **BBMap / BBDuk**.
   - Adapter contamination and low-quality bases were removed prior to assembly.

2. **RADseq assembly with ipyrad**
   - Species-specific ipyrad parameter files are provided.
   - Both reference-based and de novo assembly strategies were used, depending on species.
   - ipyrad outputs (loci, SNPs, VCFs) were used for downstream analyses.

3. **Variant filtering and sample quality control**
   - SNP filtering based on missingness and minor allele frequency was performed with **VCFtools**.
   - Individual-level QC included missingness and relatedness filtering.

4. **Linkage disequilibrium pruning**
   - LD pruning and PCA-ready datasets were generated using **PLINK2**.
   - LD pruning was applied to structure/divergence datasets but not to selection datasets, as noted in scripts.

5. **Genetic diversity analyses**
   - Genetic diversity (e.g. heterozygosity) was estimated in **R** using `vcfR`, `adegenet`, `hierfstat`, and `dartR`.
   - Analyses were conducted on VCFs retaining all sites (not only SNPs).

6. **Genetic divergence analyses**
   - Pairwise population differentiation (FST) was estimated using **StAMPP** with bootstrap support.

7. **Population structure analyses**
   - Discriminant Analysis of Principal Components (DAPC) was used to infer population structure.
   - Publication-ready figures were generated directly from the scripts.

8. **Isolation by distance**
   - Mantel tests were used to assess relationships between genetic and geographic distance.

9. **Spatial analyses (EEMS)**
   - Population-level distance matrices and coordinate files were generated in R for use with **EEMS**.
   - Additional helper functions are included for numerical correction and visualization of EEMS outputs.

---

## File description

- `Script.txt`  
  Fully annotated version of the analysis pipeline.  
  - Executable code is preserved exactly as run.
  - Annotations describe inputs, outputs, and analytical intent.
  - System-specific file paths are **not described in annotations**.

- ipyrad parameter blocks  
  Embedded within the main script; record the exact settings used for each species.

---

## Notes on reproducibility

- Absolute file paths appear **inside the code** because they reflect the original computational environment.
- For re-analysis on a different system, users should:
  - Copy the script
  - Update paths as needed

The scripts are not intended to be run without adaptation, but to provide a **faithful record of the analytical workflow** used in the study.

---

## Software requirements

Major tools and packages used include:

- **BBMap / BBDuk**
- **ipyrad**
- **VCFtools**
- **PLINK2**
- **R** (packages: `vcfR`, `adegenet`, `dartR`, `hierfstat`, `StAMPP`, `vegan`, `geosphere`, `ggplot2`, `Matrix`)
- **Python 2** (for legacy loci-to-VCF conversion)

Exact software versions are documented where relevant within the scripts.

---

## Data availability

Raw sequencing data and derived datasets are archived separately and are referenced in the associated manuscript.  
This repository contains **analysis scripts only**.

---

