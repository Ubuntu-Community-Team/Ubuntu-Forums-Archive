---
title: "New to Linux world, need help for driver"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by Asgard20032 on 2011-04-29
Hi, im new here. Im an windows user, and i wanted to try ubuntu. I installed it, but i was surprised to found no device manager. Found on internet that i should open "Hardware information", but i did not found it.
Im using the new ubuntu that was released april 2011.

I need to check my device, since my network wireless card don't work, so no internet. So i have to use an usb key  to put driver.

U.S. Robotics 802.11g Wireless Turbo PC/PCI.

I also want to check for other device, because im not sure if everything is working.

---

### Post by spiky001 on 2011-04-29
Hi if you open a terminal  Applications/Accessories Terminal then type ```
lspci
``` that will list your hardware

---

### Post by Asgard20032 on 2011-04-30
I did it... but, it don't say the right card.
my current card: U.S. Robotics 802.11g Wireless Turbo PC/PCI
the lspci say: Texas Instruments ACX 111 54 Mbps Wireless Interface

I know what is my card, since i installed it myself, my computer is open at the moment and i can read U.S robotics on the card, its written red...

what should i do?

---

### Post by Asgard20032 on 2011-04-30
Ok, bow i plugged a 100 meter cable from my computer on 2 floor to the router at first floor, so i got internet, but i need to make the wireless card work very soon, my parent will not tolerate the cable that goes trough the stair to long...





alex@Cobalt:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:0b.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
alex@Cobalt:~$ sudo lshw
[sudo] password for alex: 
cobalt                    
    description: Desktop Computer
    version: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4P8X
       vendor: ASUSTeK Computer Inc.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080009
          date: 05/12/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.9
          slot: CPU 1
          size: 2600MHz
          capacity: 3600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e0000000-efffffff
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:fe900000-fe9fffff memory:9ff00000-dfefffff
           *-display:0
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:16 memory:c0000000-cfffffff ioport:c000(size=256) memory:fe9f0000-fe9fffff memory:fe9c0000-fe9dffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AP [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 mingnt=8
                resources: memory:b0000000-bfffffff memory:fe9e0000-fe9effff
        *-generic UNCLAIMED
             description: System peripheral
             product: 82865G/PE/P Processor to I/O Memory Interface
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fecf0000-fecf0fff
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:eec0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ef00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ef20(size=32)
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ef40(size=32)
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:febff800-febffbff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:fea00000-feafffff
           *-network:0
                description: Ethernet interface
                product: 3c940 10/100/1000Base-T [Marvell]
                vendor: 3Com Corporation
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 12
                serial: 00:0c:6e:5a:31:03
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.109 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:22 memory:feafc000-feafffff ioport:d800(size=256)
           *-network:1 UNCLAIMED
                description: Network controller
                product: ACX 111 54Mbps Wireless Interface
                vendor: Texas Instruments
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:feafa000-feafbfff memory:feac0000-feadffff
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16) memory:dff00000-dff003ff
           *-cdrom
                description: DVD writer
                product: DVDR   PX-716A
                vendor: PLEXTOR
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.10
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801EB (ICH5) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:efe0(size=8) ioport:efac(size=4) ioport:efa0(size=8) ioport:efa8(size=4) ioport:ef90(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD1500HLFS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 04.0
                serial: WD-WXD0CB9M4849
                size: 139GiB (150GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003784d
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: 1ba9fcf2-8922-42ef-8419-61b5d363c0d4
                   size: 9536MiB
                   capacity: 9536MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: cf34694e-f569-44eb-8cf3-d083f4631377
                   size: 65GiB
                   capacity: 65GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-28 21:11:47 filesystem=ext4 lastmountpoint=/ modified=2011-04-29 04:00:12 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-04-30 08:44:42 state=mounted
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 35e5a060-e751-48e9-ab9c-626a250fc1ac
                   size: 60GiB
                   capacity: 60GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-28 21:11:49 filesystem=ext4 lastmountpoint=/home modified=2011-04-30 08:44:43 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-04-30 08:44:43 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST3120026AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 3.05
                serial: 3JT0V060
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=5b375b37
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: 30b5dc38-86ff-8145-becd-edeead3304c9
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-04-23 16:30:05 filesystem=ntfs state=clean
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:e800(size=256) ioport:ee80(size=64) memory:febff400-febff5ff memory:febff000-febff0ff
alex@Cobalt:~$ 






Is there any other driver that don't work except my wireless card from i post?

What should i do to make wireless card and other driver work?

---

### Post by chili555 on 2011-04-30
> 02:0b.0 Network controller: Texas Instruments [COLOR="Red"]ACX 111[/COLOR] 54Mbps Wireless InterfaceYou'll need to install ndiswrapper and use the Windows XP drivers, both the .inf and .sys files. Please see here: [http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx&page=2](http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx&page=2)

Post back if you get stuck.

---

### Post by Asgard20032 on 2011-04-30
> **chili555 said:**
> You'll need to install ndiswrapper and use the Windows XP drivers, both the .inf and .sys files. Please see here: [http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx&page=2](http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx&page=2)

Post back if you get stuck.

i already installed ndiswrapper, was sure it would make my card work... but no it don't, it require .inf

When i put my cd that come with my card, only .exe, no .inf or . sys

---

### Post by chili555 on 2011-04-30
Did you read the thread I linked? Did you read this?> Sorry for bumping, here comes actual link for this driver: [http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip](http://homedownloads.cisco.com/downloads/driver/wpc54gv2_driver_utility_v2.02.zip)
However, it haven't required files.

It is here: [ftp://ftp.lab.mlc.edu.tw/pub/Window/LAN/Planex_GW-NS54GM/Driver/winxp/](ftp://ftp.lab.mlc.edu.tw/pub/Window/LAN/Planex_GW-NS54GM/Driver/winxp/)

---

