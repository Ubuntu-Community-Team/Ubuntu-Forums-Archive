---
title: "improve ubuntu high definition playback to the level of vlc in win xp"
date: 2011-09-26
forum: Multimedia Software
---

### Post by WasMeHere on 2011-09-26
I have a fairly old computer that was once quite powerful, an hp xw8400 workstation with 2 xeon double processors (4 CPUs@3GHz) 4 GB RAM and a nvidia graphics card according to the following *lshw* output (256 MB prefetchable).```
        *-pci:2
             description: PCI bridge
             product: 5000X Chipset PCI Express x16 Port 4-7
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:1000(size=4096) memory:f0000000-f1ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G71 [Quadro FX 1500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f0000000-f0ffffff memory:d0000000-dfffffff memory:f1000000-f1ffffff ioport:1000(size=128)
```

*It can play 1080/50p video with VLC in Windows XP quite well, but only fairly well in Linux* (I have tried Ubuntu, Linux Mint, GeeXboX and Mepis, the best so far is Ubuntu Studio realtime). VLC works rather well with

1. GPU acceleration,
2. minimize video quality post-processing level and
3. skip all H.264 in-loop deblocking

but it is not perfect, particularly bad if there is a lot of motion (change) in the picture. Mplayer also works quite well but not perfectly (slightly different artefacts) with the option

[FONT="Courier New"]-lavdopts fast:threads=3[/FONT]

See also the following [_link to a previous comment on a similar subject_]("http://ubuntuforums.org/showpost.php?p=11240695&postcount=6")

Why is the graphics slower with linux? Is it because the video driver is not as efficient as in win xp? *What can I do to improve the video in linux* (of course I can buy a brand new computer, but is that necessary)? I think most of us want linux to be second to none.
;-)
Looking forward to your help
Olle

---

### Post by WasMeHere on 2011-09-27
Hello again,

*What do **you** suggest?* I am prepared to install a 'test operating system' on an empty partition, so I am not afraid of testing the limits or breaking the system.

Maybe the memory speed is important. The 4 GB of RAM is specified in the following way:
FB-DIMM DDR2 FB-DIMM Synchronous 667 MHz (1,5 ns)
and maybe it would help you to find possibilities and limitations to improve the playback, if I supply the full output of *lshw*

