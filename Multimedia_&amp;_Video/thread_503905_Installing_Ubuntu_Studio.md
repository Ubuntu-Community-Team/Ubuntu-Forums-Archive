---
title: "Installing Ubuntu Studio"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by ukulele_ninja on 2007-07-18
I just downloaded the packages for Ubuntu studio from the download page on their site using the konsole. It was very quick and such, but how do I actually install it? It says it finshed downloading the packages, but i dont know how to actually install it. Thanks!

---

### Post by theorganloft on 2007-07-18
I just obtained the .ISO image and created the DVD.  It will load directly from the DVD.:guitar:

---

### Post by adam_kimber on 2007-07-18
If you have "gdebi" installed then you can double click on them and it will install them through a shiny GUI. There is a KDE frontend for "gdebi" which I think the package is called "gebi-kde", install through Synaptic or your favorite package installer. 

If however you want to install packages via the command line (konsole in your case) just do the following, if say your package is called "ubuntustudio.deb"

```
$ dpkg -i ubuntustudio.deb
```

And off it goes. 

I however you have downloaded RPMs there are complicated ways to convert them to DEBs and as of yet I am unaware of an easy way to install RPMs on a Debian based distribution such as Ubuntu. 

Also if you have downloaded a file that ends with tar or tar.bz or tar.gz (bz and gz are compression formats names bzip and gzip respectively) you have the source code that will require compiling.

Hope this helps.

Adam

---

### Post by Gremlinzzz on 2007-07-18
[http://news.softpedia.com/news/How-to-Install-Ubuntu-Studio-54514.shtml](http://news.softpedia.com/news/How-to-Install-Ubuntu-Studio-54514.shtml)
:guitar:

---

### Post by Gremlinzzz on 2007-07-18
The ubuntu studio  theme looks pretty cool. just installed it.
:guitar:
:guitar:
:guitar: everyone plays guitar

---

