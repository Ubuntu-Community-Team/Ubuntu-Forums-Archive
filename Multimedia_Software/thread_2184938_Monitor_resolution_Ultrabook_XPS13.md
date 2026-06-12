---
title: "Monitor resolution Ultrabook XPS13"
date: 2013-10-31
forum: Multimedia Software
---

### Post by danone83 on 2013-10-31
Hi,

I have a brand new DELL Ultrabook XPS13 running Ubuntu 12.04 LTS (native). I found it weird that I cannot change the resolution of the monitor (via "Sytem settings" --> "Monitor"). It seems something is wrong with the drivers of the video card. Any idea?

Some more info:

```
daniele@dellino:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
```

---

### Post by carlwsnyder on 2013-10-31
Check to see if you have alternative resolutions set by using the terminal command **xrandr** on a line by itself, and post the output here if you need further help.  According to one article, the native resolution of your display is 1366x768 without the high-resolution option when you ordered the notebook, so you should be capable of displaying lower resolutions, just not any higher without an external display.

---

### Post by danone83 on 2013-10-31
```
daniele@dellino:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
   1920x1080      60.0*+   40.0  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
daniele@dellino:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
   1920x1080      60.0*+   40.0  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
daniele@dellino:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
   1920x1080      60.0*+   40.0  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

```

The only resoultion available from "System settings" ("Monitor") is 1920x1080. How can I change it?

---

### Post by carlwsnyder on 2013-10-31
See the Wiki @ [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) for a full explanation.

```
$ cvt 1280 720# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHzModeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
$ xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync # adds new resolution of 1280x720 at 60Hz vertical refresh
$ xrandr --addmode eDP1 1280x720_60       # adds new resolution to connected display
$ xrandr --output eDP1 --mode 1280x720_60    # sets connected display to new resolution
```Don't add the $, these indicate your Terminal prompt and don't add the # or any text following on the same line, as these are comments.

---

### Post by danone83 on 2013-11-01
Thanks a lot for your answer! It does work, but at the next system restart I get some error message saying "Impossible to apply the saved configuration for the monitor", followed by some explanation saying that "none of the selected modes was compatible with the possible modes (CRTC 63, CRTC 64 and CRTC 65)". In fact, the new resolution is not anymore available in the "System settings".

What does that mean? Is there a way to make the modification permanent?

---

### Post by danone83 on 2013-11-04
I looked more carefully at [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) and followed the instructions there to make changes via xrand persistent.

Thanks a lot for your help!

---

