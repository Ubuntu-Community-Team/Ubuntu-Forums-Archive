---
title: "happaauge tuner card causes x server to crash."
date: 2011-06-14
forum: Multimedia Software
---

### Post by underdog512 on 2011-06-14
I am trying to install a Hauppauge WinTV-HVR-1600 Tuner card in a custom built Mythbuntu 10.10 box which has an Nvidia GeForce 6200 pci graphics card installed.  

When the Tuner card is installed, x server will not start at all, stating that it is unable to load the drivers for the Nvidia card. When the tuner card is not installed, x server start without a problem. Really weird. 

Here is the output from lspci without the tuner card installed

```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 IDE interface: VIA Technologies, Inc. VT8251 AHCI/SATA 4-Port Controller
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8251 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8251 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8251 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
01:00.1 PCI bridge: VIA Technologies, Inc. VT8251 PCIE Root Port
04:0b.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:0b.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
05:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
```

Any ideas?

---

### Post by wolfen69 on 2011-06-14
Have you tried a different pci slot?

---

### Post by underdog512 on 2011-06-15
> **wolfen69 said:**
> Have you tried a different pci slot?

Just did.  No joy. I suspect that something may need to modified in xorg.conf but I am not sure what.

---

### Post by underdog512 on 2011-06-16
Bump

---

### Post by AntontheGreek on 2011-08-22
Very common problem with a cx18 card and NVidia Cards.

[http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)

this link showed me the way, still trying to get the damn thing to work in 11.04

Having trouble getting anything to display in mythTV

---

