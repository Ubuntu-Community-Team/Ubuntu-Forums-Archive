---
title: "Dual Screen not working."
date: 2011-02-13
forum: Multimedia Software
---

### Post by WG- on 2011-02-13
Hello,

I have a slight difficult problem from which I can really determine what the problem is.

I have a laptop, toshiba portege m750 and a second monitor a 17 inch from Acer, an Acer Al1713.

When I plugin the cable and start my laptop the dualmonitor setup works...

When I haven't put in the cable in my laptop before I start my laptop the dualmonitor setup will not work. Putting the cable in and going to monitor preferences and turning the screen on does not work, the second screen stays blank. However I can "go" into the screen with my mouse.

Some facts:
- The dualmonitor setup works when the cable is plugged in before the laptop is started.
- The dualmonitor setup does not work when the cable is not plugged in before the laptop is started.
- The monitor preferences detects the second monitor, when the cable is being attached after the laptop is started.
- When the dualmonitor is being setup by the monitor preferences after the cable is being attached I could still 'go' in the screen with my mouse. 

Futhermore my laptop has a Intel GMA 4500MHD video card. I have a resolution of 1280x800 on my laptop, 1280x1024 on my second monitor.

Any one can help me tackle this problem?

---

### Post by mr_luksom on 2011-02-13
After putting your video cable in before startup, can you open a terminal and post the output of:
```

xrandr

```

Also for after startup?

---

### Post by WG- on 2011-02-13
Computer is started without cable...
- xrandr without cable
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)

```

-xrandr with cable
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      75.0     60.0* 
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)

```

The xrandr when the cable is already connected to the laptop before startup you get tomorrow.

---

### Post by mr_luksom on 2011-02-13
It appears both your graphics card and linux are picking up the monitor, it just isn't setting the mode. It won't be a permanent fix, but try this to see if you get any response from the monitor (leave it unplugged from startup and connect it later)

```

xrandr --output VGA1 --mode 1024x768

```

You can substitute a different mode from the xrandr list if your monitor doesn't like it.

If that works, we just need to make it permanent.

---

### Post by WG- on 2011-02-14
Okay I gonne try that in a second.  For now the code when the cable is connected before startup...

xrandr
```
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      75.0     60.0* 
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)

```

when cable is the disconnected:
```
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by WG- on 2011-02-14
> **mr_luksom said:**
> It appears both your graphics card and linux are picking up the monitor, it just isn't setting the mode. It won't be a permanent fix, but try this to see if you get any response from the monitor (leave it unplugged from startup and connect it later)

```

xrandr --output VGA1 --mode 1024x768

```

You can substitute a different mode from the xrandr list if your monitor doesn't like it.

If that works, we just need to make it permanent.

It didn't work. The screen stays black. Turning the screen on/off or disconnecting/connecting the cable doesn't work either.

---

