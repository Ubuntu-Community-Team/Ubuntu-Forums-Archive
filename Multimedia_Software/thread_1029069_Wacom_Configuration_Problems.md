---
title: "Wacom Configuration Problems"
date: 2009-01-03
forum: Multimedia Software
---

### Post by FirewolfX-7 on 2009-01-03
Ok, while this may not be directly multimedia it is needed for my digital drawing.  I have a TwinView setup, working absolutely fine (other than games but that is a different problem) and my Wacom Hot Cell is representing the whole virtual desktop (both screens).

The Ratio Problem is bugging me but I don't know how to configure it.  I've tried a bunch of stuff but I keep running into less common problems.

I've tried xsetwacom but the list dev returns no output even though the wacom driver is fully funtional as far as I can tell well except the scroll function and the buttons, plus I haven't checked rotation.

Oh, and entering xidump -l returns only one device that looks related to the tablet: Wacom Intuos3 6x8 extension

My question is should I reinstall it or change the syntax for my command?

By the way the wacom was installed while installing Ubuntu Studio 8.10 automatically since I kept it connected the entire time while installing the distro.

---

### Post by jyaan on 2009-01-09
Apparently you need to add this to /etc/X11/xorg.conf in your wacom section : ```
Option        "Twinview" "horizontal"
``` And to restrict to a single screen : ```
Option        "ScreenNo" "0" 
```

I don't have a wacom (yet) though, so I can't test it. I also use TwinView, and I'm hoping that when it arrives I won't run into any problems because of it. I'm also having the issue where some games will try to fullscreen across both monitors instead of (being correctly restricted to) the one I launched it in. =/ Fortunately I'm not big on gaming.

---

