# 10-Minute Memo

Generate a **VC-style investment memo from any startup website in under 60 seconds.**

Paste a URL → the app scrapes the site → Gemini 2.5 Flash writes the memo.

**GitHub:** [github.com/prableenkaurr/preraise](https://github.com/prableenkaurr/preraise)

---

## What it generates

| Section | What's covered |
|---|---|
| Company Snapshot | Name, one-liner, industry, business model |
| Problem | Problem statement + why it matters |
| Product | Core product, key features, differentiation |
| Market Opportunity | Category, trends, adoption drivers |
| Competitive Landscape | Competitors, advantages, weaknesses |
| Team Signals | Hiring activity, growth indicators |
| Bull Case | Top 3 reasons it could be a category leader |
| Bear Case | Risks, competitive threats, execution risks |
| Investment Thesis | One tight VC-associate paragraph |
| Recommendation | Strong Buy / Worth Further Research / Pass |

Plus a **Confidence Score (0–100)** and an **AI chat panel** for follow-up questions.

---

## Fund personalization

Append `?fund=` to white-label the entire app for a specific firm — the navbar, hero, page title, and exported PDF title all update automatically.

| Link | Displays as |
|---|---|
| `yourdomain.com?fund=PearVC` | **10-Minute Memo for Pear VC** |
| `yourdomain.com?fund=TribeCapital` | **10-Minute Memo for Tribe Capital** |
| `yourdomain.com?fund=Sequoia` | **10-Minute Memo for Sequoia** |
| `yourdomain.com?fund=a16z` | **10-Minute Memo for a16z** |
| `yourdomain.com?fund=YCombinator` | **10-Minute Memo for Y Combinator** |
| `yourdomain.com?fund=AnyName` | **10-Minute Memo for Any Name** *(any slug works)* |

To add a fund to the known-name lookup (for exact casing), edit `lib/fund.ts`.

---

## Export

- **Export PDF** — browser print dialog, memo-only layout
- **Export Markdown** — downloads a `.md` file
- **Copy memo** — full memo to clipboard as Markdown

---

## Stack

- Next.js 14 App Router + TypeScript
- Tailwind CSS
- Google Gemini 2.5 Flash (structured JSON output via `responseSchema`)
- Cheerio for web scraping (homepage + about / careers / pricing)
- Vercel deployment ready

---

## Local development

```bash
git clone https://github.com/prableenkaurr/preraise.git
cd preraise
npm install
cp .env.example .env.local   # add your GEMINI_API_KEY
npm run dev                  # http://localhost:3000
```

### Environment variables

| Variable | Required | Notes |
|---|---|---|
| `GEMINI_API_KEY` | **Yes** | Get one free at [aistudio.google.com](https://aistudio.google.com/app/apikey) |

---

## Deploy to Vercel

```bash
npm run build        # verify build locally first
vercel --prod
```

Set `GEMINI_API_KEY` in your Vercel project → **Settings → Environment Variables**.

Or connect the GitHub repo to Vercel for automatic deployments on every push to `main`.
