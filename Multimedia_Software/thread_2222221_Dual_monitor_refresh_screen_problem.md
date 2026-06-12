---
title: "Dual monitor refresh screen problem"
date: 2014-05-05
forum: Multimedia Software
---

### Post by Tiago_Pimentel on 2014-05-05
Good afternoon,

I have a problem with my second monitor. When I connect it to windows it works perfetly, but when I connect it to my ubuntu (same laptop) everytime the screen refreshes there is a bug in the screen and then it corrects (windows blink in the wrong place in the screen).

I have a samsung series 7 laptop with a radeon graphics card and a Samsung monitor connected to it through a DVI/hdmi cable (hdmi in the laptop side). When I only allow one window to show, or duplicate the display it works fine, only on extended display there is a problem.

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 2880 x 1024, maximum 8192 x 8192
LVDS1 connected 1600x900+1280+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1600x900       60.1*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 494mm x 320mm
   1680x1050      59.9 +
   1280x1024      75.0     60.0* 
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by darek3 on 2014-06-02
Hi,

maby try this [http://ubuntuforums.org/showthread.php?t=2167153](http://ubuntuforums.org/showthread.php?t=2167153)

---

