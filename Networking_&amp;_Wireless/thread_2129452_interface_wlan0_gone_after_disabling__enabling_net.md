---
title: "interface wlan0 gone after disabling / enabling networking"
date: 2013-03-26
forum: Networking &amp; Wireless
---

### Post by mr5teff on 2013-03-26
Hey guys and gals!

I'm having quite a problem over here. After I recently disabled networking (via right click in NM applet) and enabling again my wlan0 interface has gone (my laptop was in stand-by in between) and so far no threads I was looking through on the web could help me on this issue. I tried several of the fixes they made but it seems as the problems have different causes.

Someone mentioned that the kernel may not be able to wake up the hardware again (I'm not experienced in the area around the kernel and driver issues).

Please could someone help me out here??

I'm using peppermint OS three (which is based on ubuntu 12.04) and here are some outputs I've seen being frequently asked for:
(I'm using my smartphone via USB to access my wifi just in case that'd be needed)


**ifconfig -a**
```

eth0      Link encap:Ethernet  HWaddr 48:5b:39:81:81:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168941 (168.9 KB)  TX bytes:168941 (168.9 KB)


usb0      Link encap:Ethernet  HWaddr 02:02:67:64:62:64  
          inet addr:192.168.42.207  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::2:67ff:fe64:6264/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11971 errors:2 dropped:0 overruns:0 frame:2
          TX packets:9300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12978477 (12.9 MB)  TX bytes:1595247 (1.5 MB)

```


**ifconfig wlan0 up**
```

wlan0: ERROR while getting interface flags: No such device

```


**/etc/init.d/networking restart**
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                            [ OK ] 

```


**lspci**
```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)

