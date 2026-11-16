# Designing self-reproducing RNAs with a VAE

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/philippenghe/X2A_RNA_VAE/blob/main/TD_VAE_RNA_design.ipynb)

Lab for session 11 of *Introduction to AI with applications in Science* (MDC_42001_EP),
École Polytechnique — elective **Diversification of catalytic biomolecules**. 1 h 30.

Click the badge. Everything installs and downloads itself; there is nothing to set up.

---

## What this is

You drive the generative model from Lambert C.N., Opuu V., Calvanese F. *et al.*,
*Exploring the space of self-reproducing ribozymes using generative models*,
**Nature Communications 16, 7836 (2025)**
([paper](https://doi.org/10.1038/s41467-025-63151-5) ·
[code and data](https://doi.org/10.5281/zenodo.16531362)).

The architecture and the trained weights are the authors' own. You are not
reimplementing the paper — you are running it, and then checking its designs against the
24 220 molecules they actually synthesised and assayed.

| § | | TODO |
|---|---|---|
| 1 | The alignment of 816 group I introns; one-hot encoding | 1 |
| 2 | Hamming distance; folding with ViennaRNA against the target structure | 2, 3 |
| 3 | The VAE: reparametrisation, ELBO, pre-trained weights | 4, 5 |
| 4 | Generating designs; the `scale` knob and the exploration–exploitation trade-off | 6 |
| 5 | Structure-constrained decoding | 7 |
| 6 | Confronting 24 220 measured designs | — |
| 7 | Design challenge, with a leaderboard | — |

Seven cells are marked `# TODO`; everything else is given. Each section ends with a
`check_*()` cell that tells you whether you can move on.

## Running it

**Colab** — click the badge. The notebook installs ViennaRNA and clones this repository
for the data. No GPU needed; the weights are pre-trained, so nothing is fitted during the
session. Use **File → Save a copy in Drive** to keep your work.

**Locally** —

```bash
git clone https://github.com/philippenghe/X2A_RNA_VAE.git
cd X2A_RNA_VAE
pip install torch ViennaRNA numpy pandas matplotlib scipy
jupyter lab
```

## What is in `data/`

| file | |
|---|---|
| `azo.seq` | the Azoarcus ribozyme, 193 nt |
| `azo_msa.seq` | RFAM RF00028 alignment, 817 × 193 — the entire training set |
| `target.str` | target secondary structure, dot-bracket, pseudoknot included |
| `vae_weights.dat` | the authors' trained VAE, 1 712 325 parameters |
| `design_db_T37C.csv` | 24 220 designs assayed at 37 °C, with measured activities |

All derived from the Zenodo archive above, redistributed under its terms.
