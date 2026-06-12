---
title: "Fixing wireless: how to tell my card to use wl instead of ssb?"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by lsp432 on 2009-04-14
I had to reinstall my OS, and I need to get wireless working again. I remember vaguely what needs to be done, but not how to do it.

I remember the problem being that my ethernet card uses the Broadcom b44 driver (and the ssb module on which it depends), and my wireless card needs to use the wl driver, but instead tries to use b43 and ssb, which doesn't work at all with whatever my specific wireless card is.

I can blacklist b43 in /etc/modprobe.d/blacklist.conf, but I can't blacklist ssb because the ethernet card needs it, so I need some way to tell the wireless card to use wl instead of loading ssb.


The only idea I could come up with was to manually add a line for my wireless card to /etc/udev/rules.d/70-persistent-net.rules that named it "wifi0", then add go into /etc/modules and add "alias wifi0 wl", but that didn't work; I don't really know enough about linux to understand why. I was thinking that maybe if I could figure out the longer sort of numerical ID (on the order of the ones used in /lib/modules/2.6.28-11-generic/modules.alias) that corresponds to my wireless card, I could try using that in /etc/modules instead of wifi0?

Or maybe I have no idea what I'm doing. In either case, any help on how to make the card use wl instead of ssb would be much appreciated.

---

### Post by lsp432 on 2009-04-15
Okay, I'm adding this post because after several more hours searching for information and talking to people I know, I fixed my problem, and even though my finding the solution means this info is somewhere on the net already, I'll condense it here in case anyone else comes looking:

My situation appears to be unique to a small subset of computers, in this case notebooks using both a Broadcom wireless card with the 4328 chipset and a Broadcom ethernet card that uses the b44 (and therefore ssb) driver (for example, some Dell Inspirons and Vostros).

Also, before I discuss the fix, I've determined that even though the new wl (Broadcom STA) driver supports my chipset (I was using wl in the past), it doesn't do a very good job. I'd always been subject to data transfer stalls, poor speeds, disconnects, etc, and blamed my university's poor network, but while I was fixing my wireless tonight I tried and found out that ndiswrapper with the bcmwl5 driver blows the wl driver away; it's both faster and much more stable. Also, ndiswrapper didn't give me any grief, I just had to fix the ssb issue below and that's it, worked right away.

Anyway, since ssb apparently loads right from the kernel, I couldn't find a way to make it load after the ndiswrapper driver short of recompiling a custom kernel. The best way to fix the problem, then, was to use a script that will run on boot (like /etc/rc.local) to remove the ndiswrapper driver, wl, b44, and ssb from memory, then reload them in the proper order. Code to be added to rc.local before the "exit 0" line follows: 

modprobe -r ndiswrapper wl b44 ssb
modprobe ndiswrapper
modprobe b44
/etc/init.d/networking restart

That's it. I rebooted and everything works great. Thanks to anyone who gave this topic a view over trying to help out, and I hope somebody with my same problem finds this helpful.

---

