# MineCraft Server Demand Forecasting

## Project Overview

This project analyzes player behavior data from a MineCraft research server to predict concurrent player counts and optimize resource allocation. Using 6 months of gameplay session data (April-September 2024) from 200 unique players and over 2,000 play sessions, we build predictive models to forecast peak demand periods for server license capacity planning.

## Research Question

**Can time-based features (hour of day, day of week, month) and player characteristics (experience level, previous play time) predict the number of concurrent players in hourly time windows on the MineCraft research server?**

## Motivation

A research group at UBC's Computer Science department operates a MineCraft server to study player behavior and gameplay patterns. To ensure smooth operations and cost-effective resource management, they need to:

- Predict when the most players will be online simultaneously
- Allocate sufficient software licenses to handle peak demand
- Optimize costs by avoiding over-provisioning during low-activity periods
- Schedule maintenance during minimal-impact time windows

## Dataset

The project uses two primary datasets:

1. **players.csv** (200 players)
   - Player demographics (age, gender)
   - Experience level (Beginner, Amateur, Regular, Veteran, Pro)
   - Previous gameplay hours
   - Newsletter subscription status

2. **sessions.csv** (1,500+ sessions)
   - Session start and end timestamps
   - Player identifiers linking to player characteristics
   - Enables calculation of concurrent player counts for any time window

## Methodology

- **Approach**: Multiple Linear Regression (baseline) with potential extension to Random Forest Regression
- **Key Features**: Hour of day, day of week, month, lag variables, rolling averages, player experience composition
- **Evaluation**: RMSE, MAE, R², MAPE on temporal test split (training: Apr-Jul, testing: Aug-Sep)
- **Tools**: R, tidyverse, lubridate, ggplot2

## Key Findings (Preliminary EDA)

- **Peak hours**: 21:00-23:00 (evening gaming after work/school)
- **Weekend effect**: Saturday shows ~44% more activity than Friday
- **Surprising Friday low**: Friday is the lowest-activity day (181 sessions vs. Saturday's 261)
- **Session patterns**: Most sessions are 15-30 minutes, but 15% exceed 1 hour (creating sustained demand)

