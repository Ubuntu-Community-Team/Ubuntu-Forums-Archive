---
title: "[Ubuntu (64-bit)] NVIDIA Drivers (v. 7676) not working"
date: 2005-12-01
forum: Multimedia &amp; Video
---

### Post by dadevilx on 2005-12-01
I have a problem with installing the NVIDIA Drivers (v. 7676) for my 7800GTX. I have installed the drivers following the guide on these forums, somewhere. It says: "Screens found, but none have a usable configuration". I only have this problem when I use the *nvidia* drivers, when I use the *nv* drivers it works fine.

Btw, I've only changed the #'s in front of *dri* and *GLcore*, monitor name and added the 1280x1024 resolution. The rest was auto-generated during the installation. Reinstalling Ubuntu had no effect.
*[SIZE="1"]note: same problem on the 32-bit version of Ubuntu[/SIZE]*

I've uploaded the configuration file and the logfile,
[removed]

> ***My specs:***
AMD Athlon 3800+
DFI LanParty Ultra-D
1024 MB RAM (TwinMOS)
XFX GeForce 7800GTX

Iiyama ProLite E431S-3

---

### Post by eobanb on 2005-12-01
7800 GTX, eh? I don't think that card's supported by Nvidia's Linux driver, which means you're probably stuck with nv for another month or so until their next version is released.  The Xorg log shows all the chipsets supported by the driver, and the 7800 isn't on there yet.

---

### Post by dadevilx on 2005-12-02
[QUOTE=eobanb]7800 GTX, eh? I don't think that card's supported by Nvidia's Linux driver, which means you're probably stuck with nv for another month or so until their next version is released.  The Xorg log shows all the chipsets supported by the driver, and the 7800 isn't on there yet.[/QUOTE]

And that's why a bug is fixed for that card, in the latest release (v. 7676)?

[QUOTE="nvidia.com"]Fixed GeForce 7800 GTX clocking problem that affected 3D performance.[/QUOTE]

No, it is supported. The GT is practicly the same, just running lower speeds (and some minor changes maybe). Even in some tutorial is mentioned that you have to install version 7676 with a 7800 card. 

I couldn't find any simular problem on the internet, but why does it say the screen configuration isn't usable? :confused:

*edit:*
I've found a simular problem @ nvnews.net. I'm going to read the forums, but I won't think it will help...

---

### Post by Stormbringer on 2005-12-02
[QUOTE=dadevilx]No, it is supported. The GT is practicly the same, just running lower speeds (and some minor changes maybe). Even in some tutorial is mentioned that you have to install version 7676 with a 7800 card. 
[/QUOTE]

Hello!

According to your Xorg.0.log, your card IS NOT supported by the installed driver!

```

(II) Primary Device is: PCI 05:00:0
(--) Chipset Unknown NVIDIA chip found

```

If you take a look at the output right above the forementioned lines you will see that there's no 7000 Series chipset listed.

```

(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro4 NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 280 NVS, Quadro4 380 XGL, Quadro NVS 50 PCI, GeForce4 448 Go,
	GeForce4 MX Integrated GPU, GeForce3, GeForce3 Ti 200,
	GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600, GeForce4 Ti 4400,
	0x0252, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, 0x0313, GeForce FX 5600SE,
	0x0316, 0x0317, GeForce FX Go5600, GeForce FX Go5650,
	Quadro FX Go700, 0x031D, 0x031E, 0x031F, GeForce FX 5200,
	GeForce FX 5200 Ultra, GeForce FX 5200, GeForce FX 5200SE,
	GeForce FX Go5200, GeForce FX Go5250, GeForce FX 5500,
	GeForce FX 5100, GeForce FX Go5200 32M/64M, 0x0329,
	Quadro NVS 280 PCI, Quadro FX 500/600 PCI, GeForce FX Go53xx Series,
	GeForce FX Go5100, 0x032F, GeForce FX 5900 Ultra, GeForce FX 5900,
	GeForce FX 5900XT, GeForce FX 5950 Ultra, Quadro FX 700,
	GeForce FX 5900ZT, Quadro FX 3000, GeForce FX 5700 Ultra,
	GeForce FX 5700, GeForce FX 5700LE, GeForce FX 5700VE, 0x0345,
	GeForce FX Go5700, GeForce FX Go5700, 0x0349, 0x034B,
	Quadro FX Go1000, Quadro FX 1100, 0x034F, GeForce 6800 Ultra,
	GeForce 6800, GeForce 6800 LE, 0x0043, GeForce 6800 GT, 0x0049,
	Quadro FX 4000, 0x00C0, GeForce 6800, GeForce 6800 LE,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400, 0x00CD,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, 0x0142, 0x0143,
	GeForce Go 6600, GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, 0x0147,
	GeForce Go 6600, 0x0149, 0x014B, 0x014C, 0x014D, Quadro FX 540,
	GeForce 6200, 0x0160, GeForce 6200 TurboCache(TM), 0x0162, 0x0163,
	GeForce Go 6200, 0x0163, GeForce Go 6250, GeForce Go 6200,
	GeForce Go 6250, 0x0169, 0x016B, 0x016C, 0x016D, 0x016E, 0x0210,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, 0x0220, 0x0221,
	0x0222, 0x0228

```

Sorry to tell you, but this driver will definitely not work with your card.

Either try to get a newer driver release or stick with Xorg's integrated "nv" driver until a compatible driver becomes available.

---

### Post by dadevilx on 2005-12-02
*oops*

I'd posted the wrong log file, the one with the nv driver. That's updated now, and it says "*(--) Chipset NVIDIA GPU found*", so, guess it *is* supported?

* trying again *

---

