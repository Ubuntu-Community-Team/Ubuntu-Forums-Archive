---
title: "s3 vision968 no longer works after upgrading to dapper"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by linuxfanatic1024 on 2006-06-06
OK, I have a Pentium II 333 MHz system that I just upgraded from Breezy. Well, I first did an upgrade using APT, and everything worked until I rebooted and found X just froze with a black screen.

So I tried reinstalling from scratch (I had my data backed up) and ended up with the same problem--X won't start.

I tried a dpkg-reconfigure xserver-xorg before and after the clean install and both times it "autodetected" the VESA driver. This card used to work perfectly (and quite fast) in Breezy using the "s3" driver, but now it will only work using the VESA driver. The worst part is that this card is VESA 1.2 ONLY and doesn't let me use all 2MB of the video RAM in VESA mode, so it is very SLOW.

Any ideas? ](*,)

---

### Post by kostkon on 2006-06-06
I think X.org when uses the s3 driver tries to put the card in 24bit color mode which the card does not support. Edit your xorg.conf file to use the s3 driver again, and put the colors to 16bit.

---

### Post by linuxfanatic1024 on 2006-06-06
Well, none of those color depths work. ](*,)

---

### Post by linuxfanatic1024 on 2006-06-07
Anybody have a solution for this?

---

