---
title: "Internal Laptop Mic not working in 10.04"
date: 2010-05-24
forum: Multimedia Software
---

### Post by Tombuddy on 2010-05-24
I have been going crazy with this maybe someone can help me out. I realized that in 10.04 my internal mic on my Asus G51VX does not work. 

I have already upgraded my ALSA Drivers using the latest 1.0.23, and in alsamixer it shows the iMic and Capture devices correctly, however in sound recorder and in Skype I get nothing but a low hissing sound. I believe this is a pulse audio problem and not ALSA since I didn't have a problem in Kubuntu 9.04 using ALSA which I had previously to this.

 In sound config pulseaudio shows that there is only one input and one output device which I figure should read 2 input devices since there is also a mic jack on the laptop. Either way it is really annoying not to have use of the Mic. 

Device is INTEL HD AUDIO ALC663

Simple mixer control 'i-Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]

When I turn the i-Mic on I can hear the echo of myself coming out the internal speakers but it still won't record anything even with the Capture control on and at full volume.

---

### Post by frozonecom on 2010-05-24
go to applications>>accessories>>terminal and type this:

```
sudo lspci
```

and post the output here.
```

cat /var/log/dmesg/
```

and post the output here.

---

### Post by Tombuddy on 2010-05-24
This is the output of lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260M] (rev a2)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