Best regards/Olle
```
xw8400
    description: Mini Tower Computer
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=mini-tower cpus=4 family=103C_53335X sku=PS955AV uuid=504E809F-B813-DC11-BBDA-4B54341C001A
  *-core
       description: Motherboard
       product: 0A08h
       vendor: Hewlett-Packard
       physical id: 0
       version: NA
       serial: CZC722497N
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786D5 v02.37
          date: 07/09/2009
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Xeon(R) CPU            5160  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: XU1 PROCESSOR
          size: 3GHz
          capacity: 3GHz
          width: 64 bits
          clock: 1333MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca lahf_lm tpr_shadow cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 7
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 8
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          description: CPU
          product: Intel(R) Xeon(R) CPU            5160  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: XU2 PROCESSOR
          size: 1998MHz
          capacity: 1998MHz
          width: 64 bits
          clock: 1333MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca lahf_lm tpr_shadow cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: burst internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory:0
          description: System Memory
          physical id: 3e
          slot: System board or motherboard
        *-bank:0
             description: FB-DIMM DDR2 FB-DIMM Synchronous 667 MHz (1,5 ns)
             product: 18HF12872FD667B5E3
             vendor: JEDEC ID:2C 0C 07 04 D9 06 59 1E
             physical id: 0
             serial: 1E5906D9
             slot: DIMM01
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: FB-DIMM DDR2 FB-DIMM Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 1
             slot: DIMM02
        *-bank:2
             description: FB-DIMM DDR2 FB-DIMM Synchronous 667 MHz (1,5 ns)
             product: 18HF12872FD667B5E3
             vendor: JEDEC ID:2C 0C 07 04 D9 06 59 1F
             physical id: 2
             serial: 1F5906D9
             slot: DIMM03
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: FB-DIMM DDR2 FB-DIMM Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 3
             slot: DIMM04
        *-bank:4
             description: FB-DIMM DDR2 FB-DIMM Synchronous 667 MHz (1,5 ns)
             product: 18HF12872FD667B5E3
             vendor: JEDEC ID:2C 0C 07 16 D6 12 28 DE
             physical id: 4
             serial: DE2812D6
             slot: DIMM05
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:5
             description: FB-DIMM DDR2 FB-DIMM Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 5
             slot: DIMM06
        *-bank:6
             description: FB-DIMM DDR2 FB-DIMM Synchronous 667 MHz (1,5 ns)
             product: M395T2953CZ4-CE60
             vendor: JEDEC ID:CE 01 07 19 03 21 C4 20
             physical id: 6
             serial: 20C42103
             slot: DIMM07
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:7
             description: FB-DIMM DDR2 FB-DIMM Synchronous [empty]
             vendor: JEDEC ID:
             physical id: 7
             slot: DIMM08
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 3f
          slot: System board or motherboard
          capacity: 1MiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 1MiB
             width: 2 bits
     *-cpu:2
          physical id: 0
          bus info: cpu@2
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1998MHz
          capacity: 1998MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-cpu:3
          physical id: 2
          bus info: cpu@3
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1998MHz
          capacity: 1998MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-memory:2 UNCLAIMED
          physical id: 3
     *-memory:3 UNCLAIMED
          physical id: 4
     *-pci:0
          description: Host bridge
          product: 5000X Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 12
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 5000 Series Chipset PCI Express x4 Port 2
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 memory:f2100000-f22fffff
           *-pci:0
                description: PCI bridge
                product: 6311ESB/6321ESB PCI Express Upstream Port
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress pm normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:0 memory:f2100000-f21fffff
              *-pci:0
                   description: PCI bridge
                   product: 6311ESB/6321ESB PCI Express Downstream Port E1
                   vendor: Intel Corporation
                   physical id: 0
                   bus info: pci@0000:1e:00.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:16
              *-pci:1
                   description: PCI bridge
                   product: 6311ESB/6321ESB PCI Express Downstream Port E2
                   vendor: Intel Corporation
                   physical id: 1
                   bus info: pci@0000:1e:01.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:17 memory:f2100000-f21fffff
                 *-network
                      description: Ethernet interface
                      product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
                      vendor: Broadcom Corporation
                      physical id: 0
                      bus info: pci@0000:1f:00.0
                      logical name: eth0
                      version: 01
                      serial: 00:1a:4b:54:34:1c
                      size: 100Mbit/s
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.22 ip=192.168.0.7 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                      resources: irq:89 memory:f2100000-f210ffff
           *-pci:1
                description: PCI bridge
                product: 6311ESB/6321ESB PCI Express to PCI-X Bridge
                vendor: Intel Corporation
                physical id: 0.3
                bus info: pci@0000:10:00.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress pm pcix normal_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: 5000 Series Chipset PCI Express x4 Port 3
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-pci:2
             description: PCI bridge
             product: 5000X Chipset PCI Express x16 Port 4-7
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:1000(size=4096) memory:f0000000-f1ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G71 [Quadro FX 1500]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f0000000-f0ffffff memory:d0000000-dfffffff memory:f1000000-f1ffffff ioport:1000(size=128)
        *-pci:3
             description: PCI bridge
             product: 5000 Series Chipset PCI Express x4 Port 5
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-pci:4
             description: PCI bridge
             product: 5000 Series Chipset PCI Express x4 Port 6
             vendor: Intel Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-pci:5
             description: PCI bridge
             product: 5000 Series Chipset PCI Express x4 Port 7
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0
        *-pci:6
             description: PCI bridge
             product: 631xESB/632xESB/3100 Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:88 memory:f2300000-f23fffff
           *-pci
                description: PCI bridge
                product: 6702PXH PCI Express-to-PCI Bridge A
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 09
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress msi pm pcix normal_decode bus_master cap_list
                resources: memory:f2300000-f23fffff
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                   vendor: Texas Instruments
                   physical id: 4
                   bus info: pci@0000:09:04.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm ohci bus_master cap_list
                   configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                   resources: irq:24 memory:f2304000-f23047ff memory:f2300000-f2303fff
        *-usb:0
             description: USB Controller
             product: 631xESB/632xESB/3100 Chipset UHCI USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:3000(size=32)
        *-usb:1
             description: USB Controller
             product: 631xESB/632xESB/3100 Chipset UHCI USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:3020(size=32)
        *-usb:2
             description: USB Controller
             product: 631xESB/632xESB/3100 Chipset UHCI USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3040(size=32)
        *-usb:3
             description: USB Controller
             product: 631xESB/632xESB/3100 Chipset UHCI USB Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:3060(size=32)
        *-usb:4
             description: USB Controller
             product: 631xESB/632xESB/3100 Chipset EHCI USB2 Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f2400000-f24003ff
        *-pci:7
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d9
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:f2000000-f20fffff
           *-multimedia
                description: Multimedia audio controller
                product: Vortex 1
                vendor: Aureal Semiconductor
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=au8820 latency=32 maxlatency=12 mingnt=2
                resources: irq:16 memory:f2000000-f201ffff ioport:2000(size=8) ioport:2008(size=8)
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:19 memory:f2024000-f20247ff memory:f2020000-f2023fff
        *-isa
             description: ISA bridge
             product: 631xESB/632xESB/3100 Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 631xESB/632xESB/3100 Chipset SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 09
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30b0(size=16)
           *-disk
                description: ATA Disk
                product: ST3250620AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.CH
                serial: 9QE3BH4F
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=db3cf6ba
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: d7718396-a2ad-4bc9-be09-d4573ce337a8
                   size: 49GiB
                   capacity: 49GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-08-21 16:32:59 filesystem=ntfs label=winxp state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 182GiB
                   capacity: 182GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: W95 FAT32 partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 31GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 12GiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /
                      capacity: 31GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: HPFS/NTFS partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 106GiB
           *-cdrom
                description: DVD writer
                product: DVD+-RW GSA-H21L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: W516
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
     *-pci:1
          description: Host bridge
          product: 5000 Series Chipset FSB Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:00:10.0
          version: 12
          width: 32 bits
          clock: 33MHz
          configuration: driver=i5000_edac
          resources: irq:0
     *-pci:2
          description: Host bridge
          product: 5000 Series Chipset FSB Registers
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:00:10.1
          version: 12
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: 5000 Series Chipset FSB Registers
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:00:10.2
          version: 12
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: 5000 Series Chipset Reserved Registers
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:00:11.0
          version: 12
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: 5000 Series Chipset Reserved Registers
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:00:13.0
          version: 12
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: 5000 Series Chipset FBD Registers
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:00:15.0
          version: 12
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: 5000 Series Chipset FBD Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:00:16.0
          version: 12
          width: 32 bits
          clock: 33MHz
```

