# MWA-SKA VCSBeam Scaling tool

___
___
This interactive tool has been developed to visualise how the MWA Beamforming pipeline VCSBeam might perform when applied to SKA-like datasets run on SRCNet resources.
___
___
# Description

___
___
This tool is an interactive matplotlib widget embedded in a jupyter notebook. When the notebook is run, it will display two subplots, which estimate the processing time and number of GPU-hours required to process an SKA-like dataset into one tied-array beam pointing (TAB) using VCSBeam in PSRFITs-out mode on SRCNet resources. Variables can be changed using sliders to adjust the output on the plots. These variables are:

- The number of nodes SRCNet have available for processing
- The number of GPU cards per SRCNet node which will be used for processing
- The number of SKA stations in the dataset which will be processed
- The number of SKA coarse frequency channels which will be processed

The calculations which inform these plots are based on legacy VCSBeam profiling tests performed on Pawesy supercomputers, and various assumptions.

<details>
<summary>The assumptions include:</summary>

- The SRCNet GPUs used to process the dataset perform identically to Pawesy's AMD MI250X GPU cards.
- VCSBeam wall time scales linearly with observing time
- The time required by VCSBeam to stitch together frequency channels within a sub-job run on a GPU node is identical between SRCNet and Pawesy
- There are no other unanticipated nonlinear effects due to MPI communication overheads
- There are no unanticipated nonlinear effects due to file I/O times.
- For a coarse channel, VCSBeam performance scales linearly with stations in the array
- The time required to stitch data processed in different subjobs together has been disregarded
- The SKA data has MWA-like digitisation and channel widths in this calculation.

</details>

## Component details
___
The user-facing components of this repository are:

- The conda environment file `MWA_SKA_Reqs_env.yml`
- The jupyter notebook `Interactive_MWA-SKA_Scaler.ipynb`

___
## Example usage
___

<details>
<summary>Build the conda environment</summary>

- First, run `conda env create -f MWA_SKA_Reqs_env.yml`
- Then you can activate the environment using `conda activate MWA_SKA_Requirement_Environment`

</details>

<details>
<summary>Run the tool</summary>

-After activating the environment, open the jupyter notebook using `jupyter lab` or `jupyter notebook` in the command line
- Then run the cells in the notebook until a plot appears
- You should be able to interact with this plot using the sliders.

</details>

___
## Software requirements
___

<details>
<summary>Click to expand</summary>

- [miniconda](https://www.anaconda.com/docs/getting-started/miniconda/install)

</details>

___
## Hardware requirements
___
N/A.

___
## Directory structure
___

<details>
<summary>File structure diagram</summary>

```md
MWA-SKA_VCSBeam_Scaler
|--MWA_SKA_Reqs_env.yml
|--Interactive_MWA-SKA_Scaler.ipynb
|--Readme.md
|--.gitignore
```
</details>

Everything is contained in the base directory.

___
___
# To Do
___
___
Future improvements to this code could include:

- Improvements based on addressing the assumptions listed in the description.

___
___
# Links to internal work

<details>
<summary>SRCNet Feature SP-5218: Continued work on TBB data</summary>

- SRCNet Feature: [SP-5218](https://jira.skatelescope.org/browse/SP-5218)
- SRCNet Story: [TEAL-970](https://jira.skatelescope.org/browse/TEAL-970)
</details>

<details>
<summary>Related confluence pages</summary>

- General confluence page for this feature: [link](https://confluence.skatelescope.org/x/EoYSEw)
- Confluence page on scaling calculations: [link](https://confluence.skatelescope.org/x/TqkSEw)
</details>

# Developers and Contributors

- Walker, C.R.H. (UKSRC, University of Cambridge)
- Meyers, B. (AUSSRC, Curtin University)
___
