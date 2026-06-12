---
title: "Issues with GMA 950 (Intel 810) and widescreen monitor"
date: 2008-09-06
forum: Multimedia Software
---

### Post by Fallom on 2008-09-06
Hello everybody,

Ever since version 7 I've been having a boatload of trouble running Ubuntu on my laptop that usually sends me right back to Windows.

Here's my setup:

A Toshiba laptop with an Intel GMA 950 video chip hooked up via VGA to a 22" widescreen monitor.

This is apparently a hellish combination, since not only does the Intel chip not support the 1680x1050 native resolution off the bat, but the 915resolution fix doesn't seem to work anymore. No amount of tweaking xorg.conf enables that resolution.

In addition, the fact that I have a dual monitor setup seems to drive Ubuntu crazy. If I unplug the monitor, use my laptop alone, then plug the monitor back in it simply wipes out all the work I did getting the monitor running in the first place. Ubuntu doesn't handle this well at all. I've checked the design documents, and apparently I'm supposed to simply let Ubuntu handle the drivers and hope for the best. There isn't even a gui for changing drivers anymore, the updated intel driver specifically says it has poor support for 810 chipsets, and xorg.conf is a skeleton.

If anyone with a similar setup can offer me some words of advice I'd really appreciate. I'm just incredibly disappointed that what was working for me two years ago doesn't cut it anymore.

---

### Post by veloce on 2008-09-08
> **Fallom said:**
> 

A Toshiba laptop with an Intel GMA 950 video chip hooked up via VGA to a 22" widescreen monitor.


Have you tried xrandr?  I used it to get two monitors working quite nicely. There was even a script around that would update resolutions etc based on what was connected.

I only stopped using it because I found that I couldn't use 3d stuff with dual monitors (physical limit of 2048x2048 with my card.)

---

