# PRism 🔍

> PRism is an AI-powered code review tool that analyzes pull request diffs and delivers context-aware feedback — starting as a lightweight GitHub bot and scaling into a full web dashboard for larger repos.

---

## What is PRism?

Most code review tools tell you *what* changed. PRism tells you *what it means*.

PRism goes beyond surface-level diff scanning — it builds context around your changes, understands the surrounding code, and delivers reviews that read like they came from a senior engineer on your team. No noise. No generic suggestions. Just smart, targeted feedback on what actually matters.

---

## Features

- 🤖 **GitHub Bot** — Install on any repo and get automatic AI reviews on every pull request
- 💬 **Hybrid Feedback Model** — A top-level PR summary + selective inline comments + a formal review verdict (`APPROVE` / `REQUEST_CHANGES` / `COMMENT`)
- 🧠 **Context-Aware Reviews** — Fetches surrounding code, not just the diff, for smarter LLM analysis
- 🔍 **Diff Parser** — Breaks diffs into meaningful chunks by file and hunk for precise feedback
- 📊 **Web Dashboard** *(Phase 2)* — Paste a PR link, sign in with GitHub, and get a beautiful file-by-file breakdown of the review
- 📁 **Review History** *(Phase 2)* — Track feedback trends across PRs and codebases over time

---

## How It Works

```
GitHub PR Event
      ↓
[Webhook Server]     ← Validates GitHub signature, receives PR events
      ↓
[Diff Fetcher]       ← Pulls the raw diff via GitHub API
      ↓
[Diff Parser]        ← Breaks diff into meaningful chunks by file/hunk
      ↓
[Context Builder]    ← Fetches surrounding code for richer LLM context
      ↓
[Review Engine]      ← Sends structured prompt to LLM
      ↓
[Comment Formatter]  ← Maps LLM output to exact PR line numbers
      ↓
[GitHub Comment Poster] ← Posts inline comments + summary + verdict
```

---

## Monorepo Structure

```
PRism/
├── apps/
│   ├── bot/              ← Phase 1: GitHub bot
│   └── dashboard/        ← Phase 2: Web dashboard
├── packages/
│   ├── github/           ← Shared GitHub API logic (Octokit)
│   ├── llm/              ← Shared LLM / review engine logic
│   └── diff-parser/      ← Shared diff parsing logic
└── package.json          ← Monorepo root (Turborepo)
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Runtime | Node.js + TypeScript |
| Webhook Server | Express.js |
| GitHub SDK | Octokit |
| LLM | Claude API / OpenAI |
| Monorepo | Turborepo |
| Deployment | Railway / Render |
| Dashboard (Phase 2) | Next.js + Tailwind CSS |

---

## Roadmap

- [x] Project architecture and monorepo setup
- [ ] **Phase 1** — GitHub bot (webhook → diff → LLM → comments)
- [ ] **Phase 2** — Web dashboard (GitHub OAuth + PR review UI)
- [ ] **Phase 3** — Review history, team analytics, trend tracking

---

## Getting Started

> 🚧 PRism is currently in active development. Installation instructions will be available with the Phase 1 release.

---

## Contributing

PRism is open source and contributions are welcome. Feel free to open issues, suggest features, or submit pull requests.

---

## License

MIT © [Tioluwani Enoch](https://github.com/tioluwani-enoch)
