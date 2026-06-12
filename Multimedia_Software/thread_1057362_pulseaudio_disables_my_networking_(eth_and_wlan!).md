---
title: "pulseaudio disables my networking (eth and wlan!)"
date: 2009-02-01
forum: Multimedia Software
---

### Post by KhaaL on 2009-02-01
(this is a continuation of [this thread]("http://ubuntuforums.org/showthread.php?p=6657226#post6657226").

I've been plauged by a problem for a long which appears and dissapears mysteriosly, and today i've managed to find a way to reproduce it. The problem is that pulseaudio (and perhaps alsa?) which knocks my networking off. By that i mean that the host to a ip adress cant be resolved - but i still have a ip and do get an IP when i renew it. The only way to get my networking back is by killing pulseaudio ($pulseaudio -k) and run my apps through OSS. I haven't tried ALSA yet as i just found out that pulseaudio was the root to the problem.

I have my full dmesg here:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fef0000 (usable)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fef3000 - 000000007ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7fef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3781f000 - 37fefc20
[    0.000000] ACPI: RSDP 000F7760, 0024 (r2 HPQOEM)
[    0.000000] ACPI: XSDT 7FEF30C0, 0054 (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEFA3C0, 00F4 (r3 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEF3280, 70EB (r1 HPQOEM SLIC-CPC     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7FEF0000, 0040
[    0.000000] ACPI: SLIC 7FEFA5C0, 0176 (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 7FEFA780, 02CC (r1 HPQOEM SLIC-CPC        1  LTP        1)
[    0.000000] ACPI: HPET 7FEFAAC0, 0038 (r1 HPQOEM SLIC-CPC 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 7FEFAB40, 003C (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEFA500, 007C (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781f000 - 0037fefc20]          RAMDISK ==> [003781f000 - 0037fefc20]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f5b80] 000f5b80
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fef0
[    0.000000] On node 0 totalpages: 523903
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292050 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519297
[    0.000000] Kernel command line: root=UUID=e3bb9993-d18b-4125-a107-c930e85311e1 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2805.799 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062368k/2096064k available (2576k kernel code, 32264k reserved, 1165k data, 424k init, 1178560k highmem)
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
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5611.59 BogoMIPS (lpj=11223196)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017169] ACPI: Core revision 20080609
[    0.019093] ACPI: Checking initramfs for custom DSDT
[    0.263694] ENABLING IO-APIC IRQs
[    0.263914] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.303615] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ stepping 03
[    0.304019] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5611.73 BogoMIPS (lpj=11223474)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.388130] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ stepping 03
[    0.388151] Brought up 2 CPUs
[    0.388153] Total of 2 processors activated (11223.33 BogoMIPS).
[    0.388192] CPU0 attaching sched-domain:
[    0.388194]  domain 0: span 0-1 level CPU
[    0.388196]   groups: 0 1
[    0.388200] CPU1 attaching sched-domain:
[    0.388202]  domain 0: span 0-1 level CPU
[    0.388204]   groups: 1 0
[    0.388251] net_namespace: 840 bytes
[    0.388251] Booting paravirtualized kernel on bare hardware
[    0.388251] Time: 16:54:39  Date: 02/01/09
[    0.388251] NET: Registered protocol family 16
[    0.388251] EISA bus registered
[    0.388251] ACPI: bus type pci registered
[    0.388251] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.388251] PCI: MCFG area at f0000000 reserved in E820
[    0.388251] PCI: Using MMCONFIG for extended config space
[    0.388251] PCI: Using configuration type 1 for base access
[    0.388959] ACPI: EC: Look up EC in DSDT
[    0.399622] ACPI: Interpreter enabled
[    0.399624] ACPI: (supports S0 S1 S3 S4 S5)
[    0.399637] ACPI: Using IOAPIC for interrupt routing
[    0.408994] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.408994] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.408994] pci 0000:00:02.0: PME# disabled
[    0.408994] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.408994] pci 0000:00:04.0: PME# disabled
[    0.408994] PCI: 0000:00:0a.1 reg 20 io port: [4c00, 4c3f]
[    0.408994] PCI: 0000:00:0a.1 reg 24 io port: [4c40, 4c7f]
[    0.408994] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.408994] pci 0000:00:0a.1: PME# disabled
[    0.408994] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.408994] pci 0000:00:0b.0: supports D1
[    0.408994] pci 0000:00:0b.0: supports D2
[    0.408994] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.408994] pci 0000:00:0b.0: PME# disabled
[    0.408994] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.408994] pci 0000:00:0b.1: supports D1
[    0.408994] pci 0000:00:0b.1: supports D2
[    0.408994] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.408994] pci 0000:00:0b.1: PME# disabled
[    0.408994] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]
[    0.408994] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.408994] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.408994] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.408994] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.408994] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.408994] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]
[    0.408994] PCI: 0000:00:0f.0 reg 10 io port: [9e0, 9e7]
[    0.408994] PCI: 0000:00:0f.0 reg 14 io port: [be0, be3]
[    0.408994] PCI: 0000:00:0f.0 reg 18 io port: [960, 967]
[    0.408994] PCI: 0000:00:0f.0 reg 1c io port: [b60, b63]
[    0.408994] PCI: 0000:00:0f.0 reg 20 io port: [cc00, cc0f]
[    0.408994] PCI: 0000:00:0f.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
[    0.408994] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe024000, fe027fff]
[    0.408994] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.408994] pci 0000:00:10.1: PME# disabled
[    0.408994] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02b000, fe02bfff]
[    0.408994] PCI: 0000:00:14.0 reg 14 io port: [c800, c807]
[    0.408994] pci 0000:00:14.0: supports D1
[    0.408994] pci 0000:00:14.0: supports D2
[    0.408994] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.408994] pci 0000:00:14.0: PME# disabled
[    0.408994] PCI: bridge 0000:00:02.0 io port: [b000, bfff]
[    0.408994] PCI: bridge 0000:00:02.0 32bit mmio: [fdc00000, fdcfffff]
[    0.408994] PCI: bridge 0000:00:02.0 64bit mmio pref: [fdd00000, fddfffff]
[    0.408994] PCI: 0000:02:00.0 reg 10 32bit mmio: [fa000000, faffffff]
[    0.408994] PCI: 0000:02:00.0 reg 14 64bit mmio: [d0000000, dfffffff]
[    0.408994] PCI: 0000:02:00.0 reg 1c 64bit mmio: [f8000000, f9ffffff]
[    0.408994] PCI: 0000:02:00.0 reg 24 io port: [9c00, 9c7f]
[    0.408994] PCI: 0000:02:00.0 reg 30 32bit mmio: [fbfe0000, fbffffff]
[    0.408994] PCI: bridge 0000:00:04.0 io port: [9000, 9fff]
[    0.408994] PCI: bridge 0000:00:04.0 32bit mmio: [f8000000, fbffffff]
[    0.408994] PCI: bridge 0000:00:04.0 64bit mmio pref: [d0000000, dfffffff]
[    0.409007] PCI: 0000:03:05.0 reg 10 32bit mmio: [effff000, efffffff]
[    0.409036] pci 0000:03:05.0: supports D1
[    0.409037] pci 0000:03:05.0: supports D2
[    0.409039] pci 0000:03:05.0: PME# supported from D0 D1 D2 D3hot
[    0.409042] pci 0000:03:05.0: PME# disabled
[    0.409062] PCI: 0000:03:06.0 reg 10 32bit mmio: [efffe000, efffe7ff]
[    0.409092] pci 0000:03:06.0: supports D1
[    0.409093] pci 0000:03:06.0: supports D2
[    0.409117] PCI: 0000:03:07.0 reg 10 io port: [ac00, ac1f]
[    0.409125] PCI: 0000:03:07.0 reg 14 64bit mmio: [efc00000, efdfffff]
[    0.409133] PCI: 0000:03:07.0 reg 1c 64bit mmio: [e8000000, ebffffff]
[    0.409151] pci 0000:03:07.0: supports D1
[    0.409152] pci 0000:03:07.0: supports D2
[    0.409174] PCI: 0000:03:09.0 reg 10 32bit mmio: [effe0000, effeffff]
[    0.409224] pci 0000:00:10.0: transparent bridge
[    0.409227] PCI: bridge 0000:00:10.0 io port: [a000, afff]
[    0.409229] PCI: bridge 0000:00:10.0 32bit mmio: [e8000000, efffffff]
[    0.409232] PCI: bridge 0000:00:10.0 32bit mmio pref: [fde00000, fdefffff]
[    0.409239] bus 00 -> node 0
[    0.409245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.409580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.512065] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 *10 11 14 15)
[    0.512272] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 *7 9 10 11 14 15)
[    0.512478] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.512683] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[    0.512888] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
[    0.513093] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.513297] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.513501] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.513707] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.513915] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.514122] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.514325] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.514532] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
[    0.514737] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.514943] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.515149] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.515355] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 *7 9 10 11 14 15)
[    0.515560] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.515766] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.515972] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.516230] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.516466] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.516705] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.516940] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.517178] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.517413] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.517653] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.517888] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.518128] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.518364] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.518605] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.518845] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.519081] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.519322] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.519558] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.519800] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.520048] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.520288] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.520525] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.520766] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.521002] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.521070] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.521070] pnp: PnP ACPI init
[    0.521070] ACPI: bus type pnp registered
[    0.524895] pnp: PnP ACPI: found 11 devices
[    0.524895] ACPI: ACPI bus type pnp unregistered
[    0.524895] PnPBIOS: Disabled by ACPI PNP
[    0.524895] PCI: Using ACPI for IRQ routing
[    0.532039] NET: Registered protocol family 8
[    0.532040] NET: Registered protocol family 20
[    0.532060] NetLabel: Initializing
[    0.532061] NetLabel:  domain hash size = 128
[    0.532062] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.532075] NetLabel:  unlabeled traffic allowed by default
[    0.532083] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.532087] hpet0: 3 32-bit timers, 25000000 Hz
[    0.533546] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.533548]    actual entries 65620
[    0.533655] AppArmor: AppArmor Filesystem Enabled
[    0.533682] ACPI: RTC can wake from S4
[    0.536044] Switched to high resolution mode on CPU 0
[    0.536171] Switched to high resolution mode on CPU 1
[    0.540028] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.540030] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.540033] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.540035] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.540037] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.540039] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.540041] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.540044] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.540049] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.540051] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.540059] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.540064] system 00:0a: iomem range 0xf0000-0xf3fff could not be reserved
[    0.540066] system 00:0a: iomem range 0xf4000-0xf7fff could not be reserved
[    0.540068] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.540071] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.540073] system 00:0a: iomem range 0xfefff000-0xfefff0ff could not be reserved
[    0.540076] system 00:0a: iomem range 0x7fef0000-0x7fefffff could not be reserved
[    0.540078] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.540081] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.540083] system 00:0a: iomem range 0x100000-0x7feeffff could not be reserved
[    0.540086] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.540088] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.540090] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.540093] system 00:0a: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.540095] system 00:0a: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.540098] system 00:0a: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.575222] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.575224] pci 0000:00:02.0:   IO window: 0xb000-0xbfff
[    0.575227] pci 0000:00:02.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.575230] pci 0000:00:02.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.575233] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.575235] pci 0000:00:04.0:   IO window: 0x9000-0x9fff
[    0.575238] pci 0000:00:04.0:   MEM window: 0xf8000000-0xfbffffff
[    0.575240] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.575244] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.575246] pci 0000:00:10.0:   IO window: 0xa000-0xafff
[    0.575249] pci 0000:00:10.0:   MEM window: 0xe8000000-0xefffffff
[    0.575252] pci 0000:00:10.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.575261] pci 0000:00:02.0: setting latency timer to 64
[    0.575265] pci 0000:00:04.0: setting latency timer to 64
[    0.575269] pci 0000:00:10.0: setting latency timer to 64
[    0.575271] bus: 00 index 0 io port: [0, ffff]
[    0.575273] bus: 00 index 1 mmio: [0, ffffffff]
[    0.575275] bus: 01 index 0 io port: [b000, bfff]
[    0.575276] bus: 01 index 1 mmio: [fdc00000, fdcfffff]
[    0.575278] bus: 01 index 2 mmio: [fdd00000, fddfffff]
[    0.575279] bus: 01 index 3 mmio: [0, 0]
[    0.575281] bus: 02 index 0 io port: [9000, 9fff]
[    0.575283] bus: 02 index 1 mmio: [f8000000, fbffffff]
[    0.575285] bus: 02 index 2 mmio: [d0000000, dfffffff]
[    0.575286] bus: 02 index 3 mmio: [0, 0]
[    0.575288] bus: 03 index 0 io port: [a000, afff]
[    0.575289] bus: 03 index 1 mmio: [e8000000, efffffff]
[    0.575291] bus: 03 index 2 mmio: [fde00000, fdefffff]
[    0.575293] bus: 03 index 3 io port: [0, ffff]
[    0.575294] bus: 03 index 4 mmio: [0, ffffffff]
[    0.575303] NET: Registered protocol family 2
[    0.588047] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.588264] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.588728] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.588949] TCP: Hash tables configured (established 131072 bind 65536)
[    0.588952] TCP reno registered
[    0.592078] NET: Registered protocol family 1
[    0.592171] checking if image is initramfs... it is
[    1.089405] Freeing initrd memory: 8003k freed
[    1.090205] audit: initializing netlink socket (disabled)
[    1.090221] type=2000 audit(1233507279.089:1): initialized
[    1.094582] highmem bounce pool size: 64 pages
[    1.094587] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.096265] VFS: Disk quotas dquot_6.5.1
[    1.096344] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.096433] msgmni has been set to 1743
[    1.096537] io scheduler noop registered
[    1.096539] io scheduler anticipatory registered
[    1.096541] io scheduler deadline registered
[    1.096550] io scheduler cfq registered (default)
[    1.096564] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.096593] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.096601] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.096622] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.128038] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.128049] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.128057] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.128068] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.128086] pci 0000:02:00.0: Boot video device
[    1.128192] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.128213] pcieport-driver 0000:00:02.0: found MSI capability
[    1.128230] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.128272] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.128339] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.128357] pcieport-driver 0000:00:04.0: found MSI capability
[    1.128370] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.128412] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.128705] isapnp: Scanning for PnP cards...
[    1.481482] isapnp: No Plug & Play device found
[    1.510698] hpet_resources: 0xfefff000 is busy
[    1.510760] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.512679] brd: module loaded
[    1.512739] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.512837] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.512839] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.515705] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.515709] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.517120] mice: PS/2 mouse device common for all mice
[    1.517225] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.517256] rtc0: alarms up to one year, y3k, hpet irqs
[    1.517379] EISA: Probing bus 0 at eisa.0
[    1.517388] Cannot allocate resource for EISA slot 2
[    1.517392] Cannot allocate resource for EISA slot 4
[    1.517403] EISA: Detected 0 cards.
[    1.517405] cpuidle: using governor ladder
[    1.517407] cpuidle: using governor menu
[    1.517793] TCP cubic registered
[    1.517814] Using IPI No-Shortcut mode
[    1.517973] registered taskstats version 1
[    1.518086]   Magic number: 13:635:943
[    1.518150] tty ptyye: hash matches
[    1.518187] tty tty0: hash matches
[    1.518188] tty console: hash matches
[    1.518253] rtc_cmos 00:05: setting system clock to 2009-02-01 16:54:40 UTC (1233507280)
[    1.518256] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.518258] EDD information not available.
[    1.518478] Freeing unused kernel memory: 424k freed
[    1.518525] Write protecting the kernel text: 2580k
[    1.518556] Write protecting the kernel read-only data: 940k
[    1.679448] fuse init (API version 7.9)
[    1.836804] fan PNP0C0B:00: registered as cooling_device0
[    1.836809] ACPI: Fan [FAN] (on)
[    1.841976] processor ACPI0007:00: registered as cooling_device1
[    1.842028] processor ACPI0007:01: registered as cooling_device2
[    1.849043] thermal LNXTHERM:01: registered as thermal_zone0
[    1.851019] ACPI: Thermal Zone [THRM] (40 C)
[    2.382494] usbcore: registered new interface driver usbfs
[    2.382517] usbcore: registered new interface driver hub
[    2.390018] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    2.390047] ohci1394 0000:03:05.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    2.441938] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[effff000-effff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
[    2.449029] usbcore: registered new device driver usb
[    2.450438] No dock devices found.
[    2.453175] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.453598] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    2.453608] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    2.453612] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.453635] nv_probe: set workaround bit for reversed mac addr
[    2.463297] SCSI subsystem initialized
[    2.480069] libata version 3.00 loaded.
[    2.481773] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.972457] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:18:f3:6d:ba:02
[    2.972461] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    2.973984] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[    2.973994] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
[    2.974004] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.974007] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.974046] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.974069] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfe02f000
[    3.030129] usb usb1: configuration #1 chosen from 1 choice
[    3.030150] hub 1-0:1.0: USB hub found
[    3.030159] hub 1-0:1.0: 8 ports detected
[    3.236620] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    3.236632] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    3.236644] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    3.236647] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    3.236685] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    3.236708] ehci_hcd 0000:00:0b.1: debug port 1
[    3.236712] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    3.236727] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
[    3.412020] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    3.424016] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.424138] usb usb2: configuration #1 chosen from 1 choice
[    3.424157] hub 2-0:1.0: USB hub found
[    3.424164] hub 2-0:1.0: 8 ports detected
[    3.480027] hub 1-0:1.0: unable to enumerate USB device on port 1
[    3.632372] pata_amd 0000:00:0d.0: version 0.3.10
[    3.632414] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.632491] scsi0 : pata_amd
[    3.632723] scsi1 : pata_amd
[    3.633334] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    3.633337] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    3.720418] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000e37701]
[    3.963421] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    3.963450] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    3.963514] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    3.963537] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    3.963950] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    3.963953] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[    3.963982] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    3.963999] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    3.972796] sata_nv 0000:00:0e.0: version 3.5
[    3.972812] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    3.972814] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.972853] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.972984] scsi2 : sata_nv
[    3.973058] scsi3 : sata_nv
[    3.973242] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[    3.973244] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[    4.440041] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    4.448173] ata3.00: ATA-7: ST3320820AS, 3.AHG, max UDMA/100
[    4.448176] ata3.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.464173] ata3.00: configured for UDMA/100
[    4.512020] usb 2-4: new high speed USB device using ehci_hcd and address 5
[    4.646682] usb 2-4: configuration #1 chosen from 1 choice
[    4.646916] hub 2-4:1.0: USB hub found
[    4.655513] hub 2-4:1.0: 4 ports detected
[    4.932043] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    4.940177] ata4.00: ATA-7: ST3320820AS, 3.AHG, max UDMA/100
[    4.940179] ata4.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.956176] ata4.00: configured for UDMA/100
[    4.956267] scsi 2:0:0:0: Direct-Access     ATA      ST3320820AS      3.AH PQ: 0 ANSI: 5
[    4.956402] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    4.956451] scsi 3:0:0:0: Direct-Access     ATA      ST3320820AS      3.AH PQ: 0 ANSI: 5
[    4.956511] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[    4.956533] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 23 (level, low) -> IRQ 23
[    4.956536] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    4.956573] sata_nv 0000:00:0f.0: setting latency timer to 64
[    4.957317] scsi4 : sata_nv
[    4.957384] scsi5 : sata_nv
[    4.957569] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 23
[    4.957572] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 23
[    4.976026] usb 2-6: new high speed USB device using ehci_hcd and address 6
[    5.112030] usb 2-6: configuration #1 chosen from 1 choice
[    5.416019] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    5.424044] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    5.432181] ata5.00: ATAPI: HL-DT-STDVDRRW GSA-H30L, S655, max UDMA/33
[    5.448174] ata5.00: configured for UDMA/33
[    5.646765] usb 1-1: configuration #1 chosen from 1 choice
[    5.916043] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    5.925275] ata6.00: ATA-6: WDC WD740GD-00FLC0, 33.08F33, max UDMA/133
[    5.925278] ata6.00: 145226112 sectors, multi 1: LBA48 
[    5.941246] ata6.00: configured for UDMA/133
[    5.943096] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRRW GSA-H30L  S655 PQ: 0 ANSI: 5
[    5.943236] scsi 4:0:0:0: Attached scsi generic sg2 type 5
[    5.943289] scsi 5:0:0:0: Direct-Access     ATA      WDC WD740GD-00FL 33.0 PQ: 0 ANSI: 5
[    5.943353] scsi 5:0:0:0: Attached scsi generic sg3 type 0
[    5.953028] usb 1-2: new full speed USB device using ohci_hcd and address 4
[    5.967854] Driver 'sd' needs updating - please use bus_type methods
[    5.967945] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    5.967959] sd 2:0:0:0: [sda] Write Protect is off
[    5.967961] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.967980] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.968035] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    5.968044] sd 2:0:0:0: [sda] Write Protect is off
[    5.968046] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.968063] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.968066]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.973684]  sda1 sda2
[    5.973797] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.973863] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    5.973875] sd 3:0:0:0: [sdb] Write Protect is off
[    5.973877] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.973895] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.973936] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[    5.973945] sd 3:0:0:0: [sdb] Write Protect is off
[    5.973947] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.973964] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.973967]  sdb: sdb1
[    5.993544] sd 3:0:0:0: [sdb] Attached SCSI disk
[    5.993659] sd 5:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
[    5.993676] sd 5:0:0:0: [sdc] Write Protect is off
[    5.993678] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.993696] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.993753] sd 5:0:0:0: [sdc] 145226112 512-byte hardware sectors (74356 MB)
[    5.993763] sd 5:0:0:0: [sdc] Write Protect is off
[    5.993765] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.993782] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.993784]  sdc:sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.999267] Uniform CD-ROM driver Revision: 3.20
[    5.999346] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.006750]  sdc1 sdc2 sdc3
[    6.019493] sd 5:0:0:0: [sdc] Attached SCSI disk
[    6.183216] usb 1-2: configuration #1 chosen from 1 choice
[    6.492019] usb 1-3: new full speed USB device using ohci_hcd and address 5
[    6.696167] usb 1-3: configuration #1 chosen from 1 choice
[    6.776257] usb 2-4.3: new full speed USB device using ehci_hcd and address 7
[    6.914118] usb 2-4.3: configuration #1 chosen from 1 choice
[    6.922580] usbcore: registered new interface driver libusual
[    6.924102] usbcore: registered new interface driver hiddev
[    6.928934] Initializing USB Mass Storage driver...
[    6.929000] scsi6 : SCSI emulation for USB Mass Storage devices
[    6.929067] usb-storage: device found at 6
[    6.929068] usb-storage: waiting for device to settle before scanning
[    6.935304] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input1
[    6.936117] input,hidraw0: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:0b.0-1
[    6.966112] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.1/input/input2
[    6.969134] input,hiddev96,hidraw1: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:0b.0-1
[    6.976319] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.0/input/input3
[    6.976564] input,hidraw2: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:0b.0-2
[    6.989147] hiddev97hidraw3: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:0b.0-2
[    6.989205] usbcore: registered new interface driver usbhid
[    6.989208] usbhid: v2.6:USB HID core driver
[    6.989239] usbcore: registered new interface driver usb-storage
[    6.989254] USB Mass Storage support registered.
[    7.025511] PM: Starting manual resume from disk
[    7.025514] PM: Resume from partition 8:35
[    7.025516] PM: Checking hibernation image.
[    7.025654] PM: Resume from disk failed.
[    7.056881] kjournald starting.  Commit interval 5 seconds
[    7.056898] EXT3-fs: mounted filesystem with ordered data mode.
[   11.928199] usb-storage: device scan complete
[   11.930017] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   11.930641] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   11.931264] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   11.931889] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   11.932819] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[   11.932912] sd 6:0:0:0: Attached scsi generic sg4 type 0
[   11.933549] sd 6:0:0:1: [sde] Attached SCSI removable disk
[   11.933588] sd 6:0:0:1: Attached scsi generic sg5 type 0
[   11.934299] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[   11.934335] sd 6:0:0:2: Attached scsi generic sg6 type 0
[   11.935041] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[   11.935080] sd 6:0:0:3: Attached scsi generic sg7 type 0
[   12.039287] udevd version 124 started
[   12.318530] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.364229] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.469125] ACPI: I/O resource nForce2_smbus [0x4c00-0x4c3f] conflicts with ACPI region SM00 [0x4c00-0x4c05]
[   12.469129] ACPI: Device needs an ACPI driver
[   12.469155] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   12.469169] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   12.497238] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   12.529036] ACPI: Power Button (FF) [PWRF]
[   12.529106] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.561032] ACPI: Power Button (CM) [PWRB]
[   13.182591] Linux agpgart interface v0.103
[   13.341753] nvidia: module license 'NVIDIA' taints kernel.
[   13.658621] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   13.658633] nvidia 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   13.658639] nvidia 0000:02:00.0: setting latency timer to 64
[   13.658859] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
[   13.737118] Bluetooth: Core ver 2.13
[   13.777115] NET: Registered protocol family 31
[   13.777118] Bluetooth: HCI device and connection manager initialized
[   13.777121] Bluetooth: HCI socket layer initialized
[   13.893216] Linux video capture interface: v2.00
[   13.958150] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   13.959350] usbcore: registered new interface driver btusb
[   13.994782] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   14.072802] gspca: main v2.2.0 registered
[   14.108487] cfg80211: Using static regulatory domain info
[   14.108490] cfg80211: Regulatory domain: US
[   14.108492] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.108494] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   14.108496] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   14.108498] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   14.108500] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   14.108502] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   14.108504] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   14.108506] cfg80211: Calling CRDA for country: US
[   14.148809] gspca: probing 046d:08da
[   14.253234] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   14.253246] ath5k 0000:03:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   14.253284] ath5k 0000:03:09.0: registered as 'phy0'
[   14.420101] phy0: Selected rate control algorithm 'pid'
[   14.578079] saa7130/34: v4l2 driver version 0.2.14 loaded
[   14.682889] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa2, PHY: 0x61)
[   14.682968] saa7134 0000:03:06.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   14.682981] saa7133[0]: found at 0000:03:06.0, rev: 209, irq: 19, latency: 32, mmio: 0xefffe000
[   14.682995] saa7133[0]: subsystem: 1043:4871, board: ASUS P7131 4871 [card=111,autodetected]
[   14.683004] saa7133[0]: board init: gpio is 0
[   14.727940] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   14.738295] wlan: 0.9.4
[   14.779132] ath_pci: 0.9.4
[   14.839966] saa7133[0]: i2c eeprom 00: 43 10 71 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   14.839974] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   14.839981] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 00 01 03 08 ff 00 cf ff ff ff ff
[   14.839987] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.839993] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 22 15 50 ff ff ff ff ff ff
[   14.839999] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840005] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840011] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840017] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840023] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840029] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840035] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840041] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840047] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840053] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.840059] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.985088] tuner' 2-004b: chip found @ 0x96 (saa7133[0])
[   15.065022] tda829x 2-004b: setting tuner address to 61
[   15.145145] tda829x 2-004b: type set to tda8290+75a
[   16.271051] zc3xx: probe 2wr ov vga 0x0000
[   16.340052] zc3xx: probe sensor -> 11
[   16.340054] zc3xx: Find Sensor HV7131R(c)
[   16.355179] gspca: probe ok
[   16.355193] gspca: probing 046d:08da
[   16.415442] usbcore: registered new interface driver zc3xx
[   16.415446] zc3xx: registered
[   16.415572] usbcore: registered new interface driver snd-usb-audio
[   19.008493] saa7133[0]: registered device video1 [v4l2]
[   19.008626] saa7133[0]: registered device vbi0
[   19.072437] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   19.072442] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   19.072461] HDA Intel 0000:00:10.1: setting latency timer to 64
[   19.090737] saa7134 ALSA driver for DMA sound loaded
[   19.090763] saa7133[0]/alsa: saa7133[0] at 0xefffe000 irq 19 registered as card -2
[   19.107877] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   19.189102] DVB: registering new adapter (saa7133[0])
[   19.189107] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   19.260015] tda1004x: setting up plls for 48MHz sampling clock
[   20.008349] lp: driver loaded but no devices found
[   20.101156] Adding 2144668k swap on /dev/sdc3.  Priority:-1 extents:1 across:2144668k
[   20.638775] EXT3 FS on sdc1, internal journal
[   21.365070] kjournald starting.  Commit interval 5 seconds
[   21.365412] EXT3 FS on sdc2, internal journal
[   21.365418] EXT3-fs: mounted filesystem with writeback data mode.
[   21.404884] ReiserFS: sdb1: found reiserfs format "3.6" with standard journal
[   21.404901] ReiserFS: sdb1: using ordered data mode
[   21.411238] ReiserFS: sdb1: journal params: device sdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   21.411617] ReiserFS: sdb1: checking transaction log (sdb1)
[   21.470359] ReiserFS: sdb1: Using r5 hash to sort names
[   21.504012] tda1004x: timeout waiting for DSP ready
[   21.544015] tda1004x: found firmware revision 8d -- invalid
[   21.544018] tda1004x: trying to boot from eeprom
[   21.666548] type=1505 audit(1233503700.760:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4594
[   21.817070] type=1505 audit(1233503700.912:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4599
[   21.817259] type=1505 audit(1233503700.912:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4599
[   21.882359] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.361229] ACPI: WMI: Mapper loaded
[   22.407477] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ processors (2 cpu cores) (version 2.20.00)
[   22.407530] powernow-k8:    0 : fid 0x14 (2800 MHz), vid 0x8
[   22.407533] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xa
[   22.407535] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xc
[   22.407537] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0xe
[   22.407539] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x10
[   22.407541] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x10
[   22.407542] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
[   22.618904] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.670982] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   22.670986] apm: disabled - APM is not SMP safe.
[   22.856400] ppdev: user-space parallel port driver
[   23.500023] Clocksource tsc unstable (delta = -182705077 ns)
[   23.876023] tda1004x: timeout waiting for DSP ready
[   23.920017] tda1004x: found firmware revision 1c -- invalid
[   23.920023] tda1004x: waiting for firmware upload...
[   23.920029] firmware: requesting dvb-fe-tda10046.fw
[   25.807355] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   25.807363] vboxdrv: Successfully done.
[   25.807368] vboxdrv: Found 2 processor cores.
[   25.807587] vboxdrv: fAsync=1 offMin=0xd9f48 offMax=0xd9f48
[   25.807684] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   25.807689] vboxdrv: Successfully loaded version 2.1.2 (interface 0x000a0009).
[   26.727939] NET: Registered protocol family 10
[   26.729125] lo: Disabled Privacy Extensions
[   37.232030] tda1004x: found firmware revision 20 -- ok

