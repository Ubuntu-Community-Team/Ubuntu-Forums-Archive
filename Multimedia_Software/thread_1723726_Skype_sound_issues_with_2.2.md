---
title: "Skype sound issues with 2.2"
date: 2011-04-07
forum: Multimedia Software
---

### Post by martijntje on 2011-04-07
After updating to version 2.2 this morning I am having weird sound issues. The sound has a weird metallic ring to it and is sometimes delayed, sometimes cut-off in the middle or both.

Sometimes this only happens to the notification sounds, sometimes it happens in calls too. Any ideas what I can do about it.

lshw output below:

```
martijntje
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 870 Extreme3
       vendor: ASRock
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.60 (09/14/2010)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X6 1090T Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X6 1090T Processor
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 800MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 768KiB
             capacity: 768KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
        *-bank:2
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: 996969000000000000
             vendor: Manufacturer02
             physical id: 2
             serial: 00000000
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: 996969000000000000
             vendor: Manufacturer03
             physical id: 3
             serial: 00000000
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RX780/RX790 Chipset Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port B)
             vendor: ATI Technologies Inc
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fc000000-fe9fffff ioport:d4000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF104 [GeForce GTX 460]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:19 memory:fc000000-fdffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:e800(size=128) memory:fe980000-fe9fffff
           *-multimedia
                description: Audio device
                product: GF104 High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:fe97c000-fe97ffff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port E)
             vendor: ATI Technologies Inc
             physical id: 9
             bus info: pci@0000:00:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 memory:fbe00000-fbefffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:fbefe000-fbefffff
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port F)
             vendor: ATI Technologies Inc
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) ioport:d3f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 06
                serial: 00:25:22:8d:83:1e
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.107 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:45 ioport:c800(size=256) memory:d3fff000-d3ffffff memory:d3ff8000-d3ffbfff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:44 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:fbdffc00-fbdfffff
           *-disk:0
                description: ATA Disk
                product: INTEL SSDSA2MH08
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sdb
                version: 045C
                serial: CVEM8413001F080DGN
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00061698
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 06ec90e3-d876-4c06-9649-b0b9f0c60197
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-03-16 18:20:53 filesystem=ext4 lastmountpoint=/&#65533;<K%&#65533;&#65533;&#65533;[r&#65533;&#65533;Pe#&#65533;&#65533;&#65533;&#65533;&#65533;#&#65533;&#65533;&#65533;&#65533;q&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=K%&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-04-06 07:27:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2011-04-07 13:05:43 state=mounted
           *-disk:1
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdc
                version: 1AJ1
                serial: S246J9CB142141
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b30fb
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: fab5e09f-6d09-44c6-8963-dfb314129120
                   size: 1863GiB
                   capabilities: primary multi journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-03-16 18:17:56 filesystem=ext4 lastmountpoint=/var&#65533;&#65533;@&&#65533;&#65533;&#65533; &#65533;M&#65533;&#65533;&%&#65533;&#65533;&#65533;&#65533;&#65533;&&#65533;&#65533;&#65533;&#65533;w&#65533;/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@&&#65533;&#65533;&#65533;&#65533; modified=2011-04-07 13:05:44 mounted=2011-04-07 13:05:44 state=clean
           *-disk:2
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdd
                version: 1AJ1
                serial: S246J9CB142142
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007aa7f
              *-volume
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdd1
                   capacity: 931GiB
                   capabilities: primary multi
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fbdfe000-fbdfefff
        *-usb:1
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fbdff800-fbdff8ff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fbdfd000-fbdfdfff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fbdff400-fbdff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 42
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: BD RW BD-5300S
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:fbdf8000-fbdfbfff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:4
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fbdfc000-fbdfcfff
        *-pci:4
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:fbf00000-fbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6315 Series Firewire Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:16 memory:fbfff800-fbffffff ioport:d800(size=256)
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fbdf7000-fbdf7fff
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fbdff000-fbdff0ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@3:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 10EAVS External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sda
             version: 1.75
             serial: WD-WCAU46788536
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=e8900690
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/multimedia
                version: 1.0
                serial: 1d9f556e-49fb-4bef-b6a8-f4bf4b706a8a
                size: 931GiB
                capacity: 931GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2009-04-11 17:07:07 filesystem=ext4 label=multimedia lastmountpoint=/media/multimedia&#65533;&#65533;E&#65533;&#65533;&#65533;&#65533; g&#65533;H&#1032;&#65533;&#65533;J&#840;&#65533;&#65533;@~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-04-07 13:05:57 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,barrier=1,data=ordered mounted=2011-04-07 13:05:57 state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

---

### Post by martijntje on 2011-04-09
Anybody?

---

### Post by AFarris01 on 2011-04-09
I unfortunately can't help, but I will say I'm having the same issues, plus a few.

Ever since the update to Skype Beta 2.2, Ive had issues with it randomly dropping audio and/or video during a call, continuous crashing, and the need to kill it/restart it 3-4 times before I can even make a call again with it. I am, right now, trying to re-call somebody it cut me off from about 20 minutes ago, and so far Skype has crashed on me every time I try to make an outgoing call. I've tried reinstalling from the repos, and from their website, and the only difference is the one from their site seems to crash less often... still not acceptable. It worked perfectly before the update two days ago.

If I find any solutions, I'll be sure to post them here... untill then I'm just a pissed-off user.

---

### Post by xaviers67 on 2011-04-09
Hey,

Have you tried by installation in some simulator with the windows installer, how was it's output, or you try again by reinstalling the skype as ubuntu doesn't have any of such issue.

---

### Post by martijntje on 2011-04-10
That's strange. Besides the sounds issues I have to say they made some improvements. It seems snappier, starting it for the first time seems to have been improved a lot (i tried throwing away my entire .Skype folder). It hasn't crashed on me yet.

If not for these sound issues I would be very pleased with it. Must be some hardware specific thingie. My girlfriend does not have any problems with this new version.

Can you see if there are any similarities between the hardware you use and the one I have?

---

### Post by ard.ru on 2011-04-10
Hi!
I have same issue with Skype after update a few days ago.

```

