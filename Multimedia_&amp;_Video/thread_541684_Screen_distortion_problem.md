---
title: "Screen distortion problem"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by bsh on 2007-09-03
Hi
I'm a complete Ubuntu (& linux) n00b, but i used to be good with computers in general...
I have a problem. I have a secondary pc, with a dual boot (Ubuntu 6.10 desktop x86) and windows xp. Hardware specs: AMD Duron 1200, 2x128MB SDRAM (133mhz), AGP4x MSI Nvidia GeForce2 Ti 64MB, some harddisk and cdrom, all basic stuff. The monitor i'm using is an LG Flatron 19" CRT.
Problem is, my main pc uses this same monitor, and this secondary pc too. I used to use 1024x768@100Hz or 1280x960@85Hz, they are all in the monitor's usable range (max. res is 1600x1200,75Hz i think but could be 60hz) When i use the monitor with my main pc or with the secondary pc's windows part, it displays everything fine.
But when i use ubuntu, the screen loses horizontal linearity, ie. the image gets "dense" towards the right edge of the screen. I'm using the default ubuntu nvidia driver, but tried using plain vesa.
Tried adjusting the monitor, but this linear distortion remains there, can't get rid of it.
Why could this happen? Should i install the nvidia drivers? Might that help?
Other problem is, i set up GDM correctly, defined the monitor's maximum resolution and refresh (once with the medium settings (1600x1200x75hz) and also tried the advanced setting and set the vertical refres to 79khz). Either way, the desktop won't let me select all available refresh rates. For example, at 1024x768, i can only select up to 85hz, even if my monitor is capable of doing it in 100hz. Above this resolution, i can only select 60hz, no 85hz in 1280x960 etc!
I believe the distortion is caused by the wrong refresh rate.
So any ideas what should i try?
TIA

---

### Post by ddrichardson on 2007-09-04
Specify the correct horizontal and vertical refresh rates in /etc/X11/corg.conf there is a good chance that when it was autodetected by X probing that it hasn't calculated the modes entirely correctly.

---

### Post by bsh on 2007-09-04
thanks
it hasn't been autodetected (i skipped auto detection), since the monitor is connected to the pc via rgb+hv cable and there is no vesaddc channel with that. that's why i skipped auto detection and entered the correct h+v values.

---

