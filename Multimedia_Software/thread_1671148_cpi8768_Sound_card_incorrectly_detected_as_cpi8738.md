---
title: "cpi8768 Sound card incorrectly detected as cpi8738"
date: 2011-01-19
forum: Multimedia Software
---

### Post by argoth on 2011-01-19
---EDIT: I just realized I used a p instead of an m...

Hi, 

I received a cmi8768 sound card. it is being detected as cmi8738. I'm not sure what info is needed. So I'm including my dmesg, lspci, and aplay -l

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic-pae (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 03:21:31 UTC 2010 (Ubuntu 2.6.35-24.42-generic-pae 2.6.35.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff40000 (usable)
[    0.000000]  BIOS-e820: 000000003ff40000 - 000000003ff50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff50000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffbc0000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3ff40 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 disabled
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
[    0.000000]  modified: 0000000000100000 - 000000003ff40000 (usable)
[    0.000000]  modified: 000000003ff40000 - 000000003ff50000 (ACPI data)
[    0.000000]  modified: 000000003ff50000 - 0000000040000000 (ACPI NVS)
[    0.000000]  modified: 00000000ffbc0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 15000-1a000
[    0.000000] RAMDISK: 2f572000 - 2ffb0000
[    0.000000] ACPI: RSDP 000f6b70 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 3ff40000 00030 (v01 A M I  OEMRSDT  03000430 MSFT 00000097)
[    0.000000] ACPI: FACP 3ff40200 00081 (v02 A M I  OEMFACP  03000430 MSFT 00000097)
[    0.000000] ACPI: DSDT 3ff40360 0352C (v01    P4I    P4IPE 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 3ff50000 00040
[    0.000000] ACPI: APIC 3ff40300 0005C (v01 A M I  OEMAPIC  03000430 MSFT 00000097)
[    0.000000] ACPI: OEMB 3ff50040 00040 (v01 A M I  OEMBIOS  03000430 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 131MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0003ff40
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ff40
[    0.000000] On node 0 totalpages: 261839
[    0.000000] free_area_init_node: node 0, pgdat c0840a00, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 263 pages used for memmap
[    0.000000]   HighMem zone: 33339 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:bfbc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1a00000 s39872 r0 d21568 u1048576
[    0.000000] pcpu-alloc: s39872 r0 d21568 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=d49cc2ed-18d6-4622-bf91-104a4e5db472 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5238720 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (45 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009fc65c]   TEXT DATA BSS
[    0.000000]   #3 [002f572000 - 002ffb0000]         RAMDISK
[    0.000000]   #4 [00009fd000 - 0000a04198]             BRK
[    0.000000]   #5 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #7 [000009fc00 - 00000fa250]   BIOS reserved
[    0.000000]   #8 [00000fa368 - 00000ff780]   BIOS reserved
[    0.000000]   #9 [00000fa250 - 00000fa368]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001801000]         BOOTMEM
[    0.000000]   #15 [0001801000 - 0001801004]         BOOTMEM
[    0.000000]   #16 [0001801040 - 0001801100]         BOOTMEM
[    0.000000]   #17 [0001801100 - 00018011a8]         BOOTMEM
[    0.000000]   #18 [00018011c0 - 00018041c0]         BOOTMEM
[    0.000000]   #19 [00018041c0 - 00018041dc]         BOOTMEM
[    0.000000]   #20 [0001804200 - 0001804e00]         BOOTMEM
[    0.000000]   #21 [0001804e00 - 0001804e2f]         BOOTMEM
[    0.000000]   #22 [0001804e40 - 0001804f60]         BOOTMEM
[    0.000000]   #23 [0001804f80 - 0001804fc0]         BOOTMEM
[    0.000000]   #24 [0001804fc0 - 0001805000]         BOOTMEM
[    0.000000]   #25 [0001805000 - 0001805040]         BOOTMEM
[    0.000000]   #26 [0001805040 - 0001805080]         BOOTMEM
[    0.000000]   #27 [0001805080 - 00018050c0]         BOOTMEM
[    0.000000]   #28 [00018050c0 - 0001805100]         BOOTMEM
[    0.000000]   #29 [0001805100 - 0001805140]         BOOTMEM
[    0.000000]   #30 [0001805140 - 0001805150]         BOOTMEM
[    0.000000]   #31 [0001805180 - 00018051ee]         BOOTMEM
[    0.000000]   #32 [0001805200 - 000180526e]         BOOTMEM
[    0.000000]   #33 [0001a00000 - 0001a0f000]         BOOTMEM
[    0.000000]   #34 [0001b00000 - 0001b0f000]         BOOTMEM
[    0.000000]   #35 [0001807280 - 0001807284]         BOOTMEM
[    0.000000]   #36 [00018072c0 - 00018072c4]         BOOTMEM
[    0.000000]   #37 [0001807300 - 0001807308]         BOOTMEM
[    0.000000]   #38 [0001807340 - 0001807348]         BOOTMEM
[    0.000000]   #39 [0001807380 - 0001807420]         BOOTMEM
[    0.000000]   #40 [0001807440 - 0001807488]         BOOTMEM
[    0.000000]   #41 [00018074c0 - 000180b4c0]         BOOTMEM
[    0.000000]   #42 [000180b4c0 - 000188b4c0]         BOOTMEM
[    0.000000]   #43 [000188b4c0 - 00018cb4c0]         BOOTMEM
[    0.000000]   #44 [0001b0f000 - 000200dfc0]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003ff40)
[    0.000000] Memory: 1013368k/1047808k available (5088k kernel code, 33988k reserved, 2437k data, 704k init, 134408k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc085a000 - 0xc090a000   ( 704 kB)
[    0.000000]       .data : 0xc05f80da - 0xc0859648   (2437 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f80da   (5088 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3192.090 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6384.18 BogoMIPS (lpj=12768360)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004037] Security Framework initialized
[    0.004066] AppArmor: AppArmor initialized
[    0.004069] Yama: becoming mindful.
[    0.004148] Mount-cache hash table entries: 512
[    0.004336] Initializing cgroup subsys ns
[    0.004343] Initializing cgroup subsys cpuacct
[    0.004349] Initializing cgroup subsys memory
[    0.004361] Initializing cgroup subsys devices
[    0.004364] Initializing cgroup subsys freezer
[    0.004367] Initializing cgroup subsys net_cls
[    0.004411] CPU: Physical Processor ID: 0
[    0.004414] CPU: Processor Core ID: 0
[    0.004418] mce: CPU supports 4 MCE banks
[    0.004432] CPU0: Thermal monitoring enabled (TM1)
[    0.004439] using mwait in idle threads.
[    0.004448] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.004457] ... version:                0
[    0.004459] ... bit width:              40
[    0.004462] ... generic registers:      18
[    0.004464] ... value mask:             000000ffffffffff
[    0.004467] ... max period:             0000007fffffffff
[    0.004469] ... fixed-purpose events:   0
[    0.004472] ... event mask:             000000000003ffff
[    0.009242] ACPI: Core revision 20100428
[    0.015135] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.015141] ftrace: allocating 22392 entries in 44 pages
[    0.016081] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016380] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058192] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[    0.060000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.148022] Brought up 2 CPUs
[    0.148028] Total of 2 processors activated (12768.71 BogoMIPS).
[    0.148441] devtmpfs: initialized
[    0.149449] regulator: core version 0.5
[    0.149474] Time: 15:10:53  Date: 01/19/11
[    0.149529] NET: Registered protocol family 16
[    0.149544] Trying to unpack rootfs image as initramfs...
[    0.149754] EISA bus registered
[    0.149770] ACPI: bus type pci registered
[    0.149949] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    0.149953] PCI: Using configuration type 1 for base access
[    0.153096] bio: create slab <bio-0> at 0
[    0.154863] ACPI: EC: Look up EC in DSDT
[    0.157391] ACPI: Executed 1 blocks of module-level executable AML code
[    0.166956] ACPI: Interpreter enabled
[    0.166966] ACPI: (supports S0 S1 S4 S5)
[    0.167007] ACPI: Using IOAPIC for interrupt routing
[    0.178219] ACPI Warning: Incorrect checksum in table [OEMB] - 0x08, should be 0xFF (20100428/tbutils-314)
[    0.178439] ACPI: No dock devices found.
[    0.178447] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.178643] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.179041] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.179047] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.179053] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.179058] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xffefffff] (ignored)
[    0.179082] pci 0000:00:00.0: Enabling MCH 'Overflow' Device
[    0.179096] pci 0000:00:00.0: reg 10: [mem 0xf8000000-0xfbffffff pref]
[    0.179212] pci 0000:00:06.0: reg 10: [mem 0xfecf0000-0xfecf0fff]
[    0.179324] pci 0000:00:1d.0: reg 20: [io  0xe000-0xe01f]
[    0.179392] pci 0000:00:1d.1: reg 20: [io  0xe400-0xe41f]
[    0.179461] pci 0000:00:1d.2: reg 20: [io  0xe800-0xe81f]
[    0.179527] pci 0000:00:1d.3: reg 20: [io  0xec00-0xec1f]
[    0.179593] pci 0000:00:1d.7: reg 10: [mem 0xfebffc00-0xfebfffff]
[    0.179663] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.179671] pci 0000:00:1d.7: PME# disabled
[    0.179778] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.179788] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH4 ACPI/GPIO/TCO
[    0.179796] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH4 GPIO
[    0.179827] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.179837] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.179848] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.179858] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.179868] pci 0000:00:1f.1: reg 20: [io  0xfc00-0xfc0f]
[    0.179878] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.179948] pci 0000:01:00.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    0.179957] pci 0000:01:00.0: reg 14: [io  0xa800-0xa8ff]
[    0.179966] pci 0000:01:00.0: reg 18: [mem 0xfc9f0000-0xfc9fffff]
[    0.180009] pci 0000:01:00.0: reg 30: [mem 0xfc9c0000-0xfc9dffff pref]
[    0.180042] pci 0000:01:00.0: supports D1 D2
[    0.180076] pci 0000:01:00.1: reg 10: [mem 0xe0000000-0xe7ffffff pref]
[    0.180085] pci 0000:01:00.1: reg 14: [mem 0xfc9e0000-0xfc9effff]
[    0.180127] pci 0000:01:00.1: supports D1 D2
[    0.180180] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.180187] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.180194] pci 0000:00:01.0:   bridge window [mem 0xfc900000-0xfc9fffff]
[    0.180201] pci 0000:00:01.0:   bridge window [mem 0xd7f00000-0xf7efffff pref]
[    0.180253] pci 0000:02:02.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.180357] pci 0000:02:03.0: reg 10: [io  0xb800-0xb8ff]
[    0.180410] pci 0000:02:03.0: supports D1 D2
[    0.180457] pci 0000:02:04.0: reg 10: [io  0xbc00-0xbc3f]
[    0.180512] pci 0000:02:04.0: supports D2
[    0.180516] pci 0000:02:04.0: PME# supported from D0 D2 D3hot D3cold
[    0.180523] pci 0000:02:04.0: PME# disabled
[    0.180566] pci 0000:02:05.0: reg 10: [io  0xb400-0xb4ff]
[    0.180577] pci 0000:02:05.0: reg 14: [mem 0xfeaffc00-0xfeaffcff]
[    0.180630] pci 0000:02:05.0: supports D1 D2
[    0.180635] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.180641] pci 0000:02:05.0: PME# disabled
[    0.180688] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.180696] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.180703] pci 0000:00:1e.0:   bridge window [mem 0xfca00000-0xfeafffff]
[    0.180711] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.180716] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.180722] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffffffffffff] (subtractive decode)
[    0.180739] pci_bus 0000:00: on NUMA node 0
[    0.180748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.180923] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.185189] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.185379] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.185564] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.185750] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.185936] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.186106] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.186296] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.186466] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.186563] HEST: Table is not found!
[    0.186715] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.186727] vgaarb: loaded
[    0.187044] SCSI subsystem initialized
[    0.187205] libata version 3.00 loaded.
[    0.187307] usbcore: registered new interface driver usbfs
[    0.187334] usbcore: registered new interface driver hub
[    0.187382] usbcore: registered new device driver usb
[    0.187632] ACPI: WMI: Mapper loaded
[    0.187636] PCI: Using ACPI for IRQ routing
[    0.187644] PCI: pci_cache_line_size set to 64 bytes
[    0.187760] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.187766] reserve RAM buffer: 000000003ff40000 - 000000003fffffff 
[    0.187947] NetLabel: Initializing
[    0.187951] NetLabel:  domain hash size = 128
[    0.187954] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.187979] NetLabel:  unlabeled traffic allowed by default
[    0.188137] hpet clockevent registered
[    0.188143] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.188151] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.188161] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.192132] Switching to clocksource tsc
[    0.212442] AppArmor: AppArmor Filesystem Enabled
[    0.212475] pnp: PnP ACPI init
[    0.212522] ACPI: bus type pnp registered
[    0.218174] pnp: PnP ACPI: found 11 devices
[    0.218180] ACPI: ACPI bus type pnp unregistered
[    0.218187] PnPBIOS: Disabled by ACPI PNP
[    0.218213] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.218220] system 00:07: [io  0x0800-0x087f] has been reserved
[    0.218226] system 00:07: [io  0x0400-0x041f] has been reserved
[    0.218231] system 00:07: [io  0x0480-0x04bf] has been reserved
[    0.218238] system 00:07: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.218245] system 00:07: [mem 0xffb00000-0xffbfffff] could not be reserved
[    0.218258] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.218264] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.218276] system 00:09: [io  0x0680-0x06ff] has been reserved
[    0.218282] system 00:09: [io  0x0295-0x0296] has been reserved
[    0.218295] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.218301] system 00:0a: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.218307] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.218313] system 00:0a: [mem 0x00100000-0x3fffffff] could not be reserved
[    0.218319] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
[    0.256123] pci 0000:00:1f.1: BAR 5: assigned [mem 0x40000000-0x400003ff]
[    0.256137] pci 0000:00:1f.1: BAR 5: set to [mem 0x40000000-0x400003ff] (PCI address [0x40000000-0x400003ff]
[    0.256148] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.256154] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.256163] pci 0000:00:01.0:   bridge window [mem 0xfc900000-0xfc9fffff]
[    0.256170] pci 0000:00:01.0:   bridge window [mem 0xd7f00000-0xf7efffff pref]
[    0.256180] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.256186] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.256194] pci 0000:00:1e.0:   bridge window [mem 0xfca00000-0xfeafffff]
[    0.256201] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.256227] pci 0000:00:1e.0: setting latency timer to 64
[    0.256234] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.256239] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
[    0.256244] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.256249] pci_bus 0000:01: resource 1 [mem 0xfc900000-0xfc9fffff]
[    0.256254] pci_bus 0000:01: resource 2 [mem 0xd7f00000-0xf7efffff pref]
[    0.256259] pci_bus 0000:02: resource 0 [io  0xb000-0xbfff]
[    0.256264] pci_bus 0000:02: resource 1 [mem 0xfca00000-0xfeafffff]
[    0.256269] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.256274] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffffffffffff]
[    0.256350] NET: Registered protocol family 2
[    0.256476] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.256970] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.257814] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.258422] TCP: Hash tables configured (established 131072 bind 65536)
[    0.258428] TCP reno registered
[    0.258436] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.258457] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.258653] NET: Registered protocol family 1
[    0.258824] pci 0000:01:00.0: Boot video device
[    0.258848] PCI: CLS 32 bytes, default 64
[    0.259181] cpufreq-nforce2: No nForce2 chipset.
[    0.259245] Scanning for low memory corruption every 60 seconds
[    0.259444] audit: initializing netlink socket (disabled)
[    0.259462] type=2000 audit(1295449853.252:1): initialized
[    0.273075] highmem bounce pool size: 64 pages
[    0.273087] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.275944] VFS: Disk quotas dquot_6.5.2
[    0.276073] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.277325] fuse init (API version 7.14)
[    0.277521] msgmni has been set to 1716
[    0.278207] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.278214] io scheduler noop registered
[    0.278217] io scheduler deadline registered
[    0.278247] io scheduler cfq registered (default)
[    0.278489] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.278540] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.278897] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.278915] ACPI: Power Button [PWRB]
[    0.279018] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.279030] ACPI: Sleep Button [SLPB]
[    0.279118] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.279126] ACPI: Power Button [PWRF]
[    0.279372] ACPI: acpi_idle registered with cpuidle
[    0.283591] ERST: Table is not found!
[    0.283971] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.284099] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.284619] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.284845]   alloc irq_desc for 19 on node -1
[    0.284850]   alloc kstat_irqs on node -1
[    0.284862] serial 0000:02:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.288044] brd: module loaded
[    0.289177] loop: module loaded
[    0.289617] ata_piix 0000:00:1f.1: version 2.13
[    0.289634] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.289646]   alloc irq_desc for 18 on node -1
[    0.289650]   alloc kstat_irqs on node -1
[    0.289663] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.289732] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.289903] scsi0 : ata_piix
[    0.290055] scsi1 : ata_piix
[    0.291902] isapnp: Scanning for PnP cards...
[    0.293260] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.293266] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.293901] Fixed MDIO Bus: probed
[    0.293965] PPP generic driver version 2.4.2
[    0.294047] tun: Universal TUN/TAP device driver, 1.6
[    0.294050] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.294220] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.294255]   alloc irq_desc for 23 on node -1
[    0.294259]   alloc kstat_irqs on node -1
[    0.294269] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.294295] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.294301] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.294359] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.294399] ehci_hcd 0000:00:1d.7: debug port 1
[    0.298281] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.298338] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00
[    0.312074] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.312311] hub 1-0:1.0: USB hub found
[    0.312320] hub 1-0:1.0: 8 ports detected
[    0.312466] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.312495] uhci_hcd: USB Universal Host Controller Interface driver
[    0.312560]   alloc irq_desc for 16 on node -1
[    0.312564]   alloc kstat_irqs on node -1
[    0.312575] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.312588] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.312593] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.312655] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.312699] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[    0.312904] hub 2-0:1.0: USB hub found
[    0.312912] hub 2-0:1.0: 2 ports detected
[    0.313006] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.313015] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.313021] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.313081] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.313118] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    0.313315] hub 3-0:1.0: USB hub found
[    0.313322] hub 3-0:1.0: 2 ports detected
[    0.313417] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.313426] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.313431] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.313488] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.313527] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    0.313736] hub 4-0:1.0: USB hub found
[    0.313745] hub 4-0:1.0: 2 ports detected
[    0.313839] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.313848] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.313853] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.313909] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.313934] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[    0.314136] hub 5-0:1.0: USB hub found
[    0.314143] hub 5-0:1.0: 2 ports detected
[    0.314345] PNP: No PS/2 controller found. Probing ports directly.
[    0.317526] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.317537] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.317726] mice: PS/2 mouse device common for all mice
[    0.317961] rtc_cmos 00:02: RTC can wake from S4
[    0.318039] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.318067] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.318267] device-mapper: uevent: version 1.0.3
[    0.340363] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.408151] device-mapper: multipath: version 1.1.1 loaded
[    0.408158] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.428768] EISA: Probing bus 0 at eisa.0
[    0.428817] EISA: Detected 0 cards.
[    0.448326] cpuidle: using governor ladder
[    0.448330] cpuidle: using governor menu
[    0.448942] TCP cubic registered
[    0.449206] NET: Registered protocol family 10
[    0.449872] lo: Disabled Privacy Extensions
[    0.450342] NET: Registered protocol family 17
[    0.450430] Using IPI No-Shortcut mode
[    0.450601] PM: Resume from disk failed.
[    0.450621] registered taskstats version 1
[    0.450874]   Magic number: 11:602:184
[    0.450934] acpi LNXTHERM:00: hash matches
[    0.450979] rtc_cmos 00:02: setting system clock to 2011-01-19 15:10:53 UTC (1295449853)
[    0.450984] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.450988] EDD information not available.
[    0.464587] ata2.00: ATAPI: DVDRW DRW-3S163, BSG2, max UDMA/66
[    0.464627] ata2.00: limited to UDMA/33 due to 40-wire cable
[    0.465795] ata1.00: ATA-6: WDC WD1600JB-22GVA0, 08.02D08, max UDMA/100
[    0.465801] ata1.00: 312581808 sectors, multi 16: LBA48 
[    0.480422] ata2.00: configured for UDMA/33
[    0.515461] ata1.00: configured for UDMA/100
[    0.591580] Freeing initrd memory: 10488k freed
[    0.623972] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.646006] isapnp: No Plug & Play device found
[    0.646222] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JB-22G 08.0 PQ: 0 ANSI: 5
[    0.646422] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.646516] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.646522] sd 0:0:0:0: [sda] Write Protect is off
[    0.646529] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.646574] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.646939]  sda:
[    0.647495] scsi 1:0:0:0: CD-ROM            DVDRW    DRW-3S163        BSG2 PQ: 0 ANSI: 5
[    0.651517] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    0.651522] Uniform CD-ROM driver Revision: 3.20
[    0.651660] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.651735] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.657714]  sda1 sda2 < sda5 >
[    0.678947] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.678971] Freeing unused kernel memory: 704k freed
[    0.679708] Write protecting the kernel text: 5092k
[    0.679814] Write protecting the kernel read-only data: 2016k
[    0.707435] udev[79]: starting version 163
[    0.948560] Initializing USB Mass Storage driver...
[    0.948740] scsi2 : usb-storage 1-1:1.0
[    0.948980] usbcore: registered new interface driver usb-storage
[    0.948984] USB Mass Storage support registered.
[    0.949641] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.949679] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.954642] Floppy drive(s): fd0 is 1.44M
[    0.956411] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.956476]   alloc irq_desc for 22 on node -1
[    0.956480]   alloc kstat_irqs on node -1
[    0.956492] 8139too 0000:02:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.957648] 8139too 0000:02:05.0: eth0: RealTek RTL8139 at 0xb400, 00:50:2c:a4:98:7a, IRQ 22
[    0.971946] FDC 0 is a post-1991 82077
[    1.135827] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    1.152425] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.552023] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.950094] scsi 2:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[    1.950757] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.951324] sd 2:0:0:0: [sdb] 3907024896 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.952195] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    1.952200] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    1.953819] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[    1.953823] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    1.953830]  sdb:
[   11.830411] udev[299]: starting version 163
[   11.901883] Adding 6384636k swap on /dev/sda5.  Priority:-1 extents:1 across:6384636k 
[   11.961121] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.087532] Linux agpgart interface v0.103
[   12.190246] intel_rng: FWH not detected
[   12.284880] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.351179] usbcore: registered new interface driver hiddev
[   12.367669] input: LiteON HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
[   12.368076] generic-usb 0003:03F0:0324.0001: input,hidraw0: USB HID v1.00 Keyboard [LiteON HP Basic USB Keyboard] on usb-0000:00:1d.0-2/input0
[   12.382603] input: Microsoft Microsoft Wireless Optical Desktop¬Æ 1.00 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
[   12.382820] generic-usb 0003:045E:008A.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop¬Æ 1.00] on usb-0000:00:1d.1-1/input0
[   12.466541] type=1400 audit(1295471465.509:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=523 comm="apparmor_parser"
[   12.467358] type=1400 audit(1295471465.509:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=523 comm="apparmor_parser"
[   12.467819] type=1400 audit(1295471465.509:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=523 comm="apparmor_parser"
[   12.470720] type=1400 audit(1295471465.513:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=518 comm="apparmor_parser"
[   12.471634] type=1400 audit(1295471465.513:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=518 comm="apparmor_parser"
[   12.472129] type=1400 audit(1295471465.517:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=518 comm="apparmor_parser"
[   12.494465] input: Microsoft Microsoft Wireless Optical Desktop¬Æ 1.00 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input5
[   12.494710] generic-usb 0003:045E:008A.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop¬Æ 1.00] on usb-0000:00:1d.1-1/input1
[   12.494749] usbcore: registered new interface driver usbhid
[   12.494754] usbhid: USB HID core driver
[   18.320654]  sdb1
[   18.323270] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   18.323278] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   18.323324] sd 2:0:0:0: [sdb] Attached SCSI disk
[   18.356353] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   18.359441] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.361118] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   18.376246] lp: driver loaded but no devices found
[   18.423656] Linux video capture interface: v2.00
[   18.457958] nf_conntrack version 0.5.0 (16008 buckets, 64032 max)
[   18.458298] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   18.458303] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   18.458307] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   18.506132] [drm] Initialized drm 1.1.0 20060810
[   18.511408] IR NEC protocol handler initialized
[   18.547595] IR RC5(x) protocol handler initialized
[   18.564975] IR RC6 protocol handler initialized
[   18.577596] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
[   18.577666]   alloc irq_desc for 20 on node -1
[   18.577671]   alloc kstat_irqs on node -1
[   18.577684] cx8800 0000:02:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.594511] cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected], frontend(s): 0
[   18.594519] cx88[0]: TV tuner type 44, Radio tuner type -1
[   18.603174] IR JVC protocol handler initialized
[   18.608715] IR Sony protocol handler initialized
[   18.634852] lirc_dev: IR Remote Control driver registered, major 250 
[   18.642809] IR LIRC bridge handler initialized
[   18.665267] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   18.721078] [drm] radeon defaulting to kernel modesetting.
[   18.721086] [drm] radeon kernel modesetting enabled.
[   18.721191] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.724767] [drm] initializing kernel modesetting (RV350 0x1002:0x4152).
[   18.724963] [drm] register mmio base: 0xFC9F0000
[   18.724968] [drm] register mmio size: 65536
[   18.727511] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   18.727536] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   18.727580] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[   18.727621] radeon 0000:01:00.0: GTT: 64M 0xF8000000 - 0xFBFFFFFF
[   18.727627] [drm] Generation 2 PCI interface, using max accessible memory
[   18.727634] radeon 0000:01:00.0: VRAM: 128M 0xE8000000 - 0xEFFFFFFF (128M used)
[   18.727677] [drm] radeon: irq initialized.
[   18.728622] [drm] Detected VRAM RAM=128M, BAR=128M
[   18.728628] [drm] RAM width 128bits DDR
[   18.737105] [TTM] Zone  kernel: Available graphics memory: 445076 kiB.
[   18.737111] [TTM] Zone highmem: Available graphics memory: 512280 kiB.
[   18.737115] [TTM] Initializing pool allocator.
[   18.737148] [drm] radeon: 128M of VRAM memory ready
[   18.737153] [drm] radeon: 64M of GTT memory ready.
[   18.737200] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   18.737281] [drm] Loading R300 Microcode
[   18.749635] [drm] radeon: ring at 0x00000000F8000000
[   18.749658] [drm] ring test succeeded in 0 usecs
[   18.750239] [drm] radeon: ib pool ready.
[   18.750366] [drm] ib test succeeded in 0 usecs
[   18.750542] [drm] Default TV standard: NTSC
[   18.750546] [drm] 27.000000000 MHz TV ref clk
[   18.750552] [drm] DFP table revision: 4
[   18.750650] [drm] Default TV standard: NTSC
[   18.750654] [drm] 27.000000000 MHz TV ref clk
[   18.750710] [drm] Radeon Display Connectors
[   18.750714] [drm] Connector 0:
[   18.750717] [drm]   VGA
[   18.750721] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   18.750725] [drm]   Encoders:
[   18.750728] [drm]     CRT1: INTERNAL_DAC1
[   18.750731] [drm] Connector 1:
[   18.750734] [drm]   DVI-I
[   18.750737] [drm]   HPD1
[   18.750742] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   18.750745] [drm]   Encoders:
[   18.750748] [drm]     CRT2: INTERNAL_DAC2
[   18.750751] [drm]     DFP1: INTERNAL_TMDS1
[   18.750755] [drm] Connector 2:
[   18.750758] [drm]   S-video
[   18.750760] [drm]   Encoders:
[   18.750763] [drm]     TV1: INTERNAL_DAC2
[   18.782260] All bytes are equal. It is not a TEA5767
[   18.782529] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[   18.803980] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   18.815052] tda9887 0-0043: creating new instance
[   18.815059] tda9887 0-0043: tda988[5/6/7] found
[   18.876101] tuner-simple 0-0060: creating new instance
[   18.876109] tuner-simple 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   18.880750] cx88[0]/0: found at 0000:02:02.0, rev: 5, irq: 20, latency: 32, mmio: 0xfd000000
[   18.881082] cx88[0]/0: registered device video0 [v4l2]
[   18.881232] cx88[0]/0: registered device vbi0
[   18.882226]   alloc irq_desc for 21 on node -1
[   18.882231]   alloc kstat_irqs on node -1
[   18.882243] C-Media PCI 0000:02:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.098251] [drm] fb mappable at 0xE8040000
[   19.098258] [drm] vram apper at 0xE8000000
[   19.098263] [drm] size 4177920
[   19.098267] [drm] fb depth is 24
[   19.098270] [drm]    pitch is 5440
[   19.172750] Console: switching to colour frame buffer device 170x48
[   19.195505] fb0: radeondrmfb frame buffer device
[   19.195509] drm: registered panic notifier
[   19.195515] Slow work thread pool: Starting up
[   19.195624] Slow work thread pool: Ready
[   19.195638] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[   21.316227] type=1400 audit(1295471474.361:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=959 comm="apparmor_parser"
[   21.317409] type=1400 audit(1295471474.361:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=959 comm="apparmor_parser"
[   21.353136] type=1400 audit(1295471474.397:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=981 comm="apparmor_parser"
[   21.354044] type=1400 audit(1295471474.397:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=981 comm="apparmor_parser"
[   21.354501] type=1400 audit(1295471474.397:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=981 comm="apparmor_parser"
[   21.389268] type=1400 audit(1295471474.433:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=987 comm="apparmor_parser"
[   21.390329] type=1400 audit(1295471474.433:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=987 comm="apparmor_parser"
[   21.406258] type=1400 audit(1295471474.449:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=991 comm="apparmor_parser"
[   21.410192] type=1400 audit(1295471474.453:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=983 comm="apparmor_parser"
[   21.416594] ppdev: user-space parallel port driver
[   21.442804] type=1400 audit(1295471474.485:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=983 comm="apparmor_parser"
[   21.456860] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   21.976435] RPC: Registered udp transport module.
[   21.976441] RPC: Registered tcp transport module.
[   21.976445] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   22.031955] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   22.094344] svc: failed to register lockdv1 RPC service (errno 97).
[   22.096011] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.104188] NFSD: starting 90-second grace period
[   23.509288] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   24.436559] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.489012] eth0: no IPv6 routers present
[   88.852213] show_signal_msg: 3 callbacks suppressed
[   88.852221] xbmc.bin[1447]: segfault at 4d0 ip 03663516 sp bfb3de60 error 4 in libX11.so.6.3.0[362c000+119000]
[  153.737732] eth0: link down
[  155.417777] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  591.770197] eth0: link down
[  593.456736] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1027.552540] eth0: link down
[ 1029.293704] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1529.722975] eth0: link down
[ 1531.400127] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2029.642947] eth0: link down
[ 2031.304560] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2404.662182] eth0: link down
[ 2406.324624] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 2657.031133] eth0: link down
[ 2658.714750] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3003.163942] [drm:output_poll_execute] *ERROR* delayed enqueue failed -125
[ 3034.155674] [drm:output_poll_execute] *ERROR* delayed enqueue failed -125
[ 3034.270793] [drm:output_poll_execute] *ERROR* delayed enqueue failed -125
[ 3088.312147] eth0: link down
[ 3089.990476] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3102.299809] [drm:output_poll_execute] *ERROR* delayed enqueue failed -125
[ 3252.913871] eth0: link down
[ 3254.615648] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 3530.038148] eth0: link down
[ 3531.699783] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

