# Football Prediction Market — GenLayer Intelligent Contract

A football prediction market built as a GenLayer Intelligent Contract (official GenLayer Studio example), deployed and run in GenLayer Studio.

## How it works

`football_prediction_market.py` defines a `PredictionMarket` contract:

- `__init__(game_date, team1, team2)` — creates a market for one match. The resolution URL is the BBC Sport scores-and-fixtures page for the given date.
- `resolve()` (public write) — fetches the BBC Sport page for the match date, asks an LLM to extract the final score and winning team as JSON, and validates the result with `gl.eq_principle.strict_eq`. Once resolved, the winner and score are stored on-chain. Calling it again raises "Already resolved".
- `get_resolution_data()` (public view) — returns `winner`, `score` and `has_resolved`.

## Run it

Requires GenLayer Studio and the `py-genlayer` dependency declared at the top of the file. Open the contract in GenLayer Studio, deploy it, then call `resolve()` after the match and read the result with `get_resolution_data()`.
