
# CI PAOS Website – RDMC Workshop 2026

This repository contains a small static website for the **2026 NSF Workshop on Research Data Management in Construction Engineering: Challenges and Opportunities** at Michigan Technological University.

It is a simple, no-build, front‑end project: just HTML, CSS, and JavaScript. You can open it directly in a browser or serve it with any static web server.

---

## 1. Project Structure

The core files are:

- `index.html` – main page markup (all content sections, navigation, and layout).
- `style.css` – global styles, layout, responsive behavior, and visual design.
- `script.js` – page interactivity (smooth scrolling and registration button behavior).

In addition, the page expects the following image assets in the same directory (or an `assets/` folder, if you choose to reorganize):

- `nsf.png`
- `mtu.png`
- `mtu-icc.png`
- `MTTI-logo.png`
- `mtu-mub.jpg`
- `mub-highlight.png`
- `hampton.avif`
- `hancock airport.png`
- `enterprise_logo.webp`
- `woodland_preschoo.avif`
- `bhk-childdevelopment.jpg`
- `little_husky.jpg`
- `parking_map.png`
- `isle_national_park.jpg`
- `nara_nature.jpg`
- `north_canal.jpg`

> **Note:** If you change any file or folder names, be sure to update the corresponding `src` attributes in `index.html` and any paths in CSS.

---

## 2. Requirements

You do **not** need Node.js, npm, or any build tools to run this project.

Minimum requirements:

- A modern web browser (Chrome, Firefox, Edge, Safari).
- A text editor (VS Code, Sublime, Notepad++, etc.) if you want to modify the code.
- (Optional but recommended) A simple static HTTP server for local development, such as:
  - VS Code extension: **Live Server**
  - Python’s built-in HTTP server
  - `http-server` from npm, or any similar tool

---

## 3. Getting Started (Clone / Download)

1. **Download or clone** this project into a folder on your computer, e.g.:

   ```bash
   git clone <your-repo-url> ci-paos-website
   cd ci-paos-website
   ```

   Or, if you just have a ZIP:
   - Download the ZIP
   - Extract it
   - Open the extracted folder

2. Make sure the files are arranged like this (one possible layout):

   ```text
   ci-paos-website/
   ├── index.html
   ├── style.css
   ├── script.js
   ├── nsf.png
   ├── mtu.png
   ├── mtu-icc.png
   ├── MTTI-logo.png
   ├── mtu-mub.jpg
   ├── mub-highlight.png
   ├── hampton.avif
   ├── hancock airport.png
   ├── enterprise_logo.webp
   ├── woodland_preschoo.avif
   ├── bhk-childdevelopment.jpg
   ├── little_husky.jpg
   ├── parking_map.png
   ├── isle_national_park.jpg
   ├── nara_nature.jpg
   └── north_canal.jpg
   ```

   You can also move the images into an `img/` or `assets/` directory, as long as you update all paths in `index.html`.

---

## 4. Running the Site Locally

### Option A – Open `index.html` directly

1. Navigate to the project folder.
2. Double-click `index.html` to open it in your default browser.

This is enough for a quick local preview since the project is static.

### Option B – Use a local HTTP server (recommended)

Using a local server makes paths and browser behavior closer to a real deployment.

#### Using Python (no extra installs if Python is already on your machine)

From the project folder:

