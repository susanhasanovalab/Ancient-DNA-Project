# Ancient DNA (aDNA) Damage Pattern & Authentication Analysis Pipeline

This repository contains a computational biology workflow designed to evaluate, authenticate, and analyze post-mortem degradation patterns in **Ancient DNA (aDNA)** compared to modern human DNA control datasets. 

The analysis is implemented in Python via Jupyter Notebook, utilizing programmatic sequence retrieval through the **NCBI Entrez API** and programmatic nucleotide substitution profiling.

---

## 📌 Research Overview & Objectives

Ancient DNA (aDNA) extracted from archaeological remains suffers from post-mortem decay over time. The primary bioinformatic challenge in aDNA research is distinguishing true biological single nucleotide polymorphisms (SNPs) from chemical damage artifacts (such as cytosine deamination) and modern contamination.

### **Key Research Questions Addressed:**
1. What damage patterns characterize ancient biological samples?
2. How do nucleotide substitution frequencies ($C \rightarrow T$ transitions and $G \rightarrow A$ misincorporations) differ between ancient and modern genomes?
3. How can computational deamination profiles be used for aDNA sample authentication?

---

## 🧬 Dataset Description

All sequence datasets were retrieved directly from the **NCBI Nuccore** database using the `Bio.Entrez` API module:

| Dataset Role | Organism / Sample | NCBI Accession ID | Description |
| :--- | :--- | :--- | :--- |
| **Reference Genome** | Homo sapiens | `NC_012920.1` | Revised Cambridge Reference Sequence (rCRS) Mitochondrial Genome |
| **Ancient DNA (aDNA)** | Vindija Neanderthal (aDNA) | `FM865411.1` | Complete Mitochondrial Sequence of Vindija 33.16 |
| **Modern DNA Control** | Homo sapiens | `AF347015.1` | Modern Human Control Mitochondrial Sequence |

---

## 🚀 Workflow & Pipeline Architecture

The computational pipeline consists of four major stages:

1. **Automated Sequence Fetching:** Fetching FASTA records programmatically from NCBI Nuccore via Biopython.
2. **Positional Nucleotide Alignment & Substitution Profiling:** Pairwise nucleotide-by-nucleotide comparison against the rCRS reference sequence to quantify transitions ($C \rightarrow T$, $G \rightarrow A$) and transversions.
3. **Damage Pattern Quantification:** Statistical comparison of deamination signatures between ancient and modern samples.
4. **Deamination Curve Modeling:** Visualization of position-dependent $C \rightarrow T$ decay rates at read ends (aDNA Authentication Indicator).

---

## 📊 Key Results & Visualizations

### 1. Ancient vs. Modern Misincorporation Profile
The pipeline quantifies $C \rightarrow T$ and $G \rightarrow A$ transitions. The ancient sample exhibits a significantly elevated rate of $C \rightarrow T$ transitions compared to the modern control, confirming post-mortem cytosine deamination.

### 2. Positional Cytosine Deamination Curve
An exponential decay curve of $C \rightarrow T$ transitions from the $5'$ end is modeled. High substitution frequency at read termini declining toward the interior is a hallmark signature used to authenticate genuine ancient genetic material and exclude modern contamination.

---

## 🛠️ Requirements & Installation

To run the notebook locally, ensure you have Python 3.8+ and the required packages installed:

```bash
pip install biopython pandas numpy matplotlib seaborn
