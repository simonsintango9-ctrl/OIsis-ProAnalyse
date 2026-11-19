# DERIV QUANT AI — Digit Intelligence & Market Analysis Terminal

A browser-based quantitative research and statistical digit-behavior analysis terminal for Deriv volatility markets (`1HZ10V`–`1HZ100V`, `R_10`–`R_100`, and dynamically discovered symbols).

> **Research & Epistemic Notice:** Built for market research, statistical intelligence, and strategy evaluation. It does **not** execute automated trades, does **not** request account passwords or persist private tokens in `localStorage`, and never claims guaranteed predictions or fabricated probabilities.

## All 10 Development Stages Combined

1. **Stage 1 — Architecture:** Separates WebSocket transport & endpoint isolation (`wss://api.derivws.com/trading/v1/options/ws/public` primary vs. isolated legacy `v3` adapter with configurable App ID `3496`), rolling tick buffers, quantitative engines, and terminal UI.
2. **Stage 2 — Connection Foundation:** Manages `CONNECTING`, `CONNECTED`, `RECONNECTING`, `DISCONNECTED`, and `ERROR` states, request correlation (`req_id`), heartbeat ping/pong RTT, and exponential backoff with jitter.
3. **Stage 3 — Live Market Data:** Discovers active symbols, tracks/cancels subscriptions and recovers them after reconnects, and extracts terminal decimal digits (`0–9`) safely from quote strings using symbol precision/pip metadata (`1234.56 -> 6`, `9876.30 -> 0`, `4321.50 -> 0`, `123.45 -> 5`, `1000.00 -> 0`).
4. **Stage 4 — Quantitative Engine:** Computes digit frequency across windows `25 / 50 / 100 / 200 / 500 / 1,000`, `HOT / COLD / OVERDUE / NEUTRAL` classifications, `10×10` Markov transition matrices, sequential patterns (repeats, runs, `A-B-A-B` alternations, odd/even, high/low `5–9` vs `0–4`, clusters), and statistical tests (chi-square, Wilson intervals, Shannon entropy, lag autocorrelation, multiple-testing caveats).
5. **Stage 5 — Signal Intelligence:** Evaluates **MATCHES** (`10%` uniform baseline) and **DIFFERS** (`90%` uniform baseline) across digits `0–9` and scores analytical evidence (`0–100`: `85–100` Strong, `70–84` Moderate, `55–69` Weak, `<55` Insufficient) with explicit `NO SIGNAL` gating when samples are insufficient, stale, or below threshold.
6. **Stage 6 — Market Scanner:** Monitors independent market buffers on a non-blocking **12-second default** interval with manual scan, countdown, distribution-shift detection, ranking, and scan history.
7. **Stage 7 — Historical Analysis & Backtesting:** Runs walk-forward evaluation strictly on `ticks[0..t-1]` (preventing look-ahead bias) with in-sample/out-of-sample metrics, hit rates, Brier score, log loss, and consecutive misses.
8. **Stage 8 — Professional Dashboard & Simulation Mode:** Obsidian/navy institutional interface with an isolated **Simulation Mode** clearly labeled as synthetic test data.
9. **Stage 9 — Testing:** Covers connection lifecycle, decimal digit extraction, buffer hygiene, quantitative math, `NO SIGNAL` gating, scanner behavior, look-ahead prevention, and responsive layout.
10. **Stage 10 — Production Delivery:** Ready to serve over HTTPS/WSS with SPA fallback routing and zero embedded credentials.

## Quick Start on GitHub

1. Create a new repository on **github.com** (e.g., `deriv-quant-ai-terminal`).
2. Add **`index.html`** and **`README.md`** in the repository root and commit them to `main`.
3. Open `index.html` through any local static server (or GitHub Pages / Vercel / Netlify) to launch the terminal, then click **Connect Public Feed** or **Simulation Mode**.
