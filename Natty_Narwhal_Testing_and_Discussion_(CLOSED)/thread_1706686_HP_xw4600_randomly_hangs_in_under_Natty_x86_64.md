---
title: "HP xw4600 randomly hangs in under Natty x86_64"
date: 2011-03-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cioma on 2011-03-14
Does anyone experience random hangs with HP xw4600 under Natty x86_64?

Here is my lshw output:
```
computer                  
    description: Mini Tower Computer
    product: HP xw4600 Workstation (RV724AV)
    vendor: Hewlett-Packard
    serial: CZC9491HM1
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=mini-tower family=103C_53335X power-on_password=disabled sku=RV724AV uuid=86BBAF2A-56E4-DE11-BBD8-554604F00026
  *-core
       description: Motherboard
       product: 0AA0h
       vendor: Hewlett-Packard
       physical id: 0
       serial: CZC9491HM1
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786F3 v01.22
          date: 10/28/2010
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E7600  @ 3.06GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     E7600  @ 3.06GHz
          slot: XU1 PROCESSOR
          size: 3066MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: burst internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 3a
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 9HTF12872AY-800G1
             vendor: JEDEC ID:2C 00 00 00 00 00 00 00
             physical id: 0
             serial: 2BF15EE0
             slot: XMM1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 9905321-002.A02LF
             vendor: JEDEC ID:7F 98 00 00 00 00 00 00
             physical id: 1
             serial: 3A652996
             slot: XMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: 9HTF12872AY-800G1
             vendor: JEDEC ID:2C 00 00 00 00 00 00 00
             physical id: 2
             serial: 1FF15EE0
             slot: XMM3
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 9905321-002.A02LF
             vendor: JEDEC ID:7F 98 00 00 00 00 00 00
             physical id: 3
             serial: 3A422996
             slot: XMM4
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 3b
          slot: System board or motherboard
          capacity: 4MiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 4MiB
             width: 2 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82X38/X48 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=x38_edac
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82X38/X48 Express Host-Primary PCI Express Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:f2000000-f30fffff ioport:e0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT216 [GeForce GT 220]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:f2000000-f2ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:1100(size=128) memory:f3080000-f30fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:f3000000-f3003fff
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
             resources: irq:20 ioport:2100(size=32)
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
             resources: irq:21 ioport:2120(size=32)
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
             resources: irq:22 ioport:2140(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:f3204800-f3204bff
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
             resources: irq:46 memory:f3200000-f3203fff
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
             resources: irq:41 ioport:3000(size=4096) memory:f8000000-f81fffff ioport:f8200000(size=2097152)
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
             resources: irq:42 ioport:4000(size=4096) memory:f8400000-f85fffff ioport:f8600000(size=2097152)
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
             resources: irq:43 ioport:5000(size=4096) memory:f3100000-f31fffff ioport:f8800000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5755 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:3f:00.0
                logical name: eth2
                version: 02
                serial: 00:26:55:46:04:f0
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5755-v3.29 ip=192.168.2.32 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:45 memory:f3100000-f310ffff
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
             resources: irq:20 ioport:2160(size=32)
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
             resources: irq:21 ioport:2180(size=32)
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
             resources: irq:22 ioport:21a0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:f3204c00-f3204fff
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
        *-storage
             description: RAID bus controller
             product: 82801 SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             logical name: scsi2
             logical name: scsi5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:2200(size=8) ioport:2210(size=4) ioport:2208(size=8) ioport:2214(size=4) ioport:21c0(size=32) memory:f3204000-f32047ff
           *-disk:0
                description: ATA Disk
                product: ST3250318AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: HP34
                serial: 9VY2EVH4
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a4d5b53b
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/newtec/hdd
                   version: 3.1
                   serial: 748ecb62-1921-f943-a866-e69103c7a088
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-01-13 18:58:59 filesystem=ntfs label=newtec mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM GH40L
                vendor: hp
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom2
                logical name: /dev/cdrw2
                logical name: /dev/dvd2
                logical name: /dev/dvdrw2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RB0E
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk:1
                description: ATA Disk
                product: TS128GSSD18M-M
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sdb
                version: v090
                serial: 00337605022D
                size: 120GiB (129GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8aae3438
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: fbb76ad2-b2bd-422f-87be-2518b5ece1d5
                   size: 60GiB
                   capacity: 60GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-07-22 00:25:29 filesystem=ext4 label=lin lastmountpoint=/ modified=2011-03-14 09:22:03 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-03-14 11:33:01 state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sdb2
                   logical name: /media/home/win
                   version: 3.1
                   serial: f2613b5b-bc5c-b94b-8164-b6514d8182e5
                   size: 60GiB
                   capacity: 60GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-07-24 02:06:57 filesystem=ntfs label=win modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true

```

