# SearchedBy (formerly GEO Scan): an AI product taken to production in about ten days

Own product, open beta since October 2026 · **[searchedby.com](https://searchedby.com)** · [Case page on pablodpavon.com](https://pablodpavon.com/proyectos/geo-scan.html) · Engineering notes: [searchedby-engineering](https://github.com/pablodpavon/searchedby-engineering)

![Landing page during the invite-only beta](images/landing.jpg)

**What it is.** A scan that shows a business what ChatGPT, Perplexity and Google's AI answer when a customer asks about its field, and what its website is missing to be found. You enter your site, confirm your email, and a few minutes later you get a result page.

**Why I built it.** I wanted to know whether I could take a product from idea to production with AI writing almost all of the code, while I kept the parts that need judgment: the method, the rules, and checking every result before anyone sees it. I also wanted an honest answer to a simple question: does an AI assistant even know a given business exists?

## How it works

![How one scan works](images/how-it-works.jpg)

1. **Crawl the site.** 21 automated checks in the free scan: AI bot access, structured data, content in the HTML, entity consistency.
2. **Build the questions.** The scan detects the business type and writes the questions a real customer would ask, with the city for a local business.
3. **Ask the AI engines.** The questions go to the engines by API: ChatGPT, Perplexity, Claude, and Google AI Overviews and AI Mode, configured per market.
4. **Classify and explain.** Is the business mentioned, cited or missing, and who shows up instead. A single answer is never presented as a score.
5. **Human control.** Every scan also sends me a control email, and I review each beta result before it counts.

![Example result, fictional cafe](images/result-example.jpg)

*The example uses a fictional business (lumbre-cafe.example).*

## What the AI did and what I did

The code (Python, FastAPI, SQLite, on a Hetzner server behind Cloudflare) was written with Claude Code. I wrote the method, the scoring and disclosure rules, the wording of every finding and the acceptance criteria. With AI the bottleneck moves from writing code to defining what "correct" means, and that is analyst work.

## How I know it is right

- About 3,800 automated tests (2,684 pipeline, 1,184 web app, as of 1 Nov 2026), run on two Python versions before every deploy.
- Backup before every deploy, then a file-by-file checksum comparison between my machine and the server.
- No language ships without native review. Four interface languages: English and Spanish complete; Hebrew stayed hidden until a native speaker checked it, and German is still partly hidden for the same reason.
- Anti-abuse limits, email verification and a bot check on the form, because every scan calls paid APIs.

## What I learned

- AI writes code fast, so most of my time went into rules and test cases.
- One AI answer is not a measurement. The scan labels its sample as indicative and never averages engines into one score.
- Translation is part of quality, so it gets the same release gate as code.

---

The product code lives in a private repository. This repository holds the case study; process notes and generic tooling are in [searchedby-engineering](https://github.com/pablodpavon/searchedby-engineering).

Pablo Pavon · Business & Data Analyst, Berlin · [pablodpavon.com](https://pablodpavon.com) · [LinkedIn](https://www.linkedin.com/in/pablo-damian-pavon) · [Upwork](https://www.upwork.com/freelancers/pablopavon)
