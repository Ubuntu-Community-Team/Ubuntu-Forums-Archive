---
title: "Compaq V2000 S Video problem"
date: 2010-02-12
forum: Multimedia Software
---

### Post by sickgonzo on 2010-02-12
I recently reformatted my brother's Compaq Presario V2000 laptop and everything else seems to be running fine. The only problem is that now, when I hook it up to the TV via an S Video cable, I go to my display settings and it wont allow me to extend my desktop onto another monitor (The TV). Why wont it recognize the S video cable now? Is there a Driver I need? Any help would greatly appreciated. Thanks

---

### Post by gordintoronto on 2010-02-12
For most laptops, there is a key-combination which switches between the laptop screen and/or an external monitor.  (Such as Fn-F2 or Fn-F4)  I have never seen one which supports two monitors showing different things.

Do you have the manual for the V2000?

---

### Post by sickgonzo on 2010-02-12
Unfortunately, I do not. we would right click<properties<display settings. Then there would be two boxes, one with 1 in it and the other with 2 in it. Now it just shows a computer screen without any number in it at all.

---

### Post by sickgonzo on 2010-02-12
I'm trying to enable dualview

---

### Post by efflandt on 2010-02-13
Once you connect your TV try logging out of X and logging back in, then see if it shows up, or is listed as connected in xrandr terminal command (or System > Properties > Display).

I don't have an S-Video cable handy, but following is example of xrandr output when V2000 is booted with no external display, after external VGA was connected (then logout/login), then after using xrandr to switch off laptop display and switch VGA-0 to 1360x768 (apparently the maximum it can do with 1080p display due to video RAM limit?).

```
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x 1280
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x768+0+0 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1360 x 1360
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9* 
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 1360
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected (normal left inverted right x axis y axis)
   1280x768       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)
```

Not sure if "S-video" output is limited to 640x480 for NTSC (or something else for PAL).  With an ancient Sony laptop I could set its TV output up to 1024x768 (although it was really only 480i).

---

