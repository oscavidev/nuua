# **nuua – The CSS Framework**

---

# **1. Goals of nuua**

* Unified, easily extendable design system for websites.
* Full control over appearance, naming and scaling.
* Independence from external frameworks like Tailwind.
* Clear structure: tokens → utilities → components.
* Themes realized through simple CSS variables.
* Fast, combinable layout and style building blocks.

---

# **2. Structure of nuua**

nuua is built in four layers:

1. **Design Tokens**
   Global CSS variables for colors, spacing, radius, typography, shadows and more.
   Themes override these variables.

2. **Utility Classes**
   Small, composable classes such as
   `xx-flex`, `xx-p-md`, `xx-bg-primary`, `xx-radius-lg`.

3. **Component Layer**
   Ready-to-use UI elements like buttons, cards, inputs and badges.

4. **Section Layer (later)**
   Hero sections, feature grids, pricing layouts and similar high-level blocks.

The entire system uses a customizable prefix such as `xx-`, `cx-` or `nu-`.

---

# **3. Files and Directory Structure**

Recommended layout:

```
nuua/
│
├── tokens.css        # Design tokens (CSS variables)
├── utilities.css     # Layout, spacing, color, radius, typography utilities
├── components.css    # Buttons, cards, inputs, badges
└── sections.css      # Future prebuilt section blocks
```

`tokens.css` must always load first.

---

# **4. Design Tokens (tokens.css)**

Design tokens define all fundamental stylistic values.

Example:

```css
:root {
  /* Background */
  --xx-color-bg: #050712;
  --xx-color-surface-1: #0b0f1f;
  --xx-color-surface-2: #11172a;

  /* Accents */
  --xx-color-primary: #8056ff;
  --xx-color-accent: #ffb347;
  --xx-color-danger: #ff4b6b;

  /* Text */
  --xx-color-text-primary: #f5f5ff;
  --xx-color-text-muted: #9aa0c2;

  /* Spacing */
  --xx-space-xs: 4px;
  --xx-space-sm: 8px;
  --xx-space-md: 12px;
  --xx-space-lg: 16px;
  --xx-space-xl: 24px;

  /* Radius */
  --xx-radius-sm: 4px;
  --xx-radius-md: 10px;
  --xx-radius-lg: 16px;
  --xx-radius-pill: 999px;

  /* Shadows */
  --xx-shadow-soft: 0 16px 40px rgba(0, 0, 0, 0.45);
  --xx-shadow-strong: 0 24px 60px rgba(0, 0, 0, 0.6);

  /* Typography */
  --xx-font-sans: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --xx-font-size-sm: 0.875rem;
  --xx-font-size-md: 1rem;
  --xx-font-size-lg: 1.25rem;
}
```

Themes simply override these values.

---

# **5. Utility Classes (utilities.css)**

Utilities are small building blocks for layout and styling.
All utilities rely entirely on the design tokens.

## **Layout**

```css
.xx-flex { display: flex; }
.xx-flex-col { flex-direction: column; }
.xx-flex-center { display: flex; align-items: center; justify-content: center; }

.xx-grid-2 { display: grid; grid-template-columns: repeat(2, 1fr); }
.xx-grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); }

.xx-container {
  width: 100%;
  max-width: 1120px;
  margin: 0 auto;
  padding-left: var(--xx-space-md);
  padding-right: var(--xx-space-md);
}
```

## **Spacing**

```css
.xx-p-sm { padding: var(--xx-space-sm); }
.xx-p-md { padding: var(--xx-space-md); }
.xx-p-lg { padding: var(--xx-space-lg); }

.xx-mb-sm { margin-bottom: var(--xx-space-sm); }
.xx-mb-md { margin-bottom: var(--xx-space-md); }
.xx-mb-lg { margin-bottom: var(--xx-space-lg); }

.xx-gap-sm { gap: var(--xx-space-sm); }
.xx-gap-md { gap: var(--xx-space-md); }
.xx-gap-lg { gap: var(--xx-space-lg); }
```

## **Colors**

```css
.xx-bg { background: var(--xx-color-bg); }
.xx-bg-surface-1 { background: var(--xx-color-surface-1); }
.xx-bg-surface-2 { background: var(--xx-color-surface-2); }

.xx-bg-primary { background: var(--xx-color-primary); }
.xx-bg-accent { background: var(--xx-color-accent); }

.xx-text-primary { color: var(--xx-color-text-primary); }
.xx-text-muted { color: var(--xx-color-text-muted); }
.xx-text-accent { color: var(--xx-color-accent); }
```

