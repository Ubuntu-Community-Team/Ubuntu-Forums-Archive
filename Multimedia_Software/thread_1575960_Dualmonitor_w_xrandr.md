---
title: "Dualmonitor w/ xrandr"
date: 2010-09-16
forum: Multimedia Software
---

### Post by AmateurDev on 2010-09-16
I'm trying to set up dual monitors on Xubuntu 10.04. I'm using xrandr because I've tried editing xorg.conf, but it didn't turn out so well in the past.(I also don't have a xorg.conf file on this machine). On my ATI Radeon X13, I have a 1680x1050 Dell Inspriron E1505 laptop screen(LVDS) and a 1280x1024 Samsung 913T monitor(VGA-0). By default, the Samsung is set to 1360x768. I added a new mode by running:
```

cvt 1280 1024
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA-0 1280x1024_60.00
xrandr --output VGA-0 --mode 1280x1024_60.00
```After this, I end up with with the external monitor showing on both the laptop and monitor screens. The Samsung screen is very fuzzy. The recommended resolution is 1280x1024@75hz, so I entered that into the cvt command and went through all the steps again, but the monitor says that it doesn't support that resolution.
Deciding to fix that later, I moved the VGA-0 to the left of the LVDS
```
xrandr --output VGA-0 --left-of LVDS
```but that made everything go "wonky." Both screens were all over the places with lines running through them. I logged out and logged back in, but now the LVDS has the settings of the VGA-0 and the VGA-0 is off. I set everything to how it was supposed to be and went through all these steps again with the same result. Does anyone know why the Samsung is fuzzy and why I can't move the monitor to the left of the screen?
PS - Screen 0 has a max resolution of 8192x8192.
Thanks!

---

### Post by AmateurDev on 2010-09-18
I have tested the monitor on other computers, it is not fuzzy on the other (Windows) I tested.

---

