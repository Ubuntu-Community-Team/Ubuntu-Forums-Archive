---
title: "System lockup"
date: 2010-08-08
forum: Multimedia Software
---

### Post by 4x4_Welder on 2010-08-08
I have been running into an odd problem with 10.04-  After running around on the web for a while, the screen will suddenly freeze, first in the center and then the whole thing.  If I catch it quick, I can restart the computer but usually there is a pretty quick progression.  The odd part is that the cursor still moves just fine.  
In the searching I have done, it seems to be related to nvidia drivers, but I am running a Compaq Presario with onboard video.  The hardware of this computer has given me a lot of trouble off and on, with a defective motherboard and CPU but those have since been replaced.  
Is there a recommended video card to work around this?

---

### Post by walterav on 2010-08-08
> **4x4_Welder said:**
> I have been running into an odd problem with 10.04-  After running around on the web for a while, the screen will suddenly freeze, first in the center and then the whole thing.  If I catch it quick, I can restart the computer but usually there is a pretty quick progression.  The odd part is that the cursor still moves just fine.  
In the searching I have done, it seems to be related to nvidia drivers, but I am running a Compaq Presario with onboard video.  The hardware of this computer has given me a lot of trouble off and on, with a defective motherboard and CPU but those have since been replaced.  
Is there a recommended video card to work around this?

Hi, could you post(copy/paste) the output of the following terminal command:
```
lspci
```
With that info we know a little more about your PC.

BTW is the machine getting hot (temperature)?

---

### Post by 4x4_Welder on 2010-08-08
Output:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

I have a Sabrent wireless card that I normally use as well.  

I do not think the computer is getting hot, it doesn't seem to be reliant on temperature although it has been in the upper 80s-90s here the last few weeks.  The case fan and CPU fan operate normally.

---

### Post by 4x4_Welder on 2010-08-09
I did add on a CPU temperature monitor after the last post-  Constant 40c/104F.  I'll tomorrow if the monitor is wrong or if it's really that steady of a temp.

---

### Post by 4x4_Welder on 2010-08-12
Ok, temp monitor is wrong and this does seem to be temp related as it isn't locking up at night when it's cooler.
Is there a way to kick the fans on to high speed constantly?  I like that it's quiet, but I'd rather have a computer that works.

---

