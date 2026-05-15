# Spotify Post-Release Optimizer — Data-Driven Album Sequencing

> **Analyzed 188,000+ Spotify tracks to discover what makes an album succeed *after release* — and turned the findings into a chatbot that gives artists a sequencing playbook in seconds.**

**188K tracks · 5 statistical findings (R² up to 0.79) · Python analysis + React chatbot · ISBA group project**

---

## The Problem

A song's *position* on an album materially affects how listeners experience it — but most independent and emerging artists sequence albums by gut feel. The major-label playbook (front-load the hits, save the deep cuts for tracks 7–10) is folklore, not data.

The two pains:

1. **Emerging artists** can't afford an A&R team. They need an evidence-based answer to "where do I put my best song?"
2. **Even established artists** are working with rules of thumb that are decades old and never validated against streaming-era listening behavior.

> **Why now?** Spotify's audio-feature API (energy, valence, danceability, etc.) plus 15 years of streaming history makes this an answerable question for the first time. Pre-streaming, you couldn't measure track-level retention.

---

## Users & Jobs-to-be-Done

| User | Job-to-be-Done | Today's Workaround | Pain |
|------|----------------|--------------------|------|
| **Emerging artist about to release an album** | When I sequence my tracks, I want a data-backed recommendation for where to place my strongest song. | Ask 3 friends + Reddit | Conflicting advice, no data |
| **Indie label A&R** | When I'm advising 5 artists, I want a tool that gives consistent, defensible sequencing advice. | Personal taste | Doesn't scale, hard to defend to artists |
| **Established artist post-release** | When I look at why an album underperformed, I want to know if sequencing was a factor. | Vibes | No diagnostic |

---

## The Solution

A two-part product:
1. **Statistical analysis** of 188K tracks → 5 actionable findings about what predicts post-release album performance
2. **AI chatbot** (`post-release-optimizer-DEMO-FINAL.html`) that lets an artist input their album and get a personalized sequencing recommendation

### The 5 findings

| Finding | Effect | Stat |
|---------|--------|------|
| **Quality Gap Effect** | Moderate quality gaps (10–20 points) between tracks → **+18 album-score boost** | R² = 0.42 |
| **Genre matters for front-loading** | **Pop: +22 points** from front-loading hits. Rock: no benefit. | Multi-regression |
| **Artist tier flips the playbook** | First-track quality explains **79%** of variance for emerging artists vs. **31%** for superstars | R² split by artist tier |
| **Mid-album dip is real** | Tracks 5–7 underperform vs. expectation by a measurable margin | Position-effect regression |
| **Closer effect** | Strong closers (track 10–12) lift overall album score independent of front-loading | Coefficient analysis |

### Key product decisions (and the tradeoffs)

| Decision | What I picked | What I rejected | Why |
|----------|---------------|-----------------|-----|
| **Statistical analysis BEFORE building the chatbot** | Run regressions first, validate findings, *then* turn them into a tool | Build a chatbot and let the LLM "figure it out" | The chatbot's defensibility comes from grounded findings. A pure-LLM tool would just hallucinate sequencing advice. |
| **Standalone HTML chatbot** | Single self-contained HTML file with React + Tailwind | Full stack with auth | Demo could be opened by anyone in any browser with no setup. For a 10-week class project, removing setup friction was the right call. |
| **Genre-aware recommendations** | Different rules for Pop, Rock, Hip-Hop, Country | One unified model | The data showed genre interaction effects too large to ignore. A unified model would have given mediocre advice to everyone. |
| **Artist-tier as a first-class input** | Ask the user "emerging or established?" | Pretend everyone gets the same advice | The first-track effect (79% vs. 31%) flips the playbook entirely. Asking one question changes the recommendation completely. |

---

## Impact & Metrics

| Metric | Result |
|--------|--------|
| Tracks analyzed | 188,000+ |
| Statistically significant findings | 5 (R² 0.31 → 0.79) |
| Models compared | Linear, multi-regression with interaction terms |
| Demo | Standalone HTML chatbot, opens in any browser |
| Class deliverables | Notebook + slide deck + technical PDF + working chatbot |

---

## What I'd Build Next

| Priority | Feature | Why this, why now |
|----------|---------|-------------------|
| **P0** | **Plug into the artist's actual unreleased album** | Today the chatbot uses generic input. Pulling the artist's track audio features via Spotify API → personalized recommendation grounded in *their* music. |
| **P0** | **Counterfactual mode** | "Here's what your album would have scored if you'd put track 7 first." Makes the insight visceral, not abstract. |
| **P1** | **A/B-able playlist sequencing** | Same findings apply to playlists. A creator could submit two orderings and see predicted retention. |
| **P2** | **Label-tier dashboard** | Indie labels managing 10+ artists could get a portfolio view of sequencing quality. |

**What I would NOT build next:** A full "music recommendation engine." Too crowded a space, no defensible angle vs. Spotify's own algorithms.

---

## My Role

**Group project** for the MSBA program at Santa Clara University.

**What I personally owned:**
- Hypothesis design — framed the *positions × audio features* model
- The Quality Gap analysis (the headline finding)
- Translating the regression coefficients into a user-facing chatbot prompt
- Slide narrative

**What teammates owned:**
- Initial data acquisition + cleaning
- Other regression specifications
- React chatbot frontend

---

## What I Learned

- **Findings → product is the hard step.** Running regressions is straightforward; turning a coefficient ("R²=0.42 on quality gap") into a user-facing recommendation ("space your bangers 10–20 quality points apart") is the actual product work.
- **Genre and artist tier are interaction effects, not categories.** Lumping everyone into one model was tempting and wrong. The biggest unlock came from *splitting*, not from a fancier model.
- **Standalone HTML demos beat full stacks for show-and-tell.** Zero setup, opens anywhere, works on a phone. For a portfolio piece, this is much higher reach than a localhost-only React app.

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Analysis | Python, pandas, NumPy, scikit-learn, statsmodels |
| Visualization | matplotlib, seaborn |
| Chatbot | React, JavaScript, Tailwind CSS (single-file HTML) |

---

## Files

| File | What it is |
|------|------------|
| `final-jupyter-notebook.ipynb` | Complete statistical analysis (188 K tracks, 5 findings) |
| `post-release-optimizer-DEMO-FINAL.html` | Standalone AI chatbot — open in any browser |
| `Post Release Optimizer README.pdf` | Technical documentation |

**Try the chatbot:** Download `post-release-optimizer-DEMO-FINAL.html` and open in your browser.

---

**Built by [Srinidhi Jagannathan](https://github.com/sjagannathan17)** · Santa Clara University MSBA · [LinkedIn](https://linkedin.com/in/srinidhi-jagannathan) · srinidhi.jagan11@gmail.com
