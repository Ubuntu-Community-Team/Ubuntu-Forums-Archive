---
title: "[SOLVED] cx88-dvb wont load"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by ronacc on 2007-11-20
after a recent update cx88-dvb wont load . it was working fine as recently as 2 weeks ago .  I have cx88-dvb in /etc/modules but it dosent load at boot up , sudo modprobe cx88-dvb  says no such device , checking
 $ ls /lib/modules/2.6.20-16-generic/kernel/drivers/media/video/cx88/
cx8800.ko  cx88-alsa.ko       cx88-dvb.ko         cx88xx.ko
cx8802.ko  cx88-blackbird.ko  cx88-vp3054-i2c.ko

shows that the module is there. any sugestions ? 

I filed bug #164257

---

### Post by ronacc on 2007-12-13
after updates today december 13 ,2007 cx88-dvb now loads normaly.

---

