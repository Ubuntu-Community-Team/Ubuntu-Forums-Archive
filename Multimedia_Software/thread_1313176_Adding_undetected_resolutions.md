---
title: "Adding undetected resolutions"
date: 2009-11-03
forum: Multimedia Software
---

### Post by unckybob on 2009-11-03
Hi,

I just upgraded from 9.04 to 9.10 and am very pleased. I'm still having problems with my screen resolution though.

In v9.04 I was able to set my resolution to 1280x1024. But under v9.10 the highest resolution I can get is 800x600.

I'm using an "ASUS A7N266-VM Rev. 1.03" motherboard with on board video controller.

One of the lines from the "lspci" command yields:

02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

"System-> Administration-> Hardware Drivers" suggests activating the proprietary "NVIDIA accelerated graphics driver (version 96)" I tried it and it messed up the display so badly that I was barely able to get it back to something discernable again.

I went to the following page:

wiki.ubuntu.com/X/Config/Resolution

It explains how to add undetected resolutions with "xrandr".

I tried the following as directed by the wiki:

robert@AMDBOX:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0
   640x480        60.0
   400x300        60.0     56.0
   320x240        60.0
robert@AMDBOX:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
robert@AMDBOX:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
robert@AMDBOX:~$ xrandr --addmode default 1280x1024_60.00
robert@AMDBOX:~$ xrandr --output default --mode 1280x1024_60.00
xrandr: screen cannot be larger than 800x600 (desired size 1280x1024)

I also tried the above but instead of "default" I used "VGA":

robert@AMDBOX:~$ xrandr --addmode VGA 1280x1024_60.00
xrandr: cannot find output "VGA"

I'm stymied. Can someone please help?

Thanks,
Bob

---

