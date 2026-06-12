---
title: "Sound is not working on my laptop"
date: 2008-10-30
forum: Multimedia Software
---

### Post by maven13 on 2008-10-30
Hi, After instalation, update i try to put some music on my laptop but it's not working. I am new in Ubuntu. Can some one help me i need sound every day

 Sorry for my English, iam polish

---

### Post by mdmarmer on 2008-10-30
We need to know the exact make and model of your laptop, and what sound card it has

Run this command in a terminal and post the results

lspci | grep -i audio

Sometimes this site is helpful [http://linux-laptop.net](http://linux-laptop.net)

Mike

---

### Post by maven13 on 2008-10-30
hi, 

Lspci
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
00:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
00:09.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
00:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
02:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```

This website isn't helpful for me my laptop is asus A9T

---

