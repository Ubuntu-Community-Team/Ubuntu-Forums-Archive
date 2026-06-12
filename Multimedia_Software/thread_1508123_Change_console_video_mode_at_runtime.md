---
title: "Change console video mode at runtime"
date: 2010-06-12
forum: Multimedia Software
---

### Post by BillRebey on 2010-06-12
I'm running 9.04 in console mode (no GUI), and I have GRUB set up to switch to 1600x1200 mode at when it boots the kernel.  This works great as long as a monitor is physically attached and turned on when the system boots.

However, when a monitor is not physically present at boot time, the video mode does not get switched to the desired mode, and when a monitor is attached later, I'm stuck with a 640x480 display (80x25 text).

This scenario happens quite regularly because I have a rack of Ubuntu boxes with an array of daisy-chained KVMs attached to them, and I'm doing power-fail testing, among other things.

How can I switch the console video mode at runtime, after the system is already up and running?

Alternatively, can I FORCE the desired video mode at boot time so that it is set whether a monitor is present or not?

---

