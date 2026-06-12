---
title: "Can't Run Compiz on 8.10"
date: 2009-07-09
forum: Multimedia Software
---

### Post by mcland on 2009-07-09
I can't get compiz to work on my Intrepid install.  I just installed a "new" graphics card.  It's a Quadro FX 3000 (not top of the line but all I could get my hands on work).

I'm running the 173 driver.  

Here's the info on the card from lspci:

01:00.0 VGA compatible controller: nVidia Corporation NV35GL [Quadro FX 3000] (rev a1)
	Subsystem: nVidia Corporation Device 01c9
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at f5fe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia


I found this program compiz-check in another forum and tried and this is the result:

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV35GL [Quadro FX 3000] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

I had some problems getting the driver installed, but it seems to be installed correctly.  Is this a problem or limitation with my card, or is this a driver problem?

---

### Post by rainwalker on 2009-07-09
I have a Quadro FX 3700 in my laptop, and it works fine with the v180 driver in the Restricted Drivers Manager or the v185 driver that I compiled according to [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

