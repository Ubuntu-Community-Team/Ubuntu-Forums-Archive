---
title: "link blinks"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by Byb on 2010-05-27
Hi 
I have a borrring issue with my eeePC 701 eeeBuntu3std: I can't get a connection, because I think that  (see the end):
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.29-1-netbook (root@adamm-laptop) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #0array1 SMP Mon Feb 23 15:02:03 MST 2009
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000] PAT WC disabled due to known CPU erratum.
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f780000 (usable)
[    0.000000]  BIOS-e820: 000000007f780000 - 000000007f790000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f790000 - 000000007f7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f7d0000 - 000000007f7de000 (reserved)
[    0.000000]  BIOS-e820: 000000007f7e0000 - 000000007f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] last_pfn = 0x7f780 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f780000 (usable)
[    0.000000]  modified: 000000007f780000 - 000000007f790000 (ACPI data)
[    0.000000]  modified: 000000007f790000 - 000000007f7d0000 (ACPI NVS)
[    0.000000]  modified: 000000007f7d0000 - 000000007f7de000 (reserved)
[    0.000000]  modified: 000000007f7e0000 - 000000007f800000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37a13000 - 37fef71f
[    0.000000] Allocated new RAMDISK: 006e4000 - 00cc071f
[    0.000000] Move RAMDISK from 0000000037a13000 - 0000000037fef71e to 006e4000 - 00cc071e
[    0.000000] ACPI: RSDP 000FBE50, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7F780000, 0034 (r1 A M I  OEMRSDT   3000911 MSFT       97)
[    0.000000] ACPI: FACP 7F780200, 0081 (r1 A M I  OEMFACP   3000911 MSFT       97)
[    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (16) does not match PM1_EVT_LEN (4)
[    0.000000] ACPI: DSDT 7F780400, 6069 (r1  A0797 A0797000        0 INTL 20060113)
[    0.000000] ACPI: FACS 7F790000, 0040
[    0.000000] ACPI: APIC 7F780390, 0068 (r1 A M I  OEMAPIC   3000911 MSFT       97)
[    0.000000] ACPI: OEMB 7F790040, 0046 (r1 A M I  AMI_OEM   3000911 MSFT       97)
[    0.000000] ACPI: MCFG 7F786470, 003C (r1 A M I  OEMMCFG   3000911 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 00000000 - 377fe000
[    0.000000]   bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00006e0438]    TEXT DATA BSS ==> [0000100000 - 00006e0438]
[    0.000000]   #4 [00006e1000 - 00006e4000]    INIT_PG_TABLE ==> [00006e1000 - 00006e4000]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00006e4000 - 0000cc071f]      NEW RAMDISK ==> [00006e4000 - 0000cc071f]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f780
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f780
[    0.000000] On node 0 totalpages: 521999
[    0.000000] free_area_init_node: node 0, pgdat c05b8080, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2304 pages used for memmap
[    0.000000]   HighMem zone: 292482 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
[    0.000000] NR_CPUS:2 nr_cpumask_bits:2 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Allocating 36864 bytes of per cpu data
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517919
[    0.000000] Kernel command line: root=UUID=8b33b1b3-62e9-4c53-a5af-b339a8936dfb ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 630.142 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10441920 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Memory: 2047776k/2088448k available (3179k kernel code, 39448k reserved, 1751k data, 376k init, 1179144k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xfff9d000 - 0xfffff000   ( 392 kB)
[    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.004000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.004000]       .init : 0xc05d9000 - 0xc0637000   ( 376 kB)
[    0.004000]       .data : 0xc041adaf - 0xc05d0cd4   (1751 kB)
[    0.004000]       .text : 0xc0100000 - 0xc041adaf   (3179 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004028] Calibrating delay loop (skipped), value calculated using timer frequency.. 1260.28 BogoMIPS (lpj=2520568)
[    0.004082] Security Framework initialized
[    0.004099] SELinux:  Disabled at boot.
[    0.004133] Mount-cache hash table entries: 512
[    0.004532] Initializing cgroup subsys ns
[    0.004547] Initializing cgroup subsys cpuacct
[    0.004554] Initializing cgroup subsys memory
[    0.004567] Initializing cgroup subsys freezer
[    0.004607] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004614] CPU: L2 cache: 512K
[    0.004645] Checking 'hlt' instruction... OK.
[    0.021058] SMP alternatives: switching to UP code
[    0.332343] Freeing SMP alternatives: 16k freed
[    0.332353] ACPI: Core revision 20081204
[    0.356614] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.398849] CPU0: Intel(R) Celeron(R) M processor          900MHz stepping 08
[    0.400001] APIC calibration not consistent with PM Timer: 116ms instead of 100ms
[    0.400001] APIC delta adjusted to PM-Timer: 437544 (507581)
[    0.400001] Brought up 1 CPUs
[    0.400001] Total of 1 processors activated (1260.28 BogoMIPS).
[    0.400001] CPU0 attaching NULL sched-domain.
[    0.400001] net_namespace: 1024 bytes
[    0.400001] Booting paravirtualized kernel on bare hardware
[    0.400001] regulator: core version 0.5
[    0.400001] Time: 19:03:16  Date: 05/27/10
[    0.400001] NET: Registered protocol family 16
[    0.400001] ACPI: bus type pci registered
[    0.400141] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.400152] PCI: Not using MMCONFIG.
[    0.400453] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.400460] PCI: Using configuration type 1 for base access
[    0.410683] bio: create slab <bio-0> at 0
[    0.413334] ACPI: EC: Look up EC in DSDT
[    0.434746] ACPI: Interpreter enabled
[    0.434766] ACPI: (supports S0 S1 S3 S4 S5)
[    0.434831] ACPI: Using IOAPIC for interrupt routing
[    0.435004] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.442002] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.442010] PCI: Using MMCONFIG for extended config space
[    0.461426] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.461435] ACPI: EC: driver started in poll mode
[    0.461912] ACPI: No dock devices found.
[    0.462143] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.462438] pci 0000:00:02.0: reg 10 32bit mmio: [0xf7f00000-0xf7f7ffff]
[    0.462452] pci 0000:00:02.0: reg 14 io port: [0xec00-0xec07]
[    0.462464] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.462476] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf7ec0000-0xf7efffff]
[    0.462548] pci 0000:00:02.1: reg 10 32bit mmio: [0xf7f80000-0xf7ffffff]
[    0.462704] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7eb8000-0xf7ebbfff]
[    0.462778] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.462788] pci 0000:00:1b.0: PME# disabled
[    0.462885] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.462894] pci 0000:00:1c.0: PME# disabled
[    0.462993] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.463003] pci 0000:00:1c.1: PME# disabled
[    0.463105] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.463114] pci 0000:00:1c.2: PME# disabled
[    0.463194] pci 0000:00:1d.0: reg 20 io port: [0xe400-0xe41f]
[    0.463278] pci 0000:00:1d.1: reg 20 io port: [0xe480-0xe49f]
[    0.463358] pci 0000:00:1d.2: reg 20 io port: [0xe800-0xe81f]
[    0.463438] pci 0000:00:1d.3: reg 20 io port: [0xe880-0xe89f]
[    0.463523] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf7eb7c00-0xf7eb7fff]
[    0.463605] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.463615] pci 0000:00:1d.7: PME# disabled
[    0.463808] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.463826] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.463836] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.463846] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0380-03ff
[    0.463900] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.463912] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.463927] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.463939] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.463952] pci 0000:00:1f.2: reg 20 io port: [0xffa0-0xffaf]
[    0.464065] pci 0000:00:1f.2: PME# supported from D3hot
[    0.464074] pci 0000:00:1f.2: PME# disabled
[    0.464144] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.464339] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfc0000-0xfbffffff]
[    0.464388] pci 0000:03:00.0: reg 30 32bit mmio: [0xfbfa0000-0xfbfbffff]
[    0.464447] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.464457] pci 0000:03:00.0: PME# disabled
[    0.464539] pci 0000:00:1c.1: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.464615] pci 0000:00:1c.2: bridge 32bit mmio: [0xf8000000-0xfbefffff]
[    0.464629] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf0000000-0xf6ffffff]
[    0.464703] pci 0000:00:1e.0: transparent bridge
[    0.464749] pci_bus 0000:00: on NUMA node 0
[    0.464779] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.465243] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.465408] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.465566] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.481096] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.481511] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.481914] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.482317] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.482722] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.483135] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.483544] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.483953] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.485645] SCSI subsystem initialized
[    0.485747] libata version 3.00 loaded.
[    0.486123] usbcore: registered new interface driver usbfs
[    0.486262] usbcore: registered new interface driver hub
[    0.486411] usbcore: registered new device driver usb
[    0.487560] ACPI: WMI: Mapper loaded
[    0.487566] PCI: Using ACPI for IRQ routing
[    0.500196] Bluetooth: Core ver 2.14
[    0.500413] NET: Registered protocol family 31
[    0.500418] Bluetooth: HCI device and connection manager initialized
[    0.500427] Bluetooth: HCI socket layer initialized
[    0.500434] NET: Registered protocol family 8
[    0.500440] NET: Registered protocol family 20
[    0.500557] NetLabel: Initializing
[    0.500563] NetLabel:  domain hash size = 128
[    0.500567] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.500608] NetLabel:  unlabeled traffic allowed by default
[    0.501072] hpet clockevent registered
[    0.501080] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.501092] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.501106] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.524022] pnp: PnP ACPI init
[    0.524053] ACPI: bus type pnp registered
[    0.532485] pnp: PnP ACPI: found 13 devices
[    0.532495] ACPI: ACPI bus type pnp unregistered
[    0.532532] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.532561] system 00:08: ioport range 0x380-0x383 has been reserved
[    0.532569] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.532578] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.532587] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.532596] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.532605] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.532615] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.532631] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.532640] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.532656] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.532671] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.532688] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.532697] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.532706] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.532714] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
[    0.568704] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.568712] pci 0000:00:1c.0:   IO window: disabled
[    0.568725] pci 0000:00:1c.0:   MEM window: disabled
[    0.568733] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.568746] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.568752] pci 0000:00:1c.1:   IO window: disabled
[    0.568764] pci 0000:00:1c.1:   MEM window: 0xfbf00000-0xfbffffff
[    0.568773] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.568786] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:01
[    0.568791] pci 0000:00:1c.2:   IO window: disabled
[    0.568802] pci 0000:00:1c.2:   MEM window: 0xf8000000-0xfbefffff
[    0.568813] pci 0000:00:1c.2:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff
[    0.568827] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.568833] pci 0000:00:1e.0:   IO window: disabled
[    0.568842] pci 0000:00:1e.0:   MEM window: disabled
[    0.568851] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.568890] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.568902] pci 0000:00:1c.0: setting latency timer to 64
[    0.568922] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.568931] pci 0000:00:1c.1: setting latency timer to 64
[    0.568948] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.568958] pci 0000:00:1c.2: setting latency timer to 64
[    0.568971] pci 0000:00:1e.0: setting latency timer to 64
[    0.568981] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.568989] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.568997] pci_bus 0000:04: resource 0 mem: [0x0-0x0]
[    0.569003] pci_bus 0000:04: resource 1 mem: [0x0-0x0]
[    0.569009] pci_bus 0000:04: resource 2 mem: [0x0-0x0]
[    0.569016] pci_bus 0000:04: resource 3 mem: [0x0-0x0]
[    0.569022] pci_bus 0000:03: resource 0 mem: [0x0-0x0]
[    0.569029] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.569036] pci_bus 0000:03: resource 2 mem: [0x0-0x0]
[    0.569043] pci_bus 0000:03: resource 3 mem: [0x0-0x0]
[    0.569051] pci_bus 0000:01: resource 0 mem: [0x0-0x0]
[    0.569058] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbefffff]
[    0.569065] pci_bus 0000:01: resource 2 mem: [0xf0000000-0xf6ffffff]
[    0.569072] pci_bus 0000:01: resource 3 mem: [0x0-0x0]
[    0.569079] pci_bus 0000:05: resource 0 mem: [0x0-0x0]
[    0.569085] pci_bus 0000:05: resource 1 mem: [0x0-0x0]
[    0.569091] pci_bus 0000:05: resource 2 mem: [0x0-0x0]
[    0.569098] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.569105] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.569202] NET: Registered protocol family 2
[    0.608159] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.608977] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.611121] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.612280] TCP: Hash tables configured (established 131072 bind 65536)
[    0.612290] TCP reno registered
[    0.624240] NET: Registered protocol family 1
[    0.624590] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.366844]  it is
[    2.172241] Freeing initrd memory: 6001k freed
[    2.173400] Scanning for low memory corruption every 60 seconds
[    2.174101] audit: initializing netlink socket (disabled)
[    2.174138] type=2000 audit(1274986997.172:1): initialized
[    2.198799] highmem bounce pool size: 64 pages
[    2.198815] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.207206] VFS: Disk quotas dquot_6.5.2
[    2.207488] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.210587] msgmni has been set to 1709
[    2.211174] alg: No test for stdrng (krng)
[    2.211211] io scheduler noop registered
[    2.211216] io scheduler anticipatory registered
[    2.211222] io scheduler deadline registered
[    2.211282] io scheduler cfq registered (default)
[    2.211316] pci 0000:00:02.0: Boot video device
[    2.211754] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.211861] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    2.212671] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.212766] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    2.213193] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    2.213283] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    2.213907] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.217211] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.218041] ACPI: AC Adapter [AC0] (on-line)
[    2.219989] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    2.421159] ACPI: Battery Slot [BAT0] (battery present)
[    2.422057] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.422066] ACPI: Power Button (FF) [PWRF]
[    2.422342] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.443745] ACPI: Lid Switch [LID]
[    2.444031] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.444040] ACPI: Sleep Button (CM) [SLPB]
[    2.444267] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    2.444276] ACPI: Power Button (CM) [PWRB]
[    2.446534] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.446702] processor ACPI_CPU:00: registered as cooling_device0
[    2.446714] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.470467] thermal LNXTHERM:01: registered as thermal_zone0
[    2.487045] ACPI: Thermal Zone [TZ00] (50 C)
[    2.540766] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled
[    2.546244] brd: module loaded
[    2.548585] loop: module loaded
[    2.549276] Fixed MDIO Bus: probed
[    2.549293] PPP generic driver version 2.4.2
[    2.549745] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.549932] Driver 'sd' needs updating - please use bus_type methods
[    2.550032] Driver 'sr' needs updating - please use bus_type methods
[    2.550306] ahci 0000:00:1f.2: version 3.0
[    2.550355] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.550385] ahci 0000:00:1f.2: PCI INT B disabled
[    2.550397] ahci: probe of 0000:00:1f.2 failed with error -22
[    2.550681] ata_piix 0000:00:1f.2: version 2.12
[    2.550703] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.550717] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.550813] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.550971] scsi0 : ata_piix
[    2.551434] scsi1 : ata_piix
[    2.556482] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.556492] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.884375] ata2.00: CFA: SILICONMOTION SM223AC, , max UDMA/66
[    2.884384] ata2.00: 7815024 sectors, multi 0: LBA 
[    2.900316] ata2.00: configured for UDMA/66
[    2.900595] scsi 1:0:0:0: Direct-Access     ATA      SILICONMOTION SM n/a  PQ: 0 ANSI: 5
[    2.901192] sd 1:0:0:0: [sda] 7815024 512-byte hardware sectors: (4.00 GB/3.72 GiB)
[    2.901239] sd 1:0:0:0: [sda] Write Protect is off
[    2.901246] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.901318] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.901512] sd 1:0:0:0: [sda] 7815024 512-byte hardware sectors: (4.00 GB/3.72 GiB)
[    2.901554] sd 1:0:0:0: [sda] Write Protect is off
[    2.901561] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.901630] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.901641]  sda: sda1
[    2.902753] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.903085] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.909073] usbcore: registered new interface driver libusual
[    2.909334] usbcore: registered new interface driver usbserial
[    2.909444] USB Serial support registered for generic
[    2.909576] usbcore: registered new interface driver usbserial_generic
[    2.909583] usbserial: USB Serial Driver core
[    2.909898] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.943246] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.943261] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.948473] mice: PS/2 mouse device common for all mice
[    3.028334] rtc_cmos 00:03: RTC can wake from S4
[    3.028582] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.028626] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    3.029236] device-mapper: uevent: version 1.0.3
[    3.029682] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    3.029822] device-mapper: multipath: version 1.0.5 loaded
[    3.029832] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.030430] cpuidle: using governor ladder
[    3.031191] cpuidle: using governor menu
[    3.032720] TCP cubic registered
[    3.033700] NET: Registered protocol family 10
[    3.034868] lo: Disabled Privacy Extensions
[    3.035732] NET: Registered protocol family 17
[    3.035942] Bluetooth: L2CAP ver 2.11
[    3.035947] Bluetooth: L2CAP socket layer initialized
[    3.035955] Bluetooth: SCO (Voice Link) ver 0.6
[    3.035960] Bluetooth: SCO socket layer initialized
[    3.036053] Bluetooth: RFCOMM socket layer initialized
[    3.036083] Bluetooth: RFCOMM TTY layer initialized
[    3.036088] Bluetooth: RFCOMM ver 1.10
[    3.036382] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
[    3.036414] Using IPI No-Shortcut mode
[    3.036932] registered taskstats version 1
[    3.037197]   Magic number: 10:551:92
[    3.037383] rtc_cmos 00:03: setting system clock to 2010-05-27 19:03:18 UTC (1274986998)
[    3.037393] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.037398] EDD information not available.
[    3.037918] Freeing unused kernel memory: 376k freed
[    3.038177] Write protecting the kernel text: 3180k
[    3.038282] Write protecting the kernel read-only data: 1448k
[    3.053932] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.450907] fuse init (API version 7.11)
[    3.983013] uhci_hcd: USB Universal Host Controller Interface driver
[    3.983174] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.983195] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.983204] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.983411] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.983472] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e400
[    3.983735] usb usb1: configuration #1 chosen from 1 choice
[    3.983817] hub 1-0:1.0: USB hub found
[    3.983837] hub 1-0:1.0: 2 ports detected
[    3.984197] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.984219] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.984227] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.984379] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.984440] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e480
[    3.984664] usb usb2: configuration #1 chosen from 1 choice
[    3.984743] hub 2-0:1.0: USB hub found
[    3.984762] hub 2-0:1.0: 2 ports detected
[    3.984989] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.985007] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.985015] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.985139] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.985193] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    3.985430] usb usb3: configuration #1 chosen from 1 choice
[    3.985516] hub 3-0:1.0: USB hub found
[    3.985535] hub 3-0:1.0: 2 ports detected
[    3.985752] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.985772] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.985780] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.985918] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.985972] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e880
[    3.986204] usb usb4: configuration #1 chosen from 1 choice
[    3.986281] hub 4-0:1.0: USB hub found
[    3.986300] hub 4-0:1.0: 2 ports detected
[    4.035010] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.035020] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    4.035113] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.035231] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.035240] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.035430] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.039377] ehci_hcd 0000:00:1d.7: debug port 1
[    4.039390] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.039413] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    4.052072] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.052366] usb usb5: configuration #1 chosen from 1 choice
[    4.052449] hub 5-0:1.0: USB hub found
[    4.052475] hub 5-0:1.0: 8 ports detected
[    4.364101] usb 5-5: new high speed USB device using ehci_hcd and address 2
[    4.497529] usb 5-5: configuration #1 chosen from 1 choice
[    4.648794] Initializing USB Mass Storage driver...
[    4.651099] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.651364] usbcore: registered new interface driver usb-storage
[    4.651374] USB Mass Storage support registered.
[    4.656305] usb-storage: device found at 2
[    4.656313] usb-storage: waiting for device to settle before scanning
[    4.908190] Marking TSC unstable due to TSC halts in idle
[    5.000021] Clocksource tsc unstable (delta = -125345541 ns)
[    5.150330] EXT4-fs: barriers enabled
[    5.151078] kjournald2 starting: pid 1358, dev sda1:8, commit interval 5 seconds
[    5.151109] EXT4-fs: delayed allocation enabled
[    5.151114] EXT4-fs: file extents enabled
[    5.151262] EXT4-fs: mballoc enabled
[    5.151269] EXT4-fs: mounted filesystem sda1 with ordered data mode
[    8.820900] udev: starting version 141
[    8.996338] eeepc: Eee PC Hotkey Driver
[    8.996560] eeepc: Hotkey init flags 0x41
[    8.997954] eeepc: Get control methods supported: 0x101711
[    8.998251] input: Asus EeePC extra buttons as /devices/virtual/input/input6
[    9.114243] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16/input/input7
[    9.144393] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.208860] Linux agpgart interface v0.103
[    9.226953] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    9.227420] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    9.232551] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    9.309804] Atheros(R) L2 Ethernet Driver - version 2.2.3
[    9.309813] Copyright (c) 2007 Atheros Corporation.
[    9.309906] atl2 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.309927] atl2 0000:03:00.0: setting latency timer to 64
[    9.603962] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.604296] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.668839] usb-storage: device scan complete
[    9.669715] scsi 2:0:0:0: Direct-Access     USB2.0   CardReader SD0   0100 PQ: 0 ANSI: 0
[    9.671731] iTCO_vendor_support: vendor-support=0
[    9.680148] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.680548] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[    9.680832] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.689128] intel_rng: FWH not detected
[    9.848918] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   10.104747] sd 2:0:0:0: [sdb] 15679488 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[   10.105248] sd 2:0:0:0: [sdb] Write Protect is off
[   10.105259] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.105266] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.107250] sd 2:0:0:0: [sdb] 15679488 512-byte hardware sectors: (8.02 GB/7.47 GiB)
[   10.107750] sd 2:0:0:0: [sdb] Write Protect is off
[   10.107760] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.107767] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.107781]  sdb: sdb1
[   10.109552] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.109909] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   10.801229] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000
[   10.889311] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   11.455970] i801_smbus 0000:00:1f.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.455985] ACPI: I/O resource 0000:00:1f.3 [0x400-0x41f] conflicts with ACPI region SMRG [0x400-0x40f]
[   11.455993] ACPI: Device needs an ACPI driver
[   11.489887] lp: driver loaded but no devices found
[   11.520166] netbook version 0.3b init sucessfully
[   11.520179] sys_init_module: 'netbook'->init suspiciously returned 1, it should follow 0/-E convention
[   11.520184] sys_init_module: loading module anyway...
[   11.520195] Pid: 2296, comm: modprobe Not tainted 2.6.29-1-netbook #0array1
[   11.520202] Call Trace:
[   11.520220]  [<c04155a5>] ? printk+0xf/0x12
[   11.520247]  [<c014bc44>] sys_init_module+0x107/0x186
[   11.520259]  [<c0102f6b>] sysenter_do_call+0x12/0x2f
[   11.520272]  [<c0410000>] ? cpuid4_cache_lookup+0x5c/0x2b7
[   12.329546] EXT4 FS on sda1, internal journal on sda1:8
[   13.258533] EXT4-fs: barriers enabled
[   13.259690] kjournald2 starting: pid 2535, dev sdb1:8, commit interval 5 seconds
[   13.259720] EXT4-fs warning: maximal mount count reached, running e2fsck is recommended
[   13.260242] EXT4 FS on sdb1, internal journal on sdb1:8
[   13.260251] EXT4-fs: delayed allocation enabled
[   13.260256] EXT4-fs: file extents enabled
[   13.260429] EXT4-fs: mballoc enabled
[   13.260435] EXT4-fs: recovery complete.
[   13.260446] EXT4-fs: mounted filesystem sdb1 with ordered data mode
[   17.980821] pci 0000:01:00.0: reg 10 64bit mmio: [0x000000-0x00ffff]
[   18.022599] cfg80211: Using static regulatory domain info
[   18.022608] cfg80211: Regulatory domain: JP
[   18.022613]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.022622]     (2402000 KHz - 2494000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.022631]     (5160000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.022639]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.022646] cfg80211: Calling CRDA for country: JP
[   18.043219] cfg80211: Regulatory domain changed to country: JP
[   18.043230]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.043239]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   18.043247]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[   18.043254]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[   18.043262]     (4910000 KHz - 4930000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[   18.043269]     (4910000 KHz - 4990000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[   18.043277]     (4930000 KHz - 4950000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[   18.043284]     (5030000 KHz - 5045000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[   18.043291]     (5030000 KHz - 5090000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[   18.043299]     (5050000 KHz - 5060000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[   18.043306]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   18.043313]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   18.043321]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[   18.104371] ath5k 0000:01:00.0: enabling device (0000 -> 0002)
[   18.104391] ath5k 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.104415] ath5k 0000:01:00.0: setting latency timer to 64
[   18.104695] ath5k 0000:01:00.0: registered as 'phy0'
[   18.174616] wmaster0 (ath5k): not using net_device_ops yet
[   18.177449] phy0: Selected rate control algorithm 'pid'
[   18.197577] wlan0 (ath5k): not using net_device_ops yet
[   18.199471] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   20.497022] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.497031] Bluetooth: BNEP filters: protocol multicast
[   20.533705] Bridge firewalling registered
[   22.579072] ppdev: user-space parallel port driver
[   24.296562] [drm] Initialized drm 1.1.0 20060810
[   24.394612] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.394627] pci 0000:00:02.0: setting latency timer to 64
[   24.412883] [drm:i915_gem_detect_bit_6_swizzle] *ERROR* Couldn't read from MCHBAR.  Disabling tiling.
[   24.412938] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   26.540766] atl2 0000:03:00.0: irq 27 for MSI/MSI-X
[   26.541405] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.597269] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.746218] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[   26.746745] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.062337] atl2: eth0 NIC Link is Down
[   28.014873] wlan0: authenticate with AP 00:17:44:70:f7:59
[   28.016599] wlan0: authenticated
[   28.016608] wlan0: associate with AP 00:17:44:70:f7:59
[   28.018468] wlan0: RX AssocResp from 00:17:44:70:f7:59 (capab=0x401 status=0 aid=1)
[   28.018476] wlan0: associated
[   28.019797] wlan0: disassociating by local choice (reason=3)
[   28.642197] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   29.420344] atl2: eth0 NIC Link is Down
[   31.041176] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   31.819443] atl2: eth0 NIC Link is Down
[   33.658116] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   34.429822] atl2: eth0 NIC Link is Down
[   35.998209] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   36.776380] atl2: eth0 NIC Link is Down
[   37.436078] eth0: no IPv6 routers present
[   38.612501] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   39.386747] atl2: eth0 NIC Link is Down
[   40.892692] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[   48.733151] atl2: eth0 NIC Link is Down
[   50.306131] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   51.090906] atl2: eth0 NIC Link is Down
[   52.945989] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   53.725499] atl2: eth0 NIC Link is Down
[   55.578036] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   56.360139] atl2: eth0 NIC Link is Down
[   57.978612] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   58.759178] atl2: eth0 NIC Link is Down
[   60.619215] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   63.911400] atl2: eth0 NIC Link is Down
[   65.558439] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   66.336658] atl2: eth0 NIC Link is Down
[   67.983886] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   68.761932] atl2: eth0 NIC Link is Down
[   70.408947] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   71.187169] atl2: eth0 NIC Link is Down
[   73.023300] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   73.797576] atl2: eth0 NIC Link is Down
[   75.387356] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   76.169429] atl2: eth0 NIC Link is Down
[   77.971710] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[   84.749263] atl2: eth0 NIC Link is Down
[   86.281698] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   87.061994] atl2: eth0 NIC Link is Down
[   88.711644] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   89.487266] atl2: eth0 NIC Link is Down
[   91.134297] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   91.418875] ath5k 0000:01:00.0: PCI INT A disabled
[   91.912519] atl2: eth0 NIC Link is Down
[   93.751339] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   94.522967] atl2: eth0 NIC Link is Down
[   96.152717] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   96.945281] atl2: eth0 NIC Link is Down
[   98.424940] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[  128.754560] atl2: eth0 NIC Link is Down
[  130.328405] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  131.114509] atl2: eth0 NIC Link is Down
[  132.964680] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  133.748091] atl2: eth0 NIC Link is Down
[  135.598321] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  139.275904] atl2: eth0 NIC Link is Down
[  141.133400] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  141.911579] atl2: eth0 NIC Link is Down
[  143.537274] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  144.311613] atl2: eth0 NIC Link is Down
[  145.879967] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  146.658226] atl2: eth0 NIC Link is Down
[  148.496971] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  149.268589] atl2: eth0 NIC Link is Down
[  150.836994] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  151.615240] atl2: eth0 NIC Link is Down
[  153.356904] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[  321.733310] atl2: eth0 NIC Link is Down
[  323.280537] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  324.066615] atl2: eth0 NIC Link is Down
[  325.916814] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  326.700277] atl2: eth0 NIC Link is Down
[  328.529183] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  329.308719] atl2: eth0 NIC Link is Down
[  331.163839] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  331.943364] atl2: eth0 NIC Link is Down
[  333.798466] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  334.578018] atl2: eth0 NIC Link is Down
[  336.335772] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[  339.740088] atl2: eth0 NIC Link is Down
[  341.319850] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  342.090245] atl2: eth0 NIC Link is Down
[  343.658595] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  344.436858] atl2: eth0 NIC Link is Down
[  346.062570] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  346.836893] atl2: eth0 NIC Link is Down
[  348.405295] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  349.183505] atl2: eth0 NIC Link is Down
[  351.024841] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  351.793911] atl2: eth0 NIC Link is Down
[  353.300054] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[  360.747146] atl2: eth0 NIC Link is Down
[  362.296522] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  365.742062] atl2: eth0 NIC Link is Down
[  367.389114] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  368.167406] atl2: eth0 NIC Link is Down
[  369.814847] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  370.592640] atl2: eth0 NIC Link is Down
[  372.431336] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  373.203077] atl2: eth0 NIC Link is Down
[  374.795287] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  375.574863] atl2: eth0 NIC Link is Down
[  377.448772] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  378.234822] atl2: eth0 NIC Link is Down
[  379.806284] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[  381.627793] atl2: eth0 NIC Link is Down
[  383.161914] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
[  385.743063] atl2: eth0 NIC Link is Down
[  387.295669] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  388.077784] atl2: eth0 NIC Link is Down
[  389.932934] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  390.712430] atl2: eth0 NIC Link is Down
[  392.567598] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  393.347121] atl2: eth0 NIC Link is Down
[  394.967964] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  395.746171] atl2: eth0 NIC Link is Down
[  397.650419] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  398.432226] atl2: eth0 NIC Link is Down
[  400.238739] atl2: eth0 NIC Link is Up<10 Mbps Full Duplex>
....
Please how could I have the link to remain up? I already tried other cables
Thanks for any help

---

### Post by Byb on 2010-06-03
no idea?

---

