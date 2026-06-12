---
title: "Dual Monitor with Radeon Mobility X700"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by indy86 on 2008-03-17
Hi There,

I have installed Ubuntu 7.10 a couple of weeks ago on my Samsung X25 laptop. The laptop is equipped with a ATI Radeon Mobility X700 graphic card. 

I am trying to extend my desktop to a second screen which is my BenQ Monitor (FP91G+). I have tried it using the "Screens and Graphics" Option in Ubuntu, but i did not work out for me. After having read several posts on this issue, it seems that manually fixing the xorg.conf is the only option. However, I do have a lot experience with this. Is there anyone out who can help me?

Thanx for your help!

---

### Post by askreet on 2008-03-17
I, personally, opt for using xrandr rather than touching the configuration file.  I wrote a script which changes my configuration from the automatically-detected single screen on my laptop to a dual-screen configuration at work.  This may help you:

```
#!/bin/bash
xrandr --output TMDS-1 --mode 1680x1050
xrandr --output TMDS-1 --right-of LVDS

```

Output names (TMDS-1/LVDS) may vary and can be confirmed by running xrandr by itself at the command line.

---

### Post by indy86 on 2008-03-18
Hi,

I have tried xrandr in the meantime, but did not work out for X700. I managed to duplicate the desktop on my external BenQ screen, but the resolution does not fit, even if I set it correctly with xrandr. If I move the mouse beyond a certain point, Ubuntu just freezes.

This is what xrandr says:

Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1050
VGA-0 connected 1280x1024+0+0 (normal left inverted right) 0mm x 0mm
   1400x1050@60   60.0
   1400x1050      60.0
   1280x1024@60   60.0*
   1280x1024      60.0
   1280x960       60.0
   1280x960@60    60.0
   1280x800       60.0
   1280x768       60.0
   1024x768@60    60.0
   1024x768       60.0
   800x600@60     60.3
   800x600        60.3     56.2
   800x600@56     56.2
   640x480@60     60.0
LVDS connected 1400x1050+0+0 (normal left inverted right) 0mm x 0mm
   1400x1050      60.2*+
   1280x1024      59.9
   1280x960       59.9
   1280x800       60.0
   1280x768       60.0
   1024x768       60.0     59.9
   800x600        60.3     59.9
   640x480        59.9     59.4
S-video disconnected (normal left inverted right)
DVI-0 disconnected (normal left inverted right)

By the way, I am using the Radeon drivers, but observed the same behavior with the flgrx driver.

Any help is highly appreciated :)

---