## **Radius and Shadow**

```css
.xx-radius-sm { border-radius: var(--xx-radius-sm); }
.xx-radius-md { border-radius: var(--xx-radius-md); }
.xx-radius-lg { border-radius: var(--xx-radius-lg); }
.xx-radius-pill { border-radius: var(--xx-radius-pill); }

.xx-shadow-soft { box-shadow: var(--xx-shadow-soft); }
.xx-shadow-strong { box-shadow: var(--xx-shadow-strong); }
```

## **Typography**

```css
.xx-text-sm { font-size: var(--xx-font-size-sm); }
.xx-text-md { font-size: var(--xx-font-size-md); }
.xx-text-lg { font-size: var(--xx-font-size-lg); }

.xx-font-semibold { font-weight: 600; }
.xx-uppercase { text-transform: uppercase; }
```

---

# **6. Components (components.css)**

Components are ready-built UI elements.

## **Buttons**

```css
.xx-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--xx-space-xs);
  padding: calc(var(--xx-space-sm) + 2px) var(--xx-space-lg);
  border-radius: var(--xx-radius-md);
  border: 1px solid transparent;
  font-family: var(--xx-font-sans);
  font-size: var(--xx-font-size-md);
  font-weight: 500;
  cursor: pointer;
  transition: background 0.15s, box-shadow 0.15s, transform 0.05s;
}

.xx-btn-primary {
  background: var(--xx-color-primary);
  color: var(--xx-color-text-primary);
  box-shadow: var(--xx-shadow-soft);
}

.xx-btn-ghost {
  background: transparent;
  color: var(--xx-color-text-primary);
  border-color: var(--xx-color-surface-2);
}

.xx-btn-primary:hover,
.xx-btn-ghost:hover {
  transform: translateY(-1px);
}
```

## **Cards**

```css
.xx-card {
  background: var(--xx-color-surface-1);
  border-radius: var(--xx-radius-lg);
  border: 1px solid var(--xx-color-surface-2);
  padding: var(--xx-space-lg);
  box-shadow: var(--xx-shadow-soft);
}

.xx-card-soft {
  background: var(--xx-color-surface-1);
  border-radius: var(--xx-radius-lg);
  padding: var(--xx-space-lg);
  box-shadow: none;
}
```

## **Inputs**

```css
.xx-input {
  width: 100%;
  padding: var(--xx-space-sm) var(--xx-space-md);
  border-radius: var(--xx-radius-md);
  border: 1px solid var(--xx-color-surface-2);
  background: var(--xx-color-surface-1);
  color: var(--xx-color-text-primary);
  font-family: var(--xx-font-sans);
}

.xx-input:focus {
  outline: none;
  border-color: var(--xx-color-primary);
  box-shadow: 0 0 0 1px var(--xx-color-primary);
}

.xx-input-error {
  border-color: var(--xx-color-danger);
}
```

## **Badges**

```css
.xx-badge {
  display: inline-flex;
  align-items: center;
  padding: 2px 8px;
  border-radius: var(--xx-radius-pill);
  font-size: var(--xx-font-size-sm);
  background: var(--xx-color-surface-2);
  color: var(--xx-color-text-muted);
}

.xx-badge-accent {
  background: var(--xx-color-accent);
  color: var(--xx-color-bg);
}
```

---

# **7. Demo Example**

```html
<div class="xx-bg">
  <div class="xx-container xx-p-lg">

    <button class="xx-btn xx-btn-primary xx-mb-md">
      Let’s go
    </button>

    <div class="xx-card xx-mb-lg">
      <h2 class="xx-text-lg xx-font-semibold xx-mb-sm">Title</h2>
      <p class="xx-text-muted xx-mb-md">Description text...</p>
      <input class="xx-input xx-mb-sm" placeholder="Email">
      <span class="xx-badge-accent">New</span>
    </div>

  </div>
</div>
```

---

# **8. Summary**

nuua consists of:

1. **tokens.css** – design tokens
2. **utilities.css** – utility classes
3. **components.css** – buttons, cards, inputs, badges
4. **sections.css** – future high-level web sections

nuua forms the core foundation for all upcoming website projects.

---