This is the output of cat /var/log/dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic-pae (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 (Ubuntu 2.6.32-22.33-generic-pae 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e1000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
[    0.000000]  BIOS-e820: 00000000bff80000 - 00000000bff8f000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff8f000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
[    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e1000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bff80000 (usable)
[    0.000000]  modified: 00000000bff80000 - 00000000bff8f000 (ACPI data)
[    0.000000]  modified: 00000000bff8f000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 10000-16000
[    0.000000] RAMDISK: 3736f000 - 37fef6cb
[    0.000000] Allocated new RAMDISK: 00938000 - 015b86cb
[    0.000000] Move RAMDISK from 000000003736f000 - 0000000037fef6ca to 00938000 - 015b86ca
[    0.000000] ACPI: RSDP 000f9370 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT bff80100 00084 (v01 _ASUS_ Notebook 20090527 MSFT 00000097)
[    0.000000] ACPI: FACP bff80290 000F4 (v03 052709 FACP1358 20090527 MSFT 00000097)
[    0.000000] ACPI: DSDT bff80690 0C20A (v01  G60VX G60VX001 00000001 INTL 20051117)
[    0.000000] ACPI: FACS bff8f000 00040
[    0.000000] ACPI: APIC bff80390 0006C (v01 052709 APIC1358 20090527 MSFT 00000097)
[    0.000000] ACPI: MCFG bff80440 0003C (v01 052709 OEMMCFG  20090527 MSFT 00000097)
[    0.000000] ACPI: SLIC bff80480 00176 (v01 _ASUS_ Notebook 20090527 MSFT 00000097)
[    0.000000] ACPI: ECDT bff80630 00054 (v01 052709 OEMECDT  20090527 MSFT 00000097)
[    0.000000] ACPI: DBGP bff80400 00034 (v01 052709 DBGP1358 20090527 MSFT 00000097)
[    0.000000] ACPI: BOOT bff80600 00028 (v01 052709 BOOT1358 20090527 MSFT 00000097)
[    0.000000] ACPI: OEMB bff8f040 00071 (v01 052709 OEMB1358 20090527 MSFT 00000097)
[    0.000000] ACPI: HPET bff8c8a0 00038 (v01 052709 OEMHPET  20090527 MSFT 00000097)
[    0.000000] ACPI: DMAR bff8f0c0 00108 (v01 052709 DMAR1358 20090527 MSFT 00000097)
[    0.000000] ACPI: ATKG bff8f3d0 08024 (v01 052709  OEMATKG 20090527 MSFT 00000097)
[    0.000000] ACPI: SSDT bff97f20 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4230MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00012000 - 00018f40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000092f7d8]    TEXT DATA BSS ==> [0000100000 - 000092f7d8]
[    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #5 [0000930000 - 0000937294]              BRK ==> [0000930000 - 0000937294]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000938000 - 00015b86cb]      NEW RAMDISK ==> [0000938000 - 00015b86cb]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bff80
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048334
[    0.000000] free_area_init_node: node 0, pgdat c07d4d20, node_mem_map c15ba200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221994 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8461 pages used for memmap
[    0.000000]   HighMem zone: 812149 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e1000
[    0.000000] PM: Registered nosave memory: 00000000000e1000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c3e00000 s39448 r0 d21992 u524288
[    0.000000] pcpu-alloc: s39448 r0 d21992 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1038093
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=5fa7d3de-fec1-4ad4-a9b5-3e1c88edccb9 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 26214080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:00140000)
[    0.000000] Memory: 4103320k/5242880k available (4826k kernel code, 88912k reserved, 2211k data, 672k init, 3282440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07e0000 - 0xc0888000   ( 672 kB)
[    0.000000]       .data : 0xc05b6a4b - 0xc07df7a8   (2211 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05b6a4b   (4826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2527.073 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5054.14 BogoMIPS (lpj=10108292)
[    0.004019] Security Framework initialized
[    0.004036] AppArmor: AppArmor initialized
[    0.004042] Mount-cache hash table entries: 512
[    0.004148] Initializing cgroup subsys ns
[    0.004152] Initializing cgroup subsys cpuacct
[    0.004156] Initializing cgroup subsys memory
[    0.004162] Initializing cgroup subsys devices
[    0.004163] Initializing cgroup subsys freezer
[    0.004165] Initializing cgroup subsys net_cls
[    0.004183] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004185] CPU: L2 cache: 3072K
[    0.004188] CPU: Physical Processor ID: 0
[    0.004189] CPU: Processor Core ID: 0
[    0.004193] mce: CPU supports 6 MCE banks
[    0.004200] CPU0: Thermal monitoring enabled (TM2)
[    0.004203] using mwait in idle threads.
[    0.004209] Performance Events: Core2 events, Intel PMU driver.
[    0.004214] ... version:                2
[    0.004215] ... bit width:              40
[    0.004217] ... generic registers:      2
[    0.004218] ... value mask:             000000ffffffffff
[    0.004220] ... max period:             000000007fffffff
[    0.004221] ... fixed-purpose events:   3
[    0.004223] ... event mask:             0000000700000003
[    0.004228] Checking 'hlt' instruction... OK.
[    0.022526] ACPI: Core revision 20090903
[    0.040008] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040012] ftrace: allocating 22402 entries in 44 pages
[    0.044045] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044387] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.087856] CPU0: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 3072K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.172070] CPU1: Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz stepping 0a
[    0.172078] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176016] Brought up 2 CPUs
[    0.176018] Total of 2 processors activated (10108.11 BogoMIPS).
[    0.176590] CPU0 attaching sched-domain:
[    0.176593]  domain 0: span 0-1 level MC
[    0.176595]   groups: 0 1
[    0.176600] CPU1 attaching sched-domain:
[    0.176602]  domain 0: span 0-1 level MC
[    0.176604]   groups: 1 0
[    0.176687] devtmpfs: initialized
[    0.176687] regulator: core version 0.5
[    0.176687] Time: 15:57:05  Date: 05/24/10
[    0.176687] NET: Registered protocol family 16
[    0.176687] Trying to unpack rootfs image as initramfs...
[    0.176687] EISA bus registered
[    0.176687] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.176687] ACPI: bus type pci registered
[    0.176687] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.176687] PCI: Not using MMCONFIG.
[    0.176687] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[    0.176687] PCI: Using configuration type 1 for base access
[    0.180080] bio: create slab <bio-0> at 0
[    0.181397] ACPI: EC: EC description table is found, configuring boot EC
[    0.182813] ACPI: Executed 1 blocks of module-level executable AML code
[    0.185093] ACPI: BIOS _OSI(Linux) query ignored
[    0.192600] ACPI: Interpreter enabled
[    0.192613] ACPI: (supports S0 S3 S4 S5)
[    0.192635] ACPI: Using IOAPIC for interrupt routing
[    0.192717] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.195699] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.195702] PCI: Using MMCONFIG for extended config space
[    0.204887] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.207655] ACPI Warning: Incorrect checksum in table [ATKG] - D8, should be CF (20090903/tbutils-314)
[    0.207876] ACPI: No dock devices found.
[    0.208375] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.208474] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.208478] pci 0000:00:01.0: PME# disabled
[    0.208582] pci 0000:00:1a.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.208683] pci 0000:00:1a.1: reg 20 io port: [0xb880-0xb89f]
[    0.208783] pci 0000:00:1a.2: reg 20 io port: [0xb800-0xb81f]
[    0.208884] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf9fffc00-0xf9ffffff]
[    0.208957] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.208962] pci 0000:00:1a.7: PME# disabled
[    0.209022] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf9ff8000-0xf9ffbfff]
[    0.209086] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.209091] pci 0000:00:1b.0: PME# disabled
[    0.209187] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.209192] pci 0000:00:1c.0: PME# disabled
[    0.209291] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.209295] pci 0000:00:1c.1: PME# disabled
[    0.209395] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.209400] pci 0000:00:1c.2: PME# disabled
[    0.209501] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.209506] pci 0000:00:1c.5: PME# disabled
[    0.209586] pci 0000:00:1d.0: reg 20 io port: [0xb480-0xb49f]
[    0.209688] pci 0000:00:1d.1: reg 20 io port: [0xb400-0xb41f]
[    0.209788] pci 0000:00:1d.2: reg 20 io port: [0xb080-0xb09f]
[    0.209889] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf9fff800-0xf9fffbff]
[    0.209960] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.209965] pci 0000:00:1d.7: PME# disabled
[    0.210225] pci 0000:00:1f.2: reg 10 io port: [0xb000-0xb007]
[    0.210233] pci 0000:00:1f.2: reg 14 io port: [0xac00-0xac03]
[    0.210240] pci 0000:00:1f.2: reg 18 io port: [0xa880-0xa887]
[    0.210248] pci 0000:00:1f.2: reg 1c io port: [0xa800-0xa803]
[    0.210256] pci 0000:00:1f.2: reg 20 io port: [0xa480-0xa49f]
[    0.210263] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf9fff000-0xf9fff7ff]
[    0.210313] pci 0000:00:1f.2: PME# supported from D3hot
[    0.210317] pci 0000:00:1f.2: PME# disabled
[    0.210397] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.210412] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.210426] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.210435] pci 0000:01:00.0: reg 24 io port: [0xcc00-0xcc7f]
[    0.210444] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.210558] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.210561] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfdefffff]
[    0.210565] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.210759] pci 0000:03:00.0: reg 10 64bit mmio: [0xfdffe000-0xfdffffff]
[    0.210897] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.210911] pci 0000:03:00.0: PME# disabled
[    0.211006] pci 0000:00:1c.1: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.211073] pci 0000:00:1c.2: bridge io port: [0xd000-0xdfff]
[    0.211078] pci 0000:00:1c.2: bridge 32bit mmio: [0xfe000000-0xfe9fffff]
[    0.211086] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf6000000-0xf8efffff]
[    0.211247] pci 0000:06:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.211324] pci 0000:06:00.0: reg 18 64bit mmio pref: [0xf8fff000-0xf8ffffff]
[    0.211376] pci 0000:06:00.0: reg 20 64bit mmio pref: [0xf8fe0000-0xf8feffff]
[    0.211404] pci 0000:06:00.0: reg 30 32bit mmio pref: [0xfeaf0000-0xfeafffff]
[    0.211562] pci 0000:06:00.0: supports D1 D2
[    0.211564] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.211578] pci 0000:06:00.0: PME# disabled
[    0.211730] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
[    0.211735] pci 0000:00:1c.5: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.211743] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xf8f00000-0xf8ffffff]
[    0.211787] pci 0000:07:01.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]
[    0.211847] pci 0000:07:01.0: PME# supported from D0 D3hot D3cold
[    0.211852] pci 0000:07:01.0: PME# disabled
[    0.211893] pci 0000:07:01.1: reg 10 32bit mmio: [0xfebff400-0xfebff4ff]
[    0.211953] pci 0000:07:01.1: supports D1 D2
[    0.211955] pci 0000:07:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.211960] pci 0000:07:01.1: PME# disabled
[    0.212008] pci 0000:07:01.2: reg 10 32bit mmio: [0xfebff000-0xfebff0ff]
[    0.212068] pci 0000:07:01.2: supports D1 D2
[    0.212069] pci 0000:07:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212074] pci 0000:07:01.2: PME# disabled
[    0.212116] pci 0000:07:01.3: reg 10 32bit mmio: [0xfebfec00-0xfebfecff]
[    0.212175] pci 0000:07:01.3: supports D1 D2
[    0.212177] pci 0000:07:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212182] pci 0000:07:01.3: PME# disabled
[    0.212223] pci 0000:07:01.4: reg 10 32bit mmio: [0xfebfe800-0xfebfe8ff]
[    0.212283] pci 0000:07:01.4: supports D1 D2
[    0.212285] pci 0000:07:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212290] pci 0000:07:01.4: PME# disabled
[    0.212350] pci 0000:00:1e.0: transparent bridge
[    0.212358] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.212399] pci_bus 0000:00: on NUMA node 0
[    0.212405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.212604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.212674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.212734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.212856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.212915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.233102] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    0.233233] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[    0.233359] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.233483] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 12)
[    0.233611] ACPI: PCI Interrupt Link [LNKE] (IRQs 6) *0, disabled.
[    0.233736] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    0.233863] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    0.233990] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    0.234111] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.234117] vgaarb: loaded
[    0.234220] SCSI subsystem initialized
[    0.234299] libata version 3.00 loaded.
[    0.234358] usbcore: registered new interface driver usbfs
[    0.234368] usbcore: registered new interface driver hub
[    0.234388] usbcore: registered new device driver usb
[    0.234496] ACPI: WMI: Mapper loaded
[    0.234498] PCI: Using ACPI for IRQ routing
[    0.234782] NetLabel: Initializing
[    0.234784] NetLabel:  domain hash size = 128
[    0.234785] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.234797] NetLabel:  unlabeled traffic allowed by default
[    0.234826] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.234830] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.240226] Switching to clocksource tsc
[    0.241775] AppArmor: AppArmor Filesystem Enabled
[    0.241784] pnp: PnP ACPI init
[    0.241794] ACPI: bus type pnp registered
[    0.244384] pnp: PnP ACPI: found 14 devices
[    0.244386] ACPI: ACPI bus type pnp unregistered
[    0.244390] PnPBIOS: Disabled by ACPI PNP
[    0.244399] system 00:01: iomem range 0xfed10000-0xfed19fff has been reserved
[    0.244408] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.244410] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.244412] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.244415] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.244418] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.244420] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.244423] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.244425] system 00:08: iomem range 0xfed90000-0xfed90fff has been reserved
[    0.244428] system 00:08: iomem range 0xfed91000-0xfed91fff has been reserved
[    0.244431] system 00:08: iomem range 0xfed92000-0xfed92fff has been reserved
[    0.244433] system 00:08: iomem range 0xfed93000-0xfed93fff has been reserved
[    0.244436] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.244438] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.244444] system 00:0a: ioport range 0x250-0x253 has been reserved
[    0.244446] system 00:0a: ioport range 0x256-0x25f has been reserved
[    0.244449] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.244451] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.244454] system 00:0a: iomem range 0xfec10000-0xfec17fff has been reserved
[    0.244456] system 00:0a: iomem range 0xfec18000-0xfec1ffff has been reserved
[    0.244459] system 00:0a: iomem range 0xfec20000-0xfec27fff has been reserved
[    0.244461] system 00:0a: iomem range 0xfec28000-0xfec2ffff has been reserved
[    0.244464] system 00:0a: iomem range 0xfec30000-0xfec37fff has been reserved
[    0.244466] system 00:0a: iomem range 0xfec38000-0xfec3ffff has been reserved
[    0.244471] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.244478] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.244480] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.244483] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.244485] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
[    0.279222] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.279226] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.279230] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfdefffff
[    0.279234] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.279238] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.279240] pci 0000:00:1c.0:   IO window: disabled
[    0.279246] pci 0000:00:1c.0:   MEM window: disabled
[    0.279250] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.279258] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.279259] pci 0000:00:1c.1:   IO window: disabled
[    0.279266] pci 0000:00:1c.1:   MEM window: 0xfdf00000-0xfdffffff
[    0.279270] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.279278] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.279281] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
[    0.279287] pci 0000:00:1c.2:   MEM window: 0xfe000000-0xfe9fffff
[    0.279292] pci 0000:00:1c.2:   PREFETCH window: 0x000000f6000000-0x000000f8efffff
[    0.279300] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
[    0.279304] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
[    0.279310] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
[    0.279315] pci 0000:00:1c.5:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.279323] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.279325] pci 0000:00:1e.0:   IO window: disabled
[    0.279331] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.279335] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.279353]   alloc irq_desc for 16 on node -1
[    0.279355]   alloc kstat_irqs on node -1
[    0.279361] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.279365] pci 0000:00:01.0: setting latency timer to 64
[    0.279375] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.279386] pci 0000:00:1c.0: setting latency timer to 64
[    0.279396]   alloc irq_desc for 17 on node -1
[    0.279397]   alloc kstat_irqs on node -1
[    0.279401] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.279405] pci 0000:00:1c.1: setting latency timer to 64
[    0.279416]   alloc irq_desc for 18 on node -1
[    0.279417]   alloc kstat_irqs on node -1
[    0.279420] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.279425] pci 0000:00:1c.2: setting latency timer to 64
[    0.279436] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.279441] pci 0000:00:1c.5: setting latency timer to 64
[    0.279449] pci 0000:00:1e.0: setting latency timer to 64
[    0.279454] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.279456] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.279458] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.279460] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfdefffff]
[    0.279462] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.279465] pci_bus 0000:03: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.279467] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    0.279469] pci_bus 0000:04: resource 1 mem: [0xfe000000-0xfe9fffff]
[    0.279471] pci_bus 0000:04: resource 2 pref mem [0xf6000000-0xf8efffff]
[    0.279473] pci_bus 0000:06: resource 0 io:  [0xe000-0xefff]
[    0.279475] pci_bus 0000:06: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.279478] pci_bus 0000:06: resource 2 pref mem [0xf8f00000-0xf8ffffff]
[    0.279480] pci_bus 0000:07: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.279482] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.279484] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.279518] NET: Registered protocol family 2
[    0.279607] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.279882] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.280269] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.280478] TCP: Hash tables configured (established 131072 bind 65536)
[    0.280480] TCP reno registered
[    0.280548] NET: Registered protocol family 1
[    0.280719] pci 0000:01:00.0: Boot video device
[    0.280748] Simple Boot Flag at 0x51 set to 0x1
[    0.280894] cpufreq-nforce2: No nForce2 chipset.
[    0.280918] Scanning for low memory corruption every 60 seconds
[    0.281003] audit: initializing netlink socket (disabled)
[    0.281011] type=2000 audit(1274716625.279:1): initialized
[    0.289786] highmem bounce pool size: 64 pages
[    0.289791] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.291010] VFS: Disk quotas dquot_6.5.2
[    0.291058] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.291543] fuse init (API version 7.13)
[    0.291612] msgmni has been set to 1605
[    0.291790] alg: No test for stdrng (krng)
[    0.291834] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.291837] io scheduler noop registered
[    0.291839] io scheduler anticipatory registered
[    0.291840] io scheduler deadline registered
[    0.291874] io scheduler cfq registered (default)
[    0.292001]   alloc irq_desc for 24 on node -1
[    0.292003]   alloc kstat_irqs on node -1
[    0.292011] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.292017] pcieport 0000:00:01.0: setting latency timer to 64
[    0.292137]   alloc irq_desc for 25 on node -1
[    0.292138]   alloc kstat_irqs on node -1
[    0.292146] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.292157] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.292298]   alloc irq_desc for 26 on node -1
[    0.292299]   alloc kstat_irqs on node -1
[    0.292308] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.292319] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.292459]   alloc irq_desc for 27 on node -1
[    0.292461]   alloc kstat_irqs on node -1
[    0.292469] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.292480] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.292629]   alloc irq_desc for 28 on node -1
[    0.292631]   alloc kstat_irqs on node -1
[    0.292639] pcieport 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.292650] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.292738] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.293046] pciehp 0000:00:01.0:pcie04: HPC vendor_id 8086 device_id 2a41 ss_vid 0 ss_did 0
[    0.293074] pciehp 0000:00:01.0:pcie04: service driver pciehp loaded
[    0.293099] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 2944 ss_vid 0 ss_did 0
[    0.293135] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    0.293142] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.293267] ACPI: AC Adapter [AC0] (on-line)
[    0.293333] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.293341] ACPI: Sleep Button [SLPB]
[    0.293375] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.295611] ACPI: Lid Switch [LID]
[    0.295650] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.295652] ACPI: Power Button [PWRF]
[    0.296411] ACPI: SSDT bff974d0 00248 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.297011] ACPI: SSDT bff977b0 00765 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.299164] Monitor-Mwait will be used to enter C-1 state
[    0.299187] Monitor-Mwait will be used to enter C-3 state
[    0.299197] Marking TSC unstable due to TSC halts in idle
[    0.299240] processor LNXCPU:00: registered as cooling_device0
[    0.299545] ACPI: SSDT bff97400 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.299941] ACPI: SSDT bff97720 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.300354] Switching to clocksource hpet
[    0.303665] processor LNXCPU:01: registered as cooling_device1
[    0.319497] thermal LNXTHERM:01: registered as thermal_zone0
[    0.319505] ACPI: Thermal Zone [THRM] (36 C)
[    0.320784] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.321990] brd: module loaded
[    0.322378] loop: module loaded
[    0.322450] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.322819] Fixed MDIO Bus: probed
[    0.322848] PPP generic driver version 2.4.2
[    0.322879] tun: Universal TUN/TAP device driver, 1.6
[    0.322881] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.322950] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.322971] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.322983] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.322987] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.323012] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.323039] ehci_hcd 0000:00:1a.7: debug port 1
[    0.326914] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.326929] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    0.331053] isapnp: Scanning for PnP cards...
[    0.368174] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.368291] usb usb1: configuration #1 chosen from 1 choice
[    0.368315] hub 1-0:1.0: USB hub found
[    0.368324] hub 1-0:1.0: 6 ports detected
[    0.368385]   alloc irq_desc for 23 on node -1
[    0.368387]   alloc kstat_irqs on node -1
[    0.368393] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.368414] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.368417] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.368450] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.368475] ehci_hcd 0000:00:1d.7: debug port 1
[    0.372354] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.372370] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    0.396023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.396119] usb usb2: configuration #1 chosen from 1 choice
[    0.396143] hub 2-0:1.0: USB hub found
[    0.396150] hub 2-0:1.0: 6 ports detected
[    0.396209] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.396226] uhci_hcd: USB Universal Host Controller Interface driver
[    0.396262] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.396271] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.396274] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.396304] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.396340] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000bc00
[    0.396413] usb usb3: configuration #1 chosen from 1 choice
[    0.396433] hub 3-0:1.0: USB hub found
[    0.396439] hub 3-0:1.0: 2 ports detected
[    0.396478]   alloc irq_desc for 21 on node -1
[    0.396480]   alloc kstat_irqs on node -1
[    0.396484] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.396490] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.396493] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.396520] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.396550] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    0.396626] usb usb4: configuration #1 chosen from 1 choice
[    0.396647] hub 4-0:1.0: USB hub found
[    0.396652] hub 4-0:1.0: 2 ports detected
[    0.396689]   alloc irq_desc for 19 on node -1
[    0.396691]   alloc kstat_irqs on node -1
[    0.396694] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.396700] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.396703] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.396727] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.396757] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000b800
[    0.396828] usb usb5: configuration #1 chosen from 1 choice
[    0.396848] hub 5-0:1.0: USB hub found
[    0.396853] hub 5-0:1.0: 2 ports detected
[    0.396894] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.396900] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.396903] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.396932] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.396956] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b480
[    0.397028] usb usb6: configuration #1 chosen from 1 choice
[    0.397049] hub 6-0:1.0: USB hub found
[    0.397054] hub 6-0:1.0: 2 ports detected
[    0.397093] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.397098] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.397102] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.397125] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.397148] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    0.397217] usb usb7: configuration #1 chosen from 1 choice
[    0.397240] hub 7-0:1.0: USB hub found
[    0.397245] hub 7-0:1.0: 2 ports detected
[    0.397282] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.397289] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.397292] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.397318] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.397341] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b080
[    0.397412] usb usb8: configuration #1 chosen from 1 choice
[    0.397434] hub 8-0:1.0: USB hub found
[    0.397439] hub 8-0:1.0: 2 ports detected
[    0.397523] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.401621] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.403371] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.403376] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.412187] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.412213] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.412231] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.412327] mice: PS/2 mouse device common for all mice
[    0.412454] rtc_cmos 00:03: RTC can wake from S4
[    0.412487] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.412519] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.412608] device-mapper: uevent: version 1.0.3
[    0.423942] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.433517] device-mapper: multipath: version 1.1.0 loaded
[    0.433520] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.454372] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.469647] Freeing initrd memory: 12801k freed
[    0.474774] EISA: Probing bus 0 at eisa.0
[    0.474806] EISA: Detected 0 cards.
[    0.474961] cpuidle: using governor ladder
[    0.475035] cpuidle: using governor menu
[    0.475440] TCP cubic registered
[    0.475566] NET: Registered protocol family 10
[    0.475980] lo: Disabled Privacy Extensions
[    0.476290] NET: Registered protocol family 17
[    0.478347] Using IPI No-Shortcut mode
[    0.478423] PM: Resume from disk failed.
[    0.478434] registered taskstats version 1
[    0.479121]   Magic number: 10:829:993
[    0.479205] rtc_cmos 00:03: setting system clock to 2010-05-24 15:57:05 UTC (1274716625)
[    0.479207] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.479208] EDD information not available.
[    0.688152] isapnp: No Plug & Play device found
[    0.688191] Freeing unused kernel memory: 672k freed
[    0.688595] Write protecting the kernel text: 4828k
[    0.688686] Write protecting the kernel read-only data: 1876k
[    0.705417] udev: starting version 151
[    0.712034] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    0.718798] ACPI: Battery Slot [BAT0] (battery present)
[    0.792325] Linux agpgart interface v0.103
[    0.810311] vga16fb: initializing
[    0.810314] vga16fb: mapped to 0xc00a0000
[    0.810357] fb0: VGA16 VGA frame buffer device
[    0.817168] ahci 0000:00:1f.2: version 3.0
[    0.817182] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.817222]   alloc irq_desc for 29 on node -1
[    0.817223]   alloc kstat_irqs on node -1
[    0.817234] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.817281] ahci: SSS flag set, parallel bus scan disabled
[    0.817313] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    0.817316] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pio slum part ccc ems sxs 
[    0.817321] ahci 0000:00:1f.2: setting latency timer to 64
[    0.819262] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.819294] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.819380] r8169 0000:06:00.0: setting latency timer to 64
[    0.819563]   alloc irq_desc for 30 on node -1
[    0.819564]   alloc kstat_irqs on node -1
[    0.819607] r8169 0000:06:00.0: irq 30 for MSI/MSI-X
[    0.820163] eth0: RTL8168c/8111c at 0xf8364000, 00:26:18:79:2e:1b, XID 1c4000c0 IRQ 30
[    0.827366] acpi device:1c: registered as cooling_device2
[    0.827537] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:18/LNXVIDEO:00/input/input5
[    0.827601] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    0.833453] ohci1394 0000:07:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.846283] scsi0 : ahci
[    0.848606] scsi1 : ahci
[    0.848692] scsi2 : ahci
[    0.848775] scsi3 : ahci
[    0.848854] scsi4 : ahci
[    0.848935] scsi5 : ahci
[    0.849227] ata1: SATA max UDMA/133 abar m2048@0xf9fff000 port 0xf9fff100 irq 29
[    0.849232] ata2: SATA max UDMA/133 abar m2048@0xf9fff000 port 0xf9fff180 irq 29
[    0.849233] ata3: DUMMY
[    0.849234] ata4: DUMMY
[    0.849235] ata5: DUMMY
[    0.849238] ata6: SATA max UDMA/133 abar m2048@0xf9fff000 port 0xf9fff380 irq 29
[    0.888645] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    0.903832] usb 1-3: configuration #1 chosen from 1 choice
[    1.082080] Console: switching to colour frame buffer device 80x30
[    1.168102] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.169300] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.178565] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.188549] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    1.262069] ata1.00: ATA-8: ST9320421AS, SD14, max UDMA/133
[    1.262072] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.278053] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.288474] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.299793] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    1.330797] ata1.00: configured for UDMA/133
[    1.330944] scsi 0:0:0:0: Direct-Access     ATA      ST9320421AS      SD14 PQ: 0 ANSI: 5
[    1.331062] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.331112] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.331148] sd 0:0:0:0: [sda] Write Protect is off
[    1.331150] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.331168] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.331271]  sda: sda1 sda2 sda3 < sda5
[    1.384076] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.399409]  sda6 > sda4
[    1.399754] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.052116] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.056872] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    2.057378] ata2.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    2.061121] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RR07, max UDMA/133
[    2.067039] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    2.067510] ata2.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) succeeded
[    2.071275] ata2.00: configured for UDMA/133
[    2.126883] usb 5-1: configuration #1 chosen from 1 choice
[    2.160529] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001c1f11c]
[    2.182059] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RR07 PQ: 0 ANSI: 5
[    2.512116] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.512120] Uniform CD-ROM driver Revision: 3.20
[    2.512228] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.512293] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.832109] ata6: SATA link down (SStatus 0 SControl 300)
[    3.800058] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   19.116380] udev: starting version 151
[   19.172830] Adding 995988k swap on /dev/sda6.  Priority:-1 extents:1 across:995988k 
[   19.299564] asus_laptop: Asus Laptop Support version 0.42
[   19.323027] lp: driver loaded but no devices found
[   19.335756] type=1505 audit(1274731044.352:2):  operation="profile_load" pid=676 name="/sbin/dhclient3"
[   19.336339] type=1505 audit(1274731044.356:3):  operation="profile_load" pid=676 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.336627] type=1505 audit(1274731044.356:4):  operation="profile_load" pid=676 name="/usr/lib/connman/scripts/dhclient-script"
[   19.338274] asus_laptop:   G60VX model detected
[   19.339026] input: Asus Laptop extra buttons as /devices/virtual/input/input6
[   19.339128] Registered led device: asus::touchpad
[   19.339190] Registered led device: asus::kbd_backlight
[   19.352632] Bluetooth: Core ver 2.15
[   19.355554] NET: Registered protocol family 31
[   19.355556] Bluetooth: HCI device and connection manager initialized
[   19.355559] Bluetooth: HCI socket layer initialized
[   19.359247] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   19.379529] nvidia: module license 'NVIDIA' taints kernel.
[   19.379532] Disabling lock debugging due to kernel taint
[   20.014202] Linux video capture interface: v2.00
[   20.017691] uvcvideo: Found UVC 1.00 device CNF7246 (04f2:b106)
[   20.018416] cfg80211: Calling CRDA to update world regulatory domain
[   20.045510] input: CNF7246 as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input7
[   20.045556] usbcore: registered new interface driver uvcvideo
[   20.045559] USB Video Class driver (v0.1.0)
[   20.057971] cfg80211: World regulatory domain updated:
[   20.057973]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.057975]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.057977]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.057979]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.057982]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.057983]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.058891] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   20.058893] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   20.058964] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.058992] iwlagn 0000:03:00.0: setting latency timer to 64
[   20.059046] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   20.104975] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   20.105038]   alloc irq_desc for 31 on node -1
[   20.105040]   alloc kstat_irqs on node -1
[   20.105060] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[   20.109606] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.121752] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   20.121842] usbcore: registered new interface driver btusb
[   20.132458] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b3, caps: 0xd04711/0xa00000
[   20.147449] sdhci: Secure Digital Host Controller Interface driver
[   20.147452] sdhci: Copyright(c) Pierre Ossman
[   20.149592] sdhci-pci 0000:07:01.1: SDHCI controller found [1180:0822] (rev 22)
[   20.149609] sdhci-pci 0000:07:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.150623] sdhci-pci 0000:07:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   20.151679] Registered led device: mmc0::
[   20.152729] mmc0: SDHCI controller on PCI [0000:07:01.1] using DMA
[   20.156093] ricoh-mmc: Ricoh MMC Controller disabling driver
[   20.156095] ricoh-mmc: Copyright(c) Philip Langdale
[   20.156112] ricoh-mmc: Ricoh MMC controller found at 0000:07:01.2 [1180:0843] (rev 12)
[   20.156127] ricoh-mmc: Controller is now disabled.
[   20.188424] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   20.250116] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.250127] nvidia 0000:01:00.0: setting latency timer to 64
[   20.250132] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   20.250289] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
[   20.869567] type=1505 audit(1274731045.888:5):  operation="profile_load" pid=887 name="/usr/share/gdm/guest-session/Xsession"
[   20.870861] type=1505 audit(1274731045.888:6):  operation="profile_replace" pid=888 name="/sbin/dhclient3"
[   20.871378] type=1505 audit(1274731045.888:7):  operation="profile_replace" pid=888 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.871655] type=1505 audit(1274731045.888:8):  operation="profile_replace" pid=888 name="/usr/lib/connman/scripts/dhclient-script"
[   20.874152] type=1505 audit(1274731045.892:9):  operation="profile_load" pid=889 name="/usr/bin/evince"
[   20.880926] type=1505 audit(1274731045.900:10):  operation="profile_load" pid=889 name="/usr/bin/evince-previewer"
[   20.885027] type=1505 audit(1274731045.904:11):  operation="profile_load" pid=889 name="/usr/bin/evince-thumbnailer"
[   20.932189] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   20.955957] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   21.105510] Registered led device: iwl-phy0::radio
[   21.105766] Registered led device: iwl-phy0::assoc
[   21.105822] Registered led device: iwl-phy0::RX
[   21.105982] Registered led device: iwl-phy0::TX
[   21.117058] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.129787] r8169: eth0: link down
[   21.129944] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.205635]   alloc irq_desc for 22 on node -1
[   21.205637]   alloc kstat_irqs on node -1
[   21.205643] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.205704]   alloc irq_desc for 32 on node -1
[   21.205705]   alloc kstat_irqs on node -1
[   21.205716] HDA Intel 0000:00:1b.0: irq 32 for MSI/MSI-X
[   21.205748] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.378692] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9

