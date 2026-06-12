---
title: "Alternative to Inkscape?"
date: 2012-07-26
forum: Multimedia Software
---

### Post by Gannin on 2012-07-26
I'm running Lubuntu 64-bit.

I'd like to install Inkscape as I need it for a few things, however it wants to install some dependencies I don't want, such as some gnomevfs dependencies.

Is there any good 64-bit-friendly alternative vector graphics editor out there that doesn't have a boat-load of unwanted dependencies?

---

### Post by UltimateCat on 2012-07-26
> **Gannin said:**
> I'm running Lubuntu 64-bit.

I'd like to install Inkscape as I need it for a few things, however it wants to install some dependencies I don't want, such as some gnomevfs dependencies.

Is there any good 64-bit-friendly alternative vector graphics editor out there that doesn't have a boat-load of unwanted dependencies?

I have been using GIMP for 2 years and it is a good image manipulation program.
[http://www.gimp.org/](http://www.gimp.org/)

Not sure if it has a lot of dependencies or not-
Good luck

---

### Post by ajgreeny on 2012-07-26
Have you tried installing inkscape with the **--no-install-recommends** option.  It may then bring in far fewer packages.

Worth a look-see, I think.

---

### Post by Gannin on 2012-07-26
> **UltimateCat said:**
> I have been using GIMP for 2 years and it is a good image manipulation program.
[http://www.gimp.org/](http://www.gimp.org/)

Not sure if it has a lot of dependencies or not-
Good luck

I thank you for the reply.  I already have Gimp installed, but I also need Inkscape, as I use them for different things, with Gimp being a bitmap editor and Inkscape being a vector editor.

> **ajgreeny said:**
> Have you tried installing inkscape with the **--no-install-recommends** option.  It may then bring in far fewer packages.

Worth a look-see, I think.

That does cut down somewhat on what it wants to install, but unfortunately it still wants to install the gnomevfs libs.

---

### Post by Merrattic on 2012-07-26
What's the problem with having those libs, can't be machine speed otherwise you would have trouble running inkscape in the first place (blur!)

I've not found any better vector editor on linux than Inkscape, and having used Illustrator CS3 on Windows I know which I prefer (Inkscape)

---

### Post by Kreaninw on 2012-07-27
GIMP, Inkscape, Blender. This is the rule of what they do. No need to look further :D 

As I'm using Inkscape a lot in my own business for a while now, I would say 4GB of physical RAM is not enough, you need at least 4GB on swap. I hope it will be fixed sometime in the future. So some libs shouldn't cause no pain.

---

### Post by Lars Noodén on 2012-07-27
Depending on what you are drawing, LibreOffice Draw might be a suitable substitute.  Does that clobber your system with dependencies?

---

### Post by cuyo01 on 2012-07-27
karbon, its on the repositories, if not mistaken is part of koffice, dont know how much dependencies needs for standalone installation

---

### Post by Gannin on 2012-07-27
> **Lars Noodén said:**
> Depending on what you are drawing, LibreOffice Draw might be a suitable substitute.  Does that clobber your system with dependencies?

I have it installed and it works well.  The problem is, I don't think it works quite the way I need it do.  For instance, I need to work with images that are exactly 300 px by 300 px, but in Draw it looks like you can only specify page size by inches.

> **cuyo01 said:**
> karbon, its on the repositories, if not mistaken is part of koffice, dont know how much dependencies needs for standalone installation

I believe it'll want most of the KDE libraries installed to install that.

---

### Post by vexorian on 2012-07-27
> **Gannin said:**
> I'm running Lubuntu 64-bit.

I'd like to install Inkscape as I need it for a few things, however it wants to install some dependencies I don't want, such as some gnomevfs dependencies.

Is there any good 64-bit-friendly alternative vector graphics editor out there that doesn't have a boat-load of unwanted dependencies? I wonder if there is a lighter package of inkscape that does not need so much stuff?

I think the difference from Draw to inkscape is like earth to heaven :). Imho. So, this is a drag that you have to pass on inkscape for the dreaded dependencies.

* I use inkscape with 2GB, but in 32 bits mode. It does get bad when I have many of objects in a document though.

---

### Post by mc4man on 2012-07-27
> **Gannin said:**
> I'm running Lubuntu 64-bit.

I'd like to install Inkscape as I need it for a few things, however it wants to install some dependencies I don't want, such as some gnomevfs dependencies.

Is there any good 64-bit-friendly alternative vector graphics editor out there that doesn't have a boat-load of unwanted dependencies?

If you're on 12.04 there are just 3 gnomevfs packages installed, inkscape uses them & no big deal to have installed on lubuntu, don't see what the 'issue' is in that case. (don't know about earlier that 12.04

```
sudo apt-get -s install inkscape
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libart-2.0-2 libblas3gf [COLOR="Blue"]libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra[/COLOR] liblapack3gf libwmf-bin perlmagick python-imaging
  python-lxml python-numpy python-renderpm python-reportlab
  python-reportlab-accel python-uniconvertor


```
More of a possible  issue in 12.04 is some of the inkscape extensions are broken, have been for some time now. Here I use the inkscape trunk ppa which works fine

---

### Post by Kreaninw on 2012-07-27
Inkscape in the USC can't open recent file correctly. While Inkscape Trunk has a bug when you made clipping path, bounding box won't resize itself automatically.

[https://bugs.launchpad.net/inkscape/+bug/1005085](https://bugs.launchpad.net/inkscape/+bug/1005085)

---

### Post by mc4man on 2012-07-27
> **Kreaninw said:**
> Inkscape in the USC can't open recent file correctly. While Inkscape Trunk has a bug when you made clipping path, bounding box won't resize itself automatically.

[https://bugs.launchpad.net/inkscape/+bug/1005085](https://bugs.launchpad.net/inkscape/+bug/1005085)
Guess it may be 'pick your poison' atm, though I've more confidence that inkscape trunk will fix things before Ubuntu will provide a solid package
(sometimes with trunk builds if you happen to get one that suits your usecase then it's worth making sure you can locally downgrade if the next one breaks in a manner not appreciated

---

### Post by Gemnoc on 2012-07-29
There was this other vector graphic editor, sK1. It has a Corel Draw GUI and can open .cdr files. But it's not in the Ubuntu repositories. There are .deb packages available on the project's website, but the latest are for Ubuntu 11.04 (they may work, or not, on later Ubuntu releases).

There are no newer packages because the application is being massively overhauled, with an alpha to be released sometime in the future.

[http://sk1project.org/modules.php?name=Products&product=sk1&op=download](http://sk1project.org/modules.php?name=Products&product=sk1&op=download)

---

### Post by houseworkshy on 2012-07-29
There is a stripped down inkscape "pup" which is for puppy linux, designed to be run live.  So you could use one of those in a live session for this particular job and save the results to your hd.  Scribus is a dtp which *may* do the job.  There are also several small painting/vector drawing programs, searching for vector in the software repositories pulls a lot of suggestions, some of which may be useful.

---

