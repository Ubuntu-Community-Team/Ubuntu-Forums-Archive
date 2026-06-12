---
title: "Linksys WUSB54GC / Ubuntu 12.04.2 LTS/ PC"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by lma33 on 2013-02-03
lsusb
```

Bus 001 Device 003: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2070L]

```lsb_release -d
```

Description:    Ubuntu 12.04.2 LTS

```uname -mr
```

3.2.0-37-generic-pae i686

```ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:14:85:32:14:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x6000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17293 (17.2 KB)  TX bytes:17293 (17.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:9c:a0:12:28  
          inet addr:192.168.1.154  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:9cff:fea0:1228/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2609388 (2.6 MB)  TX bytes:135046 (135.0 KB)


```iwconfig wlan0
```

wlan0     IEEE 802.11bg  ESSID:"Imgo"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:8C:3E:09:3F   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:66   Missed beacon:0


```lsmod
```

Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
vesafb                 13516  1 
ppdev                  12849  0 
arc4                   12473  2 
nvidia              10257747  40 
rt2800usb              22373  0 
snd_intel8x0           33455  2 
rt2800lib              53298  1 rt2800usb
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
serio_raw              13027  0 
snd_seq_midi           13132  0 
cfg80211              178877  2 rt2x00lib,mac80211
k8temp                 12905  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
pata_amd               13750  0 
sata_nv                23360  4 
forcedeth              58096  0 

```dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-37-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58-Ubuntu SMP Thu Jan 24 15:51:02 UTC 2013 (Ubuntu 3.2.0-37.58-generic-pae 3.2.35)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfff0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000bfff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff3000 - 00000000c0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI:    /GA-K8N-SLi, BIOS F2 07/27/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbfff0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f52c0] f52c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffa000-2000000
[    0.000000] RAMDISK: 364ea000 - 3726d000
[    0.000000] ACPI: RSDP 000f6c50 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT bfff3000 00030 (v01 Nvidia AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: FACP bfff3040 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: DSDT bfff30c0 04BF2 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS bfff0000 00040
[    0.000000] ACPI: MCFG bfff7d40 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: APIC bfff7cc0 0007C (v01 Nvidia AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2179MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x000bfff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfff0
[    0.000000] On node 0 totalpages: 786303
[    0.000000] free_area_init_node: node 0, pgdat c186b400, node_mem_map f4cea200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4360 pages used for memmap
[    0.000000]   HighMem zone: 553706 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780159
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-37-generic-pae root=UUID=46939b82-4154-4768-b67c-d48999f50d4c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12582400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bfff0)
[    0.000000] Memory: 3083144k/3145664k available (5826k kernel code, 62068k reserved, 2848k data, 744k init, 2232264k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1933000   ( 744 kB)
[    0.000000]       .data : 0xc15b08fc - 0xc1878c40   (2848 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b08fc   (5826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2010.370 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4020.74 BogoMIPS (lpj=8041480)
[    0.008015] pid_max: default: 32768 minimum: 301
[    0.008045] Security Framework initialized
[    0.008078] AppArmor: AppArmor initialized
[    0.008081] Yama: becoming mindful.
[    0.008157] Mount-cache hash table entries: 512
[    0.008335] Initializing cgroup subsys cpuacct
[    0.008343] Initializing cgroup subsys memory
[    0.008353] Initializing cgroup subsys devices
[    0.008357] Initializing cgroup subsys freezer
[    0.008361] Initializing cgroup subsys blkio
[    0.008371] Initializing cgroup subsys perf_event
[    0.008402] mce: CPU supports 5 MCE banks
[    0.008667] SMP alternatives: switching to UP code
[    0.019682] ACPI: Core revision 20110623
[    0.024041] ftrace: allocating 26580 entries in 53 pages
[    0.028094] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028448] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.068505] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 02
[    0.072003] Performance Events: AMD PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              48
[    0.072003] ... generic registers:      4
[    0.072003] ... value mask:             0000ffffffffffff
[    0.072003] ... max period:             00007fffffffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             000000000000000f
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] Brought up 1 CPUs
[    0.072003] Total of 1 processors activated (4020.74 BogoMIPS).
[    0.072003] devtmpfs: initialized
[    0.072003] EVM: security.selinux
[    0.072003] EVM: security.SMACK64
[    0.072003] EVM: security.capability
[    0.072003] PM: Registering ACPI NVS region at bfff0000 (12288 bytes)
[    0.072003] print_constraints: dummy: 
[    0.072003] RTC time: 20:48:20, date: 02/03/13
[    0.072003] NET: Registered protocol family 16
[    0.072003] EISA bus registered
[    0.072003] node 0 link 0: io port [1000, fffff]
[    0.072003] TOM: 00000000c0000000 aka 3072M
[    0.072003] node 0 link 0: mmio [d0000000, dfffffff]
[    0.072003] node 0 link 0: mmio [feb00000, fec0ffff]
[    0.072003] node 0 link 0: mmio [a0000, bffff]
[    0.072003] node 0 link 0: mmio [c0000000, ffb7ffff]
[    0.072003] bus: [00, ff] on node 0 link 0
[    0.072003] bus: 00 index 0 [io  0x0000-0xffff]
[    0.072003] bus: 00 index 1 [mem 0xc0000000-0xfcffffffff]
[    0.072003] bus: 00 index 2 [mem 0xfeb00000-0xfec0ffff]
[    0.072003] bus: 00 index 3 [mem 0x000a0000-0x000bffff]
[    0.072003] ACPI: bus type pci registered
[    0.072003] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xd0000000-0xdfffffff] (base 0xd0000000)
[    0.072003] PCI: MMCONFIG at [mem 0xd0000000-0xdfffffff] reserved in E820
[    0.072003] PCI: Using MMCONFIG for extended config space
[    0.072003] PCI: Using configuration type 1 for base access
[    0.072035] bio: create slab <bio-0> at 0
[    0.072130] ACPI: Added _OSI(Module Device)
[    0.072133] ACPI: Added _OSI(Processor Device)
[    0.072135] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.072137] ACPI: Added _OSI(Processor Aggregator Device)
[    0.073050] ACPI: EC: Look up EC in DSDT
[    0.073987] ACPI: Actual Package length (6) is larger than NumElements field (2), truncated
[    0.073992] 
[    0.077152] ACPI: Interpreter enabled
[    0.077162] ACPI: (supports S0 S1 S4 S5)
[    0.077182] ACPI: Using IOAPIC for interrupt routing
[    0.082610] ACPI: No dock devices found.
[    0.082612] HEST: Table not found.
[    0.082618] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.082675] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.082784] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.082787] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.082791] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.082794] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.082797] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff] (ignored)
[    0.082813] pci 0000:00:00.0: [10de:005e] type 0 class 0x000580
[    0.082884] pci 0000:00:01.0: [10de:0050] type 0 class 0x000601
[    0.082906] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.082918] pci 0000:00:01.1: [10de:0052] type 0 class 0x000c05
[    0.082926] pci 0000:00:01.1: reg 10: [io  0xec00-0xec1f]
[    0.082939] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
[    0.082944] pci 0000:00:01.1: reg 24: [io  0x1c40-0x1c7f]
[    0.082959] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.082963] pci 0000:00:01.1: PME# disabled
[    0.082978] pci 0000:00:02.0: [10de:005a] type 0 class 0x000c03
[    0.082986] pci 0000:00:02.0: reg 10: [mem 0xf3004000-0xf3004fff]
[    0.083013] pci 0000:00:02.0: supports D1 D2
[    0.083016] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083019] pci 0000:00:02.0: PME# disabled
[    0.083030] pci 0000:00:02.1: [10de:005b] type 0 class 0x000c03
[    0.083039] pci 0000:00:02.1: reg 10: [mem 0xfeb00000-0xfeb000ff]
[    0.083073] pci 0000:00:02.1: supports D1 D2
[    0.083075] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083079] pci 0000:00:02.1: PME# disabled
[    0.083095] pci 0000:00:04.0: [10de:0059] type 0 class 0x000401
[    0.083103] pci 0000:00:04.0: reg 10: [io  0xb800-0xb8ff]
[    0.083108] pci 0000:00:04.0: reg 14: [io  0xbc00-0xbcff]
[    0.083114] pci 0000:00:04.0: reg 18: [mem 0xf3000000-0xf3000fff]
[    0.083136] pci 0000:00:04.0: supports D1 D2
[    0.083147] pci 0000:00:06.0: [10de:0053] type 0 class 0x000101
[    0.083164] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
[    0.083189] pci 0000:00:07.0: [10de:0054] type 0 class 0x000101
[    0.083197] pci 0000:00:07.0: reg 10: [io  0x09f0-0x09f7]
[    0.083202] pci 0000:00:07.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.083207] pci 0000:00:07.0: reg 18: [io  0x0970-0x0977]
[    0.083212] pci 0000:00:07.0: reg 1c: [io  0x0b70-0x0b73]
[    0.083218] pci 0000:00:07.0: reg 20: [io  0xd000-0xd00f]
[    0.083223] pci 0000:00:07.0: reg 24: [mem 0xf3001000-0xf3001fff]
[    0.083245] pci 0000:00:08.0: [10de:0055] type 0 class 0x000101
[    0.083253] pci 0000:00:08.0: reg 10: [io  0x09e0-0x09e7]
[    0.083258] pci 0000:00:08.0: reg 14: [io  0x0be0-0x0be3]
[    0.083263] pci 0000:00:08.0: reg 18: [io  0x0960-0x0967]
[    0.083268] pci 0000:00:08.0: reg 1c: [io  0x0b60-0x0b63]
[    0.083273] pci 0000:00:08.0: reg 20: [io  0xe400-0xe40f]
[    0.083279] pci 0000:00:08.0: reg 24: [mem 0xf3002000-0xf3002fff]
[    0.083299] pci 0000:00:09.0: [10de:005c] type 1 class 0x000604
[    0.083318] pci 0000:00:0a.0: [10de:0057] type 0 class 0x000680
[    0.083326] pci 0000:00:0a.0: reg 10: [mem 0xf3003000-0xf3003fff]
[    0.083332] pci 0000:00:0a.0: reg 14: [io  0xe800-0xe807]
[    0.083357] pci 0000:00:0a.0: supports D1 D2
[    0.083359] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083363] pci 0000:00:0a.0: PME# disabled
[    0.083374] pci 0000:00:0b.0: [10de:005d] type 1 class 0x000604
[    0.083405] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083408] pci 0000:00:0b.0: PME# disabled
[    0.083422] pci 0000:00:0c.0: [10de:005d] type 1 class 0x000604
[    0.083451] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083454] pci 0000:00:0c.0: PME# disabled
[    0.083470] pci 0000:00:0d.0: [10de:005d] type 1 class 0x000604
[    0.083499] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083502] pci 0000:00:0d.0: PME# disabled
[    0.083516] pci 0000:00:0e.0: [10de:005d] type 1 class 0x000604
[    0.083544] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083547] pci 0000:00:0e.0: PME# disabled
[    0.083564] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.083586] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.083603] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.083621] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.083641] PCI: peer root bus 00 res updated from pci conf
[    0.083679] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.083683] pci 0000:00:09.0:   bridge window [io  0x6000-0x6fff]
[    0.083688] pci 0000:00:09.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.083691] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xfcffffffff] (subtractive decode)
[    0.083694] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfec0ffff] (subtractive decode)
[    0.083698] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.083719] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    0.083723] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.083745] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[    0.083749] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.083771] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[    0.083775] pci 0000:00:0d.0:   bridge window [io  0x7000-0x7fff]
[    0.083805] pci 0000:05:00.0: [10de:0391] type 0 class 0x000300
[    0.083815] pci 0000:05:00.0: reg 10: [mem 0xf0000000-0xf0ffffff]
[    0.083824] pci 0000:05:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.083833] pci 0000:05:00.0: reg 1c: [mem 0xf1000000-0xf1ffffff 64bit]
[    0.083840] pci 0000:05:00.0: reg 24: [io  0xa000-0xa07f]
[    0.083847] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.083878] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.083886] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[    0.083890] pci 0000:00:0e.0:   bridge window [io  0xa000-0xafff]
[    0.083893] pci 0000:00:0e.0:   bridge window [mem 0xf0000000-0xf2ffffff]
[    0.083898] pci 0000:00:0e.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.083908] pci_bus 0000:00: on NUMA node 0
[    0.083911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.084071] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.084321]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.084325]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.084327] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.111532] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111580] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111628] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.111674] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111720] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111767] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.111822] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111869] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.111915] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.111964] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.112019] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.112068] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.112112] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.112164] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.112218] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.112270] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.112332] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.112388] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.112444] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.112499] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.112528] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.112590] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.112653] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.112716] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.112778] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[    0.112840] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.112902] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.112964] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.113026] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.113094] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.113161] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.113228] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.113393] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.113396] vgaarb: loaded
[    0.113398] vgaarb: bridge control possible 0000:05:00.0
[    0.113553] i2c-core: driver [aat2870] using legacy suspend method
[    0.113555] i2c-core: driver [aat2870] using legacy resume method
[    0.113656] SCSI subsystem initialized
[    0.113726] libata version 3.00 loaded.
[    0.113792] usbcore: registered new interface driver usbfs
[    0.113810] usbcore: registered new interface driver hub
[    0.113837] usbcore: registered new device driver usb
[    0.113944] PCI: Using ACPI for IRQ routing
[    0.119231] PCI: pci_cache_line_size set to 64 bytes
[    0.119248] pci 0000:00:02.1: address space collision: [mem 0xfeb00000-0xfeb000ff] conflicts with PCI Bus #00 [mem 0xfeb00000-0xfec0ffff]
[    0.119287] Expanded resource reserved due to conflict with PCI Bus #00
[    0.119290] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.119293] reserve RAM buffer: 00000000bfff0000 - 00000000bfffffff 
[    0.119421] NetLabel: Initializing
[    0.119423] NetLabel:  domain hash size = 128
[    0.119424] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.119438] NetLabel:  unlabeled traffic allowed by default
[    0.127687] AppArmor: AppArmor Filesystem Enabled
[    0.127731] pnp: PnP ACPI init
[    0.127753] ACPI: bus type pnp registered
[    0.127788] pnp 00:00: [io  0x1000-0x107f]
[    0.127791] pnp 00:00: [io  0x1080-0x10ff]
[    0.127794] pnp 00:00: [io  0x1400-0x147f]
[    0.127796] pnp 00:00: [io  0x1480-0x14ff]
[    0.127799] pnp 00:00: [io  0x1800-0x187f]
[    0.127801] pnp 00:00: [io  0x1880-0x18ff]
[    0.127878] system 00:00: [io  0x1000-0x107f] has been reserved
[    0.127881] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.127885] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.127888] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.127891] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.127895] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.127900] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128018] pnp 00:01: [bus 00-ff]
[    0.128021] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.128024] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.128027] pnp 00:01: [io  0x0d00-0xffff window]
[    0.128030] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.128033] pnp 00:01: [mem 0x000c0000-0x000dffff window]
[    0.128036] pnp 00:01: [mem 0xc0000000-0xfebfffff window]
[    0.128095] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.128152] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128637] pnp 00:03: [io  0x0010-0x001f]
[    0.128639] pnp 00:03: [io  0x0022-0x003f]
[    0.128642] pnp 00:03: [io  0x0044-0x005f]
[    0.128644] pnp 00:03: [io  0x0062-0x0063]
[    0.128647] pnp 00:03: [io  0x0065-0x006f]
[    0.128649] pnp 00:03: [io  0x0074-0x007f]
[    0.128652] pnp 00:03: [io  0x0091-0x0093]
[    0.128654] pnp 00:03: [io  0x00a2-0x00bf]
[    0.128656] pnp 00:03: [io  0x00e0-0x00ef]
[    0.128659] pnp 00:03: [io  0x04d0-0x04d1]
[    0.128661] pnp 00:03: [io  0x0800-0x087f]
[    0.128664] pnp 00:03: [io  0x0295-0x0314]
[    0.128666] pnp 00:03: [io  0x0294-0x0297]
[    0.128738] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.128741] system 00:03: [io  0x0800-0x087f] has been reserved
[    0.128744] system 00:03: [io  0x0295-0x0314] has been reserved
[    0.128748] system 00:03: [io  0x0294-0x0297] could not be reserved
[    0.128751] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128764] pnp 00:04: [dma 4]
[    0.128767] pnp 00:04: [io  0x0000-0x000f]
[    0.128769] pnp 00:04: [io  0x0080-0x0090]
[    0.128772] pnp 00:04: [io  0x0094-0x009f]
[    0.128774] pnp 00:04: [io  0x00c0-0x00df]
[    0.128814] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.128826] pnp 00:05: [io  0x0070-0x0073]
[    0.128841] pnp 00:05: [irq 8]
[    0.128885] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.128894] pnp 00:06: [io  0x0061]
[    0.128935] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.128944] pnp 00:07: [io  0x00f0-0x00ff]
[    0.128951] pnp 00:07: [irq 13]
[    0.128993] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.129237] pnp 00:08: [io  0x03f8-0x03ff]
[    0.129244] pnp 00:08: [irq 4]
[    0.129324] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.129565] pnp 00:09: [io  0x02f8-0x02ff]
[    0.129571] pnp 00:09: [irq 3]
[    0.129638] pnp 00:09: Plug and Play ACPI device, IDs PNP0510 (active)
[    0.129941] pnp 00:0a: [io  0x0378-0x037f]
[    0.129944] pnp 00:0a: [io  0x0778-0x077b]
[    0.129950] pnp 00:0a: [irq 7]
[    0.129953] pnp 00:0a: [dma 3]
[    0.130033] pnp 00:0a: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.130069] pnp 00:0b: [io  0x0060]
[    0.130071] pnp 00:0b: [io  0x0064]
[    0.130077] pnp 00:0b: [irq 1]
[    0.130120] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.130151] pnp 00:0c: [mem 0xd0000000-0xdfffffff]
[    0.130209] system 00:0c: [mem 0xd0000000-0xdfffffff] has been reserved
[    0.130213] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130323] pnp 00:0d: [mem 0x000d1800-0x000d3fff]
[    0.130326] pnp 00:0d: [mem 0x000f0000-0x000f7fff]
[    0.130329] pnp 00:0d: [mem 0x000f8000-0x000fbfff]
[    0.130331] pnp 00:0d: [mem 0x000fc000-0x000fffff]
[    0.130334] pnp 00:0d: [mem 0xbfff0000-0xbfffffff]
[    0.130337] pnp 00:0d: [mem 0xffff0000-0xffffffff]
[    0.130339] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.130342] pnp 00:0d: [mem 0x00100000-0xbffeffff]
[    0.130345] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.130347] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.130413] system 00:0d: [mem 0x000d1800-0x000d3fff] has been reserved
[    0.130417] system 00:0d: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.130420] system 00:0d: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.130424] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.130427] system 00:0d: [mem 0xbfff0000-0xbfffffff] could not be reserved
[    0.130431] system 00:0d: [mem 0xffff0000-0xffffffff] has been reserved
[    0.130435] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.130438] system 00:0d: [mem 0x00100000-0xbffeffff] could not be reserved
[    0.130442] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.130446] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.130449] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.130457] pnp: PnP ACPI: found 14 devices
[    0.130459] ACPI: ACPI bus type pnp unregistered
[    0.130463] PnPBIOS: Disabled by ACPI PNP
[    0.167135] Switching to clocksource acpi_pm
[    0.167159] PCI: max bus depth: 1 pci_try_num: 2
[    0.167185] pci 0000:00:02.1: BAR 0: assigned [mem 0xc0000000-0xc00000ff]
[    0.167190] pci 0000:00:02.1: BAR 0: set to [mem 0xc0000000-0xc00000ff] (PCI address [0xc0000000-0xc00000ff])
[    0.167195] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.167198] pci 0000:00:09.0:   bridge window [io  0x6000-0x6fff]
[    0.167204] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    0.167207] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.167213] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[    0.167216] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.167222] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[    0.167225] pci 0000:00:0d.0:   bridge window [io  0x7000-0x7fff]
[    0.167232] pci 0000:05:00.0: BAR 6: assigned [mem 0xf2000000-0xf201ffff pref]
[    0.167235] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[    0.167238] pci 0000:00:0e.0:   bridge window [io  0xa000-0xafff]
[    0.167242] pci 0000:00:0e.0:   bridge window [mem 0xf0000000-0xf2ffffff]
[    0.167246] pci 0000:00:0e.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.167256] pci 0000:00:09.0: setting latency timer to 64
[    0.167261] pci 0000:00:0b.0: setting latency timer to 64
[    0.167266] pci 0000:00:0c.0: setting latency timer to 64
[    0.167271] pci 0000:00:0d.0: setting latency timer to 64
[    0.167276] pci 0000:00:0e.0: setting latency timer to 64
[    0.167280] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.167283] pci_bus 0000:00: resource 5 [mem 0xc0000000-0xfcffffffff]
[    0.167286] pci_bus 0000:00: resource 6 [mem 0xfeb00000-0xfec0ffff]
[    0.167289] pci_bus 0000:00: resource 7 [mem 0x000a0000-0x000bffff]
[    0.167293] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
[    0.167296] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.167299] pci_bus 0000:01: resource 5 [mem 0xc0000000-0xfcffffffff]
[    0.167302] pci_bus 0000:01: resource 6 [mem 0xfeb00000-0xfec0ffff]
[    0.167305] pci_bus 0000:01: resource 7 [mem 0x000a0000-0x000bffff]
[    0.167308] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.167311] pci_bus 0000:03: resource 0 [io  0x8000-0x8fff]
[    0.167314] pci_bus 0000:04: resource 0 [io  0x7000-0x7fff]
[    0.167317] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.167320] pci_bus 0000:05: resource 1 [mem 0xf0000000-0xf2ffffff]
[    0.167324] pci_bus 0000:05: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.167373] NET: Registered protocol family 2
[    0.167450] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.167746] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.167746] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.167746] TCP: Hash tables configured (established 131072 bind 65536)
[    0.167746] TCP reno registered
[    0.167746] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.167746] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.167746] NET: Registered protocol family 1
[    0.167746] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    0.167746] pci 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    0.167746] pci 0000:00:02.0: PCI INT A disabled
[    0.167746] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.167746] pci 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.167746] pci 0000:00:02.1: PCI INT B disabled
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0b.0: Linking AER extended capability
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0c.0: Linking AER extended capability
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0d.0: Linking AER extended capability
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0e.0: Linking AER extended capability
[    0.167746] pci 0000:05:00.0: Boot video device
[    0.167746] PCI: CLS 32 bytes, default 64
[    0.167746] audit: initializing netlink socket (disabled)
[    0.167746] type=2000 audit(1359924500.164:1): initialized
[    0.192998] Trying to unpack rootfs image as initramfs...
[    0.224484] highmem bounce pool size: 64 pages
[    0.224492] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.232490] VFS: Disk quotas dquot_6.5.2
[    0.232576] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.233255] fuse init (API version 7.17)
[    0.233368] msgmni has been set to 1661
[    0.244342] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.248069] io scheduler noop registered
[    0.248073] io scheduler deadline registered
[    0.248095] io scheduler cfq registered (default)
[    0.248236] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.248265] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[    0.248310] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.248328] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[    0.248365] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.248383] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[    0.248422] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.248439] pcieport 0000:00:0e.0: irq 43 for MSI/MSI-X
[    0.248508] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.248544] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.248723] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.248729] ACPI: Power Button [PWRB]
[    0.248795] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.248798] ACPI: Power Button [PWRF]
[    0.250580] ERST: Table is not found!
[    0.250581] GHES: HEST is not enabled!
[    0.250719] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.271030] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.271063] isapnp: Scanning for PnP cards...
[    0.360440] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.401603] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.468368] Linux agpgart interface v0.103
[    0.470182] brd: module loaded
[    0.471029] loop: module loaded
[    0.471332] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.471557] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[    0.471578] pata_acpi 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    0.471595] pata_acpi 0000:00:07.0: setting latency timer to 64
[    0.471603] pata_acpi 0000:00:07.0: PCI INT A disabled
[    0.471750] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[    0.471761] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    0.471777] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.471785] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.472284] Fixed MDIO Bus: probed
[    0.472310] tun: Universal TUN/TAP device driver, 1.6
[    0.472312] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.476291] PPP generic driver version 2.4.2
[    0.476426] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.476459] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.476483] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.476486] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.476530] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.476560] ehci_hcd 0000:00:02.1: debug port 1
[    0.476565] ehci_hcd 0000:00:02.1: cache line size of 32 is not supported
[    0.476587] ehci_hcd 0000:00:02.1: irq 22, io mem 0xc0000000
[    0.488316] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.488517] hub 1-0:1.0: USB hub found
[    0.488522] hub 1-0:1.0: 10 ports detected
[    0.488615] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.488639] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    0.488660] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.488663] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.488709] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.488743] ohci_hcd 0000:00:02.0: irq 23, io mem 0xf3004000
[    0.546191] hub 2-0:1.0: USB hub found
[    0.546199] hub 2-0:1.0: 10 ports detected
[    0.546290] uhci_hcd: USB Universal Host Controller Interface driver
[    0.546362] usbcore: registered new interface driver libusual
[    0.546418] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.546421] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.547224] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.552160] mousedev: PS/2 mouse device common for all mice
[    0.552323] rtc_cmos 00:05: RTC can wake from S4
[    0.552432] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.552459] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.552536] device-mapper: uevent: version 1.0.3
[    0.552612] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.552659] EISA: Probing bus 0 at eisa.0
[    0.552662] EISA: Cannot allocate resource for mainboard
[    0.552665] Cannot allocate resource for EISA slot 1
[    0.552668] Cannot allocate resource for EISA slot 2
[    0.552670] Cannot allocate resource for EISA slot 3
[    0.552673] Cannot allocate resource for EISA slot 4
[    0.552675] Cannot allocate resource for EISA slot 5
[    0.552677] Cannot allocate resource for EISA slot 6
[    0.552680] Cannot allocate resource for EISA slot 7
[    0.552682] Cannot allocate resource for EISA slot 8
[    0.552684] EISA: Detected 0 cards.
[    0.552696] cpufreq-nforce2: No nForce2 chipset.
[    0.552699] cpuidle: using governor ladder
[    0.552701] cpuidle: using governor menu
[    0.552703] EFI Variables Facility v0.08 2004-May-17
[    0.552949] TCP cubic registered
[    0.553094] NET: Registered protocol family 10
[    0.553629] NET: Registered protocol family 17
[    0.553633] Registering the dns_resolver key type
[    0.553661] Using IPI No-Shortcut mode
[    0.553762] PM: Hibernation image not present or could not be loaded.
[    0.553775] registered taskstats version 1
[    0.583222] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.915792] isapnp: No Plug & Play device found
[    0.936250] usb 1-10: new high-speed USB device number 3 using ehci_hcd
[    0.995425] Freeing initrd memory: 13836k freed
[    1.012962]   Magic number: 1:110:851
[    1.013071] rtc_cmos 00:05: setting system clock to 2013-02-03 20:48:21 UTC (1359924501)
[    1.013076] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    1.013124] powernow-k8: fid 0xc (2000 MHz), vid 0x6
[    1.013126] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.013197] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.013199] EDD information not available.
[    1.013360] Freeing unused kernel memory: 744k freed
[    1.013853] Write protecting the kernel text: 5828k
[    1.013869] Write protecting the kernel read-only data: 2380k
[    1.013871] NX-protecting the kernel data: 4412k
[    1.035582] udevd[80]: starting version 175
[    1.218897] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.219071] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    1.219078] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    1.219084] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.388028] usb 2-9: new low-speed USB device number 2 using ohci_hcd
[    1.613567] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.0/input/input3
[    1.613781] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:02.0-9/input0
[    1.613977] usbcore: registered new interface driver usbhid
[    1.613979] usbhid: USB HID core driver
[    1.740965] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x3f1 @ 7, addr 00:14:85:32:14:aa
[    1.740970] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[    1.741219] sata_nv 0000:00:07.0: version 3.5
[    1.741235] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    1.741286] sata_nv 0000:00:07.0: setting latency timer to 64
[    1.742413] scsi0 : sata_nv
[    1.742575] scsi1 : sata_nv
[    1.742725] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd000 irq 21
[    1.742729] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd008 irq 21
[    1.742756] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    1.742806] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.743235] scsi2 : sata_nv
[    1.743351] scsi3 : sata_nv
[    1.743470] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xe400 irq 20
[    1.743473] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xe408 irq 20
[    1.743492] pata_amd 0000:00:06.0: version 0.4.1
[    1.743524] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.744346] scsi4 : pata_amd
[    1.744479] scsi5 : pata_amd
[    1.744942] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.744946] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.908295] ata5.00: ATAPI: _NEC DVD_RW ND-3551A, 2.01, max UDMA/33
[    1.908306] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    1.924219] ata5.00: configured for UDMA/33
[    2.052024] ata1: SATA link down (SStatus 0 SControl 300)
[    2.056019] ata3: SATA link down (SStatus 0 SControl 300)
[    2.520027] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.528195] ata2.00: HPA detected: current 488395055, native 488397168
[    2.528200] ata2.00: ATA-7: WDC WD2500JS-00MHB0, 02.01C03, max UDMA/133
[    2.528204] ata2.00: 488395055 sectors, multi 16: LBA48 
[    2.536199] ata2.00: configured for UDMA/133
[    2.536329] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500JS-00M 02.0 PQ: 0 ANSI: 5
[    2.536542] sd 1:0:0:0: [sda] 488395055 512-byte logical blocks: (250 GB/232 GiB)
[    2.536591] sd 1:0:0:0: [sda] Write Protect is off
[    2.536595] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.536616] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.536924] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.603429]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    2.603912] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.848030] ata4: SATA link down (SStatus 0 SControl 300)
[    2.849143] scsi 4:0:0:0: CD-ROM            _NEC     DVD_RW ND-3551A  2.01 PQ: 0 ANSI: 5
[    2.850659] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.850662] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.850819] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.850976] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.113275] kjournald starting.  Commit interval 5 seconds
[    3.113311] EXT3-fs (sda5): mounted filesystem with ordered data mode
[   17.721197] Adding 6289412k swap on /dev/sda8.  Priority:-1 extents:1 across:6289412k 
[   17.733853] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.766710] udevd[364]: starting version 175
[   17.812249] lp: driver loaded but no devices found
[   18.016744] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   18.016852] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   18.161543] parport_pc 00:0a: reported by Plug and Play ACPI
[   18.161600] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.177644] EXT3-fs (sda5): using internal journal
[   18.248283] lp0: using parport0 (interrupt-driven).
[   18.449538] cfg80211: Calling CRDA to update world regulatory domain
[   18.453855] type=1400 audit(1359910118.938:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=602 comm="apparmor_parser"
[   18.454369] type=1400 audit(1359910118.938:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=602 comm="apparmor_parser"
[   18.454663] type=1400 audit(1359910118.938:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=602 comm="apparmor_parser"
[   18.477749] kjournald starting.  Commit interval 5 seconds
[   18.477989] EXT3-fs (sda6): using internal journal
[   18.477995] EXT3-fs (sda6): mounted filesystem with ordered data mode
[   18.658758] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   18.658767] snd_intel8x0 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[   18.658796] snd_intel8x0 0000:00:04.0: setting latency timer to 64
[   18.726663] kjournald starting.  Commit interval 5 seconds
[   18.727162] EXT3-fs (sda7): using internal journal
[   18.727168] EXT3-fs (sda7): mounted filesystem with ordered data mode
[   18.750954] nvidia: module license 'NVIDIA' taints kernel.
[   18.750959] Disabling lock debugging due to kernel taint
[   18.880463] usb 1-10: reset high-speed USB device number 3 using ehci_hcd
[   19.558597] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.558603] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558606] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.558610] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558613] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.558616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558619] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.558623] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558626] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.558629] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558632] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.558635] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558638] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.558642] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558645] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.558648] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558651] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.558655] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558657] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.558661] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558664] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.558667] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558670] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.558674] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558677] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.558680] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558683] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.558686] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   19.560332] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   19.560357] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   19.560369] nvidia 0000:05:00.0: setting latency timer to 64
[   19.560374] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.565873] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.64  Tue Oct 30 11:09:29 PDT 2012
[   19.577420] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   19.578924] Registered led device: rt2800usb-phy0::radio
[   19.578976] Registered led device: rt2800usb-phy0::assoc
[   19.579028] Registered led device: rt2800usb-phy0::quality
[   19.579079] usbcore: registered new interface driver rt2800usb
[   19.608169] intel8x0_measure_ac97_clock: measured 53631 usecs (2632 samples)
[   19.608173] intel8x0: clocking to 46947
[   19.622784] ppdev: user-space parallel port driver
[   19.651526] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.651532] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651535] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.651539] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651542] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.651546] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651548] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.651552] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651555] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.651558] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651561] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.651564] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651567] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.651570] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651573] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.651577] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651579] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.651583] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651586] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.651589] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651592] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.651595] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651598] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.651601] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651604] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.651608] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651610] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.651614] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651618] cfg80211: World regulatory domain updated:
[   19.651620] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.651623] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651626] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651629] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651632] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651635] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.369271] init: failsafe main process (791) killed by TERM signal
[   20.690268] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   20.690273] vesafb: scrolling: redraw
[   20.690276] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.691002] vesafb: framebuffer at 0xe0000000, mapped to 0xf8800000, using 5120k, total 5120k
[   20.691717] Console: switching to colour frame buffer device 160x64
[   20.691761] fb0: VESA VGA frame buffer device
[   20.757424] Bluetooth: Core ver 2.16
[   20.757463] NET: Registered protocol family 31
[   20.757465] Bluetooth: HCI device and connection manager initialized
[   20.757469] Bluetooth: HCI socket layer initialized
[   20.757471] Bluetooth: L2CAP socket layer initialized
[   20.758518] Bluetooth: SCO socket layer initialized
[   20.779768] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.779772] Bluetooth: BNEP filters: protocol multicast
[   20.852551] Bluetooth: RFCOMM TTY layer initialized
[   20.852559] Bluetooth: RFCOMM socket layer initialized
[   20.852561] Bluetooth: RFCOMM ver 1.11
[   20.899797] type=1400 audit(1359910121.382:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=885 comm="apparmor_parser"
[   20.910308] type=1400 audit(1359910121.394:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=885 comm="apparmor_parser"
[   21.102592] type=1400 audit(1359910121.586:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=916 comm="apparmor_parser"
[   21.107136] type=1400 audit(1359910121.590:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=917 comm="apparmor_parser"
[   21.108720] type=1400 audit(1359910121.594:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=917 comm="apparmor_parser"
[   21.109020] type=1400 audit(1359910121.594:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=917 comm="apparmor_parser"
[   21.123423] type=1400 audit(1359910121.606:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=918 comm="apparmor_parser"
[   22.503739] NVRM: Your system is not currently configured to drive a VGA console
[   22.503746] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   22.503750] NVRM: requires the use of a text-mode VGA console. Use of other console
[   22.503753] NVRM: drivers including, but not limited to, vesafb, may result in
[   22.503756] NVRM: corruption and stability problems, and is not supported.
[   23.129626] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.129974] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.136351] forcedeth 0000:00:0a.0: eth0: no link during initialization
[   23.139021] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.141979] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.546747] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 1)
[   27.549630] wlan0: authenticated
[   27.568746] wlan0: associate with 00:1e:8c:3e:09:3f (try 1)
[   27.571880] wlan0: RX AssocResp from 00:1e:8c:3e:09:3f (capab=0x11 status=0 aid=3)
[   27.571884] wlan0: associated
[   27.579308] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.872019] wlan0: no IPv6 routers present
[   45.345861] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[  321.650686] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59850, forcing to 0
[  321.650692] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[  322.011502] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 44984, forcing to 0
[  322.011508] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1195.894827] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 29300, forcing to 0
[ 1195.894838] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.

```sudo lshw -C network 
```

  *-network
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: &#1041;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 1
       bus info: usb@1:10
       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: wlan0
       &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: 00:25:9c:a0:12:28
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: ethernet physical wireless
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: broadcast=yes driver=rt2800usb driverversion=3.2.0-37-generic-pae firmware=0.29 ip=192.168.1.154 link=yes multicast=yes wireless=IEEE 802.11bg

```iwlist wlan0 scan 
```

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:8C:3E:09:3F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Imgo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000006be2c196
                    Extra: Last beacon: 10576ms ago
                    IE: Unknown: 0004496D676F
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: DD09001018020010000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1E:8C:3E:09:3F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Beeline_WiFi_WPA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006bd96189
                    Extra: Last beacon: 10648ms ago
                    IE: Unknown: 00104265656C696E655F576946695F575041
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706525500010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F202010100000FA4000027A400004243000062320000


```**After some times of works** (I watched video): the Linksys lost connection, and can't restart by *$ sudo /etc/init.d/networking restart*
The logs after lost connection:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:14:85:32:14:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x6000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74269 (74.2 KB)  TX bytes:74269 (74.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:9c:a0:12:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:79985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113614765 (113.6 MB)  TX bytes:4949456 (4.9 MB)


```iwconfig wlan0
```

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```lsmod
```

Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
vesafb                 13516  1 
ppdev                  12849  0 
arc4                   12473  2 
nvidia              10257747  40 
rt2800usb              22373  0 
snd_intel8x0           33455  3 
rt2800lib              53298  1 rt2800usb
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
snd_pcm                80916  3 snd_intel8x0,snd_ac97_codec
serio_raw              13027  0 
snd_seq_midi           13132  0 
cfg80211              178877  2 rt2x00lib,mac80211
k8temp                 12905  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
pata_amd               13750  0 
sata_nv                23360  4 
forcedeth              58096  0 

```dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-37-generic-pae (buildd@roseapple) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #58-Ubuntu SMP Thu Jan 24 15:51:02 UTC 2013 (Ubuntu 3.2.0-37.58-generic-pae 3.2.35)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfff0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000bfff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff3000 - 00000000c0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000d0000000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.3 present.
[    0.000000] DMI:    /GA-K8N-SLi, BIOS F2 07/27/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xbfff0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f52c0] f52c0
[    0.000000] initial memory mapped : 0 - 02000000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffa000-2000000
[    0.000000] RAMDISK: 364ea000 - 3726d000
[    0.000000] ACPI: RSDP 000f6c50 00014 (v00 Nvidia)
[    0.000000] ACPI: RSDT bfff3000 00030 (v01 Nvidia AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: FACP bfff3040 00074 (v01 Nvidia AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: DSDT bfff30c0 04BF2 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000C)
[    0.000000] ACPI: FACS bfff0000 00040
[    0.000000] ACPI: MCFG bfff7d40 0003C (v01 Nvidia AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: APIC bfff7cc0 0007C (v01 Nvidia AWRDACPI 42302E31 AWRD 01010101)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2179MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x000bfff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfff0
[    0.000000] On node 0 totalpages: 786303
[    0.000000] free_area_init_node: node 0, pgdat c186b400, node_mem_map f4cea200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4360 pages used for memmap
[    0.000000]   HighMem zone: 553706 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:1ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bcf000 s34240 r0 d23104 u57344
[    0.000000] pcpu-alloc: s34240 r0 d23104 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780159
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.2.0-37-generic-pae root=UUID=46939b82-4154-4768-b67c-d48999f50d4c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 12582400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bfff0)
[    0.000000] Memory: 3083144k/3145664k available (5826k kernel code, 62068k reserved, 2848k data, 744k init, 2232264k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1879000 - 0xc1933000   ( 744 kB)
[    0.000000]       .data : 0xc15b08fc - 0xc1878c40   (2848 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15b08fc   (5826 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2010.370 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4020.74 BogoMIPS (lpj=8041480)
[    0.008015] pid_max: default: 32768 minimum: 301
[    0.008045] Security Framework initialized
[    0.008078] AppArmor: AppArmor initialized
[    0.008081] Yama: becoming mindful.
[    0.008157] Mount-cache hash table entries: 512
[    0.008335] Initializing cgroup subsys cpuacct
[    0.008343] Initializing cgroup subsys memory
[    0.008353] Initializing cgroup subsys devices
[    0.008357] Initializing cgroup subsys freezer
[    0.008361] Initializing cgroup subsys blkio
[    0.008371] Initializing cgroup subsys perf_event
[    0.008402] mce: CPU supports 5 MCE banks
[    0.008667] SMP alternatives: switching to UP code
[    0.019682] ACPI: Core revision 20110623
[    0.024041] ftrace: allocating 26580 entries in 53 pages
[    0.028094] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028448] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.068505] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 02
[    0.072003] Performance Events: AMD PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              48
[    0.072003] ... generic registers:      4
[    0.072003] ... value mask:             0000ffffffffffff
[    0.072003] ... max period:             00007fffffffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             000000000000000f
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] Brought up 1 CPUs
[    0.072003] Total of 1 processors activated (4020.74 BogoMIPS).
[    0.072003] devtmpfs: initialized
[    0.072003] EVM: security.selinux
[    0.072003] EVM: security.SMACK64
[    0.072003] EVM: security.capability
[    0.072003] PM: Registering ACPI NVS region at bfff0000 (12288 bytes)
[    0.072003] print_constraints: dummy: 
[    0.072003] RTC time: 20:48:20, date: 02/03/13
[    0.072003] NET: Registered protocol family 16
[    0.072003] EISA bus registered
[    0.072003] node 0 link 0: io port [1000, fffff]
[    0.072003] TOM: 00000000c0000000 aka 3072M
[    0.072003] node 0 link 0: mmio [d0000000, dfffffff]
[    0.072003] node 0 link 0: mmio [feb00000, fec0ffff]
[    0.072003] node 0 link 0: mmio [a0000, bffff]
[    0.072003] node 0 link 0: mmio [c0000000, ffb7ffff]
[    0.072003] bus: [00, ff] on node 0 link 0
[    0.072003] bus: 00 index 0 [io  0x0000-0xffff]
[    0.072003] bus: 00 index 1 [mem 0xc0000000-0xfcffffffff]
[    0.072003] bus: 00 index 2 [mem 0xfeb00000-0xfec0ffff]
[    0.072003] bus: 00 index 3 [mem 0x000a0000-0x000bffff]
[    0.072003] ACPI: bus type pci registered
[    0.072003] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xd0000000-0xdfffffff] (base 0xd0000000)
[    0.072003] PCI: MMCONFIG at [mem 0xd0000000-0xdfffffff] reserved in E820
[    0.072003] PCI: Using MMCONFIG for extended config space
[    0.072003] PCI: Using configuration type 1 for base access
[    0.072035] bio: create slab <bio-0> at 0
[    0.072130] ACPI: Added _OSI(Module Device)
[    0.072133] ACPI: Added _OSI(Processor Device)
[    0.072135] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.072137] ACPI: Added _OSI(Processor Aggregator Device)
[    0.073050] ACPI: EC: Look up EC in DSDT
[    0.073987] ACPI: Actual Package length (6) is larger than NumElements field (2), truncated
[    0.073992] 
[    0.077152] ACPI: Interpreter enabled
[    0.077162] ACPI: (supports S0 S1 S4 S5)
[    0.077182] ACPI: Using IOAPIC for interrupt routing
[    0.082610] ACPI: No dock devices found.
[    0.082612] HEST: Table not found.
[    0.082618] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.082675] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.082784] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.082787] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.082791] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.082794] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)
[    0.082797] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xfebfffff] (ignored)
[    0.082813] pci 0000:00:00.0: [10de:005e] type 0 class 0x000580
[    0.082884] pci 0000:00:01.0: [10de:0050] type 0 class 0x000601
[    0.082906] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.082918] pci 0000:00:01.1: [10de:0052] type 0 class 0x000c05
[    0.082926] pci 0000:00:01.1: reg 10: [io  0xec00-0xec1f]
[    0.082939] pci 0000:00:01.1: reg 20: [io  0x1c00-0x1c3f]
[    0.082944] pci 0000:00:01.1: reg 24: [io  0x1c40-0x1c7f]
[    0.082959] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.082963] pci 0000:00:01.1: PME# disabled
[    0.082978] pci 0000:00:02.0: [10de:005a] type 0 class 0x000c03
[    0.082986] pci 0000:00:02.0: reg 10: [mem 0xf3004000-0xf3004fff]
[    0.083013] pci 0000:00:02.0: supports D1 D2
[    0.083016] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083019] pci 0000:00:02.0: PME# disabled
[    0.083030] pci 0000:00:02.1: [10de:005b] type 0 class 0x000c03
[    0.083039] pci 0000:00:02.1: reg 10: [mem 0xfeb00000-0xfeb000ff]
[    0.083073] pci 0000:00:02.1: supports D1 D2
[    0.083075] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083079] pci 0000:00:02.1: PME# disabled
[    0.083095] pci 0000:00:04.0: [10de:0059] type 0 class 0x000401
[    0.083103] pci 0000:00:04.0: reg 10: [io  0xb800-0xb8ff]
[    0.083108] pci 0000:00:04.0: reg 14: [io  0xbc00-0xbcff]
[    0.083114] pci 0000:00:04.0: reg 18: [mem 0xf3000000-0xf3000fff]
[    0.083136] pci 0000:00:04.0: supports D1 D2
[    0.083147] pci 0000:00:06.0: [10de:0053] type 0 class 0x000101
[    0.083164] pci 0000:00:06.0: reg 20: [io  0xf000-0xf00f]
[    0.083189] pci 0000:00:07.0: [10de:0054] type 0 class 0x000101
[    0.083197] pci 0000:00:07.0: reg 10: [io  0x09f0-0x09f7]
[    0.083202] pci 0000:00:07.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.083207] pci 0000:00:07.0: reg 18: [io  0x0970-0x0977]
[    0.083212] pci 0000:00:07.0: reg 1c: [io  0x0b70-0x0b73]
[    0.083218] pci 0000:00:07.0: reg 20: [io  0xd000-0xd00f]
[    0.083223] pci 0000:00:07.0: reg 24: [mem 0xf3001000-0xf3001fff]
[    0.083245] pci 0000:00:08.0: [10de:0055] type 0 class 0x000101
[    0.083253] pci 0000:00:08.0: reg 10: [io  0x09e0-0x09e7]
[    0.083258] pci 0000:00:08.0: reg 14: [io  0x0be0-0x0be3]
[    0.083263] pci 0000:00:08.0: reg 18: [io  0x0960-0x0967]
[    0.083268] pci 0000:00:08.0: reg 1c: [io  0x0b60-0x0b63]
[    0.083273] pci 0000:00:08.0: reg 20: [io  0xe400-0xe40f]
[    0.083279] pci 0000:00:08.0: reg 24: [mem 0xf3002000-0xf3002fff]
[    0.083299] pci 0000:00:09.0: [10de:005c] type 1 class 0x000604
[    0.083318] pci 0000:00:0a.0: [10de:0057] type 0 class 0x000680
[    0.083326] pci 0000:00:0a.0: reg 10: [mem 0xf3003000-0xf3003fff]
[    0.083332] pci 0000:00:0a.0: reg 14: [io  0xe800-0xe807]
[    0.083357] pci 0000:00:0a.0: supports D1 D2
[    0.083359] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083363] pci 0000:00:0a.0: PME# disabled
[    0.083374] pci 0000:00:0b.0: [10de:005d] type 1 class 0x000604
[    0.083405] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083408] pci 0000:00:0b.0: PME# disabled
[    0.083422] pci 0000:00:0c.0: [10de:005d] type 1 class 0x000604
[    0.083451] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083454] pci 0000:00:0c.0: PME# disabled
[    0.083470] pci 0000:00:0d.0: [10de:005d] type 1 class 0x000604
[    0.083499] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083502] pci 0000:00:0d.0: PME# disabled
[    0.083516] pci 0000:00:0e.0: [10de:005d] type 1 class 0x000604
[    0.083544] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083547] pci 0000:00:0e.0: PME# disabled
[    0.083564] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.083586] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.083603] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.083621] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.083641] PCI: peer root bus 00 res updated from pci conf
[    0.083679] pci 0000:00:09.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.083683] pci 0000:00:09.0:   bridge window [io  0x6000-0x6fff]
[    0.083688] pci 0000:00:09.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.083691] pci 0000:00:09.0:   bridge window [mem 0xc0000000-0xfcffffffff] (subtractive decode)
[    0.083694] pci 0000:00:09.0:   bridge window [mem 0xfeb00000-0xfec0ffff] (subtractive decode)
[    0.083698] pci 0000:00:09.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.083719] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    0.083723] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.083745] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[    0.083749] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.083771] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[    0.083775] pci 0000:00:0d.0:   bridge window [io  0x7000-0x7fff]
[    0.083805] pci 0000:05:00.0: [10de:0391] type 0 class 0x000300
[    0.083815] pci 0000:05:00.0: reg 10: [mem 0xf0000000-0xf0ffffff]
[    0.083824] pci 0000:05:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.083833] pci 0000:05:00.0: reg 1c: [mem 0xf1000000-0xf1ffffff 64bit]
[    0.083840] pci 0000:05:00.0: reg 24: [io  0xa000-0xa07f]
[    0.083847] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.083878] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.083886] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[    0.083890] pci 0000:00:0e.0:   bridge window [io  0xa000-0xafff]
[    0.083893] pci 0000:00:0e.0:   bridge window [mem 0xf0000000-0xf2ffffff]
[    0.083898] pci 0000:00:0e.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.083908] pci_bus 0000:00: on NUMA node 0
[    0.083911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.084071] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.084321]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.084325]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.084327] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.111532] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111580] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111628] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.111674] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111720] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111767] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.111822] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.111869] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.111915] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.111964] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.112019] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.112068] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.112112] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.112164] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.112218] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.112270] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.112332] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.112388] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.112444] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.112499] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.112528] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.112590] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.112653] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.112716] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.112778] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[    0.112840] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.112902] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.112964] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.113026] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.113094] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.113161] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.113228] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.113393] vgaarb: device added: PCI:0000:05:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.113396] vgaarb: loaded
[    0.113398] vgaarb: bridge control possible 0000:05:00.0
[    0.113553] i2c-core: driver [aat2870] using legacy suspend method
[    0.113555] i2c-core: driver [aat2870] using legacy resume method
[    0.113656] SCSI subsystem initialized
[    0.113726] libata version 3.00 loaded.
[    0.113792] usbcore: registered new interface driver usbfs
[    0.113810] usbcore: registered new interface driver hub
[    0.113837] usbcore: registered new device driver usb
[    0.113944] PCI: Using ACPI for IRQ routing
[    0.119231] PCI: pci_cache_line_size set to 64 bytes
[    0.119248] pci 0000:00:02.1: address space collision: [mem 0xfeb00000-0xfeb000ff] conflicts with PCI Bus #00 [mem 0xfeb00000-0xfec0ffff]
[    0.119287] Expanded resource reserved due to conflict with PCI Bus #00
[    0.119290] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.119293] reserve RAM buffer: 00000000bfff0000 - 00000000bfffffff 
[    0.119421] NetLabel: Initializing
[    0.119423] NetLabel:  domain hash size = 128
[    0.119424] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.119438] NetLabel:  unlabeled traffic allowed by default
[    0.127687] AppArmor: AppArmor Filesystem Enabled
[    0.127731] pnp: PnP ACPI init
[    0.127753] ACPI: bus type pnp registered
[    0.127788] pnp 00:00: [io  0x1000-0x107f]
[    0.127791] pnp 00:00: [io  0x1080-0x10ff]
[    0.127794] pnp 00:00: [io  0x1400-0x147f]
[    0.127796] pnp 00:00: [io  0x1480-0x14ff]
[    0.127799] pnp 00:00: [io  0x1800-0x187f]
[    0.127801] pnp 00:00: [io  0x1880-0x18ff]
[    0.127878] system 00:00: [io  0x1000-0x107f] has been reserved
[    0.127881] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.127885] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.127888] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.127891] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.127895] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.127900] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128018] pnp 00:01: [bus 00-ff]
[    0.128021] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.128024] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.128027] pnp 00:01: [io  0x0d00-0xffff window]
[    0.128030] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.128033] pnp 00:01: [mem 0x000c0000-0x000dffff window]
[    0.128036] pnp 00:01: [mem 0xc0000000-0xfebfffff window]
[    0.128095] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.128152] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128637] pnp 00:03: [io  0x0010-0x001f]
[    0.128639] pnp 00:03: [io  0x0022-0x003f]
[    0.128642] pnp 00:03: [io  0x0044-0x005f]
[    0.128644] pnp 00:03: [io  0x0062-0x0063]
[    0.128647] pnp 00:03: [io  0x0065-0x006f]
[    0.128649] pnp 00:03: [io  0x0074-0x007f]
[    0.128652] pnp 00:03: [io  0x0091-0x0093]
[    0.128654] pnp 00:03: [io  0x00a2-0x00bf]
[    0.128656] pnp 00:03: [io  0x00e0-0x00ef]
[    0.128659] pnp 00:03: [io  0x04d0-0x04d1]
[    0.128661] pnp 00:03: [io  0x0800-0x087f]
[    0.128664] pnp 00:03: [io  0x0295-0x0314]
[    0.128666] pnp 00:03: [io  0x0294-0x0297]
[    0.128738] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.128741] system 00:03: [io  0x0800-0x087f] has been reserved
[    0.128744] system 00:03: [io  0x0295-0x0314] has been reserved
[    0.128748] system 00:03: [io  0x0294-0x0297] could not be reserved
[    0.128751] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.128764] pnp 00:04: [dma 4]
[    0.128767] pnp 00:04: [io  0x0000-0x000f]
[    0.128769] pnp 00:04: [io  0x0080-0x0090]
[    0.128772] pnp 00:04: [io  0x0094-0x009f]
[    0.128774] pnp 00:04: [io  0x00c0-0x00df]
[    0.128814] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.128826] pnp 00:05: [io  0x0070-0x0073]
[    0.128841] pnp 00:05: [irq 8]
[    0.128885] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.128894] pnp 00:06: [io  0x0061]
[    0.128935] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.128944] pnp 00:07: [io  0x00f0-0x00ff]
[    0.128951] pnp 00:07: [irq 13]
[    0.128993] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.129237] pnp 00:08: [io  0x03f8-0x03ff]
[    0.129244] pnp 00:08: [irq 4]
[    0.129324] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.129565] pnp 00:09: [io  0x02f8-0x02ff]
[    0.129571] pnp 00:09: [irq 3]
[    0.129638] pnp 00:09: Plug and Play ACPI device, IDs PNP0510 (active)
[    0.129941] pnp 00:0a: [io  0x0378-0x037f]
[    0.129944] pnp 00:0a: [io  0x0778-0x077b]
[    0.129950] pnp 00:0a: [irq 7]
[    0.129953] pnp 00:0a: [dma 3]
[    0.130033] pnp 00:0a: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.130069] pnp 00:0b: [io  0x0060]
[    0.130071] pnp 00:0b: [io  0x0064]
[    0.130077] pnp 00:0b: [irq 1]
[    0.130120] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.130151] pnp 00:0c: [mem 0xd0000000-0xdfffffff]
[    0.130209] system 00:0c: [mem 0xd0000000-0xdfffffff] has been reserved
[    0.130213] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130323] pnp 00:0d: [mem 0x000d1800-0x000d3fff]
[    0.130326] pnp 00:0d: [mem 0x000f0000-0x000f7fff]
[    0.130329] pnp 00:0d: [mem 0x000f8000-0x000fbfff]
[    0.130331] pnp 00:0d: [mem 0x000fc000-0x000fffff]
[    0.130334] pnp 00:0d: [mem 0xbfff0000-0xbfffffff]
[    0.130337] pnp 00:0d: [mem 0xffff0000-0xffffffff]
[    0.130339] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.130342] pnp 00:0d: [mem 0x00100000-0xbffeffff]
[    0.130345] pnp 00:0d: [mem 0xfec00000-0xfec00fff]
[    0.130347] pnp 00:0d: [mem 0xfee00000-0xfee00fff]
[    0.130413] system 00:0d: [mem 0x000d1800-0x000d3fff] has been reserved
[    0.130417] system 00:0d: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.130420] system 00:0d: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.130424] system 00:0d: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.130427] system 00:0d: [mem 0xbfff0000-0xbfffffff] could not be reserved
[    0.130431] system 00:0d: [mem 0xffff0000-0xffffffff] has been reserved
[    0.130435] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.130438] system 00:0d: [mem 0x00100000-0xbffeffff] could not be reserved
[    0.130442] system 00:0d: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.130446] system 00:0d: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.130449] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.130457] pnp: PnP ACPI: found 14 devices
[    0.130459] ACPI: ACPI bus type pnp unregistered
[    0.130463] PnPBIOS: Disabled by ACPI PNP
[    0.167135] Switching to clocksource acpi_pm
[    0.167159] PCI: max bus depth: 1 pci_try_num: 2
[    0.167185] pci 0000:00:02.1: BAR 0: assigned [mem 0xc0000000-0xc00000ff]
[    0.167190] pci 0000:00:02.1: BAR 0: set to [mem 0xc0000000-0xc00000ff] (PCI address [0xc0000000-0xc00000ff])
[    0.167195] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.167198] pci 0000:00:09.0:   bridge window [io  0x6000-0x6fff]
[    0.167204] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    0.167207] pci 0000:00:0b.0:   bridge window [io  0x9000-0x9fff]
[    0.167213] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[    0.167216] pci 0000:00:0c.0:   bridge window [io  0x8000-0x8fff]
[    0.167222] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[    0.167225] pci 0000:00:0d.0:   bridge window [io  0x7000-0x7fff]
[    0.167232] pci 0000:05:00.0: BAR 6: assigned [mem 0xf2000000-0xf201ffff pref]
[    0.167235] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[    0.167238] pci 0000:00:0e.0:   bridge window [io  0xa000-0xafff]
[    0.167242] pci 0000:00:0e.0:   bridge window [mem 0xf0000000-0xf2ffffff]
[    0.167246] pci 0000:00:0e.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.167256] pci 0000:00:09.0: setting latency timer to 64
[    0.167261] pci 0000:00:0b.0: setting latency timer to 64
[    0.167266] pci 0000:00:0c.0: setting latency timer to 64
[    0.167271] pci 0000:00:0d.0: setting latency timer to 64
[    0.167276] pci 0000:00:0e.0: setting latency timer to 64
[    0.167280] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.167283] pci_bus 0000:00: resource 5 [mem 0xc0000000-0xfcffffffff]
[    0.167286] pci_bus 0000:00: resource 6 [mem 0xfeb00000-0xfec0ffff]
[    0.167289] pci_bus 0000:00: resource 7 [mem 0x000a0000-0x000bffff]
[    0.167293] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
[    0.167296] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.167299] pci_bus 0000:01: resource 5 [mem 0xc0000000-0xfcffffffff]
[    0.167302] pci_bus 0000:01: resource 6 [mem 0xfeb00000-0xfec0ffff]
[    0.167305] pci_bus 0000:01: resource 7 [mem 0x000a0000-0x000bffff]
[    0.167308] pci_bus 0000:02: resource 0 [io  0x9000-0x9fff]
[    0.167311] pci_bus 0000:03: resource 0 [io  0x8000-0x8fff]
[    0.167314] pci_bus 0000:04: resource 0 [io  0x7000-0x7fff]
[    0.167317] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    0.167320] pci_bus 0000:05: resource 1 [mem 0xf0000000-0xf2ffffff]
[    0.167324] pci_bus 0000:05: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.167373] NET: Registered protocol family 2
[    0.167450] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.167746] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.167746] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.167746] TCP: Hash tables configured (established 131072 bind 65536)
[    0.167746] TCP reno registered
[    0.167746] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.167746] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.167746] NET: Registered protocol family 1
[    0.167746] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    0.167746] pci 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    0.167746] pci 0000:00:02.0: PCI INT A disabled
[    0.167746] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.167746] pci 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.167746] pci 0000:00:02.1: PCI INT B disabled
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0b.0: Linking AER extended capability
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0c.0: Linking AER extended capability
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0d.0: Linking AER extended capability
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[    0.167746] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.167746] pci 0000:00:0e.0: Linking AER extended capability
[    0.167746] pci 0000:05:00.0: Boot video device
[    0.167746] PCI: CLS 32 bytes, default 64
[    0.167746] audit: initializing netlink socket (disabled)
[    0.167746] type=2000 audit(1359924500.164:1): initialized
[    0.192998] Trying to unpack rootfs image as initramfs...
[    0.224484] highmem bounce pool size: 64 pages
[    0.224492] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.232490] VFS: Disk quotas dquot_6.5.2
[    0.232576] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.233255] fuse init (API version 7.17)
[    0.233368] msgmni has been set to 1661
[    0.244342] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.248069] io scheduler noop registered
[    0.248073] io scheduler deadline registered
[    0.248095] io scheduler cfq registered (default)
[    0.248236] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.248265] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[    0.248310] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.248328] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[    0.248365] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.248383] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[    0.248422] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.248439] pcieport 0000:00:0e.0: irq 43 for MSI/MSI-X
[    0.248508] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.248544] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.248723] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.248729] ACPI: Power Button [PWRB]
[    0.248795] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.248798] ACPI: Power Button [PWRF]
[    0.250580] ERST: Table is not found!
[    0.250581] GHES: HEST is not enabled!
[    0.250719] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.271030] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.271063] isapnp: Scanning for PnP cards...
[    0.360440] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.401603] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.468368] Linux agpgart interface v0.103
[    0.470182] brd: module loaded
[    0.471029] loop: module loaded
[    0.471332] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.471557] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 21
[    0.471578] pata_acpi 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    0.471595] pata_acpi 0000:00:07.0: setting latency timer to 64
[    0.471603] pata_acpi 0000:00:07.0: PCI INT A disabled
[    0.471750] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 20
[    0.471761] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    0.471777] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.471785] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.472284] Fixed MDIO Bus: probed
[    0.472310] tun: Universal TUN/TAP device driver, 1.6
[    0.472312] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.476291] PPP generic driver version 2.4.2
[    0.476426] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.476459] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.476483] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.476486] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.476530] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.476560] ehci_hcd 0000:00:02.1: debug port 1
[    0.476565] ehci_hcd 0000:00:02.1: cache line size of 32 is not supported
[    0.476587] ehci_hcd 0000:00:02.1: irq 22, io mem 0xc0000000
[    0.488316] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.488517] hub 1-0:1.0: USB hub found
[    0.488522] hub 1-0:1.0: 10 ports detected
[    0.488615] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.488639] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    0.488660] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.488663] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.488709] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.488743] ohci_hcd 0000:00:02.0: irq 23, io mem 0xf3004000
[    0.546191] hub 2-0:1.0: USB hub found
[    0.546199] hub 2-0:1.0: 10 ports detected
[    0.546290] uhci_hcd: USB Universal Host Controller Interface driver
[    0.546362] usbcore: registered new interface driver libusual
[    0.546418] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.546421] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.547224] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.552160] mousedev: PS/2 mouse device common for all mice
[    0.552323] rtc_cmos 00:05: RTC can wake from S4
[    0.552432] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.552459] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.552536] device-mapper: uevent: version 1.0.3
[    0.552612] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.552659] EISA: Probing bus 0 at eisa.0
[    0.552662] EISA: Cannot allocate resource for mainboard
[    0.552665] Cannot allocate resource for EISA slot 1
[    0.552668] Cannot allocate resource for EISA slot 2
[    0.552670] Cannot allocate resource for EISA slot 3
[    0.552673] Cannot allocate resource for EISA slot 4
[    0.552675] Cannot allocate resource for EISA slot 5
[    0.552677] Cannot allocate resource for EISA slot 6
[    0.552680] Cannot allocate resource for EISA slot 7
[    0.552682] Cannot allocate resource for EISA slot 8
[    0.552684] EISA: Detected 0 cards.
[    0.552696] cpufreq-nforce2: No nForce2 chipset.
[    0.552699] cpuidle: using governor ladder
[    0.552701] cpuidle: using governor menu
[    0.552703] EFI Variables Facility v0.08 2004-May-17
[    0.552949] TCP cubic registered
[    0.553094] NET: Registered protocol family 10
[    0.553629] NET: Registered protocol family 17
[    0.553633] Registering the dns_resolver key type
[    0.553661] Using IPI No-Shortcut mode
[    0.553762] PM: Hibernation image not present or could not be loaded.
[    0.553775] registered taskstats version 1
[    0.583222] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.915792] isapnp: No Plug & Play device found
[    0.936250] usb 1-10: new high-speed USB device number 3 using ehci_hcd
[    0.995425] Freeing initrd memory: 13836k freed
[    1.012962]   Magic number: 1:110:851
[    1.013071] rtc_cmos 00:05: setting system clock to 2013-02-03 20:48:21 UTC (1359924501)
[    1.013076] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    1.013124] powernow-k8: fid 0xc (2000 MHz), vid 0x6
[    1.013126] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    1.013197] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.013199] EDD information not available.
[    1.013360] Freeing unused kernel memory: 744k freed
[    1.013853] Write protecting the kernel text: 5828k
[    1.013869] Write protecting the kernel read-only data: 2380k
[    1.013871] NX-protecting the kernel data: 4412k
[    1.035582] udevd[80]: starting version 175
[    1.218897] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.219071] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    1.219078] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    1.219084] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.388028] usb 2-9: new low-speed USB device number 2 using ohci_hcd
[    1.613567] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.0/input/input3
[    1.613781] generic-usb 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:02.0-9/input0
[    1.613977] usbcore: registered new interface driver usbhid
[    1.613979] usbhid: USB HID core driver
[    1.740965] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x3f1 @ 7, addr 00:14:85:32:14:aa
[    1.740970] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[    1.741219] sata_nv 0000:00:07.0: version 3.5
[    1.741235] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
[    1.741286] sata_nv 0000:00:07.0: setting latency timer to 64
[    1.742413] scsi0 : sata_nv
[    1.742575] scsi1 : sata_nv
[    1.742725] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd000 irq 21
[    1.742729] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd008 irq 21
[    1.742756] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
[    1.742806] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.743235] scsi2 : sata_nv
[    1.743351] scsi3 : sata_nv
[    1.743470] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xe400 irq 20
[    1.743473] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xe408 irq 20
[    1.743492] pata_amd 0000:00:06.0: version 0.4.1
[    1.743524] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.744346] scsi4 : pata_amd
[    1.744479] scsi5 : pata_amd
[    1.744942] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.744946] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.908295] ata5.00: ATAPI: _NEC DVD_RW ND-3551A, 2.01, max UDMA/33
[    1.908306] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    1.924219] ata5.00: configured for UDMA/33
[    2.052024] ata1: SATA link down (SStatus 0 SControl 300)
[    2.056019] ata3: SATA link down (SStatus 0 SControl 300)
[    2.520027] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.528195] ata2.00: HPA detected: current 488395055, native 488397168
[    2.528200] ata2.00: ATA-7: WDC WD2500JS-00MHB0, 02.01C03, max UDMA/133
[    2.528204] ata2.00: 488395055 sectors, multi 16: LBA48 
[    2.536199] ata2.00: configured for UDMA/133
[    2.536329] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500JS-00M 02.0 PQ: 0 ANSI: 5
[    2.536542] sd 1:0:0:0: [sda] 488395055 512-byte logical blocks: (250 GB/232 GiB)
[    2.536591] sd 1:0:0:0: [sda] Write Protect is off
[    2.536595] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.536616] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.536924] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.603429]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    2.603912] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.848030] ata4: SATA link down (SStatus 0 SControl 300)
[    2.849143] scsi 4:0:0:0: CD-ROM            _NEC     DVD_RW ND-3551A  2.01 PQ: 0 ANSI: 5
[    2.850659] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.850662] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.850819] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.850976] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.113275] kjournald starting.  Commit interval 5 seconds
[    3.113311] EXT3-fs (sda5): mounted filesystem with ordered data mode
[   17.721197] Adding 6289412k swap on /dev/sda8.  Priority:-1 extents:1 across:6289412k 
[   17.733853] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.766710] udevd[364]: starting version 175
[   17.812249] lp: driver loaded but no devices found
[   18.016744] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   18.016852] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   18.161543] parport_pc 00:0a: reported by Plug and Play ACPI
[   18.161600] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.177644] EXT3-fs (sda5): using internal journal
[   18.248283] lp0: using parport0 (interrupt-driven).
[   18.449538] cfg80211: Calling CRDA to update world regulatory domain
[   18.453855] type=1400 audit(1359910118.938:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=602 comm="apparmor_parser"
[   18.454369] type=1400 audit(1359910118.938:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=602 comm="apparmor_parser"
[   18.454663] type=1400 audit(1359910118.938:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=602 comm="apparmor_parser"
[   18.477749] kjournald starting.  Commit interval 5 seconds
[   18.477989] EXT3-fs (sda6): using internal journal
[   18.477995] EXT3-fs (sda6): mounted filesystem with ordered data mode
[   18.658758] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   18.658767] snd_intel8x0 0000:00:04.0: PCI INT A -> Link[APCJ] -> GSI 22 (level, low) -> IRQ 22
[   18.658796] snd_intel8x0 0000:00:04.0: setting latency timer to 64
[   18.726663] kjournald starting.  Commit interval 5 seconds
[   18.727162] EXT3-fs (sda7): using internal journal
[   18.727168] EXT3-fs (sda7): mounted filesystem with ordered data mode
[   18.750954] nvidia: module license 'NVIDIA' taints kernel.
[   18.750959] Disabling lock debugging due to kernel taint
[   18.880463] usb 1-10: reset high-speed USB device number 3 using ehci_hcd
[   19.558597] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.558603] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558606] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.558610] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558613] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.558616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558619] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.558623] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558626] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.558629] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558632] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.558635] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558638] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.558642] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558645] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.558648] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558651] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.558655] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558657] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.558661] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558664] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.558667] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558670] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.558674] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558677] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.558680] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   19.558683] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.558686] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   19.560332] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   19.560357] nvidia 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   19.560369] nvidia 0000:05:00.0: setting latency timer to 64
[   19.560374] vgaarb: device changed decodes: PCI:0000:05:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.565873] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.64  Tue Oct 30 11:09:29 PDT 2012
[   19.577420] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   19.578924] Registered led device: rt2800usb-phy0::radio
[   19.578976] Registered led device: rt2800usb-phy0::assoc
[   19.579028] Registered led device: rt2800usb-phy0::quality
[   19.579079] usbcore: registered new interface driver rt2800usb
[   19.608169] intel8x0_measure_ac97_clock: measured 53631 usecs (2632 samples)
[   19.608173] intel8x0: clocking to 46947
[   19.622784] ppdev: user-space parallel port driver
[   19.651526] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.651532] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651535] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.651539] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651542] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.651546] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651548] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.651552] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651555] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.651558] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651561] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.651564] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651567] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.651570] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651573] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.651577] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651579] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.651583] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651586] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.651589] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651592] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.651595] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651598] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.651601] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651604] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.651608] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651610] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.651614] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651618] cfg80211: World regulatory domain updated:
[   19.651620] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.651623] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651626] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651629] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.651632] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.651635] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.369271] init: failsafe main process (791) killed by TERM signal
[   20.690268] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   20.690273] vesafb: scrolling: redraw
[   20.690276] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.691002] vesafb: framebuffer at 0xe0000000, mapped to 0xf8800000, using 5120k, total 5120k
[   20.691717] Console: switching to colour frame buffer device 160x64
[   20.691761] fb0: VESA VGA frame buffer device
[   20.757424] Bluetooth: Core ver 2.16
[   20.757463] NET: Registered protocol family 31
[   20.757465] Bluetooth: HCI device and connection manager initialized
[   20.757469] Bluetooth: HCI socket layer initialized
[   20.757471] Bluetooth: L2CAP socket layer initialized
[   20.758518] Bluetooth: SCO socket layer initialized
[   20.779768] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.779772] Bluetooth: BNEP filters: protocol multicast
[   20.852551] Bluetooth: RFCOMM TTY layer initialized
[   20.852559] Bluetooth: RFCOMM socket layer initialized
[   20.852561] Bluetooth: RFCOMM ver 1.11
[   20.899797] type=1400 audit(1359910121.382:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=885 comm="apparmor_parser"
[   20.910308] type=1400 audit(1359910121.394:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=885 comm="apparmor_parser"
[   21.102592] type=1400 audit(1359910121.586:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=916 comm="apparmor_parser"
[   21.107136] type=1400 audit(1359910121.590:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=917 comm="apparmor_parser"
[   21.108720] type=1400 audit(1359910121.594:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=917 comm="apparmor_parser"
[   21.109020] type=1400 audit(1359910121.594:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=917 comm="apparmor_parser"
[   21.123423] type=1400 audit(1359910121.606:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=918 comm="apparmor_parser"
[   22.503739] NVRM: Your system is not currently configured to drive a VGA console
[   22.503746] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   22.503750] NVRM: requires the use of a text-mode VGA console. Use of other console
[   22.503753] NVRM: drivers including, but not limited to, vesafb, may result in
[   22.503756] NVRM: corruption and stability problems, and is not supported.
[   23.129626] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.129974] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.136351] forcedeth 0000:00:0a.0: eth0: no link during initialization
[   23.139021] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.141979] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.546747] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 1)
[   27.549630] wlan0: authenticated
[   27.568746] wlan0: associate with 00:1e:8c:3e:09:3f (try 1)
[   27.571880] wlan0: RX AssocResp from 00:1e:8c:3e:09:3f (capab=0x11 status=0 aid=3)
[   27.571884] wlan0: associated
[   27.579308] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.872019] wlan0: no IPv6 routers present
[   45.345861] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[  321.650686] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59850, forcing to 0
[  321.650692] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[  322.011502] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 44984, forcing to 0
[  322.011508] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1195.894827] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 29300, forcing to 0
[ 1195.894838] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1458.968819] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 49007, forcing to 0
[ 1458.968826] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1461.210859] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 15369, forcing to 0
[ 1461.210865] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1461.286846] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30061, forcing to 0
[ 1461.286856] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1461.399992] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 15369, forcing to 0
[ 1461.400002] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1462.044848] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 7710, forcing to 0
[ 1462.044854] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1462.608862] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30389, forcing to 0
[ 1462.608873] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1464.459904] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 53990, forcing to 0
[ 1464.459910] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1465.627092] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 19067, forcing to 0
[ 1465.627098] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1466.308052] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62672, forcing to 0
[ 1466.308058] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1467.651840] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 20790, forcing to 0
[ 1467.651846] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1469.033288] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 61901, forcing to 0
[ 1469.033294] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1469.887745] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 17342, forcing to 0
[ 1469.887751] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1471.887852] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 48457, forcing to 0
[ 1471.887858] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1473.001857] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 27473, forcing to 0
[ 1473.001863] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1492.085759] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 19816, forcing to 0
[ 1492.085770] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1493.862855] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 7710, forcing to 0
[ 1493.862862] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1494.073015] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 7710, forcing to 0
[ 1494.073022] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1494.169901] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 51495, forcing to 0
[ 1494.169907] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1494.420468] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 39097, forcing to 0
[ 1494.420474] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1526.558029] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 13977, forcing to 0
[ 1526.558035] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1527.577582] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 15027, forcing to 0
[ 1527.577589] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1528.775879] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 50312, forcing to 0
[ 1528.775885] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1529.074866] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59043, forcing to 0
[ 1529.074876] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1530.120146] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36646, forcing to 0
[ 1530.120153] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1530.345903] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 20857, forcing to 0
[ 1530.345910] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1531.303858] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 64904, forcing to 0
[ 1531.303864] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1532.702897] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 45923, forcing to 0
[ 1532.702904] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1533.759856] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 40570, forcing to 0
[ 1533.759862] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1534.259848] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 53150, forcing to 0
[ 1534.259854] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1534.872891] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 52835, forcing to 0
[ 1534.872897] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1536.388883] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 41097, forcing to 0
[ 1536.388889] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1536.797898] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36195, forcing to 0
[ 1536.797904] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1537.447853] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59480, forcing to 0
[ 1537.447859] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1537.567363] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 6391, forcing to 0
[ 1537.567369] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1539.279396] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 19974, forcing to 0
[ 1539.279403] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1540.437064] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 22751, forcing to 0
[ 1540.437070] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1540.585854] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 57635, forcing to 0
[ 1540.585860] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1544.112898] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 5973, forcing to 0
[ 1544.112904] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1545.237855] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 60240, forcing to 0
[ 1545.237861] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1545.304278] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 15659, forcing to 0
[ 1545.304284] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1545.917014] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59355, forcing to 0
[ 1545.917021] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1546.959622] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 44393, forcing to 0
[ 1546.959628] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1547.342888] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 5692, forcing to 0
[ 1547.342894] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1553.128501] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30590, forcing to 0
[ 1553.128507] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1554.548239] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56189, forcing to 0
[ 1554.548245] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1554.678898] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 61281, forcing to 0
[ 1554.678904] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1554.858281] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62006, forcing to 0
[ 1554.858288] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1554.994403] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62006, forcing to 0
[ 1554.994409] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1555.430902] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 54185, forcing to 0
[ 1555.430908] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1559.043541] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 7488, forcing to 0
[ 1559.043548] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1569.882852] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 11084, forcing to 0
[ 1569.882858] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1571.470660] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 18878, forcing to 0
[ 1571.470667] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1572.195291] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 7443, forcing to 0
[ 1572.195297] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1572.906852] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42497, forcing to 0
[ 1572.906859] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1572.947867] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 41021, forcing to 0
[ 1572.947874] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1586.163898] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 52377, forcing to 0
[ 1586.163905] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1587.924644] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 19963, forcing to 0
[ 1587.924650] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1588.229678] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4088, forcing to 0
[ 1588.229685] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1588.306769] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4088, forcing to 0
[ 1588.306776] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1588.650737] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4088, forcing to 0
[ 1588.650747] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1589.263777] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4088, forcing to 0
[ 1589.263788] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1590.794923] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4088, forcing to 0
[ 1590.794934] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1592.949790] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4088, forcing to 0
[ 1592.949801] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1597.864758] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4088, forcing to 0
[ 1597.864765] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1599.383894] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 63517, forcing to 0
[ 1599.383901] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1599.410857] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62836, forcing to 0
[ 1599.410863] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1600.426982] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 39692, forcing to 0
[ 1600.426988] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1600.562924] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 39692, forcing to 0
[ 1600.562935] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1600.940282] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 39692, forcing to 0
[ 1600.940292] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1607.595935] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4088, forcing to 0
[ 1607.595946] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1682.722963] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30107, forcing to 0
[ 1682.722970] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1683.074914] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 26547, forcing to 0
[ 1683.074924] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1684.294415] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 38827, forcing to 0
[ 1684.294421] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1687.037656] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 60643, forcing to 0
[ 1687.037662] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1687.432396] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4060, forcing to 0
[ 1687.432402] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1687.759934] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 55858, forcing to 0
[ 1687.759940] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1688.782934] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 34998, forcing to 0
[ 1688.782940] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1688.800094] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 39360, forcing to 0
[ 1688.800110] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1688.952089] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 39360, forcing to 0
[ 1688.952095] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1689.416285] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 38158, forcing to 0
[ 1689.416291] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1690.716871] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62523, forcing to 0
[ 1690.716877] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1691.211055] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 40939, forcing to 0
[ 1691.211061] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1694.727896] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36275, forcing to 0
[ 1694.727902] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1695.725160] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 26975, forcing to 0
[ 1695.725166] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1697.417916] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 43670, forcing to 0
[ 1697.417922] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1697.827593] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 19503, forcing to 0
[ 1697.827600] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1698.012402] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 58300, forcing to 0
[ 1698.012408] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1701.568914] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 9254, forcing to 0
[ 1701.568920] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1701.575901] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 5703, forcing to 0
[ 1701.575907] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1701.615176] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 22250, forcing to 0
[ 1701.615182] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1701.818175] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 61303, forcing to 0
[ 1701.818181] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1701.958927] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 64162, forcing to 0
[ 1701.958934] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1703.678919] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 31768, forcing to 0
[ 1703.678926] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1715.329159] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42161, forcing to 0
[ 1715.329165] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1718.488082] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 55309, forcing to 0
[ 1718.488089] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1718.625971] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 55309, forcing to 0
[ 1718.625977] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1719.829143] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 46971, forcing to 0
[ 1719.829149] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1719.901683] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 46971, forcing to 0
[ 1719.901689] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1720.175991] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62637, forcing to 0
[ 1720.175998] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1724.804304] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 49203, forcing to 0
[ 1724.804311] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1724.884071] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36133, forcing to 0
[ 1724.884077] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1725.502915] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 48745, forcing to 0
[ 1725.502922] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1726.260884] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 22072, forcing to 0
[ 1726.260891] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1726.528920] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 43923, forcing to 0
[ 1726.528926] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1732.535434] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 12224, forcing to 0
[ 1732.535445] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1733.097875] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 34673, forcing to 0
[ 1733.097881] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1733.607654] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42913, forcing to 0
[ 1733.607661] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1734.321409] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 63500, forcing to 0
[ 1734.321415] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1735.418878] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 31225, forcing to 0
[ 1735.418884] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1738.334871] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 18715, forcing to 0
[ 1738.334877] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1739.837135] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 55100, forcing to 0
[ 1739.837142] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1741.629925] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 13721, forcing to 0
[ 1741.629932] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1776.011882] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 28871, forcing to 0
[ 1776.011889] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1776.485539] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 9764, forcing to 0
[ 1776.485550] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1777.143819] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 26987, forcing to 0
[ 1777.143825] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1777.272906] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42715, forcing to 0
[ 1777.272912] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1777.348893] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42715, forcing to 0
[ 1777.348899] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1797.405437] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 20618, forcing to 0
[ 1797.405443] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1797.579558] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 19152, forcing to 0
[ 1797.579564] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1798.145819] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 54603, forcing to 0
[ 1798.145825] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1799.580891] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 24888, forcing to 0
[ 1799.580897] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1800.105274] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 28632, forcing to 0
[ 1800.105280] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1800.194797] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 28632, forcing to 0
[ 1800.194812] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1800.475889] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 53825, forcing to 0
[ 1800.475895] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1815.225905] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62673, forcing to 0
[ 1815.225911] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1815.705550] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 34049, forcing to 0
[ 1815.705557] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1815.753277] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 8551, forcing to 0
[ 1815.753284] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1817.049056] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 32809, forcing to 0
[ 1817.049063] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1817.283057] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 48543, forcing to 0
[ 1817.283063] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1818.178899] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 58638, forcing to 0
[ 1818.178905] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1819.315317] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 17911, forcing to 0
[ 1819.315324] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1819.915018] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 33251, forcing to 0
[ 1819.915024] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1833.406926] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 14352, forcing to 0
[ 1833.406933] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1845.708952] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 45176, forcing to 0
[ 1845.708958] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1846.677932] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 64811, forcing to 0
[ 1846.677938] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1847.609918] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 61536, forcing to 0
[ 1847.609924] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1847.740920] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59093, forcing to 0
[ 1847.740926] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1847.765945] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 8257, forcing to 0
[ 1847.765952] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1847.826310] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59093, forcing to 0
[ 1847.826316] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1848.103835] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59093, forcing to 0
[ 1848.103850] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1848.662968] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59093, forcing to 0
[ 1848.662979] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1849.790057] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59093, forcing to 0
[ 1849.790068] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1852.040790] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59093, forcing to 0
[ 1852.040796] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1856.341950] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59093, forcing to 0
[ 1856.341961] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1860.350864] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 33064, forcing to 0
[ 1860.350870] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1860.487902] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 33064, forcing to 0
[ 1860.487908] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1861.757935] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 57666, forcing to 0
[ 1861.757941] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1861.870902] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 22075, forcing to 0
[ 1861.870908] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1862.137023] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 54067, forcing to 0
[ 1862.137029] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1863.372977] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 23399, forcing to 0
[ 1863.372983] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1864.390441] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 10023, forcing to 0
[ 1864.390447] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1865.090811] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59093, forcing to 0
[ 1865.090817] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1888.254947] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 31884, forcing to 0
[ 1888.254954] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1891.494906] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30886, forcing to 0
[ 1891.494912] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1891.697699] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 41497, forcing to 0
[ 1891.697705] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1891.967080] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56296, forcing to 0
[ 1891.967090] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1893.212070] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 28090, forcing to 0
[ 1893.212076] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1896.884555] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 15560, forcing to 0
[ 1896.884561] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1897.450083] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 38807, forcing to 0
[ 1897.450090] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1898.104841] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 23403, forcing to 0
[ 1898.104848] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1898.591552] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 24673, forcing to 0
[ 1898.591558] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1901.632897] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 0, forcing to 0
[ 1901.632904] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1913.343948] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 19824, forcing to 0
[ 1913.343955] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1932.753947] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 53578, forcing to 0
[ 1932.753954] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1933.183080] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 27591, forcing to 0
[ 1933.183087] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1935.606286] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 37957, forcing to 0
[ 1935.606293] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1937.247418] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 21492, forcing to 0
[ 1937.247425] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1937.342187] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 21492, forcing to 0
[ 1937.342197] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1950.367143] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 10407, forcing to 0
[ 1950.367149] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1950.698910] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 37229, forcing to 0
[ 1950.698917] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1950.881003] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36099, forcing to 0
[ 1950.881009] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1950.963457] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36099, forcing to 0
[ 1950.963464] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1951.008946] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30437, forcing to 0
[ 1951.008953] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1951.768464] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30462, forcing to 0
[ 1951.768470] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1951.811327] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 47187, forcing to 0
[ 1951.811333] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1953.183413] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 32321, forcing to 0
[ 1953.183419] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1955.491942] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4810, forcing to 0
[ 1955.491948] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1965.576333] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 20747, forcing to 0
[ 1965.576339] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1966.421407] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 58310, forcing to 0
[ 1966.421413] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1966.619909] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 12431, forcing to 0
[ 1966.619915] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1968.177402] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 24868, forcing to 0
[ 1968.177408] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1978.512687] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56945, forcing to 0
[ 1978.512693] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1978.569971] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 12999, forcing to 0
[ 1978.569977] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 1979.517531] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 49831, forcing to 0
[ 1979.517538] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2007.909476] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 8135, forcing to 0
[ 2007.909487] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2009.817328] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56239, forcing to 0
[ 2009.817334] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2010.245074] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62343, forcing to 0
[ 2010.245080] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2011.890410] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 54387, forcing to 0
[ 2011.890416] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2012.188814] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 48383, forcing to 0
[ 2012.188821] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2012.266334] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 48383, forcing to 0
[ 2012.266341] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2013.468694] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 15000, forcing to 0
[ 2013.468700] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2017.067977] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 18732, forcing to 0
[ 2017.067988] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2018.503596] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 64762, forcing to 0
[ 2018.503602] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2019.556957] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56937, forcing to 0
[ 2019.556964] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2021.567954] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 50293, forcing to 0
[ 2021.567961] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2021.984955] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30997, forcing to 0
[ 2021.984961] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2040.105306] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 50180, forcing to 0
[ 2040.105316] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2040.295090] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 57606, forcing to 0
[ 2040.295096] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2040.879956] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 44800, forcing to 0
[ 2040.879962] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2120.497935] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 0, forcing to 0
[ 2120.497942] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2120.530970] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59911, forcing to 0
[ 2120.530976] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2120.998845] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 60021, forcing to 0
[ 2120.998851] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2121.071823] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 60021, forcing to 0
[ 2121.071830] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2128.787057] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 33932, forcing to 0
[ 2128.787063] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2129.415602] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 58961, forcing to 0
[ 2129.415608] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2129.767932] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 49969, forcing to 0
[ 2129.767938] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2130.821400] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59403, forcing to 0
[ 2130.821406] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2132.102970] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 46893, forcing to 0
[ 2132.102976] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2132.385946] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 0, forcing to 0
[ 2132.385953] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2132.470951] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 0, forcing to 0
[ 2132.470958] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2133.637057] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 24668, forcing to 0
[ 2133.637063] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2134.563016] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 60021, forcing to 0
[ 2134.563022] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2139.203239] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 5482, forcing to 0
[ 2139.203246] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2139.312224] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 0, forcing to 0
[ 2139.312230] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2174.044959] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 35722, forcing to 0
[ 2174.044965] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2175.128940] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 28566, forcing to 0
[ 2175.128946] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2175.474956] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 8035, forcing to 0
[ 2175.474962] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2180.584239] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 29050, forcing to 0
[ 2180.584245] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2181.538935] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 30301, forcing to 0
[ 2181.538942] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2181.538947] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59065, forcing to 0
[ 2181.538951] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2181.851732] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 5184, forcing to 0
[ 2181.851739] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2182.323585] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 24969, forcing to 0
[ 2182.323591] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2182.777104] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56209, forcing to 0
[ 2182.777110] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2182.854478] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56209, forcing to 0
[ 2182.854484] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2183.231942] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56209, forcing to 0
[ 2183.231952] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2183.740936] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56209, forcing to 0
[ 2183.740943] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2184.751983] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56209, forcing to 0
[ 2184.751990] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2186.981968] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56209, forcing to 0
[ 2186.981974] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2187.051958] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 34915, forcing to 0
[ 2187.051964] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2187.535966] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 22559, forcing to 0
[ 2187.535972] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2189.729067] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 34803, forcing to 0
[ 2189.729073] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2189.825956] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 34803, forcing to 0
[ 2189.825962] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2192.312694] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 50911, forcing to 0
[ 2192.312700] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2192.528941] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 4092, forcing to 0
[ 2192.528948] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2193.084941] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 57580, forcing to 0
[ 2193.084948] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2193.532966] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 65517, forcing to 0
[ 2193.532972] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2193.869950] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 34770, forcing to 0
[ 2193.869957] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2217.652717] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 60757, forcing to 0
[ 2217.652723] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2218.469072] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 12071, forcing to 0
[ 2218.469078] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2218.501936] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 34944, forcing to 0
[ 2218.501942] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2218.528143] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 43458, forcing to 0
[ 2218.528149] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2219.133938] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 15652, forcing to 0
[ 2219.133944] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2219.886943] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 21847, forcing to 0
[ 2219.886949] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2219.894140] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36342, forcing to 0
[ 2219.894146] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2248.303941] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 5678, forcing to 0
[ 2248.303947] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2249.533452] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 20537, forcing to 0
[ 2249.533458] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2250.068373] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 8698, forcing to 0
[ 2250.068378] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2271.266006] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59181, forcing to 0
[ 2271.266012] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2271.316940] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 10787, forcing to 0
[ 2271.316946] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2271.349949] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 5520, forcing to 0
[ 2271.349955] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2271.389976] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 40984, forcing to 0
[ 2271.389982] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2271.756459] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 49019, forcing to 0
[ 2271.756465] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2298.095492] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 19772, forcing to 0
[ 2298.095498] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2298.147579] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 20390, forcing to 0
[ 2298.147585] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2299.041947] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 9368, forcing to 0
[ 2299.041953] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2299.246969] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 60431, forcing to 0
[ 2299.246975] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2299.430951] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 59914, forcing to 0
[ 2299.430957] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2299.985119] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42278, forcing to 0
[ 2299.985125] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2301.201746] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 7035, forcing to 0
[ 2301.201752] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2323.083492] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42574, forcing to 0
[ 2323.083498] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2324.405142] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 32067, forcing to 0
[ 2324.405148] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2324.578960] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 32067, forcing to 0
[ 2324.578966] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2326.343629] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 10690, forcing to 0
[ 2326.343635] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2345.210510] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 42590, forcing to 0
[ 2345.210516] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2346.239993] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 44695, forcing to 0
[ 2346.239999] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2346.776987] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 21389, forcing to 0
[ 2346.776993] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2346.868964] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36704, forcing to 0
[ 2346.868970] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2347.138036] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36704, forcing to 0
[ 2347.138046] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2349.877974] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 20316, forcing to 0
[ 2349.877980] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2350.299003] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 50611, forcing to 0
[ 2350.299009] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2350.650970] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 25652, forcing to 0
[ 2350.650981] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2372.535457] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 14848, forcing to 0
[ 2372.535463] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2372.616960] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 12214, forcing to 0
[ 2372.616966] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2373.031959] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62700, forcing to 0
[ 2373.031965] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2373.791124] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 12867, forcing to 0
[ 2373.791130] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2376.356961] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 37734, forcing to 0
[ 2376.356967] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2376.465987] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 60583, forcing to 0
[ 2376.465993] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2376.560022] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56088, forcing to 0
[ 2376.560028] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2376.639965] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56088, forcing to 0
[ 2376.639971] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2401.724959] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36597, forcing to 0
[ 2401.724965] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2402.369916] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 61411, forcing to 0
[ 2402.369922] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2402.908037] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 37655, forcing to 0
[ 2402.908044] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2403.081140] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 63497, forcing to 0
[ 2403.081146] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2405.264622] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 54216, forcing to 0
[ 2405.264628] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2405.342105] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 54216, forcing to 0
[ 2405.342111] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2426.540998] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62317, forcing to 0
[ 2426.541004] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2426.744058] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 62317, forcing to 0
[ 2426.744068] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2427.483014] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 18038, forcing to 0
[ 2427.483020] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2427.521966] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 17560, forcing to 0
[ 2427.521973] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2427.575972] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 64104, forcing to 0
[ 2427.575978] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2428.257004] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 51801, forcing to 0
[ 2428.257011] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2428.664213] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 61316, forcing to 0
[ 2428.664219] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2428.669982] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 31027, forcing to 0
[ 2428.669988] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2429.434018] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 63411, forcing to 0
[ 2429.434025] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2450.493017] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 17866, forcing to 0
[ 2450.493028] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2450.574222] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 17866, forcing to 0
[ 2450.574232] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2451.630143] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56880, forcing to 0
[ 2451.630149] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2451.708967] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56880, forcing to 0
[ 2451.708973] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2516.909996] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 36103, forcing to 0
[ 2516.910002] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2517.445538] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56648, forcing to 0
[ 2517.445544] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2519.000075] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 56301, forcing to 0
[ 2519.000081] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2519.477021] phy0 -> rt2800usb_fill_rxdone: Error - Bad frame size 61013, forcing to 0
[ 2519.477027] phy0 -> rt2x00lib_rxdone: Error - Wrong frame size 0 max 3840.
[ 2524.504296] ieee80211 phy0: wlan0: No probe response from AP 00:1e:8c:3e:09:3f after 500ms, disconnecting.
[ 2524.519633] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2524.519640] cfg80211: Restoring regulatory settings
[ 2524.519645] cfg80211: Calling CRDA to update world regulatory domain
[ 2524.526620] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526626] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526629] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526633] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526636] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526639] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526642] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526645] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526648] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526651] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526654] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526658] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526660] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526664] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526666] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526670] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526672] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526676] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526679] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526682] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526685] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526688] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526691] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526694] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2524.526697] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526700] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2524.526703] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 2524.526707] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2524.526710] cfg80211: World regulatory domain updated:
[ 2524.526712] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2524.526716] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526719] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2524.526722] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2524.526725] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2524.526728] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2527.916602] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 1)
[ 2528.116044] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 2)
[ 2528.316041] wlan0: authenticate with 00:1e:8c:3e:09:3f (try 3)
[ 2528.516048] wlan0: authentication with 00:1e:8c:3e:09:3f timed out
[ 2540.036583] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```sudo lshw -C network 
```

  *-network
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: &#1041;&#1077;&#1089;&#1087;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1081; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 1
       bus info: usb@1:10
       &#1083;&#1086;&#1075;&#1080;&#1095;&#1077;&#1089;&#1082;&#1086;&#1077; &#1080;&#1084;&#1103;: wlan0
       &#1089;&#1077;&#1088;&#1080;&#1081;&#1085;&#1099;&#1081; &#8470;: 00:25:9c:a0:12:28
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: ethernet physical wireless
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: broadcast=yes driver=rt2800usb driverversion=3.2.0-37-generic-pae firmware=0.29 link=no multicast=yes wireless=IEEE 802.11bg

```iwlist wlan0 scan 
```

wlan0     No scan results


```

My router is asus wl500gpv2. The another devices is work correctly.

What I must to do for repair this situation, or what I need read?
Thank you!

---

### Post by lma33 on 2013-02-05
Help me, please!

---

