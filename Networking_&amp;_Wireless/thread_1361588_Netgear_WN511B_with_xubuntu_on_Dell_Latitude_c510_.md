---
title: "Netgear WN511B with xubuntu on Dell Latitude c510 (model PP01L)"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by trethomil on 2009-12-22
Having a problem setting up a Netgear WN511B wireless card on my old Dell Laptop. Here is the information requested by the sticky:

Laptop: Dell Latitude C510 (model PP01L)

Network Controller 07:00.0 Network Controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

Results of other requested code:

   $ ifconfig
   
  eth0      Link encap:Ethernet  HWaddr 00:0b:db:9f:f9:00  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:11 Base address:0x6c00 
  
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
  wlan0     Link encap:Ethernet  HWaddr 00:11:09:08:30:64  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
  wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-08-30-64-00-00-00-00-00-00-00-00-00-00  
            UP RUNNING  MTU:0  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
   
  $ iwconfig
  
  lo        no wireless extensions.
  
  eth0      no wireless extensions.
  
  wmaster0  no wireless extensions.
  
  wlan0     IEEE 802.11b  ESSID:""  
            Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
            Tx-Power=20 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:on
            Link Quality:0  Signal level:0  Noise level:0
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
   
  $ lsmod
   
  Module                  Size  Used by
  snd_intel8x0           30168  4 
  snd_ac97_codec        101216  1 snd_intel8x0
  ac97_bus                1532  1 snd_ac97_codec
  arc4                    1660  2 
  snd_pcm_oss            37920  0 
  ecb                     2524  2 
  snd_mixer_oss          16028  3 snd_pcm_oss
  snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
  snd_seq_dummy           2656  0 
  iptable_filter          3100  0 
  snd_seq_oss            28576  0 
  rt2400pci              12092  0 
  rt2x00pci               7900  1 rt2400pci
  snd_seq_midi            6432  0 
  rt2x00lib              29756  2 rt2400pci,rt2x00pci
  pcmcia                 36808  0 
  ip_tables              11692  1 iptable_filter
  snd_rawmidi            22208  1 snd_seq_midi
  led_class               4096  1 rt2x00lib
  snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
  x_tables               16544  1 ip_tables
  input_polldev           3716  1 rt2x00lib
  yenta_socket           24200  3 
  snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
  mac80211              181076  2 rt2x00pci,rt2x00lib
  rsrc_nonstatic         11644  1 yenta_socket
  joydev                 10272  0 
  snd_timer              22276  2 snd_pcm,snd_seq
  cfg80211               93052  2 rt2x00lib,mac80211
  snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
  pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
  eeprom_93cx6            1916  1 rt2400pci
  lib80211                6432  0 
  ppdev                   6688  0 
  snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_s
  q,snd_timer,snd_seq_device
  soundcore               7264  3 snd
  parport_pc             31940  1 
  lp                      8964  0 
  psmouse                56500  0 
  snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
  parport                35340  3 ppdev,parport_pc,lp
  serio_raw               5280  0 
  shpchp                 32272  0 
  dell_wmi                2564  0 
  dcdbas                  7292  0 
  usb_storage            52576  0 
  radeon                636000  2 
  ttm                    36212  1 radeon
  drm                   159584  4 radeon,ttm
  i2c_algo_bit            5760  1 radeon
  3c59x                  37604  0 
  mii                     5212  1 3c59x
  intel_agp              27484  1 
  agpgart                34988  3 ttm,drm,intel_agp
  video                  19380  0 
  output                  2780  1 video
  floppy                 54916  0 
  $ dmesg
   
  [    0.000000] Initializing cgroup subsys cpuset
  [    0.000000] Initializing cgroup subsys cpu
  [    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu
  4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
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
  [    0.000000]  BIOS-e820: 0000000000100000 - 000000000ffd3000 (usable)
  [    0.000000]  BIOS-e820: 000000000ffd3000 - 0000000010000000 (reserved)
  [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
  [    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
  [    0.000000] DMI 2.3 present.
  [    0.000000] last_pfn = 0xffd3 max_arch_pfn = 0x100000
  [    0.000000] MTRR default type: uncachable
  [    0.000000] MTRR fixed ranges enabled:
  [    0.000000]   00000-9FFFF write-back
  [    0.000000]   A0000-BFFFF uncachable
  [    0.000000]   C0000-CFFFF write-protect
  [    0.000000]   D0000-EFFFF uncachable
  [    0.000000]   F0000-FFFFF write-protect
  [    0.000000] MTRR variable ranges enabled:
  [    0.000000]   0 base 000000000 mask FF0000000 write-back
  [    0.000000]   1 base 0FEDA0000 mask FFFFE0000 write-through
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
  [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
  [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
  [    0.000000]  modified: 0000000000100000 - 000000000ffd3000 (usable)
  [    0.000000]  modified: 000000000ffd3000 - 0000000010000000 (reserved)
  [    0.000000]  modified: 00000000feda0000 - 00000000fee00000 (reserved)
  [    0.000000]  modified: 00000000ffb80000 - 0000000100000000 (reserved)
  [    0.000000] initial memory mapped : 0 - 00c00000
  [    0.000000] init_memory_mapping: 0000000000000000-000000000ffd3000
  [    0.000000] Using x86 segment limits to approximate NX protection
  [    0.000000]  0000000000 - 0000400000 page 4k
  [    0.000000]  0000400000 - 000fc00000 page 2M
  [    0.000000]  000fc00000 - 000ffd3000 page 4k
  [    0.000000] kernel direct mapping tables up to ffd3000 @ 7000-c000
  [    0.000000] RAMDISK: 0b8d5000 - 0c01d6c5
  [    0.000000] ACPI: RSDP 000fde50 00014 (v00 DELL  )
  [    0.000000] ACPI: RSDT 000fde64 00028 (v01 DELL    CPi R   27D30510 ASL  00000061)
  [    0.000000] ACPI: FACP 000fde90 00074 (v01 DELL    CPi R   27D30510 ASL  00000061)
  [    0.000000] ACPI: DSDT 0fff0000 03182 (v01 INT430 SYSFexxx 00001001 MSFT 0100000E)
  [    0.000000] ACPI: FACS 0ffff800 00040
  [    0.000000] 0MB HIGHMEM available.
  [    0.000000] 255MB LOWMEM available.
  [    0.000000]   mapped low ram: 0 - 0ffd3000
  [    0.000000]   low ram: 0 - 0ffd3000
  [    0.000000]   node 0 low ram: 00000000 - 0ffd3000
  [    0.000000]   node 0 bootmap 00008000 - 00009ffc
  [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000ffd3000]
  [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
  [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
  [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
  [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
  [    0.000000]   #4 [000b8d5000 - 000c01d6c5]          RAMDISK ==> [000b8d5000 - 000c01d6c5]
  [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
  [    0.000000]   #6 [00008a9000 - 00008ac198]              BRK ==> [00008a9000 - 00008ac198]
  [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 -0000008000]
  [    0.000000]   #8 [0000008000 - 000000a000]          BOOTMAP ==> [0000008000 - 000000a000]
  [    0.000000] Zone PFN ranges:
  [    0.000000]   DMA      0x00000000 -> 0x00001000
  [    0.000000]   Normal   0x00001000 -> 0x0000ffd3
  [    0.000000]   HighMem  0x0000ffd3 -> 0x0000ffd3
  [    0.000000] Movable zone start PFN for each node
  [    0.000000] early_node_map[3] active PFN ranges
  [    0.000000]     0: 0x00000000 -> 0x00000002
  [    0.000000]     0: 0x00000006 -> 0x0000009f
  [    0.000000]     0: 0x00000100 -> 0x0000ffd3
  [    0.000000] On node 0 totalpages: 65390
  [    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1000000
  [    0.000000]   DMA zone: 32 pages used for memmap
  [    0.000000]   DMA zone: 0 pages reserved
  [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
  [    0.000000]   Normal zone: 480 pages used for memmap
  [    0.000000]   Normal zone: 60915 pages, LIFO batch:15
  [    0.000000] Using APIC driver default
  [    0.000000] ACPI: PM-Timer IO Port: 0x808
  [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
  [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
  [    0.000000] APIC: disable apic facility
  [    0.000000] nr_irqs_gsi: 16
  [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
  [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
  [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
  [    0.000000] Allocating PCI resources starting at 10000000 (gap: 10000000:eeda0000)
  [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
  [    0.000000] PERCPU: Embedded 14 pages at c1202000, static data 35612 bytes
  [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64878
  [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=7a2e92eb-ca0e-4f39-a959-a9da56c67969 ro quiet splash
  [    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
  [    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
  [    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
  [    0.000000] Enabling fast FPU save and restore... done.
  [    0.000000] Enabling unmasked SIMD FPU exception support... done.
  [    0.000000] Initializing CPU#0
  [    0.000000] allocated 1309820 bytes of page_cgroup
  [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
  [    0.000000] Initializing HighMem for node 0 (00000000:00000000)
  [    0.000000] Memory: 242324k/261964k available (4566k kernel code, 18944k reserved, 2142k data, 540k init, 0k highmem)
  [    0.000000] virtual kernel memory layout:
  [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
  [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
  [    0.000000]     vmalloc : 0xd07d3000 - 0xff7fe000   ( 752 MB)
  [    0.000000]     lowmem  : 0xc0000000 - 0xcffd3000   ( 255 MB)
  [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
  [    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
  [    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
  [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
  [    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
  [    0.000000] NR_IRQS:2304 nr_irqs:256
  [    0.000000] Fast TSC calibration using PIT
  [    0.000000] Detected 996.762 MHz processor.
  [    0.001244] Console: colour VGA+ 80x25
  [    0.001253] console [tty0] enabled
  [    0.001336] Calibrating delay loop (skipped), value calculated using timer frequency.. 1993.52
  BogoMIPS (lpj=3987048)
  [    0.001379] Security Framework initialized
  [    0.001434] AppArmor: AppArmor initialized
  [    0.001453] Mount-cache hash table entries: 512
  [    0.001715] Initializing cgroup subsys ns
  [    0.001724] Initializing cgroup subsys cpuacct
  [    0.001735] Initializing cgroup subsys memory
  [    0.001755] Initializing cgroup subsys freezer
  [    0.001761] Initializing cgroup subsys net_cls
  [    0.001794] CPU: L1 I cache: 16K, L1 D cache: 16K
  [    0.001801] CPU: L2 cache: 512K
  [    0.001812] mce: CPU supports 5 MCE banks
  [    0.001838] Performance Counters: 
  [    0.001844] no APIC, boot with the "lapic" boot parameter to force-enable it.
  [    0.001850] no hardware sampling interrupt available.
  [    0.001855] p6 PMU driver.
  [    0.001895] ... version:                 0
  [    0.001900] ... bit width:               32
  [    0.001904] ... generic counters:        2
  [    0.001910] ... value mask:              00000000ffffffff
  [    0.001915] ... max period:              000000007fffffff
  [    0.001920] ... fixed-purpose counters:  0
  [    0.001925] ... counter mask:            0000000000000003
  [    0.001933] Checking 'hlt' instruction... OK.
  [    0.017162] SMP alternatives: switching to UP code
  [    0.028035] Freeing SMP alternatives: 19k freed
  [    0.028058] ACPI: Core revision 20090521
  [    0.036013] ACPI: setting ELCR to 0200 (from 0800)
  [    0.040170] weird, boot CPU (#0) not listed by the BIOS.
  [    0.040175] SMP motherboard not detected.
  [    0.040181] Local APIC not detected. Using dummy APIC emulation.
  [    0.040186] SMP disabled
  [    0.040510] Brought up 1 CPUs
  [    0.040519] Total of 1 processors activated (1993.52 BogoMIPS).
  [    0.044044] CPU0 attaching NULL sched-domain.
  [    0.044687] Booting paravirtualized kernel on bare hardware
  [    0.045298] regulator: core version 0.5
  [    0.045332] Time:  9:53:29  Date: 12/22/09
  [    0.045477] NET: Registered protocol family 16
  [    0.045814] EISA bus registered
  [    0.045856] ACPI: bus type pci registered
  [    0.068561] PCI: PCI BIOS revision 2.10 entry at 0xfbfee, last bus=2
  [    0.068567] PCI: Using configuration type 1 for base access
  [    0.071122] bio: create slab <bio-0> at 0
  [    0.072266] ACPI: EC: Look up EC in DSDT
  [    0.093581] ACPI: Interpreter enabled
  [    0.093601] ACPI: (supports S0 S1 S3 S4 S5)
  [    0.093653] ACPI: Using PIC for interrupt routing
  [    0.127677] ACPI: Power Resource [PADA] (on)
  [    0.131882] ACPI: ACPI Dock Station Driver: 1 docks/bays found
  [    0.142060] ACPI: PCI Root Bridge [PCI0] (0000:00)
  [    0.142154] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
  [    0.142313] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
  [    0.142422] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
  [    0.142431] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
  [    0.142465] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
  [    0.142476] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
  [    0.142487] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
  [    0.142498] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
  [    0.142509] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
  [    0.142521] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
  [    0.142568] pci 0000:00:1f.5: reg 10 io port: [0xd800-0xd8ff]
  [    0.142580] pci 0000:00:1f.5: reg 14 io port: [0xdc80-0xdcbf]
  [    0.142636] pci 0000:00:1f.6: reg 10 io port: [0xd400-0xd4ff]
  [    0.142648] pci 0000:00:1f.6: reg 14 io port: [0xdc00-0xdc7f]
  [    0.142721] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
  [    0.142732] pci 0000:01:00.0: reg 14 io port: [0xc000-0xc0ff]
  [    0.142742] pci 0000:01:00.0: reg 18 32bit mmio: [0xfcff0000-0xfcffffff]
  [    0.142761] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
  [    0.142784] pci 0000:01:00.0: supports D1 D2
  [    0.142823] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
  [    0.142831] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
  [    0.142840] pci 0000:00:01.0: bridge 32bit mmio pref: [0xe0000000-0xe7ffffff]
  [    0.142882] pci 0000:02:00.0: reg 10 io port: [0xec80-0xecff]
  [    0.142893] pci 0000:02:00.0: reg 14 32bit mmio: [0xf8fffc00-0xf8fffc7f]
  [    0.142920] pci 0000:02:00.0: reg 30 32bit mmio: [0xf9000000-0xf901ffff]
  [    0.142941] pci 0000:02:00.0: supports D1 D2
  [    0.142948] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
  [    0.142956] pci 0000:02:00.0: PME# disabled
  [    0.142996] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
  [    0.143018] pci 0000:02:01.0: supports D1 D2
  [    0.143024] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
  [    0.143032] pci 0000:02:01.0: PME# disabled
  [    0.143072] pci 0000:02:01.1: reg 10 32bit mmio: [0x000000-0x000fff]
  [    0.143094] pci 0000:02:01.1: supports D1 D2
  [    0.143100] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
  [    0.143108] pci 0000:02:01.1: PME# disabled
  [    0.143154] pci 0000:02:03.0: reg 10 32bit mmio: [0xf8ffc000-0xf8ffdfff]
  [    0.143236] pci 0000:00:1e.0: transparent bridge
  [    0.143244] pci 0000:00:1e.0: bridge io port: [0xe000-0xffff]
  [    0.143253] pci 0000:00:1e.0: bridge 32bit mmio: [0xf4000000-0xfbffffff]
  [    0.143305] pci_bus 0000:00: on NUMA node 0
  [    0.143315] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
  [    0.143533] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
  [    0.143584] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
  [    0.170456] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
  [    0.170711] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
  [    0.170964] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
  [    0.171217] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
  [    0.171687] SCSI subsystem initialized
  [    0.171880] libata version 3.00 loaded.
  [    0.172092] usbcore: registered new interface driver usbfs
  [    0.172136] usbcore: registered new interface driver hub
  [    0.172204] usbcore: registered new device driver usb
  [    0.172529] ACPI: WMI: Mapper loaded
  [    0.172535] PCI: Using ACPI for IRQ routing
  [    0.172819] Bluetooth: Core ver 2.15
  [    0.172912] NET: Registered protocol family 31
  [    0.172917] Bluetooth: HCI device and connection manager initialized
  [    0.172925] Bluetooth: HCI socket layer initialized
  [    0.172930] NetLabel: Initializing
  [    0.172934] NetLabel:  domain hash size = 128
  [    0.172938] NetLabel:  protocols = UNLABELED CIPSOv4
  [    0.172970] NetLabel:  unlabeled traffic allowed by default
  [    0.178320] pnp: PnP ACPI init
  [    0.178397] ACPI: bus type pnp registered
  [    0.198035] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
  [    0.198048] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
  [    0.198197] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
  [    0.198208] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
  [    0.198217] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
  [    0.199002] pnp 00:04: io resource (0xf000-0xf0fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199013] pnp 00:04: io resource (0xf100-0xf1fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199022] pnp 00:04: io resource (0xf200-0xf2fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199032] pnp 00:04: io resource (0xf400-0xf4fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199041] pnp 00:04: io resource (0xf500-0xf5fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199051] pnp 00:04: io resource (0xf600-0xf6fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199060] pnp 00:04: io resource (0xf800-0xf8fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199070] pnp 00:04: io resource (0xf900-0xf9fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199079] pnp 00:04: io resource (0xfa00-0xfafe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199088] pnp 00:04: io resource (0xfc00-0xfcfe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199098] pnp 00:04: io resource (0xfd00-0xfdfe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199107] pnp 00:04: io resource (0xfe00-0xfefe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
  [    0.199117] pnp 00:04: mem resource (0xfa000000-0xfbffffff) overlaps 0000:00:1e.0 BAR 14 (0xf4000000-0xfbffffff), disabling
  [    0.250156] pnp: PnP ACPI: found 17 devices
  [    0.250162] ACPI: ACPI bus type pnp unregistered
  [    0.250173] PnPBIOS: Disabled by ACPI PNP
  [    0.250202] system 00:00: iomem range 0x0-0x9fbff could not be reserved
  [    0.250211] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
  [    0.250219] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
  [    0.250228] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
  [    0.250236] system 00:00: iomem range 0x100000-0xffeffff could not be reserved
  [    0.250244] system 00:00: iomem range 0xfff0000-0xfffffff has been reserved
  [    0.250253] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
  [    0.250261] system 00:00: iomem range 0xfff80000-0xffffffff has been reserved
  [    0.250279] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
  [    0.250294] system 00:03: ioport range 0x880-0x8bf has been reserved
  [    0.250303] system 00:03: ioport range 0x8c0-0x8df has been reserved
  [    0.250310] system 00:03: ioport range 0x8e0-0x8ff has been reserved
  [    0.250335] system 00:09: ioport range 0x900-0x91f has been reserved
  [    0.250343] system 00:09: ioport range 0x3f0-0x3f1 has been reserved
  [    0.250361] system 00:0f: ioport range 0xbf40-0xbf5f has been reserved
  [    0.250369] system 00:0f: ioport range 0xbf20-0xbf3f has been reserved
  [    0.250384] system 00:10: iomem range 0xfebffc00-0xfebfffff has been reserved
  [    0.285329] AppArmor: AppArmor Filesystem Enabled
  [    0.285358] pci 0000:02:00.0: BAR 6: address space collision on of device [0xf90000000xf901ffff]
  [    0.285405] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
  [    0.285412] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
  [    0.285421] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
  [    0.285429] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
  [    0.285451] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
  [    0.285458] pci 0000:02:01.0:   IO window: 0x00e000-0x00e0ff
  [    0.285467] pci 0000:02:01.0:   IO window: 0x00e400-0x00e4ff
  [    0.285475] pci 0000:02:01.0:   PREFETCH window: 0x10000000-0x13ffffff
  [    0.285484] pci 0000:02:01.0:   MEM window: 0xf4000000-0xf7ffffff
  [    0.285493] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
  [    0.285499] pci 0000:02:01.1:   IO window: 0x00e800-0x00e8ff
  [    0.285507] pci 0000:02:01.1:   IO window: 0x00f000-0x00f0ff
  [    0.285516] pci 0000:02:01.1:   PREFETCH window: 0x14000000-0x17ffffff
  [    0.285525] pci 0000:02:01.1:   MEM window: 0x1c000000-0x1fffffff
  [    0.285533] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
  [    0.285540] pci 0000:00:1e.0:   IO window: 0xe000-0xffff
  [    0.285550] pci 0000:00:1e.0:   MEM window: 0xf4000000-0xfbffffff
  [    0.285558] pci 0000:00:1e.0:   PREFETCH window: 0x10000000-0x19ffffff
  [    0.285583] pci 0000:00:1e.0: setting latency timer to 64
  [    0.285596] pci 0000:02:01.0: enabling device (0000 -> 0003)
  [    0.285957] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
  [    0.285964] PCI: setting IRQ 11 as level-triggered
  [    0.285974] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
  [    0.285991] pci 0000:02:01.1: enabling device (0000 -> 0003)
  [    0.286002] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
  [    0.286016] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
  [    0.286023] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
  [    0.286031] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
  [    0.286038] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
  [    0.286045] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
  [    0.286052] pci_bus 0000:02: resource 0 io:  [0xe000-0xffff]
  [    0.286059] pci_bus 0000:02: resource 1 mem: [0xf4000000-0xfbffffff]
  [    0.286067] pci_bus 0000:02: resource 2 pref mem [0x10000000-0x19ffffff]
  [    0.286074] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
  [    0.286080] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
  [    0.286088] pci_bus 0000:03: resource 0 io:  [0xe000-0xe0ff]
  [    0.286094] pci_bus 0000:03: resource 1 io:  [0xe400-0xe4ff]
  [    0.286101] pci_bus 0000:03: resource 2 pref mem [0x10000000-0x13ffffff]
  [    0.286109] pci_bus 0000:03: resource 3 mem: [0xf4000000-0xf7ffffff]
  [    0.286116] pci_bus 0000:07: resource 0 io:  [0xe800-0xe8ff]
  [    0.286123] pci_bus 0000:07: resource 1 io:  [0xf000-0xf0ff]
  [    0.286130] pci_bus 0000:07: resource 2 pref mem [0x14000000-0x17ffffff]
  [    0.286137] pci_bus 0000:07: resource 3 mem: [0x1c000000-0x1fffffff]
  [    0.286239] NET: Registered protocol family 2
  [    0.286497] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
  [    0.287228] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
  [    0.287391] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
  [    0.287551] TCP: Hash tables configured (established 8192 bind 8192)
  [    0.287558] TCP reno registered
  [    0.287751] NET: Registered protocol family 1
  [    0.287905] Trying to unpack rootfs image as initramfs...
  [    0.752926] Freeing initrd memory: 7457k freed
  [    0.773830] speedstep-lib: frequency transition measured seems out of range (6000 nSec), falling back to a safe one of500000 nSec.
  [    0.773854] cpufreq-nforce2: No nForce2 chipset.
  [    0.773923] Scanning for low memory corruption every 60 seconds
  [    0.774231] audit: initializing netlink socket (disabled)
  [    0.774280] type=2000 audit(1261475608.772:1): initialized
  [    0.787671] Switched to high resolution mode on CPU 0
  [    0.793773] HugeTLB registered 4 MB page size, pre-allocated 0 pages
  [    0.798036] VFS: Disk quotas dquot_6.5.2
  [    0.798192] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
  [    0.799782] fuse init (API version 7.12)
  [    0.800048] msgmni has been set to 488
  [    0.800539] alg: No test for stdrng (krng)
  [    0.800577] io scheduler noop registered
  [    0.800583] io scheduler anticipatory registered
  [    0.800588] io scheduler deadline registered
  [    0.800715] io scheduler cfq registered (default)
  [    0.800783] pci 0000:01:00.0: Boot video device
  [    0.800981] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
  [    0.801039] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
  [    0.801765] ACPI: AC Adapter [AC] (on-line)
  [    0.801930] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
  [    0.802502] ACPI: Lid Switch [LID]
  [    0.802609] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
  [    0.802620] ACPI: Power Button [PBTN]
  [    0.802720] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
  [    0.802728] ACPI: Sleep Button [SBTN]
  [    0.803143] Marking TSC unstable due to TSC halts in idle
  [    0.803181] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
  [    0.803238] processor LNXCPU:00: registered as cooling_device0
  [    0.832852] thermal LNXTHERM:01: registered as thermal_zone0
  [    0.832871] ACPI: Thermal Zone [THM] (26 C)
  [    0.832982] isapnp: Scanning for PnP cards...
  [    1.736332] isapnp: No Plug & Play device found
  [    1.739203] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
  [    1.739343] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
  [    1.740150] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
  [    1.740724] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
  [    1.740732] PCI: setting IRQ 5 as level-triggered
  [    1.740741] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
  [    1.740756] serial 0000:00:1f.6: PCI INT B disabled
  [    1.743092] brd: module loaded
  [    1.744276] loop: module loaded
  [    1.744472] input: Macintosh mouse button emulation as /devices/virtual/input/input3
  [    1.744738] ata_piix 0000:00:1f.1: version 2.13
  [    1.744761] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
  [    1.745153] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
  [    1.745163] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
  [    1.745251] ata_piix 0000:00:1f.1: setting latency timer to 64
  [    1.745471] scsi0 : ata_piix
  [    1.745719] scsi1 : ata_piix
  [    1.747207] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
  [    1.747215] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
  [    1.754151] ACPI: Battery Slot [BAT0] (battery present)
  [    1.754248] ACPI: Battery Slot [BAT1] (battery absent)
  [    1.756529] Fixed MDIO Bus: probed
  [    1.756623] PPP generic driver version 2.4.2
  [    1.756902] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
  [    1.756950] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
  [    1.756988] uhci_hcd: USB Universal Host Controller Interface driver
  [    1.757086] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
  [    1.757104] uhci_hcd 0000:00:1d.0: setting latency timer to 64
  [    1.757112] uhci_hcd 0000:00:1d.0: UHCI Host Controller
  [    1.757244] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
  [    1.757285] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
  [    1.757525] usb usb1: configuration #1 chosen from 1 choice
  [    1.757600] hub 1-0:1.0: USB hub found
  [    1.757621] hub 1-0:1.0: 2 ports detected
  [    1.757871] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
  [    1.769729] serio: i8042 KBD port at 0x60,0x64 irq 1
  [    1.769746] serio: i8042 AUX port at 0x60,0x64 irq 12
  [    1.769896] mice: PS/2 mouse device common for all mice
  [    1.770247] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
  [    1.770275] rtc0: alarms up to one day, 114 bytes nvram
  [    1.770527] device-mapper: uevent: version 1.0.3
  [    1.770749] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
  [    1.770938] device-mapper: multipath: version 1.1.0 loaded
  [    1.770946] device-mapper: multipath round-robin: version 1.0.0 loaded
  [    1.771292] EISA: Probing bus 0 at eisa.0
  [    1.771328] EISA: Detected 0 cards.
  [    1.771536] cpuidle: using governor ladder
  [    1.771688] cpuidle: using governor menu
  [    1.773083] TCP cubic registered
  [    1.773516] NET: Registered protocol family 10
  [    1.774668] lo: Disabled Privacy Extensions
  [    1.775513] NET: Registered protocol family 17
  [    1.775561] Bluetooth: L2CAP ver 2.13
  [    1.775566] Bluetooth: L2CAP socket layer initialized
  [    1.775573] Bluetooth: SCO (Voice Link) ver 0.6
  [    1.775578] Bluetooth: SCO socket layer initialized
  [    1.775680] Bluetooth: RFCOMM TTY layer initialized
  [    1.775688] Bluetooth: RFCOMM socket layer initialized
  [    1.775693] Bluetooth: RFCOMM ver 1.11
  [    1.789900] Using IPI No-Shortcut mode
  [    1.790098] PM: Resume from disk failed.
  [    1.790130] registered taskstats version 1
  [    1.790380]   Magic number: 5:981:879
  [    1.790541] rtc_cmos 00:07: setting system clock to 2009-12-22 09:53:31 UTC (1261475611)
  [    1.790549] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
  [    1.790554] EDD information not available.
  [    1.791764] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
  [    1.928363] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM SCB5265, TD15, max UDMA/33
  [    1.944289] ata2.00: configured for UDMA/33
  [    1.972703] ata1.00: ATA-6: FUJITSU MHT2030AT, 009A, max UDMA/100
  [    1.972711] ata1.00: 58605120 sectors, multi 8: LBA 
  [    1.988629] ata1.00: configured for UDMA/100
  [    1.988927] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2030A 009A PQ: 0 ANSI: 5
  [    1.989221] sd 0:0:0:0: Attached scsi generic sg0 type 0
  [    1.989329] sd 0:0:0:0: [sda] 58605120 512-byte logical blocks: (30.0 GB/27.9 GiB)
  [    1.989472] sd 0:0:0:0: [sda] Write Protect is off
  [    1.989480] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
  [    1.989553] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
  [    1.989916]  sda:
  [    1.990777] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD SCB5265 TD15 PQ: 0 ANSI: 5
  [    1.998405] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
  [    1.998413] Uniform CD-ROM driver Revision: 3.20
  [    1.998615] sr 1:0:0:0: Attached scsi CD-ROM sr0
  [    1.998736] sr 1:0:0:0: Attached scsi generic sg1 type 5
  [    2.068072] usb 1-1: new full speed USB device using uhci_hcd and address 2
  [    2.073285]  sda1 sda2 < sda5 >
  [    2.094882] sd 0:0:0:0: [sda] Attached SCSI disk
  [    2.094917] Freeing unused kernel memory: 540k freed
  [    2.095925] Write protecting the kernel text: 4568k
  [    2.096128] Write protecting the kernel read-only data: 1836k
  [    2.276435] usb 1-1: configuration #1 chosen from 1 choice
  [    2.284046] Clocksource tsc unstable (delta = -287412467 ns)
  [    2.444873] Floppy drive(s): fd0 is 1.44M
  [    2.466595] FDC 0 is a post-1991 82077
  [    2.562485] input: Video Bus as
  /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:16/device:17/input/input5
  [    2.562595] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
  [    2.727754] Linux agpgart interface v0.103
  [    2.795391] agpgart-intel 0000:00:00.0: Intel 830M Chipset
  [    2.837709] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
  [    2.837723] 3c59x 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
  [    2.837746] 3c59x: Donald Becker and others.
  [    2.837761] 0000:02:00.0: 3Com PCI 3c905C Tornado at d0816c00.
  [    2.921857] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
  [    2.925095] [drm] Initialized drm 1.1.0 20060810
  [    2.988867] [drm] radeon default to kernel modesetting DISABLED.
  [    2.989017] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
  [    2.989856] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
  [    3.009035] Initializing USB Mass Storage driver...
  [    3.009273] scsi2 : SCSI emulation for USB Mass Storage devices
  [    3.009544] usbcore: registered new interface driver usb-storage
  [    3.009553] USB Mass Storage support registered.
  [    3.011445] usb-storage: device found at 2
  [    3.011451] usb-storage: waiting for device to settle before scanning
  [    4.670385] PM: Starting manual resume from disk
  [    4.670397] PM: Resume from partition 8:5
  [    4.670401] PM: Checking hibernation image.
  [    4.670753] PM: Resume from disk failed.
  [    4.701456] EXT4-fs (sda1): barriers enabled
  [    4.723856] kjournald2 starting: pid 317, dev sda1:8, commit interval 5 seconds
  [    4.723892] EXT4-fs (sda1): delayed allocation enabled
  [    4.723901] EXT4-fs: file extents enabled
  [    4.731581] EXT4-fs: mballoc enabled
  [    4.731623] EXT4-fs (sda1): mounted filesystem with ordered data mode
  [    5.752716] type=1505 audit(1261475615.461:2): operation="profile_load" pid=340 name=/sbin/dhclient3
  [    5.753824] type=1505 audit(1261475615.461:3): operation="profile_load" pid=340 name=/usr/lib/NetworkManager/nm-dhcp-client.action
  [    5.754440] type=1505 audit(1261475615.461:4): operation="profile_load" pid=340 name=/usr/lib/connman/scripts/dhclient-script
  [    5.864281] type=1505 audit(1261475615.573:5): operation="profile_load" pid=341 name=/usr/bin/evince
  [    5.883844] type=1505 audit(1261475615.589:6): operation="profile_load" pid=341 name=/usr/bin/evince-previewer
  [    5.895531] type=1505 audit(1261475615.601:7): operation="profile_load" pid=341 name=/usr/bin/evince-thumbnailer
  [    5.919849] type=1505 audit(1261475615.625:8): operation="profile_load" pid=343 name=/usr/lib/cups/backend/cups-pdf
  [    5.921277] type=1505 audit(1261475615.629:9): operation="profile_load" pid=343 name=/usr/sbin/cupsd
  [    5.947631] type=1505 audit(1261475615.653:10): operation="profile_load" pid=344 name=/usr/sbin/tcpdump
  [    8.009469] usb-storage: device scan complete
  [    8.012447] scsi 2:0:0:0: Direct-Access     Kingston DataTravelerMini PMAP PQ: 0 ANSI: 0 CCS
  [    8.013505] sd 2:0:0:0: Attached scsi generic sg2 type 0
  [    8.627301] sd 2:0:0:0: [sdb] 2015232 512-byte logical blocks: (1.03 GB/984 MiB)
  [    8.630276] sd 2:0:0:0: [sdb] Write Protect is off
  [    8.630285] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
  [    8.630291] sd 2:0:0:0: [sdb] Assuming drive cache: write through
  [    8.645272] sd 2:0:0:0: [sdb] Assuming drive cache: write through
  [    8.645283]  sdb: sdb1
  [    8.659262] sd 2:0:0:0: [sdb] Assuming drive cache: write through
  [    8.659270] sd 2:0:0:0: [sdb] Attached SCSI removable disk
  [   13.685539] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k 
  [   13.755196] EXT4-fs (sda1): internal journal on sda1:8
  [   14.134063] udev: starting version 147
  [   15.304626] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
  [   15.317304] dell-wmi: No known WMI GUID found
  [   15.428779] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
  [   15.774378] intel_rng: FWH not detected
  [   15.807397] lp: driver loaded but no devices found
  [   15.807877] parport_pc 00:0e: reported by Plug and Play ACPI
  [   15.807933] parport0: PC-style at 0x378 (0x778), irq 7, dma 3
  [PCSPP,TRISTATE,COMPAT,ECP,DMA]
  [   15.904443] lp0: using parport0 (interrupt-driven).
  [   16.263138] ppdev: user-space parallel port driver
  [   16.461846] lib80211: common routines for IEEE802.11 drivers
  [   16.461857] lib80211_crypt: registered algorithm 'NULL'
  [   16.500413] Synaptics Touchpad, model: 1, fw: 5.7, id: 0x9b48b1, caps: 0x804793/0x0
  [   16.500427] serio: Synaptics pass-through port at isa0060/serio1/input0
  [   16.559116] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
  [   16.727247] cfg80211: Calling CRDA to update world regulatory domain
  [   17.149202] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:00e3]
  [   17.149227] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
  [   17.149233] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
  [   17.149243] yenta_cardbus 0000:02:01.0: TI: mfunc 0x01261222, devctl 0x64
  [   17.294159] cfg80211: World regulatory domain updated:
  [   17.294170]          (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
  [   17.294178]          (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
  [   17.294186]          (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
  [   17.294193]          (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
  [   17.294200]          (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
  [   17.294208]          (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
  [   17.380500] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0418, PCI irq 11
  [   17.380511] yenta_cardbus 0000:02:01.0: Socket status: 30000006
  [   17.380529] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xe000 -0xffff
  [   17.380539] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xe000-0xffff: clean.
  [   17.381492] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
  [   17.381501] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x19ffffff
  [   17.381990] yenta_cardbus 0000:02:01.1: CardBus bridge found [1028:00e3]
  [   17.382011] yenta_cardbus 0000:02:01.1: Using CSCINT to route CSC interrupts to PCI
  [   17.382018] yenta_cardbus 0000:02:01.1: Routing CardBus interrupts to PCI
  [   17.382027] yenta_cardbus 0000:02:01.1: TI: mfunc 0x01261222, devctl 0x64
  [   17.614482] yenta_cardbus 0000:02:01.1: ISA IRQ mask 0x0418, PCI irq 11
  [   17.614493] yenta_cardbus 0000:02:01.1: Socket status: 30000020
  [   17.614510] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
  [   17.614520] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xe000-0xffff: clean.
  [   17.615458] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
  [   17.615467] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window:
  0x10000000 - 0x19ffffff
  [   17.681054] ip_tables: (C) 2000-2006 Netfilter Core Team
  [   17.831899] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
  [   17.832871] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
  [   17.833321] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
  [   17.833446] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
  [   17.834153] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
  [   17.857729] rt2400pci 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
  [   18.276089] pcmcia_socket pcmcia_socket1: pccard: CardBus card inserted into slot 1
  [   18.276134] pci 0000:07:00.0: reg 10 32bit mmio: [0x000000-0x003fff]
  [   18.278656] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
  [   18.279611] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
  [   18.280129] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
  [   18.280254] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
  [   18.280953] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
  [   18.625102] phy0: Selected rate control algorithm 'minstrel'
  [   18.626957] Registered led device: rt2400pci-phy0::radio
  [   18.627002] Registered led device: rt2400pci-phy0::quality
  [   18.687395] type=1505 audit(1261475628.393:11): operation="profile_replace" pid=730 name=/sbin/dhclient3
  [   18.701105] type=1505 audit(1261475628.409:12): operation="profile_replace" pid=730 name=/usr/lib/NetworkManager/nm-dhcp-client.action
  [   18.701740] type=1505 audit(1261475628.409:13): operation="profile_replace" pid=730 name=/usr/lib/connman/scripts/dhclient-script
  [   18.719890] type=1505 audit(1261475628.425:14): operation="profile_replace" pid=734 name=/usr/bin/evince
  [   18.742754] type=1505 audit(1261475628.449:15): operation="profile_replace" pid=734 name=/usr/bin/evince-previewer
  [   18.761424] type=1505 audit(1261475628.469:16): operation="profile_replace" pid=734 name=/usr/bin/evince-thumbnailer
  [   18.807075] type=1505 audit(1261475628.513:17): operation="profile_replace" pid=738
  name=/usr/lib/cups/backend/cups-pdf
  [   18.808557] type=1505 audit(1261475628.517:18): operation="profile_replace" pid=738
  name=/usr/sbin/cupsd
  [   18.813907] type=1505 audit(1261475628.521:19): operation="profile_replace" pid=741 name=/usr/sbin/tcpdump
  [   19.175432] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
  [   19.175469] Intel ICH 0000:00:1f.5: setting latency timer to 64
  [   19.225082] psmouse serio2: ID: 10 00 64
  [   19.826485] eth0:  setting half-duplex.
  [   19.826632] ADDRCONF(NETDEV_UP): eth0: link is not ready
  [   19.857489] input: rt2400pci as /devices/pci0000:00/0000:00:1e.0/0000:02:03.0/input/input7
  [   19.876311] ADDRCONF(NETDEV_UP): wlan0: link is not ready
  [   19.936877] intel8x0_measure_ac97_clock: measured 54768 usecs (2632 samples)
  [   19.936887] intel8x0: clocking to 48000
  [   22.841469] IBM TrackPoint firmware: 0x0b, buttons: 2/3
  [   23.122531] input: TPPS/2 IBM TrackPoint as
  /devices/platform/i8042/serio1/serio2/input/input8
  [   25.872615] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
  [   25.872645] agpgart-intel 0000:00:00.0: putting AGP V2 device into 2x mode
  [   25.872674] pci 0000:01:00.0: putting AGP V2 device into 2x mode
  [   26.111004] [drm] Setting GART location based on new memory map
  [   26.111020] [drm] Loading R100 Microcode
  [   26.111065] [drm] writeback test succeeded in 1 usecs
  [  197.307972] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
  [  197.308010] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
  [  197.308015]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
  [  197.308020]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
  [  197.308067] ata2.00: status: { DRDY ERR }
  [  202.311138] ata2.00: qc timeout (cmd 0xa0)
  [  202.311176] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
  [  202.311211] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
  [  202.311216]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
  [  202.311221]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
  [  202.311233] ata2.00: status: { DRDY ERR }
  [  207.348101] ata2: link is slow to respond, please be patient (ready=0)
  [  212.332103] ata2: device not ready (errno=-16), forcing hardreset
  [  212.332123] ata2: soft resetting link
  [  212.512341] ata2.00: configured for UDMA/33
  [  212.512665] ata2: EH complete
  [  583.304104] ata2.00: qc timeout (cmd 0xa0)
  [  583.304140] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
  [  583.304175] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
  [  583.304180]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
  [  583.304185]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
  [  583.304197] ata2.00: status: { DRDY ERR }
  [  583.304243] ata2: soft resetting link
  [  588.460229] ata2.00: qc timeout (cmd 0xa1)
  [  588.460248] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x4)
  [  588.460259] ata2.00: revalidation failed (errno=-5)
  [  593.504101] ata2: link is slow to respond, please be patient (ready=0)
  [  598.488091] ata2: device not ready (errno=-16), forcing hardreset
  [  598.488111] ata2: soft resetting link
  [  598.668339] ata2.00: configured for UDMA/33
  [  598.668664] ata2: EH complete
  [  868.000288] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
  [  868.000329] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
  [  868.000335]          cdb 4a 01 00 00 10 00 00 00  08 00 00 00 00 00 00 00
  [  868.000339]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
  [  868.000351] ata2.00: status: { DRDY }
  [  873.020093] ata2: link is slow to respond, please be patient (ready=0)
  [  878.004078] ata2: device not ready (errno=-16), forcing hardreset
  [  878.004098] ata2: soft resetting link
  [  878.184341] ata2.00: configured for UDMA/33
  [  878.184648] ata2: EH complete
  
  $ sudo lshw -C network
   
  [sudo] password for jane: 
  
    *-network:0
         description: Ethernet interface
         product: 3c905C-TX/TX-M [Tornado]
         vendor: 3Com Corporation
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 78
         serial: 00:0b:db:9f:f9:00
         size: 10MB/s
         capacity: 100MB/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
         resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:18000000-1801ffff(prefetchable)
    *-network:1
         description: Wireless interface
         product: Wireless PCI Adapter RT2400 / RT2460
         vendor: RaLink
         physical id: 3
         bus info: pci@0000:02:03.0
         logical name: wmaster0
         version: 00
         serial: 00:11:09:08:30:64
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list logical ethernet physical wireless
         configuration: broadcast=yes driver=rt2400pci latency=32 multicast=yes wireless=IEEE 802.11b
         resources: irq:5 memory:f8ffc000-f8ffdfff
    *-network UNCLAIMED
         description: Network controller
         product: BCM43XG
         vendor: Broadcom Corporation
         physical id: 1
         bus info: pci@0000:07:00.0
         version: 01
         width: 32 bits
         clock: 33MHz
         configuration: latency=0
         resources: memory:1c000000-1c003fff
   
  $ iwlist scan
   
  lo        Interface doesn't support scanning.
  eth0      Interface doesn't support scanning.
  wmaster0  Interface doesn't support scanning.
  wlan0     No scan results
  
  $ lsb_release -d
  
  Description:   Ubuntu 9.10
  
  $ uname -mr
  
  2.6.31-16-generic i686
   
  $ sudo /etc/init.d/networking restart
  
   * Reconfiguring network interfaces...                                                       [ OK ]
  
My problem is that I have successfully managed - twice - to install the driver for the WN511B. But, when I restart the computer, it doesn't work.

I also have a Radeon internal wireless card that doesn't work. The internal wireless card barely worked on windows but the Netgear worked brilliantly. It also works brilliantly on xubuntu - when it works!

Hope someone can help. I'm considering giving up on xubuntu and going back to XP. It might have been slow, but at least it worked!

---

### Post by chili555 on 2009-12-22
> wlan0 IEEE 802.11b ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:on
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0It looks perfectly healthy to me. It has a driver installed and working:> description: Wireless interface
product: Wireless PCI Adapter RT2400 / RT2460
vendor: RaLink
physical id: 3
bus info: pci@0000:02:03.0
logical name: wmaster0
version: 00
serial: 00:11:09:08:30:64
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=rt2400pci[/COLOR] What happens when you click the Network Manager icon and try to connect?

---

