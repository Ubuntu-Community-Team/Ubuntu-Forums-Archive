---
title: "video locks X in totem"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by BoHu on 2007-04-25
I noticed in Ubuntu 6.10 and now also in 7.04 that playing certain .flv or .avi  videos in totem or VLC causes X to freeze. Keyboard, mouse and display all freeze but sound continues. Not all .flv and .avi files cause this. Only certain ones. Any ideas?

---

### Post by AaronSells on 2007-06-05
Disabling proprietary nVidia drivers seemed to improve this issue for me.

---

### Post by BoHu on 2007-09-19
It's been six months but I finally figured this one out. The problem is the VIA ChromeS3 driver.  It doesn't work well in Debian based distros. Playing any video for more than a few minutes causes a hard Xorg freeze.

---

