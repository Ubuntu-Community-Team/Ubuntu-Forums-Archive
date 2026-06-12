---
title: "Screen resolution drop when using RT kernel."
date: 2011-01-21
forum: Multimedia Software
---

### Post by davemar on 2011-01-21
I'm running 10.04 64-bit, and have just installed the realtime kernel to do some audio stuff. When I boot in with the normal generic kernel my display is fine, and comes up with 1920x1200 (the correct resolution for my monitor). My monitor is connected via a VGA KVM switch through a DVI-VGA adaptor to my DVI video card (Nvidia). The xrandr -q is:
```
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
DVI-I-1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-I-2 disconnected (normal left inverted right x axis y axis)

```

When I boot in with the realtime kernel the display only comes on with a lower resolution 1600x1200 (annoyingly 4x3).  The xrandr -q doesn't show a "DVI-I-1" connection, but just a "default" one with a smaller list of resolutions (1600x1200 being the max).

Even if I do a xrandr --newmode and xrandr --addmode with the correct parameters for 1920x1200 it refuses to change resolution.

What's going on?

---

