---
title: "Switching between secondary monitor and TV with xrandr"
date: 2009-02-16
forum: Multimedia Software
---

### Post by du@dde on 2009-02-16
I have a Radeon 9800 pro and is using the open source driver (1:6.9.0+git20081003.f9826a56-0ubuntu2.1) and Ubuntu 8.10. TV out (S-video) is working fine for me when I enable* it with xrandr and only have my primary screen connected to VGA-0. However, if I connect another monitor to DVI-0 and reboot the computer - the TV-out will not work (TV is blue). Before I enable the TV I disable DVI-0 by "xrandr --DVI-0 --off".

The output below is what I get when I do a xrandr after enabling the TV out with both monitors and the TV connected. If I add "--verbose" the output says that VGA-0 is using CRTC 0 and S-video CRTC 1. But the TV is still blue. Has anyone been able to use two monitors and alternate between the secondary monitor and a TV using xrandr? Any help is appreciated. Thanks.
------------------
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 337mm x 270mm
   1280x1024      60.0*+   75.0     60.0     60.0*  
DVI-0 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0     60.0     60.0  
S-video connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        59.9*+   72.2 
------------------

*) How I enable my TV out:
xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard pal
xrandr --output S-video --auto

---