```lspci -vv:
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: [e4] Vendor Specific Information: Len=06 <?>
    Capabilities: [a0] AGP version 3.0
        Status: RQ=32 Iso- ArqSz=2 Cal=2 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
        Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fc900000-fc9fffff
    Prefetchable memory behind bridge: d7f00000-f7efffff
    Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at e000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at e400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at e800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at ec00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 23
    Region 0: Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fca00000-feafffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR+
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Elitegroup Computer Systems Device 0012
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at fc00 [size=16]
    Region 5: Memory at 40000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600] (prog-if 00 [VGA controller])
    Subsystem: ATI Technologies Inc Radeon 9600XT
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at a800 [size=256]
    Region 2: Memory at fc9f0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at fc9c0000 [disabled] [size=128K]
    Capabilities: [58] AGP version 3.0
        Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
        Command: RQ=32 ArqSz=2 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x8
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
    Subsystem: ATI Technologies Inc Radeon 9600XT (Secondary)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at fc9e0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-

02:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
    Subsystem: ATI Technologies Inc ATI TV Wonder Pro
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: [44] Vital Product Data
        No end tag found
    Capabilities: [4c] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: cx8800
    Kernel modules: cx8800

02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
    Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (500ns min, 6000ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at b800 [size=256]
    Capabilities: [c0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: C-Media PCI
    Kernel modules: snd-cmipci

02:04.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 04 [Hayes/16750])
    Subsystem: PCTel Inc HSP MicroModem 56
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at bc00 [size=64]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=55mA PME(D0+,D1-,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: serial

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (8000ns min, 16000ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at b400 [size=256]
    Region 1: Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp


```aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-SWIEC [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-SWIEC [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-SWIEC [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Thanks for any help!! I've been looking around for a while trying to fix this and all I could find was a post from 2006 ( [http://ubuntuforums.org/showthread.php?t=134903](http://ubuntuforums.org/showthread.php?t=134903) ) that didn't resolve the issue.

Again, Thanks for the help.

---

