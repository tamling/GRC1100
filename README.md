# GRC1100 — course script (Quarto)

Quarto book project for the GRC1100 (Governance, Risk & Compliance) course
script, converted from the LaTeX lecture script and modelled on the SKY2100
course-script repository.

```
_quarto.yml               project config; annotations flag (ON); answers/ excluded
includes/hypothesis.html  the Hypothesis embed snippet (header include)
index.qmd                 book landing page (the script's preface)
chapters/                 one chapter per lecture (NN-name.qmd) + figures/
_tikz/                    TikZ sources for the figures + build.sh → chapters/figures/*.svg
answers/                  per-chapter sketch-answer keys — source-only, never rendered
appendix/                 reading list, abbreviations, how-to-annotate
theme-light.scss          light theme tweaks (cosmo)
theme-dark.scss           dark theme tweaks (darkly); light backing for figures
```

Render: `quarto render`. Every page carries the **light/dark toggle**
(`format.html.theme` with a `light:`/`dark:` pair in `_quarto.yml`); the
figures are transparent SVGs that get a light backing card in dark mode via
`theme-dark.scss`.

The Hypothesis annotation layer is **on by default** (`annotations: true` +
`include-in-header` in `_quarto.yml`); set the flag to false and remove the
header include to switch it off.

## Figures

`_tikz/` holds one `.tikz` source per figure plus the shared `preamble.tex`
(course colours, TikZ styles). `sh _tikz/build.sh` rebuilds
`chapters/figures/*.svg`; it needs `pdflatex` (with TikZ) and `pdftocairo`.

## Self-checks and answers

Each chapter ends with a **Self-check** section of exercises. The sketch
answers were moved out of the chapters into `answers/NN-name.qmd`, which the
render excludes (`!answers/` in `_quarto.yml`), so answers never appear on
the published site.
