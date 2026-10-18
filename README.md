# Portfolio Website Template

> A modern, animated portfolio template for developers and creatives.

Built with **Next.js 16**, **React 19**, **TypeScript**, **Tailwind CSS 4**, and
**Framer Motion**. The template is data-driven, so most of the work needed to
make it your own happens in one file.

**Created by [Sabin Paudel](https://sabinpaudel.com.np)** ·
[Visit the original website](https://sabinpaudel.com.np)

## What is included

- Responsive home, about, projects, and contact pages
- Animated UI with Framer Motion
- Dark theme with lamp-mode toggle
- Hero, principles, featured work, about, and contact sections
- Project cards with live-demo and GitHub links
- Semantic HTML and Schema.org structured data
- Per-page metadata and Open Graph images
- Automatically generated `sitemap.xml` and `robots.txt`
- Optional Umami analytics and Google Search Console verification
- No database or API key required

## Tech stack

| Category | Technology |
| --- | --- |
| Framework | Next.js 16 with App Router |
| UI | React 19 |
| Language | TypeScript |
| Styling | Tailwind CSS 4 |
| Animation | Framer Motion |
| Icons | Lucide React |
| Effects | canvas-confetti |
| Linting | ESLint 9 |

## Pages

| Route | Content |
| --- | --- |
| `/` | Hero, principles, and featured projects |
| `/about` | Introduction, experience, education, and skills |
| `/projects` | All projects |
| `/contact` | Contact details, social links, and availability |

## Quick start

### Requirements

- Node.js 20 or newer
- npm, pnpm, yarn, or Bun

### Install and run locally

```bash
git clone <your-repository-url> my-portfolio
cd my-portfolio
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

The `.env.local` file is optional for local development. To enable optional
services, copy the example file first:

```bash
cp .env.local.example .env.local
```

## Make it your own

### 1. Edit the portfolio configuration first

Open [`app/lib/config/portfolio.ts`](./app/lib/config/portfolio.ts). This is
the single source of truth for the portfolio content.

Update these sections:

| Section | Change |
| --- | --- |
| `url` | Your production URL, including `https://` |
| `profile` | Your name, role, tagline, location, and availability |
| `geo` | Your city, country, timezone, flag, and coordinates |
| `images` | Paths to your hero, about, contact, and fallback images |
| `seo` | Page title, description, keywords, social profile URLs, and verification token |
| `contact` | Email address, phone number, and phone visibility |
| `socials` | Social links, icon names, and tooltips |
| `hero` | Hero label, heading, and call-to-action buttons |
| `heroStats` | The three statistics shown on the home page |
| `principles` | Your working principles |
| `home` | Home page section headings, descriptions, and buttons |
| `status` | The status message shown in the site chrome |
| `navigation` | Navigation labels and links |
| `footer` | Footer copy, links, sharing title, and copyright name |
| `projects` | Project details, screenshots, tags, and links |
| `projectsPage` | Projects page heading, copy, and labels |
| `aboutPage` | About page copy, experience, education, and skills |
| `contactPage` | Contact page heading and supporting copy |

You should not need to edit each page separately. The pages, layouts, SEO
metadata, structured data, sitemap, robots file, and generated Open Graph
images read from this configuration.

### 2. Replace the images

Replace the placeholder files with your own images. Keeping the same filenames
means no configuration changes are needed:

| File | Used for |
| --- | --- |
| `public/heroimage.png` | Home page hero image |
| `public/about.png` | About page profile image |
| `public/imagecp.png` | Contact page image |
| `public/picofme.png` | SEO and metadata fallback image |
| `public/projects/*.png` | Project screenshots |

If you use different filenames, update the paths in `portfolio.images` and in
each project’s `image` field. Project screenshots look best in a 16:10 ratio.

### 3. Update your projects

Add, remove, or edit entries in `portfolio.projects`. Each project supports:

```ts
{
  id: "5",
  title: "My Project",
  description: "A short description for project cards.",
  longDescription: "A longer description for the project detail content.",
  role: "Design and frontend development",
  image: "/projects/my-project.png",
  tags: ["Next.js", "TypeScript"],
  liveUrl: "https://example.com",
  githubUrl: "https://github.com/your-name/my-project",
  featured: true,
}
```

Set `githubUrl` to `null` when a project does not have a public repository.
Set `featured` to `true` to show a project on the home page.

### 4. Use the icon registry for icons

Icon values in `portfolio.ts` are strings, such as `"Github"`,
`"ArrowRight"`, or `"Briefcase"`. Available icons are registered in
[`app/lib/icons.tsx`](./app/lib/icons.tsx). If you use an icon that is not
already registered, add it there before running the build.

### 5. Update branding

| What to change | File |
| --- | --- |
| Favicon | `app/icon.svg` |
| Apple touch icon | `app/apple-icon.png` |
| Brand colors and visual theme | `app/globals.css` |
| Package name | `package.json` |

## Environment variables

Copy `.env.local.example` to `.env.local` when you want to enable either
optional integration:

```env
# Optional: Umami website ID
UMAMI_ID=

# Optional: Google Search Console verification token
GOOGLE_VERIFICATION=
```

Leave either value empty to disable that integration. Never commit
`.env.local` or secret values to Git.

## SEO checklist

Before deploying:

1. Set `url` to your real production domain.
2. Replace the default title, description, keywords, and social URLs in `seo`.
3. Check that every image path points to a file inside `public/`.
4. Add your Google Search Console token to `.env.local`, if needed.
5. Run a production build locally.
6. After deployment, verify:
   - `https://your-domain.com/sitemap.xml`
   - `https://your-domain.com/robots.txt`
   - Page titles, descriptions, and social previews

The `url` value is used for canonical URLs, metadata, structured data,
Open Graph URLs, the sitemap, and robots configuration.

## Available commands

```bash
npm run dev      # Start the development server
npm run build    # Create an optimized production build
npm run start    # Start the production server
npm run lint     # Run ESLint
```

Run the checks before deployment:

```bash
npm run lint
npm run build
```

## Project structure

```text
app/
├── (pages)/                   # About, projects, and contact routes
├── components/
│   ├── animations/            # Motion wrappers
│   ├── layout/                # Navigation, footer, and global effects
│   ├── sections/              # Home page sections
│   └── ui/                    # Reusable UI components
├── lib/
│   ├── config/portfolio.ts    # Edit this first: all portfolio data
│   ├── icons.tsx              # Icon name to Lucide component registry
│   ├── seo.ts                 # Metadata and structured-data helpers
│   └── ...                    # Hooks and utility helpers
├── globals.css                # Tailwind theme and custom styles
├── layout.tsx                 # Global metadata and application shell
├── opengraph-image.tsx        # Home page Open Graph image
├── robots.ts                  # robots.txt generator
└── sitemap.ts                 # sitemap.xml generator
public/
├── projects/                  # Project screenshots
└── *.png                      # Portfolio images
```

## Deployment

This is a standard Next.js application and can be deployed to Vercel or any
Node.js-compatible host.

### Vercel

1. Push your customized project to GitHub.
2. Import the repository into [Vercel](https://vercel.com).
3. Add `UMAMI_ID` and `GOOGLE_VERIFICATION` under project environment
   variables, if you use them.
4. Deploy with the default build command: `npm run build`.
5. Add your custom domain and update `portfolio.url` to match it.

For another Node.js host, install dependencies, run `npm run build`, and serve
the result with `npm run start`.

## License

No license file is included. Add a `LICENSE` file before redistributing or
using this template in a project with specific licensing requirements.

## Credits

Template created by **[Sabin Paudel](https://sabinpaudel.com.np)**.

If this template helps you build your portfolio, consider visiting the
[original website](https://sabinpaudel.com.np).
