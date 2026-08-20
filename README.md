# How Much of Bot Detection Is Really Bot Detection?
### A Trivial-Baseline Audit of the Cresci-2017 Benchmark

Final individual research project for DCIT 316 (Computational Models for
Social Media Mining), University of Ghana, 2025/2026.

**Author:** Thomas (Level 300, Department of Computer Science)

## Summary

Standard classifiers reach ~98% accuracy on the Cresci-2017 Twitter bot
dataset. This project asks how much of that accuracy actually requires
machine learning. Findings:

| Model                          | Accuracy |
|--------------------------------|----------|
| Trivial rule (favourites == 0) | 0.962    |
| Logistic Regression            | 0.914    |
| Random Forest (300 trees)      | 0.979    |
| Random Forest (no favourites)  | 0.958    |

A single untrained rule comes within 1.7 points of the full Random
Forest, suggesting the benchmark largely rewards collection artifacts
(account life-stage differences) rather than bot-like behaviour.

## Repository structure

notebooks/01_data_exploration.ipynb # full pipeline: EDA, models, ablation
figures/ # generated figures and result tables
paper/ # final paper (DOCX)
requirements.txt # pinned dependencies
data/ # dataset location (not committed)


## Data access

The dataset is **not** included in this repository, in line with the
Bot Repository's terms. To obtain it:

1. Visit the Bot Repository datasets page (botometer.osome.iu.edu) and
   request `cresci-2017` for academic use.
2. Unzip `cresci-2017.csv.zip` into `data/`.
3. Unzip these three sub-archives inside `data/datasets_full.csv/`:
   `genuine_accounts.csv.zip`, `social_spambots_1.csv.zip`,
   `traditional_spambots_1.csv.zip`.

Only the `users.csv` file from each subset is used; tweet files are not
needed.

## Reproduction steps

git clone https://github.com/theThomas-tech/bot-detection.git
cd bot-detection
python -m venv venv
venv\Scripts\Activate.ps1 # Windows (source venv/bin/activate on Mac/Linux)
pip install -r requirements.txt


Then obtain the data (above) and run all cells in
`notebooks/01_data_exploration.ipynb`. The train/test split uses a fixed
seed (42), so all tables and figures reproduce exactly.

## Citation

Dataset: Cresci et al. (2017), "The paradigm-shift of social spambots,"
WWW '17 Companion. See the paper's reference list for full citations.

## AI-use disclosure

Claude (Anthropic) assisted with project planning, code scaffolding,
debugging guidance, and documentation. All code was run and verified by
the author; analysis conclusions were drawn from the author's own outputs.