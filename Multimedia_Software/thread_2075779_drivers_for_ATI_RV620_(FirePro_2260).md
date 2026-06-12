---
title: "drivers for ATI RV620 (FirePro 2260)"
date: 2012-10-24
forum: Multimedia Software
---

### Post by jamaas on 2012-10-24
I did an upgrade to 12.10 and for the life of me, can not now get the graphics drivers to work properly.  I have two screens but the settings only recognise them as a single "laptop" screen.

Also I have no "additional drivers" in the repositories.  

This is the graphics card I have.

lspci -nnk | grep -iA2 vga
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV620 [FirePro 2260] [1002:95cf]
	Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:2143]
	Kernel modules: radeon

I have tried installing drivers and still no luck.  Any suggestions about how to get additional drivers?

Thanks

J

---

### Post by purecharger on 2012-11-09
I have the exact same problem. The fglrx drivers do not work, with Xorg.log reporting module failed to load "noXfree86DRIExtension" and exiting with error. I finally managed to use, i believe, the open source Radeon drivers but I'm stuck at a "Laptop" display and resolution. Worked perfectly on 12.04. Once again I get burned by upgrading distributions.

---

### Post by QIII on 2012-11-09
You actually got burned by AMD/ATI.

That chipset is among those whose driver has now been branched to legacy support.  Unfortunately, that driver will not work with X Server 1.13, which Quantal uses.

No chipset prior to Cedar (HD 54xx) is supported by drivers that will work with X Server from here on out.  That means HD 2xxx - 4xxx are unsupported by AMD/ATI in any distro using X Server 1.13 or beyond.

AMD's website specifies that the driver for your card (using their search) is version 8.982.8.3, which will work up to Ubuntu 12.04.

---

### Post by purecharger on 2012-11-09
Thanks for your reply, I didn't realized support had been stopped. Guess thats what I get for having such a crap card.

---

### Post by QIII on 2012-11-09
Wasn't a crap workstation card when you got it, probably.

---

### Post by purecharger on 2012-11-09
Actually, it was. This desktop was purchased in February from Dell and despite my request to the contrary, the IT department configured it with this card. Thanks IT.

---

### Post by hirodavid on 2013-02-07
Sadly I can confirm that trying to install the driver from AMD will bork your X.

No solution found yet.

---

