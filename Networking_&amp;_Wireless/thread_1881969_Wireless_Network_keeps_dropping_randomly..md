---
title: "Wireless Network keeps dropping randomly."
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by TheSluiceGate on 2011-11-16
Hi all,
I'm a new Xubuntu user experiencing random drops of my wireless network. Works fine on startup, lasts for maybe 15-20 minutes and then drops out. The indicator icon on the top panel still shows a strong wireless connection.

I tried to disable and then re-enable wireless networking, disconnecting and re-connecting, but to no avail. The only solution is to re-boot, and then it works fine again - until once again it drops. I could be imagining it, but it seems to drop out most regularly on large downloads.

Wireless networking works fine under Windows, as do other wireless computers on the same network.

I've been surfing a lot of message boards, including this one, for the last few weeks and I'm at my wits end. I've experimented with ndiswrapper, but at this stage I am not even sure if it is working on my system. 

I'm not going to ragequit Xubuntu, but I might invent the cryquit! **Please don't send me back to Windows!!**


[SIZE="1"]My setup:
Toshiba Satellite L25 - S121 with Xubuntu 11.10, 32bit

------------------------------

Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


eth1      IEEE 802.11bg  ESSID:"***networknamehere***"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:  00:0F:CC:BB:C7:34   
          Bit Rate:48 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=95/100  Signal level=-16 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-------------------------------------------

ipw2200               146148  0 
libipw                 46701  1 ipw2200
cfg80211              172392  2 ipw2200,libipw
lib80211               14570  3 lib80211_crypt_wep,ipw2200,libipw

----------------------------------------------

*-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:b3:d8:18
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.22 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:c0201000-c0201fff

----------------------------------------


No output for ```
dmesg | grep ndiswrapper
```


