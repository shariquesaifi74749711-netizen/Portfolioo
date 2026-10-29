# Sharique Saifi — Professional Portfolio Website

> **Aspiring Data Analyst**  
> *Turning Data Into Meaningful Insights*  
> **100% HTML5 & CSS3 • Zero JavaScript • Cinematic 3D Dark Theme**

---

## 1. Project Overview

This repository houses the personal, recruiter-facing portfolio website for **Sharique Saifi**, an aspiring Data Analyst based in Meerut, Uttar Pradesh, India. 

The website highlights a career transition rooted in a strong quantitative **B.Sc. in Mathematics** (2022) and **two years of professional administration and facility operations experience** at Fintech Services, now advancing through practical Data Analytics training at **Skill Stack Hub** covering **Excel, SQL, Power BI, Python, and Machine Learning**.

### Core Tenet: Complete Honesty & Transparency
- **No inflated titles:** Two years of experience are explicitly stated as **Facility Executive — Administration & Operations**, never as Data Analytics experience.
- **Authentic project labeling:** Projects are labeled **"In Progress"** or **"Planned"** with dual symbol and text badges.
- **Illustrative data disclosure:** All demonstration numbers (e.g., ₹12,50,000 revenue) are labeled prominently:  
  *“Illustrative demo data — not actual business results.”*
- **No fake metrics:** No fabricated proficiency percentages, fake certificates, or synthetic client testimonials.

---

## 2. Strict Technology Constraint

- **HTML5 only** for semantic structure, layout, and content.
- **CSS3 only** for typography, design system variables, responsive layouts, 3D perspective transforms, `@keyframes` background animations, and custom cursors.
- **Strictly Prohibited & Zero Inclusion:**
  - ❌ No JavaScript (`.js` files, `<script>` tags, or inline handlers like `onclick` / `onmouseover`).
  - ❌ No frontend frameworks (React, Vue, Angular, Svelte).
  - ❌ No CSS frameworks (Tailwind, Bootstrap).
  - ❌ No JS 3D / animation libraries (Three.js, GSAP, Vanta, particles.js, Tilt.js, VanillaTilt).
  - ❌ No WebGL, canvas, or external charting libraries.

---

## 3. Directory & File Structure

```text
portfolio/
│
├── index.html                  # Homepage (Hero, Stats, Skills overview, Featured projects)
├── about.html                  # Professional summary, 3 Core Pillars of career transition
├── projects.html               # All 20 Projects Hub categorized into 4 domains
├── excel-projects.html         # Category A: 5 Excel Projects + 3D preview frame
├── sql-projects.html           # Category B: 5 SQL Projects + Query console preview
├── python-ml-projects.html     # Category C: 5 Python/ML Projects + Model evaluation preview
├── powerbi-projects.html       # Category D: 5 Power BI Projects + Executive dashboard preview
├── experience.html             # Experience timeline (2 years Administration & Operations)
├── education.html              # Education timeline (B.Sc. Mathematics & Skill Stack Hub)
├── contact.html                # Contact links (Email, Phone, Verified Resume, Placeholders)
├── resume.pdf                  # Verified 1-page PDF Resume
├── README.md                   # Complete documentation & 3D Design Notes
│
├── css/
│   ├── style.css               # Design system tokens (:root), typography, header, footer
│   ├── effects-3d.css          # 3D hover/focus transforms, :has() tilt zones, cursor styling
│   ├── background-3d.css       # Cinematic 3D animated scene, stars, perspective grid, cubes
│   ├── projects.css            # Project cards, category hubs, 3D floating preview frames
│   └── responsive.css          # Breakpoints (mobile/tablet), reduced-motion, high contrast, print
│
├── assets/
│   └── icons/
│       ├── cursor-3d.svg         # Default 32x32 3D cyan/blue gradient arrow cursor
│       └── cursor-3d-pointer.svg # Pointer 32x32 3D glowing pointer cursor
│
└── projects/                   # 20 Static Project Case Study HTML Pages
    ├── excel-sales-performance.html
    ├── excel-chocolate-sales.html
    ├── excel-hotel-booking.html
    ├── excel-ecommerce-sales.html
    ├── excel-inventory-management.html
    ├── sql-sales-manager.html
    ├── sql-ecommerce-orders.html
    ├── sql-hotel-booking.html
    ├── sql-employee-hr.html
    ├── sql-customer-retention.html
    ├── ml-house-price.html
    ├── ml-customer-churn.html
    ├── ml-sales-forecasting.html
    ├── ml-customer-segmentation.html
    ├── ml-student-performance.html
    ├── powerbi-sales-revenue.html
    ├── powerbi-hotel-booking.html
    ├── powerbi-chocolate-bi.html
    ├── powerbi-ecommerce-insights.html
    └── powerbi-healthcare-analytics.html
```

---

## 4. 3D Design Notes & Technical Mechanics

### A. 3D Dark Theme Architecture
All visual depths, shadows, colors, and timings are controlled centrally in `css/style.css` via `:root` CSS custom properties:
- `--bg-dark: #050811;` and `--card-bg: rgba(13, 22, 42, 0.88);`
- Accents: `--accent: #00d2ff;` (Electric Blue) and `--accent-teal: #00f2fe;` (Teal)
- 3D Ease Curve: `--ease-3d: cubic-bezier(0.16, 1, 0.3, 1);`
- Layered Depth: `--depth-1`, `--depth-2`, `--depth-3`, `--depth-hover`

