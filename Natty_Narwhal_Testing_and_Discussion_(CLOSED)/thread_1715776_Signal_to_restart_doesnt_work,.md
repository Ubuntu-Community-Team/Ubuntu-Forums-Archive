---
title: "Signal to restart doesnt work,"
date: 2011-03-27
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-03-27
When i have to restart my system with natty the restart doesnt work correctly, i think it sends incorrect signals to my mobo because ubuntu looks like it shuts down but just hangs on a blank screen when trying to shut off/re-turn on. Im also finding that when i shut down it shuts off okay but will not start the next time i go to use my machine without doing a hard reset, im sure these problems are linked because they both seem to be a problem with the way ubuntu interacts with the mobo and i dont have this problem on the same machine if i revert to 10.10. 

Is anyone else experiencing this or have any ideas about this bug. My mobo is and asus mn378

---

### Post by Hakunka-Matata on 2011-03-28
+1 CaptainMark
Every time I attempt a restart, system shuts down, leaves power on box turned on, but I must hit the Reset Button on box to restart.  I've tried all sorts of different BIOS APIC settings, and power management, nothing helps.

Also if I turn off power to the Box, and turn back on, I must STILL hit reset button before system restarts.  Natty-11.04.amd64 - Desktop, with daily updates
Other than that, Natty ROCKS!

---

### Post by frodowiz on 2011-04-06
same here it wasnt until the last round of updates this began happening :)
linux-rules               
```
    description: Notebook
    product: HP G60 Notebook PC (NV225UA#ABA)
    vendor: Hewlett-Packard
    version: F.3E
    serial: 2CE934DYL4
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=oem-specific chassis=notebook family=103C_5335KV sku=NV225UA#ABA uuid=9321F160-94D4-11DE-B90A-E803359233F0
  *-core
       description: Motherboard
       product: 303C
       vendor: Wistron
       physical id: 0
       version: 08.60
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.3E
          date: 06/23/2009
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion Dual-Core RM-75
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: AMD Turion Dual-Core RM-75
          slot: Socket A
          size: 550MHz
          capacity: 2200MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DRAM Synchronous 800 MHz (1.2 ns)
             physical id: 0
             slot: S1
             size: 2GiB
             width: 32 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DRAM Synchronous 800 MHz (1.2 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1a00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:c0080000-c00fffff
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0006000-c0006fff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0007000-c00070ff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0008000-c0008fff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0007400-c00074ff
     *-ide:0
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:c0000000-c0003fff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi3
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:40 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:c0004000-c0005fff
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT20L
             vendor: hp
             physical id: 0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: DC05
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: ST9500420AS
             vendor: Seagate
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 0002
             serial: 5VJ3AH53
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000432d7
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /media/sda1
                version: 1.0
                serial: 2013e24d-7d31-44ff-a75c-be3966040cda
                size: 146GiB
                capacity: 146GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2010-11-06 23:26:02 filesystem=ext4 label=ubu10.10 lastmountpoint=/media/sda1 modified=2011-04-06 08:44:09 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-04-05 13:03:36 state=mounted
           *-volume:1
                description: EXT3 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                logical name: /media/sda2
                version: 1.0
                serial: 6578b2e8-8b98-49b2-8ee9-6f1f6872a355
                size: 18GiB
                capacity: 18GiB
                capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                configuration: created=2011-04-05 00:10:17 filesystem=ext3 modified=2011-04-06 08:44:11 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,commit=5,barrier=0,data=ordered mounted=2011-04-06 08:44:11 state=mounted
           *-volume:2
                description: Extended partition
                physical id: 4
                bus info: scsi@4:0.0.0,4
                logical name: /dev/sda4
                size: 18GiB
                capacity: 18GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 18GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1f:16:e7:7a:73
          capacity: 100Mbit/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:41 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht normal_decode bus_master cap_list
          resources: ioport:4000(size=4096) memory:c1000000-c1ffffff ioport:c4000000(size=469762048)
        *-display
             description: VGA compatible controller
             product: C77 [GeForce 8200M G]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:19 memory:c1000000-c1ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:4000(size=128) memory:c6000000-c601ffff
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:23 memory:c2000000-c20fffff
        *-network
             description: Wireless interface
             product: AR5001 Wireless Network Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:26:5e:4d:a4:f0
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=2.6.38-7-generic firmware=N/A ip=172.16.60.97 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
             resources: irq:23 memory:c2000000-c200ffff
     *-pci:3
          description: Host bridge
          product: Family 11h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 11h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 11h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: c
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 1962MiB (2057MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000dcbaa
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/PARTEDMAGIC
                version: FAT32
                serial: b83c-70b4
                size: 1961MiB
                capacity: 1961MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=PARTEDMAGIC mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
```

and yes, natty is looking great!

---

### Post by Hakunka-Matata on 2011-04-08
I'm still +1 on this.  Posted: output of dmesg

