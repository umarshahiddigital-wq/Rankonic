# Rankonic Digital Website

Next.js 14 website with 5 pages (Home, Services, About, Contact, Book a Call), a working contact-form API, SEO files and a draft privacy page.

## Why this stack
Next.js produces fast, search-friendly pages and includes a server route, which the contact form needs to send real email. Vercel hosts it, publishes from GitHub automatically and handles HTTPS. GitHub Pages cannot run the contact form.

## Where to edit things
| What | Where |
|---|---|
| Email, WhatsApp number, Calendly URL, menu | `content/site.js` |
| Page wording, headlines, CTA labels, page titles and descriptions | `app/page.js`, `app/services/page.js`, `app/about/page.js`, `app/contact/page.js`, `app/book-a-call/page.js` |
| Colors | `:root` at the top of `app/globals.css` |
| Founder photo | Replace `public/founder-placeholder.png` with your photo (portrait 4:5, e.g. 800x1000), same file name |
| Logo files | `public/logo-full.png`, `logo-mark.png`, `logo-wordmark.png` |
| Social share image | `public/og-image.png` (1200x630) |
| Browser icon | `app/icon.png`, `app/apple-icon.png` |

**About visual editing:** there is NO drag-and-drop visual editor in this project. Adding one needs an outside account (a CMS) and extra setup, and it was not configured. Edit the files above directly on GitHub in your browser: open a file, click the pencil icon, change only the text, click Commit. Vercel republishes in about a minute.

## Run it on your computer
1. Install Node.js (LTS) from nodejs.org.
2. In a terminal inside this folder run: `npm install`
3. Copy `.env.example` to `.env.local` and fill it in.
4. Run `npm run dev` and open http://localhost:3000
5. Before publishing, run `npm run build` to check for errors.

## Make the contact form send email
1. Create a free account at resend.com using umarshahid.digital@gmail.com.
2. Create an API key and put it in `RESEND_API_KEY`.
3. While testing, keep `CONTACT_FROM_EMAIL=Rankonic Digital <onboarding@resend.dev>` (Resend delivers this sender only to your own account email).
4. After you buy a domain, verify it in Resend (it gives DNS records to add) and change `CONTACT_FROM_EMAIL` to an address on it.
Until the key is set, the form shows an honest error and a fallback email link. It never fakes success.

## Deploy (no coding needed)
1. Create a GitHub account and a repository. Upload this project (not `node_modules` or `.env.local`).
2. Sign in at vercel.com with GitHub, click Add New, Project, choose the repository, Deploy.
3. In Vercel, Settings, Environment Variables: add the four values from `.env.example`, then redeploy.
4. Test the form on the preview address Vercel gives you.
5. Buy a domain. In Vercel, Settings, Domains, add it and copy the DNS records into your registrar. HTTPS is automatic.
6. Set `NEXT_PUBLIC_SITE_URL` to your real domain (e.g. `https://yourdomain.com`) and redeploy. This fixes canonical URLs, sitemap and structured data.
Costs: a domain (yearly) is unavoidable. Vercel, Resend and GitHub have free plans, but limits and prices change, so check their pricing pages.

## Calendly
Create a Calendly account, copy your link and paste it into `calendlyUrl` in `content/site.js`. Until then the Book a Call page shows an email/WhatsApp fallback and no empty iframe.

## Pre-launch checklist
- [ ] Contact form tested end to end; the email arrives at umarshahid.digital@gmail.com
- [ ] `NEXT_PUBLIC_SITE_URL` set to the real domain; view page source and confirm canonical links
- [ ] HTTPS padlock works on the live domain
- [ ] `/sitemap.xml` and `/robots.txt` open on the live site
- [ ] Founder photo replaced; Calendly URL added
- [ ] Privacy policy reviewed by a legal professional
- [ ] WhatsApp button opens a chat with +92 321 4357247
- [ ] Every page checked on your phone
- [ ] Site added to Google Search Console, sitemap submitted, home page indexing requested
- [ ] Lighthouse run in Chrome (F12, Lighthouse) and issues fixed

## Keyword map (starting themes, not verified search-volume data)
Home: guest posting and link building services. Services: SEO link-building services. About: Rankonic Digital / SEO agency partner. Contact: contact Rankonic Digital. Book a Call: SEO consultation.

## Not done or not verified
- Real email delivery was not tested (needs your Resend key). Validation, the honeypot and the "not configured" error path were tested.
- Rate limiting is in-memory, so it is best-effort on serverless hosting.
- No Lighthouse, accessibility-tool or screenshot testing was run. Pages were checked for HTTP 200, one H1 each, unique titles and canonicals, and a successful production build.
- The logo file has an opaque dark background. Transparent versions were made by keying out the dark color, so check the edges on your screen.
- Structured data was not run through Google's validator and uses the placeholder domain until you set the real URL. No ratings, reviews or address were added.
- Fonts are system fonts (no Google Fonts), for speed and privacy.
