---
title: "LIRC sluggish if it works"
date: 2010-06-23
forum: Multimedia Software
---

### Post by molder on 2010-06-23
I am really having a tough time getting my MCE remote to work with XBMC.  I have got to the point where sometimes it work but then it gets VERY sluggish and my system crashes.  Any ideas anyone?


lircd.conf:
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Dish Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/dish/general.conf"
```

lshw output:
```
andrew@MythTV-Zeus:~$ sudo lshw
[sudo] password for andrew: 
mythtv-zeus               
    description: Mini Tower Computer
    product: Dimension 4700
    vendor: Dell Inc.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-0000-1020-8020-80C04F202020
  *-core
       description: Motherboard
       product: 0DH682
       vendor: Dell Inc.
       physical id: 0
       serial: ..CN708214BC00OC.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A10 (01/04/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.60GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: Microprocessor
          size: 3600MHz
          capacity: 4GHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
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
          physical id: 1000
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: 7F98000000000000
             physical id: 0
             serial: B12859B9
             slot: CHANNEL A DIMM 0
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             product: F6456U61E5667F
             vendor: 7F7F7F7F7FF70000
             physical id: 1
             serial: 00000000
             slot: CHANNEL B DIMM 0
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: FFFFFFFFFFFFFFFF
             physical id: 2
             serial: FFFFFFFF
             slot: CHANNEL A DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             product: S1024R3NN2QK-I
             vendor: 7FA8000000000000
             physical id: 3
             serial: 00000000
             slot: CHANNEL B DIMM 1
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:dcf00000-dfffffff memory:c0000000-cfffffff(prefetchable)
           *-display
                description: VGA compatible controller
                product: G96 [GeForce 9500 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:dd000000-ddffffff memory:c0000000-cfffffff(prefetchable) memory:de000000-dfffffff ioport:dc80(size=128) memory:dcf00000-dcf7ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:dce00000-dcefffff memory:d0000000-d01fffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:ff80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ff60(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff20(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:ffa80800-ffa80bff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:c000(size=4096) memory:dcc00000-dcdfffff memory:d0200000-d02fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 10
                serial: 00:0e:2e:aa:c4:1c
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:16 ioport:cc00(size=256) memory:dccfa700-dccfa7ff memory:d0200000-d020ffff(prefetchable)
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2
                resources: irq:17 ioport:c880(size=64)
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:18 memory:dccfa800-dccfafff memory:dccfc000-dccfffff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD reader
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd
                configuration: status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD400BD-75JM
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAMA2174630
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=52592a7a
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 71816119-bfa9-4bff-a1ef-68619c99eaa0
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-06-20 13:28:07 filesystem=ext4 lastmountpoint=/&#65533;&#65533;_&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;%&#65533; &#65533;x@&#65533;z&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;H&#65533;&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-06-20 15:09:05 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-06-23 12:12:55 state=mounted
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /home
                   version: 1.0
                   serial: 0c6a2b35-1691-4e06-ac67-da752d2ddf95
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-06-19 18:47:31 filesystem=ext4 label=MythTV-Zeus Bad lastmountpoint=/home&#65533;&#65533;G.&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;;&#65533;&#1920;&#65533;T&#5438;&#65533;&#65533;%&#65533; &#65533;&#65533;W&#65533;C&#65533;W&#65533;&#65533;*&#65533;&#65533;*&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-06-23 12:12:57 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2010-06-23 12:12:57 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 568b2105-be23-448f-bd0a-18eb2c3bb82e
                   size: 1958MiB
                   capacity: 1958MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-disk:1
                description: ATA Disk
                product: WDC WD10EADS-00L
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WCAU4C574913
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fe7c178b
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /home/andrew/Videos/Movies
                   version: 1.0
                   serial: 06ebece0-57f2-4eab-a436-8f70ddc3e39c
                   size: 329GiB
                   capacity: 329GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-06-21 08:31:20 filesystem=ext4 label=Movies lastmountpoint=/home/andrew/Videos/Movies:&#65533;&#65533;0-&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;T&#65533;>5&#65533;%&#65533; &#65533;&#65533;&#65533;/&#65533;&#65533;>5&#65533;.&#65533;!&#65533;X modified=2010-06-23 12:12:59 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2010-06-23 12:12:59 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.1.0,2
                   logical name: /dev/sdb2
                   size: 602GiB
                   capacity: 602GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /home/andrew/Videos/TV_Shows
                      capacity: 602GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:ece0(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:7
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             size: 1927MiB (2021MB)
             capabilities: partitioned partitioned:dos
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/8272-C495
                version: FAT32
                serial: 8272-c495
                size: 1925MiB
                capacity: 1926MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted

```

lsusb output:
```
andrew@MythTV-Zeus:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 047d:105e Kensington Bluetooth EDR Dongle
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 125f:1015 A-DATA Technology Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by bedek on 2010-06-24
Here are my steps:

1) edited /etc/lirc/hardware.conf, in that file I've changed:
from REMOTE="None"
to REMOTE="Toshiba"
where "Toshiba" is the name of my remote as in /etc/lirc/lircd.conf

2) because my remote is not standard I've had to generate lircd.conf using comand:
irrecord -f -d /dev/lirc0 /tmp/Toshiba

Your configuration looks fine, the only thing which I've notice yesterday is that sometimes ir receiver is receiving signals even when I'm not pressing any buttons, I might cover some it a bit to be less sensitive.

---

### Post by molder on 2010-06-24
The red light on my receiver is on almost at all time.  It does appear to acknowledge signals from my other remotes.  This receiver works perfectly with Windows 7.

---

