---
title: "XBMCBuntu wireless issue"
date: 2012-04-15
forum: Networking &amp; Wireless
---

### Post by rhossack on 2012-04-15
I just installed the 64bit version of XBMCBuntu and cannot connect to my router via wireless connection.

It just keeps recycling the message saying that I'm now disconnected and never connects.

It was working fine with SalineOS but cannot connect to my router.   Any help would be appreciated.

---

### Post by Jose Catre-Vandis on 2012-04-15
ifconfig output needed
iwconfig output needed
dmesg output needed
lshw -c network output needed

will it connect OK with a wired connection ?

---

### Post by rhossack on 2012-04-15
> **Jose Catre-Vandis said:**
> ifconfig output needed
Thanks for the quick reply.
I ran the ifconfig report and then copied it to the desktop but I can't find an editor in XMBCbuntu to open the file so I can paste it to this message.
> 
iwconfig output needed
dmesg output needed
lshw -c network output needed
I have since found a work around to my issue.  If I click on the icon and choose to create a new network and type in the name of the existing one it will connect.
> will it connect OK with a wired connection ?
I did not try that but since I have my hdhomerun hooked to the router and it sees that I'm assuming it works.

Let me see about an editor for this so I can do somme cut and paste of the codes generated.

Thanks,
Ron

---

### Post by rhossack on 2012-04-15
> **Jose Catre-Vandis said:**
> ifconfig output needed
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:00:a3:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:02:72:ae:58:4e  
          inet6 addr: fe80::202:72ff:feae:584e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:27 overruns:0 frame:0
          TX packets:95 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7040 (7.0 KB)  TX bytes:30881 (30.8 KB)

