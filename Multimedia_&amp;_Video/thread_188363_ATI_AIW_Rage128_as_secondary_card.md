---
title: "ATI AIW Rage128 as secondary card"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by chrisost on 2006-06-04
I have two video cards in my machine: the first is a GeForce2 (AGP), the second a All-in-Wonder Rage128 (PCI).  I don't want a multi-monitor setup, only to enable TV tuning and capture on the AIW.

Perusing the GATOS site, I found reference to the V4L2 kernel modulue, which seemed to provide the functionality I need.  The documentation stated that the kernel module depended on X to initialize the card.

I created Screen entries in my xorg.conf for each card.  The GeForce card works just fine.  However, when starting X, I get an error reported that the V_BIOS could not be read on the AIW.  I tried with both the r128 driver and the vesa driver.  Both reported the same error; however the r128 driver caused X to fail while the vesa driver allowed X to start correctly. Regardless, the V4L2 module does not initialize correctly.

I have tried to find ways of enabling the TV tuner, without success.  All GATOS documentation refers to XFree86, and doesnt seem to work with Xorg.

How can I enable the TV tuner on an AIW Rage128 as a secondary card?

---

### Post by mantas on 2006-06-06
This module worked for me on ubuntu breezy with ATI all in wonder pro.
I'll try it with dapper at the end of the week (before WC :)))

---

### Post by chrisost on 2006-06-06
As I've been reading more, it seems that the problem may be due to Xorg 7.0 not correctly initializing the second video card.  I keep getting errors in my Xorg.0.log about not being able to read the V_BIOS, which seems to indicate that the card is not correctly initialized.  Can anyone confirm that this is a problem with Xorg?

edit: See this thread: [http://www.ubuntuforums.org/showthread.php?t=190547](http://www.ubuntuforums.org/showthread.php?t=190547)

---

