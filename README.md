# AI Tutor

An adaptive learning companion powered by [Claude Code](https://docs.anthropic.com/en/docs/claude-code). It maintains a persistent knowledge graph of your understanding and teaches through exercises and explanations — like Anki, but conversational.

## How It Works

The `CLAUDE.md` file instructs Claude Code to act as an adaptive tutor. It maintains a `LEARNER.md` file that tracks:

- Your learning goals
- Concepts you've encountered, with understanding levels (1–3) and dependencies
- When each concept was last reviewed
- Brief session history

Each conversation is like an Anki review session: the tutor presents material, tests understanding through exercises, and updates your knowledge state based on your performance and feedback. The knowledge graph is built incrementally — it emerges from what you actually study, not from a predefined curriculum.

## Setup

1. Copy or clone this repo into a new directory for your subject
2. Add your learning materials (PDFs, textbooks, papers, notes) to the directory
3. Run `claude` in the directory

That's it. No code to install — this is just a prompt file.

## Usage

Talk to it like a tutor:

- "I want to learn group theory from this textbook"
- "Explain eigenvalues to me"
- "Give me an exercise on integration by parts"
- "Too hard" / "I already know this" / "Skip"
- "What should I review?"

The tutor will teach through explanation and exercises, track your understanding in `LEARNER.md`, and suggest what to work on next.

## Design

**One repo per subject.** Each instance is scoped to one topic or a set of related materials. Examples:

- A directory for "Linear Algebra" with a textbook PDF
- A directory for "ML Papers" with 10 related papers for a research project
- A directory for "Rust Programming" with the Rust book

**No code, just a prompt.** The LLM processes the knowledge graph in-context. This keeps it simple, auditable, and easy to modify. If you want to change how the tutor behaves, edit `CLAUDE.md`.

**Git timestamps as memory.** The tutor commits `LEARNER.md` after updates, so the full history of your learning is preserved in git. This data can later be used to study how well the LLM tracks learning progress, calibrate forgetting curves, or train better tutoring strategies.

## Background

This project is a proof of concept for **workflow-preserving, skill-sustaining AI** — an alternative to the default chatbot pattern where the AI simply gives you the answer. Instead, the AI builds a model of what you know and teaches you to understand the material yourself.

See: Ghosh et al., "Chatbots Are Not (Yet) Suitable for AI-Assisted Learning" (2025/2026) for the motivation.
