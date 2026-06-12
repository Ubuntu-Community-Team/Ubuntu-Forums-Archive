---
title: "kernel 2.6.31-16-generic, ralink 3071 speed veryyy slow"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by _mikec_ on 2009-12-14
Speeds with my Ralink 3071 usb adapters are poor to none, i have updated the system and now the speeds are so slow i cannot watch youtube videos normally anymore, it's like if i was on a 56Kbps modem!. even surfing the web is poor. I have also noticed that my computer got very slow in loading applications. I didn't had problems before with Ubuntu Karmic 9.10. I am currently using Xubuntu Karmic 9.10. main problem is the internet wireless connection... I am dual booting this pc with windows xp and speeds within windows xp are normal and what i expect which is high speed internet, no problem on windows xp all updates applied.

some system information.

lsusb:
**Bus 001 Device 002: ID 07b8:3071 D-Link Corp. **
I am not sure why it says D-Link Corp though, since it's supposed to be a Ralink chipset. When i blacklist rt2800usb i get a wireless connection, but why should i use rt2800 when my chipset is rt3071 ??

ifconfig:
> ra0       Link encap:Ethernet  HWaddr 00:12:0e:b3:b9:89  
          inet addr:xxxxxxxxxxxx  Bcast:xxxxxxxxxxxxx Mask:xxxxxxxxxxxx
          inet6 addr: xxxxxxxxxxxx /64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5549826 (5.5 MB)  TX bytes:780757 (780.7 KB)iwconfig:
> ra0       RT2870 Wireless  ESSID:"XXXXXXX"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: xxxxxxxxxxxx   
          Bit Rate=36 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-76 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0lsmod:
> cbc                     3516  141 
aes_i586                8124  142 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
binfmt_misc             8356  1 
dm_crypt               12928  0 
snd_intel8x0           30168  4 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  3 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_rawmidi            22208  1 snd_seq_midi
ppdev                   6688  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
nvidia               4704212  22 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_nforce2             6784  0 
parport_pc             31940  1 
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
shpchp                 32272  0 
soundcore               7264  3 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
**rt2870sta             488820  1 **
reiserfs              229288  1 
usbhid                 38208  0 
floppy                 54916  0 
forcedeth              54152  0 
nvidia_agp              6200  1 
agpgart                34988  2 nvidia,nvidia_agp

