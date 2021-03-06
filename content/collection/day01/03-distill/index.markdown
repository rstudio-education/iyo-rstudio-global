---
title: "Why R?"
weight: 3
subtitle: "We still don't have a place to put all our R stuff!"
links:
- icon: campground
  icon_pack: fas
  name: slides
  url: "/slides/03-why-r.html"
- icon: hiking
  icon_pack: fas
  name: activity
  url: "collection/day01/03-distill/#activity"
---

<script src="{{< blogdown/postref >}}index_files/fitvids/fitvids.min.js"></script>

## Why R?

<div class="shareagain" style="min-width:300px;margin:1em auto;">
<iframe src="/slides/03-why-r.html" width="1600" height="900" style="border:2px solid currentColor;" loading="lazy" allowfullscreen></iframe>
<script>fitvids('.shareagain', {players: 'iframe'});</script>
</div>

## Activity

TIME: ⏱ 10 minutes

### Pre-requisites

First, make sure you have the latest version of the distill package installed from CRAN:

``` r
install.packages("distill")
```

Restart your R session. If you use RStudio, use the menu item *Session &gt; Restart R* or the associated keyboard shortcut:

-   <kbd>Ctrl + Shift + F10</kbd> (Windows and Linux) or
-   <kbd>Command + Shift + F10<kbd> (Mac OS).

``` r
packageVersion("distill")
[1] ‘1.2’
```

### Create GitHub repo

We’ll follow a [“New Project, GitHub first”](https://happygitwithr.com/new-github-first.html) workflow.

Go online to your GitHub account, and create a new repository and **YES** initialize this repository by adding a `README` file.

### Clone GitHub repo

We just created the remote repository on GitHub. To make a local copy on our computer that we can actually work in, we’ll clone that repository into a new RStudio project. This will allow us to sync between the two locations: your remote (the one you see on github.com) and your local desktop.

Use the RStudio IDE project wizard:

1.  Open up RStudio to create a new project where your website’s files will live.

2.  Click `File > New Project > Version Control > Git`.

3.  Paste the URL from GitHub (either HTTPS or SSH).

4.  Be intentional about where you tell RStudio to create this new Project on your workstation.

5.  Click Create Project.

**Alternatively**, do this (but note that it requires a [GitHub personal access token](https://happygitwithr.com/credential-caching.html#get-a-pat)):

``` r
usethis::create_from_github("apreshill/iyo-distill", 
                            destdir = "/Users/alison/rscratch")
```

### First commit & push

**Everyone - all together now!**

Use the RStudio IDE to commit and push these files:

-   `*.Rproj`

-   `.gitignore`

-   `*.Rproj`

-   `.gitignore`

### Create a new distill site

Inside your current distill project, use the R console:

``` r
library(distill)
```

Let’s start with a simple website:

``` r
create_website(dir = ".", title = "iyo-distill", gh_pages = TRUE)
```

Now, let’s commit all these new files and push to GitHub.

### Build site

Please *close* the RStudio IDE and re-open it. Look in your Git pane, you should see a single file has changed:

<center>

<img src="rproj-git.png" width="500"/>

</center>

Let’s look at the diff:

<center>

<img src="rproj-diff.png" width="500"/>

</center>

Let’s go ahead and commit this file before we start adding to our site.

You should now see a **Build** tab that looks like this:

![RStudio build site tab](https://rstudio-education.github.io/sharing-short-notice/images/screenshots/build-site.png)

Click that :hammer: **Build Website** button, and explore your site!

### Add a postcard

Docs: <https://rstudio.github.io/distill/website.html#postcards>

Now, delete your `about.Rmd` (trust me!). We’ll create a new one with the postcards package.

``` r
postcards::create_postcard(template = "jolla", file = "about.Rmd") 
```

This time, :hammer: **Build Website** instead of knitting :yarn:.

You should be able to now see your new “about” page.

### Site navigation

`_site.yml` controls this- you can add and remove pages here.

Also note, here is your output format:

``` yaml
output: distill::distill_article
```

And here is your output directory (i.e., when you build the site, all the HTML files go here):

``` yaml
output_dir: "docs"
```

### Publish a distill site

We want to publish the “/docs” folder.

Easy:

-   Publish to GitHub pages

    <https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site#creating-your-site>

Medium:

``` r
> usethis::use_github_pages(branch = "main", path = "/docs")
✓ Setting active project to '/Users/alison/rscratch/iyo-distill'
✓ Activating GitHub Pages for 'apreshill/iyo-distill'
✓ GitHub Pages is publishing from:
● URL: 'https://apreshill.github.io/giyo-distill/'
● Branch: 'main'
● Path: '/docs'
```

### Share your site!

Add it to your repository details :heart:
