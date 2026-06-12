---
title: "Need help debug - Crash/Reboot during file transfers"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by BB2008 on 2012-12-30
Hi All:

I have a 2002 era PC (MSI motherboard, AMD CPU) running 32 bit 12.04 server edition. I use it as a fileserver, to share media (via samba) on my home network between other ubuntu and windows machines. I have been observing this issue intermittently for sometime now that during accessing files from this machine (via samba) or transfering files to/from this server (via scp/sftp), the server will become unresponsive, thereby stopping the acesses/transfer (as the case maybe), midway.

Initially I thought maybe the onboard NIC was starting to go bad, so I bought a PCI based Gigabit NIC to see if that helps, but no luck. When this happened today I thought maybe I need to look closely at the logs of the server, see if I can catch something there. I have inlined the syslog below - keep in mind that the network freeze event happened at 10:23am.

```


Dec 30 10:17:01 WORKHORSE CRON[2865]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 10:23:35 WORKHORSE kernel: Kernel logging (proc) stopped.
Dec 30 10:23:35 WORKHORSE rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="529" x-info="http://www.rsyslog.com"] exiting on signal 15.
Dec 30 10:24:25 WORKHORSE kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec 30 10:24:25 WORKHORSE rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="528" x-info="http://www.rsyslog.com"] start
Dec 30 10:24:25 WORKHORSE rsyslogd: rsyslogd's groupid changed to 103
Dec 30 10:24:25 WORKHORSE rsyslogd: rsyslogd's userid changed to 101
Dec 30 10:24:25 WORKHORSE rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Linux version 3.2.0-35-generic-pae (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 (Ubuntu 3.2.0-35.55-generic-pae 3.2.34)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] KERNEL supported cpus:
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   Intel GenuineIntel
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   AMD AuthenticAMD
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   NSC Geode by NSC
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   Cyrix CyrixInstead
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   Centaur CentaurHauls
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   UMC UMC UMC UMC
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007dff0000 (usable)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 000000007dff0000 - 000000007dff3000 (ACPI NVS)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 000000007dff3000 - 000000007e000000 (ACPI data)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] DMI 2.2 present.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] DMI: MICRO-STAR INTERNATIONAL CO., LTD KM266-8235/MS-6738, BIOS 6.00 PG 03/18/2003
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] last_pfn = 0x7dff0 max_arch_pfn = 0x1000000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] MTRR default type: uncachable
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   00000-9FFFF write-back
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   C0000-C7FFF write-protect
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   C8000-FFFFF uncachable
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] MTRR variable ranges enabled:
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   1 base 07E000000 mask FFE000000 uncachable
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   2 base 0C0000000 mask FF0000000 write-combining
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   3 base 0C0000000 mask FF0000000 write-combining
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   4 disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   5 disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   6 disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   7 disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] found SMP MP-table at [c00f6740] f6740
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] initial memory mapped : 0 - 02000000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] RAMDISK: 364ea000 - 3726d000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: RSDP 000f8240 00014 (v00 VT8375)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: RSDT 7dff3000 0002C (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: FACP 7dff3040 00074 (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: DSDT 7dff30c0 039ED (v01 VT8375 AWRDACPI 00001000 MSFT 0100000D)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: FACS 7dff0000 00040
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: APIC 7dff6ac0 0005A (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] 1123MB HIGHMEM available.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] 891MB LOWMEM available.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   low ram: 0 - 37bfe000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Zone PFN ranges:
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0007dff0
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Movable zone start PFN for each node
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]     0: 0x00000100 -> 0x0007dff0
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] On node 0 totalpages: 515967
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] free_area_init_node: node 0, pgdat c186b1c0, node_mem_map f552a200
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   HighMem zone: 2248 pages used for memmap
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]   HighMem zone: 285482 pages, LIFO batch:31
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Using APIC driver default
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] nr_irqs_gsi: 40
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Allocating PCI resources starting at 7e000000 (gap: 7e000000:80c00000)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7be3000 s34240 r0 d23104 u57344
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] pcpu-alloc: [0] 0 
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 511935
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=98b2c29d-b319-4b35-8843-87dedb2051d4 ro
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Initializing CPU#0
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] allocated 8257024 bytes of page_cgroup
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007dff0)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Memory: 2014552k/2064320k available (5825k kernel code, 49316k reserved, 2849k data, 744k init, 1150920k highmem)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] virtual kernel memory layout:
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]       .init : 0xc1879000 - 0xc1933000   ( 744 kB)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]       .data : 0xc15b05bc - 0xc1878a00   (2849 kB)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000]       .text : 0xc1000000 - 0xc15b05bc   (5825 kB)
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Hierarchical RCU implementation.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Console: colour dummy device 80x25
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] console [tty0] enabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Fast TSC calibration using PIT
Dec 30 10:24:25 WORKHORSE kernel: [    0.000000] Detected 1799.812 MHz processor.
Dec 30 10:24:25 WORKHORSE kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3599.62 BogoMIPS (lpj=7199248)
Dec 30 10:24:25 WORKHORSE kernel: [    0.004025] pid_max: default: 32768 minimum: 301
Dec 30 10:24:25 WORKHORSE kernel: [    0.004082] Security Framework initialized
Dec 30 10:24:25 WORKHORSE kernel: [    0.004154] AppArmor: AppArmor initialized
Dec 30 10:24:25 WORKHORSE kernel: [    0.004162] Yama: becoming mindful.
Dec 30 10:24:25 WORKHORSE kernel: [    0.004294] Mount-cache hash table entries: 512
Dec 30 10:24:25 WORKHORSE kernel: [    0.004619] Initializing cgroup subsys cpuacct
Dec 30 10:24:25 WORKHORSE kernel: [    0.004636] Initializing cgroup subsys memory
Dec 30 10:24:25 WORKHORSE kernel: [    0.004658] Initializing cgroup subsys devices
Dec 30 10:24:25 WORKHORSE kernel: [    0.004667] Initializing cgroup subsys freezer
Dec 30 10:24:25 WORKHORSE kernel: [    0.004677] Initializing cgroup subsys blkio
Dec 30 10:24:25 WORKHORSE kernel: [    0.004695] Initializing cgroup subsys perf_event
Dec 30 10:24:25 WORKHORSE kernel: [    0.004744] CPU: CLK_CTL MSR was 60031223. Reprogramming to 20031223
Dec 30 10:24:25 WORKHORSE kernel: [    0.004761] mce: CPU supports 4 MCE banks
Dec 30 10:24:25 WORKHORSE kernel: [    0.004893] SMP alternatives: switching to UP code
Dec 30 10:24:25 WORKHORSE kernel: [    0.017959] Freeing SMP alternatives: 24k freed
Dec 30 10:24:25 WORKHORSE kernel: [    0.018045] ACPI: Core revision 20110623
Dec 30 10:24:25 WORKHORSE kernel: [    0.023418] ftrace: allocating 26576 entries in 53 pages
Dec 30 10:24:25 WORKHORSE kernel: [    0.028229] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 30 10:24:25 WORKHORSE kernel: [    0.028725] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 30 10:24:25 WORKHORSE kernel: [    0.071616] CPU0: AMD Athlon(tm) XP 2200+ stepping 01
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] Performance Events: AMD PMU driver.
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] ... version:                0
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] ... bit width:              48
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] ... generic registers:      4
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] ... value mask:             0000ffffffffffff
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] ... max period:             00007fffffffffff
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] ... fixed-purpose events:   0
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] ... event mask:             000000000000000f
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] Brought up 1 CPUs
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] Total of 1 processors activated (3599.62 BogoMIPS).
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] devtmpfs: initialized
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] EVM: security.selinux
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] EVM: security.SMACK64
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] EVM: security.capability
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] PM: Registering ACPI NVS region at 7dff0000 (12288 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] print_constraints: dummy: 
Dec 30 10:24:25 WORKHORSE kernel: [    0.072003] RTC time: 15:24:16, date: 12/30/12
Dec 30 10:24:25 WORKHORSE kernel: [    0.072030] NET: Registered protocol family 16
Dec 30 10:24:25 WORKHORSE kernel: [    0.072277] EISA bus registered
Dec 30 10:24:25 WORKHORSE kernel: [    0.072303] ACPI: bus type pci registered
Dec 30 10:24:25 WORKHORSE kernel: [    0.080912] PCI: PCI BIOS revision 2.10 entry at 0xfbd20, last bus=1
Dec 30 10:24:25 WORKHORSE kernel: [    0.080920] PCI: Using configuration type 1 for base access
Dec 30 10:24:25 WORKHORSE kernel: [    0.083080] bio: create slab <bio-0> at 0
Dec 30 10:24:25 WORKHORSE kernel: [    0.083275] ACPI: Added _OSI(Module Device)
Dec 30 10:24:25 WORKHORSE kernel: [    0.083283] ACPI: Added _OSI(Processor Device)
Dec 30 10:24:25 WORKHORSE kernel: [    0.083289] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 30 10:24:25 WORKHORSE kernel: [    0.083295] ACPI: Added _OSI(Processor Aggregator Device)
Dec 30 10:24:25 WORKHORSE kernel: [    0.084044] ACPI: EC: Look up EC in DSDT
Dec 30 10:24:25 WORKHORSE kernel: [    0.087876] ACPI: Interpreter enabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.087897] ACPI: (supports S0 S1 S4 S5)
Dec 30 10:24:25 WORKHORSE kernel: [    0.087932] ACPI: Using IOAPIC for interrupt routing
Dec 30 10:24:25 WORKHORSE kernel: [    0.092712] ACPI: No dock devices found.
Dec 30 10:24:25 WORKHORSE kernel: [    0.092733] HEST: Table not found.
Dec 30 10:24:25 WORKHORSE kernel: [    0.092746] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Dec 30 10:24:25 WORKHORSE kernel: [    0.092856] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 30 10:24:25 WORKHORSE kernel: [    0.093061] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Dec 30 10:24:25 WORKHORSE kernel: [    0.093066] pci_root PNP0A03:00: host bridge window [io  0x0d00-0x3fff] (ignored)
Dec 30 10:24:25 WORKHORSE kernel: [    0.093070] pci_root PNP0A03:00: host bridge window [io  0x4100-0x4fff] (ignored)
Dec 30 10:24:25 WORKHORSE kernel: [    0.093074] pci_root PNP0A03:00: host bridge window [io  0x5010-0xffff] (ignored)
Dec 30 10:24:25 WORKHORSE kernel: [    0.093078] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Dec 30 10:24:25 WORKHORSE kernel: [    0.093082] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
Dec 30 10:24:25 WORKHORSE kernel: [    0.093086] pci_root PNP0A03:00: host bridge window [mem 0x7e000000-0xfebfffff] (ignored)
Dec 30 10:24:25 WORKHORSE kernel: [    0.093115] pci 0000:00:00.0: [1106:3116] type 0 class 0x000600
Dec 30 10:24:25 WORKHORSE kernel: [    0.093131] pci 0000:00:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093213] pci 0000:00:01.0: [1106:b091] type 1 class 0x000604
Dec 30 10:24:25 WORKHORSE kernel: [    0.093261] pci 0000:00:01.0: supports D1
Dec 30 10:24:25 WORKHORSE kernel: [    0.093288] pci 0000:00:06.0: [10ec:8169] type 0 class 0x000200
Dec 30 10:24:25 WORKHORSE kernel: [    0.093305] pci 0000:00:06.0: reg 10: [io  0x9000-0x90ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093315] pci 0000:00:06.0: reg 14: [mem 0xd8181000-0xd81810ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093354] pci 0000:00:06.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093380] pci 0000:00:06.0: supports D1 D2
Dec 30 10:24:25 WORKHORSE kernel: [    0.093383] pci 0000:00:06.0: PME# supported from D1 D2 D3hot D3cold
Dec 30 10:24:25 WORKHORSE kernel: [    0.093390] pci 0000:00:06.0: PME# disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.093413] pci 0000:00:07.0: [1095:3512] type 0 class 0x000180
Dec 30 10:24:25 WORKHORSE kernel: [    0.093429] pci 0000:00:07.0: reg 10: [io  0x9400-0x9407]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093439] pci 0000:00:07.0: reg 14: [io  0x9800-0x9803]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093449] pci 0000:00:07.0: reg 18: [io  0x9c00-0x9c07]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093459] pci 0000:00:07.0: reg 1c: [io  0xa000-0xa003]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093469] pci 0000:00:07.0: reg 20: [io  0xa400-0xa40f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093479] pci 0000:00:07.0: reg 24: [mem 0xd8180000-0xd81801ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093489] pci 0000:00:07.0: reg 30: [mem 0x00000000-0x0007ffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093515] pci 0000:00:07.0: supports D1 D2
Dec 30 10:24:25 WORKHORSE kernel: [    0.093546] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
Dec 30 10:24:25 WORKHORSE kernel: [    0.093589] pci 0000:00:10.0: reg 20: [io  0xa800-0xa81f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093628] pci 0000:00:10.0: supports D1 D2
Dec 30 10:24:25 WORKHORSE kernel: [    0.093631] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 10:24:25 WORKHORSE kernel: [    0.093636] pci 0000:00:10.0: PME# disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.093658] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
Dec 30 10:24:25 WORKHORSE kernel: [    0.093701] pci 0000:00:10.1: reg 20: [io  0xac00-0xac1f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093740] pci 0000:00:10.1: supports D1 D2
Dec 30 10:24:25 WORKHORSE kernel: [    0.093743] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 10:24:25 WORKHORSE kernel: [    0.093748] pci 0000:00:10.1: PME# disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.093773] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
Dec 30 10:24:25 WORKHORSE kernel: [    0.093817] pci 0000:00:10.2: reg 20: [io  0xb000-0xb01f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093856] pci 0000:00:10.2: supports D1 D2
Dec 30 10:24:25 WORKHORSE kernel: [    0.093859] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 10:24:25 WORKHORSE kernel: [    0.093864] pci 0000:00:10.2: PME# disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.093885] pci 0000:00:10.3: [1106:3104] type 0 class 0x000c03
Dec 30 10:24:25 WORKHORSE kernel: [    0.093902] pci 0000:00:10.3: reg 10: [mem 0xd8182000-0xd81820ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.093968] pci 0000:00:10.3: supports D1 D2
Dec 30 10:24:25 WORKHORSE kernel: [    0.093971] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 10:24:25 WORKHORSE kernel: [    0.093976] pci 0000:00:10.3: PME# disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.094002] pci 0000:00:11.0: [1106:3177] type 0 class 0x000601
Dec 30 10:24:25 WORKHORSE kernel: [    0.094063] HPET not enabled in BIOS. You might try hpet=force boot option
Dec 30 10:24:25 WORKHORSE kernel: [    0.094079] pci 0000:00:11.0: quirk: [io  0x4000-0x407f] claimed by vt8235 PM
Dec 30 10:24:25 WORKHORSE kernel: [    0.094088] pci 0000:00:11.0: quirk: [io  0x5000-0x500f] claimed by vt8235 SMB
Dec 30 10:24:25 WORKHORSE kernel: [    0.094137] pci 0000:00:11.1: [1106:0571] type 0 class 0x000101
Dec 30 10:24:25 WORKHORSE kernel: [    0.094183] pci 0000:00:11.1: reg 20: [io  0xb400-0xb40f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094251] pci 0000:00:12.0: [1106:3065] type 0 class 0x000200
Dec 30 10:24:25 WORKHORSE kernel: [    0.094268] pci 0000:00:12.0: reg 10: [io  0xb800-0xb8ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094279] pci 0000:00:12.0: reg 14: [mem 0xd8183000-0xd81830ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094340] pci 0000:00:12.0: supports D1 D2
Dec 30 10:24:25 WORKHORSE kernel: [    0.094342] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 10:24:25 WORKHORSE kernel: [    0.094348] pci 0000:00:12.0: PME# disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.094408] pci 0000:01:00.0: [5333:8d04] type 0 class 0x000300
Dec 30 10:24:25 WORKHORSE kernel: [    0.094424] pci 0000:01:00.0: reg 10: [mem 0xd8000000-0xd807ffff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094434] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xd7ffffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094466] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094494] pci 0000:01:00.0: supports D1 D2
Dec 30 10:24:25 WORKHORSE kernel: [    0.094529] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094540] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xd80fffff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094546] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd7ffffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094555] pci_bus 0000:00: on NUMA node 0
Dec 30 10:24:25 WORKHORSE kernel: [    0.094561] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 30 10:24:25 WORKHORSE kernel: [    0.094857]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
Dec 30 10:24:25 WORKHORSE kernel: [    0.106796] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
Dec 30 10:24:25 WORKHORSE kernel: [    0.106941] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
Dec 30 10:24:25 WORKHORSE kernel: [    0.107083] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Dec 30 10:24:25 WORKHORSE kernel: [    0.107222] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Dec 30 10:24:25 WORKHORSE kernel: [    0.107352] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
Dec 30 10:24:25 WORKHORSE kernel: [    0.107471] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
Dec 30 10:24:25 WORKHORSE kernel: [    0.107613] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
Dec 30 10:24:25 WORKHORSE kernel: [    0.107733] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
Dec 30 10:24:25 WORKHORSE kernel: [    0.108057] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 30 10:24:25 WORKHORSE kernel: [    0.108068] vgaarb: loaded
Dec 30 10:24:25 WORKHORSE kernel: [    0.108073] vgaarb: bridge control possible 0000:01:00.0
Dec 30 10:24:25 WORKHORSE kernel: [    0.108298] i2c-core: driver [aat2870] using legacy suspend method
Dec 30 10:24:25 WORKHORSE kernel: [    0.108305] i2c-core: driver [aat2870] using legacy resume method
Dec 30 10:24:25 WORKHORSE kernel: [    0.108493] SCSI subsystem initialized
Dec 30 10:24:25 WORKHORSE kernel: [    0.108639] libata version 3.00 loaded.
Dec 30 10:24:25 WORKHORSE kernel: [    0.108762] usbcore: registered new interface driver usbfs
Dec 30 10:24:25 WORKHORSE kernel: [    0.108788] usbcore: registered new interface driver hub
Dec 30 10:24:25 WORKHORSE kernel: [    0.108859] usbcore: registered new device driver usb
Dec 30 10:24:25 WORKHORSE kernel: [    0.109049] PCI: Using ACPI for IRQ routing
Dec 30 10:24:25 WORKHORSE kernel: [    0.109062] PCI: pci_cache_line_size set to 32 bytes
Dec 30 10:24:25 WORKHORSE kernel: [    0.109130] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
Dec 30 10:24:25 WORKHORSE kernel: [    0.109135] reserve RAM buffer: 000000007dff0000 - 000000007fffffff 
Dec 30 10:24:25 WORKHORSE kernel: [    0.109354] NetLabel: Initializing
Dec 30 10:24:25 WORKHORSE kernel: [    0.109361] NetLabel:  domain hash size = 128
Dec 30 10:24:25 WORKHORSE kernel: [    0.109366] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 30 10:24:25 WORKHORSE kernel: [    0.109392] NetLabel:  unlabeled traffic allowed by default
Dec 30 10:24:25 WORKHORSE kernel: [    0.125795] AppArmor: AppArmor Filesystem Enabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.125909] pnp: PnP ACPI init
Dec 30 10:24:25 WORKHORSE kernel: [    0.125953] ACPI: bus type pnp registered
Dec 30 10:24:25 WORKHORSE kernel: [    0.126474] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.126572] pnp 00:01: [bus 00-ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126577] pnp 00:01: [io  0x0cf8-0x0cff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126581] pnp 00:01: [io  0x0000-0x0cf7 window]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126585] pnp 00:01: [io  0x0d00-0x3fff window]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126588] pnp 00:01: [io  0x4000-0x407f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126591] pnp 00:01: [io  0x4080-0x40ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126594] pnp 00:01: [io  0x4100-0x4fff window]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126597] pnp 00:01: [io  0x5000-0x500f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126600] pnp 00:01: [io  0x5010-0xffff window]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126604] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126607] pnp 00:01: [mem 0x000c0000-0x000dffff window]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126611] pnp 00:01: [mem 0x7e000000-0xfebfffff window]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126697] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.126958] pnp 00:02: [io  0x0010-0x001f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126963] pnp 00:02: [io  0x0022-0x003f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126966] pnp 00:02: [io  0x0044-0x005f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126969] pnp 00:02: [io  0x0062-0x0063]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126972] pnp 00:02: [io  0x0065-0x006f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126975] pnp 00:02: [io  0x0074-0x007f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126978] pnp 00:02: [io  0x0091-0x0093]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126981] pnp 00:02: [io  0x00a2-0x00bf]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126984] pnp 00:02: [io  0x00e0-0x00ef]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126987] pnp 00:02: [io  0x04d0-0x04d1]
Dec 30 10:24:25 WORKHORSE kernel: [    0.126990] pnp 00:02: [io  0x0294-0x0297]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127063] system 00:02: [io  0x04d0-0x04d1] has been reserved
Dec 30 10:24:25 WORKHORSE kernel: [    0.127073] system 00:02: [io  0x0294-0x0297] has been reserved
Dec 30 10:24:25 WORKHORSE kernel: [    0.127081] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.127102] pnp 00:03: [dma 4]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127106] pnp 00:03: [io  0x0000-0x000f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127109] pnp 00:03: [io  0x0080-0x0090]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127112] pnp 00:03: [io  0x0094-0x009f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127115] pnp 00:03: [io  0x00c0-0x00df]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127161] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.127178] pnp 00:04: [io  0x0070-0x0073]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127205] pnp 00:04: [irq 8]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127259] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.127274] pnp 00:05: [io  0x0061]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127320] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.127335] pnp 00:06: [io  0x00f0-0x00ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127343] pnp 00:06: [irq 13]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127400] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.127551] pnp 00:07: [io  0x03f2-0x03f5]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127566] pnp 00:07: [io  0x03f7]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127573] pnp 00:07: [irq 6]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127577] pnp 00:07: [dma 2]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127648] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.127856] pnp 00:08: [io  0x03f8-0x03ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127864] pnp 00:08: [irq 4]
Dec 30 10:24:25 WORKHORSE kernel: [    0.127956] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.128227] pnp 00:09: [io  0x02f8-0x02ff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.128236] pnp 00:09: [irq 3]
Dec 30 10:24:25 WORKHORSE kernel: [    0.128339] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.128778] pnp 00:0a: [io  0x0378-0x037f]
Dec 30 10:24:25 WORKHORSE kernel: [    0.128783] pnp 00:0a: [io  0x0778-0x077b]
Dec 30 10:24:25 WORKHORSE kernel: [    0.128790] pnp 00:0a: [irq 7]
Dec 30 10:24:25 WORKHORSE kernel: [    0.128793] pnp 00:0a: [dma 3]
Dec 30 10:24:25 WORKHORSE kernel: [    0.128890] pnp 00:0a: Plug and Play ACPI device, IDs PNP0401 (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.128947] pnp 00:0b: [io  0x0060]
Dec 30 10:24:25 WORKHORSE kernel: [    0.128951] pnp 00:0b: [io  0x0064]
Dec 30 10:24:25 WORKHORSE kernel: [    0.128958] pnp 00:0b: [irq 1]
Dec 30 10:24:25 WORKHORSE kernel: [    0.129017] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Dec 30 10:24:25 WORKHORSE kernel: [    0.129053] pnp: PnP ACPI: found 12 devices
Dec 30 10:24:25 WORKHORSE kernel: [    0.129061] ACPI: ACPI bus type pnp unregistered
Dec 30 10:24:25 WORKHORSE kernel: [    0.129072] PnPBIOS: Disabled by ACPI PNP
Dec 30 10:24:25 WORKHORSE kernel: [    0.167050] Switching to clocksource acpi_pm
Dec 30 10:24:25 WORKHORSE kernel: [    0.167117] PCI: max bus depth: 1 pci_try_num: 2
Dec 30 10:24:25 WORKHORSE kernel: [    0.167171] pci 0000:00:07.0: BAR 6: assigned [mem 0x80000000-0x8007ffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167185] pci 0000:00:06.0: BAR 6: assigned [mem 0x80080000-0x8009ffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167196] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8080000-0xd808ffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167205] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167217] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xd80fffff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167226] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd7ffffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167252] pci 0000:00:01.0: setting latency timer to 64
Dec 30 10:24:25 WORKHORSE kernel: [    0.167259] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167263] pci_bus 0000:00: resource 1 [mem 0x00000000-0x3ffffffff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167267] pci_bus 0000:01: resource 1 [mem 0xd8000000-0xd80fffff]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167271] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd7ffffff pref]
Dec 30 10:24:25 WORKHORSE kernel: [    0.167399] NET: Registered protocol family 2
Dec 30 10:24:25 WORKHORSE kernel: [    0.167542] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.167542] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.168394] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.169875] TCP: Hash tables configured (established 131072 bind 65536)
Dec 30 10:24:25 WORKHORSE kernel: [    0.169898] TCP reno registered
Dec 30 10:24:25 WORKHORSE kernel: [    0.169909] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.169960] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.170197] NET: Registered protocol family 1
Dec 30 10:24:25 WORKHORSE kernel: [    0.170235] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Dec 30 10:24:25 WORKHORSE kernel: [    0.170619] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.170629] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.170667] pci 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.170694] pci 0000:00:10.0: PCI INT A disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.170712] pci 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.170733] pci 0000:00:10.1: PCI INT B disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.170750] pci 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.170771] pci 0000:00:10.2: PCI INT C disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.170788] pci 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.170846] pci 0000:00:10.3: PCI INT D disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.170867] pci 0000:01:00.0: Boot video device
Dec 30 10:24:25 WORKHORSE kernel: [    0.170872] PCI: CLS 32 bytes, default 32
Dec 30 10:24:25 WORKHORSE kernel: [    0.171640] audit: initializing netlink socket (disabled)
Dec 30 10:24:25 WORKHORSE kernel: [    0.171670] type=2000 audit(1356881056.164:1): initialized
Dec 30 10:24:25 WORKHORSE kernel: [    0.201884] Trying to unpack rootfs image as initramfs...
Dec 30 10:24:25 WORKHORSE kernel: [    0.237361] highmem bounce pool size: 64 pages
Dec 30 10:24:25 WORKHORSE kernel: [    0.237395] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 30 10:24:25 WORKHORSE kernel: [    0.248387] VFS: Disk quotas dquot_6.5.2
Dec 30 10:24:25 WORKHORSE kernel: [    0.248528] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 30 10:24:25 WORKHORSE kernel: [    0.249630] fuse init (API version 7.17)
Dec 30 10:24:25 WORKHORSE kernel: [    0.249798] msgmni has been set to 1686
Dec 30 10:24:25 WORKHORSE kernel: [    0.260522] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 30 10:24:25 WORKHORSE kernel: [    0.264255] io scheduler noop registered
Dec 30 10:24:25 WORKHORSE kernel: [    0.264285] io scheduler deadline registered
Dec 30 10:24:25 WORKHORSE kernel: [    0.264346] io scheduler cfq registered (default)
Dec 30 10:24:25 WORKHORSE kernel: [    0.264670] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 30 10:24:25 WORKHORSE kernel: [    0.264732] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 30 10:24:25 WORKHORSE kernel: [    0.265019] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Dec 30 10:24:25 WORKHORSE kernel: [    0.265039] ACPI: Power Button [PWRB]
Dec 30 10:24:25 WORKHORSE kernel: [    0.265128] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Dec 30 10:24:25 WORKHORSE kernel: [    0.265141] ACPI: Sleep Button [SLPB]
Dec 30 10:24:25 WORKHORSE kernel: [    0.265216] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Dec 30 10:24:25 WORKHORSE kernel: [    0.265227] ACPI: Power Button [PWRF]
Dec 30 10:24:25 WORKHORSE kernel: [    0.265328] ACPI: Fan [FAN] (on)
Dec 30 10:24:25 WORKHORSE kernel: [    0.265400] Marking TSC unstable due to TSC halts in idle
Dec 30 10:24:25 WORKHORSE kernel: [    0.265418] ACPI: acpi_idle registered with cpuidle
Dec 30 10:24:25 WORKHORSE kernel: [    0.267454] thermal LNXTHERM:00: registered as thermal_zone0
Dec 30 10:24:25 WORKHORSE kernel: [    0.267463] ACPI: Thermal Zone [THRM] (51 C)
Dec 30 10:24:25 WORKHORSE kernel: [    0.267520] ERST: Table is not found!
Dec 30 10:24:25 WORKHORSE kernel: [    0.267526] GHES: HEST is not enabled!
Dec 30 10:24:25 WORKHORSE kernel: [    0.267878] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.288348] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 30 10:24:25 WORKHORSE kernel: [    0.288402] isapnp: Scanning for PnP cards...
Dec 30 10:24:25 WORKHORSE kernel: [    0.380936] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 30 10:24:25 WORKHORSE kernel: [    0.422518] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 30 10:24:25 WORKHORSE kernel: [    0.508912] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 30 10:24:25 WORKHORSE kernel: [    0.528687] Linux agpgart interface v0.103
Dec 30 10:24:25 WORKHORSE kernel: [    0.528828] agpgart: Detected VIA PM266/KM266 chipset
Dec 30 10:24:25 WORKHORSE kernel: [    0.616704] agpgart-via 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Dec 30 10:24:25 WORKHORSE kernel: [    0.619341] brd: module loaded
Dec 30 10:24:25 WORKHORSE kernel: [    0.625139] loop: module loaded
Dec 30 10:24:25 WORKHORSE kernel: [    0.625965] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Dec 30 10:24:25 WORKHORSE kernel: [    0.625976] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Dec 30 10:24:25 WORKHORSE kernel: [    0.626014] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Dec 30 10:24:25 WORKHORSE kernel: [    0.626156] pata_acpi 0000:00:11.1: PCI INT A disabled
Dec 30 10:24:25 WORKHORSE kernel: [    0.626837] Fixed MDIO Bus: probed
Dec 30 10:24:25 WORKHORSE kernel: [    0.626879] tun: Universal TUN/TAP device driver, 1.6
Dec 30 10:24:25 WORKHORSE kernel: [    0.626885] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 30 10:24:25 WORKHORSE kernel: [    0.627051] PPP generic driver version 2.4.2
Dec 30 10:24:25 WORKHORSE kernel: [    0.627271] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 30 10:24:25 WORKHORSE kernel: [    0.627309] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.627356] ehci_hcd 0000:00:10.3: EHCI Host Controller
Dec 30 10:24:25 WORKHORSE kernel: [    0.627443] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
Dec 30 10:24:25 WORKHORSE kernel: [    0.627550] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd8182000
Dec 30 10:24:25 WORKHORSE kernel: [    0.636406] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
Dec 30 10:24:25 WORKHORSE kernel: [    0.636835] hub 1-0:1.0: USB hub found
Dec 30 10:24:25 WORKHORSE kernel: [    0.636850] hub 1-0:1.0: 6 ports detected
Dec 30 10:24:25 WORKHORSE kernel: [    0.637013] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 30 10:24:25 WORKHORSE kernel: [    0.637054] uhci_hcd: USB Universal Host Controller Interface driver
Dec 30 10:24:25 WORKHORSE kernel: [    0.637142] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.637171] uhci_hcd 0000:00:10.0: UHCI Host Controller
Dec 30 10:24:25 WORKHORSE kernel: [    0.637271] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Dec 30 10:24:25 WORKHORSE kernel: [    0.637321] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000a800
Dec 30 10:24:25 WORKHORSE kernel: [    0.637577] hub 2-0:1.0: USB hub found
Dec 30 10:24:25 WORKHORSE kernel: [    0.637589] hub 2-0:1.0: 2 ports detected
Dec 30 10:24:25 WORKHORSE kernel: [    0.637683] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.637701] uhci_hcd 0000:00:10.1: UHCI Host Controller
Dec 30 10:24:25 WORKHORSE kernel: [    0.637777] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Dec 30 10:24:25 WORKHORSE kernel: [    0.637816] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000ac00
Dec 30 10:24:25 WORKHORSE kernel: [    0.638061] hub 3-0:1.0: USB hub found
Dec 30 10:24:25 WORKHORSE kernel: [    0.638072] hub 3-0:1.0: 2 ports detected
Dec 30 10:24:25 WORKHORSE kernel: [    0.638163] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 10:24:25 WORKHORSE kernel: [    0.638181] uhci_hcd 0000:00:10.2: UHCI Host Controller
Dec 30 10:24:25 WORKHORSE kernel: [    0.638254] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Dec 30 10:24:25 WORKHORSE kernel: [    0.638285] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b000
Dec 30 10:24:25 WORKHORSE kernel: [    0.638517] hub 4-0:1.0: USB hub found
Dec 30 10:24:25 WORKHORSE kernel: [    0.638528] hub 4-0:1.0: 2 ports detected
Dec 30 10:24:25 WORKHORSE kernel: [    0.638717] usbcore: registered new interface driver libusual
Dec 30 10:24:25 WORKHORSE kernel: [    0.638811] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Dec 30 10:24:25 WORKHORSE kernel: [    0.638819] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Dec 30 10:24:25 WORKHORSE kernel: [    0.639055] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 30 10:24:25 WORKHORSE kernel: [    0.639267] mousedev: PS/2 mouse device common for all mice
Dec 30 10:24:25 WORKHORSE kernel: [    0.644675] rtc_cmos 00:04: RTC can wake from S4
Dec 30 10:24:25 WORKHORSE kernel: [    0.644889] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Dec 30 10:24:25 WORKHORSE kernel: [    0.644941] rtc0: alarms up to one year, y3k, 242 bytes nvram
Dec 30 10:24:25 WORKHORSE kernel: [    0.645091] device-mapper: uevent: version 1.0.3
Dec 30 10:24:25 WORKHORSE kernel: [    0.645226] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Dec 30 10:24:25 WORKHORSE kernel: [    0.645325] EISA: Probing bus 0 at eisa.0
Dec 30 10:24:25 WORKHORSE kernel: [    0.645364] Cannot allocate resource for EISA slot 4
Dec 30 10:24:25 WORKHORSE kernel: [    0.645371] Cannot allocate resource for EISA slot 5
Dec 30 10:24:25 WORKHORSE kernel: [    0.645390] EISA: Detected 0 cards.
Dec 30 10:24:25 WORKHORSE kernel: [    0.645415] cpufreq-nforce2: No nForce2 chipset.
Dec 30 10:24:25 WORKHORSE kernel: [    0.645478] cpuidle: using governor ladder
Dec 30 10:24:25 WORKHORSE kernel: [    0.645553] cpuidle: using governor menu
Dec 30 10:24:25 WORKHORSE kernel: [    0.645559] EFI Variables Facility v0.08 2004-May-17
Dec 30 10:24:25 WORKHORSE kernel: [    0.645933] TCP cubic registered
Dec 30 10:24:25 WORKHORSE kernel: [    0.646186] NET: Registered protocol family 10
Dec 30 10:24:25 WORKHORSE kernel: [    0.647040] NET: Registered protocol family 17
Dec 30 10:24:25 WORKHORSE kernel: [    0.647053] Registering the dns_resolver key type
Dec 30 10:24:25 WORKHORSE kernel: [    0.647108] Using IPI No-Shortcut mode
Dec 30 10:24:25 WORKHORSE kernel: [    0.647349] PM: Hibernation image not present or could not be loaded.
Dec 30 10:24:25 WORKHORSE kernel: [    0.647375] registered taskstats version 1
Dec 30 10:24:25 WORKHORSE kernel: [    0.787577] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Dec 30 10:24:25 WORKHORSE kernel: [    0.971649] isapnp: No Plug & Play device found
Dec 30 10:24:25 WORKHORSE kernel: [    1.183393] Freeing initrd memory: 13836k freed
Dec 30 10:24:25 WORKHORSE kernel: [    1.234566]   Magic number: 8:258:438
Dec 30 10:24:25 WORKHORSE kernel: [    1.234819] rtc_cmos 00:04: setting system clock to 2012-12-30 15:24:17 UTC (1356881057)
Dec 30 10:24:25 WORKHORSE kernel: [    1.234831] powernow-k8: Processor cpuid 681 not supported
Dec 30 10:24:25 WORKHORSE kernel: [    1.234874] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 30 10:24:25 WORKHORSE kernel: [    1.234880] EDD information not available.
Dec 30 10:24:25 WORKHORSE kernel: [    1.235221] Freeing unused kernel memory: 744k freed
Dec 30 10:24:25 WORKHORSE kernel: [    1.237209] Write protecting the kernel text: 5828k
Dec 30 10:24:25 WORKHORSE kernel: [    1.237255] Write protecting the kernel read-only data: 2380k
Dec 30 10:24:25 WORKHORSE kernel: [    1.552861] Floppy drive(s): fd0 is 1.44M
Dec 30 10:24:25 WORKHORSE kernel: [    1.572101] FDC 0 is a post-1991 82077
Dec 30 10:24:25 WORKHORSE kernel: [    1.610167] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 30 10:24:25 WORKHORSE kernel: [    1.610256] r8169 0000:00:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 30 10:24:25 WORKHORSE kernel: [    1.610283] r8169 0000:00:06.0: PCI: Disallowing DAC for device
Dec 30 10:24:25 WORKHORSE kernel: [    1.610314] r8169 0000:00:06.0: (unregistered net_device): not PCI Express
Dec 30 10:24:25 WORKHORSE kernel: [    1.611135] r8169 0000:00:06.0: eth0: RTL8169sb/8110sb at 0xf840c000, 00:e0:52:bf:66:4a, XID 10000000 IRQ 17
Dec 30 10:24:25 WORKHORSE kernel: [    1.611149] r8169 0000:00:06.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec 30 10:24:25 WORKHORSE kernel: [    1.631026] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
Dec 30 10:24:25 WORKHORSE kernel: [    1.631053] via_rhine: Broken BIOS detected, avoid_D3 enabled
Dec 30 10:24:25 WORKHORSE kernel: [    1.644573] sata_sil 0000:00:07.0: version 2.4
Dec 30 10:24:25 WORKHORSE kernel: [    1.644714] sata_sil 0000:00:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 30 10:24:25 WORKHORSE kernel: [    1.650112] scsi0 : sata_sil
Dec 30 10:24:25 WORKHORSE kernel: [    1.654501] scsi1 : sata_sil
Dec 30 10:24:25 WORKHORSE kernel: [    1.654672] ata1: SATA max UDMA/100 mmio m512@0xd8180000 tf 0xd8180080 irq 18
Dec 30 10:24:25 WORKHORSE kernel: [    1.654682] ata2: SATA max UDMA/100 mmio m512@0xd8180000 tf 0xd81800c0 irq 18
Dec 30 10:24:25 WORKHORSE kernel: [    1.655865] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
Dec 30 10:24:25 WORKHORSE kernel: [    1.655887] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Dec 30 10:24:25 WORKHORSE kernel: [    1.655931] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
Dec 30 10:24:25 WORKHORSE kernel: [    1.678689] via-rhine 0000:00:12.0: eth1: VIA Rhine II at 0xd8183000, 00:10:dc:fe:ef:7b, IRQ 23
Dec 30 10:24:25 WORKHORSE kernel: [    1.679425] via-rhine 0000:00:12.0: eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000
Dec 30 10:24:25 WORKHORSE kernel: [    1.679486] pata_via 0000:00:11.1: version 0.3.4
Dec 30 10:24:25 WORKHORSE kernel: [    1.679523] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Dec 30 10:24:25 WORKHORSE kernel: [    1.683706] scsi2 : pata_via
Dec 30 10:24:25 WORKHORSE kernel: [    1.687469] scsi3 : pata_via
Dec 30 10:24:25 WORKHORSE kernel: [    1.689829] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xb400 irq 14
Dec 30 10:24:25 WORKHORSE kernel: [    1.689840] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xb408 irq 15
Dec 30 10:24:25 WORKHORSE kernel: [    1.972060] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 30 10:24:25 WORKHORSE kernel: [    1.980201] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S223L, SB02, max UDMA/100
Dec 30 10:24:25 WORKHORSE kernel: [    1.996183] ata1.00: configured for UDMA/100
Dec 30 10:24:25 WORKHORSE kernel: [    1.997317] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223L  SB02 PQ: 0 ANSI: 5
Dec 30 10:24:25 WORKHORSE kernel: [    2.001272] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 30 10:24:25 WORKHORSE kernel: [    2.001290] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 30 10:24:25 WORKHORSE kernel: [    2.002170] sr 0:0:0:0: Attached scsi CD-ROM sr0
Dec 30 10:24:25 WORKHORSE kernel: [    2.002605] sr 0:0:0:0: Attached scsi generic sg0 type 5
Dec 30 10:24:25 WORKHORSE kernel: [    2.320055] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 30 10:24:25 WORKHORSE kernel: [    2.328308] ata2.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
Dec 30 10:24:25 WORKHORSE kernel: [    2.328317] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 30 10:24:25 WORKHORSE kernel: [    2.336292] ata2.00: configured for UDMA/100
Dec 30 10:24:25 WORKHORSE kernel: [    2.336535] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Dec 30 10:24:25 WORKHORSE kernel: [    2.336906] sd 1:0:0:0: Attached scsi generic sg1 type 0
Dec 30 10:24:25 WORKHORSE kernel: [    2.337210] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 30 10:24:25 WORKHORSE kernel: [    2.337307] sd 1:0:0:0: [sda] Write Protect is off
Dec 30 10:24:25 WORKHORSE kernel: [    2.337316] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 30 10:24:25 WORKHORSE kernel: [    2.337355] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 30 10:24:25 WORKHORSE kernel: [    2.384729]  sda: sda1 sda2 < sda5 sda6 sda7 >
Dec 30 10:24:25 WORKHORSE kernel: [    2.385915] sd 1:0:0:0: [sda] Attached SCSI disk
Dec 30 10:24:25 WORKHORSE kernel: [    2.971575] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Dec 30 10:24:25 WORKHORSE kernel: [    6.547595] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 30 10:24:25 WORKHORSE kernel: [    6.547611] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 30 10:24:25 WORKHORSE kernel: [    6.671406] Adding 3905532k swap on /dev/sda5.  Priority:-1 extents:1 across:3905532k 
Dec 30 10:24:25 WORKHORSE kernel: [    6.703758] lp: driver loaded but no devices found
Dec 30 10:24:25 WORKHORSE kernel: [    7.125903] parport_pc 00:0a: reported by Plug and Play ACPI
Dec 30 10:24:25 WORKHORSE kernel: [    7.126029] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Dec 30 10:24:25 WORKHORSE kernel: [    7.208645] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Dec 30 10:24:25 WORKHORSE kernel: [    7.212580] lp0: using parport0 (interrupt-driven).
Dec 30 10:24:25 WORKHORSE kernel: [    7.344704] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 30 10:24:25 WORKHORSE kernel: [    7.580661] type=1400 audit(1356881063.841:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=391 comm="apparmor_parser"
Dec 30 10:24:25 WORKHORSE kernel: [    7.585096] type=1400 audit(1356881063.845:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=391 comm="apparmor_parser"
Dec 30 10:24:25 WORKHORSE kernel: [    7.585489] type=1400 audit(1356881063.845:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=391 comm="apparmor_parser"
Dec 30 10:24:25 WORKHORSE kernel: [    7.844495] r8169 0000:00:06.0: eth0: link down
Dec 30 10:24:25 WORKHORSE kernel: [    7.844508] r8169 0000:00:06.0: eth0: link down
Dec 30 10:24:25 WORKHORSE kernel: [    7.854031] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Dec 30 10:24:25 WORKHORSE kernel: [    7.854939] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 30 10:24:25 WORKHORSE kernel: [    7.876320] irda_init()
Dec 30 10:24:25 WORKHORSE kernel: [    7.876370] NET: Registered protocol family 23
Dec 30 10:24:25 WORKHORSE kernel: [    8.454985] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Dec 30 10:24:25 WORKHORSE failsafe: Failsafe of 120 seconds reached.
Dec 30 10:24:26 WORKHORSE kernel: [    9.810054] ppdev: user-space parallel port driver
Dec 30 10:24:26 WORKHORSE kernel: [    9.908575] vesafb: mode is 640x480x32, linelength=2560, pages=0
Dec 30 10:24:26 WORKHORSE kernel: [    9.908582] vesafb: scrolling: redraw
Dec 30 10:24:26 WORKHORSE kernel: [    9.908588] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Dec 30 10:24:26 WORKHORSE kernel: [    9.909463] vesafb: framebuffer at 0xd0000000, mapped to 0xf8600000, using 1216k, total 1216k
Dec 30 10:24:26 WORKHORSE kernel: [    9.910865] Console: switching to colour frame buffer device 80x30
Dec 30 10:24:26 WORKHORSE kernel: [    9.918926] fb0: VESA VGA frame buffer device
Dec 30 10:24:27 WORKHORSE dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 30 10:24:27 WORKHORSE kernel: [   11.309793] r8169 0000:00:06.0: eth0: link up
Dec 30 10:24:27 WORKHORSE kernel: [   11.310176] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 30 10:24:35 WORKHORSE dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 30 10:24:35 WORKHORSE dhclient: DHCPREQUEST of 192.168.1.140 on eth0 to 255.255.255.255 port 67
Dec 30 10:24:35 WORKHORSE dhclient: DHCPOFFER of 192.168.1.140 from 192.168.1.1
Dec 30 10:24:35 WORKHORSE dhclient: DHCPACK of 192.168.1.140 from 192.168.1.1
Dec 30 10:24:35 WORKHORSE dhclient: bound to 192.168.1.140 -- renewal in 40368 seconds.
Dec 30 10:24:35 WORKHORSE kernel: [   19.554368] init: failsafe main process (586) killed by TERM signal
Dec 30 10:24:35 WORKHORSE kernel: [   19.659022] type=1400 audit(1356881075.917:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=879 comm="apparmor_parser"
Dec 30 10:24:35 WORKHORSE kernel: [   19.659926] type=1400 audit(1356881075.917:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=879 comm="apparmor_parser"
Dec 30 10:24:35 WORKHORSE kernel: [   19.660965] type=1400 audit(1356881075.921:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=879 comm="apparmor_parser"
Dec 30 10:24:35 WORKHORSE kernel: [   19.671025] type=1400 audit(1356881075.929:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=881 comm="apparmor_parser"
Dec 30 10:24:36 WORKHORSE acpid: starting up with proc fs
Dec 30 10:24:36 WORKHORSE acpid: 1 rule loaded
Dec 30 10:24:36 WORKHORSE acpid: waiting for events: event logging is off
Dec 30 10:24:36 WORKHORSE cron[914]: (CRON) INFO (pidfile fd = 3)
Dec 30 10:24:36 WORKHORSE cron[934]: (CRON) STARTUP (fork ok)
Dec 30 10:24:36 WORKHORSE cron[934]: (CRON) INFO (Running @reboot jobs)
Dec 30 10:24:37 WORKHORSE kernel: [   21.504034] eth0: no IPv6 routers present
Dec 30 11:28:58 WORKHORSE ntpdate[782]: step time server 91.189.94.4 offset 3854.724801 sec


```

