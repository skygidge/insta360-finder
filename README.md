# Insta360 Creator Story Finder

An automated research agent that hunts the web each week for **real people doing remarkable things with Insta360 cameras** — the kind of stories worth featuring on the [Insta360 creator-stories blog](https://www.insta360.com/blog/category/creator-stories).

## ▶️ Open the Finder

**The live finder lives here:**

# → [skygidge.github.io/insta360-finder](https://skygidge.github.io/insta360-finder/)

Browse every story the agent has surfaced, filtered by source, confidence, and date.

---

## What it does

Once a week an AI agent runs, rotating through a different set of sources each time:

| Week | Focus |
|------|-------|
| **A** | Reddit + YouTube |
| **B** | News articles + scientific journals |
| **C** | Forums + source discovery |

For every candidate it records the creator, location, what they did, the Insta360 product involved, why the story matters, a source link, and a confidence rating. It skips anyone already featured or already found, and it prioritizes 2025–present content.

The agent learns between runs: it tracks which queries paid off, which sources block scraping, and any feedback on story quality, so each week is a little sharper than the last.

## Repository layout

| Path | Purpose |
|------|---------|
| [`index.html`](index.html) | The live finder — the web viewer published via GitHub Pages |
| [`prompt.md`](prompt.md) | The weekly agent prompt (the finder's full instructions) |
| [`data/exclusion_list.json`](data/exclusion_list.json) | Creators already featured — never suggested again |
| [`data/learnings.json`](data/learnings.json) | Rotating week type, past queries, blocked sources, feedback |
| [`data/results/all_stories.json`](data/results/all_stories.json) | The master list of every story found |
| [`data/results/stories_YYYY-MM-DD.json`](data/results/) | One file per weekly run |
| [`data/results/report_YYYY-MM-DD.md`](data/results/) | Human-readable run reports and top picks |

## How a run works

Each weekly run follows this sequence:

1. Read the exclusion list, master story list, and learnings.
2. Check `next_week_type` and research the matching sources.
3. Write that run's findings to a new `stories_YYYY-MM-DD.json`.
4. Append the new stories to `all_stories.json`.
5. Update `learnings.json` with what worked and what didn't.
6. Publish a short report with the top 2–3 picks.

All reads and writes go through the GitHub Contents API, so the agent can run remotely with no local checkout.

## Story bar

A strong story has a person doing something visually striking or unusual, an Insta360 camera playing a meaningful role, and real stakes — emotional, practical, or a clear before/after. Every entry must be genuine; no fictional examples.
