---
title: "Ubuntu 10.10 No sound."
date: 2010-12-15
forum: Multimedia Software
---

### Post by dslreports_snakeoil on 2010-12-15
I did a fresh install from 10.04 to 10.10. In 10.4 my sound was fine, now it's not.

uname -a:
Linux box 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

aplay -l:
aplay: device_list:235: no soundcards found...

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

 head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

Here is the lspci out put:
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
04:05.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

The hardware:
description: Desktop Computer
product: MS-7253
vendor: MICRO-STAR INTERNATIONAL CO., LTD
version: 1.00
width: 32 bits
capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
configuration: boot=normal chassis=desktop cpus=2
*-core
description: Motherboard
product: MS-7253
vendor: MICRO-STAR INTERNATIONAL CO., LTD
physical id: 0
version: 1.00
*-firmware
description: BIOS
vendor: Phoenix Technologies, LTD
physical id: 0
version: V1.2 (01/25/2007)
size: 128KiB
capacity: 448KiB
capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect sock
etedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5pr


product: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+

 *-multimedia UNCLAIMED
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress cap_list
          configuration: latency=0

When I look at my sound there is nothing listed in any of the following tabs:

Hardware, Input, Applications.

The out put tab has Dummy output listed.

The sound card is on board the mother board.

---

