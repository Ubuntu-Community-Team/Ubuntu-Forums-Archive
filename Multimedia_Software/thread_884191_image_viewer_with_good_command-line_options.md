---
title: "image viewer with good command-line options"
date: 2008-08-08
forum: Multimedia Software
---

### Post by BetterSense on 2008-08-08
I'm building a picture frame. Upon boot, i want the system to display images that have been pre-loaded onto a flashdrive. I'm trying to find a program with convenient command line switches. gwenview works doing the following, except the pictures don't advance. you have to use the arrow keys.

```
gwenview -f --filter-name *.jpg /media/disk/pictures/

```
gwenview -f --filter-name *.jpg /media/disk/pictures/

is there a way to make it slideshow with command line options, or is there another program that will?

---

### Post by kerry_s on 2008-08-08
try feh-> [http://linuxbrit.co.uk/feh/wiki/FehHelp](http://linuxbrit.co.uk/feh/wiki/FehHelp)

**sudo apt-get install feh**

it can even pull images over the internet if you want. :)

---

### Post by BetterSense on 2008-08-10
Nice. It appears that can do exactly what I want. I wasn't planning on having internet access, but heck if it could full photos from a flickr or something...

---

### Post by jimav on 2013-04-13
The feh link has changed to [http://linuxbrit.co.uk/software/feh/]("http://linuxbrit.co.uk/software/feh/")

---

### Post by nothingspecial on 2013-04-13
Thanks for the info, but this post is old and needs to be put to sleep.

Closed.

---

