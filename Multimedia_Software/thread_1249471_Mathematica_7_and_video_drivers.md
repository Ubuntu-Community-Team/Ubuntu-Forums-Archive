---
title: "Mathematica 7 and video drivers"
date: 2009-08-25
forum: Multimedia Software
---

### Post by Mercredi on 2009-08-25
I recently installed Mathematica 7, and quicly found that three-dimensional plots did not display. A friend who's rather more Linux-savvy than I am concluded the problem was with my video drivers (I seem to have "Intel Corporation 4 Series Chipset" as my video/graphics card), could not find newer versions for Ubuntu, and so installed newer Debian drivers for me from source.

I'm now able to see three-dimensional plots, but cannot reliably rotate them. Also, because the drivers are not what Ubuntu expects, the system considers them to be broken packages and I am unable to use the package manager (including apt-get on the commandline) or run any updates without removing them.

Is there a good solution to this? Failing that, is there a way to back up the drivers my friend installed, so that I can re-install them more easily?

EDIT: I rolled back my friend's graphics fix and followed the instructions in the sticky'd Intelgraphics performance guide. This fixed the package manager issues, but I'm still seeing the same problems in Mathematica with rotating 3-d images reliably.

---

