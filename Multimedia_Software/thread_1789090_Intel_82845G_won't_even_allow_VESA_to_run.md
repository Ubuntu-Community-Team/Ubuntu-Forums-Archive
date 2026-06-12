---
title: "Intel 82845G won't even allow VESA to run"
date: 2011-06-23
forum: Multimedia Software
---

### Post by jnwebster on 2011-06-23
I have a 7-year-old Dell Inspiron 1100 laptop that I'm trying to install Lubuntu 11.04 onto. Everything works fine except for the video driver. I cannot load the intel graphics driver nor the VESA driver. My display resolution is stuck at 640x480 in the top left corner of a 1024x768 screen and there are streaks of garbage on the bottom.
Here is the relevant info from lscpi:```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```
Here is the relevant info from xrandr -q:```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480         0.0* 

```
I've tried the suggestions at the links below, and they don't work.
[http://ubuntuforums.org/showthread.php?t=1729761]("http://ubuntuforums.org/showthread.php?t=1729761")
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus]("https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus")
And a few others. Here is the result of one attempt:
```
dennis@dennis-laptop:~$ xrandr --newmode "1024x768" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
dennis@dennis-laptop:~$ xrandr --addmode default 1024x768
xrandr: Failed to get size of gamma for output default
dennis@dennis-laptop:~$ xrandr --verbose --output default --mode 1024x768
xrandr: Failed to get size of gamma for output default
screen 0: 1024x768 270x203 mm  96.00dpi
crtc 0:     1024x768   59.9 +0+0 "default"
xrandr: Configure crtc 0 failed
crtc 0: disable
screen 0: revert
crtc 0: revert

```
Can anyone help me? Or at least point me in the right direction? I know there's probably some simple little change I could do to make it work, but I can't seem to find it through google searches.
I just want VESA to work so I can switch to native 1024x768 resolution.

---

### Post by cccc on 2011-07-18
> **jnwebster said:**
> 
Can anyone help me? Or at least point me in the right direction? I know there's probably some simple little change I could do to make it work, but I can't seem to find it through google searches.
I just want VESA to work so I can switch to native 1024x768 resolution.

Try this solution:

[http://ubuntuforums.org/showthread.php?t=1739646#7](http://ubuntuforums.org/showthread.php?t=1739646#7)

---

### Post by jnwebster on 2011-07-20
Thanks for the tip, but I eventually got it working using the advice from this thread:

[http://ubuntuforums.org/showpost.php?p=11014558&postcount=3](http://ubuntuforums.org/showpost.php?p=11014558&postcount=3)

I installed 'startup-manager' and set the resolution to 1024x768 and it works perfectly now.

---

