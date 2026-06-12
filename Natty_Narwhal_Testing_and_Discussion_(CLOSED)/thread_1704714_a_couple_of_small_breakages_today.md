---
title: "a couple of small breakages today"
date: 2011-03-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-03-11
Depending on your hardware, drivers ect. the upgrade of libgl1-mesa-glx may cause software center to segfault (possibly a few other apps also
libgl1-mesa-glx (7.10.1~git20110215.cc1636b6-0ubuntu2) to 7.10.1-0ubuntu1

the main bug is here,(2+ years old, but as reemerged) - the most likely to be affected are nouveau users (nvidia
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219)

Also a possibility is that the global menu with focus on the desktop may have disappeared, if so, it can be attributed to the upgrade of appmenu-gtk, reverting to previous version will restore if affected
[https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/733050](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/733050)

---

### Post by dino99 on 2011-03-11
no trouble here with i386 & nvidia-current (default genuine package) on 8500gt with gnome classic

---

### Post by mc4man on 2011-03-11
> no trouble here with i386 & nvidia-current 
The sc deal would only be w/ nouveau, nvidia-current is fine

As far a gm on desktop see here on 2 installs, though never know..

---

### Post by dino99 on 2011-03-11
ok but your title will make the buzz

---

