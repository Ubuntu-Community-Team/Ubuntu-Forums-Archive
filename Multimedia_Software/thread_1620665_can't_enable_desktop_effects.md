---
title: "can't enable desktop effects"
date: 2010-11-13
forum: Multimedia Software
---

### Post by sinnerz2000 on 2010-11-13
i am not able to enable desktop effects, my computer config is amd64 3000+ cpu and a 1.5gb ddr2 ram and no graphic card. compiz check detects software mode, how to enable opengl?

---

### Post by gordintoronto on 2010-11-13
You have a graphics adapter, probably on the motherboard. Run Accessories/Terminal and enter the command: lspci

The line which includes the word "VGA" identifies your graphics adapter. In Ubuntu 10.10, you can go to System/Administration/Additional Drivers. Perhaps Ubuntu will offer to install a driver for your video adapter. If not, you can't get "desktop effects." They don't add anything useful to your computer, they just include some "eye candy."

---

### Post by realzippy on 2010-11-13
You can paste into terminal:
```
lspci |grep VGA
```
to get your graphics adapter line directly.If it is an ATI,you might run basic desktop effects,since the "free" ATI driver is pretty good.
*If* desktop effects are useful,is a different discussion ;*my* Cube is ;-),but
most spices in a good dinner also are not useful.

---

### Post by sinnerz2000 on 2010-11-13
> **realzippy said:**
> You can paste into terminal:
```
lspci |grep VGA
```
to get your graphics adapter line directly.If it is an ATI,you might run basic desktop effects,since the "free" ATI driver is pretty good.
*If* desktop effects are useful,is a different discussion ;*my* Cube is ;-),but
most spices in a good dinner also are not useful.

this is what i get ```
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
```
ubuntu is not offering any display drivers
and compiz-check says this
```
Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use 
```

---

### Post by wojox on 2010-11-13
Worth a shot [OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

---

### Post by sinnerz2000 on 2010-11-13
> **wojox said:**
> Worth a shot [OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

which do u think will work from these?

---

### Post by Yellow Pasque on 2010-11-13
VIA chipset = don't bother trying to get 3D acceleration in Linux
Get a graphics card if you need 3D.

---

### Post by realzippy on 2010-11-14
> **sinnerz2000 said:**
> which do u think will work from these?

None.The new VIA beta driver unfortunately is not for your graphics device.
So,as suggested,you will need a graphics card;suggest some cheap nvidia,even
an old used GT 6600 e.g. will perform great in desktop effects...

---

### Post by sinnerz2000 on 2010-11-14
thanks everyone for help, i'll try to get my nvidia 7300le working again and i'll try it then.

---

