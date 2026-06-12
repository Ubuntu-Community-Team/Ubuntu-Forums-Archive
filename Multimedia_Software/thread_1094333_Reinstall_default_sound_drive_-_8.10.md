---
title: "Reinstall default sound drive??? - 8.10"
date: 2009-03-12
forum: Multimedia Software
---

### Post by JordBrow on 2009-03-12
Hi, I appreciate any input in advance for my problem.  I've recently fully switched form vista to Ubuntu 8.10 and so therefore a real newbie.  After the install, everything seem to be working well until I installed Skype.  As I have since found out there has been a history of people having problems getting the microphone working as I was. 

I tried searching through forum posts trying to find a fix and came up empty handed.  Now I've been left without any sound working at all.  When the system loads, the sound icon in the corner has a little red x and if I try to click it, I get the following error message: 

No volume control GStreamer plugins and/or devices found.

I would appreciate if anyone could inform me if there is a way to reset back to the install default sound settings or some other way of getting the sound working again.  Also, it would be nice to figure out a way for the microphone to work, but I would be happy just having sound.

I've seen from other forum posts that the output of dmesg and lspci are helpful so here you go:

dmesg gives:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009bc00 (usable)
[    0.000000]  BIOS-e820: 000000000009bc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7aa8000 (usable)
[    0.000000]  BIOS-e820: 00000000b7aa8000 - 00000000b7ad0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7ad0000 - 00000000b7ae1000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7ae1000 - 00000000b7ae2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7ae2000 - 00000000b7b0a000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7b0a000 - 00000000b7b0b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7b0b000 - 00000000b7b0c000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7b0c000 - 00000000b7b17000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7b17000 - 00000000b7b1d000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7b1d000 - 00000000b7b39000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7b39000 - 00000000b7c00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xb7c00 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3781b000 - 37fef6a7
[    0.000000] ACPI: RSDP 000F03B0, 0024 (r2   Sony)
[    0.000000] ACPI: XSDT B7B15F10, 005C (r1   Sony     VAIO 20080709 MSFT    10013)
[    0.000000] ACPI: FACP B7B0AA90, 00F4 (r4   Sony     VAIO 20080709 MSFT    10013)
[    0.000000] ACPI: DSDT B7B0C010, 7AFE (r1   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: FACS B7B1CD40, 0040
[    0.000000] ACPI: APIC B7B14F10, 006C (r2   Sony     VAIO 20080709 MSFT    10013)
[    0.000000] ACPI: MCFG B7B1BC90, 003C (r1   Sony     VAIO 20080709 MSFT       97)
[    0.000000] ACPI: HPET B7B1BC10, 0038 (r1   Sony     VAIO 20080709 MSFT    10013)
[    0.000000] ACPI: SLIC B7B17C10, 0176 (r1   Sony     VAIO 20080709 Sony  1000000)
[    0.000000] ACPI: SSDT B7AE1590, 0505 (r1   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: SSDT B7ACCC10, 02E4 (r1   Sony     VAIO 20080709 INTL 20051117)
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] 2044MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781b000 - 0037fef6a7]          RAMDISK ==> [003781b000 - 0037fef6a7]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009bc00 - 0000100000]    BIOS reserved ==> [000009bc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00fd650] 000fd650
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000b7c00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000b7aa8
[    0.000000]     0: 0x000b7b39 -> 0x000b7c00
[    0.000000] On node 0 totalpages: 752378
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3943 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 518520 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b7c00000:28400000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 745763
[    0.000000] Kernel command line: root=UUID=531fd4e3-e581-4016-b7a6-27c3acd6bb51 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1993.534 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2968168k/3010560k available (2576k kernel code, 40396k reserved, 1165k data, 424k init, 2092476k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3987.06 BogoMIPS (lpj=7974136)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... <7>spurious 8259A interrupt: IRQ7.
[    0.016015] OK.
[    0.017826] ACPI: Core revision 20080609
[    0.020487] ACPI: Checking initramfs for custom DSDT
[    0.360188] ENABLING IO-APIC IRQs
[    0.360378] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[    0.402669] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.404025] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3987.09 BogoMIPS (lpj=7974182)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.488494] CPU1: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[    0.488511] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.492047] Brought up 2 CPUs
[    0.492050] Total of 2 processors activated (7974.15 BogoMIPS).
[    0.492071] CPU0 attaching sched-domain:
[    0.492074]  domain 0: span 0-1 level MC
[    0.492076]   groups: 0 1
[    0.492082] CPU1 attaching sched-domain:
[    0.492085]  domain 0: span 0-1 level MC
[    0.492087]   groups: 1 0
[    0.492160] net_namespace: 840 bytes
[    0.492160] Booting paravirtualized kernel on bare hardware
[    0.492292] Time: 16:31:11  Date: 03/12/09
[    0.492316] NET: Registered protocol family 16
[    0.492334] EISA bus registered
[    0.492334] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.492334] ACPI: bus type pci registered
[    0.492334] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.492334] PCI: MCFG area at e0000000 reserved in E820
[    0.492334] PCI: Using MMCONFIG for extended config space
[    0.492334] PCI: Using configuration type 1 for base access
[    0.493508] ACPI: EC: Look up EC in DSDT
[    0.500196] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.504839] ACPI: Interpreter enabled
[    0.504844] ACPI: (supports S0 S3 S4 S5)
[    0.504862] ACPI: Using IOAPIC for interrupt routing
[    0.504939] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.548243] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.548243] ACPI: EC: driver started in interrupt mode
[    0.548264] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.548264] PCI: 0000:00:02.0 reg 10 64bit mmio: [d0000000, d03fffff]
[    0.548264] PCI: 0000:00:02.0 reg 18 64bit mmio: [c0000000, cfffffff]
[    0.548264] PCI: 0000:00:02.0 reg 20 io port: [e140, e147]
[    0.548264] PCI: 0000:00:02.1 reg 10 64bit mmio: [d0400000, d04fffff]
[    0.548285] PCI: 0000:00:1a.0 reg 20 io port: [e0e0, e0ff]
[    0.548374] PCI: 0000:00:1a.1 reg 20 io port: [e0c0, e0df]
[    0.548463] PCI: 0000:00:1a.2 reg 20 io port: [e0a0, e0bf]
[    0.548554] PCI: 0000:00:1a.7 reg 10 32bit mmio: [d4204c00, d4204fff]
[    0.548617] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.548623] pci 0000:00:1a.7: PME# disabled
[    0.548672] PCI: 0000:00:1b.0 reg 10 64bit mmio: [d4200000, d4203fff]
[    0.548727] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.548732] pci 0000:00:1b.0: PME# disabled
[    0.548806] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.548811] pci 0000:00:1c.0: PME# disabled
[    0.548885] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.548890] pci 0000:00:1c.1: PME# disabled
[    0.548963] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.548968] pci 0000:00:1c.2: PME# disabled
[    0.549038] PCI: 0000:00:1d.0 reg 20 io port: [e080, e09f]
[    0.549127] PCI: 0000:00:1d.1 reg 20 io port: [e060, e07f]
[    0.549216] PCI: 0000:00:1d.2 reg 20 io port: [e040, e05f]
[    0.549306] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d4204800, d4204bff]
[    0.549368] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.549374] pci 0000:00:1d.7: PME# disabled
[    0.549610] PCI: 0000:00:1f.2 reg 10 io port: [e130, e137]
[    0.549618] PCI: 0000:00:1f.2 reg 14 io port: [e120, e123]
[    0.549626] PCI: 0000:00:1f.2 reg 18 io port: [e110, e117]
[    0.549635] PCI: 0000:00:1f.2 reg 1c io port: [e100, e103]
[    0.549643] PCI: 0000:00:1f.2 reg 20 io port: [e020, e03f]
[    0.549651] PCI: 0000:00:1f.2 reg 24 32bit mmio: [d4204000, d42047ff]
[    0.549689] pci 0000:00:1f.2: PME# supported from D3hot
[    0.549694] pci 0000:00:1f.2: PME# disabled
[    0.549722] PCI: 0000:00:1f.3 reg 10 64bit mmio: [d4205000, d42050ff]
[    0.549742] PCI: 0000:00:1f.3 reg 20 io port: [e000, e01f]
[    0.552109] PCI: 0000:01:00.0 reg 10 64bit mmio: [d2d20000, d2d23fff]
[    0.552122] PCI: 0000:01:00.0 reg 18 io port: [d000, d0ff]
[    0.552166] PCI: 0000:01:00.0 reg 30 32bit mmio: [d2d00000, d2d1ffff]
[    0.552198] pci 0000:01:00.0: supports D1
[    0.552200] pci 0000:01:00.0: supports D2
[    0.552202] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.552209] pci 0000:01:00.0: PME# disabled
[    0.552264] PCI: bridge 0000:00:1c.0 io port: [d000, dfff]
[    0.552269] PCI: bridge 0000:00:1c.0 32bit mmio: [d2d00000, d40fffff]
[    0.552339] PCI: bridge 0000:00:1c.1 io port: [c000, cfff]
[    0.552344] PCI: bridge 0000:00:1c.1 32bit mmio: [d1900000, d2cfffff]
[    0.552631] PCI: 0000:04:00.0 reg 10 64bit mmio: [d0500000, d0501fff]
[    0.552939] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.552972] pci 0000:04:00.0: PME# disabled
[    0.553027] PCI: bridge 0000:00:1c.2 io port: [b000, bfff]
[    0.553032] PCI: bridge 0000:00:1c.2 32bit mmio: [d0500000, d18fffff]
[    0.553090] PCI: 0000:05:03.0 reg 10 32bit mmio: [d4100000, d41007ff]
[    0.553149] pci 0000:05:03.0: PME# supported from D0 D3hot D3cold
[    0.553154] pci 0000:05:03.0: PME# disabled
[    0.553193] PCI: 0000:05:03.1 reg 10 32bit mmio: [d4100900, d41009ff]
[    0.553252] pci 0000:05:03.1: supports D1
[    0.553254] pci 0000:05:03.1: supports D2
[    0.553256] pci 0000:05:03.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.553262] pci 0000:05:03.1: PME# disabled
[    0.553299] PCI: 0000:05:03.2 reg 10 32bit mmio: [d4100800, d41008ff]
[    0.553358] pci 0000:05:03.2: supports D1
[    0.553359] pci 0000:05:03.2: supports D2
[    0.553361] pci 0000:05:03.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.553367] pci 0000:05:03.2: PME# disabled
[    0.553432] pci 0000:00:1e.0: transparent bridge
[    0.553440] PCI: bridge 0000:00:1e.0 32bit mmio: [d4100000, d41fffff]
[    0.553475] bus 00 -> node 0
[    0.553486] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.553829] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.553968] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.554124] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.554279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.573080] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.573080] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.573080] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.573080] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.573080] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.573080] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.573080] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.576137] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.576224] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.576224] pnp: PnP ACPI init
[    0.576224] ACPI: bus type pnp registered
[    0.592229] pnp: PnP ACPI: found 10 devices
[    0.592232] ACPI: ACPI bus type pnp unregistered
[    0.592235] PnPBIOS: Disabled by ACPI PNP
[    0.592250] PCI: Using ACPI for IRQ routing
[    0.600040] NET: Registered protocol family 8
[    0.600043] NET: Registered protocol family 20
[    0.600060] NetLabel: Initializing
[    0.600060] NetLabel:  domain hash size = 128
[    0.600060] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.600063] NetLabel:  unlabeled traffic allowed by default
[    0.600071] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.600077] hpet0: 4 64-bit timers, 14318180 Hz
[    0.602025] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.602028]    actual entries 65620
[    0.602110] AppArmor: AppArmor Filesystem Enabled
[    0.602138] ACPI: RTC can wake from S4
[    0.604040] Switched to high resolution mode on CPU 0
[    0.604528] Switched to high resolution mode on CPU 1
[    0.608023] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.608031] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.608034] system 00:05: ioport range 0x1000-0x100f has been reserved
[    0.608037] system 00:05: ioport range 0x800-0x803 has been reserved
[    0.608040] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.608042] system 00:05: ioport range 0x500-0x53f has been reserved
[    0.608045] system 00:05: ioport range 0x164e-0x164f has been reserved
[    0.608054] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.608057] system 00:09: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.608060] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.608063] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.608067] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.608070] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.608075] system 00:09: iomem range 0xfeb00000-0xfeb03fff has been reserved
[    0.608078] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.643157] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.643161] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.643169] pci 0000:00:1c.0:   MEM window: 0xd2d00000-0xd40fffff
[    0.643174] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.643182] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.643186] pci 0000:00:1c.1:   IO window: 0xc000-0xcfff
[    0.643193] pci 0000:00:1c.1:   MEM window: 0xd1900000-0xd2cfffff
[    0.643198] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.643206] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.643210] pci 0000:00:1c.2:   IO window: 0xb000-0xbfff
[    0.643217] pci 0000:00:1c.2:   MEM window: 0xd0500000-0xd18fffff
[    0.643222] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.643230] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.643232] pci 0000:00:1e.0:   IO window: disabled
[    0.643239] pci 0000:00:1e.0:   MEM window: 0xd4100000-0xd41fffff
[    0.643244] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.643263] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.643269] pci 0000:00:1c.0: setting latency timer to 64
[    0.643279] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.643285] pci 0000:00:1c.1: setting latency timer to 64
[    0.643295] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.643300] pci 0000:00:1c.2: setting latency timer to 64
[    0.643309] pci 0000:00:1e.0: setting latency timer to 64
[    0.643314] bus: 00 index 0 io port: [0, ffff]
[    0.643316] bus: 00 index 1 mmio: [0, ffffffff]
[    0.643318] bus: 01 index 0 io port: [d000, dfff]
[    0.643320] bus: 01 index 1 mmio: [d2d00000, d40fffff]
[    0.643323] bus: 01 index 2 mmio: [0, 0]
[    0.643324] bus: 01 index 3 mmio: [0, 0]
[    0.643326] bus: 02 index 0 io port: [c000, cfff]
[    0.643329] bus: 02 index 1 mmio: [d1900000, d2cfffff]
[    0.643331] bus: 02 index 2 mmio: [0, 0]
[    0.643333] bus: 02 index 3 mmio: [0, 0]
[    0.643335] bus: 04 index 0 io port: [b000, bfff]
[    0.643337] bus: 04 index 1 mmio: [d0500000, d18fffff]
[    0.643339] bus: 04 index 2 mmio: [0, 0]
[    0.643341] bus: 04 index 3 mmio: [0, 0]
[    0.643343] bus: 05 index 0 mmio: [0, 0]
[    0.643345] bus: 05 index 1 mmio: [d4100000, d41fffff]
[    0.643347] bus: 05 index 2 mmio: [0, 0]
[    0.643349] bus: 05 index 3 io port: [0, ffff]
[    0.643351] bus: 05 index 4 mmio: [0, ffffffff]
[    0.643358] NET: Registered protocol family 2
[    0.656053] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.656274] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.656599] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.656783] TCP: Hash tables configured (established 131072 bind 65536)
[    0.656786] TCP reno registered
[    0.664078] NET: Registered protocol family 1
[    0.664182] checking if image is initramfs... it is
[    1.348805] Freeing initrd memory: 8017k freed
[    1.349812] audit: initializing netlink socket (disabled)
[    1.349832] type=2000 audit(1236875471.348:1): initialized
[    1.355737] highmem bounce pool size: 64 pages
[    1.355743] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.357987] VFS: Disk quotas dquot_6.5.1
[    1.358065] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.358157] msgmni has been set to 1727
[    1.358275] io scheduler noop registered
[    1.358278] io scheduler anticipatory registered
[    1.358280] io scheduler deadline registered
[    1.358292] io scheduler cfq registered (default)
[    1.358305] pci 0000:00:02.0: Boot video device
[    1.358773] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.358825] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.358876] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.358916] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.358951] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.359061] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.359111] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.359160] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.359195] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.359231] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.359342] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.359392] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.359441] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.359478] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.359515] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.359838] isapnp: Scanning for PnP cards...
[    1.713859] isapnp: No Plug & Play device found
[    1.743825] hpet_resources: 0xfed00000 is busy
[    1.743922] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.746007] brd: module loaded
[    1.746072] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.746183] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.752340] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.755729] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.755734] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.755737] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.755740] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.755742] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.756071] mice: PS/2 mouse device common for all mice
[    1.756187] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.756217] rtc0: alarms up to one year, y3k, hpet irqs
[    1.756329] EISA: Probing bus 0 at eisa.0
[    1.756336] Cannot allocate resource for EISA slot 1
[    1.756366] EISA: Detected 0 cards.
[    1.756368] cpuidle: using governor ladder
[    1.756371] cpuidle: using governor menu
[    1.756872] TCP cubic registered
[    1.756900] Using IPI No-Shortcut mode
[    1.757059] registered taskstats version 1
[    1.757187]   Magic number: 1:58:540
[    1.757283] rtc_cmos 00:06: setting system clock to 2009-03-12 16:31:12 UTC (1236875472)
[    1.757286] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.757289] EDD information not available.
[    1.757521] Freeing unused kernel memory: 424k freed
[    1.757557] Write protecting the kernel text: 2580k
[    1.757583] Write protecting the kernel read-only data: 940k
[    1.785764] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.920563] fuse init (API version 7.9)
[    2.047067] ACPI: SSDT B7AE5C10, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.047582] ACPI: SSDT B7AE3810, 07A2 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.048475] Monitor-Mwait will be used to enter C-1 state
[    2.048478] Monitor-Mwait will be used to enter C-2 state
[    2.048481] Monitor-Mwait will be used to enter C-3 state
[    2.048669] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.048728] processor ACPI0007:00: registered as cooling_device0
[    2.048732] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.049423] ACPI: SSDT B7AE4D90, 00FD (r1  PmRef    ApIst     3000 INTL 20051117)
[    2.049922] ACPI: SSDT B7AE2F90, 0047 (r1  PmRef    ApCst     3000 INTL 20051117)
[    2.050930] Marking TSC unstable due to TSC halts in idle
[    2.051117] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.051162] processor ACPI0007:01: registered as cooling_device1
[    2.051166] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.171144] thermal LNXTHERM:01: registered as thermal_zone0
[    2.174519] ACPI: Thermal Zone [TZ00] (57 C)
[    2.184083] thermal LNXTHERM:02: registered as thermal_zone1
[    2.187036] ACPI: Thermal Zone [TZ01] (57 C)
[    2.419714] usbcore: registered new interface driver usbfs
[    2.419742] usbcore: registered new interface driver hub
[    2.419775] usbcore: registered new device driver usb
[    2.423026] USB Universal Host Controller Interface driver v3.0
[    2.423069] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.423078] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.423082] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.423128] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.423166] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e0e0
[    2.423302] usb usb1: configuration #1 chosen from 1 choice
[    2.423329] hub 1-0:1.0: USB hub found
[    2.423336] hub 1-0:1.0: 2 ports detected
[    2.488126] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.523164] No dock devices found.
[    2.525982] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.525992] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.525996] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.526020] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.526056] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e0c0
[    2.526144] usb usb2: configuration #1 chosen from 1 choice
[    2.526172] hub 2-0:1.0: USB hub found
[    2.526178] hub 2-0:1.0: 2 ports detected
[    2.546019] SCSI subsystem initialized
[    2.584403] libata version 3.00 loaded.
[    2.628336] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.628347] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.628352] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.628377] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.628414] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e0a0
[    2.628509] usb usb3: configuration #1 chosen from 1 choice
[    2.628536] hub 3-0:1.0: USB hub found
[    2.628543] hub 3-0:1.0: 2 ports detected
[    2.732394] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.732412] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.732416] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.732445] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.736335] ehci_hcd 0000:00:1a.7: debug port 1
[    2.736343] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.736351] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd4204c00
[    2.752555] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.752774] usb usb4: configuration #1 chosen from 1 choice
[    2.752802] hub 4-0:1.0: USB hub found
[    2.752811] hub 4-0:1.0: 6 ports detected
[    2.960275] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.960286] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.960291] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.960316] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.960354] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    2.960442] usb usb5: configuration #1 chosen from 1 choice
[    2.960469] hub 5-0:1.0: USB hub found
[    2.960475] hub 5-0:1.0: 2 ports detected
[    3.000059] Clocksource tsc unstable (delta = -154322088 ns)
[    3.064225] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.064233] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.064238] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.064260] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.064292] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[    3.064375] usb usb6: configuration #1 chosen from 1 choice
[    3.064403] hub 6-0:1.0: USB hub found
[    3.064409] hub 6-0:1.0: 2 ports detected
[    3.120089] usb 4-2: new high speed USB device using ehci_hcd and address 2
[    3.255490] usb 4-2: configuration #1 chosen from 1 choice
[    3.272176] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.272184] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.272188] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.272211] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.272246] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e040
[    3.272332] usb usb7: configuration #1 chosen from 1 choice
[    3.272358] hub 7-0:1.0: USB hub found
[    3.272364] hub 7-0:1.0: 2 ports detected
[    3.376290] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.376304] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.376308] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.376334] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.380246] ehci_hcd 0000:00:1d.7: debug port 1
[    3.380253] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.380259] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd4204800
[    3.388062] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    3.396577] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.396665] usb usb8: configuration #1 chosen from 1 choice
[    3.396692] hub 8-0:1.0: USB hub found
[    3.396698] hub 8-0:1.0: 6 ports detected
[    3.452114] hub 6-0:1.0: unable to enumerate USB device on port 2
[    3.604238] sky2 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.604249] sky2 0000:01:00.0: setting latency timer to 64
[    3.604273] sky2 0000:01:00.0: v1.22 addr 0xd2d20000 irq 16 Yukon-2 EC Ultra rev 3
[    3.605284] sky2 eth0: addr 00:1d:ba:26:3b:fc
[    3.605422] ahci 0000:00:1f.2: version 3.0
[    3.605433] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.605542] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    3.605545] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    3.605551] ahci 0000:00:1f.2: setting latency timer to 64
[    3.605710] scsi0 : ahci
[    3.606083] scsi1 : ahci
[    3.606150] scsi2 : ahci
[    3.607281] scsi3 : ahci
[    3.607378] ata1: SATA max UDMA/133 abar m2048@0xd4204000 port 0xd4204100 irq 219
[    3.607383] ata2: SATA max UDMA/133 abar m2048@0xd4204000 port 0xd4204180 irq 219
[    3.607385] ata3: DUMMY
[    3.607387] ata4: DUMMY
[    3.924099] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.925232] ata1.00: ACPI cmd f5/00:00:00:00:00:00 filtered out
[    3.925238] ata1.00: ATA-8: ST9250827AS, 3.AAB, max UDMA/133
[    3.925241] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.926529] ata1.00: ACPI cmd f5/00:00:00:00:00:00 filtered out
[    3.926532] ata1.00: ACPI cmd f5/00:00:00:00:00:00 filtered out
[    3.926546] ata1.00: configured for UDMA/133
[    4.112083] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    4.285468] usb 6-2: configuration #1 chosen from 1 choice
[    4.304932] usbcore: registered new interface driver hiddev
[    4.308595] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input2
[    4.309457] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[    4.314458] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input3
[    4.314698] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2
[    4.314720] usbcore: registered new interface driver usbhid
[    4.314723] usbhid: v2.6:USB HID core driver
[    4.664099] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.677556] ata2.00: ATAPI: Optiarc DVD RW AD-7560S, SS02, max UDMA/100, ATAPI AN
[    4.691981] ata2.00: configured for UDMA/100
[    4.704212] scsi 0:0:0:0: Direct-Access     ATA      ST9250827AS      3.AA PQ: 0 ANSI: 5
[    4.705383] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SS02 PQ: 0 ANSI: 5
[    4.705470] ohci1394 0000:05:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.758179] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[d4100000-d41007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.771610] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.771648] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.788898] Driver 'sr' needs updating - please use bus_type methods
[    4.793190] Driver 'sd' needs updating - please use bus_type methods
[    4.793279] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.793295] sd 0:0:0:0: [sda] Write Protect is off
[    4.793297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.793321] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.793380] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.793395] sd 0:0:0:0: [sda] Write Protect is off
[    4.793397] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.793421] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.793425]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.797943] Uniform CD-ROM driver Revision: 3.20
[    4.798019] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.811692]  sda1 sda2 < sda5 >
[    4.842006] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.016677] PM: Starting manual resume from disk
[    5.016680] PM: Resume from partition 8:5
[    5.016682] PM: Checking hibernation image.
[    5.016881] PM: Resume from disk failed.
[    5.079193] kjournald starting.  Commit interval 5 seconds
[    5.079222] EXT3-fs: mounted filesystem with ordered data mode.
[    6.032138] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460302cad42b]
[   12.214874] udevd version 124 started
[   12.581099] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.649234] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.658127] Linux agpgart interface v0.103
[   12.761304] agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset
[   12.761841] agpgart-intel 0000:00:00.0: detected 131068K stolen memory
[   12.769747] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   12.794444] ACPI: Battery Slot [BAT0] (battery present)
[   12.796383] ACPI: AC Adapter [ADP1] (on-line)
[   12.796463] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   12.798111] ACPI: Lid Switch [LID0]
[   12.798181] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.816041] ACPI: Power Button (CM) [PWRB]
[   13.038822] sony-laptop: Sony Notebook Control Driver v0.6.
[   13.041588] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/SNY5001:00/input/input6
[   13.056121] input: Sony Vaio Jogdial as /devices/virtual/input/input7
[   13.088822] sony-laptop: detected Sony Vaio N Series
[   13.103552] acpi device:16: registered as cooling_device2
[   13.103937] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:14/input/input8
[   13.120035] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.184071] cfg80211: Using static regulatory domain info
[   13.184074] cfg80211: Regulatory domain: US
[   13.184076] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.184079] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   13.184082] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.184084] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.184087] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.184089] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.184092] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   13.184094] cfg80211: Calling CRDA for country: US
[   13.417516] sdhci: Secure Digital Host Controller Interface driver
[   13.417519] sdhci: Copyright(c) Pierre Ossman
[   13.559529] sdhci-pci 0000:05:03.1: SDHCI controller found [1180:0822] (rev 22)
[   13.559547] sdhci-pci 0000:05:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.560565] sdhci-pci 0000:05:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   13.562626] mmc0: SDHCI controller on PCI [0000:05:03.1] using DMA
[   13.630453] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   13.693544] Linux video capture interface: v2.00
[   13.736176] mmc0: new SDHC card at address 2351
[   13.959324] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:18b3)
[   13.960147] input: UVC Camera (05ca:18b3) as /devices/pci0000:00/0000:00:1a.7/usb4/4-2/4-2:1.0/input/input10
[   13.973134] usbcore: registered new interface driver uvcvideo
[   13.973139] USB Video Class driver (v0.1.0)
[   14.033776] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   14.033779] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   14.033879] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.033916] iwlagn 0000:04:00.0: setting latency timer to 64
[   14.033984] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   14.056866] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.058232] iwlagn 0000:04:00.0: PCI INT A disabled
[   14.059612] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.413628] mmcblk0: mmc0:2351 SD04G 3870720KiB 
[   14.413677]  mmcblk0: p1
[   14.535073] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   14.596014] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input11
[   15.159560] lp: driver loaded but no devices found
[   15.311052] Adding 8723252k swap on /dev/sda5.  Priority:-1 extents:1 across:8723252k
[   15.847678] EXT3 FS on sda1, internal journal
[   16.926212] type=1505 audit(1236875487.898:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4198
[   17.087745] type=1505 audit(1236875488.058:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4203
[   17.087993] type=1505 audit(1236875488.058:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4203
[   17.239112] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.953087] ACPI: WMI: Mapper loaded
[   18.876900] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.951083] apm: BIOS not found.
[   19.155961] ppdev: user-space parallel port driver
[   20.195586] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   20.197004] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
[   20.197460] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   20.197466] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   20.197468] sonypi: device allocated minor is 60
[   20.197743] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input12
[   20.252152] input: Sony Vaio Keys as /devices/platform/sonypi/input/input13
[   21.288042] ACPI: EC: missing confirmations, switch off interrupt mode.
[   21.329457] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
[   21.369675] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 664)
[   21.409881] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 666)
[   21.450085] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
[   21.759008] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   21.759015] vboxdrv: Successfully done.
[   21.759018] vboxdrv: Found 2 processor cores.
[   21.759132] vboxdrv: fAsync=0 offMin=0x2a8 offMax=0x1130
[   21.759138] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   21.759141] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   23.546428] Bluetooth: Core ver 2.13
[   23.548342] NET: Registered protocol family 31
[   23.548352] Bluetooth: HCI device and connection manager initialized
[   23.548360] Bluetooth: HCI socket layer initialized
[   23.570889] Bluetooth: L2CAP ver 2.11
[   23.570901] Bluetooth: L2CAP socket layer initialized
[   23.585919] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.585932] Bluetooth: BNEP filters: protocol multicast
[   23.613542] Bridge firewalling registered
[   23.637438] Bluetooth: SCO (Voice Link) ver 0.6
[   23.637450] Bluetooth: SCO socket layer initialized
[   23.787895] Bluetooth: RFCOMM socket layer initialized
[   23.789108] Bluetooth: RFCOMM TTY layer initialized
[   23.789119] Bluetooth: RFCOMM ver 1.10
[   27.568426] [drm] Initialized drm 1.1.0 20060810
[   27.575047] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.575059] pci 0000:00:02.0: setting latency timer to 64
[   27.575391] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   27.924696] sky2 eth0: enabling interface
[   27.929727] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   27.929817] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   27.929978] firmware: requesting lbm-iwlwifi-5000-1.ucode
[   27.998169] iwlagn loaded firmware version 5.4.1.16
[   28.159237] Registered led device: iwl-phy0:radio
[   28.159900] Registered led device: iwl-phy0:assoc
[   28.160495] Registered led device: iwl-phy0:RX
[   28.161757] Registered led device: iwl-phy0:TX
[   28.507536] set status page addr 0x07fff000
[   28.664036] iwlagn: Error sending REPLY_ADD_STA: time out after 500ms.
[   28.664388] iwlagn: Error: Response NULL in 'REPLY_ADD_STA'
[   28.780605] NET: Registered protocol family 17
[   29.759159] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   30.459558] wlan0: authenticate with AP 00:1a:6c:88:5b:a0
[   30.461124] wlan0: authenticated
[   30.461138] wlan0: associate with AP 00:1a:6c:88:5b:a0
[   30.463844] wlan0: RX AssocResp from 00:1a:6c:88:5b:a0 (capab=0x421 status=0 aid=108)
[   30.463857] wlan0: associated
[   30.522986] wlan0: disassociating by local choice (reason=3)
[   35.130363] NET: Registered protocol family 10
[   35.132896] lo: Disabled Privacy Extensions
[   35.137077] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.400123] eth0: no IPv6 routers present
[   51.680184] wlan0: deauthenticated (Reason: 2)
[   76.051237] CPU0 attaching NULL sched-domain.
[   76.051257] CPU1 attaching NULL sched-domain.
[   76.053176] CPU0 attaching sched-domain:
[   76.053188]  domain 0: span 0-1 level MC
[   76.053196]   groups: 0 1
[   76.053210] CPU1 attaching sched-domain:
[   76.053215]  domain 0: span 0-1 level MC
[   76.053222]   groups: 1 0
[   77.323822] wlan0: authenticate with AP 00:1a:6c:88:5b:a0
[   77.325387] wlan0: authenticated
[   77.325393] wlan0: associate with AP 00:1a:6c:88:5b:a0
[   77.327323] wlan0: RX ReassocResp from 00:1a:6c:88:5b:a0 (capab=0x421 status=0 aid=109)
[   77.327327] wlan0: associated
[   77.331513] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.644053] wlan0: no IPv6 routers present
[ 4693.588408] sky2 eth0: disabling interface
[ 4693.803185] wlan0: direct probe to AP 00:1a:6c:88:5b:a0 try 1
[ 4693.806032] wlan0 direct probe responded
[ 4693.806048] wlan0: authenticate with AP 00:1a:6c:88:5b:a0
[ 4693.807530] wlan0: authenticated
[ 4693.807544] wlan0: associate with AP 00:1a:6c:88:5b:a0
[ 4693.812074] wlan0: deauthenticating by local choice (reason=3)
[ 4693.832421] iwlagn 0000:04:00.0: PCI INT A disabled
[ 4694.654925] PM: Syncing filesystems ... done.
[ 4694.656780] PM: Preparing system for mem sleep
[ 4694.657289] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 4694.657972] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 4694.658011] PM: Entering mem sleep
[ 4694.658013] Suspending console(s) (use no_console_suspend to debug)
[ 4694.658921] pci 0000:00:02.0: PCI INT A disabled
[ 4694.712260] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 664)
[ 4694.752451] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 666)
[ 4694.756021] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 4695.053195] sd 0:0:0:0: [sda] Stopping disk
[ 4695.917448] ACPI handle has no context!
[ 4695.917525] mmc0: card 2351 removed
[ 4695.918088] MMC: killing requests for dead queue
[ 4695.920205] ACPI handle has no context!
[ 4695.920211] sdhci-pci 0000:05:03.1: PCI INT B disabled
[ 4695.920218] ACPI handle has no context!
[ 4695.937118] ACPI handle has no context!
[ 4696.032241] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 4696.048134] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 4696.048184] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 4696.048235] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 4696.048525] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 4696.064133] uhci_hcd 0000:00:1a.2: PCI INT C disabled
[ 4696.064184] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 4696.064235] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 4696.064329] PM: suspend devices took 1.408 seconds
[ 4696.064582] ACPI: Preparing to enter system sleep state S3
[ 4696.065595] Disabling non-boot CPUs ...
[ 4696.168019] CPU 1 is now offline
[ 4696.168022] SMP alternatives: switching to UP code
[ 4696.177559] CPU0 attaching NULL sched-domain.
[ 4696.177562] CPU1 attaching NULL sched-domain.
[ 4696.177600] CPU0 attaching NULL sched-domain.
[ 4696.177754] CPU1 is down
[ 4696.177868] Extended CMOS year: 2000
[ 4696.177868] Back to C!
[ 4696.177868] Extended CMOS year: 2000
[ 4696.177868] Enabling non-boot CPUs ...
[ 4696.177868] SMP alternatives: switching to SMP code
[ 4696.187991] Booting processor 1/1 ip 6000
[ 4696.069698] Initializing CPU#1
[ 4696.069698] Calibrating delay using timer specific routine.. 3987.15 BogoMIPS (lpj=7974315)
[ 4696.069698] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 4696.069698] CPU: L2 cache: 2048K
[ 4696.069698] CPU: Physical Processor ID: 0
[ 4696.069698] CPU: Processor Core ID: 1
[ 4696.276457] CPU1: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d
[ 4696.276496] CPU0 attaching NULL sched-domain.
[ 4696.276568] CPU0 attaching sched-domain:
[ 4696.276571]  domain 0: span 0-1 level MC
[ 4696.276573]   groups: 0 1
[ 4696.276577] CPU1 attaching sched-domain:
[ 4696.276579]  domain 0: span 0-1 level MC
[ 4696.276581]   groups: 1 0
[ 4696.277017] CPU1 is up
[ 4696.277019] ACPI: Waking up from system sleep state S3
[ 4696.280017] Switched to high resolution mode on CPU 1
[ 4696.478081] sony-laptop: unable to restore brightness level<5>sony-laptop: detected Sony Vaio N Series
[ 4696.496377] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 4696.547924] pci 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900003)
[ 4696.554670] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x4, writing 0xd0400004)
[ 4696.554676] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 4696.554689] uhci_hcd 0000:00:1a.0: enabling device (0000 -> 0001)
[ 4696.554696] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4696.554703] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 4696.554714] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 4696.554729] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x8 (was 0x1, writing 0xe0e1)
[ 4696.554775] usb usb1: root hub lost power or was reset
[ 4696.554796] uhci_hcd 0000:00:1a.1: enabling device (0000 -> 0001)
[ 4696.554800] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 4696.554806] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 4696.554817] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 4696.554832] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x8 (was 0x1, writing 0xe0c1)
[ 4696.554876] usb usb2: root hub lost power or was reset
[ 4696.554894] uhci_hcd 0000:00:1a.2: enabling device (0000 -> 0001)
[ 4696.554898] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[ 4696.554905] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 4696.554916] uhci_hcd 0000:00:1a.2: restoring config space at offset 0xf (was 0x300, writing 0x305)
[ 4696.554931] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x8 (was 0x1, writing 0xe0a1)
[ 4696.554976] usb usb3: root hub lost power or was reset
[ 4696.568086] ehci_hcd 0000:00:1a.7: enabling device (0000 -> 0002)
[ 4696.568090] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[ 4696.568097] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 4696.568115] ehci_hcd 0000:00:1a.7: restoring config space at offset 0xf (was 0x300, writing 0x305)
[ 4696.568136] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x4 (was 0x0, writing 0xd4204c00)
[ 4696.568181] pci 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[ 4696.568202] pci 0000:00:1b.0: restoring config space at offset 0x4 (was 0xc0000004, writing 0xd4200004)
[ 4696.568207] pci 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4696.568242] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 4696.568264] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 4696.568271] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 4696.568314] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[ 4696.568333] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20b)
[ 4696.568355] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 4696.568362] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 4696.568405] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[ 4696.568423] pcieport-driver 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[ 4696.568445] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 4696.568452] pcieport-driver 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 4696.568495] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[ 4696.568504] uhci_hcd 0000:00:1d.0: enabling device (0000 -> 0001)
[ 4696.568508] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 4696.568514] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 4696.568525] uhci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 4696.568540] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x8 (was 0x1, writing 0xe081)
[ 4696.568584] usb usb5: root hub lost power or was reset
[ 4696.568604] uhci_hcd 0000:00:1d.1: enabling device (0000 -> 0001)
[ 4696.568608] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 4696.568614] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 4696.568626] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x205)
[ 4696.568640] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0xe061)
[ 4696.568685] usb usb6: root hub lost power or was reset
[ 4696.568719] uhci_hcd 0000:00:1d.2: enabling device (0000 -> 0001)
[ 4696.568723] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 4696.568730] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 4696.568741] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x30b)
[ 4696.568755] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0xe041)
[ 4696.568800] usb usb7: root hub lost power or was reset
[ 4696.584081] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[ 4696.584085] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 4696.584092] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 4696.584110] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 4696.584132] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x4 (was 0x0, writing 0xd4204800)
[ 4696.584189] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 4696.584206] pci 0000:00:1e.0: setting latency timer to 64
[ 4696.600118] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 4696.600161] ahci 0000:00:1f.2: setting latency timer to 64
[ 4696.616115] sky2 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 4696.616127] sky2 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xd2d00000)
[ 4696.616148] sky2 0000:01:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xd001)
[ 4696.616158] sky2 0000:01:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd2d20004)
[ 4696.616165] sky2 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4696.616175] sky2 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 4696.648089] ohci1394 0000:05:03.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010b)
[ 4696.648113] ohci1394 0000:05:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xd4100000)
[ 4696.648119] ohci1394 0000:05:03.0: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 4696.648126] ohci1394 0000:05:03.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 4696.700758] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[d4100000-d41007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 4696.720091] sdhci-pci 0000:05:03.1: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 4696.720114] sdhci-pci 0000:05:03.1: restoring config space at offset 0x4 (was 0x0, writing 0xd4100900)
[ 4696.720119] sdhci-pci 0000:05:03.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 4696.720126] sdhci-pci 0000:05:03.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 4696.720142] sdhci-pci 0000:05:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 4696.720145] sdhci-pci 0000:05:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[ 4696.721164] pci 0000:05:03.2: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 4696.721186] pci 0000:05:03.2: restoring config space at offset 0x4 (was 0x0, writing 0xd4100800)
[ 4696.721191] pci 0000:05:03.2: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[ 4696.721198] pci 0000:05:03.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100006)
[ 4696.899732] mmc0: new SDHC card at address 2351
[ 4696.899757] mmc mmc0:2351: parent mmc0 should not be sleeping
[ 4696.899897] mmcblk1: mmc0:2351 SD04G 3870720KiB 
[ 4696.899939]  mmcblk1: p1
[ 4696.920080] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4696.947857] ata2.00: configured for UDMA/100
[ 4696.960077] ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
[ 4696.960079] ata2: irq_stat 0x40000008
[ 4697.248047] usb 6-2: reset full speed USB device using uhci_hcd and address 3
[ 4697.402138] sd 0:0:0:0: [sda] Starting disk
[ 4698.104049] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4698.193142] ata1.00: ACPI cmd f5/00:00:00:00:00:00 filtered out
[ 4698.193144] ata1.00: ACPI cmd f5/00:00:00:00:00:00 filtered out
[ 4698.193147] ata1.00: ACPI cmd f5/00:00:00:00:00:00 filtered out
[ 4698.194075] ACPI Error (dsopcode-0595): Field [CMDX] at 224 exceeds Buffer [SCBF] size 168 (bits) [20080609]
[ 4698.194080] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SATA.GTFB] (Node f744e108), AE_AML_BUFFER_LIMIT
[ 4698.194130] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SATA.SPT0._SDD] (Node f744e048), AE_AML_BUFFER_LIMIT
[ 4698.194179] ata1.00: ACPI _SDD failed (AE 0x300c)
[ 4698.194181] ata1.00: revalidation failed (errno=-5)
[ 4703.424051] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 4703.424907] ACPI Error (dsopcode-0595): Field [CMDX] at 224 exceeds Buffer [SCBF] size 168 (bits) [20080609]
[ 4703.424912] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SATA.GTFB] (Node f744e108), AE_AML_BUFFER_LIMIT
[ 4703.424962] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SATA.SPT0._SDD] (Node f744e048), AE_AML_BUFFER_LIMIT
[ 4703.425011] ata1.00: ACPI _SDD failed (AE 0x300c)
[ 4703.425013] ata1.00: ACPI: failed the second time, disabled
[ 4703.425499] ata1.00: configured for UDMA/133
[ 4703.440079] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 4703.440095] sd 0:0:0:0: [sda] Write Protect is off
[ 4703.440097] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4703.440123] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4703.440149] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 4703.440163] sd 0:0:0:0: [sda] Write Protect is off
[ 4703.440165] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4703.440190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4704.488039] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 4704.531131] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
[ 4704.571383] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 664)
[ 4704.611621] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call2 (line 666)
[ 4704.651914] sonypi command failed at /build/buildd/linux-2.6.27/drivers/char/sonypi.c : sonypi_call1 (line 653)
[ 4704.664063] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 4704.664068] pci 0000:00:02.0: setting latency timer to 64
[ 4704.665693] PM: resume devices took 8.188 seconds
[ 4704.665699] ------------[ cut here ]------------
[ 4704.665700] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
[ 4704.665703] Modules linked in: ipv6 af_packet i915 drm binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth vboxdrv sonypi ppdev acpi_cpufreq cpufreq_conservative cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand freq_table wmi pci_slot sbs container sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport mmc_block arc4 ecb crypto_blkcipher iwlagn joydev uvcvideo iwlcore psmouse rfkill compat_ioctl32 videodev evdev serio_raw pcspkr sdhci_pci v4l1_compat sdhci led_class mmc_core lbm_cw_mac80211 lbm_cw_cfg80211 video output sony_laptop button intel_agp ac battery agpgart shpchp pci_hotplug ext3 jbd mbcache sd_mod crc_t10dif sr_mod cdrom sg usbhid hid ahci libata scsi_mod ohci1394 dock ieee1394 ehci_hcd sky2 uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 4704.665753] Pid: 28718, comm: pm-suspend Not tainted 2.6.27-11-generic #1
[ 4704.665756]  [<c037d236>] ? printk+0x1d/0x1f
[ 4704.665760]  [<c0131e99>] warn_on_slowpath+0x59/0x90
[ 4704.665764]  [<c014d305>] ? sched_clock_cpu+0xd5/0x170
[ 4704.665768]  [<c014c15f>] ? down_trylock+0x2f/0x40
[ 4704.665771]  [<c0132572>] ? try_acquire_console_sem+0x12/0x40
[ 4704.665775]  [<c024ed00>] ? kobject_put+0x20/0x50
[ 4704.665778]  [<c015d2b4>] suspend_test_finish+0x74/0x80
[ 4704.665782]  [<c015d3a6>] suspend_devices_and_enter+0xe6/0x190
[ 4704.665785]  [<c015d621>] enter_state+0xd1/0x100
[ 4704.665787]  [<c015d6d5>] state_store+0x85/0xd0
[ 4704.665790]  [<c015d650>] ? state_store+0x0/0xd0
[ 4704.665792]  [<c024ebc4>] kobj_attr_store+0x24/0x30
[ 4704.665795]  [<c01ffac7>] sysfs_write_file+0x97/0x100
[ 4704.665799]  [<c01b2760>] vfs_write+0xa0/0x110
[ 4704.665802]  [<c01ffa30>] ? sysfs_write_file+0x0/0x100
[ 4704.665805]  [<c01b28a2>] sys_write+0x42/0x70
[ 4704.665807]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[ 4704.665810]  [<c0370000>] ? enable_nonboot_cpus+0x60/0xc0
[ 4704.665814]  =======================
[ 4704.665815] ---[ end trace 287cbc341e8a4892 ]---
[ 4704.666019] PM: Finishing wakeup.
[ 4704.666021] Restarting tasks ... done.
[ 4708.217152] sky2 eth0: enabling interface
[ 4708.222212] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4708.253777] iwlagn 0000:04:00.0: enabling device (0000 -> 0002)
[ 4708.253824] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 4708.253950] iwlagn 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 4708.254076] iwlagn 0000:04:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd0500004)
[ 4708.254120] iwlagn 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4708.254168] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[ 4708.283465] Registered led device: iwl-phy0:radio
[ 4708.283519] Registered led device: iwl-phy0:assoc
[ 4708.283560] Registered led device: iwl-phy0:RX
[ 4708.283605] Registered led device: iwl-phy0:TX
[ 4708.301887] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4708.326855] wlan0: direct probe to AP 00:1a:6c:88:5b:a0 try 1
[ 4708.327291] wlan0: direct probe to AP 00:1a:6c:88:5b:a0 try 1
[ 4708.330051] wlan0 direct probe responded
[ 4708.330057] wlan0: authenticate with AP 00:1a:6c:88:5b:a0
[ 4708.331563] wlan0: authenticated
[ 4708.331569] wlan0: associate with AP 00:1a:6c:88:5b:a0
[ 4708.334863] wlan0: RX AssocResp from 00:1a:6c:88:5b:a0 (capab=0x421 status=0 aid=84)
[ 4708.334869] wlan0: associated
[ 4708.347480] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4708.362923] wlan0: disassociating by local choice (reason=3)
[ 4708.364707] wlan0: deauthenticated (Reason: 2)
[ 4709.885153] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 4709.886147] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4713.386209] wlan0: authenticate with AP 00:1a:6c:88:5b:a0
[ 4713.387857] wlan0: authenticated
[ 4713.387870] wlan0: associate with AP 00:1a:6c:88:5b:a0
[ 4713.389843] wlan0: RX ReassocResp from 00:1a:6c:88:5b:a0 (capab=0x421 status=0 aid=85)
[ 4713.389854] wlan0: associated
[ 4718.444070] wlan0: no IPv6 routers present
[ 4720.304065] eth0: no IPv6 routers present
```




lspci gives:


```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
05:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
```



Again, any help would be greatly appreciated.

---

### Post by markbuntu on 2009-03-12
Troubleshooting help is here, including alsa reinstallation instructions and help with the ICH9 audio chip(see HDA for that).

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Once you get your sound set up properly skype should work with just a few changes in the skype configuration but get your sound working properly first.

---

### Post by JordBrow on 2009-03-12
Thanks for the reply.  I've been through this page quickly before and didn't find anything that helps.  On a second more thorough pass through I get to "Getting Information From Your Machine" section where it says to enter:

lsusb
lspci
aplay -l
arecord -l
cat /proc/asound/cards
cat /proc/asound/modules

I don't see in the documentation about what to do when:

aplay -l   gives "aplay: device_list:215: no soundcards found..."
arecord -l gives "arecord: device_list:215: no soundcards found..."

and 

cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory

Any other help would again be appreciated.  To me it looks like the sound card has been completely dropped from the system.  But what do I know, I'm the one asking questions here.  I'm really out in the dark and don't know what to do or where to start.  

Here is the output for:

lsusb

```
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 05ca:18b3 Ricoh Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c526 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

