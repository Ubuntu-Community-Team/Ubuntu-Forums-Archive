---
title: "ati drivers freeze ubuntu solid"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by moshuptrail on 2007-04-25
I've been having a problem with my laptop freezing solid while in Firefox, and almost always on a page with a .aspx extension.  It freezes so bad the only cure is to shut off the power.  

I tried the following cures:
1. increase video memory allocated in Bios to 32M
2. boot from 386 kernel instead of K7 kernel
3. re-configure xorg,conf using sudo dpkg-reconfigure -phigh xserver-xorg
4. set option RenderAccel = 0 in xorg.conf
5. tried driver fglrx (didn't work at all)
6. tried driver vesa

Problem solved, although video performance lags now.

I know from reading other posts that ati cards/drivers really stink, but I can't change the video card in my laptop.  Anyone know of any other ways to fix this?

xorg recognizes the card as: ATI Technologies, Inc. Radeon 320M (RS200 IGP)

---