dmesg:
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
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
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-AFFFF uncachable
[    0.000000]   B0000-BFFFF write-combining
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 0E0000000 mask FFE000000 write-combining
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  modified: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  modified: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000001fff0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 001fc00000 page 2M
[    0.000000]  001fc00000 - 001fff0000 page 4k
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 10000-15000
[    0.000000] RAMDISK: 1789b000 - 18033768
[    0.000000] ACPI: RSDP 000f7ba0 00014 (v00 FIC   )
[    0.000000] ACPI: RSDT 1fff3000 0002C (v01 FIC    AU31     42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 1fff3040 00074 (v01 FIC    AU31     42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 1fff30c0 03C88 (v01 FIC    AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 1fff0000 00040
[    0.000000] ACPI: APIC 1fff6d80 0006E (v01 FIC    AU31     42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 0 - 1fff0000
[    0.000000]   node 0 low ram: 00000000 - 1fff0000
[    0.000000]   node 0 bootmap 00011000 - 00015000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [001789b000 - 0018033768]          RAMDISK ==> [001789b000 - 0018033768]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008a9000 - 00008ac118]              BRK ==> [00008a9000 - 00008ac118]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000015000]          BOOTMAP ==> [0000011000 - 0000015000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130943
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125968 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1402000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129919
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=167d49b7-a2ea-4b17-9e60-83ec6e89f432 ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2620800 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 500720k/524224k available (4566k kernel code, 22780k reserved, 2142k data, 540k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xe07f0000 - 0xff7fe000   ( 496 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2171.655 MHz processor.
[    0.001810] Console: colour VGA+ 80x25
[    0.001814] console [tty0] enabled
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4343.31 BogoMIPS (lpj=8686620)
[    0.004034] Security Framework initialized
[    0.004064] AppArmor: AppArmor initialized
[    0.004072] Mount-cache hash table entries: 512
[    0.004222] Initializing cgroup subsys ns
[    0.004227] Initializing cgroup subsys cpuacct
[    0.004231] Initializing cgroup subsys memory
[    0.004241] Initializing cgroup subsys freezer
[    0.004244] Initializing cgroup subsys net_cls
[    0.004258] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004261] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004265] mce: CPU supports 4 MCE banks
[    0.004283] Performance Counters: AMD PMU driver.
[    0.004295] ... version:                 0
[    0.004297] ... bit width:               48
[    0.004299] ... generic counters:        4
[    0.004301] ... value mask:              0000ffffffffffff
[    0.004303] ... max period:              00007fffffffffff
[    0.004305] ... fixed-purpose counters:  0
[    0.004307] ... counter mask:            000000000000000f
[    0.004312] Checking 'hlt' instruction... OK.
[    0.020487] SMP alternatives: switching to UP code
[    0.025722] Freeing SMP alternatives: 19k freed
[    0.025745] ACPI: Core revision 20090521
[    0.036432] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.076119] CPU0: AMD Athlon(tm) XP 3000+ stepping 00
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (4343.31 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] Booting paravirtualized kernel on bare hardware
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 11:18:20  Date: 12/15/09
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.108951] PCI: PCI BIOS revision 2.10 entry at 0xfbcd0, last bus=2
[    0.108954] PCI: Using configuration type 1 for base access
[    0.109953] bio: create slab <bio-0> at 0
[    0.110700] ACPI: EC: Look up EC in DSDT
[    0.115345] ACPI: Interpreter enabled
[    0.115352] ACPI: (supports S0 S3 S4 S5)
[    0.115374] ACPI: Using IOAPIC for interrupt routing
[    0.121073] ACPI: No dock devices found.
[    0.121181] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.121233] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe1ffffff]
[    0.121250] pci 0000:00:00.0: nForce2 C1 Halt Disconnect fixup
[    0.121452] pci 0000:00:01.1: reg 10 io port: [0xe400-0xe41f]
[    0.121488] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.121492] pci 0000:00:01.1: PME# disabled
[    0.121524] pci 0000:00:02.0: reg 10 32bit mmio: [0xe5080000-0xe5080fff]
[    0.121559] pci 0000:00:02.0: supports D1 D2
[    0.121561] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.121565] pci 0000:00:02.0: PME# disabled
[    0.121592] pci 0000:00:02.1: reg 10 32bit mmio: [0xe5083000-0xe5083fff]
[    0.121626] pci 0000:00:02.1: supports D1 D2
[    0.121629] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.121633] pci 0000:00:02.1: PME# disabled
[    0.121665] pci 0000:00:02.2: reg 10 32bit mmio: [0xe5086000-0xe50860ff]
[    0.121706] pci 0000:00:02.2: supports D1 D2
[    0.121708] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.121713] pci 0000:00:02.2: PME# disabled
[    0.121746] pci 0000:00:04.0: reg 10 32bit mmio: [0xe5087000-0xe5087fff]
[    0.121753] pci 0000:00:04.0: reg 14 io port: [0xd000-0xd007]
[    0.121784] pci 0000:00:04.0: supports D1 D2
[    0.121786] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.121790] pci 0000:00:04.0: PME# disabled
[    0.121817] pci 0000:00:05.0: reg 10 32bit mmio: [0xe5000000-0xe507ffff]
[    0.121851] pci 0000:00:05.0: supports D1 D2
[    0.121877] pci 0000:00:06.0: reg 10 io port: [0xd400-0xd4ff]
[    0.121884] pci 0000:00:06.0: reg 14 io port: [0xd800-0xd87f]
[    0.121890] pci 0000:00:06.0: reg 18 32bit mmio: [0xe5081000-0xe5081fff]
[    0.121918] pci 0000:00:06.0: supports D1 D2
[    0.121982] pci 0000:00:09.0: reg 20 io port: [0xf000-0xf00f]
[    0.122089] pci 0000:01:08.0: reg 10 32bit mmio: [0xe4000000-0xe400ffff]
[    0.122097] pci 0000:01:08.0: reg 14 io port: [0xc000-0xc007]
[    0.122140] pci 0000:01:08.0: PME# supported from D3hot D3cold
[    0.122145] pci 0000:01:08.0: PME# disabled
[    0.122184] pci 0000:00:08.0: bridge io port: [0xc000-0xcfff]
[    0.122188] pci 0000:00:08.0: bridge 32bit mmio: [0xe4000000-0xe4ffffff]
[    0.122223] pci 0000:02:00.0: reg 10 32bit mmio: [0xe2000000-0xe2ffffff]
[    0.122230] pci 0000:02:00.0: reg 14 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.122237] pci 0000:02:00.0: reg 18 32bit mmio: [0xd8000000-0xd807ffff]
[    0.122253] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.122306] pci 0000:00:1e.0: bridge 32bit mmio: [0xe2000000-0xe3ffffff]
[    0.122310] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.122321] pci_bus 0000:00: on NUMA node 0
[    0.122326] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.122457] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.122569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.159731] ACPI: Invalid _PRS IRQ 0
[    0.159815] ACPI: PCI Interrupt Link [LNK1] (IRQs *0 20)
[    0.159900] ACPI: Invalid _PRS IRQ 0
[    0.159982] ACPI: PCI Interrupt Link [LNK2] (IRQs *0 20), disabled.
[    0.160075] ACPI: Invalid _PRS IRQ 0
[    0.160156] ACPI: PCI Interrupt Link [LNK3] (IRQs *0 20), disabled.
[    0.160240] ACPI: Invalid _PRS IRQ 0
[    0.160320] ACPI: PCI Interrupt Link [LNK4] (IRQs *0 20)
[    0.160403] ACPI: Invalid _PRS IRQ 0
[    0.160483] ACPI: PCI Interrupt Link [LNK5] (IRQs *0 20), disabled.
[    0.160567] ACPI: Invalid _PRS IRQ 0
[    0.160647] ACPI: PCI Interrupt Link [LUBA] (IRQs *0 20)
[    0.160729] ACPI: Invalid _PRS IRQ 0
[    0.160809] ACPI: PCI Interrupt Link [LUBB] (IRQs *0 20)
[    0.160892] ACPI: Invalid _PRS IRQ 0
[    0.160972] ACPI: PCI Interrupt Link [LMAC] (IRQs *0 20)
[    0.161058] ACPI: Invalid _PRS IRQ 0
[    0.161139] ACPI: PCI Interrupt Link [LAPU] (IRQs *0 20)
[    0.161225] ACPI: Invalid _PRS IRQ 0
[    0.161305] ACPI: PCI Interrupt Link [LACI] (IRQs *0 20)
[    0.161391] ACPI: Invalid _PRS IRQ 0
[    0.161471] ACPI: PCI Interrupt Link [LSMB] (IRQs *0 20), disabled.
[    0.161555] ACPI: Invalid _PRS IRQ 0
[    0.161635] ACPI: PCI Interrupt Link [LUB2] (IRQs *0 20)
[    0.161721] ACPI: Invalid _PRS IRQ 0
[    0.161801] ACPI: PCI Interrupt Link [LFIR] (IRQs *0 20), disabled.
[    0.161885] ACPI: Invalid _PRS IRQ 0
[    0.161965] ACPI: PCI Interrupt Link [LIDE] (IRQs *0 20), disabled.
[    0.162068] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
[    0.162160] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[    0.162252] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[    0.162343] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[    0.162434] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.162572] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.162711] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[    0.162848] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.162986] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0
[    0.163123] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[    0.163217] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[    0.163353] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.163490] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    0.163634] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.163854] SCSI subsystem initialized
[    0.163933] libata version 3.00 loaded.
[    0.164047] usbcore: registered new interface driver usbfs
[    0.164066] usbcore: registered new interface driver hub
[    0.164098] usbcore: registered new device driver usb
[    0.164241] ACPI: WMI: Mapper loaded
[    0.164244] PCI: Using ACPI for IRQ routing
[    0.164399] Bluetooth: Core ver 2.15
[    0.164433] NET: Registered protocol family 31
[    0.164435] Bluetooth: HCI device and connection manager initialized
[    0.164439] Bluetooth: HCI socket layer initialized
[    0.164441] NetLabel: Initializing
[    0.164443] NetLabel:  domain hash size = 128
[    0.164445] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.164462] NetLabel:  unlabeled traffic allowed by default
[    0.166862] pnp: PnP ACPI init
[    0.166888] ACPI: bus type pnp registered
[    0.170512] pnp: PnP ACPI: found 13 devices
[    0.170515] ACPI: ACPI bus type pnp unregistered
[    0.170520] PnPBIOS: Disabled by ACPI PNP
[    0.170533] system 00:00: ioport range 0x4000-0x407f has been reserved
[    0.170537] system 00:00: ioport range 0x4080-0x40ff has been reserved
[    0.170540] system 00:00: ioport range 0x4400-0x447f has been reserved
[    0.170543] system 00:00: ioport range 0x4480-0x44ff has been reserved
[    0.170547] system 00:00: ioport range 0x4200-0x427f has been reserved
[    0.170550] system 00:00: ioport range 0x4280-0x42ff has been reserved
[    0.170556] system 00:01: ioport range 0x5000-0x503f has been reserved
[    0.170559] system 00:01: ioport range 0x5100-0x513f has been reserved
[    0.170566] system 00:02: iomem range 0xf0000-0xf3fff could not be reserved
[    0.170570] system 00:02: iomem range 0xf4000-0xf7fff could not be reserved
[    0.170573] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[    0.170576] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[    0.170580] system 00:02: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    0.170584] system 00:02: iomem range 0xffff0000-0xffffffff has been reserved
[    0.170587] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    0.170590] system 00:02: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.170594] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.170597] system 00:02: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.170604] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.170607] system 00:04: ioport range 0x800-0x805 has been reserved
[    0.205314] AppArmor: AppArmor Filesystem Enabled
[    0.205337] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.205341] pci 0000:00:08.0:   IO window: 0xc000-0xcfff
[    0.205347] pci 0000:00:08.0:   MEM window: 0xe4000000-0xe4ffffff
[    0.205352] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.205360] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.205362] pci 0000:00:1e.0:   IO window: disabled
[    0.205367] pci 0000:00:1e.0:   MEM window: 0xe2000000-0xe3ffffff
[    0.205372] pci 0000:00:1e.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.205384] pci 0000:00:08.0: setting latency timer to 64
[    0.205394] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.205397] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.205400] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.205403] pci_bus 0000:01: resource 1 mem: [0xe4000000-0xe4ffffff]
[    0.205406] pci_bus 0000:02: resource 1 mem: [0xe2000000-0xe3ffffff]
[    0.205409] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.205451] NET: Registered protocol family 2
[    0.205554] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.205865] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.206049] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.206223] TCP: Hash tables configured (established 16384 bind 16384)
[    0.206226] TCP reno registered
[    0.206298] NET: Registered protocol family 1
[    0.206371] Trying to unpack rootfs image as initramfs...
[    0.425521] Freeing initrd memory: 7777k freed
[    0.434709] cpufreq-nforce2: Detected nForce2 chipset revision A2
[    0.434712] cpufreq-nforce2: FSB changing is maybe unstable and can lead to crashes and data loss.
[    0.434726] cpufreq-nforce2: FSB currently at 166 MHz, FID 13.0
[    0.434749] Marking TSC unstable due to cpufreq changes
[    0.435614] Scanning for low memory corruption every 60 seconds
[    0.435746] audit: initializing netlink socket (disabled)
[    0.435767] type=2000 audit(1260875900.432:1): initialized
[    0.436025] Switched to high resolution mode on CPU 0
[    0.444276] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.445867] VFS: Disk quotas dquot_6.5.2
[    0.445926] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.446517] fuse init (API version 7.12)
[    0.446604] msgmni has been set to 993
[    0.446830] alg: No test for stdrng (krng)
[    0.446845] io scheduler noop registered
[    0.446848] io scheduler anticipatory registered
[    0.446850] io scheduler deadline registered
[    0.446894] io scheduler cfq registered (default)
[    0.500061] pci 0000:02:00.0: Boot video device
[    0.500171] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.500196] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.500345] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.500351] ACPI: Power Button [PWRF]
[    0.500410] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.500414] ACPI: Power Button [PWRB]
[    0.500801] processor LNXCPU:00: registered as cooling_device0
[    0.503523] isapnp: Scanning for PnP cards...
[    0.858994] isapnp: No Plug & Play device found
[    0.860244] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.860367] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.860684] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.861759] brd: module loaded
[    0.862250] loop: module loaded
[    0.862331] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.862608] pata_amd 0000:00:09.0: version 0.4.1
[    0.862677] pata_amd 0000:00:09.0: setting latency timer to 64
[    0.862791] scsi0 : pata_amd
[    0.862906] scsi1 : pata_amd
[    0.863769] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.863773] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.864512] Fixed MDIO Bus: probed
[    0.864551] PPP generic driver version 2.4.2
[    0.864653] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.864903] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.864909]   alloc irq_desc for 22 on node -1
[    0.864912]   alloc kstat_irqs on node -1
[    0.864920] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
[    0.864940] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    0.864944] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    0.865013] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    0.865051] ehci_hcd 0000:00:02.2: debug port 1
[    0.865057] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    0.865075] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe5086000
[    0.876023] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    0.876127] usb usb1: configuration #1 chosen from 1 choice
[    0.876166] hub 1-0:1.0: USB hub found
[    0.876178] hub 1-0:1.0: 6 ports detected
[    0.876240] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.876489] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    0.876493]   alloc irq_desc for 21 on node -1
[    0.876495]   alloc kstat_irqs on node -1
[    0.876500] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
[    0.876511] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.876514] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.876549] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.876574] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe5080000
[    0.934066] usb usb2: configuration #1 chosen from 1 choice
[    0.934094] hub 2-0:1.0: USB hub found
[    0.934105] hub 2-0:1.0: 3 ports detected
[    0.934365] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[    0.934368]   alloc irq_desc for 20 on node -1
[    0.934371]   alloc kstat_irqs on node -1
[    0.934376] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
[    0.934385] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    0.934388] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    0.934427] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    0.934461] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe5083000
[    0.990067] usb usb3: configuration #1 chosen from 1 choice
[    0.990094] hub 3-0:1.0: USB hub found
[    0.990105] hub 3-0:1.0: 3 ports detected
[    0.990157] uhci_hcd: USB Universal Host Controller Interface driver
[    0.990251] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.990254] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.991007] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.991074] mice: PS/2 mouse device common for all mice
[    0.991164] rtc_cmos 00:06: RTC can wake from S4
[    0.991205] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.991230] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.991309] device-mapper: uevent: version 1.0.3
[    0.991410] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.991507] device-mapper: multipath: version 1.1.0 loaded
[    0.991510] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.991635] EISA: Probing bus 0 at eisa.0
[    0.991656] Cannot allocate resource for EISA slot 4
[    0.991658] Cannot allocate resource for EISA slot 5
[    0.991673] EISA: Detected 0 cards.
[    0.991749] cpuidle: using governor ladder
[    0.991751] cpuidle: using governor menu
[    0.992310] TCP cubic registered
[    0.992463] NET: Registered protocol family 10
[    0.992928] lo: Disabled Privacy Extensions
[    0.993255] NET: Registered protocol family 17
[    0.993280] Bluetooth: L2CAP ver 2.13
[    0.993282] Bluetooth: L2CAP socket layer initialized
[    0.993286] Bluetooth: SCO (Voice Link) ver 0.6
[    0.993288] Bluetooth: SCO socket layer initialized
[    0.993322] Bluetooth: RFCOMM TTY layer initialized
[    0.993325] Bluetooth: RFCOMM socket layer initialized
[    0.993328] Bluetooth: RFCOMM ver 1.11
[    0.993342] powernow-k8: Processor cpuid 6a0 not supported
[    0.993361] Using IPI No-Shortcut mode
[    0.993427] PM: Resume from disk failed.
[    0.993443] registered taskstats version 1
[    0.993563]   Magic number: 5:600:327
[    0.993670] rtc_cmos 00:06: setting system clock to 2009-12-15 11:18:21 UTC (1260875901)
[    0.993674] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.993676] EDD information not available.
[    1.015087] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.029925] ata1.00: ATA-7: Maxtor 6L160P0, BAH41BM0, max UDMA/133
[    1.029929] ata1.00: 320173056 sectors, multi 16: LBA48 
[    1.029954] ata1: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc700c0c0) ACPI=0x7f01f (15:600:0x13)
[    1.045872] ata1.00: configured for UDMA/133
[    1.046017] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L160P0   BAH4 PQ: 0 ANSI: 5
[    1.046145] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.046193] sd 0:0:0:0: [sda] 320173056 512-byte logical blocks: (163 GB/152 GiB)
[    1.046252] sd 0:0:0:0: [sda] Write Protect is off
[    1.046255] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.046286] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.046446]  sda: sda1 sda2 < sda5 sda6 >
[    1.123176] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.188021] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.337355] usb 1-1: configuration #1 chosen from 1 choice
[    1.384344] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-H552B, GA04, max UDMA/33
[    1.384374] ata2.01: ATAPI: LITE-ON LTR-52246S, 6S02, max UDMA/33
[    1.384396] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc700c0c0) ACPI=0x701f (60:60:0x1f)
[    1.384402] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc700c0c0) ACPI=0x701f (60:60:0x1f)
[    1.400273] ata2.00: configured for UDMA/33
[    1.416274] ata2.01: configured for UDMA/33
[    1.425414] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552B GA04 PQ: 0 ANSI: 5
[    1.428601] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[    1.428605] Uniform CD-ROM driver Revision: 3.20
[    1.428689] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.428731] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.433454] scsi 1:0:1:0: CD-ROM            LITE-ON  LTR-52246S       6S02 PQ: 0 ANSI: 5
[    1.482276] sr1: scsi3-mmc drive: 113x/52x writer cd/rw xa/form2 cdda tray
[    1.482349] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.482388] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.482416] Freeing unused kernel memory: 540k freed
[    1.483050] Write protecting the kernel text: 4568k
[    1.483083] Write protecting the kernel read-only data: 1836k
[    1.676389] Linux agpgart interface v0.103
[    1.678891] agpgart: Detected NVIDIA nForce2 chipset
[    1.688296] Floppy drive(s): fd0 is 1.44M
[    1.692066] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    1.704616] agpgart-nvidia 0000:00:00.0: AGP aperture is 32M @ 0xe0000000
[    1.704820] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.705122] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    1.705130] forcedeth 0000:00:04.0: PCI INT A -> Link[APCH] -> GSI 22 (level, high) -> IRQ 22
[    1.705136] forcedeth 0000:00:04.0: setting latency timer to 64
[    1.705187] nv_probe: set workaround bit for reversed mac addr
[    1.709259] FDC 0 is a post-1991 82077
[    1.907072] usb 2-2: configuration #1 chosen from 1 choice
[    1.917265] usbcore: registered new interface driver hiddev
[    1.924369] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input4
[    1.924473] generic-usb 0003:046D:C01E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-2/input0
[    1.924496] usbcore: registered new interface driver usbhid
[    1.924500] usbhid: v2.6:USB HID core driver
[    2.225034] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:40:ca:81:a3:e5
[    2.225041] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[    2.972561] PM: Starting manual resume from disk
[    2.972567] PM: Resume from partition 8:6
[    2.972569] PM: Checking hibernation image.
[    2.984018] PM: Resume from disk failed.
[    3.012031] REISERFS (device sda5): found reiserfs format "3.6" with standard journal
[    3.012045] REISERFS (device sda5): using ordered data mode
[    3.041875] REISERFS (device sda5): journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    3.042744] REISERFS (device sda5): checking transaction log (sda5)
[    3.101702] REISERFS (device sda5): Using r5 hash to sort names
[    3.676874] type=1505 audit(1260875904.182:2): operation="profile_load" pid=386 name=/sbin/dhclient3
[    3.677183] type=1505 audit(1260875904.182:3): operation="profile_load" pid=386 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.677359] type=1505 audit(1260875904.182:4): operation="profile_load" pid=386 name=/usr/lib/connman/scripts/dhclient-script
[    3.734145] type=1505 audit(1260875904.238:5): operation="profile_load" pid=387 name=/usr/bin/evince
[    3.739909] type=1505 audit(1260875904.242:6): operation="profile_load" pid=387 name=/usr/bin/evince-previewer
[    3.743313] type=1505 audit(1260875904.246:7): operation="profile_load" pid=387 name=/usr/bin/evince-thumbnailer
[    3.807025] type=1505 audit(1260875904.310:8): operation="profile_load" pid=389 name=/usr/lib/cups/backend/cups-pdf
[    3.807417] type=1505 audit(1260875904.310:9): operation="profile_load" pid=389 name=/usr/sbin/cupsd
[    3.809961] type=1505 audit(1260875904.314:10): operation="profile_load" pid=390 name=/usr/sbin/tcpdump
[    7.841114] Adding 1855468k swap on /dev/sda6.  Priority:-1 extents:1 across:1855468k 
[    8.462638] udev: starting version 147
[    9.392830] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.399246] rtusb init --->
[    9.399841] 
[    9.399842] 
[    9.399843] === pAd = e0d6a000, size = 566744 ===
[    9.399844] 
[    9.399846] <-- RTMPAllocAdapterBlock, Status=0
[    9.400706] usbcore: registered new interface driver rt2870
[    9.468431] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[    9.474865] rtusb init --->
[    9.474874] Error: Driver 'rt2870' is already registered, aborting...
[    9.474880] usbcore: error -17 registering interface     driver rt2870
[    9.728259] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.964767] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    9.964790] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   11.326295] nvidia: module license 'NVIDIA' taints kernel.
[   11.326302] Disabling lock debugging due to kernel taint
[   11.589151] parport_pc 00:0b: reported by Plug and Play ACPI
[   11.589242] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   11.607087] lp: driver loaded but no devices found
[   11.608215] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   11.608222]   alloc irq_desc for 19 on node -1
[   11.608225]   alloc kstat_irqs on node -1
[   11.608234] nvidia 0000:02:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, high) -> IRQ 19
[   11.608688] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   11.676214] lp0: using parport0 (interrupt-driven).
[   11.795635] ppdev: user-space parallel port driver
[   12.037894] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.739862] type=1505 audit(1260893913.242:11): operation="profile_replace" pid=814 name=/sbin/dhclient3
[   12.740274] type=1505 audit(1260893913.246:12): operation="profile_replace" pid=814 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.740451] type=1505 audit(1260893913.246:13): operation="profile_replace" pid=814 name=/usr/lib/connman/scripts/dhclient-script
[   12.748486] type=1505 audit(1260893913.254:14): operation="profile_replace" pid=815 name=/usr/bin/evince
[   12.754510] type=1505 audit(1260893913.258:15): operation="profile_replace" pid=815 name=/usr/bin/evince-previewer
[   12.758001] type=1505 audit(1260893913.262:16): operation="profile_replace" pid=815 name=/usr/bin/evince-thumbnailer
[   12.774191] type=1505 audit(1260893913.278:17): operation="profile_replace" pid=819 name=/usr/lib/cups/backend/cups-pdf
[   12.774587] type=1505 audit(1260893913.278:18): operation="profile_replace" pid=819 name=/usr/sbin/cupsd
[   12.776991] type=1505 audit(1260893913.282:19): operation="profile_replace" pid=820 name=/usr/sbin/tcpdump
[   13.403322] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[   13.403331] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 21 (level, high) -> IRQ 21
[   13.403378] Intel ICH 0000:00:06.0: setting latency timer to 64
[   13.724034] intel8x0_measure_ac97_clock: measured 52785 usecs (2560 samples)
[   13.724039] intel8x0: clocking to 48000
[   13.949897] <-- RTMPAllocTxRxRingMemory, Status=0
[   13.951693] -->RTUSBVenderReset
[   13.951819] <--RTUSBVenderReset
[   14.387789] --> Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[   14.387794] 1. Phy Mode = 0
[   14.387796] 2. Phy Mode = 0
[   14.481387] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   14.496138] 3. Phy Mode = 0
[   14.502637] MCS Set = 00 00 00 00 00
[   14.996984] RTUSBFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== RTMPInitialize, Status=0
[   15.010195] 0x1300 = 00073200
[   19.237850] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
[   19.237866] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode
[   19.237924] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode
[   22.228808] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 590
[   22.294017] DRS: unkown mode,default use 11N 1S AP 
[   22.294026] DRS: unkown mode (SupRateLen=0, ExtRateLen=0, MCSSet[0]=0x0, MCSSet[1]=0x0)
[   25.440019] ra0: no IPv6 routers present
[   25.680017] eth0: no IPv6 routers present
[   39.346373] padlock: VIA PadLock not detected.
[   42.505760] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 590
[   62.332539] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 590
[   62.332810] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[   62.382805] DRS: unkown mode,default use 11N 1S AP 
[   62.382813] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[   69.480092] #
[   77.393276] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 475
[   80.056988] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[   80.815649] DRS: unkown mode,default use 11N 1S AP 
[   80.815657] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[   81.863132] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 590
[  114.682151] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 590
[  114.760318] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
[  115.019543] ERROR!!! ASSOC - Can't find BSS after receiving Assoc response
[  115.019554] DRS: unkown mode,default use 11N 1S AP 
[  115.019557] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  126.354087] BulkOutDataPacket failed: ReasonCode=-2!
[  126.354092]     >>BulkOut Req=0x1b5, Complete=0x1b4, Other=0x1
[  126.354095]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  129.698069] BulkOutDataPacket failed: ReasonCode=-2!
[  129.698074]     >>BulkOut Req=0x1b6, Complete=0x1b5, Other=0x2
[  129.698077]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  131.834198] BulkOutDataPacket failed: ReasonCode=-2!
[  131.834256]     >>BulkOut Req=0x1b6, Complete=0x1b5, Other=0x3
[  131.834259]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  133.967075] BulkOutDataPacket failed: ReasonCode=-2!
[  133.967080]     >>BulkOut Req=0x1b6, Complete=0x1b5, Other=0x4
[  133.967083]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  136.122074] BulkOutDataPacket failed: ReasonCode=-2!
[  136.122078]     >>BulkOut Req=0x1b6, Complete=0x1b5, Other=0x5
[  136.122082]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  138.334064] BulkOutDataPacket failed: ReasonCode=-2!
[  138.334069]     >>BulkOut Req=0x1b6, Complete=0x1b5, Other=0x6
[  138.334073]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  140.470068] BulkOutDataPacket failed: ReasonCode=-2!
[  140.470072]     >>BulkOut Req=0x1b6, Complete=0x1b5, Other=0x7
[  140.470076]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  142.626068] BulkOutDataPacket failed: ReasonCode=-2!
[  142.626073]     >>BulkOut Req=0x1b6, Complete=0x1b5, Other=0x8
[  142.626076]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  146.926190] BulkOutDataPacket failed: ReasonCode=-2!
[  146.926195]     >>BulkOut Req=0x1b7, Complete=0x1b6, Other=0x9
[  146.926198]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  149.116078] BulkOutDataPacket failed: ReasonCode=-2!
[  149.116083]     >>BulkOut Req=0x1b7, Complete=0x1b6, Other=0xa
[  149.116086]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  151.169992] #
[  151.250188] BulkOutDataPacket failed: ReasonCode=-2!
[  151.250193]     >>BulkOut Req=0x1b7, Complete=0x1b6, Other=0xb
[  151.250196]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  154.693294] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 434
[  155.286093] BulkOutDataPacket failed: ReasonCode=-2!
[  155.286098]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0xc
[  155.286101]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  157.405973] BulkOutDataPacket failed: ReasonCode=-2!
[  157.405977]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0xd
[  157.405981]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  159.590092] BulkOutDataPacket failed: ReasonCode=-2!
[  159.590097]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0xe
[  159.590100]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  161.750090] BulkOutDataPacket failed: ReasonCode=-2!
[  161.750095]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0xf
[  161.750099]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  163.861971] BulkOutDataPacket failed: ReasonCode=-2!
[  163.861976]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0x10
[  163.861979]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  166.017968] BulkOutDataPacket failed: ReasonCode=-2!
[  166.017973]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0x11
[  166.017976]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  168.177968] BulkOutDataPacket failed: ReasonCode=-2!
[  168.177973]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0x12
[  168.177976]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  170.346091] BulkOutDataPacket failed: ReasonCode=-2!
[  170.346096]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0x13
[  170.346099]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  172.493967] BulkOutDataPacket failed: ReasonCode=-2!
[  172.493972]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0x14
[  172.493975]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  174.651717] BulkOutDataPacket failed: ReasonCode=-2!
[  174.651722]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0x15
[  174.651725]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  176.834087] BulkOutDataPacket failed: ReasonCode=-2!
[  176.834092]     >>BulkOut Req=0x1b9, Complete=0x1b8, Other=0x16
[  176.834095]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  179.981971] BulkOutDataPacket failed: ReasonCode=-2!
[  179.981975]     >>BulkOut Req=0x1ba, Complete=0x1b9, Other=0x17
[  179.981979]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  184.193982] BulkOutDataPacket failed: ReasonCode=-2!
[  184.193987]     >>BulkOut Req=0x1bb, Complete=0x1ba, Other=0x18
[  184.193991]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  188.517981] BulkOutDataPacket failed: ReasonCode=-2!
[  188.517985]     >>BulkOut Req=0x1bc, Complete=0x1bb, Other=0x19
[  188.517989]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  192.685995] BulkOutDataPacket failed: ReasonCode=-2!
[  192.686000]     >>BulkOut Req=0x1bd, Complete=0x1bc, Other=0x1a
[  192.686003]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  194.826248] BulkOutDataPacket failed: ReasonCode=-2!
[  194.826253]     >>BulkOut Req=0x1bd, Complete=0x1bc, Other=0x1b
[  194.826256]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  197.966004] BulkOutDataPacket failed: ReasonCode=-2!
[  197.966009]     >>BulkOut Req=0x1be, Complete=0x1bd, Other=0x1c
[  197.966012]     >>BulkOut Header:58 0 0 44 0 0 0 0
[  201.142011] BulkOutDataPacket failed: ReasonCode=-2!
[  201.142016]     >>BulkOut Req=0x1bf, Complete=0x1be, Other=0x1d
[  201.142019]     >>BulkOut Header:68 2 0 44 0 0 0 0
[  204.278024] BulkOutDataPacket failed: ReasonCode=-2!
[  204.278029]     >>BulkOut Req=0x1c0, Complete=0x1bf, Other=0x1e
[  204.278033]     >>BulkOut Header:58 0 0 44 0 0 0 0
[  206.418024] BulkOutDataPacket failed: ReasonCode=-2!
[  206.418029]     >>BulkOut Req=0x1c0, Complete=0x1bf, Other=0x1f
[  206.418032]     >>BulkOut Header:58 0 0 44 0 0 0 0
[  210.555297] BulkOutDataPacket failed: ReasonCode=-2!
[  210.555301]     >>BulkOut Req=0x1c2, Complete=0x1c1, Other=0x20
[  210.555305]     >>BulkOut Header:64 0 0 44 0 0 0 0
[  214.691688] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 351
[  217.774081] BulkOutDataPacket failed: ReasonCode=-2!
[  217.774086]     >>BulkOut Req=0x1c8, Complete=0x1c7, Other=0x21
[  217.774089]     >>BulkOut Header:58 0 0 44 0 0 0 0
[  219.902083] BulkOutDataPacket failed: ReasonCode=-2!
[  219.902088]     >>BulkOut Req=0x1c8, Complete=0x1c7, Other=0x22
[  219.902092]     >>BulkOut Header:58 0 0 44 0 0 0 0
[  224.138091] BulkOutDataPacket failed: ReasonCode=-2!
[  224.138096]     >>BulkOut Req=0x1ca, Complete=0x1c9, Other=0x23
[  224.138099]     >>BulkOut Header:70 0 0 44 0 0 0 0
[  294.683684] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 434
[  298.969076] DRS: unkown mode,default use 11N 1S AP 
[  298.969084] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  301.914335] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 434
[  323.706536] BulkOutDataPacket failed: ReasonCode=-2!
[  323.706540]     >>BulkOut Req=0x48b, Complete=0x48a, Other=0x24
[  323.706544]     >>BulkOut Header:c0 0 0 44 0 0 0 0
[  330.142040] BulkOutDataPacket failed: ReasonCode=-2!
[  330.142045]     >>BulkOut Req=0x491, Complete=0x490, Other=0x25
[  330.142048]     >>BulkOut Header:a0 3 0 44 0 0 0 0
[  337.575344] #
[  394.691622] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 590
[  399.576114] #
[  495.996170] #

