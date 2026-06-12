---
title: "slow system while playing music?"
date: 2009-01-03
forum: Multimedia Software
---

### Post by soy1jaguar on 2009-01-03
two days ago i did the change. happy to say i left windows xp behind, i love ubuntu but i really don know much about it. installation ...not a problem ...my ipod..it recognized right away, same with my camera, the only issue thta i have so far is that whenever im playing music and i tried to do saomething else like going online, the computer slows down dramatically, dont know why, need help:confused:

---

### Post by cariboo on 2009-01-03
What application are you using to play music, and what are your computer specs. In a Applications-->Accessories-->Terminal type:

```
sudo lshw
```

and paste the output in your next post.

Jim

---

### Post by soy1jaguar on 2009-01-04
> **cariboo907 said:**
> What application are you using to play music, and what are your computer specs. In a Applications-->Accessories-->Terminal type:

```
sudo lshw
```

and paste the output in your next post.

Jim

pollo@pollo-desktop:~$ sudo lshw
[sudo] password for pollo: 
pollo-desktop             
    description: Desktop Computer
    product: 5430US
    vendor: Compaq
    version: C01BDABB
    serial: 3D21KKLNL0HY
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=0051BC92-EF55-BD11-AB38-F119424D380E
  *-core
       description: Motherboard
       product: 0784h
       vendor: Compaq
       physical id: 0
       serial: 3D21KKLNL0HY
       slot: HeadPhone & Line Out
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 1
          version: 686Y2 v2.06 (12/03/2001)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.1.2
          slot: XU1
          size: 1800MHz
          capacity: 2300MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 256KiB
             capacity: 4MiB
             capabilities: burst internal write-back data
     *-memory:0
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 200 MHz (5.0 ns)
             product: NT256D64S88A0G-7K
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 0
             serial: 00000000
             slot: XMM1
             size: 256MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 200 MHz (5.0 ns)
             product: NT256D64S88A0G-7K
             vendor: JEDEC ID:7F 7F 7F 0B 00 00 00 00
             physical id: 1
             serial: 00000000
             slot: XMM2
             size: 256MiB
             width: 64 bits
             clock: 200MHz (5.0ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 22
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: XU15
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 MX 420]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB12LV26 IEEE-1394 Controller (Link)
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=66 maxlatency=4 mingnt=2 module=ohci1394
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 03
                serial: 00:02:a5:fa:fc:59
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
           *-communication
                description: Modem
                product: HSP MicroModem 56
                vendor: PCTel Inc
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=serial latency=0
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: Maxtor 4D080H4
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: DAH0
                serial: D40LQBNE
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b74510e2
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 1f584d60-6752-4639-8226-696a21344a96
                   size: 3882MiB
                   capacity: 3882MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-31 12:35:43 filesystem=ext3 modified=2009-01-02 15:48:11 mounted=2009-01-02 15:46:59 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 70GiB
                   capacity: 70GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1466MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 67GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1466MiB
                      capabilities: nofs
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM DVD-117
                vendor: Compaq
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.03
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: CD-R/CD-RW writer
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                capabilities: audio cd-r cd-rw
                configuration: status=nodisc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi
          physical id: 3
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 9321
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             version: 9321
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
             version: 9321
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
             version: 9321
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:29:f8:b3:d1:d1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
pollo@pollo-desktop:~$

---

### Post by rushikesh988 on 2009-01-04
it may depend on ur configuretion of computer ....

TRY making a swap space larger 
or u can use   light versions of ubuntu such as

XUBUNTU

---

