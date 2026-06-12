---
title: "No high LCD resolution with nVidia card"
date: 2009-12-12
forum: Multimedia Software
---

### Post by ReelExterminator on 2009-12-12
Hi, I'm having some trouble figuring out why I can't set my resolution to the 2048×1152 that my new LCD monitor supports.

I have a GeForce 6600GT video card with DVI output. Gigabyte's _[product page]("http://www.giga-byte.com/Products/VGA/Products_Overview.aspx?ClassValue=VGA&ProductID=1286&ProductName=GV-NX66T256DE")_ says that the DVI output supports resolutions "up to 2560x1600 at 60 Hz." The monitor is a Samsung SyncMaster 2343 that has a native resolution of 2048×1152. After doing a bit of troubleshooting I read that my single link DVI cable doesn't support that resolution, so I went out and bought a dual link DVI cable (fourth connector in _[Wikipedia's image]("http://en.wikipedia.org/wiki/Digital_Visual_Interface#Connector")_). Still no success.

With the nv driver, I am limited to 1280×1024, while with the nvidia driver I am limited to 1920×1080. I have tried adding a new mode using xrandr, but that failed as well:

```
xrandr --newmode "2048x1152" 156.80 2048 2096 2128 2208 1152 1155 1160 1185 -hsync +vsync
xrandr --addmode default 2048x1152
xrandr --output default --mode 2048x1152

```
The first time the last command is run, this error occurs (using nv it says cannot be larger than 1280×1024):
```

xrandr: screen cannot be larger than 1920x1080 (desired size 2048x1152

```
and subsequent times, the screen flashes briefly before xrandr returns with the error:
```
xrandr: Configure crtc 0 failed
```

I thought the problem might be nvidia's drivers, but using the nv drivers the same thing happens. I thought everything was supposed to be automatic with the new xorg.conf-less X configuration :)

I've tried searching through the forums but it seems every problem is slightly different and I haven't found a solution that works.

---

### Post by SJrX on 2009-12-13
Hey, Have you tried a VGA cable to see if you can get that resolution at all. Also Ubuntu 6.06 is really old and is passed is out of support, have you considered upgrading to a newer version?

---

### Post by ReelExterminator on 2009-12-13
Whoops, fixed that - I'm running 9.10. I'll check how the VGA output works when I get home, but I'd like in the end to use DVI since it's sharper, especially at this higher resolution.

---

### Post by nss0000 on 2009-12-13
I'd be very surprised if an "ancient history" Vid-card like a 6600xx could support 2048x1100 resolution. 

My current 9800gtx+ does 1920x1200 just fine. Get a current NV260 card for robust hi-rez support.

---

### Post by ReelExterminator on 2009-12-20
So using a regular VGA cable works at 2048×1152. Why is using a DVI cable so difficult? ns0000, as I mentioned in my first post the video card specs say it supports up to 2560×1536 over DVI so I'm not so certain that a new video card would solve the problem. Is it not possible to use high resolutions over DVI with Ubuntu?

---

### Post by Dz. on 2010-02-01
I confirm that. It does not work in Ubuntu with DVI, only with VGA. Although Windows support it without problems. I have Samsung 2343BW, nvidia GeForce 7100 and Ubuntu 9.04.

---

