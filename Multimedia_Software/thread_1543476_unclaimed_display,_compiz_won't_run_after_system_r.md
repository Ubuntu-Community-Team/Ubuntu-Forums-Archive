---
title: "unclaimed display, compiz won't run after system restore"
date: 2010-08-01
forum: Multimedia Software
---

### Post by vangop on 2010-08-01
Hi,
I tarred my system (NVidia based) and restored it on 2 other different machines. (Intel g965 and SIS 661/741/760)
On both of them I see ```
$ sudo lshw -C display
  *-display UNCLAIMED     

```
As a result I can't enable compiz (visual effects), cairo dock is unusable (noGL version, GL won't run at all) - it shows a huge black rectangle as its background even when the dock is hidden.
I think the problem is that the video driver is not enabled, I need your help making it work.
After the restore during the 1st boot X complained that it can't find NVidia and showed me the options 
* use default settings
* generate new settings (I used this one)
So now one of the PCs:

```
$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
       resources: memory:c0000000-c7ffffff(prefetchable) memory:cfee0000-cfefffff ioport:ac00(size=128)

```

```
$ lsmod |grep sis
sis_agp                 4047  1 
i2c_sis96x              3024  0 
agpgart                31724  1 sis_agp
sis900                 17048  0 
mii                     4381  1 sis900

```

```
$ lspci 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0a.0 Communication controller: Conexant Systems, Inc. SoftV92 SpeakerPhone SoftRing Modem with SmartSP (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```
Do I need to reconfigure X? Or do something else to fix the graphics?

---

### Post by vangop on 2010-08-02
Any 1? Is it the problem that after the restore the system didn't catch the right modules/drivers or the X config is wrong? Do I need to reinstall or reconfig X?
How can I reconfigure the X server? Can I somehow make it configure the way it gets configured upon a fresh install?

---

