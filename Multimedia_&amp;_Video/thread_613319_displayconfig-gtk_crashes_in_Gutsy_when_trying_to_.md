---
title: "displayconfig-gtk crashes in Gutsy when trying to set up second monitor"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by MikeBenza on 2007-11-14
I'm trying to get my second monitor working with my Sony VAIO laptop in Gutsy.   The following shows up in lspci:

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```I've attached my dmesg output.

Here's the problem:
I go into System -> Administration -> Screens and Graphics.  It detects I have a second monitor, but it doesn't configure it.  I imported the configuration for my Optiquest Q19wb.  I set it up as a widescreen, with the native resolution.  I set it as an extension to the desktop and click Test.

If I'm lucky, the screen will go black and flicker a bit, the come back just in time to see the Screens and Graphics (displayconfig-gtk) window disappear.  But my second monitor is setup just as it was before -- a mirror of my desktop.

If I'm less lucky, the screen will go black and then it won't come back and I need to reset it with Alt+SysRq+REISUB.

If I'm even less lucky, the screen will go black and those keys won't do anything so I need to hold the power button to shut it down.

If I'm completely out of luck for the day, holding the power button won't even shut off the computer -- I need to remove the battery and pull the power out.



Which level of unluckiness seems random, though the most common is 
it completely locks up (no Alt+SysRq+REISUB) but the power button still works.  One time I clicked 'Ok' to apply the settings and all kinds of xorg things broke -- It started but in some sort of emergency resolution mode, and tons of applets didn't start.  I restored the xorg.conf backup, and rebooted and it came back (mostly) normal (I needed to restart again to make sure all the applets started).

What do I need to do to get my second monitor working?  What tools are there available to help diagnose the problem?

---

### Post by MikeBenza on 2007-11-18
Who do I even report the problem to?  Where can I send diagnostics?

---

