# `aura-css-animations`

[![npm version](https://badge.fury.io/js/%40aura-cs-animations.svg)](https://www.npmjs.com/package/aura-css-animations)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**`aura-css-animations`** is a lightweight, pure CSS NPM package designed to bring dynamic, vibrant, and advanced animations to your web projects without any JavaScript dependencies. It offers granular control over animation properties through a utility-first approach and provides ready-to-use presets for common effects.

## 🌟 Why `aura-css-animations`?

Many animation libraries are heavy, require JavaScript, or limit your creative freedom. `aura-css-animations` fills this gap by:

* **Pure CSS:** All animations are powered by `@keyframes` and CSS properties, ensuring maximum performance and compatibility.
* **Zero JavaScript Dependencies:** No runtime JS overhead. Integrate seamlessly with any frontend framework or vanilla HTML/CSS.
* **Utility-First:** Apply precise animation properties directly in your HTML using single-purpose classes (e.g., `aura-css-duration-fast`, `aura-css-ease-bounce`).
* **Highly Customizable:** Leverage CSS Custom Properties (variables) to easily adjust durations, delays, easing, and more, enabling dynamic runtime theming.
* **Vibrant & Advanced:** A rich collection of modern keyframe animations, from subtle fades to complex, multi-step effects like wobbles, flips, and light speed.
* **Accessibility Conscious:** Provides utilities and guidance to respect users' `prefers-reduced-motion` settings.

## ✨ Features

* **Extensive Keyframes:** A wide array of pre-defined animation sequences (fade, slide, zoom, rotate, bounce, shake, pulse, spin, text reveal, gradient shifts, wobble, flip, jello, rubber band, light speed, hinge, background noise).
* **Granular Utility Classes:** Control `animation-name`, `animation-duration`, `animation-delay`, `animation-timing-function`, `animation-fill-mode`, `animation-iteration-count`, `animation-direction`, and `animation-play-state`.
* **CSS Variable Driven:** Customize animation properties globally or locally by overriding CSS variables.
* **Pre-composed Presets:** Quick-start classes for common animation patterns (e.g., `aura-css-button-hover-pulse`, `aura-css-card-entrance`, `aura-css-text-typing`).
* **Accessibility Utilities:** Classes to easily manage animations for users with motion sensitivities.

## 🌐 Browser Compatibility

`aura-css-animations` is designed for **modern evergreen browsers**, including:

* Google Chrome (latest versions)
* Mozilla Firefox (latest versions)
* Apple Safari (latest versions)
* Microsoft Edge (latest versions)

The CSS features used (CSS Animations, Transforms, Transitions, CSS Custom Properties, `@media (prefers-reduced-motion)`) are widely supported in these environments.

**Important Note on Older Browsers:**
While `autoprefixer` is included in the recommended build setup to add necessary vendor prefixes, full compatibility with very old browsers like Internet Explorer 11 (IE11) is **not guaranteed** due to their limited or absent support for modern CSS features such as CSS Custom Properties. For projects requiring extensive support for legacy browsers, additional polyfills or alternative approaches may be necessary, which are outside the scope of this pure CSS animation package.

## 🚀 Installation

```bash
npm install aura-css-animations postcss postcss-cli autoprefixer cssnano
# Or using yarn:
# yarn add aura-css-animations postcss postcss-cli autoprefixer cssnano
```

### Build Setup

`aura-css-animations` uses PostCSS to compile its CSS from source and to allow for future purging/optimization.

1.  **Create `postcss.config.js`** in your project's root (if you don't have one):
    ```javascript
    // postcss.config.js
    module.exports = {
      plugins: [
        require('autoprefixer'), // Add vendor prefixes for broader compatibility
        require('cssnano')({    // Minify CSS for production bundles
          preset: 'default',
        }),
        // Add other PostCSS plugins here, e.g., PurgeCSS for unused CSS removal
      ],
    };
    ```
2.  **Add build script to your `package.json`**:
    ```json
    {
      "scripts": {
        "build:css": "postcss path/to/your/main.css --dir path/to/your/output --config postcss.config.js",
        "watch:css": "postcss path/to/your/main.css --dir path/to/your/output --watch --config postcss.config.js"
      }
    }
    ```
    *Replace `path/to/your/main.css` with the path to your project's main CSS file where you `@import` `aura-css-animations`.*
    *Replace `path/to/your/output` with your desired output directory (e.g., `public/css`).*

## 📚 Usage

### 1. Import into your project's main CSS file

In your primary CSS file (e.g., `src/styles.css` in a React/Next.js app, or `css/main.css` in a static site):

```css
/* src/styles.css or css/main.css */

/* Import Aura CSS Animations Core */
@import 'aura-css-animations/dist/index.css';

/* Your other custom CSS */
body {
  font-family: sans-serif;
  margin: 0;
  padding: 20px;
  background-color: #f0f0f0;
}

.my-element {
  background-color: #3498db;
  color: white;
  padding: 20px;
  margin: 20px;
  border-radius: 8px;
  text-align: center;
}
```

### 2. Apply Utility Classes in your HTML/JSX

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aura CSS Animations Demo</title>
    <link rel="stylesheet" href="path/to/your/compiled/main.css">
    <style>
        /* Example of overriding a variable for a specific element */
        .my-custom-duration {
            --aura-css-duration-normal: 2s; /* Make normal animations slower for this element */
        }
    </style>
</head>
<body>

    <h1 class="my-element aura-css aura-css-fade-in aura-css-duration-slowest aura-css-delay-300">
        Welcome to Aura CSS Animations!
    </h1>

    <div class="my-element aura-css aura-css-slide-in-up aura-css-ease-bounce aura-css-delay-500">
        This element slides in with a bounce effect.
    </div>

    <button class="my-element aura-css-button-hover-pulse">
        Hover Me!
    </button>

    <p class="my-element aura-css-text-typing aura-css-fill-forwards aura-css-delay-1000">
        This text will type itself out.
    </p>

    <div class="my-element aura-css-background-gradient-loop" style="height: 100px;">
        Animated Background
    </div>

    <img src="[https://placehold.co/100x100/aabbcc/ffffff?text=Logo](https://placehold.co/100x100/aabbcc/ffffff?text=Logo)" alt="Logo"
         class="aura-css aura-css-spin-on-load aura-css-duration-long aura-css-ease-linear">

    <div class="my-element aura-css-wobble-hover">
        Wobble on Hover
    </div>

    <div class="my-element aura-css aura-css-light-speed-in aura-css-delay-700">
        Light Speed Entrance
    </div>

    <!-- Accessibility Example: This element's animation will be reduced if user prefers -->
    <div class="my-element aura-css aura-css-bounce aura-css-reduce-motion">
        Reduced Motion Example
    </div>

</body>
</html>
```

### 3. Customization with CSS Variables

You can override any of the CSS variables defined in `src/_variables.css` to customize the animations.

```css
/* In your custom CSS file, after importing aura-css-animations */

/* Change default animation duration globally */
:root {
  --aura-css-duration-normal: 400ms;
  --aura-css-ease-bounce: cubic-bezier(0.1, 0.9, 0.2, 1.1); /* Softer bounce */
}

/* Or for a specific element/component */
.my-custom-animated-element {
  --aura-css-duration-normal: 1.5s; /* Longer duration for this specific element */
  --aura-css-delay-100: 0.5s; /* Longer delay for this specific element */
}
```

### 4. Dynamic Control (with minimal JS)

Since `aura-css-animations` is pure CSS, dynamic control (e.g., playing an animation on click, or when an element enters the viewport) is handled by adding/removing classes using JavaScript.

```javascript
// Example: Play bounce animation on click
document.getElementById('myButton').addEventListener('click', function() {
  this.classList.remove('aura-css-bounce'); // Remove to allow re-triggering
  void this.offsetWidth; // Trigger reflow
  this.classList.add('aura-css-bounce'); // Add to play animation
});
```

### 5. Accessibility (`prefers-reduced-motion`)

The package includes base styles that respect `prefers-reduced-motion`. For elements where you want to explicitly ensure animations are removed or simplified for users with this preference, apply the `aura-css-reduce-motion` class.

```html
<div class="aura-css aura-css-bounce aura-css-reduce-motion">
  This animation respects user's motion preference.
</div>
```

## 🤝 Contributing

Contributions are welcome! If you'd like to contribute, please follow these steps:

1.  Fork the repository.
2.  Clone your forked repository: `git clone git@github.com:rajasekar-arch/aura-css-animations.git`
3.  Install dependencies: `npm install`
4.  Build the project: `npm run build`
5.  Run tests: `npm test` (if tests are added in the future)
6.  Create a new branch for your feature or bug fix.
7.  Make your changes, ensuring they adhere to the coding standards and include tests/examples.
8.  Commit your changes and push to your fork.
9.  Open a pull request to the main repository.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE] file for details.