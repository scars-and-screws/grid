# 📐 CSS Grid Layout - Complete Guide

> A comprehensive CSS Grid tutorial repository with practical examples and visual demonstrations.

---

## 📋 Table of Contents

- [What is CSS Grid?](#-what-is-css-grid)
- [When to Use CSS Grid](#-when-to-use-css-grid)
- [Grid Container Properties](#-grid-container-properties)
- [Grid Item Properties](#-grid-item-properties)
- [Code Examples in This Repository](#-code-examples-in-this-repository)
- [Quick Reference](#-quick-reference)

---

## 🎯 What is CSS Grid?

CSS Grid Layout is a **two-dimensional layout system** designed specifically for the web. It lets you work with both **rows and columns** simultaneously, making it perfect for creating complex, responsive layouts.

```
┌─────────────────────────────────────────────┐
│              CSS GRID LAYOUT                │
├─────────────┬─────────────┬─────────────────┤
│   Column 1  │   Column 2  │    Column 3     │
├─────────────┼─────────────┼─────────────────┤
│   Row 1     │             │                 │
├─────────────┼─────────────┼─────────────────┤
│   Row 2     │             │                 │
└─────────────┴─────────────┴─────────────────┘
```

### ✨ Key Benefits

| Feature | Description |
|---------|-------------|
| 📦 **Two-dimensional** | Control both rows AND columns at the same time |
| 🎨 **Clean HTML** | No wrapper divs needed for layout |
| 📱 **Responsive** | Easy to create responsive layouts |
| 🎯 **Precise control** | Place items exactly where you want them |
| 🔧 **Flexible sizing** | Use `fr` units for proportional sizing |

---

## 🤔 When to Use CSS Grid

### ✅ Use CSS Grid When:

| Scenario | Example |
|----------|---------|
| 🏗️ **Page layouts** | Header, sidebar, content, footer |
| 📊 **Dashboard layouts** | Cards, widgets, data panels |
| 🖼️ **Image galleries** | Photo grids, portfolios |
| 📋 **Form layouts** | Complex multi-column forms |
| 🎪 **Overlapping content** | Items that need to overlap |

### ❌ Avoid CSS Grid When:

| Scenario | Better Alternative |
|----------|-------------------|
| 📏 Single row/column | Use **Flexbox** |
| 📝 Text content flow | Use **normal flow** |
| 🔄 Unknown number of items | Consider **Flexbox** |

### 🔄 Grid vs Flexbox

```
┌────────────────────────┬────────────────────────┐
│      CSS GRID 📐       │     FLEXBOX 📏         │
├────────────────────────┼────────────────────────┤
│  Two-dimensional       │  One-dimensional       │
│  Layout-first          │  Content-first         │
│  Explicit placement    │  Content distribution  │
│  Complex layouts       │  Simple alignment      │
└────────────────────────┴────────────────────────┘
```

---

## 🏠 Grid Container Properties

To create a grid, set `display: grid` on the parent container.

### 📌 `display: grid`

```css
.container {
    display: grid;
}
```

This transforms the element into a grid container, and its direct children become grid items.

---

### 📊 `grid-template-columns`

Defines the number and size of columns.

```css
/* Fixed pixel values */
grid-template-columns: 200px 200px 200px;

/* Fractional units (fr) - proportional */
grid-template-columns: 1fr 1fr 2fr;

/* Mixed values */
grid-template-columns: 200px 1fr 2fr;

/* repeat() function */
grid-template-columns: repeat(3, 1fr);
```

#### Visual Example:
```
grid-template-columns: 1fr 1fr 2fr;

┌──────────┬──────────┬────────────────────┐
│    1fr   │    1fr   │        2fr         │
│   (25%)  │   (25%)  │       (50%)        │
└──────────┴──────────┴────────────────────┘
```

---

### 📊 `grid-template-rows`

Defines the number and size of rows.

```css
/* Fixed pixel values */
grid-template-rows: 150px 100px 100px;

/* Auto-sizing */
grid-template-rows: auto 1fr auto;

/* Mixed - used in basic.css for page layout */
grid-template-rows: 120px 60px 100px 400px 50px;
```

#### Visual Example:
```
grid-template-rows: 150px 100px 100px;

┌──────────────────────────────────┐
│           150px (Row 1)          │
├──────────────────────────────────┤
│           100px (Row 2)          │
├──────────────────────────────────┤
│           100px (Row 3)          │
└──────────────────────────────────┘
```

---

### 📏 `grid-gap` / `gap`

Controls spacing between grid cells.

```css
/* Uniform gap */
grid-gap: 20px;

/* Different row and column gaps */
grid-gap: 20px 10px; /* row-gap column-gap */

/* Individual properties */
grid-row-gap: 15px;
grid-column-gap: 10px;
```

#### Visual Example:
```
grid-gap: 20px 10px;

┌─────────┐10px┌─────────┐10px┌─────────┐
│ Item 1  │    │ Item 2  │    │ Item 3  │
└─────────┘    └─────────┘    └─────────┘
    20px          20px           20px
┌─────────┐    ┌─────────┐    ┌─────────┐
│ Item 4  │    │ Item 5  │    │ Item 6  │
└─────────┘    └─────────┘    └─────────┘
```

---

### 🗺️ `grid-template-areas`

Creates a visual map of your layout using named areas.

```css
.container {
    grid-template-areas:
        "header header header"
        "menu menu menu"
        "box1 box2 sidebar"
        "content content sidebar"
        "footer footer footer";
}
```

#### Visual Representation:
```
┌─────────────────────────────────────────┐
│               📌 HEADER                 │
├─────────────────────────────────────────┤
│               🍔 MENU                   │
├───────────┬───────────┬─────────────────┤
│  📦 BOX1  │  📦 BOX2  │                 │
├───────────┴───────────┤   📋 SIDEBAR    │
│      📄 CONTENT       │                 │
├───────────────────────┴─────────────────┤
│               🦶 FOOTER                 │
└─────────────────────────────────────────┘
```

---

## 📍 Grid Item Properties

Properties applied to grid items (children of the grid container).

### 🔢 `grid-row` & `grid-column`

Position items using line numbers.

```css
/* Full syntax */
grid-row-start: 2;
grid-row-end: 3;
grid-column-start: 1;
grid-column-end: 3;

/* Shorthand */
grid-row: 2 / 3;     /* start / end */
grid-column: 1 / 3;   /* start / end */
```

#### Visual Example:
```
Grid Lines:    1         2         3         4
               │         │         │         │
           ┌───┴─────────┴─────────┴─────────┴───┐
Row 1    1─┤ Cell(1,1) │ Cell(1,2) │ Cell(1,3)  │
           ├───────────┼───────────┼────────────┤
Row 2    2─┤ Cell(2,1) │ Cell(2,2) │ Cell(2,3)  │
           ├───────────┼───────────┼────────────┤
Row 3    3─┤ Cell(3,1) │ Cell(3,2) │ Cell(3,3)  │
           └───────────┴───────────┴────────────┘
         4─

grid-column: 2/4; = spans from line 2 to line 4
```

---

### 🎯 `grid-area`

Assigns an item to a named grid area OR positions using line numbers.

```css
/* Using named areas */
.header {
    grid-area: header;
}

/* Using line numbers (shorthand) */
/* grid-area: row-start / column-start / row-end / column-end */
.item {
    grid-area: 2 / 3 / 3 / 4;
}
```

---

### 📐 Spanning Multiple Cells

```css
/* Span 2 columns */
grid-column: 1 / 3;
/* OR */
grid-column: span 2;

/* Span 2 rows */
grid-row: 1 / 3;
/* OR */
grid-row: span 2;
```

#### Visual Example:
```
grid-column: 2/4; (spans columns 2-3)

┌───────────┬───────────────────────────┐
│  Item 1   │        Item 2             │ ← spans 2 columns
├───────────┼───────────┬───────────────┤
│  Item 3   │  Item 4   │    Item 5     │
└───────────┴───────────┴───────────────┘
```

---

## 📂 Code Examples in This Repository

This repository contains two practical examples demonstrating CSS Grid concepts:

---

### 📄 Example 1: Basic Grid (`index.html` + `style.css`)

A simple 6-item grid demonstrating core grid concepts.

#### HTML Structure:
```html
<div class="container">
    <div class="items items1">First</div>
    <div class="items items2">Second</div>
    <div class="items items3">Third</div>
    <div class="items items4">Fourth</div>
    <div class="items items5">Fifth</div>
    <div class="items items6">Sixth</div>
</div>
```

#### Key CSS Properties Used:

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 2fr;    /* 3 columns: 25%, 25%, 50% */
    grid-template-rows: 150px 100px 100px; /* 3 rows with fixed heights */
    grid-gap: 20px 10px;                   /* 20px row gap, 10px column gap */
}
```

#### Visual Layout:
```
Grid line:   1              2              3                        4
             │              │              │                        │
         ┌───┴──────────────┴──────────────┼────────────────────────┴───┐
         │      🟤 Sixth (grid-column: 1/3)│      🟢 Second             │
Row 1    │      spans columns 1-2          │                            │
(150px)  │                                 │                            │
         ├──────────────┬──────────────────┴────────────────────────────┤
         │ 🟧 First     │  🟣 Third (grid-column: 2/4)                  │
Row 2    │              │  spans columns 2-3                            │
(100px)  │              │                                               │
         ├──────────────┼──────────────────┬────────────────────────────┤
         │ 💗 Fourth    │     🔵 Fifth     │        (empty)             │
Row 3    │              │                  │                            │
(100px)  │              │                  │                            │
         └──────────────┴──────────────────┴────────────────────────────┘
```

> **Note:** Grid lines are numbered starting from 1. When using `grid-column: 2/4`, 
> the item spans from line 2 to line 4, covering columns 2 and 3.

#### 🎓 Concepts Demonstrated:

| Property | Usage | Description |
|----------|-------|-------------|
| `grid-template-columns` | `1fr 1fr 2fr` | Creates proportional columns |
| `grid-template-rows` | `150px 100px 100px` | Fixed row heights |
| `grid-gap` | `20px 10px` | Different row/column spacing |
| `grid-column` | `1/3` or `2/4` | Item spans multiple columns (line to line) |
| `grid-row` | `1/2` | Item positioned in specific row |

---

### 📄 Example 2: Page Layout (`basic.html` + `basic.css`)

A complete page layout using `grid-template-areas` for semantic placement.

#### HTML Structure:
```html
<div class="container">
    <div class="items header">Header</div>
    <div class="items menu">Menu</div>
    <div class="items box1">Box 1</div>
    <div class="items box2">Box 2</div>
    <div class="items sidebar">Sidebar</div>
    <div class="items content">Content</div>
    <div class="items footer">Footer</div>
</div>
```

#### Key CSS Properties Used:

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: 120px 60px 100px 400px 50px;
    grid-gap: 15px;
    grid-template-areas:
        "header header header"
        "menu menu menu"
        "box1 box2 sidebar"
        "content content sidebar"
        "footer footer footer";
}

.header { grid-area: header; }
.menu { grid-area: menu; }
.sidebar { grid-area: sidebar; }
/* ... etc */
```

#### Visual Layout:
```
┌─────────────────────────────────────────────────────────┐
│                 🟧 HEADER (120px)                       │
│              grid-area: header                          │
├─────────────────────────────────────────────────────────┤
│                 🟢 MENU (60px)                          │
│              grid-area: menu                            │
├─────────────────┬─────────────────┬─────────────────────┤
│  🟣 BOX1        │  💗 BOX2        │                     │
│  (100px)        │  (100px)        │   🔵 SIDEBAR        │
│  grid-area:     │  grid-area:     │   (spans 2 rows)    │
│  box1           │  box2           │   grid-area:        │
├─────────────────┴─────────────────┤   sidebar           │
│         🔷 CONTENT (400px)        │                     │
│         grid-area: content        │                     │
├───────────────────────────────────┴─────────────────────┤
│                🟡 FOOTER (50px)                         │
│              grid-area: footer                          │
└─────────────────────────────────────────────────────────┘
```

#### 🎓 Concepts Demonstrated:

| Property | Usage | Description |
|----------|-------|-------------|
| `grid-template-areas` | Named layout map | Visual grid definition |
| `grid-area` | `header`, `menu`, etc. | Assigns items to named areas |
| `repeat()` | `repeat(3, 1fr)` | Creates 3 equal columns |
| Spanning rows | `sidebar` spans rows 3-4 | One area spanning multiple rows |

---

## 📚 Quick Reference

### 🏠 Container Properties

| Property | Description | Example |
|----------|-------------|---------|
| `display: grid` | Creates grid container | `display: grid;` |
| `grid-template-columns` | Define columns | `1fr 1fr 2fr` |
| `grid-template-rows` | Define rows | `100px auto 100px` |
| `grid-gap` / `gap` | Space between cells | `20px` or `20px 10px` |
| `grid-template-areas` | Named layout map | `"header header"` |

### 📍 Item Properties

| Property | Description | Example |
|----------|-------------|---------|
| `grid-column` | Column position/span | `1 / 3` or `span 2` |
| `grid-row` | Row position/span | `2 / 4` or `span 2` |
| `grid-area` | Named area or shorthand | `header` or `1/1/2/3` |

### 📐 Sizing Units

| Unit | Description | Example |
|------|-------------|---------|
| `fr` | Fractional unit | `1fr 2fr` (1:2 ratio) |
| `px` | Fixed pixels | `200px` |
| `%` | Percentage | `50%` |
| `auto` | Content-based | `auto` |
| `minmax()` | Range | `minmax(100px, 1fr)` |
| `repeat()` | Repetition | `repeat(3, 1fr)` |

---

## 🚀 Getting Started

1. Clone this repository
2. Open `index.html` in your browser for the basic example
3. Open `basic.html` for the page layout example
4. Modify the CSS files to experiment with grid properties!

---

## 📖 Resources

- 🔗 [MDN CSS Grid Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
- 🔗 [CSS-Tricks Complete Grid Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)
- 🎮 [Grid Garden - Interactive Learning](https://cssgridgarden.com/)

---

## 📝 License

Feel free to use this code for learning and experimenting with CSS Grid! 🎉

---

Made with 💙 for learning CSS Grid
