---
title: "Wrong resolution with multi monitors"
date: 2009-05-12
forum: Multimedia Software
---

### Post by publicv on 2009-05-12
Hi,

I have a laptop with a 1400x900 display.

After installation of 9.04 I connected an external display that is capable of 1920x1200 to it, and tried to use both monitors at the same time as well as only the external monitor by itself.

The problem is that I can only set it up for a maximum resolution of 1400x900 (like the lower resolution laptop display).

Under 8.10 it worked out of the box.

```
sudo xrandr -s 1920x1200
```
says
```
Size 1920x1200 not found in available modes
```

```
sudo xrandr -q
```
gives
```

Screen 0: minimum 320 x 200, current 1440 x 900, maximum 2880 x 900
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1440x900       59.9* 
   1280x800       59.8  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
LVDS connected (normal left inverted right x axis y axis)
   1440x900       60.2 +   59.9     40.2  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

Any idea what's going on?

---

