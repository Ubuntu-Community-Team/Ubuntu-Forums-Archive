---
title: "Huawei E173 Mobile Broadband  - Ubuntu 12.04 LTS 32-bit"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by vynonline on 2013-03-23
I have a huawei mobile broadband usb modem E173 and am using ubuntu 12.04 LTS 32-bit build. I have been facing issues on it. I am able to connect to internet with it and ubuntu detects it. But [COLOR=#ff0000]sometimes[/COLOR] the modem is not recognised when the computer boots and I can't connect :( .

From my observation, 
[LIST]
[*]The device is not detected if it has been plugged in when the pc is switched off and again booted. 
[*]If the device is not detected , reconnecting it won't make it detected. The computer needs to be restarted and modem to be connected after booting for it to be recognized. 
[*]When i used to dual boot ubuntu with Win7 , after [COLOR=#ff0000]using internet in ubuntu and rebooting in win7 also didn't make modem to be detected in win7[/COLOR]. I imagined having ubuntu alone as the OS will rectify the problem. [COLOR=#ff0000]A point to note is that using Fedora 16 '*Verne*' back then along with Win7 didn't create this issue.[/COLOR] 
[*]The device is detected everytime if its connected after boot. 
[/LIST]

I am using a desktop PC and would like to keep my modem connected always. So I do appreciate some assistance in this matter. :)

---

### Post by alexfish on 2013-03-23
That "it works every time if pluged after boot" Interesting , 

Looks like you may have do  this all the time, keep up with system updates and monitor what happens.

Do not know how many usb ports you have , can try swapping ports

Interestingly is your system Desktop or Laptop

Alex

---

### Post by vynonline on 2013-03-24
Thanks for the response.

I am using a desktop and that's why its such an inconvenience for me.
I have tried swapping up the ports and no luck with that.

I did have the same problem when I was dual-booting windows and '*Precise Pangolin*' build and windows even was not able to recognize my device after reboot from ubuntu as mentioned in my first post. I have currently switched to having only Ubuntu in my PC and it happens that I am not the sole user of the machine. So I happen to recieve many 'not so good' remarks about switching it to linux as this 'problem' seems to be inconvenience to others.

I switched to Ubuntu as it seems to be more User-GUI friendly than other distro's. But i may have to try other distro's if this problem's continues because i dont know to rectify it on my own.

---

### Post by sanderj on 2013-03-24
Could this be such a USB modem that also acts a USB flash drive? You need to swap its functionality with some software tool.

Quick test: what is the output of 'lsusb' when:
- usb modem is unplugged
- usb modem is plugged in and recognized
- usb modem is plugged in and not recognized

And after you plug it in, what is the output of dmesg?

---

### Post by vynonline on 2013-03-24
> **sanderj said:**
> Could this be such a USB modem that also acts a USB flash drive? You need to swap its functionality with some software tool.

Quick test: what is the output of 'lsusb' when:
- usb modem is unplugged
- usb modem is plugged in and recognized
- usb modem is plugged in and not recognized

And after you plug it in, what is the output of dmesg?

Yes it has a memory card reader too . I dont know how to swap the functionality.

Will post the required outputs ASAP. (~When i get home)

Thank you for your assistance :KS

---

### Post by vynonline on 2013-03-24
The lsusb outputs :

When device is unplugged :
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 8564:1000  
Bus 003 Device 002: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
```

When device is plugged in and recognized :
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 8564:1000  
Bus 003 Device 002: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 001 Device 008: ID 12d1:1436 Huawei Technologies Co., Ltd. 
```

When the device is plugged in but not recognized :
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 8564:1000  
Bus 001 Device 004: ID 12d1:1436 Huawei Technologies Co., Ltd. 
Bus 003 Device 002: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
```

dmesg output after plugged in but not recognised

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-39-generic-pae (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #62-Ubuntu SMP Wed Feb 27 22:25:11 UTC 2013 (Ubuntu 3.2.0-39.62-generic-pae 3.2.39)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fedf800 (usable)
[    0.000000]  BIOS-e820: 000000007fedf800 - 000000007fee0000 (reserved)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Acer AcerPower Series/E946GZ               , BIOS R01-A3 06/01/2007
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fedf max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] total RAM covered: 2047M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 2      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2047MB, range: 1MB, type UC
[    0.000000] found SMP MP-table at [c00f3640] f3640
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffa000-2000000
[    0.000000] RAMDISK: 364f2000 - 37271000
[    0.000000] ACPI: RSDP 000f7800 00014 (v00 ACRSYS)
[    0.000000] ACPI: RSDT 7fee3040 0003C (v01 ACRSYS ACRPRDCT 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 7fee30c0 00074 (v01 ACRSYS ACRPRDCT 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 7fee3180 044ED (v01 ACRSYS AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 7fee0000 00040
[    0.000000] ACPI: SLIC 7fee77c0 00176 (v01 ACRSYS ACRPRDCT 42302E31 AWRD 00000001)
[    0.000000] ACPI: MCFG 7fee7980 0003C (v01 ACRSYS ACRPRDCT 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 7fee76c0 00084 (v01 ACRSYS ACRPRDCT 42302E31 AWRD 00000000)
[    0.000000] ACPI: SSDT 7fee7a00 0019E (v01  PmRef  Cpu0Ist 00003000 INTL 20040311)
[    0.000000] ACPI: SSDT 7fee7e90 002F1 (v01  PmRef    CpuPm 00003000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1154MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x0007fedf
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fedf
[    0.000000] On node 0 totalpages: 523886
[    0.000000] free_area_init_node: node 0, pgdat c186b380, node_mem_map f54f2200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2310 pages used for memmap
[    0.000000]   HighMem zone: 293339 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7ff00000 (gap: 7ff00000:60100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb9000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519792
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-39-generic-pae root=UUID=7c487426-b209-4266-ae6b-ad3469bec075 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8383728 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007fedf)
[    0.000000] Memory: 2045700k/2095996k available (5827k kernel code, 49844k reserved, 2847k data, 740k init, 1182596k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1932000   ( 740 kB)
[    0.000000]       .data : 0xc15b0d3c - 0xc1878c00   (2847 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b0d3c   (5827 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f500a000 soft=f500c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2200.166 MHz processor.
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4400.33 BogoMIPS (lpj=8800664)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004032] Security Framework initialized
[    0.004053] AppArmor: AppArmor initialized
[    0.004055] Yama: becoming mindful.
[    0.004114] Mount-cache hash table entries: 512
[    0.004263] Initializing cgroup subsys cpuacct
[    0.004270] Initializing cgroup subsys memory
[    0.004278] Initializing cgroup subsys devices
[    0.004281] Initializing cgroup subsys freezer
[    0.004283] Initializing cgroup subsys blkio
[    0.004290] Initializing cgroup subsys perf_event
[    0.004318] CPU: Physical Processor ID: 0
[    0.004320] CPU: Processor Core ID: 0
[    0.004323] mce: CPU supports 6 MCE banks
[    0.004332] CPU0: Thermal monitoring enabled (TM2)
[    0.004337] using mwait in idle threads.
[    0.006509] ACPI: Core revision 20110623
[    0.012014] ftrace: allocating 26100 entries in 52 pages
[    0.016060] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016429] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.056735] CPU0: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz stepping 0d
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] PEBS disabled due to CPU errata.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.060003] CPU 1 irqstacks, hard=f50f2000 soft=f50f4000
[    0.060003] Booting Node   0, Processors  #1
[    0.060003] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.148042] NMI watchdog enabled, takes one hw-pmu counter.
[    0.148086] Brought up 2 CPUs
[    0.148088] Total of 2 processors activated (8800.72 BogoMIPS).
[    0.149413] devtmpfs: initialized
[    0.149413] EVM: security.selinux
[    0.149413] EVM: security.SMACK64
[    0.149413] EVM: security.capability
[    0.149413] PM: Registering ACPI NVS region at 7fee0000 (12288 bytes)
[    0.149413] print_constraints: dummy: 
[    0.149413] RTC time: 10:15:43, date: 03/24/13
[    0.149413] NET: Registered protocol family 16
[    0.149413] Trying to unpack rootfs image as initramfs...
[    0.149413] EISA bus registered
[    0.149413] ACPI: bus type pci registered
[    0.149413] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149413] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.149413] PCI: Using MMCONFIG for extended config space
[    0.149413] PCI: Using configuration type 1 for base access
[    0.152595] bio: create slab <bio-0> at 0
[    0.152687] ACPI: Added _OSI(Module Device)
[    0.152690] ACPI: Added _OSI(Processor Device)
[    0.152693] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.152695] ACPI: Added _OSI(Processor Aggregator Device)
[    0.153728] ACPI: EC: Look up EC in DSDT
[    0.157658] ACPI: SSDT 7fee7e00 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.157906] ACPI: Dynamic OEM Table Load:
[    0.157910] ACPI: SSDT   (null) 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.158130] ACPI: Interpreter enabled
[    0.158138] ACPI: (supports S0 S3 S4 S5)
[    0.158159] ACPI: Using IOAPIC for interrupt routing
[    0.162742] ACPI: No dock devices found.
[    0.162745] HEST: Table not found.
[    0.162750] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.162812] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.162941] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.162945] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.162948] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.162951] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.162954] pci_root PNP0A08:00: host bridge window [mem 0x7ff00000-0xfebfffff] (ignored)
[    0.162968] pci 0000:00:00.0: [8086:2970] type 0 class 0x000600
[    0.163024] pci 0000:00:01.0: [8086:2971] type 1 class 0x000604
[    0.163076] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.163080] pci 0000:00:01.0: PME# disabled
[    0.163129] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.163146] pci 0000:00:1b.0: reg 10: [mem 0xfdff8000-0xfdffbfff 64bit]
[    0.163223] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.163228] pci 0000:00:1b.0: PME# disabled
[    0.163250] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.163328] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.163332] pci 0000:00:1c.0: PME# disabled
[    0.163356] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.163432] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.163436] pci 0000:00:1c.1: PME# disabled
[    0.163460] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.163536] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.163541] pci 0000:00:1c.2: PME# disabled
[    0.163564] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.163642] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.163647] pci 0000:00:1c.3: PME# disabled
[    0.163670] pci 0000:00:1c.4: [8086:27e0] type 1 class 0x000604
[    0.163747] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.163751] pci 0000:00:1c.4: PME# disabled
[    0.163775] pci 0000:00:1c.5: [8086:27e2] type 1 class 0x000604
[    0.163851] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.163856] pci 0000:00:1c.5: PME# disabled
[    0.163878] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.163922] pci 0000:00:1d.0: reg 20: [io  0xff00-0xff1f]
[    0.163957] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.164000] pci 0000:00:1d.1: reg 20: [io  0xfe00-0xfe1f]
[    0.164048] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.164092] pci 0000:00:1d.2: reg 20: [io  0xfd00-0xfd1f]
[    0.164125] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.164169] pci 0000:00:1d.3: reg 20: [io  0xfc00-0xfc1f]
[    0.164210] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.164228] pci 0000:00:1d.7: reg 10: [mem 0xfdfff000-0xfdfff3ff]
[    0.164311] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.164316] pci 0000:00:1d.7: PME# disabled
[    0.164334] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.164403] pci 0000:00:1f.0: [8086:27b0] type 0 class 0x000601
[    0.164522] pci 0000:00:1f.1: [8086:27df] type 0 class 0x000101
[    0.164536] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.164546] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.164556] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.164567] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.164578] pci 0000:00:1f.1: reg 20: [io  0xfb00-0xfb0f]
[    0.164616] pci 0000:00:1f.2: [8086:27c0] type 0 class 0x000101
[    0.164631] pci 0000:00:1f.2: reg 10: [io  0xfa00-0xfa07]
[    0.164640] pci 0000:00:1f.2: reg 14: [io  0xf900-0xf903]
[    0.164649] pci 0000:00:1f.2: reg 18: [io  0xf800-0xf807]
[    0.164658] pci 0000:00:1f.2: reg 1c: [io  0xf700-0xf703]
[    0.164667] pci 0000:00:1f.2: reg 20: [io  0xf600-0xf60f]
[    0.164676] pci 0000:00:1f.2: reg 24: [mem 0xfdffe000-0xfdffe3ff]
[    0.164708] pci 0000:00:1f.2: PME# supported from D3hot
[    0.164712] pci 0000:00:1f.2: PME# disabled
[    0.164726] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.164781] pci 0000:00:1f.3: reg 20: [io  0x0500-0x051f]
[    0.164862] pci 0000:01:00.0: [10de:0a65] type 0 class 0x000300
[    0.164874] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
[    0.164888] pci 0000:01:00.0: reg 14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.164902] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.164912] pci 0000:01:00.0: reg 24: [io  0xaf00-0xaf7f]
[    0.164921] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.164985] pci 0000:01:00.1: [10de:0be3] type 0 class 0x000403
[    0.164997] pci 0000:01:00.1: reg 10: [mem 0xfbffc000-0xfbffffff]
[    0.165104] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.165108] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.165112] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.165117] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xcfffffff 64bit pref]
[    0.165160] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.165165] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
[    0.165169] pci 0000:00:1c.0:   bridge window [mem 0xfd500000-0xfd5fffff]
[    0.165176] pci 0000:00:1c.0:   bridge window [mem 0xfd200000-0xfd2fffff 64bit pref]
[    0.165252] pci 0000:03:00.0: [8086:109a] type 0 class 0x000200
[    0.165279] pci 0000:03:00.0: reg 10: [mem 0xfcfe0000-0xfcffffff]
[    0.165297] pci 0000:03:00.0: reg 14: [mem 0xfc800000-0xfcbfffff]
[    0.165316] pci 0000:03:00.0: reg 18: [io  0x8f00-0x8f1f]
[    0.165467] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.165474] pci 0000:03:00.0: PME# disabled
[    0.165507] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.165522] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.165526] pci 0000:00:1c.1:   bridge window [io  0x8000-0x8fff]
[    0.165531] pci 0000:00:1c.1:   bridge window [mem 0xfc800000-0xfcffffff]
[    0.165538] pci 0000:00:1c.1:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.165581] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.165585] pci 0000:00:1c.2:   bridge window [io  0x7000-0x7fff]
[    0.165590] pci 0000:00:1c.2:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.165597] pci 0000:00:1c.2:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.165640] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.165644] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.165648] pci 0000:00:1c.3:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.165655] pci 0000:00:1c.3:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.165698] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.165703] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.165707] pci 0000:00:1c.4:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.165714] pci 0000:00:1c.4:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.165757] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    0.165761] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
[    0.165766] pci 0000:00:1c.5:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.165773] pci 0000:00:1c.5:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.165817] pci 0000:08:03.0: [1106:3044] type 0 class 0x000c00
[    0.165836] pci 0000:08:03.0: reg 10: [mem 0xfd4ff000-0xfd4ff7ff]
[    0.165848] pci 0000:08:03.0: reg 14: [io  0xef00-0xef7f]
[    0.165923] pci 0000:08:03.0: supports D2
[    0.165925] pci 0000:08:03.0: PME# supported from D2 D3hot D3cold
[    0.165930] pci 0000:08:03.0: PME# disabled
[    0.165976] pci 0000:00:1e.0: PCI bridge to [bus 08-08] (subtractive decode)
[    0.165980] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.165985] pci 0000:00:1e.0:   bridge window [mem 0xfd400000-0xfd4fffff]
[    0.165991] pci 0000:00:1e.0:   bridge window [mem 0xfd300000-0xfd3fffff 64bit pref]
[    0.165994] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.165997] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.166032] pci_bus 0000:00: on NUMA node 0
[    0.166036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.166173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.166212] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.166249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.166286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.166323] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.166359] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.166396] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.166524]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.166528]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.166530] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.176741] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.176796] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.176848] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.176900] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 11 12 14 *15)
[    0.176951] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.177003] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.177057] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.177110] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 *15)
[    0.177268] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.177273] vgaarb: loaded
[    0.177275] vgaarb: bridge control possible 0000:01:00.0
[    0.177404] i2c-core: driver [aat2870] using legacy suspend method
[    0.177406] i2c-core: driver [aat2870] using legacy resume method
[    0.177510] SCSI subsystem initialized
[    0.184457] libata version 3.00 loaded.
[    0.184457] usbcore: registered new interface driver usbfs
[    0.184457] usbcore: registered new interface driver hub
[    0.184457] usbcore: registered new device driver usb
[    0.184457] PCI: Using ACPI for IRQ routing
[    0.191226] PCI: pci_cache_line_size set to 64 bytes
[    0.191336] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
[    0.191340] reserve RAM buffer: 000000007fedf800 - 000000007fffffff 
[    0.191480] NetLabel: Initializing
[    0.191482] NetLabel:  domain hash size = 128
[    0.191484] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.191496] NetLabel:  unlabeled traffic allowed by default
[    0.201314] AppArmor: AppArmor Filesystem Enabled
[    0.201352] pnp: PnP ACPI init
[    0.201372] ACPI: bus type pnp registered
[    0.201494] pnp 00:00: [bus 00-ff]
[    0.201498] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.201501] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.201503] pnp 00:00: [io  0x0d00-0xffff window]
[    0.201506] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.201509] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.201512] pnp 00:00: [mem 0x7ff00000-0xfebfffff window]
[    0.201583] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.201648] pnp 00:01: [io  0x0010-0x001f]
[    0.201650] pnp 00:01: [io  0x0022-0x003f]
[    0.201652] pnp 00:01: [io  0x0044-0x005f]
[    0.201655] pnp 00:01: [io  0x0062-0x0063]
[    0.201657] pnp 00:01: [io  0x0065-0x006f]
[    0.201662] pnp 00:01: [io  0x0074-0x007f]
[    0.201664] pnp 00:01: [io  0x0091-0x0093]
[    0.201667] pnp 00:01: [io  0x00a2-0x00bf]
[    0.201669] pnp 00:01: [io  0x00e0-0x00ef]
[    0.201671] pnp 00:01: [io  0x04d0-0x04d1]
[    0.201673] pnp 00:01: [io  0x0290-0x029f]
[    0.201675] pnp 00:01: [io  0x0800-0x087f]
[    0.201678] pnp 00:01: [io  0x0880-0x088f]
[    0.201758] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.201761] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.201764] system 00:01: [io  0x0800-0x087f] has been reserved
[    0.201767] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.201771] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.201786] pnp 00:02: [dma 4]
[    0.201788] pnp 00:02: [io  0x0000-0x000f]
[    0.201790] pnp 00:02: [io  0x0080-0x0090]
[    0.201793] pnp 00:02: [io  0x0094-0x009f]
[    0.201795] pnp 00:02: [io  0x00c0-0x00df]
[    0.201827] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.201840] pnp 00:03: [io  0x0070-0x0073]
[    0.201853] pnp 00:03: [irq 8]
[    0.201885] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.201895] pnp 00:04: [io  0x0061]
[    0.201928] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.201938] pnp 00:05: [io  0x00f0-0x00ff]
[    0.201944] pnp 00:05: [irq 13]
[    0.201976] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.202246] pnp 00:06: [io  0x03f8-0x03ff]
[    0.202252] pnp 00:06: [irq 4]
[    0.202320] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.202524] pnp 00:07: [io  0x02f8-0x02ff]
[    0.202530] pnp 00:07: [irq 3]
[    0.202593] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.202802] pnp 00:08: [io  0x0378-0x037f]
[    0.202808] pnp 00:08: [irq 7]
[    0.202864] pnp 00:08: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.202984] pnp 00:09: [io  0x0060]
[    0.202987] pnp 00:09: [io  0x0064]
[    0.202992] pnp 00:09: [irq 12]
[    0.203028] pnp 00:09: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.203088] pnp 00:0a: [io  0x0400-0x04bf]
[    0.203145] system 00:0a: [io  0x0400-0x04bf] has been reserved
[    0.203149] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.203170] pnp 00:0b: [mem 0xffb80000-0xffbfffff]
[    0.203208] pnp 00:0b: Plug and Play ACPI device, IDs INT0800 (active)
[    0.203411] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.203480] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.203484] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.203653] pnp 00:0d: [mem 0x000ce400-0x000cffff]
[    0.203656] pnp 00:0d: [mem 0x000f0000-0x000f7fff]
[    0.203658] pnp 00:0d: [mem 0x000f8000-0x000fbfff]
[    0.203660] pnp 00:0d: [mem 0x000fc000-0x000fffff]
[    0.203663] pnp 00:0d: [mem 0x7ff00000-0x7fffffff]
[    0.203665] pnp 00:0d: [mem 0x7fee0000-0x7fefffff]
[    0.203671] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.203673] pnp 00:0d: [mem 0x00100000-0x7fedffff]
[    0.203676] pnp 00:0d: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.203678] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.203681] pnp 00:0d: [mem 0xfed13000-0xfed1dfff]
[    0.203683] pnp 00:0d: [mem 0xfed20000-0xfed8ffff]
[    0.203686] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.203688] pnp 00:0d: [mem 0xffb00000-0xffb7ffff]
[    0.203690] pnp 00:0d: [mem 0xfff00000-0xffffffff]
[    0.203693] pnp 00:0d: [mem 0x000e0000-0x000effff]
[    0.203782] system 00:0d: [mem 0x000ce400-0x000cffff] has been reserved
[    0.203786] system 00:0d: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.203789] system 00:0d: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.203792] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.203795] system 00:0d: [mem 0x7ff00000-0x7fffffff] could not be reserved
[    0.203799] system 00:0d: [mem 0x7fee0000-0x7fefffff] could not be reserved
[    0.203802] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.203805] system 00:0d: [mem 0x00100000-0x7fedffff] could not be reserved
[    0.203808] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.203812] system 00:0d: [mem 0xfed13000-0xfed1dfff] has been reserved
[    0.203815] system 00:0d: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.203818] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.203821] system 00:0d: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.203824] system 00:0d: [mem 0xfff00000-0xffffffff] has been reserved
[    0.203828] system 00:0d: [mem 0x000e0000-0x000effff] has been reserved
[    0.203831] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.203842] pnp: PnP ACPI: found 14 devices
[    0.203844] ACPI: ACPI bus type pnp unregistered
[    0.203849] PnPBIOS: Disabled by ACPI PNP
[    0.240443] Switching to clocksource acpi_pm
[    0.240727] PCI: max bus depth: 1 pci_try_num: 2
[    0.240805] pci 0000:01:00.0: BAR 6: assigned [mem 0xc0000000-0xc007ffff pref]
[    0.240809] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.240812] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.240816] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.240821] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xcfffffff 64bit pref]
[    0.240826] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.240829] pci 0000:00:1c.0:   bridge window [io  0x9000-0x9fff]
[    0.240835] pci 0000:00:1c.0:   bridge window [mem 0xfd500000-0xfd5fffff]
[    0.240839] pci 0000:00:1c.0:   bridge window [mem 0xfd200000-0xfd2fffff 64bit pref]
[    0.240846] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.240849] pci 0000:00:1c.1:   bridge window [io  0x8000-0x8fff]
[    0.240855] pci 0000:00:1c.1:   bridge window [mem 0xfc800000-0xfcffffff]
[    0.240859] pci 0000:00:1c.1:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.240866] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.240869] pci 0000:00:1c.2:   bridge window [io  0x7000-0x7fff]
[    0.240875] pci 0000:00:1c.2:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.240879] pci 0000:00:1c.2:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.240886] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.240889] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.240894] pci 0000:00:1c.3:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.240899] pci 0000:00:1c.3:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.240905] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
[    0.240909] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.240914] pci 0000:00:1c.4:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.240919] pci 0000:00:1c.4:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.240925] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
[    0.240929] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
[    0.240934] pci 0000:00:1c.5:   bridge window [mem 0xfd700000-0xfd7fffff]
[    0.240939] pci 0000:00:1c.5:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.240946] pci 0000:00:1e.0: PCI bridge to [bus 08-08]
[    0.240949] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    0.240955] pci 0000:00:1e.0:   bridge window [mem 0xfd400000-0xfd4fffff]
[    0.240959] pci 0000:00:1e.0:   bridge window [mem 0xfd300000-0xfd3fffff 64bit pref]
[    0.240987] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.240992] pci 0000:00:01.0: setting latency timer to 64
[    0.241001] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.241006] pci 0000:00:1c.0: setting latency timer to 64
[    0.241017] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.241022] pci 0000:00:1c.1: setting latency timer to 64
[    0.241032] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.241037] pci 0000:00:1c.2: setting latency timer to 64
[    0.241049] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.241054] pci 0000:00:1c.3: setting latency timer to 64
[    0.241061] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.241065] pci 0000:00:1c.4: setting latency timer to 64
[    0.241072] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.241076] pci 0000:00:1c.5: setting latency timer to 64
[    0.241083] pci 0000:00:1e.0: setting latency timer to 64
[    0.241087] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.241090] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.241093] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.241096] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.241099] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xcfffffff 64bit pref]
[    0.241102] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.241104] pci_bus 0000:02: resource 1 [mem 0xfd500000-0xfd5fffff]
[    0.241107] pci_bus 0000:02: resource 2 [mem 0xfd200000-0xfd2fffff 64bit pref]
[    0.241110] pci_bus 0000:03: resource 0 [io  0x8000-0x8fff]
[    0.241113] pci_bus 0000:03: resource 1 [mem 0xfc800000-0xfcffffff]
[    0.241115] pci_bus 0000:03: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.241118] pci_bus 0000:04: resource 0 [io  0x7000-0x7fff]
[    0.241121] pci_bus 0000:04: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.241124] pci_bus 0000:04: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.241126] pci_bus 0000:05: resource 0 [io  0xd000-0xdfff]
[    0.241129] pci_bus 0000:05: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.241132] pci_bus 0000:05: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    0.241134] pci_bus 0000:06: resource 0 [io  0xc000-0xcfff]
[    0.241137] pci_bus 0000:06: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.241140] pci_bus 0000:06: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    0.241143] pci_bus 0000:07: resource 0 [io  0xb000-0xbfff]
[    0.241145] pci_bus 0000:07: resource 1 [mem 0xfd700000-0xfd7fffff]
[    0.241148] pci_bus 0000:07: resource 2 [mem 0xfd600000-0xfd6fffff 64bit pref]
[    0.241151] pci_bus 0000:08: resource 0 [io  0xe000-0xefff]
[    0.241154] pci_bus 0000:08: resource 1 [mem 0xfd400000-0xfd4fffff]
[    0.241156] pci_bus 0000:08: resource 2 [mem 0xfd300000-0xfd3fffff 64bit pref]
[    0.241159] pci_bus 0000:08: resource 4 [io  0x0000-0xffff]
[    0.241162] pci_bus 0000:08: resource 5 [mem 0x00000000-0xfffffffff]
[    0.241214] NET: Registered protocol family 2
[    0.241304] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.241599] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.242168] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.242437] TCP: Hash tables configured (established 131072 bind 65536)
[    0.242440] TCP reno registered
[    0.242443] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.242456] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.242558] NET: Registered protocol family 1
[    0.242620] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.242640] pci 0000:00:1d.0: PCI INT A disabled
[    0.242649] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.242666] pci 0000:00:1d.1: PCI INT B disabled
[    0.242674] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.242691] pci 0000:00:1d.2: PCI INT C disabled
[    0.242699] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.242717] pci 0000:00:1d.3: PCI INT D disabled
[    0.242728] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.242763] pci 0000:00:1d.7: PCI INT A disabled
[    0.242793] pci 0000:01:00.0: Boot video device
[    0.242813] PCI: CLS 64 bytes, default 64
[    0.243206] audit: initializing netlink socket (disabled)
[    0.243221] type=2000 audit(1364120143.240:1): initialized
[    0.264890] highmem bounce pool size: 64 pages
[    0.264896] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.267188] VFS: Disk quotas dquot_6.5.2
[    0.267257] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.267870] fuse init (API version 7.17)
[    0.267972] msgmni has been set to 1685
[    0.268349] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.268379] io scheduler noop registered
[    0.268381] io scheduler deadline registered
[    0.268389] io scheduler cfq registered (default)
[    0.268533] pcieport 0000:00:01.0: setting latency timer to 64
[    0.268574] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.268631] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.268673] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.268736] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.268775] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.268837] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.268876] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.268940] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.268980] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.269045] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.269084] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
[    0.269146] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.269185] pcieport 0000:00:1c.5: irq 46 for MSI/MSI-X
[    0.269280] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.269304] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.269401] intel_idle: MWAIT substates: 0x220
[    0.269403] intel_idle: does not run on family 6 model 15
[    0.269490] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.269496] ACPI: Power Button [PWRB]
[    0.269555] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.269558] ACPI: Power Button [PWRF]
[    0.269618] ACPI: Fan [FAN] (on)
[    0.271397] thermal LNXTHERM:00: registered as thermal_zone0
[    0.271400] ACPI: Thermal Zone [THRM] (40 C)
[    0.271445] ERST: Table is not found!
[    0.271447] GHES: HEST is not enabled!
[    0.271540] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.291951] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.292250] isapnp: Scanning for PnP cards...
[    0.412525] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.477876] Freeing initrd memory: 13820k freed
[    0.645301] isapnp: No Plug & Play device found
[    0.772604] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.793073] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.793418] Linux agpgart interface v0.103
[    0.795428] brd: module loaded
[    0.796360] loop: module loaded
[    0.796565] ata_piix 0000:00:1f.1: version 2.13
[    0.796584] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.796631] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.796992] scsi0 : ata_piix
[    0.797092] scsi1 : ata_piix
[    0.797563] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfb00 irq 14
[    0.797567] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfb08 irq 15
[    0.797588] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.797600] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.797652] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.797723] ata2: port disabled--ignoring
[    0.797999] scsi2 : ata_piix
[    0.798087] scsi3 : ata_piix
[    0.798616] ata3: SATA max UDMA/133 cmd 0xfa00 ctl 0xf900 bmdma 0xf600 irq 19
[    0.798620] ata4: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf608 irq 19
[    0.799048] Fixed MDIO Bus: probed
[    0.799070] tun: Universal TUN/TAP device driver, 1.6
[    0.799072] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.799180] PPP generic driver version 2.4.2
[    0.799306] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.799325] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.799346] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.799350] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.799403] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.799422] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.803323] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.803338] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    0.816045] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.816261] hub 1-0:1.0: USB hub found
[    0.816266] hub 1-0:1.0: 8 ports detected
[    0.816363] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.816381] uhci_hcd: USB Universal Host Controller Interface driver
[    0.816400] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.816408] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.816411] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.816467] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.816490] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
[    0.816635] hub 2-0:1.0: USB hub found
[    0.816639] hub 2-0:1.0: 2 ports detected
[    0.816713] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.816721] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.816724] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.816776] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.816799] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
[    0.816942] hub 3-0:1.0: USB hub found
[    0.816946] hub 3-0:1.0: 2 ports detected
[    0.817020] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.817027] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.817031] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.817081] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.817113] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
[    0.817261] hub 4-0:1.0: USB hub found
[    0.817266] hub 4-0:1.0: 2 ports detected
[    0.817339] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.817346] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.817350] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.817400] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.817431] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
[    0.817575] hub 5-0:1.0: USB hub found
[    0.817579] hub 5-0:1.0: 2 ports detected
[    0.817703] usbcore: registered new interface driver libusual
[    0.817759] i8042: PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    0.817762] i8042: PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.818139] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.818146] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.818290] mousedev: PS/2 mouse device common for all mice
[    0.818467] rtc_cmos 00:03: RTC can wake from S4
[    0.818584] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.818607] rtc0: alarms up to one month, 242 bytes nvram
[    0.818670] device-mapper: uevent: version 1.0.3
[    0.818759] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.818797] EISA: Probing bus 0 at eisa.0
[    0.818822] Cannot allocate resource for EISA slot 7
[    0.818824] Cannot allocate resource for EISA slot 8
[    0.818826] EISA: Detected 0 cards.
[    0.818838] cpufreq-nforce2: No nForce2 chipset.
[    0.818840] cpuidle: using governor ladder
[    0.818842] cpuidle: using governor menu
[    0.818845] EFI Variables Facility v0.08 2004-May-17
[    0.819136] TCP cubic registered
[    0.819270] NET: Registered protocol family 10
[    0.819897] NET: Registered protocol family 17
[    0.819902] Registering the dns_resolver key type
[    0.819927] Using IPI No-Shortcut mode
[    0.820070] PM: Hibernation image not present or could not be loaded.
[    0.820084] registered taskstats version 1
[    0.827250]   Magic number: 5:563:275
[    0.827298] tty tty12: hash matches
[    0.827359] rtc_cmos 00:03: setting system clock to 2013-03-24 10:15:44 UTC (1364120144)
[    0.827966] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.827968] EDD information not available.
[    0.952310] ata4.01: NODEV after polling detection
[    0.960283] ata4.00: ATAPI: HL-DT-ST DVDRAM_GSA-H60N, CA01, max UDMA/100
[    0.960366] ata3.00: ATA-8: Hitachi HDP725016GLA380, GMBOA52A, max UDMA/133
[    0.960369] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.976235] ata4.00: configured for UDMA/100
[    0.976473] ata3.00: configured for UDMA/133
[    0.976689] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDP72501 GMBO PQ: 0 ANSI: 5
[    0.976824] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.976863] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    0.976878] sd 2:0:0:0: [sda] Write Protect is off
[    0.976881] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.976905] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.982229] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM_GSA-H60N  CA01 PQ: 0 ANSI: 5
[    0.987968] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.987974] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.988166] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    0.988293] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.003615]  sda: sda1 sda2 sda3
[    1.004055] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.004134] Freeing unused kernel memory: 740k freed
[    1.004449] Write protecting the kernel text: 5828k
[    1.004469] Write protecting the kernel read-only data: 2380k
[    1.004471] NX-protecting the kernel data: 4412k
[    1.021978] udevd[92]: starting version 175
[    1.075148] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    1.075152] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.075182] e1000e 0000:03:00.0: Disabling ASPM L0s L1
[    1.075200] e1000e 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.075224] e1000e 0000:03:00.0: setting latency timer to 64
[    1.075403] e1000e 0000:03:00.0: irq 47 for MSI/MSI-X
[    1.102330] firewire_ohci 0000:08:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.102340] firewire_ohci 0000:08:03.0: setting latency timer to 64
[    1.128040] usb 1-2: new high-speed USB device number 2 using ehci_hcd
[    1.164112] firewire_ohci: Added fw-ohci device 0000:08:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    1.184486] e1000e 0000:03:00.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:19:21:35:9c:33
[    1.184491] e1000e 0000:03:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.184504] e1000e 0000:03:00.0: eth0: MAC: 2, PHY: 2, PBA No: FFFFFF-0FF
[    1.240052] Refined TSC clocksource calibration: 2200.078 MHz.
[    1.240061] Switching to clocksource tsc
[    1.317038] Initializing USB Mass Storage driver...
[    1.317134] scsi4 : usb-storage 1-2:1.0
[    1.317216] usbcore: registered new interface driver usb-storage
[    1.317218] USB Mass Storage support registered.
[    1.404731] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.480038] usb 1-5: new high-speed USB device number 4 using ehci_hcd
[    1.616649] scsi5 : usb-storage 1-5:1.5
[    1.616821] scsi6 : usb-storage 1-5:1.6
[    1.664159] firewire_core: created device fw0: GUID 00001921ff217dfb, S400
[    1.856386] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    2.507617] scsi 4:0:0:0: Direct-Access     JetFlash Transcend 8GB    1100 PQ: 0 ANSI: 4
[    2.508286] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.508840] sd 4:0:0:0: [sdb] 15950592 512-byte logical blocks: (8.16 GB/7.60 GiB)
[    2.509519] sd 4:0:0:0: [sdb] Write Protect is off
[    2.509522] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    2.510212] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.510216] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.513088] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.513093] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.514150]  sdb: sdb1
[    2.516336] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.516341] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.516347] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    2.617278] scsi 5:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[    2.618108] scsi 6:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[    2.620714] sr1: scsi-1 drive
[    2.620921] sr 5:0:0:0: Attached scsi CD-ROM sr1
[    2.621009] sr 5:0:0:0: Attached scsi generic sg3 type 5
[    2.621233] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    2.623587] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    3.089310] Adding 1999868k swap on /dev/sda2.  Priority:-1 extents:1 across:1999868k 
[    3.941416] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.062792] udevd[376]: starting version 175
[    4.916437] lp: driver loaded but no devices found
[    5.136326] parport_pc 00:08: reported by Plug and Play ACPI
[    5.136370] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    5.232215] lp0: using parport0 (interrupt-driven).
[    5.364823] ppdev: user-space parallel port driver
[    5.383832] leds_ss4200: no LED devices found
[    6.069519] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input2
[    6.166580] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
[    6.166738] generic-usb 0003:04F2:0111.0001: input,hidraw0: USB HID v1.10 Keyboard [Chicony USB Keyboard] on usb-0000:00:1d.1-2/input0
[    6.207272] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input4
[    6.209175] generic-usb 0003:04F2:0111.0002: input,hiddev0,hidraw1: USB HID v1.10 Device [Chicony USB Keyboard] on usb-0000:00:1d.1-2/input1
[    6.210023] usbcore: registered new interface driver usbhid
[    6.210026] usbhid: USB HID core driver
[    6.302634] cdc_ether 1-5:1.1: wwan0: register 'cdc_ether' at usb-0000:00:1d.7-5, Mobile Broadband Network Device, 02:50:f3:00:00:00
[    6.302663] usbcore: registered new interface driver cdc_ether
[    6.629954] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.630021] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[    6.630050] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    6.697894] usbcore: registered new interface driver usbserial
[    6.697912] USB Serial support registered for generic
[    6.697956] usbcore: registered new interface driver usbserial_generic
[    6.697958] usbserial: USB Serial Driver core
[    6.715656] USB Serial support registered for GSM modem (1-port)
[    6.715722] option 1-5:1.0: GSM modem (1-port) converter detected
[    6.716296] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB0
[    6.716329] option 1-5:1.3: GSM modem (1-port) converter detected
[    6.716526] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB1
[    6.716541] option 1-5:1.4: GSM modem (1-port) converter detected
[    6.716670] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB2
[    6.716719] usbcore: registered new interface driver option
[    6.716721] option: v0.7.2:USB Driver for GSM modems
[    6.890025] hda_codec: ALC888: BIOS auto-probing.
[    6.898653] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    6.898791] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    6.898887] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    6.898988] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    6.899081] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    6.899173] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    6.899266] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    6.899360] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    6.899765] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.899769] hda_intel: Disabling MSI
[    6.899816] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[    6.909394] type=1400 audit(1364120150.578:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=564 comm="apparmor_parser"
[    6.909415] type=1400 audit(1364120150.578:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=664 comm="apparmor_parser"
[    6.909855] type=1400 audit(1364120150.578:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=564 comm="apparmor_parser"
[    6.909877] type=1400 audit(1364120150.578:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=664 comm="apparmor_parser"
[    6.910110] type=1400 audit(1364120150.578:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=564 comm="apparmor_parser"
[    6.910134] type=1400 audit(1364120150.578:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=664 comm="apparmor_parser"
[    6.910908] type=1400 audit(1364120150.578:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=510 comm="apparmor_parser"
[    6.912064] type=1400 audit(1364120150.582:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=510 comm="apparmor_parser"
[    6.912326] type=1400 audit(1364120150.582:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=510 comm="apparmor_parser"
[    7.277201] nvidia: module license 'NVIDIA' taints kernel.
[    7.277205] Disabling lock debugging due to kernel taint
[    7.976026] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[    8.000025] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[    8.024142] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[    8.048026] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[    8.048184] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    8.048285] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    8.048365] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[    8.048445] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[    8.049380] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.049391] nvidia 0000:01:00.0: setting latency timer to 64
[    8.049397] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.050024] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.40  Thu Apr  5 21:28:09 PDT 2012
[    8.776928] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    8.776931] vesafb: scrolling: redraw
[    8.776934] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    8.778012] vesafb: framebuffer at 0xcf000000, mapped to 0xf8800000, using 1216k, total 1216k
[    8.778293] fbcon: VESA VGA (fb0) is primary device
[    8.778368] Console: switching to colour frame buffer device 80x30
[    8.778383] fb0: VESA VGA frame buffer device
[   10.333961] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.491832] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   10.744171] init: failsafe main process (841) killed by TERM signal
[   11.643473] type=1400 audit(1364120155.310:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=908 comm="apparmor_parser"
[   12.007335] audit_printk_skb: 39 callbacks suppressed
[   12.007339] type=1400 audit(1364120155.678:25): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=928 comm="apparmor_parser"
[   12.014643] type=1400 audit(1364120155.682:26): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=926 comm="apparmor_parser"
[   12.014654] type=1400 audit(1364120155.682:27): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=915 comm="apparmor_parser"
[   12.015199] type=1400 audit(1364120155.682:28): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=926 comm="apparmor_parser"
[   12.015209] type=1400 audit(1364120155.682:29): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=915 comm="apparmor_parser"
[   12.386384] Bluetooth: Core ver 2.16
[   12.386407] NET: Registered protocol family 31
[   12.386409] Bluetooth: HCI device and connection manager initialized
[   12.386413] Bluetooth: HCI socket layer initialized
[   12.386415] Bluetooth: L2CAP socket layer initialized
[   12.386429] Bluetooth: SCO socket layer initialized
[   12.410576] Bluetooth: RFCOMM TTY layer initialized
[   12.410582] Bluetooth: RFCOMM socket layer initialized
[   12.410584] Bluetooth: RFCOMM ver 1.11
[   13.210802] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.210805] Bluetooth: BNEP filters: protocol multicast
[   15.958869] e1000e 0000:03:00.0: irq 47 for MSI/MSI-X
[   16.012132] e1000e 0000:03:00.0: irq 47 for MSI/MSI-X
[   16.012691] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.013088] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  163.039312] usb 1-5: USB disconnect, device number 4
[  163.039506] option: option_instat_callback: error -108
[  163.039673] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  163.039712] option 1-5:1.0: device disconnected
[  163.039800] cdc_ether 1-5:1.1: wwan0: unregister 'cdc_ether' usb-0000:00:1d.7-5, Mobile Broadband Network Device
[  163.056971] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  163.057002] option 1-5:1.3: device disconnected
[  163.057195] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  163.057221] option 1-5:1.4: device disconnected
[  185.676024] usb 1-5: new high-speed USB device number 5 using ehci_hcd
[  185.812404] scsi7 : usb-storage 1-5:1.0
[  185.812866] scsi8 : usb-storage 1-5:1.1
[  185.813079] usb 1-5: USB disconnect, device number 5
[  189.896031] usb 1-5: new high-speed USB device number 6 using ehci_hcd
[  190.033248] option 1-5:1.0: GSM modem (1-port) converter detected
[  190.033525] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB0
[  190.036026] cdc_ether 1-5:1.1: wwan0: register 'cdc_ether' at usb-0000:00:1d.7-5, Mobile Broadband Network Device, 02:50:f3:00:00:00
[  190.036270] option 1-5:1.3: GSM modem (1-port) converter detected
[  190.036775] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB1
[  190.036923] option 1-5:1.4: GSM modem (1-port) converter detected
[  190.037045] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB2
[  190.037281] scsi9 : usb-storage 1-5:1.5
[  190.037609] scsi10 : usb-storage 1-5:1.6
[  191.038220] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  191.039602] scsi 10:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  191.043190] sr1: scsi-1 drive
[  191.043447] sr 9:0:0:0: Attached scsi CD-ROM sr1
[  191.044766] sr 9:0:0:0: Attached scsi generic sg3 type 5
[  191.047027] sd 10:0:0:0: Attached scsi generic sg4 type 0
[  191.049958] sd 10:0:0:0: [sdc] Attached SCSI removable disk
```

---

### Post by alexfish on 2013-03-24
[URL="http://ubuntuforums.org/member.php?u=1406577"]**[COLOR=#000000][/COLOR]**[COLOR=#000000]Hi vynonline

Best leave the card functionality as is

USB Modems on Ubuntu generally get switch by usb_modeswitch this is an all in package for switching modems with cd storage

IE the drivers for windows are usually stored on them , this has to be ejected just like a normal CD ,then the device is seen as a
modem , if it is an inconvence to plug and un-plug the modem can you put it on an usb lead ,

depending on Ubuntu version been used , but this sporadic behaviour generally dissapears after a few updates

Alex[/COLOR][B][COLOR=#000000]
[/COLOR][/B][/URL]

---

### Post by vynonline on 2013-03-27
Thanks for all of your help , I was not able to reply for a short time .

Yeah alexfish , I am going to leave my card functionality as it is. I am going to wait out for few more updates, But is there a way i can report this bug to canonical so that it will be fixed in most recent updates and rather than being forgotten about?

---

### Post by alexfish on 2013-03-27
Hi vynonline , will have alook though the bugs reports , but not sure if the problem is under control , may be it is.!

Reason have look though the Dmesg , First con fig shows the modem as generic , but then goes on to configure the Ether Interface

> 
[  190.033248] option 1-5:1.0: GSM modem (1-port) converter detected 
[  190.033525] usb 1-5:GSM modem (1-port) converter now attached to ttyUSB0  
[  190.036026]
 cdc_ether 1-5:1.1: wwan0: register 'cdc_ether' at usb-0000:00:1d.7-5, Mobile Broadband Network Device, 02:50:f3:00:00:00 [COLOR=#008000]<<<< THIS ONE .... ETHER INTERFACE[/COLOR]
[  190.036270] option 1-5:1.3: GSM modem (1-port) converter detected [  190.036775] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB1 <<< THIS OR
[  190.036923] option 1-5:1.4: GSM modem (1-port) converter detected [  190.037045] usb 1-5: GSM modem (1-port) converter now attached to ttyUSB2 <<< THIS For ETHER type connection
[  190.037281] scsi9 : usb-storage 1-5:1.5 [  190.037609] scsi10 : usb-storage 1-5:1.6 
[  191.038220] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2 
[  191.039602] scsi 10:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2So from what can be see This is the best Set Up for this type modem .

If the device connects on the correct port ' there are normally Two connection ports on these Types of devices , 
First is for standard 3/4g Second is for connecting to network + uses the Ether interface, Will look further into this.

Also should see the interface in network manager use the tool

command for this is

"nm-tool"

BR
Alex

---

### Post by vynonline on 2013-03-28
> **alexfish said:**
> Hi vynonline , will have alook though the bugs reports , but not sure if the problem is under control , may be it is.!

Reason have look though the Dmesg , First con fig shows the modem as generic , but then goes on to configure the Ether Interface

So from what can be see This is the best Set Up for this type modem .

If the device connects on the correct port ' there are normally Two connection ports on these Types of devices , 
First is for standard 3/4g Second is for connecting to network + uses the Ether interface, Will look further into this.

Also should see the interface in network manager use the tool

command for this is

"nm-tool"

BR
Alex

There was a lot of technical jargon in there which i quite didn't understand. ;)

I believe you meant that the device acts as an ethernet controller and also is a mobile broadband device, which is true as the mobile partner application in windows can make it configure to use either RAS ( modem\dial-up ) or NDIS modes, and ubuntu only identifies one port of it at a time.
The network sharing center in windows helps in connecting via both dial-up and Mobile broadband if configured. The dial up connection is represented as a normal wired connection and NDIS as a wireless connection.

Personally as a user, I dont feel this is the best set-up for this modem.

I was wondering if this post in the forum is enough to report this issue to ubuntu developers or is there a need to send bug reports to anyone in ubuntu development team.

---

### Post by alexfish on 2013-03-28
Know you can connect to the other port using ppp direct or wv dial , this frees up ttyUSB0 , which can be used for texting , have tested several of these device but did
not notice much difference in speed , exept the ether intrface makes  bridging a doddle  , can have a look through this old How To , see foot of post

Best go to End or near end of thread , there is a link for Huawei , also did a how to install + how to install only the bits required to switch the modem , IE Adapted the Script should switch most of Huawei devices

The choice is up to you s to a choice , but if go Huawei driver + MP Then Ether interface will be seen by NM but modem will not be seen by MM - "modem-manager" 

the one thing I did notice was the logging , the Syslog was choked with MP logging , hence why I did a mod on the Script.
[SIZE=2]
[/SIZE][h=3][SIZE=2] 				 					 						 					  					 					[How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]]("http://ubuntuforums.org/showthread.php?t=1466490") 				[/SIZE][/h]
BR

Alex

---

### Post by vynonline on 2013-03-29
Sorry to be still blabbering around. But i couldn't quite grasp the  contents of that large thread . Is this what you intend me to do?

> [FONT=Verdana][SIZE=2]**Some devices need time to settle**[/SIZE][/FONT][FONT=Verdana][SIZE=2] **:**  if there is sporadic identification of the device or the ports been  registered this may more notable in 10.04 , try connecting the device  after boot
**or**[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]
Add in [COLOR=Blue]/etc/modprobe.conf[/COLOR] a delay for the usb-storage[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2] 	Code:

 	
sudo gedit /etc/modprobe.conf 
[/SIZE][/FONT][FONT=Verdana][SIZE=2]add the following line 
 	Code:

 	
options usb-storage delay_use=1 
[/SIZE][/FONT]

OR :

> Can try this
 	Code:
 	
sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules 
scroll down to the line which shows the id's of the device

EXAMPLE:
 	 		 			 			 				# Huawei E169
[COLOR=Blue]ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"[/COLOR] 			 		
 	
 
disable the line with a** #** . Add a line so it looks like the below . also double check the ID's prior to saving
 	Code:
 	
# Huawei E169 #ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'" ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="/sbin/modprobe  option" 
save the file : unplug the device then reconnect : note  changes by using the "usb-devices" command

If the mode-switching has been disabled (**device not switching**) remove the "**#**": note changes by using the "usb-devices" command
**If the above has no effect reverse the changes **:

Sorry I didn't really get what is mentioned there.

---

### Post by vynonline on 2013-03-29
adding usb-storage delay didn't work. I even set the delay to 60 and could hear the tone for recognization after the delay.

```

# Huawei E173 (Viettel 3G)
ATTRS{idVendor}=="Huawei", ATTRS{idProduct}=="14b5", RUN+="usb_modeswitch '%b/%k'"

# Huawei E173
ATTRS{idVendor}=="Huawei", ATTRS{idProduct}=="1557", RUN+="usb_modeswitch '%b/%k'"

# Huawei E173s
ATTRS{idVendor}=="Huawei", ATTRS{idProduct}=="1c0b", RUN+="usb_modeswitch '%b/%k'"

```

No device with product id 1436 is shown . ( does 12d1 mean huawei?)
So does creating a new line with RUN+="usb_modeswitch '%b/%k'" for 1436 help?

---

### Post by alexfish on 2013-03-29
I said go to end of , IE , the last 2 or three pages of the the THREAD.

Also note the thread is for up to 11.04:: you are on 12+ , but the info at the end of thread may help.

IE with reference to YOUR DEVICE , There are methodes in the thread of how to Idendify the device,

Do not blindy post info From other Threads.


Alex

---

### Post by vynonline on 2013-03-30
Sorry. But I do have a doubt, if my device isn't listed in that 40-usb_modeswitch.rules . That should be the cause right? why modeswitch doesn't happen?

---

### Post by vynonline on 2013-03-30
Hey alexfish,

I installed huawei drivers and your usbmod script but stil i need to reconnect my device at every boot.

Thank you.

---

### Post by alexfish on 2013-03-30
Each device is different , I already mention Your device is configuring as it should be , as to , does it configure post or pre boot, does not
matter, this is mentioned in the how to, but do know that if connect to different port , then you get use of the divice as in other os's
only exeption is the ether port , only advantage of this is bridging, but this can also be achieved , best to read Ubuntu documentation,
If you read the end of the post there is a command to connect to connect to the second port,

If read through the how to , Carefully and digest the info , then eventually You will Succeed ,

That fact that the device does configure but not they way you expect it to be does no prove there is a bug,

Have fun

Alex

---

### Post by Jw_King on 2013-08-13
Hey Vynuponline,

I had the same problem with the same device. The problem is that usb_modeswitch switches the device from its default operation (product id 1446 which is a storage device) to the incorrect product id of 1436. In fact, it should change it to product id 140c, which is the correct product id for the modem. In order to make this happen, you need to make a small change to the usb_modechange configuration files. First open terminal. Then open the default configuration for usb_modeswitch for the huawei 1446 device with the following command: sudo nano /usr/share/usb_modeswitch/12d1:1446 . In the file which opens, you need to change the messagecontent to the following MessageContent="55534243000000000000000000000011060000000000000000000000000000" and save by ctrl-x, then yes. You'll note that there's just a one digit difference in the messagecontent with what was in the file. Now, after reboot, if you type lsusb in terminal you will see the modem correctly configured as 12d1:140c and you can connect with wvdial. 

Actually I  noted that sometimes the device still manages not to be switched at all by usb_modeswitch. This only seems to happen after a cold boot (i.e. power was removed from the device) and I'm still trying to figure this out. Anyway, unplug - replug works ...

---

### Post by vynonline on 2014-01-26
I have found a fix somewhat by installing the huawei provided driver. It is mentioned here : [http://www.huaweidevice.co.in/Downloads/Linux-Installation-User-Guide.pdf](http://www.huaweidevice.co.in/Downloads/Linux-Installation-User-Guide.pdf)

The driver required is here : [http://huaweifirmwares.com/download/huawei-linxu-driver-download/](http://huaweifirmwares.com/download/huawei-linxu-driver-download/)

It is necessary to only follow steps till page 4 of the pdf . ( till ./install ..... )

The above setup displays failure in ubuntu 13.04 + , but still the datacard will be detected in network-manager ( or modemmanager.. whatever it may be , it will be detected )

It als adds > xhost + in your autostart which is rumoured to be a security issue ..

EDIT:

Re enabling access control and removing HuaweiAutorun (xhost +) doesn't disrupt functionality of modem .. 
> 
xhost -
cd /etc/xdg/autostart/
rm -f HuaweiAutoStart.desktop

---

