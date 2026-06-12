---
title: "Anything 3D crashes in Ubuntu."
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by theyain on 2007-09-01
Every time I open up a program that uses 3D objects, I am sent directly to the login screen.  I thought It might be the video card drivers, so I uninstalled them .  I Still have that problem.  I tried restarting my computer.  No effect. 

I haven't always had this problem.  Before this happened I could play different games with an okay frame rate (I have a Via UniChrome S3, in other words, a very crappy card).  But now I can't do anything.  Help?

---

### Post by kissg1988 on 2007-09-02
Well, this is a known problem, it's because the Unichrome DRI driver contains some major bugs. I have a PC with a VIA Unichrome graphics adapter (P4M800 chipset) and I experience "assertion failed" errors and sometimes even lockups, when I try to run any games or 3D apps with Wine...
Okay, the bad news are, that there are no solution to this problem, as far as I know.
The good news are, that I found a workaround on the net, that MAY correct (in fact, avoid) some of the bugs in the driver.

First of all, don't forget to install the latest drivers. I got my card working with the SVN version only. Using the drivers shipped with Ubuntu 7.04, the X server didn't even start, when I tried to load the drivers, so my only choice was to use the vesa driver, which was really slow.

This is an excellent guide for installing the drivers from source:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

The workaround is described here:
[http://bugs.freedesktop.org/show_bug.cgi?id=10966](http://bugs.freedesktop.org/show_bug.cgi?id=10966)

I hope, this helps you solving your problem.

---

