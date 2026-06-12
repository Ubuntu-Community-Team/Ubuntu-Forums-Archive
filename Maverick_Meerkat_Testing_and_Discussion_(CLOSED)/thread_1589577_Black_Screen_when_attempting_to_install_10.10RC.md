---
title: "Black Screen when attempting to install 10.10RC"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Uncle Spellbinder on 2010-10-06
Can't get past the initial dialogue on install of 10.10RC. Goes to black screen and I have to do a hard reboot. Same when I try using WUBI. My system recently had the video card (nVidia 9800GT) and the power source go out. Had them both replaced. I now have an ATI card. I'm going to assume this is a video card issue. Any ideas?


My current desktop specs...

HP Pavilion Elite M9360F(KQ499AA) 
Operating System - Windows Vista Home Premium 64-bit
Processor - Intel Core 2 Quad Q9300(2.50GHz)
Processor Main Features - 64 bit Quad-Core Processor
Cache Per Processor - 6MB L2 Cache
Memory - 8GB DDR2 800
Hard Drives - 2 x 500GB SATA 7200RPM
Optical Drive - Blu-ray player & SuperMulti DVD burner with LightScribe Technology drive
Graphics - ATI XFX Radeon 4650, with 512MB dedicated video memory (DirectX 10 ready).
Audio - Realtek Integrated High Definition Audio
Ethernet - Integrated 10/100/1000Mbps network interface
Wireless Card - Wireless LAN 802.11 b/g/n
NTSC TV tuner, over-the-air ATSC high-definition Digital TV tuner, and FM tuner
[Hauppauge WinTV HVR-1800 (Model 78xxx, Combo ATSC/QAM)]
HP Media Center remote control with IR (infrared) receiver

---

### Post by cariboo on 2010-10-06
Does it boot to a desktop, or does it stop at the plymouth logo?

If your system won't boot, press any key when you see the keyboard and the man at the bottom of the screen, to see the menu. Press F6 and select nomodeset. The press enter.

---

### Post by Uncle Spellbinder on 2010-10-06
Thanks, cariboo907. That did the trick. Still haven't installed yet though. 

What on earth happened to the installer??? I use to be able to click "use unallocated space" > "Install" > Done. Or "Install alongside Windows" > Use slider to determine space for Ubuntu > "Install" > Done. None of that seems available anymore. FAR more complicated than it should be. Seems like a MAJOR step back.

---

### Post by cariboo on 2010-10-06
There is a new version of the installer, there has been much teeth gnashing about the changes. There are still some things that need to be changed, but I think it's a little to late now. Hopefully the rest of our complaints will be addressed in the next release.

---

### Post by Uncle Spellbinder on 2010-10-06
So, until the next release, I need to do manual partitioning? Never been my strong suit. Maybe I'll just install 10.04 again and upgrade.

---