and lspci

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
05:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

```

---

### Post by markbuntu on 2009-03-12
Help for the intel ICH9, which is your sound chip can be found in the drivers/hda section of that link I gave you

---

### Post by JordBrow on 2009-03-12
ok, now been through drivers/hda section and tried everything that looked like it went with a sony VGN-NS140D laptop:

options snd-hda-intel model=sony     -> from the list linked in the thread.
options snd-hda-intel model=vaio     -> also from the list linked in the thread
options snd-hda-intel sony-assamd    -> from the /user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz  on my computer.

am I not using these correctly?  I checked System>Preferences>Sound

All except Default Mixer Tracks are selected to ALSA - Advanced Linux Sound Architecture.  When I try pressing the test button beside I get the following error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Not sure if this helps at all.  Again not sure where to go from here. 

Thanks for your help in advance.

---

### Post by JordBrow on 2009-03-13
ok, how about this, I restarted and used the older kernel.  
Now sound works using: HDA Intel ALC262 Analog (OSS).

Is it be possible to recompile the newer kernel to see if the sound is restored? How would I go about doing that if its possible?

Thanks

---

### Post by JordBrow on 2009-03-13
Ok, its back to where I started, sound works but no microphone in skype, I'm much happier now :-) 

I ended up having to reinstall the kernel:

sudo apt-get install --reinstall linux-image-2.6.27-11-generic

And everythings good.

Thanks for your help, I appreciate your time.

---

