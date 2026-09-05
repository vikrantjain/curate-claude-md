---
name: curate-claude-md
description: Rules for creating, updating, or trimming a CLAUDE.md file. Use before writing a new CLAUDE.md, before adding or changing ANY line in an existing one (including a single bullet appended at the end of a task), when asked to "remember this about the project" or "update the project instructions", and when deciding whether a fact belongs in CLAUDE.md or in a doc, a README, or a skill.
---

# Curating CLAUDE.md

A CLAUDE.md is a **briefing read before every action**, not a record of what happened. The
record wins by default, one defensible paragraph at a time — these rules make the briefing win.

When a case below isn't covered, decide it from that sentence: does the next session need this
before it acts, or only while doing one specific thing — or not at all, because the code or git
already says it?

## The rules

1. **Not a log, not a plan.** No work done, no work planned, no status, no "done" markers,
   no changelog, no "what we tried". Git holds the history and the delivery plan holds the
   schedule; a file that opens with what was already built gets read as a report instead of
   instructions. Cutting this content is deletion, not relocation — it is already in git.

2. **No dates on your own work.** Write *"corrected"*, not *"corrected 2026-03-11"*. Dates
   that are facts about the subject stay — a pinned version, an upstream release, a spec
   revision, a deadline.

3. **Point, don't duplicate.** If a doc, README, or spec already holds the content, link it
   in one line and stop. A summary written beside a pointer goes stale silently and is then
   trusted — that is worse than no summary. Progressive disclosure: the briefing says where
   to look, the doc answers when you get there.

4. **Let the code speak.** Anything discoverable by reading the code — structure, file
   layout, signatures, what a module does — stays out; name where to look instead. Code that
   needs a CLAUDE.md paragraph to be understood needs a better name or a comment, in the code.

5. **Include a line only if forgetting it causes a silent wrong result** — not inconvenience,
   but a plausible wrong answer, a false green, an empty value. Say what breaks without it; a
   rule that cannot name its failure mode is advice, and advice is not followed. Apply this
   per line, not per file: drift arrives as a paragraph that passes "is this true and useful?"
   and fails this one.

6. **Procedures go in a skill; evidence goes in `docs/`.** Checklists, style rules, syntax
   tables and setup steps are needed *while doing a specific task*, not before every action.
   Measurements, result tables and verification logs are the proof of a rule, not the rule.

7. **Keep it short enough to be read every time.** Roughly 150 lines, no section over ~40 —
   a longer one is a doc wearing a heading. Past that, audit instead of appending. Every line
   is paid on every session in that directory, including sessions that never touch it.

8. **Write into the file that owns the fact.** Only the working directory's CLAUDE.md and its
   ancestors load. A subproject with its own file owns its context: the parent names it in one
   line — **immediate children only** — and stops, or the root becomes a map of the whole tree
   and goes stale from every direction at once. Exception, per rule 5: a child's file does
   **not** load for a session running at the parent, so a constraint that fails silently gets
   its imperative restated there — one line, explanation left in the child. Same for an
   invariant spanning two siblings: duplicate the imperative on each side, not the explanation.

## Updating an existing file

1. Read the **whole** file — accretion is invisible line by line; that is how it got there.
2. For each paragraph ask: **is this the rule, or the proof the rule is real?** Proof that
   exists nowhere else moves to `docs/`, leaving at most a one-clause citation. Proof already
   recorded elsewhere — git history, an existing doc, the code itself — is **deleted, not
   relocated**: a doc created to hold it is a second copy, which is rule 3's failure, and the
   staler copy is the one that gets trusted.
3. Strip dates from your own work, then re-check the whole file against rule 5.
