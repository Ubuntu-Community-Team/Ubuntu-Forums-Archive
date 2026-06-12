---
title: "Network crashes randomly in 10.04LTS requiring reboot"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by dead4red on 2011-01-14
IN SHORT: My network crashes randomly under regular traffic and more rapidly under high traffic (i.e. running Transmission) and I have to reboot to get it to start working again. Please, HELP!

About system:
Toshiba Satellite A105-S2021
512MB RAM
BIOS V2.30 (Latest)
Ubuntu 10.04LTS (Fresh install, not an upgrade) (Only OS on this machine)
2.6.32-27-generic #49-Ubuntu SMP
Running on 100% on cord power but battery is 100% and tests fine
Temperatures all normal (CPU ~40 degrees C) and fans fully operational

"lshw -C network" output while network is functional:
  *-network:0            
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 01
       serial: 00:16:e3:0d:2f:7b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.102 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:c0200000-c020ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:34:ed:a6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.100 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:a000(size=256) memory:c0211000-c02110ff


Report in Message log immediately after network crash: (Full dmesg in following post)

[ 2240.000049] ------------[ cut here ]------------
[ 2240.000066] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
[ 2240.000070] Hardware name: Satellite A105
[ 2240.000073] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[ 2240.000075] Modules linked in: binfmt_misc ppdev arc4 snd_hda_codec_realtek snd_hda_codec_si3054 fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy joydev snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia snd_timer snd_seq_device radeon ttm ath5k snd drm_kms_helper mac80211 ath yenta_socket drm i2c_algo_bit rsrc_nonstatic cfg80211 ati_agp soundcore video psmouse serio_raw led_class pcmcia_core i2c_piix4 output snd_page_alloc agpgart shpchp lp parport 8139too 8139cp mii sata_sil pata_atiixp
[ 2240.000136] Pid: 0, comm: swapper Not tainted 2.6.32-27-generic #49-Ubuntu
[ 2240.000139] Call Trace:
[ 2240.000147]  [<c014c802>] warn_slowpath_common+0x72/0xa0
[ 2240.000152]  [<c04da1ee>] ? dev_watchdog+0x1fe/0x210
[ 2240.000156]  [<c04da1ee>] ? dev_watchdog+0x1fe/0x210
[ 2240.000160]  [<c014c87b>] warn_slowpath_fmt+0x2b/0x30
[ 2240.000164]  [<c04da1ee>] dev_watchdog+0x1fe/0x210
[ 2240.000171]  [<c0163d70>] ? insert_work+0x60/0xb0
[ 2240.000178]  [<c012a688>] ? default_spin_lock_flags+0x8/0x10
[ 2240.000184]  [<c058d9bf>] ? _spin_lock_irqsave+0x2f/0x50
[ 2240.000188]  [<c0164036>] ? __queue_work+0x36/0x50
[ 2240.000193]  [<c015ba1e>] run_timer_softirq+0x13e/0x2c0
[ 2240.000199]  [<c01764bc>] ? tick_handle_oneshot_broadcast+0x12c/0x140
[ 2240.000204]  [<c04d9ff0>] ? dev_watchdog+0x0/0x210
[ 2240.000208]  [<c0153448>] __do_softirq+0x98/0x1b0
[ 2240.000216]  [<c01a0054>] ? handle_IRQ_event+0x54/0x150
[ 2240.000220]  [<c01a32e9>] ? move_native_irq+0x19/0x50
[ 2240.000224]  [<c01535a5>] do_softirq+0x45/0x50
[ 2240.000228]  [<c01536f5>] irq_exit+0x65/0x70
[ 2240.000233]  [<c0591e35>] do_IRQ+0x55/0xc0
[ 2240.000237]  [<c016d935>] ? sched_clock_local+0xa5/0x180
[ 2240.000242]  [<c0103a30>] common_interrupt+0x30/0x40
[ 2240.000247]  [<c016007b>] ? k_getrusage+0x3b/0x2f0
[ 2240.000253]  [<c039e714>] ? acpi_idle_enter_simple+0x117/0x148
[ 2240.000257]  [<c039e42a>] acpi_idle_enter_bm+0xd1/0x2a4
[ 2240.000263]  [<c04a254a>] cpuidle_idle_call+0x7a/0x100
[ 2240.000267]  [<c01021d4>] cpu_idle+0x94/0xd0
[ 2240.000273]  [<c057b248>] rest_init+0x58/0x60
[ 2240.000280]  [<c07a58ec>] start_kernel+0x351/0x357
[ 2240.000285]  [<c07a53c7>] ? unknown_bootoption+0x0/0x19e
[ 2240.000290]  [<c07a50aa>] i386_start_kernel+0xaa/0xb1
[ 2240.000293] ---[ end trace a12b427b5053b0da ]---
[ 2243.000102] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2255.000098] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

