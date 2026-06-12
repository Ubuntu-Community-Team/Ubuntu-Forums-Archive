---
title: "ATI - S-video out"
date: 2011-01-24
forum: Multimedia Software
---

### Post by osoroco on 2011-01-24
Long time user, first time poster, registered and popping cherry on this post

Situation: trying to get S-Video out from ATI Radeon 4350 -with the fglrx driver- (ubuntu 10.10)
I've managed to get S-video out with the radeon driver, but the screen is sort of slanted and goes off the physical tv screen. If this can be corrected I'll go for the radeon driver. 

I've already been [here]("http://ubuntuforums.org/showthread.php?t=625435&page=4") and no luck. 

xrandr -q gives this: ```
root@media:~# xrandr -q 
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x720       60.0 +
   1280x960       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        60.0  
   640x480        75.0     60.0  
TV connected (normal left inverted right x axis y axis)
   1024x768       30.0 +
   800x600        30.0 +
   720x576        30.0 +
   720x480        30.0 +
   640x480        30.0 +
CV disconnected (normal left inverted right x axis y axis)
```

So it is being detected (in fact when I run the command the TV flickers a bit)

If I do xrandr --output/addmode/newmode with SVideo, S-Video, S-video, Svideo or svideo i get ```
warning: output Svideo not found; ignoring
```

However using TV I get: 
```
root@media:~# xrandr --output TV --mode 800x600 
xrandr: cannot find crtc for output TV
root@media:~# xrandr --addmode TV 800x600 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32

```

The catalyst control center doesn't let me enable the TV display (it appears grayed out)
The gnome-display-properties tool is also useless, after 'enabling' the tv-out, it asks me to log out/in but after doing so, nothing happens.

Any help is appreciated, and thanks in advanced.

---

