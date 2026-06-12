---
title: "MSI CB54G2 Card won't connect.  Any help Appreciated"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by Sky Aisling on 2010-12-16
[SIZE=3]**MSI CB54G2 Card won't connect.  Any help Appreciated**[/SIZE]

        [LEFT][SIZE=3]**Compaq Presario 2100US**[/SIZE][/LEFT]
        [LEFT][SIZE=3]**XUbuntu 10.10 Maverick Meerkat *[SIZE=2](also tried with 10.04 and Puppy(s) with no connection in either OS)[/SIZE]***[/SIZE]
[SIZE=3]**Kernel: 2.6.35-22-generic i686**[/SIZE][/LEFT]
    [LEFT][SIZE=3]**RAM Memory: 938.7 MiB**[/SIZE][/LEFT]
    [LEFT][SIZE=3]**Processor: Celeron**[/SIZE][/LEFT]
    [LEFT][SIZE=3]**MSI Wireless 11G CardBus CB54G2 driver rt2500pci**[/SIZE]

[/LEFT]
        [LEFT][SIZE=3]Driver **rt2500pci** is present.[/SIZE][/LEFT]
    [LEFT][SIZE=3]Both green lights are active on card.[/SIZE][/LEFT]
    [LEFT][SIZE=3]Network Manager icon in system tray says 'connected'.[/SIZE][/LEFT]
    [LEFT][SIZE=3]'Ping' of Firefox says Firefox ***not*** receiving anything from system.[/SIZE]
[SIZE=3]
[/SIZE][/LEFT]
        [LEFT][SIZE=3]Here is sudo lshw -C network.[/SIZE][/LEFT]
    [LEFT][SIZE=3]Here is iwconfig.[/SIZE][/LEFT]
    [LEFT][SIZE=3]Here is dmesg.[/SIZE][/LEFT]
    [LEFT][SIZE=3]Here is iwlist scan[/SIZE][/LEFT]
    [LEFT][SIZE=3]Here is sudo /etc/init.d/networking restart[/SIZE]
[/LEFT]
[SIZE=3][/SIZE][LEFT][SIZE=3]
Hummm? Can't seem to make an attachment stick to this message.  Here is the terminal text:

