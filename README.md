# Agentic Workflows Project

This project implements a small multi agent workflow that generates a short research report from a topic. It shows how to combine planning, tool based research, writing, and editing in one end to end flow.

## What this project does

Given a topic, the system runs a simple pipeline:

1. A planner agent creates a short plan as a list of steps
2. An executor agent reads each step and chooses the right agent to run it
3. A research agent gathers external info using tools (arXiv, web search, Wikipedia)
4. A writer agent drafts parts of the report
5. An editor agent critiques and improves the draft
6. The final output is a Markdown research report

## Goal

The goal is to build an agentic workflow that is reliable and easy to extend.

This includes:
- writing prompts for different agent roles
- enabling tool use for research
- orchestrating multiple steps with shared context
- using feedback to improve a draft

## Why it matters

Many real ML and data products need more than one single model call. This project is a simple example of how to structure multi step LLM work so it can:
- run repeatably
- keep a history of what happened at each step
- produce a final output that can be reviewed and improved

## What is included

- `Agentic_Workflows.ipynb`
  - `planner_agent` generates a plan as a Python list
  - `research_agent` uses tool calls to gather sources
  - `writer_agent` drafts technical text
  - `editor_agent` revises and improves drafts
  - `executor_agent` coordinates the workflow (the orchestrator)

Unit tests are included in the notebook to validate each agent function.

## Requirements

You need:
- Python 3.x
- Jupyter Notebook
- `aisuite`
- the local modules used by the notebook:
  - `research_tools`
  - `unittests`

If your `research_tools` uses external APIs (example Tavily), you may need the related API key in your environment variables.

## How to run

1. Open `Agentic_Workflows.ipynb`
2. Run the cells in order
3. Run the unit test cells to confirm each agent works
4. Run the final example that calls `executor_agent(topic)`

The executor limits the plan to a maximum of 4 steps by default to keep runtime reasonable.

## Output

The final step returns a Markdown research report for the chosen topic, with references gathered by the research tools.

