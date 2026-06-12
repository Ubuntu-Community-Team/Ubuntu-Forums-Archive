---
title: "Tuner not detected"
date: 2011-02-08
forum: Mythbuntu
---

### Post by Chrus on 2011-02-08
Hi all

Just installed Mythbuntu 10.10 on my HTPC and I'm having a little trouble with the tuner. Please bear with me as this is my first experience with myth, and I've never tried to get a tuner working on any form of linux before.

The tuner I'm attempting to set up is a Gigabyte U7300 USB digital tuner.

I'm not really sure where to start with this one. I've included below some hopefully useful info. I'll be happy to provide any additional info. To me it looks like its not being detected at all.

Oh... and 'ls /dev/ | grep dvb' doesn't return anything. 

Any advice would be greatly appreciated.

Thanks.

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xcffa0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0E0000000 mask 0E0000000 uncachable
[    0.000000]   1 base 000000000 mask 000000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  modified: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  modified: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  modified: 00000000cfff0000 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 9a5000-a86000
[    0.000000] RAMDISK: 375ab000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 00a80000 - 014c4ded
[    0.000000] Move RAMDISK from 00000000375ab000 - 0000000037fefdec to 00a80000 - 014c4dec
[    0.000000] ACPI: RSDP 000faab0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT cffa0000 00040 (v01 081309 RSDT0925 20090813 MSFT 00000097)
[    0.000000] ACPI: FACP cffa0200 00084 (v01 081309 FACP0925 20090813 MSFT 00000097)
[    0.000000] ACPI: DSDT cffa04a0 070E9 (v01   NVDA NVDAACPI 00001000 INTL 20051117)
[    0.000000] ACPI: FACS cffae000 00040
[    0.000000] ACPI: APIC cffa0390 00080 (v01 081309 APIC0925 20090813 MSFT 00000097)
[    0.000000] ACPI: MCFG cffa0410 0003C (v01 081309 OEMMCFG  20090813 MSFT 00000097)
[    0.000000] ACPI: WDRT cffa0450 00047 (v01 081309 NV-WDRT  20090813 MSFT 00000097)
[    0.000000] ACPI: OEMB cffae040 00079 (v01 081309 OEMB0925 20090813 MSFT 00000097)
[    0.000000] ACPI: HPET cffaa4a0 00038 (v01 081309 OEMHPET0 20090813 MSFT 00000097)
[    0.000000] ACPI: NVHD cffae0c0 00284 (v01 081309  NVHDCP  20090813 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2439MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000cffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cffa0
[    0.000000] On node 0 totalpages: 851759
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c14c6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4880 pages used for memmap
[    0.000000]   HighMem zone: 619666 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [15000 - 157ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2ed8000 s36416 r0 d20928 u65536
[    0.000000] pcpu-alloc: s36416 r0 d20928 u65536 alloc=16*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845103
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=e88766e5-497c-41fa-900c-cfe8203b3a2f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 17037120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (51 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a1000 - 00009a41bf]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009fc00 - 00000e6560]   BIOS reserved
[    0.000000]   #7 [00000e66ac - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000e6560 - 00000e66ac]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [00009a5000 - 0000a80000]         PGTABLE
[    0.000000]   #12 [0000a80000 - 00014c5000]     NEW RAMDISK
[    0.000000]   #13 [00014c5000 - 00014c6000]         BOOTMEM
[    0.000000]   #14 [00014c6000 - 0002ec6000]         BOOTMEM
[    0.000000]   #15 [0002ec6000 - 0002ec6004]         BOOTMEM
[    0.000000]   #16 [0002ec6040 - 0002ec6100]         BOOTMEM
[    0.000000]   #17 [0002ec6100 - 0002ec6154]         BOOTMEM
[    0.000000]   #18 [0002ec6180 - 0002ec9180]         BOOTMEM
[    0.000000]   #19 [0002ec9180 - 0002ec9268]         BOOTMEM
[    0.000000]   #20 [0002ec9280 - 0002ed5280]         BOOTMEM
[    0.000000]   #21 [0002ed5280 - 0002ed52a5]         BOOTMEM
[    0.000000]   #22 [0002ed52c0 - 0002ed52e7]         BOOTMEM
[    0.000000]   #23 [0002ed5300 - 0002ed5434]         BOOTMEM
[    0.000000]   #24 [0002ed5440 - 0002ed5480]         BOOTMEM
[    0.000000]   #25 [0002ed5480 - 0002ed54c0]         BOOTMEM
[    0.000000]   #26 [0002ed54c0 - 0002ed5500]         BOOTMEM
[    0.000000]   #27 [0002ed5500 - 0002ed5540]         BOOTMEM
[    0.000000]   #28 [0002ed5540 - 0002ed5580]         BOOTMEM
[    0.000000]   #29 [0002ed5580 - 0002ed55c0]         BOOTMEM
[    0.000000]   #30 [0002ed55c0 - 0002ed5600]         BOOTMEM
[    0.000000]   #31 [0002ed5600 - 0002ed5640]         BOOTMEM
[    0.000000]   #32 [0002ed5640 - 0002ed5680]         BOOTMEM
[    0.000000]   #33 [0002ed5680 - 0002ed56c0]         BOOTMEM
[    0.000000]   #34 [0002ed56c0 - 0002ed56d0]         BOOTMEM
[    0.000000]   #35 [0002ed5700 - 0002ed576a]         BOOTMEM
[    0.000000]   #36 [0002ed5780 - 0002ed57ea]         BOOTMEM
[    0.000000]   #37 [0002ed8000 - 0002ee6000]         BOOTMEM
[    0.000000]   #38 [0002ee8000 - 0002ef6000]         BOOTMEM
[    0.000000]   #39 [0002ef8000 - 0002f06000]         BOOTMEM
[    0.000000]   #40 [0002f08000 - 0002f16000]         BOOTMEM
[    0.000000]   #41 [0002ed7800 - 0002ed7804]         BOOTMEM
[    0.000000]   #42 [0002ed7840 - 0002ed7844]         BOOTMEM
[    0.000000]   #43 [0002ed7880 - 0002ed7890]         BOOTMEM
[    0.000000]   #44 [0002ed78c0 - 0002ed78d0]         BOOTMEM
[    0.000000]   #45 [0002ed7900 - 0002ed7980]         BOOTMEM
[    0.000000]   #46 [0002ed7980 - 0002ed79ac]         BOOTMEM
[    0.000000]   #47 [0002f16000 - 0002f1a000]         BOOTMEM
[    0.000000]   #48 [0002f1a000 - 0002f9a000]         BOOTMEM
[    0.000000]   #49 [0002f9a000 - 0002fda000]         BOOTMEM
[    0.000000]   #50 [0002fda000 - 0004019740]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000cffa0)
[    0.000000] Memory: 3342428k/3407488k available (4928k kernel code, 64608k reserved, 2336k data, 684k init, 2498184k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1600.006 MHz processor.
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.01 BogoMIPS (lpj=6400024)
[    0.004023] pid_max: default: 32768 minimum: 301
[    0.004071] Security Framework initialized
[    0.004107] AppArmor: AppArmor initialized
[    0.004112] Yama: becoming mindful.
[    0.004234] Mount-cache hash table entries: 512
[    0.004483] Initializing cgroup subsys ns
[    0.004493] Initializing cgroup subsys cpuacct
[    0.004504] Initializing cgroup subsys memory
[    0.004523] Initializing cgroup subsys devices
[    0.004529] Initializing cgroup subsys freezer
[    0.004535] Initializing cgroup subsys net_cls
[    0.004582] Atom PSE erratum detected, BIOS microcode update recommended
[    0.004592] CPU: Physical Processor ID: 0
[    0.004597] CPU: Processor Core ID: 0
[    0.004603] mce: CPU supports 5 MCE banks
[    0.004617] CPU0: Thermal monitoring enabled (TM1)
[    0.004625] using mwait in idle threads.
[    0.004639] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.004659] ... version:                3
[    0.004663] ... bit width:              40
[    0.004668] ... generic registers:      2
[    0.004673] ... value mask:             000000ffffffffff
[    0.004678] ... max period:             000000007fffffff
[    0.004683] ... fixed-purpose events:   3
[    0.004688] ... event mask:             0000000700000003
[    0.011778] ACPI: Core revision 20100428
[    0.029619] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.029632] ftrace: allocating 21758 entries in 43 pages
[    0.032110] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032544] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074159] CPU0: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
[    0.076000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.164183]  #2
[    0.008000] Initializing CPU#2
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.256226]  #3 Ok.
[    0.008000] Initializing CPU#3
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.348020] Brought up 4 CPUs
[    0.348029] Total of 4 processors activated (12799.90 BogoMIPS).
[    0.349865] devtmpfs: initialized
[    0.353570] regulator: core version 0.5
[    0.353647] Time: 18:50:11  Date: 02/08/11
[    0.353737] NET: Registered protocol family 16
[    0.353764] Trying to unpack rootfs image as initramfs...
[    0.354080] EISA bus registered
[    0.354104] ACPI: bus type pci registered
[    0.354270] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.354278] PCI: not using MMCONFIG
[    0.354616] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[    0.354621] PCI: Using configuration type 1 for base access
[    0.357020] bio: create slab <bio-0> at 0
[    0.361694] ACPI: EC: Look up EC in DSDT
[    0.366118] ACPI: Executed 1 blocks of module-level executable AML code
[    0.384818] ACPI: Interpreter enabled
[    0.384829] ACPI: (supports S0 S1 S3 S4 S5)
[    0.384885] ACPI: Using IOAPIC for interrupt routing
[    0.385019] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.390159] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
[    0.390166] PCI: Using MMCONFIG for extended config space
[    0.426230] ACPI: No dock devices found.
[    0.426243] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.427260] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.428093] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.428102] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.428109] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.428116] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.428123] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xfbffffff]
[    0.428130] pci_root PNP0A03:00: host bridge window [mem 0xfe000000-0xfebfffff]
[    0.428397] pci 0000:00:03.0: reg 10: [io  0x4f00-0x4fff]
[    0.428527] pci 0000:00:03.2: reg 10: [io  0x4900-0x493f]
[    0.428548] pci 0000:00:03.2: reg 20: [io  0x4d00-0x4d3f]
[    0.428558] pci 0000:00:03.2: reg 24: [io  0x4e00-0x4e3f]
[    0.428590] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.428601] pci 0000:00:03.2: PME# disabled
[    0.428754] pci 0000:00:03.5: reg 10: [mem 0xfae80000-0xfaefffff]
[    0.428874] pci 0000:00:04.0: reg 10: [mem 0xfae7f000-0xfae7ffff]
[    0.428918] pci 0000:00:04.0: supports D1 D2
[    0.428923] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.428930] pci 0000:00:04.0: PME# disabled
[    0.428968] pci 0000:00:04.1: reg 10: [mem 0xfae7ec00-0xfae7ecff]
[    0.429018] pci 0000:00:04.1: supports D1 D2
[    0.429024] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429031] pci 0000:00:04.1: PME# disabled
[    0.429077] pci 0000:00:06.0: reg 10: [mem 0xfae7d000-0xfae7dfff]
[    0.429120] pci 0000:00:06.0: supports D1 D2
[    0.429126] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429133] pci 0000:00:06.0: PME# disabled
[    0.429170] pci 0000:00:06.1: reg 10: [mem 0xfae7e800-0xfae7e8ff]
[    0.429221] pci 0000:00:06.1: supports D1 D2
[    0.429226] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429233] pci 0000:00:06.1: PME# disabled
[    0.429279] pci 0000:00:08.0: reg 10: [mem 0xfae78000-0xfae7bfff]
[    0.429323] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.429330] pci 0000:00:08.0: PME# disabled
[    0.429422] pci 0000:00:0a.0: reg 10: [mem 0xfae7c000-0xfae7cfff]
[    0.429433] pci 0000:00:0a.0: reg 14: [io  0xd080-0xd087]
[    0.429443] pci 0000:00:0a.0: reg 18: [mem 0xfae7e400-0xfae7e4ff]
[    0.429453] pci 0000:00:0a.0: reg 1c: [mem 0xfae7e000-0xfae7e00f]
[    0.429486] pci 0000:00:0a.0: supports D1 D2
[    0.429491] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429500] pci 0000:00:0a.0: PME# disabled
[    0.429537] pci 0000:00:0b.0: reg 10: [io  0xd000-0xd007]
[    0.429546] pci 0000:00:0b.0: reg 14: [io  0xcc00-0xcc03]
[    0.429555] pci 0000:00:0b.0: reg 18: [io  0xc880-0xc887]
[    0.429565] pci 0000:00:0b.0: reg 1c: [io  0xc800-0xc803]
[    0.429574] pci 0000:00:0b.0: reg 20: [io  0xc480-0xc48f]
[    0.429583] pci 0000:00:0b.0: reg 24: [mem 0xfae76000-0xfae77fff]
[    0.429821] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429833] pci 0000:00:0c.0: PME# disabled
[    0.429937] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429944] pci 0000:00:10.0: PME# disabled
[    0.430166] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430177] pci 0000:00:15.0: PME# disabled
[    0.430428] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430440] pci 0000:00:16.0: PME# disabled
[    0.430681] pci 0000:00:17.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430693] pci 0000:00:17.0: PME# disabled
[    0.430937] pci 0000:00:18.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430948] pci 0000:00:18.0: PME# disabled
[    0.431074] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.431083] pci 0000:00:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.431092] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.431100] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.431107] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.431114] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.431121] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.431127] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.431134] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xfbffffff] (subtractive decode)
[    0.431141] pci 0000:00:09.0:   bridge window [mem 0xfe000000-0xfebfffff] (subtractive decode)
[    0.431297] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.431316] pci 0000:00:0c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.431328] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.431348] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.431417] pci 0000:03:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.431433] pci 0000:03:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.431449] pci 0000:03:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.431460] pci 0000:03:00.0: reg 24: [io  0xec00-0xec7f]
[    0.431471] pci 0000:03:00.0: reg 30: [mem 0xfafe0000-0xfaffffff pref]
[    0.431546] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.431554] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.431562] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.431571] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.431773] pci 0000:04:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.431846] pci 0000:04:00.0: supports D1
[    0.431852] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
[    0.431860] pci 0000:04:00.0: PME# disabled
[    0.431889] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.431911] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.431930] pci 0000:00:15.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.431943] pci 0000:00:15.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.431963] pci 0000:00:15.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432141] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.432161] pci 0000:00:16.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.432174] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.432194] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432352] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.432371] pci 0000:00:17.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.432384] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.432405] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432568] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.432586] pci 0000:00:18.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.432599] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.432618] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432699] pci_bus 0000:00: on NUMA node 0
[    0.432711] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.433187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]
[    0.433373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.433521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.433729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.433901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.434070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.434243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.473133] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.473721] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.474307] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.474886] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.475468] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *0, disabled.
[    0.476075] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.476659] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.477239] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.477818] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.478399] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.478978] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.479558] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.480170] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.480755] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.481335] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.481916] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.482521] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *11
[    0.483103] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.483685] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.484298] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.484880] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.485469] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.486053] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.486639] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.487222] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.487806] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.488416] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.489004] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.489590] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.490174] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.490762] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.491347] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.491950] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *15
[    0.492573] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.493170] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.493768] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *15
[    0.494359] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.494953] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.495543] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *9
[    0.496172] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.496855] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.497452] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.498046] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *9
[    0.498639] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *10
[    0.499230] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
[    0.499817] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
[    0.500444] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *11
[    0.501046] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *9
[    0.501642] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *15
[    0.502240] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *14
[    0.502366] HEST: Table is not found!
[    0.502592] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.502601] vgaarb: loaded
[    0.503021] SCSI subsystem initialized
[    0.503057] libata version 3.00 loaded.
[    0.503057] usbcore: registered new interface driver usbfs
[    0.503057] usbcore: registered new interface driver hub
[    0.503057] usbcore: registered new device driver usb
[    0.504485] ACPI: WMI: Mapper loaded
[    0.504491] PCI: Using ACPI for IRQ routing
[    0.504507] PCI: pci_cache_line_size set to 64 bytes
[    0.504671] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.504678] reserve RAM buffer: 00000000cffa0000 - 00000000cfffffff 
[    0.504907] NetLabel: Initializing
[    0.504913] NetLabel:  domain hash size = 128
[    0.504917] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.504944] NetLabel:  unlabeled traffic allowed by default
[    0.505046] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.505059] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.505072] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.516177] Switching to clocksource tsc
[    0.537289] AppArmor: AppArmor Filesystem Enabled
[    0.537330] pnp: PnP ACPI init
[    0.537371] ACPI: bus type pnp registered
[    0.551748] pnp: PnP ACPI: found 12 devices
[    0.551755] ACPI: ACPI bus type pnp unregistered
[    0.551764] PnPBIOS: Disabled by ACPI PNP
[    0.551796] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.551804] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.551811] system 00:05: [io  0x4000-0x407f] has been reserved
[    0.551818] system 00:05: [io  0x4080-0x40ff] has been reserved
[    0.551825] system 00:05: [io  0x4400-0x447f] has been reserved
[    0.551831] system 00:05: [io  0x4480-0x44ff] has been reserved
[    0.551838] system 00:05: [io  0x4800-0x487f] has been reserved
[    0.551845] system 00:05: [io  0x4880-0x48ff] has been reserved
[    0.551853] system 00:05: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.551861] system 00:05: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.551868] system 00:05: [mem 0x000de000-0x000dffff window] has been reserved
[    0.551876] system 00:05: [mem 0xfefe2000-0xfefe3fff] has been reserved
[    0.551883] system 00:05: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.551891] system 00:05: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.551907] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.551914] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.551927] system 00:09: [io  0x0a00-0x0a0f] has been reserved
[    0.551934] system 00:09: [io  0x0a10-0x0a1f] has been reserved
[    0.551947] system 00:0a: [mem 0xfc000000-0xfdffffff] has been reserved
[    0.551960] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.551968] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.551975] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.551983] system 00:0b: [mem 0x00100000-0xdfffffff] could not be reserved
[    0.551990] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.590999] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.591006] pci 0000:00:09.0:   bridge window [io  disabled]
[    0.591015] pci 0000:00:09.0:   bridge window [mem disabled]
[    0.591022] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    0.591033] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.591037] pci 0000:00:0c.0:   bridge window [io  disabled]
[    0.591052] pci 0000:00:0c.0:   bridge window [mem disabled]
[    0.591065] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.591084] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.591092] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.591100] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.591108] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.591118] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.591122] pci 0000:00:15.0:   bridge window [io  disabled]
[    0.591137] pci 0000:00:15.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.591148] pci 0000:00:15.0:   bridge window [mem pref disabled]
[    0.591166] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.591171] pci 0000:00:16.0:   bridge window [io  disabled]
[    0.591184] pci 0000:00:16.0:   bridge window [mem disabled]
[    0.591195] pci 0000:00:16.0:   bridge window [mem pref disabled]
[    0.591213] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.591217] pci 0000:00:17.0:   bridge window [io  disabled]
[    0.591231] pci 0000:00:17.0:   bridge window [mem disabled]
[    0.591242] pci 0000:00:17.0:   bridge window [mem pref disabled]
[    0.591259] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.591264] pci 0000:00:18.0:   bridge window [io  disabled]
[    0.591277] pci 0000:00:18.0:   bridge window [mem disabled]
[    0.591288] pci 0000:00:18.0:   bridge window [mem pref disabled]
[    0.591318] pci 0000:00:09.0: setting latency timer to 64
[    0.592206] ACPI: PCI Interrupt Link [LRP0] enabled at IRQ 23
[    0.592217]   alloc irq_desc for 23 on node -1
[    0.592222]   alloc kstat_irqs on node -1
[    0.592238] pci 0000:00:0c.0: PCI INT A -> Link[LRP0] -> GSI 23 (level, low) -> IRQ 23
[    0.592252] pci 0000:00:0c.0: setting latency timer to 64
[    0.592269] pci 0000:00:10.0: setting latency timer to 64
[    0.593103] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 22
[    0.593111]   alloc irq_desc for 22 on node -1
[    0.593116]   alloc kstat_irqs on node -1
[    0.593126] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 22 (level, low) -> IRQ 22
[    0.593140] pci 0000:00:15.0: setting latency timer to 64
[    0.593975] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 21
[    0.593983]   alloc irq_desc for 21 on node -1
[    0.593988]   alloc kstat_irqs on node -1
[    0.593999] pci 0000:00:16.0: PCI INT A -> Link[LRP4] -> GSI 21 (level, low) -> IRQ 21
[    0.594012] pci 0000:00:16.0: setting latency timer to 64
[    0.594847] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 20
[    0.594855]   alloc irq_desc for 20 on node -1
[    0.594860]   alloc kstat_irqs on node -1
[    0.594871] pci 0000:00:17.0: PCI INT A -> Link[LRP5] -> GSI 20 (level, low) -> IRQ 20
[    0.594901] pci 0000:00:17.0: setting latency timer to 64
[    0.595746] ACPI: PCI Interrupt Link [LRP6] enabled at IRQ 23
[    0.595756] pci 0000:00:18.0: PCI INT A -> Link[LRP6] -> GSI 23 (level, low) -> IRQ 23
[    0.595769] pci 0000:00:18.0: setting latency timer to 64
[    0.595781] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.595787] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.595793] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.595799] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.595805] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfbffffff]
[    0.595812] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.595819] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.595825] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.595830] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.595836] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.595843] pci_bus 0000:01: resource 8 [mem 0xe0000000-0xfbffffff]
[    0.595849] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.595855] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.595861] pci_bus 0000:03: resource 1 [mem 0xfaf00000-0xfbffffff]
[    0.595868] pci_bus 0000:03: resource 2 [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.595874] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.595955] NET: Registered protocol family 2
[    0.596119] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.596714] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.597680] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.598160] TCP: Hash tables configured (established 131072 bind 65536)
[    0.598167] TCP reno registered
[    0.598177] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.598196] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.598443] NET: Registered protocol family 1
[    0.675171] pci 0000:03:00.0: Boot video device
[    0.675185] PCI: CLS 64 bytes, default 64
[    0.675924] cpufreq-nforce2: No nForce2 chipset.
[    0.675999] Scanning for low memory corruption every 60 seconds
[    0.676263] audit: initializing netlink socket (disabled)
[    0.676286] type=2000 audit(1297191010.672:1): initialized
[    0.695678] highmem bounce pool size: 64 pages
[    0.695691] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.699499] VFS: Disk quotas dquot_6.5.2
[    0.699650] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.701176] fuse init (API version 7.14)
[    0.701416] msgmni has been set to 1648
[    0.708461] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.708469] io scheduler noop registered
[    0.708474] io scheduler deadline registered
[    0.708520] io scheduler cfq registered (default)
[    0.708796] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.708925]   alloc irq_desc for 40 on node -1
[    0.708930]   alloc kstat_irqs on node -1
[    0.708960] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
[    0.709180] pcieport 0000:00:15.0: setting latency timer to 64
[    0.709303]   alloc irq_desc for 41 on node -1
[    0.709308]   alloc kstat_irqs on node -1
[    0.709332] pcieport 0000:00:15.0: irq 41 for MSI/MSI-X
[    0.709523] pcieport 0000:00:16.0: setting latency timer to 64
[    0.709646]   alloc irq_desc for 42 on node -1
[    0.709651]   alloc kstat_irqs on node -1
[    0.709674] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
[    0.709875] pcieport 0000:00:17.0: setting latency timer to 64
[    0.710003]   alloc irq_desc for 43 on node -1
[    0.710007]   alloc kstat_irqs on node -1
[    0.710038] pcieport 0000:00:17.0: irq 43 for MSI/MSI-X
[    0.710229] pcieport 0000:00:18.0: setting latency timer to 64
[    0.710353]   alloc irq_desc for 44 on node -1
[    0.710357]   alloc kstat_irqs on node -1
[    0.710380] pcieport 0000:00:18.0: irq 44 for MSI/MSI-X
[    0.710645] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.710705] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.710963] intel_idle: MWAIT substates: 0x10
[    0.710968] intel_idle: v0.4 model 0x1C
[    0.710972] intel_idle: lapic_timer_reliable_states 0x6
[    0.711314] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.711336] ACPI: Power Button [PWRB]
[    0.711485] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.711495] ACPI: Power Button [PWRF]
[    0.712219] ACPI: acpi_idle yielding to intel_idle
[    0.726583] ERST: Table is not found!
[    0.726847] isapnp: Scanning for PnP cards...
[    0.727375] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.727518] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.728027] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.731153] brd: module loaded
[    0.732556] loop: module loaded
[    0.734000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[    0.734013] pata_acpi 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    0.734070] pata_acpi 0000:00:0b.0: setting latency timer to 64
[    0.734094] pata_acpi 0000:00:0b.0: PCI INT A disabled
[    0.735014] Fixed MDIO Bus: probed
[    0.735121] PPP generic driver version 2.4.2
[    0.735242] tun: Universal TUN/TAP device driver, 1.6
[    0.735248] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.735456] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.736347] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.736358] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.736394] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.736401] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.736507] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.736551] ehci_hcd 0000:00:04.1: debug port 1
[    0.736564] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.736602] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfae7ec00
[    0.746897] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.747201] hub 1-0:1.0: USB hub found
[    0.747214] hub 1-0:1.0: 6 ports detected
[    0.748201] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 20
[    0.748213] ehci_hcd 0000:00:06.1: PCI INT B -> Link[UB12] -> GSI 20 (level, low) -> IRQ 20
[    0.748246] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.748253] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.748359] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.748401] ehci_hcd 0000:00:06.1: debug port 1
[    0.748414] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
[    0.748450] ehci_hcd 0000:00:06.1: irq 20, io mem 0xfae7e800
[    0.758893] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.759175] hub 2-0:1.0: USB hub found
[    0.759188] hub 2-0:1.0: 6 ports detected
[    0.759348] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.760227] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    0.760238] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    0.760270] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.760277] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.760388] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.760437] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfae7f000
[    0.817155] hub 3-0:1.0: USB hub found
[    0.817169] hub 3-0:1.0: 6 ports detected
[    0.818146] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
[    0.818156] ohci_hcd 0000:00:06.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
[    0.818187] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.818194] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.818307] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.818357] ohci_hcd 0000:00:06.0: irq 22, io mem 0xfae7d000
[    0.873204] hub 4-0:1.0: USB hub found
[    0.873220] hub 4-0:1.0: 6 ports detected
[    0.873405] uhci_hcd: USB Universal Host Controller Interface driver
[    0.873686] PNP: No PS/2 controller found. Probing ports directly.
[    0.875389] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.875408] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.875625] mice: PS/2 mouse device common for all mice
[    0.875973] rtc_cmos 00:07: RTC can wake from S4
[    0.876096] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.876163] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.876534] device-mapper: uevent: version 1.0.3
[    0.877025] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.877401] device-mapper: multipath: version 1.1.1 loaded
[    0.877410] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.877840] EISA: Probing bus 0 at eisa.0
[    0.877849] EISA: Cannot allocate resource for mainboard
[    0.877857] Cannot allocate resource for EISA slot 1
[    0.877865] Cannot allocate resource for EISA slot 2
[    0.877873] Cannot allocate resource for EISA slot 3
[    0.877881] Cannot allocate resource for EISA slot 4
[    0.877888] Cannot allocate resource for EISA slot 5
[    0.877896] Cannot allocate resource for EISA slot 6
[    0.877904] Cannot allocate resource for EISA slot 7
[    0.877911] Cannot allocate resource for EISA slot 8
[    0.877917] EISA: Detected 0 cards.
[    0.878728] cpuidle: using governor ladder
[    0.879178] cpuidle: using governor menu
[    0.880040] TCP cubic registered
[    0.880518] NET: Registered protocol family 10
[    0.881600] lo: Disabled Privacy Extensions
[    0.882248] NET: Registered protocol family 17
[    0.882424] Using IPI No-Shortcut mode
[    0.882709] PM: Resume from disk failed.
[    0.882739] registered taskstats version 1
[    0.883492]   Magic number: 15:272:847
[    0.883679] rtc_cmos 00:07: setting system clock to 2011-02-08 18:50:11 UTC (1297191011)
[    0.883688] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.883693] EDD information not available.
[    0.967378] Freeing initrd memory: 10516k freed
[    1.052037] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    1.080177] isapnp: No Plug & Play device found
[    1.080233] Freeing unused kernel memory: 684k freed
[    1.080818] Write protecting the kernel text: 4932k
[    1.080894] Write protecting the kernel read-only data: 1976k
[    1.122796] udev[99]: starting version 163
[    1.332322] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.338115] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    1.338133] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[    1.338149] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.406512] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:27:f1:45
[    1.406522] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.406567] ahci 0000:00:0b.0: version 3.0
[    1.406599] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    1.406691]   alloc irq_desc for 45 on node -1
[    1.406699]   alloc kstat_irqs on node -1
[    1.406722] ahci 0000:00:0b.0: irq 45 for MSI/MSI-X
[    1.406738] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
[    1.406893] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.406905] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pio slum part sxs 
[    1.406918] ahci 0000:00:0b.0: setting latency timer to 64
[    1.408728] scsi0 : ahci
[    1.409167] scsi1 : ahci
[    1.409379] scsi2 : ahci
[    1.409621] scsi3 : ahci
[    1.409878] scsi4 : ahci
[    1.410117] scsi5 : ahci
[    1.410637] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 45
[    1.410646] ata2: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76180 irq 45
[    1.410653] ata3: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76200 irq 45
[    1.410659] ata4: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76280 irq 45
[    1.410666] ata5: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76300 irq 45
[    1.410672] ata6: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76380 irq 45
[    1.568033] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    1.728040] ata2: SATA link down (SStatus 0 SControl 300)
[    1.728062] ata4: SATA link down (SStatus 0 SControl 300)
[    1.728082] ata5: SATA link down (SStatus 0 SControl 300)
[    1.728126] ata6: SATA link down (SStatus 0 SControl 300)
[    1.728134] ata3: SATA link down (SStatus 0 SControl 300)
[    1.728145] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.769254] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    1.769262] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.771222] ata1.00: configured for UDMA/133
[    1.771489] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    1.772059] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.772096] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.772274] sd 0:0:0:0: [sda] Write Protect is off
[    1.772285] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.772375] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.772835]  sda: sda1 sda2 < sda5 >
[    1.806314] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.832518] usbcore: registered new interface driver hiddev
[    1.838975] input: Cypress-Weikeng USB Adapter as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input2
[    1.839275] generic-usb 0003:06F2:0011.0001: input,hidraw0: USB HID v1.10 Keyboard [Cypress-Weikeng USB Adapter] on usb-0000:00:06.0-1/input0
[    1.849071] input: Cypress-Weikeng USB Adapter as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.1/input/input3
[    1.849469] generic-usb 0003:06F2:0011.0002: input,hidraw1: USB HID v1.10 Mouse [Cypress-Weikeng USB Adapter] on usb-0000:00:06.0-1/input1
[    1.849541] usbcore: registered new interface driver usbhid
[    1.849549] usbhid: USB HID core driver
[    2.280027] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.010936] udev[377]: starting version 163
[   10.137980] Adding 12285948k swap on /dev/sda5.  Priority:-1 extents:1 across:12285948k 
[   10.152113] lp: driver loaded but no devices found
[   10.264217] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[   10.264237] ACPI: resource nForce2_smbus [io  0x4e00-0x4e3f] conflicts with ACPI region SM00 [??? 0x00004e00-0x00004e3f flags 0x30]
[   10.264246] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.335300] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.498553] Linux agpgart interface v0.103
[   10.572933] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.612218] type=1400 audit(1297191021.225:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=600 comm="apparmor_parser"
[   10.613112] type=1400 audit(1297191021.225:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=600 comm="apparmor_parser"
[   10.613640] type=1400 audit(1297191021.229:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=600 comm="apparmor_parser"
[   10.636903] type=1400 audit(1297191021.249:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=619 comm="apparmor_parser"
[   10.657199] cfg80211: Calling CRDA to update world regulatory domain
[   10.694022] cfg80211: World regulatory domain updated:
[   10.694034]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.694045]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.694054]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.694064]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.694073]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.694083]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.740585] [drm] Initialized drm 1.1.0 20060810
[   11.141375] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 19
[   11.141396]   alloc irq_desc for 19 on node -1
[   11.141405]   alloc kstat_irqs on node -1
[   11.141431] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[   11.141455] ath9k 0000:04:00.0: setting latency timer to 64
[   11.154055] RPC: Registered udp transport module.
[   11.154065] RPC: Registered tcp transport module.
[   11.154072] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   11.230660] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   11.230680] nouveau 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   11.230699] nouveau 0000:03:00.0: setting latency timer to 64
[   11.254064] Slow work thread pool: Starting up
[   11.278829] type=1400 audit(1297191021.893:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=830 comm="apparmor_parser"
[   11.286372] Slow work thread pool: Ready
[   11.286600] FS-Cache: Loaded
[   11.287811] type=1400 audit(1297191021.901:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=828 comm="apparmor_parser"
[   11.292129] type=1400 audit(1297191021.905:8): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=831 comm="apparmor_parser"
[   11.294512] type=1400 audit(1297191021.909:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=835 comm="apparmor_parser"
[   11.298611] type=1400 audit(1297191021.913:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=828 comm="apparmor_parser"
[   11.299135] type=1400 audit(1297191021.913:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=828 comm="apparmor_parser"
[   11.391294] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x0ace80b1)
[   11.404079] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   11.405755] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   11.407031] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   11.407049] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   11.407062] hda_intel: Disable MSI for Nvidia chipset
[   11.407156] HDA Intel 0000:00:08.0: setting latency timer to 64
[   11.420493] [drm] nouveau 0000:03:00.0: Attempting to load BIOS image from PRAMIN
[   11.460701] FS-Cache: Netfs 'nfs' registered for caching
[   11.497783] [drm] nouveau 0000:03:00.0: ... appears to be valid
[   11.497794] [drm] nouveau 0000:03:00.0: BIT BIOS found
[   11.497804] [drm] nouveau 0000:03:00.0: Bios version 62.79.65.00
[   11.497815] [drm] nouveau 0000:03:00.0: TMDS table revision 2.0 not currently supported
[   11.497824] [drm] nouveau 0000:03:00.0: Found Display Configuration Block version 4.0
[   11.497833] [drm] nouveau 0000:03:00.0: Raw DCB entry 0: 02000300 0000001e
[   11.497842] [drm] nouveau 0000:03:00.0: Raw DCB entry 1: 01011322 00020030
[   11.497851] [drm] nouveau 0000:03:00.0: Raw DCB entry 2: 02022332 00020010
[   11.497859] [drm] nouveau 0000:03:00.0: Raw DCB entry 3: 0000000e 00000000
[   11.497869] [drm] nouveau 0000:03:00.0: DCB connector table: VHER 0x40 5 16 4
[   11.497878] [drm] nouveau 0000:03:00.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   11.497887] [drm] nouveau 0000:03:00.0:   1: 0x00001131: type 0x31 idx 1 tag 0x07
[   11.497896] [drm] nouveau 0000:03:00.0:   2: 0x00002261: type 0x61 idx 2 tag 0x08
[   11.507276] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xDEEA
[   11.588475] ath: EEPROM regdomain: 0x60
[   11.588484] ath: EEPROM indicates we should expect a direct regpair map
[   11.588495] ath: Country alpha2 being used: 00
[   11.588501] ath: Regpair used: 0x60
[   11.623083] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xE1C2
[   11.623097] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xE1C4
[   11.623117] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xE285
[   11.623142] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xE34A
[   11.623152] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xE3AF
[   11.640749] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.643133] Registered led device: ath9k-phy0::radio
[   11.643212] Registered led device: ath9k-phy0::assoc
[   11.643283] Registered led device: ath9k-phy0::tx
[   11.643355] Registered led device: ath9k-phy0::rx
[   11.643388] phy0: Atheros AR9280 Rev:2 mem=0xf88a0000, irq=19
[   11.644595] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   11.651043] [drm] nouveau 0000:03:00.0: 0xE3AF: Condition still not met after 20ms, skipping following opcodes
[   11.651068] [drm] nouveau 0000:03:00.0: 0xC852: parsing output script 0
[   11.651086] [drm] nouveau 0000:03:00.0: 0xC852: parsing output script 0
[   11.651113] [drm] nouveau 0000:03:00.0: Detected 256MiB VRAM
[   11.651120] [drm] nouveau 0000:03:00.0: Stolen system memory at: 0x00d0000000
[   11.765304] [TTM] Zone  kernel: Available graphics memory: 427722 kiB.
[   11.765316] [TTM] Zone highmem: Available graphics memory: 1676814 kiB.
[   11.765324] [TTM] Initializing pool allocator.
[   11.801886] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
[   11.801943] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   11.802455] [drm] nouveau 0000:03:00.0: Allocating FIFO number 1
[   11.809337] [drm] nouveau 0000:03:00.0: nouveau_channel_alloc: initialised FIFO 1
[   11.810570] [drm] nouveau 0000:03:00.0: Detected a DAC output
[   11.810580] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[   11.810586] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[   11.810593] [drm] nouveau 0000:03:00.0: Detected a VGA connector
[   11.810898] [drm] nouveau 0000:03:00.0: Detected a DVI-D connector
[   11.811026] [drm] nouveau 0000:03:00.0: Detected a HDMI connector
[   11.822234] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.832417] svc: failed to register lockdv1 RPC service (errno 97).
[   11.838265] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   11.838936] NFSD: starting 90-second grace period
[   12.090255] [drm] nouveau 0000:03:00.0: allocated 1360x768 fb: 0x40250000, bo f490da00
[   12.093308] [drm] nouveau 0000:03:00.0: 0xC870: parsing output script 1
[   12.093327] [drm] nouveau 0000:03:00.0: 0xC87E: parsing output script 2
[   12.093414] [drm] nouveau 0000:03:00.0: 0xC794: parsing clock script 0
[   12.093695] [drm] nouveau 0000:03:00.0: 0xBF00: parsing clock script 1
[   12.094041] Console: switching to colour frame buffer device 170x48
[   12.095314] fb0: nouveaufb frame buffer device
[   12.095319] drm: registered panic notifier
[   12.095339] [drm] Initialized nouveau 0.0.16 20090420 for 0000:03:00.0 on minor 0
[   12.328530] hda_codec: ALC662 rev1: BIOS auto-probing.
[   14.421047] [drm] nouveau 0000:03:00.0: Allocating FIFO number 2
[   14.427041] [drm] nouveau 0000:03:00.0: nouveau_channel_alloc: initialised FIFO 2
[   18.963207] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   21.953514] eth0: no IPv6 routers present
[  362.965664] eth0: link down.
[  364.873295] eth0: link up.
```

lspci:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xcffa0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0E0000000 mask 0E0000000 uncachable
[    0.000000]   1 base 000000000 mask 000000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cffa0000 (usable)
[    0.000000]  modified: 00000000cffa0000 - 00000000cffae000 (ACPI data)
[    0.000000]  modified: 00000000cffae000 - 00000000cfff0000 (ACPI NVS)
[    0.000000]  modified: 00000000cfff0000 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 9a5000-a86000
[    0.000000] RAMDISK: 375ab000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 00a80000 - 014c4ded
[    0.000000] Move RAMDISK from 00000000375ab000 - 0000000037fefdec to 00a80000 - 014c4dec
[    0.000000] ACPI: RSDP 000faab0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT cffa0000 00040 (v01 081309 RSDT0925 20090813 MSFT 00000097)
[    0.000000] ACPI: FACP cffa0200 00084 (v01 081309 FACP0925 20090813 MSFT 00000097)
[    0.000000] ACPI: DSDT cffa04a0 070E9 (v01   NVDA NVDAACPI 00001000 INTL 20051117)
[    0.000000] ACPI: FACS cffae000 00040
[    0.000000] ACPI: APIC cffa0390 00080 (v01 081309 APIC0925 20090813 MSFT 00000097)
[    0.000000] ACPI: MCFG cffa0410 0003C (v01 081309 OEMMCFG  20090813 MSFT 00000097)
[    0.000000] ACPI: WDRT cffa0450 00047 (v01 081309 NV-WDRT  20090813 MSFT 00000097)
[    0.000000] ACPI: OEMB cffae040 00079 (v01 081309 OEMB0925 20090813 MSFT 00000097)
[    0.000000] ACPI: HPET cffaa4a0 00038 (v01 081309 OEMHPET0 20090813 MSFT 00000097)
[    0.000000] ACPI: NVHD cffae0c0 00284 (v01 081309  NVHDCP  20090813 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2439MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000cffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cffa0
[    0.000000] On node 0 totalpages: 851759
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c14c6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4880 pages used for memmap
[    0.000000]   HighMem zone: 619666 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [15000 - 157ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2ed8000 s36416 r0 d20928 u65536
[    0.000000] pcpu-alloc: s36416 r0 d20928 u65536 alloc=16*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845103
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=e88766e5-497c-41fa-900c-cfe8203b3a2f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 17037120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (51 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a1000 - 00009a41bf]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009fc00 - 00000e6560]   BIOS reserved
[    0.000000]   #7 [00000e66ac - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000e6560 - 00000e66ac]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [00009a5000 - 0000a80000]         PGTABLE
[    0.000000]   #12 [0000a80000 - 00014c5000]     NEW RAMDISK
[    0.000000]   #13 [00014c5000 - 00014c6000]         BOOTMEM
[    0.000000]   #14 [00014c6000 - 0002ec6000]         BOOTMEM
[    0.000000]   #15 [0002ec6000 - 0002ec6004]         BOOTMEM
[    0.000000]   #16 [0002ec6040 - 0002ec6100]         BOOTMEM
[    0.000000]   #17 [0002ec6100 - 0002ec6154]         BOOTMEM
[    0.000000]   #18 [0002ec6180 - 0002ec9180]         BOOTMEM
[    0.000000]   #19 [0002ec9180 - 0002ec9268]         BOOTMEM
[    0.000000]   #20 [0002ec9280 - 0002ed5280]         BOOTMEM
[    0.000000]   #21 [0002ed5280 - 0002ed52a5]         BOOTMEM
[    0.000000]   #22 [0002ed52c0 - 0002ed52e7]         BOOTMEM
[    0.000000]   #23 [0002ed5300 - 0002ed5434]         BOOTMEM
[    0.000000]   #24 [0002ed5440 - 0002ed5480]         BOOTMEM
[    0.000000]   #25 [0002ed5480 - 0002ed54c0]         BOOTMEM
[    0.000000]   #26 [0002ed54c0 - 0002ed5500]         BOOTMEM
[    0.000000]   #27 [0002ed5500 - 0002ed5540]         BOOTMEM
[    0.000000]   #28 [0002ed5540 - 0002ed5580]         BOOTMEM
[    0.000000]   #29 [0002ed5580 - 0002ed55c0]         BOOTMEM
[    0.000000]   #30 [0002ed55c0 - 0002ed5600]         BOOTMEM
[    0.000000]   #31 [0002ed5600 - 0002ed5640]         BOOTMEM
[    0.000000]   #32 [0002ed5640 - 0002ed5680]         BOOTMEM
[    0.000000]   #33 [0002ed5680 - 0002ed56c0]         BOOTMEM
[    0.000000]   #34 [0002ed56c0 - 0002ed56d0]         BOOTMEM
[    0.000000]   #35 [0002ed5700 - 0002ed576a]         BOOTMEM
[    0.000000]   #36 [0002ed5780 - 0002ed57ea]         BOOTMEM
[    0.000000]   #37 [0002ed8000 - 0002ee6000]         BOOTMEM
[    0.000000]   #38 [0002ee8000 - 0002ef6000]         BOOTMEM
[    0.000000]   #39 [0002ef8000 - 0002f06000]         BOOTMEM
[    0.000000]   #40 [0002f08000 - 0002f16000]         BOOTMEM
[    0.000000]   #41 [0002ed7800 - 0002ed7804]         BOOTMEM
[    0.000000]   #42 [0002ed7840 - 0002ed7844]         BOOTMEM
[    0.000000]   #43 [0002ed7880 - 0002ed7890]         BOOTMEM
[    0.000000]   #44 [0002ed78c0 - 0002ed78d0]         BOOTMEM
[    0.000000]   #45 [0002ed7900 - 0002ed7980]         BOOTMEM
[    0.000000]   #46 [0002ed7980 - 0002ed79ac]         BOOTMEM
[    0.000000]   #47 [0002f16000 - 0002f1a000]         BOOTMEM
[    0.000000]   #48 [0002f1a000 - 0002f9a000]         BOOTMEM
[    0.000000]   #49 [0002f9a000 - 0002fda000]         BOOTMEM
[    0.000000]   #50 [0002fda000 - 0004019740]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000cffa0)
[    0.000000] Memory: 3342428k/3407488k available (4928k kernel code, 64608k reserved, 2336k data, 684k init, 2498184k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1600.006 MHz processor.
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.01 BogoMIPS (lpj=6400024)
[    0.004023] pid_max: default: 32768 minimum: 301
[    0.004071] Security Framework initialized
[    0.004107] AppArmor: AppArmor initialized
[    0.004112] Yama: becoming mindful.
[    0.004234] Mount-cache hash table entries: 512
[    0.004483] Initializing cgroup subsys ns
[    0.004493] Initializing cgroup subsys cpuacct
[    0.004504] Initializing cgroup subsys memory
[    0.004523] Initializing cgroup subsys devices
[    0.004529] Initializing cgroup subsys freezer
[    0.004535] Initializing cgroup subsys net_cls
[    0.004582] Atom PSE erratum detected, BIOS microcode update recommended
[    0.004592] CPU: Physical Processor ID: 0
[    0.004597] CPU: Processor Core ID: 0
[    0.004603] mce: CPU supports 5 MCE banks
[    0.004617] CPU0: Thermal monitoring enabled (TM1)
[    0.004625] using mwait in idle threads.
[    0.004639] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.004659] ... version:                3
[    0.004663] ... bit width:              40
[    0.004668] ... generic registers:      2
[    0.004673] ... value mask:             000000ffffffffff
[    0.004678] ... max period:             000000007fffffff
[    0.004683] ... fixed-purpose events:   3
[    0.004688] ... event mask:             0000000700000003
[    0.011778] ACPI: Core revision 20100428
[    0.029619] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.029632] ftrace: allocating 21758 entries in 43 pages
[    0.032110] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032544] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074159] CPU0: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
[    0.076000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.164183]  #2
[    0.008000] Initializing CPU#2
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.256226]  #3 Ok.
[    0.008000] Initializing CPU#3
[    0.008000] Atom PSE erratum detected, BIOS microcode update recommended
[    0.348020] Brought up 4 CPUs
[    0.348029] Total of 4 processors activated (12799.90 BogoMIPS).
[    0.349865] devtmpfs: initialized
[    0.353570] regulator: core version 0.5
[    0.353647] Time: 18:50:11  Date: 02/08/11
[    0.353737] NET: Registered protocol family 16
[    0.353764] Trying to unpack rootfs image as initramfs...
[    0.354080] EISA bus registered
[    0.354104] ACPI: bus type pci registered
[    0.354270] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.354278] PCI: not using MMCONFIG
[    0.354616] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=7
[    0.354621] PCI: Using configuration type 1 for base access
[    0.357020] bio: create slab <bio-0> at 0
[    0.361694] ACPI: EC: Look up EC in DSDT
[    0.366118] ACPI: Executed 1 blocks of module-level executable AML code
[    0.384818] ACPI: Interpreter enabled
[    0.384829] ACPI: (supports S0 S1 S3 S4 S5)
[    0.384885] ACPI: Using IOAPIC for interrupt routing
[    0.385019] PCI: MMCONFIG for domain 0000 [bus 00-1f] at [mem 0xfc000000-0xfdffffff] (base 0xfc000000)
[    0.390159] PCI: MMCONFIG at [mem 0xfc000000-0xfdffffff] reserved in ACPI motherboard resources
[    0.390166] PCI: Using MMCONFIG for extended config space
[    0.426230] ACPI: No dock devices found.
[    0.426243] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.427260] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.428093] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.428102] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.428109] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.428116] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.428123] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xfbffffff]
[    0.428130] pci_root PNP0A03:00: host bridge window [mem 0xfe000000-0xfebfffff]
[    0.428397] pci 0000:00:03.0: reg 10: [io  0x4f00-0x4fff]
[    0.428527] pci 0000:00:03.2: reg 10: [io  0x4900-0x493f]
[    0.428548] pci 0000:00:03.2: reg 20: [io  0x4d00-0x4d3f]
[    0.428558] pci 0000:00:03.2: reg 24: [io  0x4e00-0x4e3f]
[    0.428590] pci 0000:00:03.2: PME# supported from D3hot D3cold
[    0.428601] pci 0000:00:03.2: PME# disabled
[    0.428754] pci 0000:00:03.5: reg 10: [mem 0xfae80000-0xfaefffff]
[    0.428874] pci 0000:00:04.0: reg 10: [mem 0xfae7f000-0xfae7ffff]
[    0.428918] pci 0000:00:04.0: supports D1 D2
[    0.428923] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.428930] pci 0000:00:04.0: PME# disabled
[    0.428968] pci 0000:00:04.1: reg 10: [mem 0xfae7ec00-0xfae7ecff]
[    0.429018] pci 0000:00:04.1: supports D1 D2
[    0.429024] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429031] pci 0000:00:04.1: PME# disabled
[    0.429077] pci 0000:00:06.0: reg 10: [mem 0xfae7d000-0xfae7dfff]
[    0.429120] pci 0000:00:06.0: supports D1 D2
[    0.429126] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429133] pci 0000:00:06.0: PME# disabled
[    0.429170] pci 0000:00:06.1: reg 10: [mem 0xfae7e800-0xfae7e8ff]
[    0.429221] pci 0000:00:06.1: supports D1 D2
[    0.429226] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429233] pci 0000:00:06.1: PME# disabled
[    0.429279] pci 0000:00:08.0: reg 10: [mem 0xfae78000-0xfae7bfff]
[    0.429323] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.429330] pci 0000:00:08.0: PME# disabled
[    0.429422] pci 0000:00:0a.0: reg 10: [mem 0xfae7c000-0xfae7cfff]
[    0.429433] pci 0000:00:0a.0: reg 14: [io  0xd080-0xd087]
[    0.429443] pci 0000:00:0a.0: reg 18: [mem 0xfae7e400-0xfae7e4ff]
[    0.429453] pci 0000:00:0a.0: reg 1c: [mem 0xfae7e000-0xfae7e00f]
[    0.429486] pci 0000:00:0a.0: supports D1 D2
[    0.429491] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429500] pci 0000:00:0a.0: PME# disabled
[    0.429537] pci 0000:00:0b.0: reg 10: [io  0xd000-0xd007]
[    0.429546] pci 0000:00:0b.0: reg 14: [io  0xcc00-0xcc03]
[    0.429555] pci 0000:00:0b.0: reg 18: [io  0xc880-0xc887]
[    0.429565] pci 0000:00:0b.0: reg 1c: [io  0xc800-0xc803]
[    0.429574] pci 0000:00:0b.0: reg 20: [io  0xc480-0xc48f]
[    0.429583] pci 0000:00:0b.0: reg 24: [mem 0xfae76000-0xfae77fff]
[    0.429821] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429833] pci 0000:00:0c.0: PME# disabled
[    0.429937] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.429944] pci 0000:00:10.0: PME# disabled
[    0.430166] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430177] pci 0000:00:15.0: PME# disabled
[    0.430428] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430440] pci 0000:00:16.0: PME# disabled
[    0.430681] pci 0000:00:17.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430693] pci 0000:00:17.0: PME# disabled
[    0.430937] pci 0000:00:18.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.430948] pci 0000:00:18.0: PME# disabled
[    0.431074] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.431083] pci 0000:00:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.431092] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.431100] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.431107] pci 0000:00:09.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.431114] pci 0000:00:09.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.431121] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.431127] pci 0000:00:09.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.431134] pci 0000:00:09.0:   bridge window [mem 0xe0000000-0xfbffffff] (subtractive decode)
[    0.431141] pci 0000:00:09.0:   bridge window [mem 0xfe000000-0xfebfffff] (subtractive decode)
[    0.431297] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.431316] pci 0000:00:0c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.431328] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.431348] pci 0000:00:0c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.431417] pci 0000:03:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.431433] pci 0000:03:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.431449] pci 0000:03:00.0: reg 1c: [mem 0xf8000000-0xf9ffffff 64bit pref]
[    0.431460] pci 0000:03:00.0: reg 24: [io  0xec00-0xec7f]
[    0.431471] pci 0000:03:00.0: reg 30: [mem 0xfafe0000-0xfaffffff pref]
[    0.431546] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.431554] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.431562] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.431571] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.431773] pci 0000:04:00.0: reg 10: [mem 0xfebf0000-0xfebfffff 64bit]
[    0.431846] pci 0000:04:00.0: supports D1
[    0.431852] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
[    0.431860] pci 0000:04:00.0: PME# disabled
[    0.431889] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.431911] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.431930] pci 0000:00:15.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.431943] pci 0000:00:15.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.431963] pci 0000:00:15.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432141] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.432161] pci 0000:00:16.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.432174] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.432194] pci 0000:00:16.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432352] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.432371] pci 0000:00:17.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.432384] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.432405] pci 0000:00:17.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432568] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.432586] pci 0000:00:18.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.432599] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.432618] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.432699] pci_bus 0000:00: on NUMA node 0
[    0.432711] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.433187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PBB0._PRT]
[    0.433373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.433521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.433729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.433901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.434070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.434243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.473133] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.473721] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.474307] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.474886] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.475468] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *0, disabled.
[    0.476075] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.476659] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.477239] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.477818] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.478399] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.478978] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.479558] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.480170] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *0, disabled.
[    0.480755] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.481335] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.481916] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.482521] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *11
[    0.483103] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.483685] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.484298] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.484880] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.485469] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.486053] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.486639] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.487222] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.487806] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.488416] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.489004] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.489590] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.490174] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.490762] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.491347] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.491950] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *15
[    0.492573] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.493170] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.493768] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *15
[    0.494359] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.494953] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.495543] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *9
[    0.496172] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.496855] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.497452] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.498046] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *9
[    0.498639] ACPI: PCI Interrupt Link [LRP0] (IRQs 20 21 22 23) *10
[    0.499230] ACPI: PCI Interrupt Link [LRP1] (IRQs 20 21 22 23) *0, disabled.
[    0.499817] ACPI: PCI Interrupt Link [LRP2] (IRQs 20 21 22 23) *0, disabled.
[    0.500444] ACPI: PCI Interrupt Link [LRP3] (IRQs 20 21 22 23) *11
[    0.501046] ACPI: PCI Interrupt Link [LRP4] (IRQs 20 21 22 23) *9
[    0.501642] ACPI: PCI Interrupt Link [LRP5] (IRQs 20 21 22 23) *15
[    0.502240] ACPI: PCI Interrupt Link [LRP6] (IRQs 20 21 22 23) *14
[    0.502366] HEST: Table is not found!
[    0.502592] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.502601] vgaarb: loaded
[    0.503021] SCSI subsystem initialized
[    0.503057] libata version 3.00 loaded.
[    0.503057] usbcore: registered new interface driver usbfs
[    0.503057] usbcore: registered new interface driver hub
[    0.503057] usbcore: registered new device driver usb
[    0.504485] ACPI: WMI: Mapper loaded
[    0.504491] PCI: Using ACPI for IRQ routing
[    0.504507] PCI: pci_cache_line_size set to 64 bytes
[    0.504671] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.504678] reserve RAM buffer: 00000000cffa0000 - 00000000cfffffff 
[    0.504907] NetLabel: Initializing
[    0.504913] NetLabel:  domain hash size = 128
[    0.504917] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.504944] NetLabel:  unlabeled traffic allowed by default
[    0.505046] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.505059] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.505072] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.516177] Switching to clocksource tsc
[    0.537289] AppArmor: AppArmor Filesystem Enabled
[    0.537330] pnp: PnP ACPI init
[    0.537371] ACPI: bus type pnp registered
[    0.551748] pnp: PnP ACPI: found 12 devices
[    0.551755] ACPI: ACPI bus type pnp unregistered
[    0.551764] PnPBIOS: Disabled by ACPI PNP
[    0.551796] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.551804] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.551811] system 00:05: [io  0x4000-0x407f] has been reserved
[    0.551818] system 00:05: [io  0x4080-0x40ff] has been reserved
[    0.551825] system 00:05: [io  0x4400-0x447f] has been reserved
[    0.551831] system 00:05: [io  0x4480-0x44ff] has been reserved
[    0.551838] system 00:05: [io  0x4800-0x487f] has been reserved
[    0.551845] system 00:05: [io  0x4880-0x48ff] has been reserved
[    0.551853] system 00:05: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.551861] system 00:05: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.551868] system 00:05: [mem 0x000de000-0x000dffff window] has been reserved
[    0.551876] system 00:05: [mem 0xfefe2000-0xfefe3fff] has been reserved
[    0.551883] system 00:05: [mem 0xfefe1000-0xfefe1fff] has been reserved
[    0.551891] system 00:05: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.551907] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.551914] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.551927] system 00:09: [io  0x0a00-0x0a0f] has been reserved
[    0.551934] system 00:09: [io  0x0a10-0x0a1f] has been reserved
[    0.551947] system 00:0a: [mem 0xfc000000-0xfdffffff] has been reserved
[    0.551960] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.551968] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.551975] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.551983] system 00:0b: [mem 0x00100000-0xdfffffff] could not be reserved
[    0.551990] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.590999] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.591006] pci 0000:00:09.0:   bridge window [io  disabled]
[    0.591015] pci 0000:00:09.0:   bridge window [mem disabled]
[    0.591022] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    0.591033] pci 0000:00:0c.0: PCI bridge to [bus 02-02]
[    0.591037] pci 0000:00:0c.0:   bridge window [io  disabled]
[    0.591052] pci 0000:00:0c.0:   bridge window [mem disabled]
[    0.591065] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.591084] pci 0000:00:10.0: PCI bridge to [bus 03-03]
[    0.591092] pci 0000:00:10.0:   bridge window [io  0xe000-0xefff]
[    0.591100] pci 0000:00:10.0:   bridge window [mem 0xfaf00000-0xfbffffff]
[    0.591108] pci 0000:00:10.0:   bridge window [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.591118] pci 0000:00:15.0: PCI bridge to [bus 04-04]
[    0.591122] pci 0000:00:15.0:   bridge window [io  disabled]
[    0.591137] pci 0000:00:15.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.591148] pci 0000:00:15.0:   bridge window [mem pref disabled]
[    0.591166] pci 0000:00:16.0: PCI bridge to [bus 05-05]
[    0.591171] pci 0000:00:16.0:   bridge window [io  disabled]
[    0.591184] pci 0000:00:16.0:   bridge window [mem disabled]
[    0.591195] pci 0000:00:16.0:   bridge window [mem pref disabled]
[    0.591213] pci 0000:00:17.0: PCI bridge to [bus 06-06]
[    0.591217] pci 0000:00:17.0:   bridge window [io  disabled]
[    0.591231] pci 0000:00:17.0:   bridge window [mem disabled]
[    0.591242] pci 0000:00:17.0:   bridge window [mem pref disabled]
[    0.591259] pci 0000:00:18.0: PCI bridge to [bus 07-07]
[    0.591264] pci 0000:00:18.0:   bridge window [io  disabled]
[    0.591277] pci 0000:00:18.0:   bridge window [mem disabled]
[    0.591288] pci 0000:00:18.0:   bridge window [mem pref disabled]
[    0.591318] pci 0000:00:09.0: setting latency timer to 64
[    0.592206] ACPI: PCI Interrupt Link [LRP0] enabled at IRQ 23
[    0.592217]   alloc irq_desc for 23 on node -1
[    0.592222]   alloc kstat_irqs on node -1
[    0.592238] pci 0000:00:0c.0: PCI INT A -> Link[LRP0] -> GSI 23 (level, low) -> IRQ 23
[    0.592252] pci 0000:00:0c.0: setting latency timer to 64
[    0.592269] pci 0000:00:10.0: setting latency timer to 64
[    0.593103] ACPI: PCI Interrupt Link [LRP3] enabled at IRQ 22
[    0.593111]   alloc irq_desc for 22 on node -1
[    0.593116]   alloc kstat_irqs on node -1
[    0.593126] pci 0000:00:15.0: PCI INT A -> Link[LRP3] -> GSI 22 (level, low) -> IRQ 22
[    0.593140] pci 0000:00:15.0: setting latency timer to 64
[    0.593975] ACPI: PCI Interrupt Link [LRP4] enabled at IRQ 21
[    0.593983]   alloc irq_desc for 21 on node -1
[    0.593988]   alloc kstat_irqs on node -1
[    0.593999] pci 0000:00:16.0: PCI INT A -> Link[LRP4] -> GSI 21 (level, low) -> IRQ 21
[    0.594012] pci 0000:00:16.0: setting latency timer to 64
[    0.594847] ACPI: PCI Interrupt Link [LRP5] enabled at IRQ 20
[    0.594855]   alloc irq_desc for 20 on node -1
[    0.594860]   alloc kstat_irqs on node -1
[    0.594871] pci 0000:00:17.0: PCI INT A -> Link[LRP5] -> GSI 20 (level, low) -> IRQ 20
[    0.594901] pci 0000:00:17.0: setting latency timer to 64
[    0.595746] ACPI: PCI Interrupt Link [LRP6] enabled at IRQ 23
[    0.595756] pci 0000:00:18.0: PCI INT A -> Link[LRP6] -> GSI 23 (level, low) -> IRQ 23
[    0.595769] pci 0000:00:18.0: setting latency timer to 64
[    0.595781] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.595787] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.595793] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.595799] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.595805] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfbffffff]
[    0.595812] pci_bus 0000:00: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.595819] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.595825] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.595830] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.595836] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.595843] pci_bus 0000:01: resource 8 [mem 0xe0000000-0xfbffffff]
[    0.595849] pci_bus 0000:01: resource 9 [mem 0xfe000000-0xfebfffff]
[    0.595855] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.595861] pci_bus 0000:03: resource 1 [mem 0xfaf00000-0xfbffffff]
[    0.595868] pci_bus 0000:03: resource 2 [mem 0xe0000000-0xf9ffffff 64bit pref]
[    0.595874] pci_bus 0000:04: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.595955] NET: Registered protocol family 2
[    0.596119] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.596714] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.597680] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.598160] TCP: Hash tables configured (established 131072 bind 65536)
[    0.598167] TCP reno registered
[    0.598177] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.598196] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.598443] NET: Registered protocol family 1
[    0.675171] pci 0000:03:00.0: Boot video device
[    0.675185] PCI: CLS 64 bytes, default 64
[    0.675924] cpufreq-nforce2: No nForce2 chipset.
[    0.675999] Scanning for low memory corruption every 60 seconds
[    0.676263] audit: initializing netlink socket (disabled)
[    0.676286] type=2000 audit(1297191010.672:1): initialized
[    0.695678] highmem bounce pool size: 64 pages
[    0.695691] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.699499] VFS: Disk quotas dquot_6.5.2
[    0.699650] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.701176] fuse init (API version 7.14)
[    0.701416] msgmni has been set to 1648
[    0.708461] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.708469] io scheduler noop registered
[    0.708474] io scheduler deadline registered
[    0.708520] io scheduler cfq registered (default)
[    0.708796] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.708925]   alloc irq_desc for 40 on node -1
[    0.708930]   alloc kstat_irqs on node -1
[    0.708960] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
[    0.709180] pcieport 0000:00:15.0: setting latency timer to 64
[    0.709303]   alloc irq_desc for 41 on node -1
[    0.709308]   alloc kstat_irqs on node -1
[    0.709332] pcieport 0000:00:15.0: irq 41 for MSI/MSI-X
[    0.709523] pcieport 0000:00:16.0: setting latency timer to 64
[    0.709646]   alloc irq_desc for 42 on node -1
[    0.709651]   alloc kstat_irqs on node -1
[    0.709674] pcieport 0000:00:16.0: irq 42 for MSI/MSI-X
[    0.709875] pcieport 0000:00:17.0: setting latency timer to 64
[    0.710003]   alloc irq_desc for 43 on node -1
[    0.710007]   alloc kstat_irqs on node -1
[    0.710038] pcieport 0000:00:17.0: irq 43 for MSI/MSI-X
[    0.710229] pcieport 0000:00:18.0: setting latency timer to 64
[    0.710353]   alloc irq_desc for 44 on node -1
[    0.710357]   alloc kstat_irqs on node -1
[    0.710380] pcieport 0000:00:18.0: irq 44 for MSI/MSI-X
[    0.710645] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.710705] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.710963] intel_idle: MWAIT substates: 0x10
[    0.710968] intel_idle: v0.4 model 0x1C
[    0.710972] intel_idle: lapic_timer_reliable_states 0x6
[    0.711314] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.711336] ACPI: Power Button [PWRB]
[    0.711485] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.711495] ACPI: Power Button [PWRF]
[    0.712219] ACPI: acpi_idle yielding to intel_idle
[    0.726583] ERST: Table is not found!
[    0.726847] isapnp: Scanning for PnP cards...
[    0.727375] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.727518] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.728027] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.731153] brd: module loaded
[    0.732556] loop: module loaded
[    0.734000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[    0.734013] pata_acpi 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    0.734070] pata_acpi 0000:00:0b.0: setting latency timer to 64
[    0.734094] pata_acpi 0000:00:0b.0: PCI INT A disabled
[    0.735014] Fixed MDIO Bus: probed
[    0.735121] PPP generic driver version 2.4.2
[    0.735242] tun: Universal TUN/TAP device driver, 1.6
[    0.735248] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.735456] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.736347] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.736358] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.736394] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.736401] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.736507] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.736551] ehci_hcd 0000:00:04.1: debug port 1
[    0.736564] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.736602] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfae7ec00
[    0.746897] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.747201] hub 1-0:1.0: USB hub found
[    0.747214] hub 1-0:1.0: 6 ports detected
[    0.748201] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 20
[    0.748213] ehci_hcd 0000:00:06.1: PCI INT B -> Link[UB12] -> GSI 20 (level, low) -> IRQ 20
[    0.748246] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.748253] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.748359] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.748401] ehci_hcd 0000:00:06.1: debug port 1
[    0.748414] ehci_hcd 0000:00:06.1: cache line size of 64 is not supported
[    0.748450] ehci_hcd 0000:00:06.1: irq 20, io mem 0xfae7e800
[    0.758893] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.759175] hub 2-0:1.0: USB hub found
[    0.759188] hub 2-0:1.0: 6 ports detected
[    0.759348] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.760227] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    0.760238] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    0.760270] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.760277] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.760388] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.760437] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfae7f000
[    0.817155] hub 3-0:1.0: USB hub found
[    0.817169] hub 3-0:1.0: 6 ports detected
[    0.818146] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
[    0.818156] ohci_hcd 0000:00:06.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
[    0.818187] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.818194] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.818307] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.818357] ohci_hcd 0000:00:06.0: irq 22, io mem 0xfae7d000
[    0.873204] hub 4-0:1.0: USB hub found
[    0.873220] hub 4-0:1.0: 6 ports detected
[    0.873405] uhci_hcd: USB Universal Host Controller Interface driver
[    0.873686] PNP: No PS/2 controller found. Probing ports directly.
[    0.875389] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.875408] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.875625] mice: PS/2 mouse device common for all mice
[    0.875973] rtc_cmos 00:07: RTC can wake from S4
[    0.876096] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.876163] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.876534] device-mapper: uevent: version 1.0.3
[    0.877025] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.877401] device-mapper: multipath: version 1.1.1 loaded
[    0.877410] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.877840] EISA: Probing bus 0 at eisa.0
[    0.877849] EISA: Cannot allocate resource for mainboard
[    0.877857] Cannot allocate resource for EISA slot 1
[    0.877865] Cannot allocate resource for EISA slot 2
[    0.877873] Cannot allocate resource for EISA slot 3
[    0.877881] Cannot allocate resource for EISA slot 4
[    0.877888] Cannot allocate resource for EISA slot 5
[    0.877896] Cannot allocate resource for EISA slot 6
[    0.877904] Cannot allocate resource for EISA slot 7
[    0.877911] Cannot allocate resource for EISA slot 8
[    0.877917] EISA: Detected 0 cards.
[    0.878728] cpuidle: using governor ladder
[    0.879178] cpuidle: using governor menu
[    0.880040] TCP cubic registered
[    0.880518] NET: Registered protocol family 10
[    0.881600] lo: Disabled Privacy Extensions
[    0.882248] NET: Registered protocol family 17
[    0.882424] Using IPI No-Shortcut mode
[    0.882709] PM: Resume from disk failed.
[    0.882739] registered taskstats version 1
[    0.883492]   Magic number: 15:272:847
[    0.883679] rtc_cmos 00:07: setting system clock to 2011-02-08 18:50:11 UTC (1297191011)
[    0.883688] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.883693] EDD information not available.
[    0.967378] Freeing initrd memory: 10516k freed
[    1.052037] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    1.080177] isapnp: No Plug & Play device found
[    1.080233] Freeing unused kernel memory: 684k freed
[    1.080818] Write protecting the kernel text: 4932k
[    1.080894] Write protecting the kernel read-only data: 1976k
[    1.122796] udev[99]: starting version 163
[    1.332322] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.338115] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[    1.338133] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 21 (level, low) -> IRQ 21
[    1.338149] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.406512] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:01:2e:27:f1:45
[    1.406522] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    1.406567] ahci 0000:00:0b.0: version 3.0
[    1.406599] ahci 0000:00:0b.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    1.406691]   alloc irq_desc for 45 on node -1
[    1.406699]   alloc kstat_irqs on node -1
[    1.406722] ahci 0000:00:0b.0: irq 45 for MSI/MSI-X
[    1.406738] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
[    1.406893] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.406905] ahci 0000:00:0b.0: flags: 64bit ncq sntf led pio slum part sxs 
[    1.406918] ahci 0000:00:0b.0: setting latency timer to 64
[    1.408728] scsi0 : ahci
[    1.409167] scsi1 : ahci
[    1.409379] scsi2 : ahci
[    1.409621] scsi3 : ahci
[    1.409878] scsi4 : ahci
[    1.410117] scsi5 : ahci
[    1.410637] ata1: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76100 irq 45
[    1.410646] ata2: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76180 irq 45
[    1.410653] ata3: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76200 irq 45
[    1.410659] ata4: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76280 irq 45
[    1.410666] ata5: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76300 irq 45
[    1.410672] ata6: SATA max UDMA/133 abar m8192@0xfae76000 port 0xfae76380 irq 45
[    1.568033] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    1.728040] ata2: SATA link down (SStatus 0 SControl 300)
[    1.728062] ata4: SATA link down (SStatus 0 SControl 300)
[    1.728082] ata5: SATA link down (SStatus 0 SControl 300)
[    1.728126] ata6: SATA link down (SStatus 0 SControl 300)
[    1.728134] ata3: SATA link down (SStatus 0 SControl 300)
[    1.728145] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.769254] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    1.769262] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.771222] ata1.00: configured for UDMA/133
[    1.771489] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    1.772059] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.772096] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.772274] sd 0:0:0:0: [sda] Write Protect is off
[    1.772285] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.772375] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.772835]  sda: sda1 sda2 < sda5 >
[    1.806314] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.832518] usbcore: registered new interface driver hiddev
[    1.838975] input: Cypress-Weikeng USB Adapter as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0/input/input2
[    1.839275] generic-usb 0003:06F2:0011.0001: input,hidraw0: USB HID v1.10 Keyboard [Cypress-Weikeng USB Adapter] on usb-0000:00:06.0-1/input0
[    1.849071] input: Cypress-Weikeng USB Adapter as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.1/input/input3
[    1.849469] generic-usb 0003:06F2:0011.0002: input,hidraw1: USB HID v1.10 Mouse [Cypress-Weikeng USB Adapter] on usb-0000:00:06.0-1/input1
[    1.849541] usbcore: registered new interface driver usbhid
[    1.849549] usbhid: USB HID core driver
[    2.280027] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.010936] udev[377]: starting version 163
[   10.137980] Adding 12285948k swap on /dev/sda5.  Priority:-1 extents:1 across:12285948k 
[   10.152113] lp: driver loaded but no devices found
[   10.264217] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
[   10.264237] ACPI: resource nForce2_smbus [io  0x4e00-0x4e3f] conflicts with ACPI region SM00 [??? 0x00004e00-0x00004e3f flags 0x30]
[   10.264246] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.335300] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.498553] Linux agpgart interface v0.103
[   10.572933] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.612218] type=1400 audit(1297191021.225:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=600 comm="apparmor_parser"
[   10.613112] type=1400 audit(1297191021.225:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=600 comm="apparmor_parser"
[   10.613640] type=1400 audit(1297191021.229:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=600 comm="apparmor_parser"
[   10.636903] type=1400 audit(1297191021.249:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=619 comm="apparmor_parser"
[   10.657199] cfg80211: Calling CRDA to update world regulatory domain
[   10.694022] cfg80211: World regulatory domain updated:
[   10.694034]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.694045]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.694054]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.694064]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.694073]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.694083]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.740585] [drm] Initialized drm 1.1.0 20060810
[   11.141375] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 19
[   11.141396]   alloc irq_desc for 19 on node -1
[   11.141405]   alloc kstat_irqs on node -1
[   11.141431] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[   11.141455] ath9k 0000:04:00.0: setting latency timer to 64
[   11.154055] RPC: Registered udp transport module.
[   11.154065] RPC: Registered tcp transport module.
[   11.154072] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   11.230660] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   11.230680] nouveau 0000:03:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   11.230699] nouveau 0000:03:00.0: setting latency timer to 64
[   11.254064] Slow work thread pool: Starting up
[   11.278829] type=1400 audit(1297191021.893:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=830 comm="apparmor_parser"
[   11.286372] Slow work thread pool: Ready
[   11.286600] FS-Cache: Loaded
[   11.287811] type=1400 audit(1297191021.901:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=828 comm="apparmor_parser"
[   11.292129] type=1400 audit(1297191021.905:8): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=831 comm="apparmor_parser"
[   11.294512] type=1400 audit(1297191021.909:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=835 comm="apparmor_parser"
[   11.298611] type=1400 audit(1297191021.913:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=828 comm="apparmor_parser"
[   11.299135] type=1400 audit(1297191021.913:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=828 comm="apparmor_parser"
[   11.391294] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x0ace80b1)
[   11.404079] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   11.405755] HDA Intel 0000:00:08.0: power state changed by ACPI to D0
[   11.407031] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   11.407049] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   11.407062] hda_intel: Disable MSI for Nvidia chipset
[   11.407156] HDA Intel 0000:00:08.0: setting latency timer to 64
[   11.420493] [drm] nouveau 0000:03:00.0: Attempting to load BIOS image from PRAMIN
[   11.460701] FS-Cache: Netfs 'nfs' registered for caching
[   11.497783] [drm] nouveau 0000:03:00.0: ... appears to be valid
[   11.497794] [drm] nouveau 0000:03:00.0: BIT BIOS found
[   11.497804] [drm] nouveau 0000:03:00.0: Bios version 62.79.65.00
[   11.497815] [drm] nouveau 0000:03:00.0: TMDS table revision 2.0 not currently supported
[   11.497824] [drm] nouveau 0000:03:00.0: Found Display Configuration Block version 4.0
[   11.497833] [drm] nouveau 0000:03:00.0: Raw DCB entry 0: 02000300 0000001e
[   11.497842] [drm] nouveau 0000:03:00.0: Raw DCB entry 1: 01011322 00020030
[   11.497851] [drm] nouveau 0000:03:00.0: Raw DCB entry 2: 02022332 00020010
[   11.497859] [drm] nouveau 0000:03:00.0: Raw DCB entry 3: 0000000e 00000000
[   11.497869] [drm] nouveau 0000:03:00.0: DCB connector table: VHER 0x40 5 16 4
[   11.497878] [drm] nouveau 0000:03:00.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   11.497887] [drm] nouveau 0000:03:00.0:   1: 0x00001131: type 0x31 idx 1 tag 0x07
[   11.497896] [drm] nouveau 0000:03:00.0:   2: 0x00002261: type 0x61 idx 2 tag 0x08
[   11.507276] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xDEEA
[   11.588475] ath: EEPROM regdomain: 0x60
[   11.588484] ath: EEPROM indicates we should expect a direct regpair map
[   11.588495] ath: Country alpha2 being used: 00
[   11.588501] ath: Regpair used: 0x60
[   11.623083] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xE1C2
[   11.623097] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xE1C4
[   11.623117] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xE285
[   11.623142] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xE34A
[   11.623152] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xE3AF
[   11.640749] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.643133] Registered led device: ath9k-phy0::radio
[   11.643212] Registered led device: ath9k-phy0::assoc
[   11.643283] Registered led device: ath9k-phy0::tx
[   11.643355] Registered led device: ath9k-phy0::rx
[   11.643388] phy0: Atheros AR9280 Rev:2 mem=0xf88a0000, irq=19
[   11.644595] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   11.651043] [drm] nouveau 0000:03:00.0: 0xE3AF: Condition still not met after 20ms, skipping following opcodes
[   11.651068] [drm] nouveau 0000:03:00.0: 0xC852: parsing output script 0
[   11.651086] [drm] nouveau 0000:03:00.0: 0xC852: parsing output script 0
[   11.651113] [drm] nouveau 0000:03:00.0: Detected 256MiB VRAM
[   11.651120] [drm] nouveau 0000:03:00.0: Stolen system memory at: 0x00d0000000
[   11.765304] [TTM] Zone  kernel: Available graphics memory: 427722 kiB.
[   11.765316] [TTM] Zone highmem: Available graphics memory: 1676814 kiB.
[   11.765324] [TTM] Initializing pool allocator.
[   11.801886] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
[   11.801943] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   11.802455] [drm] nouveau 0000:03:00.0: Allocating FIFO number 1
[   11.809337] [drm] nouveau 0000:03:00.0: nouveau_channel_alloc: initialised FIFO 1
[   11.810570] [drm] nouveau 0000:03:00.0: Detected a DAC output
[   11.810580] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[   11.810586] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[   11.810593] [drm] nouveau 0000:03:00.0: Detected a VGA connector
[   11.810898] [drm] nouveau 0000:03:00.0: Detected a DVI-D connector
[   11.811026] [drm] nouveau 0000:03:00.0: Detected a HDMI connector
[   11.822234] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.832417] svc: failed to register lockdv1 RPC service (errno 97).
[   11.838265] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   11.838936] NFSD: starting 90-second grace period
[   12.090255] [drm] nouveau 0000:03:00.0: allocated 1360x768 fb: 0x40250000, bo f490da00
[   12.093308] [drm] nouveau 0000:03:00.0: 0xC870: parsing output script 1
[   12.093327] [drm] nouveau 0000:03:00.0: 0xC87E: parsing output script 2
[   12.093414] [drm] nouveau 0000:03:00.0: 0xC794: parsing clock script 0
[   12.093695] [drm] nouveau 0000:03:00.0: 0xBF00: parsing clock script 1
[   12.094041] Console: switching to colour frame buffer device 170x48
[   12.095314] fb0: nouveaufb frame buffer device
[   12.095319] drm: registered panic notifier
[   12.095339] [drm] Initialized nouveau 0.0.16 20090420 for 0000:03:00.0 on minor 0
[   12.328530] hda_codec: ALC662 rev1: BIOS auto-probing.
[   14.421047] [drm] nouveau 0000:03:00.0: Allocating FIFO number 2
[   14.427041] [drm] nouveau 0000:03:00.0: nouveau_channel_alloc: initialised FIFO 2
[   18.963207] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   21.953514] eth0: no IPv6 routers present
[  362.965664] eth0: link down.
[  364.873295] eth0: link up.
```

