---
title: "External display - Play movies without need to extend desktop"
date: 2008-11-08
forum: Multimedia Software
---

### Post by Plnt on 2008-11-08
Hi,

I'm using HP Compaq 2510p notebook (Intel GM965/GL960 graphics card) with connected VGA output.

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2960 x 1850
VGA connected (normal left inverted right x axis y axis)
   1680x1050      60.0 +   60.0
   1600x1200      59.9
   1280x1024      75.0     59.9
   1440x900       59.9
   1280x960       59.9
   1152x864       74.8
   1024x768       75.1     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     66.7     60.0
   720x400        70.1
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+   60.0
   1280x768       60.0
   1024x768       60.0
   800x600        60.3
   640x480        59.9
TV disconnected (normal left inverted right x axis y axis)
```

I'd like to use 1280x800 resolution on my internal notebook display (LVDS) and play movies on external VGA display with 1680x1050 resolution. The problem is that if I try to enable VGA external output with xrandr, it clones the current display or extend the desktop with VGA output. In both cases the main resolution is at least 1680x1050 which means that I can't see some parts of the desktop on my LVDS internal display.

I'd like to start mplayer, VLC or some other multimedia player to play movies on the external VGA display without touching the desktop settings. Is there some way how to do that?

Thanks

---