```bash
# For Python 3
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

in your browser.

#### Using VS Code Live Server

1. Open the folder in VS Code.
2. Install the **Live Server** extension (if not already installed).
3. Right-click `index.html` → **Open with Live Server**.

---

## 5. Code Overview

### 5.1 `index.html`

Responsible for:

- The sticky header navigation with anchor links to sections like:
  - About
  - Application
  - Dates
  - Program
  - Venue
  - Lodging
  - Childcare
  - Places
  - Committee
  - Disclosure
- The hero section with workshop title, date, and sponsor logos.
- All content sections:
  - About the Workshop
  - Application & registration button
  - Important Dates (cards)
  - Program (Day 1 & Day 2 agendas)
  - Venue details and campus map link
  - Lodging & Transportation cards
  - Childcare & Family Care resources
  - Parking information and map
  - Places to Visit Nearby
  - Organization Committee & Coordinators
  - Disclosure and Code of Conduct (collapsible `<details>` sections)
- Footer with contact information.

The HTML links to the stylesheet and script like this:

```html
<link rel="stylesheet" href="style.css" />
<script src="script.js"></script>
```

If you change file names or move them to subfolders, update these paths accordingly.

---

### 5.2 `style.css`

Responsible for:

- Base reset (margin, padding, box-sizing).
- Typography and color theme (yellow/black/white palette).
- Sticky header and centered navigation.
- Hero banner and logo styles.
- Section layout with card-like appearance and drop shadows.
- Important Dates cards in a responsive flex grid.
- Agenda tables styling (headers, alternating rows, hover states).
- Venue layout with side-by-side images.
- Lodging/transportation, childcare, and places-to-visit cards (3-column grids on desktop, stacked on mobile).
- Parking map image styling.
- Disclosure section with expandable boxes using `<details>` and custom summary styling.
- Fixed bottom footer and additional body padding to avoid overlap.
- Responsive breakpoints at 900px and 480px to ensure usability on tablets and phones.

If you move or rename the CSS file, ensure the `<link>` in `index.html` points to the correct path.

---

### 5.3 `script.js`

Provides two main behaviors:

1. **Smooth Scroll Navigation**

   All anchor links that start with `#` are wired to scroll smoothly to their target sections:

   ```js
   document.querySelectorAll('a[href^="#"]').forEach(anchor => {
     anchor.addEventListener("click", function(e) {
       e.preventDefault();
       document.querySelector(this.getAttribute("href")).scrollIntoView({
         behavior: "smooth"
       });
     });
   });
   ```

2. **Registration Button Alert**

   The *“Notify Me When Registration Opens”* button (with class `.register-btn`) shows an alert when clicked:

   ```js
   document.querySelector(".register-btn").addEventListener("click", () => {
     alert("Registration will open soon! Stay tuned.");
   });
   ```

   You can replace this with a real registration form, a link to an external portal, or an email subscription mechanism.

---

## 6. Customization

Here are common customization points if someone wants to adapt the page:

- **Workshop title, date, and location:**  
  Edit the hero `<h1>` and date/place `<p>` in `index.html`.

- **Navigation items / section names:**  
  Update the `<nav>` links and corresponding section `id` attributes.

- **Program and important dates:**  
  Edit the **Important Dates** cards and **Agenda** tables directly in `index.html`.

- **Logos and images:**  
  Replace any image files while keeping the same file names, or update the `src` attributes where needed.

- **Colors and fonts:**  
  Adjust in `style.css`, especially:
  - Background (`body`, `header`, `.hero`, etc.)
  - Primary accent color (`#ffcd00`)
  - Font family (currently `"Poppins", sans-serif`)

- **Registration button behavior:**  
  Modify the `.register-btn` event listener in `script.js`. For example, redirect to a form:

  ```js
  document.querySelector(".register-btn").addEventListener("click", () => {
    window.location.href = "https://example.com/your-registration-form";
  });
  ```

---

## 7. Deployment

Because this is a static site, you can deploy it easily to:

- GitHub Pages
- GitLab Pages
- Netlify
- Vercel
- Any standard web server / hosting provider

Basic deployment steps are typically:

1. Push your code to a Git repository.
2. Connect the repository to your hosting platform.
3. Configure the root directory (usually the project root with `index.html`).
4. Deploy / publish.

Refer to your hosting provider’s documentation for exact steps.

---

## 8. License & Acknowledgements

- **Content ownership:** The workshop details, logos, and institutional information belong to their respective owners (e.g., Michigan Technological University, NSF, ICC, MTTI).
- **Code:** Unless otherwise specified in the repository, treat this as internal workshop website code. You can add a specific open-source license (e.g., MIT, BSD) if you publish it publicly.

If you share or fork this site, please update the contact information and attribution as needed.

---

## 9. Contact

For questions about the workshop website or configuration, refer to the contact details in the footer of `index.html` (e.g., organizing committee email/phone), or update them to your own contact points if you are reusing the template.
