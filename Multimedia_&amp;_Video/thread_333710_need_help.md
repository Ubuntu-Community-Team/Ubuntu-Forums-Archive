---
title: "need help"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by Doug11 on 2007-01-07
I tried to install one of the nvidia drivers but i think i installed the wrong one. I went to reboot but now my x server wont start up. What do I have to do ot uninstall the driver and reconfig x server so that I can start my graphical interaface again.

---

### Post by bigken on 2007-01-07
at the command prompt type sudo dpkg-reconfigure xserver-xorg select nvidia or nv as your driver and use the space bear to select your screen resolutions ;)

---

### Post by Doug11 on 2007-01-07
Is there a way to tell exactly which model my card is. Is supposed to be a 128MB by Nvidia but now I'm second guessing.

---

### Post by Canute on 2007-01-07
```
lspci
``` should do the trick.

---

### Post by bigken on 2007-01-08
you also take a look inside the pc or the makers web site and check the spec of your pc ;)

---

### Post by Doug11 on 2007-01-08
Have a laptop so not quite that easy. Here is the result of that command. Guess I found my answer. Reason being I wanted to try run Beryl, but it would display the splash screen for about 2 seconds then crash and go back to the login screen. Its SiS m760GX.



00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

---

### Post by bigken on 2007-01-08
just do a search sis video and beryl/compiz

---

