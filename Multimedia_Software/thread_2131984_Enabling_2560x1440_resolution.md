---
title: "Enabling 2560x1440 resolution"
date: 2013-04-03
forum: Multimedia Software
---

### Post by Tuure247 on 2013-04-03
Hi!


I just bought a new display (Asus PB278Q) and I'd like to use the 2560x1440 resolution it supports on Ubuntu 12.10.


I've got switchable graphics on my laptop. Intel HD4000 and Nvidia 630M. I haven't got the Nvidia drivers to work with unity.


The display works with the Intel graphics card with the following settings under Windows:
Resolution 2560x1440,
Refresh Rate: 50Hz,
Timing Standard: CVT-RB


The max resolution I can choose on Ubuntu is 1920x1200. I've tried the following:
gtf 2560 1440 35
xrandr --newmode "2560x1440_35.00"  173.58  2560 2696 2968 3376  1440 1441 1444 1469  -HSync +Vsync
xrandr --addmode HDMI1 2560x1440_35.00


If I then select the 2560x1440 resolution I get a tiled screen with blinking strange colors. With 50Hz I get no signal to the hdmi.

I'd greatly appreciate any ideas regarding how to get the display working with the full resolution on Ubuntu.

---

