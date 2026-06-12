---
title: "Strange fglrx error"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by slint on 2007-05-30
I have Ubuntu 32bit installed on an AMD64 laptop with an ATI xpress 1100 video card.
I installed fglrx via restricted-manager and 3d was working very well in all apps.
Today I played Quake III as usual but after some time the game refused to start up, and I noticed that also glchess couldn't switch to 3d mode.
Other 3d apps still work, like 3d screensavers, billard-gl and google-earth.
It seems that my video driver has lost some of its functionality so that some apps don't work anymore.
But I'm quite sure I didn't change or update anything in my system since I was not connected to the net.

---

### Post by eye208 on 2007-05-30
Open a terminal and enter "fglrxinfo". What does the output say?

---

### Post by slint on 2007-06-01
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)


Seems fine.

---

### Post by slint on 2007-06-06
I bring this up since I cannot file a bug report on such a particular issue. I don't even know how it was produced.
I suspect some functionality of the driver was broken, but reinstalling it or even updating to the newest kernel and modules in the ubuntu repository didn't fix it.
Any clue?

EDIT:
another problem I noticed is that, when using the fglrx driver, I cannot log out from my gnome session since it hangs on a black screen instead of loading GDM. This problem doesn't appear if I use the default open-source driver.

---

### Post by slint on 2007-06-14
The glChess problem was due to some missing python-related packages, now it works (follow the instructions in the project's home page on sourceforge).

The other two problems (Quake III and logout resulting in a system freeze) still remain.

---

