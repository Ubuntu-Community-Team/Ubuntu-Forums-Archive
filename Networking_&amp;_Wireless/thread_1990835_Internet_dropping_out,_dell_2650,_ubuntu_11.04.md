---
title: "Internet dropping out, dell 2650, ubuntu 11.04"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by esity on 2012-05-29
I have a couple dell 2650's I got for cheap. I am trying to get everything working but I have 1 machine that keeps dropping the connection. I can perform sudo apt-get update and it works fine but when i try to install something it will just sit at 0% and not download and if i do an update it will just sit at 0%. Not sure what is going on. I also have an airport extreme. Let me know if you can help me, i want to pull my hair out.

---

### Post by DELL JonathanS on 2012-05-30
Congrats on the new/old 2650s! Can you please paste the output of "dmesg" after you do an apt-get update that works followed by apt-get install that sits at 0%? Also what does "ethtool eth0" show? -- or if you are using a different NIC for your internet connection run ethtool on that instead. Does name resolution work ok i.e. "dig ubuntuforums.org" ? And are you able to do other types of network access -- ping or wget, or is it just apt-get that is having trouble?

---

### Post by esity on 2012-06-03
sorry about the time delay. just moved so i finally have internet again. I can't do install or update at all with any of them. currently i have an airport extreme hooked up to a 8 port gigabit switch. all three boxes that have ubuntu 11.04 won't connect to external sources. i can ping my airport extreme and other computes but i can't ping external things. 

any ideas?

