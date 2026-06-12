---
title: "Can't boot: conflict with integrated graphics and nVidia card"
date: 2008-08-08
forum: Multimedia Software
---

### Post by jonathanmotes on 2008-08-08
Does anyone know how to fix this? The Hardy live disc will not work if the card is plugged into the motherboard (It hangs about 1/3 way through the bootup process). The integrated graphics is Intel 845G and the graphics card is an nVidia GeForce FX 5500.The card works fine with Windows XP, however.

Please help!

---

### Post by Anlace on 2008-08-08
Greetings,

Make sure that the integrated graphics is disabled in BIOS.

It would also be a good idea to make sure that your motherboard has the latest version of BIOS as well though you'll probably need Windows, or access to a Windows computer, and a floppy drive to make the flash disc.  Check your motherboard's manufacturer web site for the update.

---

### Post by jonathanmotes on 2008-08-08
Thanks for the reply! I will try that. But, is there a way to make them both work - so that I can have cloned screens - or hopefully (with proper xorg.conf configuration) have one screen extend the other?

---

### Post by Anlace on 2008-08-09
I don't know the answer to that one . . . . good luck with it though, I'm sure someone has got it working at some point!

---

### Post by elcid89 on 2008-08-09
> **jonathanmotes said:**
> Does anyone know how to fix this? The Hardy live disc will not work if the card is plugged into the motherboard (It hangs about 1/3 way through the bootup process). The integrated graphics is Intel 845G and the graphics card is an nVidia GeForce FX 5500.The card works fine with Windows XP, however.

Please help!

I found that the drivers in my case were conflicting. I have a Dell GX270, onboard Intel Extreme Graphics (i82875) and an ATI HD2400 in the AGP slot. 

There's no way in the BIOS to disable the onboard video. You can select AGP as primary, but BIOS loads them both anyway, and Ubuntu therefore sees them both and loads both drivers.

I ended up removing the Intel driver (xserver-xorg-video-intel) to get it to work correctly. As long as that driver was present, ATI refused to load and MESA came up consistently in fglrxinfo. Once it was removed, *pouf* instant joy.

---

