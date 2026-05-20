---
project: Personal Website
status: draft-ready
source_template: https://github.com/RATIU5/zaggonaut
created: 2026-05-20
owner: Javier Vergara
implementation_target: Windsurf AI
---

# Personal Website — Astro Zaggonaut Requirements

> **Purpose:** This document is the implementation brief for adapting the [Zaggonaut Astro template](https://github.com/RATIU5/zaggonaut) into a minimal personal website for Javier Vergara. It is written so it can be copied into Windsurf as the requirements source for the build.

## 1. Goal

Build a clean, minimal, fast personal website based on the Zaggonaut Astro template that presents Javier Vergara’s professional profile, experience, and active projects.

The site should feel:

- Minimalistic.
- Professional.
- Founder/operator-oriented.
- More polished and personal than the default template.
- Slightly more colorful than Zaggonaut, but still restrained.
- Focused on projects, experience, and practical expertise.

The site should not feel like:

- A flashy startup landing page.
- A generic CV export.
- A corporate legal profile.
- A loud personal brand site.
- A heavily animated portfolio.

## 2. Source material

Use these sources for content:

1. Javier’s LinkedIn profile PDF.
2. Existing Obsidian project context.
3. The current Zaggonaut template structure.

Important extracted LinkedIn facts:

- **Name:** Javier Vergara.
- **Location:** Cyprus.
- **Email:** javier@trauko.eu.
- **LinkedIn:** `https://www.linkedin.com/in/javier-vergara-eu`.
- **Current headline:** Operational GDPR for lean teams | I help your company integrate GDPR into the tools you already use | Let’s connect!
- **Core profile theme:** Practical GDPR, data protection, privacy operations, startup operations, and building usable systems for lean teams.
- **Top skills:** Data Privacy Best Practices, Privacy Regulations, Organization Skills.
- **Languages:** Spanish, English, German.
- **Certifications:** Fellow of Information Privacy (FIP), Attorney, Certified Information Privacy Technologist (CIPT), Notion Workflows Badge, Notion Certified Admin.
- **Education:** University of Helsinki LLM International Business Law; University of Tartu MA Information Technology Law; Universidad de Chile LLB.

## 3. Template constraints

Base the implementation on Zaggonaut.

Known template details:

- Astro 6.
- TypeScript.
- Tailwind CSS 4.
- Content Collections.
- TOML config in `content/configuration.toml`.
- Project entries in `content/projects/*.md`.
- Blog entries in `content/blogs/*.md`.
- Main styling in `src/styles/global.css`.
- Main layout in `src/layouts/Layout.astro`.
- Hero in `src/components/home/Hero.astro`.
- Featured projects in `src/components/home/FeaturedProjects.astro`.
- Project snippets in `src/components/ProjectSnippet.astro`.
- Projects index in `src/pages/projects/index.astro`.
- Existing Zaggonaut README says `pnpm` is the only supported package manager.

Use the existing structure as much as possible. Prefer content/config updates and small component edits over a full redesign.

## 4. Visual direction

### 4.1 Base style

Keep the site mostly neutral:

- Background: white or the template’s default light neutral background.
- Text: black or `#222222`.
- Overall palette: mostly black/white/neutral.
- Preserve Zaggonaut’s minimal, mono, retro-inspired feeling where it helps.
- Avoid heavy gradients, neon sections, colorful backgrounds, and busy UI.

### 4.2 Required colors

Use the following colors only as accents, primarily around the profile picture / identity mark:

- Blue: `#38B6FF`.
- Yellow: `#FFDE59`.

Rules:

- These colors should be used around the profile image only, for example:
  - split circular border,
  - small offset blocks/shapes behind the profile picture,
  - subtle ring/outline,
  - small accent marks near the hero image.
- Do not use these colors as full-page backgrounds.
- Do not recolor all buttons, tags, or headers with these colors.
- Do not make the website look like a blue/yellow brand site. It should still look mostly monochrome.

### 4.3 Typography

Use default template fonts unless a change is needed for readability.

Acceptable:

- Keep IBM Plex Mono from the template.
- Keep Zaggonaut’s display font for headings if it remains legible.
- Body text must be readable and not too small.

Preferred text colors:

- Primary text: `#111111` or `#222222`.
- Muted text: neutral gray.
- Dark mode can remain if it is not broken, but light mode should be the primary visual target.

### 4.4 Profile image treatment

The current Zaggonaut hero image is grayscale and circular. Adapt it:

- Use Javier’s profile picture if available in the project assets.
- Keep it circular.
- Remove or reduce forced grayscale if it makes the picture feel flat.
- Add a subtle `#38B6FF` / `#FFDE59` accent treatment around the image.
- Keep image size close to the existing template scale unless the layout requires a small increase.

Suggested implementation:

- Modify `src/components/home/Hero.astro`.
- Wrap the image in a relative container.
- Add two absolute accent layers behind the image:
  - one blue offset shape,
  - one yellow offset shape.
- Keep the image itself on top with a clean border.

## 5. Site structure

Implement a small personal website with the following pages:

1. Home.
2. Projects.
3. Project detail pages.
4. Optional blog/articles page, but only if useful.

### 5.1 Navigation

The navigation should be minimal:

- Home.
- Projects.
- Articles or Notes only if content exists.
- LinkedIn icon/link.
- GitHub icon/link only if Javier provides a GitHub URL.

If there is no active blog content, either:

- remove Blog from the menu, or
- rename Blog to Notes and add 1–2 useful starter notes.

Do not leave default Zaggonaut demo content visible.

## 6. Home page content

### 6.1 Hero section

Hero should clearly explain who Javier is and what he works on.

Recommended copy:

```text
Javier Vergara
Operational GDPR, privacy systems, and AI-enabled operations for lean teams.
```

Alternative subtitle:

```text
I build practical systems for data protection, market research, automation, and founder-led operations.
```

Hero requirements:

- Show Javier’s name clearly.
- Mention operational GDPR / privacy systems.
- Mention practical systems / operations / AI workflows without making the site only about AI.
- Use one short CTA to Projects.
- Optional second CTA to LinkedIn.

Recommended CTA:

- Primary: `View Projects` → `/projects`.
- Secondary: `Connect on LinkedIn` → Javier’s LinkedIn URL.

### 6.2 Short intro section

Add a short intro below the hero or inside the homepage content.

Suggested copy:

```text
I work at the intersection of data protection, startup operations, and practical automation. My background combines law, compliance, privacy, customer operations, and entrepreneurship — from Wise, Salv, and 3Commas to building my own projects.

Today I am focused on turning complex operational problems into systems that lean teams can actually maintain.
```

Keep this concise. Avoid a long biography on the homepage.

### 6.3 Featured projects

The homepage should feature the main current projects:

1. Call Brad.
2. Kontana.
3. Atlaset.

Optionally add FinKratt as a past/startup project if it helps the professional story.

The featured project cards should be concise and link to detail pages.

## 7. Projects page

The Projects page is the core page of the website.

It should include:

- A short page intro.
- Cards/list items for active projects.
- Tags for each project.
- Clean project detail pages using Zaggonaut content collections.

Recommended page title:

```text
Projects
```

Recommended description:

```text
Current and past work across operational GDPR, AI-enabled operations, market research, automation, and startup building.
```

## 8. Project content requirements

Create Markdown project files in `content/projects/`.

### 8.1 Call Brad

File: `content/projects/call-brad.md`

Frontmatter draft:

```yaml
---
title: Call Brad
slug: call-brad
description: Practical GDPR systems for lean teams.
longDescription: Call Brad helps growing companies turn GDPR from scattered documents and legal anxiety into practical privacy systems their teams can maintain.
cardImage: "/project-images/call-brad.png"
tags: ["GDPR", "privacy operations", "data protection", "lean teams"]
liveDemoUrl: "https://callbrad.eu"
timestamp: 2024-07-01T00:00:00+00:00
featured: true
---
```

Body content should include:

```markdown
## What it is

Call Brad helps growing companies manage GDPR in a practical, operational way.

The focus is not compliance theatre. The focus is building privacy systems that real teams can understand, maintain, and use inside their existing tools.

## What it helps with

- Practical GDPR Workspace setup.
- Privacy records creation and maintenance.
- RoPA, DPIA, TIA, vendor review, and data subject request workflows.
- DPO and privacy operations support.
- Employee training and internal guidance.
- Practical GDPR implementation for lean teams.

## Positioning

Operational GDPR for lean teams.

Call Brad sits between traditional legal advice, generic template packs, and heavy enterprise privacy software. It is for companies that need structure without bureaucracy.
```

### 8.2 Kontana

File: `content/projects/kontana.md`

Frontmatter draft:

```yaml
---
title: Kontana
slug: kontana
description: Market research and competitive analysis for sharper positioning.
longDescription: Kontana is focused on disciplined market research, competitor analysis, and useful positioning insights.
cardImage: "/project-images/kontana.png"
tags: ["market research", "competitive analysis", "positioning"]
timestamp: 2026-01-01T00:00:00+00:00
featured: true
---
```

Body content should include:

```markdown
## What it is

Kontana is a research-led project focused on market understanding, competitive analysis, and positioning clarity.

## Focus areas

- Market mapping.
- Competitor teardown and comparison.
- Category and positioning research.
- Customer language and buying-trigger analysis.
- Turning research notes into decisions.

## Current role

Kontana is still developing. The website should present it as an active research/building project without overclaiming maturity.
```

### 8.3 Atlaset

File: `content/projects/atlaset.md`

Frontmatter draft:

```yaml
---
title: Atlaset
slug: atlaset
description: Systems, automation, AI workflows, and practical implementation.
longDescription: Atlaset focuses on helping teams design better operating systems, automate useful workflows, and implement AI where it actually improves execution.
cardImage: "/project-images/atlaset.png"
tags: ["automation", "AI workflows", "operations", "systems"]
timestamp: 2026-01-01T00:00:00+00:00
featured: true
---
```

Body content should include:

```markdown
## What it is

Atlaset sits around execution, systems, automation, operations, AI workflows, and practical implementation.

## Focus areas

- SOPs and operating systems.
- Automation and workflow design.
- AI-assisted research and content operations.
- Internal tooling.
- Dashboards, handoffs, and process improvement.

## Positioning guardrail

Avoid vague “AI will change everything” positioning. Atlaset should be shown through concrete examples, practical systems, and operator-level lessons.
```

### 8.4 FinKratt — optional past project

File: `content/projects/finkratt.md`

Use only if the site should include past founder experience.

Frontmatter draft:

```yaml
---
title: FinKratt
slug: finkratt
description: Personal finance startup focused on debt reduction, savings, and financial control.
longDescription: FinKratt was a personal finance startup built from concept through market validation and MVP development.
cardImage: "/project-images/finkratt.png"
tags: ["startup", "personal finance", "MVP", "founder experience"]
liveDemoUrl: "https://finkratt.com/"
timestamp: 2023-04-01T00:00:00+00:00
featured: false
---
```

Body content should include:

```markdown
## What it was

FinKratt was a personal finance startup focused on helping people reduce debt, build savings, and regain control of their finances.

## Role

Javier co-founded the company, built the concept from scratch, validated the market, and developed the MVP.

## Why it matters

It is part of Javier’s founder/operator background and connects legal, compliance, product, and startup execution experience.
```

## 9. Experience content

The site does not need to reproduce the entire LinkedIn CV. Keep experience selective and narrative-led.

Include a short experience section either:

- on the homepage below projects, or
- as a separate `About` section/page if that fits the implementation better.

Recommended structure:

### Current focus

- Call Brad — Privacy Lifeguard / practical GDPR systems.
- Atlaset — systems, automation, AI workflows, and implementation.
- Kontana — market research and competitive analysis.

### Previous experience

- FinKratt — Co-Founder, personal finance startup.
- 3Commas.io — Senior Legal Counsel; managed internal privacy programme and privacy business function.
- Salv — Legal Counsel and Compliance Specialist; GDPR, contracts, client integration, compliance and fintech operations.
- Wise — compliance quality assurance, enhanced due diligence, and customer support.
- Earlier legal and entrepreneurial work in Chile.

Suggested concise copy:

```text
Before focusing on my own projects, I worked across legal, privacy, compliance, fintech operations, customer support, and startup building — including roles at Wise, Salv, 3Commas, and FinKratt.
```

## 10. About/profile content

If an About section/page is added, use this as the basis:

```markdown
## About

I’m Javier Vergara, a lawyer, privacy professional, and founder/operator working across data protection, practical systems, and AI-enabled operations.

My background combines law, data protection, compliance, startup operations, customer-facing fintech work, and entrepreneurship. I have worked at Wise, Salv, and 3Commas, co-founded FinKratt, and now focus on building practical systems through Call Brad, Atlaset, and Kontana.

I’m especially interested in making complex obligations and messy workflows usable for lean teams.
```

Keep tone professional, direct, and not too self-promotional.

## 11. Certifications and credibility

Add a compact credibility section, not a long credentials wall.

Suggested label:

```text
Credentials
```

Include:

- Fellow of Information Privacy (FIP).
- Certified Information Privacy Technologist (CIPT).
- Attorney.
- Notion Certified Admin.
- Notion Workflows Badge.
- LLM International Business Law — University of Helsinki.
- MA Information Technology Law — University of Tartu.
- LLB — Universidad de Chile.

This can be implemented as:

- a simple bullet list,
- a compact grid,
- or a small section below experience.

## 12. Blog / Articles / Notes

The default Zaggonaut blog content must be removed.

Options:

### Option A — remove blog from navigation for v1

Recommended if there are no ready articles.

Requirements:

- Remove Blog from `content/configuration.toml` menu.
- Delete or ignore demo blog file.
- Ensure build does not show demo content on homepage.

### Option B — rename Blog to Notes

Use only if adding 1–2 starter notes.

Possible starter notes:

1. `Operational GDPR for lean teams`.
2. `A template is not a privacy programme`.
3. `What competitor websites reveal about market maturity`.
4. `AI workflows only work when the handoff is clear`.

If adding notes, keep them short and high-quality. Do not publish filler.

## 13. Configuration requirements

Update `content/configuration.toml`.

Recommended config values:

```toml
[_.site]
baseUrl = "https://javiervergara.eu"

[_.globalMeta]
title = "Javier Vergara"
description = "Operational GDPR, privacy systems, and AI-enabled operations for lean teams."
longDescription = "Javier Vergara works at the intersection of data protection, startup operations, market research, automation, and practical systems for lean teams."
cardImage = "/social-card.png"
keywords = ["Javier Vergara", "GDPR", "data protection", "privacy operations", "automation", "AI workflows", "market research", "startup operations"]

[_.projectMeta]
title = "Projects — Javier Vergara"
description = "Current and past work across operational GDPR, AI-enabled operations, market research, automation, and startup building."
longDescription = "Projects by Javier Vergara, including Call Brad, Kontana, Atlaset, and selected past startup work."
cardImage = "/social-card.png"
keywords = ["Call Brad", "Kontana", "Atlaset", "GDPR", "privacy", "automation", "market research"]

[_.hero]
title = "Javier Vergara"
subtitle = "Operational GDPR, privacy systems,<br />and AI-enabled operations for lean teams."
image = "/javier-profile.jpg"
ctaText = "View Projects"
ctaUrl = "/projects"

[_.personal]
name = "Javier Vergara"
githubProfile = ""
twitterProfile = ""
linkedinProfile = "https://www.linkedin.com/in/javier-vergara-eu"

[_.texts]
articlesName = "Notes"
projectsName = "Projects"
viewAll = "View All"
noArticles = "No notes found."
noProjects = "No projects found."

[_.menu]
home = "/"
projects = "/projects"
```

If the final domain is different, replace `https://javiervergara.eu` with the correct domain before deployment.

## 14. Styling implementation requirements

Modify `src/styles/global.css` carefully.

Required changes:

- Ensure light background remains neutral.
- Set primary text to black or `#222222`.
- Change the template accent variables away from default emerald if needed.
- Do not globally apply `#38B6FF` and `#FFDE59` everywhere.

Suggested variable direction:

```css
@theme {
  --color-zag-dark: #222222;
  --color-zag-light: #ffffff;
  --color-zag-dark-muted: var(--color-neutral-600);
  --color-zag-light-muted: var(--color-neutral-400);
  --color-zag-accent-light: #38B6FF;
  --color-zag-accent-light-muted: #8fd8ff;
  --color-zag-accent-dark: #FFDE59;
  --color-zag-accent-dark-muted: #d6b93f;
}
```

But if this makes tags/buttons too colorful, keep accent variables neutral and implement blue/yellow only in the hero profile image wrapper.

## 15. Component implementation requirements

### 15.1 Hero profile image accent

Modify `src/components/home/Hero.astro`.

Requirements:

- Add a wrapper around the image.
- Add blue/yellow accent shapes.
- Keep layout responsive.
- Keep image circular.
- Use descriptive alt text.

Implementation direction:

```astro
<div class="relative mb-4 h-44 w-44 shrink-0">
  <div class="absolute inset-0 translate-x-2 translate-y-2 rounded-full bg-[#38B6FF]" aria-hidden="true"></div>
  <div class="absolute inset-0 -translate-x-2 -translate-y-2 rounded-full bg-[#FFDE59]" aria-hidden="true"></div>
  <img
    src={config.hero.image}
    alt={`${config.hero.title} profile photo`}
    class="relative z-10 h-44 w-44 rounded-full border-4 border-white object-cover shadow-sm"
  />
</div>
```

Adjust classes to match the final template code style.

### 15.2 Homepage sections

The current homepage has:

- Hero.
- FeaturedProjects.
- FeaturedArticles.

Update it so it does not feel like a generic blog theme.

Preferred v1:

- Hero.
- Short intro.
- Featured projects.
- Compact experience/credentials section.
- Optional notes only if real content exists.

If no notes are added, remove `FeaturedArticles` from `src/pages/index.astro`.

### 15.3 Footer

The default footer currently includes random quotes. Remove random quote logic.

Replace with a simple footer line:

```text
Javier Vergara — practical systems for privacy, operations, and research.
```

Keep social icons if links exist.

## 16. Assets

Required assets:

- `/public/javier-profile.jpg` — Javier profile image.
- `/public/social-card.png` — optional Open Graph image.
- `/public/project-images/call-brad.png` — optional.
- `/public/project-images/kontana.png` — optional.
- `/public/project-images/atlaset.png` — optional.
- `/public/project-images/finkratt.png` — optional.

If project images are not available, use simple neutral placeholders or omit card images only if the template supports it. Do not use random stock images.

## 17. Content cleanup requirements

Remove or replace all default Zaggonaut demo content:

- Replace `content/projects/zaggonaut.md`.
- Remove or replace `content/blogs/html-intro.md`.
- Replace default images and metadata.
- Replace default footer quote behavior.
- Replace default social links.
- Replace default `Zaggonaut` copy everywhere visible.

No page should contain:

- “Zaggonaut” as site owner/title, except maybe in code comments or attribution if needed.
- demo HTML blog content.
- random quote text.
- placeholder Twitter links.
- default stock imagery unless intentionally retained and renamed.

## 18. Accessibility and quality requirements

The implementation must preserve the template’s quality standards:

- Responsive on mobile, tablet, desktop.
- Keyboard accessible navigation.
- Visible focus states.
- Good color contrast.
- Alt text for profile image and meaningful images.
- No broken links.
- No horizontal overflow on mobile.
- No console errors.
- SEO metadata updated.
- Lighthouse should remain strong.

## 19. Development commands

Use pnpm.

```bash
pnpm install
pnpm dev
pnpm build
pnpm preview
pnpm lint
pnpm format
```

If `pnpm lint` uses Biome with auto-write, review changes after running it.

## 20. Acceptance criteria

The implementation is complete when:

- The site builds successfully with `pnpm build`.
- Homepage shows Javier’s name, profile image, positioning, intro, and featured projects.
- Projects page lists Call Brad, Kontana, Atlaset, and optionally FinKratt.
- Each project has a detail page with non-placeholder content.
- Design is mostly neutral with only subtle blue/yellow profile image accents.
- Text is black or `#222222` on a white/default neutral background.
- Default Zaggonaut demo content is removed.
- Footer no longer shows random quotes.
- LinkedIn link points to Javier’s real profile.
- No broken navigation links.
- Mobile layout works cleanly.
- There are no obvious accessibility regressions.

## 21. Suggested implementation order for Windsurf

1. Install dependencies and run the template locally.
2. Update `content/configuration.toml` with Javier’s metadata, hero, menu, and social links.
3. Replace/remove demo project and blog content.
4. Add project Markdown files for Call Brad, Kontana, Atlaset, and optional FinKratt.
5. Add profile image and optional social/project assets to `public/`.
6. Modify `Hero.astro` for profile image accent treatment.
7. Update homepage layout to include intro, projects, and compact credibility/experience sections.
8. Remove or simplify blog/articles if no real notes are added.
9. Simplify footer and remove random quotes.
10. Adjust CSS variables and styling while keeping the site minimal.
11. Run `pnpm build` and fix any schema/type errors.
12. Run responsive and accessibility checks.
13. Final cleanup: remove placeholder links, stock images, default Zaggonaut content, and unused files.

## 22. Guardrails for the AI implementer

- Do not invent achievements, clients, metrics, or case studies.
- Do not overstate Kontana or Atlaset maturity.
- Do not turn the site into a sales page for only Call Brad.
- Do not make the whole site blue/yellow.
- Do not keep demo content.
- Do not add unnecessary animation libraries.
- Do not introduce a CMS unless explicitly requested.
- Do not switch from pnpm unless the template is intentionally refactored.
- Prefer simple content and clean layout over clever UI.

## 23. Final positioning summary

Use this as the north star:

```text
Javier Vergara works at the intersection of practical GDPR, privacy operations, startup systems, market research, and AI-enabled execution. The website should present him as a credible, practical founder/operator — not as a generic consultant, influencer, or traditional legal profile.
```
