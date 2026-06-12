---
title: "a media centre that works?"
date: 2008-06-29
forum: Multimedia Software
---

### Post by jonhewer on 2008-06-29
hi all,

until yesterday i was happily running kubuntu feisty and freevo 1.7.3

i decided i'd upgrade to hardy (via upgrading to gutsy) and that all seemed to work.  however, i then find out that my freevo installation was broken.

i've tried reinstalling freevo, and have given elisa and xbmc a go as well.  i haven't been able to get any of them to work properly, and am struggling to find any decent installation guides for any of them at all.

all i'm after is a pretty basic media centre application, which will allow me to play my avi files.

as an aside, there is a bug in alsa for my on board sound, so i'm using oss instead.  does this limit my choice of media centre at all?

thanks,
jon

---

### Post by syczu on 2008-06-29
I was using this [http://geexbox.org/en/index.html]("http://geexbox.org/en/index.html") for a while.

---

### Post by Cresho on 2008-06-29
actually, i was in the same boat as you.  I managed to get the xbox media center working.  I did further research and it is open source created by people on their free time.

I was basically looking for a linux software which will play xacti hd1000 videos and this one plays them just fine.  the xacti hd1000 files are 1920x1080 i or p and it is just awsome to see it running on my desktop.  I am planning on buying a xacti hd1010 or a hd1000  this thing plays dvd's too.

here is the tutorial
go to system->administration->software sources

click on third party software and add these two
```

deb [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/team-xbmc-hardy/ubuntu](http://ppa.launchpad.net/team-xbmc-hardy/ubuntu) hardy main

```
close and reload

open terminal and enter this
sudo apt-get update

and now to install
sudo apt-get install xbmc

you can launch it in applications->sounds & Video xbmc

or in terminal type xmbc

There are tons of skins, and tons of plugins and I mean tons.  you just need to look very hard.

[http://xbmc.org/forum/showthread.php?t=33327](http://xbmc.org/forum/showthread.php?t=33327)> [QUOTE][QUOTE][/QUOTE][/QUOTE]

---

