# hlusicQA blog

## Introduction

This is the repository of my personal blog which is also a reference to my professional part of life.
For the past few years I have been working as a quality assurance engineer (or QA, or tester...).
Having a certain experience with both manual testing, automation testing, and documentation writing and maintaining,
I decided to describe you my own experiences. Some of them are my advices to you, some are questions I am raising,
some are just my personal opinion, and some are invitation for a constructive discussion.

> Author: Vilim Hlušička  
> Contact: [vilim.hlusicka@gmail.com](vilim.hlusicka@gmail.com)  
> Initialization of draft of this blog: 15.10.2025.

## Setting up HUGO website

### What is HUGO

HUGO is the fast open-source static site generator used for building websites, most commonly simple sites such as blogs, repositories and CVs.

It is very simple to use as it generates the whole website with given theme. Content is written in Markdown format which makes it easy to generate and update.

### Get started with HUGO

Depending on which platform you intend to develop on, you can choose installation manuals [here](https://gohugo.io/installation/).

Basically you will first need to install:
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Go](https://go.dev/doc/install)
- [Dart Sass](https://gohugo.io/functions/css/sass/#dart-sass)

After meeting the prerequisites you are ready to install HUGO, although this is all already described in previously linked installation manuals.  
Don't worry, knowledge of Go is not mandatory, but some basics with Git and general knowledge or programming is nice to have - or better to say, must have.

### Basic use of HUGO

1. Create a project: `hugo new site myblog`
2. Switch to that folder: `cd myblog`
and initialize git: `git init`  
and install the theme: `git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke`  
'Ananke' is a theme, so feel free to choose any other.  
Tell HUGO to use this theme with:`echo 'theme = "ananke"' >> hugo.toml`
3. Create your first post: `hugo new posts/my-first-post.md`  
Open the Markdown file with any text editor and edit it, write in it.
4. Change `draft: true` into `draft: false` within Markdown file to publish it:
```
---
title: "My First Post"
date: 2025-10-14T22:00:00+02:00
draft: true
---
```
5. Start server: `hugo server -D`  
Open local web with URL `http://localhost:1313`, or whatever URL is printed in the terminal after running server
6. That's it, you can now develop your website until you publish it to public.

---
### Create additional page

Additional page like "About" can be created similar as creating a new post. Here are the steps:
1. Run this command: `hugo new about.md`. The `content/about.md` will be created.
2. Open it and edit it to look something like this:
```
+++
date = '2025-10-20T20:59:26+02:00'
draft = false
title = 'About'
layout = 'about'
type = 'page'
+++
Hi there! This is my QA blog and I'll share some knowledge here.
```
3. Add it to the `hugo.yoml` file:
```
[[menu.main]]
    weight = 4
    identifier = "about"
    pre = ""
    post = ""
    name = "About"
    url = "/about/"
    title = ""
```
3. Run `hugo serve` and check it out!

---
### File structure

File structure in Hugo is a bit specific and it is very important not to make the mistake by changing anything inside the `public/` or `theme/` folders. This folder is used for **generated output** and everytime you start the Hugo server all the changes you made within that folder will be overriden.

In case any changes need to be done to some specific page (home, about, categories, etc) or some part of a page (header, footer, menu), it is best to do the following:
- Copy the wanted `.html` file from `public/` folder
- Return to root folder of the project (where the .toml file is located)
- Create a folder `layouts`. If the original file was nested in some additional folder, create also the full relative path
- Paste the `.html` file in newly created folder(s)
- Edit **that pasted file**

---
## Git(hub)

### Push to public
Static page from the `public` folder needs to be copy/pasted into the folder which is intended to be uploaded to repository which is set on GitHub Pages.
From that folder execute the following git commands:
```
git add .

git commit -m "Deploy <todays date>"

git push main gh-pages
```

After that the latest version of Hugo page is available on GitHub Pages.
