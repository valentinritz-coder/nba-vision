# NBA Betting Research Pipeline

This repository contains a research pipeline to build a **clean,
reproducible and temporally safe NBA dataset** for predictive modeling
and betting research.

The primary objective of this project is **not to build a model
immediately**, but to create a **robust data foundation** from official
NBA statistics before experimenting with machine learning, clustering
and betting strategies.

The project follows a strict principle:

> Build the data foundation first. Modeling comes later.

------------------------------------------------------------------------

# Project Goals

Short term goals:

1.  Ingest raw data from the official NBA Stats API (`stats.nba.com`)
2.  Store raw responses without modification
3.  Normalize the data into relational tables
4.  Build a reproducible match-level dataset
5.  Enable safe temporal feature engineering
6.  Prepare the foundation for predictive models and betting simulations

Future goals:

-   player clustering
-   team clustering
-   advanced features
-   predictive models
-   betting simulation
-   closing line value analysis
-   bankroll simulation

------------------------------------------------------------------------

# Design Principles

## 1. Raw data is immutable

All API responses must be stored exactly as received. Raw data is never
modified.

## 2. Temporal safety

No feature may use information that was not available **before the game
tipoff**.

## 3. Layer separation

RAW DATA → NORMALIZED DATA → FEATURES

## 4. Reproducibility

The full dataset must be rebuildable from scratch.

## 5. Small iterations

1.  ingestion
2.  normalization
3.  basic features
4.  baseline models
5.  advanced features
6.  clustering
7.  betting logic

------------------------------------------------------------------------

# Data Sources

Primary data source:

NBA Stats API\
https://stats.nba.com

Example endpoint used initially:

`leaguedashteamstats`

------------------------------------------------------------------------

# Repository Structure

nba-betting/

src/\
    config/\
    ingestion/\
    normalization/\
    features/\
    models/\
    backtest/\
    betting/\
    utils/

data/\
    raw/\
    processed/

configs/

tests/

migrations/

reports/

------------------------------------------------------------------------

# Core Database Layers

## Raw Layer

Stores API responses exactly as received.

Example table: `raw_api_responses`

Fields include: - endpoint - request parameters - response json -
fetched_at - source

## Normalized Layer

Clean relational tables:

-   teams
-   players
-   games
-   team_game_stats
-   player_game_stats
-   odds_snapshots

## Feature Layer

Match-level dataset used for modeling.

Example: `match_features`

Each row represents a **single game prediction point**.

------------------------------------------------------------------------

# Technology Stack

Python 3.12

Core libraries:

-   SQLAlchemy 2.0
-   Alembic
-   PostgreSQL
-   httpx
-   pandas or polars
-   pydantic-settings

Dev tools:

-   ruff
-   pytest
-   mypy (optional)

------------------------------------------------------------------------

# Initial Pipeline

1.  Fetch NBA API data\
2.  Store raw API response\
3.  Normalize team stats\
4.  Build match-level dataset\
5.  Train baseline logistic regression model

------------------------------------------------------------------------

# Development Philosophy

The project prioritizes:

-   correctness over speed
-   clarity over cleverness
-   reproducibility over convenience

Fancy modeling is useless if the dataset is flawed.

------------------------------------------------------------------------

# Disclaimer

This repository is intended for research and experimentation. Sports
betting involves risk.