hope someone can help me out here

---

### Post by simosx on 2010-05-24
For sound issues such as this, what you need to do is run a special program that will extract hardware information that will help to figure out the problem.

On the terminal run
[INDENT]wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh)[/INDENT]
(ALSA is the Audio subsystem for the Linux kernel)

Then, execute the program 'alsa-info.sh' with

[INDENT]sh alsa-info.sh[/INDENT]

It will give you a URL with the details of your sound card. Please post that URL here for more help.

---

### Post by FirstByté on 2010-05-25
> **simosx said:**
> For sound issues such as this, what you need to do is run a special program that will extract hardware information that will help to figure out the problem.

On the terminal run
[INDENT]wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh)[/INDENT]
(ALSA is the Audio subsystem for the Linux kernel)

Then, execute the program 'alsa-info.sh' with

[INDENT]sh alsa-info.sh[/INDENT]

It will give you a URL with the details of your sound card. **Please post that URL here for more help.**

I hope Canonical has taken notice of this 'upgrade' bug perculiar to all 10.04 upgrades... I bet many wouldn't notice till they try to place calls on Skype... A thing that worked on earlier releases of Ubuntu. I noticed when a frined of mine raised the issue, then I figured out I was suffering from same :(

Here's my 'alsa-info' it's in text file though.

