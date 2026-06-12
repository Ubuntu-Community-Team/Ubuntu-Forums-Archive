---
title: "Firewire not configured?"
date: 2009-02-22
forum: Multimedia Software
---

### Post by POWMS on 2009-02-22
Hello
I have a fresh install of 8.10 on my laptop. I have installed Kdenlive and Kino (from Synaptic). When I plug in my DV camcorder, there is an error connecting to 'raw IEEE 1394'.
The firewire work fine thru Windows, which I don't have on the computer anymore.
lspci shows the firewire is there:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0b.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

Any suggestions?
Thanks.

---

### Post by ubuMike on 2009-09-22
I had the same problem. Try running kino as super user:

```
sudo kino
```

You can check here too:
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

---