And here is dmesg output:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-6-generic (buildd@crested) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-5ubuntu1) ) #34-Ubuntu SMP Tue Mar 8 14:15:57 UTC 2011 (Ubuntu 2.6.38-6.34-generic 2.6.38-rc7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-6-generic root=UUID=fbb76ad2-b2bd-422f-87be-2518b5ece1d5 ro vga=799
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000097c00 (usable)
[    0.000000]  BIOS-e820: 0000000000097c00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000defc1da0 (usable)
[    0.000000]  BIOS-e820: 00000000defc1da0 - 00000000defc1e00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000defc1e00 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed40000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed45000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP xw4600 Workstation/0AA0h, BIOS 786F3 v01.22 10/28/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E3FFF write-protect
[    0.000000]   E4000-EFFFF write-back
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 100000000 mask FE0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdefc1 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000f9bf0] f9bf0
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000defc1000
[    0.000000]  0000000000 - 00dee00000 page 2M
[    0.000000]  00dee00000 - 00defc1000 page 4k
[    0.000000] kernel direct mapping tables up to defc1000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ defbb000-defc1000
[    0.000000] RAMDISK: 366e2000 - 37369000
[    0.000000] ACPI: RSDP 00000000000e6410 00024 (v02 COMPAQ)
[    0.000000] ACPI: XSDT 00000000defc1ee8 00064 (v01 HPQOEM SLIC-WKS 20101028      00000000)
[    0.000000] ACPI: FACP 00000000defc2088 000F4 (v03 COMPAQ          DEFC2647      00000000)
[    0.000000] ACPI: DSDT 00000000defc2647 09C48 (v01 COMPAQ DSDT_PRJ 00000001 MSFT 0100000E)
[    0.000000] ACPI: FACS 00000000defc1e00 00040
[    0.000000] ACPI: APIC 00000000defc217c 00084 (v01 COMPAQ BEARLX38 00000001      00000000)
[    0.000000] ACPI: ASF! 00000000defc2200 00063 (v32 COMPAQ BEARLX38 00000001      00000000)
[    0.000000] ACPI: MCFG 00000000defc2263 0003C (v01 COMPAQ BEARLX38 00000001      00000000)
[    0.000000] ACPI: TCPA 00000000defc229f 00032 (v01 COMPAQ BEARLX38 00000001      00000000)
[    0.000000] ACPI: SLIC 00000000defc22d1 00176 (v01 HPQOEM SLIC-WKS 00000001      00000000)
[    0.000000] ACPI: HPET 00000000defc2447 00038 (v01 COMPAQ BEARLX38 00000001      00000000)
[    0.000000] ACPI: DMAR 00000000defc247f 00158 (v01 COMPAQ BEARLX38 00000001      00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [000000011fffb000 - 000000011fffffff]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff88011be00000-ffff88011f7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000097
[    0.000000]     0: 0x00000100 -> 0x000defc1
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 1044296
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 894969 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0xf808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000097000 - 0000000000098000
[    0.000000] PM: Registered nosave memory: 0000000000098000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000defc1000 - 00000000defc2000
[    0.000000] PM: Registered nosave memory: 00000000defc1000 - 00000000defc2000
[    0.000000] PM: Registered nosave memory: 00000000defc2000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f4000000
[    0.000000] PM: Registered nosave memory: 00000000f4000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fed40000
[    0.000000] PM: Registered nosave memory: 00000000fed40000 - 00000000fed45000
[    0.000000] PM: Registered nosave memory: 00000000fed45000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:14000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800dec00000 s83840 r8192 d22656 u524288
[    0.000000] pcpu-alloc: s83840 r8192 d22656 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1028162
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-6-generic root=UUID=fbb76ad2-b2bd-422f-87be-2518b5ece1d5 ro vga=799
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: at /build/buildd/linux-2.6.38/drivers/pci/dmar.c:634 warn_invalid_dmar+0x8f/0xa0()
[    0.000000] Hardware name: HP xw4600 Workstation
[    0.000000] Your BIOS is broken; DMAR reported at address fed90000 returns all ones!
[    0.000000] BIOS vendor: Hewlett-Packard; Ver: 786F3 v01.22; Product Version:  
[    0.000000] Modules linked in:
[    0.000000] Pid: 0, comm: swapper Not tainted 2.6.38-6-generic #34-Ubuntu
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff810656df>] ? warn_slowpath_common+0x7f/0xc0
[    0.000000]  [<ffffffff8106577f>] ? warn_slowpath_fmt_taint+0x3f/0x50
[    0.000000]  [<ffffffff81ade13e>] ? __early_set_fixmap+0x96/0x9d
[    0.000000]  [<ffffffff8131383f>] ? warn_invalid_dmar+0x8f/0xa0
[    0.000000]  [<ffffffff81ade5b9>] ? early_iounmap+0xf3/0x13c
[    0.000000]  [<ffffffff81af8d7d>] ? check_zero_address+0xd4/0x116
[    0.000000]  [<ffffffff813578b4>] ? acpi_get_table_with_size+0x58/0xba
[    0.000000]  [<ffffffff815cb97d>] ? _etext+0x0/0x3
[    0.000000]  [<ffffffff81af8dd8>] ? detect_intel_iommu+0x19/0xb0
[    0.000000]  [<ffffffff81acfe47>] ? pci_iommu_alloc+0x47/0x72
[    0.000000]  [<ffffffff81addefe>] ? mem_init+0x19/0xec
[    0.000000]  [<ffffffff81ac8a9c>] ? start_kernel+0x201/0x400
[    0.000000]  [<ffffffff81ac8388>] ? x86_64_start_reservations+0x132/0x136
[    0.000000]  [<ffffffff81ac845d>] ? x86_64_start_kernel+0xd1/0xe0
[    0.000000] ---[ end trace a7919e7f17c0a725 ]---
[    0.000000] Disabling lock debugging due to kernel taint
[    0.000000] Memory: 4025044k/4718592k available (5934k kernel code, 541408k absent, 152140k reserved, 5016k data, 960k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3066.832 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6133.66 BogoMIPS (lpj=30668320)
[    0.000010] pid_max: default: 32768 minimum: 301
[    0.000031] Security Framework initialized
[    0.000047] AppArmor: AppArmor initialized
[    0.000049] Yama: becoming mindful.
[    0.010285] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012899] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.014182] Mount-cache hash table entries: 256
[    0.014333] Initializing cgroup subsys ns
[    0.014341] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.014345] Initializing cgroup subsys cpuacct
[    0.014350] Initializing cgroup subsys memory
[    0.014359] Initializing cgroup subsys devices
[    0.014362] Initializing cgroup subsys freezer
[    0.014365] Initializing cgroup subsys net_cls
[    0.014368] Initializing cgroup subsys blkio
[    0.014402] CPU: Physical Processor ID: 0
[    0.014404] CPU: Processor Core ID: 0
[    0.014407] mce: CPU supports 6 MCE banks
[    0.014415] CPU0: Thermal monitoring enabled (TM2)
[    0.014420] using mwait in idle threads.
[    0.016454] ACPI: Core revision 20110112
[    0.020015] ftrace: allocating 24321 entries in 96 pages
[    0.028393] DMAR: Host address width 36
[    0.028399] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.028409] DMAR: parse DMAR table failure.
[    0.028412] Setting APIC routing to flat
[    0.028710] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.129856] CPU0: Intel(R) Core(TM)2 Duo CPU     E7600  @ 3.06GHz stepping 0a
[    0.130000] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.130000] ... version:                2
[    0.130000] ... bit width:              40
[    0.130000] ... generic registers:      2
[    0.130000] ... value mask:             000000ffffffffff
[    0.130000] ... max period:             000000007fffffff
[    0.130000] ... fixed-purpose events:   3
[    0.130000] ... event mask:             0000000700000003
[    0.130000] Booting Node   0, Processors  #1
[    0.290020] Brought up 2 CPUs
[    0.290027] Total of 2 processors activated (12267.18 BogoMIPS).
[    0.290571] devtmpfs: initialized
[    0.290658] print_constraints: dummy: 
[    0.290681] Time: 10:32:52  Date: 03/14/11
[    0.290710] NET: Registered protocol family 16
[    0.290734] Trying to unpack rootfs image as initramfs...
[    0.290808] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.290813] ACPI: bus type pci registered
[    0.290868] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
[    0.290873] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
[    0.297802] PCI: Using configuration type 1 for base access
[    0.300033] bio: create slab <bio-0> at 0
[    0.303757] ACPI: EC: Look up EC in DSDT
[    0.400343] ACPI: Interpreter enabled
[    0.400353] ACPI: (supports S0 S3 S4 S5)
[    0.400370] ACPI: Using IOAPIC for interrupt routing
[    0.430101] ACPI: No dock devices found.
[    0.430114] HEST: Table not found.
[    0.430118] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.460211] ACPI Error: [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.460226] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff880117634af0), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.460235] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.460241] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110112/nspredef-352)
[    0.460250] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.460546] pci_root PNP0A08:00: host bridge window [mem 0xf8000000-0xfebfffff]
[    0.460551] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.460554] pci_root PNP0A08:00: host bridge window [io  0x1000-0x2fff]
[    0.460557] pci_root PNP0A08:00: host bridge window [io  0x3000-0x6fff]
[    0.460560] pci_root PNP0A08:00: host bridge window [io  0x7000-0xafff]
[    0.460563] pci_root PNP0A08:00: host bridge window [io  0xb000-0xffff]
[    0.460566] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.460570] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xf3ffffff]
[    0.460573] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.460588] pci 0000:00:00.0: [8086:29e0] type 0 class 0x000600
[    0.460622] pci 0000:00:01.0: [8086:29e1] type 1 class 0x000604
[    0.460645] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.460648] pci 0000:00:01.0: PME# disabled
[    0.460680] pci 0000:00:1a.0: [8086:2937] type 0 class 0x000c03
[    0.460716] pci 0000:00:1a.0: reg 20: [io  0x2100-0x211f]
[    0.460760] pci 0000:00:1a.1: [8086:2938] type 0 class 0x000c03
[    0.460796] pci 0000:00:1a.1: reg 20: [io  0x2120-0x213f]
[    0.460833] pci 0000:00:1a.2: [8086:2939] type 0 class 0x000c03
[    0.460869] pci 0000:00:1a.2: reg 20: [io  0x2140-0x215f]
[    0.460914] pci 0000:00:1a.7: [8086:293c] type 0 class 0x000c03
[    0.460933] pci 0000:00:1a.7: reg 10: [mem 0xf3204800-0xf3204bff]
[    0.460998] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.461002] pci 0000:00:1a.7: PME# disabled
[    0.461021] pci 0000:00:1b.0: [8086:293e] type 0 class 0x000403
[    0.461034] pci 0000:00:1b.0: reg 10: [mem 0xf3200000-0xf3203fff 64bit]
[    0.461079] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.461082] pci 0000:00:1b.0: PME# disabled
[    0.461098] pci 0000:00:1c.0: [8086:2940] type 1 class 0x000604
[    0.461147] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.461150] pci 0000:00:1c.0: PME# disabled
[    0.461169] pci 0000:00:1c.4: [8086:2948] type 1 class 0x000604
[    0.461214] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.461217] pci 0000:00:1c.4: PME# disabled
[    0.461234] pci 0000:00:1c.5: [8086:294a] type 1 class 0x000604
[    0.461279] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.461282] pci 0000:00:1c.5: PME# disabled
[    0.461302] pci 0000:00:1d.0: [8086:2934] type 0 class 0x000c03
[    0.461341] pci 0000:00:1d.0: reg 20: [io  0x2160-0x217f]
[    0.461379] pci 0000:00:1d.1: [8086:2935] type 0 class 0x000c03
[    0.461415] pci 0000:00:1d.1: reg 20: [io  0x2180-0x219f]
[    0.461453] pci 0000:00:1d.2: [8086:2936] type 0 class 0x000c03
[    0.461489] pci 0000:00:1d.2: reg 20: [io  0x21a0-0x21bf]
[    0.461534] pci 0000:00:1d.7: [8086:293a] type 0 class 0x000c03
[    0.461554] pci 0000:00:1d.7: reg 10: [mem 0xf3204c00-0xf3204fff]
[    0.461617] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.461620] pci 0000:00:1d.7: PME# disabled
[    0.461636] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.461684] pci 0000:00:1f.0: [8086:2916] type 0 class 0x000601
[    0.461752] pci 0000:00:1f.0: quirk: [io  0xf800-0xf87f] claimed by ICH6 ACPI/GPIO/TCO
[    0.461758] pci 0000:00:1f.0: quirk: [io  0xfa00-0xfa3f] claimed by ICH6 GPIO
[    0.461763] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0400 (mask 007f)
[    0.461768] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0480 (mask 000f)
[    0.461773] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0cb0 (mask 000f)
[    0.461809] pci 0000:00:1f.2: [8086:2822] type 0 class 0x000104
[    0.461824] pci 0000:00:1f.2: reg 10: [io  0x2200-0x2207]
[    0.461831] pci 0000:00:1f.2: reg 14: [io  0x2210-0x2213]
[    0.461837] pci 0000:00:1f.2: reg 18: [io  0x2208-0x220f]
[    0.461844] pci 0000:00:1f.2: reg 1c: [io  0x2214-0x2217]
[    0.461850] pci 0000:00:1f.2: reg 20: [io  0x21c0-0x21df]
[    0.461857] pci 0000:00:1f.2: reg 24: [mem 0xf3204000-0xf32047ff]
[    0.461884] pci 0000:00:1f.2: PME# supported from D3hot
[    0.461887] pci 0000:00:1f.2: PME# disabled
[    0.461928] pci 0000:01:00.0: [10de:0a20] type 0 class 0x000300
[    0.461936] pci 0000:01:00.0: reg 10: [mem 0xf2000000-0xf2ffffff]
[    0.461945] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.461954] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.461960] pci 0000:01:00.0: reg 24: [io  0x1100-0x117f]
[    0.461966] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.462006] pci 0000:01:00.1: [10de:0be2] type 0 class 0x000403
[    0.462013] pci 0000:01:00.1: reg 10: [mem 0xf3000000-0xf3003fff]
[    0.462074] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.462078] pci 0000:00:01.0:   bridge window [io  0x1000-0x1fff]
[    0.462080] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf30fffff]
[    0.462083] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.462115] pci 0000:00:1c.0: PCI bridge to [bus 28-28]
[    0.462119] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.462123] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.462127] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.462163] pci 0000:00:1c.4: PCI bridge to [bus 34-34]
[    0.462168] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.462171] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.462175] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.462231] pci 0000:3f:00.0: [14e4:167b] type 0 class 0x000200
[    0.462252] pci 0000:3f:00.0: reg 10: [mem 0xf3100000-0xf310ffff 64bit]
[    0.462341] pci 0000:3f:00.0: PME# supported from D3hot D3cold
[    0.462345] pci 0000:3f:00.0: PME# disabled
[    0.462369] pci 0000:00:1c.5: PCI bridge to [bus 3f-3f]
[    0.462374] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.462377] pci 0000:00:1c.5:   bridge window [mem 0xf3100000-0xf31fffff]
[    0.462383] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.462435] pci 0000:00:1e.0: PCI bridge to [bus 10-10] (subtractive decode)
[    0.462439] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.462443] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.462447] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.462449] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfebfffff] (subtractive decode)
[    0.462451] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.462452] pci 0000:00:1e.0:   bridge window [io  0x1000-0x2fff] (subtractive decode)
[    0.462454] pci 0000:00:1e.0:   bridge window [io  0x3000-0x6fff] (subtractive decode)
[    0.462456] pci 0000:00:1e.0:   bridge window [io  0x7000-0xafff] (subtractive decode)
[    0.462458] pci 0000:00:1e.0:   bridge window [io  0xb000-0xffff] (subtractive decode)
[    0.462459] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.462461] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xf3ffffff] (subtractive decode)
[    0.462463] pci 0000:00:1e.0:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
[    0.462480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.462599] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG1._PRT]
[    0.462641] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX1._PRT]
[    0.462676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX5._PRT]
[    0.462708] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX6._PRT]
[    0.462741] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.462865] ACPI Error: [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.462872] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node ffff880117634af0), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.462883] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110112/nspredef-352)
[    0.469581] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.469624] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.469662] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.469700] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.469740] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.469778] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.469816] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.469854] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.470019] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.470024] vgaarb: loaded
[    0.470176] SCSI subsystem initialized
[    0.470243] libata version 3.00 loaded.
[    0.470281] usbcore: registered new interface driver usbfs
[    0.470291] usbcore: registered new interface driver hub
[    0.470312] usbcore: registered new device driver usb
[    0.470584] wmi: Mapper loaded
[    0.470587] PCI: Using ACPI for IRQ routing
[    0.470590] PCI: pci_cache_line_size set to 64 bytes
[    0.470653] reserve RAM buffer: 0000000000097c00 - 000000000009ffff 
[    0.470655] reserve RAM buffer: 00000000defc1da0 - 00000000dfffffff 
[    0.470740] NetLabel: Initializing
[    0.470743] NetLabel:  domain hash size = 128
[    0.470745] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.470756] NetLabel:  unlabeled traffic allowed by default
[    0.470785] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.470791] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.470796] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.481010] Freeing initrd memory: 12828k freed
[    0.490050] Switching to clocksource hpet
[    0.496091] AppArmor: AppArmor Filesystem Enabled
[    0.496133] pnp: PnP ACPI init
[    0.496150] ACPI: bus type pnp registered
[    0.496334] pnp 00:00: [mem 0xf8000000-0xfebfffff window]
[    0.496336] pnp 00:00: [bus 00-ff]
[    0.496338] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.496339] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.496341] pnp 00:00: [io  0x1000-0x2fff window]
[    0.496342] pnp 00:00: [io  0x3000-0x6fff window]
[    0.496344] pnp 00:00: [io  0x7000-0xafff window]
[    0.496345] pnp 00:00: [io  0xb000-0xffff window]
[    0.496346] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.496348] pnp 00:00: [mem 0xe0000000-0xf3ffffff window]
[    0.496349] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.496402] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.496416] pnp 00:01: [io  0x00f0-0x00ff]
[    0.496428] pnp 00:01: [irq 13]
[    0.496449] pnp 00:01: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.496458] pnp 00:02: [io  0x0000-0x000f]
[    0.496460] pnp 00:02: [io  0x0080-0x008f]
[    0.496461] pnp 00:02: [io  0x00c0-0x00df]
[    0.496462] pnp 00:02: [dma 4]
[    0.496480] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.496487] pnp 00:03: [io  0x0070-0x0071]
[    0.496490] pnp 00:03: [irq 8]
[    0.496510] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.496517] pnp 00:04: [io  0x0061]
[    0.496534] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.496543] pnp 00:05: [irq 12]
[    0.496564] pnp 00:05: Plug and Play ACPI device, IDs PNP0f13 PNP0f0e (active)
[    0.496571] pnp 00:06: [io  0x0060]
[    0.496572] pnp 00:06: [io  0x0064]
[    0.496576] pnp 00:06: [irq 1]
[    0.496593] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.496689] pnp 00:07: Plug and Play ACPI device, IDs PNP0401 (disabled)
[    0.496805] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 PNP0500 (disabled)
[    0.496930] pnp 00:09: [irq 6]
[    0.496932] pnp 00:09: [dma 2]
[    0.496934] pnp 00:09: [io  0x03f0-0x03f5]
[    0.496935] pnp 00:09: [io  0x03f7]
[    0.496961] pnp 00:09: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.496993] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.497016] pnp 00:0a: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.497023] pnp 00:0b: [mem 0xfed40000-0xfed44fff]
[    0.497043] pnp 00:0b: Plug and Play ACPI device, IDs BCM0102 PNP0c31 (active)
[    0.497068] pnp 00:0c: [mem 0xfed00000-0xfed003ff]
[    0.497091] pnp 00:0c: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.497221] pnp 00:0d: [io  0x0010-0x001f]
[    0.497223] pnp 00:0d: [io  0x0050-0x0053]
[    0.497224] pnp 00:0d: [io  0x0072-0x0077]
[    0.497226] pnp 00:0d: [io  0x0090-0x009f]
[    0.497284] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.497292] pnp 00:0e: [io  0x0400-0x041f]
[    0.497293] pnp 00:0e: [io  0x0420-0x043f]
[    0.497294] pnp 00:0e: [io  0x0440-0x045f]
[    0.497296] pnp 00:0e: [io  0x0460-0x047f]
[    0.497297] pnp 00:0e: [io  0x0480-0x048f]
[    0.497298] pnp 00:0e: [io  0xf800-0xf81f]
[    0.497300] pnp 00:0e: [io  0xf820-0xf83f]
[    0.497301] pnp 00:0e: [io  0xf840-0xf85f]
[    0.497302] pnp 00:0e: [io  0xf860-0xf87f]
[    0.497303] pnp 00:0e: [io  0xfa00-0xfa3f]
[    0.497305] pnp 00:0e: [io  0xfc00-0xfc7f]
[    0.497306] pnp 00:0e: [io  0xfc80-0xfcff]
[    0.497307] pnp 00:0e: [io  0xfe00-0xfe7f]
[    0.497308] pnp 00:0e: [io  0xfe80-0xfeff]
[    0.497322] pnp 00:0e: disabling [io  0xf800-0xf81f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]
[    0.497327] pnp 00:0e: disabling [io  0xf820-0xf83f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]
[    0.497332] pnp 00:0e: disabling [io  0xf840-0xf85f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]
[    0.497336] pnp 00:0e: disabling [io  0xf860-0xf87f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]
[    0.497375] system 00:0e: [io  0x0400-0x041f] has been reserved
[    0.497378] system 00:0e: [io  0x0420-0x043f] has been reserved
[    0.497381] system 00:0e: [io  0x0440-0x045f] has been reserved
[    0.497385] system 00:0e: [io  0x0460-0x047f] has been reserved
[    0.497388] system 00:0e: [io  0x0480-0x048f] has been reserved
[    0.497391] system 00:0e: [io  0xfa00-0xfa3f] has been reserved
[    0.497394] system 00:0e: [io  0xfc00-0xfc7f] has been reserved
[    0.497397] system 00:0e: [io  0xfc80-0xfcff] has been reserved
[    0.497400] system 00:0e: [io  0xfe00-0xfe7f] has been reserved
[    0.497403] system 00:0e: [io  0xfe80-0xfeff] has been reserved
[    0.497407] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.497423] pnp 00:0f: [io  0x04d0-0x04d1]
[    0.497461] system 00:0f: [io  0x04d0-0x04d1] has been reserved
[    0.497465] system 00:0f: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.499806] Switched to NOHz mode on CPU #0
[    0.499855] Switched to NOHz mode on CPU #1
[    0.499930] pnp 00:10: [mem 0x00000000-0x0009ffff]
[    0.499933] pnp 00:10: [mem 0x00100000-0xdfffffff]
[    0.499936] pnp 00:10: [mem 0x000e4000-0x000fffff]
[    0.499938] pnp 00:10: [mem 0xfec01000-0xfecfffff]
[    0.499941] pnp 00:10: [mem 0xfed00400-0xfed3ffff]
[    0.499944] pnp 00:10: [mem 0xfed45000-0xffffffff]
[    0.499946] pnp 00:10: [mem 0xf4000000-0xf7ffffff]
[    0.499949] pnp 00:10: [mem 0x000ce200-0x000e3fff]
[    0.500020] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.500024] system 00:10: [mem 0x00100000-0xdfffffff] could not be reserved
[    0.500028] system 00:10: [mem 0x000e4000-0x000fffff] could not be reserved
[    0.500031] system 00:10: [mem 0xfec01000-0xfecfffff] has been reserved
[    0.500035] system 00:10: [mem 0xfed00400-0xfed3ffff] has been reserved
[    0.500038] system 00:10: [mem 0xfed45000-0xffffffff] has been reserved
[    0.500041] system 00:10: [mem 0xf4000000-0xf7ffffff] has been reserved
[    0.500045] system 00:10: [mem 0x000ce200-0x000e3fff] has been reserved
[    0.500048] system 00:10: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.500057] pnp: PnP ACPI: found 17 devices
[    0.500060] ACPI: ACPI bus type pnp unregistered
[    0.505879] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf8000000-0xf81fffff]
[    0.505884] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.505888] pci 0000:00:1c.4: BAR 14: assigned [mem 0xf8400000-0xf85fffff]
[    0.505892] pci 0000:00:1c.4: BAR 15: assigned [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.505896] pci 0000:00:1c.5: BAR 15: assigned [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.505901] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.505904] pci 0000:00:1c.4: BAR 13: assigned [io  0x4000-0x4fff]
[    0.505908] pci 0000:00:1c.5: BAR 13: assigned [io  0x5000-0x5fff]
[    0.505912] pci 0000:01:00.0: BAR 6: assigned [mem 0xf3080000-0xf30fffff pref]
[    0.505916] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.505919] pci 0000:00:01.0:   bridge window [io  0x1000-0x1fff]
[    0.505923] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf30fffff]
[    0.505927] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.505932] pci 0000:00:1c.0: PCI bridge to [bus 28-28]
[    0.505935] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.505940] pci 0000:00:1c.0:   bridge window [mem 0xf8000000-0xf81fffff]
[    0.505945] pci 0000:00:1c.0:   bridge window [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.505951] pci 0000:00:1c.4: PCI bridge to [bus 34-34]
[    0.505955] pci 0000:00:1c.4:   bridge window [io  0x4000-0x4fff]
[    0.505960] pci 0000:00:1c.4:   bridge window [mem 0xf8400000-0xf85fffff]
[    0.505964] pci 0000:00:1c.4:   bridge window [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.505971] pci 0000:00:1c.5: PCI bridge to [bus 3f-3f]
[    0.505974] pci 0000:00:1c.5:   bridge window [io  0x5000-0x5fff]
[    0.505979] pci 0000:00:1c.5:   bridge window [mem 0xf3100000-0xf31fffff]
[    0.505984] pci 0000:00:1c.5:   bridge window [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.505990] pci 0000:00:1e.0: PCI bridge to [bus 10-10]
[    0.505993] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.505997] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.506001] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.506017] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.506021] pci 0000:00:01.0: setting latency timer to 64
[    0.506027] pci 0000:00:1c.0: setting latency timer to 64
[    0.506033] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.506038] pci 0000:00:1c.4: setting latency timer to 64
[    0.506044] pci 0000:00:1c.5: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.506048] pci 0000:00:1c.5: setting latency timer to 64
[    0.506053] pci 0000:00:1e.0: setting latency timer to 64
[    0.506056] pci_bus 0000:00: resource 4 [mem 0xf8000000-0xfebfffff]
[    0.506058] pci_bus 0000:00: resource 5 [io  0x0000-0x0cf7]
[    0.506059] pci_bus 0000:00: resource 6 [io  0x1000-0x2fff]
[    0.506061] pci_bus 0000:00: resource 7 [io  0x3000-0x6fff]
[    0.506062] pci_bus 0000:00: resource 8 [io  0x7000-0xafff]
[    0.506064] pci_bus 0000:00: resource 9 [io  0xb000-0xffff]
[    0.506065] pci_bus 0000:00: resource 10 [mem 0x000a0000-0x000bffff]
[    0.506067] pci_bus 0000:00: resource 11 [mem 0xe0000000-0xf3ffffff]
[    0.506069] pci_bus 0000:00: resource 12 [mem 0xfed40000-0xfed44fff]
[    0.506071] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.506072] pci_bus 0000:01: resource 1 [mem 0xf2000000-0xf30fffff]
[    0.506074] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.506076] pci_bus 0000:28: resource 0 [io  0x3000-0x3fff]
[    0.506077] pci_bus 0000:28: resource 1 [mem 0xf8000000-0xf81fffff]
[    0.506079] pci_bus 0000:28: resource 2 [mem 0xf8200000-0xf83fffff 64bit pref]
[    0.506081] pci_bus 0000:34: resource 0 [io  0x4000-0x4fff]
[    0.506082] pci_bus 0000:34: resource 1 [mem 0xf8400000-0xf85fffff]
[    0.506084] pci_bus 0000:34: resource 2 [mem 0xf8600000-0xf87fffff 64bit pref]
[    0.506086] pci_bus 0000:3f: resource 0 [io  0x5000-0x5fff]
[    0.506087] pci_bus 0000:3f: resource 1 [mem 0xf3100000-0xf31fffff]
[    0.506089] pci_bus 0000:3f: resource 2 [mem 0xf8800000-0xf89fffff 64bit pref]
[    0.506091] pci_bus 0000:10: resource 4 [mem 0xf8000000-0xfebfffff]
[    0.506092] pci_bus 0000:10: resource 5 [io  0x0000-0x0cf7]
[    0.506094] pci_bus 0000:10: resource 6 [io  0x1000-0x2fff]
[    0.506095] pci_bus 0000:10: resource 7 [io  0x3000-0x6fff]
[    0.506097] pci_bus 0000:10: resource 8 [io  0x7000-0xafff]
[    0.506098] pci_bus 0000:10: resource 9 [io  0xb000-0xffff]
[    0.506100] pci_bus 0000:10: resource 10 [mem 0x000a0000-0x000bffff]
[    0.506102] pci_bus 0000:10: resource 11 [mem 0xe0000000-0xf3ffffff]
[    0.506103] pci_bus 0000:10: resource 12 [mem 0xfed40000-0xfed44fff]
[    0.506132] NET: Registered protocol family 2
[    0.506252] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.507229] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.511955] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.512580] TCP: Hash tables configured (established 524288 bind 65536)
[    0.512584] TCP reno registered
[    0.512593] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.512640] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.512796] NET: Registered protocol family 1
[    0.512957] pci 0000:01:00.0: Boot video device
[    0.512969] PCI: CLS 64 bytes, default 64
[    0.512971] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.512975] Placing 64MB software IO TLB between ffff8800dac00000 - ffff8800dec00000
[    0.512979] software IO TLB at phys 0xdac00000 - 0xdec00000
[    0.513197] Scanning for low memory corruption every 60 seconds
[    0.513290] audit: initializing netlink socket (disabled)
[    0.513300] type=2000 audit(1300098771.510:1): initialized
[    0.523114] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.524414] VFS: Disk quotas dquot_6.5.2
[    0.524456] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.524903] fuse init (API version 7.16)
[    0.524970] msgmni has been set to 7886
[    0.525152] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.525176] io scheduler noop registered
[    0.525180] io scheduler deadline registered
[    0.525208] io scheduler cfq registered (default)
[    0.525290] pcieport 0000:00:01.0: setting latency timer to 64
[    0.525316] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.525352] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.525381] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.525427] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.525456] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    0.525501] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.525529] pcieport 0000:00:1c.5: irq 43 for MSI/MSI-X
[    0.525594] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.525612] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.526567] vesafb: framebuffer at 0xf1000000, mapped to 0xffffc90005100000, using 7552k, total 7552k
[    0.526572] vesafb: mode is 1600x1200x32, linelength=6400, pages=0
[    0.526574] vesafb: scrolling: redraw
[    0.526577] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.584560] Console: switching to colour frame buffer device 200x75
[    0.642769] fb0: VESA VGA frame buffer device
[    0.642972] intel_idle: MWAIT substates: 0x22220
[    0.642974] intel_idle: does not run on family 6 model 23
[    0.643056] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.690016] ACPI: Power Button [PBTN]
[    0.690243] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.690575] ACPI: Power Button [PWRF]
[    0.690935] ACPI: acpi_idle registered with cpuidle
[    0.690965] Marking TSC unstable due to TSC halts in idle
[    0.692064] ERST: Table is not found!
[    0.692278] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.693809] serial 00:08: [irq 4]
[    0.693813] serial 00:08: [io  0x03f8-0x03ff]
[    0.694038] serial 00:08: activated
[    0.714715] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.715179] Linux agpgart interface v0.103
[    0.716206] brd: module loaded
[    0.716729] loop: module loaded
[    0.716926] i2c-core: driver [adp5520] using legacy suspend method
[    0.717203] i2c-core: driver [adp5520] using legacy resume method
[    0.717745] Fixed MDIO Bus: probed
[    0.717917] PPP generic driver version 2.4.2
[    0.718135] tun: Universal TUN/TAP device driver, 1.6
[    0.718361] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.718688] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.718998] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.719328] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.719330] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.719592] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.730062] ehci_hcd 0000:00:1a.7: debug port 1
[    0.734160] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.734173] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xf3204800
[    0.750014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.750379] hub 1-0:1.0: USB hub found
[    0.750550] hub 1-0:1.0: 6 ports detected
[    0.750783] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.751108] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.751111] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.751369] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.760051] ehci_hcd 0000:00:1d.7: debug port 1
[    0.764158] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.764168] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf3204c00
[    0.780015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.780366] hub 2-0:1.0: USB hub found
[    0.780536] hub 2-0:1.0: 6 ports detected
[    0.780766] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.781052] uhci_hcd: USB Universal Host Controller Interface driver
[    0.781370] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.781692] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.781694] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.781953] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.790041] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00002100
[    0.790405] hub 3-0:1.0: USB hub found
[    0.790575] hub 3-0:1.0: 2 ports detected
[    0.790799] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.791121] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.791123] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.791388] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.791760] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00002120
[    0.792100] hub 4-0:1.0: USB hub found
[    0.792270] hub 4-0:1.0: 2 ports detected
[    0.806217] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.820236] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.820239] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.834082] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.847990] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00002140
[    0.861873] hub 5-0:1.0: USB hub found
[    0.875564] hub 5-0:1.0: 2 ports detected
[    0.889226] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.903010] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.903013] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.916685] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.930424] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002160
[    0.944102] hub 6-0:1.0: USB hub found
[    0.957699] hub 6-0:1.0: 2 ports detected
[    0.971185] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.984753] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.984756] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.998298] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.012000] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00002180
[    1.025767] hub 7-0:1.0: USB hub found
[    1.039373] hub 7-0:1.0: 2 ports detected
[    1.052919] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.066533] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.066535] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.079962] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.093401] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000021a0
[    1.106819] hub 8-0:1.0: USB hub found
[    1.120111] hub 8-0:1.0: 2 ports detected
[    1.133380] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    1.149388] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.162650] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.180872] mousedev: PS/2 mouse device common for all mice
[    1.193886] rtc_cmos 00:03: RTC can wake from S4
[    1.230082] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.243031] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.256362] device-mapper: uevent: version 1.0.3
[    1.269281] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.282444] device-mapper: multipath: version 1.2.0 loaded
[    1.295533] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.308609] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    1.308704] cpuidle: using governor ladder
[    1.335054] cpuidle: using governor menu
[    1.348300] TCP cubic registered
[    1.361464] NET: Registered protocol family 10
[    1.374874] NET: Registered protocol family 17
[    1.387841] Registering the dns_resolver key type
[    1.400878] PM: Hibernation image not present or could not be loaded.
[    1.400888] registered taskstats version 1
[    1.413946]   Magic number: 3:569:527
[    1.426772] rtc_cmos 00:03: setting system clock to 2011-03-14 10:32:53 UTC (1300098773)
[    1.439770] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.452799] EDD information not available.
[    1.467110] Freeing unused kernel memory: 960k freed
[    1.480395] Write protecting the kernel read-only data: 10240k
[    1.494130] Freeing unused kernel memory: 192k freed
[    1.511058] Freeing unused kernel memory: 1440k freed
[    1.559662] udev[77]: starting version 167
[    1.660031] usb 6-2: new low speed USB device using uhci_hcd and address 3
[    1.676095] ahci 0000:00:1f.2: version 3.0
[    1.676117] ahci 0000:00:1f.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.690387] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.690395] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
[    1.704419] tg3.c:v3.116 (December 3, 2010)
[    1.716992] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    1.716995] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ccc sxs 
[    1.716998] ahci 0000:00:1f.2: setting latency timer to 64
[    1.747890] tg3 0000:3f:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.748826] scsi0 : ahci
[    1.776204] tg3 0000:3f:00.0: setting latency timer to 64
[    1.778089] FDC 0 is a post-1991 82077
[    1.793556] scsi1 : ahci
[    1.807694] scsi2 : ahci
[    1.821414] scsi3 : ahci
[    1.835045] scsi4 : ahci
[    1.848461] scsi5 : ahci
[    1.850079] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input2
[    1.850156] generic-usb 0003:04F2:0111.0001: input,hidraw0: USB HID v1.10 Keyboard [Chicony USB Keyboard] on usb-0000:00:1d.0-1/input0
[    1.889870] ata1: SATA max UDMA/133 abar m2048@0xf3204000 port 0xf3204100 irq 44
[    1.904076] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    1.918408] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    1.932529] ata4: SATA max UDMA/133 abar m2048@0xf3204000 port 0xf3204280 irq 44
[    1.932573] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input3
[    1.932684] generic-usb 0003:04F2:0111.0002: input,hiddev0,hidraw1: USB HID v1.10 Device [Chicony USB Keyboard] on usb-0000:00:1d.0-1/input1
[    1.932696] usbcore: registered new interface driver usbhid
[    1.932697] usbhid: USB HID core driver
[    2.005438] ata5: SATA max UDMA/133 abar m2048@0xf3204000 port 0xf3204300 irq 44
[    2.020556] ata6: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    2.053310] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input4
[    2.069168] generic-usb 0003:046D:C019.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[    2.094401] tg3 0000:3f:00.0: eth0: Tigon3 [partno(BCM95755) rev a002] (PCI Express) MAC address 00:26:55:46:04:f0
[    2.110435] tg3 0000:3f:00.0: eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.126609] tg3 0000:3f:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.142786] tg3 0000:3f:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.200017] usb 7-2: new low speed USB device using uhci_hcd and address 2
[    2.380031] ata4: SATA link down (SStatus 0 SControl 300)
[    2.396316] ata1: SATA link down (SStatus 0 SControl 300)
[    2.412442] ata5: SATA link down (SStatus 0 SControl 300)
[    2.448001] input: Microsoft Comfort Optical Mouse 1000 as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input5
[    2.464807] generic-usb 0003:045E:00F6.0004: input,hidraw3: USB HID v1.11 Mouse [Microsoft Comfort Optical Mouse 1000] on usb-0000:00:1d.1-2/input0
[    2.780024] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.797014] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.813869] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.830522] ata6.00: ATA-7: TS128GSSD18M-M, v090331, max UDMA/133
[    2.830524] ata6.00: 252411904 sectors, multi 1: LBA48 NCQ (depth 1), AA
[    2.830535] ata2.00: ATA-8: ST3250318AS, HP34, max UDMA/100
[    2.830536] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.831458] ata2.00: configured for UDMA/100
[    2.831550] scsi 1:0:0:0: Direct-Access     ATA      ST3250318AS      HP34 PQ: 0 ANSI: 5
[    2.831694] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.831852] sd 1:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.831891] sd 1:0:0:0: [sda] Write Protect is off
[    2.831893] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.831910] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.834146] ata6.00: configured for UDMA/133
[    2.834158] ata3.00: ATAPI: hp      DVD-RAM GH40L, RB0E, max UDMA/100
[    2.840860]  sda: sda1
[    2.864208] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.048905] ata3.00: configured for UDMA/100
[    3.084326] scsi 2:0:0:0: CD-ROM            hp       DVD-RAM GH40L    RB0E PQ: 0 ANSI: 5
[    3.110232] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.127518] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.145143] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.145242] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    3.162905] scsi 5:0:0:0: Direct-Access     ATA      TS128GSSD18M-M   v090 PQ: 0 ANSI: 5
[    3.180673] sd 5:0:0:0: [sdb] 252411904 512-byte logical blocks: (129 GB/120 GiB)
[    3.180691] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    3.216121] sd 5:0:0:0: [sdb] Write Protect is off
[    3.233617] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.233642] sd 5:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.251667]  sdb: sdb1 sdb2
[    3.269416] sd 5:0:0:0: [sdb] Attached SCSI disk
[    3.336547] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    3.354542] EXT4-fs (sdb1): write access will be enabled during recovery
[    3.768883] EXT4-fs (sdb1): orphan cleanup on readonly fs
[    3.786682] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 2360869
[    3.786730] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 2628529
[    3.786753] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 2623321
[    3.786774] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 2490505
[    3.786785] EXT4-fs (sdb1): ext4_orphan_cleanup: deleting unreferenced inode 2622967
[    3.786795] EXT4-fs (sdb1): 5 orphan inodes deleted
[    3.804544] EXT4-fs (sdb1): recovery complete
[    3.851743] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    9.575481] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    9.575691] udev[433]: starting version 167
[    9.604860] lp: driver loaded but no devices found
[    9.665126] EDAC MC: Ver: 2.1.0 Mar  8 2011
[    9.717035] [drm] Initialized drm 1.1.0 20060810
[    9.770129] type=1400 audit(1300098781.842:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=713 comm="apparmor_parser"
[    9.770612] type=1400 audit(1300098781.842:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=713 comm="apparmor_parser"
[    9.770864] type=1400 audit(1300098781.842:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=713 comm="apparmor_parser"
[    9.898910] type=1400 audit(1300098781.962:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=786 comm="apparmor_parser"
[    9.899439] type=1400 audit(1300098781.962:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=786 comm="apparmor_parser"
[    9.899692] type=1400 audit(1300098781.962:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=786 comm="apparmor_parser"
[    9.908198] type=1400 audit(1300098781.972:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=785 comm="apparmor_parser"
[    9.915720] type=1400 audit(1300098781.982:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=793 comm="apparmor_parser"
[    9.917746] type=1400 audit(1300098781.982:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=791 comm="apparmor_parser"
[    9.923328] type=1400 audit(1300098781.992:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/clamd" pid=794 comm="apparmor_parser"
[    9.956854] parport_pc 00:07: [irq 5]
[    9.956858] parport_pc 00:07: [dma 1]
[    9.956864] parport_pc 00:07: [io  0x0378-0x037f]
[    9.956868] parport_pc 00:07: [io  0x0778-0x077d]
[    9.967505] parport_pc 00:07: activated
[    9.967511] parport_pc 00:07: reported by Plug and Play ACPI
[    9.967564] parport0: PC-style at 0x378 (0x778), irq 5, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    9.995557] EDAC MC0: Giving out device to 'x38_edac' 'x38': DEV 0000:00:00.0
[   10.031173] udev[525]: renamed network interface eth0 to eth2
[   10.052385] lp0: using parport0 (interrupt-driven).
[   10.053383] tg3 0000:3f:00.0: irq 45 for MSI/MSI-X
[   10.061196] tpm_tis 00:0b: 1.2 TPM (device-id 0x1002, rev-id 2)
[   10.084789] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.084794] nouveau 0000:01:00.0: setting latency timer to 64
[   10.097196] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   10.141157] ppdev: user-space parallel port driver
[   10.265432] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a5000a2)
[   10.265436] checking generic (f1000000 760000) vs hw (e0000000 10000000)
[   10.265438] checking generic (f1000000 760000) vs hw (f0000000 2000000)
[   10.265440] fb: conflicting fb hw usage nouveaufb vs VESA VGA - removing generic driver
[   10.265877] Console: switching to colour dummy device 80x25
[   10.348241] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   10.433810] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   10.433814] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   10.433817] [drm] nouveau 0000:01:00.0: Bios version 70.16.2e.00
[   10.433819] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
[   10.433826] [drm] nouveau 0000:01:00.0: TMDS table version 2.0
[   10.433828] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[   10.433831] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000302 00020030
[   10.433833] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 02000300 00000000
[   10.433834] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01032310 00000000
[   10.433836] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02021362 00020010
[   10.433838] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[   10.433840] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   10.433842] [drm] nouveau 0000:01:00.0:   1: 0x00002161: type 0x61 idx 1 tag 0x08
[   10.433844] [drm] nouveau 0000:01:00.0:   2: 0x00000200: type 0x00 idx 2 tag 0xff
[   10.433848] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD3F5
[   10.500028] [drm] nouveau 0000:01:00.0: 0xD717: Condition still not met after 20ms, skipping following opcodes
[   10.509282] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.509336] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   10.509359] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.530027] [drm] nouveau 0000:01:00.0: 0xD71B: Condition still not met after 20ms, skipping following opcodes
[   10.530050] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD905
[   10.590078] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE78C
[   10.590089] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE7CA
[   10.590384] input: HP WMI hotkeys as /devices/virtual/input/input6
[   10.597632] hda_codec: ALC262: SKU not ready 0x411111f0
[   10.651580] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEA0A
[   10.651583] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xEA6F
[   10.680033] [drm] nouveau 0000:01:00.0: 0xEA6F: Condition still not met after 20ms, skipping following opcodes
[   12.174651] [drm] nouveau 0000:01:00.0: 3 available performance level(s)
[   12.174656] [drm] nouveau 0000:01:00.0: 0: memory 135MHz core 135MHz shader 270MHz voltage 900mV
[   12.174658] [drm] nouveau 0000:01:00.0: 1: memory 324MHz core 405MHz shader 810MHz voltage 900mV
[   12.174661] [drm] nouveau 0000:01:00.0: 3: memory 400MHz core 625MHz shader 1360MHz voltage 1000mV
[   12.174678] [drm] nouveau 0000:01:00.0: c: memory 950MHz core 550MHz shader 1400MHz voltage 900mV
[   12.174964] [TTM] Zone  kernel: Available graphics memory: 2020232 kiB.
[   12.174966] [TTM] Initializing pool allocator.
[   12.174980] [drm] nouveau 0000:01:00.0: Detected 1024MiB VRAM
[   12.174993] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   12.185833] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   12.207814] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.207816] [drm] No driver support for vblank timestamp query.
[   12.488554] [drm] nouveau 0000:01:00.0: allocated 1920x1200 fb: 0x60000000, bo ffff8800d2c93c00
[   12.490129] Console: switching to colour frame buffer device 240x75
[   12.492604] fb0: nouveaufb frame buffer device
[   12.492607] drm: registered panic notifier
[   12.492652] [drm] Initialized nouveau 0.0.16 20090420 for 0000:01:00.0 on minor 0
[   12.492722] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.492727] hda_intel: Disable MSI for Nvidia chipset
[   12.492788] HDA Intel 0000:01:00.1: setting latency timer to 64
[   13.072361] watchdog (1873): /proc/1873/oom_adj is deprecated, please use /proc/1873/oom_score_adj instead.
[   13.307410] tg3 0000:3f:00.0: eth2: Link is up at 1000 Mbps, full duplex
[   13.307412] tg3 0000:3f:00.0: eth2: Flow control is off for TX and off for RX
[   13.307767] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   14.330628] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   15.457544] audit_printk_skb: 15 callbacks suppressed
[   15.457547] type=1400 audit(1300098787.522:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=2053 comm="apparmor_parser"
[   15.458113] type=1400 audit(1300098787.522:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=2053 comm="apparmor_parser"
[   19.280224] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.120007] eth2: no IPv6 routers present
[   27.034528] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```

---

### Post by flying_surprise on 2011-04-18
What kind of hang do you mean?

Kernel Panic? (scroll lock (?) blinking)
Graphics not redrawing correctly?
Mouse pointer freeze?

---

