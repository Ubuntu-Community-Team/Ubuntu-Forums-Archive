---
title: "HELP! Updates lead to failure in establishing a wired connection"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by rbaleksandar on 2010-05-21
Hi :)

  One of the (many many) problems that I had with Ubuntu 10.4 was that I wasn't able to connect using a wired. It really came to me as a huge surprise, because that's a problem that I have never encountered. I had dealings with wireless-issues in the past. But **never** a wired connection failed. The thing is that we (in the dormitory where I live) had a network problem recently. A hardware piece got fried and we weren't able to replace it for about 3 weeks (go figure :X ). But in the past 3 days or so we're back online. The thing is - none of my neighbours (all of them are using Windows) has network issues now. Usually it was on the contrary - I was the one who had beautiful connection while they had to deal with a load of d@ng. That said - I made a fresh install of Ubuntu 9.10. The problem got resolved and I was as happy as a chick during her first wedding night with Don Goivanni in her bed. BUT after I updated (note - update and **NOT upgrade**) my system, I was suddenly unable to use the wired connection. The strange thing is that the NM says that I am connected AND I even get some short bursts of network traffic (last for 2-3 seconds) but usually not enough to load even a simple web page. Ping always returns 100% loss no matter how long the package burst lasts. I have slept this night for about 3 hours looking for a solution. None has been found so far. So I come here and ask for any advice/help you guys can offer. I don't have WAPs at home so wired connection is the only way for me to use this modern thing called internet.


Cheers,
rba

---

### Post by shai3421 on 2010-05-21
You should read the following thread:

