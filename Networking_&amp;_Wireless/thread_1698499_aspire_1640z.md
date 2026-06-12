---
title: "aspire 1640z"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by notbert on 2011-03-02
Hello, all. I have an Aspire 1640z laptop running a wubi install of Version 10.10. The computer had been running Hardy, and the wireless was working fine up until about a month ago, it could then be described as spotty at best. It will, with effort, connect to an unsecured network. However the connection speed varies wildly, it disconnects randomly, and drops packets even when sitting right next to the AP. All other wireless machines on the network are without issue, and I have tried connecting to other networks with the same result. Here's some of the output

```
Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

```
iwconfig
eth1      IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:46:E7:30   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-60 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:0   Missed beacon:0

```

```
ifconfig
eth1      Link encap:Ethernet  HWaddr 00:16:6f:10:f9:dd  
          inet addr:xxx.xxx.x.x  Bcast:xxx.xxx.x.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe10:f9dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:418 errors:0 dropped:14 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:319076 (319.0 KB)  TX bytes:50060 (50.0 KB)
          Interrupt:17 Memory:b0101000-b0101fff
```

```
output from lshw -C network
*-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:10:f9:dd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=xxx.xxx.x.x latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:b0101000-b0101fff
```

```
Kernel Info
2.6.35-27-generic i686
```

```
dmesg output:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-27-generic (buildd@palmer) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 (Ubuntu 2.6.35-27.48-generic 2.6.35.11)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 00000000000e4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f680000 (usable)
[    0.000000]  BIOS-e820: 000000003f680000 - 000000003f68b000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f68b000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f680 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 00000000000e4000 (reserved)
[    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f680000 (usable)
[    0.000000]  modified: 000000003f680000 - 000000003f68b000 (ACPI data)
[    0.000000]  modified: 000000003f68b000 - 000000003f700000 (ACPI NVS)
[    0.000000]  modified: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 2eedc000 - 2f920000
[    0.000000] ACPI: RSDP 000f6bd0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3f684fa4 00044 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3f68ae88 00074 (v01 INTEL  ALVISO   06040000 LOHR 0000005F)
[    0.000000] ACPI: DSDT 3f68581e 0566A (v01 INTEL  ALVISO   06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f69bfc0 00040
[    0.000000] ACPI: APIC 3f68aefc 00068 (v01 INTEL  ALVISO   06040000 LOHR 0000005F)
[    0.000000] ACPI: HPET 3f68af64 00038 (v01 INTEL  ALVISO   06040000 LOHR 0000005F)
[    0.000000] ACPI: MCFG 3f68af9c 0003C (v01 INTEL  ALVISO   06040000 LOHR 0000005F)
[    0.000000] ACPI: BOOT 3f68afd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3f6853d9 00235 (v01  PmRef  Cpu0Ist 00003000 INTL 20030224)
[    0.000000] ACPI: SSDT 3f685201 001D8 (v01  PmRef  Cpu0Cst 00003001 INTL 20030224)
[    0.000000] ACPI: SSDT 3f684fe8 00219 (v01  PmRef    CpuPm 00003000 INTL 20030224)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f680
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f680
[    0.000000] On node 0 totalpages: 259600
[    0.000000] free_area_init_node: node 0, pgdat c0801fc0, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32132 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257570
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5194220 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (49 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a4adc]   TEXT DATA BSS
[    0.000000]   #3 [002eedc000 - 002f920000]         RAMDISK
[    0.000000]   #4 [000009f800 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00009a5000 - 00009a8150]             BRK
[    0.000000]   #6 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #7 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #8 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #9 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #10 [0001001000 - 00017f1000]         BOOTMEM
[    0.000000]   #11 [00017f1000 - 00017f1004]         BOOTMEM
[    0.000000]   #12 [00017f1040 - 00017f1100]         BOOTMEM
[    0.000000]   #13 [00017f1100 - 00017f1154]         BOOTMEM
[    0.000000]   #14 [00017f1180 - 00017f4180]         BOOTMEM
[    0.000000]   #15 [00017f4180 - 00017f418c]         BOOTMEM
[    0.000000]   #16 [00017f41c0 - 00017f47c0]         BOOTMEM
[    0.000000]   #17 [00017f47c0 - 00017f47e5]         BOOTMEM
[    0.000000]   #18 [00017f4800 - 00017f4827]         BOOTMEM
[    0.000000]   #19 [00017f4840 - 00017f4a00]         BOOTMEM
[    0.000000]   #20 [00017f4a00 - 00017f4a40]         BOOTMEM
[    0.000000]   #21 [00017f4a40 - 00017f4a80]         BOOTMEM
[    0.000000]   #22 [00017f4a80 - 00017f4ac0]         BOOTMEM
[    0.000000]   #23 [00017f4ac0 - 00017f4b00]         BOOTMEM
[    0.000000]   #24 [00017f4b00 - 00017f4b40]         BOOTMEM
[    0.000000]   #25 [00017f4b40 - 00017f4b80]         BOOTMEM
[    0.000000]   #26 [00017f4b80 - 00017f4bc0]         BOOTMEM
[    0.000000]   #27 [00017f4bc0 - 00017f4c00]         BOOTMEM
[    0.000000]   #28 [00017f4c00 - 00017f4c40]         BOOTMEM
[    0.000000]   #29 [00017f4c40 - 00017f4c80]         BOOTMEM
[    0.000000]   #30 [00017f4c80 - 00017f4cc0]         BOOTMEM
[    0.000000]   #31 [00017f4cc0 - 00017f4d00]         BOOTMEM
[    0.000000]   #32 [00017f4d00 - 00017f4d40]         BOOTMEM
[    0.000000]   #33 [00017f4d40 - 00017f4d50]         BOOTMEM
[    0.000000]   #34 [00017f4d80 - 00017f4d90]         BOOTMEM
[    0.000000]   #35 [00017f4dc0 - 00017f4e27]         BOOTMEM
[    0.000000]   #36 [00017f4e40 - 00017f4ea7]         BOOTMEM
[    0.000000]   #37 [0001800000 - 000180e000]         BOOTMEM
[    0.000000]   #38 [0001a00000 - 0001a0e000]         BOOTMEM
[    0.000000]   #39 [00017f6ec0 - 00017f6ec4]         BOOTMEM
[    0.000000]   #40 [00017f6f00 - 00017f6f04]         BOOTMEM
[    0.000000]   #41 [00017f6f40 - 00017f6f48]         BOOTMEM
[    0.000000]   #42 [00017f6f80 - 00017f6f88]         BOOTMEM
[    0.000000]   #43 [00017f6fc0 - 00017f7068]         BOOTMEM
[    0.000000]   #44 [00017f7080 - 00017f70e8]         BOOTMEM
[    0.000000]   #45 [00017f7100 - 00017fb100]         BOOTMEM
[    0.000000]   #46 [000180e000 - 000188e000]         BOOTMEM
[    0.000000]   #47 [000188e000 - 00018ce000]         BOOTMEM
[    0.000000]   #48 [0001a0e000 - 0001f021ec]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f680)
[    0.000000] Memory: 1004864k/1038848k available (4935k kernel code, 33536k reserved, 2337k data, 688k init, 129544k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081b000 - 0xc08c7000   ( 688 kB)
[    0.000000]       .data : 0xc05d1fce - 0xc081a7a8   (2337 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d1fce   (4935 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1733.182 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3466.36 BogoMIPS (lpj=6932728)
[    0.004012] pid_max: default: 32768 minimum: 301
[    0.004033] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004056] Yama: becoming mindful.
[    0.004122] Mount-cache hash table entries: 512
[    0.004279] Initializing cgroup subsys ns
[    0.004284] Initializing cgroup subsys cpuacct
[    0.004289] Initializing cgroup subsys memory
[    0.004301] Initializing cgroup subsys devices
[    0.004304] Initializing cgroup subsys freezer
[    0.004307] Initializing cgroup subsys net_cls
[    0.004344] mce: CPU supports 5 MCE banks
[    0.004354] CPU0: Thermal monitoring enabled (TM2)
[    0.004363] Performance Events: p6 PMU driver.
[    0.004372] ... version:                0
[    0.004375] ... bit width:              32
[    0.004377] ... generic registers:      2
[    0.004380] ... value mask:             00000000ffffffff
[    0.004382] ... max period:             000000007fffffff
[    0.004385] ... fixed-purpose events:   0
[    0.004387] ... event mask:             0000000000000003
[    0.005452] SMP alternatives: switching to UP code
[    0.014553] ACPI: Core revision 20100428
[    0.024009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.024014] ftrace: allocating 21761 entries in 43 pages
[    0.028075] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028445] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069994] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    0.072000] Brought up 1 CPUs
[    0.072000] Total of 1 processors activated (3466.36 BogoMIPS).
[    0.072000] devtmpfs: initialized
[    0.072000] regulator: core version 0.5
[    0.072000] Time: 10:14:22  Date: 03/02/11
[    0.072000] NET: Registered protocol family 16
[    0.072000] EISA bus registered
[    0.072000] ACPI: bus type pci registered
[    0.072000] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.072000] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.072000] PCI: Using MMCONFIG for extended config space
[    0.072000] PCI: Using configuration type 1 for base access
[    0.072000] bio: create slab <bio-0> at 0
[    0.072629] ACPI: EC: Look up EC in DSDT
[    0.076350] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.204100] ACPI: Interpreter enabled
[    0.204106] ACPI: (supports S0 S3 S4 S5)
[    0.204131] ACPI: Using IOAPIC for interrupt routing
[    0.208788] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.209053] ACPI: No dock devices found.
[    0.209058] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.209624] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.210758] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.210762] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xbfff] (ignored)
[    0.210765] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.210769] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.210773] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.210776] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.210780] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    0.210783] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff] (ignored)
[    0.210787] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff] (ignored)
[    0.210846] pci 0000:00:02.0: reg 10: [mem 0xb0080000-0xb00fffff]
[    0.210851] pci 0000:00:02.0: reg 14: [io  0x1800-0x1807]
[    0.210857] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
[    0.210862] pci 0000:00:02.0: reg 1c: [mem 0xb0000000-0xb003ffff]
[    0.210892] pci 0000:00:02.1: reg 10: [mem 0x00000000-0x0007ffff]
[    0.210990] pci 0000:00:1b.0: reg 10: [mem 0xd000c000-0xd000ffff 64bit]
[    0.211049] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.211055] pci 0000:00:1b.0: PME# disabled
[    0.211147] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.211153] pci 0000:00:1c.0: PME# disabled
[    0.211247] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.211253] pci 0000:00:1c.1: PME# disabled
[    0.211346] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.211352] pci 0000:00:1c.2: PME# disabled
[    0.211415] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.211475] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.211535] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.211595] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.211653] pci 0000:00:1d.7: reg 10: [mem 0xb0040000-0xb00403ff]
[    0.211713] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.211719] pci 0000:00:1d.7: PME# disabled
[    0.211865] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.211871] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.211876] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 1600-167f
[    0.211881] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 0060-006f
[    0.211909] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.211918] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.211926] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.211934] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.211942] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.212026] pci 0000:00:1f.3: reg 20: [io  0x18e0-0x18ff]
[    0.212116] pci 0000:00:1c.0: PCI bridge to [bus 09-09]
[    0.212122] pci 0000:00:1c.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.212128] pci 0000:00:1c.0:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.212137] pci 0000:00:1c.0:   bridge window [mem 0x00000000-0x000fffff pref] (disabled)
[    0.212196] pci 0000:00:1c.1: PCI bridge to [bus 0a-0a]
[    0.212201] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0000] (disabled)
[    0.212207] pci 0000:00:1c.1:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.212216] pci 0000:00:1c.1:   bridge window [mem 0x00000000-0x000fffff pref] (disabled)
[    0.212273] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.212278] pci 0000:00:1c.2:   bridge window [io  0x0000-0x0000] (disabled)
[    0.212284] pci 0000:00:1c.2:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.212292] pci 0000:00:1c.2:   bridge window [mem 0x00000000-0x000fffff pref] (disabled)
[    0.212357] pci 0000:06:01.0: reg 10: [mem 0xb0100000-0xb0100fff]
[    0.212385] pci 0000:06:01.0: supports D1 D2
[    0.212387] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212393] pci 0000:06:01.0: PME# disabled
[    0.212438] pci 0000:06:04.0: reg 10: [mem 0xb0101000-0xb0101fff]
[    0.212507] pci 0000:06:04.0: PME# supported from D0 D3hot D3cold
[    0.212513] pci 0000:06:04.0: PME# disabled
[    0.212558] pci 0000:06:08.0: reg 10: [io  0x2000-0x20ff]
[    0.212568] pci 0000:06:08.0: reg 14: [mem 0xb0102000-0xb01020ff]
[    0.212629] pci 0000:06:08.0: supports D1 D2
[    0.212632] pci 0000:06:08.0: PME# supported from D1 D2 D3hot D3cold
[    0.212638] pci 0000:06:08.0: PME# disabled
[    0.212687] pci 0000:00:1e.0: PCI bridge to [bus 06-07] (subtractive decode)
[    0.212693] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.212699] pci 0000:00:1e.0:   bridge window [mem 0xb0100000-0xb01fffff]
[    0.212707] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.212711] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.212714] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.212766] pci_bus 0000:07: [bus 07-08] partially hidden behind transparent bridge 0000:06 [bus 06-07]
[    0.212794] pci_bus 0000:00: on NUMA node 0
[    0.212800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.213075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.213174] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.213273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.213471] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.221635] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.221755] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.221871] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.221985] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.222099] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.222214] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.222327] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.222442] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.222493] HEST: Table is not found!
[    0.222572] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.222583] vgaarb: loaded
[    0.222786] SCSI subsystem initialized
[    0.222836] libata version 3.00 loaded.
[    0.222895] usbcore: registered new interface driver usbfs
[    0.222910] usbcore: registered new interface driver hub
[    0.222938] usbcore: registered new device driver usb
[    0.223084] ACPI: WMI: Mapper loaded
[    0.223086] PCI: Using ACPI for IRQ routing
[    0.223090] PCI: pci_cache_line_size set to 64 bytes
[    0.223170] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.223173] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.223176] reserve RAM buffer: 000000003f680000 - 000000003fffffff 
[    0.223286] NetLabel: Initializing
[    0.223289] NetLabel:  domain hash size = 128
[    0.223291] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.223308] NetLabel:  unlabeled traffic allowed by default
[    0.223343] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.223351] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.223356] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.228020] Switching to clocksource tsc
[    0.240563] AppArmor: AppArmor Filesystem Enabled
[    0.240592] pnp: PnP ACPI init
[    0.240630] ACPI: bus type pnp registered
[    0.242482] pnp: PnP ACPI: found 9 devices
[    0.242486] ACPI: ACPI bus type pnp unregistered
[    0.242491] PnPBIOS: Disabled by ACPI PNP
[    0.242508] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.242512] system 00:01: [mem 0xf0000000-0xf0003fff] has been reserved
[    0.242516] system 00:01: [mem 0xf0004000-0xf0004fff] has been reserved
[    0.242520] system 00:01: [mem 0xf0005000-0xf0005fff] has been reserved
[    0.242523] system 00:01: [mem 0xf0008000-0xf000bfff] has been reserved
[    0.242527] system 00:01: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.242536] system 00:05: [io  0x0680-0x06ff] has been reserved
[    0.242539] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.242543] system 00:05: [io  0x1000-0x107f] has been reserved
[    0.242546] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.242550] system 00:05: [io  0x1600-0x167f] has been reserved
[    0.278978] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.278983] pci 0000:00:1c.0: BAR 14: assigned [mem 0x44000000-0x441fffff]
[    0.278987] pci 0000:00:1c.0: BAR 15: assigned [mem 0x44200000-0x443fffff 64bit pref]
[    0.278991] pci 0000:00:1c.1: BAR 14: assigned [mem 0x44400000-0x445fffff]
[    0.278995] pci 0000:00:1c.1: BAR 15: assigned [mem 0x44600000-0x447fffff 64bit pref]
[    0.278999] pci 0000:00:1c.2: BAR 14: assigned [mem 0x44800000-0x449fffff]
[    0.279003] pci 0000:00:1c.2: BAR 15: assigned [mem 0x44a00000-0x44bfffff 64bit pref]
[    0.279007] pci 0000:00:02.1: BAR 0: assigned [mem 0x44c00000-0x44c7ffff]
[    0.279013] pci 0000:00:02.1: BAR 0: set to [mem 0x44c00000-0x44c7ffff] (PCI address [0x44c00000-0x44c7ffff]
[    0.279018] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.279022] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.279025] pci 0000:00:1c.2: BAR 13: assigned [io  0x5000-0x5fff]
[    0.279029] pci 0000:00:1c.0: PCI bridge to [bus 09-09]
[    0.279034] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.279041] pci 0000:00:1c.0:   bridge window [mem 0x44000000-0x441fffff]
[    0.279047] pci 0000:00:1c.0:   bridge window [mem 0x44200000-0x443fffff 64bit pref]
[    0.279055] pci 0000:00:1c.1: PCI bridge to [bus 0a-0a]
[    0.279060] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.279067] pci 0000:00:1c.1:   bridge window [mem 0x44400000-0x445fffff]
[    0.279072] pci 0000:00:1c.1:   bridge window [mem 0x44600000-0x447fffff 64bit pref]
[    0.279081] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    0.279085] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
[    0.279092] pci 0000:00:1c.2:   bridge window [mem 0x44800000-0x449fffff]
[    0.279098] pci 0000:00:1c.2:   bridge window [mem 0x44a00000-0x44bfffff 64bit pref]
[    0.279108] pci 0000:06:01.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.279112] pci 0000:06:01.0: BAR 16: assigned [mem 0x48000000-0x4bffffff]
[    0.279115] pci 0000:06:01.0: BAR 13: assigned [io  0x2400-0x24ff]
[    0.279119] pci 0000:06:01.0: BAR 14: assigned [io  0x2800-0x28ff]
[    0.279122] pci 0000:06:01.0: CardBus bridge to [bus 07-08]
[    0.279125] pci 0000:06:01.0:   bridge window [io  0x2400-0x24ff]
[    0.279131] pci 0000:06:01.0:   bridge window [io  0x2800-0x28ff]
[    0.279138] pci 0000:06:01.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.279144] pci 0000:06:01.0:   bridge window [mem 0x48000000-0x4bffffff]
[    0.279151] pci 0000:00:1e.0: PCI bridge to [bus 06-07]
[    0.279155] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.279162] pci 0000:00:1e.0:   bridge window [mem 0xb0100000-0xb01fffff]
[    0.279168] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.279186] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.279194]   alloc irq_desc for 17 on node -1
[    0.279197]   alloc kstat_irqs on node -1
[    0.279206] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.279214] pci 0000:00:1c.0: setting latency timer to 64
[    0.279225] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.279229]   alloc irq_desc for 16 on node -1
[    0.279231]   alloc kstat_irqs on node -1
[    0.279236] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.279242] pci 0000:00:1c.1: setting latency timer to 64
[    0.279253] pci 0000:00:1c.2: enabling device (0000 -> 0003)
[    0.279257]   alloc irq_desc for 18 on node -1
[    0.279259]   alloc kstat_irqs on node -1
[    0.279263] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.279270] pci 0000:00:1c.2: setting latency timer to 64
[    0.279279] pci 0000:00:1e.0: setting latency timer to 64
[    0.279294] pci 0000:06:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.279301] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.279304] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.279308] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    0.279311] pci_bus 0000:09: resource 1 [mem 0x44000000-0x441fffff]
[    0.279314] pci_bus 0000:09: resource 2 [mem 0x44200000-0x443fffff 64bit pref]
[    0.279317] pci_bus 0000:0a: resource 0 [io  0x4000-0x4fff]
[    0.279320] pci_bus 0000:0a: resource 1 [mem 0x44400000-0x445fffff]
[    0.279324] pci_bus 0000:0a: resource 2 [mem 0x44600000-0x447fffff 64bit pref]
[    0.279327] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.279330] pci_bus 0000:02: resource 1 [mem 0x44800000-0x449fffff]
[    0.279333] pci_bus 0000:02: resource 2 [mem 0x44a00000-0x44bfffff 64bit pref]
[    0.279337] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    0.279340] pci_bus 0000:06: resource 1 [mem 0xb0100000-0xb01fffff]
[    0.279343] pci_bus 0000:06: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.279346] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.279349] pci_bus 0000:06: resource 5 [mem 0x00000000-0xffffffff]
[    0.279352] pci_bus 0000:07: resource 0 [io  0x2400-0x24ff]
[    0.279355] pci_bus 0000:07: resource 1 [io  0x2800-0x28ff]
[    0.279358] pci_bus 0000:07: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.279362] pci_bus 0000:07: resource 3 [mem 0x48000000-0x4bffffff]
[    0.279410] NET: Registered protocol family 2
[    0.279499] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.279797] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.280884] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.281545] TCP: Hash tables configured (established 131072 bind 65536)
[    0.281549] TCP reno registered
[    0.281555] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.281578] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.281736] NET: Registered protocol family 1
[    0.281765] pci 0000:00:02.0: Boot video device
[    0.281902] PCI: CLS 64 bytes, default 64
[    0.282021] Simple Boot Flag at 0x36 set to 0x1
[    0.282156] cpufreq-nforce2: No nForce2 chipset.
[    0.282194] Scanning for low memory corruption every 60 seconds
[    0.282414] audit: initializing netlink socket (disabled)
[    0.282431] type=2000 audit(1299060862.276:1): initialized
[    0.295720] Trying to unpack rootfs image as initramfs...
[    0.312282] highmem bounce pool size: 64 pages
[    0.312290] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.320276] VFS: Disk quotas dquot_6.5.2
[    0.320366] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.321168] fuse init (API version 7.14)
[    0.321281] msgmni has been set to 1709
[    0.662263] Freeing initrd memory: 10512k freed
[    0.674065] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.674071] io scheduler noop registered
[    0.674073] io scheduler deadline registered
[    0.674095] io scheduler cfq registered (default)
[    0.674241] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.674291]   alloc irq_desc for 40 on node -1
[    0.674293]   alloc kstat_irqs on node -1
[    0.674308] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.674427] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.674470]   alloc irq_desc for 41 on node -1
[    0.674472]   alloc kstat_irqs on node -1
[    0.674481] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.674589] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.674633]   alloc irq_desc for 42 on node -1
[    0.674635]   alloc kstat_irqs on node -1
[    0.674644] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.674769] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.674886] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.688132] ACPI: AC Adapter [ACAD] (on-line)
[    0.688233] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.688302] ACPI: Lid Switch [LID]
[    0.688362] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.688368] ACPI: Power Button [PWRB]
[    0.688423] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.688428] ACPI: Sleep Button [SLPB]
[    0.688480] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.688484] ACPI: Power Button [PWRF]
[    0.688719] ACPI: acpi_idle registered with cpuidle
[    0.688885] Marking TSC unstable due to TSC halts in idle
[    0.690730] Switching to clocksource hpet
[    0.724070] thermal LNXTHERM:01: registered as thermal_zone0
[    0.724080] ACPI: Thermal Zone [THRM] (56 C)
[    0.724158] ACPI: Battery Slot [BAT1] (battery absent)
[    0.724198] ERST: Table is not found!
[    0.724248] isapnp: Scanning for PnP cards...
[    0.730040] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.731776] brd: module loaded
[    0.732441] loop: module loaded
[    0.732657] ata_piix 0000:00:1f.1: version 2.13
[    0.732674] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.732719] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.776378] scsi0 : ata_piix
[    0.776468] scsi1 : ata_piix
[    0.776635] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.776639] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.777045] Fixed MDIO Bus: probed
[    0.777086] PPP generic driver version 2.4.2
[    0.777141] tun: Universal TUN/TAP device driver, 1.6
[    0.777144] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.777232] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.777254]   alloc irq_desc for 23 on node -1
[    0.777256]   alloc kstat_irqs on node -1
[    0.777263] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.777275] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.777280] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.777325] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.777363] ehci_hcd 0000:00:1d.7: debug port 1
[    0.781237] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.781279] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0040000
[    0.785348] ata2: port disabled. ignoring.
[    0.828918] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.829065] hub 1-0:1.0: USB hub found
[    0.829071] hub 1-0:1.0: 8 ports detected
[    0.829159] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.829177] uhci_hcd: USB Universal Host Controller Interface driver
[    0.829204] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.829211] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.829215] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.829254] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.829282] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.829411] hub 2-0:1.0: USB hub found
[    0.829416] hub 2-0:1.0: 2 ports detected
[    0.829481]   alloc irq_desc for 19 on node -1
[    0.829484]   alloc kstat_irqs on node -1
[    0.829490] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.829497] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.829501] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.829538] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.829576] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.829707] hub 3-0:1.0: USB hub found
[    0.829712] hub 3-0:1.0: 2 ports detected
[    0.829773] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.829780] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.829784] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.829819] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.829856] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.830007] hub 4-0:1.0: USB hub found
[    0.830011] hub 4-0:1.0: 2 ports detected
[    0.830075] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.830082] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.830086] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.830126] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.830163] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.830291] hub 5-0:1.0: USB hub found
[    0.830297] hub 5-0:1.0: 2 ports detected
[    0.830431] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.922886] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.922892] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.010218] mice: PS/2 mouse device common for all mice
[    1.010449] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.010482] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.010619] device-mapper: uevent: version 1.0.3
[    1.010738] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.010793] device-mapper: multipath: version 1.1.1 loaded
[    1.010797] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.054350] EISA: Probing bus 0 at eisa.0
[    1.054357] Cannot allocate resource for EISA slot 1
[    1.054360] Cannot allocate resource for EISA slot 2
[    1.054363] Cannot allocate resource for EISA slot 3
[    1.054365] Cannot allocate resource for EISA slot 4
[    1.054368] Cannot allocate resource for EISA slot 5
[    1.054381] EISA: Detected 0 cards.
[    1.097988] isapnp: No Plug & Play device found
[    1.098070] cpuidle: using governor ladder
[    1.098151] cpuidle: using governor menu
[    1.098475] TCP cubic registered
[    1.098650] NET: Registered protocol family 10
[    1.099070] lo: Disabled Privacy Extensions
[    1.099315] NET: Registered protocol family 17
[    1.099647] Using IPI No-Shortcut mode
[    1.099737] PM: Resume from disk failed.
[    1.099751] registered taskstats version 1
[    1.100014]   Magic number: 3:357:223
[    1.100106] rtc_cmos 00:06: setting system clock to 2011-03-02 10:14:23 UTC (1299060863)
[    1.100109] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.100112] EDD information not available.
[    1.114324] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.124650] ata1.00: ATA-6: ST9100825A, 3.06, max UDMA/100
[    1.124654] ata1.00: 195371568 sectors, multi 16: LBA48 
[    1.124697] ata1.01: ATAPI: Slimtype DVDRW SSW-8015S, HRS2, max UDMA/66
[    1.140682] ata1.00: configured for UDMA/100
[    1.156423] ata1.01: configured for UDMA/66
[    1.158275] scsi 0:0:0:0: Direct-Access     ATA      ST9100825A       3.06 PQ: 0 ANSI: 5
[    1.158423] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.161095] scsi 0:0:1:0: CD-ROM            Slimtype DVDRW SSW-8015S  HRS2 PQ: 0 ANSI: 5
[    1.161292] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    1.172668] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.172672] Uniform CD-ROM driver Revision: 3.20
[    1.172780] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.172836] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.172897] sd 0:0:0:0: [sda] Write Protect is off
[    1.172900] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.172927] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.173093]  sda: sda1
[    1.184892] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.184911] Freeing unused kernel memory: 688k freed
[    1.185327] Write protecting the kernel text: 4936k
[    1.185370] Write protecting the kernel read-only data: 1980k
[    1.202370] udev[67]: starting version 163
[    1.431889] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.431918] 8139cp 0000:06:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.439173] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.439222] 8139too 0000:06:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.440521] 8139too 0000:06:08.0: eth0: RealTek RTL8139 at 0x2000, 00:16:36:3d:60:66, IRQ 16
[    1.935951] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[   19.953476] udev[305]: starting version 163
[   20.059572] lp: driver loaded but no devices found
[   20.188456] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   20.188595] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   20.354597] intel_rng: FWH not detected
[   20.534617] lib80211: common routines for IEEE802.11 drivers
[   20.534622] lib80211_crypt: registered algorithm 'NULL'
[   20.550076] Linux agpgart interface v0.103
[   20.566601] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   20.567247] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   20.583535] yenta_cardbus 0000:06:01.0: CardBus bridge found [1025:009e]
[   20.583556] yenta_cardbus 0000:06:01.0: Enabling burst memory read transactions
[   20.583562] yenta_cardbus 0000:06:01.0: Using CSCINT to route CSC interrupts to PCI
[   20.583565] yenta_cardbus 0000:06:01.0: Routing CardBus interrupts to PCI
[   20.583572] yenta_cardbus 0000:06:01.0: TI: mfunc 0x01111112, devctl 0x66
[   20.584636] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   20.690875] type=1400 audit(1299078883.085:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=554 comm="apparmor_parser"
[   20.691612] type=1400 audit(1299078883.085:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=554 comm="apparmor_parser"
[   20.692050] type=1400 audit(1299078883.089:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=554 comm="apparmor_parser"
[   20.732223] [drm] Initialized drm 1.1.0 20060810
[   20.772981] cfg80211: Calling CRDA to update world regulatory domain
[   20.817999] cfg80211: World regulatory domain updated:
[   20.818003]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.818007]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.818011]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.818014]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.818018]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.818021]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.828859] yenta_cardbus 0000:06:01.0: ISA IRQ mask 0x0cf8, PCI irq 18
[   20.828865] yenta_cardbus 0000:06:01.0: Socket status: 30000007
[   20.828870] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #08
[   20.828882] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[   20.828887] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff 0x2400-0x24ff 0x2800-0x28ff
[   20.841885] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge window: [mem 0xb0100000-0xb01fffff]
[   20.841890] pcmcia_socket pcmcia_socket0: cs: memory probe 0xb0100000-0xb01fffff: excluding 0xb0100000-0xb010ffff
[   20.841908] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[   20.841912] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
[   20.846519] libipw: 802.11 data/management/control stack, git-1.1.13
[   20.846524] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   20.918789] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   20.918794] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   20.918914] ipw2200 0000:06:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.932810] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   20.938850] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   20.940911] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   20.941655] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   20.942271] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   20.953674] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xd3fff 0xe0000-0xe3fff 0xe8000-0xfffff
[   20.953747] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   20.953817] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   20.953887] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   20.968125] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.968133] i915 0000:00:02.0: setting latency timer to 64
[   21.021968] [drm] set up 7M of stolen space
[   21.173960] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   21.174429] [drm] initialized overlay support
[   21.523619] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   21.780166] Skipping EDID probe due to cached edid
[   21.994143] Console: switching to colour frame buffer device 160x50
[   21.999401] fb0: inteldrmfb frame buffer device
[   21.999404] drm: registered panic notifier
[   22.000612] Slow work thread pool: Starting up
[   22.006195] Slow work thread pool: Ready
[   22.006205] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.006392] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.006438]   alloc irq_desc for 43 on node -1
[   22.006440]   alloc kstat_irqs on node -1
[   22.006454] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   22.006489] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   22.018164] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000/0x0
[   22.053630] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   22.107393] hda_codec: ALC883: BIOS auto-probing.
[   22.236190] Skipping EDID probe due to cached edid
[   22.518250] Adding 261116k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261116k 
[   22.573354] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   22.844647] type=1400 audit(1299078885.241:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=753 comm="apparmor_parser"
[   22.845558] type=1400 audit(1299078885.241:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=753 comm="apparmor_parser"
[   22.902825] type=1400 audit(1299078885.297:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=775 comm="apparmor_parser"
[   22.915658] type=1400 audit(1299078885.309:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=778 comm="apparmor_parser"
[   22.922496] ppdev: user-space parallel port driver
[   22.926806] type=1400 audit(1299078885.321:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=778 comm="apparmor_parser"
[   22.927216] type=1400 audit(1299078885.321:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=778 comm="apparmor_parser"
[   22.959788] eth0: link down
[   22.960294] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.980178] type=1400 audit(1299078885.377:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=783 comm="apparmor_parser"
[   23.348304] Skipping EDID probe due to cached edid
[   23.442410] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   23.836356] Skipping EDID probe due to cached edid
[   24.700330] Skipping EDID probe due to cached edid
[   25.188323] Skipping EDID probe due to cached edid
[   25.688324] Skipping EDID probe due to cached edid
[   26.176695] Skipping EDID probe due to cached edid
[   27.505928] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   33.040023] eth1: no IPv6 routers present
[   33.344224] Skipping EDID probe due to cached edid
[   33.848202] Skipping EDID probe due to cached edid
[   34.336275] Skipping EDID probe due to cached edid
[   34.824212] Skipping EDID probe due to cached edid
[   37.168213] Skipping EDID probe due to cached edid
[   40.628244] Skipping EDID probe due to cached edid
[   41.240212] Skipping EDID probe due to cached edid
[  606.900616] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  606.901089] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  617.296041] eth0: no IPv6 routers present
[ 1418.857276] eth0: link down
```

I have also tried installing the compat-wireless backport module with no effect. Any help would be much appreciated!

Edit: Also wanted to note that the ethernet connection is working normally.

---

### Post by notbert on 2011-03-27
Still a no luck with this issue, unfortunately. I've given ndiswrapper a go (Freezes the system after a few minutes), waited it out for a kernel/firmware update, and gave the whole thing a fresh install. One thing I've since noticed is that my syslog is getting blown up with the following

```
Mar 27 14:56:20 ubuntu wpa_supplicant[857]: CTRL-EVENT-CONNECTED - Connection to 00:12:17:46:e7:30 completed (reauth) [id=0 id_str=]
Mar 27 14:56:20 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  associating -> associated
Mar 27 14:56:20 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  associated -> completed
Mar 27 14:56:41 ubuntu wpa_supplicant[857]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 27 14:56:41 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  completed -> disconnected
Mar 27 14:56:42 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Mar 27 14:56:42 ubuntu wpa_supplicant[857]: Trying to associate with 00:12:17:46:e7:30 (SSID='linksys' freq=2437 MHz)
Mar 27 14:56:42 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  scanning -> associating
Mar 27 14:56:42 ubuntu wpa_supplicant[857]: Associated with 00:12:17:46:e7:30
Mar 27 14:56:42 ubuntu wpa_supplicant[857]: CTRL-EVENT-CONNECTED - Connection to 00:12:17:46:e7:30 completed (reauth) [id=0 id_str=]
Mar 27 14:56:42 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  associating -> associated
Mar 27 14:56:42 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  associated -> completed
Mar 27 14:56:52 ubuntu wpa_supplicant[857]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Mar 27 14:56:52 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  completed -> disconnected
Mar 27 14:56:52 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Mar 27 14:56:52 ubuntu wpa_supplicant[857]: Trying to associate with 00:12:17:46:e7:30 (SSID='linksys' freq=2437 MHz)
Mar 27 14:56:52 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  scanning -> associating
Mar 27 14:56:52 ubuntu wpa_supplicant[857]: Associated with 00:12:17:46:e7:30
Mar 27 14:56:52 ubuntu wpa_supplicant[857]: CTRL-EVENT-CONNECTED - Connection to 00:12:17:46:e7:30 completed (reauth) [id=0 id_str=]
Mar 27 14:56:52 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  associating -> associated
Mar 27 14:56:52 ubuntu NetworkManager[762]: <info> (eth1): supplicant connection state:  associated -> completed
Mar 27 14:56:52 ubuntu wpa_supplicant[857]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

Not sure if that indicates a problem with network-manager or what. Any ideas?

---

