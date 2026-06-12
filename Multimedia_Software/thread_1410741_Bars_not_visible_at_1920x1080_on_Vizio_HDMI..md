---
title: "Bars not visible at 1920x1080 on Vizio HDMI."
date: 2010-02-19
forum: Multimedia Software
---

### Post by PinkFloyd102489 on 2010-02-19
Hello everyone!

Im using a Vizio 22" 1080p LCD HDTV has a monitor for my Ubuntu server over HDMI. It works great, except I cannot see the top or bottom bar at any resolution. Id really like to get it working at 1920x1080.

Any thoughts? Ive been tinkering with the xorg.conf a bit to no avail.

---

### Post by PinkFloyd102489 on 2010-02-21
Update: In addition to not being able to see the top or bottom, I cannot see the far left or far right sides either.

It's almost like the display is zoomed in a bit.

---

### Post by mcduck on 2010-02-22
Most likely the display *is* zoomed a bit. you'll have to change that from the *display's* options...

It's quite cpmmon that televisions use some level of zooming for HDMI inputs by default, because for normal television picture that often makes sense (just a leftover from the old CRT televisions where part of the CRT tube was always hidden from the viewer, so the picture couldn't use the full screen area).

Just check your display's options, and if you see anyhting zooming/scaling related then turn it off, and if you see anything like "pixel-perfect", "pixel-per-pixel" or similar then enable that. (The basic idea is to disable all image processing the display might do).

---

### Post by PinkFloyd102489 on 2010-02-24
> **mcduck said:**
> Most likely the display *is* zoomed a bit. you'll have to change that from the *display's* options...

It's quite cpmmon that televisions use some level of zooming for HDMI inputs by default, because for normal television picture that often makes sense (just a leftover from the old CRT televisions where part of the CRT tube was always hidden from the viewer, so the picture couldn't use the full screen area).

Just check your display's options, and if you see anyhting zooming/scaling related then turn it off, and if you see anything like "pixel-perfect", "pixel-per-pixel" or similar then enable that. (The basic idea is to disable all image processing the display might do).

I checked that and cannot find any thing in the HDMI options about zoom.

---

### Post by Dr Droid on 2010-02-24
This probably won't help any and I apologize for that but I have not even been able to get my Nvidia-Settings to detect my VIZIO 42" via HDMI on my HP Compaq 8510w. Vizio seems to not support many things either... For example I cannot find IR codes for their remotes and other things... Aside from that the VIZIO 42 is the best TV ive ever owned

---

### Post by efflandt on 2010-02-24
**xrandr** is used to test different modelines.  See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

**cvt** wasn't able to come up with a proper 1080p mode when I VGA connected my laptop, so grabbed this automatic mode from /var/log/Xorg.0.log of my DVI to HDMI connected desktop:

(II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)

Examples of commands used to set that in a script (and turn off laptop display (names of devices may vary for different video card/chips):

```
#!/bin/bash
xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output LVDS1 --off
xrandr --output VGA1 --mode 1920x1080_60.00
exit
```

---

