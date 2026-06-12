---
title: "Problem DVI - HDMI"
date: 2010-06-23
forum: Multimedia Software
---

### Post by fipem on 2010-06-23
Hi there, recently I upgrade mi connection between my PC to my TV, from VGA to HDMI, now I can't watch heavy mkv files coz they jump during the playback, I cant watch MD content on youtube coz the video keeps loading from time to time even if the video is fully loaded,resuming, crappy - not fluid. 

I tried changing resolutions and refresh rate between 1280 x 720 and 1920 x 1080 but nothing.

Do I need to change my video card to be able to see 1080p media at 1920 x 1080 res in my ubuntu?

Any help please? He re some specs:

description: Desktop Computer
    product: MS-7280
    vendor: MSI
    version: 1.0
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-0019DBF60554
  *-core
       description: Motherboard
       product: MS-7280
       vendor: MSI
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V1.5 (03/05/2007)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.11.1
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 2300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM SDRAM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR2 Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM DDR2 Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GiB
             width: 64 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.11.1
          size: 3800MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RD580 [CrossFire Xpress 3200] Chipset Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS480 PCI-X Root Port
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:9000(size=4096) memory:f8800000-fe8fffff ioport:bff00000(size=536870912)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8500 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fd000000-fdffffff memory:c0000000-cfffffff(prefetchable) memory:fa000000-fbffffff ioport:9c00(size=128) memory:fe8e0000-fe8fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:a000(size=4096) memory:fe900000-fe9fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:19:db:f6:73:dd
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:26 ioport:a800(size=256) memory:fe9ff000-fe9fffff memory:fe9c0000-fe9dffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:e800(size=8) ioport:e400(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d800(size=16) memory:febffc00-febfffff
           *-disk:0
                description: ATA Disk
                product: WDC WD3200AAKS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 12.0
                serial: WD-WCARW1655800
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=51135113
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/Downloads
                   version: 3.1
                   serial: 7c2c6b6d-a971-7e47-8dd4-ef04088afb50
                   size: 298GiB
                   capacity: 298GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-11-05 16:39:31 filesystem=ntfs label=Downloads mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC WD10EARS-00Z
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 80.0
                serial: WD-WMAVU2172043
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000de8ad
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/sdb1
                   version: 3.1
                   serial: a549fe38-e785-4012-b9b7-16c14d5b70b1
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-06-22 19:28:36 filesystem=ntfs label=Bodega mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:febfe000-febfefff
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:febfd000-febfdfff
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:febfc000-febfcfff
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:17 memory:febfb000-febfbfff
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:febfa000-febfafff
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:febff800-febff8ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
             resources: ioport:b00(size=16)
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG SP0822N
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/sdc
                version: WA10
                serial: S06QJ20YC54791
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00000001
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@4:0.0.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: 175a0144-d16a-4614-a940-32f7b57c7726
                   size: 38GiB
                   capacity: 38GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2010-06-22 19:50:03 filesystem=ext4 modified=2010-06-22 19:50:20 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@4:0.0.0,2
                   logical name: /dev/sdc2
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdc5
                      logical name: /
                      capacity: 34GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdc6
                      capacity: 1553MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-4082B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: A209
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:febf4000-febf7fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:b000(size=4096) memory:fea00000-feafffff memory:80000000-800fffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 2
                bus info: pci@0000:03:02.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32
                resources: irq:20 memory:feafd000-feafd7ff ioport:bc00(size=128)
           *-network
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: eth1
                version: 10
                serial: 00:19:db:f6:05:54
                size: 10MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:21 ioport:b800(size=256) memory:feafcc00-feafccff memory:80000000-8001ffff(prefetchable)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

X Config file:


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SHARP HDMI"
    HorizSync       15.0 - 75.0
    VertRefresh     23.0 - 76.0
    Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    Option         "NoLogo" "True"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768_60 +0+0"
# Removed Option "metamodes" "1920x1080 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

TV

[http://www.sharpusa.com/ForHome/HomeEntertainment/LCDTVs/LC46LE700UN.aspx]("http://www.sharpusa.com/ForHome/HomeEntertainment/LCDTVs/LC46LE700UN.aspx")

Basic Specifications
Screen Size Class	46" Class (45-63/64" Diagonal)
Panel Type	X-Gen LCD Panel
10-bit LCD Panel	Yes
Pixel Resolution	Full 1920 x 1080 HD Resolution
Backlight System	Full Array LED
Viewing Angles	176º H / 176º V
LED Life (hours)1	100,000
Audio System	10W + 10W
120HzFrameRate	Yes
Tuning System	ATSC / QAM / NTSC
Spectral Contrast Engine Level	MC (over 2,000,000:1)
Aspect Ratio	16:9
Response Time	4ms
Features
AQUOS® Series	Yes
Quattron quad pixel technology	No
AQUOS Net	Yes
AQUOS AdvantageSM Support	Yes
Digital Still Picture Display	Yes
Game-Optimized	Yes
Terminals
Inputs
HDMI®	4 (v1.3 with deep color)
HD Component	2 (1080p compatible)
Composite Video	RCA x 2
S-Video	4-pin DIN x 1
Audio Inputs (L/R)	4 RCA
RS-232C	1
PC	1 (15-pin D-sub)
Ethernet Input	1
Power
Power Consumption AC (watts)	90W
Power Source	120 V, 60 Hz
Weight & Dimensions
Dimensions
Dimensions (wxhxd) (inches)	43-9/32" x 27-3/32" x 3-45/64"
Dimensions with Stand (wxhxd) (inches)	43-9/32" x 29-3/32" x 13-45/64"
Weight
Product Weight (lbs.)	40.8
Weight with Stand (lbs.)	47.4
Additional Specifications
Cabinet Color	Black
Limited Warranty	1 year parts and labor from date of purchase
Included Accessories
Remote Control	Yes
Table Stand	Yes

<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

O.S. You are using Ubuntu 10.04 LTS
- the Lucid Lynx - released in April 2010 and supported until April 2013.

---

### Post by fipem on 2010-06-24
Please guys any help?

---