The "eth0" is repeated infinitely until reboot with an ACPI error (lillian-laptop kernel: [  390.211912] ACPI Error: No installed handler for fixed event [00000000] (20090903/evevent-306) every several minutes as well. I have been having these ACPI errors a lot and can not find the cause. I have checked my temps and all are normal. I have flashed my BIOS to the latest v2.30 and am running the BIOS defaults. I can not find anything in the BIOS that would appear to help. It is pretty simple BIOS. I have also run the memory test through GRUB for several hours in all of the patterns and come back with absolutely no memory errors (in both memory configurations of 1 X 512MB and 2 X 512MB sticks. I do think that it is not my  router as I have swapped out routers (Linksys), omitted routers, and connected directly to my cable modem (Ubee/Ambit) and still have the same problem. Security setting in Network Manager are WEP 128-bit and IPv6 is "Ignore" for both Ethernet and wireless (as my ISP, RoadRunner, does not support IPv6). Could this be an IPv6 issue? Also, my other machines networks appear fine and appear to have no outage when the network fails in my Ubuntu laptop. Also, this machine worked perfectly on it's original install of 9.10 then I upgraded via "sudo apt-get update && sudo apt-get dist-upgrade"  to 10.04 and the network failure began. I then eventually upgraded to 10.10 via "sudo apt-get update && sudo apt-get dist-upgrade" and it continued. So, I did a clean install of 10.04LTS from CD hoping to fix it. It did not. Is there any way that picking up ACPI between 9.10 and 10.04 has done something permanent or that I have failed to undo or change? I would not think network hardware failure since it affects both my Ethernet and my Wireless at the same time. I have been using Ubuntu for over a year and various Linux distros  on and off for over 12 years but am still quite the nubee. I really need help here. I would appreciate any suggestions. I am following this post with a dmesg file from fresh boot to just after network crashes.

---

### Post by dead4red on 2011-01-14
dmesg output from fresh boot to network crash (too large to attach... SORRY):

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-27-generic (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 (Ubuntu 2.6.32-27.49-generic 2.6.32.26+drm33.12)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ea0000 - 0000000037eb0000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eb0000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
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
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  modified: 0000000037ea0000 - 0000000037eb0000 (ACPI data)
[    0.000000]  modified: 0000000037eb0000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  modified: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 297a0000 - 29f377fb
[    0.000000] ACPI: RSDP 000f75e0 00014 (v00 TOSINV)
[    0.000000] ACPI: RSDT 37eaaae6 00038 (v01 TOSINV   RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 37eafef6 00074 (v01 TOSINV Goldfish 06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 37eaaf3a 04FBC (v01 TOSINV    SB450 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 37eb0fc0 00040
[    0.000000] ACPI: APIC 37eaff6a 0005A (v01 TOSINV ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 37eaffc4 0003C (v01 TOSINV   MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 37eaad19 00221 (v01 TOSINV  Cpu0Cst 00003001 INTL 20030224)
[    0.000000] ACPI: SSDT 37eaab1e 001FB (v01 TOSINV    CpuPm 00003000 INTL 20030224)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 6MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [00297a0000 - 0029f377fb]          RAMDISK ==> [00297a0000 - 0029f377fb]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008dd000 - 00008e0118]              BRK ==> [00008dd000 - 00008e0118]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f7630] f7630
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00037ea0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00037ea0
[    0.000000] On node 0 totalpages: 228911
[    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c1001200
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
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 38000000 (gap: 38000000:a8000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227121
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-27-generic root=UUID=071a42a3-e3dc-48eb-af87-c64409da89dc ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4580160 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00037ea0)
[    0.000000] Memory: 886956k/916096k available (4682k kernel code, 28380k reserved, 2120k data, 656k init, 6792k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc0849000   ( 656 kB)
[    0.000000]       .data : 0xc0592a37 - 0xc07a4ce8   (2120 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0592a37   (4682 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1692.166 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3384.33 BogoMIPS (lpj=6768664)
[    0.004029] Security Framework initialized
[    0.004060] AppArmor: AppArmor initialized
[    0.004068] Mount-cache hash table entries: 512
[    0.004221] Initializing cgroup subsys ns
[    0.004227] Initializing cgroup subsys cpuacct
[    0.004232] Initializing cgroup subsys memory
[    0.004244] Initializing cgroup subsys devices
[    0.004247] Initializing cgroup subsys freezer
[    0.004250] Initializing cgroup subsys net_cls
[    0.004278] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004282] CPU: L2 cache: 1024K
[    0.004287] mce: CPU supports 5 MCE banks
[    0.004298] CPU0: Thermal monitoring enabled (TM1)
[    0.004310] Performance Events: p6 PMU driver.
[    0.004319] ... version:                0
[    0.004322] ... bit width:              32
[    0.004324] ... generic registers:      2
[    0.004326] ... value mask:             00000000ffffffff
[    0.004329] ... max period:             000000007fffffff
[    0.004331] ... fixed-purpose events:   0
[    0.004334] ... event mask:             0000000000000003
[    0.004339] Checking 'hlt' instruction... OK.
[    0.021034] SMP alternatives: switching to UP code
[    0.029263] Freeing SMP alternatives: 19k freed
[    0.029279] ACPI: Core revision 20090903
[    0.044011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.044022] ftrace: allocating 21786 entries in 43 pages
[    0.048116] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052110]   alloc irq_desc for 21 on node 0
[    0.052112]   alloc kstat_irqs on node 0
[    0.052256] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.091957] CPU0: Intel(R) Celeron(R) M processor         1.70GHz stepping 08
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (3384.33 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] devtmpfs: initialized
[    0.092001] regulator: core version 0.5
[    0.092001] Time:  1:54:35  Date: 01/14/11
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.092001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 3
[    0.092001] PCI: MCFG area at e0000000 reserved in E820
[    0.092001] PCI: Using MMCONFIG for extended config space
[    0.092001] PCI: Using configuration type 1 for base access
[    0.092001] bio: create slab <bio-0> at 0
[    0.092001] ACPI: EC: Look up EC in DSDT
[    0.108077] ACPI: Interpreter enabled
[    0.108082] ACPI: (supports S0 S3 S4 S5)
[    0.108108] ACPI: Using IOAPIC for interrupt routing
[    0.147803] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
[    0.147866] ACPI: Power Resource [PFA1] (off)
[    0.148131] ACPI: No dock devices found.
[    0.148800] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.149016] pci 0000:00:12.0: reg 10 io port: [0x8440-0x8447]
[    0.149027] pci 0000:00:12.0: reg 14 io port: [0x8430-0x8433]
[    0.149038] pci 0000:00:12.0: reg 18 io port: [0x8420-0x8427]
[    0.149049] pci 0000:00:12.0: reg 1c io port: [0x8410-0x8413]
[    0.149060] pci 0000:00:12.0: reg 20 io port: [0x8400-0x840f]
[    0.149071] pci 0000:00:12.0: reg 24 32bit mmio: [0xc0004000-0xc00041ff]
[    0.149083] pci 0000:00:12.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
[    0.149125] pci 0000:00:12.0: supports D1 D2
[    0.149186] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0005000-0xc0005fff]
[    0.149320] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0006000-0xc0006fff]
[    0.149466] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0007000-0xc0007fff]
[    0.149554] pci 0000:00:13.2: supports D1 D2
[    0.149557] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.149564] pci 0000:00:13.2: PME# disabled
[    0.149617] pci 0000:00:14.0: reg 10 io port: [0x8450-0x845f]
[    0.149628] pci 0000:00:14.0: reg 14 32bit mmio: [0xc0004400-0xc00047ff]
[    0.149674] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.149733] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.149744] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.149755] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
[    0.149766] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
[    0.149777] pci 0000:00:14.1: reg 20 io port: [0x8460-0x846f]
[    0.149902] pci 0000:00:14.2: reg 10 64bit mmio: [0xc0000000-0xc0003fff]
[    0.149983] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.149989] pci 0000:00:14.2: PME# disabled
[    0.150205] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.150212] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.150219] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.150236] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.150254] pci 0000:01:05.0: supports D1 D2
[    0.150285] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.150290] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.150295] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.150373] pci 0000:02:04.0: reg 10 32bit mmio: [0xc0200000-0xc020ffff]
[    0.150538] pci 0000:02:06.0: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]
[    0.150576] pci 0000:02:06.0: supports D1 D2
[    0.150579] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.150587] pci 0000:02:06.0: PME# disabled
[    0.150655] pci 0000:02:07.0: reg 10 io port: [0xa000-0xa0ff]
[    0.150667] pci 0000:02:07.0: reg 14 32bit mmio: [0xc0211000-0xc02110ff]
[    0.150753] pci 0000:02:07.0: supports D1 D2
[    0.150756] pci 0000:02:07.0: PME# supported from D1 D2 D3hot
[    0.150763] pci 0000:02:07.0: PME# disabled
[    0.150834] pci 0000:00:14.4: transparent bridge
[    0.150844] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.150851] pci 0000:00:14.4: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.150902] pci_bus 0000:00: on NUMA node 0
[    0.150907] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.151110] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.151263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.153410] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.153534] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.153655] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.153775] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.153894] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.154013] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.154133] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.154252] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.154382] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.154386] vgaarb: loaded
[    0.154549] SCSI subsystem initialized
[    0.154632] libata version 3.00 loaded.
[    0.154725] usbcore: registered new interface driver usbfs
[    0.154745] usbcore: registered new interface driver hub
[    0.154778] usbcore: registered new device driver usb
[    0.154944] ACPI: WMI: Mapper loaded
[    0.154947] PCI: Using ACPI for IRQ routing
[    0.155147] NetLabel: Initializing
[    0.155149] NetLabel:  domain hash size = 128
[    0.155151] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.155170] NetLabel:  unlabeled traffic allowed by default
[    0.155220] Switching to clocksource tsc
[    0.156001] AppArmor: AppArmor Filesystem Enabled
[    0.156001] pnp: PnP ACPI init
[    0.156001] ACPI: bus type pnp registered
[    0.170810] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:12.0 BAR 6 (0x0-0x7ffff), disabling
[    0.170821] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.170906] pnp: PnP ACPI: found 10 devices
[    0.170908] ACPI: ACPI bus type pnp unregistered
[    0.170914] PnPBIOS: Disabled by ACPI PNP
[    0.170931] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.170941] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.170944] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.170948] system 00:08: ioport range 0x400-0x401 has been reserved
[    0.170952] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.170955] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.170959] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.170962] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.170966] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.170969] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.170973] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.170976] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.170980] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.170984] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.170987] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.170991] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.170995] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.170998] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.171002] system 00:08: ioport range 0x280-0x293 has been reserved
[    0.171005] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.171012] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.171016] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.171020] system 00:09: iomem range 0xc0004800-0xc0004fff has been reserved
[    0.205791] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.205795] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.205801] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.205806] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.205815] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.205818] pci 0000:02:06.0:   IO window: 0x00a400-0x00a4ff
[    0.205825] pci 0000:02:06.0:   IO window: 0x00a800-0x00a8ff
[    0.205833] pci 0000:02:06.0:   PREFETCH window: 0x38000000-0x3bffffff
[    0.205841] pci 0000:02:06.0:   MEM window: 0x40000000-0x43ffffff
[    0.205849] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.205854] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.205862] pci 0000:00:14.4:   MEM window: 0xc0200000-0xc02fffff
[    0.205869] pci 0000:00:14.4:   PREFETCH window: 0x38000000-0x3bffffff
[    0.205906] pci 0000:02:06.0: enabling device (0004 -> 0007)
[    0.205917]   alloc irq_desc for 23 on node -1
[    0.205920]   alloc kstat_irqs on node -1
[    0.205927] pci 0000:02:06.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.205937] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.205941] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.205944] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.205947] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.205951] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.205954] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.205957] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xc02fffff]
[    0.205961] pci_bus 0000:02: resource 2 pref mem [0x38000000-0x3bffffff]
[    0.205964] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.205967] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.205971] pci_bus 0000:03: resource 0 io:  [0xa400-0xa4ff]
[    0.205974] pci_bus 0000:03: resource 1 io:  [0xa800-0xa8ff]
[    0.205977] pci_bus 0000:03: resource 2 pref mem [0x38000000-0x3bffffff]
[    0.205980] pci_bus 0000:03: resource 3 mem: [0x40000000-0x43ffffff]
[    0.206027] NET: Registered protocol family 2
[    0.206139] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.206590] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.208375] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.209565] TCP: Hash tables configured (established 131072 bind 65536)
[    0.209571] TCP reno registered
[    0.209767] NET: Registered protocol family 1
[    0.209799] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.884685] pci 0000:01:05.0: Boot video device
[    0.884956] cpufreq-nforce2: No nForce2 chipset.
[    0.885000] Scanning for low memory corruption every 60 seconds
[    0.885151] audit: initializing netlink socket (disabled)
[    0.885176] type=2000 audit(1294970075.884:1): initialized
[    0.897523] Trying to unpack rootfs image as initramfs...
[    0.912812] highmem bounce pool size: 64 pages
[    0.912822] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.914818] VFS: Disk quotas dquot_6.5.2
[    0.914908] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.921154] fuse init (API version 7.13)
[    0.921312] msgmni has been set to 1719
[    0.921652] alg: No test for stdrng (krng)
[    0.921736] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.921741] io scheduler noop registered
[    0.921743] io scheduler anticipatory registered
[    0.921745] io scheduler deadline registered
[    0.921805] io scheduler cfq registered (default)
[    0.921952] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.921980] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.937067] ACPI: AC Adapter [ADP0] (on-line)
[    0.937196] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.937202] ACPI: Power Button [PWRB]
[    0.937263] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.937333] ACPI: Lid Switch [LID]
[    0.937402] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.937405] ACPI: Power Button [PWRF]
[    0.937855] fan PNP0C0B:00: registered as cooling_device0
[    0.937869] ACPI: Fan [FAN1] (off)
[    0.938269] Marking TSC unstable due to TSC halts in idle
[    0.938468] processor LNXCPU:00: registered as cooling_device1
[    0.942589] Switching to clocksource acpi_pm
[    1.160273] thermal LNXTHERM:01: registered as thermal_zone0
[    1.160291] ACPI: Thermal Zone [TZCR] (49 C)
[    1.162247] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.163867] brd: module loaded
[    1.169025] loop: module loaded
[    1.169177] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.169403] pata_acpi 0000:00:12.0: enabling device (0005 -> 0007)
[    1.169415]   alloc irq_desc for 22 on node -1
[    1.169418]   alloc kstat_irqs on node -1
[    1.169428] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.169517]   alloc irq_desc for 16 on node -1
[    1.169519]   alloc kstat_irqs on node -1
[    1.169525] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.169549] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.169936] Fixed MDIO Bus: probed
[    1.169983] PPP generic driver version 2.4.2
[    1.170040] tun: Universal TUN/TAP device driver, 1.6
[    1.170043] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.170134] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.170159]   alloc irq_desc for 19 on node -1
[    1.170162]   alloc kstat_irqs on node -1
[    1.170167] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.170194] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.170230] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    1.170306] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0007000
[    1.170354] isapnp: Scanning for PnP cards...
[    1.219716] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.219831] usb usb1: configuration #1 chosen from 1 choice
[    1.219868] hub 1-0:1.0: USB hub found
[    1.219880] hub 1-0:1.0: 8 ports detected
[    1.219972] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.219989] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.220023] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.220232] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    1.220254] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0005000
[    1.237238] Freeing initrd memory: 7773k freed
[    1.299221] usb usb2: configuration #1 chosen from 1 choice
[    1.299269] hub 2-0:1.0: USB hub found
[    1.299293] hub 2-0:1.0: 4 ports detected
[    1.299391] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.299421] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.299497] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.299531] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0006000
[    1.387350] usb usb3: configuration #1 chosen from 1 choice
[    1.387383] hub 3-0:1.0: USB hub found
[    1.387399] hub 3-0:1.0: 4 ports detected
[    1.387478] uhci_hcd: USB Universal Host Controller Interface driver
[    1.387620] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.433802] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.433809] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.433938] mice: PS/2 mouse device common for all mice
[    1.434728] ACPI Error: Could not disable RealTimeClock events (20090903/evxfevnt-373)
[    1.434735] rtc_cmos 00:04: RTC can wake from S4
[    1.434795] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.434829] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.434970] device-mapper: uevent: version 1.0.3
[    1.435316] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.435385] device-mapper: multipath: version 1.1.0 loaded
[    1.435389] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.435550] EISA: Probing bus 0 at eisa.0
[    1.435560] Cannot allocate resource for EISA slot 1
[    1.435592] Cannot allocate resource for EISA slot 8
[    1.435595] EISA: Detected 0 cards.
[    1.435700] cpuidle: using governor ladder
[    1.435770] cpuidle: using governor menu
[    1.436312] TCP cubic registered
[    1.436507] NET: Registered protocol family 10
[    1.437032] lo: Disabled Privacy Extensions
[    1.437383] NET: Registered protocol family 17
[    1.437449] Using IPI No-Shortcut mode
[    1.437545] PM: Resume from disk failed.
[    1.437566] registered taskstats version 1
[    1.438203]   Magic number: 11:14:913
[    1.438335] rtc_cmos 00:04: setting system clock to 2011-01-14 01:54:37 UTC (1294970077)
[    1.438339] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.438342] EDD information not available.
[    1.569270] isapnp: No Plug & Play device found
[    1.569381] Freeing unused kernel memory: 656k freed
[    1.570084] Write protecting the kernel text: 4684k
[    1.570127] Write protecting the kernel read-only data: 1840k
[    1.577710] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.592887] udev: starting version 151
[    1.668360] ACPI: Battery Slot [BAT0] (battery present)
[    1.913951] scsi0 : pata_atiixp
[    1.919408] scsi1 : pata_atiixp
[    1.921113] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8460 irq 14
[    1.921118] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8468 irq 15
[    1.921390] sata_sil 0000:00:12.0: version 2.4
[    1.921637] scsi2 : sata_sil
[    1.921954] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.921973] 8139cp 0000:02:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.922096] scsi3 : sata_sil
[    1.922468] ata3: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc0004080 irq 22
[    1.922473] ata4: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc00040c0 irq 22
[    2.252780] ata2.00: ATAPI: MATSHITADVD-RAM UJ-841S, 1.50, max UDMA/33
[    2.268725] ata2.00: configured for UDMA/33
[    2.272533] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-841S  1.50 PQ: 0 ANSI: 5
[    2.281035] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.281040] Uniform CD-ROM driver Revision: 3.20
[    2.281343] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.281506] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    2.352372] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.707311] ata3.00: ATA-6: TOSHIBA MK1032GSX, AS021G, max UDMA/100
[    2.707315] ata3.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.721134] ata3.00: configured for UDMA/100
[    2.721268] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1032GS AS02 PQ: 0 ANSI: 5
[    2.721425] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.721696] sd 2:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    2.721753] sd 2:0:0:0: [sda] Write Protect is off
[    2.721757] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.721787] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.721948]  sda: sda1 sda2 < sda5 >
[    2.789070] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.040066] ata4: SATA link down (SStatus 0 SControl 300)
[    3.047594] 8139too Fast Ethernet driver 0.9.28
[    3.047661]   alloc irq_desc for 20 on node -1
[    3.047664]   alloc kstat_irqs on node -1
[    3.047675] 8139too 0000:02:07.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.051455] eth0: RealTek RTL8139 at 0xa000, 00:a0:d1:34:ed:a6, IRQ 20
[    3.412210] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   17.409017] Adding 2621432k swap on /dev/sda5.  Priority:-1 extents:1 across:2621432k 
[   17.433194] udev: starting version 151
[   17.599344] lp: driver loaded but no devices found
[   17.754122] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.895966] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8450, revision 0
[   17.906711] Linux agpgart interface v0.103
[   18.074214] cfg80211: Calling CRDA to update world regulatory domain
[   18.111832] cfg80211: World regulatory domain updated:
[   18.111838]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.111842]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.111845]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.111849]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.111852]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.111855]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.129171] acpi device:17: registered as cooling_device2
[   18.129687] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:15/LNXVIDEO:00/input/input5
[   18.130128] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   18.151689] yenta_cardbus 0000:02:06.0: CardBus bridge found [1179:ff10]
[   18.151727] yenta_cardbus 0000:02:06.0: Using CSCINT to route CSC interrupts to PCI
[   18.151730] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   18.151738] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01111002, devctl 0x44
[   18.177651] [drm] Initialized drm 1.1.0 20060810
[   18.196663] type=1505 audit(1294970094.257:2):  operation="profile_load" pid=493 name="/sbin/dhclient3"
[   18.197423] type=1505 audit(1294970094.257:3):  operation="profile_load" pid=493 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.197842] type=1505 audit(1294970094.257:4):  operation="profile_load" pid=493 name="/usr/lib/connman/scripts/dhclient-script"
[   18.199822] type=1505 audit(1294970094.257:5):  operation="profile_replace" pid=494 name="/sbin/dhclient3"
[   18.211409] type=1505 audit(1294970094.269:6):  operation="profile_replace" pid=494 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.211844] type=1505 audit(1294970094.269:7):  operation="profile_replace" pid=494 name="/usr/lib/connman/scripts/dhclient-script"
[   18.380977] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0ef8, PCI irq 23
[   18.380985] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   18.380996] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   18.381001] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[   18.381285] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   18.381289] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x38000000 - 0x3bffffff
[   18.387037] ath5k 0000:02:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.387113] ath5k 0000:02:04.0: registered as 'phy0'
[   18.979654] [drm] radeon defaulting to kernel modesetting.
[   18.979661] [drm] radeon kernel modesetting enabled.
[   18.979752] radeon 0000:01:05.0: power state changed by ACPI to D0
[   18.979763] radeon 0000:01:05.0: power state changed by ACPI to D0
[   18.979777]   alloc irq_desc for 17 on node -1
[   18.979780]   alloc kstat_irqs on node -1
[   18.979789] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.000273] [drm] radeon: Initializing kernel modesetting.
[   19.002086] [drm] register mmio base: 0xC0100000
[   19.002090] [drm] register mmio size: 65536
[   19.002433] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   19.002452] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   19.002511] [drm] Generation 2 PCI interface, using max accessible memory
[   19.002515] [drm] radeon: VRAM 128M
[   19.002517] [drm] radeon: VRAM from 0x38000000 to 0x3FFFFFFF
[   19.002520] [drm] radeon: GTT 32M
[   19.002522] [drm] radeon: GTT from 0x40000000 to 0x41FFFFFF
[   19.002560] [drm] radeon: irq initialized.
[   19.002884] [drm] Detected VRAM RAM=128M, BAR=256M
[   19.002889] [drm] RAM width 128bits DDR
[   19.003017] [TTM] Zone  kernel: Available graphics memory: 444462 kiB.
[   19.003020] [TTM] Zone highmem: Available graphics memory: 447858 kiB.
[   19.003050] [drm] radeon: 128M of VRAM memory ready
[   19.003053] [drm] radeon: 32M of GTT memory ready.
[   19.003081] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   19.003880] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[   19.004055] [drm] radeon: cp idle (0x10000C03)
[   19.004478] [drm] Loading R300 Microcode
[   19.005022] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   19.009697] [drm] radeon: ring at 0x0000000040000000
[   19.009724] [drm] ring test succeeded in 1 usecs
[   19.009883] [drm] radeon: ib pool ready.
[   19.009960] [drm] ib test succeeded in 0 usecs
[   19.010018] [drm] Default TV standard: NTSC
[   19.010020] [drm] 14.318180000 MHz TV ref clk
[   19.010114] [drm] Panel ID String: LPL                     
[   19.010117] [drm] Panel Size 1280x800
[   19.010172] [drm] Default TV standard: NTSC
[   19.010174] [drm] 14.318180000 MHz TV ref clk
[   19.010207] [drm] Radeon Display Connectors
[   19.010209] [drm] Connector 0:
[   19.010211] [drm]   VGA
[   19.010214] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   19.010216] [drm]   Encoders:
[   19.010219] [drm]     CRT1: INTERNAL_DAC2
[   19.010221] [drm] Connector 1:
[   19.010222] [drm]   LVDS
[   19.010225] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   19.010227] [drm]   Encoders:
[   19.010229] [drm]     LCD1: INTERNAL_LVDS
[   19.010231] [drm] Connector 2:
[   19.010233] [drm]   S-video
[   19.010235] [drm]   Encoders:
[   19.010236] [drm]     TV1: INTERNAL_DAC2
[   19.142511] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   19.142521] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
[   19.177409] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   19.332596] type=1505 audit(1294970095.393:8):  operation="profile_load" pid=646 name="/usr/share/gdm/guest-session/Xsession"
[   19.345342] type=1505 audit(1294970095.405:9):  operation="profile_replace" pid=648 name="/sbin/dhclient3"
[   19.346109] type=1505 audit(1294970095.405:10):  operation="profile_replace" pid=648 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.359256] type=1505 audit(1294970095.417:11):  operation="profile_replace" pid=648 name="/usr/lib/connman/scripts/dhclient-script"
[   19.378034] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   19.380534] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   19.381567] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.382430] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.383351] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.465507] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   19.520309] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.613639] [drm] fb mappable at 0xD0040000
[   19.613643] [drm] vram apper at 0xD0000000
[   19.613645] [drm] size 4096000
[   19.613647] [drm] fb depth is 24
[   19.613649] [drm]    pitch is 5120
[   19.617760] fb0: radeondrmfb frame buffer device
[   19.617765] registered panic notifier
[   19.617775] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   19.625300] vga16fb: initializing
[   19.625306] vga16fb: mapped to 0xc00a0000
[   19.625313] vga16fb: not registering due to another framebuffer present
[   19.769528] hda_codec: ALC861: BIOS auto-probing.
[   19.770358] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   19.839554] Console: switching to colour frame buffer device 160x50
[   20.208002] ath: EEPROM regdomain: 0x64
[   20.208050] ath: EEPROM indicates we should expect a direct regpair map
[   20.208057] ath: Country alpha2 being used: 00
[   20.208059] ath: Regpair used: 0x64
[   20.237844] ppdev: user-space parallel port driver
[   20.248342] phy0: Selected rate control algorithm 'minstrel'
[   20.249313] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   21.122779] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.749303] wlan0: deauthenticating from 00:23:69:1b:2c:02 by local choice (reason=3)
[   28.749503] wlan0: direct probe to AP 00:23:69:1b:2c:02 (try 1)
[   28.753619] wlan0: direct probe responded
[   28.753626] wlan0: authenticate with AP 00:23:69:1b:2c:02 (try 1)
[   28.758338] wlan0: authenticated
[   28.758369] wlan0: associate with AP 00:23:69:1b:2c:02 (try 1)
[   28.760368] wlan0: RX AssocResp from 00:23:69:1b:2c:02 (capab=0x411 status=0 aid=1)
[   28.760375] wlan0: associated
[   28.761212] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.276036] eth0: no IPv6 routers present
[   39.044028] wlan0: no IPv6 routers present
[  390.211912] ACPI Error: No installed handler for fixed event [00000000] (20090903/evevent-306)
[ 1014.790644] ACPI Error: No installed handler for fixed event [00000000] (20090903/evevent-306)
[ 1355.767055] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1355.767061] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1355.767064] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 2235.500049] No probe response from AP 00:23:69:1b:2c:02 after 500ms, disconnecting.
[ 2240.000049] ------------[ cut here ]------------
[ 2240.000066] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
[ 2240.000070] Hardware name: Satellite A105
[ 2240.000073] NETDEV WATCHDOG: eth0 (8139too): transmit queue 0 timed out
[ 2240.000075] Modules linked in: binfmt_misc ppdev arc4 snd_hda_codec_realtek snd_hda_codec_si3054 fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy joydev snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq pcmcia snd_timer snd_seq_device radeon ttm ath5k snd drm_kms_helper mac80211 ath yenta_socket drm i2c_algo_bit rsrc_nonstatic cfg80211 ati_agp soundcore video psmouse serio_raw led_class pcmcia_core i2c_piix4 output snd_page_alloc agpgart shpchp lp parport 8139too 8139cp mii sata_sil pata_atiixp
[ 2240.000136] Pid: 0, comm: swapper Not tainted 2.6.32-27-generic #49-Ubuntu
[ 2240.000139] Call Trace:
[ 2240.000147]  [<c014c802>] warn_slowpath_common+0x72/0xa0
[ 2240.000152]  [<c04da1ee>] ? dev_watchdog+0x1fe/0x210
[ 2240.000156]  [<c04da1ee>] ? dev_watchdog+0x1fe/0x210
[ 2240.000160]  [<c014c87b>] warn_slowpath_fmt+0x2b/0x30
[ 2240.000164]  [<c04da1ee>] dev_watchdog+0x1fe/0x210
[ 2240.000171]  [<c0163d70>] ? insert_work+0x60/0xb0
[ 2240.000178]  [<c012a688>] ? default_spin_lock_flags+0x8/0x10
[ 2240.000184]  [<c058d9bf>] ? _spin_lock_irqsave+0x2f/0x50
[ 2240.000188]  [<c0164036>] ? __queue_work+0x36/0x50
[ 2240.000193]  [<c015ba1e>] run_timer_softirq+0x13e/0x2c0
[ 2240.000199]  [<c01764bc>] ? tick_handle_oneshot_broadcast+0x12c/0x140
[ 2240.000204]  [<c04d9ff0>] ? dev_watchdog+0x0/0x210
[ 2240.000208]  [<c0153448>] __do_softirq+0x98/0x1b0
[ 2240.000216]  [<c01a0054>] ? handle_IRQ_event+0x54/0x150
[ 2240.000220]  [<c01a32e9>] ? move_native_irq+0x19/0x50
[ 2240.000224]  [<c01535a5>] do_softirq+0x45/0x50
[ 2240.000228]  [<c01536f5>] irq_exit+0x65/0x70
[ 2240.000233]  [<c0591e35>] do_IRQ+0x55/0xc0
[ 2240.000237]  [<c016d935>] ? sched_clock_local+0xa5/0x180
[ 2240.000242]  [<c0103a30>] common_interrupt+0x30/0x40
[ 2240.000247]  [<c016007b>] ? k_getrusage+0x3b/0x2f0
[ 2240.000253]  [<c039e714>] ? acpi_idle_enter_simple+0x117/0x148
[ 2240.000257]  [<c039e42a>] acpi_idle_enter_bm+0xd1/0x2a4
[ 2240.000263]  [<c04a254a>] cpuidle_idle_call+0x7a/0x100
[ 2240.000267]  [<c01021d4>] cpu_idle+0x94/0xd0
[ 2240.000273]  [<c057b248>] rest_init+0x58/0x60
[ 2240.000280]  [<c07a58ec>] start_kernel+0x351/0x357
[ 2240.000285]  [<c07a53c7>] ? unknown_bootoption+0x0/0x19e
[ 2240.000290]  [<c07a50aa>] i386_start_kernel+0xaa/0xb1
[ 2240.000293] ---[ end trace a12b427b5053b0da ]---
[ 2243.000102] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 2255.000098] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

