---
title: "xorg: How can I default to a lower resolution than max at GDM startup?"
date: 2009-07-29
forum: Multimedia Software
---

### Post by toupeiro on 2009-07-29
I've been fiddling with this idea for the last hour and can't seem to get anywhere, but here is ultimately what I am trying to accomplish:

Lets say I have a monitor that supports every resolution available from 640x480 - 2560x1600 and I have every one of those modes in my xorg.conf  By default, GDM and Gnome seem to want to use the max available resolution, but I don't want it to use that resolution.  I want it to use 1600x1200 at GDM and by default in Gnome. If I want to scale up with xrandr, then I will do so, but every time X-windows starts, I want my default resolution to be lower, with the higher resolutions still selectable without restarting X.

 If I remove larger modes from xorg.conf, xrandr seems to lose the ability to scale back up to them, and since I cannot use xrandr at gdm, I need to figure out a way to make this work without interactivity.

Has anyone tried to do this before?

---

### Post by toupeiro on 2009-08-17
hopeful bump

---

