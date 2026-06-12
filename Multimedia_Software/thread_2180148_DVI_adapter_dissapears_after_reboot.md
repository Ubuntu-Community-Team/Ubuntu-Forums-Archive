---
title: "DVI adapter dissapears after reboot"
date: 2013-10-11
forum: Multimedia Software
---

### Post by ben-kessell on 2013-10-11
Hi All,

I'm using a T500 with the minidock and running Ubuntu 13.04. The dock provides multiple port extensions and that way I can use DVI for my second monitor. After some recent struggles getting my old windows partition mounted, a single line of edits to /etc/ftsab and a reboot: It's like the DVI adapter never existed. It was, literally, working a minute ago. What gives? Where did it go and why is the dock's VGA port working and not it's brother, the DVI?

Here's what xrandr shows
```

root@XCalibur ~# xrandr
Screen 0: minimum 320 x 200, current 3200 x 1528, maximum 32767 x 32767
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.2*+   50.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+1280+448 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       70.1     60.0  
   800x600        60.3     56.2  
   640x480        66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

---

