---
title: "VGA works, DVI does not, same monitor"
date: 2009-04-27
forum: Multimedia Software
---

### Post by mikesmithv on 2009-04-27
I was hoping this would be fixed in Jaunty but it was not.  My monitor has both VGA and DVI inputs but I am force to use the VGA for Ubuntu (Windows works fine with DVI).  Here is what xrandr reports when VGA input is used:

```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1453 x 1800
VGA connected (normal left inverted right x axis y axis)
   1440x900       59.9 +   75.0     59.9  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 370mm x 230mm
   1440x900       59.9*+   59.9  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
```

This is what xrandr reports when DVI input is used:

```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1453 x 1800
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 370mm x 230mm
   1440x900       59.9*+   59.9  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
```

The monitor is a Dell SE198WFP 19-inch Widescreen and the video chip is Intel 945GM.  Does anyone know why the same monitor would be treated differently or how I can fix this?

---

