---
title: "how to enable internal DVB-T tv tuner"
date: 2010-12-31
forum: Multimedia Software
---

### Post by JaJaBinks on 2010-12-31
Hello and welcome to 2011
I have just installed ubuntu 10.10 as dual boot with windows 7 on a new desktop computer with an internal DVB-T tv tuner.

attempts thus far to enable the device have been fruitless.

after much research, i installed MythTV, but the installation of the backend stalled at the capture card setup which will not allow me to enter a DVB Device number.

I then installed TVtime but when i run TVtime television viewer, it flashes a screen very briefly and does nothing else.

I am assuming my problem is to do with a driver for the device, but have not yet been able to locate one.

I checked linuxtv but no luck

any help would be appreciated - thanks

following is output from 'lspci -vmm'

                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 10236MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: BD  B  DH8E2L
                vendor: hp
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 8HD9
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller [8086:3B30]
             vendor: Intel Corporation [8086]
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fb0ff800-fb0ff8ff ioport:400(size=32)
     *-scsi:0
          physical id: 5
          bus info: usb@2:1.1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             size: 244MiB (255MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=f4baf4ba
           *-volume
                description: Windows FAT volume
                vendor: ,O6*mIHC
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/KINGSTON
                version: FAT16
                serial: b6da-7e1e
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 6
          bus info: usb@2:1.2
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdc
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=8f9c798a
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 2
                bus info: scsi@7:0.0.0,2
                logical name: /dev/sdc2
                logical name: /media/WDEXTHD
                version: FAT32
                serial: 7cb0-df74
                size: 74GiB
                capacity: 74GiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:2
          physical id: 7
          bus info: usb@2:1.3
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdd
             size: 7632MiB (8002MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=c3072e18
           *-volume
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 1
                bus info: scsi@8:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/TSB USB DRV
                version: FAT32
                serial: 063a-5da9
                size: 7621MiB
                capacity: 7628MiB
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=TSB USB DRV mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:3
          physical id: 8
          bus info: usb@2:1.7
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sde
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@9:0.0.1
             logical name: /dev/sdf
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@9:0.0.2
             logical name: /dev/sdg
        *-disk:3
             description: SCSI Disk
             product: MS/MS-Pro
             vendor: Generic-
             physical id: 0.0.3
             bus info: scsi@9:0.0.3
             logical name: /dev/sdh
             version: 1.03
             serial: 3
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdh
  *-power UNCLAIMED
       product: Standard Efficiency
       physical id: 1
       capacity: 32768mWh
stephen@HPE-377a:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood PRO [Radeon HD 5500 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
04:00.0 Multimedia controller: Philips Semiconductors Device 7231 (rev ca)
05:00.0 Network controller: RaLink RT3092 Wireless 802.11n 2T/2R PCIe
stephen@HPE-377a:~$ lsmultimedia
lsmultimedia: command not found
stephen@HPE-377a:~$ lspci -t
-[0000:00]-+-00.0
           +-03.0-[01]--+-00.0
           |            \-00.1
           +-08.0
           +-08.1
           +-08.2
           +-08.3
           +-10.0
           +-10.1
           +-16.0
           +-1a.0
           +-1b.0
           +-1c.0-[02]----00.0
           +-1c.2-[03]----00.0
           +-1c.3-[04]----00.0
           +-1c.5-[05]----00.0
           +-1d.0
           +-1e.0-[06]--
           +-1f.0
           +-1f.2
           \-1f.3
stephen@HPE-377a:~$ lspci -n
00:00.0 0600: 8086:d131 (rev 11)
00:03.0 0604: 8086:d138 (rev 11)
00:08.0 0880: 8086:d155 (rev 11)
00:08.1 0880: 8086:d156 (rev 11)
00:08.2 0880: 8086:d157 (rev 11)
00:08.3 0880: 8086:d158 (rev 11)
00:10.0 0880: 8086:d150 (rev 11)
00:10.1 0880: 8086:d151 (rev 11)
00:16.0 0780: 8086:3b64 (rev 06)
00:1a.0 0c03: 8086:3b3c (rev 06)
00:1b.0 0403: 8086:3b56 (rev 06)
00:1c.0 0604: 8086:3b42 (rev 06)
00:1c.2 0604: 8086:3b46 (rev 06)
00:1c.3 0604: 8086:3b48 (rev 06)
00:1c.5 0604: 8086:3b4c (rev 06)
00:1d.0 0c03: 8086:3b34 (rev 06)
00:1e.0 0604: 8086:244e (rev a6)
00:1f.0 0601: 8086:3b08 (rev 06)
00:1f.2 0104: 8086:2822 (rev 06)
00:1f.3 0c05: 8086:3b30 (rev 06)
01:00.0 0300: 1002:68d9
01:00.1 0403: 1002:aa60
02:00.0 0200: 10ec:8168 (rev 03)
03:00.0 0c00: 1106:3403
04:00.0 0480: 1131:7231 (rev ca)
05:00.0 0280: 1814:3092
stephen@HPE-377a:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d131] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b08] (rev 06)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood PRO [Radeon HD 5500 Series] [1002:68d9]
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:00.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6315 Series Firewire Controller [1106:3403]
04:00.0 Multimedia controller [0480]: Philips Semiconductors Device [1131:7231] (rev ca)
05:00.0 Network controller [0280]: RaLink RT3092 Wireless 802.11n 2T/2R PCIe [1814:3092]
stephen@HPE-377a:~$ lspci -vmm
Slot:	00:00.0
Class:	Host bridge
Vendor:	Intel Corporation
Device:	Core Processor DMI
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	11

Slot:	00:03.0
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	Core Processor PCI Express Root Port 1
Rev:	11

Slot:	00:08.0
Class:	System peripheral
Vendor:	Intel Corporation
Device:	Core Processor System Management Registers
SVendor:	Unknown vendor 003c
SDevice:	Device 009c
Rev:	11

Slot:	00:08.1
Class:	System peripheral
Vendor:	Intel Corporation
Device:	Core Processor Semaphore and Scratchpad Registers
SVendor:	Unknown vendor 003c
SDevice:	Device 009c
Rev:	11

Slot:	00:08.2
Class:	System peripheral
Vendor:	Intel Corporation
Device:	Core Processor System Control and Status Registers
SVendor:	Unknown vendor 003c
SDevice:	Device 009c
Rev:	11

Slot:	00:08.3
Class:	System peripheral
Vendor:	Intel Corporation
Device:	Core Processor Miscellaneous Registers
SVendor:	Unknown vendor 003c
SDevice:	Device 009c
Rev:	11

Slot:	00:10.0
Class:	System peripheral
Vendor:	Intel Corporation
Device:	Core Processor QPI Link
SVendor:	Unknown vendor 003c
SDevice:	Device 009c
Rev:	11

Slot:	00:10.1
Class:	System peripheral
Vendor:	Intel Corporation
Device:	Core Processor QPI Routing and Protocol Registers
SVendor:	Unknown vendor 003c
SDevice:	Device 009c
Rev:	11

Slot:	00:16.0
Class:	Communication controller
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset HECI Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	06

Slot:	00:1a.0
Class:	USB Controller
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset USB2 Enhanced Host Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	06
ProgIf:	20

Slot:	00:1b.0
Class:	Audio device
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset High Definition Audio
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	06

Slot:	00:1c.0
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset PCI Express Root Port 1
Rev:	06

Slot:	00:1c.2
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset PCI Express Root Port 3
Rev:	06

Slot:	00:1c.3
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset PCI Express Root Port 4
Rev:	06

Slot:	00:1c.5
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset PCI Express Root Port 6
Rev:	06

Slot:	00:1d.0
Class:	USB Controller
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset USB2 Enhanced Host Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	06
ProgIf:	20

Slot:	00:1e.0
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	82801 PCI Bridge
Rev:	a6
ProgIf:	01

Slot:	00:1f.0
Class:	ISA bridge
Vendor:	Intel Corporation
Device:	5 Series Chipset LPC Interface Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	06

Slot:	00:1f.2
Class:	RAID bus controller
Vendor:	Intel Corporation
Device:	82801 SATA RAID Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	06

Slot:	00:1f.3
Class:	SMBus
Vendor:	Intel Corporation
Device:	5 Series/3400 Series Chipset SMBus Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	06

Slot:	01:00.0
Class:	VGA compatible controller
Vendor:	ATI Technologies Inc
Device:	Redwood PRO [Radeon HD 5500 Series]
SVendor:	Hewlett-Packard Company
SDevice:	Device 6870

Slot:	01:00.1
Class:	Audio device
Vendor:	ATI Technologies Inc
Device:	Redwood HDMI Audio [Radeon HD 5600 Series]
SVendor:	Hewlett-Packard Company
SDevice:	Device aa60

Slot:	02:00.0
Class:	Ethernet controller
Vendor:	Realtek Semiconductor Co., Ltd.
Device:	RTL8111/8168B PCI Express Gigabit Ethernet controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
Rev:	03

Slot:	03:00.0
Class:	FireWire (IEEE 1394)
Vendor:	VIA Technologies, Inc.
Device:	VT6315 Series Firewire Controller
SVendor:	Hewlett-Packard Company
SDevice:	Device 2a9c
ProgIf:	10

Slot:	04:00.0
Class:	Multimedia controller
Vendor:	Philips Semiconductors
Device:	Device 7231
SVendor:	Avermedia Technologies Inc
SDevice:	Device 890f
Rev:	ca

Slot:	05:00.0
Class:	Network controller
Vendor:	RaLink
Device:	RT3092 Wireless 802.11n 2T/2R PCIe
SVendor:	Unknown vendor 15a9
SDevice:	Device 0015

---

### Post by BicyclerBoy on 2010-12-31
As you have found on LinuxTV..
Does not seem to be any support for this tuner card/chipset.
Avermedia is fairly bad for support.
Haupauge is much better.

You really need to check Linux compatibility before spending the money.

But I guess you can use windoze with the tuner card.

---

### Post by JaJaBinks on 2010-12-31
Thanks and yes windows seems to be the only option at present

---

