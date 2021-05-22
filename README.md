# sc-ngff (*Single cell Next Generation File Format*)

This repository houses some thoughts on what a next-generation file format might look like for single cell 'omics and imaging.  Will likely contain written examples with data-driven examples to follow.

The idea for this repository is heavily influenced by the following people, topics, and discussions:
- [AnnData #237](https://github.com/theislab/anndata/issues/237)
- [AnnData #555](https://github.com/theislab/anndata/issues/555)
- HuBMAP All-Hands 2021 Day 3 discussions
- [OME NGFF](https://github.com/ome/ngff)

## Goal

The major goal is understand what my requirements for language-agnostic file-format/data-storage-model look like, and be able to use this to inform discussions on this topic with others.  I intend this not to include implementation details (such as what backend file store format, e.g. [>ZARR<](https://zarr.readthedocs.io/en/stable/), etc.).

Ultimately, I would like to illustrate use-cases that are not easily accessible given the current standards.

## Rationale

The existence of capable and ubiqutous 'data models'/'data schema'/'file formats' 
- is the foundation for a healthy ecosystem of tool development, support, and adoption; 
- enables data sharing, Open(ish) Science, and innovation;
- lowers the bar of entry to data analysis and data interpretation.

That said, discussions about these topics:
- aren't super sexy;
- can get stuck in the implementation details/weeds

The lines separating the fields of single cell 'omics, (subcellular) bioimaging, hyperplexed spatial molecular profiling, etc. are becoming increasingly blurred.  
Coming from the sequencing-based single cell 'omics side, the computational community is semi-fractured due to the existence of file formats that haven't been easily interoperable, and these file formats being tied to programming languages.  While there is rough analysis parity between the Seurat (R-based) and Scanpy (Python-based) analysis tools, the implementations of their file formats have made it difficult to move between the two ecosystems fluidly.  From the imaging perspective, the standard OME-TIFF is a cumbersome file format for multiplexed imaging modalities like CODEX, IMC, MIBI, etc.  Sequencing and imaging based hyperplexed methods like merFISH (in situ) or spatial transcriptomics are further blurring the lines.  

Over the last three years, we've seen an explosion of multimodal profiling technologies, such as simultaneous transcriptome + proteome + CRISPR screen (ECCITE-seq), or simultaneous transcriptome and epigenome (SNARE-seq/Multiome).

Is there a generalized schema that can be used to store and enable analysis of:
- Droplet-based sc/snRNA-seq
- Droplet-based snATAC-seq
- Droplet-based methylation assays
- Droplet-based protein/TCR/BCR expression assays
- Spatial scRNA-seq
- Spatial snATAC-seq
- MIBI, CODEX, IMC, CyCIF
- Spatial Mass-Spec
- Assays I forgot or don't know about
- Combinations of all the above _on the same cells/observations_


## Disclaimers

I will likely use the terms 'data model', 'data schema', and 'file format' interchangibly here which (a) is likely incorrect and (b) demonstrates my limited understanding in this space.

I am heavily influenced by the AnnData/ScanPy ecosystem so I many examples given here may appear to be specific to that format due to my familiarity with it.  That said, there is an isomorphism between all the major file formats.

## Table of Contents

0. Nomenclature
1. One format to capture different analayses of the same observations
2. Two different cases of "multi-modal" data and how "modes" is overloaded

Appendix: Musings on a generalized analysis workflow


## Contributing

This is an important topic. Any thoughts, please feel free to add a pull request or reach out at [bill.flynn@jax.org](mailto:bill.flynn@jax.org).
