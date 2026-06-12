---
title: "Display on second monitor lags / glitches"
date: 2013-09-04
forum: Multimedia Software
---

### Post by tithemi on 2013-09-04
I'm running Lubuntu 13.04 on a Dell Latitude E6430 with a dell docking station and the second monitor is connected via DVI.
I have tried with the default Lubuntu install, Ubuntu-Desktop (Unity), Gnome Shell, and Classic Gnome. I've tried with lightdm and gdm.
They all result in the same issue. The second monitor will work, but it lags badly (ex: move the mouse cursor around the screen and it leaves a trail everywhere). 
If I turn on the option to have my mouse highlighted when I press ctrl, that will force the screen to refresh, but that is not a viable solution.

Here is the output from running `xrandr -q`:
```
$ xrandr -qScreen 0: minimum 320 x 200, current 2880 x 960, maximum 32767 x 32767
LVDS2 connected 1600x900+0+60 (normal left inverted right x axis y axis) 310mm x 174mm
   1600x900       60.0*+   40.0  
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA2 disconnected (normal left inverted right x axis y axis)
LVDS-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected 1280x960+1600+0 (normal left inverted right x axis y axis) 376mm x 300mm
   1280x1024      60.0 +   75.0  
   1280x960       60.0* 
   1152x921       66.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 disconnected (normal left inverted right x axis y axis)
  1024x768 (0x72)   65.0MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x73)   40.0MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x74)   36.0MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz



```

I've tried changing the refresh rate for the second monitor (DP-2) using this command: `xrandr -s 1280x960 -r 75` for example, but I get the following error:
```
$ xrandr -s 1280x960 -r 75
Size 1280x960 not found in available modes

```


I am not using any proprietary drivers either.


Any help would be appreciated. Thanks.

---

### Post by Bucky Ball on 2013-09-04
*Thread moved to **Multimedia & Video**.*

Welcome to the forums. You may have more luck here.

---

### Post by tithemi on 2013-09-04
Thanks Bucky Ball. I appreciate it.

Here is an update: A friend recommended I try installing Jockey. That has fixed the lag on the second monitor, for the most part (there is still a trail on the mouse, but only for a split second) and I can live with it now. However, now my mouse flickers constantly when on my primary (laptop) monitor.

Updated output from xrandr

```
$ xrandr -qScreen 0: minimum 320 x 200, current 2880 x 960, maximum 32767 x 32767
LVDS1 connected 1600x900+0+60 (normal left inverted right x axis y axis) 310mm x 174mm
   1600x900       60.0*+   40.0  
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS-2 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 connected 1280x960+1600+0 (normal left inverted right x axis y axis) 376mm x 300mm
   1280x1024      60.0 +   75.0  
   1280x960       60.0* 
   1152x921       66.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-2 disconnected (normal left inverted right x axis y axis)
  1024x768 (0x72)   65.0MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x73)   40.0MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x74)   36.0MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz

```

---

### Post by tithemi on 2013-09-04
Another update. After Running that xrandr command (just with -q flag, nothing else), I the lag came back on the second monitor and the mouse stopped flickering on the main monitor... This is really annoying!

---