### B. Cursor-Reactive Depth via Pure CSS Hover Zones (`:has()`)
- **Constraint:** A cursor tracking object that smoothly follows the pointer across the screen requires JavaScript `mousemove` listeners, which are strictly prohibited.
- **Pure CSS Solution:**
  1. The hero card and project cards embed an invisible 3×3 grid of hover zones (nine `<span class="tilt-zone" aria-hidden="true">` elements).
  2. Pure CSS `:has()` rules detect which ninth of the card the mouse is hovering over (e.g., `.tilt-card-zones:has(.zone-tl:hover) .tilt-card-body`), applying tailored `rotateX()`, `rotateY()`, and `translateZ()` rotations with soft easing transitions.
  3. Interactive links and buttons sit at `z-index: 10`, ensuring they remain fully clickable above the zones.
  4. Graceful fallback: Browsers lacking `:has()` support smoothly fall back to a uniform vertical 3D lift via `@supports not selector(:has(*))`.

### C. 3D-Style Custom SVG Cursors
- Two faux-3D SVG files are defined in `assets/icons/`:
  - `cursor-3d.svg`: 32×32 px arrow with cyan/blue gradient, top-left highlight bevel, and drop shadow. Hotspot at `(4, 4)`.
  - `cursor-3d-pointer.svg`: 32×32 px pointer with teal gradient and edge illumination. Hotspot at `(6, 2)`.
- Applied via CSS:
  ```css
  @media (hover: hover) and (pointer: fine) {
    html { cursor: url("../assets/icons/cursor-3d.svg") 4 4, auto; }
    a, button, summary, [tabindex] { cursor: url("../assets/icons/cursor-3d-pointer.svg") 6 2, pointer; }
  }
  ```

### D. Cinematic 3D Movie Background Scene
The background is rendered entirely with HTML and CSS:
1. **Three-Layer Parallax Starfield:** Far, mid, and near stars drifting on independent `@keyframes` loops.
2. **Perspective Grid Floor:** A linear gradient grid tilted with `rotateX(66deg)` moving toward the viewer with background-position translation.
3. **Floating Wireframe Cubes:** 5 translucent CSS cubes constructed from 6 individual faces each (`transform-style: preserve-3d`), slowly tumbling near page margins.
4. **Cinematic Light Beam & Vignette:** A soft radial gradient light beam sweeping across the viewport with peripheral vignette and an inline SVG fractal noise data URI.

### E. Tuning or Disabling Effects
- **To adjust tilt angles:** Modify degrees in `css/effects-3d.css` (e.g., change `7deg` to `4deg`).
- **To adjust star speed:** Edit animation durations on `.scene-stars--far` (default 160s) in `css/background-3d.css`.
- **To add an optional looping video:** Place an MP4 file in `assets/video/scene-loop.mp4` and insert `<video autoplay muted loop playsinline preload="metadata">` inside `.scene`. The CSS fallback will automatically remain active underneath.

---

## 5. Accessibility & Responsive Support

- **Reduced Motion:** When a visitor enables `prefers-reduced-motion: reduce`, all `@keyframes` star animations, grid scrolling, cube rotations, 3D tilts, and sheen sweeps are disabled (`animation: none !important; transform: none !important;`), presenting a clean, static dark interface.
- **High Contrast:** When `prefers-contrast: more` is active, borders strengthen to 2px, backgrounds become solid, and background scene opacity is reduced to prioritize readability.
- **Mobile Devices (<768px):** Navigation switches to a responsive wrapped layout (no JS hamburger required), background cubes are reduced to preserve GPU cycles, and hover states do not stick on touch.
- **Print Styles:** `@media print` completely strips the 3D scene, header, and buttons, generating clean black-and-white readable output.
- **Screen Readers:** All decorative background scene elements and hover zones carry `aria-hidden="true"`. A visible skip-to-content link is provided as the first focusable element.

---

## 6. Personal Details Status & Checklist

| Field | Value / Status | Note |
|---|---|---|
| **Name** | Sharique Saifi | Confirmed |
| **Headline** | Aspiring Data Analyst | Confirmed |
| **Location** | Meerut, Uttar Pradesh, India | Confirmed |
| **Email** | `shariquesaifi74749711@gmail.com` | Active `mailto:` link |
| **Phone** | `+91 7464975011` | Active `tel:` link |
| **Education** | B.Sc. in Mathematics (CCS University, 2022) | Confirmed |
| **Training** | Skill Stack Hub (Data Analytics) | In progress |
| **Experience** | 2 Years — Facility Executive (Fintech Services) | Administration & Operations |
| **Employment Dates** | *To be confirmed by candidate* | Displayed as placeholder |
| **LinkedIn URL** | *Coming Soon* | Placeholder until real URL provided |
| **GitHub URL** | *Coming Soon* | Placeholder until real URL provided |
| **Resume PDF** | `resume.pdf` | Included & fully downloadable |

---

## 7. Local Setup & Static Deployment

### Running Locally
Because this project contains zero JavaScript and zero build steps:
1. Clone or download the folder.
2. Double-click `index.html` (or right-click and open with Chrome, Edge, Firefox, or Safari).
3. The site runs instantly without needing a local development server.

### Deploying to Static Hosting
The portfolio is 100% static and compatible with any static web host:

#### GitHub Pages
1. Push the repository to GitHub.
2. Go to **Settings > Pages**.
3. Under **Branch**, select `main` and root `/`.
4. Click **Save**. The website will be live in seconds.

#### Vercel
```bash
vercel deploy --prod
```

#### Netlify
Drag and drop the project folder directly into the Netlify dashboard.
