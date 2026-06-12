---
title: "Black screen when trying to access console - Nvidia broken, can't reinstall"
date: 2010-06-21
forum: Multimedia Software
---

### Post by The Bright Side on 2010-06-21
Hey guys,

yesteray, after I ran the Update Manager on Linux 64 with the latest updates - several pieces of software, but no new kernel, all my compiz effects were gone. When I tried to re-enable them, it behaved as if no driver was installed.

Nvidia-Settings still reports the latest stable driver (195.36.24) as installed and I can fully configure it, but actually have 3D effects on my desktop? Hellz no.

So I tried to boot into the console to reinstall the driver. My screen stays black when trying to use the console. I tried Recovery mode, typing "sudo service gdm stop" into the Gnome terminal, or hitting CTRL-ALT-F1 or CTRL-ALT-BACKSPACE in Gnome. Everything leads to a black screen - my computer can no longer display the console.

This blows... Any ideas what's going on? Everything used to work flawlessly, but since Canonical decided to implant that crappy unfinished Nouveau into Ubuntu, it's all messy. Since the drivers stopped working correctly, I also have choppy video when going full screen in Flash.

Graphics card: GeForce 6150SE nForce 430
Ubuntu: Lucid Lynx 64

Pleeeeaaaase help! :-(

Thanks!
M.

---

### Post by The Bright Side on 2010-06-21
I booted from my Live CD, which obviously runs Nouveau by default, and I was able to use the console. Any idea how I can put Nouveau back as the graphics driver in my system? Is it enough to just reinstall it via Synaptic and then un-blacklist it?

---

