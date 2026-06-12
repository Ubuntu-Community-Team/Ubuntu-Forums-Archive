---
title: "Dual Monitors in Jaunty"
date: 2009-04-23
forum: Multimedia Software
---

### Post by Devilotx on 2009-04-23
I'm having some serious issues getting dual monitors working in Jaunty, 

I've got an Nvidia Geforce 7950 GX2 card powering one display (sli in Windows, don't know about in Linux) and a Geforce 7300 to power the secondary display,

Ubuntu Jaunty doesn't even seem to notice the second card, the nvidia drivers show 2 7950's (which tells me it's not in SLI in Linux) but the 7300 just isn't there.

Not sure how to enable it, if it's even possible.

output of LSPCI

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
04:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
04:01.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
05:00.0 3D controller: nVidia Corporation G71 [GeForce 7950 GX2] (rev a1)
06:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GX2] (rev a1)
07:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
09:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

---

### Post by Almighty on 2009-04-24
Are you using the Nvidia drivers?

---

