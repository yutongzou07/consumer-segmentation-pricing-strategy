# consumer-segmentation-pricing-strategy
# Athena Softworks: Consumer Segmentation & Pricing Strategy

**Market intelligence case analysis** — factor analysis, K-means segmentation, Gabor-Granger pricing, and market share simulation to guide a game acquisition decision.

[Open in Colab](https://colab.research.google.com/github/yutongzou07/consumer-segmentation-pricing-strategy/blob/main/Market_intelligence_final_project_code.ipynb)

## Business Problem

Athena Softworks, a PC RPG publisher, is deciding which of three candidate game titles to acquire, how to price it, and how to position it in market. The analysis needed to independently validate a decision already in progress by another team, using a customer survey (40 gameplay-motivation items, purchase intent, and preference rankings).

Three decisions were in scope:
- **Which game to acquire** — Warrior Guild, Seraph Guardians, or Evercrest
- **How to price it** — profit-maximizing, premium, or penetration pricing
- **How to position it** — targeted vs. non-targeted marketing strategy

## Approach

**1. Market sizing**
Estimated the 2019 premium PC RPG market at ~$780M (derived from SuperData's premium PC games report) and projected ~$803M for 2020 pre-COVID, with a qualitative assessment of COVID-19's likely demand impact.

**2. Factor analysis**
Reduced 40 Likert-scale gameplay motivation statements into **11 interpretable factors** (e.g. Narrative Focus, Completion/Achievement, Strategy, Destruction, Exploration, Competitiveness), each named and interpreted from factor loadings.

**3. K-means clustering**
Segmented players into **8 distinct groups** based on factor scores — including Narrative Role-Players, Strategists, Completionists, Immersive Progression Players, and Competitive Players — then profiled each segment's demographics (age, gender, income).

**4. Gabor-Granger pricing analysis**
Built demand and revenue curves for each candidate game from stated willingness-to-pay data, handling structural and incomplete missing data explicitly.

**5. Segment-to-game regression**
Used OLS regression to identify which player segments were willing to pay the most for each title.

**6. Revenue and market share modeling**
Estimated first-year gross/net revenue (net of Steam's tiered platform fee and developer royalty), then built a market share simulation — first under naive assumptions (equal pricing, one purchase per customer), then a revised model incorporating realistic pricing tiers, multi-game purchase behavior, and segment-level heterogeneity.

## Key Findings

- **Pricing:** Optimal Gabor-Granger price points clustered around $32–$35 across all three titles, with revenue-maximizing demand between 75–82%.
- **Revenue:** Warrior Guild projected the highest naive first-year net revenue (~$56.5M), narrowly ahead of Seraph Guardians (~$55.9M) and Evercrest (~$53.7M).
- **Segment fit:** Immersive Progression Players showed the highest willingness to pay across all three games; Competitive Players (youngest, lowest income) showed the lowest — signaling weaker monetization potential for a competitive-multiplayer title.
- **Market share, naive model:** Seraph Guardians captured ~50% of surveyed demand under an equal-pricing, single-purchase assumption.
- **Market share, revised model:** After introducing realistic tiered pricing ($24.99–$29.99 for Warrior Guild, $44.99–$49.99 for Seraph Guardians, $34.99–$39.99 for Evercrest), multi-game purchase probability, and segment weighting, estimates shifted meaningfully — Seraph Guardians fell to 31.9%, Warrior Guild rose to 27.7%, and Evercrest held near 9.3%. This showed the naive model had overstated demand concentration.

## Recommendation

**Acquire Seraph Guardians**, priced at **$44.99–$49.99** (premium tier), with a **non-targeted positioning strategy**.

Rationale:
- Highest and most stable predicted market share across both the naive and revised models
- As a single-player title, demand is independent rather than conditional on reaching critical multiplayer mass — lower adoption risk than Warrior Guild, which would also face intense price competition from free-to-play competitors
- Performed well across multiple segments (Immersive Progression Players, Completionists, Strategists) rather than depending on one niche, supporting a broad positioning around strategic choice, planning, and immersive world-building rather than narrow segment targeting

## Tools

Python — pandas, scikit-learn (K-means, factor analysis), statsmodels (OLS regression), matplotlib, Monte Carlo–style purchase simulation

## Notes

This project was completed as an individual capstone for Duke Fuqua's *Marketing 552Q: Market Intelligence* (Prof. Allison Chaney). Athena Softworks and all game titles are fictional case study material. Raw survey data and assignment materials are not included in this repository per course policy; this repo contains only original analysis and code.
