---
title: "Add Screen Resolution"
date: 2011-11-11
forum: Multimedia Software
---

### Post by wilsondd on 2011-11-11
I've installed Ubuntu 11.10 and am enjoying it. However, everything (notifications, menus, etc) seemed larger than before. Its one of those small things that has been bothering me. So, I thought that maybe the resolution needed to be changed. "Displays" showed that I was already on the largest setting (1280x800). The computer is an HP Pavilion laptop and "System Info: Graphics" says that my driver is "Mobile Intel® GM45 Express Chipset".

I found instructions here on how to force-add a resolution:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

But, I get an error when I go to add the new mode. Any ideas? Here is the progression as I try to follow the instructions given to add a 1440x900 resolution.

Before doing anything, xrandr gives:
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```I run "cvt 1440 900" to copy off the second part and paste into the "--newmode" command next:
```

$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

``````

$ xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

``````

$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
  1440x900_60.00 (0xcc)  106.5MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz

``````

$ xrandr --addmode LVDS1 1440x900_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32

```

---

### Post by MoreOrLess on 2011-11-12
You can't make a resolution larger than your screen can handle. What model is the laptop?

---

### Post by wannabegeek on 2011-11-12
I believe you can scale the screen image up...it won't be native but may work for you.

See xrandr --scale

---

### Post by wilsondd on 2011-11-12
I have an HP dv5t-1000. If it isn't supposed to be changed, thats fine. The more I think about it, the more I think it isn't the resolution or anything. Maybe the sizes of some of the things were changed for 11.10 and I just need to get used to it.

---

### Post by wilsondd on 2011-11-12
Thanks for the suggestion. I tried it (xrandr --scale 1.125x1.125) and it did change. However, it was a bit fuzzy (as expected, I suppose) and the mouse couldn't travel across the whole screen.

Thanks anyways for the prompt reply.

---

### Post by pSYcl0Ne on 2012-01-03
I have a 1024x600 Netbook and 11.04

xrandr --fb 1024x600 --output LVDS1 --scale 1.25x1.25

was working perfect up until a recent update - which I assume is the same problem as with 11.10. As above, the mouse is now 'stuck' top left within the 1024x600 dimensions when the screen is outputting 1280x750. The right hand and bottom of the screens are out of range.

It was perfect before! Why'd they break it? :sadface

I am hoping there is some way to trick the desktop with some panning to get the old result back. Any ideas?

---