[http://ubuntuforums.org/showthread.php?t=1309178](http://ubuntuforums.org/showthread.php?t=1309178)

It describes almost the exact same problem you have, and it has several suggestions for resolving it, the first of them is replacing your router (is it D-Link maybe?).

---

### Post by rbaleksandar on 2010-05-21
I don't have access to the router for I am not the admin or a mamber of the network team. Besides it works for so many 
others but not for me. So the problem isn't in the router but in my Ubuntu. Thanks for the reply. Will have a look.

---

### Post by Peter09 on 2010-05-21
Can you post the output of ifconfig.
 
Also have you checked syslog for errors. Note that network manager is not really needed for a hardwired connection.

---

### Post by rbaleksandar on 2010-05-21
Can't post this right now but when I get home I'll use the internet of my neighbour to post the output. Until then - suffering and lots of pain. What I am sure is that the problem comes along with one or more of the latest updates that were also installed in Ubuntu 10.4, when it came out. Kernel maybe?


EDIT:

Here is what ifconfig returns:
```

eth0      Link encap:Ethernet  HWaddr 00:16:d4:f6:83:74  
          inet addr:$$$$$$$  Bcast:$$$$$$$$$$  Mask:255.255.0.0
          inet6 addr: fe80::216:d4ff:fef6:8374/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15445048 (15.4 MB)  TX bytes:1508624 (1.5 MB)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146995 (146.9 KB)  TX bytes:146995 (146.9 KB)

```

Here's what dmesg returns (couldn't find anything suspicious (based on my poor knowledge of networking) in the whole pile of code):
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-21-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) ) #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 (Ubuntu 2.6.31-21.59-generic)
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
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe80000 (usable)
[    0.000000]  BIOS-e820: 000000007fe80000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7fe80 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
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
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fe80000 (usable)
[    0.000000]  modified: 000000007fe80000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  modified: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a5000 - 37fefd3d
[    0.000000] Allocated new RAMDISK: 008b3000 - 00ffdd3d
[    0.000000] Move RAMDISK from 00000000378a5000 - 0000000037fefd3c to 008b3000 - 00ffdd3c
[    0.000000] ACPI: RSDP 000f75e0 00014 (v00 TOSCPL)
[    0.000000] ACPI: RSDT 7fe873e7 00054 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fe8fc78 00074 (v01 TOSCPL CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: DSDT 7fe89194 06AE4 (v01 TOSCPL CALISTGA 06040000 INTL 20060608)
[    0.000000] ACPI: FACS 7fe90fc0 00040
[    0.000000] ACPI: SLIC 7fe8fcec 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
[    0.000000] ACPI: APIC 7fe8fe62 00068 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 7fe8feca 00038 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fe8ff02 0003C (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: BOOT 7fe8ffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 7fe8ff70 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7fe88b41 0064F (v01 SataRe  SataPri 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fe884af 00692 (v01 SataRe  SataSec 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fe879c7 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fe87921 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fe8743b 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ae160]    TEXT DATA BSS ==> [0000100000 - 00008ae160]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008af000 - 00008b20f4]              BRK ==> [00008af000 - 00008b20f4]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008b3000 - 0000ffdd3d]      NEW RAMDISK ==> [00008b3000 - 0000ffdd3d]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7670] f7670
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fe80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fe80
[    0.000000] On node 0 totalpages: 523803
[    0.000000] free_area_init_node: node 0, pgdat c0788d40, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294260 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c200a000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519709
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic root=UUID=31236515-1078-4799-8e2c-c43ea85f3894 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10478080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fe80)
[    0.000000] Memory: 2051432k/2095616k available (4583k kernel code, 42944k reserved, 2142k data, 544k init, 1186312k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc081a000   ( 544 kB)
[    0.000000]       .data : 0xc0579d78 - 0xc0791848   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0579d78   (4583 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1862.074 MHz processor.
[    0.003261] Console: colour VGA+ 80x25
[    0.003265] console [tty0] enabled
[    0.003448] hpet clockevent registered
[    0.003453] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.003460] Calibrating delay loop (skipped), value calculated using timer frequency.. 3724.14 BogoMIPS (lpj=7448296)
[    0.003482] Security Framework initialized
[    0.003506] AppArmor: AppArmor initialized
[    0.003515] Mount-cache hash table entries: 512
[    0.003661] Initializing cgroup subsys ns
[    0.003667] Initializing cgroup subsys cpuacct
[    0.003672] Initializing cgroup subsys memory
[    0.003679] Initializing cgroup subsys devices
[    0.003682] Initializing cgroup subsys freezer
[    0.003685] Initializing cgroup subsys net_cls
[    0.003700] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003703] CPU: L2 cache: 2048K
[    0.003707] CPU: Physical Processor ID: 0
[    0.003709] CPU: Processor Core ID: 0
[    0.003713] mce: CPU supports 6 MCE banks
[    0.003722] CPU0: Thermal monitoring handled by SMI
[    0.003727] using mwait in idle threads.
[    0.003735] Performance Counters: no PMU driver, software counters only.
[    0.003741] Checking 'hlt' instruction... OK.
[    0.019256] ACPI: Core revision 20090521
[    0.032453] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.072624] CPU0: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3723.98 BogoMIPS (lpj=7447965)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring handled by SMI
[    0.160538] CPU1: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[    0.160556] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164024] Brought up 2 CPUs
[    0.164027] Total of 2 processors activated (7448.13 BogoMIPS).
[    0.164085] CPU0 attaching sched-domain:
[    0.164089]  domain 0: span 0-1 level MC
[    0.164092]   groups: 0 1
[    0.164099] CPU1 attaching sched-domain:
[    0.164101]  domain 0: span 0-1 level MC
[    0.164104]   groups: 1 0
[    0.164197] Booting paravirtualized kernel on bare hardware
[    0.164239] regulator: core version 0.5
[    0.164239] Time:  2:47:48  Date: 05/21/10
[    0.164239] NET: Registered protocol family 16
[    0.164248] EISA bus registered
[    0.164259] ACPI: bus type pci registered
[    0.164338] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164342] PCI: MCFG area at e0000000 reserved in E820
[    0.164344] PCI: Using MMCONFIG for extended config space
[    0.164347] PCI: Using configuration type 1 for base access
[    0.165488] bio: create slab <bio-0> at 0
[    0.165488] ACPI: EC: Look up EC in DSDT
[    0.172056] ACPI: BIOS _OSI(Linux) query ignored
[    0.172957] ACPI: Interpreter enabled
[    0.172964] ACPI: (supports S0 S3 S4 S5)
[    0.172987] ACPI: Using IOAPIC for interrupt routing
[    0.180026] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.212094] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.248821] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.248825] ACPI: EC: driver started in poll mode
[    0.249287] ACPI: No dock devices found.
[    0.249847] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.249970] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.249974] pci 0000:00:01.0: PME# disabled
[    0.250071] pci 0000:00:1b.0: reg 10 64bit mmio: [0xde300000-0xde303fff]
[    0.250136] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.250142] pci 0000:00:1b.0: PME# disabled
[    0.250234] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.250239] pci 0000:00:1c.0: PME# disabled
[    0.250334] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.250340] pci 0000:00:1c.1: PME# disabled
[    0.250434] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.250440] pci 0000:00:1c.2: PME# disabled
[    0.250511] pci 0000:00:1d.0: reg 20 io port: [0x1800-0x181f]
[    0.250580] pci 0000:00:1d.1: reg 20 io port: [0x1820-0x183f]
[    0.250648] pci 0000:00:1d.2: reg 20 io port: [0x1840-0x185f]
[    0.250717] pci 0000:00:1d.3: reg 20 io port: [0x1860-0x187f]
[    0.250790] pci 0000:00:1d.7: reg 10 32bit mmio: [0xde304000-0xde3043ff]
[    0.250857] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.250863] pci 0000:00:1d.7: PME# disabled
[    0.251041] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.251046] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.251053] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1670 (mask 000f)
[    0.251130] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.251139] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.251148] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.251157] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.251166] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
[    0.251204] pci 0000:00:1f.2: PME# supported from D3hot
[    0.251209] pci 0000:00:1f.2: PME# disabled
[    0.251275] pci 0000:00:1f.3: reg 20 io port: [0x18c0-0x18df]
[    0.251389] pci 0000:01:00.0: reg 10 32bit mmio: [0xdd000000-0xddffffff]
[    0.251414] pci 0000:01:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.251439] pci 0000:01:00.0: reg 1c 64bit mmio: [0xdc000000-0xdcffffff]
[    0.251465] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.251611] pci 0000:00:01.0: bridge 32bit mmio: [0xdc000000-0xddffffff]
[    0.251617] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.251681] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.251687] pci 0000:00:1c.0: bridge 32bit mmio: [0xd6000000-0xd7ffffff]
[    0.251696] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0000000-0xd1ffffff]
[    0.251792] pci 0000:04:00.0: reg 10 64bit mmio: [0xd8000000-0xd8001fff]
[    0.251914] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.251922] pci 0000:04:00.0: PME# disabled
[    0.252019] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.252025] pci 0000:00:1c.1: bridge 32bit mmio: [0xd8000000-0xd9ffffff]
[    0.252034] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xd2000000-0xd3ffffff]
[    0.252115] pci 0000:05:00.0: reg 10 io port: [0x4000-0x40ff]
[    0.252146] pci 0000:05:00.0: reg 18 64bit mmio: [0xda000000-0xda000fff]
[    0.252177] pci 0000:05:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.252243] pci 0000:05:00.0: supports D1 D2
[    0.252245] pci 0000:05:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.252253] pci 0000:05:00.0: PME# disabled
[    0.252335] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    0.252341] pci 0000:00:1c.2: bridge 32bit mmio: [0xda000000-0xdbffffff]
[    0.252350] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xd4000000-0xd5ffffff]
[    0.252411] pci 0000:06:04.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.252441] pci 0000:06:04.0: supports D1 D2
[    0.252444] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.252450] pci 0000:06:04.0: PME# disabled
[    0.252503] pci 0000:06:04.1: reg 10 32bit mmio: [0xde005000-0xde0057ff]
[    0.252514] pci 0000:06:04.1: reg 14 32bit mmio: [0xde000000-0xde003fff]
[    0.252581] pci 0000:06:04.1: supports D1 D2
[    0.252584] pci 0000:06:04.1: PME# supported from D0 D1 D2 D3hot
[    0.252590] pci 0000:06:04.1: PME# disabled
[    0.252641] pci 0000:06:04.2: reg 10 32bit mmio: [0xde004000-0xde004fff]
[    0.252713] pci 0000:06:04.2: supports D1 D2
[    0.252715] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
[    0.252721] pci 0000:06:04.2: PME# disabled
[    0.252772] pci 0000:06:04.3: reg 10 32bit mmio: [0xde005800-0xde0058ff]
[    0.252845] pci 0000:06:04.3: supports D1 D2
[    0.252848] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
[    0.252854] pci 0000:06:04.3: PME# disabled
[    0.252920] pci 0000:00:1e.0: transparent bridge
[    0.252929] pci 0000:00:1e.0: bridge 32bit mmio: [0xde000000-0xde0fffff]
[    0.252991] pci_bus 0000:00: on NUMA node 0
[    0.252997] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.253200] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.253296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.253382] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.253468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.253574] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.259865] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.259978] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.260102] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.260213] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.260323] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.260435] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.260546] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.260657] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.260850] SCSI subsystem initialized
[    0.260872] libata version 3.00 loaded.
[    0.260872] usbcore: registered new interface driver usbfs
[    0.260872] usbcore: registered new interface driver hub
[    0.260872] usbcore: registered new device driver usb
[    0.260872] ACPI: WMI: Mapper loaded
[    0.260872] PCI: Using ACPI for IRQ routing
[    0.272011] Bluetooth: Core ver 2.15
[    0.272027] NET: Registered protocol family 31
[    0.272027] Bluetooth: HCI device and connection manager initialized
[    0.272027] Bluetooth: HCI socket layer initialized
[    0.272027] NetLabel: Initializing
[    0.272027] NetLabel:  domain hash size = 128
[    0.272027] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.272041] NetLabel:  unlabeled traffic allowed by default
[    0.272075] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.272081] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.288009] pnp: PnP ACPI init
[    0.288023] ACPI: bus type pnp registered
[    0.424068] pnp: PnP ACPI: found 10 devices
[    0.424071] ACPI: ACPI bus type pnp unregistered
[    0.424074] PnPBIOS: Disabled by ACPI PNP
[    0.424088] system 00:01: ioport range 0xfe00-0xfe7f has been reserved
[    0.424091] system 00:01: ioport range 0xfe80-0xfeff has been reserved
[    0.424095] system 00:01: ioport range 0xff00-0xff7f has been reserved
[    0.424099] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.424103] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.424106] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.424110] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.424114] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.424118] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.424121] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.424125] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.424133] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.424140] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.424144] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.424147] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.458838] AppArmor: AppArmor Filesystem Enabled
[    0.458910] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff]
[    0.458914] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.458917] pci 0000:00:01.0:   IO window: disabled
[    0.458922] pci 0000:00:01.0:   MEM window: 0xdc000000-0xddffffff
[    0.458926] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.458932] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.458936] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.458944] pci 0000:00:1c.0:   MEM window: 0xd6000000-0xd7ffffff
[    0.458950] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000d1ffffff
[    0.458959] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.458963] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.458970] pci 0000:00:1c.1:   MEM window: 0xd8000000-0xd9ffffff
[    0.458976] pci 0000:00:1c.1:   PREFETCH window: 0x000000d2000000-0x000000d3ffffff
[    0.458986] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.458990] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.458997] pci 0000:00:1c.2:   MEM window: 0xda000000-0xdbffffff
[    0.459003] pci 0000:00:1c.2:   PREFETCH window: 0x000000d4000000-0x000000d5ffffff
[    0.459018] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
[    0.459021] pci 0000:06:04.0:   IO window: 0x005000-0x0050ff
[    0.459028] pci 0000:06:04.0:   IO window: 0x005400-0x0054ff
[    0.459035] pci 0000:06:04.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.459042] pci 0000:06:04.0:   MEM window: 0x84000000-0x87ffffff
[    0.459047] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.459052] pci 0000:00:1e.0:   IO window: 0x5000-0x5fff
[    0.459059] pci 0000:00:1e.0:   MEM window: 0xde000000-0xde0fffff
[    0.459065] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.459078]   alloc irq_desc for 16 on node -1
[    0.459080]   alloc kstat_irqs on node -1
[    0.459086] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.459091] pci 0000:00:01.0: setting latency timer to 64
[    0.459100]   alloc irq_desc for 17 on node -1
[    0.459102]   alloc kstat_irqs on node -1
[    0.459106] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.459112] pci 0000:00:1c.0: setting latency timer to 64
[    0.459122] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.459128] pci 0000:00:1c.1: setting latency timer to 64
[    0.459139]   alloc irq_desc for 18 on node -1
[    0.459142]   alloc kstat_irqs on node -1
[    0.459146] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.459152] pci 0000:00:1c.2: setting latency timer to 64
[    0.459161] pci 0000:00:1e.0: setting latency timer to 64
[    0.459172] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.459180] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.459183] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.459187] pci_bus 0000:01: resource 1 mem: [0xdc000000-0xddffffff]
[    0.459190] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.459193] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.459196] pci_bus 0000:02: resource 1 mem: [0xd6000000-0xd7ffffff]
[    0.459200] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xd1ffffff]
[    0.459203] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.459206] pci_bus 0000:04: resource 1 mem: [0xd8000000-0xd9ffffff]
[    0.459209] pci_bus 0000:04: resource 2 pref mem [0xd2000000-0xd3ffffff]
[    0.459213] pci_bus 0000:05: resource 0 io:  [0x4000-0x4fff]
[    0.459216] pci_bus 0000:05: resource 1 mem: [0xda000000-0xdbffffff]
[    0.459219] pci_bus 0000:05: resource 2 pref mem [0xd4000000-0xd5ffffff]
[    0.459222] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.459225] pci_bus 0000:06: resource 1 mem: [0xde000000-0xde0fffff]
[    0.459229] pci_bus 0000:06: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.459232] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.459235] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.459238] pci_bus 0000:07: resource 0 io:  [0x5000-0x50ff]
[    0.459241] pci_bus 0000:07: resource 1 io:  [0x5400-0x54ff]
[    0.459244] pci_bus 0000:07: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.459248] pci_bus 0000:07: resource 3 mem: [0x84000000-0x87ffffff]
[    0.459286] NET: Registered protocol family 2
[    0.459388] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.459733] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.460424] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.460762] TCP: Hash tables configured (established 131072 bind 65536)
[    0.460765] TCP reno registered
[    0.460872] NET: Registered protocol family 1
[    0.460942] Trying to unpack rootfs image as initramfs...
[    0.500580] Switched to high resolution mode on CPU 1
[    0.503993] Switched to high resolution mode on CPU 0
[    0.683163] Freeing initrd memory: 7467k freed
[    0.688414] Simple Boot Flag at 0x36 set to 0x1
[    0.688625] cpufreq-nforce2: No nForce2 chipset.
[    0.688657] Scanning for low memory corruption every 60 seconds
[    0.688777] audit: initializing netlink socket (disabled)
[    0.688796] type=2000 audit(1274410068.688:1): initialized
[    0.698258] highmem bounce pool size: 64 pages
[    0.698265] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.700038] VFS: Disk quotas dquot_6.5.2
[    0.700108] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.700769] fuse init (API version 7.12)
[    0.700861] msgmni has been set to 1705
[    0.701120] alg: No test for stdrng (krng)
[    0.701136] io scheduler noop registered
[    0.701139] io scheduler anticipatory registered
[    0.701141] io scheduler deadline registered
[    0.701191] io scheduler cfq registered (default)
[    0.701332] pci 0000:01:00.0: Boot video device
[    0.701471]   alloc irq_desc for 24 on node -1
[    0.701474]   alloc kstat_irqs on node -1
[    0.701485] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.701493] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.701621]   alloc irq_desc for 25 on node -1
[    0.701624]   alloc kstat_irqs on node -1
[    0.701633] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.701645] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.701811]   alloc irq_desc for 26 on node -1
[    0.701813]   alloc kstat_irqs on node -1
[    0.701822] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.701834] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.702001]   alloc irq_desc for 27 on node -1
[    0.702004]   alloc kstat_irqs on node -1
[    0.702013] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.702024] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.702138] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.702259] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.702438] ACPI: AC Adapter [ACAD] (off-line)
[    0.702516] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.702520] ACPI: Power Button [PWRF]
[    0.702578] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.702618] ACPI: Lid Switch [LID0]
[    0.702672] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.702675] ACPI: Power Button [PWRB]
[    0.704787] ACPI: SSDT 7fe8816d 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.706134] ACPI: SSDT 7fe87c26 004C2 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.711859] Marking TSC unstable due to TSC halts in idle
[    0.711919] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.711985] processor LNXCPU:00: registered as cooling_device0
[    0.712007] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.713034] ACPI: SSDT 7fe883e7 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.713932] ACPI: SSDT 7fe880e8 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.715653] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.715717] processor LNXCPU:01: registered as cooling_device1
[    0.715739] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.796664] isapnp: Scanning for PnP cards...
[    1.163418] isapnp: No Plug & Play device found
[    1.320184] ACPI: Battery Slot [BAT1] (battery present)
[    1.320507] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.323975] brd: module loaded
[    1.325196] loop: module loaded
[    1.325383] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.325669] ata_piix 0000:00:1f.2: version 2.13
[    1.325706]   alloc irq_desc for 19 on node -1
[    1.325728]   alloc kstat_irqs on node -1
[    1.325735] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.325759] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.480070] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.480296] scsi0 : ata_piix
[    1.480522] scsi1 : ata_piix
[    1.483073] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    1.483076] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    1.485438] Fixed MDIO Bus: probed
[    1.485555] PPP generic driver version 2.4.2
[    1.485779] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.485821]   alloc irq_desc for 23 on node -1
[    1.485842]   alloc kstat_irqs on node -1
[    1.485847] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.485878] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.485882] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.485974] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.485980] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.489949] ehci_hcd 0000:00:1d.7: debug port 1
[    1.489957] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.489989] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xde304000
[    1.505036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.505230] usb usb1: configuration #1 chosen from 1 choice
[    1.505302] hub 1-0:1.0: USB hub found
[    1.505332] hub 1-0:1.0: 8 ports detected
[    1.505516] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.505552] uhci_hcd: USB Universal Host Controller Interface driver
[    1.505616] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.505640] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.505644] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.505711] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.505775] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    1.505970] usb usb2: configuration #1 chosen from 1 choice
[    1.506034] hub 2-0:1.0: USB hub found
[    1.506060] hub 2-0:1.0: 2 ports detected
[    1.506162] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.506188] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.506192] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.506258] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.506345] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    1.506539] usb usb3: configuration #1 chosen from 1 choice
[    1.506603] hub 3-0:1.0: USB hub found
[    1.506628] hub 3-0:1.0: 2 ports detected
[    1.506731] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.506756] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.506760] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.506831] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.506918] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    1.507113] usb usb4: configuration #1 chosen from 1 choice
[    1.507178] hub 4-0:1.0: USB hub found
[    1.507203] hub 4-0:1.0: 2 ports detected
[    1.507305] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.507330] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.507334] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.507424] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.507491] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    1.507686] usb usb5: configuration #1 chosen from 1 choice
[    1.507751] hub 5-0:1.0: USB hub found
[    1.507776] hub 5-0:1.0: 2 ports detected
[    1.508029] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.508483] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.508674] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.508681] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.508685] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.508707] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.508711] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.508839] mice: PS/2 mouse device common for all mice
[    1.509158] rtc_cmos 00:07: RTC can wake from S4
[    1.509230] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.509319] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.509580] device-mapper: uevent: version 1.0.3
[    1.509837] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.510119] device-mapper: multipath: version 1.1.0 loaded
[    1.510122] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.510446] EISA: Probing bus 0 at eisa.0
[    1.510471] Cannot allocate resource for EISA slot 1
[    1.510474] Cannot allocate resource for EISA slot 2
[    1.510477] Cannot allocate resource for EISA slot 3
[    1.510497] Cannot allocate resource for EISA slot 4
[    1.510500] Cannot allocate resource for EISA slot 5
[    1.510532] EISA: Detected 0 cards.
[    1.511045] cpuidle: using governor ladder
[    1.511361] cpuidle: using governor menu
[    1.512335] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.512641] TCP cubic registered
[    1.513165] NET: Registered protocol family 10
[    1.514310] lo: Disabled Privacy Extensions
[    1.515141] NET: Registered protocol family 17
[    1.515196] Bluetooth: L2CAP ver 2.13
[    1.515198] Bluetooth: L2CAP socket layer initialized
[    1.515201] Bluetooth: SCO (Voice Link) ver 0.6
[    1.515203] Bluetooth: SCO socket layer initialized
[    1.515337] Bluetooth: RFCOMM TTY layer initialized
[    1.515340] Bluetooth: RFCOMM socket layer initialized
[    1.515361] Bluetooth: RFCOMM ver 1.11
[    1.516260] Using IPI No-Shortcut mode
[    1.516416] PM: Resume from disk failed.
[    1.516449] registered taskstats version 1
[    1.516776]   Magic number: 10:17:764
[    1.516780] atkbd serio2: hash matches
[    1.517108] rtc_cmos 00:07: setting system clock to 2010-05-21 02:47:50 UTC (1274410070)
[    1.517131] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.517133] EDD information not available.
[    1.645031] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WT03, max UDMA/33
[    1.657133] ata1.00: ATA-7: TOSHIBA MK1237GSX, DL130M, max UDMA/100
[    1.657136] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.661091] ata2.00: configured for UDMA/33
[    1.669373] ata1.00: configured for UDMA/100
[    1.669916] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1237GS DL13 PQ: 0 ANSI: 5
[    1.670225] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.670325] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.670704] sd 0:0:0:0: [sda] Write Protect is off
[    1.670707] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.670771] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.671115]  sda:
[    1.674148] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WT03 PQ: 0 ANSI: 5
[    1.686753] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.686761] Uniform CD-ROM driver Revision: 3.20
[    1.687114] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.687214] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.698314]  sda1 sda2 < sda5 sda6 sda7 >
[    1.733959] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.734092] Freeing unused kernel memory: 544k freed
[    1.735084] Write protecting the kernel text: 4584k
[    1.735240] Write protecting the kernel read-only data: 1840k
[    1.825051] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.896483] hub 1-0:1.0: unable to enumerate USB device on port 6
[    2.001078] Clocksource tsc unstable (delta = -85537789 ns)
[    2.047068] Linux agpgart interface v0.103
[    2.124733] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.124798] r8169 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.124924] r8169 0000:05:00.0: setting latency timer to 64
[    2.146498]   alloc irq_desc for 28 on node -1
[    2.146503]   alloc kstat_irqs on node -1
[    2.146564] r8169 0000:05:00.0: irq 28 for MSI/MSI-X
[    2.148217] eth0: RTL8101e at 0xf80e6000, 00:16:d4:f6:83:74, XID 34000000 IRQ 28
[    2.270833] ohci1394 0000:06:04.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.328288] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[de005000-de0057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.425226] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    2.572159] usb 4-2: not running at top speed; connect to a high speed hub
[    2.585427] acpi device:04: registered as cooling_device2
[    2.585963] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input5
[    2.586068] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.627438] usb 4-2: configuration #1 chosen from 1 choice
[    3.601497] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f74bb4012b3]
[    3.996857] PM: Starting manual resume from disk
[    3.996862] PM: Resume from partition 8:5
[    3.996865] PM: Checking hibernation image.
[    3.997191] PM: Resume from disk failed.
[    4.038989] EXT4-fs (sda1): barriers enabled
[    4.055688] kjournald2 starting: pid 372, dev sda1:8, commit interval 5 seconds
[    4.056031] EXT4-fs (sda1): delayed allocation enabled
[    4.056036] EXT4-fs: file extents enabled
[    4.066547] EXT4-fs: mballoc enabled
[    4.066601] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.838308] type=1505 audit(1274410073.819:2): operation="profile_load" pid=397 name=/usr/share/gdm/guest-session/Xsession
[    4.855325] type=1505 audit(1274410073.835:3): operation="profile_load" pid=398 name=/sbin/dhclient3
[    4.856969] type=1505 audit(1274410073.838:4): operation="profile_load" pid=398 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.857832] type=1505 audit(1274410073.838:5): operation="profile_load" pid=398 name=/usr/lib/connman/scripts/dhclient-script
[    4.927763] type=1505 audit(1274410073.907:6): operation="profile_load" pid=399 name=/usr/bin/evince
[    4.953679] type=1505 audit(1274410073.934:7): operation="profile_load" pid=399 name=/usr/bin/evince-previewer
[    4.968870] type=1505 audit(1274410073.950:8): operation="profile_load" pid=399 name=/usr/bin/evince-thumbnailer
[    5.006740] type=1505 audit(1274410073.987:9): operation="profile_load" pid=401 name=/usr/lib/cups/backend/cups-pdf
[    6.203752] Adding 4000144k swap on /dev/sda5.  Priority:-1 extents:1 across:4000144k 
[    6.704902] EXT4-fs (sda1): internal journal on sda1:8
[    7.064723] udev: starting version 147
[    7.382664] EXT4-fs (sda6): barriers enabled
[    7.433254] kjournald2 starting: pid 483, dev sda6:8, commit interval 5 seconds
[    7.565992] EXT4-fs (sda6): internal journal on sda6:8
[    7.565999] EXT4-fs (sda6): delayed allocation enabled
[    7.566021] EXT4-fs: file extents enabled
[    7.568169] EXT4-fs: mballoc enabled
[    7.568226] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    8.451638] Linux video capture interface: v2.00
[    8.484690] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[    8.490460] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input6
[    8.490585] usbcore: registered new interface driver uvcvideo
[    8.490589] USB Video Class driver (v0.1.0)
[    9.186648] lp: driver loaded but no devices found
[    9.188247] cfg80211: Calling CRDA to update world regulatory domain
[    9.335323] intel_rng: FWH not detected
[    9.431239] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x82e0b1, caps: 0xb04711/0xe0440d
[    9.431292] synaptics: Toshiba Satellite A200 detected, limiting rate to 40pps.
[    9.469984] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[    9.485934] sdhci: Secure Digital Host Controller Interface driver
[    9.485938] sdhci: Copyright(c) Pierre Ossman
[    9.533406] sdhci-pci 0000:06:04.3: SDHCI controller found [104c:803c] (rev 0)
[    9.533448] sdhci-pci 0000:06:04.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    9.533631] Registered led device: mmc0::
[    9.533729] mmc0: SDHCI controller on PCI [0000:06:04.3] using DMA
[    9.815393] tifm_7xx1 0000:06:04.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    9.820481] yenta_cardbus 0000:06:04.0: CardBus bridge found [1179:ff00]
[    9.820522] yenta_cardbus 0000:06:04.0: Enabling burst memory read transactions
[    9.820547] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
[    9.820550] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
[    9.820557] yenta_cardbus 0000:06:04.0: TI: mfunc 0x10aa1b22, devctl 0x64
[    9.941332] EXT4-fs (sda7): barriers enabled
[    9.954315] kjournald2 starting: pid 693, dev sda7:8, commit interval 5 seconds
[    9.955163] EXT4-fs (sda7): internal journal on sda7:8
[    9.955168] EXT4-fs (sda7): delayed allocation enabled
[    9.955172] EXT4-fs: file extents enabled
[    9.965461] EXT4-fs: mballoc enabled
[    9.965496] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   10.053238] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   10.053263] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[   10.053267] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #06 to #0a
[   10.053296] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   10.053300] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.
[   10.053870] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xde000000 - 0xde0fffff
[   10.053874] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   10.187099] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   10.187103] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   10.187319] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.187328] iwlagn 0000:04:00.0: setting latency timer to 64
[   10.187392] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   10.242470] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   10.242630]   alloc irq_desc for 29 on node -1
[   10.242633]   alloc kstat_irqs on node -1
[   10.242692] iwlagn 0000:04:00.0: irq 29 for MSI/MSI-X
[   10.298403] cfg80211: World regulatory domain updated:
[   10.298425] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.298429] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.298432] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.298453] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.298456] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.298460] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.349155] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.965980] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.481072] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.485624] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   11.487521] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.489148] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.491154] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.999623]   alloc irq_desc for 22 on node -1
[   11.999627]   alloc kstat_irqs on node -1
[   11.999654] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.999754] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.107151] hda_codec: Unknown model for ALC861-VD, trying auto-probe from BIOS...
[   12.107375] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   12.272100] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   12.452683] usb 2-2: configuration #1 chosen from 1 choice
[   12.498808] usbcore: registered new interface driver hiddev
[   12.512996] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input9
[   12.513277] generic-usb 0003:046D:C050.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2/input0
[   12.513336] usbcore: registered new interface driver usbhid
[   12.513339] usbhid: v2.6:USB HID core driver
[   13.982418] __ratelimit: 6 callbacks suppressed
[   13.982422] type=1505 audit(1274410082.962:12): operation="profile_replace" pid=940 name=/usr/share/gdm/guest-session/Xsession
[   13.990450] type=1505 audit(1274410082.970:13): operation="profile_replace" pid=941 name=/sbin/dhclient3
[   13.992044] type=1505 audit(1274410082.974:14): operation="profile_replace" pid=941 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.992929] type=1505 audit(1274410082.974:15): operation="profile_replace" pid=941 name=/usr/lib/connman/scripts/dhclient-script
[   14.005614] type=1505 audit(1274410082.986:16): operation="profile_replace" pid=942 name=/usr/bin/evince
[   14.034928] type=1505 audit(1274410083.014:17): operation="profile_replace" pid=942 name=/usr/bin/evince-previewer
[   14.059653] type=1505 audit(1274410083.038:18): operation="profile_replace" pid=942 name=/usr/bin/evince-thumbnailer
[   14.087520] type=1505 audit(1274410083.066:19): operation="profile_replace" pid=944 name=/usr/lib/cups/backend/cups-pdf
[   14.089513] type=1505 audit(1274410083.070:20): operation="profile_replace" pid=944 name=/usr/sbin/cupsd
[   14.106033] type=1505 audit(1274410083.086:21): operation="profile_replace" pid=946 name=/usr/sbin/tcpdump
[   15.086306] r8169: eth0: link down
[   15.086823] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.325898] ppdev: user-space parallel port driver
[   70.680243] usb 1-3: new high speed USB device using ehci_hcd and address 4
[   70.960639] usb 1-3: configuration #1 chosen from 1 choice
[   71.058654] Initializing USB Mass Storage driver...
[   71.080535] input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.1/input/input10
[   71.080730] generic-usb 0003:1058:1103.0002: input,hidraw1: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-3/input1
[   71.081083] scsi2 : SCSI emulation for USB Mass Storage devices
[   71.081332] usbcore: registered new interface driver usb-storage
[   71.081336] USB Mass Storage support registered.
[   71.083095] usb-storage: device found at 4
[   71.083098] usb-storage: waiting for device to settle before scanning
[   76.089575] usb-storage: device scan complete
[   76.107778] scsi 2:0:0:0: Direct-Access     WD       My Book          1028 PQ: 0 ANSI: 4
[   76.108895] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   76.130496] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   76.143738] sd 2:0:0:0: [sdb] Write Protect is off
[   76.143747] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[   76.143772] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   76.179498] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   76.179526]  sdb: sdb1 < sdb5 sdb6 sdb7 sdb8 sdb9 sdb10 sdb11 >
[   76.306989] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   76.307001] sd 2:0:0:0: [sdb] Attached SCSI disk
[  130.917697] EXT4-fs (sdb11): barriers enabled
[  130.944127] kjournald2 starting: pid 1835, dev sdb11:8, commit interval 5 seconds
[  131.298245] EXT4-fs (sdb11): internal journal on sdb11:8
[  131.298277] EXT4-fs (sdb11): delayed allocation enabled
[  131.298342] EXT4-fs: file extents enabled
[  131.313611] EXT4-fs: mballoc enabled
[  131.313679] EXT4-fs (sdb11): recovery complete
[  131.313688] EXT4-fs (sdb11): mounted filesystem with ordered data mode
[  238.976200] CE: hpet increasing min_delta_ns to 15000 nsec
[  468.734356] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  468.735351] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  468.736477] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  468.737602] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  468.738679] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  468.738700] psmouse.c: issuing reconnect request
[  470.436092] CE: hpet increasing min_delta_ns to 22500 nsec
[  470.436195] CE: hpet increasing min_delta_ns to 33750 nsec
[  470.436296] CE: hpet increasing min_delta_ns to 50624 nsec
[  470.436399] CE: hpet increasing min_delta_ns to 75936 nsec
[ 1850.257863] r8169: eth0: link up
[ 1850.261753] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1860.284016] eth0: no IPv6 routers present
[ 2463.801612] /dev/vmmon[4987]: Module vmmon: registered with major=10 minor=165
[ 2463.801621] /dev/vmmon[4987]: Module vmmon: initialized
[ 2463.884052] /dev/vmci[4995]: VMCI: Driver initialized.
[ 2463.884221] /dev/vmci[4995]: Module vmci: registered with major=10 minor=55
[ 2463.884242] /dev/vmci[4995]: Module vmci: initialized
[ 2465.306296] /dev/vmnet: open called by PID 5045 (vmnet-bridge)
[ 2465.306327] /dev/vmnet: hub 0 does not exist, allocating memory.
[ 2465.306392] /dev/vmnet: port on hub 0 successfully opened
[ 2465.306428] bridge-eth0: up
[ 2465.306434] bridge-eth0: attached
[ 2466.508727] /dev/vmnet: open called by PID 5052 (vmnet-dhcpd)
[ 2466.508761] /dev/vmnet: hub 8 does not exist, allocating memory.
[ 2466.508826] /dev/vmnet: port on hub 8 successfully opened
[ 2466.537120] /dev/vmnet: open called by PID 5056 (vmnet-natd)
[ 2466.537158] /dev/vmnet: port on hub 8 successfully opened
[ 2466.571411] /dev/vmnet: open called by PID 5057 (vmnet-netifup)
[ 2466.571467] /dev/vmnet: port on hub 8 successfully opened
[ 2467.177353] /dev/vmnet: open called by PID 5061 (vmnet-dhcpd)
[ 2467.177388] /dev/vmnet: hub 1 does not exist, allocating memory.
[ 2467.177454] /dev/vmnet: port on hub 1 successfully opened
[ 2467.186479] /dev/vmnet: open called by PID 5063 (vmnet-netifup)
[ 2467.186535] /dev/vmnet: port on hub 1 successfully opened
[ 2467.672145] bridge-eth0: disabling the bridge
[ 2467.688122] bridge-eth0: down
[ 2467.688148] bridge-eth0: detached
[ 2527.651808] /dev/vmci[5127]: Module vmci: unloaded
[ 2527.717477] /dev/vmmon[5136]: Module vmmon: unloaded
[ 2528.248272] /dev/vmmon[5178]: Module vmmon: registered with major=10 minor=165
[ 2528.248301] /dev/vmmon[5178]: Module vmmon: initialized
[ 2528.296360] /dev/vmci[5186]: VMCI: Driver initialized.
[ 2528.296579] /dev/vmci[5186]: Module vmci: registered with major=10 minor=55
[ 2528.296583] /dev/vmci[5186]: Module vmci: initialized
[ 2529.779758] /dev/vmnet: open called by PID 5235 (vmnet-bridge)
[ 2529.779789] /dev/vmnet: hub 0 does not exist, allocating memory.
[ 2529.779855] /dev/vmnet: port on hub 0 successfully opened
[ 2529.779892] bridge-eth0: up
[ 2529.779897] bridge-eth0: attached
[ 2530.949296] /dev/vmnet: open called by PID 5242 (vmnet-dhcpd)
[ 2530.949330] /dev/vmnet: hub 8 does not exist, allocating memory.
[ 2530.949414] /dev/vmnet: port on hub 8 successfully opened
[ 2530.965588] /dev/vmnet: open called by PID 5246 (vmnet-natd)
[ 2530.965623] /dev/vmnet: port on hub 8 successfully opened
[ 2530.991410] /dev/vmnet: open called by PID 5247 (vmnet-netifup)
[ 2530.991443] /dev/vmnet: port on hub 8 successfully opened
[ 2531.604660] /dev/vmnet: open called by PID 5249 (vmnet-dhcpd)
[ 2531.604714] /dev/vmnet: hub 1 does not exist, allocating memory.
[ 2531.604780] /dev/vmnet: port on hub 1 successfully opened
[ 2531.617397] /dev/vmnet: open called by PID 5251 (vmnet-netifup)
[ 2531.617456] /dev/vmnet: port on hub 1 successfully opened
[ 2541.125168] vmnet8: no IPv6 routers present
[ 2542.429171] vmnet1: no IPv6 routers present
[ 2697.931890] cheese[5265]: segfault at 0 ip 08057f94 sp bf8fa100 error 4 in cheese[8048000+25000]
[ 3394.996010] bridge-eth0: disabling the bridge on dev down
[ 3395.005307] bridge-eth0: down
[ 3395.008632] bridge-eth0: detached
[ 3396.197886] r8169: eth0: link up
[ 3396.199930] /dev/vmnet: open called by PID 5235 (vmnet-bridge)
[ 3396.199964] /dev/vmnet: hub 0 does not exist, allocating memory.
[ 3396.200066] /dev/vmnet: port on hub 0 successfully opened
[ 3396.200122] bridge-eth0: up
[ 3396.200128] bridge-eth0: attached
[ 3406.333224] eth0: no IPv6 routers present
[ 4944.616020] usb 1-3: USB disconnect, address 4
[ 4944.664355] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[ 4944.664380] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[ 4944.664383] EXT4-fs: mballoc: 0 generated and it took 0
[ 4944.664385] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[19800.408247] usb 1-1: new high speed USB device using ehci_hcd and address 5
[19800.543836] usb 1-1: configuration #1 chosen from 1 choice
[19808.213917] usb 1-1: USB disconnect, address 5
[19876.976079] bridge-eth0: disabling the bridge on dev down
[19876.985270] bridge-eth0: down
[19876.991206] bridge-eth0: detached
[19878.920884] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[19878.920889] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[19878.920914] PM: Basic memory bitmaps created
[19878.920916] PM: Syncing filesystems ... done.
[19878.985063] Freezing user space processes ... (elapsed 0.00 seconds) done.
[19878.987589] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[19878.987871] PM: Shrinking memory...  -\|/-\|/-\|/-\|done (135516 pages freed)
[19886.732731] PM: Freed 542064 kbytes in 7.74 seconds (70.03 MB/s)
[19886.732752] Suspending console(s) (use no_console_suspend to debug)
[19886.964214] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[19886.964840] ACPI handle has no context!
[19886.965023] ACPI handle has no context!
[19886.965030] sdhci-pci 0000:06:04.3: PME# disabled
[19886.965058] sdhci-pci 0000:06:04.3: PCI INT C disabled
[19886.965065] ACPI handle has no context!
[19886.980346] ACPI handle has no context!
[19886.980376] tifm_7xx1 0000:06:04.2: PME# disabled
[19886.980386] tifm_7xx1 0000:06:04.2: PCI INT C disabled
[19886.980416] ACPI handle has no context!
[19886.996418] ACPI handle has no context!
[19887.028601] ata_piix 0000:00:1f.2: PCI INT B disabled
[19887.028692] HDA Intel 0000:00:1b.0: PCI INT A disabled
[19887.046417] ACPI: Preparing to enter system sleep state S4
[19887.062734] PM: Saving platform NVS memory
[19887.102804] Disabling non-boot CPUs ...
[19887.105413] CPU 1 is now offline
[19887.105416] SMP alternatives: switching to UP code
[19887.118524] CPU0 attaching NULL sched-domain.
[19887.118528] CPU1 attaching NULL sched-domain.
[19887.118536] CPU0 attaching NULL sched-domain.
[19887.119105] CPU1 is down
[19887.119427] PM: Creating hibernation image: 
[19887.120013] PM: Need to copy 125771 pages
[19887.120013] PM: Normal pages needed: 80689 + 1024 + 42, available pages: 146534
[19887.120013] PM: Restoring platform NVS memory
[19887.120013] CPU0: Thermal monitoring handled by SMI
[19887.120013] Enabling non-boot CPUs ...
[19887.120013] SMP alternatives: switching to SMP code
[19887.124459] Booting processor 1 APIC 0x1 ip 0x6000
[19887.117889] Initializing CPU#1
[19887.117889] Calibrating delay using timer specific routine.. 3724.10 BogoMIPS (lpj=7448205)
[19887.117889] CPU: L1 I cache: 32K, L1 D cache: 32K
[19887.117889] CPU: L2 cache: 2048K
[19887.117889] CPU: Physical Processor ID: 0
[19887.117889] CPU: Processor Core ID: 1
[19887.117889] mce: CPU supports 6 MCE banks
[19887.117889] CPU1: Thermal monitoring handled by SMI
[19887.212505] CPU1: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[19887.212613] CPU0 attaching NULL sched-domain.
[19887.213020] Switched to high resolution mode on CPU 1
[19887.228024] CPU0 attaching sched-domain:
[19887.228028]  domain 0: span 0-1 level MC
[19887.228030]   groups: 0 1
[19887.228035] CPU1 attaching sched-domain:
[19887.228037]  domain 0: span 0-1 level MC
[19887.228040]   groups: 1 0
[19887.229020] CPU1 is up
[19887.229187] ACPI: Waking up from system sleep state S4
[19887.412304] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[19887.412683] ehci_hcd 0000:00:1d.7: PME# disabled
[19887.412707] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x38060600, writing 0x380a0600)
[19887.412805] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80001, writing 0x2b80005)
[19887.413246] yenta_cardbus 0000:06:04.0: restoring config space at offset 0xf (was 0x34001ff, writing 0x5c001ff)
[19887.413274] yenta_cardbus 0000:06:04.0: restoring config space at offset 0x3 (was 0x824000, writing 0x82a808)
[19887.428035] ohci1394 0000:06:04.1: restoring config space at offset 0xf (was 0x4020200, writing 0x402020a)
[19887.428063] ohci1394 0000:06:04.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[19887.428072] ohci1394 0000:06:04.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100016)
[19888.004282] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[19888.004295] HDA Intel 0000:00:1b.0: setting latency timer to 64
[19888.004345] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[19888.004395] usb usb2: root hub lost power or was reset
[19888.004441] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[19888.004498] usb usb3: root hub lost power or was reset
[19888.004518] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[19888.004560] usb usb4: root hub lost power or was reset
[19888.004580] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[19888.004619] usb usb5: root hub lost power or was reset
[19888.004640] ehci_hcd 0000:00:1d.7: PME# disabled
[19888.004645] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[19888.004651] usb usb1: root hub lost power or was reset
[19888.008534] ehci_hcd 0000:00:1d.7: debug port 1
[19888.008541] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[19888.008552] pci 0000:00:1e.0: setting latency timer to 64
[19888.008562] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[19888.008568] ata_piix 0000:00:1f.2: setting latency timer to 64
[19888.010440] pci 0000:01:00.0: PME# disabled
[19888.010451] r8169 0000:05:00.0: wake-up capability disabled by ACPI
[19888.010482] r8169 0000:05:00.0: PME# disabled
[19888.040112] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445469661112320430 new 18445469655801320512 attempts 1
[19888.172812] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[19888.172816] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[19888.172892] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[19888.172895] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[19888.188735] ata2.00: configured for UDMA/33
[19888.189119] ata1.00: configured for UDMA/100
[19888.204154] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[de005000-de0057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[19888.204337] tifm_7xx1 0000:06:04.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[19888.204363] sdhci-pci 0000:06:04.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[19889.056327] sd 0:0:0:0: [sda] Starting disk
[19889.348075] usb 2-2: reset low speed USB device using uhci_hcd and address 2
[19889.655576] PM: Image restored successfully.
[19889.715421] Restarting tasks ... done.
[19889.717754] PM: Basic memory bitmaps freed
[19889.824077] usb 1-6: new high speed USB device using ehci_hcd and address 6
[19889.970567] usb 1-6: configuration #1 chosen from 1 choice
[19889.972569] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[19889.976097] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input11
[19889.976322] usb 4-2: USB disconnect, address 2
[19897.853060] r8169: eth0: link down
[19897.853366] /dev/vmnet: open called by PID 5235 (vmnet-bridge)
[19897.853386] /dev/vmnet: hub 0 does not exist, allocating memory.
[19897.853449] /dev/vmnet: port on hub 0 successfully opened
[19897.853477] bridge-eth0: up
[19897.853549] ADDRCONF(NETDEV_UP): eth0: link is not ready
[19897.853567] bridge-eth0: attached
[19897.868618] bridge-eth0: disabling the bridge
[19897.884131] bridge-eth0: down
[19897.884148] bridge-eth0: detached
[19910.559203] usb 1-6: USB disconnect, address 6
[19910.824208] usb 1-6: new high speed USB device using ehci_hcd and address 7
[19910.892490] hub 1-0:1.0: unable to enumerate USB device on port 6
[19911.080394] hub 1-0:1.0: unable to enumerate USB device on port 6
[19911.324141] usb 1-6: new high speed USB device using ehci_hcd and address 9
[19911.392487] hub 1-0:1.0: unable to enumerate USB device on port 6
[19911.660165] usb 4-2: new full speed USB device using uhci_hcd and address 3
[19911.807431] usb 4-2: not running at top speed; connect to a high speed hub
[19911.861658] usb 4-2: configuration #1 chosen from 1 choice
[19911.871871] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[19911.880652] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input12
[20936.813381] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-4965-2.ucode
[20936.918436] iwlagn 0000:04:00.0: loaded firmware version 228.61.2.24
[20937.166720] Registered led device: iwl-phy0::radio
[20937.166846] Registered led device: iwl-phy0::assoc
[20937.166948] Registered led device: iwl-phy0::RX
[20937.167048] Registered led device: iwl-phy0::TX
[20937.226051] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20937.226789] /dev/vmnet: open called by PID 5235 (vmnet-bridge)
[20937.226822] /dev/vmnet: hub 0 does not exist, allocating memory.
[20937.226886] /dev/vmnet: port on hub 0 successfully opened
[20937.226915] bridge-wlan0: is a Wireless Adapter
[20937.226940] bridge-wlan0: up
[20937.237381] bridge-wlan0: attached
[20937.237609] bridge-wlan0: disabling the bridge
[20937.248199] bridge-wlan0: down
[20937.248230] bridge-wlan0: detached
[20937.912243] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[20938.164455] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[20938.164493] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[20938.164525] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[20938.164706] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[20938.165041] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[20938.165423] cfg80211: Found new beacon on frequency: 5200 MHz (Ch 40) on phy0
[20938.182886] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[20947.349577] wlan0: authenticate with AP 00:0b:0e:14:75:45
[20947.350353] wlan0: authenticated
[20947.350356] wlan0: associate with AP 00:0b:0e:14:75:45
[20947.362562] wlan0: RX AssocResp from 00:0b:0e:14:75:45 (capab=0x401 status=0 aid=1)
[20947.362566] wlan0: associated
[20947.384053] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[20947.384178] cfg80211: Calling CRDA for country: DE
[20947.399377] /dev/vmnet: open called by PID 5235 (vmnet-bridge)
[20947.399410] /dev/vmnet: hub 0 does not exist, allocating memory.
[20947.399473] /dev/vmnet: port on hub 0 successfully opened
[20947.399504] bridge-wlan0: is a Wireless Adapter
[20947.399508] bridge-wlan0: up
[20947.399531] bridge-wlan0: attached
[20947.479215] cfg80211: Received country IE:
[20947.479221] cfg80211: Regulatory domain: DE
[20947.479223] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[20947.479245] 	(5170000 KHz - 5330000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[20947.479248] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[20947.479251] cfg80211: CRDA thinks this should applied:
[20947.479253] cfg80211: Regulatory domain: DE
[20947.479255] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[20947.479258] 	(2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[20947.479279] 	(5150000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[20947.479282] 	(5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[20947.479284] cfg80211: We intersect both of these and get:
[20947.479286] cfg80211: Regulatory domain: 98
[20947.479288] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[20947.479309] 	(5170000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[20947.479312] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[20947.479318] cfg80211: Leaving channel 2412 MHz intact on phy0 - no rule found in band on Country IE
[20947.479321] cfg80211: Leaving channel 2417 MHz intact on phy0 - no rule found in band on Country IE
[20947.479342] cfg80211: Leaving channel 2422 MHz intact on phy0 - no rule found in band on Country IE
[20947.479345] cfg80211: Leaving channel 2427 MHz intact on phy0 - no rule found in band on Country IE
[20947.479348] cfg80211: Leaving channel 2432 MHz intact on phy0 - no rule found in band on Country IE
[20947.479351] cfg80211: Leaving channel 2437 MHz intact on phy0 - no rule found in band on Country IE
[20947.479372] cfg80211: Leaving channel 2442 MHz intact on phy0 - no rule found in band on Country IE
[20947.479375] cfg80211: Leaving channel 2447 MHz intact on phy0 - no rule found in band on Country IE
[20947.479378] cfg80211: Leaving channel 2452 MHz intact on phy0 - no rule found in band on Country IE
[20947.479381] cfg80211: Leaving channel 2457 MHz intact on phy0 - no rule found in band on Country IE
[20947.479384] cfg80211: Leaving channel 2462 MHz intact on phy0 - no rule found in band on Country IE
[20947.479405] cfg80211: Leaving channel 2467 MHz intact on phy0 - no rule found in band on Country IE
[20947.479408] cfg80211: Leaving channel 2472 MHz intact on phy0 - no rule found in band on Country IE
[20947.479416] cfg80211: Current regulatory domain updated by AP to: DE
[20947.479436] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[20947.479439] 	(5170000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[20947.479442] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[20952.087498] wlan0: disassociating by local choice (reason=3)
[20952.102375] bridge-wlan0: disabling the bridge
[20952.116068] bridge-wlan0: down
[20952.116103] bridge-wlan0: detached
[20952.121663] wlan0: authenticate with AP 00:0b:0e:25:0e:c4
[20957.396058] wlan0: no IPv6 routers present
[20958.774375] wlan0: authenticate with AP 00:0b:0e:14:75:42
[20958.776463] wlan0: authenticated
[20958.776467] wlan0: associate with AP 00:0b:0e:14:75:42
[20958.804389] wlan0: RX AssocResp from 00:0b:0e:14:75:42 (capab=0x401 status=0 aid=1)
[20958.804395] wlan0: associated
[20958.854667] /dev/vmnet: open called by PID 5235 (vmnet-bridge)
[20958.854702] /dev/vmnet: hub 0 does not exist, allocating memory.
[20958.854766] /dev/vmnet: port on hub 0 successfully opened
[20958.854797] bridge-wlan0: is a Wireless Adapter
[20958.854802] bridge-wlan0: up
[20958.854827] bridge-wlan0: attached
[21405.240043] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x022f000e
[22625.177594] atkbd.c: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
[22625.177603] atkbd.c: Use 'setkeycodes e060 <keycode>' to make it known.
[24854.639125] operapluginwrap[8027]: segfault at 0 ip 01d3b4b4 sp bf8e760c error 4 in libflashplayer.so[1a08000+994000]
[27974.783045] bridge-wlan0: disabling the bridge
[27974.797311] bridge-wlan0: down
[27974.797367] bridge-wlan0: detached
[27974.869727] /dev/vmnet: open called by PID 9201 (vmnet-bridge)
[27974.869761] /dev/vmnet: hub 0 does not exist, allocating memory.
[27974.869825] /dev/vmnet: port on hub 0 successfully opened
[27974.869857] bridge-wlan0: is a Wireless Adapter
[27974.869882] bridge-wlan0: up
[27974.869886] bridge-wlan0: attached
[27975.036943] /dev/vmnet: open called by PID 9202 (vmnet-netifup)
[27975.037007] /dev/vmnet: hub 1 does not exist, allocating memory.
[27975.037166] /dev/vmnet: port on hub 1 successfully opened
[27975.279145] /dev/vmnet: open called by PID 9204 (vmnet-dhcpd)
[27975.279231] /dev/vmnet: port on hub 1 successfully opened
[27975.542520] /dev/vmnet: open called by PID 9206 (vmnet-netifup)
[27975.542580] /dev/vmnet: hub 8 does not exist, allocating memory.
[27975.542738] /dev/vmnet: port on hub 8 successfully opened
[27975.693962] /dev/vmnet: open called by PID 9208 (vmnet-dhcpd)
[27975.694046] /dev/vmnet: port on hub 8 successfully opened
[27975.779217] /dev/vmnet: open called by PID 9212 (vmnet-natd)
[27975.779302] /dev/vmnet: port on hub 8 successfully opened
[27985.384184] vmnet1: no IPv6 routers present
[27985.988036] vmnet8: no IPv6 routers present
[28142.635509] bridge-wlan0: disabling the bridge
[28142.644233] bridge-wlan0: down
[28142.644269] bridge-wlan0: detached
[28142.716841] /dev/vmnet: open called by PID 9324 (vmnet-bridge)
[28142.716874] /dev/vmnet: hub 0 does not exist, allocating memory.
[28142.716937] /dev/vmnet: port on hub 0 successfully opened
[28142.716988] bridge-wlan0: is a Wireless Adapter
[28142.716993] bridge-wlan0: up
[28142.716998] bridge-wlan0: attached
[28143.082548] /dev/vmnet: open called by PID 9327 (vmnet-natd)
[28143.082579] /dev/vmnet: hub 8 does not exist, allocating memory.
[28143.082644] /dev/vmnet: port on hub 8 successfully opened
[28473.563651] wlan0: disassociating by local choice (reason=3)
[28473.581988] bridge-wlan0: disabling the bridge
[28473.593210] bridge-wlan0: down
[28473.593248] bridge-wlan0: detached
[28473.640144] wlan0: deauthenticating by local choice (reason=3)
[28475.661205] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[28475.661210] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[28475.661233] PM: Basic memory bitmaps created
[28475.661235] PM: Syncing filesystems ... done.
[28475.917157] Freezing user space processes ... (elapsed 0.01 seconds) done.
[28475.933621] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[28475.933899] PM: Shrinking memory...  -\|/-\|/-\|/-\|/-\|/-\|/-done (226030 pages freed)
[28485.747021] PM: Freed 904120 kbytes in 9.81 seconds (92.16 MB/s)
[28485.747025] Suspending console(s) (use no_console_suspend to debug)
[28485.772306] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[28485.772959] ACPI handle has no context!
[28485.773181] ACPI handle has no context!
[28485.773207] sdhci-pci 0000:06:04.3: PME# disabled
[28485.773216] sdhci-pci 0000:06:04.3: PCI INT C disabled
[28485.773241] ACPI handle has no context!
[28485.788353] ACPI handle has no context!
[28485.788382] tifm_7xx1 0000:06:04.2: PME# disabled
[28485.788410] tifm_7xx1 0000:06:04.2: PCI INT C disabled
[28485.788440] ACPI handle has no context!
[28485.804415] ACPI handle has no context!
[28485.836597] ata_piix 0000:00:1f.2: PCI INT B disabled
[28485.836668] HDA Intel 0000:00:1b.0: PCI INT A disabled
[28485.854373] ACPI: Preparing to enter system sleep state S4
[28485.869260] PM: Saving platform NVS memory
[28485.909661] Disabling non-boot CPUs ...
[28485.912230] CPU 1 is now offline
[28485.912233] SMP alternatives: switching to UP code
[28485.925193] CPU0 attaching NULL sched-domain.
[28485.925197] CPU1 attaching NULL sched-domain.
[28485.925225] CPU0 attaching NULL sched-domain.
[28485.925768] CPU1 is down
[28485.926090] PM: Creating hibernation image: 
[28485.928011] PM: Need to copy 125021 pages
[28485.928011] PM: Normal pages needed: 82614 + 1024 + 42, available pages: 144610
[28485.928011] PM: Restoring platform NVS memory
[28485.928011] CPU0: Thermal monitoring handled by SMI
[28485.928011] Enabling non-boot CPUs ...
[28485.928011] SMP alternatives: switching to SMP code
[28485.931147] Booting processor 1 APIC 0x1 ip 0x6000
[28485.924430] Initializing CPU#1
[28485.924430] Calibrating delay using timer specific routine.. 3724.15 BogoMIPS (lpj=7448316)
[28485.924430] CPU: L1 I cache: 32K, L1 D cache: 32K
[28485.924430] CPU: L2 cache: 2048K
[28485.924430] CPU: Physical Processor ID: 0
[28485.924430] CPU: Processor Core ID: 1
[28485.924430] mce: CPU supports 6 MCE banks
[28485.924430] CPU1: Thermal monitoring handled by SMI
[28486.020591] CPU1: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
[28486.020706] CPU0 attaching NULL sched-domain.
[28486.021019] Switched to high resolution mode on CPU 1
[28486.036021] CPU0 attaching sched-domain:
[28486.036025]  domain 0: span 0-1 level MC
[28486.036028]   groups: 0 1
[28486.036032] CPU1 attaching sched-domain:
[28486.036035]  domain 0: span 0-1 level MC
[28486.036037]   groups: 1 0
[28486.037021] CPU1 is up
[28486.037181] ACPI: Waking up from system sleep state S4
[28486.220305] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[28486.220684] ehci_hcd 0000:00:1d.7: PME# disabled
[28486.220709] pci 0000:00:1e.0: restoring config space at offset 0x6 (was 0x38060600, writing 0x380a0600)
[28486.220806] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80001, writing 0x2b80005)
[28486.221051] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100406)
[28486.221244] yenta_cardbus 0000:06:04.0: restoring config space at offset 0xf (was 0x34001ff, writing 0x5c001ff)
[28486.221272] yenta_cardbus 0000:06:04.0: restoring config space at offset 0x3 (was 0x824000, writing 0x82a808)
[28486.236086] ohci1394 0000:06:04.1: restoring config space at offset 0xf (was 0x4020200, writing 0x402020a)
[28486.236114] ohci1394 0000:06:04.1: restoring config space at offset 0x3 (was 0x800000, writing 0x802010)
[28486.236123] ohci1394 0000:06:04.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100016)
[28486.532188] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445469655801320512 new 18445469654407320458 attempts 1
[28486.956544] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[28486.956570] HDA Intel 0000:00:1b.0: setting latency timer to 64
[28486.956639] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[28486.956737] usb usb2: root hub lost power or was reset
[28486.956793] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[28486.956870] usb usb3: root hub lost power or was reset
[28486.956927] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[28486.956997] usb usb4: root hub lost power or was reset
[28486.957054] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[28486.957124] usb usb5: root hub lost power or was reset
[28486.957181] ehci_hcd 0000:00:1d.7: PME# disabled
[28486.957187] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[28486.957211] usb usb1: root hub lost power or was reset
[28486.961147] ehci_hcd 0000:00:1d.7: debug port 1
[28486.961154] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[28486.961185] pci 0000:00:1e.0: setting latency timer to 64
[28486.961213] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[28486.961218] ata_piix 0000:00:1f.2: setting latency timer to 64
[28486.963382] pci 0000:01:00.0: PME# disabled
[28486.963392] r8169 0000:05:00.0: wake-up capability disabled by ACPI
[28486.963459] r8169 0000:05:00.0: PME# disabled
[28487.125707] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[28487.125711] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[28487.125872] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[28487.125893] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
[28487.141477] ata2.00: configured for UDMA/33
[28487.142057] ata1.00: configured for UDMA/100
[28487.156268] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[de005000-de0057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[28487.156585] tifm_7xx1 0000:06:04.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[28487.156620] sdhci-pci 0000:06:04.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[28487.904644] sd 0:0:0:0: [sda] Starting disk
[28487.931488] PM: Image restored successfully.
[28488.042984] Restarting tasks ... done.
[28488.049077] PM: Basic memory bitmaps freed
[28488.336198] usb 1-6: new high speed USB device using ehci_hcd and address 11
[28488.404367] hub 1-0:1.0: unable to enumerate USB device on port 6
[28488.428194] usb 2-2: USB disconnect, address 2
[28488.692233] usb 2-2: new low speed USB device using uhci_hcd and address 3
[28488.868735] usb 2-2: configuration #1 chosen from 1 choice
[28488.886222] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input13
[28488.886439] generic-usb 0003:046D:C050.0003: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2/input0
[28488.886562] usb 4-2: USB disconnect, address 3
[28489.148202] usb 4-2: new full speed USB device using uhci_hcd and address 4
[28489.295362] usb 4-2: not running at top speed; connect to a high speed hub
[28489.347766] usb 4-2: configuration #1 chosen from 1 choice
[28489.354612] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[28489.359839] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input14
[28492.165775] r8169: eth0: link up
[28492.165785] r8169: eth0: link up
[28492.167026] /dev/vmnet: open called by PID 9324 (vmnet-bridge)
[28492.167054] /dev/vmnet: hub 0 does not exist, allocating memory.
[28492.167119] /dev/vmnet: port on hub 0 successfully opened
[28492.167150] bridge-eth0: up
[28492.167154] bridge-eth0: attached
[28500.532211] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445469654407320458 new 18445469654409019273 attempts 1
[28502.596054] eth0: no IPv6 routers present
[28589.078563] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

```
  I thought that the problem might be somehow related to the VMware Network (I remember having a problem with WinXP as host where the guest stole my internet connection although I set it to NAT and therefore I was able to surf only inside the virtual machine :D - I might install a guest OS now to see if something like this happens).



EDIT: I have made a great progress (from my point of view of course). First of all I tried the commands given in the link posted above (although the problem there is different - they have either connection through the browser or repositories, and I have none whatsoever). This gave me an idea. Since my connection is somehow jumping occasionally, I decided to run these **mtr**, **traceroute** etc. a couple of times. Here's what I got:

**mtr:**
- sometimes I get Loss = 0% (except by the ???, where it's always 100% loss)
- sometimes I get Loss = 33% or 66% (again - ??? has 100% loss)
- sometimes I get nothing. Just *HOST: rbaleksandar Loss% Snt Last Avg Best Wrst StDev*. That is - an empty table

**traceroute:**
- sometimes I get many IP adresses
- sometimes I get only * * *

**tracepath:**
- doesn't return anything. I have to press Ctrl+C to stop it.


  The idea that came to me was to unplug, than plug the cable and see what's the network traffic doing. For my GREAT surprise I realized after 2-3 testing rounds that a couple of seconds after I plug the cable and Ubuntu connects to the network, I get a full speed and everything works. After that the shaky behavior starts again until the next plug/unplug of the network cable.

  Second thing I tried out is to go to the computer center of my faculty and use my cable to connect to the uni-network there (because at some point I thought that maybe one tiny cable in my twisted-pair 'sausage' doesn't make good contact (which is quite a possibility considering the shaky connection). And here comes another surprise - it works perfect there! So I guess I'll have to ask someone from the network-team why the hell is all this happening to me.

---

### Post by Cphood on 2010-05-22
I lost the wired connection with 10,04 after an update to the jockey.gtk and jockey. common files. 10.04 would connect wireless as would two other computers on the Linksys 54GL router.  Ubuntu 9.10 live cd would give a wired connection but the live cd for 10.04 would not. Re-installed 10.04, but stll no wired connection.  Turned everything off, (computer..router..modem), after 5 minutes turned everything on and rebooted.  Wired connection was established and it has worked flawlessly since. Hope this helps.

---

### Post by rbaleksandar on 2010-05-22
Thanks for the reply. I'll contact the network team these days. In your case you've lost the ability to establish a wired connection at all. For me it's just the network at home. It uses a proxy, so this might be the problem. Because otherwise I don't see a difference in the network in the computer center and the one at home (because both are a part of the university network).

---

