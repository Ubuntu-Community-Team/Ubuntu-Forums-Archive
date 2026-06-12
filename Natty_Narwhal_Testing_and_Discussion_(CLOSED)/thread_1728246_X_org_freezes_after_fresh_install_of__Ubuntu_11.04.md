---
title: "X org freezes after fresh install of  Ubuntu 11.04"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ufuser1 on 2011-04-13
hi

This is a fresh, new install of ubuntu 11.04. Throughout the installation I didn't encounter any problems so everything went fine.. but now after booting it up it freezes instantly in the desktop.I can see unity and the wallpaper but clicking or right clicking does nothing. I exited the xorg server using ctrl+alt+f7 and switting ttys's and the console works fine. How can I fix the freeze issue? I dont remember having this problem with any other previous version of ubuntu.

Any input will be appreciated!

---

### Post by jonnywombat on 2011-04-13
same issue here..

live cd without unity works fine, but once installed system freezes as desktop loads.

---

### Post by ufuser1 on 2011-04-13
> **jonnywombat said:**
> same issue here..

live cd without unity works fine, but once installed system freezes as desktop loads.

Now also my cds wont be recgonized by the sytem after installing ubuntu so I can't even reinstall it.. what a load of BS.

---

### Post by ufuser1 on 2011-04-14
Turns out its all unity fault. I can switch to classic mode in the login window and everything works fine. I've trued numerous tests and after launching unity from the terminal I get lots of errors and warnings and then the screen freezes.. anyone else having a similar problem?

---

### Post by cariboo on 2011-04-14
What graphics driver are you using?

---

### Post by tormod on 2011-04-15
Unity does make some graphic drivers crash. Your best option is to file a bug report. If you have an ATI card, use "ubuntu-bug xserver-xorg-video-ati", or -intel for Intel cards.

---

### Post by ufuser1 on 2011-04-18
Finally found a bug report for this issue... only for 7300/7400 nvidia cards atm.
[https://bugs.launchpad.net/unity/+bug/728745](https://bugs.launchpad.net/unity/+bug/728745)

---

