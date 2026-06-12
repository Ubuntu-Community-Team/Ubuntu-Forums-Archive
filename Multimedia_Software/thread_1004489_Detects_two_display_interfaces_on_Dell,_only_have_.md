---
title: "Detects two display interfaces on Dell, only have one."
date: 2008-12-07
forum: Multimedia Software
---

### Post by Andy-N on 2008-12-07
Hi there,

I'm running a fresh install of Ubuntu 8.10 on a Dell GX620 Optiplex. It has one DVI output on the back connected to DVI to VGA dongle to a 17" SONY flatscreen monitor.

I've previously had this setup running Windows XP at a resolution of 1280x1024 and would like this resolution again.

However when I run "Screen Resolution" I see two monitors attached (there's only one). I can only see what's on "Unknown" which shows me a limited list of resolutions to choose from, whereas "SONY 17" shows the list I would expect. But setting "Unknown" to "Off" and "SONY 17" to some resolution causes my monitor to turn off.

Here's some output from various things in the hope it might aid diagnosis:

xrandr:

```

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 2432 x 1024
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   60.0     60.0  
   1600x1024      60.2  
   1440x900       59.9  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        60.0     59.9  
   720x400        70.1  

```

lspci (relevant parts)

```

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
0

```

Any thoughts/help/suggestions would be greatly appreciated.

---