sky@sky-Presario-2100:~$ sudo lshw -C network
[sudo] password for sky: 
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:54:41:1a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
       resources: irq:10 ioport:2400(size=256) memory:d0004000-d0004fff memory:54000000-5400ffff
  *-network
       description: Wireless interface
       product: RT2500 802.11g
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:db:0c:fb:66
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=2.6.35-22-generic firmware=N/A ip=10.42.43.1 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:50000000-50001fff
sky@sky-Presario-2100:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell:[COLOR=Yellow] [COLOR=Magenta]there is a number here[/COLOR][/COLOR]   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
sky@sky-Presario-2100:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bf70000 (usable)
[    0.000000]  BIOS-e820: 000000003bf70000 - 000000003bf7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bf7f000 - 000000003bf80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf80000 - 000000003c000000 (reserved)
[    0.000000]  BIOS-e820: 000000004bf80000 - 000000004c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3bf70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 base 03BF80000 mask FFFF80000 uncachable
[    0.000000]   5 base 04BF80000 mask FFFF80000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bf70000 (usable)
[    0.000000]  modified: 000000003bf70000 - 000000003bf7f000 (ACPI data)
[    0.000000]  modified: 000000003bf7f000 - 000000003bf80000 (ACPI NVS)
[    0.000000]  modified: 000000003bf80000 - 000000003c000000 (reserved)
[    0.000000]  modified: 000000004bf80000 - 000000004c000000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 2c590000 - 2cfd4000
[    0.000000] ACPI: RSDP 000f6c90 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3bf78f4f 0002C (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3bf7ef64 00074 (v01 ATI    Salmon   06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 3bf78f7b 05FE9 (v01    ATI MS2_1535 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3bf7ffc0 00040
[    0.000000] ACPI: BOOT 3bf7efd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine
[    0.000000] 71MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003bf70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bf70
[    0.000000] On node 0 totalpages: 245503
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 143 pages used for memmap
[    0.000000]   HighMem zone: 18147 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 4c000000 (gap: 4c000000:b3f80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243584
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=100e9503-5700-4ffe-945e-17843d02972c ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4912000 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (41 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [002c590000 - 002cfd4000]         RAMDISK
[    0.000000]   #4 [000009f800 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a1000 - 00009a4228]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 0001781000]         BOOTMEM
[    0.000000]   #11 [0001781000 - 0001781004]         BOOTMEM
[    0.000000]   #12 [0001781040 - 0001781100]         BOOTMEM
[    0.000000]   #13 [0001781100 - 0001781154]         BOOTMEM
[    0.000000]   #14 [0001781180 - 0001784180]         BOOTMEM
[    0.000000]   #15 [0001784180 - 0001784188]         BOOTMEM
[    0.000000]   #16 [00017841c0 - 00017847c0]         BOOTMEM
[    0.000000]   #17 [00017847c0 - 00017848d8]         BOOTMEM
[    0.000000]   #18 [0001784900 - 0001784940]         BOOTMEM
[    0.000000]   #19 [0001784940 - 0001784980]         BOOTMEM
[    0.000000]   #20 [0001784980 - 00017849c0]         BOOTMEM
[    0.000000]   #21 [00017849c0 - 0001784a00]         BOOTMEM
[    0.000000]   #22 [0001784a00 - 0001784a40]         BOOTMEM
[    0.000000]   #23 [0001784a40 - 0001784a80]         BOOTMEM
[    0.000000]   #24 [0001784a80 - 0001784ac0]         BOOTMEM
[    0.000000]   #25 [0001784ac0 - 0001784b00]         BOOTMEM
[    0.000000]   #26 [0001784b00 - 0001784b40]         BOOTMEM
[    0.000000]   #27 [0001784b40 - 0001784b50]         BOOTMEM
[    0.000000]   #28 [0001784b80 - 0001784bea]         BOOTMEM
[    0.000000]   #29 [0001784c00 - 0001784c6a]         BOOTMEM
[    0.000000]   #30 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #31 [0001786c80 - 0001786c84]         BOOTMEM
[    0.000000]   #32 [0001786cc0 - 0001786cc4]         BOOTMEM
[    0.000000]   #33 [0001786d00 - 0001786d04]         BOOTMEM
[    0.000000]   #34 [0001786d40 - 0001786d44]         BOOTMEM
[    0.000000]   #35 [0001786d80 - 0001786e30]         BOOTMEM
[    0.000000]   #36 [0001786e40 - 0001786ee8]         BOOTMEM
[    0.000000]   #37 [0001786f00 - 000178af00]         BOOTMEM
[    0.000000]   #38 [000180e000 - 000188e000]         BOOTMEM
[    0.000000]   #39 [000178af00 - 00017caf00]         BOOTMEM
[    0.000000]   #40 [000188e000 - 0001d3d380]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0003bf70)
[    0.000000] Memory: 949280k/982464k available (4928k kernel code, 32732k reserved, 2336k data, 684k init, 73160k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1595.061 MHz processor.
[    0.008015] Calibrating delay loop (skipped), value calculated using timer frequency.. 3190.12 BogoMIPS (lpj=6380244)
[    0.008028] pid_max: default: 32768 minimum: 301
[    0.008099] Security Framework initialized
[    0.008153] AppArmor: AppArmor initialized
[    0.008160] Yama: becoming mindful.
[    0.008303] Mount-cache hash table entries: 512
[    0.008682] Initializing cgroup subsys ns
[    0.008694] Initializing cgroup subsys cpuacct
[    0.008705] Initializing cgroup subsys memory
[    0.008732] Initializing cgroup subsys devices
[    0.008739] Initializing cgroup subsys freezer
[    0.008745] Initializing cgroup subsys net_cls
[    0.008827] CPU0: Hyper-Threading is disabled
[    0.008836] mce: CPU supports 4 MCE banks
[    0.008879] Performance Events: Netburst events, 
[    0.008890] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.008895] no hardware sampling interrupt available.
[    0.008900] Netburst P4/Xeon PMU driver.
[    0.008917] ... version:                0
[    0.008922] ... bit width:              40
[    0.008926] ... generic registers:      18
[    0.008932] ... value mask:             000000ffffffffff
[    0.008937] ... max period:             0000007fffffffff
[    0.008941] ... fixed-purpose events:   0
[    0.008946] ... event mask:             000000000003ffff
[    0.013931] SMP alternatives: switching to UP code
[    0.035304] Freeing SMP alternatives: 24k freed
[    0.035363] ACPI: Core revision 20100428
[    0.055138] ACPI: setting ELCR to 0200 (from 0420)
[    0.056042] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.056054] ftrace: allocating 21758 entries in 43 pages
[    0.060240] weird, boot CPU (#0) not listed by the BIOS.
[    0.060248] SMP motherboard not detected.
[    0.060253] Local APIC not detected. Using dummy APIC emulation.
[    0.060257] SMP disabled
[    0.060669] Brought up 1 CPUs
[    0.060678] Total of 1 processors activated (3190.12 BogoMIPS).
[    0.064456] devtmpfs: initialized
[    0.068391] regulator: core version 0.5
[    0.068456] Time:  0:05:02  Date: 12/17/10
[    0.068585] NET: Registered protocol family 16
[    0.068967] EISA bus registered
[    0.069007] ACPI: bus type pci registered
[    0.069296] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[    0.069302] PCI: Using configuration type 1 for base access
[    0.072288] bio: create slab <bio-0> at 0
[    0.074591] ACPI: EC: Look up EC in DSDT
[    0.088254] ACPI: Interpreter enabled
[    0.088271] ACPI: (supports S0 S3 S4 S5)
[    0.088324] ACPI: Using PIC for interrupt routing
[    0.101475] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.101497] ACPI: No dock devices found.
[    0.101511] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.105563] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.109153] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.109161] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.109167] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.109172] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.109179] pci_root PNP0A03:00: host bridge window [mem 0x3c000000-0xfff7ffff] (ignored)
[    0.109184] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d7fff] (ignored)
[    0.109190] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.109196] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.109241] pci 0000:00:00.0: reg 10: [mem 0xd4000000-0xd7ffffff pref]
[    0.109252] pci 0000:00:00.0: reg 14: [mem 0xd0005000-0xd0005fff pref]
[    0.109367] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd0000fff]
[    0.109417] pci 0000:00:02.0: PME# supported from D3cold
[    0.109427] pci 0000:00:02.0: PME# disabled
[    0.109471] pci 0000:00:06.0: reg 10: [io  0x1000-0x10ff]
[    0.109481] pci 0000:00:06.0: reg 14: [mem 0xd0001000-0xd0001fff]
[    0.109526] pci 0000:00:06.0: supports D1 D2
[    0.109535] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.109544] pci 0000:00:06.0: PME# disabled
[    0.109670] pci 0000:00:08.0: reg 10: [mem 0xd0002000-0xd0002fff]
[    0.109680] pci 0000:00:08.0: reg 14: [io  0x1400-0x14ff]
[    0.109724] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.109735] pci 0000:00:08.0: PME# disabled
[    0.109776] pci 0000:00:0a.0: reg 10: [mem 0xd0003000-0xd0003fff]
[    0.109800] pci 0000:00:0a.0: supports D1 D2
[    0.109808] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.109818] pci 0000:00:0a.0: PME# disabled
[    0.109880] pci 0000:00:10.0: reg 20: [io  0x2000-0x200f]
[    0.109978] pci 0000:00:11.0: quirk: [io  0x8000-0x803f] claimed by ali7101 ACPI
[    0.109987] pci 0000:00:11.0: quirk: [io  0x8040-0x805f] claimed by ali7101 SMB
[    0.110028] pci 0000:00:12.0: reg 10: [io  0x2400-0x24ff]
[    0.110038] pci 0000:00:12.0: reg 14: [mem 0xd0004000-0xd0004fff]
[    0.110067] pci 0000:00:12.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.110090] pci 0000:00:12.0: supports D1 D2
[    0.110097] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.110106] pci 0000:00:12.0: PME# disabled
[    0.110188] pci 0000:01:05.0: reg 10: [mem 0xd8000000-0xdfffffff pref]
[    0.110198] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.110208] pci 0000:01:05.0: reg 18: [mem 0xd0300000-0xd030ffff]
[    0.110230] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.110258] pci 0000:01:05.0: supports D1 D2
[    0.110302] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.110313] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.110320] pci 0000:00:01.0:   bridge window [mem 0xd0300000-0xd03fffff]
[    0.110328] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xdfffffff pref]
[    0.110379] pci_bus 0000:00: on NUMA node 0
[    0.110391] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.110542] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.115431] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[    0.115765] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[    0.116146] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 10) *0, disabled.
[    0.116477] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 10) *0, disabled.
[    0.116798] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[    0.117115] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
[    0.117430] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[    0.117750] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[    0.118069] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 *10)
[    0.118176] HEST: Table is not found!
[    0.118476] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.118484] vgaarb: loaded
[    0.119014] SCSI subsystem initialized
[    0.119221] libata version 3.00 loaded.
[    0.119433] usbcore: registered new interface driver usbfs
[    0.119475] usbcore: registered new interface driver hub
[    0.119603] usbcore: registered new device driver usb
[    0.120158] ACPI: WMI: Mapper loaded
[    0.120166] PCI: Using ACPI for IRQ routing
[    0.120180] PCI: pci_cache_line_size set to 64 bytes
[    0.120267] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.120274] reserve RAM buffer: 000000003bf70000 - 000000003bffffff 
[    0.120602] NetLabel: Initializing
[    0.120609] NetLabel:  domain hash size = 128
[    0.120612] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.120646] NetLabel:  unlabeled traffic allowed by default
[    0.120808] Switching to clocksource tsc
[    0.146574] AppArmor: AppArmor Filesystem Enabled
[    0.146633] pnp: PnP ACPI init
[    0.146696] ACPI: bus type pnp registered
[    0.149791] ERROR: Unable to locate IOAPIC for GSI 8
[    0.149903] ERROR: Unable to locate IOAPIC for GSI 13
[    0.150119] ERROR: Unable to locate IOAPIC for GSI 1
[    0.150233] ERROR: Unable to locate IOAPIC for GSI 12
[    0.150413] pnp 00:07: disabling [io  0x8004-0x8005] because it overlaps 0000:00:11.0 BAR 13 [io  0x8000-0x803f]
[    0.152312] ERROR: Unable to locate IOAPIC for GSI 7
[    0.154256] ERROR: Unable to locate IOAPIC for GSI 4
[    0.154748] pnp: PnP ACPI: found 10 devices
[    0.154756] ACPI: ACPI bus type pnp unregistered
[    0.154768] PnPBIOS: Disabled by ACPI PNP
[    0.154811] system 00:07: [io  0x040b] has been reserved
[    0.154817] system 00:07: [io  0x0480-0x048f] has been reserved
[    0.154823] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.154829] system 00:07: [io  0x04d6] has been reserved
[    0.154836] system 00:07: [io  0x8000-0x807f] could not be reserved
[    0.154842] system 00:07: [io  0xff00-0xff01] has been reserved
[    0.154848] system 00:07: [io  0xfe00-0xfefe] has been reserved
[    0.154858] system 00:07: [mem 0xd000a000-0xd000afff] has been reserved
[    0.194167] pci 0000:00:0a.0: BAR 15: assigned [mem 0x4c000000-0x4fffffff pref]
[    0.194178] pci 0000:00:0a.0: BAR 16: assigned [mem 0x50000000-0x53ffffff]
[    0.194185] pci 0000:00:12.0: BAR 6: assigned [mem 0x54000000-0x5400ffff pref]
[    0.194195] pci 0000:00:0a.0: BAR 13: assigned [io  0x1800-0x18ff]
[    0.194201] pci 0000:00:0a.0: BAR 14: assigned [io  0x1c00-0x1cff]
[    0.194209] pci 0000:01:05.0: BAR 6: assigned [mem 0xd0320000-0xd033ffff pref]
[    0.194216] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.194224] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.194232] pci 0000:00:01.0:   bridge window [mem 0xd0300000-0xd03fffff]
[    0.194239] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xdfffffff pref]
[    0.194248] pci 0000:00:0a.0: CardBus bridge to [bus 02-05]
[    0.194253] pci 0000:00:0a.0:   bridge window [io  0x1800-0x18ff]
[    0.194261] pci 0000:00:0a.0:   bridge window [io  0x1c00-0x1cff]
[    0.194268] pci 0000:00:0a.0:   bridge window [mem 0x4c000000-0x4fffffff pref]
[    0.194275] pci 0000:00:0a.0:   bridge window [mem 0x50000000-0x53ffffff]
[    0.194311] pci 0000:00:0a.0: enabling device (0000 -> 0003)
[    0.194852] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[    0.194859] PCI: setting IRQ 11 as level-triggered
[    0.194869] pci 0000:00:0a.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[    0.194885] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.194890] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.194896] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.194901] pci_bus 0000:01: resource 1 [mem 0xd0300000-0xd03fffff]
[    0.194906] pci_bus 0000:01: resource 2 [mem 0xd8000000-0xdfffffff pref]
[    0.194913] pci_bus 0000:02: resource 0 [io  0x1800-0x18ff]
[    0.194918] pci_bus 0000:02: resource 1 [io  0x1c00-0x1cff]
[    0.194923] pci_bus 0000:02: resource 2 [mem 0x4c000000-0x4fffffff pref]
[    0.194929] pci_bus 0000:02: resource 3 [mem 0x50000000-0x53ffffff]
[    0.195049] NET: Registered protocol family 2
[    0.195258] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.195953] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.198274] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.199640] TCP: Hash tables configured (established 131072 bind 65536)
[    0.199653] TCP reno registered
[    0.199676] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.199719] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.200059] NET: Registered protocol family 1
[    0.415190] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    0.415235] pci 0000:01:05.0: Boot video device
[    0.415245] PCI: CLS 32 bytes, default 64
[    0.415448] Simple Boot Flag at 0x37 set to 0x1
[    0.415731] cpufreq-nforce2: No nForce2 chipset.
[    0.415805] Scanning for low memory corruption every 60 seconds
[    0.416195] audit: initializing netlink socket (disabled)
[    0.416230] type=2000 audit(1292544302.412:1): initialized
[    0.431481] Trying to unpack rootfs image as initramfs...
[    0.451512] highmem bounce pool size: 64 pages
[    0.451530] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.459430] VFS: Disk quotas dquot_6.5.2
[    0.459675] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.461393] fuse init (API version 7.14)
[    0.461749] msgmni has been set to 1711
[    0.468074] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.468085] io scheduler noop registered
[    0.468090] io scheduler deadline registered
[    0.468125] io scheduler cfq registered (default)
[    0.468472] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.468545] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.469426] ACPI: AC Adapter [ACAD] (on-line)
[    0.469703] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.469719] ACPI: Power Button [PWRB]
[    0.469828] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.474172] ACPI: Lid Switch [LID]
[    0.474416] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.474432] ACPI: Power Button [PWRF]
[    0.474810] ACPI: acpi_idle registered with cpuidle
[    0.475090] Marking TSC unstable due to TSC halts in idle
[    0.484311] Switching to clocksource acpi_pm
[    0.486398] thermal LNXTHERM:01: registered as thermal_zone0
[    0.486430] ACPI: Thermal Zone [THRM] (48 C)
[    0.486816] ERST: Table is not found!
[    0.487464] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.487673] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.488760] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.488968] serial 0000:00:08.0: enabling device (0000 -> 0003)
[    0.489498] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[    0.489506] PCI: setting IRQ 10 as level-triggered
[    0.489518] serial 0000:00:08.0: PCI INT A -> Link[LNK6] -> GSI 10 (level, low) -> IRQ 10
[    0.489532] serial 0000:00:08.0: PCI INT A disabled
[    0.496752] ACPI: Battery Slot [BAT1] (battery absent)
[    0.496843] isapnp: Scanning for PnP cards...
[    0.503125] brd: module loaded
[    0.504799] loop: module loaded
[    0.505623] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    0.505742] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    0.506844] Fixed MDIO Bus: probed
[    0.506971] PPP generic driver version 2.4.2
[    0.507186] tun: Universal TUN/TAP device driver, 1.6
[    0.507192] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.507480] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.507548] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.561130] ACPI: PCI Interrupt Link [LNK8] enabled at IRQ 10
[    0.561147] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNK8] -> GSI 10 (level, low) -> IRQ 10
[    0.561211] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.561501] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    0.561562] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[    0.644524] hub 1-0:1.0: USB hub found
[    0.644546] hub 1-0:1.0: 4 ports detected
[    0.644731] uhci_hcd: USB Universal Host Controller Interface driver
[    0.645018] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.647973] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.648000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.653184] mice: PS/2 mouse device common for all mice
[    0.653847] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.653899] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    0.654236] device-mapper: uevent: version 1.0.3
[    0.658040] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.664404] device-mapper: multipath: version 1.1.1 loaded
[    0.664419] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.665014] EISA: Probing bus 0 at eisa.0
[    0.665036] Cannot allocate resource for EISA slot 1
[    0.665042] Cannot allocate resource for EISA slot 2
[    0.665080] Cannot allocate resource for EISA slot 8
[    0.665084] EISA: Detected 0 cards.
[    0.669017] cpuidle: using governor ladder
[    0.669183] cpuidle: using governor menu
[    0.669928] TCP cubic registered
[    0.670318] NET: Registered protocol family 10
[    0.671300] lo: Disabled Privacy Extensions
[    0.671781] NET: Registered protocol family 17
[    0.671950] Using IPI No-Shortcut mode
[    0.672402] PM: Resume from disk failed.
[    0.672440] registered taskstats version 1
[    0.672746]   Magic number: 6:822:51
[    0.672963] rtc_cmos 00:02: setting system clock to 2010-12-17 00:05:05 UTC (1292544305)
[    0.672971] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.672974] EDD information not available.
[    0.690723] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.095858] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    1.183821] isapnp: No Plug & Play device found
[    1.504000] Freeing initrd memory: 10512k freed
[    1.531528] Freeing unused kernel memory: 684k freed
[    1.533395] Write protecting the kernel text: 4932k
[    1.533457] Write protecting the kernel read-only data: 1976k
[    1.604636] udev[65]: starting version 163
[    2.266566] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    2.266571]   originally by Donald Becker <becker@scyld.com>
[    2.266573]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    2.267178] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    2.267191] natsemi 0000:00:12.0: PCI INT A -> Link[LNK1] -> GSI 10 (level, low) -> IRQ 10
[    2.306619] natsemi eth0: NatSemi DP8381[56] at 0xd0004000 (0000:00:12.0), 00:0b:cd:54:41:1a, IRQ 10, port TP.
[    2.306721] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    2.319189] scsi0 : pata_ali
[    2.330843] scsi1 : pata_ali
[    2.331468] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[    2.331477] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[    2.382983] Initializing USB Mass Storage driver...
[    2.403913] scsi2 : usb-storage 1-2:1.0
[    2.414803] usbcore: registered new interface driver usb-storage
[    2.414812] USB Mass Storage support registered.
[    2.492525] ata1.00: ATA-5: HITACHI_DK23EA-30, 00K4A0A2, max UDMA/100
[    2.492536] ata1.00: 58605120 sectors, multi 16: LBA 
[    2.500409] ata1.00: configured for UDMA/100
[    2.500759] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23EA-3 00K4 PQ: 0 ANSI: 5
[    2.501287] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.501802] sd 0:0:0:0: [sda] 58605120 512-byte logical blocks: (30.0 GB/27.9 GiB)
[    2.501971] sd 0:0:0:0: [sda] Write Protect is off
[    2.501979] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.502054] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.502599]  sda: sda1 sda2 < sda5 >
[    2.557427] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.680452] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R2312, 1905, max MWDMA2
[    2.680509] ata2.00: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled
[    2.680514] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    2.696383] ata2.00: configured for MWDMA2
[    2.705109] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2312 1905 PQ: 0 ANSI: 5
[    2.718636] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.718649] Uniform CD-ROM driver Revision: 3.20
[    2.719071] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.719295] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.215162] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.426188] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[    3.427760] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.437160] sd 2:0:0:0: [sdb] 3948543 512-byte logical blocks: (2.02 GB/1.88 GiB)
[    3.444250] sd 2:0:0:0: [sdb] Write Protect is off
[    3.444263] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    3.444271] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.470107] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.470135]  sdb: sdb1
[    3.502210] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    3.502224] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   20.236496] Adding 1253372k swap on /dev/sda5.  Priority:-1 extents:1 across:1253372k 
[   20.398658] udev[278]: starting version 163
[   20.605982] lp: driver loaded but no devices found
[   21.059596] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.191370] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.304359] Linux agpgart interface v0.103
[   21.409317] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input4
[   21.409523] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   21.415708] yenta_cardbus 0000:00:0a.0: CardBus bridge found [103c:002a]
[   21.415742] yenta_cardbus 0000:00:0a.0: O2: enabling read prefetch/write burst
[   21.570355] type=1400 audit(1292544326.391:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=399 comm="apparmor_parser"
[   21.571439] type=1400 audit(1292544326.391:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=399 comm="apparmor_parser"
[   21.572187] type=1400 audit(1292544326.395:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=399 comm="apparmor_parser"
[   21.669932] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x00b8, PCI irq 11
[   21.669941] yenta_cardbus 0000:00:0a.0: Socket status: 30000821
[   21.681552] psmouse serio1: ID: 10 00 64
[   21.763140] parport_pc 00:08: reported by Plug and Play ACPI
[   21.763226] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   21.847951] agpgart-ati 0000:00:00.0: Ati IGP330/340/345/350/M chipset
[   21.848223] reserve_ram_pages_type failed 0x35351000-0x35352000, track 0x10, req 0x10
[   21.848783] reserve_ram_pages_type failed 0x3534d000-0x3534e000, track 0x10, req 0x10
[   21.850117] reserve_ram_pages_type failed 0x35354000-0x35355000, track 0x10, req 0x10
[   21.850700] reserve_ram_pages_type failed 0x35355000-0x35356000, track 0x10, req 0x10
[   21.851256] reserve_ram_pages_type failed 0x35352000-0x35353000, track 0x10, req 0x10
[   21.851862] reserve_ram_pages_type failed 0x310b3000-0x310b4000, track 0x10, req 0x10
[   21.914418] reserve_ram_pages_type failed 0x3124e000-0x3124f000, track 0x10, req 0x10
[   21.914982] reserve_ram_pages_type failed 0x31250000-0x31251000, track 0x10, req 0x10
[   21.915541] reserve_ram_pages_type failed 0x31247000-0x31248000, track 0x10, req 0x10
[   21.988748] lp0: using parport0 (interrupt-driven).
[   21.996241] reserve_ram_pages_type failed 0x35219000-0x3521a000, track 0x10, req 0x10
[   21.996834] reserve_ram_pages_type failed 0x35244000-0x35245000, track 0x10, req 0x10
[   21.997391] reserve_ram_pages_type failed 0x353da000-0x353db000, track 0x10, req 0x10
[   21.997948] reserve_ram_pages_type failed 0x35243000-0x35244000, track 0x10, req 0x10
[   21.998505] reserve_ram_pages_type failed 0x3536d000-0x3536e000, track 0x10, req 0x10
[   21.999061] reserve_ram_pages_type failed 0x350f2000-0x350f3000, track 0x10, req 0x10
[   21.999617] reserve_ram_pages_type failed 0x35246000-0x35247000, track 0x10, req 0x10
[   22.126226] reserve_ram_pages_type failed 0x3120d000-0x3120e000, track 0x10, req 0x10
[   22.163326] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   22.172856] input: PS2++ Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   22.632163] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   22.632237] pci 0000:02:00.0: reg 10: [mem 0xffffe000-0xffffffff]
[   22.632337] pci 0000:02:00.0: BAR 0: assigned [mem 0x50000000-0x50001fff]
[   22.632349] pci 0000:02:00.0: BAR 0: set to [mem 0x50000000-0x50001fff] (PCI address [0x50000000-0x50001fff]
[   22.827053] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   22.829770] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   22.836962] ppdev: user-space parallel port driver
[   22.880850]  excluding 0x3f0-0x3ff 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   22.881574] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   22.882534] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   22.883654] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xdc000-0xfffff
[   22.883829] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   22.883991] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   22.920231] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   22.941338] [drm] Initialized drm 1.1.0 20060810
[   23.313079] cfg80211: Calling CRDA to update world regulatory domain
[   23.493983] cfg80211: World regulatory domain updated:
[   23.493998]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.494005]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.494012]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.494019]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.494025]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.494031]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.055399] rt2500pci 0000:02:00.0: enabling device (0000 -> 0002)
[   24.055428] rt2500pci 0000:02:00.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[   24.055442] rt2500pci 0000:02:00.0: setting latency timer to 64
[   24.101457] [drm] radeon defaulting to kernel modesetting.
[   24.101469] [drm] radeon kernel modesetting enabled.
[   24.101667] radeon 0000:01:05.0: power state changed by ACPI to D0
[   24.101689] radeon 0000:01:05.0: power state changed by ACPI to D0
[   24.102212] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[   24.102223] radeon 0000:01:05.0: PCI INT A -> Link[LNK0] -> GSI 10 (level, low) -> IRQ 10
[   24.120797] ALI 5451 0000:00:06.0: enabling device (0005 -> 0007)
[   24.121341] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[   24.121349] PCI: setting IRQ 5 as level-triggered
[   24.121359] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNK7] -> GSI 5 (level, low) -> IRQ 5
[   24.168624] [drm] initializing kernel modesetting (RS200 0x1002:0x4337).
[   24.178392] [drm] register mmio base: 0xD0300000
[   24.178401] [drm] register mmio size: 65536
[   24.178787] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   24.178823] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   24.178881] radeon 0000:01:05.0: putting AGP V2 device into 4x mode
[   24.178898] radeon 0000:01:05.0: GTT: 64M 0xD4000000 - 0xD7FFFFFF
[   24.178912] radeon 0000:01:05.0: VRAM: 64M 0x3C000000 - 0x3FFFFFFF (64M used)
[   24.287145] [drm] radeon: irq initialized.
[   24.287346] [drm] Detected VRAM RAM=64M, BAR=128M
[   24.287356] [drm] RAM width 64bits DDR
[   24.304580] [TTM] Zone  kernel: Available graphics memory: 443670 kiB.
[   24.304589] [TTM] Zone highmem: Available graphics memory: 480250 kiB.
[   24.304594] [TTM] Initializing pool allocator.
[   24.304667] [drm] radeon: 64M of VRAM memory ready
[   24.304674] [drm] radeon: 64M of GTT memory ready.
[   24.337547] type=1400 audit(1292544329.159:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=680 comm="apparmor_parser"
[   24.338640] type=1400 audit(1292544329.159:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=680 comm="apparmor_parser"
[   24.339252] type=1400 audit(1292544329.159:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=680 comm="apparmor_parser"
[   24.434185] [drm] Loading R100 Microcode
[   24.438500] type=1400 audit(1292544329.259:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=689 comm="apparmor_parser"
[   24.483898] [drm] radeon: ring at 0x00000000D4000000
[   24.483931] [drm] ring test succeeded in 1 usecs
[   24.484963] [drm] radeon: ib pool ready.
[   24.485172] [drm] ib test succeeded in 0 usecs
[   24.504477] [drm] Panel ID String: QDI141X1LH03            
[   24.504489] [drm] Panel Size 1024x768
[   24.508702] [drm] Default TV standard: NTSC
[   24.508714] [drm] 14.318180000 MHz TV ref clk
[   24.508726] [drm] Default TV standard: NTSC
[   24.508730] [drm] 14.318180000 MHz TV ref clk
[   24.509337] [drm] Radeon Display Connectors
[   24.509347] [drm] Connector 0:
[   24.509351] [drm]   VGA
[   24.509357] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   24.509361] [drm]   Encoders:
[   24.509365] [drm]     CRT1: INTERNAL_DAC1
[   24.509369] [drm] Connector 1:
[   24.509372] [drm]   LVDS
[   24.509378] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   24.509381] [drm]   Encoders:
[   24.509385] [drm]     LCD1: INTERNAL_LVDS
[   24.509388] [drm] Connector 2:
[   24.509391] [drm]   S-video
[   24.509394] [drm]   Encoders:
[   24.509398] [drm]     TV1: INTERNAL_DAC2
[   24.535715] phy0: Selected rate control algorithm 'minstrel'
[   24.538809] Registered led device: rt2500pci-phy0::radio
[   24.539177] Registered led device: rt2500pci-phy0::quality
[   24.616603] type=1400 audit(1292544329.439:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=689 comm="apparmor_parser"
[   24.683870] type=1400 audit(1292544329.503:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=689 comm="apparmor_parser"
[   24.787749] type=1400 audit(1292544329.607:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=711 comm="apparmor_parser"
[   24.801576] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.849468] eth0: DSPCFG accepted after 0 usec.
[   24.855907] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.072185] [drm] fb mappable at 0xD8040000
[   25.072196] [drm] vram apper at 0xD8000000
[   25.072200] [drm] size 3145728
[   25.072204] [drm] fb depth is 24
[   25.072207] [drm]    pitch is 4096
[   25.293007] Console: switching to colour frame buffer device 128x48
[   25.309871] fb0: radeondrmfb frame buffer device
[   25.309877] drm: registered panic notifier
[   25.322198] Slow work thread pool: Starting up
[   25.331445] Slow work thread pool: Ready
[   25.331487] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   27.064122] AC'97 1 does not respond - RESET
[   27.080236] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   27.080256] ali mixer 1 creating error.
[   29.054757] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   46.820125] wlan0: Creating new IBSS network, BSSID 92:9c:64:9a:28:c1
[   48.005105] ip_tables: (C) 2000-2006 Netfilter Core Team
[   48.128615] nf_conntrack version 0.5.0 (15007 buckets, 60028 max)
[   48.138464] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   48.138477] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   48.138482] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   48.992094] wlan0: no IPv6 routers present
[   66.621411] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  128.256136] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  190.119131] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  252.352941] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  313.379858] ACPI: EC: GPE storm detected, transactions will use polling mode
[  347.104095] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  379.104097] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  411.104403] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  443.104087] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  475.104122] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  500.549579] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
sky@sky-Presario-2100:~$ 