Any help figured out it appreciated.

---

### Post by simosx on 2010-05-26
> **FirstByté said:**
> I hope Canonical has taken notice of this 'upgrade' bug perculiar to all 10.04 upgrades... I bet many wouldn't notice till they try to place calls on Skype... A thing that worked on earlier releases of Ubuntu. I noticed when a frined of mine raised the issue, then I figured out I was suffering from same :(

Here's my 'alsa-info' it's in text file though.

Any help figured out it appreciated.

The alsa-info output shows that you have 'alsa-driver' (the Alsa kernel module) at version 1.0.21 while the Alsa library is at 1.0.22.

In addition, it appears that your alsa-info.txt is truncated; there are sections missing such as the dmesg output, etc. See 
[http://www.alsa-project.org/db/?f=fd4e474d6a86b436ec099186793df142a2b94170](http://www.alsa-project.org/db/?f=fd4e474d6a86b436ec099186793df142a2b94170)
for a full alsa-info.sh output. If you have trouble attaching the file, you can select to have the output submitted to [www.alsa-project.org](www.alsa-project.org), then simply post the link here.

A regression would be Ubuntu's fault if we forgot to include backported Alsa patches in the newer kernel update. I doubt there have been Alsa backported patches, though you would need to do some searching here in the changelog for the kernel update.

---

### Post by FirstByté on 2010-05-27
> **simosx said:**
> The alsa-info output shows that you have 'alsa-driver' (the Alsa kernel module) at version 1.0.21 while the Alsa library is at 1.0.22.

In addition, it appears that your alsa-info.txt is truncated; there are sections missing such as the dmesg output, etc. See 
[http://www.alsa-project.org/db/?f=fd4e474d6a86b436ec099186793df142a2b94170](http://www.alsa-project.org/db/?f=fd4e474d6a86b436ec099186793df142a2b94170)
for a full alsa-info.sh output. If you have trouble attaching the file, you can select to have the output submitted to [www.alsa-project.org](www.alsa-project.org), then simply post the link here.

A regression would be Ubuntu's fault if we forgot to include backported Alsa patches in the newer kernel update. I doubt there have been Alsa backported patches, though you would need to do some searching here in the changelog for the kernel update.

I tried running this script a couple times but somehow I can't get to set the operand not even --help or -e or anything close.

It just runs verbrose... and that's it. Thus I can't sellect the "upload online function"

Thanks for the prompt reply too. I got this earlier but was rushing to meet deadline <my bad :( >

---

### Post by FirstByté on 2010-05-28
> **simosx said:**
> [B][I]
[...][/I][/B] **If you have trouble attaching the file**, you can select to have the output submitted to [www.alsa-project.org](www.alsa-project.org), then simply post the link here.

A regression would be Ubuntu's fault if we forgot to include backported Alsa patches in the newer kernel update. I doubt there have been Alsa backported patches, though you would need to do some searching here in the changelog for the kernel update.

Honestly I do have problems getting that done. I can't select the "post online feature". Any help?

---

### Post by simosx on 2010-05-29
> **FirstByté said:**
> Honestly I do have problems getting that done. I can't select the "post online feature". Any help?

Use the command line specified at
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
(see section 'Is ALSA using the correct model?')

If you still cannot send the report to alsa-project.org, you can attach it to here in ubuntuforums.org.

---

### Post by lidex on 2010-05-30
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by FirstByté on 2010-05-30
> **lidex said:**
> First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

From alsa documentation:

Thanks immensely for the heads-up on this. Well, I guess I aready somehow got the 'CLI' version of the "~$ alsamixer"; it was cool seeing the GUI one too. :)

After a little messing arounds, I suspect the issue was rather with my laptop built-in mic; because plugging in an external mic worked. However how much I tried to adjust the [gnome-]alsamixer, it didn't capture sound from the in-built mic. Even the PulseAudio Volume Control showed input levels way below 'silent'.


Once again thanks. I hope I can get to resolve this issue with the built-in mic soon.

> Hardware:

Dell Studio 14
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

Distributor ID:	Ubuntu (2.6.32-22-generic)
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid


---

### Post by lidex on 2010-05-31
> **FirstByté said:**
> Thanks immensely for the heads-up on this. Well, I guess I aready somehow got the 'CLI' version of the "~$ alsamixer"; it was cool seeing the GUI one too. :)

After a little messing arounds, I suspect the issue was rather with my laptop built-in mic; because plugging in an external mic worked. However how much I tried to adjust the [gnome-]alsamixer, it didn't capture sound from the in-built mic. Even the PulseAudio Volume Control showed input levels way below 'silent'.


Once again thanks. I hope I can get to resolve this issue with the built-in mic soon.

I suspect an alsa upgrade may fix this issue. Follow the alsa-upgrade link in my sig.

---

