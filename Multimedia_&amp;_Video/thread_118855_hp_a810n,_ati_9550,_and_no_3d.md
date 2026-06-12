---
title: "hp a810n, ati 9550, and no 3d"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by john131971 on 2006-01-17
Hello one and all!

Have been playing around with this problem for weeks.
No matter what i try I haven't figured out how to turn 3d on
Starting to thinks it's a hardware problem, have started researching the motherboard in question.  Has on on-board video (sis 760) and the only option in bios is agp/onboard or pci.   I have tried both to no avail.

I have followed the how-to in regard to installing ati updated driver and still no 3d.

Not sure be have a feeling that the onboard video is being detected by kernel and causing a conflict with the ati card.   

lspci
[HTML]0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02 )
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media I O] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 90)
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS]: Unknown device 018 0 (rev 01)
0000:00:0a.0 Communication controller: Lucent Microelectronics V.92 56K WinModem  (rev 03)
0000:00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev 80)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 96 00]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Se condary)
[/HTML]

thanks

---

### Post by centered effect on 2006-06-02
I have a similar/almost exact issue with the exact system, but with a Nvidia card.  Did you ever get this resolved?

---

### Post by centered effect on 2006-06-03
I solved the problem using this thread:
[http://www.ubuntuforums.org/showthread.php?t=186294](http://www.ubuntuforums.org/showthread.php?t=186294)

---

### Post by john131971 on 2006-06-04
no go on 3d using ati...
my other machine with fx5200 card is working fine

I must need some serious hand holding for this one
remember error for log xitch about change to internal apg

In the future I will only buy hardware fully supported by linux.

thanks

---