```


**lshw -C network**
```

  *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 48:5b:39:81:81:cf
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f9fc0000-f9ffffff ioport:ec00(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:02:67:64:62:64
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.207 link=yes multicast=yes

```


**dmesg**
```

[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f690000 (usable)
[    0.000000]  BIOS-e820: 000000007f690000 - 000000007f69e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f69e000 - 000000007f6e0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: ASUSTeK Computer INC. 1008PG/1008PG, BIOS 0501    03/26/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f690 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F700000 mask 0FFF00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] total RAM covered: 2039M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2039MB, range: 1MB, type UC
[    0.000000] reg 2, base: 2040MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 359a8000 - 36ccc000
[    0.000000] ACPI: RSDP 000fbf30 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 7f690100 0006C (v01 _ASUS_ Notebook 03001026 MSFT 00000097)
[    0.000000] ACPI: FACP 7f690290 000F4 (v04 A_M_I_ OEMFACP  03001026 MSFT 00000097)
[    0.000000] ACPI: DSDT 7f690490 083BD (v02  A1498 A1498000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7f69e000 00040
[    0.000000] ACPI: APIC 7f690390 0005C (v02 A_M_I_ OEMAPIC  03001026 MSFT 00000097)
[    0.000000] ACPI: MCFG 7f6903f0 0003C (v01 A_M_I_ OEMMCFG  03001026 MSFT 00000097)
[    0.000000] ACPI: ECDT 7f690430 00055 (v01 A_M_I_ OEMECDT  03001026 MSFT 00000097)
[    0.000000] ACPI: OEMB 7f69e040 00061 (v01 A_M_I_ AMI_OEM  03001026 MSFT 00000097)
[    0.000000] ACPI: HPET 7f698850 00038 (v01 A_M_I_ OEMHPET  03001026 MSFT 00000097)
[    0.000000] ACPI: GSCI 7f69e0b0 02024 (v01 A_M_I_ GMCHSCI  03001026 MSFT 00000097)
[    0.000000] ACPI: SSDT 7f6a0df0 004F0 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: SLIC 7f698890 00176 (v01 _ASUS_ Notebook 03001026 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f690
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f690
[    0.000000] On node 0 totalpages: 521759
[    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map f49b8200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292244 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s31616 r0 d21632 u2097152
[    0.000000] pcpu-alloc: s31616 r0 d21632 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517681
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=35668265-1ebf-41ac-a8d0-8a8261ac48d4 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8349696 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f690)
[    0.000000] Memory: 2031976k/2087488k available (5627k kernel code, 55060k reserved, 2764k data, 712k init, 1178184k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
[    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.472 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.94 BogoMIPS (lpj=6649888)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004065] Security Framework initialized
[    0.004103] AppArmor: AppArmor initialized
[    0.004108] Yama: becoming mindful.
[    0.004228] Mount-cache hash table entries: 512
[    0.004495] Initializing cgroup subsys cpuacct
[    0.004510] Initializing cgroup subsys memory
[    0.004528] Initializing cgroup subsys devices
[    0.004534] Initializing cgroup subsys freezer
[    0.004540] Initializing cgroup subsys blkio
[    0.004556] Initializing cgroup subsys perf_event
[    0.004605] CPU: Physical Processor ID: 0
[    0.004610] CPU: Processor Core ID: 0
[    0.004616] mce: CPU supports 5 MCE banks
[    0.004630] CPU0: Thermal monitoring enabled (TM2)
[    0.004638] using mwait in idle threads.
[    0.009298] ACPI: Core revision 20110623
[    0.024026] ftrace: allocating 25954 entries in 51 pages
[    0.032094] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032585] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074424] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.076004] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.076004] ... version:                3
[    0.076004] ... bit width:              40
[    0.076004] ... generic registers:      2
[    0.076004] ... value mask:             000000ffffffffff
[    0.076004] ... max period:             000000007fffffff
[    0.076004] ... fixed-purpose events:   3
[    0.076004] ... event mask:             0000000700000003
[    0.076004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.076004] CPU 1 irqstacks, hard=f3cea000 soft=f3cec000
[    0.076004] Booting Node   0, Processors  #1 Ok.
[    0.076004] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.164063] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164146] Brought up 2 CPUs
[    0.164155] Total of 2 processors activated (6649.93 BogoMIPS).
[    0.164719] devtmpfs: initialized
[    0.164719] EVM: security.selinux
[    0.164719] EVM: security.SMACK64
[    0.164719] EVM: security.capability
[    0.164719] PM: Registering ACPI NVS region at 7f69e000 (270336 bytes)
[    0.168652] print_constraints: dummy: 
[    0.168704] RTC time: 11:41:06, date: 03/26/13
[    0.168792] NET: Registered protocol family 16
[    0.168887] Trying to unpack rootfs image as initramfs...
[    0.169232] EISA bus registered
[    0.169326] ACPI: bus type pci registered
[    0.169526] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.169537] PCI: not using MMCONFIG
[    0.169814] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.169822] PCI: Using configuration type 1 for base access
[    0.184234] bio: create slab <bio-0> at 0
[    0.184550] ACPI: Added _OSI(Module Device)
[    0.184559] ACPI: Added _OSI(Processor Device)
[    0.184567] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.184575] ACPI: Added _OSI(Processor Aggregator Device)
[    0.189469] ACPI: EC: EC description table is found, configuring boot EC
[    0.194623] ACPI: Executed 1 blocks of module-level executable AML code
[    0.205116] ACPI: SSDT 7f6a0300 00326 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.208936] ACPI: Dynamic OEM Table Load:
[    0.208948] ACPI: SSDT   (null) 00326 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.209486] ACPI: SSDT 7f6a06c0 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.210629] ACPI: Dynamic OEM Table Load:
[    0.210641] ACPI: SSDT   (null) 00724 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.211509] ACPI: SSDT 7f6a00e0 00217 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.212821] ACPI: Dynamic OEM Table Load:
[    0.212833] ACPI: SSDT   (null) 00217 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.213159] ACPI: SSDT 7f6a0630 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.214317] ACPI: Dynamic OEM Table Load:
[    0.214329] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.214933] ACPI: Interpreter enabled
[    0.214958] ACPI: (supports S0 S3 S4 S5)
[    0.215020] ACPI: Using IOAPIC for interrupt routing
[    0.215109] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.216781] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.216791] PCI: Using MMCONFIG for extended config space
[    0.230949] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.234544] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.235091] ACPI: No dock devices found.
[    0.235099] HEST: Table not found.
[    0.235111] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.235364] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.235873] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.235884] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.235895] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.235905] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.235915] pci_root PNP0A08:00: host bridge window [mem 0x7f700000-0xfed8ffff]
[    0.235949] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.236068] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.236091] pci 0000:00:02.0: reg 10: [mem 0xf9e00000-0xf9e7ffff]
[    0.236106] pci 0000:00:02.0: reg 14: [io  0xdc00-0xdc07]
[    0.236120] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.236134] pci 0000:00:02.0: reg 1c: [mem 0xf9d00000-0xf9dfffff]
[    0.236205] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.236225] pci 0000:00:02.1: reg 10: [mem 0xf9e80000-0xf9efffff]
[    0.236373] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.236409] pci 0000:00:1b.0: reg 10: [mem 0xf9cf8000-0xf9cfbfff 64bit]
[    0.236545] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.236558] pci 0000:00:1b.0: PME# disabled
[    0.236605] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.236755] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.236767] pci 0000:00:1c.0: PME# disabled
[    0.236820] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.236963] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.236975] pci 0000:00:1c.2: PME# disabled
[    0.237025] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.237167] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.237179] pci 0000:00:1c.3: PME# disabled
[    0.237233] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.237312] pci 0000:00:1d.0: reg 20: [io  0xd400-0xd41f]
[    0.237379] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.237454] pci 0000:00:1d.1: reg 20: [io  0xd480-0xd49f]
[    0.237518] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.237593] pci 0000:00:1d.2: reg 20: [io  0xd800-0xd81f]
[    0.237657] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.237731] pci 0000:00:1d.3: reg 20: [io  0xd880-0xd89f]
[    0.237811] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.237848] pci 0000:00:1d.7: reg 10: [mem 0xf9cf7c00-0xf9cf7fff]
[    0.237983] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.237995] pci 0000:00:1d.7: PME# disabled
[    0.238035] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.238175] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.238365] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.238405] pci 0000:00:1f.2: reg 10: [io  0xd080-0xd087]
[    0.238427] pci 0000:00:1f.2: reg 14: [io  0xd000-0xd003]
[    0.238447] pci 0000:00:1f.2: reg 18: [io  0xcc00-0xcc07]
[    0.238468] pci 0000:00:1f.2: reg 1c: [io  0xc880-0xc883]
[    0.238489] pci 0000:00:1f.2: reg 20: [io  0xc800-0xc81f]
[    0.238510] pci 0000:00:1f.2: reg 24: [mem 0xf9cf7800-0xf9cf7bff]
[    0.238598] pci 0000:00:1f.2: PME# supported from D3hot
[    0.238610] pci 0000:00:1f.2: PME# disabled
[    0.238720] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.238819] pci 0000:00:1c.2: PCI bridge to [bus 02-03]
[    0.238836] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.238853] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf8ffffff 64bit pref]
[    0.238977] pci 0000:01:00.0: [1969:1062] type 0 class 0x000200
[    0.239023] pci 0000:01:00.0: reg 10: [mem 0xf9fc0000-0xf9ffffff 64bit]
[    0.239050] pci 0000:01:00.0: reg 18: [io  0xec00-0xec7f]
[    0.239227] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.239240] pci 0000:01:00.0: PME# disabled
[    0.244080] pci 0000:00:1c.3: PCI bridge to [bus 01-01]
[    0.244096] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.244109] pci 0000:00:1c.3:   bridge window [mem 0xf9f00000-0xf9ffffff]
[    0.244238] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.244264] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.244274] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.244284] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.244295] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.244305] pci 0000:00:1e.0:   bridge window [mem 0x7f700000-0xfed8ffff] (subtractive decode)
[    0.244348] pci_bus 0000:00: on NUMA node 0
[    0.244366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.244766] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.244904] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.244981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.245069]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.245082]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.245090] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.263969] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.264187] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.264361] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.264526] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.264715] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.264886] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.265054] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.265222] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.265576] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.265607] vgaarb: loaded
[    0.265614] vgaarb: bridge control possible 0000:00:02.0
[    0.266029] i2c-core: driver [aat2870] using legacy suspend method
[    0.266037] i2c-core: driver [aat2870] using legacy resume method
[    0.266297] SCSI subsystem initialized
[    0.266468] libata version 3.00 loaded.
[    0.266648] usbcore: registered new interface driver usbfs
[    0.266697] usbcore: registered new interface driver hub
[    0.266809] usbcore: registered new device driver usb
[    0.267136] PCI: Using ACPI for IRQ routing
[    0.267200] PCI: pci_cache_line_size set to 64 bytes
[    0.267327] Expanded resource reserved due to conflict with PCI Bus 0000:00
[    0.267336] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.267345] reserve RAM buffer: 000000007f690000 - 000000007fffffff 
[    0.267680] NetLabel: Initializing
[    0.267687] NetLabel:  domain hash size = 128
[    0.267692] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.267724] NetLabel:  unlabeled traffic allowed by default
[    0.267902] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.267917] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.267933] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.272556] Switching to clocksource hpet
[    0.296099] AppArmor: AppArmor Filesystem Enabled
[    0.296167] pnp: PnP ACPI init
[    0.296220] ACPI: bus type pnp registered
[    0.296502] pnp 00:00: [bus 00-ff]
[    0.296513] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.296523] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.296532] pnp 00:00: [io  0x0d00-0xffff window]
[    0.296541] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.296551] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.296559] pnp 00:00: [mem 0x7f700000-0xfed8ffff window]
[    0.296742] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.296784] pnp 00:01: [mem 0xfed14000-0xfed19fff]
[    0.296793] pnp 00:01: [mem 0xfed90000-0xfed93fff]
[    0.296918] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.296929] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.296940] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.297045] pnp 00:02: [dma 4]
[    0.297054] pnp 00:02: [io  0x0000-0x000f]
[    0.297062] pnp 00:02: [io  0x0081-0x0083]
[    0.297069] pnp 00:02: [io  0x0087]
[    0.297076] pnp 00:02: [io  0x0089-0x008b]
[    0.297084] pnp 00:02: [io  0x008f]
[    0.297091] pnp 00:02: [io  0x00c0-0x00df]
[    0.297185] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.297226] pnp 00:03: [io  0x0070-0x0071]
[    0.297250] pnp 00:03: [irq 8]
[    0.297334] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.297446] pnp 00:04: [io  0x0060]
[    0.297454] pnp 00:04: [io  0x0064]
[    0.297471] pnp 00:04: [irq 1]
[    0.297570] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.297680] pnp 00:05: [irq 12]
[    0.297779] pnp 00:05: Plug and Play ACPI device, IDs SYN0a13 SYN0a00 SYN0002 PNP0f13 (active)
[    0.297814] pnp 00:06: [io  0x0061]
[    0.297901] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.297935] pnp 00:07: [io  0x00f0-0x00ff]
[    0.297951] pnp 00:07: [irq 13]
[    0.298043] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.298448] pnp 00:08: [io  0x0010-0x001f]
[    0.298458] pnp 00:08: [io  0x0022-0x003f]
[    0.298467] pnp 00:08: [io  0x0044-0x004d]
[    0.298480] pnp 00:08: [io  0x0050-0x005e]
[    0.298487] pnp 00:08: [io  0x0063]
[    0.298494] pnp 00:08: [io  0x0065]
[    0.298502] pnp 00:08: [io  0x0067-0x006f]
[    0.298510] pnp 00:08: [io  0x0072-0x007f]
[    0.298517] pnp 00:08: [io  0x0080]
[    0.298525] pnp 00:08: [io  0x0084-0x0086]
[    0.298531] pnp 00:08: [io  0x0088]
[    0.298539] pnp 00:08: [io  0x008c-0x008e]
[    0.298547] pnp 00:08: [io  0x0090-0x009f]
[    0.298555] pnp 00:08: [io  0x00a2-0x00bf]
[    0.298563] pnp 00:08: [io  0x00e0-0x00ef]
[    0.298570] pnp 00:08: [io  0x025c-0x025f]
[    0.298578] pnp 00:08: [io  0x0380-0x0383]
[    0.298586] pnp 00:08: [io  0x0400-0x041f]
[    0.298594] pnp 00:08: [io  0x04d0-0x04d1]
[    0.298602] pnp 00:08: [io  0x0800-0x087f]
[    0.298611] pnp 00:08: [io  0x0400-0x03ff disabled]
[    0.298619] pnp 00:08: [io  0x0480-0x04bf]
[    0.298628] pnp 00:08: [mem 0xfed1c000-0xfed1ffff]
[    0.298637] pnp 00:08: [mem 0xfed20000-0xfed3ffff]
[    0.298645] pnp 00:08: [mem 0xfed50000-0xfed8ffff]
[    0.298653] pnp 00:08: [mem 0xffb00000-0xffbfffff]
[    0.298661] pnp 00:08: [mem 0xfff00000-0xffffffff]
[    0.298862] system 00:08: [io  0x025c-0x025f] has been reserved
[    0.298873] system 00:08: [io  0x0380-0x0383] has been reserved
[    0.298883] system 00:08: [io  0x0400-0x041f] has been reserved
[    0.298892] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.298902] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.298912] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.298923] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.298934] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.298944] system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.298954] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.298964] system 00:08: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.298977] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.299194] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.299291] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.299481] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.299490] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.299647] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.299659] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.299671] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.299797] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.299950] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.299962] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.300744] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.300754] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.300763] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.300771] pnp 00:0c: [mem 0x00100000-0x7f6fffff]
[    0.300779] pnp 00:0c: [mem 0xfed90000-0xffffffff]
[    0.300991] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.301003] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.301014] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.301024] system 00:0c: [mem 0x00100000-0x7f6fffff] could not be reserved
[    0.301035] system 00:0c: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.301047] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.301642] pnp: PnP ACPI: found 13 devices
[    0.301651] ACPI: ACPI bus type pnp unregistered
[    0.301660] PnPBIOS: Disabled by ACPI PNP
[    0.343264] PCI: max bus depth: 1 pci_try_num: 2
[    0.343346] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.343361] pci 0000:00:1c.2: BAR 13: assigned [io  0x1000-0x1fff]
[    0.343372] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80200000-0x803fffff]
[    0.343385] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.343397] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.343407] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.343417] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.343430] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff]
[    0.343443] pci 0000:00:1c.0:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.343459] pci 0000:00:1c.2: PCI bridge to [bus 02-03]
[    0.343469] pci 0000:00:1c.2:   bridge window [io  0x1000-0x1fff]
[    0.343483] pci 0000:00:1c.2:   bridge window [mem 0xfa000000-0xfbffffff]
[    0.343495] pci 0000:00:1c.2:   bridge window [mem 0xf4000000-0xf8ffffff 64bit pref]
[    0.343512] pci 0000:00:1c.3: PCI bridge to [bus 01-01]
[    0.343521] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    0.343535] pci 0000:00:1c.3:   bridge window [mem 0xf9f00000-0xf9ffffff]
[    0.343548] pci 0000:00:1c.3:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.343564] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.343598] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.343636] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.343650] pci 0000:00:1c.0: setting latency timer to 64
[    0.343667] pci 0000:00:1c.2: enabling device (0106 -> 0107)
[    0.343691] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.343703] pci 0000:00:1c.2: setting latency timer to 64
[    0.343733] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.343746] pci 0000:00:1c.3: setting latency timer to 64
[    0.343766] pci 0000:00:1e.0: setting latency timer to 64
[    0.343779] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.343788] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.343798] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.343807] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.343817] pci_bus 0000:00: resource 8 [mem 0x7f700000-0xfed8ffff]
[    0.343826] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.343835] pci_bus 0000:04: resource 1 [mem 0x80200000-0x803fffff]
[    0.343844] pci_bus 0000:04: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.343853] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.343862] pci_bus 0000:02: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.343871] pci_bus 0000:02: resource 2 [mem 0xf4000000-0xf8ffffff 64bit pref]
[    0.343881] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.343889] pci_bus 0000:01: resource 1 [mem 0xf9f00000-0xf9ffffff]
[    0.343899] pci_bus 0000:01: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.343908] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.343917] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.343926] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.343934] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.343944] pci_bus 0000:05: resource 8 [mem 0x7f700000-0xfed8ffff]
[    0.344098] NET: Registered protocol family 2
[    0.344286] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.344939] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.346022] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.346575] TCP: Hash tables configured (established 131072 bind 65536)
[    0.346586] TCP reno registered
[    0.346599] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.346624] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.346852] NET: Registered protocol family 1
[    0.346899] pci 0000:00:02.0: Boot video device
[    0.346973] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.347004] pci 0000:00:1d.0: PCI INT A disabled
[    0.347025] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.347053] pci 0000:00:1d.1: PCI INT B disabled
[    0.347074] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.347102] pci 0000:00:1d.2: PCI INT C disabled
[    0.347123] pci 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.347151] pci 0000:00:1d.3: PCI INT D disabled
[    0.347174] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.347231] pci 0000:00:1d.7: PCI INT A disabled
[    0.347267] PCI: CLS 32 bytes, default 64
[    0.348407] audit: initializing netlink socket (disabled)
[    0.348434] type=2000 audit(1364298065.344:1): initialized
[    0.411097] highmem bounce pool size: 64 pages
[    0.411114] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.427168] VFS: Disk quotas dquot_6.5.2
[    0.427379] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.429317] fuse init (API version 7.17)
[    0.429637] msgmni has been set to 1667
[    0.430803] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.430914] io scheduler noop registered
[    0.430921] io scheduler deadline registered
[    0.430953] io scheduler cfq registered (default)
[    0.431274] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.431367] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.431522] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.431609] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    0.431764] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.431846] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.432122] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.432205] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.432431] intel_idle: MWAIT substates: 0x20220
[    0.432449] intel_idle: v0.4 model 0x1C
[    0.432454] intel_idle: lapic_timer_reliable_states 0x2
[    0.432462] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.432631] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.432786] ACPI: AC Adapter [AC0] (on-line)
[    0.433015] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.438236] ACPI: Lid Switch [LID]
[    0.438431] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.438447] ACPI: Sleep Button [SLPB]
[    0.438599] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.438611] ACPI: Power Button [PWRB]
[    0.438764] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.438777] ACPI: Power Button [PWRF]
[    0.452294] thermal LNXTHERM:00: registered as thermal_zone0
[    0.452304] ACPI: Thermal Zone [TZ00] (34 C)
[    0.452391] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.452420] ACPI: Battery Slot [BAT0] (battery present)
[    0.452526] ERST: Table is not found!
[    0.452532] GHES: HEST is not enabled!
[    0.452830] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.453522] isapnp: Scanning for PnP cards...
[    0.556902] ACPI: Battery Slot [BAT0] (battery present)
[    0.808301] isapnp: No Plug & Play device found
[    1.207317] Freeing initrd memory: 19600k freed
[    1.265061] Linux agpgart interface v0.103
[    1.265239] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.265409] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.265644] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.265905] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.270141] brd: module loaded
[    1.272409] loop: module loaded
[    1.272719] ahci 0000:00:1f.2: version 3.0
[    1.272767] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.272850] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.272954] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    1.272963] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.272973] ahci 0000:00:1f.2: setting latency timer to 64
[    1.274167] scsi0 : ahci
[    1.274405] scsi1 : ahci
[    1.274615] scsi2 : ahci
[    1.274815] scsi3 : ahci
[    1.275301] ata1: SATA max UDMA/133 abar m1024@0xf9cf7800 port 0xf9cf7900 irq 43
[    1.275308] ata2: DUMMY
[    1.275312] ata3: DUMMY
[    1.275316] ata4: DUMMY
[    1.276679] Fixed MDIO Bus: probed
[    1.276743] tun: Universal TUN/TAP device driver, 1.6
[    1.276748] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.276907] PPP generic driver version 2.4.2
[    1.277182] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.277231] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.277268] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.277276] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.277403] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.277441] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.277459] ehci_hcd 0000:00:1d.7: debug port 1
[    1.281356] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.281396] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9cf7c00
[    1.296035] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.296358] hub 1-0:1.0: USB hub found
[    1.296371] hub 1-0:1.0: 8 ports detected
[    1.296549] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.296587] uhci_hcd: USB Universal Host Controller Interface driver
[    1.296636] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.296659] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.296666] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.296808] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.296849] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    1.297185] hub 2-0:1.0: USB hub found
[    1.297197] hub 2-0:1.0: 2 ports detected
[    1.297338] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.297355] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.297362] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.297485] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.297545] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    1.297875] hub 3-0:1.0: USB hub found
[    1.297886] hub 3-0:1.0: 2 ports detected
[    1.298030] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.298046] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.298053] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.298178] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.298235] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    1.298578] hub 4-0:1.0: USB hub found
[    1.298590] hub 4-0:1.0: 2 ports detected
[    1.298727] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.298744] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.298751] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.298896] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.298954] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    1.299286] hub 5-0:1.0: USB hub found
[    1.299298] hub 5-0:1.0: 2 ports detected
[    1.299583] usbcore: registered new interface driver libusual
[    1.299705] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.318156] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.318179] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.318562] mousedev: PS/2 mouse device common for all mice
[    1.319530] rtc_cmos 00:03: RTC can wake from S4
[    1.319741] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.319786] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.319966] device-mapper: uevent: version 1.0.3
[    1.320215] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.320314] EISA: Probing bus 0 at eisa.0
[    1.320321] EISA: Cannot allocate resource for mainboard
[    1.320328] Cannot allocate resource for EISA slot 1
[    1.320333] Cannot allocate resource for EISA slot 2
[    1.320339] Cannot allocate resource for EISA slot 3
[    1.320344] Cannot allocate resource for EISA slot 4
[    1.320349] Cannot allocate resource for EISA slot 5
[    1.320355] Cannot allocate resource for EISA slot 6
[    1.320360] Cannot allocate resource for EISA slot 7
[    1.320366] Cannot allocate resource for EISA slot 8
[    1.320370] EISA: Detected 0 cards.
[    1.320387] cpufreq-nforce2: No nForce2 chipset.
[    1.320561] cpuidle: using governor ladder
[    1.320853] cpuidle: using governor menu
[    1.320858] EFI Variables Facility v0.08 2004-May-17
[    1.321459] TCP cubic registered
[    1.321756] NET: Registered protocol family 10
[    1.323206] NET: Registered protocol family 17
[    1.323255] Registering the dns_resolver key type
[    1.323305] Using IPI No-Shortcut mode
[    1.323722] PM: Hibernation image not present or could not be loaded.
[    1.323748] registered taskstats version 1
[    1.339412] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.345312]   Magic number: 5:234:682
[    1.345470] rtc_cmos 00:03: setting system clock to 2013-03-26 11:41:07 UTC (1364298067)
[    1.346517] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.346523] EDD information not available.
[    1.592113] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.593416] ata1.00: unexpected _GTF length (8)
[    1.593695] ata1.00: ATA-8: WDC WD2500BEVT-80A23T0, 01.01A01, max UDMA/133
[    1.593703] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.595027] ata1.00: unexpected _GTF length (8)
[    1.595306] ata1.00: configured for UDMA/133
[    1.595615] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-8 01.0 PQ: 0 ANSI: 5
[    1.595963] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.596093] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.596201] sd 0:0:0:0: [sda] Write Protect is off
[    1.596212] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.596299] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.608096] usb 1-6: new high-speed USB device number 2 using ehci_hcd
[    1.649089]  sda: sda1 sda2 < sda5 > sda3
[    1.650309] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.650379] Freeing unused kernel memory: 712k freed
[    1.650863] Write protecting the kernel text: 5628k
[    1.650954] Write protecting the kernel read-only data: 2324k
[    1.695714] udevd[93]: starting version 175
[    1.860137] usb 1-8: new high-speed USB device number 3 using ehci_hcd
[    1.863328] wmi: Mapper loaded
[    1.962281] atl1c 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.962310] atl1c 0000:01:00.0: setting latency timer to 64
[    1.984113] [drm] Initialized drm 1.1.0 20060810
[    2.022298] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.022366] i915 0000:00:02.0: setting latency timer to 64
[    2.072432] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    2.072447] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.072454] [drm] Driver supports precise vblank timestamp query.
[    2.094118] atl1c 0000:01:00.0: version 1.0.1.0-NAPI
[    2.128346] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.459213] [drm] initialized overlay support
[    2.477286] fbcon: inteldrmfb (fb0) is primary device
[    2.477442] Console: switching to colour frame buffer device 128x37
[    2.477518] fb0: inteldrmfb frame buffer device
[    2.477524] drm: registered panic notifier
[    2.493485] acpi device:2c: registered as cooling_device2
[    2.493771] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.493973] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.494055] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.494118] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   16.138767] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.166904] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.188860] udevd[313]: starting version 175
[   16.294781] lp: driver loaded but no devices found
[   16.883522] Bluetooth: Core ver 2.16
[   16.883718] NET: Registered protocol family 31
[   16.883726] Bluetooth: HCI device and connection manager initialized
[   16.883735] Bluetooth: HCI socket layer initialized
[   16.883743] Bluetooth: L2CAP socket layer initialized
[   16.883765] Bluetooth: SCO socket layer initialized
[   16.910406] ppdev: user-space parallel port driver
[   16.936122] Bluetooth: RFCOMM TTY layer initialized
[   16.936140] Bluetooth: RFCOMM socket layer initialized
[   16.936148] Bluetooth: RFCOMM ver 1.11
[   16.955499] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.955510] Bluetooth: BNEP filters: protocol multicast
[   17.198568] type=1400 audit(1364298083.347:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=562 comm="apparmor_parser"
[   17.200810] type=1400 audit(1364298083.351:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=562 comm="apparmor_parser"
[   17.434206] Linux video capture interface: v2.00
[   17.449017] uvcvideo: Found UVC 1.00 device USB2.0 UVC 1.3M WebCam (13d3:5116)
[   17.456416] input: USB2.0 UVC 1.3M WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input6
[   17.456950] usbcore: registered new interface driver uvcvideo
[   17.456959] USB Video Class driver (1.1.1)
[   17.486221] usbcore: registered new interface driver usbserial
[   17.486295] USB Serial support registered for generic
[   17.486421] usbcore: registered new interface driver usbserial_generic
[   17.486429] usbserial: USB Serial Driver core
[   17.504519] USB Serial support registered for GSM modem (1-port)
[   17.504803] option 1-8:1.0: GSM modem (1-port) converter detected
[   17.507510] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
[   17.507587] option 1-8:1.1: GSM modem (1-port) converter detected
[   17.532356] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
[   17.532434] option 1-8:1.2: GSM modem (1-port) converter detected
[   17.537516] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
[   17.537583] usbcore: registered new interface driver option
[   17.537591] option: v0.7.2:USB Driver for GSM modems
[   17.719490] type=1400 audit(1364298083.867:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=639 comm="apparmor_parser"
[   17.724133] type=1400 audit(1364298083.875:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=639 comm="apparmor_parser"
[   17.729025] type=1400 audit(1364298083.879:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=639 comm="apparmor_parser"
[   17.755482] type=1400 audit(1364298083.903:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=644 comm="apparmor_parser"
[   17.757919] type=1400 audit(1364298083.907:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=644 comm="apparmor_parser"
[   17.758837] type=1400 audit(1364298083.907:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=644 comm="apparmor_parser"
[   17.767507] type=1400 audit(1364298083.915:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=643 comm="apparmor_parser"
[   17.774240] type=1400 audit(1364298083.923:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=646 comm="apparmor_parser"
[   18.187956] init: failsafe main process (669) killed by TERM signal
[   18.294545] asus_wmi: ASUS WMI generic driver loaded
[   18.296938] asus_wmi: Initialization: 0x0
[   18.297054] asus_wmi: BIOS WMI version: 0.8
[   18.297276] asus_wmi: SFUN value: 0x0
[   18.326328] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input7
[   18.453001] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04733/0xa40000/0xa0000
[   18.525334] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   18.848963] atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
[   18.861258] asus_wmi: Backlight controlled by ACPI video driver
[   18.874817] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.874928] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.874990] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   18.909073] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.912079] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.151310] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.151875] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.966565] Adding 975868k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:975868k 
[  415.120096] usb 1-1: new high-speed USB device number 4 using ehci_hcd
[  439.960764] usb 1-1: USB disconnect, device number 4
[  440.332133] usb 1-1: new high-speed USB device number 5 using ehci_hcd
[  440.578645] usbcore: registered new interface driver cdc_ether
[  440.586161] rndis_host 1-1:1.0: usb0: register 'rndis_host' at usb-0000:00:1d.7-1, RNDIS device, 02:02:67:64:62:64
[  440.589551] usbcore: registered new interface driver rndis_host
[  451.232064] usb0: no IPv6 routers present

```

---

### Post by Iowan on 2013-03-26
I'd ask about  **rfkill list**, but the fact that the adapter doesn't show up in the hardware lists is bewildering. 
I presume it is also missing from */etc/udev/rules.d/70-persistent-net.rules*.

---

### Post by mr5teff on 2013-03-27
Hi Iowan!

Thanks for your reply. I too assume something bad :(

Le outputs:

**rfkill list**
```

0: asus-wlan: Wireless LAN	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: asus-wwan3g: Wireless WAN
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```


**/etc/udev/rules.d/70-persistent-net.rules**
```

# This file maintains persistent names for network interfaces.# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="48:5b:39:81:81:cf", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="1c:4b:d6:67:a9:23", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x0cf3:0x9271 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="d8:5d:4c:90:72:79", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

```


The USB is the one I'm having plugged in, but at least here there is something mentioned of wlan0. Unfortunately I don't have a clue here :(.
Do you have any idea?

---

### Post by schragge on 2013-03-27
> **Iowan said:**
> the fact that the adapter doesn't show up in the hardware lists is bewildering.This doesn't wonder me as on my system the ethernet controller gets displayed as bridge device:
```

[color=green]$[/color] sudo lshw -short -C bridge
[color=green]H/W path    Device     Class       Description
==============================================
/0/1                   bridge      CK804 ISA Bridge
/0/9                   bridge      CK804 PCI Bridge
/0/a        eth0       bridge      CK804 Ethernet Controller
/0/b                   bridge      CK804 PCIE Bridge
/0/c                   bridge      CK804 PCIE Bridge
/0/d                   bridge      CK804 PCIE Bridge
/0/e                   bridge      CK804 PCIE Bridge
/0/100                 bridge      K8 [Athlon64/Opteron] HyperTransport Technolo
/0/101                 bridge      K8 [Athlon64/Opteron] Address Map
/0/102                 bridge      K8 [Athlon64/Opteron] DRAM Controller
/0/103                 bridge      K8 [Athlon64/Opteron] Miscellaneous Control
[/color]
```

The udev rule hints at [ath9k](http://linuxwireless.org/en/users/Drivers/ath9k) as appropriate kernel driver. Perhaps compiling a newer version from [compat-wireless](http://linuxwireless.org/en/users/Download/stable/) would help?

---

### Post by mr5teff on 2013-03-28
Hi all!

Sorry for the late reply, I was travelling to my hometown. 
Anyway, the magic of Linux stroke again. It works again. Without having done anything at all. Why? No clue. :P

I can remember having read somewhere that if the hardware can't be "woken up" it might help to take out the battery and keeping your on/off switch pressed for 30 seconds and thus resetting the hardware to default. Tried it but to no avail, so I can't guarantee if this is a valid approach.
But it might be sth similiar.
For me, I had the laptop turned on the last time yesterday around noon, then packed stuff and everything and just now having it turned on again, so it was turned off for more than 24 hours. Maybe that has to do anything with it.

Well, at least it works again. :)

Thank you for your replies and happy coding! :)

Greetz
Stefan

---

