# Viability Matrices — conference demo

One self-contained HTML file. No build step, no server, no dependencies.

## Running it

- **Locally:** double-click `viability-matrices.html`.
- **On the web:** drop it in a GitHub repo as `index.html` and enable Pages, or drag it onto Netlify Drop.

Everything works with no keys. Placement, scoring, cross-walks, ellipse width, and the written
interpretation all run on deterministic rules inside the file.

## Optional keys (Setup tab)

| Key | Adds | Without it |
|---|---|---|
| Anthropic API key | Claude writes the "Reading" section, and reads free-text mission evidence for the stated-vs-revealed gap | Templated interpretation; free-text box is ignored |
| api.data.gov key | Live College Scorecard enrolment-trend lookups | `DEMO_KEY` for a handful of calls, then the stored snapshot |

Keys live in memory for the tab only.

## What each side does

**Student matrix (Vol. 1, Ch. 6).** Consent → short or full form → academic proxy → eight readiness
dimensions → placement with mobility paths. Refuses to place anyone when an axis has no evidence.

**Institutional matrix (Vol. 3, Ch. 1).** Resources (vertical) against mission integrity (horizontal),
matching Figure 3. Resources compresses the five capitals: financial capital measured from five public
indicators, the other four judged 1–5, all weighted equally. The result card then runs three cross-walks:

- **Figure 4** — archetype availability, including a verdict on the archetype the institution claims
- **Figure 6** — how each of the four learning environments behaves in this quadrant
- **Figure 2** — a mismatch warning when the intended environment's required capital is judged thin

and closes with which student types the institution can honestly serve, which is where the two
frameworks join.

**Load the worked case** reproduces Ashcombe State University from Ch. 1 §4. It lands in Quadrant III,
close enough to the mission-integrity boundary that the drift note fires, with a Tournament mismatch
warning on thin reputational capital — the chapter's own diagnosis, arrived at by the instrument.

## Three things worth demonstrating deliberately

1. **The instrument withholds placement on missing evidence.** Skip the academic proxy and the student
   side returns "Not enough to place" with two candidate quadrants rather than defaulting to the middle.
2. **Straight-lining is caught.** Several readiness and mission-integrity items are reverse-scored, so
   clicking 5 down the whole form produces a middling result, not a flattering one.
3. **Public data cannot reach the mission-integrity axis.** That asymmetry is visible on screen — every
   field is tagged live / stored / entered — and is the argument for the second axis.

## Fallback chain for institutional data

live Scorecard → stored snapshot (23 New England institutions, from `thomasmennella/higheredanalysis`)
→ manual entry. Endowment per FTE and tuition dependence aren't in those feeds and are entered by hand.

## Calibration notes

- Student horizontal band boundary sits near SAT 1180 — roughly the top quartile of test takers, where
  Ch. 6's own 16–24% high-intelligence estimate lands.
- Mission-integrity quadrant boundary sits at an item mean of 3.2 on the 1–5 scale.
- Blank inputs are dropped rather than scored as zero; they widen the ellipse instead.
