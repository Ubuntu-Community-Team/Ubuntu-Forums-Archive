---
title: "Linksys WMP54GS 64-bit driver (broadcom chipset) where?"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by terrant on 2009-04-06
OK, title pretty much says it all. I'm a Windows user currently beta'ing 7 (and kinda liking it) but I'd like to give Ubuntu a try. Right now my big gripe is networking.

I use a wirelesss router (linksys WRT54g) and wireless NIC (WMP54gs). I am curreently on a 32-bit OS, so natch I don't have the 64-bit drivers yet. That's fine. I can install them..

IF I can find them!

I know I have teh Broadcom chipset. Which accoring to every forum I've tried makes it insanely easy to find 64-bit drivers, even though linksys hasn't gotten around to making those themselves.

I went to Broadcom's website. None of the device/chipset IDs looked anything like min (4318) or the compatible list:
PCI\VEN_14E4&DEV_4318&REV_02
PCI\VEN_14E4&DEV_4318
PCI\VEN_14E4&CC_028000
PCI\VEN_14E4&CC_0280
PCI\VEN_14E4
PCI\CC_028000
PCI\CC_0280

Everywhere I go I here people posting "Oh if you have Broadcom, it's realy easy to get this to work" yet I can't seem to do so.

It doesn't help that I can't get online via ethernet in ubuntu for the same reason, but I can always boot into windows, find what I need, reboot into ubuntu, install the drivers, and call it a happy day. If, once again, I can find them.

So long story short, if anyone knows a sane place to get the drivers for my wireless NIC, I will be happy. I think Ubuntu's a cool idea and I want to give it a try, but after a full day of frustration over one driver I'm ready to uninstall. Honestly, Vista didn't give me this much of a headache!

---

### Post by Sam Lars on 2009-04-07
What version of Ubuntu are you using?
Also, how are you trying to install the drivers?  If you use the b43 driver in the kernel, you may have some luck.

---

