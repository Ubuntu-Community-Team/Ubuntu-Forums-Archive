---
title: "Kernel Segfault from a SCREENSAVER??"
date: 2009-11-28
forum: Multimedia Software
---

### Post by SuperMike on 2009-11-28
Today my mouse didn't work after returning to my desktop with CTRL+ALT+F7. The hard drive was churning, so I waited a moment. Finally my desktop went black and then back to normal again. I checked my event logs and found this:

Nov 28 08:02:08 supermike kernel: [957885.054529] gnome-screensav[14983]: segfault at 00000350 eip b6e22885 esp bfe2d540 error 4
Nov 28 08:03:05 supermike kernel: [957912.899343] gnome-screensav[21344]: segfault at 00000350 eip b6df8885 esp bf8048e0 error 4

I guess I'm lucky it didn't completely bonk up my workstation that I would have to reboot.

(I'm on Ubuntu 8.04 right now.)

Anyway, the big question I had was who had the bright idea to stick the screensaver at the kernel level instead of the user level? I mean, is it really worth it to give it that kind of escalation? No one likes to know that it was the screensaver that caused their workstation to crash. I mean, that's what we would expect from Windows, not Linux.

---

