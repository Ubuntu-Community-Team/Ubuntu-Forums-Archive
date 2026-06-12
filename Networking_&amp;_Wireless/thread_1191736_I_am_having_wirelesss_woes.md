---
title: "I am having wirelesss woes"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by Zom-b on 2009-06-19
so I have been working on fixing up this laptop, got all the parts and got it up and running, and it needed an operating system, so I naturally decided to put some xubuntu on it, everything works well except that it doesn't seem to want to use wireless, I have teh restricted drivers installed and in use, give me a few minutes and I will be adding some readouts
since the dmesg is too big I'll just add it as code
```

zomb@zomb-laptop:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009 (Ubuntu 2.6.28-13.44-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eff000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x37ef0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000037ef0000 (usable)
[    0.000000]  modified: 0000000037ef0000 - 0000000037eff000 (ACPI data)
[    0.000000]  modified: 0000000037eff000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  modified: 0000000037f00000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 377a2000 - 37edf700
[    0.000000] Allocated new RAMDISK: 0087b000 - 00fb8700
[    0.000000] Move RAMDISK from 00000000377a2000 - 0000000037edf6ff to 0087b000 - 00fb86ff
[    0.000000] ACPI: RSDP 000F8080, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 37EF8BF0, 0034 (r1 HP     3091     20040830  LTP        0)
[    0.000000] ACPI: FACP 37EFEE4B, 0074 (r1 HP     3091     20040830 PTL        5F)
[    0.000000] ACPI: DSDT 37EF8C24, 6227 (r1 HP     3091     20040830 MSFT  100000E)
[    0.000000] ACPI: FACS 37EFFFC0, 0040
[    0.000000] ACPI: SSDT 37EFEEBF, 00B5 (r1 PTLTD  POWERNOW 20040830  LTP        1)
[    0.000000] ACPI: APIC 37EFEF74, 0050 (r1 PTLTD  	 3091   20040830  LTP        0)
[    0.000000] ACPI: MCFG 37EFEFC4, 003C (r1 PTLTD    MCFG   20040830  LTP        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 10MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087b000 - 0000fb8700]      NEW RAMDISK ==> [000087b000 - 0000fb8700]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f8130] 000f8130
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x00037ef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x00037ef0
[    0.000000] On node 0 totalpages: 228981
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 22 pages used for memmap
[    0.000000]   HighMem zone: 2780 pages, LIFO batch:0
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] SB4X0 revision 0x11
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227191
[    0.000000] Kernel command line: root=UUID=a01d429a-3f1f-4e81-99b5-952faed273e3 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1591.977 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 4582080 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 888144k/916416k available (4110k kernel code, 27608k reserved, 2197k data, 532k init, 11208k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05039df   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3183.95 BogoMIPS (lpj=6367908)
[    0.004030] Security Framework initialized
[    0.004037] SELinux:  Disabled at boot.
[    0.004059] AppArmor: AppArmor initialized
[    0.004068] Mount-cache hash table entries: 512
[    0.004196] Initializing cgroup subsys ns
[    0.004200] Initializing cgroup subsys cpuacct
[    0.004203] Initializing cgroup subsys memory
[    0.004207] Initializing cgroup subsys freezer
[    0.004220] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004223] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004235] Checking 'hlt' instruction... OK.
[    0.020625] SMP alternatives: switching to UP code
[    0.164155] Freeing SMP alternatives: 18k freed
[    0.164160] ACPI: Core revision 20080926
[    0.166812] ACPI: Checking initramfs for custom DSDT
[    0.536533] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.578339] CPU0: AMD Turion(tm) 64 Mobile Technology ML-28 stepping 02
[    0.580002] Brought up 1 CPUs
[    0.580002] Total of 1 processors activated (3183.95 BogoMIPS).
[    0.580002] CPU0 attaching NULL sched-domain.
[    0.580002] net_namespace: 776 bytes
[    0.580002] Booting paravirtualized kernel on bare hardware
[    0.580002] Time: 13:11:44  Date: 06/19/09
[    0.580002] regulator: core version 0.5
[    0.580002] NET: Registered protocol family 16
[    0.580002] EISA bus registered
[    0.580002] ACPI: bus type pci registered
[    0.580002] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.580002] PCI: Not using MMCONFIG.
[    0.580002] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=5
[    0.580002] PCI: Using configuration type 1 for base access
[    0.580002] ACPI: EC: Look up EC in DSDT
[    0.582077] ACPI: Interpreter enabled
[    0.582081] ACPI: (supports S0 S3 S4 S5)
[    0.582101] ACPI: Using IOAPIC for interrupt routing
[    0.582254] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.583396] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.583474] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.583474] PCI: Using MMCONFIG for extended config space
[    0.588489] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.588491] ACPI: EC: driver started in interrupt mode
[    0.588609] ACPI: No dock devices found.
[    0.588619] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.588763] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0000000-0xc0000fff]
[    0.588865] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0001000-0xc0001fff]
[    0.588974] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0002000-0xc0002fff]
[    0.589028] pci 0000:00:13.2: supports D1 D2
[    0.589032] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.589038] pci 0000:00:13.2: PME# disabled
[    0.589096] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
[    0.592004] pci 0000:00:14.0: reg 14 32bit mmio: [0xc0003000-0xc00033ff]
[    0.592044] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.592099] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.592108] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.592117] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
[    0.592126] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
[    0.592135] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
[    0.592317] pci 0000:00:14.5: reg 10 32bit mmio: [0xc0003400-0xc00034ff]
[    0.592415] pci 0000:00:14.6: reg 10 32bit mmio: [0xc0003800-0xc00038ff]
[    0.592574] pci 0000:01:05.0: reg 10 32bit mmio: [0xc8000000-0xcfffffff]
[    0.592578] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.592584] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.592595] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.592601] pci 0000:01:05.0: supports D1 D2
[    0.592620] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.592624] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.592629] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xcfffffff]
[    0.592684] pci 0000:05:00.0: reg 10 io port: [0xa000-0xa0ff]
[    0.592696] pci 0000:05:00.0: reg 14 32bit mmio: [0xc0208000-0xc02080ff]
[    0.592753] pci 0000:05:00.0: supports D1 D2
[    0.592756] pci 0000:05:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.592762] pci 0000:05:00.0: PME# disabled
[    0.592801] pci 0000:05:02.0: reg 10 32bit mmio: [0xc0204000-0xc0205fff]
[    0.592923] pci 0000:05:09.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.592939] pci 0000:05:09.0: supports D1 D2
[    0.592941] pci 0000:05:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.592948] pci 0000:05:09.0: PME# disabled
[    0.593008] pci 0000:05:09.2: reg 10 32bit mmio: [0xc0208800-0xc0208fff]
[    0.593019] pci 0000:05:09.2: reg 14 32bit mmio: [0xc0200000-0xc0203fff]
[    0.593081] pci 0000:05:09.2: supports D1 D2
[    0.593083] pci 0000:05:09.2: PME# supported from D0 D1 D2 D3hot
[    0.593089] pci 0000:05:09.2: PME# disabled
[    0.593146] pci 0000:05:09.3: reg 10 32bit mmio: [0xc0206000-0xc0207fff]
[    0.593212] pci 0000:05:09.3: supports D1 D2
[    0.593214] pci 0000:05:09.3: PME# supported from D0 D1 D2 D3hot
[    0.593220] pci 0000:05:09.3: PME# disabled
[    0.593276] pci 0000:05:09.4: reg 10 32bit mmio: [0xc0209400-0xc02094ff]
[    0.593288] pci 0000:05:09.4: reg 14 32bit mmio: [0xc0209000-0xc02090ff]
[    0.593299] pci 0000:05:09.4: reg 18 32bit mmio: [0xc0208400-0xc02084ff]
[    0.593349] pci 0000:05:09.4: supports D1 D2
[    0.593351] pci 0000:05:09.4: PME# supported from D0 D1 D2 D3hot
[    0.593358] pci 0000:05:09.4: PME# disabled
[    0.593421] pci 0000:00:14.4: transparent bridge
[    0.593430] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.593436] pci 0000:00:14.4: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.593481] bus 00 -> node 0
[    0.593487] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.593671] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.593831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.595726] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.595860] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.595991] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.596129] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.596258] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.596390] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.596522] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.596651] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.596795] ACPI: WMI: Mapper loaded
[    0.596991] SCSI subsystem initialized
[    0.597036] libata version 3.00 loaded.
[    0.597085] usbcore: registered new interface driver usbfs
[    0.597105] usbcore: registered new interface driver hub
[    0.597134] usbcore: registered new device driver usb
[    0.597250] PCI: Using ACPI for IRQ routing
[    0.597378] Bluetooth: Core ver 2.13
[    0.597378] NET: Registered protocol family 31
[    0.597378] Bluetooth: HCI device and connection manager initialized
[    0.597378] Bluetooth: HCI socket layer initialized
[    0.597378] NET: Registered protocol family 8
[    0.597378] NET: Registered protocol family 20
[    0.597378] NetLabel: Initializing
[    0.597378] NetLabel:  domain hash size = 128
[    0.597378] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.597378] NetLabel:  unlabeled traffic allowed by default
[    0.597378] AppArmor: AppArmor Filesystem Enabled
[    0.597378] pnp: PnP ACPI init
[    0.597378] ACPI: bus type pnp registered
[    0.598287] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.600402] pnp: PnP ACPI: found 10 devices
[    0.600404] ACPI: ACPI bus type pnp unregistered
[    0.600408] PnPBIOS: Disabled by ACPI PNP
[    0.600418] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.600422] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.600425] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.600434] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.600437] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.600440] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.600443] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.600447] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.600450] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.600453] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.600456] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.600459] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.600462] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.600465] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.600468] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.600472] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.600475] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.600478] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.600481] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.600485] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.600491] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.600495] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.635231] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.635234] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.635239] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.635242] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff
[    0.635255] pci 0000:05:09.0: CardBus bridge, secondary bus 0000:06
[    0.635258] pci 0000:05:09.0:   IO window: 0x00a400-0x00a4ff
[    0.635264] pci 0000:05:09.0:   IO window: 0x00a800-0x00a8ff
[    0.635271] pci 0000:05:09.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.635277] pci 0000:05:09.0:   MEM window: 0x54000000-0x57ffffff
[    0.635284] pci 0000:00:14.4: PCI bridge, secondary bus 0000:05
[    0.635288] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.635295] pci 0000:00:14.4:   MEM window: 0xc0200000-0xc02fffff
[    0.635301] pci 0000:00:14.4:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.635333] pci 0000:05:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.635340] pci 0000:05:09.0: setting latency timer to 64
[    0.635347] bus: 00 index 0 io port: [0x00-0xffff]
[    0.635349] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.635352] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.635355] bus: 01 index 1 mmio: [0xc0100000-0xc01fffff]
[    0.635357] bus: 01 index 2 mmio: [0xc8000000-0xcfffffff]
[    0.635360] bus: 01 index 3 mmio: [0x0-0x0]
[    0.635362] bus: 05 index 0 io port: [0xa000-0xafff]
[    0.635364] bus: 05 index 1 mmio: [0xc0200000-0xc02fffff]
[    0.635367] bus: 05 index 2 mmio: [0x50000000-0x53ffffff]
[    0.635369] bus: 05 index 3 io port: [0x00-0xffff]
[    0.635372] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    0.635374] bus: 06 index 0 io port: [0xa400-0xa4ff]
[    0.635377] bus: 06 index 1 io port: [0xa800-0xa8ff]
[    0.635379] bus: 06 index 2 mmio: [0x50000000-0x53ffffff]
[    0.635382] bus: 06 index 3 mmio: [0x54000000-0x57ffffff]
[    0.635394] NET: Registered protocol family 2
[    0.635510] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.635902] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.637036] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.637644] TCP: Hash tables configured (established 131072 bind 65536)
[    0.637647] TCP reno registered
[    0.637781] NET: Registered protocol family 1
[    0.637944] checking if image is initramfs... it is
[    1.136009] Switched to high resolution mode on CPU 0
[    1.401296] Freeing initrd memory: 7413k freed
[    1.401421] cpufreq: No nForce2 chipset.
[    1.401574] audit: initializing netlink socket (disabled)
[    1.401598] type=2000 audit(1245417104.400:1): initialized
[    1.411305] highmem bounce pool size: 64 pages
[    1.411312] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.412674] VFS: Disk quotas dquot_6.5.1
[    1.412741] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.413399] fuse init (API version 7.10)
[    1.413484] msgmni has been set to 1727
[    1.413676] alg: No test for stdrng (krng)
[    1.413689] io scheduler noop registered
[    1.413691] io scheduler anticipatory registered
[    1.413694] io scheduler deadline registered
[    1.413711] io scheduler cfq registered (default)
[    1.413720] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    2.080047] pci 0000:01:05.0: Boot video device
[    2.080161] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.080170] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.082996] ACPI: AC Adapter [ACAD] (on-line)
[    2.083615] ACPI: Battery Slot [BAT1] (battery absent)
[    2.083698] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.083702] ACPI: Power Button (FF) [PWRF]
[    2.083751] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.083753] ACPI: Power Button (CM) [PWRB]
[    2.083801] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.083804] ACPI: Sleep Button (CM) [SLPB]
[    2.083855] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    2.084314] ACPI: Lid Switch [LID]
[    2.084486] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.084512] processor ACPI_CPU:00: registered as cooling_device0
[    2.084516] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.087348] thermal LNXTHERM:01: registered as thermal_zone0
[    2.088520] ACPI: Thermal Zone [THRM] (98 C)
[    2.088569] isapnp: Scanning for PnP cards...
[    2.444078] isapnp: No Plug & Play device found
[    2.445596] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.446005] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.446013] serial 0000:00:14.6: PCI INT B disabled
[    2.446932] brd: module loaded
[    2.447343] loop: module loaded
[    2.447443] Fixed MDIO Bus: probed
[    2.447450] PPP generic driver version 2.4.2
[    2.447544] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.447578] Driver 'sd' needs updating - please use bus_type methods
[    2.447588] Driver 'sr' needs updating - please use bus_type methods
[    2.447961] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.448042] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    2.448193] scsi0 : pata_atiixp
[    2.448324] scsi1 : pata_atiixp
[    2.450064] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    2.450067] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    2.614550] ata1.00: ATA-8: SAMSUNG HM160HC, LQ100-10, max UDMA/100
[    2.614554] ata1.00: 312581808 sectors, multi 16: LBA48 
[    2.630481] ata1.00: configured for UDMA/100
[    2.792662] ata2.00: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CC15, max MWDMA2
[    2.808644] ata2.00: configured for MWDMA2
[    2.811058] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HC  LQ10 PQ: 0 ANSI: 5
[    2.811177] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.811201] sd 0:0:0:0: [sda] Write Protect is off
[    2.811204] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.811236] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.811321] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.811341] sd 0:0:0:0: [sda] Write Protect is off
[    2.811344] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.811373] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.811377]  sda: sda1 sda2 < sda5 >
[    2.868197] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.868266] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.872299] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CC15 PQ: 0 ANSI: 5
[    2.883869] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.883872] Uniform CD-ROM driver Revision: 3.20
[    2.883994] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.884043] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.884656] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.884690] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.884733] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.884828] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.884919] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[    2.896009] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.896099] usb usb1: configuration #1 chosen from 1 choice
[    2.896136] hub 1-0:1.0: USB hub found
[    2.896146] hub 1-0:1.0: 8 ports detected
[    2.896330] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.896345] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.896364] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.896411] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.896437] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[    2.956074] usb usb2: configuration #1 chosen from 1 choice
[    2.956105] hub 2-0:1.0: USB hub found
[    2.956118] hub 2-0:1.0: 4 ports detected
[    2.956241] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.956253] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.956307] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.956324] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[    3.016081] usb usb3: configuration #1 chosen from 1 choice
[    3.016114] hub 3-0:1.0: USB hub found
[    3.016132] hub 3-0:1.0: 4 ports detected
[    3.016254] uhci_hcd: USB Universal Host Controller Interface driver
[    3.016369] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    3.018301] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.018306] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.018444] mice: PS/2 mouse device common for all mice
[    3.018688] rtc_cmos 00:04: RTC can wake from S4
[    3.018735] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.018772] rtc0: alarms up to one month, 114 bytes nvram
[    3.018859] device-mapper: uevent: version 1.0.3
[    3.019017] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.019084] device-mapper: multipath: version 1.0.5 loaded
[    3.019087] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.019189] EISA: Probing bus 0 at eisa.0
[    3.019199] Cannot allocate resource for EISA slot 1
[    3.019242] Cannot allocate resource for EISA slot 8
[    3.019244] EISA: Detected 0 cards.
[    3.019315] cpuidle: using governor ladder
[    3.019374] cpuidle: using governor menu
[    3.020106] TCP cubic registered
[    3.020240] NET: Registered protocol family 10
[    3.020806] lo: Disabled Privacy Extensions
[    3.021240] NET: Registered protocol family 17
[    3.021265] Bluetooth: L2CAP ver 2.11
[    3.021267] Bluetooth: L2CAP socket layer initialized
[    3.021270] Bluetooth: SCO (Voice Link) ver 0.6
[    3.021272] Bluetooth: SCO socket layer initialized
[    3.021304] Bluetooth: RFCOMM socket layer initialized
[    3.021314] Bluetooth: RFCOMM TTY layer initialized
[    3.021316] Bluetooth: RFCOMM ver 1.10
[    3.021349] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-28 processors (1 cpu cores) (version 2.20.00)
[    3.021403] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4
[    3.021406] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
[    3.021461] Using IPI No-Shortcut mode
[    3.021562] registered taskstats version 1
[    3.021736]   Magic number: 13:421:180
[    3.021879] rtc_cmos 00:04: setting system clock to 2009-06-19 13:11:47 UTC (1245417107)
[    3.021883] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.021885] EDD information not available.
[    3.022510] Freeing unused kernel memory: 532k freed
[    3.022713] Write protecting the kernel text: 4112k
[    3.022782] Write protecting the kernel read-only data: 1524k
[    3.059836] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.596479] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.596520] 8139cp 0000:05:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.600312] 8139too Fast Ethernet driver 0.9.28
[    3.600371] 8139too 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.602609] eth0: RealTek RTL8139 at 0xa000, 00:c0:9f:cc:7a:35, IRQ 18
[    3.602618] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.614368] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.672111] ssb: Sonics Silicon Backplane found on PCI device 0000:05:02.0
[    3.683604] ohci1394 0000:05:09.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.733506] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c0208800-c0208fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.091200] Marking TSC unstable due to TSC halts in idle
[    4.126904] PM: Starting manual resume from disk
[    4.126908] PM: Resume from partition 8:5
[    4.126910] PM: Checking hibernation image.
[    4.127142] PM: Resume from disk failed.
[    4.180086] kjournald starting.  Commit interval 5 seconds
[    4.180099] EXT3-fs: mounted filesystem with ordered data mode.
[    5.068163] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00006ba8f1]
[    9.497606] udev: starting version 141
[    9.795867] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0e/device:0f/input/input6
[    9.820199] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    9.850804] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.237159] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   10.244394] Linux agpgart interface v0.103
[   10.253269] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   10.308365] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.316669] sdhci: Secure Digital Host Controller Interface driver
[   10.316673] sdhci: Copyright(c) Pierre Ossman
[   10.318772] sdhci-pci 0000:05:09.4: SDHCI controller found [104c:8034] (rev 0)
[   10.318795] sdhci-pci 0000:05:09.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.318998] mmc0: SDHCI controller on PCI [0000:05:09.4] using PIO
[   10.319067] mmc1: SDHCI controller on PCI [0000:05:09.4] using PIO
[   10.319167] mmc2: SDHCI controller on PCI [0000:05:09.4] using PIO
[   10.429150] yenta_cardbus 0000:05:09.0: CardBus bridge found [103c:3091]
[   10.429179] yenta_cardbus 0000:05:09.0: Enabling burst memory read transactions
[   10.429186] yenta_cardbus 0000:05:09.0: Using CSCINT to route CSC interrupts to PCI
[   10.429189] yenta_cardbus 0000:05:09.0: Routing CardBus interrupts to PCI
[   10.429196] yenta_cardbus 0000:05:09.0: TI: mfunc 0x01a01b22, devctl 0x64
[   10.449199] cfg80211: Calling CRDA to update world regulatory domain
[   10.545650] cfg80211: World regulatory domain updated:
[   10.545656] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.545660] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.545663] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.545666] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.545669] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.545672] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.661178] yenta_cardbus 0000:05:09.0: ISA IRQ mask 0x0ee8, PCI irq 17
[   10.661185] yenta_cardbus 0000:05:09.0: Socket status: 30000006
[   10.661191] pci_bus 0000:05: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   10.661199] yenta_cardbus 0000:05:09.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   10.661204] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[   10.661453] yenta_cardbus 0000:05:09.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   10.661458] yenta_cardbus 0000:05:09.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   10.661998] tifm_7xx1 0000:05:09.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.705166] b43-phy0: Broadcom 4318 WLAN found
[   10.769918] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.778188] phy0: Selected rate control algorithm 'pid'
[   10.821446] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   10.880080] MC'97 0 converters and GPIO not ready (0x1)
[   10.881587] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.029343] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.031764] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   11.032787] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.033615] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.034508] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.154013] lp: driver loaded but no devices found
[   11.287659] Adding 2626588k swap on /dev/sda5.  Priority:-1 extents:1 across:2626588k
[   11.308981] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   11.349591] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   11.830468] EXT3 FS on sda1, internal journal
[   12.977721] type=1505 audit(1245417117.454:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1948
[   12.977929] type=1505 audit(1245417117.454:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1948
[   12.977995] type=1505 audit(1245417117.454:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1948
[   12.978058] type=1505 audit(1245417117.454:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1948
[   13.177734] type=1505 audit(1245417117.654:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1953
[   13.178035] type=1505 audit(1245417117.654:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1953
[   13.215495] type=1505 audit(1245417117.690:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1957
[   15.666298] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.666302] Bluetooth: BNEP filters: protocol multicast
[   15.686738] Bridge firewalling registered
[   16.819724] pci 0000:01:05.0: power state changed by ACPI to D0
[   16.819740] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.940560] [drm] Initialized drm 1.1.0 20060810
[   16.977363] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   17.351297] ppdev: user-space parallel port driver
[   17.475902] [drm] Setting GART location based on new memory map
[   17.476622] [drm] Loading R300 Microcode
[   17.476644] [drm] Num pipes: 2
[   17.476651] [drm] writeback test succeeded in 1 usecs
[   20.523163] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   20.571621] input: b43-phy0 as /devices/virtual/input/input9
[   20.624085] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   20.817833] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   20.857111] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   20.984390] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   21.116062] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   21.165798] Registered led device: b43-phy0::radio
[   21.195360] b43-phy0: Radio turned on by software
[   21.195800] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.576066] b43-phy0: Radio hardware status changed to DISABLED
[   21.644066] b43-phy0: Radio turned on by software
[   21.644072] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   30.604041] eth0: no IPv6 routers present
[   40.632038] Clocksource tsc unstable (delta = -224499016 ns)
[  675.238216] eth0: link down
[ 1115.433728] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

```

---

### Post by Ayuthia on 2009-06-19
> [   21.644072] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.

This says that the wireless card is currently off.  Can you try flipping the wireless switch a few times to see if it activates it?  If it does not, please try:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo iwlist scan
```

It looks like that some 4318 cards are not turning on for some reason.

---

### Post by Zom-b on 2009-06-19
> **Ayuthia said:**
> This says that the wireless card is currently off.  Can you try flipping the wireless switch a few times to see if it activates it?  If it does not, please try:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo iwlist scan
```

It looks like that some 4318 cards are not turning on for some reason.

it's not a switch, it's a button, but it's not lit up with the regular network manager, but when I had wicd installed it lit up, it still didn't work with that though

and the output for those commands:
```

zomb@zomb-laptop:~$ sudo modprobe -r b43 ssb
[sudo] password for zomb: 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
zomb@zomb-laptop:~$ sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
zomb@zomb-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


```

nvm wlan0 is showing up again

---