---

### Post by BicyclerBoy on 2011-09-27
Are you running the nVidia proprietary driver ?

I would think this is required to get any video performance because the GPU is weak.
The only GPU acceleration is openGL & overlays.

The CPUs probably suit multi-threaded versions of mplayer.
Run a 64bit OS.

glxinfo | grep OpenGL

---

### Post by WasMeHere on 2011-09-27
> **BicyclerBoy said:**
> Are you running the nVidia proprietary driver ?

I would think this is required to get any video performance because the GPU is weak.
The only GPU acceleration is openGL & overlays.

The CPUs probably suit multi-threaded versions of mplayer.
Run a 64bit OS.

glxinfo | grep OpenGL

Thank you for the tips,

I have tried but not succeeded in running the nVidia proprietary driver. *Can you help me to install it* (and to get rid of the software that is installed by default and sits in its way)?

I have tried more than one 64bit OS, but so far none has beaten the 32-bit ubuntu studio. Mplayer with 3 or 4 threads specified works fairly well and I can see that several CPUs are working. So I think that my mplayer already can do multi-threading.

So if it does not help with the proprietary driver, you think that a newer video card would help?

```
olle@xw8400:~$ glxinfo|grep -i opengl
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: Quadro FX 1500/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 270.41.06
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
olle@xw8400:~$ 
```

---

### Post by .... on 2011-09-27
You should try and use vdpau where possible, either directly with mplayer, or using va-api->vdpau wrapper: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)

---

### Post by WasMeHere on 2011-09-27
> **.... said:**
> You should try and use vdpau where possible, either directly with mplayer, or using va-api->vdpau wrapper: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)

Thanks for the tip,

I have tried but not succeeded to use vdpau. I have found information, that I need the proprietary nvidia driver, and I have not yet managed to install it. I will look at you link now...> PPA description

Packages related to the proprietary ATI driver (Catalyst). Currently, this PPA contains a modified version of libva and a rebuild of vlc against it. You will also need the latest xvba-video package from: [http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/) for hardware video acceleration.

Will this work for nvidia?

---

