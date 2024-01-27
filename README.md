# MDN Learn: HTML & CSS Challenges

Testing my Web Development skills facing the challenges suggested by
[MDN Learn](https://developer.mozilla.org/en-US/docs/Learn)

## Where are the JavaScript challenges

Now a days, there are so many `client-side` websites done with `JavaScript`.
Furthermore, with `Node.js` you can create `full-stack` or `server-side` apps
with this language. As I wanted to learn and improve my skills in `JavaScript` I
decide to create two specific repositories to do so:

- [JavaScript Challenges](https://github.com/pabcrudel/javascript-challenges)
- [JS Refactoring & Unit
  Testing](https://github.com/pabcrudel/js-refactoring-and-unit-testing)

## How to Merge 2 Git Repositories and preserve history

When I start doing the MDN Learn challenges, I've made a repository for CSS
challenges and another one for HTML. However, when I was doing the task of
[Typesetting a community school homepage](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Typesetting_a_homepage)
I thought that having 2 separated repositories have no sense so I merge them.

### How to do it step-by-step

#### 1. Clone repositories to merge

First of all you must clone the repositories that you want to merge. To make
this process easier I specify a sorter name to each repository: html and css.

```bash
git clone https://github.com/<username>/<repository-name>.git html
```

In my case, I clone this repositories.

```bash
git clone https://github.com/pabcrudel/mdn-learn-html-introduction.git html
```

```bash
git clone https://github.com/pabcrudel/mdn-learn-css-challenges.git css
```

#### 2. Create a new repository

Create a new folder and start a new repository there.

```bash
mkdir merged-challenges
cd merged-challenges
git init
```

#### 3. Add the existing repositories as a remotes

```bash
git remote add <remote-name> <remote-path>
```

I cloned my repositories in the same parent folder so I use a simple
relative path.

```bash
git remote add html ../html
git remote add css ../css
```

#### 4. Merge the repositories

This step is a little bit tricky. If there were conflicts, you must solve it
before merging. In order to avoid problems, I prefer not to auto-commit changes.

```bash
git fetch <remote-name>
git merge <remote-name>/<branch-name> --no-commit --allow-unrelated-histories
```

I chose to start with HTML. As it was the first one, there was no conflicts.
However, when I do so with CSS I had to resolve them because I had 2
`README.md` or `LICENSE.md`.

```bash
git fetch html
git merge html/main --no-commit --allow-unrelated-histories
git commit -m "Merging from html/main"
```

```bash
git fetch css
git merge css/main --no-commit --allow-unrelated-histories

# [... solve conflicts ...]

git commit -m "Merging from html/css"
```

#### 5. Testing that the history have been preserved

To do so you must inspect the logs.

```bash
git log --oneline --graph --decorate
```

That's what I get from that command. As you can see, all commits from each
repository are there so I can go back in history:

```txt
* 28db2f5 (HEAD -> main) change: Format document
* 973b47a change: Move html tasks to a html folder
*   c19ef30 Merge remote-tracking branch 'html/main'
|\  
| * e98d76c (html/main) change: Remove unused font variants
| * 0341973 add: Navigation menu styles
| * 6717f34 add: List styles
| * 08a3c72 add: Link styles
| * 63ac3b0 change: Use of variables to improve color management
| * a6897a8 add: General text styling
| * 2c3669e add: Font family to regular texts and headings
| * e645a8b add: Task starting point
| * 8c6a089 change: Move task to it's folder
| * 524f4c4 change: Title name
| * 9963a7f change: Corrected
| * 7761c62 change: Add abbreviation fro "Esq"
| * cee5fdc change: add semantic html5 tags
| * 8c52a4e add: Starting point
| * 3f80086 add: Create a letter using semantic html tags
| * d0e0878 add: Use 'abbr' tag to improve screen readers perform
| * 0cf97ed add: Use definition list to provide organizing terms and their definitions
| * 0fcbea0 add: Create semantic links instead of "click here" ones
| * dceb67a add: Create links to files in the same folder and outer folder
| * 609d1e7 add: Create hyperlinks with titles and email links with default subject
| * 1b0ed99 add: Emphasize words using 'strong' and 'em' tags
| * ebe6990 add: Style lists using ordered and unordered ones
| * af570a0 add: Format text using headings and paragraphs
| * d4cdb18 add: Create a home for this project
| * 65b7ef7 refactor: Rewrite title
| * 193fd9b Initial commit
* d5e1d37 change: Move css tasks to a css folder
*   8c26a0d Merge remote-tracking branch 'css/main'
|\  
| * 478d8ca (css/main) add: Create a layout for the design
| * 9213316 change: Format document
| * 0582546 add: Complete Responsive Web Design exercises
| * 98c896e add: Complete Position exercises
| * fc93ce1 add: Complete Grid exercises
| * 050a11f add: Complete Float exercises
| * 54ed8a9 add: Complete Flexbox exercises
| * b166480 add: FlexboxFroggy & GridGarden done
| * 1c7e0df add: CSS Layout tasks starting point
| * 0732640 change: Update colors
| * b961007 change: Be specific instead of shorthand because of shorthands do more things
| * 8bf4fdf change: Only first children, not <p> child
| * 30768f8 change: Orange color for anchor must have the ':link' pseudo element
| * 097852a add: Stylize card following the instructions
| * 326d39f change: Link to the CSS file
| * 41b7319 change: All images fits inside it's container
| * c8bfd99 change: Stylize the inner box with relative units that depends on it's parent
| * df632b3 change: Set fixed heights although it's contents overflows
| * ba500d1 change: Add font size using relative and absolute units
| * cd3b53d change: Set the same color in different ways
| * c7a513b change: Stylize boxes using overflow
| * 49d99f0 change: Add margin using shorthand version
| * e3db940 change: Use inline-flex to avoid span bad behavior
| * 2e18e65 change: Set width by calculating siblings box properties
| * 7567a87 add: Instructions for the final exercise
| * ff94a93 add: Images of the tasks
| *   4c0aa83 Merge branch 'main' of https://github.com/pabcrudel/mdn-learn-css-syntax
| |\  
| | * 6339465 add: Create LICENSE
| * | 5777e29 add: Initial state of css properties tasks
| * | 515ac86 change: Title and introduction matches the repo purpose
| * | c4e6378 change: Wrap css syntax exercises in it's own folder
| |/  
| * 7b469a4 refactor: Change colors by reordering layers
| * 71d73a0 refactor: Reset background color without using colors
| * 59452b3 refactor: Stylize anchors depending on it's content
| * 140e857 refactor: Use ids and classes to add style
| * 755a473 refactor: Add style to paragraphs and list items by combining with it's parent
| * 3a51144 refactor: Use pseudo classes to style by some conditions
| * 2b4d582 add: Create a Markdown with the task statement
| * b8a0537 add: Stylize headings and span html tag
| * 69ead5c add: Starting point of MDN Learn tasks
| * 70db640 add: README.md
| * e34d50d add: Text files line breaks must be Unix like (LF)
* ec85872 add: Readme
* 30deae3 add: Text files line breaks must be Unix like (LF)
* bc23975 add: MIT License
```

#### 6. Remove remotes

Once successfully merged, you can remove the remotes or leave them there. In my
case, I prefer to remove them because I want to upload it to GitHub.

If you remove the remotes and inspect the logs again, all tags that references
the legacy repositories will disappear.

```bash
git remote remove <remote-name>
```

Don't forget to remove both remotes.

```bash
git remote remove html
git remote remove css
```

Then you can upload to GitHub this merged repository.
