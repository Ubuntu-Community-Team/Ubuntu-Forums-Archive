---
title: "2nd Display shows white screen only"
date: 2012-07-31
forum: Multimedia Software
---

### Post by osarusan on 2012-07-31
PC Info: Ubuntu 12.04 x64, ATI Radeon HD4770 and ATI Radeon HD 4200
Bios settings: Surroundview Enabled. FGLRX with Catalyst 12.4

I'm trying to get a surroundview desktop on my 2-display system and I need some help.

When I enable Xinerama, both screens display the desktop, but there are a lot of graphical glitches; tearing, artifacts, etc that make it a poor experience.

When I disable Xinerama, I get a smooth desktop, however within a few secodns after loading, the 2nd display displays a white screen only. It briefly displays my desktop, and then this white overlay pops up (image attached). I can move the mouse onto the white screen and even right-click it as if it were an extension of the desktop, but I can't view anything on it, or see windows on the display.

Is there a way to make this setup work without Xinerama? Or must I use Xinerama and live with the graphical glitches? (xorg.conf also attached for reference)

---

### Post by osarusan on 2012-07-31
Update: I found some more information here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/885989](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/885989)

---

