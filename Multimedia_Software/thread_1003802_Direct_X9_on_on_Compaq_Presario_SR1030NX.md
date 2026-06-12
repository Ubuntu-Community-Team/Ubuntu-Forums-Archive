---
title: "Direct X9 on on Compaq Presario SR1030NX"
date: 2008-12-06
forum: Multimedia Software
---

### Post by eeverman on 2008-12-06
Hi - I am trying to get Direct X9 (DX9) working within Wine on Unbuntu 8.10.  I've really no idea what I'm doing, so please bear with me.

Back story:  I need to get Mavis Beacon Teaches Typing Platinum 20 (Win XP app which does reportedly work under Wine) for a friend, but it crashes on startup due to no DX9 support.

I ran [FONT="Fixedsys"]hwinfo --bridge[/FONT] and got this:

[FONT="Fixedsys"]
---------------------------------------------
desktop:~$ hwinfo --bridge
12: PCI 11.0: 0601 ISA bridge                                   
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3227
  Unique ID: 7EWs.ptQEkwKGKSD
  SysFS ID: /devices/pci0000:00/0000:00:11.0
  SysFS BusID: 0000:00:11.0
  Hardware Class: bridge
  Model: "VIA VT8237 ISA bridge [KT600/K8T800/K8T890 South]"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3227 "VT8237 ISA bridge [KT600/K8T800/K8T890 South]"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x80ed "A7V600/K8V-X/A8V Deluxe motherboard"
  Module Alias: "pci:v00001106d00003227sv00001043sd000080EDbc06sc01i00"
  Driver Info #0:
    Driver Status: i2c_viapro is active
    Driver Activation Cmd: "modprobe i2c_viapro"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 01.0: 0604 PCI bridge (Normal decode)
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_1106_b198
  Unique ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "VIA VT8237 PCI Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0xb198 "VT8237 PCI Bridge"
  Module Alias: "pci:v00001106d0000B198sv00000000sd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

24: PCI 00.0: 0600 Host bridge
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3205
  Unique ID: qLht.aHZVy30iOa8
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: bridge
  Model: "VIA VT8378 [KM400/A] Chipset Host Bridge"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3205 "VT8378 [KM400/A] Chipset Host Bridge"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8118 
  Driver: "agpgart-via"
  Driver Modules: "via_agp"
  Memory Range: 0xe0000000-0xe3ffffff (rw,prefetchable)
  Module Alias: "pci:v00001106d00003205sv00001043sd00008118bc06sc00i00"
  Driver Info #0:
    Driver Status: via_agp is active
    Driver Activation Cmd: "modprobe via_agp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
---------------------------------------------
[/FONT]

I did some searching, but could not find a driver that specifically matched the VIA chipset.  xorg.conf is basically empty - I know this is supposed to be configured, but... I've no idea where to start.  This is the relevant section I think:


[FONT="Fixedsys"]---------------------------------------------
Section "Device"
	Identifier	"Configured Video Device"
EndSection
---------------------------------------------[/FONT]

Um, somewhere a forum post also said this was relevant:

[FONT="Fixedsys"]---------------------------------------------
lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
---------------------------------------------[/FONT]


I would really appreciate some suggestions here - where do I start??

Thanks in advance for your help,

--ee

---

### Post by eeverman on 2008-12-06
I should probably mention that this computer has integrated VIA graphics....

---