> iwconfig output needed
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by rhossack on 2012-04-15
> **Jose Catre-Vandis said:**
> 
dmesg output needed
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@zirconium) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 (Ubuntu 3.0.0-16.29-generic 3.0.20)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000098400 (usable)
[    0.000000]  BIOS-e820: 0000000000098400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fc91000 (usable)
[    0.000000]  BIOS-e820: 000000007fcf0000 - 000000007fcf3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fcf3000 - 000000007fd00000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fd00000 - 000000007fe00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Gigabyte Technology Co., Ltd. GA-MA785GM-US2H/GA-MA785GM-US2H, BIOS F12a 07/08/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fc91 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 00007FD00000 mask FFFFFFF00000 uncachable
[    0.000000]   2 base 00007FE00000 mask FFFFFFE00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2045MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2046MB, range: 2MB, type UC
[    0.000000] total RAM covered: 2045M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 4M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2045MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2046MB, range: 2MB, type UC
[    0.000000] found SMP MP-table at [c00f56b0] f56b0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0094000] 94000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35a40000 - 36d18000
[    0.000000] ACPI: RSDP 000f7070 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 7fcf3000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 7fcf3040 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 7fcf30c0 074DB (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 7fcf0000 00040
[    0.000000] ACPI: SSDT 7fcfa680 0095E (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: HPET 7fcfb000 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 7fcfb040 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: APIC 7fcfa5c0 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1156MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fc91
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000098
[    0.000000]     0: 0x00000100 -> 0x0007fc91
[    0.000000] On node 0 totalpages: 523289
[    0.000000] free_area_init_node: node 0, pgdat c17b54c0, node_mem_map f4a40200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3944 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2314 pages used for memmap
[    0.000000]   HighMem zone: 293769 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000098000 - 0000000000099000
[    0.000000] PM: Registered nosave memory: 0000000000099000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7fe00000 (gap: 7fe00000:60200000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f7000000 s26240 r0 d22912 u524288
[    0.000000] pcpu-alloc: s26240 r0 d22912 u524288 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519199
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=9577e646-4678-46dc-9dd1-3f7949525f28 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8374288 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fc91)
[    0.000000] Memory: 2038508k/2093636k available (5340k kernel code, 54648k reserved, 2596k data, 696k init, 1184332k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17c1000 - 0xc186f000   ( 696 kB)
[    0.000000]       .data : 0xc1537104 - 0xc17c0140   (2596 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1537104   (5340 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f3c0a000 soft=f3c0c000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2812.658 MHz processor.
[    0.008004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5625.31 BogoMIPS (lpj=11250632)
[    0.008009] pid_max: default: 32768 minimum: 301
[    0.008029] Security Framework initialized
[    0.008044] AppArmor: AppArmor initialized
[    0.008045] Yama: becoming mindful.
[    0.008096] Mount-cache hash table entries: 512
[    0.008209] Initializing cgroup subsys cpuacct
[    0.008215] Initializing cgroup subsys memory
[    0.008222] Initializing cgroup subsys devices
[    0.008224] Initializing cgroup subsys freezer
[    0.008227] Initializing cgroup subsys net_cls
[    0.008229] Initializing cgroup subsys blkio
[    0.008235] Initializing cgroup subsys perf_event
[    0.008257] CPU: Physical Processor ID: 0
[    0.008259] CPU: Processor Core ID: 0
[    0.008262] mce: CPU supports 6 MCE banks
[    0.008270] using AMD E400 aware idle routine
[    0.012637] ACPI: Core revision 20110413
[    0.016026] ftrace: allocating 24901 entries in 49 pages
[    0.020070] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020636] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063579] CPU0: AMD Athlon(tm) II X2 240 Processor stepping 02
[    0.064003] Performance Events: AMD PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      4
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000000f
[    0.064003] CPU 1 irqstacks, hard=f3cb8000 soft=f3cba000
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 94000
[    0.012000] Initializing CPU#1
[    0.152018] Brought up 2 CPUs
[    0.152020] Total of 2 processors activated (11250.76 BogoMIPS).
[    0.152018] System has AMD C1E enabled
[    0.152042] Switch to broadcast mode on CPU1
[    0.152509] Switch to broadcast mode on CPU0
[    0.152509] devtmpfs: initialized
[    0.152509] PM: Registering ACPI NVS region at 7fcf0000 (12288 bytes)
[    0.153486] print_constraints: dummy: 
[    0.153507] Time:  2:44:59  Date: 04/16/12
[    0.153538] NET: Registered protocol family 16
[    0.153614] EISA bus registered
[    0.153618] node 0 link 0: io port [c000, ffff]
[    0.153621] TOM: 0000000080000000 aka 2048M
[    0.153623] Fam 10h mmconf [mem 0xe0000000-0xe00fffff]
[    0.153626] node 0 link 0: mmio [a0000, bffff]
[    0.153628] node 0 link 0: mmio [80000000, dfffffff]
[    0.153631] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.153633] node 0 link 0: mmio [e0000000, e03fffff] ==> [e0100000, e03fffff]
[    0.153636] bus: [00, 03] on node 0 link 0
[    0.153638] bus: 00 index 0 [io  0x0000-0xffff]
[    0.153546] Trying to unpack rootfs image as initramfs...
[    0.153643] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.153645] bus: 00 index 2 [mem 0x80000000-0xdfffffff]
[    0.153647] bus: 00 index 3 [mem 0xe0400000-0xffffffff]
[    0.153648] bus: 00 index 4 [mem 0xe0100000-0xe03fffff]
[    0.153657] Extended Config Space enabled on 1 nodes
[    0.153663] ACPI: bus type pci registered
[    0.153713] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.153716] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.153717] PCI: Using MMCONFIG for extended config space
[    0.153719] PCI: Using configuration type 1 for base access
[    0.154349] bio: create slab <bio-0> at 0
[    0.155063] ACPI: EC: Look up EC in DSDT
[    0.155769] ACPI: Interpreter enabled
[    0.155773] ACPI: (supports S0 S3 S4 S5)
[    0.155788] ACPI: Using IOAPIC for interrupt routing
[    0.297945] ACPI: No dock devices found.
[    0.297948] HEST: Table not found.
[    0.297952] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.298002] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.298092] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.298094] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.298096] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.298098] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.298100] pci_root PNP0A03:00: host bridge window [mem 0x7ff00000-0xfebfffff]
[    0.298113] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
[    0.298124] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.298161] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
[    0.298193] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.298195] pci 0000:00:02.0: PME# disabled
[    0.298215] pci 0000:00:0a.0: [1022:9609] type 1 class 0x000604
[    0.298245] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.298247] pci 0000:00:0a.0: PME# disabled
[    0.298271] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.298290] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    0.298299] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    0.298308] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    0.298318] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    0.298327] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    0.298336] pci 0000:00:11.0: reg 24: [mem 0xfe02f000-0xfe02f3ff]
[    0.298391] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.298404] pci 0000:00:12.0: reg 10: [mem 0xfe02e000-0xfe02efff]
[    0.298467] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.298479] pci 0000:00:12.1: reg 10: [mem 0xfe02d000-0xfe02dfff]
[    0.298547] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.298565] pci 0000:00:12.2: reg 10: [mem 0xfe02c000-0xfe02c0ff]
[    0.298646] pci 0000:00:12.2: supports D1 D2
[    0.298647] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.298651] pci 0000:00:12.2: PME# disabled
[    0.298670] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.298683] pci 0000:00:13.0: reg 10: [mem 0xfe02b000-0xfe02bfff]
[    0.298746] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.298758] pci 0000:00:13.1: reg 10: [mem 0xfe02a000-0xfe02afff]
[    0.298826] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.298844] pci 0000:00:13.2: reg 10: [mem 0xfe029000-0xfe0290ff]
[    0.298924] pci 0000:00:13.2: supports D1 D2
[    0.298926] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.298930] pci 0000:00:13.2: PME# disabled
[    0.298952] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.299048] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.299064] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.299073] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.299082] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.299091] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.299100] pci 0000:00:14.1: reg 20: [io  0xfa00-0xfa0f]
[    0.299156] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.299177] pci 0000:00:14.2: reg 10: [mem 0xfe024000-0xfe027fff 64bit]
[    0.299241] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.299245] pci 0000:00:14.2: PME# disabled
[    0.299258] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.299331] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.299371] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.299384] pci 0000:00:14.5: reg 10: [mem 0xfe028000-0xfe028fff]
[    0.299449] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.299463] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.299475] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.299486] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.299500] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.299546] pci 0000:01:00.0: [10de:0a65] type 0 class 0x000300
[    0.299555] pci 0000:01:00.0: reg 10: [mem 0xfb000000-0xfbffffff]
[    0.299565] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.299575] pci 0000:01:00.0: reg 1c: [mem 0xde000000-0xdfffffff 64bit pref]
[    0.299582] pci 0000:01:00.0: reg 24: [io  0xef00-0xef7f]
[    0.299589] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.299640] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    0.299650] pci 0000:01:00.1: reg 10: [mem 0xfcffc000-0xfcffffff]
[    0.304053] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.304059] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.304062] pci 0000:00:02.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.304066] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.304103] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    0.304117] pci 0000:02:00.0: reg 10: [io  0xde00-0xdeff]
[    0.304137] pci 0000:02:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.304150] pci 0000:02:00.0: reg 20: [mem 0xfdfe0000-0xfdfeffff 64bit pref]
[    0.304159] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.304206] pci 0000:02:00.0: supports D1 D2
[    0.304208] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.304211] pci 0000:02:00.0: PME# disabled
[    0.312054] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.312060] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.312062] pci 0000:00:0a.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.312066] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.312121] pci 0000:03:0e.0: [104c:8024] type 0 class 0x000c00
[    0.312144] pci 0000:03:0e.0: reg 10: [mem 0xfdeff000-0xfdeff7ff]
[    0.312156] pci 0000:03:0e.0: reg 14: [mem 0xfdef8000-0xfdefbfff]
[    0.312249] pci 0000:03:0e.0: supports D1 D2
[    0.312251] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.312256] pci 0000:03:0e.0: PME# disabled
[    0.312289] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.312293] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.312297] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.312301] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff pref]
[    0.312303] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.312305] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.312307] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.312309] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.312312] pci 0000:00:14.4:   bridge window [mem 0x7ff00000-0xfebfffff] (subtractive decode)
[    0.312323] pci_bus 0000:00: on NUMA node 0
[    0.312329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.312546] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.312598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.312630] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.312658]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.312660]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.312662] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.322169] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.322202] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.322233] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.322262] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.322291] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.322321] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.322350] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.322380] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.322456] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.322459] vgaarb: loaded
[    0.322460] vgaarb: bridge control possible 0000:01:00.0
[    0.322615] SCSI subsystem initialized
[    0.324019] libata version 3.00 loaded.
[    0.324019] usbcore: registered new interface driver usbfs
[    0.324019] usbcore: registered new interface driver hub
[    0.324019] usbcore: registered new device driver usb
[    0.324019] PCI: Using ACPI for IRQ routing
[    0.331123] PCI: pci_cache_line_size set to 64 bytes
[    0.331129] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.331195] reserve RAM buffer: 0000000000098400 - 000000000009ffff 
[    0.331197] reserve RAM buffer: 000000007fc91000 - 000000007fffffff 
[    0.331271] NetLabel: Initializing
[    0.331272] NetLabel:  domain hash size = 128
[    0.331273] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.331282] NetLabel:  unlabeled traffic allowed by default
[    0.331311] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.331315] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.333051] Switching to clocksource hpet
[    0.338700] Switched to NOHz mode on CPU #1
[    0.338704] Switched to NOHz mode on CPU #0
[    0.340593] AppArmor: AppArmor Filesystem Enabled
[    0.340618] pnp: PnP ACPI init
[    0.340632] ACPI: bus type pnp registered
[    0.340717] pnp 00:00: [bus 00-ff]
[    0.340720] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.340722] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.340724] pnp 00:00: [io  0x0d00-0xffff window]
[    0.340726] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.340727] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.340731] pnp 00:00: [mem 0x7ff00000-0xfebfffff window]
[    0.340775] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.340784] pnp 00:01: [io  0x0010-0x001f]
[    0.340785] pnp 00:01: [io  0x0022-0x003f]
[    0.340787] pnp 00:01: [io  0x0044-0x005f]
[    0.340788] pnp 00:01: [io  0x0062-0x0063]
[    0.340790] pnp 00:01: [io  0x0065-0x006f]
[    0.340791] pnp 00:01: [io  0x0074-0x007f]
[    0.340793] pnp 00:01: [io  0x0091-0x0093]
[    0.340794] pnp 00:01: [io  0x00a2-0x00bf]
[    0.340796] pnp 00:01: [io  0x00e0-0x00ef]
[    0.340797] pnp 00:01: [io  0x04d0-0x04d1]
[    0.340799] pnp 00:01: [io  0x0220-0x0225]
[    0.340800] pnp 00:01: [io  0x0290-0x0294]
[    0.340843] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.340845] system 00:01: [io  0x0220-0x0225] has been reserved
[    0.340847] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.340850] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.452132] pnp 00:02: [io  0x4100-0x411f]
[    0.452135] pnp 00:02: [io  0x0228-0x022f]
[    0.452137] pnp 00:02: [io  0x040b]
[    0.452139] pnp 00:02: [io  0x04d6]
[    0.452140] pnp 00:02: [io  0x0c00-0x0c01]
[    0.452141] pnp 00:02: [io  0x0c14]
[    0.452143] pnp 00:02: [io  0x0c50-0x0c52]
[    0.452144] pnp 00:02: [io  0x0c6c-0x0c6d]
[    0.452146] pnp 00:02: [io  0x0c6f]
[    0.452147] pnp 00:02: [io  0x0cd0-0x0cd1]
[    0.452148] pnp 00:02: [io  0x0cd2-0x0cd3]
[    0.452150] pnp 00:02: [io  0x0cd4-0x0cdf]
[    0.452151] pnp 00:02: [io  0x4000-0x40fe]
[    0.452153] pnp 00:02: [io  0x4210-0x4217]
[    0.452154] pnp 00:02: [io  0x0b00-0x0b0f]
[    0.452156] pnp 00:02: [io  0x0b10-0x0b1f]
[    0.452157] pnp 00:02: [io  0x0b20-0x0b3f]
[    0.452159] pnp 00:02: [mem 0x00000000-0x00000fff window]
[    0.452161] pnp 00:02: [mem 0xfee00400-0xfee00fff window]
[    0.452168] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.452195] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0007ffff pref]
[    0.452200] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:02:00.0 BAR 6 [mem 0x00000000-0x0000ffff pref]
[    0.452244] system 00:02: [io  0x4100-0x411f] has been reserved
[    0.452246] system 00:02: [io  0x0228-0x022f] has been reserved
[    0.452248] system 00:02: [io  0x040b] has been reserved
[    0.452250] system 00:02: [io  0x04d6] has been reserved
[    0.452252] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    0.452254] system 00:02: [io  0x0c14] has been reserved
[    0.452256] system 00:02: [io  0x0c50-0x0c52] has been reserved
[    0.452258] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
[    0.452260] system 00:02: [io  0x0c6f] has been reserved
[    0.452262] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    0.452264] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    0.452266] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
[    0.452268] system 00:02: [io  0x4000-0x40fe] has been reserved
[    0.452270] system 00:02: [io  0x4210-0x4217] has been reserved
[    0.452272] system 00:02: [io  0x0b00-0x0b0f] has been reserved
[    0.452274] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    0.452276] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    0.452278] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
[    0.452282] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.452358] pnp 00:03: [dma 4]
[    0.452360] pnp 00:03: [io  0x0000-0x000f]
[    0.452361] pnp 00:03: [io  0x0080-0x0090]
[    0.452363] pnp 00:03: [io  0x0094-0x009f]
[    0.452364] pnp 00:03: [io  0x00c0-0x00df]
[    0.452389] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.452423] pnp 00:04: [irq 0 disabled]
[    0.452434] pnp 00:04: [irq 8]
[    0.452436] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.452457] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.452475] pnp 00:05: [io  0x0070-0x0073]
[    0.452495] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.452501] pnp 00:06: [io  0x0061]
[    0.452521] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.452527] pnp 00:07: [io  0x00f0-0x00ff]
[    0.452534] pnp 00:07: [irq 13]
[    0.452555] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.452766] pnp 00:08: [io  0x03f8-0x03ff]
[    0.452773] pnp 00:08: [irq 4]
[    0.452816] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.452956] pnp 00:09: [io  0x0378-0x037f]
[    0.452964] pnp 00:09: [irq 7]
[    0.453003] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.453087] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.453125] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.453127] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.453245] pnp 00:0b: [mem 0x000d4400-0x000d7fff]
[    0.453246] pnp 00:0b: [mem 0x000f0000-0x000f7fff]
[    0.453248] pnp 00:0b: [mem 0x000f8000-0x000fbfff]
[    0.453250] pnp 00:0b: [mem 0x000fc000-0x000fffff]
[    0.453251] pnp 00:0b: [mem 0x7fcf0000-0x7fcfffff]
[    0.453253] pnp 00:0b: [mem 0xffff0000-0xffffffff]
[    0.453255] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.453256] pnp 00:0b: [mem 0x00100000-0x7fceffff]
[    0.453258] pnp 00:0b: [mem 0x7fd00000-0x7fdfffff]
[    0.453260] pnp 00:0b: [mem 0x7fe00000-0x7fefffff]
[    0.453261] pnp 00:0b: [mem 0x00000000-0xffffffff disabled]
[    0.453263] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    0.453265] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    0.453266] pnp 00:0b: [mem 0xfff80000-0xfffeffff]
[    0.453270] pnp 00:0b: disabling [mem 0x000d4400-0x000d7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.453273] pnp 00:0b: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.453276] pnp 00:0b: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.453278] pnp 00:0b: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.453281] pnp 00:0b: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.453284] pnp 00:0b: disabling [mem 0x00100000-0x7fceffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.453308] pnp 00:0b: [Firmware Bug]: [mem 0x00000000-0xffffffff disabled] covers only part of AMD MMCONFIG area [mem 0xe0000000-0xe00fffff]; adding more reservations
[    0.453336] system 00:0b: [mem 0x7fcf0000-0x7fcfffff] could not be reserved
[    0.453338] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    0.453340] system 00:0b: [mem 0x7fd00000-0x7fdfffff] has been reserved
[    0.453342] system 00:0b: [mem 0x7fe00000-0x7fefffff] could not be reserved
[    0.453344] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.453347] system 00:0b: [mem 0xfee00000-0xfee00fff] could not be reserved
[    0.453349] system 00:0b: [mem 0xfff80000-0xfffeffff] has been reserved
[    0.453351] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.453367] pnp: PnP ACPI: found 12 devices
[    0.453369] ACPI: ACPI bus type pnp unregistered
[    0.453372] PnPBIOS: Disabled by ACPI PNP
[    0.482269] Freeing initrd memory: 19296k freed
[    0.488932] PCI: max bus depth: 1 pci_try_num: 2
[    0.488948] pci 0000:01:00.0: BAR 6: assigned [mem 0xd0000000-0xd007ffff pref]
[    0.488950] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.488953] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.488955] pci 0000:00:02.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.488958] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.488962] pci 0000:02:00.0: BAR 6: assigned [mem 0xfdf00000-0xfdf0ffff pref]
[    0.488964] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
[    0.488966] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.488968] pci 0000:00:0a.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.488971] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.488974] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.488977] pci 0000:00:14.4:   bridge window [io  0xc000-0xcfff]
[    0.488982] pci 0000:00:14.4:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.488986] pci 0000:00:14.4:   bridge window [mem 0xfdd00000-0xfddfffff pref]
[    0.489002] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.489005] pci 0000:00:02.0: setting latency timer to 64
[    0.489010] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.489012] pci 0000:00:0a.0: setting latency timer to 64
[    0.489019] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.489020] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.489022] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.489024] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.489026] pci_bus 0000:00: resource 8 [mem 0x7ff00000-0xfebfffff]
[    0.489028] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.489030] pci_bus 0000:01: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.489032] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.489034] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.489036] pci_bus 0000:02: resource 1 [mem 0xfdc00000-0xfdcfffff]
[    0.489038] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.489040] pci_bus 0000:03: resource 0 [io  0xc000-0xcfff]
[    0.489042] pci_bus 0000:03: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.489044] pci_bus 0000:03: resource 2 [mem 0xfdd00000-0xfddfffff pref]
[    0.489045] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.489047] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.489049] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.489051] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000dffff]
[    0.489053] pci_bus 0000:03: resource 8 [mem 0x7ff00000-0xfebfffff]
[    0.489084] NET: Registered protocol family 2
[    0.489134] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.489283] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.489674] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.489874] TCP: Hash tables configured (established 131072 bind 65536)
[    0.489876] TCP reno registered
[    0.489878] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.489886] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.489975] NET: Registered protocol family 1
[    0.848298] pci 0000:01:00.0: Boot video device
[    0.848314] PCI: CLS 4 bytes, default 64
[    0.848627] audit: initializing netlink socket (disabled)
[    0.848635] type=2000 audit(1334544298.848:1): initialized
[    0.866617] highmem bounce pool size: 64 pages
[    0.866622] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.872974] VFS: Disk quotas dquot_6.5.2
[    0.873037] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.873587] fuse init (API version 7.16)
[    0.873685] msgmni has been set to 1706
[    0.874198] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.874266] io scheduler noop registered
[    0.874269] io scheduler deadline registered
[    0.874297] io scheduler cfq registered (default)
[    0.874399] pcieport 0000:00:02.0: setting latency timer to 64
[    0.874426] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.874463] pcieport 0000:00:0a.0: setting latency timer to 64
[    0.874483] pcieport 0000:00:0a.0: irq 41 for MSI/MSI-X
[    0.874530] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.874549] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.874643] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.874647] ACPI: Power Button [PWRB]
[    0.874682] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.874684] ACPI: Power Button [PWRF]
[    0.874704] ACPI: acpi_idle registered with cpuidle
[    0.874723] ACPI: processor limited to max C-state 1
[    0.916858] ERST: Table is not found!
[    0.916918] isapnp: Scanning for PnP cards...
[    0.916944] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.937392] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.270672] isapnp: No Plug & Play device found
[    1.302497] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.302815] Linux agpgart interface v0.103
[    1.303826] brd: module loaded
[    1.304235] loop: module loaded
[    1.304368] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.304612] Fixed MDIO Bus: probed
[    1.304629] PPP generic driver version 2.4.2
[    1.304658] tun: Universal TUN/TAP device driver, 1.6
[    1.304659] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.304710] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.304726] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.304735] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.304758] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.304765] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.304786] ehci_hcd 0000:00:12.2: debug port 1
[    1.304812] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    1.316076] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.316220] hub 1-0:1.0: USB hub found
[    1.316224] hub 1-0:1.0: 6 ports detected
[    1.316300] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.316314] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.316340] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.316347] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.316367] ehci_hcd 0000:00:13.2: debug port 1
[    1.316394] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    1.328077] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.328198] hub 2-0:1.0: USB hub found
[    1.328201] hub 2-0:1.0: 6 ports detected
[    1.328266] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.328281] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.328297] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.328325] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.328356] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    1.388367] hub 3-0:1.0: USB hub found
[    1.388374] hub 3-0:1.0: 3 ports detected
[    1.388432] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.388446] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.388475] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.388493] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    1.448175] hub 4-0:1.0: USB hub found
[    1.448182] hub 4-0:1.0: 3 ports detected
[    1.448241] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.448257] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.448285] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.448317] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    1.508180] hub 5-0:1.0: USB hub found
[    1.508186] hub 5-0:1.0: 3 ports detected
[    1.508245] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.508260] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.508287] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.508303] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    1.568179] hub 6-0:1.0: USB hub found
[    1.568186] hub 6-0:1.0: 3 ports detected
[    1.568245] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.568262] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.568293] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.568309] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    1.628063] usb 1-3: new high speed USB device number 2 using ehci_hcd
[    1.628183] hub 7-0:1.0: USB hub found
[    1.628189] hub 7-0:1.0: 2 ports detected
[    1.628249] uhci_hcd: USB Universal Host Controller Interface driver
[    1.628330] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.661952] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.661954] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.848078] Refined TSC clocksource calibration: 2812.709 MHz.
[    1.848089] Switching to clocksource tsc
[    1.912157] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.912268] mousedev: PS/2 mouse device common for all mice
[    1.912356] rtc_cmos 00:05: RTC can wake from S4
[    1.912435] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.912467] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.912548] device-mapper: uevent: version 1.0.3
[    1.912599] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.912622] EISA: Probing bus 0 at eisa.0
[    1.912624] EISA: Cannot allocate resource for mainboard
[    1.912626] Cannot allocate resource for EISA slot 1
[    1.912627] Cannot allocate resource for EISA slot 2
[    1.912628] Cannot allocate resource for EISA slot 3
[    1.912630] Cannot allocate resource for EISA slot 4
[    1.912631] Cannot allocate resource for EISA slot 5
[    1.912632] Cannot allocate resource for EISA slot 6
[    1.912633] Cannot allocate resource for EISA slot 7
[    1.912635] Cannot allocate resource for EISA slot 8
[    1.912636] EISA: Detected 0 cards.
[    1.912643] cpufreq-nforce2: No nForce2 chipset.
[    1.912645] cpuidle: using governor ladder
[    1.912646] cpuidle: using governor menu
[    1.912648] EFI Variables Facility v0.08 2004-May-17
[    1.912839] TCP cubic registered
[    1.912936] NET: Registered protocol family 10
[    1.913351] NET: Registered protocol family 17
[    1.913363] Registering the dns_resolver key type
[    1.913380] Using IPI No-Shortcut mode
[    1.913429] PM: Hibernation image not present or could not be loaded.
[    1.913438] registered taskstats version 1
[    1.920505]   Magic number: 8:83:713
[    1.920591] rtc_cmos 00:05: setting system clock to 2012-04-16 02:45:00 UTC (1334544300)
[    1.920597] powernow-k8: Found 1 AMD Athlon(tm) II X2 240 Processor (2 cpu cores) (version 2.20.00)
[    1.920623] powernow-k8:    0 : pstate 0 (2800 MHz)
[    1.920624] powernow-k8:    1 : pstate 1 (2100 MHz)
[    1.920626] powernow-k8:    2 : pstate 2 (1600 MHz)
[    1.920627] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.920727] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.920730] EDD information not available.
[    1.920855] Freeing unused kernel memory: 696k freed
[    1.921012] Write protecting the kernel text: 5344k
[    1.921041] Write protecting the kernel read-only data: 2188k
[    1.939807] udevd[82]: starting version 173
[    1.985501] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.985519] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.985549] r8169 0000:02:00.0: setting latency timer to 64
[    1.985590] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.985952] r8169 0000:02:00.0: eth0: RTL8168c/8111c at 0xf8010000, 6c:f0:49:00:a3:68, XID 1c4000c0 IRQ 42
[    1.986406] scsi0 : pata_atiixp
[    1.988037] scsi1 : pata_atiixp
[    1.988543] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    1.988546] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    1.988697] ahci 0000:00:11.0: version 3.0
[    1.988720] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.988819] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.988822] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.990343] scsi2 : ahci
[    1.991697] scsi3 : ahci
[    1.994253] scsi4 : ahci
[    1.994964] wmi: Mapper loaded
[    1.996098] scsi5 : ahci
[    1.996211] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.996215] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.996218] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.996221] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    2.136118] usb 4-2: new low speed USB device number 2 using ohci_hcd
[    2.316088] ata5: SATA link down (SStatus 0 SControl 300)
[    2.320085] ata6: SATA link down (SStatus 0 SControl 300)
[    2.488083] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.488115] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.490542] ata4.00: ATAPI: ATAPI   iHAS124   B, AL0A, max UDMA/100
[    2.491413] ata4.00: configured for UDMA/100
[    2.497751] ata3.00: ATA-8: WDC WD6400AARS-00Y5B1, 80.00A80, max UDMA/133
[    2.497754] ata3.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.499410] ata3.00: configured for UDMA/133
[    2.499604] scsi 2:0:0:0: Direct-Access     ATA      WDC WD6400AARS-0 80.0 PQ: 0 ANSI: 5
[    2.499761] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.499814] sd 2:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.499851] sd 2:0:0:0: [sda] Write Protect is off
[    2.499854] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.499868] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.500946] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS124   B      AL0A PQ: 0 ANSI: 5
[    2.504516] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.504520] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.504644] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.504710] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.526835]  sda: sda1 sda2 < sda5 >
[    2.527125] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.529407] firewire_ohci 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.540357] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input2
[    2.540431] generic-usb 0003:413C:2105.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:12.1-2/input0
[    2.540445] usbcore: registered new interface driver usbhid
[    2.540447] usbhid: USB HID core driver
[    2.584080] usb 4-3: new low speed USB device number 3 using ohci_hcd
[    2.584169] firewire_ohci: Added fw-ohci device 0000:03:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.756371] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input3
[    2.756465] generic-usb 0003:0461:4D22.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.1-3/input0
[    3.084166] firewire_core: created device fw0: GUID 00e4fc4b0000241d, S400
[    3.874289] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    3.874292] vesafb: scrolling: redraw
[    3.874295] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.874556] vesafb: framebuffer at 0xdf000000, mapped to 0xf8200000, using 1216k, total 1216k
[    3.874671] Console: switching to colour frame buffer device 80x30
[    3.874683] fb0: VESA VGA frame buffer device
[    4.020157] Btrfs loaded
[    4.024968] xor: automatically using best checksumming function: pIII_sse
[    4.044008]    pIII_sse  : 11592.000 MB/sec
[    4.044009] xor: using function: pIII_sse (11592.000 MB/sec)
[    4.044411] device-mapper: dm-raid45: initialized v0.2594b
[    4.318988] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.186804] udevd[374]: starting version 173
[    6.209227] Adding 2092028k swap on /dev/sda5.  Priority:-1 extents:1 across:2092028k 
[    7.460362] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.500512] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io 0xb00-0xb0f]
[    7.500515] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.517411] lp: driver loaded but no devices found
[    7.682936] type=1400 audit(1334544306.255:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=518 comm="apparmor_parser"
[    7.682952] type=1400 audit(1334544306.255:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=546 comm="apparmor_parser"
[    7.683251] type=1400 audit(1334544306.255:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=518 comm="apparmor_parser"
[    7.683276] type=1400 audit(1334544306.255:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=546 comm="apparmor_parser"
[    7.683452] type=1400 audit(1334544306.255:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=518 comm="apparmor_parser"
[    7.683480] type=1400 audit(1334544306.255:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=546 comm="apparmor_parser"
[    7.713826] parport_pc 00:09: reported by Plug and Play ACPI
[    7.713880] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.732360] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    7.732423] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[    7.808188] lp0: using parport0 (interrupt-driven).
[    7.830864] ppdev: user-space parallel port driver
[    8.005049] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.005054] hda_intel: codec_mask forced to 0xff
[    8.093607] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    8.094378] r8712u: DriverVersion: v7_0.20100831
[    8.094389] r8712u: register rtl8712_netdev_ops to netdev_ops
[    8.094392] r8712u: USB_SPEED_HIGH with 4 endpoints
[    8.095046] r8712u: Boot from EFUSE: Autoload OK
[    8.833896] nvidia: module license 'NVIDIA' taints kernel.
[    8.833900] Disabling lock debugging due to kernel taint
[    9.286623] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.286631] nvidia 0000:01:00.0: setting latency timer to 64
[    9.286635] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.286790] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
[    9.447345] r8712u: CustomerID = 0x0000
[    9.447349] r8712u: MAC Address from efuse = 00:02:72:ae:58:4e
[    9.448673] usbcore: registered new interface driver r8712u
[   10.746320] type=1400 audit(1334544309.319:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=780 comm="apparmor_parser"
[   10.746748] type=1400 audit(1334544309.319:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=780 comm="apparmor_parser"
[   10.746971] type=1400 audit(1334544309.319:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=780 comm="apparmor_parser"
[   11.048010] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   11.426587] type=1400 audit(1334544309.999:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=779 comm="apparmor_parser"
[   12.052010] hda-intel: Codec #1 probe error; disabling it...
[   12.132704] r8169 0000:02:00.0: eth0: link down
[   12.133056] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.192911] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   12.346173] lirc_dev: IR Remote Control driver registered, major 249 
[   12.421787] init: failsafe main process (728) killed by TERM signal
[   12.424505] init: alsa-restore main process (854) terminated with status 19
[   12.820267] init: xbmcbuntu-wait (lightdm) main process (886) killed by TERM signal
[   12.820452] init: xbmcbuntu-wait (ubiquity) main process (887) killed by TERM signal
[   12.920491] r8712u: 1 RCR=0x153f00e
[   12.921240] r8712u: 2 RCR=0x553f00e
[   13.028437] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.088023] hda-intel: Codec #2 probe error; disabling it...
[   14.124009] hda-intel: Codec #3 probe error; disabling it...
[   14.190923] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.190928] hda_intel: codec_mask forced to 0xf2
[   14.190953] HDA Intel 0000:01:00.1: setting latency timer to 64
[   17.244056] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x400f0000
[   18.252064] hda-intel: Codec #4 probe error; disabling it...
[   19.288065] hda-intel: Codec #5 probe error; disabling it...
[   20.328018] hda-intel: Codec #6 probe error; disabling it...
[   21.372045] hda-intel: Codec #7 probe error; disabling it...
[   21.672070] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
[   21.688141] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input4
[   24.575949] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.578108] r8712u: [r8712_got_addbareq_event_callback] mac = 00:24:7b:f2:81:9c, seq = 0, tid = 0
[   25.137587] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.534448] init: plymouth-stop pre-start process (1279) terminated with status 1
[   35.584044] wlan0: no IPv6 routers present
[   53.452285] r8712u: [r8712_got_addbareq_event_callback] mac = 00:24:7b:f2:81:9c, seq = 0, tid = 0
[   64.176036] wlan0: no IPv6 routers present
[   82.436205] r8712u: [r8712_got_addbareq_event_callback] mac = 00:24:7b:f2:81:9c, seq = 0, tid = 0
[   92.800078] wlan0: no IPv6 routers present
[  111.419408] r8712u: [r8712_got_addbareq_event_callback] mac = 00:24:7b:f2:81:9c, seq = 0, tid = 0
[  122.368067] wlan0: no IPv6 routers present