**(****The madness occurs somewhere around here****)**

[   40.313799] Bluetooth: L2CAP ver 2.11
[   40.313807] Bluetooth: L2CAP socket layer initialized
[   40.337206] Bluetooth: SCO (Voice Link) ver 0.6
[   40.337213] Bluetooth: SCO socket layer initialized
[   40.347871] Bluetooth: RFCOMM socket layer initialized
[   40.347893] Bluetooth: RFCOMM TTY layer initialized
[   40.347897] Bluetooth: RFCOMM ver 1.10
[   40.376369] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.376377] Bluetooth: BNEP filters: protocol multicast
[   40.450669] Bridge firewalling registered
[   44.532621] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.667229] NET: Registered protocol family 17
[   46.913633] wlan0: direct probe to AP 00:1b:2f:e4:ed:d0 try 1
[   47.112032] wlan0: direct probe to AP 00:1b:2f:e4:ed:d0 try 2
[   47.312038] wlan0: direct probe to AP 00:1b:2f:e4:ed:d0 try 3
[   47.512029] wlan0: direct probe to AP 00:1b:2f:e4:ed:d0 timed out
[   54.960027] eth0: no IPv6 routers present
[  943.068442] ath5k phy0: noise floor calibration timeout (2437MHz)
[  943.070739] ath5k phy0: noise floor calibration timeout (2462MHz)
[  944.181594] wlan0: authenticate with AP 00:18:f8:67:8d:e8
[  944.184213] wlan0: authenticated
[  944.184225] wlan0: associate with AP 00:18:f8:67:8d:e8
[  944.186225] wlan0: RX AssocResp from 00:18:f8:67:8d:e8 (capab=0x411 status=0 aid=1)
[  944.186233] wlan0: associated
[  944.187124] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  955.140033] wlan0: no IPv6 routers present
[ 1006.208291] wlan0 direct probe responded
[ 1006.208304] wlan0: authenticate with AP 00:18:f8:67:8d:e8
[ 1006.216143] wlan0: authenticated
[ 1006.216155] wlan0: associate with AP 00:18:f8:67:8d:e8
[ 1006.218741] wlan0: RX ReassocResp from 00:18:f8:67:8d:e8 (capab=0x411 status=0 aid=1)
[ 1006.218750] wlan0: associated
[ 1010.222818] wlan0: deauthenticated (Reason: 15)
[ 1010.233106] wlan0: direct probe to AP 00:18:f8:67:8d:e8 try 1
[ 1010.240131] wlan0 direct probe responded
[ 1010.240143] wlan0: authenticate with AP 00:18:f8:67:8d:e8
[ 1010.241949] wlan0: authenticated
[ 1010.241956] wlan0: associate with AP 00:18:f8:67:8d:e8
[ 1010.244307] wlan0: RX ReassocResp from 00:18:f8:67:8d:e8 (capab=0x411 status=0 aid=1)
[ 1010.244314] wlan0: associated
[ 1046.609294] wlan0: disassociating by local choice (reason=3)
[ 1046.649059] wlan0: deauthenticating by local choice (reason=3)
```


Since I have no idea where to look and how to proceed, i'm hoping for the community to aid me in this matter...

---

### Post by markbuntu on 2009-02-01
start pulseaudio from a terminal with

pulseaudio -vvv

and see what messages you get. 

Are you running vitual box?
and bluetooth audio?
through a firewall?
If so, that could be a large part of your problem.

---

### Post by KhaaL on 2009-02-02
thanks for the great tips. I'll try to answer your questions as good as i can:

*Yes, I run virtualbox

*I have in the past tried to get bluetooth audio going but it failed miserably to my dissapointment. I got bluez-audio, bluez-input, bluez-network and bluez-serial installed.

*no firewall whatsoever


I did try to run applications with pulseaudio now, but i can't get any success in it playing... I'm thinking of removing pulse and reverting to alsa - the only way i'm keeping it now is because it might have some valuable information for the devs. could this be a bug or is it something i managed to mess up?


Here's the full output from running pulseaudio -vvv

```

