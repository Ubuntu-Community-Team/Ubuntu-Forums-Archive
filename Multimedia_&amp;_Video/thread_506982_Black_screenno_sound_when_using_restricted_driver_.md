---
title: "Black screen/no sound when using restricted driver for nvidia 6600AGP"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by srg on 2007-07-22
Hi,
I am completely new to Linux/Ubuntu.  After going through all the forum posts i have not been able to find a solution to using nvidia driver without getting black screen/no sound (drums) on reboot.

I would really appreciate if anyone can offer a solution or any advise on how to proceed to track down the cause of this?

So far I have tried installing the driver with the Restricted Driver Manager, Envy scripts and following the instructions downloading direct from Nvidia.com.  Each time the results were the same - Black screen/no sound when gdm starts

I went back to scratch, re-installed Fiesty Fawn and enabled nvidia driver in restricted driver manager.  Then based on what I could find in other similar posts I have tried the following..

Cleaned up Xorg.conf

Added to the screen section 
Option         "UseDisplayDevice" "DFP-0"
Option         "UseEDIDFreqs" "False"

Added to the monitor section the exact HorizSync and VertRefresh values for my Philips LCD

Tried adding Option "NvAGP" to the device section and explicity enabling and disabling it.

My motherboard is an Asus P4V800D-X with AGP and PCI Express slots
Primary graphics adapter is set in BIOS as AGP
Bios is the latest available.

Also tried setting AGP Mode 8X and 4X
AGP Fast Write Enabled and Disabled
AGP aperature size 128M and 64M

xorg.conf and Xorg.0.log attached from the failed boot.
I don't know if this is relevant or not by I see this line in the log file which looks odd considering it is an AGP card...

```
(II) NVIDIA(0): NVIDIA GPU GeForce Go 6600 GT at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.61.00
(II) NVIDIA(0): Detected PCI Express Link width: 8X
```

---

### Post by srg on 2007-07-24
Anyone give me a push in the right direction how I can further troubleshoot this?
It's frustrating that something that is trivial and just works in XP is quite a chore in Linux.

---