### Post by .... on 2011-09-27
> **Olle Wiklund said:**
> Thanks for the tip,

I have tried but not succeeded to use vdpau. I have found information, that I need the proprietary nvidia driver, and I have not yet managed to install it. I will look at you link now...
You did manage to install it
> OpenGL version string: 2.1.2 NVIDIA 270.41.06

---

### Post by WasMeHere on 2011-09-27
> **.... said:**
> You did manage to install it

Well, I think it was installed by default in ubuntu studio. That explains why it is 'best in [ubuntu]class'.

But I still have an error with vdpau:
[[FONT="Courier New"]vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.[/FONT]
```
olle@xw8400:/media/data/Bilder/2011/09/07$ mplayer -vo vdpau -vc ffh264vdpau 00009.MTS 
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 00009.MTS.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 50.000000
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   8.8 (08.7) of 17804.5 ( 4:56:44.5)  1.5% 
Exiting... (Quit)
olle@xw8400:/media/data/Bilder/2011/09/07$ 

``` In one post this error was called stupid. And it's stubborn too ;-)
> **Kradziej said:**
> To all who get this stupid vdpau error both in vlc and mplayer


Uninstall nvidia-current and go to nvidia page to download drivers 
Should work now 
Probably symlinks are messed up in packages from repo

---

### Post by .... on 2011-09-27
This is the point where I call BS and move on to something else...

---

### Post by WasMeHere on 2011-09-27
As you can see in the code below, mplayer works fairly well with

[FONT="Courier New"]-lavdopts fast:threads=3
A:  33.0 V:  33.0 **A-V:  0.029**[/FONT]

What to do now? How can I get vdpau to work, now that I already have the proprietary driver (are you sure that I have it)?
questions, questions from a confused
Olle
```
alias mplayermts='mplayer -lavdopts fast:threads=3'
alias vlcmts='vlc --rt-priority --rate 0.9'
olle@xw8400:/media/data/Bilder/2011/09/07$ mplayermts -vo vdpau -vc ffh264vdpau 00009.MTS 
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 00009.MTS.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 50.000000
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  24.3 (24.3) of 17804.5 ( 4:56:44.5)  1.7% 
Exiting... (Quit)
olle@xw8400:/media/data/Bilder/2011/09/07$ mplayermts  00009.MTS 
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 00009.MTS.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 50.000000
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
A:  33.0 V:  33.0 A-V:  0.029 ct: -0.020 1633/1633 78%  7%  1.4% 5 0 
Exiting... (Quit)
olle@xw8400:/media/data/Bilder/2011/09/07$ 

```

---

### Post by BicyclerBoy on 2011-09-27
The quadro FX1500 does not have any VDPAU bitstream processor.
Check the driver readme appendix A.
VDPAU started with FX1600.

If this is a PCIe mobo you could get a
GT430/240/220/520

GT430 is full height & best VDPAU /HDMI audio etc
GT520 is feature set D but **too slow** to run shader de-interlacing/scaling etc.
GT240 is fast than necessary & full height
GT220 is ideal. Just fast enough
You need to install a vdpau library..

Your CPU horsepower should have no problem with decode/post decode filters..
The video h/w is is just too slow..

VDPAU is an open std proposed /supported by nVidia.
No one else has used it for the h/w api.
VAAPI is an open std that is supported by intel driver & nVidia h/w by using a private cross-over library.
There is a private lib to provide VAAPI with AMD XvBA.
VLC only supports VAAPI.
VAAPI is a not complete & does not compare to VDPAU yet.
MythTV, mplayer, ffmpeg, libav, XBMC can support VDPAU directly.

---

### Post by WasMeHere on 2011-09-28
> **BicyclerBoy said:**
> ...
If this is a PCIe mobo you could get a
GT430/240/220/520

GT430 is full height & best VDPAU /HDMI audio etc
GT520 is feature set D but **too slow** to run shader de-interlacing/scaling etc.
GT240 is fast than necessary & full height
GT220 is ideal. Just fast enough
You need to install a vdpau library..

Your CPU horsepower should have no problem with decode/post decode filters..
The video h/w is is just too slow..
...
Thank you BicyclerBoy,

*lshw* tells me that the mobo has PCIe:
[FONT="Courier New"]5000X Chipset PCI Express x16 Port 4-7[/FONT]
and I feel encouraged to get a new video card.

By the way, I visited your beautiful Aotearoha in 1994 :-)
It is almost antipodal to my Sverige.