---

### Post by ronnielsen1 on 2011-02-08
Does lsusb show anything?

---

### Post by Chrus on 2011-02-08
lsusb give me this:
```
Bus 004 Device 002: ID 06f2:0011 Emine Technology Co. KVM Switch Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1b80:d393 Afatech 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by ronnielsen1 on 2011-02-08
[http://ubuntuforums.org/showthread.php?t=1458746](http://ubuntuforums.org/showthread.php?t=1458746)

The Afatech one is your tuner. I have to go to work so I don't have time to check. Check out the link above. Good luck. Try the different utilities like tvtime, etc and see what the link tells you.

---

### Post by Chrus on 2011-02-08
Thanks mate. Something to work with. Will let you know if i get anywhere with it.

Cheers.

---

### Post by Chrus on 2011-02-09
Still not having any joy with this one.

I followed this post ([http://ubuntuforums.org/showpost.php?p=9712937&postcount=126]("http://ubuntuforums.org/showpost.php?p=9712937&postcount=126")) with no results.

Cant get anything out of TV Time or VLC either.

Any other advice?

Is it worth persisting with this tuner? Or would I be better off buying a new one that will actually work?

---

### Post by ronnielsen1 on 2011-02-09
I can't find any specific SOLVED instances of this card but it seems that kaffeine might pick up on this tuner. You could try installing kaffeine and see if it picks up on your card and it would be a starting point anyway.

---

### Post by Chrus on 2011-02-09
No luck with Kaffeine eihter. Its still not showing up at all.

---

### Post by Chrus on 2011-02-09
Forgive me if this a stupid question, but im kinda new to the whole TV tuner card in linux thing.

But I should be seeing an adapter0 in /dev/dvb/, right?

At the moment the dvb folder isnt even there.

---

### Post by ronnielsen1 on 2011-02-12
Sorry, my internet provider went down for a couple of days. Not sure about that one

---

### Post by spegru on 2011-02-12
Tuners should be visible, whether working or not, using either lsusb for usb types or lspci for onboard ones.
If they dont appear in the list make sure y0ou are looking properly as sometimes with generic no-name types, they will appear under a chipset name instead of what you were expecting.
If they really dont appear check that it's really working/plugged in properly, and in the case of USB types, make sure the USB lead is reasonable quality as some cannot deliver enough power. Similarly for usb types make sure that the usb port itself can deliver enough power - if in doubt about that try using a powered usb hub.
If the device is detected using lsusb/lspci then you also need firmware  - which needs to be in/lib/firmware and be there when the device is plugged in. Alot of firmware is often included with the distro but not necessarily yours. Look out for 'warm' or 'cold' messages from lsusb/lspci for that one - if 'cold' then you dont have the firmware. Try googling the usb or pci ID  and linuxtv to find it.
If you are in ubuntu or mint or other gnome system I suggest Me-Tv rather than kaffiene, which is mainly a KDE thing

---

### Post by F15h3r on 2011-02-24
Hey there, i am also having U7300 USB TV dongle. But when i plug it in, and do lsusb i get one new line:

Bus 002 Device 006: ID 1b80:d393 Afatech

I did some google-ing, and found out that this could be some chip vendor to gigabyte or something..

I tried to get it working with [this]("http://my.opera.com/linuxadore/blog/gigabyte-u7000-dvb-t-usb-dongle-on-ubuntu-10-4") tutorial, but no luck, cause tutorial is for u7000..

I am pretty new to ubuntu & linux-tv.. So i dont really know what i can do next..

Regards!

---

### Post by winewood on 2011-02-24
[SIZE=2]I found that the Silicon Dust **HDHomeRun**[/SIZE][SIZE=2]is the best tuner for viewing TV for me.  I can connect it anywhere on my network to my Antenna or video source, and I am only left with configuring a program to use it.

Get the Dual one, and you can record on one side, and channel surf on the other.  My mythbox hooked up to it, and I didn't even have to mess with drivers.
[/SIZE]

---

### Post by SpeedyGonsales on 2012-06-11
Try this: [http://linuxtv.org/wiki/index.php/Gigabyte_U7300](http://linuxtv.org/wiki/index.php/Gigabyte_U7300)

Now my Gigabyte U7300 adapter is working in Ubuntu. :guitar:

---

