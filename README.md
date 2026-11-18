# Sip Happens Café — feedback widget

Homework #1 of the React course: a feedback widget for a café. Visitors rate the service with
**Good**, **Neutral** or **Bad**, and the app shows the number of votes in each category, the total
and the percentage of positive feedback.

## Tech stack

Vite, React 19, TypeScript, CSS Modules, modern-normalize, ESLint, Prettier. Deployed to Vercel.

## Getting started

Requires Node.js 22.12 or newer.

```bash
npm install
npm run dev
```

Then open [http://localhost:5173](http://localhost:5173).

## Scripts

| Command                | What it does                                 |
| ---------------------- | -------------------------------------------- |
| `npm run dev`          | Start the dev server                         |
| `npm run build`        | Check types and build the production version |
| `npm run preview`      | Serve the built `dist/` locally              |
| `npm run lint`         | Check code with ESLint                       |
| `npm run format`       | Format all files with Prettier               |
| `npm run format:check` | Check formatting without changing files      |

## Project structure

```
src/
    main.tsx                    entry point
    index.css                   global styles
    types/
        votes.ts                shared types: Votes, VoteType
    components/
        App/                    owns the votes state, computes totals, renders the rest
        CafeInfo/               café name and description
        VoteOptions/            Good / Neutral / Bad buttons and Reset
        VoteStats/              vote counts, total and positive rate
        Notification/           "No feedback yet" message
```

Each component folder has a `.tsx` file and a `.module.css` file with the same name.

## How it works

- `App` keeps the votes in state (`{ good, neutral, bad }`) and passes `handleVote` and `resetVotes`
  to `VoteOptions` as callbacks.
- `totalVotes` and `positiveRate` are computed from the state on every render, not stored.
- Until the first vote, `Notification` is shown instead of `VoteStats`, and the **Reset** button is
  hidden.