```
sudo dmesg > startuplogger.txt
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu1) ) #41-Ubuntu SMP Tue Apr 5 19:29:52 UTC 2011 (Ubuntu 2.6.38-8.41-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006ff80000 (usable)
[    0.000000]  BIOS-e820: 000000006ff80000 - 000000006ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006ff8e000 - 000000006ffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006ffd0000 - 0000000070000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M3A78-CM, BIOS 2801    08/23/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x6ff80 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFFC0000000 write-back
[    0.000000]   1 base 000040000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 000060000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3670e000 - 3737f000
[    0.000000] ACPI: RSDP 000fb520 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 6ff80000 00040 (v01 082310 RSDT1625 20100823 MSFT 00000097)
[    0.000000] ACPI: FACP 6ff80200 00084 (v01 082310 FACP1625 20100823 MSFT 00000097)
[    0.000000] ACPI: DSDT 6ff805d0 0733E (v01  A0901 A0901001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 6ff8e000 00040
[    0.000000] ACPI: APIC 6ff80390 0007C (v01 082310 APIC1625 20100823 MSFT 00000097)
[    0.000000] ACPI: MCFG 6ff80410 0003C (v01 082310 OEMMCFG  20100823 MSFT 00000097)
[    0.000000] ACPI: OEMB 6ff8e040 00071 (v01 082310 OEMB1625 20100823 MSFT 00000097)
[    0.000000] ACPI: SRAT 6ff87910 000B0 (v03 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 6ff879c0 00038 (v01 082310 OEMHPET  20100823 MSFT 00000097)
[    0.000000] ACPI: SSDT 6ff87a00 003FC (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 903MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0006ff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0006ff80
[    0.000000] On node 0 totalpages: 458510
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f590e200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1808 pages used for memmap
[    0.000000]   HighMem zone: 229490 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 70000000:8f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5400000 s28800 r0 d24448 u524288
[    0.000000] pcpu-alloc: s28800 r0 d24448 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454926
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=497a14e5-d299-43c7-ae42-3e835a4fce5a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9172160 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0006ff80)
[    0.000000] Memory: 1787492k/1834496k available (5188k kernel code, 46548k reserved, 2540k data, 700k init, 925192k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112d1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112d1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:728 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2400.500 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4801.00 BogoMIPS (lpj=9602000)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004038] Security Framework initialized
[    0.004058] AppArmor: AppArmor initialized
[    0.004060] Yama: becoming mindful.
[    0.004128] Mount-cache hash table entries: 512
[    0.004280] Initializing cgroup subsys ns
[    0.004284] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004288] Initializing cgroup subsys cpuacct
[    0.004294] Initializing cgroup subsys memory
[    0.004304] Initializing cgroup subsys devices
[    0.004307] Initializing cgroup subsys freezer
[    0.004310] Initializing cgroup subsys net_cls
[    0.004312] Initializing cgroup subsys blkio
[    0.004348] CPU: Physical Processor ID: 0
[    0.004351] CPU: Processor Core ID: 0
[    0.004354] mce: CPU supports 6 MCE banks
[    0.009609] ACPI: Core revision 20110112
[    0.014525] ftrace: allocating 23640 entries in 47 pages
[    0.016067] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016370] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057366] CPU0: AMD Phenom(tm) 8750 Triple-Core Processor stepping 03
[    0.060003] Performance Events: AMD PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              48
[    0.060003] ... generic registers:      4
[    0.060003] ... value mask:             0000ffffffffffff
[    0.060003] ... max period:             00007fffffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000000000f
[    0.060003] CPU 1 irqstacks, hard=f44d0000 soft=f44d2000
[    0.060003] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.148071] CPU 2 irqstacks, hard=f44dc000 soft=f44de000
[    0.148073]  #2
[    0.008000] Initializing CPU#2
[    0.240020] Brought up 3 CPUs
[    0.240023] Total of 3 processors activated (14401.82 BogoMIPS).
[    0.240745] devtmpfs: initialized
[    0.241180] print_constraints: dummy: 
[    0.241210] Time:  5:47:14  Date: 04/08/11
[    0.241243] NET: Registered protocol family 16
[    0.241326] EISA bus registered
[    0.241331] node 0 link 0: io port [1000, ffffff]
[    0.241335] TOM: 0000000080000000 aka 2048M
[    0.241337] Fam 10h mmconf [e0000000, efffffff]
[    0.241339] node 0 link 0: mmio [a0000, bffff]
[    0.241342] node 0 link 0: mmio [80000000, cfffffff]
[    0.241345] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.241349] node 0 link 0: mmio [f0000000, fbcfffff]
[    0.241351] node 0 link 0: mmio [fbd00000, fbdfffff]
[    0.241353] node 0 link 0: mmio [fbe00000, ffefffff]
[    0.241356] bus: [00, 07] on node 0 link 0
[    0.241359] bus: 00 index 0 [io  0x0000-0xffff]
[    0.241361] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.241363] bus: 00 index 2 [mem 0x80000000-0xdfffffff]
[    0.241365] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.241375] Extended Config Space enabled on 1 nodes
[    0.241252] Trying to unpack rootfs image as initramfs...
[    0.241385] ACPI: bus type pci registered
[    0.241453] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.241456] PCI: not using MMCONFIG
[    0.242168] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.242170] PCI: Using configuration type 1 for base access
[    0.242171] PCI: Using configuration type 1 for extended access
[    0.242192] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.242194] mtrr: probably your BIOS does not setup all CPUs.
[    0.242195] mtrr: corrected configuration.
[    0.244042] bio: create slab <bio-0> at 0
[    0.244936] ACPI: EC: Look up EC in DSDT
[    0.246461] ACPI: Executed 2 blocks of module-level executable AML code
[    0.292620] ACPI: Interpreter enabled
[    0.292625] ACPI: (supports S0 S1 S3 S4 S5)
[    0.292645] ACPI: Using IOAPIC for interrupt routing
[    0.292667] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.294330] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.294333] PCI: Using MMCONFIG for extended config space
[    0.516805] ACPI: No dock devices found.
[    0.516807] HEST: Table not found.
[    0.516812] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.516888] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.517039] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.517042] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.517045] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.517047] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.517050] pci_root PNP0A03:00: host bridge window [mem 0x70000000-0xdfffffff]
[    0.517052] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfed44fff]
[    0.517070] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    0.517116] pci 0000:00:01.0: [1043:9602] type 1 class 0x000604
[    0.517153] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
[    0.517180] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.517183] pci 0000:00:06.0: PME# disabled
[    0.517215] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.517235] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.517245] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.517255] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.517265] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.517275] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.517285] pci 0000:00:11.0: reg 24: [mem 0xfbcff800-0xfbcffbff]
[    0.517306] pci 0000:00:11.0: set SATA to AHCI mode
[    0.517340] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.517354] pci 0000:00:12.0: reg 10: [mem 0xfbcfe000-0xfbcfefff]
[    0.517418] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.517432] pci 0000:00:12.1: reg 10: [mem 0xfbcfd000-0xfbcfdfff]
[    0.517502] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.517521] pci 0000:00:12.2: reg 10: [mem 0xfbcff000-0xfbcff0ff]
[    0.517592] pci 0000:00:12.2: supports D1 D2
[    0.517594] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.517598] pci 0000:00:12.2: PME# disabled
[    0.517619] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.517633] pci 0000:00:13.0: reg 10: [mem 0xfbcfc000-0xfbcfcfff]
[    0.517697] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.517710] pci 0000:00:13.1: reg 10: [mem 0xfbcfb000-0xfbcfbfff]
[    0.517779] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.517799] pci 0000:00:13.2: reg 10: [mem 0xfbcfa800-0xfbcfa8ff]
[    0.517869] pci 0000:00:13.2: supports D1 D2
[    0.517871] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.517875] pci 0000:00:13.2: PME# disabled
[    0.517899] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.517992] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.518009] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.518019] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.518028] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.518038] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.518048] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.518097] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.518120] pci 0000:00:14.2: reg 10: [mem 0xfbcf4000-0xfbcf7fff 64bit]
[    0.518178] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.518182] pci 0000:00:14.2: PME# disabled
[    0.518195] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.518270] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.518311] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.518325] pci 0000:00:14.5: reg 10: [mem 0xfbcf9000-0xfbcf9fff]
[    0.518392] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.518408] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.518422] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.518436] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.518452] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.518500] pci 0000:01:05.0: [1002:9611] type 0 class 0x000300
[    0.518509] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.518514] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
[    0.518518] pci 0000:01:05.0: reg 18: [mem 0xfbef0000-0xfbefffff]
[    0.518529] pci 0000:01:05.0: reg 24: [mem 0xfbd00000-0xfbdfffff]
[    0.518542] pci 0000:01:05.0: supports D1 D2
[    0.518581] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.518585] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.518588] pci 0000:00:01.0:   bridge window [mem 0xfbd00000-0xfbefffff]
[    0.518592] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.518630] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.518643] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.518663] pci 0000:02:00.0: reg 18: [mem 0xfbfff000-0xfbffffff 64bit]
[    0.518677] pci 0000:02:00.0: reg 20: [mem 0xfaff0000-0xfaffffff 64bit pref]
[    0.518687] pci 0000:02:00.0: reg 30: [mem 0xfbfc0000-0xfbfdffff pref]
[    0.518715] pci 0000:02:00.0: supports D1 D2
[    0.518717] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.518721] pci 0000:02:00.0: PME# disabled
[    0.524044] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.524048] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    0.524051] pci 0000:00:06.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.524055] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.524116] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.524121] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.524126] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.524130] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.524133] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.524135] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.524138] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.524140] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.524142] pci 0000:00:14.4:   bridge window [mem 0x70000000-0xdfffffff] (subtractive decode)
[    0.524145] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfed44fff] (subtractive decode)
[    0.524157] pci_bus 0000:00: on NUMA node 0
[    0.524160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.524358] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.524392] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.524439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.524499]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.527299] Freeing initrd memory: 12740k freed
[    0.528801] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.528840] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.528875] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.528908] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.528941] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.528977] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.529012] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 *11 12 14 15)
[    0.529046] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.529210] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.529213] vgaarb: loaded
[    0.529464] SCSI subsystem initialized
[    0.529486] libata version 3.00 loaded.
[    0.529486] usbcore: registered new interface driver usbfs
[    0.529486] usbcore: registered new interface driver hub
[    0.529486] usbcore: registered new device driver usb
[    0.529486] wmi: Mapper loaded
[    0.529486] PCI: Using ACPI for IRQ routing
[    0.529486] PCI: pci_cache_line_size set to 64 bytes
[    0.529486] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.529486] reserve RAM buffer: 000000006ff80000 - 000000006fffffff 
[    0.529486] NetLabel: Initializing
[    0.529486] NetLabel:  domain hash size = 128
[    0.529486] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.529486] NetLabel:  unlabeled traffic allowed by default
[    0.529486] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.529486] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.532061] Switching to clocksource hpet
[    0.534645] Switched to NOHz mode on CPU #0
[    0.534749] Switched to NOHz mode on CPU #2
[    0.534776] Switched to NOHz mode on CPU #1
[    0.538064] AppArmor: AppArmor Filesystem Enabled
[    0.538092] pnp: PnP ACPI init
[    0.538110] ACPI: bus type pnp registered
[    0.538241] pnp 00:00: [bus 00-ff]
[    0.538244] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.538246] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.538248] pnp 00:00: [io  0x0d00-0xffff window]
[    0.538251] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.538253] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.538255] pnp 00:00: [mem 0x70000000-0xdfffffff window]
[    0.538258] pnp 00:00: [mem 0xf0000000-0xfed44fff window]
[    0.538318] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.538404] pnp 00:01: [mem 0x00000000-0xffffffff disabled]
[    0.538407] pnp 00:01: [mem 0x70000000-0x7fffffff]
[    0.538458] system 00:01: [mem 0x70000000-0x7fffffff] has been reserved
[    0.538462] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.538503] pnp 00:02: [dma 4]
[    0.538505] pnp 00:02: [io  0x0000-0x000f]
[    0.538508] pnp 00:02: [io  0x0081-0x0083]
[    0.538510] pnp 00:02: [io  0x0087]
[    0.538511] pnp 00:02: [io  0x0089-0x008b]
[    0.538513] pnp 00:02: [io  0x008f]
[    0.538515] pnp 00:02: [io  0x00c0-0x00df]
[    0.538541] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.538552] pnp 00:03: [io  0x0070-0x0071]
[    0.538577] pnp 00:03: [irq 8]
[    0.538608] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.538619] pnp 00:04: [io  0x0061]
[    0.538644] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.538655] pnp 00:05: [io  0x00f0-0x00ff]
[    0.538659] pnp 00:05: [irq 13]
[    0.538687] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.539215] pnp 00:06: [io  0x03f0-0x03f5]
[    0.539219] pnp 00:06: [io  0x03f7]
[    0.539223] pnp 00:06: [irq 6]
[    0.539225] pnp 00:06: [dma 2]
[    0.539287] pnp 00:06: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.539944] pnp 00:07: [io  0x0378-0x037f]
[    0.539948] pnp 00:07: [irq 7]
[    0.539955] pnp 00:07: [dma 0 disabled]
[    0.540217] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.540246] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.540282] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.540758] pnp 00:09: [io  0x03f8-0x03ff]
[    0.540762] pnp 00:09: [irq 4]
[    0.540764] pnp 00:09: [dma 0 disabled]
[    0.540847] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.540922] pnp 00:0a: [io  0x0060]
[    0.540924] pnp 00:0a: [io  0x0064]
[    0.540926] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.540928] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.540982] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.540985] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.540988] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.541060] pnp 00:0b: [io  0x0010-0x001f]
[    0.541062] pnp 00:0b: [io  0x0022-0x003f]
[    0.541064] pnp 00:0b: [io  0x0062-0x0063]
[    0.541065] pnp 00:0b: [io  0x0065-0x006f]
[    0.541067] pnp 00:0b: [io  0x0072-0x007f]
[    0.541072] pnp 00:0b: [io  0x0080]
[    0.541074] pnp 00:0b: [io  0x0084-0x0086]
[    0.541076] pnp 00:0b: [io  0x0088]
[    0.541077] pnp 00:0b: [io  0x008c-0x008e]
[    0.541079] pnp 00:0b: [io  0x0090-0x009f]
[    0.541081] pnp 00:0b: [io  0x00a2-0x00bf]
[    0.541083] pnp 00:0b: [io  0x00b1]
[    0.541085] pnp 00:0b: [io  0x00e0-0x00ef]
[    0.541086] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.541088] pnp 00:0b: [io  0x040b]
[    0.541093] pnp 00:0b: [io  0x04d6]
[    0.541095] pnp 00:0b: [io  0x0c00-0x0c01]
[    0.541097] pnp 00:0b: [io  0x0c14]
[    0.541098] pnp 00:0b: [io  0x0c50-0x0c51]
[    0.541100] pnp 00:0b: [io  0x0c52]
[    0.541104] pnp 00:0b: [io  0x0c6c]
[    0.541106] pnp 00:0b: [io  0x0c6f]
[    0.541108] pnp 00:0b: [io  0x0cd0-0x0cd1]
[    0.541109] pnp 00:0b: [io  0x0cd2-0x0cd3]
[    0.541111] pnp 00:0b: [io  0x0cd4-0x0cd5]
[    0.541113] pnp 00:0b: [io  0x0cd6-0x0cd7]
[    0.541115] pnp 00:0b: [io  0x0cd8-0x0cdf]
[    0.541117] pnp 00:0b: [io  0x0b00-0x0b3f]
[    0.541119] pnp 00:0b: [io  0x0800-0x089f]
[    0.541120] pnp 00:0b: [io  0x0b20-0x0b2f]
[    0.541122] pnp 00:0b: [io  0x0000-0xffffffff disabled]
[    0.541124] pnp 00:0b: [io  0x0900-0x090f]
[    0.541126] pnp 00:0b: [io  0x0910-0x091f]
[    0.541128] pnp 00:0b: [io  0xfe00-0xfefe]
[    0.541130] pnp 00:0b: [mem 0xffb80000-0xffbfffff]
[    0.541132] pnp 00:0b: [mem 0xfec10000-0xfec1001f]
[    0.541134] pnp 00:0b: [mem 0xfed40000-0xfed44fff]
[    0.541231] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.541233] system 00:0b: [io  0x040b] has been reserved
[    0.541235] system 00:0b: [io  0x04d6] has been reserved
[    0.541238] system 00:0b: [io  0x0c00-0x0c01] has been reserved
[    0.541240] system 00:0b: [io  0x0c14] has been reserved
[    0.541242] system 00:0b: [io  0x0c50-0x0c51] has been reserved
[    0.541245] system 00:0b: [io  0x0c52] has been reserved
[    0.541247] system 00:0b: [io  0x0c6c] has been reserved
[    0.541249] system 00:0b: [io  0x0c6f] has been reserved
[    0.541251] system 00:0b: [io  0x0cd0-0x0cd1] has been reserved
[    0.541254] system 00:0b: [io  0x0cd2-0x0cd3] has been reserved
[    0.541256] system 00:0b: [io  0x0cd4-0x0cd5] has been reserved
[    0.541258] system 00:0b: [io  0x0cd6-0x0cd7] has been reserved
[    0.541261] system 00:0b: [io  0x0cd8-0x0cdf] has been reserved
[    0.541263] system 00:0b: [io  0x0b00-0x0b3f] has been reserved
[    0.541265] system 00:0b: [io  0x0800-0x089f] has been reserved
[    0.541268] system 00:0b: [io  0x0b20-0x0b2f] has been reserved
[    0.541270] system 00:0b: [io  0x0900-0x090f] has been reserved
[    0.541273] system 00:0b: [io  0x0910-0x091f] has been reserved
[    0.541275] system 00:0b: [io  0xfe00-0xfefe] has been reserved
[    0.541278] system 00:0b: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.541281] system 00:0b: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.541284] system 00:0b: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.541287] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.541419] pnp 00:0c: [io  0x0000-0xffffffff disabled]
[    0.541421] pnp 00:0c: [io  0x0230-0x023f]
[    0.541423] pnp 00:0c: [io  0x0290-0x029f]
[    0.541425] pnp 00:0c: [io  0x0300-0x030f]
[    0.541427] pnp 00:0c: [io  0x0a30-0x0a3f]
[    0.541481] system 00:0c: [io  0x0230-0x023f] has been reserved
[    0.541483] system 00:0c: [io  0x0290-0x029f] has been reserved
[    0.541486] system 00:0c: [io  0x0300-0x030f] has been reserved
[    0.541488] system 00:0c: [io  0x0a30-0x0a3f] has been reserved
[    0.541491] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.541529] pnp 00:0d: [mem 0xe0000000-0xefffffff]
[    0.541583] system 00:0d: [mem 0xe0000000-0xefffffff] has been reserved
[    0.541586] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.556333] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    0.556335] pnp 00:0e: [mem 0x000c0000-0x000cffff]
[    0.556337] pnp 00:0e: [mem 0x000e0000-0x000fffff]
[    0.556339] pnp 00:0e: [mem 0x00100000-0x6fffffff]
[    0.556341] pnp 00:0e: [mem 0xfed45000-0xffffffff]
[    0.556403] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.556406] system 00:0e: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.556409] system 00:0e: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.556412] system 00:0e: [mem 0x00100000-0x6fffffff] could not be reserved
[    0.556414] system 00:0e: [mem 0xfed45000-0xffffffff] could not be reserved
[    0.556417] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.556502] pnp: PnP ACPI: found 15 devices
[    0.556504] ACPI: ACPI bus type pnp unregistered
[    0.556507] PnPBIOS: Disabled by ACPI PNP
[    0.592834] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.592838] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.592841] pci 0000:00:01.0:   bridge window [mem 0xfbd00000-0xfbefffff]
[    0.592845] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.592849] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.592851] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    0.592855] pci 0000:00:06.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.592858] pci 0000:00:06.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.592862] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.592864] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.592869] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.592873] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.592894] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.592897] pci 0000:00:06.0: setting latency timer to 64
[    0.592905] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.592907] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.592909] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.592912] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.592914] pci_bus 0000:00: resource 8 [mem 0x70000000-0xdfffffff]
[    0.592916] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.592919] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.592921] pci_bus 0000:01: resource 1 [mem 0xfbd00000-0xfbefffff]
[    0.592923] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.592926] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.592928] pci_bus 0000:02: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.592931] pci_bus 0000:02: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.592933] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.592936] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.592939] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.592941] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.592943] pci_bus 0000:03: resource 8 [mem 0x70000000-0xdfffffff]
[    0.592946] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.592982] NET: Registered protocol family 2
[    0.593059] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.593302] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.593903] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.594193] TCP: Hash tables configured (established 131072 bind 65536)
[    0.594196] TCP reno registered
[    0.594199] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.594210] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.594294] NET: Registered protocol family 1
[    0.594304] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.740031] pci 0000:01:05.0: Boot video device
[    0.740036] PCI: CLS 64 bytes, default 64
[    0.740320] cpufreq-nforce2: No nForce2 chipset.
[    0.740434] audit: initializing netlink socket (disabled)
[    0.740442] type=2000 audit(1302241633.736:1): initialized
[    0.749241] highmem bounce pool size: 64 pages
[    0.749246] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.750967] VFS: Disk quotas dquot_6.5.2
[    0.751031] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.751783] fuse init (API version 7.16)
[    0.751883] msgmni has been set to 1709
[    0.752217] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.752257] io scheduler noop registered
[    0.752259] io scheduler deadline registered
[    0.752278] io scheduler cfq registered (default)
[    0.752382] pcieport 0000:00:06.0: setting latency timer to 64
[    0.752417] pcieport 0000:00:06.0: irq 40 for MSI/MSI-X
[    0.752481] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.752502] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.752649] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.752655] ACPI: Power Button [PWRB]
[    0.752705] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.752708] ACPI: Power Button [PWRF]
[    0.752878] ACPI: acpi_idle registered with cpuidle
[    0.832327] ERST: Table is not found!
[    0.832394] isapnp: Scanning for PnP cards...
[    0.832413] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.852883] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.189499] isapnp: No Plug & Play device found
[    1.404618] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.404896] Linux agpgart interface v0.103
[    1.406290] brd: module loaded
[    1.406882] loop: module loaded
[    1.406962] i2c-core: driver [adp5520] using legacy suspend method
[    1.406963] i2c-core: driver [adp5520] using legacy resume method
[    1.407092] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.407123] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.407422] Fixed MDIO Bus: probed
[    1.407455] PPP generic driver version 2.4.2
[    1.407490] tun: Universal TUN/TAP device driver, 1.6
[    1.407492] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.407571] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.407591] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.407603] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.407641] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.408045] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.408061] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.408074] ehci_hcd 0000:00:12.2: debug port 1
[    1.408098] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbcff000
[    1.420031] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.420159] hub 1-0:1.0: USB hub found
[    1.420164] hub 1-0:1.0: 6 ports detected
[    1.420259] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.420270] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.420314] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.420351] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.420367] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.420381] ehci_hcd 0000:00:13.2: debug port 1
[    1.420405] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbcfa800
[    1.432031] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.432146] hub 2-0:1.0: USB hub found
[    1.432150] hub 2-0:1.0: 6 ports detected
[    1.432238] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.432253] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.432263] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.432298] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.432358] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbcfe000
[    1.492113] hub 3-0:1.0: USB hub found
[    1.492123] hub 3-0:1.0: 3 ports detected
[    1.492193] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.492203] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.492239] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.492289] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbcfd000
[    1.552112] hub 4-0:1.0: USB hub found
[    1.552124] hub 4-0:1.0: 3 ports detected
[    1.552197] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.552207] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.552243] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.552294] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbcfc000
[    1.612109] hub 5-0:1.0: USB hub found
[    1.612120] hub 5-0:1.0: 3 ports detected
[    1.612212] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.612222] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.612259] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.616043] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbcfb000
[    1.676119] hub 6-0:1.0: USB hub found
[    1.676131] hub 6-0:1.0: 3 ports detected
[    1.676204] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.676213] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.676249] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.680049] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbcf9000
[    1.740021] Refined TSC clocksource calibration: 2400.085 MHz.
[    1.740024] Switching to clocksource tsc
[    1.740148] hub 7-0:1.0: USB hub found
[    1.740159] hub 7-0:1.0: 2 ports detected
[    1.740232] uhci_hcd: USB Universal Host Controller Interface driver
[    1.740308] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.740707] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.740713] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.740867] mousedev: PS/2 mouse device common for all mice
[    1.741001] rtc_cmos 00:03: RTC can wake from S4
[    1.764060] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.764085] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.764158] device-mapper: uevent: version 1.0.3
[    1.764238] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.764307] device-mapper: multipath: version 1.2.0 loaded
[    1.764309] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.764378] EISA: Probing bus 0 at eisa.0
[    1.764380] EISA: Cannot allocate resource for mainboard
[    1.764382] Cannot allocate resource for EISA slot 1
[    1.764383] Cannot allocate resource for EISA slot 2
[    1.764385] Cannot allocate resource for EISA slot 3
[    1.764386] Cannot allocate resource for EISA slot 4
[    1.764388] Cannot allocate resource for EISA slot 5
[    1.764390] Cannot allocate resource for EISA slot 6
[    1.764391] Cannot allocate resource for EISA slot 7
[    1.764393] Cannot allocate resource for EISA slot 8
[    1.764394] EISA: Detected 0 cards.
[    1.764445] cpuidle: using governor ladder
[    1.764447] cpuidle: using governor menu
[    1.764716] TCP cubic registered
[    1.764834] NET: Registered protocol family 10
[    1.765375] NET: Registered protocol family 17
[    1.765390] Registering the dns_resolver key type
[    1.765414] powernow-k8: Found 1 AMD Phenom(tm) 8750 Triple-Core Processor (3 cpu cores) (version 2.20.00)
[    1.765440] powernow-k8:    0 : pstate 0 (2400 MHz)
[    1.765442] powernow-k8:    1 : pstate 1 (1200 MHz)
[    1.765592] Using IPI No-Shortcut mode
[    1.765680] PM: Hibernation image not present or could not be loaded.
[    1.765691] registered taskstats version 1
[    1.765904]   Magic number: 7:351:769
[    1.765934] mem kmsg: hash matches
[    1.765990] rtc_cmos 00:03: setting system clock to 2011-04-08 05:47:15 UTC (1302241635)
[    1.765993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.765994] EDD information not available.
[    1.766081] Freeing unused kernel memory: 700k freed
[    1.766360] Write protecting the kernel text: 5192k
[    1.766402] Write protecting the kernel read-only data: 2148k
[    1.785731] <30>udev[66]: starting version 167
[    1.788349] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.795901] xor: automatically using best checksumming function: pIII_sse
[    1.812004]    pIII_sse  :  9807.000 MB/sec
[    1.812007] xor: using function: pIII_sse (9807.000 MB/sec)
[    1.814485] device-mapper: dm-raid45: initialized v0.2594b
[    1.850820] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.850846] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.850882] r8169 0000:02:00.0: setting latency timer to 64
[    1.850930] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
[    1.851429] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf8002000, 90:e6:ba:d9:3b:5c, XID 1c4000c0 IRQ 41
[    1.861335] scsi0 : pata_atiixp
[    1.864246] scsi1 : pata_atiixp
[    1.864711] Floppy drive(s): fd0 is 1.44M
[    1.864877] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.864880] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.866070] ahci 0000:00:11.0: version 3.0
[    1.866091] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.866206] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.866209] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.867025] scsi2 : ahci
[    1.867441] scsi3 : ahci
[    1.867505] scsi4 : ahci
[    1.867581] scsi5 : ahci
[    1.867713] ata3: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcff900 irq 22
[    1.867716] ata4: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcff980 irq 22
[    1.867720] ata5: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffa00 irq 22
[    1.867723] ata6: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffa80 irq 22
[    1.883800] FDC 0 is a post-1991 82077
[    2.188047] ata6: SATA link down (SStatus 0 SControl 300)
[    2.240024] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    2.356018] ata4: softreset failed (device not ready)
[    2.356022] ata4: applying SB600 PMP SRST workaround and retrying
[    2.356038] ata3: softreset failed (device not ready)
[    2.356042] ata3: applying SB600 PMP SRST workaround and retrying
[    2.360017] ata5: softreset failed (device not ready)
[    2.360020] ata5: applying SB600 PMP SRST workaround and retrying
[    2.468090] input: Microsoft Microsoft® Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input2
[    2.468174] generic-usb 0003:045E:00B0.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Digital Media Pro Keyboard] on usb-0000:00:12.0-1/input0
[    2.477209] input: Microsoft Microsoft® Digital Media Pro Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input3
[    2.477274] generic-usb 0003:045E:00B0.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Microsoft® Digital Media Pro Keyboard] on usb-0000:00:12.0-1/input1
[    2.477286] usbcore: registered new interface driver usbhid
[    2.477288] usbhid: USB HID core driver
[    2.528033] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.528058] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.528637] ata4.00: ATA-7: WDC WD800AAJS-60PSA0, 21.12M22, max UDMA/100
[    2.528640] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.529070] ata3.00: ATA-8: ST3250318AS, CC38, max UDMA/133
[    2.529072] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.529274] ata4.00: configured for UDMA/100
[    2.530239] ata3.00: configured for UDMA/133
[    2.530370] scsi 2:0:0:0: Direct-Access     ATA      ST3250318AS      CC38 PQ: 0 ANSI: 5
[    2.530542] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.530554] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.530595] sd 2:0:0:0: [sda] Write Protect is off
[    2.530598] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.530618] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.530679] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800AAJS-60 21.1 PQ: 0 ANSI: 5
[    2.530829] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.530916] sd 3:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.530988] sd 3:0:0:0: [sdb] Write Protect is off
[    2.530990] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.531018] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.532028] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.533064] ata5.00: ATA-8: ST3250318AS, CC38, max UDMA/133
[    2.533066] ata5.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.534268] ata5.00: configured for UDMA/133
[    2.534353] scsi 4:0:0:0: Direct-Access     ATA      ST3250318AS      CC38 PQ: 0 ANSI: 5
[    2.534469] sd 4:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.534505] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.534532] sd 4:0:0:0: [sdc] Write Protect is off
[    2.534536] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.534560] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.563495]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    2.563759] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.586977]  sdc: sdc1 sdc2 sdc3 < sdc5 sdc6 > sdc4
[    2.587399] sd 4:0:0:0: [sdc] Attached SCSI disk
[    2.641696]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    2.642167] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.676021] usb 4-3: new low speed USB device using ohci_hcd and address 2
[    2.876089] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4
[    2.876181] generic-usb 0003:045E:008A.0003: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:12.1-3/input0
[    2.907170] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input5
[    2.907270] generic-usb 0003:045E:008A.0004: input,hidraw3: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:12.1-3/input1
[    3.987463] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   11.803444] <30>udev[361]: starting version 167
[   11.817090] lp: driver loaded but no devices found
[   11.869416] parport_pc 00:07: reported by Plug and Play ACPI
[   11.869471] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.875033] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.884907] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.890552] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   11.893281] SP5100 TCO timer: Watchdog reboot not detected.
[   11.893363] SP5100 TCO timer: initialized (0xf80a40f0). heartbeat=60 sec (nowayout=0)
[   11.906318] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.906323] Disabling lock debugging due to kernel taint
[   11.928414] Adding 2150396k swap on /dev/sda7.  Priority:-1 extents:1 across:2150396k 
[   11.955520] type=1400 audit(1302256045.683:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=499 comm="apparmor_parser"
[   11.955854] type=1400 audit(1302256045.683:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=499 comm="apparmor_parser"
[   11.956084] type=1400 audit(1302256045.687:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=499 comm="apparmor_parser"
[   11.956181] lp0: using parport0 (interrupt-driven).
[   11.965274] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
[   11.994400] Adding 2048280k swap on /dev/sdb5.  Priority:-2 extents:1 across:2048280k 
[   12.079807] ppdev: user-space parallel port driver
[   12.107116] [fglrx] Maximum main memory to use for locked dma buffers: 1643 MBytes.
[   12.107175] [fglrx]   vendor: 1002 device: 9611 count: 1
[   12.107584] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
[   12.107597] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.107602] pci 0000:01:05.0: setting latency timer to 64
[   12.108018] [fglrx] Kernel PAT support is enabled
[   12.108042] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   12.145837] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.517096] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   13.604632] EXT4-fs (sda10): mounted filesystem with ordered data mode. Opts: (null)
[   15.074133] type=1400 audit(1302256048.803:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=904 comm="apparmor_parser"
[   15.074553] type=1400 audit(1302256048.803:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=904 comm="apparmor_parser"
[   15.076102] type=1400 audit(1302256048.807:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=906 comm="apparmor_parser"
[   15.076544] type=1400 audit(1302256048.807:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=906 comm="apparmor_parser"
[   15.076762] type=1400 audit(1302256048.807:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=906 comm="apparmor_parser"
[   15.079417] type=1400 audit(1302256048.807:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=905 comm="apparmor_parser"
[   15.082031] type=1400 audit(1302256048.811:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=907 comm="apparmor_parser"
[   15.141353] r8169 0000:02:00.0: eth0: link down
[   15.141363] r8169 0000:02:00.0: eth0: link down
[   15.141601] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.552789] [fglrx] GART Table is not in FRAME_BUFFER range 
[   15.552981] [fglrx] Could not enable MSI; System prevented initialization
[   15.553575] [fglrx] Firegl kernel thread PID: 1178
[   15.553665] [fglrx] Firegl kernel thread PID: 1179
[   15.553718] [fglrx] Firegl kernel thread PID: 1180
[   15.554089] [fglrx] IRQ 18 Enabled
[   15.813641] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   15.870202] EXT4-fs (sda10): re-mounted. Opts: commit=0
[   16.063510] [fglrx] Gart USWC size:552 M.
[   16.063513] [fglrx] Gart cacheable size:215 M.
[   16.063518] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   16.063521] [fglrx] Reserved FB block: Unshared offset:fffc000, size:4000 
[   17.511462] r8169 0000:02:00.0: eth0: link up
[   17.511690] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.977021] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   18.979631] EXT4-fs (sda10): re-mounted. Opts: commit=0
[   27.728013] eth0: no IPv6 routers present
```

