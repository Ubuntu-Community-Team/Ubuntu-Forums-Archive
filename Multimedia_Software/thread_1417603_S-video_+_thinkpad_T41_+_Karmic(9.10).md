---
title: "S-video + thinkpad T41 + Karmic(9.10)"
date: 2010-02-27
forum: Multimedia Software
---

### Post by Siverback on 2010-02-27
I can't seem to figure out how to get the S-Video output working on my T41, and most of the info that I seem to be finding is for older versions before xrandr so files and settings don't seem to match:

Nutshell: I'm getting nothing.  Some suggestions are to reboot and you should at least get the display mirrored on whatever you have connected to the S-Video, I'm not even getting that.  The xrandr status reports:
 [INDENT]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
mark@bunny:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)
[/INDENT]I know that it's not a hardware/cable problem because this exact setup works fine under windows (even though there i'm working with a hacked video driver setup since one doesn't exist for any of the "modern" versions of windows, ati radeon 7500 (mobile))

Anyone know how to get this working/have ideas what to check/try?

Thanks...

---

### Post by Siverback on 2010-02-28
Ok, can someone at least tell me if I'm not getting an answer because no one knows, because it's something I should be able to find easily or something else???

thanks...

---

### Post by howwhi on 2010-03-04
Sorry, I can't help you with the S-video but I thought I would add my concerns here as well.  Recently acquired two different ThinkPad T41s from different sources.  Both are in very good, used, condition.  Tried to install Karmic on each of them.  Installs seem to go well enough; runs to completion.  After reboot, systems run for a couple of minutes and freeze up - HARD.  No lights (toggling caps lock), no camera and no action.

As I just got the second unit today, I hadn't thought it an O/S problem.  Now that I've seen two units do the same thing, I gotta ask:  What does Karmic have against ThinkPad T41s??

Just installed Xubuntu on one T41 and am installing "another" linux on the other as a test.

Howard

---

