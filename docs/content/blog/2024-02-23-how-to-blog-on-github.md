+++
title = "How to document and blog on github pages"
description = "How to setup your own documentation hub"
date = 2024-02-23T00:00:00+06:00
updated = 2024-02-23T00:00:00+06:00
draft = false
template = "blog/page.html"

[extra]
lead = "This is a meta post about how to document"
+++

# Taking note

Rocking it like the 90s, static web sites are easier to host and maintain.

[Github](https://pages.github.com/) provides free hosting, stepping in for geocities.

I tend to take notes in [markdown](https://www.markdownguide.org/basic-syntax/), even if I'm just using notepad.  It's pretty intuitive syntax.

For simplicity I chose [Zola](https://www.getzola.org/) for the static website generator.  It is a single executable with no dependencies, and has github actions supported.  The project isn't a snob about supporting Windows.


# Github hosting

## Create repo on github

[Follow the guide](https://pages.github.com/).

Additionally I created an orphaned branch that the gh-pages will be published too.

```
git checkout --orphan gh-pages
git reset --hard
git commit --allow-empty -m "init gh-pages branch"
git push origin gh-pages
git checkout main
```

```Command line```

# Zola

## Windows Installation

I just [downloaded the release zip](https://github.com/getzola/zola/releases), and then added the folder I extracted to the path so I could use the command from any terminal window.

## Adidok theme

I installed this via a submodule.  Assuming your main repo has a "docs" sub directory where you are keeping your markdown, from the root of the repo run something like this to install

```
git submodule add https://github.com/aaranxu/adidoks.git docs/themes/adidoks    
```

### Customize Adidok

This required a little more reading of the manual.  Anything in the template can be overidden if the same content is found in your own content folder.  This includes the html templates.  To remove the hero list on the index page required changes to the index.html template.

## Build and test website

To build, make sure you are in the docs directory.  Then run the zola command: ```zola build```

To test on the local machine only (and you can make live content changes here too) run ```zola serve```

## Zola github action

[Zola github pages documentation](https://www.getzola.org/documentation/deployment/github-pages/)

You may look in the ```.github/workflows``` directory to see the docs.yml Zola publishing workflow based on those instructions.

## Content creation

Create [markdown](https://www.markdownguide.org/basic-syntax/) files in the ```docs``` sub-directory to be included in that section of the website, and the ```blog``` sub-directory for the blog section.  Pay attention to the "front matter" in the markdown docs.

For content creation getting the markdown right is probably the biggest hassle over just taking notes normally with Markdown.

Zola adds "[shotcodes](https://www.getzola.org/documentation/content/shortcodes/)" to its flavor of markdown.

