---
title: "Why there are plenty of xorg.conf versions?"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by eyalben on 2007-12-14
Hy,

I just installed ubuntu Gusty Gibbon.

I installed the restricted driver for my ATI X550 video card and it works fine.

Then I updated my computer and it's stopped working.

Now trying to reinstall it through the GUI won't work.

I tried to look at the /etc/X11/xorg.conf settings and found out that it has tons of configuration file without any logic:

/etc/X11/xorg.conf.1  /etc/X11/xorg.conf.5  /etc/X11/xorg.conf.bkup
/etc/X11/xorg.conf.2  /etc/X11/xorg.conf.6  /etc/X11/xorg.conf.failsafe
/etc/X11/xorg.conf.3  /etc/X11/xorg.conf.7  /etc/X11/xorg.conf.failsafe.bak
/etc/X11/xorg.conf.4  /etc/X11/xorg.conf.8  

Why does there are 8 versions of this file and why should I guess which is the current working file?
How can I know which file is the one my X server uses?


Thank you,

Eyal

---

### Post by disturbedite on 2007-12-14
isn't it self explanatory.  it says right there...

every time a change is made to the xorg config (the file name specifically xorg.conf is the current working version) it is backed up.
all those others are backups.

---

