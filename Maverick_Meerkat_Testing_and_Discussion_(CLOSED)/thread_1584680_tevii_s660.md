---
title: "tevii s660"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by SOME1 on 2010-09-29
Hi, 
I am testing ubuntu 10.10 for a week and so far it's working really well (better from 10.04 on my pc). 

I have [tevii s660 DVB-S2 box]("http://www.tevii.com/Products_S660_1.asp"). the manufactor driver is based on [video 4 linux (v4l)]("http://www.linuxtv.org/repo/") project. It worked well on ubuntu 10.04 but it's not working on ubuntu 10.10. From what I have read it's look like the kernel 2.6.35 is the problem. 

I contact the manufacor support and they send me a [new beta drivers]("http://www.tevii.com/s2-liplianin_tevii_20100820.tgz") but it's looks like those drivers doesn't work with this kernel too. 
I tried to compile the last cvs version from v4l but the s660 is not working yet. 

Is there something I can do except waiting for the manufactor new drivers or downgrade back to 10.04? 

thank you.

---

### Post by JustRon on 2010-09-29
Could you post the output of the following command which shows why the DVB device doesn't work:

```
dmesg | grep dvb
```

---

### Post by SOME1 on 2010-09-29
the command you asked does not return anything. 

if I ran dmesg alone, this is the output: 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee5000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fee5000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  modified: 000000007fed0000 - 000000007fee5000 (ACPI data)
[    0.000000]  modified: 000000007fee5000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  modified: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375ac000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a5000 - 013e8182
[    0.000000] Move RAMDISK from 00000000375ac000 - 0000000037fef181 to 009a5000 - 013e8181
[    0.000000] ACPI: RSDP 000f6c00 00024 (v02 IBM   )
[    0.000000] ACPI: XSDT 7fed6fe7 0005C (v01 IBM    TP-1Y    00001290  LTP 00000000)
[    0.000000] ACPI: FACP 7fed7100 000F4 (v03 IBM    TP-1Y    00001290 IBM  00000001)
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20100428/tbfadt-526)
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 0x000000000000102C/0x0 (20100428/tbfadt-557)
[    0.000000] ACPI: DSDT 7fed72e7 0DB15 (v01 IBM    TP-1Y    00001290 MSFT 0100000E)
[    0.000000] ACPI: FACS 7fef6000 00040
[    0.000000] ACPI: SSDT 7fed72b4 00033 (v01 IBM    TP-1Y    00001290 MSFT 0100000E)
[    0.000000] ACPI: ECDT 7fee4dfc 00052 (v01 IBM    TP-1Y    00001290 IBM  00000001)
[    0.000000] ACPI: TCPA 7fee4e4e 00032 (v01 IBM    TP-1Y    00001290 PTL  00000001)
[    0.000000] ACPI: APIC 7fee4e80 0005A (v01 IBM    TP-1Y    00001290 IBM  00000001)
[    0.000000] ACPI: MCFG 7fee4eda 0003C (v01 IBM    TP-1Y    00001290 IBM  00000001)
[    0.000000] ACPI: BOOT 7fee4fd8 00028 (v01 IBM    TP-1Y    00001290  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523872
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c13ea020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294340 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519778
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=f220d3bf-de8f-4011-88a2-8a1e6b909a7c ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479660 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (49 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [000009f000 - 0000100000]   BIOS reserved
[    0.000000]   #4 [00009a1000 - 00009a415c]             BRK
[    0.000000]   #5 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #6 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #7 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #8 [00009a5000 - 00013e9000]     NEW RAMDISK
[    0.000000]   #9 [00013e9000 - 00013ea000]         BOOTMEM
[    0.000000]   #10 [00013ea000 - 00023ea000]         BOOTMEM
[    0.000000]   #11 [00023ea000 - 00023ea004]         BOOTMEM
[    0.000000]   #12 [00023ea040 - 00023ea100]         BOOTMEM
[    0.000000]   #13 [00023ea100 - 00023ea154]         BOOTMEM
[    0.000000]   #14 [00023ea180 - 00023ed180]         BOOTMEM
[    0.000000]   #15 [00023ed180 - 00023ed1f0]         BOOTMEM
[    0.000000]   #16 [00023ed200 - 00023f3200]         BOOTMEM
[    0.000000]   #17 [00023f3200 - 00023f3227]         BOOTMEM
[    0.000000]   #18 [00023f3240 - 00023f3438]         BOOTMEM
[    0.000000]   #19 [00023f3440 - 00023f3480]         BOOTMEM
[    0.000000]   #20 [00023f3480 - 00023f34c0]         BOOTMEM
[    0.000000]   #21 [00023f34c0 - 00023f3500]         BOOTMEM
[    0.000000]   #22 [00023f3500 - 00023f3540]         BOOTMEM
[    0.000000]   #23 [00023f3540 - 00023f3580]         BOOTMEM
[    0.000000]   #24 [00023f3580 - 00023f35c0]         BOOTMEM
[    0.000000]   #25 [00023f35c0 - 00023f3600]         BOOTMEM
[    0.000000]   #26 [00023f3600 - 00023f3640]         BOOTMEM
[    0.000000]   #27 [00023f3640 - 00023f3680]         BOOTMEM
[    0.000000]   #28 [00023f3680 - 00023f36c0]         BOOTMEM
[    0.000000]   #29 [00023f36c0 - 00023f3700]         BOOTMEM
[    0.000000]   #30 [00023f3700 - 00023f3740]         BOOTMEM
[    0.000000]   #31 [00023f3740 - 00023f3780]         BOOTMEM
[    0.000000]   #32 [00023f3780 - 00023f37c0]         BOOTMEM
[    0.000000]   #33 [00023f37c0 - 00023f3800]         BOOTMEM
[    0.000000]   #34 [00023f3800 - 00023f3810]         BOOTMEM
[    0.000000]   #35 [00023f3840 - 00023f3850]         BOOTMEM
[    0.000000]   #36 [00023f3880 - 00023f38ea]         BOOTMEM
[    0.000000]   #37 [00023f3900 - 00023f396a]         BOOTMEM
[    0.000000]   #38 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #39 [00023f5980 - 00023f5984]         BOOTMEM
[    0.000000]   #40 [00023f59c0 - 00023f59c4]         BOOTMEM
[    0.000000]   #41 [00023f5a00 - 00023f5a04]         BOOTMEM
[    0.000000]   #42 [00023f5a40 - 00023f5a44]         BOOTMEM
[    0.000000]   #43 [00023f5a80 - 00023f5b30]         BOOTMEM
[    0.000000]   #44 [00023f5b40 - 00023f5be8]         BOOTMEM
[    0.000000]   #45 [00023f5c00 - 00023f9c00]         BOOTMEM
[    0.000000]   #46 [000240e000 - 000248e000]         BOOTMEM
[    0.000000]   #47 [000248e000 - 00024ce000]         BOOTMEM
[    0.000000]   #48 [00024ce000 - 0002ecc82c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fed0)
[    0.000000] Memory: 2048588k/2095936k available (4928k kernel code, 46900k reserved, 2336k data, 684k init, 1186632k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1861.914 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3723.82 BogoMIPS (lpj=7447656)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004042] Security Framework initialized
[    0.004070] AppArmor: AppArmor initialized
[    0.004073] Yama: becoming mindful.
[    0.004144] Mount-cache hash table entries: 512
[    0.004308] Initializing cgroup subsys ns
[    0.004314] Initializing cgroup subsys cpuacct
[    0.004319] Initializing cgroup subsys memory
[    0.004331] Initializing cgroup subsys devices
[    0.004334] Initializing cgroup subsys freezer
[    0.004337] Initializing cgroup subsys net_cls
[    0.004376] mce: CPU supports 5 MCE banks
[    0.004387] CPU0: Thermal monitoring enabled (TM2)
[    0.004400] Performance Events: p6 PMU driver.
[    0.004409] ... version:                0
[    0.004411] ... bit width:              32
[    0.004414] ... generic registers:      2
[    0.004416] ... value mask:             00000000ffffffff
[    0.004419] ... max period:             000000007fffffff
[    0.004421] ... fixed-purpose events:   0
[    0.004423] ... event mask:             0000000000000003
[    0.005428] SMP alternatives: switching to UP code
[    0.013787] Freeing SMP alternatives: 24k freed
[    0.013798] ACPI: Core revision 20100428
[    0.032009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032015] ftrace: allocating 21758 entries in 43 pages
[    0.036070] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036443] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076886] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    0.080000] Brought up 1 CPUs
[    0.080000] Total of 1 processors activated (3723.82 BogoMIPS).
[    0.080000] devtmpfs: initialized
[    0.080000] regulator: core version 0.5
[    0.080000] Time:  0:30:44  Date: 09/30/10
[    0.080000] NET: Registered protocol family 16
[    0.080000] EISA bus registered
[    0.080000] ACPI: bus type pci registered
[    0.080000] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.080000] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.080000] PCI: Using MMCONFIG for extended config space
[    0.080000] PCI: Using configuration type 1 for base access
[    0.080000] bio: create slab <bio-0> at 0
[    0.081302] ACPI: EC: EC description table is found, configuring boot EC
[    0.097296] ACPI: Interpreter enabled
[    0.097300] ACPI: (supports S0 S3 S4 S5)
[    0.097326] ACPI: Using IOAPIC for interrupt routing
[    0.105356] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.105409] ACPI: Power Resource [PUBS] (on)
[    0.109264] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.109269] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.109295] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.109357] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.109361] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.109364] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.109368] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.109371] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.109375] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
[    0.109452] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.109456] pci 0000:00:01.0: PME# disabled
[    0.109575] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.109580] pci 0000:00:1c.0: PME# disabled
[    0.109675] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.109680] pci 0000:00:1c.2: PME# disabled
[    0.109742] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
[    0.109803] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
[    0.109863] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
[    0.109923] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
[    0.109979] pci 0000:00:1d.7: reg 10: [mem 0xb0000000-0xb00003ff]
[    0.110039] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.110045] pci 0000:00:1d.7: PME# disabled
[    0.110143] pci 0000:00:1e.2: reg 10: [io  0x1c00-0x1cff]
[    0.110151] pci 0000:00:1e.2: reg 14: [io  0x1880-0x18bf]
[    0.110159] pci 0000:00:1e.2: reg 18: [mem 0xb0000800-0xb00009ff]
[    0.110167] pci 0000:00:1e.2: reg 1c: [mem 0xb0000400-0xb00004ff]
[    0.110204] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.110209] pci 0000:00:1e.2: PME# disabled
[    0.110242] pci 0000:00:1e.3: reg 10: [io  0x2400-0x24ff]
[    0.110250] pci 0000:00:1e.3: reg 14: [io  0x2000-0x207f]
[    0.110297] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.110302] pci 0000:00:1e.3: PME# disabled
[    0.110390] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.110397] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.110402] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.110407] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 1600-167f
[    0.110412] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 15e0-15ef
[    0.110448] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.110456] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.110464] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.110472] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.110480] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.110513] pci 0000:00:1f.2: PME# supported from D3hot
[    0.110518] pci 0000:00:1f.2: PME# disabled
[    0.110576] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
[    0.110652] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xc7ffffff pref]
[    0.110658] pci 0000:01:00.0: reg 14: [io  0x3000-0x30ff]
[    0.110664] pci 0000:01:00.0: reg 18: [mem 0xb0100000-0xb010ffff]
[    0.110680] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.110698] pci 0000:01:00.0: supports D1 D2
[    0.110709] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.110718] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.110722] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.110726] pci 0000:00:01.0:   bridge window [mem 0xb0100000-0xb01fffff]
[    0.110730] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc7ffffff pref]
[    0.110835] pci 0000:02:00.0: reg 10: [mem 0xb0200000-0xb020ffff 64bit]
[    0.110927] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.110933] pci 0000:02:00.0: PME# disabled
[    0.110954] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.110966] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.110972] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.110978] pci 0000:00:1c.0:   bridge window [mem 0xb0200000-0xb02fffff]
[    0.110986] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.111043] pci 0000:00:1c.2: PCI bridge to [bus 03-0a]
[    0.111048] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.111053] pci 0000:00:1c.2:   bridge window [mem 0xb2000000-0xb3ffffff]
[    0.111062] pci 0000:00:1c.2:   bridge window [mem 0xc8000000-0xc80fffff 64bit pref]
[    0.111128] pci 0000:0b:00.0: reg 10: [mem 0xb4000000-0xb4000fff]
[    0.111156] pci 0000:0b:00.0: supports D1 D2
[    0.111158] pci 0000:0b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.111164] pci 0000:0b:00.0: PME# disabled
[    0.111222] pci 0000:0b:02.0: reg 10: [mem 0xb4001000-0xb4001fff]
[    0.111296] pci 0000:0b:02.0: PME# supported from D0 D3hot D3cold
[    0.111302] pci 0000:0b:02.0: PME# disabled
[    0.111366] pci 0000:00:1e.0: PCI bridge to [bus 0b-0e] (subtractive decode)
[    0.111372] pci 0000:00:1e.0:   bridge window [io  0x5000-0x8fff]
[    0.111377] pci 0000:00:1e.0:   bridge window [mem 0xb4000000-0xbfffffff]
[    0.111385] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.111388] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.111392] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.111465] pci_bus 0000:00: on NUMA node 0
[    0.111470] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.112086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.112163] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.112246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.112336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.117489] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.117696] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.117902] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.118107] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.118311] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.118519] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.118724] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.118928] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.119005] HEST: Table is not found!
[    0.119084] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.119088] vgaarb: loaded
[    0.119266] SCSI subsystem initialized
[    0.119312] libata version 3.00 loaded.
[    0.119369] usbcore: registered new interface driver usbfs
[    0.119383] usbcore: registered new interface driver hub
[    0.119412] usbcore: registered new device driver usb
[    0.119545] ACPI: WMI: Mapper loaded
[    0.119547] PCI: Using ACPI for IRQ routing
[    0.119550] PCI: pci_cache_line_size set to 64 bytes
[    0.119630] Expanded resource reserved due to conflict with Adapter ROM
[    0.119634] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.119637] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.119640] reserve RAM buffer: 000000007fed0000 - 000000007fffffff 
[    0.119740] NetLabel: Initializing
[    0.119742] NetLabel:  domain hash size = 128
[    0.119744] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.119759] NetLabel:  unlabeled traffic allowed by default
[    0.119916] hpet clockevent registered
[    0.119921] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.119928] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.119934] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.124019] Switching to clocksource tsc
[    0.135826] AppArmor: AppArmor Filesystem Enabled
[    0.135854] pnp: PnP ACPI init
[    0.135881] ACPI: bus type pnp registered
[    0.139723] pnp: PnP ACPI: found 14 devices
[    0.139726] ACPI: ACPI bus type pnp unregistered
[    0.139731] PnPBIOS: Disabled by ACPI PNP
[    0.139747] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.139751] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.139755] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.139758] system 00:00: [mem 0x000c8000-0x000cbfff] could not be reserved
[    0.139761] system 00:00: [mem 0x000cc000-0x000cffff] could not be reserved
[    0.139765] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.139769] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
[    0.139772] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.139775] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.139779] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.139782] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.139786] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.139790] system 00:00: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.139793] system 00:00: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.139802] system 00:02: [io  0x1000-0x107f] has been reserved
[    0.139805] system 00:02: [io  0x1180-0x11bf] has been reserved
[    0.139808] system 00:02: [io  0x15e0-0x15ef] has been reserved
[    0.139811] system 00:02: [io  0x1600-0x1641] has been reserved
[    0.139815] system 00:02: [io  0x1644-0x167f] has been reserved
[    0.139818] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved
[    0.139822] system 00:02: [mem 0xf0008000-0xf000bfff] has been reserved
[    0.139825] system 00:02: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.139829] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.139832] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.176085] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.176090] pci 0000:00:1c.0: BAR 13: assigned [io  0x9000-0x9fff]
[    0.176094] pci 0000:01:00.0: BAR 6: assigned [mem 0xb0120000-0xb013ffff pref]
[    0.176098] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.176102] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.176107] pci 0000:00:01.0:   bridge window [mem 0xb0100000-0xb01fffff]
[    0.176111] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc7ffffff pref]
[    0.176116] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.176120] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
[    0.176127] pci 0000:00:1c.0:   bridge window [mem 0xb0200000-0xb02fffff]
[    0.176132] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.176141] pci 0000:00:1c.2: PCI bridge to [bus 03-0a]
[    0.176145] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.176152] pci 0000:00:1c.2:   bridge window [mem 0xb2000000-0xb3ffffff]
[    0.176157] pci 0000:00:1c.2:   bridge window [mem 0xc8000000-0xc80fffff 64bit pref]
[    0.176167] pci 0000:0b:00.0: BAR 15: assigned [mem 0xd0000000-0xd3ffffff pref]
[    0.176171] pci 0000:0b:00.0: BAR 16: assigned [mem 0xb8000000-0xbbffffff]
[    0.176174] pci 0000:0b:00.0: BAR 13: assigned [io  0x5000-0x50ff]
[    0.176177] pci 0000:0b:00.0: BAR 14: assigned [io  0x5400-0x54ff]
[    0.176180] pci 0000:0b:00.0: CardBus bridge to [bus 0c-0d]
[    0.176183] pci 0000:0b:00.0:   bridge window [io  0x5000-0x50ff]
[    0.176189] pci 0000:0b:00.0:   bridge window [io  0x5400-0x54ff]
[    0.176196] pci 0000:0b:00.0:   bridge window [mem 0xd0000000-0xd3ffffff pref]
[    0.176202] pci 0000:0b:00.0:   bridge window [mem 0xb8000000-0xbbffffff]
[    0.176208] pci 0000:00:1e.0: PCI bridge to [bus 0b-0e]
[    0.176212] pci 0000:00:1e.0:   bridge window [io  0x5000-0x8fff]
[    0.176219] pci 0000:00:1e.0:   bridge window [mem 0xb4000000-0xbfffffff]
[    0.176225] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.176242]   alloc irq_desc for 16 on node -1
[    0.176245]   alloc kstat_irqs on node -1
[    0.176252] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.176257] pci 0000:00:01.0: setting latency timer to 64
[    0.176267]   alloc irq_desc for 20 on node -1
[    0.176269]   alloc kstat_irqs on node -1
[    0.176273] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.176278] pci 0000:00:1c.0: setting latency timer to 64
[    0.176289]   alloc irq_desc for 22 on node -1
[    0.176291]   alloc kstat_irqs on node -1
[    0.176295] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.176300] pci 0000:00:1c.2: setting latency timer to 64
[    0.176309] pci 0000:00:1e.0: setting latency timer to 64
[    0.176322] pci 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.176330] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.176333] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.176336] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.176339] pci_bus 0000:01: resource 1 [mem 0xb0100000-0xb01fffff]
[    0.176342] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xc7ffffff pref]
[    0.176345] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.176348] pci_bus 0000:02: resource 1 [mem 0xb0200000-0xb02fffff]
[    0.176351] pci_bus 0000:02: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.176354] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.176357] pci_bus 0000:03: resource 1 [mem 0xb2000000-0xb3ffffff]
[    0.176360] pci_bus 0000:03: resource 2 [mem 0xc8000000-0xc80fffff 64bit pref]
[    0.176363] pci_bus 0000:0b: resource 0 [io  0x5000-0x8fff]
[    0.176366] pci_bus 0000:0b: resource 1 [mem 0xb4000000-0xbfffffff]
[    0.176369] pci_bus 0000:0b: resource 2 [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.176372] pci_bus 0000:0b: resource 4 [io  0x0000-0xffff]
[    0.176375] pci_bus 0000:0b: resource 5 [mem 0x00000000-0xffffffff]
[    0.176378] pci_bus 0000:0c: resource 0 [io  0x5000-0x50ff]
[    0.176381] pci_bus 0000:0c: resource 1 [io  0x5400-0x54ff]
[    0.176384] pci_bus 0000:0c: resource 2 [mem 0xd0000000-0xd3ffffff pref]
[    0.176387] pci_bus 0000:0c: resource 3 [mem 0xb8000000-0xbbffffff]
[    0.176430] NET: Registered protocol family 2
[    0.176506] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.176785] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.177783] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.178408] TCP: Hash tables configured (established 131072 bind 65536)
[    0.178413] TCP reno registered
[    0.178419] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.178443] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.178588] NET: Registered protocol family 1
[    0.178732] pci 0000:01:00.0: Boot video device
[    0.178748] PCI: CLS 32 bytes, default 64
[    0.178862] Simple Boot Flag at 0x35 set to 0x1
[    0.178991] cpufreq-nforce2: No nForce2 chipset.
[    0.179029] Scanning for low memory corruption every 60 seconds
[    0.179234] audit: initializing netlink socket (disabled)
[    0.179250] type=2000 audit(1285806644.172:1): initialized
[    0.191607] Trying to unpack rootfs image as initramfs...
[    0.208324] highmem bounce pool size: 64 pages
[    0.208332] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.216142] VFS: Disk quotas dquot_6.5.2
[    0.216231] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.216957] fuse init (API version 7.14)
[    0.217061] msgmni has been set to 1683
[    0.224506] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.224511] io scheduler noop registered
[    0.224514] io scheduler deadline registered
[    0.224532] io scheduler cfq registered (default)
[    0.224664] pcieport 0000:00:01.0: setting latency timer to 64
[    0.224690]   alloc irq_desc for 40 on node -1
[    0.224692]   alloc kstat_irqs on node -1
[    0.224703] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.224769] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.224811]   alloc irq_desc for 41 on node -1
[    0.224813]   alloc kstat_irqs on node -1
[    0.224822] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.224925] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.224967]   alloc irq_desc for 42 on node -1
[    0.224970]   alloc kstat_irqs on node -1
[    0.224978] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.225101] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.225195] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.225928] ACPI: AC Adapter [AC] (on-line)
[    0.226009] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.226602] ACPI: Lid Switch [LID]
[    0.226663] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.226669] ACPI: Sleep Button [SLPB]
[    0.226729] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.226733] ACPI: Power Button [PWRF]
[    0.226971] ACPI: acpi_idle registered with cpuidle
[    0.227489] Marking TSC unstable due to TSC halts in idle
[    0.231958] Switching to clocksource hpet
[    0.233568] thermal LNXTHERM:01: registered as thermal_zone0
[    0.233578] ACPI: Thermal Zone [THM0] (94 C)
[    0.233644] ERST: Table is not found!
[    0.233803] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.234770] serial 00:0a: activated
[    0.234898] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.235024]   alloc irq_desc for 23 on node -1
[    0.235026]   alloc kstat_irqs on node -1
[    0.235033] serial 0000:00:1e.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.235040] serial 0000:00:1e.3: PCI INT B disabled
[    0.236357] brd: module loaded
[    0.236956] loop: module loaded
[    0.237156] ata_piix 0000:00:1f.2: version 2.13
[    0.237172] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.244537] isapnp: Scanning for PnP cards...
[    0.329836] ACPI: Battery Slot [BAT0] (battery present)
[    0.392280] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.396328] scsi0 : ata_piix
[    0.396481] scsi1 : ata_piix
[    0.397573] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
[    0.397577] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
[    0.398005] Fixed MDIO Bus: probed
[    0.398047] PPP generic driver version 2.4.2
[    0.398129] tun: Universal TUN/TAP device driver, 1.6
[    0.398131] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.398232] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.398457] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.398969] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.398981]   alloc irq_desc for 19 on node -1
[    0.398984]   alloc kstat_irqs on node -1
[    0.398993] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.399013] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.399018] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.399059] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.399094] ehci_hcd 0000:00:1d.7: debug port 1
[    0.402988] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.403012] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xb0000000
[    0.428043] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.428254] hub 1-0:1.0: USB hub found
[    0.428261] hub 1-0:1.0: 8 ports detected
[    0.428360] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.428380] uhci_hcd: USB Universal Host Controller Interface driver
[    0.428979] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.429505] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.429518] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.429530] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.429534] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.429598] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.429646] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    0.429784] hub 2-0:1.0: USB hub found
[    0.429790] hub 2-0:1.0: 2 ports detected
[    0.430026] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.430560] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.430569]   alloc irq_desc for 17 on node -1
[    0.430572]   alloc kstat_irqs on node -1
[    0.430579] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.430587] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.430591] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.430634] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.430673] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
[    0.430803] hub 3-0:1.0: USB hub found
[    0.430807] hub 3-0:1.0: 2 ports detected
[    0.430865]   alloc irq_desc for 18 on node -1
[    0.430867]   alloc kstat_irqs on node -1
[    0.430873] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.430879] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.430883] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.430917] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.430955] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    0.431091] hub 4-0:1.0: USB hub found
[    0.431095] hub 4-0:1.0: 2 ports detected
[    0.431154] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.431161] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.431165] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.431205] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.431232] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
[    0.431354] hub 5-0:1.0: USB hub found
[    0.431358] hub 5-0:1.0: 2 ports detected
[    0.431501] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.435447] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.435454] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.440335] mice: PS/2 mouse device common for all mice
[    0.440511] rtc_cmos 00:06: RTC can wake from S4
[    0.440558] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.440592] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.440737] device-mapper: uevent: version 1.0.3
[    0.440870] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.446046] device-mapper: multipath: version 1.1.1 loaded
[    0.446050] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.492382] EISA: Probing bus 0 at eisa.0
[    0.492391] Cannot allocate resource for EISA slot 1
[    0.492394] Cannot allocate resource for EISA slot 2
[    0.492397] Cannot allocate resource for EISA slot 3
[    0.492399] Cannot allocate resource for EISA slot 4
[    0.492402] Cannot allocate resource for EISA slot 5
[    0.492404] Cannot allocate resource for EISA slot 6
[    0.492407] Cannot allocate resource for EISA slot 7
[    0.492409] Cannot allocate resource for EISA slot 8
[    0.492411] EISA: Detected 0 cards.
[    0.496081] cpuidle: using governor ladder
[    0.496143] cpuidle: using governor menu
[    0.496470] TCP cubic registered
[    0.496624] NET: Registered protocol family 10
[    0.497007] lo: Disabled Privacy Extensions
[    0.497236] NET: Registered protocol family 17
[    0.498913] P-state transition latency capped at 20 uS
[    0.499230] Using IPI No-Shortcut mode
[    0.499342] PM: Resume from disk failed.
[    0.499355] registered taskstats version 1
[    0.499627]   Magic number: 10:746:507
[    0.499743] rtc_cmos 00:06: setting system clock to 2010-09-30 00:30:44 UTC (1285806644)
[    0.499746] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.499748] EDD information not available.
[    0.509653] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.589004] ata2.00: ATA-6: IC25N080ATMR04-0, MO4OADEA, max UDMA/100
[    0.589009] ata2.00: 156301488 sectors, multi 16: LBA 
[    0.589106] ata1.00: ATA-6: TOSHIBA MK8032GAX, AB311E, max UDMA/100
[    0.589110] ata1.00: 156301488 sectors, multi 16: LBA48 
[    0.589124] ata1.00: applying bridge limits
[    0.604979] ata1.00: configured for UDMA/100
[    0.605401] ata2.00: configured for UDMA/100
[    0.759645] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.883948] Freeing initrd memory: 10512k freed
[    0.936130] isapnp: No Plug & Play device found
[    0.936388] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8032GA AB31 PQ: 0 ANSI: 5
[    0.936620] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.936790] scsi 1:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[    0.936914] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    0.936991] sd 1:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.937051] sd 1:0:0:0: [sdb] Write Protect is off
[    0.937054] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.937080] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.937234] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.937285]  sdb:
[    0.937427] sd 0:0:0:0: [sda] Write Protect is off
[    0.937430] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.937454] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.937595]  sda:
[    0.956722] hub 1-1:1.0: USB hub found
[    0.956815] hub 1-1:1.0: 4 ports detected
[    0.969752]  sda1 sda2 < sda5 > sda3
[    0.983310] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.228192] usb 1-1.1: new high speed USB device using ehci_hcd and address 3
[    1.286673]  sdb1
[    1.286877] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.286895] Freeing unused kernel memory: 684k freed
[    1.287360] Write protecting the kernel text: 4932k
[    1.287401] Write protecting the kernel read-only data: 1976k
[    1.303483] udev[68]: starting version 163
[    1.321742] hub 1-1.1:1.0: USB hub found
[    1.322057] hub 1-1.1:1.0: 4 ports detected
[    1.505558] Floppy drive(s): fd0 is 1.44M
[    1.520200] usb 1-1.2: new high speed USB device using ehci_hcd and address 4
[    1.550313] tg3.c:v3.110 (April 9, 2010)
[    1.550336] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.550350] tg3 0000:02:00.0: setting latency timer to 64
[    1.559893] FDC 0 is a National Semiconductor PC87306
[    1.601920] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:21:86:61:32:14
[    1.601926] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.601930] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.601934] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.639901] Initializing USB Mass Storage driver...
[    1.640123] scsi2 : usb-storage 1-1.2:1.0
[    1.640266] usbcore: registered new interface driver usb-storage
[    1.640269] USB Mass Storage support registered.
[    1.704190] usb 1-1.3: new high speed USB device using ehci_hcd and address 5
[    1.858158] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    1.894447] scsi3 : usb-storage 1-1.3:1.0
[    1.968187] usb 1-1.4: new high speed USB device using ehci_hcd and address 6
[    2.071522] scsi4 : usb-storage 1-1.4:1.0
[    2.144318] usb 1-1.1.1: new full speed USB device using ehci_hcd and address 7
[    2.236843] hub 1-1.1.1:1.0: USB hub found
[    2.237051] hub 1-1.1.1:1.0: 4 ports detected
[    2.308316] usb 1-1.1.2: new high speed USB device using ehci_hcd and address 8
[    2.642960] scsi 2:0:0:0: Direct-Access     Seagate  FreeAgent        102D PQ: 0 ANSI: 4
[    2.643385] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.910344] scsi 3:0:0:0: Direct-Access     WD       My Book 1112     1009 PQ: 0 ANSI: 4
[    2.923961] scsi 3:0:0:1: Enclosure         WD       SES Device       1009 PQ: 0 ANSI: 4
[    2.924395] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.924511] scsi 3:0:0:1: Attached scsi generic sg4 type 13
[    2.941697] sd 3:0:0:0: [sdd] 3905656832 512-byte logical blocks: (1.99 TB/1.81 TiB)
[    2.953941] sd 3:0:0:0: [sdd] Write Protect is off
[    2.953945] sd 3:0:0:0: [sdd] Mode Sense: 23 00 10 00
[    2.953948] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[    2.982688] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[    2.982694]  sdd: [mac] sdd1 sdd2 sdd3 sdd4
[    3.012694] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[    3.012698] sd 3:0:0:0: [sdd] Attached SCSI disk
[    3.070579] scsi 4:0:0:0: Direct-Access     WD       My Book          1015 PQ: 0 ANSI: 4
[    3.072209] scsi 4:0:0:1: Enclosure         WD       My Book Device   1015 PQ: 0 ANSI: 4
[    3.072606] sd 4:0:0:0: Attached scsi generic sg5 type 0
[    3.072739] scsi 4:0:0:1: Attached scsi generic sg6 type 13
[    3.074058] sd 4:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[    3.074811] sd 4:0:0:0: [sde] 7814025568 512-byte logical blocks: (4.00 TB/3.63 TiB)
[    3.075807] sd 4:0:0:0: [sde] Write Protect is off
[    3.075810] sd 4:0:0:0: [sde] Mode Sense: 10 00 00 00
[    3.075813] sd 4:0:0:0: [sde] Assuming drive cache: write through
[    3.077561] sd 4:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[    3.079310] sd 4:0:0:0: [sde] Assuming drive cache: write through
[    3.079314]  sde: sde1 sde2
[    3.081559] sd 4:0:0:0: [sde] Very big device. Trying to use READ CAPACITY(16).
[    3.083183] sd 4:0:0:0: [sde] Assuming drive cache: write through
[    3.083186] sd 4:0:0:0: [sde] Attached SCSI disk
[    6.871808] sd 2:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    6.873042] sd 2:0:0:0: [sdc] Write Protect is off
[    6.873046] sd 2:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[    6.873049] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.876045] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.876052]  sdc: sdc1
[    6.888289] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    6.888293] sd 2:0:0:0: [sdc] Attached SCSI disk
[   15.252459] udev[351]: starting version 163
[   15.292961] Adding 3905532k swap on /dev/sda5.  Priority:-1 extents:1 across:3905532k 
[   15.353918] lp: driver loaded but no devices found
[   15.530192] intel_rng: FWH not detected
[   15.555958] Non-volatile memory driver v1.3
[   15.558858] lib80211: common routines for IEEE802.11 drivers
[   15.558862] lib80211_crypt: registered algorithm 'NULL'
[   15.715970] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input4
[   15.796478] parport_pc 00:0b: reported by Plug and Play ACPI
[   15.796537] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   15.805985] Linux agpgart interface v0.103
[   15.826604] yenta_cardbus 0000:0b:00.0: CardBus bridge found [1014:056c]
[   15.850939] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   15.861779] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   15.898536] lp0: using parport0 (interrupt-driven).
[   15.988754] yenta_cardbus 0000:0b:00.0: ISA IRQ mask 0x0c38, PCI irq 16
[   15.988759] yenta_cardbus 0000:0b:00.0: Socket status: 30000006
[   15.988768] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge window: [io  0x5000-0x8fff]
[   15.988772] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x8fff: excluding 0x5000-0x50ff 0x5400-0x54ff
[   15.997763] ppdev: user-space parallel port driver
[   16.029902] irda_init()
[   16.029921] NET: Registered protocol family 23
[   16.069596] psmouse serio1: ID: 10 00 64
[   16.087467] ses 3:0:0:1: Attached Enclosure device
[   16.087478] ses 4:0:0:1: Attached Enclosure device
[   16.093729] nsc-ircc 00:0c: activated
[   16.093734] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   16.093818] nsc-ircc, chip->init
[   16.093830] nsc-ircc, Found chip at base=0x02e
[   16.093866] nsc-ircc, driver loaded (Dag Brattli)
[   16.105346] IrDA: Registered device irda0
[   16.105350] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   16.127796] cfg80211: Calling CRDA to update world regulatory domain
[   16.148973] logips2pp: Detected unknown logitech mouse model 62
[   16.149989] usbcore: registered new interface driver hiddev
[   16.165774] libipw: 802.11 data/management/control stack, git-1.1.13
[   16.165778] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.177035] 
[   16.177043] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge window: [mem 0xb4000000-0xbfffffff]
[   16.177049] pcmcia_socket pcmcia_socket0: cs: memory probe 0xb4000000-0xbfffffff: excluding 0xb4000000-0xb47fffff 0xb8000000-0xbbffffff
[   16.177069] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge window: [mem 0xd0000000-0xd7ffffff 64bit pref]
[   16.177073] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0000000-0xd7ffffff: excluding 0xd0000000-0xd7ffffff
[   16.194837] cfg80211: World regulatory domain updated:
[   16.194843]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.194846]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.194850]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.194853]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.194856]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.194859]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.224665] type=1400 audit(1285799460.222:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=661 comm="apparmor_parser"
[   16.225346] type=1400 audit(1285799460.222:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=661 comm="apparmor_parser"
[   16.225720] type=1400 audit(1285799460.222:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=661 comm="apparmor_parser"
[   16.274878] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.274883] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.274995]   alloc irq_desc for 21 on node -1
[   16.274998]   alloc kstat_irqs on node -1
[   16.275006] ipw2200 0000:0b:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.275786] [drm] Initialized drm 1.1.0 20060810
[   16.297724] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.341658] input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.4/1-1.4:1.1/input/input5
[   16.341976] generic-usb 0003:1058:1105.0001: input,hidraw0: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-1.4/input1
[   16.342312] usbcore: registered new interface driver usbhid
[   16.342315] usbhid: USB HID core driver
[   16.345520] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
[   16.347265] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   16.348057] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.348688] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   16.356433] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
[   16.356554] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   16.356632] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   16.356697] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.601127] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   16.601131] thinkpad_acpi: http://ibm-acpi.sf.net/
[   16.601133] thinkpad_acpi: ThinkPad BIOS 1YET65WW (1.29 ), EC 1YHT29WW-1.06
[   16.601136] thinkpad_acpi: IBM ThinkPad T43p, model 2668A69
[   16.610167] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   16.635361] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[   16.641836] Registered led device: tpacpi::thinklight
[   16.642496] Registered led device: tpacpi::power
[   16.643076] Registered led device: tpacpi::standby
[   16.665019] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   16.699016] thinkpad_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode
[   16.701810] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   16.713554] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input7
[   16.745171] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.745202] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   16.751348] [drm] radeon defaulting to kernel modesetting.
[   16.751352] [drm] radeon kernel modesetting enabled.
[   16.751546] radeon 0000:01:00.0: power state changed by ACPI to D0
[   16.751588] radeon 0000:01:00.0: power state changed by ACPI to D0
[   16.751608] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.751615] radeon 0000:01:00.0: setting latency timer to 64
[   16.778822] [drm] initializing kernel modesetting (RV380 0x1002:0x3154).
[   16.788103] [drm] register mmio base: 0xB0100000
[   16.788106] [drm] register mmio size: 65536
[   16.788279] [drm] Generation 2 PCI interface, using max accessible memory
[   16.788286] radeon 0000:01:00.0: VRAM: 128M 0xC0000000 - 0xC7FFFFFF (128M used)
[   16.788290] radeon 0000:01:00.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
[   16.788335]   alloc irq_desc for 43 on node -1
[   16.788338]   alloc kstat_irqs on node -1
[   16.788350] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[   16.788356] radeon 0000:01:00.0: radeon: using MSI.
[   16.788390] [drm] radeon: irq initialized.
[   16.788878] [drm] Detected VRAM RAM=128M, BAR=128M
[   16.788883] [drm] RAM width 128bits DDR
[   16.796870] [TTM] Zone  kernel: Available graphics memory: 436588 kiB.
[   16.796874] [TTM] Zone highmem: Available graphics memory: 1029904 kiB.
[   16.796876] [TTM] Initializing pool allocator.
[   16.796900] [drm] radeon: 128M of VRAM memory ready
[   16.796902] [drm] radeon: 512M of GTT memory ready.
[   16.796929] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   16.797732] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   16.799225] [drm] PCIE GART of 512M enabled (table at 0xC0040000).
[   16.800143] [drm] Loading R300 Microcode
[   16.810028] [drm] radeon: ring at 0x00000000A0000000
[   16.810052] [drm] ring test succeeded in 1 usecs
[   16.810227] [drm] radeon: ib pool ready.
[   16.810304] [drm] ib test succeeded in 0 usecs
[   16.810424] [drm] DFP table revision: 4
[   16.810476] [drm] Panel ID String: SXGA+ Single (85MHz)    
[   16.810478] [drm] Panel Size 1400x1050
[   16.810512] [drm] Default TV standard: NTSC
[   16.810515] [drm] 27.000000000 MHz TV ref clk
[   16.810517] [drm] Default TV standard: NTSC
[   16.810519] [drm] 27.000000000 MHz TV ref clk
[   16.810550] [drm] Radeon Display Connectors
[   16.810552] [drm] Connector 0:
[   16.810554] [drm]   VGA
[   16.810557] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   16.810559] [drm]   Encoders:
[   16.810561] [drm]     CRT1: INTERNAL_DAC1
[   16.810563] [drm] Connector 1:
[   16.810565] [drm]   DVI-D
[   16.810566] [drm]   HPD1
[   16.810569] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   16.810571] [drm]   Encoders:
[   16.810573] [drm]     DFP1: INTERNAL_TMDS1
[   16.810574] [drm] Connector 2:
[   16.810576] [drm]   LVDS
[   16.810578] [drm]   Encoders:
[   16.810579] [drm]     LCD1: INTERNAL_LVDS
[   16.810581] [drm] Connector 3:
[   16.810583] [drm]   S-video
[   16.810584] [drm]   Encoders:
[   16.810586] [drm]     TV1: INTERNAL_DAC2
[   17.037220] type=1400 audit(1285799461.034:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=914 comm="apparmor_parser"
[   17.045158] type=1400 audit(1285799461.042:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=916 comm="apparmor_parser"
[   17.045847] type=1400 audit(1285799461.042:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=916 comm="apparmor_parser"
[   17.046227] type=1400 audit(1285799461.042:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=916 comm="apparmor_parser"
[   17.051188] type=1400 audit(1285799461.046:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=918 comm="apparmor_parser"
[   17.062570] [drm] radeon: power management initialized
[   17.089636] type=1400 audit(1285799461.086:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=918 comm="apparmor_parser"
[   17.096253] type=1400 audit(1285799461.094:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=918 comm="apparmor_parser"
[   17.098274] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   17.392370] usb 1-1.1.2: device descriptor read/64, error -110
[   17.467857] [drm] fb mappable at 0xC00C0000
[   17.467860] [drm] vram apper at 0xC0000000
[   17.467862] [drm] size 9216000
[   17.467864] [drm] fb depth is 24
[   17.467866] [drm]    pitch is 7680
[   17.556309] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.663128] Console: switching to colour frame buffer device 175x65
[   17.670435] fb0: radeondrmfb frame buffer device
[   17.670437] drm: registered panic notifier
[   17.670803] Slow work thread pool: Starting up
[   17.671371] Slow work thread pool: Ready
[   17.671380] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[   17.704050] intel8x0_measure_ac97_clock: measured 55411 usecs (2670 samples)
[   17.704055] intel8x0: clocking to 48000
[   21.482502] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   27.784024] eth1: no IPv6 routers present
[   32.612297] usb 1-1.1.2: device descriptor read/64, error -110
[   32.788295] usb 1-1.1.2: new high speed USB device using ehci_hcd and address 9
[   47.860341] usb 1-1.1.2: device descriptor read/64, error -110
[   58.761493] lib80211_crypt: registered algorithm 'WEP'
[   63.036282] usb 1-1.1.2: device descriptor read/64, error -110
[   63.212280] usb 1-1.1.2: new high speed USB device using ehci_hcd and address 10
[   67.430897] EXT3-fs: barriers not enabled
[   67.455798] kjournald starting.  Commit interval 5 seconds
[   67.456360] EXT3-fs (sdc1): warning: maximal mount count reached, running e2fsck is recommended
[   67.457632] EXT3-fs (sdc1): using internal journal
[   67.457638] EXT3-fs (sdc1): mounted filesystem with ordered data mode
[   67.548398] EXT3-fs: barriers not enabled
[   67.571674] kjournald starting.  Commit interval 5 seconds
[   67.572798] EXT3-fs (sdd3): warning: maximal mount count reached, running e2fsck is recommended
[   67.574318] EXT3-fs (sdd3): using internal journal
[   67.574324] EXT3-fs (sdd3): mounted filesystem with ordered data mode
[   67.775402] EXT3-fs: barriers not enabled
[   67.793926] kjournald starting.  Commit interval 5 seconds
[   67.795041] EXT3-fs (sde1): warning: maximal mount count reached, running e2fsck is recommended
[   67.796258] EXT3-fs (sde1): using internal journal
[   67.796264] EXT3-fs (sde1): mounted filesystem with ordered data mode
[   68.014272] EXT3-fs: barriers not enabled
[   68.042388] kjournald starting.  Commit interval 5 seconds
[   68.043526] EXT3-fs (sde2): warning: maximal mount count reached, running e2fsck is recommended
[   68.068523] EXT3-fs (sde2): using internal journal
[   68.068531] EXT3-fs (sde2): mounted filesystem with ordered data mode
[   68.232164] usb 1-1.1.2: device descriptor read/8, error -110
[   73.352100] usb 1-1.1.2: device descriptor read/8, error -110
[   73.528362] usb 1-1.1.2: new high speed USB device using ehci_hcd and address 11
[   78.548089] usb 1-1.1.2: device descriptor read/8, error -110
[   83.668193] usb 1-1.1.2: device descriptor read/8, error -110
[   83.772340] hub 1-1.1:1.0: unable to enumerate USB device on port 2
[   83.844320] usb 1-1.1.3: new full speed USB device using ehci_hcd and address 12
[   86.439440] 12:1:1: endpoint lacks sample rate attribute bit, cannot set.
[   86.439941] 12:1:2: endpoint lacks sample rate attribute bit, cannot set.
[   86.440325] 12:1:3: endpoint lacks sample rate attribute bit, cannot set.
[   86.440686] 12:1:4: endpoint lacks sample rate attribute bit, cannot set.
[   86.441060] 12:1:5: endpoint lacks sample rate attribute bit, cannot set.
[   86.441685] 12:1:6: endpoint lacks sample rate attribute bit, cannot set.
[   86.442062] 12:1:7: endpoint lacks sample rate attribute bit, cannot set.
[   86.442436] 12:1:8: endpoint lacks sample rate attribute bit, cannot set.
[   86.443416] 12:2:1: endpoint lacks sample rate attribute bit, cannot set.
[   86.443795] 12:2:2: endpoint lacks sample rate attribute bit, cannot set.
[   86.444457] 12:2:3: endpoint lacks sample rate attribute bit, cannot set.
[   86.444923] 12:2:4: endpoint lacks sample rate attribute bit, cannot set.
[   86.446349] usbcore: registered new interface driver snd-usb-audio
[   87.126907] 12:1:1: endpoint lacks sample rate attribute bit, cannot set.
[   87.236738] 12:2:1: endpoint lacks sample rate attribute bit, cannot set.
[   87.360437] 12:2:1: endpoint lacks sample rate attribute bit, cannot set.
[   87.363686] 12:1:1: endpoint lacks sample rate attribute bit, cannot set.
[   87.502832] 12:2:1: endpoint lacks sample rate attribute bit, cannot set.
[   87.519747] cannot submit datapipe for urb 0, error -28: not enough bandwidth
```

thank you.

---

### Post by SOME1 on 2010-09-29
I have many usb devices in my pc, so to simplified it, I disconnected them all, and this is the output of dmesg after the only usb that connect is the tevii s660: 

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee5000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fee5000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  modified: 000000007fed0000 - 000000007fee5000 (ACPI data)
[    0.000000]  modified: 000000007fee5000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  modified: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375ac000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a5000 - 013e8182
[    0.000000] Move RAMDISK from 00000000375ac000 - 0000000037fef181 to 009a5000 - 013e8181
[    0.000000] ACPI: RSDP 000f6c00 00024 (v02 IBM   )
[    0.000000] ACPI: XSDT 7fed6fe7 0005C (v01 IBM    TP-1Y    00001290  LTP 00000000)
[    0.000000] ACPI: FACP 7fed7100 000F4 (v03 IBM    TP-1Y    00001290 IBM  00000001)
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20100428/tbfadt-526)
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 0x000000000000102C/0x0 (20100428/tbfadt-557)
[    0.000000] ACPI: DSDT 7fed72e7 0DB15 (v01 IBM    TP-1Y    00001290 MSFT 0100000E)
[    0.000000] ACPI: FACS 7fef6000 00040
[    0.000000] ACPI: SSDT 7fed72b4 00033 (v01 IBM    TP-1Y    00001290 MSFT 0100000E)
[    0.000000] ACPI: ECDT 7fee4dfc 00052 (v01 IBM    TP-1Y    00001290 IBM  00000001)
[    0.000000] ACPI: TCPA 7fee4e4e 00032 (v01 IBM    TP-1Y    00001290 PTL  00000001)
[    0.000000] ACPI: APIC 7fee4e80 0005A (v01 IBM    TP-1Y    00001290 IBM  00000001)
[    0.000000] ACPI: MCFG 7fee4eda 0003C (v01 IBM    TP-1Y    00001290 IBM  00000001)
[    0.000000] ACPI: BOOT 7fee4fd8 00028 (v01 IBM    TP-1Y    00001290  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523872
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c13ea020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294340 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519778
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=f220d3bf-de8f-4011-88a2-8a1e6b909a7c ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479660 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (49 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [000009f000 - 0000100000]   BIOS reserved
[    0.000000]   #4 [00009a1000 - 00009a415c]             BRK
[    0.000000]   #5 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #6 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #7 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #8 [00009a5000 - 00013e9000]     NEW RAMDISK
[    0.000000]   #9 [00013e9000 - 00013ea000]         BOOTMEM
[    0.000000]   #10 [00013ea000 - 00023ea000]         BOOTMEM
[    0.000000]   #11 [00023ea000 - 00023ea004]         BOOTMEM
[    0.000000]   #12 [00023ea040 - 00023ea100]         BOOTMEM
[    0.000000]   #13 [00023ea100 - 00023ea154]         BOOTMEM
[    0.000000]   #14 [00023ea180 - 00023ed180]         BOOTMEM
[    0.000000]   #15 [00023ed180 - 00023ed1f0]         BOOTMEM
[    0.000000]   #16 [00023ed200 - 00023f3200]         BOOTMEM
[    0.000000]   #17 [00023f3200 - 00023f3227]         BOOTMEM
[    0.000000]   #18 [00023f3240 - 00023f3438]         BOOTMEM
[    0.000000]   #19 [00023f3440 - 00023f3480]         BOOTMEM
[    0.000000]   #20 [00023f3480 - 00023f34c0]         BOOTMEM
[    0.000000]   #21 [00023f34c0 - 00023f3500]         BOOTMEM
[    0.000000]   #22 [00023f3500 - 00023f3540]         BOOTMEM
[    0.000000]   #23 [00023f3540 - 00023f3580]         BOOTMEM
[    0.000000]   #24 [00023f3580 - 00023f35c0]         BOOTMEM
[    0.000000]   #25 [00023f35c0 - 00023f3600]         BOOTMEM
[    0.000000]   #26 [00023f3600 - 00023f3640]         BOOTMEM
[    0.000000]   #27 [00023f3640 - 00023f3680]         BOOTMEM
[    0.000000]   #28 [00023f3680 - 00023f36c0]         BOOTMEM
[    0.000000]   #29 [00023f36c0 - 00023f3700]         BOOTMEM
[    0.000000]   #30 [00023f3700 - 00023f3740]         BOOTMEM
[    0.000000]   #31 [00023f3740 - 00023f3780]         BOOTMEM
[    0.000000]   #32 [00023f3780 - 00023f37c0]         BOOTMEM
[    0.000000]   #33 [00023f37c0 - 00023f3800]         BOOTMEM
[    0.000000]   #34 [00023f3800 - 00023f3810]         BOOTMEM
[    0.000000]   #35 [00023f3840 - 00023f3850]         BOOTMEM
[    0.000000]   #36 [00023f3880 - 00023f38ea]         BOOTMEM
[    0.000000]   #37 [00023f3900 - 00023f396a]         BOOTMEM
[    0.000000]   #38 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #39 [00023f5980 - 00023f5984]         BOOTMEM
[    0.000000]   #40 [00023f59c0 - 00023f59c4]         BOOTMEM
[    0.000000]   #41 [00023f5a00 - 00023f5a04]         BOOTMEM
[    0.000000]   #42 [00023f5a40 - 00023f5a44]         BOOTMEM
[    0.000000]   #43 [00023f5a80 - 00023f5b30]         BOOTMEM
[    0.000000]   #44 [00023f5b40 - 00023f5be8]         BOOTMEM
[    0.000000]   #45 [00023f5c00 - 00023f9c00]         BOOTMEM
[    0.000000]   #46 [000240e000 - 000248e000]         BOOTMEM
[    0.000000]   #47 [000248e000 - 00024ce000]         BOOTMEM
[    0.000000]   #48 [00024ce000 - 0002ecc82c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fed0)
[    0.000000] Memory: 2048588k/2095936k available (4928k kernel code, 46900k reserved, 2336k data, 684k init, 1186632k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 798.126 MHz processor.
[    0.008009] Calibrating delay loop (skipped), value calculated using timer frequency.. 1596.25 BogoMIPS (lpj=3192504)
[    0.008022] pid_max: default: 32768 minimum: 301
[    0.008074] Security Framework initialized
[    0.008118] AppArmor: AppArmor initialized
[    0.008124] Yama: becoming mindful.
[    0.008259] Mount-cache hash table entries: 512
[    0.008541] Initializing cgroup subsys ns
[    0.008551] Initializing cgroup subsys cpuacct
[    0.008562] Initializing cgroup subsys memory
[    0.008586] Initializing cgroup subsys devices
[    0.008593] Initializing cgroup subsys freezer
[    0.008599] Initializing cgroup subsys net_cls
[    0.008665] mce: CPU supports 5 MCE banks
[    0.008684] CPU0: Thermal monitoring enabled (TM2)
[    0.008703] Performance Events: p6 PMU driver.
[    0.008721] ... version:                0
[    0.008726] ... bit width:              32
[    0.008731] ... generic registers:      2
[    0.008737] ... value mask:             00000000ffffffff
[    0.008742] ... max period:             000000007fffffff
[    0.008748] ... fixed-purpose events:   0
[    0.008753] ... event mask:             0000000000000003
[    0.012011] SMP alternatives: switching to UP code
[    0.028917] Freeing SMP alternatives: 24k freed
[    0.028936] ACPI: Core revision 20100428
[    0.060015] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.060026] ftrace: allocating 21758 entries in 43 pages
[    0.064095] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.064496] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.106596] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    0.108000] Brought up 1 CPUs
[    0.108000] Total of 1 processors activated (1596.25 BogoMIPS).
[    0.108000] devtmpfs: initialized
[    0.108000] regulator: core version 0.5
[    0.108000] Time:  1:45:03  Date: 09/30/10
[    0.108000] NET: Registered protocol family 16
[    0.108152] EISA bus registered
[    0.108170] ACPI: bus type pci registered
[    0.108317] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.108326] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.108332] PCI: Using MMCONFIG for extended config space
[    0.108337] PCI: Using configuration type 1 for base access
[    0.110721] bio: create slab <bio-0> at 0
[    0.115744] ACPI: EC: EC description table is found, configuring boot EC
[    0.148021] ACPI: Interpreter enabled
[    0.148029] ACPI: (supports S0 S3 S4 S5)
[    0.148090] ACPI: Using IOAPIC for interrupt routing
[    0.168462] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.168570] ACPI: Power Resource [PUBS] (on)
[    0.173974] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.173985] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.174046] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.174185] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.174193] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.174201] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.174209] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.174217] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.174226] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
[    0.174351] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.174359] pci 0000:00:01.0: PME# disabled
[    0.174513] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.174523] pci 0000:00:1c.0: PME# disabled
[    0.174645] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.174654] pci 0000:00:1c.2: PME# disabled
[    0.174736] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
[    0.174817] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
[    0.174896] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
[    0.174974] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
[    0.175049] pci 0000:00:1d.7: reg 10: [mem 0xb0000000-0xb00003ff]
[    0.175125] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.175134] pci 0000:00:1d.7: PME# disabled
[    0.175262] pci 0000:00:1e.2: reg 10: [io  0x1c00-0x1cff]
[    0.175274] pci 0000:00:1e.2: reg 14: [io  0x1880-0x18bf]
[    0.175288] pci 0000:00:1e.2: reg 18: [mem 0xb0000800-0xb00009ff]
[    0.175301] pci 0000:00:1e.2: reg 1c: [mem 0xb0000400-0xb00004ff]
[    0.175350] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.175358] pci 0000:00:1e.2: PME# disabled
[    0.175403] pci 0000:00:1e.3: reg 10: [io  0x2400-0x24ff]
[    0.175416] pci 0000:00:1e.3: reg 14: [io  0x2000-0x207f]
[    0.175477] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.175486] pci 0000:00:1e.3: PME# disabled
[    0.175597] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.175610] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.175620] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.175629] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 1600-167f
[    0.175638] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 15e0-15ef
[    0.175689] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.175702] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.175714] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.175727] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.175739] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.175784] pci 0000:00:1f.2: PME# supported from D3hot
[    0.175793] pci 0000:00:1f.2: PME# disabled
[    0.175866] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
[    0.175975] pci 0000:01:00.0: reg 10: [mem 0xc0000000-0xc7ffffff pref]
[    0.175986] pci 0000:01:00.0: reg 14: [io  0x3000-0x30ff]
[    0.175997] pci 0000:01:00.0: reg 18: [mem 0xb0100000-0xb010ffff]
[    0.176024] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.176052] pci 0000:01:00.0: supports D1 D2
[    0.176070] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.176086] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.176094] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.176103] pci 0000:00:01.0:   bridge window [mem 0xb0100000-0xb01fffff]
[    0.176112] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc7ffffff pref]
[    0.176245] pci 0000:02:00.0: reg 10: [mem 0xb0200000-0xb020ffff 64bit]
[    0.176355] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.176366] pci 0000:02:00.0: PME# disabled
[    0.176393] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.176413] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.176423] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.176433] pci 0000:00:1c.0:   bridge window [mem 0xb0200000-0xb02fffff]
[    0.176446] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.176522] pci 0000:00:1c.2: PCI bridge to [bus 03-0a]
[    0.176531] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.176541] pci 0000:00:1c.2:   bridge window [mem 0xb2000000-0xb3ffffff]
[    0.176555] pci 0000:00:1c.2:   bridge window [mem 0xc8000000-0xc80fffff 64bit pref]
[    0.176642] pci 0000:0b:00.0: reg 10: [mem 0xb4000000-0xb4000fff]
[    0.176679] pci 0000:0b:00.0: supports D1 D2
[    0.176685] pci 0000:0b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176695] pci 0000:0b:00.0: PME# disabled
[    0.176769] pci 0000:0b:02.0: reg 10: [mem 0xb4001000-0xb4001fff]
[    0.176857] pci 0000:0b:02.0: PME# supported from D0 D3hot D3cold
[    0.176867] pci 0000:0b:02.0: PME# disabled
[    0.176946] pci 0000:00:1e.0: PCI bridge to [bus 0b-0e] (subtractive decode)
[    0.176956] pci 0000:00:1e.0:   bridge window [io  0x5000-0x8fff]
[    0.176966] pci 0000:00:1e.0:   bridge window [mem 0xb4000000-0xbfffffff]
[    0.176979] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.176987] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.176994] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.177087] pci_bus 0000:00: on NUMA node 0
[    0.177099] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.177423] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.177597] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.177786] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.177991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.189908] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.190355] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.190796] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.191236] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.191676] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.192134] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.192575] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.193015] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.193178] HEST: Table is not found!
[    0.193340] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.193350] vgaarb: loaded
[    0.193733] SCSI subsystem initialized
[    0.193823] libata version 3.00 loaded.
[    0.193947] usbcore: registered new interface driver usbfs
[    0.193978] usbcore: registered new interface driver hub
[    0.194040] usbcore: registered new device driver usb
[    0.194330] ACPI: WMI: Mapper loaded
[    0.194335] PCI: Using ACPI for IRQ routing
[    0.194341] PCI: pci_cache_line_size set to 64 bytes
[    0.194467] Expanded resource reserved due to conflict with Adapter ROM
[    0.194475] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.194482] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.194489] reserve RAM buffer: 000000007fed0000 - 000000007fffffff 
[    0.194695] NetLabel: Initializing
[    0.194700] NetLabel:  domain hash size = 128
[    0.194704] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.194733] NetLabel:  unlabeled traffic allowed by default
[    0.195074] hpet clockevent registered
[    0.195082] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.195094] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.195106] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.200040] Switching to clocksource tsc
[    0.224748] AppArmor: AppArmor Filesystem Enabled
[    0.224783] pnp: PnP ACPI init
[    0.224822] ACPI: bus type pnp registered
[    0.232718] pnp: PnP ACPI: found 14 devices
[    0.232724] ACPI: ACPI bus type pnp unregistered
[    0.232732] PnPBIOS: Disabled by ACPI PNP
[    0.232761] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.232770] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.232778] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.232786] system 00:00: [mem 0x000c8000-0x000cbfff] could not be reserved
[    0.232794] system 00:00: [mem 0x000cc000-0x000cffff] could not be reserved
[    0.232803] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
[    0.232811] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
[    0.232819] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.232827] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.232835] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.232843] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.232852] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.232860] system 00:00: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.232869] system 00:00: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.232887] system 00:02: [io  0x1000-0x107f] has been reserved
[    0.232894] system 00:02: [io  0x1180-0x11bf] has been reserved
[    0.232902] system 00:02: [io  0x15e0-0x15ef] has been reserved
[    0.232910] system 00:02: [io  0x1600-0x1641] has been reserved
[    0.232917] system 00:02: [io  0x1644-0x167f] has been reserved
[    0.232926] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved
[    0.232934] system 00:02: [mem 0xf0008000-0xf000bfff] has been reserved
[    0.232942] system 00:02: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.232950] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.232958] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.271251] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.271262] pci 0000:00:1c.0: BAR 13: assigned [io  0x9000-0x9fff]
[    0.271271] pci 0000:01:00.0: BAR 6: assigned [mem 0xb0120000-0xb013ffff pref]
[    0.271279] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.271287] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.271296] pci 0000:00:01.0:   bridge window [mem 0xb0100000-0xb01fffff]
[    0.271305] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xc7ffffff pref]
[    0.271315] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.271323] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
[    0.271334] pci 0000:00:1c.0:   bridge window [mem 0xb0200000-0xb02fffff]
[    0.271344] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.271358] pci 0000:00:1c.2: PCI bridge to [bus 03-0a]
[    0.271365] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.271376] pci 0000:00:1c.2:   bridge window [mem 0xb2000000-0xb3ffffff]
[    0.271387] pci 0000:00:1c.2:   bridge window [mem 0xc8000000-0xc80fffff 64bit pref]
[    0.271403] pci 0000:0b:00.0: BAR 15: assigned [mem 0xd0000000-0xd3ffffff pref]
[    0.271411] pci 0000:0b:00.0: BAR 16: assigned [mem 0xb8000000-0xbbffffff]
[    0.271418] pci 0000:0b:00.0: BAR 13: assigned [io  0x5000-0x50ff]
[    0.271425] pci 0000:0b:00.0: BAR 14: assigned [io  0x5400-0x54ff]
[    0.271432] pci 0000:0b:00.0: CardBus bridge to [bus 0c-0d]
[    0.271439] pci 0000:0b:00.0:   bridge window [io  0x5000-0x50ff]
[    0.271449] pci 0000:0b:00.0:   bridge window [io  0x5400-0x54ff]
[    0.271460] pci 0000:0b:00.0:   bridge window [mem 0xd0000000-0xd3ffffff pref]
[    0.271471] pci 0000:0b:00.0:   bridge window [mem 0xb8000000-0xbbffffff]
[    0.271481] pci 0000:00:1e.0: PCI bridge to [bus 0b-0e]
[    0.271489] pci 0000:00:1e.0:   bridge window [io  0x5000-0x8fff]
[    0.271500] pci 0000:00:1e.0:   bridge window [mem 0xb4000000-0xbfffffff]
[    0.271511] pci 0000:00:1e.0:   bridge window [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.271535]   alloc irq_desc for 16 on node -1
[    0.271540]   alloc kstat_irqs on node -1
[    0.271553] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.271563] pci 0000:00:01.0: setting latency timer to 64
[    0.271579]   alloc irq_desc for 20 on node -1
[    0.271584]   alloc kstat_irqs on node -1
[    0.271593] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.271602] pci 0000:00:1c.0: setting latency timer to 64
[    0.271619]   alloc irq_desc for 22 on node -1
[    0.271624]   alloc kstat_irqs on node -1
[    0.271632] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.271642] pci 0000:00:1c.2: setting latency timer to 64
[    0.271656] pci 0000:00:1e.0: setting latency timer to 64
[    0.271678] pci 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.271690] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.271697] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.271704] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.271711] pci_bus 0000:01: resource 1 [mem 0xb0100000-0xb01fffff]
[    0.271718] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xc7ffffff pref]
[    0.271726] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.271732] pci_bus 0000:02: resource 1 [mem 0xb0200000-0xb02fffff]
[    0.271739] pci_bus 0000:02: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.271747] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.271753] pci_bus 0000:03: resource 1 [mem 0xb2000000-0xb3ffffff]
[    0.271761] pci_bus 0000:03: resource 2 [mem 0xc8000000-0xc80fffff 64bit pref]
[    0.271768] pci_bus 0000:0b: resource 0 [io  0x5000-0x8fff]
[    0.271775] pci_bus 0000:0b: resource 1 [mem 0xb4000000-0xbfffffff]
[    0.271782] pci_bus 0000:0b: resource 2 [mem 0xd0000000-0xd7ffffff 64bit pref]
[    0.271789] pci_bus 0000:0b: resource 4 [io  0x0000-0xffff]
[    0.271795] pci_bus 0000:0b: resource 5 [mem 0x00000000-0xffffffff]
[    0.271803] pci_bus 0000:0c: resource 0 [io  0x5000-0x50ff]
[    0.271809] pci_bus 0000:0c: resource 1 [io  0x5400-0x54ff]
[    0.271816] pci_bus 0000:0c: resource 2 [mem 0xd0000000-0xd3ffffff pref]
[    0.271823] pci_bus 0000:0c: resource 3 [mem 0xb8000000-0xbbffffff]
[    0.271901] NET: Registered protocol family 2
[    0.272055] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.272601] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.274116] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.274879] TCP: Hash tables configured (established 131072 bind 65536)
[    0.274885] TCP reno registered
[    0.274893] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.274919] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.275104] NET: Registered protocol family 1
[    0.275287] pci 0000:01:00.0: Boot video device
[    0.275312] PCI: CLS 32 bytes, default 64
[    0.275450] Simple Boot Flag at 0x35 set to 0x1
[    0.275651] cpufreq-nforce2: No nForce2 chipset.
[    0.275723] Scanning for low memory corruption every 60 seconds
[    0.276075] audit: initializing netlink socket (disabled)
[    0.276097] type=2000 audit(1285811103.272:1): initialized
[    0.304799] Trying to unpack rootfs image as initramfs...
[    0.340766] highmem bounce pool size: 64 pages
[    0.340780] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.344676] VFS: Disk quotas dquot_6.5.2
[    0.344823] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.352660] fuse init (API version 7.14)
[    0.352896] msgmni has been set to 1683
[    0.361027] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.361035] io scheduler noop registered
[    0.361041] io scheduler deadline registered
[    0.361076] io scheduler cfq registered (default)
[    0.361320] pcieport 0000:00:01.0: setting latency timer to 64
[    0.361362]   alloc irq_desc for 40 on node -1
[    0.361367]   alloc kstat_irqs on node -1
[    0.361383] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.361503] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.361559]   alloc irq_desc for 41 on node -1
[    0.361564]   alloc kstat_irqs on node -1
[    0.361578] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.361754] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.361810]   alloc irq_desc for 42 on node -1
[    0.361815]   alloc kstat_irqs on node -1
[    0.361829] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.362057] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.362246] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.362851] ACPI: AC Adapter [AC] (off-line)
[    0.363017] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.363280] ACPI: Lid Switch [LID]
[    0.363417] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.363429] ACPI: Sleep Button [SLPB]
[    0.363564] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.363574] ACPI: Power Button [PWRF]
[    0.364139] ACPI: acpi_idle registered with cpuidle
[    0.364941] Marking TSC unstable due to TSC halts in idle
[    0.373366] Switching to clocksource hpet
[    0.384059] thermal LNXTHERM:01: registered as thermal_zone0
[    0.384081] ACPI: Thermal Zone [THM0] (69 C)
[    0.384268] ERST: Table is not found!
[    0.384547] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.386416] serial 00:0a: activated
[    0.386596] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    0.386862]   alloc irq_desc for 23 on node -1
[    0.386868]   alloc kstat_irqs on node -1
[    0.386881] serial 0000:00:1e.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.386893] serial 0000:00:1e.3: PCI INT B disabled
[    0.394389] brd: module loaded
[    0.395752] loop: module loaded
[    0.396280] isapnp: Scanning for PnP cards...
[    0.403761] ata_piix 0000:00:1f.2: version 2.13
[    0.403787] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.492516] ACPI: Battery Slot [BAT0] (battery present)
[    0.556312] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.560709] scsi0 : ata_piix
[    0.560928] scsi1 : ata_piix
[    0.563139] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
[    0.563147] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
[    0.564169] Fixed MDIO Bus: probed
[    0.564263] PPP generic driver version 2.4.2
[    0.564390] tun: Universal TUN/TAP device driver, 1.6
[    0.564395] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.564582] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.568150] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.568509] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    0.568527]   alloc irq_desc for 19 on node -1
[    0.568532]   alloc kstat_irqs on node -1
[    0.568546] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.568574] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.568581] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.568667] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.568719] ehci_hcd 0000:00:1d.7: debug port 1
[    0.572602] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.576925] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xb0000000
[    0.596782] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.597097] hub 1-0:1.0: USB hub found
[    0.597109] hub 1-0:1.0: 8 ports detected
[    0.597279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.597314] uhci_hcd: USB Universal Host Controller Interface driver
[    0.597652] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.597959] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.597977] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.597991] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.597999] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.598098] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.598158] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    0.598435] hub 2-0:1.0: USB hub found
[    0.598446] hub 2-0:1.0: 2 ports detected
[    0.599777] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.600048] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    0.600061]   alloc irq_desc for 17 on node -1
[    0.600067]   alloc kstat_irqs on node -1
[    0.600079] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.600092] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.600099] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.600194] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.600249] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001820
[    0.600528] hub 3-0:1.0: USB hub found
[    0.600539] hub 3-0:1.0: 2 ports detected
[    0.600657]   alloc irq_desc for 18 on node -1
[    0.600662]   alloc kstat_irqs on node -1
[    0.600672] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.600685] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.600692] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.600769] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.600830] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    0.601120] hub 4-0:1.0: USB hub found
[    0.601130] hub 4-0:1.0: 2 ports detected
[    0.601247] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.601260] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.601267] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.601348] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.601384] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001860
[    0.601654] hub 5-0:1.0: USB hub found
[    0.601664] hub 5-0:1.0: 2 ports detected
[    0.601963] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.656568] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.656583] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.656851] mice: PS/2 mouse device common for all mice
[    0.657185] rtc_cmos 00:06: RTC can wake from S4
[    0.657276] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.657319] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.657613] device-mapper: uevent: version 1.0.3
[    0.661073] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.664924] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.668295] device-mapper: multipath: version 1.1.1 loaded
[    0.668302] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.668582] EISA: Probing bus 0 at eisa.0
[    0.668594] Cannot allocate resource for EISA slot 1
[    0.668601] Cannot allocate resource for EISA slot 2
[    0.668607] Cannot allocate resource for EISA slot 3
[    0.668612] Cannot allocate resource for EISA slot 4
[    0.668618] Cannot allocate resource for EISA slot 5
[    0.668624] Cannot allocate resource for EISA slot 6
[    0.668630] Cannot allocate resource for EISA slot 7
[    0.668635] Cannot allocate resource for EISA slot 8
[    0.668640] EISA: Detected 0 cards.
[    0.676740] cpuidle: using governor ladder
[    0.676913] cpuidle: using governor menu
[    0.677590] TCP cubic registered
[    0.677931] NET: Registered protocol family 10
[    0.678743] lo: Disabled Privacy Extensions
[    0.679260] NET: Registered protocol family 17
[    0.680157] P-state transition latency capped at 20 uS
[    0.680568] Using IPI No-Shortcut mode
[    0.680769] PM: Resume from disk failed.
[    0.680791] registered taskstats version 1
[    0.681220]   Magic number: 10:611:762
[    0.681230] atkbd serio0: hash matches
[    0.681362] rtc_cmos 00:06: setting system clock to 2010-09-30 01:45:04 UTC (1285811104)
[    0.681370] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.681375] EDD information not available.
[    0.752822] ata1.00: ATA-6: TOSHIBA MK8032GAX, AB311E, max UDMA/100
[    0.752833] ata1.00: 156301488 sectors, multi 16: LBA48 
[    0.752866] ata1.00: applying bridge limits
[    0.753035] ata2.00: ATA-6: IC25N080ATMR04-0, MO4OADEA, max UDMA/100
[    0.753043] ata2.00: 156301488 sectors, multi 16: LBA 
[    0.761347] ata1.00: configured for UDMA/100
[    0.769424] ata2.00: configured for UDMA/100
[    1.011545] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.099729] isapnp: No Plug & Play device found
[    1.100034] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8032GA AB31 PQ: 0 ANSI: 5
[    1.100405] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.100702] scsi 1:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[    1.100968] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.101118] sd 1:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.101254] sd 1:0:0:0: [sdb] Write Protect is off
[    1.101262] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.101320] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.101481] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.101662] sd 0:0:0:0: [sda] Write Protect is off
[    1.101670] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.101796] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.101979]  sdb:
[    1.102300]  sda: sdb1
[    1.122766] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.133573]  sda1 sda2 < sda5 > sda3
[    1.147805] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.506158] Freeing initrd memory: 10512k freed
[    1.517002] Freeing unused kernel memory: 684k freed
[    1.517975] Write protecting the kernel text: 4932k
[    1.518068] Write protecting the kernel read-only data: 1976k
[    1.560258] udev[68]: starting version 163
[    2.033037] Floppy drive(s): fd0 is 1.44M
[    2.060281] FDC 0 is a National Semiconductor PC87306
[    2.110693] tg3.c:v3.110 (April 9, 2010)
[    2.110725] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.110744] tg3 0000:02:00.0: setting latency timer to 64
[    2.156345] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:21:86:61:32:14
[    2.156356] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.156366] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.156374] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.272824] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   15.689989] Adding 3905532k swap on /dev/sda5.  Priority:-1 extents:1 across:3905532k 
[   15.745841] udev[331]: starting version 163
[   16.044800] lp: driver loaded but no devices found
[   16.120136] usb 1-4: device descriptor read/64, error -110
[   16.137754] intel_rng: FWH not detected
[   16.393291] lib80211: common routines for IEEE802.11 drivers
[   16.393300] lib80211_crypt: registered algorithm 'NULL'
[   16.465702] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   16.667335] Non-volatile memory driver v1.3
[   16.876858] parport_pc 00:0b: reported by Plug and Play ACPI
[   16.876920] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   16.897281] Linux agpgart interface v0.103
[   16.914842] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input4
[   16.914955] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.941075] yenta_cardbus 0000:0b:00.0: CardBus bridge found [1014:056c]
[   17.008062] lp0: using parport0 (interrupt-driven).
[   17.068635] yenta_cardbus 0000:0b:00.0: ISA IRQ mask 0x0c38, PCI irq 16
[   17.068645] yenta_cardbus 0000:0b:00.0: Socket status: 30000006
[   17.068661] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge window: [io  0x5000-0x8fff]
[   17.068670] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x8fff: excluding 0x5000-0x50ff 0x5400-0x54ff
[   17.164574] ppdev: user-space parallel port driver
[   17.350392] irda_init()
[   17.350431] NET: Registered protocol family 23
[   17.356952] 
[   17.356964] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge window: [mem 0xb4000000-0xbfffffff]
[   17.356975] pcmcia_socket pcmcia_socket0: cs: memory probe 0xb4000000-0xbfffffff: excluding 0xb4000000-0xb47fffff 0xb8000000-0xbbffffff
[   17.357020] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge window: [mem 0xd0000000-0xd7ffffff 64bit pref]
[   17.357029] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0000000-0xd7ffffff: excluding 0xd0000000-0xd7ffffff
[   17.417398] cfg80211: Calling CRDA to update world regulatory domain
[   17.419679] nsc-ircc 00:0c: activated
[   17.419691] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   17.427259] nsc-ircc, chip->init
[   17.427278] nsc-ircc, Found chip at base=0x02e
[   17.427316] nsc-ircc, driver loaded (Dag Brattli)
[   17.451346] IrDA: Registered device irda0
[   17.451356] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   17.500924] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0/0x0
[   17.500937] serio: Synaptics pass-through port at isa0060/serio1/input0
[   17.554861] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   17.568586] type=1400 audit(1285803921.382:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=625 comm="apparmor_parser"
[   17.570301] type=1400 audit(1285803921.382:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=625 comm="apparmor_parser"
[   17.571174] type=1400 audit(1285803921.382:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=625 comm="apparmor_parser"
[   17.578911] cfg80211: World regulatory domain updated:
[   17.578918]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.578927]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.578935]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.578942]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.578950]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.578957]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.586543] libipw: 802.11 data/management/control stack, git-1.1.13
[   17.586551] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   17.618713] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
[   17.620861] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   17.621706] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.622427] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.623217] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
[   17.623356] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   17.647950] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   17.654461] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   17.812372] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.812380] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.812563]   alloc irq_desc for 21 on node -1
[   17.812569]   alloc kstat_irqs on node -1
[   17.812583] ipw2200 0000:0b:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.826705] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.901634] [drm] Initialized drm 1.1.0 20060810
[   18.254943] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   18.254950] thinkpad_acpi: http://ibm-acpi.sf.net/
[   18.254956] thinkpad_acpi: ThinkPad BIOS 1YET65WW (1.29 ), EC 1YHT29WW-1.06
[   18.254962] thinkpad_acpi: IBM ThinkPad T43p, model 2668A69
[   18.271301] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   18.372823] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[   18.377642] Registered led device: tpacpi::thinklight
[   18.378599] Registered led device: tpacpi::power
[   18.380781] Registered led device: tpacpi::standby
[   18.443026] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   18.502330] thinkpad_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode
[   18.503770] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   18.669770] type=1400 audit(1285803922.482:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=792 comm="apparmor_parser"
[   18.685774] type=1400 audit(1285803922.498:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=794 comm="apparmor_parser"
[   18.694824] type=1400 audit(1285803922.506:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=794 comm="apparmor_parser"
[   18.706506] type=1400 audit(1285803922.518:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=794 comm="apparmor_parser"
[   18.738553] type=1400 audit(1285803922.550:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=797 comm="apparmor_parser"
[   18.787619] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.787662] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   18.809277] type=1400 audit(1285803922.622:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=797 comm="apparmor_parser"
[   18.857637] type=1400 audit(1285803922.670:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=797 comm="apparmor_parser"
[   18.875938] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   18.930603] [drm] radeon defaulting to kernel modesetting.
[   18.930612] [drm] radeon kernel modesetting enabled.
[   18.930835] radeon 0000:01:00.0: power state changed by ACPI to D0
[   18.930927] radeon 0000:01:00.0: power state changed by ACPI to D0
[   18.930942] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.930954] radeon 0000:01:00.0: setting latency timer to 64
[   18.967346] [drm] initializing kernel modesetting (RV380 0x1002:0x3154).
[   18.984084] [drm] register mmio base: 0xB0100000
[   18.984092] [drm] register mmio size: 65536
[   18.984324] [drm] Generation 2 PCI interface, using max accessible memory
[   18.984337] radeon 0000:01:00.0: VRAM: 128M 0xC0000000 - 0xC7FFFFFF (128M used)
[   18.984345] radeon 0000:01:00.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
[   18.984411]   alloc irq_desc for 43 on node -1
[   18.984417]   alloc kstat_irqs on node -1
[   18.984435] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[   18.984445] radeon 0000:01:00.0: radeon: using MSI.
[   18.984495] [drm] radeon: irq initialized.
[   18.985033] [drm] Detected VRAM RAM=128M, BAR=128M
[   18.985041] [drm] RAM width 128bits DDR
[   18.999966] [TTM] Zone  kernel: Available graphics memory: 436588 kiB.
[   18.999974] [TTM] Zone highmem: Available graphics memory: 1029904 kiB.
[   18.999980] [TTM] Initializing pool allocator.
[   19.000058] [drm] radeon: 128M of VRAM memory ready
[   19.000063] [drm] radeon: 512M of GTT memory ready.
[   19.000105] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   19.002707] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   19.006096] [drm] PCIE GART of 512M enabled (table at 0xC0040000).
[   19.032535] [drm] Loading R300 Microcode
[   19.050195] [drm] radeon: ring at 0x00000000A0000000
[   19.050224] [drm] ring test succeeded in 1 usecs
[   19.050590] [drm] radeon: ib pool ready.
[   19.053144] [drm] ib test succeeded in 0 usecs
[   19.055039] [drm] DFP table revision: 4
[   19.057020] [drm] Panel ID String: SXGA+ Single (85MHz)    
[   19.057027] [drm] Panel Size 1400x1050
[   19.057573] [drm] Default TV standard: NTSC
[   19.057578] [drm] 27.000000000 MHz TV ref clk
[   19.057585] [drm] Default TV standard: NTSC
[   19.057589] [drm] 27.000000000 MHz TV ref clk
[   19.057897] [drm] Radeon Display Connectors
[   19.057903] [drm] Connector 0:
[   19.057907] [drm]   VGA
[   19.057914] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   19.057919] [drm]   Encoders:
[   19.057923] [drm]     CRT1: INTERNAL_DAC1
[   19.057928] [drm] Connector 1:
[   19.057932] [drm]   DVI-D
[   19.057935] [drm]   HPD1
[   19.057941] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   19.057946] [drm]   Encoders:
[   19.057950] [drm]     DFP1: INTERNAL_TMDS1
[   19.057954] [drm] Connector 2:
[   19.057958] [drm]   LVDS
[   19.057962] [drm]   Encoders:
[   19.057966] [drm]     LCD1: INTERNAL_LVDS
[   19.057970] [drm] Connector 3:
[   19.057974] [drm]   S-video
[   19.057977] [drm]   Encoders:
[   19.057981] [drm]     TV1: INTERNAL_DAC2
[   19.249679] [drm] radeon: power management initialized
[   19.353517] [drm] fb mappable at 0xC00C0000
[   19.353524] [drm] vram apper at 0xC0000000
[   19.353529] [drm] size 5914624
[   19.353533] [drm] fb depth is 24
[   19.353538] [drm]    pitch is 5632
[   19.418320] Console: switching to colour frame buffer device 175x65
[   19.434710] fb0: radeondrmfb frame buffer device
[   19.434715] drm: registered panic notifier
[   19.435364] Slow work thread pool: Starting up
[   19.435446] Slow work thread pool: Ready
[   19.435460] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[   19.606167] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.848041] intel8x0_measure_ac97_clock: measured 55294 usecs (2664 samples)
[   19.848049] intel8x0: clocking to 48000
[   20.518016] psmouse serio2: ID: 10 00 64
[   23.589570] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[   24.130377] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   24.362332] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7
[   26.076058] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
[   30.624038] eth1: no IPv6 routers present
[   31.336187] usb 1-4: device descriptor read/64, error -110
[   31.552061] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   46.664051] usb 1-4: device descriptor read/64, error -110
[   48.928302] lib80211_crypt: registered algorithm 'WEP'
[   61.880052] usb 1-4: device descriptor read/64, error -110
[   62.096058] usb 1-4: new high speed USB device using ehci_hcd and address 4
[   67.116078] usb 1-4: device descriptor read/8, error -110
[   72.236127] usb 1-4: device descriptor read/8, error -110
[   72.452049] usb 1-4: new high speed USB device using ehci_hcd and address 5
```

thanks again.

---

### Post by SOME1 on 2010-09-30
Thank you! 
I have finally got it to work on ubuntu 10.10 using the dmesg you recommended. 

I will publish it here after some more tests. 
thanks again.

edit: I post my solution [here]("http://ubuntuforums.org/showpost.php?p=9927773&postcount=32").

---

