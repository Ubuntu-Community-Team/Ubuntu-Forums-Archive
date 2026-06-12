---
title: "Blender problem with external monitor"
date: 2008-05-30
forum: Multimedia Software
---

### Post by jrutila on 2008-05-30
I'm facing problem using Blender (windowed and fullscreen) with external monitor.

My system:
ThinkPad X61 Tablet
Ubuntu 8.04 (Hardy) (running Gnome)

lspci:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

/var/log/Xorg.0.log:
```

(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so

```
-> So it is using intel

glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

blender:
```

Blender 2.45 (sub 0) Build

```

Now, when I use blender with my laptop screen (LVDS) it works flawlessly.
After I hook up my monitor (1920x1200) I do
```

xrandr --output VGA --auto
xrandr --output LVDS --off

```
When I start blender (with -w or without) it starts fine but the blender-window doesn't update. So it just shows the windows that were behind it when it started. If I resize the blender-window, it is updated and shows right. But when I try to do something with it (like Open...), it doesn't show the new "Open.."-panel. Moving the cursor over buttons shows the buttons under cursor.

This is quite annoying as I would like to do 3d with external monitor. Has anyone else encountered the same problem?

EDIT: I have narrowed the problem a little. Apparently this problem occurs only if the blender-window is located (even partly) outside the LVDS virtual screen (1400x1050), see below. So, my LVDS-display is off and if blender-window is bigger than 1400x1050, it won't work. Same happens with glxgears. When I move the glxgears-window outside the LVDS-area (1400x1050), gears stop running. It looks like the 3d memory (or something) is reserved only for the 1400x1050 area.

```

Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 1920 x 1400
VGA connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+   59.9  
   1600x1200      59.9  
   1680x1050      59.9  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1400x1050      50.0 +
   1280x1024      59.9  
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0     59.9  

```

Thank you.

---