---

### Post by rhossack on 2012-04-15
the forum wouldn't let me post all in one message so split it up.  When I tried to use 'lshw -c' to a text file it would come up with zero bytes and an empty file.

> **Jose Catre-Vandis said:**
> 
lshw -c network output needed
ron-ga-ma785gm-us2h
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=36434630-3439-3030-4133-3638FFFFFFFF
  *-core
       description: Motherboard
       product: GA-MA785GM-US2H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F12a
          date: 07/08/2010
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) II X2 240 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.6.2
          slot: Socket M2
          size: 2800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: c
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns) [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 800 MHz (1.2 ns) [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.2
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=32
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fb000000-fcffffff ioport:c0000000(size=536870912)
           *-display
                description: VGA compatible controller
                product: GT218 [GeForce 210]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fb000000-fbffffff memory:c0000000-cfffffff memory:de000000-dfffffff ioport:ef00(size=128) memory:d0000000-d007ffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fcffc000-fcffffff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 5)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fdc00000-fdcfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 6c:f0:49:00:a3:68
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:de00(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:fdf00000-fdf0ffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=32
             resources: irq:22 ioport:ff00(size=8) ioport:fe00(size=4) ioport:fd00(size=8) ioport:fc00(size=4) ioport:fb00(size=16) memory:fe02f000-fe02f3ff
           *-disk
                description: ATA Disk
                product: WDC WD6400AARS-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 80.0
                serial: WD-WCAV5D344220
                size: 596GiB (640GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000ed826
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9577e646-4678-46dc-9dd1-3f7949525f28
                   size: 594GiB
                   capacity: 594GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-04-08 11:16:47 filesystem=ext4 lastmountpoint=/ modified=2012-04-08 11:24:43 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-04-15 19:45:05 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2043MiB
                   capacity: 2043MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2043MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: iHAS124   B
                vendor: ATAPI
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: AL0A
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02e000-fe02efff
        *-usb:1
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:16 memory:fe02d000-fe02dfff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:fe02c000-fe02c0ff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02b000-fe02bfff
        *-usb:4
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe02a000-fe02afff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:19 memory:fe029000-fe0290ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=32
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fa00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:fe024000-fe027fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI

will it connect OK with a wired connection ?[/QUOTE]
 Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
             resources: ioport:c000(size=4096) memory:fde00000-fdefffff memory:fdd00000-fddfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: e
                bus info: pci@0000:03:0e.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:22 memory:fdeff000-fdeff7ff memory:fdef8000-fdefbfff
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:fe028000-fe028fff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:02:72:ae:58:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated

---

### Post by Jose Catre-Vandis on 2012-04-16
OK. From what I can see your wireless driver is loading (r8712u) but not associating.

Do you have security on your wireless? If so drop it (temporarily) and then try.

If it connects then its the security that is causing the problem and you will need to set and fix the settings in Network Manager / wicd (whatever XMBCbuntu is using)

---

### Post by gordintoronto on 2012-04-16
What wireless device do you have? From terminal:
lspci
lsusb

You could install Ubuntu, then install XBMC in it. The only advantage is that more people might be able to help you.

---

### Post by rhossack on 2012-04-17
> **Jose Catre-Vandis said:**
> OK. From what I can see your wireless driver is loading (r8712u) but not associating.

Do you have security on your wireless? If so drop it (temporarily) and then try.Security?   I have a password to log onto my router.
> If it connects then its the security that is causing the problem and you will need to set and fix the settings in Network Manager / wicd (whatever XMBCbuntu is using)
Not clear about the security question

---

### Post by rhossack on 2012-04-17
> **gordintoronto said:**
> What wireless device do you have? From terminal:
lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
> lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 004 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
> You could install Ubuntu, then install XBMC in it. The only advantage is that more people might be able to help you.
I may have to do this ...

Thanks for your help

---

### Post by gordintoronto on 2012-04-18
"I have since found a work around to my issue. If I click on the icon and choose to create a new network and type in the name of the existing one it will connect."

Is it working OK? I'm not sure what icon you are clicking on (network manager?) or what you do next.

---

### Post by rhossack on 2012-04-19
> **gordintoronto said:**
> "I have since found a work around to my issue. If I click on the icon and choose to create a new network and type in the name of the existing one it will connect."

Is it working OK? I'm not sure what icon you are clicking on (network manager?) or what you do next.
The "wireless network connection" and then I click new connection and type the name in and it has connected about 50% of the time.

---

### Post by Jose Catre-Vandis on 2012-04-20
Have you got your SSID discoverable on your router? If not, you will/may have to type it in each time....

---

### Post by rhossack on 2012-04-21
> **Jose Catre-Vandis said:**
> Have you got your SSID discoverable on your router? If not, you will/may have to type it in each time....
I think found my problem.  I hard wired it and it worked great.  Put my 10 year old wireless G pci card in and it connected just fine.
Scratching my head I put the Patriot N USB back in and it won't connect.

I decided to re-install SalineOS and it still would not connect.

I then have this brilliant idea ... there are 6 USB ports, four in the back and two up front.

Put the USB in the front and it connects.

I then tried every port in the back and with one it connects just fine and the other 3 it won't.  MB issue?... so now to re-install XMBC and start over.

I really appreciate all the help you gave this idiot and now to see how to flag this as SOLVED.

---

### Post by Jose Catre-Vandis on 2012-04-22
Well done :)

---