-----------------------------------------

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-12-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ea0000 - 0000000037eb3000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eb3000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: TOSHIBA Satellite L25                    /Satellite L25                    , BIOS V1.90    01/05/06
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x37ea0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 037F00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 512MB, type WB
[    0.000000] reg 1, base: 512MB, range: 256MB, type WB
[    0.000000] reg 2, base: 768MB, range: 128MB, type WB
[    0.000000] reg 3, base: 895MB, range: 1MB, type UC
[    0.000000] total RAM covered: 895M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 256M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 895MB, range: 1MB, type UC
[    0.000000] reg 2, base: 896MB, range: 128MB, type UC
[    0.000000] found SMP MP-table at [c00f73b0] f73b0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 365f6000 - 372f3000
[    0.000000] ACPI: RSDP 000f7450 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 37eae1d6 00038 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 37eb2f00 00074 (v01 ATI    Goldfish 06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 37eae62b 048D5 (v01    ATI    SB400 06040000 MSFT 0100000C)
[    0.000000] ACPI: FACS 37eb3fc0 00040
[    0.000000] ACPI: APIC 37eb2f74 00050 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 37eb2fc4 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 37eae410 0021B (v01  PmRef  Cpu0Cst 00003001 INTL 20030224)
[    0.000000] ACPI: SSDT 37eae20e 00202 (v01  PmRef    CpuPm 00003000 INTL 20030224)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00037ea0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00037ea0
[    0.000000] On node 0 totalpages: 228911
[    0.000000] free_area_init_node: node 0, pgdat c17b11c0, node_mem_map f5ef6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 14 pages used for memmap
[    0.000000]   HighMem zone: 1684 pages, LIFO batch:0
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x82
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 38000000 (gap: 38000000:a8000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f5800000 s26240 r0 d22912 u4194304
[    0.000000] pcpu-alloc: s26240 r0 d22912 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227121
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=027c8a6c-adc4-4999-a0ff-7bc84f911db7 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3664128 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00037ea0)
[    0.000000] Memory: 881188k/916096k available (5329k kernel code, 34456k reserved, 2589k data, 696k init, 6792k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17bc000 - 0xc186a000   ( 696 kB)
[    0.000000]       .data : 0xc1534784 - 0xc17bbd80   (2589 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1534784   (5329 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5408000 soft=f540a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.840 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.68 BogoMIPS (lpj=6383360)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004042] Security Framework initialized
[    0.004072] AppArmor: AppArmor initialized
[    0.004075] Yama: becoming mindful.
[    0.004156] Mount-cache hash table entries: 512
[    0.004353] Initializing cgroup subsys cpuacct
[    0.004362] Initializing cgroup subsys memory
[    0.004375] Initializing cgroup subsys devices
[    0.004379] Initializing cgroup subsys freezer
[    0.004382] Initializing cgroup subsys net_cls
[    0.004386] Initializing cgroup subsys blkio
[    0.004398] Initializing cgroup subsys perf_event
[    0.004438] Disabled fast string operations
[    0.004449] mce: CPU supports 5 MCE banks
[    0.004464] CPU0: Thermal monitoring enabled (TM1)
[    0.004764] SMP alternatives: switching to UP code
[    0.016587] Freeing SMP alternatives: 24k freed
[    0.016612] ACPI: Core revision 20110413
[    0.016618] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.016758] ACPI: Forced DSDT copy: length 0x048D5 copied locally, original unmapped
[    0.024020] ftrace: allocating 24885 entries in 49 pages
[    0.028141] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028517] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.069243] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[    0.072003] Performance Events: p6 PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              32
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             00000000ffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             0000000000000003
[    0.072003] Brought up 1 CPUs
[    0.072003] Total of 1 processors activated (3191.68 BogoMIPS).
[    0.072003] devtmpfs: initialized
[    0.072003] PM: Registering ACPI NVS region at 37eb3000 (315392 bytes)
[    0.073433] print_constraints: dummy: 
[    0.073471] Time: 16:48:17  Date: 11/16/11
[    0.073530] NET: Registered protocol family 16
[    0.073706] EISA bus registered
[    0.073719] ACPI: bus type pci registered
[    0.073822] PCI: MMCONFIG for domain 0000 [bus 00-0d] at [mem 0xe0000000-0xe0dfffff] (base 0xe0000000)
[    0.073828] PCI: MMCONFIG at [mem 0xe0000000-0xe0dfffff] reserved in E820
[    0.073831] PCI: Using MMCONFIG for extended config space
[    0.073833] PCI: Using configuration type 1 for base access
[    0.075239] bio: create slab <bio-0> at 0
[    0.076510] ACPI: EC: Look up EC in DSDT
[    0.140097] ACPI: Interpreter enabled
[    0.140105] ACPI: (supports S0 S3 S4 S5)
[    0.140133] ACPI: Using IOAPIC for interrupt routing
[    0.146278] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.146425] ACPI: No dock devices found.
[    0.146429] HEST: Table not found.
[    0.146435] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.146840] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.147631] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.147636] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.147640] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.147644] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.147648] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    0.147652] pci_root PNP0A03:00: host bridge window [mem 0x38000000-0xfebfffff] (ignored)
[    0.147657] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.147660] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.147677] pci 0000:00:00.0: [1002:5a31] type 0 class 0x000600
[    0.147731] pci 0000:00:01.0: [1002:5a3f] type 1 class 0x000604
[    0.147827] pci 0000:00:13.0: [1002:4374] type 0 class 0x000c03
[    0.147858] pci 0000:00:13.0: reg 10: [mem 0xc0004000-0xc0004fff]
[    0.148001] pci 0000:00:13.1: [1002:4375] type 0 class 0x000c03
[    0.148040] pci 0000:00:13.1: reg 10: [mem 0xc0005000-0xc0005fff]
[    0.148191] pci 0000:00:13.2: [1002:4373] type 0 class 0x000c03
[    0.148225] pci 0000:00:13.2: reg 10: [mem 0xc0006000-0xc0006fff]
[    0.148351] pci 0000:00:13.2: supports D1 D2
[    0.148355] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.148363] pci 0000:00:13.2: PME# disabled
[    0.148400] pci 0000:00:14.0: [1002:4372] type 0 class 0x000c05
[    0.148421] pci 0000:00:14.0: reg 10: [io  0x8040-0x804f]
[    0.148439] pci 0000:00:14.0: reg 14: [mem 0xc0007000-0xc00073ff]
[    0.148515] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.148545] pci 0000:00:14.1: [1002:4376] type 0 class 0x000101
[    0.148575] pci 0000:00:14.1: reg 10: [io  0x8430-0x8437]
[    0.148592] pci 0000:00:14.1: reg 14: [io  0x8424-0x8427]
[    0.148609] pci 0000:00:14.1: reg 18: [io  0x8428-0x842f]
[    0.148627] pci 0000:00:14.1: reg 1c: [io  0x8420-0x8423]
[    0.148644] pci 0000:00:14.1: reg 20: [io  0x8410-0x841f]
[    0.148729] pci 0000:00:14.3: [1002:4377] type 0 class 0x000601
[    0.148859] pci 0000:00:14.4: [1002:4371] type 1 class 0x000604
[    0.148937] pci 0000:00:14.5: [1002:4370] type 0 class 0x000401
[    0.148967] pci 0000:00:14.5: reg 10: [mem 0xc0007400-0xc00074ff]
[    0.149108] pci 0000:00:14.6: [1002:4378] type 0 class 0x000703
[    0.149138] pci 0000:00:14.6: reg 10: [mem 0xc0007800-0xc00078ff]
[    0.149321] pci 0000:01:05.0: [1002:5a62] type 0 class 0x000300
[    0.149338] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.149348] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.149357] pci 0000:01:05.0: reg 18: [mem 0xc0100000-0xc010ffff]
[    0.149384] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.149403] pci 0000:01:05.0: supports D1 D2
[    0.149433] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.149441] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.149446] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.149451] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.149499] pci 0000:09:01.0: [104c:ac56] type 2 class 0x000607
[    0.149535] pci 0000:09:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.149574] pci 0000:09:01.0: supports D1 D2
[    0.149577] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.149585] pci 0000:09:01.0: PME# disabled
[    0.149620] pci 0000:09:02.0: [10ec:8139] type 0 class 0x000200
[    0.149655] pci 0000:09:02.0: reg 10: [io  0xa000-0xa0ff]
[    0.149675] pci 0000:09:02.0: reg 14: [mem 0xc0200000-0xc02000ff]
[    0.149797] pci 0000:09:02.0: supports D1 D2
[    0.149800] pci 0000:09:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.149808] pci 0000:09:02.0: PME# disabled
[    0.149845] pci 0000:09:04.0: [8086:4220] type 0 class 0x000280
[    0.149881] pci 0000:09:04.0: reg 10: [mem 0xc0201000-0xc0201fff]
[    0.150021] pci 0000:09:04.0: PME# supported from D0 D3hot D3cold
[    0.150029] pci 0000:09:04.0: PME# disabled
[    0.150109] pci 0000:00:14.4: PCI bridge to [bus 09-0e] (subtractive decode)
[    0.150120] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.150128] pci 0000:00:14.4:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.150136] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.150141] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.150145] pci 0000:00:14.4:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.150234] pci_bus 0000:00: on NUMA node 0
[    0.150239] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.150431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.150526] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.150591]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.150596]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.150599] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.153418] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.153485] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.153550] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.153614] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.153677] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.153741] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.153805] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.153869] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.154012] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.154017] vgaarb: loaded
[    0.154019] vgaarb: bridge control possible 0000:01:05.0
[    0.154351] SCSI subsystem initialized
[    0.154446] libata version 3.00 loaded.
[    0.154518] usbcore: registered new interface driver usbfs
[    0.154535] usbcore: registered new interface driver hub
[    0.154574] usbcore: registered new device driver usb
[    0.154701] PCI: Using ACPI for IRQ routing
[    0.155356] PCI: pci_cache_line_size set to 64 bytes
[    0.155443] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.155446] reserve RAM buffer: 0000000037ea0000 - 0000000037ffffff 
[    0.155611] NetLabel: Initializing
[    0.155614] NetLabel:  domain hash size = 128
[    0.155616] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.155634] NetLabel:  unlabeled traffic allowed by default
[    0.167895] AppArmor: AppArmor Filesystem Enabled
[    0.168037] pnp: PnP ACPI init
[    0.168090] ACPI: bus type pnp registered
[    0.168602] pnp 00:00: [bus 00-ff]
[    0.168608] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.168612] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.168615] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.168619] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.168623] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.168626] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.168630] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.168633] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.168637] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.168640] pnp 00:00: [mem 0x38000000-0xfebfffff window]
[    0.168644] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.168648] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.168651] pnp 00:00: [io  0x0d00-0xffff window]
[    0.168768] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.168800] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.168882] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.168888] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.169384] pnp 00:02: [io  0x0000-0x001f]
[    0.169388] pnp 00:02: [io  0x0080-0x008f]
[    0.169391] pnp 00:02: [io  0x00c0-0x00df]
[    0.169395] pnp 00:02: [dma 4]
[    0.169439] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.169464] pnp 00:03: [io  0x00f0-0x00fe]
[    0.169489] pnp 00:03: [irq 13]
[    0.169544] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.169560] pnp 00:04: [io  0x0070-0x0071]
[    0.169568] pnp 00:04: [irq 8]
[    0.169610] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.169622] pnp 00:05: [io  0x0061]
[    0.169665] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.169681] pnp 00:06: [io  0x0060]
[    0.169684] pnp 00:06: [io  0x0064]
[    0.169691] pnp 00:06: [irq 1]
[    0.169741] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.169757] pnp 00:07: [irq 12]
[    0.169819] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.169840] pnp 00:08: [io  0x002e-0x002f]
[    0.169844] pnp 00:08: [io  0x0068-0x006f]
[    0.169847] pnp 00:08: [io  0x0072-0x0073]
[    0.169850] pnp 00:08: [io  0x1080]
[    0.169853] pnp 00:08: [io  0x00b0-0x00b1]
[    0.169856] pnp 00:08: [io  0x0092]
[    0.169859] pnp 00:08: [io  0x0200-0x020f]
[    0.169862] pnp 00:08: [io  0x040b]
[    0.169865] pnp 00:08: [io  0x04d0-0x04d1]
[    0.169868] pnp 00:08: [io  0x04d6]
[    0.169871] pnp 00:08: [io  0x0530-0x0537]
[    0.169874] pnp 00:08: [io  0x0c00-0x0c01]
[    0.169877] pnp 00:08: [io  0x0c14]
[    0.169880] pnp 00:08: [io  0x0c50-0x0c52]
[    0.169883] pnp 00:08: [io  0x0c6c]
[    0.169886] pnp 00:08: [io  0x0c6f]
[    0.169888] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.169892] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.169895] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.169898] pnp 00:08: [io  0x8000-0x805f]
[    0.169902] pnp 00:08: [io  0x8100-0x81ff window]
[    0.169905] pnp 00:08: [io  0x0f40-0x0f47]
[    0.169908] pnp 00:08: [io  0x0280-0x0293]
[    0.169911] pnp 00:08: [io  0x087f]
[    0.169989] system 00:08: [io  0x1080] has been reserved
[    0.169994] system 00:08: [io  0x0200-0x020f] has been reserved
[    0.169997] system 00:08: [io  0x040b] has been reserved
[    0.170001] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.170005] system 00:08: [io  0x04d6] has been reserved
[    0.170009] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.170013] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.170017] system 00:08: [io  0x0c14] has been reserved
[    0.170020] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.170024] system 00:08: [io  0x0c6c] has been reserved
[    0.170028] system 00:08: [io  0x0c6f] has been reserved
[    0.170032] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.170036] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.170040] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.170044] system 00:08: [io  0x8000-0x805f] could not be reserved
[    0.170048] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.170052] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.170056] system 00:08: [io  0x0280-0x0293] has been reserved
[    0.170060] system 00:08: [io  0x087f] has been reserved
[    0.170065] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.170156] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.170160] pnp 00:09: [mem 0xfff80000-0xffffffff]
[    0.170163] pnp 00:09: [mem 0x00000000-0x00000fff]
[    0.170179] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.170231] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.170236] system 00:09: [mem 0xfff80000-0xffffffff] has been reserved
[    0.170240] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.170297] pnp: PnP ACPI: found 10 devices
[    0.170299] ACPI: ACPI bus type pnp unregistered
[    0.170305] PnPBIOS: Disabled by ACPI PNP
[    0.207312] Switching to clocksource acpi_pm
[    0.207349] PCI: max bus depth: 2 pci_try_num: 3
[    0.207388] pci 0000:00:14.4: BAR 15: assigned [mem 0x38000000-0x3bffffff pref]
[    0.207395] pci 0000:01:05.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
[    0.207401] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.207406] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.207412] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.207417] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]
[    0.207426] pci 0000:09:01.0: BAR 15: assigned [mem 0x38000000-0x3bffffff pref]
[    0.207432] pci 0000:09:01.0: BAR 16: assigned [mem 0x3c000000-0x3fffffff]
[    0.207436] pci 0000:09:01.0: BAR 0: assigned [mem 0xc0202000-0xc0202fff]
[    0.207446] pci 0000:09:01.0: BAR 0: set to [mem 0xc0202000-0xc0202fff] (PCI address [0xc0202000-0xc0202fff])
[    0.207450] pci 0000:09:01.0: BAR 13: assigned [io  0xa400-0xa4ff]
[    0.207454] pci 0000:09:01.0: BAR 14: assigned [io  0xa800-0xa8ff]
[    0.207458] pci 0000:09:01.0: CardBus bridge to [bus 0a-0d]
[    0.207462] pci 0000:09:01.0:   bridge window [io  0xa400-0xa4ff]
[    0.207470] pci 0000:09:01.0:   bridge window [io  0xa800-0xa8ff]
[    0.207478] pci 0000:09:01.0:   bridge window [mem 0x38000000-0x3bffffff pref]
[    0.207486] pci 0000:09:01.0:   bridge window [mem 0x3c000000-0x3fffffff]
[    0.207494] pci 0000:00:14.4: PCI bridge to [bus 09-0e]
[    0.207499] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.207509] pci 0000:00:14.4:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.207516] pci 0000:00:14.4:   bridge window [mem 0x38000000-0x3bffffff pref]
[    0.207553] pci 0000:09:01.0: enabling device (0000 -> 0003)
[    0.207581] pci 0000:09:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.207593] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.207597] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.207601] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.207604] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
[    0.207608] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]
[    0.207612] pci_bus 0000:09: resource 0 [io  0xa000-0xafff]
[    0.207616] pci_bus 0000:09: resource 1 [mem 0xc0200000-0xc02fffff]
[    0.207620] pci_bus 0000:09: resource 2 [mem 0x38000000-0x3bffffff pref]
[    0.207623] pci_bus 0000:09: resource 4 [io  0x0000-0xffff]
[    0.207627] pci_bus 0000:09: resource 5 [mem 0x00000000-0xffffffff]
[    0.207631] pci_bus 0000:0a: resource 0 [io  0xa400-0xa4ff]
[    0.207634] pci_bus 0000:0a: resource 1 [io  0xa800-0xa8ff]
[    0.207638] pci_bus 0000:0a: resource 2 [mem 0x38000000-0x3bffffff pref]
[    0.207642] pci_bus 0000:0a: resource 3 [mem 0x3c000000-0x3fffffff]
[    0.207723] NET: Registered protocol family 2
[    0.207828] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.207828] Switched to NOHz mode on CPU #0
[    0.207828] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.207828] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.209008] TCP: Hash tables configured (established 131072 bind 65536)
[    0.209017] TCP reno registered
[    0.209032] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.209082] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.209400] NET: Registered protocol family 1
[    0.209444] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.884079] pci 0000:01:05.0: Boot video device
[    0.884102] PCI: CLS 32 bytes, default 64
[    0.884759] audit: initializing netlink socket (disabled)
[    0.884785] type=2000 audit(1321462097.884:1): initialized
[    0.913942] Trying to unpack rootfs image as initramfs...
[    0.960437] highmem bounce pool size: 64 pages
[    0.960448] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.984714] VFS: Disk quotas dquot_6.5.2
[    0.984859] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.985991] fuse init (API version 7.16)
[    0.986151] msgmni has been set to 1707
[    1.000599] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.000660] io scheduler noop registered
[    1.000663] io scheduler deadline registered
[    1.000697] io scheduler cfq registered (default)
[    1.000925] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.000970] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.005269] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.011920] ACPI: AC Adapter [ACAD] (on-line)
[    1.012159] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.017870] ACPI: Lid Switch [LID]
[    1.017993] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.018004] ACPI: Power Button [PWRB]
[    1.018077] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.018082] ACPI: Power Button [PWRF]
[    1.018146] ACPI: acpi_idle registered with cpuidle
[    1.018646] Marking TSC unstable due to TSC halts in idle
[    1.043158] thermal LNXTHERM:00: registered as thermal_zone0
[    1.043165] ACPI: Thermal Zone [THRM] (63 C)
[    1.043260] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.043291] ERST: Table is not found!
[    1.043491] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.045275] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.045288] serial 0000:00:14.6: PCI INT B disabled
[    1.045478] Linux agpgart interface v0.103
[    1.047358] brd: module loaded
[    1.052160] ACPI: Battery Slot [BAT1] (battery absent)
[    1.052212] isapnp: Scanning for PnP cards...
[    1.058115] loop: module loaded
[    1.058536] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.058614] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.059125] Fixed MDIO Bus: probed
[    1.059161] PPP generic driver version 2.4.2
[    1.059274] tun: Universal TUN/TAP device driver, 1.6
[    1.059278] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.059401] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.059438] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.059468] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.059531] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    1.059636] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000
[    1.103872] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.184253] hub 1-0:1.0: USB hub found
[    1.184266] hub 1-0:1.0: 8 ports detected
[    1.184440] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.184496] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.184532] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.184694] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    1.184743] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000
[    1.256417] hub 2-0:1.0: USB hub found
[    1.256432] hub 2-0:1.0: 4 ports detected
[    1.256565] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.256601] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.256691] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.256736] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000
[    1.412534] hub 3-0:1.0: USB hub found
[    1.412550] hub 3-0:1.0: 4 ports detected
[    1.412686] uhci_hcd: USB Universal Host Controller Interface driver
[    1.412896] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.415958] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.415983] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.420349] mousedev: PS/2 mouse device common for all mice
[    1.420610] rtc_cmos 00:04: RTC can wake from S4
[    1.420778] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.420824] rtc0: alarms up to one month, 114 bytes nvram
[    1.421035] device-mapper: uevent: version 1.0.3
[    1.421177] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.421232] EISA: Probing bus 0 at eisa.0
[    1.421248] Cannot allocate resource for EISA slot 1
[    1.421283] Cannot allocate resource for EISA slot 8
[    1.421286] EISA: Detected 0 cards.
[    1.421307] cpufreq-nforce2: No nForce2 chipset.
[    1.421357] cpuidle: using governor ladder
[    1.421428] cpuidle: using governor menu
[    1.421431] EFI Variables Facility v0.08 2004-May-17
[    1.421827] TCP cubic registered
[    1.422042] NET: Registered protocol family 10
[    1.422825] NET: Registered protocol family 17
[    1.422863] Registering the dns_resolver key type
[    1.422908] Using IPI No-Shortcut mode
[    1.423037] PM: Hibernation image not present or could not be loaded.
[    1.423059] registered taskstats version 1
[    1.452091] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.679939] isapnp: No Plug & Play device found
[    1.793526] Freeing initrd memory: 13300k freed
[    1.842448]   Magic number: 3:717:843
[    1.842558] pci 0000:09:04.0: hash matches
[    1.842652] rtc_cmos 00:04: setting system clock to 2011-11-16 16:48:19 UTC (1321462099)
[    1.842685] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.842687] EDD information not available.
[    1.842873] Freeing unused kernel memory: 696k freed
[    1.843635] Write protecting the kernel text: 5332k
[    1.843687] Write protecting the kernel read-only data: 2188k
[    1.867529] udevd[76]: starting version 173
[    2.094715] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.094763] 8139cp 0000:09:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.095406] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.095479] 8139too 0000:09:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.112086] scsi0 : pata_atiixp
[    2.115442] scsi1 : pata_atiixp
[    2.115847] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    2.115852] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    2.126841] 8139too 0000:09:02.0: eth0: RealTek RTL8139 at 0xa000, 00:16:36:2b:a8:3c, IRQ 21
[    2.281411] ata2.00: ATAPI: DVD/CDRW UJDA770, 1.50, max UDMA/33
[    2.281523] ata1.00: ATA-6: FUJITSU MHV2060AH, 00400097, max UDMA/100
[    2.281527] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.288665] ata2.00: configured for UDMA/33
[    2.296757] ata1.00: configured for UDMA/100
[    2.296963] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060A 0040 PQ: 0 ANSI: 5
[    2.297234] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.297652] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.297726] sd 0:0:0:0: [sda] Write Protect is off
[    2.297731] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.297762] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.300043] scsi 1:0:0:0: CD-ROM            MATSHITA DVD/CDRW UJDA770 1.50 PQ: 0 ANSI: 5
[    2.301765] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.301770] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.301936] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.302028] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.404423]  sda: sda1 sda2 < sda5 >
[    2.404941] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.770570] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.520399] udevd[277]: starting version 173
[   12.568367] lp: driver loaded but no devices found
[   12.659249] Adding 914428k swap on /dev/sda5.  Priority:-1 extents:1 across:914428k 
[   12.879045] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.100253] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.102151] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   13.218804] lib80211: common routines for IEEE802.11 drivers
[   13.218813] lib80211_crypt: registered algorithm 'NULL'
[   13.247544] yenta_cardbus 0000:09:01.0: CardBus bridge found [1179:ff31]
[   13.247579] yenta_cardbus 0000:09:01.0: Using CSCINT to route CSC interrupts to PCI
[   13.247583] yenta_cardbus 0000:09:01.0: Routing CardBus interrupts to PCI
[   13.247591] yenta_cardbus 0000:09:01.0: TI: mfunc 0x015c1d22, devctl 0x44
[   13.343792] cfg80211: Calling CRDA to update world regulatory domain
[   13.363013] type=1400 audit(1321462111.016:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=538 comm="apparmor_parser"
[   13.363677] type=1400 audit(1321462111.016:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=538 comm="apparmor_parser"
[   13.364189] type=1400 audit(1321462111.020:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=538 comm="apparmor_parser"
[   13.440743] [drm] Initialized drm 1.1.0 20060810
[   13.461922] libipw: 802.11 data/management/control stack, git-1.1.13
[   13.461930] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.484941] yenta_cardbus 0000:09:01.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   13.484949] yenta_cardbus 0000:09:01.0: Socket status: 30000007
[   13.484964] yenta_cardbus 0000:09:01.0: pcmcia: parent PCI bridge window: [io  0xa000-0xafff]
[   13.484969] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: excluding 0xa000-0xa0ff 0xa400-0xa4ff
[   13.611439] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.611447] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.629756]  0xa800-0xa8ff
[   13.730467] yenta_cardbus 0000:09:01.0: pcmcia: parent PCI bridge window: [mem 0xc0200000-0xc02fffff]
[   13.730476] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0200000-0xc02fffff: excluding 0xc0200000-0xc020ffff
[   13.730493] yenta_cardbus 0000:09:01.0: pcmcia: parent PCI bridge window: [mem 0x38000000-0x3bffffff pref]
[   13.730497] pcmcia_socket pcmcia_socket0: cs: memory probe 0x38000000-0x3bffffff: excluding 0x38000000-0x3bffffff
[   13.795545] ipw2200 0000:09:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.795588] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   14.025256] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0/0x0
[   14.025270] synaptics: Toshiba Satellite L25                     detected, limiting rate to 40pps.
[   14.060240] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input4
[   14.119848] [drm] radeon defaulting to kernel modesetting.
[   14.119856] [drm] radeon kernel modesetting enabled.
[   14.119970] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.185237] [drm] initializing kernel modesetting (RS400 0x1002:0x5A62 0x1179:0xFF31).
[   14.185274] [drm] register mmio base: 0xC0100000
[   14.185276] [drm] register mmio size: 65536
[   14.185485] [drm] Generation 2 PCI interface, using max accessible memory
[   14.185495] radeon 0000:01:05.0: VRAM: 128M 0x0000000038000000 - 0x000000003FFFFFFF (128M used)
[   14.185500] radeon 0000:01:05.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   14.185518] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.185520] [drm] Driver supports precise vblank timestamp query.
[   14.185556] [drm] radeon: irq initialized.
[   14.185917] [drm] Detected VRAM RAM=128M, BAR=256M
[   14.185924] [drm] RAM width 128bits DDR
[   14.189614] [TTM] Zone  kernel: Available graphics memory: 444208 kiB.
[   14.189619] [TTM] Zone highmem: Available graphics memory: 447604 kiB.
[   14.189622] [TTM] Initializing pool allocator.
[   14.189664] [drm] radeon: 128M of VRAM memory ready
[   14.189667] [drm] radeon: 512M of GTT memory ready.
[   14.189709] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.220138] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[   14.237027] radeon 0000:01:05.0: WB enabled
[   14.264095] [drm] Loading R300 Microcode
[   14.436183] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.566856] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.643941] [drm] radeon: ring at 0x0000000040001000
[   14.643971] [drm] ring test succeeded in 1 usecs
[   14.644590] [drm] radeon: ib pool ready.
[   14.644688] [drm] ib test succeeded in 0 usecs
[   14.645272] [drm] Panel ID String: LPL                     
[   14.645275] [drm] Panel Size 1024x768
[   14.660405] [drm] radeon legacy LVDS backlight initialized
[   14.663282] cfg80211: World regulatory domain updated:
[   14.663288] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.663293] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.663297] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.663301] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.663305] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.663308] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.672147] [drm] Radeon Display Connectors
[   14.672155] [drm] Connector 0:
[   14.672158] [drm]   VGA
[   14.672162] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   14.672165] [drm]   Encoders:
[   14.672167] [drm]     CRT1: INTERNAL_DAC2
[   14.672169] [drm] Connector 1:
[   14.672171] [drm]   LVDS
[   14.672175] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   14.672177] [drm]   Encoders:
[   14.672180] [drm]     LCD1: INTERNAL_LVDS
[   14.672182] [drm] Connector 2:
[   14.672184] [drm]   S-video
[   14.672186] [drm]   Encoders:
[   14.672188] [drm]     TV1: INTERNAL_DAC2
[   14.741336] MC'97 0 converters and GPIO not ready (0x1)
[   14.743882] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x20f 0x280-0x297 0x370-0x377
[   14.754946] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x408-0x40f 0x4d0-0x4d7
[   14.784209] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   14.785158] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   14.786047] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   14.786115] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   14.786182] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   14.786257] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.873039] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[   14.924205] [drm] Radeon display connector LVDS-1: Found valid EDID
[   15.133037] [drm] fb mappable at 0xD0040000
[   15.133043] [drm] vram apper at 0xD0000000
[   15.133045] [drm] size 3145728
[   15.133047] [drm] fb depth is 24
[   15.133050] [drm]    pitch is 4096
[   15.133381] fbcon: radeondrmfb (fb0) is primary device
[   15.134656] Console: switching to colour frame buffer device 128x48
[   15.134706] fb0: radeondrmfb frame buffer device
[   15.134709] drm: registered panic notifier
[   15.134727] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[   15.212631] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.212638] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212642] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.212646] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212650] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.212654] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212657] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.212661] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212665] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.212669] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212672] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.212676] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212680] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.212684] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212687] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.212691] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212695] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.212699] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212702] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.212706] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.212710] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.212714] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   15.214180] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   15.221268] 8139too 0000:09:02.0: eth0: link down
[   15.222218] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.482096] init: failsafe main process (708) killed by TERM signal
[   15.491753] ppdev: user-space parallel port driver
[   15.557620] type=1400 audit(1321462113.212:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=762 comm="apparmor_parser"
[   15.572690] type=1400 audit(1321462113.228:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=762 comm="apparmor_parser"
[   16.292096] lib80211_crypt: registered algorithm 'WEP'
[   17.380990] type=1400 audit(1321462115.036:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=805 comm="apparmor_parser"
[   17.387066] type=1400 audit(1321462115.040:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=806 comm="apparmor_parser"
[   17.387760] type=1400 audit(1321462115.040:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=806 comm="apparmor_parser"
[   17.388543] type=1400 audit(1321462115.044:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=806 comm="apparmor_parser"
[   17.403829] type=1400 audit(1321462115.056:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=807 comm="apparmor_parser"
[   17.759585] init: apport pre-start process (845) terminated with status 1
[   17.835112] init: apport post-stop process (875) terminated with status 1
[   18.369435] Bluetooth: Core ver 2.16
[   18.369504] NET: Registered protocol family 31
[   18.369507] Bluetooth: HCI device and connection manager initialized
[   18.369511] Bluetooth: HCI socket layer initialized
[   18.369514] Bluetooth: L2CAP socket layer initialized
[   18.370825] Bluetooth: SCO socket layer initialized
[   18.422712] Bluetooth: RFCOMM TTY layer initialized
[   18.422722] Bluetooth: RFCOMM socket layer initialized
[   18.422725] Bluetooth: RFCOMM ver 1.11
[   18.481077] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.481085] Bluetooth: BNEP filters: protocol multicast
[   19.889242] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   20.197338] init: plymouth-stop pre-start process (1171) terminated with status 1
[   21.649794] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   27.104077] eth1: no IPv6 routers present
[ 1708.460083] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[ 1725.147407] 8139too 0000:09:02.0: eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 1725.147839] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1735.728085] eth0: no IPv6 routers present
[ 3330.903390] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.[/SIZE]

-----------------------------------

---

### Post by TheSluiceGate on 2011-11-16
Is this significant from my bootup log?

```


[ 3330.903390] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.


```

---

### Post by Toz on 2011-11-16
See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889784]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889784").

Perhaps its power management related ([https://bbs.archlinux.org/viewtopic.php?id=125232]("https://bbs.archlinux.org/viewtopic.php?id=125232")). Try disabling power management:
```
sudo iwconfig wlan0 power off
```

---

### Post by TheSluiceGate on 2011-11-16
I'm not quite sure quite what's required /meant by that first page you linked. Perhaps you can explain?

Thanks for that suggestion about power management.
I'd forgotten that I'd actually bought a new wireless pci card since the last time I tried switching off power management for it.

I'll try and get back asap.

---

### Post by TheSluiceGate on 2011-11-16
I tried that command for wlan0 and wlan1 just in case and got the output:

```

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan1 ; No such device.

```

Also I followed the instructions on that page you linked first, and got the following results:

[IMG]http://img850.imageshack.us/img850/7866/updatingproblemreport00.png[/IMG]

---

### Post by TheSluiceGate on 2011-11-16
Any thoughts anybody?

---

### Post by TheSluiceGate on 2011-11-16
Oh Xubuntu, it's almost over between you and me....

Windows, I hate you, but I may not be able to live without you...

---

### Post by TheSluiceGate on 2011-11-16
OK, I've tested a few times and it definitely drops the connectiona  lot quicker if I try to download large files, or try to load a large webpage while also streaming music.

Anyone? Please can you help.

---

### Post by Toz on 2011-11-16
> **TheSluiceGate said:**
> I tried that command for wlan0 and wlan1 just in case and got the output:

```

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.

Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan1 ; No such device.

```

Also I followed the instructions on that page you linked first, and got the following results:

[IMG]http://img850.imageshack.us/img850/7866/updatingproblemreport00.png[/IMG]

Sorry, that should of been eth1.
> 
Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)


eth1 IEEE 802.11bg ESSID:"***networknamehere***"
Mode:Managed Frequency:2.412 GHz Access Point: 00:0F:CC:BB:C7:34
Bit Rate:48 Mb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thr:off Fragment thr:off
[COLOR="Red"]Power Management: on[/COLOR]
Link Quality=95/100 Signal level=-16 dBm Noise level=-83 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Try instead:
```
sudo iwconfig eth1 power off
```

As for the bug report, it was meant to show you that one already existed. Feel free to add your information to the bug report and hopefully expedite its fix.

---

### Post by TheSluiceGate on 2011-11-16
Hey Toz,
thanks for your continued help.

Ok, so I successfully switched off power management, and initially things looked good, but it was actually while posting a reply to this thread a few minutes ago that the connection dropped. I rebooted to post this to you now.

[SIZE="1"](Also, as an aside, Power Management seems to switch itself back on when I reboot!)[/SIZE]

Any other ideas?

Thanks.

---

### Post by Toz on 2011-11-16
Is the essid on your router hidden (not being broadcast)? If so, try making it visible to see if that helps.

You can automate the power management of the wireless device by adding the following command to **/etc/rc.local** just above the **exit 0** command:
```
iwconfig eth1 power off
```

---

### Post by TheSluiceGate on 2011-11-16
No I have not got a hidden SSID.

[SIZE="1"](Also I have added that script to rc.local - thanks!)[/SIZE]

---

### Post by TheSluiceGate on 2011-11-17
Can anyone help with this?

---

### Post by TheSluiceGate on 2011-11-17
Sorry for the bump, but I really want to get this sorted...

---

### Post by Toz on 2011-11-17
Is the power management suggestion helping? Has there been any improvement? If not, when the wireless connection drops, post back the results of:
```
sudo iwconfig eth1
```.

---

### Post by TheSluiceGate on 2011-11-17
Hi Toz,
As I mentioned in my previous post, power management has made no noticeable difference at all. 

I am about to try and wirelessly connect to a different network than my home network as described above. Should the connection drop I will post the results of your code.
thanks.

---

### Post by TheSluiceGate on 2011-11-17
ok, different network, same disconnecting result:

Here's the code:

```

IEEE 802.11bg  ESSID:"network name"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:B8:7D:96   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:E3D9-566F-67   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=-20 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by Toz on 2011-11-17
Sorry, but I don't have any more suggestions to fix the problem. Perhaps the best is to add your information to the existing bug report at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889784]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/889784").

---

### Post by TheSluiceGate on 2011-11-17
Thanks for trying.

Should I stop bumping this thread in an attempt to see if someone else can help? Or should I just report the bug and let it lie for now?

---

### Post by Toz on 2011-11-17
Its up to you if you want to bump - maybe someone else might have some other ideas.

If you search google for "ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command" you'll find plenty of reports ([see here]("http://www.google.ca/search?q=ipw2200%3A+Failed+to+send+SYSTEM_CONFIG%3A+Already+sending+a+command.&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#q=ipw2200:+Failed+to+send+SYSTEM_CONFIG:+Already+sending+a+command.&hl=en&client=firefox-a&tbo=1&rls=org.mozilla:en-US:official&output=search&source=lnt&tbs=qdr:y&sa=X&ei=NJ3FTtr5LOHK2AWUirWwCQ&ved=0CAsQpwUoBQ&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=12a78ad1626ad583&biw=1143&bih=727")) but not many solutions. It is my understanding that the ipw2x00 firmware hasn't been updated in years, but there has been a recent spike in complaints about this similar issue. I'm guessing, though I can't prove it, some sort of kernel regression. Suggestions that I have come across included disabling power management and resetting router settings. However, you've disabled the power management features and tried another router. I guess one potential reason remains - a faulty wireless card. Do you dual-boot? Can you try the card in windows to see if it works? If this isn't an issue, then a bug report maybe the route you need to follow.

I just did a few more searches and came across this: [http://forums.gentoo.org/viewtopic-t-819782-start-0.html]("http://forums.gentoo.org/viewtopic-t-819782-start-0.html"). It would appear that downgrading the firmware worked (interesting since firmware hasn't changed in a while). Unfortunately, I'm not sure how this can be accomplished in ubuntu. The firmware files are available at: [http://ipw2200.sourceforge.net/firmware.php]("http://ipw2200.sourceforge.net/firmware.php").

---

### Post by TheSluiceGate on 2011-11-17
Hey thanks, that's a lot to digest. Looks like it's best not to bump for now, at least I've given that a serious looking over. 

Oh yeah, and I don't dual boot, but the wireless card worked perfectly in Windows.

---

### Post by TheSluiceGate on 2011-11-21
Hi All,
Toz has really done a lot to help me out here, but it's not worked out. I've decided not to downgrade my firmware.

Any other takers? There seems to be a lot of geniuses out there on the board...

---

### Post by TheSluiceGate on 2011-11-22
Anyone? Anyone? Beuller?

[IMG]http://www.kinesisinc.com/files/2011/03/large-ferris-buellers-day-off-blu-ray4.jpg[/IMG]

---

### Post by cajunlibra on 2011-11-22
I'm having a similar issue on Ubuntu.  I dualboot with XP SP3 and don't have this problem except in 11.10. I didn't have a problem in 11.04. I've seen that the issue was solved [here]("http://www.bigfatostrich.com/2011/10/solved-ubuntu-11-10-wireless-issues/") for broadcom adapters.

---

### Post by mihamtalamac on 2011-11-24
I had exactly the same problem (although I use Ubuntu 11.10).

 intel pro 2200bg wireless card using ipw2200 driver. Connection was constantly dropping (I migrated from Ubuntu 9.10 a week ago where everything was working fine, so this cannot be a faulty wireless card issue). I tried many solutions for wireless card issues for Ubuntu 11.10 (turn off the power management and so on) and the thing that helped me was to turn off N channel of my wireless router (now I only have bg functionalities of my router).

Connection is now stable :) . But speed of copying large files from another computer (running Win7) is on average 700-800 kB/s, which is really slow (before killing the N channel, speed was like this). It looks like that new Ubuntu has major issues with its wireless section.

Hope this can help someone with similar issues.

---

### Post by TheSluiceGate on 2011-11-27
> **mihamtalamac said:**
> I had exactly the same problem (although I use Ubuntu 11.10).

 intel pro 2200bg wireless card using ipw2200 driver. Connection was constantly dropping (I migrated from Ubuntu 9.10 a week ago where everything was working fine, so this cannot be a faulty wireless card issue). I tried many solutions for wireless card issues for Ubuntu 11.10 (turn off the power management and so on) and the thing that helped me was to turn off N channel of my wireless router (now I only have bg functionalities of my router).

Connection is now stable :) . But speed of copying large files from another computer (running Win7) is on average 700-800 kB/s, which is really slow (before killing the N channel, speed was like this). It looks like that new Ubuntu has major issues with its wireless section.

Hope this can help someone with similar issues.

Hey thanks for posting - I'll definitely check this out.

---

### Post by cajunlibra on 2011-11-29
My router is b and g only and I'm still having the problem. I can restart networkmanager but it doesn't work every time.

---

### Post by fdrake on 2011-11-29
i guess it's time for a kernel upgrade! Usually that solves (or exposes) some hardware issues!

---

### Post by cajunlibra on 2011-11-29
I've run all of the updates. Am I missing something?

---

### Post by fdrake on 2011-11-29
> **cajunlibra said:**
> I've run all of the updates. Am I missing something?
what kernel are you running?
```

uname r

```

check the new one and try to install it:
```

sudo apt-cache search linux-image 
sudo apt-get install linux-image-x.x.x-xx

```
progress and check release by release.. don't get the latest one right the way.

---

### Post by cajunlibra on 2011-11-29
3.0.0-13-generic

isn't that the latest one?

---

### Post by sasukeskapa on 2012-09-02
For this method worked :)
[http://ubuntuforums.org/showthread.php?t=1873537](http://ubuntuforums.org/showthread.php?t=1873537)
(Bad driver was the cause for me.)

---