I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/usb_device_46d_8da_noserial_if1_sound_card_0_alsa_control__1
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.usb_device_46d_8da_noserial_if1_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:1...
I: alsa-util.c: PCM device front:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:1...
I: alsa-util.c: PCM device surround40:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:1...
I: alsa-util.c: PCM device surround41:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:1...
I: alsa-util.c: PCM device surround50:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround51:1...
I: alsa-util.c: PCM device surround51:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:1...
I: alsa-util.c: PCM device surround71:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying hw:1 as last resort...
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
I: module-alsa-source.c: Successfully opened device hw:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 0 "alsa_input.usb_device_46d_8da_noserial_if1_sound_card_0_alsa_capture_0" with sample spec "s16le 1ch 16000Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 1 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module.c: Loaded "module-alsa-source" (index: #0; argument: "device_id=1 source_name=alsa_input.usb_device_46d_8da_noserial_if1_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_26c_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_26c_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: alsa-util.c: Couldn't open PCM device front:0: Device or resource busy
D: alsa-util.c: Trying surround40:0...
I: alsa-util.c: Couldn't open PCM device surround40:0: Device or resource busy
D: alsa-util.c: Trying surround41:0...
I: alsa-util.c: Couldn't open PCM device surround41:0: Device or resource busy
D: alsa-util.c: Trying surround50:0...
I: alsa-util.c: Couldn't open PCM device surround50:0: Device or resource busy
D: alsa-util.c: Trying surround51:0...
I: alsa-util.c: Couldn't open PCM device surround51:0: Device or resource busy
D: alsa-util.c: Trying surround71:0...
I: alsa-util.c: Couldn't open PCM device surround71:0: Device or resource busy
D: alsa-util.c: Trying hw:0 as last resort...
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_10de_26c_sound_card_0_alsa_playback_0"): initialization failed.
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_26c_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_26c_sound_card_0_alsa_control__1
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=2 source_name=alsa_input.pci_1131_7133_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:2...
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.front.0:CARD=2'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM front:2
I: alsa-util.c: Couldn't open PCM device front:2: No such file or directory
D: alsa-util.c: Trying surround40:2...
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround40.0:CARD=2'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround40:2
I: alsa-util.c: Couldn't open PCM device surround40:2: No such file or directory
D: alsa-util.c: Trying surround41:2...
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=2'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround41:2
I: alsa-util.c: Couldn't open PCM device surround41:2: No such file or directory
D: alsa-util.c: Trying surround50:2...
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=2'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround50:2
I: alsa-util.c: Couldn't open PCM device surround50:2: No such file or directory
D: alsa-util.c: Trying surround51:2...
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround51.0:CARD=2'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround51:2
I: alsa-util.c: Couldn't open PCM device surround51:2: No such file or directory
D: alsa-util.c: Trying surround71:2...
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SAA7134.pcm.surround71.0:CARD=2'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM surround71:2
I: alsa-util.c: Couldn't open PCM device surround71:2: No such file or directory
D: alsa-util.c: Trying hw:2 as last resort...
W: alsa-util.c: Device hw:2 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-source.c: Successfully opened device hw:2.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:2'
I: alsa-util.c: Cannot find mixer control "Capture".
W: alsa-util.c: Cannot find fallback mixer control "Mic".
I: source.c: Created source 2 "alsa_input.pci_1131_7133_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-source.c: Using 8 fragments of size 1760 bytes.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-alsa-source" (index: #2; argument: "device_id=2 source_name=alsa_input.pci_1131_7133_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1131_7133_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 3 modules.
I: module.c: Loaded "module-hal-detect" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #4; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-rtp-send' with args 'source=@DEFAULT_MONITOR@ loop=0' due to GConf configuration.
E: module-rtp-send.c: Source does not exist.
E: module.c: Failed to load  module "module-rtp-send" (argument: "source=@DEFAULT_MONITOR@ loop=0"): initialization failed.
E: module-gconf.c: pa_module_load() failed
D: module-gconf.c: Loading module 'module-rtp-recv' with args '' due to GConf configuration.
I: module.c: Loaded "module-rtp-recv" (index: #6; argument: "").
D: module-gconf.c: Loading module 'module-native-protocol-tcp' with args 'auth-anonymous=1' due to GConf configuration.
I: protocol-native.c: using already loaded auth cookie.
I: protocol-native.c: using already loaded auth cookie.
I: module.c: Loaded "module-native-protocol-tcp" (index: #7; argument: "auth-anonymous=1").
D: module-gconf.c: Loading module 'module-esound-protocol-tcp' with args 'auth-anonymous=1' due to GConf configuration.
I: module.c: Loaded "module-esound-protocol-tcp" (index: #8; argument: "auth-anonymous=1").
D: module-gconf.c: Loading module 'module-zeroconf-publish' with args '' due to GConf configuration.
D: module-zeroconf-publish.c: Publishing services in Zeroconf
D: module-zeroconf-publish.c: Successfully created entry group for khaal@Xeraphim: ALSA PCM on hw:1 (USB Audio) via DMA.
D: module-zeroconf-publish.c: Successfully created entry group for khaal@Xeraphim: ALSA PCM on front:0 (ALC888 Analog) via DMA.
D: module-zeroconf-publish.c: Successfully created entry group for khaal@Xeraphim: ALSA PCM on hw:2 (SAA7134 PCM) via DMA.
I: module.c: Loaded "module-zeroconf-publish" (index: #9; argument: "").
D: module-gconf.c: Loading module 'module-zeroconf-discover' with args '' due to GConf configuration.
I: module.c: Loaded "module-zeroconf-discover" (index: #10; argument: "").
I: module.c: Loaded "module-gconf" (index: #11; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #12; argument: "").
D: module-default-device-restore.c: No previous default sink setting, ignoring.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #13; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #14; argument: "").
D: module-suspend-on-idle.c: Source alsa_input.usb_device_46d_8da_noserial_if1_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1131_7133_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #16; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-zeroconf-publish.c: Successfully established service khaal@Xeraphim: ALSA PCM on hw:1 (USB Audio) via DMA.
I: module-zeroconf-publish.c: Successfully established service khaal@Xeraphim: ALSA PCM on front:0 (ALC888 Analog) via DMA.
I: module-zeroconf-publish.c: Successfully established service khaal@Xeraphim: ALSA PCM on hw:2 (SAA7134 PCM) via DMA.
I: module-zeroconf-publish.c: Successfully established main service.
I: module-suspend-on-idle.c: Source alsa_input.pci_1131_7133_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_input.usb_device_46d_8da_noserial_if1_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: client.c: Created 0 "Native client (UNIX socket client)"
I: client.c: Freed 0 "Native client (UNIX socket client)"
I: protocol-native.c: connection died.
I: client.c: Created 1 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 1 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 1 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 2 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 2 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 2 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 3 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 3 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 3 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 4 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 4 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 4 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 5 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 5 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 5 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 6 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 6 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 6 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 7 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 7 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 7 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 8 "EsounD client (UNIX socket client)"
D: module-rtp-recv.c: Checking for dead streams ...
I: client.c: Created 9 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 9 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 9 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 10 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 10 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
D: sink-input.c: Assertion 'data->sink' failed at pulsecore/sink-input.c:110, function pa_sink_input_new.
D: protocol-esound.c: read(): EOF
I: client.c: Freed 8 "EsounD client (UNIX socket client)"
I: client.c: Freed 10 "gnome-sound-properties"
I: protocol-native.c: connection died.
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
I: client.c: Created 11 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 11 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 11 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 12 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 12 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 12 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 13 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 13 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 13 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 14 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 14 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Created 15 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 15 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 15 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Freed 14 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 16 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 16 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 16 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 17 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 17 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 17 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 18 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 18 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 18 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 19 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 19 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 19 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 20 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 20 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Created 21 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 21 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 21 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Freed 20 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 22 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 22 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 22 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/volume_uuid_7220EAB420EA7E8B, member=PropertyModified
D: module-rtp-recv.c: Checking for dead streams ...
I: client.c: Created 23 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 23 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 23 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 24 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 24 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 24 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 25 "Native client (UNIX socket client)"
I: client.c: Freed 25 "Native client (UNIX socket client)"
I: protocol-native.c: connection died.
I: client.c: Created 26 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 26 changed name from "Native client (UNIX socket client)" to "gnome-volume-control"
I: client.c: Freed 26 "gnome-volume-control"
I: protocol-native.c: connection died.
I: client.c: Created 27 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 27 changed name from "Native client (UNIX socket client)" to "gnome-volume-control"
I: client.c: Freed 27 "gnome-volume-control"
I: protocol-native.c: connection died.
I: client.c: Created 28 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 28 changed name from "Native client (UNIX socket client)" to "gnome-volume-control"
I: client.c: Freed 28 "gnome-volume-control"
I: protocol-native.c: connection died.
I: client.c: Created 29 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 29 changed name from "Native client (UNIX socket client)" to "gnome-volume-control"
I: client.c: Freed 29 "gnome-volume-control"
I: protocol-native.c: connection died.
D: module-rtp-recv.c: Checking for dead streams ...
I: client.c: Created 30 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 30 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 30 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
I: client.c: Created 31 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 31 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [skype]"
I: client.c: Freed 31 "ALSA plug-in [skype]"
I: protocol-native.c: connection died.
D: module-rtp-recv.c: Checking for dead streams ...
I: client.c: Created 32 "Native client (UNIX socket client)"
I: client.c: Freed 32 "Native client (UNIX socket client)"
I: protocol-native.c: connection died.
I: client.c: Created 33 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 33 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 33 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 34 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 34 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 34 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 35 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 35 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 35 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 36 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 36 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 36 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 37 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 37 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 37 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 38 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 38 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 38 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 39 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 39 changed name from "Native client (UNIX socket client)" to "gnome-sound-properties"
I: client.c: Freed 39 "gnome-sound-properties"
I: protocol-native.c: connection died.
I: client.c: Created 40 "EsounD client (UNIX socket client)"
D: protocol-esound.c: read(): EOF
I: client.c: Freed 40 "EsounD client (UNIX socket client)"
D: module-rtp-recv.c: Checking for dead streams ...
I: client.c: Created 41 "EsounD client (UNIX socket client)"
I: client.c: Created 42 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 42 changed name from "Native client (UNIX socket client)" to "Totem Movie Player"
I: client.c: Freed 42 "Totem Movie Player"
I: protocol-native.c: connection died.
I: client.c: Created 43 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 43 changed name from "Native client (UNIX socket client)" to "Totem Movie Player"
I: client.c: Freed 43 "Totem Movie Player"
I: protocol-native.c: connection died.
I: client.c: Created 44 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 44 changed name from "Native client (UNIX socket client)" to "Totem Movie Player"
I: client.c: Freed 44 "Totem Movie Player"
I: protocol-native.c: connection died.
I: client.c: Created 45 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 45 changed name from "Native client (UNIX socket client)" to "Totem Movie Player"
D: sink-input.c: Assertion 'data->sink' failed at pulsecore/sink-input.c:110, function pa_sink_input_new.
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: protocol-esound.c: read(): EOF
I: client.c: Freed 41 "EsounD client (UNIX socket client)"
I: client.c: Freed 45 "Totem Movie Player"
I: protocol-native.c: connection died.
I: client.c: Created 46 "EsounD client (UNIX socket client)"
I: client.c: Created 47 "Native client (UNIX socket client)"
I: client.c: Freed 47 "Native client (UNIX socket client)"
I: protocol-native.c: connection died.
I: client.c: Created 48 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 48 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [vlc]"
I: client.c: Freed 48 "ALSA plug-in [vlc]"
I: protocol-native.c: connection died.
I: client.c: Created 49 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 49 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [vlc]"
D: sink-input.c: Assertion 'data->sink' failed at pulsecore/sink-input.c:110, function pa_sink_input_new.
D: sink-input.c: Assertion 'data->sink' failed at pulsecore/sink-input.c:110, function pa_sink_input_new.
I: client.c: Freed 49 "ALSA plug-in [vlc]"
I: protocol-native.c: connection died.
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
I: client.c: Created 50 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 50 changed name from "Native client (UNIX socket client)" to "MPlayer"
D: sink-input.c: Assertion 'data->sink' failed at pulsecore/sink-input.c:110, function pa_sink_input_new.
I: client.c: Freed 50 "MPlayer"
I: protocol-native.c: connection died.
I: client.c: Created 51 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 51 changed name from "Native client (UNIX socket client)" to "MPlayer"
D: sink-input.c: Assertion 'data->sink' failed at pulsecore/sink-input.c:110, function pa_sink_input_new.
I: client.c: Freed 51 "MPlayer"
I: protocol-native.c: connection died.
D: module-rtp-recv.c: Checking for dead streams ...
D: module-rtp-recv.c: Checking for dead streams ...
^CI: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-alsa-source" (index: #0).
D: module-zeroconf-publish.c: Removing entry group for khaal@Xeraphim: ALSA PCM on hw:1 (USB Audio) via DMA.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 0 "alsa_input.usb_device_46d_8da_noserial_if1_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #0).
I: module.c: Unloading "module-alsa-source" (index: #1).
D: module-zeroconf-publish.c: Removing entry group for khaal@Xeraphim: ALSA PCM on front:0 (ALC888 Analog) via DMA.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_10de_26c_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #1).
I: module.c: Unloading "module-alsa-source" (index: #2).
D: module-zeroconf-publish.c: Removing entry group for khaal@Xeraphim: ALSA PCM on hw:2 (SAA7134 PCM) via DMA.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 2 "alsa_input.pci_1131_7133_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #2).
I: module.c: Unloading "module-hal-detect" (index: #3).
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus.Local, path=/org/freedesktop/DBus/Local, member=Disconnected
I: module.c: Unloaded "module-hal-detect" (index: #3).
I: module.c: Unloading "module-esound-protocol-unix" (index: #4).
I: client.c: Freed 46 "EsounD client (UNIX socket client)"
I: module.c: Unloaded "module-esound-protocol-unix" (index: #4).
I: module.c: Unloading "module-native-protocol-unix" (index: #5).
I: module.c: Unloaded "module-native-protocol-unix" (index: #5).
I: module.c: Unloading "module-rtp-recv" (index: #6).
I: module.c: Unloaded "module-rtp-recv" (index: #6).
I: module.c: Unloading "module-native-protocol-tcp" (index: #7).
I: module.c: Unloaded "module-native-protocol-tcp" (index: #7).
I: module.c: Unloading "module-esound-protocol-tcp" (index: #8).
I: module.c: Unloaded "module-esound-protocol-tcp" (index: #8).
I: module.c: Unloading "module-zeroconf-publish" (index: #9).
I: module.c: Unloaded "module-zeroconf-publish" (index: #9).
I: module.c: Unloading "module-zeroconf-discover" (index: #10).
I: module.c: Unloaded "module-zeroconf-discover" (index: #10).
I: module.c: Unloading "module-gconf" (index: #11).
D: module-gconf.c: Unloading module #10
D: module-gconf.c: Unloading module #7
D: module-gconf.c: Unloading module #8
D: module-gconf.c: Unloading module #9
D: module-gconf.c: Unloading module #6
I: module.c: Unloaded "module-gconf" (index: #11).
I: module.c: Unloading "module-volume-restore" (index: #12).
I: module.c: Unloaded "module-volume-restore" (index: #12).
I: module.c: Unloading "module-default-device-restore" (index: #13).
I: module.c: Unloaded "module-default-device-restore" (index: #13).
I: module.c: Unloading "module-rescue-streams" (index: #14).
I: module.c: Unloaded "module-rescue-streams" (index: #14).
I: module.c: Unloading "module-suspend-on-idle" (index: #15).
I: module.c: Unloaded "module-suspend-on-idle" (index: #15).
I: module.c: Unloading "module-x11-publish" (index: #16).
I: module.c: Unloaded "module-x11-publish" (index: #16).
I: main.c: Daemon terminated.
```

---

### Post by markbuntu on 2009-02-03
Looks like you have rtp receiving enabled in pulseaudio. You should try turning that off. It also looks like alsa is having a problem with the driver from the alsa-util messages.

Pulseaudio is definitely crapping out on you but it could be the alsa driver that is causing it or maybe some application grabbing the sound hardware. Make absolutely sure that no application is trying to use the sound, there may be something using OSS which will screw everything up and give you messages like "unable to open" and "device or resource busy". Skype can do that among others. 

You can also try reverting to alsa so you can see if it is really a pulseaudio issue or not. You can also try setting up the pulseaudio sound server according to this guide to ensure that all your applications use pulse.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by KhaaL on 2009-02-03
You are my hero. A million thanks! I disabled everything with network access, multicast/rtp and it made pulseaudio jolly again and i can finally listen to amarok while watching youtube and vlc simultaniously :D

you rock :guitar:

---