lsb_release -d:
**Description:    Ubuntu 9.10**

uname -mr:
**2.6.31-16-generic i686**

---

### Post by _mikec_ on 2009-12-15
please help, this connection is driving me crazy !.

---

### Post by _mikec_ on 2009-12-16
any one ? no one ? echo ? echooo .. lol..mm .

---

### Post by yakshbuntu on 2009-12-19
Hi, 

Try this

**sudo iwconfig wlan0 rate 54M**

replace wlan0 with ra0 or whatever interface you have (I am not sure if it is ra0 or wlan0 on your sys)

Then try hitting youtube and check if it increases speed. I am having a similar kind of problem, after kernel 2.6.31 wireless defaults to 1 Mbps and only increases when there is a lot of data flow, I guess the change is for power saving even though it is affecting my desktop. This happens in all distributions with 2.6.31 kernels

If you find net fast, after reapplying the rate to 54M, you can add the following to make it permanent

edit rc.local 

**sudo vi /etc/rc.local**



then add the following before last line (change wlan0 to the appropriate interface, maybe ra0 i guess in your case)

**iwconfig wlan0 rate 54M**

---

### Post by hardtofi on 2010-05-17
Seeing that you have the rate set for 36 Mbit and I suppose you wouldn't consider 36 Mbit being like a 56k modem that doesn't seems to be your problem.

Have you tried building the driver from source? I got myself a realtek based usb wifi and had tons of problems getting it to work. The most confusing/hard part ws to actually locate where I could get the working drivers and firmware ( [http://www.ralinktech.com.tw/support.php?s=2]("http://www.ralinktech.com.tw/support.php?s=2")) since looking at realtek.com doesn't give much.

I also had to blacklist rt2800usb which made things go bad.

---

### Post by JohnDoe365 on 2010-05-19
You are not alone. I walked through a big list of complaints regarding WiFi speed in 10.04. This is not hardware related but a WiFi subsystem or kernel bug.

Please try the following:

disable WiFi
re-enable
wait for re-association

Is speed back to normal?

Also see [http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3)

If speed is back ... sorry won't last for long, the speed drops back to unacceptable slow.

Regard to leave a message at 
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936)
to see the issue quickly addressed.

---

