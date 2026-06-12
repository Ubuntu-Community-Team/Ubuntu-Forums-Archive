---
title: "Tri-Monitor Configuration - 2 cards"
date: 2011-02-19
forum: Multimedia Software
---

### Post by syntaxsniffer on 2011-02-19
Hello everyone!

I am attempting to setup a three-monitor setup on Ubuntu 10.10 (64-bit).

I have a built-in ATI graphics card that I have two monitors connected to (VGA and DVI) - they work wonderful.

Now here's the tricky part...
I added an NVidia GeForce 8400 GS to add a third monitor to the setup.  This monitor stays in power-save mode and does not act like it get's a signal.  If I let Ubuntu install the prop drivers for ATI or NVidia, I am left with only a terminal upon rebooting - I usually end up wiping the machine at that point and trying again with a fresh slate.

With the default clean install of Ubuntu 64-bit 10.10, I get all three monitors the two ATI's are mirrored and the NVidia has the purple background with the white ubuntu logo and the 5 red dots under it.

Does anyone have any idea what is going on here?  I am at a complete loss.

---

### Post by BicyclerBoy on 2011-02-20
Have never tried 2 cards the same type ...
Only suggestion is look in the output of running
dmesg

& look in log file
/var/log/Xorg.0.log

Maybe the xorg.conf needs the device sections to point to the right PCI id  & select the driver.

---

