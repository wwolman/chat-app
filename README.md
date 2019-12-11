# Chat Interface

The starting steps for a simple interactive chat interface.

## Steps to complete the assignment

### Outline

1. [Setup the Layout](#1-setup-the-layout)
   - Each student will complete
2. [Custom Styling](#2-custom-styling)
   - Group members will divide the tasks


---
## 1. Setup the layout

*⏱ Time to complete: 15-20 mins*

**🎯 Each student should complete this independently, testing along the way. TEST THE SITE LAYOUT IN ALL SCREEN SIZES AFTER EACH LETTER/STEP**
---

### A. Design system properties

Create a block of styling properties. These are example values, change these as a group (add more if required).

```css
:root {
  --col-bg: #ffffff;
  --col-bg-fg: #222222;
  --col-accent1:  palevioletred;
  --col-accent1-fg: #000000;
  --col-accent2:  plum;
  --col-accent2-fg: #000000;
  --col-accent3:  mediumslateblue;
  --col-accent3-fg: #ffffff;
  --col-action: firebrick;
  --col-action-fg: #ffffff;
  --col-error: tomato;
  --col-error-fg: #000000;
  --font-body: serif;
  --font-heading: sans-serif;
  --animations: 0.3s;
}
```

### B. Document defaults

Setup the document defaults. Adjust these as you see fit. Note the heading has properties that will affect other parts of the layout. Complete everything before adjusting these values.

```css
body {
  background-color: var(--col-bg);
  color: var(--col-bg-fg);
  font-family: var(--font-body);
}
h1, h2, h3, h4, h5, h6 {
  font-family: var(--font-heading);
  line-height: 1.25;
  margin: 0.25em 0;
}
h1 {
  font-size: 1.25em;
}
```

### C. Top bar for branding (fixed)

Add styling for the top banner. Modify content or style as needed.

```css
.branding {
  background-color: var(--col-accent2);
  color: var(--col-accent2-fg);
  position: fixed;
  top: 0;
  left: 0;
  z-index: 2;
  width: 100%;
  overflow: hidden;
  text-align: center;
}
```

### D. Side panel of contacts/conversations (fixed)

Style the `other` side panel. Also noticed we're preparing for functionality as well when the `open` class gets added:

```css
.others {
  background-color: var(--col-accent1);
  color: var(--col-accent1-fg);
  position: fixed;
  top: 0;
  left: -100%;
  z-index: 3;
  width: 100%;
  height: 100%;
  padding: 0 1em;
  padding-top: 2.1875em;
}
  .others .panel {
    overflow-y: scroll;
    opacity: 0;
    transition: opacity var(--animations);
  }
.others.open {
  left: 0;
}
  .others.open .panel {
    opacity: 1;
  }
```

### E. Toggle conversation window

This is for the button 

```css
.toggle-others {
  background-color: var(--col-accent3);
  color: var(--col-accent3-fg);
  position: fixed;
  top: 0.5em;
  left: 1em;
  line-height: 1.25;
  z-index: 4;
  padding: 0;
  border: none;
  padding: 0 0.5em;
}
```

### F. Setup conversation window

Adjust the conversation so it doesn't get content stuck under the fixed header.

```css
.conversation {
  padding: 0 1em;
  margin-top: 2.1875em;
}
```

### G. Medium screen styling

Review the following styles for the first media query. 

**Note the drastic change to the functionality of the `.others` sidebar when the `open` class is added or removed. _Try it!_**

```css
@media screen and (min-width: 40em) {
  .others {
    display: block;
    left: 0;
    z-index: 1;
    width: 20em;
    opacity: 1;
    transform: translateX(-20em);
    transition: transform var(--animations);
  }
  .others.open {
    transform: translateX(0em);
  }
  .conversation {
    transition: margin-left var(--animations);
  }
  .others.open ~ .conversation {
    margin-left: 20em;
  }
  .toggle-others {
    position: absolute;
    top: 3em;
    left: auto;
    right: -1.5em;
    width: 1.5em;
    height: 5em;
    padding: 0.25em;
    text-align: center;
  }
  .toggle-others span {
    writing-mode: vertical-rl;
  } 
}
```

### G. Larger screen styling

Add one more media query for larger screens

```css
@media screen and (min-width: 60em) {
  .others {
    width: 30em;
    transform: translateX(-30em);
  }
  .others.open ~ .conversation {
    margin-left: 30em;
  }
}
```


---
## 2. Custom Styling

**🎯 Each student will complete one of these for their group**
---

Divide the tasks amongst group members and complete the work in branch. When complete, merge the branches into the `origin` (remote) repository.

### A. Message block
1. Quickly wireframe a single message block layout, adding all the properties of a `messages` Object that you deem useful/required
2. Review as a group, consider revisions or other configurations before finalizing a choice
3. Sketch the styling (borders, shadows, lines, spacing, shading, etc)
4. Create the HTML for one chat message `article`
5. Fully style the `article` with a class of `.message` using CSS.
6. Create a rule for elements with class `.from-me` to overwrite styles given to `.message` to show it's from the logged in user
7. Create a rule for elements with class `.from-them` to do the same, but show it's from the opposite user

padding between
margin top bottom
display inline


### B. User card
1. Quickly wireframe a list item for a single user, including any relevant information (even if you have to make it up, or the data may be inaccessible)
2. Review as a group, consider revisions or other configurations before finalizing a choice
3. Sketch the styling (borders, shadows, lines, spacing, shading, etc)
4. Create the HTML for the new chat `li`
5. Fully style the `li` with a class of `.usercard` using CSS.
6. Create a rule for elements with class `.selected` so that it's clear from the "Other Conversations" slide out panel that the active conversation is that conversation card
7. Create a modified (if necessary) version of the card with a slightly bigger profile for the `header` of the `#conversation` block of the page, identifying the user you are speaking to.


### C. Input form
1. Quickly wireframe the form that takes the input text from the user, include a few buttons if necessary
2. Review as a group, consider revisions or other configurations before finalizing a choice
3. Sketch the styling (borders, shadows, lines, spacing, shading, etc)
4. Create the HTML for the new chat `form`. Give the msg input component an id of `message`. Give the `<form>` itself an id of `newMsg`. The form will be inside of the `#conversation <footer>`
5. Fully style the `form` with a class of `.newmsg` using CSS.
6. Consider what happens when a user has a longer message to type; test to ensure styling accounts for that
7. Create appropriate style for mouse or form interactions, as well as consideration for an `.error` state