Best regards
Olle

---

### Post by WasMeHere on 2011-09-30
Now I have installed and started to optimize a new graphics pci card, Gigabyte GT 430 with nvidia processor according to the suggestion by *BicyclerBoy*. It works with the same software (video driver) as for the previous card.

Mplayer can use *vdpau* and take advantage of GPU acceleration, and the CPU load is decreased from approx. 50% to very low levels. There is no need to use more than one thread. The playback quality of 1080/50p video is improved, but I must admit, that it is not perfect out of the box. I continue to tweak the command to run mplayer.```
alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau'
``` The graphics driver is set to use adaptive clocking, which means the the video may lag in the beginning before it 'understands' that it must speed-up. I need not use the options ```
-lavdopts fast:threads=4
``` to get sufficient processing speed. I can even decode and show two HD videos at the same time.

Summary:
We could not achieve the performance of Windows XP with the old card :-(
It was obvious that modern software needs a new card, so I bought one, and now my xw8400 workstation works for high definition video :-)

Thanks *BicyclerBoy* and *.... 'four-dots'*
Best regards
Olle

*Edit: The performance of VLC was not improved. Probably it can be tweaked, but it is not obvious for me how to do it*

---

### Post by BicyclerBoy on 2011-09-30
VLC has to use VAAPI & the VDPAU backend for VAAPI from spitted-desktop systems.
I think you need to compile VLC with VAAPI or find a ppa with it...
But VAAPI does not allow the full usage of VDPAU: VA-deinterlace, hqscaling, denoise, sharpen, colorspace etc. Some of these are good for SD DVD material.

I glad it works but I still think your machine should have worked better/same as WinXP.
Maybe the linux kernel support for multi-processors is not as good as XP?

Are you using audio hq re-sampling (alsa or pa) ?
The VLC yadif(x2) de-interlacing filter does increase CPU load..

Playback of real 50Hz media on a 60Hz refresh rate monitor will result in 5Hz euro-judder from the frame pull-down scheme. Is this what you are reporting ?

I have never had to change the adaptive clocking config to get instant HD playback (single & dual-head).

---

### Post by WasMeHere on 2012-02-29
'Long time no post' ;-)

But now I have good news. Yesterday I downloaded the ***daily build of Lubuntu Precise*** (alpha, almost beta), that soon will be 12.04 LTS.

1. I ran Lubuntu live from the iso on a computer, that has problems to show 720-30p video with Ubuntu 10.04.

- AMD Athlon 64 X2 Dual Core Processor 4400+
- 2 GB RAM
- nvidia GeForce 7050 PV / nForce 630a/PCI/SSE2/3DNOW!
- driver 2.1.2 NVIDIA 195.36.24

Lubuntu could play 720-30p video perfectly and did a good job although not perfect with 1080-50p. This was running live with the nouveau driver, and I could not use vdpau. The driver has improved a lot from the present LTS graphics driver and/or LXDE is faster than gnome.

2. I installed Lubuntu to a separate partition on my multimedia computer (triple boot: Ubuntu Studio, Windows XP and Lubuntu).

- double xeon (4 cpus)
- 4 GB RAM
- GeForce GT 430/PCIe/SSE2
- driver 4.2.0 NVIDIA 295.20

So I expected perfect performance playing 1080-50p with a proprietary driver and vdpau, and it is. Actually, mplayer can use but did not need vdpau to play the full HD video. Now linux is not lagging behind Windows XP, Lubuntu is actually doing better, which can be seen on particularly difficult video clips with a lot of motion (change between the frames).

New summary:
We can achieve at least the graphics performance of Windows XP. With a new card and new software an old workstation is still going strong. It was obvious that modern software needs a new card, so I bought one, and now my xw8400 workstation works well with high definition video.

I think the improvement is due to both LXDE and the new graphics drivers.

Happy end :KS

[I]Edit: In order to edit the start menu, I downloaded alacarte. It belongs to gnome, and without warning I received the gnome 3 desktop with Unity. I discovered it, when I checked the available desktop sessions at login.

Anyway, I could test the performance of mplayer and the graphics driver with Unity and compiz. The video was choppy and the cpus were really busy, also with vdpau, that almost left the cpus idling with LXDE. So a large part of the improvement is due to the light-weight desktop environment.[/I]

---