miverson@ubuntu4:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic-pae (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 (Ubuntu 2.6.38-8.42-generic-pae 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000f7ff0000 (usable)
[    0.000000]  BIOS-e820: 00000000f7ff0000 - 00000000f7ffec00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000f7ffec00 - 00000000f7fff000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000180000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Concurrent Computer Corp. MediaHawk                  /0H3099, BIOS A16 08/19/2003
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x180000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EBFFF uncachable
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask F80000000 write-back
[    0.000000]   2 base 0F8000000 mask FF8000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000f8000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] initial memory mapped : 0 - 01e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1dfb000-1e00000
[    0.000000] RAMDISK: 365ee000 - 372ef000
[    0.000000] ACPI: RSDP 000fdc60 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000fdc74 00030 (v01 DELL   PE2650   00000001 MSFT 0100000A)
[    0.000000] ACPI: FACP 000fdca4 00074 (v01 DELL   PE2650   00000001 MSFT 0100000A)
[    0.000000] ACPI: DSDT f7ff0000 0346A (v01 DELL   PE2650   00000001 MSFT 0100000A)
[    0.000000] ACPI: FACS f7fffc00 00040
[    0.000000] ACPI: APIC 000fdd18 00088 (v01 DELL   PE2650   00000001 MSFT 0100000A)
[    0.000000] ACPI: SPCR 000fdda0 00050 (v01 DELL   PE2650   00000001 MSFT 0100000A)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 5252MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00180000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x000f7ff0
[    0.000000]     0: 0x00100000 -> 0x00180000
[    0.000000] On node 0 totalpages: 1539968
[    0.000000] free_area_init_node: node 0, pgdat c17babc0, node_mem_map f35ee200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 10505 pages used for memmap
[    0.000000]   HighMem zone: 1301225 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 17, address 0xfec00000, GSI 0-15
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec01000] gsi_base[16])
[    0.000000] IOAPIC[1]: apic_id 9, version 17, address 0xfec01000, GSI 16-31
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec02000] gsi_base[32])
[    0.000000] IOAPIC[2]: apic_id 10, version 17, address 0xfec02000, GSI 32-47
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at f7fff000 (gap: f7fff000:6c01000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s32320 r0 d20928 u524288
[    0.000000] pcpu-alloc: s32320 r0 d20928 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1527679
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-8-generic-pae root=/dev/mapper/ubuntu4-root ro quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 31456960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00180000)
[    0.000000] Memory: 6055960k/6291456k available (5349k kernel code, 103912k reserved, 2599k data, 720k init, 5246920k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17c4000 - 0xc1878000   ( 720 kB)
[    0.000000]       .data : 0xc1539545 - 0xc17c3540   (2599 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1539545   (5349 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:1024 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2787.251 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5574.50 BogoMIPS (lpj=11149004)
[    0.008014] pid_max: default: 32768 minimum: 301
[    0.008046] Security Framework initialized
[    0.008075] AppArmor: AppArmor initialized
[    0.008078] Yama: becoming mindful.
[    0.008161] Mount-cache hash table entries: 512
[    0.008381] Initializing cgroup subsys ns
[    0.008388] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.008393] Initializing cgroup subsys cpuacct
[    0.008401] Initializing cgroup subsys memory
[    0.008415] Initializing cgroup subsys devices
[    0.008419] Initializing cgroup subsys freezer
[    0.008423] Initializing cgroup subsys net_cls
[    0.008426] Initializing cgroup subsys blkio
[    0.008480] CPU: Physical Processor ID: 0
[    0.008484] CPU: Processor Core ID: 0
[    0.008488] mce: CPU supports 4 MCE banks
[    0.008502] CPU0: Thermal monitoring enabled (TM1)
[    0.014122] ACPI: Core revision 20110112
[    0.017254] ftrace: allocating 24250 entries in 48 pages
[    0.020115] Enabling APIC mode:  Flat.  Using 3 I/O APICs
[    0.020758] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.024001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.024001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.024001] ..... (found apic 0 pin 0) ...
[    0.066234] ....... works.
[    0.066237] CPU0: Intel(R) Xeon(TM) CPU 2.80GHz stepping 09
[    0.068003] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      18
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             0000007fffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000003ffff
[    0.068003] CPU 1 irqstacks, hard=f74b2000 soft=f74b4000
[    0.068003] Booting Node   0, Processors  #1
[    0.012000] Initializing CPU#1
[    0.156043] Brought up 2 CPUs
[    0.156050] Total of 2 processors activated (11149.48 BogoMIPS).
[    0.156466] devtmpfs: initialized
[    0.157862] print_constraints: dummy: 
[    0.157901] Time:  0:22:59  Date: 06/04/12
[    0.157970] NET: Registered protocol family 16
[    0.158050] Trying to unpack rootfs image as initramfs...
[    0.158276] EISA bus registered
[    0.158297] ACPI: bus type pci registered
[    0.177089] PCI: PCI BIOS revision 2.10 entry at 0xfc93e, last bus=5
[    0.177096] PCI: Using configuration type 1 for base access
[    0.179851] bio: create slab <bio-0> at 0
[    0.182593] ACPI: EC: Look up EC in DSDT
[    0.188046] ACPI: Interpreter enabled
[    0.188063] ACPI: (supports S0 S4 S5)
[    0.188098] ACPI: Using IOAPIC for interrupt routing
[    0.202264] ACPI: No dock devices found.
[    0.202272] HEST: Table not found.
[    0.202282] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.203503] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00])
[    0.205495] pci_root PNP0A03:00: host bridge window [io  0x0000-0x03af] (ignored)
[    0.205503] pci_root PNP0A03:00: host bridge window [io  0x03b0-0x03df] (ignored)
[    0.205511] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.205518] pci_root PNP0A03:00: host bridge window [io  0x03e0-0x0cf7] (ignored)
[    0.205525] pci_root PNP0A03:00: host bridge window [io  0x0d00-0x0fff] (ignored)
[    0.205532] pci_root PNP0A03:00: host bridge window [io  0xe000-0xefff] (ignored)
[    0.205538] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000e7fff] (ignored)
[    0.205550] pci_root PNP0A03:00: host bridge window [mem 0xfd000000-0xfebfffff] (ignored)
[    0.205583] pci 0000:00:00.0: [1166:0014] type 0 class 0x000600
[    0.205636] pci 0000:00:00.1: [1166:0014] type 0 class 0x000600
[    0.205681] pci 0000:00:00.2: [1166:0014] type 0 class 0x000600
[    0.205743] pci 0000:00:04.0: [1028:000c] type 0 class 0x00ff00
[    0.205771] pci 0000:00:04.0: reg 10: [mem 0xfeb80000-0xfeb80fff pref]
[    0.205789] pci 0000:00:04.0: reg 14: [io  0xecf8-0xecff]
[    0.205805] pci 0000:00:04.0: reg 18: [io  0xece8-0xecef]
[    0.205854] pci 0000:00:04.0: reg 30: [mem 0xfe000000-0xfe00ffff pref]
[    0.205906] pci 0000:00:04.1: [1028:0008] type 0 class 0x00ff00
[    0.205933] pci 0000:00:04.1: reg 10: [mem 0xfe102000-0xfe102fff]
[    0.205950] pci 0000:00:04.1: reg 14: [io  0xec80-0xecbf]
[    0.205967] pci 0000:00:04.1: reg 18: [mem 0xfeb00000-0xfeb7ffff pref]
[    0.206078] pci 0000:00:04.2: [1028:000d] type 0 class 0x00ff00
[    0.206105] pci 0000:00:04.2: reg 10: [io  0xecf4-0xecf7]
[    0.206244] pci 0000:00:0e.0: [1002:4752] type 0 class 0x000300
[    0.206270] pci 0000:00:0e.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.206287] pci 0000:00:0e.0: reg 14: [io  0xe800-0xe8ff]
[    0.206304] pci 0000:00:0e.0: reg 18: [mem 0xfe101000-0xfe101fff]
[    0.206353] pci 0000:00:0e.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.206382] pci 0000:00:0e.0: supports D1 D2
[    0.206404] pci 0000:00:0f.0: [1166:0201] type 0 class 0x000600
[    0.206471] pci 0000:00:0f.1: [1166:0212] type 0 class 0x000101
[    0.206492] pci 0000:00:0f.1: reg 10: [io  0x08c0-0x08c7]
[    0.206508] pci 0000:00:0f.1: reg 14: [io  0x08c8-0x08cb]
[    0.206523] pci 0000:00:0f.1: reg 18: [io  0x08d0-0x08d7]
[    0.206544] pci 0000:00:0f.1: reg 1c: [io  0x08d8-0x08db]
[    0.206567] pci 0000:00:0f.1: reg 20: [io  0x08b0-0x08bf]
[    0.206620] pci 0000:00:0f.2: [1166:0220] type 0 class 0x000c03
[    0.206641] pci 0000:00:0f.2: reg 10: [mem 0xfe100000-0xfe100fff]
[    0.206726] pci 0000:00:0f.3: [1166:0225] type 0 class 0x000601
[    0.206835] pci 0000:00:10.0: [1166:0101] type 0 class 0x000600
[    0.206912] pci 0000:00:10.2: [1166:0101] type 0 class 0x000600
[    0.206992] pci 0000:00:11.0: [1166:0101] type 0 class 0x000600
[    0.207078] pci 0000:00:11.2: [1166:0101] type 0 class 0x000600
[    0.207175] pci_bus 0000:00: on NUMA node 0
[    0.207186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.215295] ACPI: PCI Root Bridge [PCI4] (domain 0000 [bus 04-ff])
[    0.225244] pci_root PNP0A03:01: host bridge window [io  0xc000-0xcfff] (ignored)
[    0.225253] pci_root PNP0A03:01: host bridge window [mem 0xfb000000-0xfcdfffff] (ignored)
[    0.225292] pci 0000:04:08.0: [8086:0309] type 1 class 0x000604
[    0.225495] pci 0000:05:06.0: [9005:00cf] type 0 class 0x000100
[    0.225523] pci 0000:05:06.0: reg 10: [io  0xcc00-0xccff]
[    0.225545] pci 0000:05:06.0: reg 14: [mem 0xfccff000-0xfccfffff 64bit]
[    0.225591] pci 0000:05:06.0: reg 30: [mem 0xfcd00000-0xfcd1ffff pref]
[    0.225639] pci 0000:05:06.1: [9005:00cf] type 0 class 0x000100
[    0.225664] pci 0000:05:06.1: reg 10: [io  0xc800-0xc8ff]
[    0.225685] pci 0000:05:06.1: reg 14: [mem 0xfccfe000-0xfccfefff 64bit]
[    0.225729] pci 0000:05:06.1: reg 30: [mem 0xfcd00000-0xfcd1ffff pref]
[    0.225814] pci 0000:04:08.0: PCI bridge to [bus 05-05]
[    0.225824] pci 0000:04:08.0:   bridge window [io  0xc000-0xcfff]
[    0.225834] pci 0000:04:08.0:   bridge window [mem 0xfcc00000-0xfcdfffff]
[    0.225844] pci 0000:04:08.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.225859] pci_bus 0000:04: on NUMA node 0
[    0.225869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI4._PRT]
[    0.225997] ACPI: PCI Interrupt Routing Table [\_SB_.PCI4.ZION._PRT]
[    0.230884] ACPI: PCI Root Bridge [PCI3] (domain 0000 [bus 03])
[    0.239931] pci_root PNP0A03:02: host bridge window [io  0xd000-0xdfff] (ignored)
[    0.239941] pci_root PNP0A03:02: host bridge window [mem 0xfce00000-0xfcffffff] (ignored)
[    0.239983] pci 0000:03:06.0: [14e4:16a7] type 0 class 0x000200
[    0.240030] pci 0000:03:06.0: reg 10: [mem 0xfcf10000-0xfcf1ffff 64bit]
[    0.240108] pci 0000:03:06.0: PME# supported from D3hot D3cold
[    0.240117] pci 0000:03:06.0: PME# disabled
[    0.240154] pci 0000:03:08.0: [14e4:16a7] type 0 class 0x000200
[    0.240182] pci 0000:03:08.0: reg 10: [mem 0xfcf00000-0xfcf0ffff 64bit]
[    0.240255] pci 0000:03:08.0: PME# supported from D3hot D3cold
[    0.240263] pci 0000:03:08.0: PME# disabled
[    0.240309] pci_bus 0000:03: on NUMA node 0
[    0.240319] ACPI: PCI Interrupt Routing Table [\_SB_.PCI3._PRT]
[    0.243558] ACPI: PCI Root Bridge [PCI2] (domain 0000 [bus 02])
[    0.246467] pci_bus 0000:02: on NUMA node 0
[    0.246477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI2._PRT]
[    0.249308] ACPI: PCI Root Bridge [PCI1] (domain 0000 [bus 01])
[    0.252631] pci_bus 0000:01: on NUMA node 0
[    0.252640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.253079] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.253238] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.253417] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.253588] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 *11 12 14)
[    0.253753] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.253936] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.254102] ACPI: PCI Interrupt Link [LNK6] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.254261] ACPI: PCI Interrupt Link [LNK7] (IRQs 3 4 5 6 7 9 *10 11 12 14)
[    0.254426] ACPI: PCI Interrupt Link [LNK8] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.254608] ACPI: PCI Interrupt Link [LNK9] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.254768] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.254930] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 10 11 12 14)
[    0.255111] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14)
[    0.255276] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14)
[    0.255437] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 9 10 11 12 14)
[    0.255595] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14)
[    0.255781] ACPI: PCI Interrupt Link [LN10] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.255948] ACPI: PCI Interrupt Link [LN11] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.256135] ACPI: PCI Interrupt Link [LN12] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.256305] ACPI: PCI Interrupt Link [LN13] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.256493] ACPI: PCI Interrupt Link [LN14] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.256655] ACPI: PCI Interrupt Link [LN15] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.256836] ACPI: PCI Interrupt Link [LN16] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.256999] ACPI: PCI Interrupt Link [LN17] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.257159] ACPI: PCI Interrupt Link [LN18] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.257328] ACPI: PCI Interrupt Link [LN19] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.257519] ACPI: PCI Interrupt Link [LN1A] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.257681] ACPI: PCI Interrupt Link [LN1B] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.257841] ACPI: PCI Interrupt Link [LN1C] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.258005] ACPI: PCI Interrupt Link [LN1D] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.258173] ACPI: PCI Interrupt Link [LN1E] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.258334] ACPI: PCI Interrupt Link [LN1F] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.258509] ACPI: PCI Interrupt Link [LUSB] (IRQs 3 4 *5 6 7 10 11 12 14)
[    0.258823] vgaarb: device added: PCI:0000:00:0e.0,decodes=io+mem,owns=io+mem,locks=none
[    0.258853] vgaarb: loaded
[    0.259335] SCSI subsystem initialized
[    0.259470] libata version 3.00 loaded.
[    0.259586] usbcore: registered new interface driver usbfs
[    0.259614] usbcore: registered new interface driver hub
[    0.259704] usbcore: registered new device driver usb
[    0.260076] wmi: Mapper loaded
[    0.260082] PCI: Using ACPI for IRQ routing
[    0.260096] PCI: pci_cache_line_size set to 64 bytes
[    0.260244] reserve RAM buffer: 00000000f7ff0000 - 00000000f7ffffff 
[    0.260483] NetLabel: Initializing
[    0.260488] NetLabel:  domain hash size = 128
[    0.260492] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.260518] NetLabel:  unlabeled traffic allowed by default
[    0.280685] AppArmor: AppArmor Filesystem Enabled
[    0.280757] pnp: PnP ACPI init
[    0.280809] ACPI: bus type pnp registered
[    0.281817] pnp 00:00: [bus 00]
[    0.281825] pnp 00:00: [io  0x0000-0x03af window]
[    0.281831] pnp 00:00: [io  0x03b0-0x03df window]
[    0.281837] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.281844] pnp 00:00: [io  0x03e0-0x0cf7 window]
[    0.281850] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.281855] pnp 00:00: [io  0x0d00-0x0fff window]
[    0.281861] pnp 00:00: [io  0xe000-0xefff window]
[    0.281868] pnp 00:00: [mem 0x000d0000-0x000e7fff window]
[    0.281879] pnp 00:00: [mem 0xfd000000-0xfebfffff window]
[    0.281890] pnp 00:00: [mem 0x00000000-0xffffffff window]
[    0.281899] pnp 00:00: [mem 0x100000000-0xfffffffff window]
[    0.282051] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.282109] pnp 00:01: [io  0x0080-0x009f]
[    0.282115] pnp 00:01: [io  0x0000-0x001f]
[    0.282121] pnp 00:01: [io  0x00c0-0x00df]
[    0.282126] pnp 00:01: [io  0x040b]
[    0.282131] pnp 00:01: [io  0x04d6]
[    0.282137] pnp 00:01: [dma 4]
[    0.282199] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.282242] pnp 00:02: [io  0x00f0-0x00ff]
[    0.282261] pnp 00:02: [irq 13]
[    0.282322] pnp 00:02: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.282370] pnp 00:03: [io  0x0061]
[    0.282447] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.282842] pnp 00:04: [io  0x03f0-0x03f5]
[    0.282847] pnp 00:04: [io  0x03f7]
[    0.282859] pnp 00:04: [irq 6]
[    0.282864] pnp 00:04: [dma 2]
[    0.283030] pnp 00:04: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.285157] pnp 00:05: [io  0x03f8-0x03ff]
[    0.285173] pnp 00:05: [irq 4]
[    0.285326] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.285578] pnp 00:06: [io  0x02f8-0x02ff]
[    0.285588] pnp 00:06: [irq 3]
[    0.285732] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.285785] pnp 00:07: [io  0x0070-0x007f]
[    0.285797] pnp 00:07: [irq 8]
[    0.285867] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.285913] pnp 00:08: [io  0x0800-0x089f]
[    0.285918] pnp 00:08: [io  0x08a0-0x08af]
[    0.285924] pnp 00:08: [io  0x0c00-0x0cd7]
[    0.285929] pnp 00:08: [io  0x0f50-0x0f58]
[    0.285934] pnp 00:08: [io  0x08e0-0x08e3]
[    0.285939] pnp 00:08: [io  0x00e0-0x00ef]
[    0.286078] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.286086] system 00:08: [io  0x08a0-0x08af] has been reserved
[    0.286093] system 00:08: [io  0x0c00-0x0cd7] has been reserved
[    0.286099] system 00:08: [io  0x0f50-0x0f58] has been reserved
[    0.286106] system 00:08: [io  0x08e0-0x08e3] has been reserved
[    0.286115] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.290853] pnp 00:09: [bus 04-ff]
[    0.290861] pnp 00:09: [io  0x03b0-0x03af window disabled]
[    0.290868] pnp 00:09: [mem 0x000a0000-0x0009ffff window disabled]
[    0.290874] pnp 00:09: [io  0xc000-0xcfff window]
[    0.290881] pnp 00:09: [mem 0xfb000000-0xfcdfffff window]
[    0.291026] pnp 00:09: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.295448] pnp 00:0a: [bus 03]
[    0.295456] pnp 00:0a: [io  0xd000-0xdfff window]
[    0.295462] pnp 00:0a: [mem 0xfce00000-0xfcffffff window]
[    0.295618] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.298885] pnp 00:0b: [bus 02]
[    0.298892] pnp 00:0b: [io  0x03b0-0x03af window disabled]
[    0.298899] pnp 00:0b: [mem 0x000a0000-0x0009ffff window disabled]
[    0.298906] pnp 00:0b: [io  0x0000-0xffff window]
[    0.298912] pnp 00:0b: [mem 0x00000000-0xffffffff window]
[    0.299049] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.301943] pnp 00:0c: [bus 01]
[    0.301950] pnp 00:0c: [io  0x03b0-0x03af window disabled]
[    0.301957] pnp 00:0c: [mem 0x000a0000-0x0009ffff window disabled]
[    0.301964] pnp 00:0c: [io  0x0000-0xffff window]
[    0.301970] pnp 00:0c: [mem 0x00000000-0xffffffff window]
[    0.302120] pnp 00:0c: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.304260] pnp: PnP ACPI: found 13 devices
[    0.304266] ACPI: ACPI bus type pnp unregistered
[    0.304275] PnPBIOS: Disabled by ACPI PNP
[    0.343545] Switching to clocksource acpi_pm
[    0.343681] pci 0000:05:06.1: address space collision: [mem 0xfcd00000-0xfcd1ffff pref] conflicts with 0000:05:06.0 [mem 0xfcd00000-0xfcd1ffff pref]
[    0.343718] pci 0000:00:0e.0: BAR 6: assigned [mem 0xf8000000-0xf801ffff pref]
[    0.343732] pci 0000:04:08.0: BAR 15: assigned [mem 0xf8100000-0xf81fffff pref]
[    0.343740] pci 0000:05:06.1: BAR 6: assigned [mem 0xf8100000-0xf811ffff pref]
[    0.343747] pci 0000:04:08.0: PCI bridge to [bus 05-05]
[    0.343755] pci 0000:04:08.0:   bridge window [io  0xc000-0xcfff]
[    0.343766] pci 0000:04:08.0:   bridge window [mem 0xfcc00000-0xfcdfffff]
[    0.343776] pci 0000:04:08.0:   bridge window [mem 0xf8100000-0xf81fffff pref]
[    0.343816] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.343823] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.343831] pci_bus 0000:04: resource 0 [io  0x0000-0xffff]
[    0.343837] pci_bus 0000:04: resource 1 [mem 0x00000000-0xfffffffff]
[    0.343843] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
[    0.343850] pci_bus 0000:05: resource 1 [mem 0xfcc00000-0xfcdfffff]
[    0.343857] pci_bus 0000:05: resource 2 [mem 0xf8100000-0xf81fffff pref]
[    0.343864] pci_bus 0000:03: resource 0 [io  0x0000-0xffff]
[    0.343871] pci_bus 0000:03: resource 1 [mem 0x00000000-0xfffffffff]
[    0.343877] pci_bus 0000:02: resource 0 [io  0x0000-0xffff]
[    0.343884] pci_bus 0000:02: resource 1 [mem 0x00000000-0xfffffffff]
[    0.343890] pci_bus 0000:01: resource 0 [io  0x0000-0xffff]
[    0.343896] pci_bus 0000:01: resource 1 [mem 0x00000000-0xfffffffff]
[    0.343974] NET: Registered protocol family 2
[    0.343974] Switched to NOHz mode on CPU #0
[    0.343974] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.343560] Switched to NOHz mode on CPU #1
[    0.343974] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.343974] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.343974] TCP: Hash tables configured (established 131072 bind 65536)
[    0.343974] TCP reno registered
[    0.343974] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.343974] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.343974] NET: Registered protocol family 1
[    0.343974] pci 0000:00:0e.0: Boot video device
[    0.360123] PCI: CLS 64 bytes, default 64
[    0.360411] cpufreq-nforce2: No nForce2 chipset.
[    0.360753] audit: initializing netlink socket (disabled)
[    0.360775] type=2000 audit(1338769379.356:1): initialized
[    0.375361] highmem bounce pool size: 64 pages
[    0.375375] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.379642] VFS: Disk quotas dquot_6.5.2
[    0.379802] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.381458] fuse init (API version 7.16)
[    0.381699] msgmni has been set to 1580
[    0.382325] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.382417] io scheduler noop registered
[    0.382422] io scheduler deadline registered
[    0.382464] io scheduler cfq registered (default)
[    0.382815] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.382876] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.383278] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.383290] ACPI: Power Button [PWRF]
[    0.385718] ACPI: acpi_idle registered with cpuidle
[    0.391791] ERST: Table is not found!
[    0.392092] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.400115] isapnp: Scanning for PnP cards...
[    0.412630] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.608854] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.703856] Freeing initrd memory: 13316k freed
[    0.754800] isapnp: No Plug & Play device found
[    0.779648] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.800205] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.800469] serial 0000:00:04.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.820783] 0000:00:04.1: ttyS4 at I/O 0xec80 (irq = 23) is a 16550A
[    0.821159] Linux agpgart interface v0.103
[    0.823312] brd: module loaded
[    0.824341] loop: module loaded
[    0.824532] i2c-core: driver [adp5520] using legacy suspend method
[    0.824536] i2c-core: driver [adp5520] using legacy resume method
[    0.824858] pata_acpi 0000:00:0f.1: setting latency timer to 64
[    0.825452] Fixed MDIO Bus: probed
[    0.825504] PPP generic driver version 2.4.2
[    0.825590] tun: Universal TUN/TAP device driver, 1.6
[    0.825593] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.825759] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.825791] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.826018] ACPI: PCI Interrupt Link [LUSB] enabled at IRQ 11
[    0.826034] ohci_hcd 0000:00:0f.2: PCI INT A -> Link[LUSB] -> GSI 11 (level, low) -> IRQ 11
[    0.826061] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[    0.826145] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
[    0.826245] ohci_hcd 0000:00:0f.2: irq 11, io mem 0xfe100000
[    0.882241] hub 1-0:1.0: USB hub found
[    0.882251] hub 1-0:1.0: 4 ports detected
[    0.882383] uhci_hcd: USB Universal Host Controller Interface driver
[    0.882546] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.884677] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.884688] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.884915] mousedev: PS/2 mouse device common for all mice
[    0.885102] rtc_cmos 00:07: RTC can wake from S4
[    0.885231] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.885267] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.885402] device-mapper: uevent: version 1.0.3
[    0.885543] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.885685] device-mapper: multipath: version 1.2.0 loaded
[    0.885692] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.885830] EISA: Probing bus 0 at eisa.0
[    0.885835] EISA: Cannot allocate resource for mainboard
[    0.885876] EISA: Detected 0 cards.
[    0.885992] cpuidle: using governor ladder
[    0.885999] cpuidle: using governor menu
[    0.886540] TCP cubic registered
[    0.886751] NET: Registered protocol family 10
[    0.887837] NET: Registered protocol family 17
[    0.887871] Registering the dns_resolver key type
[    0.887949] Using IPI No-Shortcut mode
[    0.888164] PM: Hibernation image not present or could not be loaded.
[    0.888189] registered taskstats version 1
[    0.888500]   Magic number: 0:119:354
[    0.888508] input event0: hash matches
[    0.888626] rtc_cmos 00:07: setting system clock to 2012-06-04 00:23:00 UTC (1338769380)
[    0.888632] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.888635] EDD information not available.
[    0.888769] Freeing unused kernel memory: 720k freed
[    0.889490] Write protecting the kernel text: 5352k
[    0.889618] Write protecting the kernel read-only data: 2188k
[    0.939214] <30>udev[62]: starting version 167
[    1.191715] scsi0 : pata_serverworks
[    1.193245] scsi1 : pata_serverworks
[    1.193466] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8b0 irq 14
[    1.193474] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8b8 irq 15
[    1.222829] Floppy drive(s): fd0 is 1.44M
[    1.242024] FDC 0 is a National Semiconductor PC87306
[    1.248299] aic7xxx 0000:05:06.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
[    1.253490] tg3.c:v3.116 (December 3, 2010)
[    1.253530] tg3 0000:03:06.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    1.256067] usb 1-2: new low speed USB device using ohci_hcd and address 2
[    1.356349] ata1.00: ATAPI: TEAC CD-ROM CD-224E, K.9A, max UDMA/33
[    1.360098] Refined TSC clocksource calibration: 2787.396 MHz.
[    1.360106] Switching to clocksource tsc
[    1.464343] ata1.00: configured for UDMA/33
[    1.466683] scsi 0:0:0:0: CD-ROM            TEAC     CD-224E          K.9A PQ: 0 ANSI: 5
[    1.469173] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    1.469186] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.469535] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.469669] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.524525] tg3 0000:03:06.0: eth0: Tigon3 [partno(BCM95703A30) rev 1002] (PCIX:133MHz:64-bit) MAC address 00:0b:db:e7:56:e8
[    1.524532] tg3 0000:03:06.0: eth0: attached PHY is 5703 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.524538] tg3 0000:03:06.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.524543] tg3 0000:03:06.0: eth0: dma_rwctrl[769c4000] dma_mask[64-bit]
[    1.524589] tg3 0000:03:08.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
[    1.570373] tg3 0000:03:08.0: eth1: Tigon3 [partno(BCM95703A30) rev 1002] (PCIX:133MHz:64-bit) MAC address 00:0b:db:e7:56:e9
[    1.570384] tg3 0000:03:08.0: eth1: attached PHY is 5703 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.570392] tg3 0000:03:08.0: eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.570399] tg3 0000:03:08.0: eth1: dma_rwctrl[769c4000] dma_mask[64-bit]
[    1.625468] input: Generic USB Keyboard as /devices/pci0000:00/0000:00:0f.2/usb1/1-2/1-2:1.0/input/input1
[    1.628771] generic-usb 0003:040B:2000.0001: input,hidraw0: USB HID v1.10 Keyboard [Generic USB Keyboard] on usb-0000:00:0f.2-2/input0
[    1.639362] input: Generic USB Keyboard as /devices/pci0000:00/0000:00:0f.2/usb1/1-2/1-2:1.1/input/input2
[    1.639724] generic-usb 0003:040B:2000.0002: input,hidraw1: USB HID v1.10 Mouse [Generic USB Keyboard] on usb-0000:00:0f.2-2/input1
[    1.639779] usbcore: registered new interface driver usbhid
[    1.639785] usbhid: USB HID core driver
[   16.460030] scsi2 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   16.460033]         <Adaptec aic7899 Ultra160 SCSI adapter>
[   16.460035]         aic7899: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   16.460037] 
[   16.460406] aic7xxx 0000:05:06.1: PCI INT B -> GSI 31 (level, low) -> IRQ 31
[   16.464640] scsi 2:0:0:0: Direct-Access     IBM      IC35L036UCDY10-0 S27F PQ: 0 ANSI: 3
[   16.464656] scsi2:A:0:0: Tagged Queuing enabled.  Depth 8
[   16.464671] scsi target2:0:0: Beginning Domain Validation
[   16.466204] scsi target2:0:0: wide asynchronous
[   16.467430] scsi target2:0:0: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 127)
[   16.474444] scsi target2:0:0: Ending Domain Validation
[   17.765947] scsi 2:0:6:0: Processor         PE/PV    1x5 SCSI BP      1.1  PQ: 0 ANSI: 2
[   17.765965] scsi target2:0:6: Beginning Domain Validation
[   17.792968] scsi target2:0:6: Ending Domain Validation
[   19.857589] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   19.858054] scsi 2:0:6:0: Attached scsi generic sg2 type 3
[   19.858814] sd 2:0:0:0: [sda] 71132959 512-byte logical blocks: (36.4 GB/33.9 GiB)
[   19.859989] sd 2:0:0:0: [sda] Write Protect is off
[   19.859999] sd 2:0:0:0: [sda] Mode Sense: cb 00 00 08
[   19.861045] sd 2:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   19.878767]  sda: sda1 sda2 < sda5 >
[   19.880931] sd 2:0:0:0: [sda] Attached SCSI disk
[   20.345049] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   23.259968] <30>udev[301]: starting version 167
[   23.310661] lp: driver loaded but no devices found
[   23.365293] Adding 2097148k swap on /dev/mapper/ubuntu4-swap_1.  Priority:-1 extents:1 across:2097148k 
[   23.496981] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   23.644476] piix4_smbus 0000:00:0f.0: SMBus Host Controller at 0x8a0, revision 0
[   24.137851] type=1400 audit(1338769403.746:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=453 comm="apparmor_parser"
[   24.138871] type=1400 audit(1338769403.746:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=453 comm="apparmor_parser"
[   24.139519] type=1400 audit(1338769403.746:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=453 comm="apparmor_parser"
[   24.977741] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.222669] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.359187] type=1400 audit(1338769404.966:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=603 comm="apparmor_parser"
[   25.362278] type=1400 audit(1338769404.970:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=603 comm="apparmor_parser"
[   25.362870] type=1400 audit(1338769404.970:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=603 comm="apparmor_parser"
[   25.367290] type=1400 audit(1338769404.974:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=604 comm="apparmor_parser"
[   28.745991] tg3 0000:03:06.0: eth0: Link is up at 1000 Mbps, full duplex
[   28.745998] tg3 0000:03:06.0: eth0: Flow control is on for TX and on for RX
[   28.746157] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.764018] tg3 0000:03:08.0: eth1: Link is up at 1000 Mbps, full duplex
[   28.764025] tg3 0000:03:08.0: eth1: Flow control is on for TX and on for RX
[   28.764176] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   31.672034] scsi3 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   31.672037]         <Adaptec aic7899 Ultra160 SCSI adapter>
[   31.672038]         aic7899: Ultra160 Wide Channel B, SCSI Id=7, 32/253 SCBs
[   31.672040] 
[   31.672555] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.120008] eth0: no IPv6 routers present
[   39.168010] eth1: no IPv6 routers present
[ 1415.650088] usb 1-2: USB disconnect, address 2
[ 3239.676035] tg3 0000:03:08.0: BAR 0: set to [mem 0xfcf00000-0xfcf0ffff 64bit] (PCI address [0xfcf00000-0xfcf0ffff])
[ 3239.926433] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3242.929077] tg3 0000:03:08.0: eth1: Link is up at 1000 Mbps, full duplex
[ 3242.929084] tg3 0000:03:08.0: eth1: Flow control is on for TX and on for RX
[ 3242.929237] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3253.552009] eth1: no IPv6 routers present
[ 3292.432055] tg3 0000:03:06.0: BAR 0: set to [mem 0xfcf10000-0xfcf1ffff 64bit] (PCI address [0xfcf10000-0xfcf1ffff])
[ 3292.682477] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3295.726974] tg3 0000:03:06.0: eth0: Link is up at 1000 Mbps, full duplex
[ 3295.726981] tg3 0000:03:06.0: eth0: Flow control is on for TX and on for RX
[ 3295.727133] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3306.512009] eth0: no IPv6 routers present
[ 5023.668045] tg3 0000:03:06.0: BAR 0: set to [mem 0xfcf10000-0xfcf1ffff 64bit] (PCI address [0xfcf10000-0xfcf1ffff])
[ 5023.918512] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5026.837237] tg3 0000:03:06.0: eth0: Link is up at 1000 Mbps, full duplex
[ 5026.837244] tg3 0000:03:06.0: eth0: Flow control is on for TX and on for RX
[ 5026.837395] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5037.536010] eth0: no IPv6 routers present
[ 5040.204034] tg3 0000:03:08.0: BAR 0: set to [mem 0xfcf00000-0xfcf0ffff 64bit] (PCI address [0xfcf00000-0xfcf0ffff])
[ 5040.454403] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5043.394115] tg3 0000:03:08.0: eth1: Link is up at 1000 Mbps, full duplex
[ 5043.394122] tg3 0000:03:08.0: eth1: Flow control is on for TX and on for RX
[ 5043.394276] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 5054.320014] eth1: no IPv6 routers present

---

### Post by esity on 2012-06-05
anyone have this issue before or can offer me some advice?

---

### Post by DELL JonathanS on 2012-06-15
Thanks Esity. It sounds like this might be a routing or network mask issue. What does these outputs look like:
ifconfig -a

netstat -rn

Is the Airport Extreme your gateway (i.e. last device before the modem)? Or is that something else?

---

