---
title: "Sony DV Firewire camera, does not play with Skype and Google+ Hangouts"
date: 2014-06-03
forum: Multimedia Software
---

### Post by Nick_Manolas on 2014-06-03
Hello everyone. I'm a Linux begginer and i've installed Ubuntu 14.04 32bit recently. Everything works fine but my Sony DV Firewire camera (DCR-PC330E PAL) which is not recognised in Skype and Google+ hangouts. The camera is only recognised with Kino.

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Fujitsu Technology Solutions Conexant softmodem SmartCP [1734:10ad]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] [8086:27c5] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
01:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1001]
    Kernel driver in use: iwl3945
07:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: e100
07:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: firewire_ohci
07:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: sdhci-pci
07:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: r592
07:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
    Subsystem: Fujitsu Technology Solutions Device [1734:10ad]
    Kernel driver in use: r852
```

```
nickman@laptop:~$ uname -r
3.13.0-27-generic
```

```
nickman@laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00f1 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
nickman@laptop:~$ sudo ln /dev/fw0 /dev/raw1394
[sudo] password for nickman: 
nickman@laptop:~$ sudo chmod 664 /dev/raw1394
nickman@laptop:~$ dvgrab
Found AV/C device with GUID 0x080046010436d379
libiec61883 error: Failed to get channels available.
Waiting for DV...
Capture Started

"dvgrab-001.dv": damaged frame near: timecode 45:85:85.45 date 2003.03.30 02:23:19
This means that there were missing or invalid FireWire packets.

"dvgrab-001.dv": damaged frame near: timecode 45:85:85.45 date 2003.03.30 02:23:57
This means that there were missing or invalid FireWire packets.

"dvgrab-001.dv": damaged frame near: timecode 45:85:85.45 date 2003.03.30 02:24:22
This means that there were missing or invalid FireWire packets.

"dvgrab-001.dv": damaged frame near: timecode 45:85:85.45 date 2003.03.30 02:25:00
This means that there were missing or invalid FireWire packets.
"dvgrab-001.dv":   999.89 MiB  7281 frames timecode 45:85:85.45 date 2003.03.30 02:25:44
Warning: 4 damaged frames.                                                      

"dvgrab-002.dv": damaged frame near: timecode 45:85:85.45 date 2003.03.30 02:27:23
This means that there were missing or invalid FireWire packets.

"dvgrab-002.dv": damaged frame near: timecode 45:85:85.45 date 2003.03.30 02:29:50
This means that there were missing or invalid FireWire packets.
"dvgrab-002.dv":   999.89 MiB  7281 frames timecode 45:85:85.45 date 2003.03.30 02:30:36
Warning: 2 damaged frames.
```

I would appreciate any help that could solve my problem, because using Skype or Google+ hangouts, is essential to me. Thank you all, very much for your time and effort.

Nick

---

