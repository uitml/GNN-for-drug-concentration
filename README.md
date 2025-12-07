# LOD-library-191-molecules-_LC_MS

This repository implements a chemistry-informed Graph Neural Network (GNN) that integrates local atomic descriptors with global molecular features to model structure–property relationships in the LOD library with 191 small molecules in LC–MS equipment. Molecules are converted from SMILES into graphs where each atom node carries rich structural information (i.e., aromaticity, charge, valence, hybridization, mass-based descriptors), and each node is additionally augmented with global geometry features (molecular volume, length, width, height) to give the model full-molecule context beyond connectivity. A multi-layer Graph Attention Network (GAT), inspired by TChemGNN, learns both local substructure effects and broader molecular shape. The workflow includes graph construction, feature assembly, and a LOOCV training strategy optimized for small chemical datasets, providing a robust, structure-aware deep learning framework for molecular property prediction.

### Goal: 

The goal of this project is to develop a structure-aware GNN framework that combines local atomic features with global molecular geometry to improve prediction of LC–MS molecular properties. By integrating chemically meaningful descriptors with graph attention mechanisms, the model aims to capture both functional-group effects and whole-molecule structural influences. This enables accurate, data-efficient learning on small chemical libraries such as the 191-molecules in the LOD set.

### Notebooks
 **https://github.com/TLutchyn/LOD-library-191-molecules-_LC_MS/blob/main/LOD_library_LOOCV_8Kepochs_tricks.ipynb**

## 📚 Related Work & Inspiration: Efficient-ChemGNN

The work “Efficient Learning of Molecular Properties Using Graph Neural Networks Enhanced with Chemistry Knowledge” demonstrates that combining classical chemical insight with graph neural networks (GNNs) can substantially improve molecular property prediction. 

## ✅ What We Adopt / Extend from TChemGNN in This Repository

In our project (own LOD-library-191-molecules-LC–MS + GNN), we draw strong inspiration from these ideas — and integrate them into a specialized LC–MS context:

### - Rich atom + molecular-level features
We encode atom-level descriptors (aromaticity, ring membership, degree, valence, formal charge, atomic number, hybridization, hydrogen count, mass-based scaling, etc.) — capturing electronic, steric, and topological aspects. This mirrors and extends the philosophy of combining local and global chemical features.

### - Bond-based graph structure + molecular shape/size descriptors
As in Efficient-ChemGNN, we acknowledge that bonds alone may not capture all relevant chemical context for LC–MS signal behavior — therefore we allow inclusion of molecular‐level descriptors such as volumes, widths, lengths, heights (if available). This helps the GNN to “see” beyond just connectivity and get structural context relevant for ionization or fragmentation in LC–MS.

### - Graph Neural Network architecture using attention layers (GAT)
Our use of GAT layers aligns with the attention-based message-passing architecture favored in GNN chemical modeling. Attention allows the network to weigh different atoms/substructures differently, analogous to how certain functional groups or atom environments contribute more strongly to LC–MS response.

### - Designed for small-library, small-data regimes (≈ 191 molecules)
Similarly to Efficient-ChemGNN’s focus on small-molecule datasets, our model is built to work with limited data, leveraging chemistry-informed features and architecture choices to maximize predictive power despite small sample size.

### - Focus on chemically meaningful predictions (LC–MS response, intensity, concentration)
Unlike many generic molecular‐property predictors, our target is the signal/concentration behavior in LC–MS — a domain where structural context, ionization likelihood, steric hindrance, and electronic features matter significantly. By combining GNN and chemistry knowledge, we aim to bridge cheminformatics and analytical mass-spec modeling.

## 🚀 What Makes Our Project Unique (TChemGNN and Other GNN Approaches)

Whereas Efficient-ChemGNN proves the general value of combining global molecular features with GNNs, our project stands out by:

Specializing for LC–MS datasets — the feature engineering, target property (LC–MS response/concentration), and architecture are tuned for mass-spec chemical analytics.

A comprehensive atom-level feature set, including several mass-based and hydrogen/valence-based descriptors, in addition to classical bond connectivity — designed to capture nuances affecting ionization and detection.

Graph Attention Network layers tailored to chemical graphs — allowing attention to pick up on chemically relevant substructures (aromatic rings, heteroatoms, charged centers), which may drive LC–MS behavior more than simple topology.

LOOCV (Leave-One-Out Cross-Validation) for robust evaluation on a small, chemically diverse dataset — ensuring each unique molecule is tested as “new,” reflecting real-world usage where new compounds arise.

Practical applicability for analytical chemistry workflows — the code expects small to mid-size libraries, requires modest computational resources, and can integrate with LC–MS data (SMILES + signal/conc) directly, making it accessible for chemistry labs rather than only computational groups.

## Tailored for Small Chemical Libraries (N ≈ 191 molecules)

Most ML methods assume large datasets, but LC–MS quantification libraries are usually small.

This work is unique because it:

- uses LOOCV, ideal for limited molecular sets;

- handles rare or unique structural motifs with tailored GAT attention behavior;

- demonstrates stable predictions even for molecules with no close structural analogs.

## 🧭 Summary

This codes builds on the foundational ideas demonstrated in TChemGNN, applying them to an LC–MS–oriented molecular library. By combining atom-level chemical descriptors, global molecular features, and a GAT-based graph architecture, we aim to deliver a data-efficient, chemically informed, and practically usable GNN-based prediction framework for LC–MS concentration.

### 🔍 Notebooks

Notebook runs in [Google Colab](https://colab.research.google.com/) and supports interactive uploads, inference, and file processing. No local setup required.

