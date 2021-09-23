# Tailwindcss JIT mode Setup

Tailwindcss is a utility-first CSS framework packed with classes that can be composed to build any design, directly in your markup.

For tailwindcss documentation, visit  [tailwindcss.com](https://tailwindcss.com/docs)

## Installation

Download ZIP file or clone the repository and follow this 2 steps

` npm install `

Run one of follwing script.

1. `npm run dev`
2. `npm run watch` - **Recommend while Developing**
3. `npm run production`

Now open `index.html` inside `public` folder and write some code

All setup is done

## Configuration

This setup also include all official plugins of tailwindcss.

#### tailwind.config.js

```
module.exports = {
  mode: 'jit',
  purge: [
    './public/**/*.html'
  ],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [
    require('@tailwindcss/typography'),
    require('@tailwindcss/forms'),
    require('@tailwindcss/line-clamp'),
    require('@tailwindcss/aspect-ratio'),
  ],
}
```
#### webpack.mix.js

You can also set custom folder path for css files at postCss second argument

```
const mix = require('laravel-mix');

mix.postCss('resources/css/app.css', 'public/assets/css', [
    require('tailwindcss')
]);

```

#### **resources/css/app.css**

If you want to add your custom class and want to use any directive like **@layer**, **@apply** etc., open **resources/css/app.css**
and apply.

````
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  h1 {
    @apply text-2xl;  
  }
  h2 {
    @apply text-xl;
  }
}

@layer components {
  .btn-blue {
    @apply bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded;
  }
}

@layer utilities {
  @variants hover, focus {
    .filter-none {
      filter: none;
    }
    .filter-grayscale {
      filter: grayscale(100%);
    }
  }
}

````
