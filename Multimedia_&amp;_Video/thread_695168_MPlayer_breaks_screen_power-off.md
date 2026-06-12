---
title: "MPlayer breaks screen power-off"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by lodp on 2008-02-12
Hi,

Playing videos with mplayer (using KMplayer as a front-end) seems to disable the power saving option to switch off the display after a custom period. I guess mplayer keeps the display from being switched off while playing, and that's fine, but it doesn't restore that feature after the player is closed.

Anybody else having that problem, or know how I can find out more about it?

---

### Post by xzero1 on 2008-02-13
There are other applications that have the same effect. After using certain video applications, the screen will not power down.

---

### Post by xzero1 on 2008-02-14
It could also be a hidden window waiting for keyboard input  -- which could cause the same symptom.

---

### Post by lodp on 2008-04-15
I don't think so, it really only happens after i've run Mplayer in full-screen mode. Does anybody know a solution to this?

---

### Post by peakshysteria on 2008-04-15
I'm sure people could help better if you told us the OS and video card

---

### Post by lodp on 2008-04-17
sorry, i should have thought of that.

i'm running feisty with an ATI Mobility Radeon X1300 video card. I'm using xorg-driver-fglrx.

come to think of it, maybe i should try the restricted driver, just to see..

EDIT: now i'm confused. is the xorg-driver-fglrx the restricted one or the non-restricted one? the package is installed, but the restricted driver management thingy in system settings says the restricted driver is not being used. /etc/X11/xorg.conf just says: 'Driver; "fglrx"'

---

