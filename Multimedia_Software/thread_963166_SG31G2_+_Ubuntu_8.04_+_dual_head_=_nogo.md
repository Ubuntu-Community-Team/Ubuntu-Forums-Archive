---
title: "SG31G2 + Ubuntu 8.04 + dual head = nogo?"
date: 2008-10-30
forum: Multimedia Software
---

### Post by linklemming on 2008-10-30
Trying to setup my SG31G2 (Intel GMA 3100) to run dual head in Ubuntu Hardy Heron 8.04

Left Monitor - Dell 1905FP connected to VGA port on XPC via VGA cable
Right Monitor - Dell 1905FP connected to DVI port.on XPC via DVI cable

On bootup, XPC screen shows up on both screens as does Ubuntu Splash Screen

Login prompt switches to just Left monitor and thats all I get no matter what I do.

I am using the latest Intel driver as its included in 8.04 and trying to upgrade it , it tells me its the latest.

Seeing as how its the Intel driver, I followed the following information:

[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

I haved played with the xorg.conf (about 20 different configurations) and xrandr

Using xrandr, it should be really simple and should work without xorg.conf changes

First I do xrandr -q and get

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
1280x1024 60.0*+ 75.0 59.9
1152x864 74.8
1024x768 75.1 60.0
800x600 75.0 60.3
640x480 75.0 60.0
720x400 70.1
TMDS-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
1280x1024 60.0*+ 75.0 59.9
1152x864 74.8
1024x768 75.1 60.0
800x600 75.0 60.3
640x480 75.0 60.0
720x400 70.1

To do a 'simple clone monitor' setup I enter the following command

xrandr --output TMDS-1 --same-as VGA

And nothing happens, right monitor is still blank.

I have tried hundreds of xandr commands but decided to focus on the simplest.

Any ideas?

Gary

---

### Post by jim-nf on 2008-11-01
I've a problem with the onboard SG31G2 and getting the G31 card to run at all.

All I can achieve with the GMA3100 is running the VESA drivers - how did you get the intel drivers working?

I want to use the dual head too eventually, perhaps I can help, once I get over the first hurdle.

Can you help me out?

TIA!

---

