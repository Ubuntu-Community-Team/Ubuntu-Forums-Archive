---
title: "Screen Resolution bigger than actual display"
date: 2013-08-11
forum: Multimedia Software
---

### Post by chutchick on 2013-08-11
Good Day! I have been wrestling with this problem since last week. I am a fairly new Linux user and was impressed with its many features.

>I installed a ubuntu 13.04-64-bit alongside Windows 8.
>Can only go up to 1024x768 on my Display.
>My Monitor's native resolution is 1366x768 (Monitor is AOC 15'6'' LCD connected via VGA)
>Installed Nvidia drivers via sudo apt-get install nvidia-current (apt-get update and headers-generic command came b4)
>With the Nvidia drivers running, i can now go to 1360x768 on the display settings
HOWEVER: Here's the main problem for me:
Upon switching to 1360x768 via Settings / Nvidia Settings this is what happens.

[IMG]http://i41.tinypic.com/2la8t94.jpg[/IMG]
The black box represents the view from my monitor. Everything else is offscreen.

I have tried:
-Pressing the auto-adjust button on monitor
-Reset settings on Monitor
-Using nVidia drivers 304-310 and 313. (All the same result)

Additional Info:
-All Settings > Display shows my monitor as "Unknown"
-xrandr displays my connection as VGA-0
-nVidia labels my connection (in nvidia-settings) as CRT-0

I have also tried fiddling around with xorg.conf and xrandr --fb & xrandr modelines but all in vain.
Please help me PLEASE.

---

### Post by carlwsnyder on 2013-08-11
What is the output from xrandr on a line by itself in terminal?

---

### Post by chutchick on 2013-08-11
```

Screen 0: minimum 8 x 8, current 1024 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       59.8  
   800x600        60.3     56.2  
   640x480        59.9  
   320x240        60.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)

```

---

### Post by carlwsnyder on 2013-08-11
VGA-0 (that is a zero, not an O) is the correct designation for your display which is connected for modelines. ie.```
xrandr --newmode 1368x768   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA-0 1368x768
xrandr --output VGA-0 --mode 1368x768
```The results from before almost look like a 1024x600 box for your monitor.  I am hoping it is something like forgetting the correct polarity on your hsync/vsync settings at the end of the line.  You should be able to copy/paste the lines from the code box into your terminal to get them to run, as they are adapted from the screen mode shell script I use every session.

---

### Post by chutchick on 2013-08-12
First of all. Thank you for helping me. But it seems there's still more to be done.

```
xrandr --newmode 1368x768   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

```
This went ok. No errors of the sort.

```
xrandr --addmode VGA-0 1368x768

```
This however, produced this result:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30

```

---

### Post by carlwsnyder on 2013-09-07
Check with **xrandr** without any parameters, but the reported error usually means that you are trying to add a mode which already exists.  If that is the case, you can use your Settings menu >> Display to choose the correct setting.

---

### Post by tgalati4 on 2013-09-07
Try a different VGA cable.  There are 14 wires (one is typically not used) that send signals and that communicate to the PC what kind of monitor.  The fact that it comes up as "unknown" is a clue.  So the fallback/safety resolution for an "unknown" monitor is 1024by768.  If your cable is old, broken, or missing a few wires, then that would contribute to the lack of auto-detection.

---

