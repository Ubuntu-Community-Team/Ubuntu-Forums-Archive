---
title: "Problem with youtube"
date: 2018-10-02
forum: Multimedia Software
---

### Post by albertodgar on 2018-10-02
[ATTACH=CONFIG]281234[/ATTACH] I have the problem that Youtube looks like in the picture so I can't press the widescreen button. Only after ctrl+ - and then ctrl + + it gets normal. Does anybody knows how to solve it?

---

### Post by Claus7 on 2018-10-04
Hello,

have you tried from your browser to reduce the fonts size and/or zoom level? This might fix your problem, since these shortcuts are responsible for the zoom level of your browser.

Regards!

---

### Post by albertodgar on 2018-10-09
oh I thought I had answered. Yes, after doing zoom out, it fit. But if I then put the zoom in the original way, it still fit untill I shut Mozilla Firefox. What I'd like is not to have to do this every time to fix the problem with normal zoom.

---

### Post by Autodave on 2018-10-09
Is this a laptop or desktop?  What video card are you using?  Did you install a driver for the video card? If so, what one and where did you get it from?

---

### Post by albertodgar on 2018-10-10
This is a laptop. The details for the video card I think are that:

lspci -vnn | grep VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 620 [8086:5916] (rev 02) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company HD Graphics 620 [103c:81ed]
    Flags: bus master, fast devsel, latency 0, IRQ 125
    Memory at a0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

I'm not sure if this is what you asked for. The dirvers I've installed are those who were installed with ubuntu.

---

### Post by Claus7 on 2018-10-11
Hello,

also please show the output of: xrandr -q

Regards!

---

### Post by albertodgar on 2018-10-11
xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768      60.00*+  40.00  
   1360x768      59.80    59.96  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
HDMI-1 disconnected (normal left inverted right x axis y axis)

Here it is.

---

### Post by albertodgar on 2018-10-11
Hello,

> **albertodgar said:**
> 
eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm


so, as already mentioned, you have a laptop where the laptop screen is called embedded display port style adapter (edp). 

> **albertodgar said:**
> 
   1366x768      60.00*+  40.00
  

The current mode, marked with a star (*) is the 1366x768 (widthxheight) at 60 Hz.
Is is also the preferred one since it is marked with a plus (+). So the monitor reports that preferred mode to the driver.

The available modes are the rest including:
> **albertodgar said:**
> 
   1360x768      59.80    59.96  
   

where the same resolution supports two different frequencies.

How about changing the mode with the following command:
```
xrandr --output eDP-1 --mode 1360x768 --rate 59.80
```

and check what happens?

In order to revert it back to the original one you should type:
```
xrandr --output eDP-1 --mode 1366x768 --rate 60.00
```

Regards!

It seems that it works. Thanks!!

Is it there a way to make the change permanent?

---

### Post by sasafrass452 on 2018-10-14
I'm having this issue, as well. Any way to fix it?

---

### Post by Claus7 on 2018-10-15
Hello,

you could create a resolution.sh file and add the line code in question. Save it under ~/Documents or anywhere else, just remember the place. Then open a terminal, navigate to the place that you have saved the file and change permissions by making it executable:
chmod 755 resolution.sh

Finally, go to the startup applications and add the file in the list.

Regards!

---

### Post by shantiq on 2018-10-17
NB:   a safer way to view YT videos is to play them away from the browser; it always more stable;   install mpv or use vlc

open terminal and enter:

```
 mpv [https://www.youtube.com/watch?v=u6lKkyCGy4A](https://www.youtube.com/watch?v=u6lKkyCGy4A)
```

or

```
 cvlc [https://www.youtube.com/watch?v=u6lKkyCGy4A](https://www.youtube.com/watch?v=u6lKkyCGy4A)
``` 

or VLC CTRL+V and enter URL


personally I almost never use browsers for vids as too many potential pitfalls

---