Since the above looked very much like a reboot to my untrained eyes, I thought I should do an actual reboot and see what the log looks like then. The log from the intentional reboot is inlined below.

```

Dec 30 19:17:01 WORKHORSE CRON[2155]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 30 19:26:38 WORKHORSE kernel: Kernel logging (proc) stopped.
Dec 30 19:26:38 WORKHORSE rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="528" x-info="http://www.rsyslog.com"] exiting on signal 15.
Dec 30 19:27:27 WORKHORSE kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec 30 19:27:27 WORKHORSE rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="508" x-info="http://www.rsyslog.com"] start
Dec 30 19:27:27 WORKHORSE rsyslogd: rsyslogd's groupid changed to 103
Dec 30 19:27:27 WORKHORSE rsyslogd: rsyslogd's userid changed to 101
Dec 30 19:27:27 WORKHORSE rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Linux version 3.2.0-35-generic-pae (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #55-Ubuntu SMP Wed Dec 5 18:04:39 UTC 2012 (Ubuntu 3.2.0-35.55-generic-pae 3.2.34)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] KERNEL supported cpus:
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   Intel GenuineIntel
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   AMD AuthenticAMD
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   NSC Geode by NSC
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   Cyrix CyrixInstead
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   Centaur CentaurHauls
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   Transmeta GenuineTMx86
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   Transmeta TransmetaCPU
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   UMC UMC UMC UMC
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007dff0000 (usable)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 000000007dff0000 - 000000007dff3000 (ACPI NVS)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 000000007dff3000 - 000000007e000000 (ACPI data)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] DMI 2.2 present.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] DMI: MICRO-STAR INTERNATIONAL CO., LTD KM266-8235/MS-6738, BIOS 6.00 PG 03/18/2003
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] last_pfn = 0x7dff0 max_arch_pfn = 0x1000000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] MTRR default type: uncachable
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   00000-9FFFF write-back
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   C0000-C7FFF write-protect
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   C8000-FFFFF uncachable
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] MTRR variable ranges enabled:
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   1 base 07E000000 mask FFE000000 uncachable
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   2 base 0C0000000 mask FF0000000 write-combining
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   3 base 0C0000000 mask FF0000000 write-combining
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   4 disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   5 disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   6 disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   7 disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] found SMP MP-table at [c00f6740] f6740
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] initial memory mapped : 0 - 02000000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] RAMDISK: 364ea000 - 3726d000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: RSDP 000f8240 00014 (v00 VT8375)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: RSDT 7dff3000 0002C (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: FACP 7dff3040 00074 (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: DSDT 7dff30c0 039ED (v01 VT8375 AWRDACPI 00001000 MSFT 0100000D)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: FACS 7dff0000 00040
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: APIC 7dff6ac0 0005A (v01 VT8375 AWRDACPI 42302E31 AWRD 00000000)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] 1123MB HIGHMEM available.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] 891MB LOWMEM available.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   low ram: 0 - 37bfe000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Zone PFN ranges:
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   HighMem  0x00037bfe -> 0x0007dff0
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Movable zone start PFN for each node
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]     0: 0x00000100 -> 0x0007dff0
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] On node 0 totalpages: 515967
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] free_area_init_node: node 0, pgdat c186b1c0, node_mem_map f552a200
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   HighMem zone: 2248 pages used for memmap
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]   HighMem zone: 285482 pages, LIFO batch:31
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Using APIC driver default
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] nr_irqs_gsi: 40
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Allocating PCI resources starting at 7e000000 (gap: 7e000000:80c00000)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f7be3000 s34240 r0 d23104 u57344
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] pcpu-alloc: [0] 0 
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 511935
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-35-generic-pae root=UUID=98b2c29d-b319-4b35-8843-87dedb2051d4 ro
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Initializing CPU#0
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] allocated 8257024 bytes of page_cgroup
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0007dff0)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Memory: 2014552k/2064320k available (5825k kernel code, 49316k reserved, 2849k data, 744k init, 1150920k highmem)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] virtual kernel memory layout:
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]       .init : 0xc1879000 - 0xc1933000   ( 744 kB)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]       .data : 0xc15b05bc - 0xc1878a00   (2849 kB)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000]       .text : 0xc1000000 - 0xc15b05bc   (5825 kB)
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Hierarchical RCU implementation.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] NR_IRQS:2304 nr_irqs:256 16
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Console: colour dummy device 80x25
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] console [tty0] enabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Fast TSC calibration using PIT
Dec 30 19:27:27 WORKHORSE kernel: [    0.000000] Detected 1799.653 MHz processor.
Dec 30 19:27:27 WORKHORSE kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3599.30 BogoMIPS (lpj=7198612)
Dec 30 19:27:27 WORKHORSE kernel: [    0.004025] pid_max: default: 32768 minimum: 301
Dec 30 19:27:27 WORKHORSE kernel: [    0.004081] Security Framework initialized
Dec 30 19:27:27 WORKHORSE kernel: [    0.004152] AppArmor: AppArmor initialized
Dec 30 19:27:27 WORKHORSE kernel: [    0.004160] Yama: becoming mindful.
Dec 30 19:27:27 WORKHORSE kernel: [    0.004293] Mount-cache hash table entries: 512
Dec 30 19:27:27 WORKHORSE kernel: [    0.004619] Initializing cgroup subsys cpuacct
Dec 30 19:27:27 WORKHORSE kernel: [    0.004636] Initializing cgroup subsys memory
Dec 30 19:27:27 WORKHORSE kernel: [    0.004658] Initializing cgroup subsys devices
Dec 30 19:27:27 WORKHORSE kernel: [    0.004667] Initializing cgroup subsys freezer
Dec 30 19:27:27 WORKHORSE kernel: [    0.004676] Initializing cgroup subsys blkio
Dec 30 19:27:27 WORKHORSE kernel: [    0.004694] Initializing cgroup subsys perf_event
Dec 30 19:27:27 WORKHORSE kernel: [    0.004743] CPU: CLK_CTL MSR was 60031223. Reprogramming to 20031223
Dec 30 19:27:27 WORKHORSE kernel: [    0.004760] mce: CPU supports 4 MCE banks
Dec 30 19:27:27 WORKHORSE kernel: [    0.004894] SMP alternatives: switching to UP code
Dec 30 19:27:27 WORKHORSE kernel: [    0.017952] Freeing SMP alternatives: 24k freed
Dec 30 19:27:27 WORKHORSE kernel: [    0.018039] ACPI: Core revision 20110623
Dec 30 19:27:27 WORKHORSE kernel: [    0.023419] ftrace: allocating 26576 entries in 53 pages
Dec 30 19:27:27 WORKHORSE kernel: [    0.028231] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 30 19:27:27 WORKHORSE kernel: [    0.028727] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 30 19:27:27 WORKHORSE kernel: [    0.071615] CPU0: AMD Athlon(tm) XP 2200+ stepping 01
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] Performance Events: AMD PMU driver.
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] ... version:                0
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] ... bit width:              48
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] ... generic registers:      4
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] ... value mask:             0000ffffffffffff
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] ... max period:             00007fffffffffff
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] ... fixed-purpose events:   0
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] ... event mask:             000000000000000f
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] Brought up 1 CPUs
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] Total of 1 processors activated (3599.30 BogoMIPS).
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] devtmpfs: initialized
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] EVM: security.selinux
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] EVM: security.SMACK64
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] EVM: security.capability
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] PM: Registering ACPI NVS region at 7dff0000 (12288 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] print_constraints: dummy: 
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] RTC time:  0:27:18, date: 12/31/12
Dec 30 19:27:27 WORKHORSE kernel: [    0.072003] NET: Registered protocol family 16
Dec 30 19:27:27 WORKHORSE kernel: [    0.072267] EISA bus registered
Dec 30 19:27:27 WORKHORSE kernel: [    0.072293] ACPI: bus type pci registered
Dec 30 19:27:27 WORKHORSE kernel: [    0.080905] PCI: PCI BIOS revision 2.10 entry at 0xfbd20, last bus=1
Dec 30 19:27:27 WORKHORSE kernel: [    0.080913] PCI: Using configuration type 1 for base access
Dec 30 19:27:27 WORKHORSE kernel: [    0.083075] bio: create slab <bio-0> at 0
Dec 30 19:27:27 WORKHORSE kernel: [    0.083271] ACPI: Added _OSI(Module Device)
Dec 30 19:27:27 WORKHORSE kernel: [    0.083278] ACPI: Added _OSI(Processor Device)
Dec 30 19:27:27 WORKHORSE kernel: [    0.083285] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 30 19:27:27 WORKHORSE kernel: [    0.083291] ACPI: Added _OSI(Processor Aggregator Device)
Dec 30 19:27:27 WORKHORSE kernel: [    0.084044] ACPI: EC: Look up EC in DSDT
Dec 30 19:27:27 WORKHORSE kernel: [    0.087872] ACPI: Interpreter enabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.087894] ACPI: (supports S0 S1 S4 S5)
Dec 30 19:27:27 WORKHORSE kernel: [    0.087928] ACPI: Using IOAPIC for interrupt routing
Dec 30 19:27:27 WORKHORSE kernel: [    0.092706] ACPI: No dock devices found.
Dec 30 19:27:27 WORKHORSE kernel: [    0.092727] HEST: Table not found.
Dec 30 19:27:27 WORKHORSE kernel: [    0.092739] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Dec 30 19:27:27 WORKHORSE kernel: [    0.092849] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 30 19:27:27 WORKHORSE kernel: [    0.093053] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Dec 30 19:27:27 WORKHORSE kernel: [    0.093058] pci_root PNP0A03:00: host bridge window [io  0x0d00-0x3fff] (ignored)
Dec 30 19:27:27 WORKHORSE kernel: [    0.093062] pci_root PNP0A03:00: host bridge window [io  0x4100-0x4fff] (ignored)
Dec 30 19:27:27 WORKHORSE kernel: [    0.093066] pci_root PNP0A03:00: host bridge window [io  0x5010-0xffff] (ignored)
Dec 30 19:27:27 WORKHORSE kernel: [    0.093070] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Dec 30 19:27:27 WORKHORSE kernel: [    0.093074] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
Dec 30 19:27:27 WORKHORSE kernel: [    0.093078] pci_root PNP0A03:00: host bridge window [mem 0x7e000000-0xfebfffff] (ignored)
Dec 30 19:27:27 WORKHORSE kernel: [    0.093106] pci 0000:00:00.0: [1106:3116] type 0 class 0x000600
Dec 30 19:27:27 WORKHORSE kernel: [    0.093122] pci 0000:00:00.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093205] pci 0000:00:01.0: [1106:b091] type 1 class 0x000604
Dec 30 19:27:27 WORKHORSE kernel: [    0.093253] pci 0000:00:01.0: supports D1
Dec 30 19:27:27 WORKHORSE kernel: [    0.093279] pci 0000:00:06.0: [10ec:8169] type 0 class 0x000200
Dec 30 19:27:27 WORKHORSE kernel: [    0.093296] pci 0000:00:06.0: reg 10: [io  0x9000-0x90ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093307] pci 0000:00:06.0: reg 14: [mem 0xd8181000-0xd81810ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093345] pci 0000:00:06.0: reg 30: [mem 0x00000000-0x0001ffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093372] pci 0000:00:06.0: supports D1 D2
Dec 30 19:27:27 WORKHORSE kernel: [    0.093375] pci 0000:00:06.0: PME# supported from D1 D2 D3hot D3cold
Dec 30 19:27:27 WORKHORSE kernel: [    0.093382] pci 0000:00:06.0: PME# disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.093404] pci 0000:00:07.0: [1095:3512] type 0 class 0x000180
Dec 30 19:27:27 WORKHORSE kernel: [    0.093420] pci 0000:00:07.0: reg 10: [io  0x9400-0x9407]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093430] pci 0000:00:07.0: reg 14: [io  0x9800-0x9803]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093440] pci 0000:00:07.0: reg 18: [io  0x9c00-0x9c07]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093450] pci 0000:00:07.0: reg 1c: [io  0xa000-0xa003]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093460] pci 0000:00:07.0: reg 20: [io  0xa400-0xa40f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093470] pci 0000:00:07.0: reg 24: [mem 0xd8180000-0xd81801ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093480] pci 0000:00:07.0: reg 30: [mem 0x00000000-0x0007ffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093506] pci 0000:00:07.0: supports D1 D2
Dec 30 19:27:27 WORKHORSE kernel: [    0.093536] pci 0000:00:10.0: [1106:3038] type 0 class 0x000c03
Dec 30 19:27:27 WORKHORSE kernel: [    0.093580] pci 0000:00:10.0: reg 20: [io  0xa800-0xa81f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093619] pci 0000:00:10.0: supports D1 D2
Dec 30 19:27:27 WORKHORSE kernel: [    0.093622] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 19:27:27 WORKHORSE kernel: [    0.093627] pci 0000:00:10.0: PME# disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.093648] pci 0000:00:10.1: [1106:3038] type 0 class 0x000c03
Dec 30 19:27:27 WORKHORSE kernel: [    0.093691] pci 0000:00:10.1: reg 20: [io  0xac00-0xac1f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093730] pci 0000:00:10.1: supports D1 D2
Dec 30 19:27:27 WORKHORSE kernel: [    0.093733] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 19:27:27 WORKHORSE kernel: [    0.093738] pci 0000:00:10.1: PME# disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.093764] pci 0000:00:10.2: [1106:3038] type 0 class 0x000c03
Dec 30 19:27:27 WORKHORSE kernel: [    0.093808] pci 0000:00:10.2: reg 20: [io  0xb000-0xb01f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093847] pci 0000:00:10.2: supports D1 D2
Dec 30 19:27:27 WORKHORSE kernel: [    0.093850] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 19:27:27 WORKHORSE kernel: [    0.093855] pci 0000:00:10.2: PME# disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.093877] pci 0000:00:10.3: [1106:3104] type 0 class 0x000c03
Dec 30 19:27:27 WORKHORSE kernel: [    0.093894] pci 0000:00:10.3: reg 10: [mem 0xd8182000-0xd81820ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.093960] pci 0000:00:10.3: supports D1 D2
Dec 30 19:27:27 WORKHORSE kernel: [    0.093963] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 19:27:27 WORKHORSE kernel: [    0.093968] pci 0000:00:10.3: PME# disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.093994] pci 0000:00:11.0: [1106:3177] type 0 class 0x000601
Dec 30 19:27:27 WORKHORSE kernel: [    0.094055] HPET not enabled in BIOS. You might try hpet=force boot option
Dec 30 19:27:27 WORKHORSE kernel: [    0.094073] pci 0000:00:11.0: quirk: [io  0x4000-0x407f] claimed by vt8235 PM
Dec 30 19:27:27 WORKHORSE kernel: [    0.094081] pci 0000:00:11.0: quirk: [io  0x5000-0x500f] claimed by vt8235 SMB
Dec 30 19:27:27 WORKHORSE kernel: [    0.094131] pci 0000:00:11.1: [1106:0571] type 0 class 0x000101
Dec 30 19:27:27 WORKHORSE kernel: [    0.094176] pci 0000:00:11.1: reg 20: [io  0xb400-0xb40f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094245] pci 0000:00:12.0: [1106:3065] type 0 class 0x000200
Dec 30 19:27:27 WORKHORSE kernel: [    0.094262] pci 0000:00:12.0: reg 10: [io  0xb800-0xb8ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094272] pci 0000:00:12.0: reg 14: [mem 0xd8183000-0xd81830ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094333] pci 0000:00:12.0: supports D1 D2
Dec 30 19:27:27 WORKHORSE kernel: [    0.094336] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 30 19:27:27 WORKHORSE kernel: [    0.094341] pci 0000:00:12.0: PME# disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.094401] pci 0000:01:00.0: [5333:8d04] type 0 class 0x000300
Dec 30 19:27:27 WORKHORSE kernel: [    0.094417] pci 0000:01:00.0: reg 10: [mem 0xd8000000-0xd807ffff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094427] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xd7ffffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094459] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094487] pci 0000:01:00.0: supports D1 D2
Dec 30 19:27:27 WORKHORSE kernel: [    0.094522] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094533] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xd80fffff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094539] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd7ffffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094548] pci_bus 0000:00: on NUMA node 0
Dec 30 19:27:27 WORKHORSE kernel: [    0.094554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 30 19:27:27 WORKHORSE kernel: [    0.094847]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
Dec 30 19:27:27 WORKHORSE kernel: [    0.106862] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
Dec 30 19:27:27 WORKHORSE kernel: [    0.107007] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
Dec 30 19:27:27 WORKHORSE kernel: [    0.107149] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Dec 30 19:27:27 WORKHORSE kernel: [    0.107289] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Dec 30 19:27:27 WORKHORSE kernel: [    0.107419] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
Dec 30 19:27:27 WORKHORSE kernel: [    0.107538] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
Dec 30 19:27:27 WORKHORSE kernel: [    0.107680] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
Dec 30 19:27:27 WORKHORSE kernel: [    0.107798] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
Dec 30 19:27:27 WORKHORSE kernel: [    0.108116] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Dec 30 19:27:27 WORKHORSE kernel: [    0.108127] vgaarb: loaded
Dec 30 19:27:27 WORKHORSE kernel: [    0.108132] vgaarb: bridge control possible 0000:01:00.0
Dec 30 19:27:27 WORKHORSE kernel: [    0.108360] i2c-core: driver [aat2870] using legacy suspend method
Dec 30 19:27:27 WORKHORSE kernel: [    0.108368] i2c-core: driver [aat2870] using legacy resume method
Dec 30 19:27:27 WORKHORSE kernel: [    0.108552] SCSI subsystem initialized
Dec 30 19:27:27 WORKHORSE kernel: [    0.108697] libata version 3.00 loaded.
Dec 30 19:27:27 WORKHORSE kernel: [    0.108821] usbcore: registered new interface driver usbfs
Dec 30 19:27:27 WORKHORSE kernel: [    0.108848] usbcore: registered new interface driver hub
Dec 30 19:27:27 WORKHORSE kernel: [    0.108917] usbcore: registered new device driver usb
Dec 30 19:27:27 WORKHORSE kernel: [    0.109108] PCI: Using ACPI for IRQ routing
Dec 30 19:27:27 WORKHORSE kernel: [    0.109121] PCI: pci_cache_line_size set to 32 bytes
Dec 30 19:27:27 WORKHORSE kernel: [    0.109190] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
Dec 30 19:27:27 WORKHORSE kernel: [    0.109195] reserve RAM buffer: 000000007dff0000 - 000000007fffffff 
Dec 30 19:27:27 WORKHORSE kernel: [    0.109415] NetLabel: Initializing
Dec 30 19:27:27 WORKHORSE kernel: [    0.109422] NetLabel:  domain hash size = 128
Dec 30 19:27:27 WORKHORSE kernel: [    0.109427] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 30 19:27:27 WORKHORSE kernel: [    0.109454] NetLabel:  unlabeled traffic allowed by default
Dec 30 19:27:27 WORKHORSE kernel: [    0.125899] AppArmor: AppArmor Filesystem Enabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.126013] pnp: PnP ACPI init
Dec 30 19:27:27 WORKHORSE kernel: [    0.126058] ACPI: bus type pnp registered
Dec 30 19:27:27 WORKHORSE kernel: [    0.126577] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.126676] pnp 00:01: [bus 00-ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126681] pnp 00:01: [io  0x0cf8-0x0cff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126685] pnp 00:01: [io  0x0000-0x0cf7 window]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126689] pnp 00:01: [io  0x0d00-0x3fff window]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126692] pnp 00:01: [io  0x4000-0x407f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126695] pnp 00:01: [io  0x4080-0x40ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126698] pnp 00:01: [io  0x4100-0x4fff window]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126701] pnp 00:01: [io  0x5000-0x500f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126704] pnp 00:01: [io  0x5010-0xffff window]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126708] pnp 00:01: [mem 0x000a0000-0x000bffff window]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126711] pnp 00:01: [mem 0x000c0000-0x000dffff window]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126715] pnp 00:01: [mem 0x7e000000-0xfebfffff window]
Dec 30 19:27:27 WORKHORSE kernel: [    0.126802] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.127063] pnp 00:02: [io  0x0010-0x001f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127068] pnp 00:02: [io  0x0022-0x003f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127071] pnp 00:02: [io  0x0044-0x005f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127074] pnp 00:02: [io  0x0062-0x0063]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127077] pnp 00:02: [io  0x0065-0x006f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127080] pnp 00:02: [io  0x0074-0x007f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127083] pnp 00:02: [io  0x0091-0x0093]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127086] pnp 00:02: [io  0x00a2-0x00bf]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127089] pnp 00:02: [io  0x00e0-0x00ef]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127092] pnp 00:02: [io  0x04d0-0x04d1]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127095] pnp 00:02: [io  0x0294-0x0297]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127169] system 00:02: [io  0x04d0-0x04d1] has been reserved
Dec 30 19:27:27 WORKHORSE kernel: [    0.127179] system 00:02: [io  0x0294-0x0297] has been reserved
Dec 30 19:27:27 WORKHORSE kernel: [    0.127187] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.127209] pnp 00:03: [dma 4]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127213] pnp 00:03: [io  0x0000-0x000f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127216] pnp 00:03: [io  0x0080-0x0090]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127219] pnp 00:03: [io  0x0094-0x009f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127222] pnp 00:03: [io  0x00c0-0x00df]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127267] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.127284] pnp 00:04: [io  0x0070-0x0073]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127312] pnp 00:04: [irq 8]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127366] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.127381] pnp 00:05: [io  0x0061]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127427] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.127442] pnp 00:06: [io  0x00f0-0x00ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127450] pnp 00:06: [irq 13]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127507] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.127659] pnp 00:07: [io  0x03f2-0x03f5]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127674] pnp 00:07: [io  0x03f7]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127681] pnp 00:07: [irq 6]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127684] pnp 00:07: [dma 2]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127756] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.127965] pnp 00:08: [io  0x03f8-0x03ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.127973] pnp 00:08: [irq 4]
Dec 30 19:27:27 WORKHORSE kernel: [    0.128114] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.128339] pnp 00:09: [io  0x02f8-0x02ff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.128348] pnp 00:09: [irq 3]
Dec 30 19:27:27 WORKHORSE kernel: [    0.128439] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.128894] pnp 00:0a: [io  0x0378-0x037f]
Dec 30 19:27:27 WORKHORSE kernel: [    0.128898] pnp 00:0a: [io  0x0778-0x077b]
Dec 30 19:27:27 WORKHORSE kernel: [    0.128905] pnp 00:0a: [irq 7]
Dec 30 19:27:27 WORKHORSE kernel: [    0.128908] pnp 00:0a: [dma 3]
Dec 30 19:27:27 WORKHORSE kernel: [    0.129006] pnp 00:0a: Plug and Play ACPI device, IDs PNP0401 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.129086] pnp 00:0b: [io  0x0060]
Dec 30 19:27:27 WORKHORSE kernel: [    0.129090] pnp 00:0b: [io  0x0064]
Dec 30 19:27:27 WORKHORSE kernel: [    0.129165] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 30 19:27:27 WORKHORSE kernel: [    0.129179] pnp: PnP ACPI: found 12 devices
Dec 30 19:27:27 WORKHORSE kernel: [    0.129187] ACPI: ACPI bus type pnp unregistered
Dec 30 19:27:27 WORKHORSE kernel: [    0.129197] PnPBIOS: Disabled by ACPI PNP
Dec 30 19:27:27 WORKHORSE kernel: [    0.167168] Switching to clocksource acpi_pm
Dec 30 19:27:27 WORKHORSE kernel: [    0.167234] PCI: max bus depth: 1 pci_try_num: 2
Dec 30 19:27:27 WORKHORSE kernel: [    0.167286] pci 0000:00:07.0: BAR 6: assigned [mem 0x80000000-0x8007ffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167300] pci 0000:00:06.0: BAR 6: assigned [mem 0x80080000-0x8009ffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167310] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8080000-0xd808ffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167320] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167331] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xd80fffff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167340] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xd7ffffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167366] pci 0000:00:01.0: setting latency timer to 64
Dec 30 19:27:27 WORKHORSE kernel: [    0.167373] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167376] pci_bus 0000:00: resource 1 [mem 0x00000000-0x3ffffffff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167381] pci_bus 0000:01: resource 1 [mem 0xd8000000-0xd80fffff]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167384] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd7ffffff pref]
Dec 30 19:27:27 WORKHORSE kernel: [    0.167512] NET: Registered protocol family 2
Dec 30 19:27:27 WORKHORSE kernel: [    0.167651] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.167651] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.168367] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.169849] TCP: Hash tables configured (established 131072 bind 65536)
Dec 30 19:27:27 WORKHORSE kernel: [    0.169871] TCP reno registered
Dec 30 19:27:27 WORKHORSE kernel: [    0.169882] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.169932] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.170171] NET: Registered protocol family 1
Dec 30 19:27:27 WORKHORSE kernel: [    0.170209] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
Dec 30 19:27:27 WORKHORSE kernel: [    0.170592] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.170602] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.170640] pci 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.170666] pci 0000:00:10.0: PCI INT A disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.170684] pci 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.170705] pci 0000:00:10.1: PCI INT B disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.170722] pci 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.170743] pci 0000:00:10.2: PCI INT C disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.170760] pci 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.170818] pci 0000:00:10.3: PCI INT D disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.170839] pci 0000:01:00.0: Boot video device
Dec 30 19:27:27 WORKHORSE kernel: [    0.170844] PCI: CLS 32 bytes, default 32
Dec 30 19:27:27 WORKHORSE kernel: [    0.171617] audit: initializing netlink socket (disabled)
Dec 30 19:27:27 WORKHORSE kernel: [    0.171646] type=2000 audit(1356913638.164:1): initialized
Dec 30 19:27:27 WORKHORSE kernel: [    0.201849] Trying to unpack rootfs image as initramfs...
Dec 30 19:27:27 WORKHORSE kernel: [    0.237326] highmem bounce pool size: 64 pages
Dec 30 19:27:27 WORKHORSE kernel: [    0.237361] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 30 19:27:27 WORKHORSE kernel: [    0.248324] VFS: Disk quotas dquot_6.5.2
Dec 30 19:27:27 WORKHORSE kernel: [    0.248465] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 30 19:27:27 WORKHORSE kernel: [    0.249571] fuse init (API version 7.17)
Dec 30 19:27:27 WORKHORSE kernel: [    0.249738] msgmni has been set to 1686
Dec 30 19:27:27 WORKHORSE kernel: [    0.260843] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 30 19:27:27 WORKHORSE kernel: [    0.264201] io scheduler noop registered
Dec 30 19:27:27 WORKHORSE kernel: [    0.264230] io scheduler deadline registered
Dec 30 19:27:27 WORKHORSE kernel: [    0.264292] io scheduler cfq registered (default)
Dec 30 19:27:27 WORKHORSE kernel: [    0.264602] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 30 19:27:27 WORKHORSE kernel: [    0.264665] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 30 19:27:27 WORKHORSE kernel: [    0.264949] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Dec 30 19:27:27 WORKHORSE kernel: [    0.264968] ACPI: Power Button [PWRB]
Dec 30 19:27:27 WORKHORSE kernel: [    0.265059] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Dec 30 19:27:27 WORKHORSE kernel: [    0.265072] ACPI: Sleep Button [SLPB]
Dec 30 19:27:27 WORKHORSE kernel: [    0.265149] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Dec 30 19:27:27 WORKHORSE kernel: [    0.265160] ACPI: Power Button [PWRF]
Dec 30 19:27:27 WORKHORSE kernel: [    0.265262] ACPI: Fan [FAN] (on)
Dec 30 19:27:27 WORKHORSE kernel: [    0.265335] Marking TSC unstable due to TSC halts in idle
Dec 30 19:27:27 WORKHORSE kernel: [    0.265353] ACPI: acpi_idle registered with cpuidle
Dec 30 19:27:27 WORKHORSE kernel: [    0.267392] thermal LNXTHERM:00: registered as thermal_zone0
Dec 30 19:27:27 WORKHORSE kernel: [    0.267401] ACPI: Thermal Zone [THRM] (52 C)
Dec 30 19:27:27 WORKHORSE kernel: [    0.267459] ERST: Table is not found!
Dec 30 19:27:27 WORKHORSE kernel: [    0.267465] GHES: HEST is not enabled!
Dec 30 19:27:27 WORKHORSE kernel: [    0.267813] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.288281] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 30 19:27:27 WORKHORSE kernel: [    0.288335] isapnp: Scanning for PnP cards...
Dec 30 19:27:27 WORKHORSE kernel: [    0.376901] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 30 19:27:27 WORKHORSE kernel: [    0.422836] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 30 19:27:27 WORKHORSE kernel: [    0.508786] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 30 19:27:27 WORKHORSE kernel: [    0.528693] Linux agpgart interface v0.103
Dec 30 19:27:27 WORKHORSE kernel: [    0.528834] agpgart: Detected VIA PM266/KM266 chipset
Dec 30 19:27:27 WORKHORSE kernel: [    0.616556] agpgart-via 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Dec 30 19:27:27 WORKHORSE kernel: [    0.619183] brd: module loaded
Dec 30 19:27:27 WORKHORSE kernel: [    0.624976] loop: module loaded
Dec 30 19:27:27 WORKHORSE kernel: [    0.625790] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Dec 30 19:27:27 WORKHORSE kernel: [    0.625800] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Dec 30 19:27:27 WORKHORSE kernel: [    0.625839] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Dec 30 19:27:27 WORKHORSE kernel: [    0.625983] pata_acpi 0000:00:11.1: PCI INT A disabled
Dec 30 19:27:27 WORKHORSE kernel: [    0.626647] Fixed MDIO Bus: probed
Dec 30 19:27:27 WORKHORSE kernel: [    0.626696] tun: Universal TUN/TAP device driver, 1.6
Dec 30 19:27:27 WORKHORSE kernel: [    0.626702] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 30 19:27:27 WORKHORSE kernel: [    0.626856] PPP generic driver version 2.4.2
Dec 30 19:27:27 WORKHORSE kernel: [    0.627070] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 30 19:27:27 WORKHORSE kernel: [    0.627107] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.627163] ehci_hcd 0000:00:10.3: EHCI Host Controller
Dec 30 19:27:27 WORKHORSE kernel: [    0.627252] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
Dec 30 19:27:27 WORKHORSE kernel: [    0.627358] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd8182000
Dec 30 19:27:27 WORKHORSE kernel: [    0.636210] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
Dec 30 19:27:27 WORKHORSE kernel: [    0.636640] hub 1-0:1.0: USB hub found
Dec 30 19:27:27 WORKHORSE kernel: [    0.636655] hub 1-0:1.0: 6 ports detected
Dec 30 19:27:27 WORKHORSE kernel: [    0.636821] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 30 19:27:27 WORKHORSE kernel: [    0.636860] uhci_hcd: USB Universal Host Controller Interface driver
Dec 30 19:27:27 WORKHORSE kernel: [    0.636947] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.636975] uhci_hcd 0000:00:10.0: UHCI Host Controller
Dec 30 19:27:27 WORKHORSE kernel: [    0.637075] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Dec 30 19:27:27 WORKHORSE kernel: [    0.637125] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000a800
Dec 30 19:27:27 WORKHORSE kernel: [    0.637378] hub 2-0:1.0: USB hub found
Dec 30 19:27:27 WORKHORSE kernel: [    0.637390] hub 2-0:1.0: 2 ports detected
Dec 30 19:27:27 WORKHORSE kernel: [    0.637491] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.637509] uhci_hcd 0000:00:10.1: UHCI Host Controller
Dec 30 19:27:27 WORKHORSE kernel: [    0.637580] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
Dec 30 19:27:27 WORKHORSE kernel: [    0.637619] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000ac00
Dec 30 19:27:27 WORKHORSE kernel: [    0.637869] hub 3-0:1.0: USB hub found
Dec 30 19:27:27 WORKHORSE kernel: [    0.637880] hub 3-0:1.0: 2 ports detected
Dec 30 19:27:27 WORKHORSE kernel: [    0.637972] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
Dec 30 19:27:27 WORKHORSE kernel: [    0.637989] uhci_hcd 0000:00:10.2: UHCI Host Controller
Dec 30 19:27:27 WORKHORSE kernel: [    0.638061] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
Dec 30 19:27:27 WORKHORSE kernel: [    0.638092] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b000
Dec 30 19:27:27 WORKHORSE kernel: [    0.638324] hub 4-0:1.0: USB hub found
Dec 30 19:27:27 WORKHORSE kernel: [    0.638335] hub 4-0:1.0: 2 ports detected
Dec 30 19:27:27 WORKHORSE kernel: [    0.638522] usbcore: registered new interface driver libusual
Dec 30 19:27:27 WORKHORSE kernel: [    0.638628] i8042: PNP: No PS/2 controller found. Probing ports directly.
Dec 30 19:27:27 WORKHORSE kernel: [    0.644195] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 30 19:27:27 WORKHORSE kernel: [    0.644246] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 30 19:27:27 WORKHORSE kernel: [    0.644586] mousedev: PS/2 mouse device common for all mice
Dec 30 19:27:27 WORKHORSE kernel: [    0.644927] rtc_cmos 00:04: RTC can wake from S4
Dec 30 19:27:27 WORKHORSE kernel: [    0.645125] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Dec 30 19:27:27 WORKHORSE kernel: [    0.645168] rtc0: alarms up to one year, y3k, 242 bytes nvram
Dec 30 19:27:27 WORKHORSE kernel: [    0.645307] device-mapper: uevent: version 1.0.3
Dec 30 19:27:27 WORKHORSE kernel: [    0.645434] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Dec 30 19:27:27 WORKHORSE kernel: [    0.645536] EISA: Probing bus 0 at eisa.0
Dec 30 19:27:27 WORKHORSE kernel: [    0.645575] Cannot allocate resource for EISA slot 4
Dec 30 19:27:27 WORKHORSE kernel: [    0.645582] Cannot allocate resource for EISA slot 5
Dec 30 19:27:27 WORKHORSE kernel: [    0.645602] EISA: Detected 0 cards.
Dec 30 19:27:27 WORKHORSE kernel: [    0.645627] cpufreq-nforce2: No nForce2 chipset.
Dec 30 19:27:27 WORKHORSE kernel: [    0.645679] cpuidle: using governor ladder
Dec 30 19:27:27 WORKHORSE kernel: [    0.645752] cpuidle: using governor menu
Dec 30 19:27:27 WORKHORSE kernel: [    0.645758] EFI Variables Facility v0.08 2004-May-17
Dec 30 19:27:27 WORKHORSE kernel: [    0.646127] TCP cubic registered
Dec 30 19:27:27 WORKHORSE kernel: [    0.646384] NET: Registered protocol family 10
Dec 30 19:27:27 WORKHORSE kernel: [    0.647242] NET: Registered protocol family 17
Dec 30 19:27:27 WORKHORSE kernel: [    0.647255] Registering the dns_resolver key type
Dec 30 19:27:27 WORKHORSE kernel: [    0.647309] Using IPI No-Shortcut mode
Dec 30 19:27:27 WORKHORSE kernel: [    0.647551] PM: Hibernation image not present or could not be loaded.
Dec 30 19:27:27 WORKHORSE kernel: [    0.647577] registered taskstats version 1
Dec 30 19:27:27 WORKHORSE kernel: [    0.895868] isapnp: No Plug & Play device found
Dec 30 19:27:27 WORKHORSE kernel: [    1.182779] Freeing initrd memory: 13836k freed
Dec 30 19:27:27 WORKHORSE kernel: [    1.233983]   Magic number: 8:290:457
Dec 30 19:27:27 WORKHORSE kernel: [    1.234233] rtc_cmos 00:04: setting system clock to 2012-12-31 00:27:19 UTC (1356913639)
Dec 30 19:27:27 WORKHORSE kernel: [    1.234245] powernow-k8: Processor cpuid 681 not supported
Dec 30 19:27:27 WORKHORSE kernel: [    1.234288] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 30 19:27:27 WORKHORSE kernel: [    1.234294] EDD information not available.
Dec 30 19:27:27 WORKHORSE kernel: [    1.234612] Freeing unused kernel memory: 744k freed
Dec 30 19:27:27 WORKHORSE kernel: [    1.236631] Write protecting the kernel text: 5828k
Dec 30 19:27:27 WORKHORSE kernel: [    1.236671] Write protecting the kernel read-only data: 2380k
Dec 30 19:27:27 WORKHORSE kernel: [    1.514591] Floppy drive(s): fd0 is 1.44M
Dec 30 19:27:27 WORKHORSE kernel: [    1.538557] FDC 0 is a post-1991 82077
Dec 30 19:27:27 WORKHORSE kernel: [    1.563624] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Dec 30 19:27:27 WORKHORSE kernel: [    1.563710] r8169 0000:00:06.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 30 19:27:27 WORKHORSE kernel: [    1.563736] r8169 0000:00:06.0: PCI: Disallowing DAC for device
Dec 30 19:27:27 WORKHORSE kernel: [    1.563766] r8169 0000:00:06.0: (unregistered net_device): not PCI Express
Dec 30 19:27:27 WORKHORSE kernel: [    1.594921] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
Dec 30 19:27:27 WORKHORSE kernel: [    1.594950] via_rhine: Broken BIOS detected, avoid_D3 enabled
Dec 30 19:27:27 WORKHORSE kernel: [    1.598907] r8169 0000:00:06.0: eth0: RTL8169sb/8110sb at 0xf840c000, 00:e0:52:bf:66:4a, XID 10000000 IRQ 17
Dec 30 19:27:27 WORKHORSE kernel: [    1.598935] r8169 0000:00:06.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
Dec 30 19:27:27 WORKHORSE kernel: [    1.609796] sata_sil 0000:00:07.0: version 2.4
Dec 30 19:27:27 WORKHORSE kernel: [    1.609926] sata_sil 0000:00:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 30 19:27:27 WORKHORSE kernel: [    1.613783] scsi0 : sata_sil
Dec 30 19:27:27 WORKHORSE kernel: [    1.616154] scsi1 : sata_sil
Dec 30 19:27:27 WORKHORSE kernel: [    1.616341] ata1: SATA max UDMA/100 mmio m512@0xd8180000 tf 0xd8180080 irq 18
Dec 30 19:27:27 WORKHORSE kernel: [    1.616351] ata2: SATA max UDMA/100 mmio m512@0xd8180000 tf 0xd81800c0 irq 18
Dec 30 19:27:27 WORKHORSE kernel: [    1.623238] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
Dec 30 19:27:27 WORKHORSE kernel: [    1.623265] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Dec 30 19:27:27 WORKHORSE kernel: [    1.623309] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
Dec 30 19:27:27 WORKHORSE kernel: [    1.643569] via-rhine 0000:00:12.0: eth1: VIA Rhine II at 0xd8183000, 00:10:dc:fe:ef:7b, IRQ 23
Dec 30 19:27:27 WORKHORSE kernel: [    1.644372] via-rhine 0000:00:12.0: eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000
Dec 30 19:27:27 WORKHORSE kernel: [    1.644433] pata_via 0000:00:11.1: version 0.3.4
Dec 30 19:27:27 WORKHORSE kernel: [    1.644468] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
Dec 30 19:27:27 WORKHORSE kernel: [    1.648515] scsi2 : pata_via
Dec 30 19:27:27 WORKHORSE kernel: [    1.652288] scsi3 : pata_via
Dec 30 19:27:27 WORKHORSE kernel: [    1.654590] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xb400 irq 14
Dec 30 19:27:27 WORKHORSE kernel: [    1.654601] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xb408 irq 15
Dec 30 19:27:27 WORKHORSE kernel: [    1.936062] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 30 19:27:27 WORKHORSE kernel: [    1.944202] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S223L, SB02, max UDMA/100
Dec 30 19:27:27 WORKHORSE kernel: [    1.960183] ata1.00: configured for UDMA/100
Dec 30 19:27:27 WORKHORSE kernel: [    1.961330] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223L  SB02 PQ: 0 ANSI: 5
Dec 30 19:27:27 WORKHORSE kernel: [    1.965332] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 30 19:27:27 WORKHORSE kernel: [    1.965348] cdrom: Uniform CD-ROM driver Revision: 3.20
Dec 30 19:27:27 WORKHORSE kernel: [    1.966228] sr 0:0:0:0: Attached scsi CD-ROM sr0
Dec 30 19:27:27 WORKHORSE kernel: [    1.966677] sr 0:0:0:0: Attached scsi generic sg0 type 5
Dec 30 19:27:27 WORKHORSE kernel: [    2.284055] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Dec 30 19:27:27 WORKHORSE kernel: [    2.292308] ata2.00: ATA-7: SAMSUNG HD103UJ, 1AA01113, max UDMA7
Dec 30 19:27:27 WORKHORSE kernel: [    2.292318] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 30 19:27:27 WORKHORSE kernel: [    2.300292] ata2.00: configured for UDMA/100
Dec 30 19:27:27 WORKHORSE kernel: [    2.300537] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
Dec 30 19:27:27 WORKHORSE kernel: [    2.300902] sd 1:0:0:0: Attached scsi generic sg1 type 0
Dec 30 19:27:27 WORKHORSE kernel: [    2.301204] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Dec 30 19:27:27 WORKHORSE kernel: [    2.301302] sd 1:0:0:0: [sda] Write Protect is off
Dec 30 19:27:27 WORKHORSE kernel: [    2.301311] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 30 19:27:27 WORKHORSE kernel: [    2.301349] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 30 19:27:27 WORKHORSE kernel: [    2.352413]  sda: sda1 sda2 < sda5 sda6 sda7 >
Dec 30 19:27:27 WORKHORSE kernel: [    2.353574] sd 1:0:0:0: [sda] Attached SCSI disk
Dec 30 19:27:27 WORKHORSE kernel: [    2.931023] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Dec 30 19:27:27 WORKHORSE kernel: [    6.551766] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 30 19:27:27 WORKHORSE kernel: [    6.551783] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 30 19:27:27 WORKHORSE kernel: [    6.687462] Adding 3905532k swap on /dev/sda5.  Priority:-1 extents:1 across:3905532k 
Dec 30 19:27:27 WORKHORSE kernel: [    6.717592] lp: driver loaded but no devices found
Dec 30 19:27:27 WORKHORSE kernel: [    7.012516] parport_pc 00:0a: reported by Plug and Play ACPI
Dec 30 19:27:27 WORKHORSE kernel: [    7.012636] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Dec 30 19:27:27 WORKHORSE kernel: [    7.135892] lp0: using parport0 (interrupt-driven).
Dec 30 19:27:27 WORKHORSE kernel: [    7.251022] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Dec 30 19:27:27 WORKHORSE kernel: [    7.333731] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 30 19:27:27 WORKHORSE kernel: [    7.547496] type=1400 audit(1356913645.805:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=369 comm="apparmor_parser"
Dec 30 19:27:27 WORKHORSE kernel: [    7.550601] type=1400 audit(1356913645.809:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=369 comm="apparmor_parser"
Dec 30 19:27:27 WORKHORSE kernel: [    7.551021] type=1400 audit(1356913645.809:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=369 comm="apparmor_parser"
Dec 30 19:27:27 WORKHORSE kernel: [    7.809821] r8169 0000:00:06.0: eth0: link down
Dec 30 19:27:27 WORKHORSE kernel: [    7.809837] r8169 0000:00:06.0: eth0: link down
Dec 30 19:27:27 WORKHORSE kernel: [    7.820203] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 30 19:27:27 WORKHORSE kernel: [    7.878834] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Dec 30 19:27:27 WORKHORSE kernel: [    7.923120] irda_init()
Dec 30 19:27:27 WORKHORSE kernel: [    7.923162] NET: Registered protocol family 23
Dec 30 19:27:27 WORKHORSE kernel: [    8.417029] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
Dec 30 19:27:27 WORKHORSE failsafe: Failsafe of 120 seconds reached.
Dec 30 19:27:28 WORKHORSE kernel: [    9.816942] ppdev: user-space parallel port driver
Dec 30 19:27:28 WORKHORSE kernel: [    9.922739] vesafb: mode is 640x480x32, linelength=2560, pages=0
Dec 30 19:27:28 WORKHORSE kernel: [    9.922748] vesafb: scrolling: redraw
Dec 30 19:27:28 WORKHORSE kernel: [    9.922753] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Dec 30 19:27:28 WORKHORSE kernel: [    9.923623] vesafb: framebuffer at 0xd0000000, mapped to 0xf8680000, using 1216k, total 1216k
Dec 30 19:27:28 WORKHORSE kernel: [    9.925385] Console: switching to colour frame buffer device 80x30
Dec 30 19:27:28 WORKHORSE kernel: [    9.933459] fb0: VESA VGA frame buffer device
Dec 30 19:27:29 WORKHORSE dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Dec 30 19:27:29 WORKHORSE kernel: [   11.300935] r8169 0000:00:06.0: eth0: link up
Dec 30 19:27:29 WORKHORSE kernel: [   11.301330] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 30 19:27:34 WORKHORSE dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Dec 30 19:27:34 WORKHORSE dhclient: DHCPREQUEST of 192.168.1.140 on eth0 to 255.255.255.255 port 67
Dec 30 19:27:34 WORKHORSE dhclient: DHCPOFFER of 192.168.1.140 from 192.168.1.1
Dec 30 19:27:34 WORKHORSE dhclient: DHCPACK of 192.168.1.140 from 192.168.1.1
Dec 30 19:27:34 WORKHORSE dhclient: bound to 192.168.1.140 -- renewal in 37456 seconds.
Dec 30 19:27:34 WORKHORSE kernel: [   16.592440] init: failsafe main process (575) killed by TERM signal
Dec 30 19:27:34 WORKHORSE kernel: [   16.701758] type=1400 audit(1356913654.961:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=862 comm="apparmor_parser"
Dec 30 19:27:34 WORKHORSE kernel: [   16.702543] type=1400 audit(1356913654.961:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=862 comm="apparmor_parser"
Dec 30 19:27:34 WORKHORSE kernel: [   16.702971] type=1400 audit(1356913654.961:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=862 comm="apparmor_parser"
Dec 30 19:27:34 WORKHORSE kernel: [   16.713349] type=1400 audit(1356913654.973:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=864 comm="apparmor_parser"
Dec 30 19:27:35 WORKHORSE acpid: starting up with proc fs
Dec 30 19:27:35 WORKHORSE acpid: 1 rule loaded
Dec 30 19:27:35 WORKHORSE acpid: waiting for events: event logging is off
Dec 30 19:27:35 WORKHORSE cron[898]: (CRON) INFO (pidfile fd = 3)
Dec 30 19:27:35 WORKHORSE cron[917]: (CRON) STARTUP (fork ok)
Dec 30 19:27:35 WORKHORSE cron[917]: (CRON) INFO (Running @reboot jobs)
Dec 30 19:27:40 WORKHORSE kernel: [   21.936031] eth0: no IPv6 routers present
Dec 30 19:27:43 WORKHORSE ntpdate[765]: step time server 91.189.94.4 offset 0.720961 sec


```

The above confirms that it was a reboot...

Knowing the above, the one thing that I have not tried yet is to see if after a network freeze event, will the server come back online - I always used to try pinging immediately, and got no response.

But the real question I guess at this point is - why is this happening, and where can I look to get more information on this?

Any help will be greatly appreciated. Let me know if more data is needed, I will post back replies as soon as I can.

Thanks for looking, and have a blessed day!

---