ard@ard-desktop:~$ sudo lshw
ard-desktop               
    description: Desktop Computer
    product: P35-DS4
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-001A4D5E1490
  *-core
       description: Motherboard
       product: P35-DS4
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F9 (11/30/2007)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E4700  @ 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU
          slot: Socket 775
          size: 2600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: A1
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:a000(size=4096) memory:f4000000-f7ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 8800 GTS 512]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f4000000-f5ffffff ioport:a000(size=128) memory:f7000000-f701ffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d100(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:d200(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d000(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fa104000-fa1043ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:fa100000-fa103fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:8000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:b000(size=4096) memory:fa000000-fa0fffff ioport:80400000(size=2097152)
           *-storage
                description: SATA controller
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:16 memory:fa000000-fa001fff
           *-ide
                description: IDE interface
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
                resources: irq:17 ioport:b000(size=8) ioport:b100(size=4) ioport:b200(size=8) ioport:b300(size=4) ioport:b400(size=16)
              *-disk
                   description: ATA Disk
                   product: WDC WD2500JB-00F
                   vendor: Western Digital
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/sdc
                   version: 15.0
                   serial: WD-WCAEP1007463
                   size: 232GiB (250GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=0006dbf0
                 *-volume
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: scsi@4:0.0.0,1
                      logical name: /dev/sdc1
                      version: 1.0
                      serial: 418f961e-f225-4f00-a7e4-371b5e735717
                      size: 232GiB
                      capacity: 232GiB
                      capabilities: primary journaled large_files ext3 ext2 initialized
                      configuration: created=2008-01-27 16:22:22 filesystem=ext3 label=ubuntu_home modified=2011-04-01 03:01:55 mounted=2011-04-01 02:51:09 state=clean
              *-cdrom
                   description: DVD writer
                   product: DVD-RW  DVR-109
                   vendor: PIONEER
                   physical id: 0.1.0
                   bus info: scsi@4:0.1.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: 1.40
                   capabilities: removable audio cd-r cd-rw dvd dvd-r
                   configuration: ansiversion=5 status=nodisc
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:c000(size=4096) memory:f8000000-f9ffffff ioport:80600000(size=2097152)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 01
                serial: 00:1a:4d:5e:14:90
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:44 ioport:c000(size=256) memory:f9000000-f9000fff memory:80600000-8060ffff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d300(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d400(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d500(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fa105000-fa1053ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:9000(size=4096)
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:d600(size=8) ioport:d700(size=4) ioport:d800(size=8) ioport:d900(size=4) ioport:da00(size=16) ioport:db00(size=16)
           *-disk:0
                description: ATA Disk
                product: WDC WD3200AAKS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 12.0
                serial: WD-WCASE0197619
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=1dd527d5
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: a8cb7462-ddae-ec4d-a07e-8ef209c54b63
                   size: 248GiB
                   capacity: 248GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-04-18 01:17:54 filesystem=ntfs label=vista_root modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 04fa75c2-efeb-4c37-b73c-8e373865ad85
                   size: 2039MiB
                   capacity: 2039MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 70b361af-8be4-4423-a43b-f18120f40652
                   size: 47GiB
                   capacity: 47GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-04-19 14:11:53 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;y&#65533;&#65533;&#65533;&#65533;K&#65533;&#65533;@&#65533;Th&#65533;&#65533;&#65533;<^z&#65533;&#65533;&#65533;&#65533;&#65533;=y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-04-05 23:03:52 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-04-09 22:54:47 state=mounted
           *-disk:1
                description: ATA Disk
                product: WDC WD10EADS-65L
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WCAU48529415
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00050af2
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/ubuntu_media
                   version: 1.0
                   serial: dc646c3e-5975-4d1f-ab8d-ee7083045755
                   size: 931GiB
                   capacity: 931GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2009-05-15 23:51:25 filesystem=ext4 label=ubuntu_media lastmountpoint=/media/ubuntu_media&#65533;&#65533;&#65533;y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;>&#65533;&#65533;g&#65533;&#65533;&#65533;&#65533;g&#65533;&#65533;&#65533;@&#65533;y&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-04-09 22:54:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2011-04-09 22:54:48 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fa106000-fa1060ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:dd00(size=8) ioport:de00(size=4) ioport:df00(size=8) ioport:e000(size=4) ioport:e100(size=16) ioport:e200(size=16)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by Jojia on 2011-04-11
Having the same problems here, just did a fresh install of ubuntu 10.10 and after installing skype 2.2 the sound is really bad. choppy, laggy, tinny robotic or whatever you wanna call it.

---

### Post by tarasu on 2011-04-16
same issue on ubuntu 10.10 and mint 10 julia
inxi -F:
```

System:    Host mint Kernel 2.6.35-28-generic i686 (32 bit) Distro Linux Mint 10 Julia
CPU:       Dual core Intel Core2 4400 (-MCP-) cache 2048 KB flags (lm nx sse sse2 sse3 ssse3) bmips 7980.4 
           Clock Speeds: (1) 1200.00 MHz (2) 1200.00 MHz
Graphics:  Card nVidia G92 [GeForce 9800 GT] X.Org 1.9.0 Res: 1680x1050@50.0hz 
           GLX Renderer GeForce 9800 GT/PCI/SSE2 GLX Version 3.3.0 NVIDIA 270.41.03 Direct Rendering Yes
Audio:     Card-1 Creative Labs SB0400 Audigy2 Value driver EMU10K1_Audigy at port cc00 BusID: 02:02.0
           Card-2 Microsoft Corp. LifeCam VX-1000 driver snd-usb-audio
           Sound: Advanced Linux Sound Architecture Version 1.0.23
Network:   Card Realtek RTL-8110SC/8169SC Gigabit Ethernet driver r8169 v: 2.3LK-NAPI at port c800 BusID: 02:05.0
Disks:     HDD Total Size: 1470.3GB (70.6% used) 1: /dev/sda ST3500320AS 500.1GB 47C 
           2: /dev/sdc ST3320620AS 320.1GB 52C 3: /dev/sdd SAMSUNG_SP2504C 250.1GB 47C 
           4: /dev/sdb ST3400620AS 400.1GB 47C 
Partition: ID:/ size: 9.7G used: 3.8G (41%) fs: ext4 ID:/home size: 36G used: 375M (2%) fs: ext4 
           ID:swap-1 size: 0.27GB used: 0.00GB (0%) fs: swap 
Info:      Processes 169 Uptime 1:00 Memory 456.3/2896.8MB Runlevel 2 Client Shell inxi 1.4.12

```
p.s. sound card E-MU 1212m
p.p.s. works fine when pulseaudio is disabled (add line "autospawn=no" to ~/.pulse/client.conf and restart or kill process pulseaudio), but I need it.

---

### Post by DarrenO on 2011-04-16
Having the robotic bad sound output as well with Skype 2.2. Using Ubuntu 10.04. Mic works fine, webcam works fine.

D.

EDIT: I killed pulseaudio and restarted Skype and it seems to be working now. Not making sense.

---

### Post by Nyrobie on 2011-05-13
> **DarrenO said:**
> Having the robotic bad sound output as well with Skype 2.2. Using Ubuntu 10.04. Mic works fine, webcam works fine.

D.

EDIT: I killed pulseaudio and restarted Skype and it seems to be working now. Not making sense.


How do you kill pulseaudio?

---

### Post by Nyrobie on 2011-05-13
nvm I figured it out. I just wasnt sure what happen if I killed the process and I didnt know if it would restart on its own or I needed some command to restart it.

---

### Post by DarrenO on 2011-05-13
Click on the System menu and open the Task Manager. Under the Process tab, you can find pulseaudio process and kill it. I just rebooted to restart it.

---

### Post by lidex on 2011-05-14
I doubt this is an ubuntu issue:
[https://support.skype.com/en/faq/FA197/What-can-I-do-if-I-am-experiencing-poor-sound-quality-in-Skype-for-Linux](https://support.skype.com/en/faq/FA197/What-can-I-do-if-I-am-experiencing-poor-sound-quality-in-Skype-for-Linux)
[http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)

---

### Post by mcdebugger on 2011-08-06
I have the same problem on gentoo. Both with my ATI HD integrated audio and EMU-1616m. Downgrading to 2.1.0.81 static version helped but of course want to use latest version. Killing PulseAudio isn't a fix because PA needed by huge of other applications. It's better for skype to die at all with such a bad linux support.

---

