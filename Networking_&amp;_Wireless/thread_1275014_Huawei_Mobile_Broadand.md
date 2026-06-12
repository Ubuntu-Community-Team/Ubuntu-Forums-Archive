---
title: "Huawei Mobile Broadand"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by qhrille on 2009-09-25
Hi 

I've got a new Huawei E182E Usb Mobile Broadband Device.

I'm running Ubuntu 9.04 with the latest updates and it won't get recognized as a mobile broadband device by the network manager, i.e don't show up at all. And I've tried to manually configure the device with the correct parameters in the network manager but nothing seems to work.

But it will auto mount as a usb memory stick device and I can read the windows installation files and info from the build in usb "drive"

I have used until recently and very successfully a Huawei E220 USB Mobile Broadband device. 

Using the lsusb command i get this information: 
Bus 001 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. 

And using dmesg command gives:
```

[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000005f6d0000 - 000000005f6e5000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005f6e5000 - 000000005f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005f700000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x5f6d0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005f6d0000 (usable)
[    0.000000]  modified: 000000005f6d0000 - 000000005f6e5000 (ACPI data)
[    0.000000]  modified: 000000005f6e5000 - 000000005f700000 (ACPI NVS)
[    0.000000]  modified: 000000005f700000 - 0000000060000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378b9000 - 37fefba7
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb3ba7
[    0.000000] Move RAMDISK from 00000000378b9000 - 0000000037fefba6 to 0087d000 - 00fb3ba6
[    0.000000] ACPI: RSDP 000F6BF0, 0024 (r2 IBM   )
[    0.000000] ACPI: XSDT 5F6D4765, 005C (r1 IBM    TP-74        2090  LTP        0)
[    0.000000] ACPI: FACP 5F6D4800, 00F4 (r3 IBM    TP-74        2090 IBM         1)
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080926]
[    0.000000] ACPI: DSDT 5F6D49E7, 10397 (r1 IBM    TP-74        2090 MSFT  100000E)
[    0.000000] ACPI: FACS 5F6F6000, 0040
[    0.000000] ACPI: SSDT 5F6D49B4, 0033 (r1 IBM    TP-74        2090 MSFT  100000E)
[    0.000000] ACPI: ECDT 5F6E4D7E, 0052 (r1 IBM    TP-74        2090 IBM         1)
[    0.000000] ACPI: TCPA 5F6E4DD0, 0032 (r1 IBM    TP-74        2090 PTL         1)
[    0.000000] ACPI: APIC 5F6E4E02, 005A (r1 IBM    TP-74        2090 IBM         1)
[    0.000000] ACPI: MCFG 5F6E4E5C, 003C (r1 IBM    TP-74        2090 IBM         1)
[    0.000000] ACPI: BOOT 5F6E4FD8, 0028 (r1 IBM    TP-74        2090  LTP        1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 642MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fb3ba7]      NEW RAMDISK ==> [000087d000 - 0000fb3ba7]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0005f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0005f6d0
[    0.000000] On node 0 totalpages: 390741
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1286 pages used for memmap
[    0.000000]   HighMem zone: 163276 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
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
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 387687
[    0.000000] Kernel command line: root=UUID=c9ae5357-475e-4914-9aad-c40d5ee2e23e ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1496.274 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 7817280 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1526336k/1563456k available (4115k kernel code, 35816k reserved, 2199k data, 532k init, 658248k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.54 BogoMIPS (lpj=5985096)
[    0.004048] Security Framework initialized
[    0.004064] SELinux:  Disabled at boot.
[    0.004098] AppArmor: AppArmor initialized
[    0.004109] Mount-cache hash table entries: 512
[    0.004313] Initializing cgroup subsys ns
[    0.004320] Initializing cgroup subsys cpuacct
[    0.004324] Initializing cgroup subsys memory
[    0.004329] Initializing cgroup subsys freezer
[    0.004351] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004354] CPU: L2 cache: 2048K
[    0.004374] Checking 'hlt' instruction... OK.
[    0.020894] SMP alternatives: switching to UP code
[    0.148523] Freeing SMP alternatives: 18k freed
[    0.148529] ACPI: Core revision 20080926
[    0.160114] ACPI: Checking initramfs for custom DSDT
[    0.572585] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.614189] CPU0: Intel(R) Pentium(R) M processor 1.50GHz stepping 08
[    0.616002] Brought up 1 CPUs
[    0.616002] Total of 1 processors activated (2992.54 BogoMIPS).
[    0.616002] CPU0 attaching NULL sched-domain.
[    0.616002] net_namespace: 776 bytes
[    0.616002] Booting paravirtualized kernel on bare hardware
[    0.616002] Time: 10:49:21  Date: 09/25/09
[    0.616002] regulator: core version 0.5
[    0.616002] NET: Registered protocol family 16
[    0.616002] EISA bus registered
[    0.616002] ACPI: bus type pci registered
[    0.616002] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.616002] PCI: MCFG area at e0000000 reserved in E820
[    0.616002] PCI: Using MMCONFIG for extended config space
[    0.616002] PCI: Using configuration type 1 for base access
[    0.616002] ACPI: EC: EC description table is found, configuring boot EC
[    0.629601] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.756496] ACPI: Interpreter enabled
[    0.756500] ACPI: (supports S0 S3 S4 S5)
[    0.756525] ACPI: Using IOAPIC for interrupt routing
[    0.773343] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.773346] ACPI: EC: driver started in interrupt mode
[    0.778423] ACPI: ACPI Dock Station Driver: 4 docks/bays found
[    0.778438] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.778525] pci 0000:00:02.0: reg 10 32bit mmio: [0xa0080000-0xa00fffff]
[    0.778531] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.778536] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
[    0.778542] pci 0000:00:02.0: reg 1c 32bit mmio: [0xa0000000-0xa003ffff]
[    0.778575] pci 0000:00:02.1: reg 10 32bit mmio: [0x000000-0x07ffff]
[    0.778700] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.778706] pci 0000:00:1c.0: PME# disabled
[    0.778776] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.778839] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.778901] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.778964] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[    0.779030] pci 0000:00:1d.7: reg 10 32bit mmio: [0xa0040000-0xa00403ff]
[    0.779077] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.779083] pci 0000:00:1d.7: PME# disabled
[    0.779182] pci 0000:00:1e.2: reg 10 io port: [0x1c00-0x1cff]
[    0.779190] pci 0000:00:1e.2: reg 14 io port: [0x18c0-0x18ff]
[    0.779199] pci 0000:00:1e.2: reg 18 32bit mmio: [0xa0040800-0xa00409ff]
[    0.779208] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xa0040400-0xa00404ff]
[    0.779238] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.779243] pci 0000:00:1e.2: PME# disabled
[    0.779283] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]
[    0.779291] pci 0000:00:1e.3: reg 14 io port: [0x2000-0x207f]
[    0.779333] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.779338] pci 0000:00:1e.3: PME# disabled
[    0.779437] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.779444] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.779450] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.779488] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.779497] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.779505] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.779514] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.779522] pci 0000:00:1f.2: reg 20 io port: [0x1810-0x181f]
[    0.779547] pci 0000:00:1f.2: PME# supported from D3hot
[    0.779553] pci 0000:00:1f.2: PME# disabled
[    0.779618] pci 0000:00:1f.3: reg 20 io port: [0x18a0-0x18bf]
[    0.779729] pci 0000:02:00.0: reg 10 64bit mmio: [0xa0100000-0xa010ffff]
[    0.779788] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.779795] pci 0000:02:00.0: PME# disabled
[    0.780015] pci 0000:00:1c.0: bridge 32bit mmio: [0xa0100000-0xa01fffff]
[    0.780074] pci 0000:04:00.0: reg 10 32bit mmio: [0xa0200000-0xa0200fff]
[    0.780089] pci 0000:04:00.0: supports D1 D2
[    0.780091] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.780098] pci 0000:04:00.0: PME# disabled
[    0.780151] pci 0000:04:00.1: reg 10 32bit mmio: [0xa0201000-0xa02010ff]
[    0.780212] pci 0000:04:00.1: supports D1 D2
[    0.780214] pci 0000:04:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.780221] pci 0000:04:00.1: PME# disabled
[    0.780288] pci 0000:04:02.0: reg 10 32bit mmio: [0xa0202000-0xa0202fff]
[    0.780352] pci 0000:04:02.0: PME# supported from D0 D3hot D3cold
[    0.780358] pci 0000:04:02.0: PME# disabled
[    0.780425] pci 0000:00:1e.0: transparent bridge
[    0.780430] pci 0000:00:1e.0: bridge io port: [0x3000-0x6fff]
[    0.780436] pci 0000:00:1e.0: bridge 32bit mmio: [0xa0200000-0xafffffff]
[    0.780445] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.780486] bus 00 -> node 0
[    0.780495] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.780787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.780991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.784217] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.784529] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.784839] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.785146] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.785456] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.785762] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.786068] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.786377] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.786528] ACPI: Power Resource [PUBS] (on)
[    0.786528] ACPI: WMI: Mapper loaded
[    0.786528] SCSI subsystem initialized
[    0.786528] libata version 3.00 loaded.
[    0.786528] usbcore: registered new interface driver usbfs
[    0.786528] usbcore: registered new interface driver hub
[    0.786528] usbcore: registered new device driver usb
[    0.786528] PCI: Using ACPI for IRQ routing
[    0.786528] Expanded resource reserved due to conflict with Adapter ROM
[    0.786528] Bluetooth: Core ver 2.13
[    0.786528] NET: Registered protocol family 31
[    0.786528] Bluetooth: HCI device and connection manager initialized
[    0.786528] Bluetooth: HCI socket layer initialized
[    0.786528] NET: Registered protocol family 8
[    0.786528] NET: Registered protocol family 20
[    0.786528] NetLabel: Initializing
[    0.786528] NetLabel:  domain hash size = 128
[    0.786528] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.786528] NetLabel:  unlabeled traffic allowed by default
[    0.786528] hpet clockevent registered
[    0.786528] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.786528] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.786528] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.792078] AppArmor: AppArmor Filesystem Enabled
[    0.792086] pnp: PnP ACPI init
[    0.792086] ACPI: bus type pnp registered
[    0.799393] pnp: PnP ACPI: found 11 devices
[    0.799396] ACPI: ACPI bus type pnp unregistered
[    0.799400] PnPBIOS: Disabled by ACPI PNP
[    0.799412] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.799416] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.799419] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.799423] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    0.799426] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.799430] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.799433] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.799437] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.799440] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.799444] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.799447] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.799451] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.799455] system 00:00: iomem range 0x100000-0x5fffffff could not be reserved
[    0.799459] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.799468] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.799471] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.799475] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.799478] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.799482] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.799485] system 00:02: ioport range 0x15c0-0x15df has been reserved
[    0.799489] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.799493] system 00:02: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.799496] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.799500] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.799504] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.834252] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.834255] pci 0000:00:1c.0:   IO window: disabled
[    0.834263] pci 0000:00:1c.0:   MEM window: 0xa0100000-0xa01fffff
[    0.834268] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.834279] pci 0000:04:00.0: CardBus bridge, secondary bus 0000:05
[    0.834282] pci 0000:04:00.0:   IO window: 0x003000-0x0030ff
[    0.834289] pci 0000:04:00.0:   IO window: 0x003400-0x0034ff
[    0.834295] pci 0000:04:00.0:   PREFETCH window: 0xd0000000-0xd3ffffff
[    0.834302] pci 0000:04:00.0:   MEM window: 0xa4000000-0xa7ffffff
[    0.834309] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.834313] pci 0000:00:1e.0:   IO window: 0x3000-0x6fff
[    0.834320] pci 0000:00:1e.0:   MEM window: 0xa0200000-0xafffffff
[    0.834326] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000d7ffffff
[    0.834345] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.834352] pci 0000:00:1c.0: setting latency timer to 64
[    0.834361] pci 0000:00:1e.0: setting latency timer to 64
[    0.834373] pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.834381] bus: 00 index 0 io port: [0x00-0xffff]
[    0.834384] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.834387] bus: 02 index 0 mmio: [0x0-0x0]
[    0.834389] bus: 02 index 1 mmio: [0xa0100000-0xa01fffff]
[    0.834392] bus: 02 index 2 mmio: [0x0-0x0]
[    0.834394] bus: 02 index 3 mmio: [0x0-0x0]
[    0.834397] bus: 04 index 0 io port: [0x3000-0x6fff]
[    0.834400] bus: 04 index 1 mmio: [0xa0200000-0xafffffff]
[    0.834403] bus: 04 index 2 mmio: [0xd0000000-0xd7ffffff]
[    0.834405] bus: 04 index 3 io port: [0x00-0xffff]
[    0.834408] bus: 04 index 4 mmio: [0x000000-0xffffffff]
[    0.834411] bus: 05 index 0 io port: [0x3000-0x30ff]
[    0.834413] bus: 05 index 1 io port: [0x3400-0x34ff]
[    0.834416] bus: 05 index 2 mmio: [0xd0000000-0xd3ffffff]
[    0.834419] bus: 05 index 3 mmio: [0xa4000000-0xa7ffffff]
[    0.834430] NET: Registered protocol family 2
[    0.834555] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.834864] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.835716] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.836316] TCP: Hash tables configured (established 131072 bind 65536)
[    0.836321] TCP reno registered
[    0.836472] NET: Registered protocol family 1
[    0.836637] checking if image is initramfs... it is
[    1.288011] Switched to high resolution mode on CPU 0
[    1.645019] Freeing initrd memory: 7386k freed
[    1.645084] Simple Boot Flag at 0x35 set to 0x1
[    1.645139] cpufreq: No nForce2 chipset.
[    1.645344] audit: initializing netlink socket (disabled)
[    1.645373] type=2000 audit(1253875761.644:1): initialized
[    1.655108] highmem bounce pool size: 64 pages
[    1.655117] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.656741] VFS: Disk quotas dquot_6.5.1
[    1.656812] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.657572] fuse init (API version 7.10)
[    1.657674] msgmni has been set to 1711
[    1.657899] alg: No test for stdrng (krng)
[    1.657916] io scheduler noop registered
[    1.657918] io scheduler anticipatory registered
[    1.657921] io scheduler deadline registered
[    1.657938] io scheduler cfq registered (default)
[    1.657955] pci 0000:00:02.0: Boot video device
[    1.670174] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.670226] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.670265] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.670282] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.670300] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.670315] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.670405] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.670459] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.670994] ACPI: AC Adapter [AC] (on-line)
[    1.701515] ACPI: Battery Slot [BAT0] (battery present)
[    1.701605] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.701608] ACPI: Power Button (FF) [PWRF]
[    1.701665] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.702066] ACPI: Lid Switch [LID]
[    1.702120] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.702127] ACPI: Sleep Button (CM) [SLPB]
[    1.706028] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.706057] processor ACPI_CPU:00: registered as cooling_device0
[    1.706062] ACPI: Processor [CPU] (supports 8 throttling states)
[    1.714655] thermal LNXTHERM:01: registered as thermal_zone0
[    1.716565] ACPI: Thermal Zone [THM0] (53 C)
[    1.716619] isapnp: Scanning for PnP cards...
[    2.070721] isapnp: No Plug & Play device found
[    2.072059] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.072509] serial 0000:00:1e.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    2.072517] serial 0000:00:1e.3: PCI INT B disabled
[    2.073327] brd: module loaded
[    2.073696] loop: module loaded
[    2.073778] Fixed MDIO Bus: probed
[    2.073787] PPP generic driver version 2.4.2
[    2.073857] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.073889] Driver 'sd' needs updating - please use bus_type methods
[    2.073900] Driver 'sr' needs updating - please use bus_type methods
[    2.073947] ahci 0000:00:1f.2: version 3.0
[    2.073971] ahci: probe of 0000:00:1f.2 failed with error -22
[    2.074016] ata_piix 0000:00:1f.2: version 2.12
[    2.074023] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.228021] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.228115] scsi0 : ata_piix
[    2.228210] scsi1 : ata_piix
[    2.229445] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    2.229449] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    2.392423] ata1.00: ATA-6: HTC426060G9AT00, 00P3A0A3, max UDMA/100
[    2.392427] ata1.00: 117210240 sectors, multi 16: LBA48 
[    2.392445] ata1.00: applying bridge limits
[    2.408427] ata1.00: configured for UDMA/100
[    2.564209] scsi 0:0:0:0: Direct-Access     ATA      HTC426060G9AT00  00P3 PQ: 0 ANSI: 5
[    2.564329] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    2.564350] sd 0:0:0:0: [sda] Write Protect is off
[    2.564353] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.564384] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.564456] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    2.564473] sd 0:0:0:0: [sda] Write Protect is off
[    2.564476] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.564505] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.564509]  sda: sda1 sda2 < sda5 >
[    2.702260] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.702312] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.703065] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.703609] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    2.703620] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.703647] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.703652] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.703728] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.707645] ehci_hcd 0000:00:1d.7: debug port 1
[    2.707653] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.707670] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xa0040000
[    2.720009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.720104] usb usb1: configuration #1 chosen from 1 choice
[    2.720139] hub 1-0:1.0: USB hub found
[    2.720149] hub 1-0:1.0: 8 ports detected
[    2.720294] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.720314] uhci_hcd: USB Universal Host Controller Interface driver
[    2.720697] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.720703] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.720711] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.720715] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.720771] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.720805] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001820
[    2.720901] usb usb2: configuration #1 chosen from 1 choice
[    2.720930] hub 2-0:1.0: USB hub found
[    2.720939] hub 2-0:1.0: 2 ports detected
[    2.721506] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    2.721514] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.721521] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.721525] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.721573] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.721607] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840
[    2.721700] usb usb3: configuration #1 chosen from 1 choice
[    2.721729] hub 3-0:1.0: USB hub found
[    2.721737] hub 3-0:1.0: 2 ports detected
[    2.721833] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.721840] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.721844] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.721891] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.721925] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.722008] usb usb4: configuration #1 chosen from 1 choice
[    2.722041] hub 4-0:1.0: USB hub found
[    2.722049] hub 4-0:1.0: 2 ports detected
[    2.722136] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.722144] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.722148] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.722194] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.722218] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001880
[    2.722315] usb usb5: configuration #1 chosen from 1 choice
[    2.722344] hub 5-0:1.0: USB hub found
[    2.722353] hub 5-0:1.0: 2 ports detected
[    2.722521] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.730089] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.730095] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.730220] mice: PS/2 mouse device common for all mice
[    2.730401] rtc_cmos 00:06: RTC can wake from S4
[    2.730438] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.730472] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.730550] device-mapper: uevent: version 1.0.3
[    2.730666] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.730720] device-mapper: multipath: version 1.0.5 loaded
[    2.730723] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.730810] EISA: Probing bus 0 at eisa.0
[    2.730818] Cannot allocate resource for EISA slot 1
[    2.730821] Cannot allocate resource for EISA slot 2
[    2.730824] Cannot allocate resource for EISA slot 3
[    2.730827] Cannot allocate resource for EISA slot 4
[    2.730830] Cannot allocate resource for EISA slot 5
[    2.730833] Cannot allocate resource for EISA slot 6
[    2.730844] EISA: Detected 0 cards.
[    2.730930] cpuidle: using governor ladder
[    2.731004] cpuidle: using governor menu
[    2.731605] TCP cubic registered
[    2.731734] NET: Registered protocol family 10
[    2.732215] lo: Disabled Privacy Extensions
[    2.732583] NET: Registered protocol family 17
[    2.732603] Bluetooth: L2CAP ver 2.11
[    2.732605] Bluetooth: L2CAP socket layer initialized
[    2.732609] Bluetooth: SCO (Voice Link) ver 0.6
[    2.732611] Bluetooth: SCO socket layer initialized
[    2.732644] Bluetooth: RFCOMM socket layer initialized
[    2.732652] Bluetooth: RFCOMM TTY layer initialized
[    2.732655] Bluetooth: RFCOMM ver 1.10
[    2.733238] Using IPI No-Shortcut mode
[    2.733322] registered taskstats version 1
[    2.733454]   Magic number: 9:743:831
[    2.733463] scsi target0:0:0: hash matches
[    2.733540] rtc_cmos 00:06: setting system clock to 2009-09-25 10:49:23 UTC (1253875763)
[    2.733545] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.733547] EDD information not available.
[    2.733908] Freeing unused kernel memory: 532k freed
[    2.734044] Write protecting the kernel text: 4116k
[    2.734092] Write protecting the kernel read-only data: 1528k
[    2.738073] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.371676] tg3.c:v3.94 (August 14, 2008)
[    3.371697] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.371712] tg3 0000:02:00.0: setting latency timer to 64
[    3.413122] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:0a:e4:3b:3c:51
[    3.413128] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    3.413131] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.464118] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.640977] usb 3-1: configuration #1 chosen from 1 choice
[    3.706095] usbcore: registered new interface driver hiddev
[    3.710652] Marking TSC unstable due to TSC halts in idle
[    3.718103] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
[    3.718322] generic-usb 0003:03F0:0024.0001: input,hidraw0: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:1d.1-1/input0
[    3.718344] usbcore: registered new interface driver usbhid
[    3.718348] usbhid: v2.6:USB HID core driver
[    3.791790] PM: Starting manual resume from disk
[    3.791794] PM: Resume from partition 8:5
[    3.791796] PM: Checking hibernation image.
[    3.791993] PM: Resume from disk failed.
[    3.821160] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.821163] EXT3-fs: write access will be enabled during recovery.
[    3.880037] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    4.051728] usb 4-1: configuration #1 chosen from 1 choice
[    4.292032] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    4.466999] usb 4-2: configuration #1 chosen from 1 choice
[    5.753419] kjournald starting.  Commit interval 5 seconds
[    5.753438] EXT3-fs: sda1: orphan cleanup on readonly fs
[    5.753444] ext3_orphan_cleanup: deleting unreferenced inode 2892697
[    5.753486] ext3_orphan_cleanup: deleting unreferenced inode 3039989
[    5.753494] EXT3-fs: sda1: 2 orphan inodes deleted
[    5.753496] EXT3-fs: recovery complete.
[    5.784023] Clocksource tsc unstable (delta = -76447097 ns)
[    5.793814] EXT3-fs: mounted filesystem with ordered data mode.
[   15.593001] udev: starting version 141
[   15.843224] irda_init()
[   15.843239] NET: Registered protocol family 23
[   16.549604] nsc-ircc 00:09: activated
[   16.549610] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   16.549640] nsc-ircc, chip->init
[   16.549653] nsc-ircc, Found chip at base=0x164e
[   16.549690] nsc-ircc, driver loaded (Dag Brattli)
[   16.550521] IrDA: Registered device irda0
[   16.550524] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   16.559861] intel_rng: FWH not detected
[   16.579474] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   16.579611] usbcore: registered new interface driver btusb
[   16.647148] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6
[   16.649337] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.731300] ieee80211_crypt: registered algorithm 'NULL'
[   16.747740] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.747744] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.848185] Linux agpgart interface v0.103
[   17.054738] Non-volatile memory driver v1.2
[   17.143656] sdhci: Secure Digital Host Controller Interface driver
[   17.143660] sdhci: Copyright(c) Pierre Ossman
[   17.146306] sdhci-pci 0000:04:00.1: SDHCI controller found [1180:0822] (rev 13)
[   17.146328] sdhci-pci 0000:04:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.149478] mmc0: SDHCI controller on PCI [0000:04:00.1] using PIO
[   17.227581] yenta_cardbus 0000:04:00.0: CardBus bridge found [1014:0555]
[   17.253239] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.253243] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.268031] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   17.268756] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   17.272515] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   17.308323] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   17.325519] iTCO_vendor_support: vendor-support=0
[   17.327919] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   17.328089] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   17.328179] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.355474] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   17.355478] thinkpad_acpi: http://ibm-acpi.sf.net/
[   17.355481] thinkpad_acpi: ThinkPad BIOS 74ET64WW (2.09 ), EC 74HT27WW-1.02
[   17.355484] thinkpad_acpi: IBM ThinkPad X41, model 252563G
[   17.361021] yenta_cardbus 0000:04:00.0: ISA IRQ mask 0x0cb0, PCI irq 16
[   17.361026] yenta_cardbus 0000:04:00.0: Socket status: 30000006
[   17.361034] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x6fff
[   17.361038] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x6fff: clean.
[   17.362129] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xa0200000 - 0xafffffff
[   17.362133] yenta_cardbus 0000:04:00.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd7ffffff
[   17.365485] ipw2200 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.365901] Registered led device: tpacpi::thinklight
[   17.366093] thinkpad_acpi: acpi_bus_get_device(bay) failed: -19
[   17.366098] thinkpad_acpi: disabling subdriver bay
[   17.366161] Registered led device: tpacpi::power
[   17.366207] Registered led device: tpacpi:orange:batt
[   17.366270] Registered led device: tpacpi:green:batt
[   17.366317] Registered led device: tpacpi::dock_active
[   17.366362] Registered led device: tpacpi::bay_active
[   17.366407] Registered led device: tpacpi::dock_batt
[   17.366454] Registered led device: tpacpi::unknown_led
[   17.366500] Registered led device: tpacpi::standby
[   17.367351] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   17.367452] ipw2200 0000:04:02.0: firmware: requesting ipw2200-bss.fw
[   17.368657] thinkpad_acpi: CMOS NVRAM (7) and EC (0) do not agree on display brightness level
[   17.369015] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   17.417855] mmc0: new SDHC card at address 8fe4
[   17.468861] psmouse serio1: ID: 10 00 64<6>ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
[   17.703659] mmcblk0: mmc0:8fe4 SD08G 7.40 GiB 
[   17.703737]  mmcblk0: p1
[   18.042732] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   18.056598] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input8
[   18.060372] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   18.062140] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.062886] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   18.063503] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   18.064316] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.104033] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.104200] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   19.028035] intel8x0_measure_ac97_clock: measured 55442 usecs
[   19.028038] intel8x0: clocking to 48000
[   19.280469] lp: driver loaded but no devices found
[   19.350553] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
[   19.898666] EXT3 FS on sda1, internal journal
[   21.289748] type=1505 audit(1253875782.054:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2023
[   21.354113] type=1505 audit(1253875782.118:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2027
[   21.354262] type=1505 audit(1253875782.118:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2027
[   21.354323] type=1505 audit(1253875782.118:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2027
[   21.354375] type=1505 audit(1253875782.118:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2027
[   21.544344] type=1505 audit(1253875782.310:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2032
[   21.544644] type=1505 audit(1253875782.310:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2032
[   21.581055] type=1505 audit(1253875782.346:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2036
[   23.613920] RPC: Registered udp transport module.
[   23.613924] RPC: Registered tcp transport module.
[   23.696202] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   23.800414] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   23.814554] NFSD: starting 90-second grace period
[   23.979756] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   23.979760] vboxdrv: Successfully done.
[   23.979762] vboxdrv: Found 1 processor cores.
[   23.979892] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   23.979895] vboxdrv: Successfully loaded version 3.0.4 (interface 0x000e0000).
[   25.804227] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.804231] Bluetooth: BNEP filters: protocol multicast
[   26.094396] Bridge firewalling registered
[   27.704024] ppdev: user-space parallel port driver
[   28.678727] [drm] Initialized drm 1.1.0 20060810
[   28.688447] pci 0000:00:02.0: power state changed by ACPI to D0
[   28.688460] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.688469] pci 0000:00:02.0: setting latency timer to 64
[   28.688714] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   28.794218] [drm:i915_setparam] *ERROR* unknown parameter 4
[   28.794247] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   30.418067] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   31.412233] hci_cmd_task: hci0 command tx timeout
[   31.417922] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.904028] eth1: no IPv6 routers present
[   67.704719] ieee80211_crypt: registered algorithm 'CCMP'
[   68.321246] padlock: VIA PadLock not detected.
[   68.420279] ieee80211_crypt: registered algorithm 'TKIP'
[  114.516053] usb 1-4: new high speed USB device using ehci_hcd and address 5
[  114.697621] usb 1-4: configuration #1 chosen from 1 choice
[  114.896207] Initializing USB Mass Storage driver...
[  114.966154] scsi2 : SCSI emulation for USB Mass Storage devices
[  114.983268] usb-storage: device found at 5
[  114.983277] usb-storage: waiting for device to settle before scanning
[  114.985239] scsi3 : SCSI emulation for USB Mass Storage devices
[  115.004419] usbcore: registered new interface driver usb-storage
[  115.004432] USB Mass Storage support registered.
[  115.053308] usb-storage: device found at 5
[  115.053316] usb-storage: waiting for device to settle before scanning
[  119.992149] usb-storage: device scan complete
[  119.992822] scsi 2:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  120.003389] sr0: scsi-1 drive
[  120.003398] Uniform CD-ROM driver Revision: 3.20
[  120.003627] sr 2:0:0:0: Attached scsi CD-ROM sr0
[  120.003803] sr 2:0:0:0: Attached scsi generic sg1 type 5
[  120.135099] usb-storage: device scan complete
[  120.136543] scsi 3:0:0:0: Direct-Access     HUAWEI   TF CARD Storage       PQ: 0 ANSI: 2
[  120.138713] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  120.138876] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  131.262396] ISO 9660 Extensions: Microsoft Joliet Level 1
[  131.263390] ISOFS: changing to secondary root
[  762.686589] [drm:i915_getparam] *ERROR* Unknown parameter 6

```

