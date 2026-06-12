---
title: "X/ACPI/PCI Problem"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by simonbonner on 2007-10-06
Hi Ubuntu-ers:

I'm having a strange problem with X/ACPI/PCI that I was hoping someone might be able to help with. This morning I was playing around with my webcam trying to get it to work -- no success yet. Along the way I installed several different drivers, the easycam2 package, and xawtv.

This afternoon I rebooted my computer, and suddenly Xorg seemed to be having troubles. The Nvidia driver complained that it couldn't start X, but it's been working fine for weeks. Switched back to the nv driver and it worked, but no mouse/erase/touchpad, no sound, wireless not detected, and warnings about cpu scaling not being available. 

This is occuring with kernel  2.6.20-16-generic, Luckily, I still have 2.6.20-15-generic, and it seems to work fine. I've compared the Xorg.0.log produced when I boot into both, and here are the results.

I've attached a file that pairs all of the differences in the log. The first difference is:

2.6.20-15: (II) Open ACPI successful (/var/run/acpid.socket)
2.6.10-16: (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
	(II) No APM support in BIOS or kernel

What does this mean?

Tried uninstalling everything I installed this morning, but to no avail.

System Infmation:
Dell Inspiron 8200
Intel P4M 1.7 GHz
NVIDIA GeForce 440 GO
Feisty Fawn 7.04


Any suggestions would be greatly appreciated.

Cheers,

Simon

---

### Post by nick_h on 2007-10-07
It looks like a problem with your restriced drivers.  Have you tried re-installing them?

---