---

### Post by dead4red on 2011-01-14
Here is the "dmesg | tail -n 30 > ~/Desktop/output.txt" output. I was
running Transmission seeding two torrents and downloading two. Speeds
were about 100KB/s down and 200KB/s up which is nowhere near the
~1.5MB/s down and 300KB/s up I normally run.

[  175.816133]  [<c04da1ee>] ? dev_watchdog+0x1fe/0x210
[  175.816137]  [<c04da1ee>] ? dev_watchdog+0x1fe/0x210
[  175.816141]  [<c014c87b>] warn_slowpath_fmt+0x2b/0x30
[  175.816146]  [<c04da1ee>] dev_watchdog+0x1fe/0x210
[  175.816153]  [<c0163d70>] ? insert_work+0x60/0xb0
[  175.816159]  [<c012a688>] ? default_spin_lock_flags+0x8/0x10
[  175.816165]  [<c058d9bf>] ? _spin_lock_irqsave+0x2f/0x50
[  175.816170]  [<c0164036>] ? __queue_work+0x36/0x50
[  175.816174]  [<c015ba1e>] run_timer_softirq+0x13e/0x2c0
[  175.816179]  [<c0103a30>] ? common_interrupt+0x30/0x40
[  175.816184]  [<c04d9ff0>] ? dev_watchdog+0x0/0x210
[  175.816188]  [<c0153448>] __do_softirq+0x98/0x1b0
[  175.816193]  [<c01535a5>] do_softirq+0x45/0x50
[  175.816196]  [<c01536f5>] irq_exit+0x65/0x70
[  175.816201]  [<c0591efc>] smp_apic_timer_interrupt+0x5c/0x8b
[  175.816206]  [<c0590173>] ? notifier_call_chain+0x43/0x60
[  175.816210]  [<c0103df1>] apic_timer_interrupt+0x31/0x40
[  175.816215]  [<c01700e0>] ? profile_setup+0xa0/0x1f0
[  175.816220]  [<c0129a7a>] ? native_safe_halt+0xa/0x10
[  175.816226]  [<c039e28b>] acpi_idle_do_entry+0x37/0x58
[  175.816230]  [<c039e311>] acpi_idle_enter_c1+0x65/0xad
[  175.816235]  [<c04a254a>] cpuidle_idle_call+0x7a/0x100
[  175.816239]  [<c01021d4>] cpu_idle+0x94/0xd0
[  175.816246]  [<c057b248>] rest_init+0x58/0x60
[  175.816253]  [<c07a58ec>] start_kernel+0x351/0x357
[  175.816258]  [<c07a53c7>] ? unknown_bootoption+0x0/0x19e
[  175.816262]  [<c07a50aa>] i386_start_kernel+0xaa/0xb1
[  175.816266] ---[ end trace 006d7b965fd9911c ]---
[  178.818022] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  190.816401] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

---

### Post by killament on 2013-03-18
Hey dead4red - were you ever able to solve this issue?
I have the exact same machine and have installed Xubuntu 12.10 and am  having the exact same problem as you - network connection for wired lan  keeps going down randomly during heavy transfers.
I scoured the net and tried updating the BIOS, the noapci and noacpi boot options, but those didn't work.

Any suggestions? Or did you not get it fixed?

Thanks!

---

### Post by mörgæs on 2013-03-18
The thread two years old, and much could have changed since then.
Closing the thread, but feel free to create a new one. Please remember to begin with a complete hardware description.

---