---

### Post by CaptainMark on 2011-04-10
yeah I'm still the same, 11.04 is shaping up to be a right shambles so far, i don't get this problem with a kubuntu 11.04 live cd. I've burned a copy of opensuse 11.4 ready for ubuntu launch dates, if the huge list of disappointments isn't corrected by launch, I'm jumping ship

---

### Post by Quackers on 2011-04-10
This has happened to me, but only 3 or 4 times, in 11.04. Most of the time the shutdown and restart work fine. Just occasionally it will, as you say, appear to close down then hang at a black screen. At that point I press and hold Alt GR and Sys Rq keys and press R E I S U B to reboot. It's a bit safer than using the power button.

---

### Post by Hakunka-Matata on 2011-04-11
Yes Quackers, I do the same thiing, after rebooting with ALT SYS REQ "REISUB" I still have to do a hard reset on the box to start the POST process.  That is not a fix for my Motherboard BIOS combo

---

### Post by CaptainMark on 2011-04-11
mine just randomly seems to work today, run todays updates see what you get, i cant imagine it was anything else ive done, i installed starup-manager from software centre today but tis unlikely to be that

---

### Post by dino99 on 2011-04-11
its often the case when a process is still running when you shut down:

 like:
 freeing memory need few seconds after closing an app
 apparmor still busy
 syncing process
 ...

simply dont close app & shut down at same time can help
and watch logs to find usefull errors

you can force a fsck on next boot: sudo shutdown -r now

---

### Post by CaptainMark on 2011-04-11
no somethings defintely changed, i tried any number of combinations of shut downs, over the last 3 weeks or so and all of a sudden its just fine, 100% of the time and im not doing anything different in my shut down technique

---

