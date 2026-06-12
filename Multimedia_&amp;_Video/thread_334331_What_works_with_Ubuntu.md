---
title: "What works with Ubuntu?"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by Drate on 2007-01-08
I seem to consistently find all the hardware that is problematic with Ubuntu.

I currently Have an NV5M64 [RIVA TNT2 Model 64/Model 64 Pro].  I had an ATI All In Wonder, but gave it away.

Apparently you shouldn't just switch out video cards in Ubuntu.  Yeah, I had to reinstall Ubuntu just to get xserver up again.

Now I have updated my drivers by Automatix and then again by a system update after putting in TSEliot's repo.  Beforing and after both updates Google Earth was not liking it, but after both it liked it even less.  I at least got SOME kind of functional possibilities before, but now I get nothing but an unrecognized card error.  I also notice that certain other apps and games are offering various complaints about the video and fail to load properly or at all.

What must I do to fix my situation now, and also when looking into buying a new computer, or new parts for my computer, how do I know what will work with Ubuntu?

-Dustin

P.S.  I would love to be a die-hard supporter of Ubuntu because I love the philosophy you present, but there is no way I can convince others to try it with all the problems I've had with Wireless NICs and video cards.  If it can't perform the more basic functions without an advanced knowledge of Linux or an extremely helpful Forum (which you definitely ARE), then I can't tell people "it's easy to use".  Please, I WANT to to push this in my own area, even set up some programs with local schools for learning Linux via Ubuntu.

---

### Post by teaker1s on 2007-01-08
reinstall for display driver not required.
all you do is at grub boot recovery and
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

---

### Post by hal10000 on 2007-01-08
There are several sites in which you can look for linux compatible hardware, e.g.:
[http://www.linux-drivers.org/](http://www.linux-drivers.org/) (look throgh the links too, they are better than the site itself)
[http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)

---

