# 🚀 Multi CPU-PDDS (Multi CPU Parallel Dynamically Dimensioned Search)

This repository implements **Multi CPU-PDDS**, a scalable auto-calibration framework for large-scale hydrologic and hydrodynamic modeling. It runs each model evaluation on multiple CPUs, in addition to running several candidate parameter sets concurrently, while the underlying PDDS search logic stays unchanged. The framework integrates parameter sampling, model execution, post-processing, and optimization into an automated pipeline, orchestrated through **Jupyter Notebooks** for transparency, traceability, and reproducibility.

---

## 📂 Project Structure

```
BASE_DIR/
├── Multi_CPU-PDDS/
│   ├── Scripts/
│   │   ├── notebooks/        # All Python scripts (e.g., Model_run.py)
│   │   └── shapefiles/       # Shapefiles used for spatial masking/clipping
│   ├── configs/              # Ostrich config files and parameter templates (GENPARM, SOILPARM, etc.)
│   ├── best_parm/            # Best performing parameter sets selected from calibration
│   ├── obj_function/         # CSVs of objective function and other metrics
│   ├── param_save/           # Backup of each iteration's parameter files
│   ├── Linux/                # Compiled Ostrich binary (e.g., OstrichMPI)
│   ├── Source/               # Source code or templates for LIS/Ostrich if applicable
│   └── ILDAS_Auto_cal.sh     # Bash script to automate model + calibration execution
│
├── lis_input_files/          # LIS forcing and initialization NetCDF input files
│
└── output/
    ├── LSM_IMD*/             # LIS routing output directories (from different model configs)
    ├── processed_data*/      # Post-processed routed streamflow and merged data
    └── error_metrix/         # Error matrix output (NSE, KGE, etc.) for each run
```

---

## 🚀 How to Run Multi CPU-PDDS

### 1. 📥 Clone the Repository

Clone the repository into your working base directory:

```bash
git clone https://github.com/hydrosenselab/Multi_CPU-PDDS.git
cd Multi_CPU-PDDS
```

### 2. 🛠️ Set Up the Conda Environment

Create and activate a conda environment with all required libraries:

```bash
conda env create -f geo_env.yml
conda activate geo_env
```

### 3. 📁 Configure Paths and Scripts

- Open and edit `Multi_CPU-PDDS/Scripts/notebooks/config_paths.py`.
  - Set all necessary base paths, filenames, and directories as variables.
  - This ensures portability and reproducibility across systems.
- Modify the `Multi_CPU-PDDS/ILDAS_Auto_cal.sh` shell script.
  - Update paths to LIS executables, data directories, and environment modules based on your HPC or local system.