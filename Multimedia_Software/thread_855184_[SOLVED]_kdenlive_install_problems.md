---
title: "[SOLVED] kdenlive install problems"
date: 2008-07-10
forum: Multimedia Software
---

### Post by Naegling23 on 2008-07-10
Im trying to install kdenlive on my kubuntu hardy desktop.  However, when it goes to instal, im gettting a broken package for mlt 0.2.5.  It appears that mlt-data 0.2.5 is causing this (but im not 100% sure) does anyone know how to fix this and get it installed?  I previously had 4.0 running, I just removed it in order to upgrade, and now I seem to be left without kdenlive.

---

### Post by Naegling23 on 2008-07-11
problem solved!

using the thread
[http://ubuntuforums.org/showthread.php?t=604435](http://ubuntuforums.org/showthread.php?t=604435)

I decided to try
sudo apt-get --purge remove mlt mlt++

after that, I just installed kdenlive without a problem.

---