---

### Post by GeorgeVita on 2009-09-25
Hi **qhrille**,
at your **dmesg** you can see the virtual CDROM created as **sr0** what if eject it: ```
sudo eject sr0
``` do you have a new **lsusb** respond? Try again network manager after eject and post here the results to follow up.

Regards,
George

---

### Post by qhrille on 2009-09-26
Hi GeorgeVita

Thank you for your reply

I've tried both:
```

sudo eject sr0

```

and
```

sudo umount /media/Mobile\ Partner

```

Both commands resulted in this:

lsusb
```

Bus 001 Device 008: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0a5c:201e Broadcom Corp. IBM Integrated Bluetooth IV
Bus 004 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Regards 
qhrille

---

### Post by GeorgeVita on 2009-09-26
Hi **qhrille**,
your case seems to be similar with that 'solved' at:
[http://ubuntuforums.org/showpost.php?p=7622263&postcount=3](http://ubuntuforums.org/showpost.php?p=7622263&postcount=3)

You must install **udev-extras** and add a new rule to turn your device to modem mode. There is described a long command that 'copies' data to the created file. After reboot it can be possibly used (via network manager).

Regards,
George

---

### Post by ddrichardson on 2009-09-26
It shouldn't need reboot - just restart udev.

---

### Post by mikecanada on 2010-02-07
Did you ever get the Huawei E182E internet key to work ?

Just replace my working Sierra Wireless 597 with same E182E,thinking now it,s a winmodem device only. Also was told the new Telus 306 won,t work with Ubuntu either.

The Huawei web site says,s the E182E is a linux device,strange

                       Cheers Mike.... maybe should build a list of internet sticks we know won,t work with linux seems Rogers Rocket Stick is no good either

---