sky@sky-Presario-2100:~$ lsmod \ grep CB54G2
Usage: lsmod
sky@sky-Presario-2100:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
usb_storage            40172  1 
ipt_MASQUERADE          1419  1 
xt_state                1014  1 
ipt_REJECT              2004  2 
xt_tcpudp               1927  4 
iptable_filter          1302  1 
nf_nat_h323             5121  0 
nf_conntrack_h323      46894  1 nf_nat_h323
nf_nat_pptp             1996  0 
nf_conntrack_pptp       4681  1 nf_nat_pptp
nf_conntrack_proto_gre     3901  1 nf_conntrack_pptp
nf_nat_proto_gre        1271  1 nf_nat_pptp
nf_nat_tftp              728  0 
nf_conntrack_tftp       2905  1 nf_nat_tftp
nf_nat_sip              5574  0 
nf_conntrack_sip       18703  1 nf_nat_sip
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
nf_conntrack_ftp        5361  1 nf_nat_ftp
iptable_nat             3752  1 
nf_nat                 16289  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10783  4 iptable_nat,nf_nat
nf_conntrack           63258  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
ip_tables              10460  2 iptable_filter,iptable_nat
x_tables               15921  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
arc4                    1165  2 
rt2500pci              13731  0 
rt2x00pci               6029  1 rt2500pci
rt2x00lib              27275  2 rt2500pci,rt2x00pci
radeon                825934  2 
snd_ali5451            15875  4 
led_class               2633  1 rt2x00lib
snd_ac97_codec         99227  1 snd_ali5451
mac80211              231541  2 rt2x00pci,rt2x00lib
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_ali5451,snd_ac97_codec
cfg80211              144470  2 rt2x00lib,mac80211
snd_seq_midi            4588  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
eeprom_93cx6            1345  1 rt2500pci
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
pcmcia                 35973  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  4 radeon,ttm,drm_kms_helper
parport_pc             26058  1 
psmouse                59033  0 
snd                    49006  15 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
yenta_socket           21518  0 
ati_agp                 5202  1 
i2c_algo_bit            5168  1 radeon
video                  18712  0 
pcmcia_rsrc            10566  1 yenta_socket
i2c_ali15x3             5190  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
output                  1883  1 video
soundcore                880  1 snd
shpchp                 29886  0 
i2c_ali1535             4865  0 
snd_page_alloc          7120  1 snd_pcm
agpgart                32011  3 ttm,drm,ati_agp
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
natsemi                24030  0 
pata_ali                7976  2 
sky@sky-Presario-2100:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 5E:FF:B8:78:BF:68
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 1329468ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C

sky@sky-Presario-2100:~$ lsb-release.d
lsb-release.d: command not found
sky@sky-Presario-2100:~$ lsb_release.d
lsb_release.d: command not found
sky@sky-Presario-2100:~$ isb_release.d
isb_release.d: command not found
sky@sky-Presario-2100:~$ lsb_release -d
Description:    Ubuntu 10.10
sky@sky-Presario-2100:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
   ...done.
sky@sky-Presario-2100:~$ 

[/SIZE][/LEFT]

---

### Post by Sky Aisling on 2010-12-18
Sorta Solved...was able to connect at Library and local coffee shop.  So must have something to do with this private network.

---

