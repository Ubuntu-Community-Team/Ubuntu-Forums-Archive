---
title: "Edgy and Xinerama"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by Oreo on 2007-01-02
I see there have been two unanswered threads with the same problem I have.

I upgraded from Dapper to Edgy, and I find that my Xinerama "on" does not work well with Edgy, either with my Beamer (lcd projector) or with my external monitor. There are parts of one desktop that leak over onto the other monitor. Using my external monitor (resolution 1280x1024) and internal monitor (1280x800) are different sizes. Now I get the desktop wallpaper 2 1/3 times.

I was not able to use the fglrx, so I had to revert to the xorg driver. If I successfully reverted to xorg, why doesn't my old xorg.conf work like it did before?

Thanks,
Oreo

---

### Post by TLE on 2007-01-04
I think there was an update of Xorg from dapper to edgy. I also had to configure things from scratch.

BTW what do you mean revert from **fglrx** to xorg. **fglrx** is a driver xorg is not (it's the graphical system). If you have an ati card you should be using either the **fglrx**, **ati** or **radeon** driver.

I use the **fglrx** supported Xinerama myself. So my suggestion would be to configure it from scratch. Backup your xorg.conf, re-enable the fglrx driver and read the man page to **aticonfig**. That should get you started.

---

