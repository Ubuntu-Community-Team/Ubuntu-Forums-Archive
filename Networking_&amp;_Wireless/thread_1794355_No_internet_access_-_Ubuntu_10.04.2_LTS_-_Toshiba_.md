---
title: "No internet access - Ubuntu 10.04.2 LTS - Toshiba SG20"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by mytinytown on 2011-06-30
I have an old Toshiba SG20 with Ubuntu 10.04.2 LTS. I had it all set up and lost networking and had to start over. This time I get no internet access. I had ip forwarding set up and I just get nothing.

Here are some codes suggested on the Ubuntu post format:
```

**lspci** 00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP] 00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40) 00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40) 00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 00:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d) 00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02) 00:0b.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
```

```
**ifconfig** eth0      Link encap:Ethernet  HWaddr 00:10:c6:18:6d:e0             inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0           inet6 addr: fe80::210:c6ff:fe18:6de0/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:618 errors:0 dropped:0 overruns:0 frame:0           TX packets:568 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:133409 (133.4 KB)  TX bytes:202291 (202.2 KB)           Interrupt:10 Base address:0xcc00   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:244 errors:0 dropped:0 overruns:0 frame:0           TX packets:244 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:15708 (15.7 KB)  TX bytes:15708 (15.7 KB)  wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-3B-1F-D5-30-30-00-00-00-00-00-00-00-00             UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:715 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)           Interrupt:9 Base address:0x100   wlan0     Link encap:Ethernet  HWaddr 00:09:5b:3b:1f:d5             inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0           inet6 addr: fe80::209:5bff:fe3b:1fd5/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)           Interrupt:9 Base address:0x100 
```

```
**iwconfig** lo        no wireless extensions.  eth1      no wireless extensions.  eth0      no wireless extensions.  wifi0     IEEE 802.11b  ESSID:"MyTinyTown_B"             Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5              Bit Rate:11 Mb/s   Sensitivity=1/3             Retry short limit:8   RTS thr:off   Fragment thr:off           Encryption key:****-****-****-****-****-****-**   Security mode:restricted           Power Management:off            wlan0     IEEE 802.11b  ESSID:"MyTinyTown_B"             Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5              Bit Rate:11 Mb/s   Sensitivity=1/3             Retry short limit:8   RTS thr:off   Fragment thr:off           Encryption key:****-****-****-****-****-****-** Security mode:restricted           Power Management:off           Link Quality:0  Signal level:0  Noise level:0           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           Tx excessive retries:0  Invalid misc:15   Missed beacon:0
```

```
**> lsmod** Module                  Size  Used by aoe                    22485  0  nfsd                  238874  11  lockd                  64849  1 nfsd nfs_acl                 2245  1 nfsd auth_rpcgss            33767  1 nfsd sunrpc                193085  10 nfsd,lockd,nfs_acl,auth_rpcgss exportfs                3437  1 nfsd arc4                    1153  2  lib80211_crypt_wep      2667  1  iptable_filter          1369  0  iptable_nat             3543  0  nf_nat                 15560  1 iptable_nat nf_conntrack_ipv4      10346  3 iptable_nat,nf_nat autofs4                22715  2  nf_conntrack           60943  3 iptable_nat,nf_nat,nf_conntrack_ipv4 nf_defrag_ipv4          1073  1 nf_conntrack_ipv4 ip_tables               9899  2 iptable_filter,iptable_nat hostap_cs              48580  3  x_tables               14175  2 iptable_nat,ip_tables hostap                 99846  1 hostap_cs lib80211                5046  3 lib80211_crypt_wep,hostap_cs,hostap pcmcia                 30912  1 hostap_cs lm80                   10573  0  yenta_socket           20536  3  rsrc_nonstatic         10559  1 yenta_socket ppdev                   5259  0  via686a                11082  0  via_agp                 5310  1  lp                      7028  0  serio_raw               3978  0  pcmcia_core            32996  4 hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic i2c_viapro              5637  0  parport_pc             26250  1  shpchp                 28899  0  agpgart                31788  1 via_agp parport                32635  3 ppdev,lp,parport_pc 8139too                18673  0  8139cp                 16602  0  e100                   28563  0  pata_via                7272  3  mii                     4381  3 8139too,8139cp,e100
```

```
[B]lsmod | grep "wlan_module_name"
This shows nothing?
[/B]
```

```
**dmesg** [    0.000000] Initializing cgroup subsys cpuset [    0.000000] Initializing cgroup subsys cpu [    0.000000] Linux version 2.6.32-32-generic-pae (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #62-Ubuntu SMP Wed Apr 20 22:10:33 UTC 2011 (Ubuntu 2.6.32-32.62-generic-pae 2.6.32.38+drm33.16) [    0.000000] KERNEL supported cpus: [    0.000000]   Intel GenuineIntel [    0.000000]   AMD AuthenticAMD [    0.000000]   NSC Geode by NSC [    0.000000]   Cyrix CyrixInstead [    0.000000]   Centaur CentaurHauls [    0.000000]   Transmeta GenuineTMx86 [    0.000000]   Transmeta TransmetaCPU [    0.000000]   UMC UMC UMC UMC [    0.000000] BIOS-provided physical RAM map: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable) [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable) [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved) [    0.000000] DMI 2.2 present. [    0.000000] last_pfn = 0x20000 max_arch_pfn = 0x1000000 [    0.000000] MTRR default type: uncachable [    0.000000] MTRR fixed ranges enabled: [    0.000000]   00000-9FFFF write-back [    0.000000]   A0000-FFFFF uncachable [    0.000000] MTRR variable ranges enabled: [    0.000000]   0 base 000000000 mask FE0000000 write-back [    0.000000]   1 base 0D0000000 mask FFC000000 write-combining [    0.000000]   2 disabled [    0.000000]   3 disabled [    0.000000]   4 disabled [    0.000000]   5 disabled [    0.000000]   6 disabled [    0.000000]   7 disabled [    0.000000] PAT not supported by CPU. [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved) [    0.000000] Scanning 1 areas for low memory corruption [    0.000000] modified physical RAM map: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable) [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved) [    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable) [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved) [    0.000000]  modified: 0000000000100000 - 0000000020000000 (usable) [    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved) [    0.000000] initial memory mapped : 0 - 00e00000 [    0.000000] init_memory_mapping: 0000000000000000-0000000020000000 [    0.000000] Using x86 segment limits to approximate NX protection [    0.000000]  0000000000 - 0000200000 page 4k [    0.000000]  0000200000 - 0020000000 page 2M [    0.000000] kernel direct mapping tables up to 20000000 @ 7000-c000 [    0.000000] RAMDISK: 177f2000 - 1803f504 [    0.000000] ACPI Error: A valid RSDP was not found (20090903/tbxfroot-219) [    0.000000] 0MB HIGHMEM available. [    0.000000] 512MB LOWMEM available. [    0.000000]   mapped low ram: 0 - 20000000 [    0.000000]   low ram: 0 - 20000000 [    0.000000]   node 0 low ram: 00000000 - 20000000 [    0.000000]   node 0 bootmap 00008000 - 0000c000 [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0020000000] [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000] [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000] [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000] [    0.000000]   #3 [0000100000 - 0000936838]    TEXT DATA BSS ==> [0000100000 - 0000936838] [    0.000000]   #4 [00177f2000 - 001803f504]          RAMDISK ==> [00177f2000 - 001803f504] [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000] [    0.000000]   #6 [0000937000 - 000093e0be]              BRK ==> [0000937000 - 000093e0be] [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000] [    0.000000]   #8 [0000008000 - 000000c000]          BOOTMAP ==> [0000008000 - 000000c000] [    0.000000] Zone PFN ranges: [    0.000000]   DMA      0x00000000 -> 0x00001000 [    0.000000]   Normal   0x00001000 -> 0x00020000 [    0.000000]   HighMem  0x00020000 -> 0x00020000 [    0.000000] Movable zone start PFN for each node [    0.000000] early_node_map[3] active PFN ranges [    0.000000]     0: 0x00000000 -> 0x00000002 [    0.000000]     0: 0x00000006 -> 0x000000a0 [    0.000000]     0: 0x00000100 -> 0x00020000 [    0.000000] On node 0 totalpages: 130972 [    0.000000] free_area_init_node: node 0, pgdat c07d6dc0, node_mem_map c1001000 [    0.000000]   DMA zone: 32 pages used for memmap [    0.000000]   DMA zone: 0 pages reserved [    0.000000]   DMA zone: 3964 pages, LIFO batch:0 [    0.000000]   Normal zone: 992 pages used for memmap [    0.000000]   Normal zone: 125984 pages, LIFO batch:31 [    0.000000] Using APIC driver default [    0.000000] SFI: Simple Firmware Interface v0.7 http://simplefirmware.org [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic" [    0.000000] APIC: disable apic facility [    0.000000] nr_irqs_gsi: 16 [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000 [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000 [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000 [    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dfff0000) [    0.000000] Booting paravirtualized kernel on bare hardware [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1 [    0.000000] PERCPU: Embedded 15 pages/cpu @c1600000 s39736 r0 d21704 u2097152 [    0.000000] pcpu-alloc: s39736 r0 d21704 u2097152 alloc=1*2097152 [    0.000000] pcpu-alloc: [0] 0  [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129948 [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-32-generic-pae root=/dev/mapper/magnia-root ro quiet [    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes) [    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) [    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) [    0.000000] Enabling fast FPU save and restore... done. [    0.000000] Enabling unmasked SIMD FPU exception support... done. [    0.000000] Initializing CPU#0 [    0.000000] allocated 2621440 bytes of page_cgroup [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups [    0.000000] Initializing HighMem for node 0 (00000000:00000000) [    0.000000] Memory: 499408k/524288k available (4827k kernel code, 24112k reserved, 2217k data, 684k init, 0k highmem) [    0.000000] virtual kernel memory layout: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB) [    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB) [    0.000000]     vmalloc : 0xe0800000 - 0xff9fe000   ( 497 MB) [    0.000000]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB) [    0.000000]       .init : 0xc07e2000 - 0xc088d000   ( 684 kB) [    0.000000]       .data : 0xc05b6fbf - 0xc07e1748   (2217 kB) [    0.000000]       .text : 0xc0100000 - 0xc05b6fbf   (4827 kB) [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok. [    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1 [    0.000000] Hierarchical RCU implementation. [    0.000000] NR_IRQS:2304 nr_irqs:256 [    0.000000] Console: colour dummy device 80x25 [    0.000000] console [tty0] enabled [    0.000000] Fast TSC calibration using PIT [    0.000000] Detected 568.639 MHz processor. [    0.008016] Calibrating delay loop (skipped), value calculated using timer frequency.. 1137.27 BogoMIPS (lpj=2274556) [    0.008104] Security Framework initialized [    0.008228] AppArmor: AppArmor initialized [    0.008265] Mount-cache hash table entries: 512 [    0.008835] Initializing cgroup subsys ns [    0.008855] Initializing cgroup subsys cpuacct [    0.008875] Initializing cgroup subsys memory [    0.008917] Initializing cgroup subsys devices [    0.008930] Initializing cgroup subsys freezer [    0.008941] Initializing cgroup subsys net_cls [    0.009042] CPU: L1 I cache: 16K, L1 D cache: 16K [    0.009057] CPU: L2 cache: 128K [    0.009079] mce: CPU supports 5 MCE banks [    0.009144] Performance Events:  [    0.009156] no APIC, boot with the "lapic" boot parameter to force-enable it. [    0.009167] no hardware sampling interrupt available. [    0.009176] p6 PMU driver. [    0.009189] ... version:                0 [    0.009198] ... bit width:              32 [    0.009207] ... generic registers:      2 [    0.009217] ... value mask:             00000000ffffffff [    0.009228] ... max period:             000000007fffffff [    0.009237] ... fixed-purpose events:   0 [    0.009246] ... event mask:             0000000000000003 [    0.009267] Checking 'hlt' instruction... OK. [    0.026151] SMP alternatives: switching to UP code [    0.055541] Freeing SMP alternatives: 19k freed [    0.055636] ftrace: converting mcount calls to 0f 1f 44 00 00 [    0.055680] ftrace: allocating 22354 entries in 44 pages [    0.060498] Enabling APIC mode:  Flat.  Using 0 I/O APICs [    0.060522] weird, boot CPU (#0) not listed by the BIOS. [    0.060532] SMP motherboard not detected. [    0.060545] Local APIC not detected. Using dummy APIC emulation. [    0.060554] SMP disabled [    0.061502] Brought up 1 CPUs [    0.061528] Total of 1 processors activated (1137.27 BogoMIPS). [    0.061619] CPU0 attaching NULL sched-domain. [    0.062671] devtmpfs: initialized [    0.065943] regulator: core version 0.5 [    0.066007] Time: 23:51:55  Date: 06/30/11 [    0.066284] NET: Registered protocol family 16 [    0.066887] EISA bus registered [    0.100470] PCI: PCI BIOS revision 2.10 entry at 0xfb360, last bus=2 [    0.100483] PCI: Using configuration type 1 for base access [    0.105352] bio: create slab <bio-0> at 0 [    0.105800] ACPI: Interpreter disabled. [    0.106099] vgaarb: loaded [    0.106683] SCSI subsystem initialized [    0.107084] libata version 3.00 loaded. [    0.107609] usbcore: registered new interface driver usbfs [    0.107694] usbcore: registered new interface driver hub [    0.107908] usbcore: registered new device driver usb [    0.108715] PCI: Probing PCI hardware [    0.108732] PCI: Probing PCI hardware (bus 00) [    0.108905] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xd0000000-0xd3ffffff] [    0.109072] pci 0000:00:01.0: supports D1 [    0.109272] pci 0000:00:07.1: reg 20 io port: [0xc000-0xc00f] [    0.109431] pci 0000:00:07.4: quirk: region 6000-607f claimed by vt82c686 HW-mon [    0.109447] pci 0000:00:07.4: quirk: region 5000-500f claimed by vt82c686 SMB [    0.109534] pci 0000:00:08.0: reg 10 io port: [0xcc00-0xccff] [    0.109554] pci 0000:00:08.0: reg 14 32bit mmio: [0xd5020000-0xd50200ff] [    0.109618] pci 0000:00:08.0: supports D1 D2 [    0.109630] pci 0000:00:08.0: PME# supported from D1 D2 D3hot D3cold [    0.109644] pci 0000:00:08.0: PME# disabled [    0.109719] pci 0000:00:09.0: reg 10 32bit mmio: [0xd5021000-0xd5021fff] [    0.109738] pci 0000:00:09.0: reg 14 io port: [0xd000-0xd03f] [    0.109757] pci 0000:00:09.0: reg 18 32bit mmio: [0xd5000000-0xd501ffff] [    0.109793] pci 0000:00:09.0: reg 30 32bit mmio pref: [0x000000-0x00ffff] [    0.109827] pci 0000:00:09.0: supports D1 D2 [    0.109838] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold [    0.109852] pci 0000:00:09.0: PME# disabled [    0.109913] pci 0000:00:0a.0: reg 10 32bit mmio: [0xd5022000-0xd50220ff] [    0.109932] pci 0000:00:0a.0: reg 14 io port: [0xd400-0xd407] [    0.109950] pci 0000:00:0a.0: reg 18 io port: [0xd800-0xd8ff] [    0.110009] pci 0000:00:0a.0: PME# supported from D3hot D3cold [    0.110022] pci 0000:00:0a.0: PME# disabled [    0.110085] pci 0000:00:0b.0: reg 10 32bit mmio: [0xd5023000-0xd5023fff] [    0.110120] pci 0000:00:0b.0: supports D1 D2 [    0.110130] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold [    0.110144] pci 0000:00:0b.0: PME# disabled [    0.111947] pci 0000:00:07.0: VIA IRQ router [1106:0686] [    0.112657] NetLabel: Initializing [    0.112671] NetLabel:  domain hash size = 128 [    0.112679] NetLabel:  protocols = UNLABELED CIPSOv4 [    0.112741] NetLabel:  unlabeled traffic allowed by default [    0.112997] Switching to clocksource tsc [    0.121105] AppArmor: AppArmor Filesystem Enabled [    0.121138] pnp: PnP ACPI: disabled [    0.121156] PnPBIOS: Scanning system for PnP BIOS support... [    0.121718] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbda0 [    0.121740] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbdd0, dseg 0xf0000 [    0.125665] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver [    0.125740] system 00:07: iomem range 0x0-0x9ffff could not be reserved [    0.125760] system 00:07: iomem range 0xfffffffffffe0000-0xffffffffffffffff has been reserved [    0.125777] system 00:07: iomem range 0xfffffffffee00000-0xfffffffffee0ffff has been reserved [    0.125793] system 00:07: iomem range 0x100000-0x1fffffff could not be reserved [    0.125820] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved [    0.125835] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved [    0.125849] system 00:08: iomem range 0xf8000-0xfffff could not be reserved [    0.125863] system 00:08: iomem range 0xd3000-0xd3fff has been reserved [    0.126936] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01 [    0.126952] pci 0000:00:01.0:   IO window: disabled [    0.126967] pci 0000:00:01.0:   MEM window: disabled [    0.126979] pci 0000:00:01.0:   PREFETCH window: disabled [    0.126998] pci 0000:00:0b.0: CardBus bridge, secondary bus 0000:02 [    0.127011] pci 0000:00:0b.0:   IO window: 0x001000-0x0010ff [    0.127026] pci 0000:00:0b.0:   IO window: 0x001400-0x0014ff [    0.127041] pci 0000:00:0b.0:   PREFETCH window: 0x20000000-0x23ffffff [    0.127055] pci 0000:00:0b.0:   MEM window: 0x24000000-0x27ffffff [    0.127092] pci 0000:00:01.0: setting latency timer to 64 [    0.127123] PCI: setting IRQ 12 as level-triggered [    0.127136] pci 0000:00:0b.0: found PCI INT A -> IRQ 12 [    0.127197] pci_bus 0000:00: resource 0 io:  [0x00-0xffff] [    0.127211] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff] [    0.127225] pci_bus 0000:02: resource 0 io:  [0x1000-0x10ff] [    0.127237] pci_bus 0000:02: resource 1 io:  [0x1400-0x14ff] [    0.127249] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x23ffffff] [    0.127262] pci_bus 0000:02: resource 3 mem: [0x24000000-0x27ffffff] [    0.127452] NET: Registered protocol family 2 [    0.127925] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) [    0.129393] TCP established hash table entries: 16384 (order: 5, 131072 bytes) [    0.129986] TCP bind hash table entries: 16384 (order: 5, 131072 bytes) [    0.131004] TCP: Hash tables configured (established 16384 bind 16384) [    0.131029] TCP reno registered [    0.131632] NET: Registered protocol family 1 [    0.131747] pci 0000:00:01.0: disabling DAC on VIA PCI bridge [    0.131770] pci 0000:00:07.0: Disabling VIA external APIC routing [    0.131905] pci 0000:00:09.0: Firmware left e100 interrupts enabled; disabling [    0.132687] cpufreq-nforce2: No nForce2 chipset. [    0.132822] Scanning for low memory corruption every 60 seconds [    0.133568] audit: initializing netlink socket (disabled) [    0.133639] type=2000 audit(1309477915.130:1): initialized [    0.173293] Trying to unpack rootfs image as initramfs... [    0.215878] HugeTLB registered 2 MB page size, pre-allocated 0 pages [    0.231790] VFS: Disk quotas dquot_6.5.2 [    0.232304] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) [    0.239925] fuse init (API version 7.13) [    0.240624] msgmni has been set to 976 [    0.247686] alg: No test for stdrng (krng) [    0.248145] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) [    0.248166] io scheduler noop registered [    0.248175] io scheduler anticipatory registered [    0.248184] io scheduler deadline registered [    0.248431] io scheduler cfq registered (default) [    0.248934] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 [    0.249044] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 [    0.254957] isapnp: Scanning for PnP cards... [    0.268168] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled [    0.268440] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A [    0.268744] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A [    0.270177] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A [    0.270761] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A [    0.330079] brd: module loaded [    0.337598] loop: module loaded [    0.338219] input: Macintosh mouse button emulation as /devices/virtual/input/input0 [    0.340931] Fixed MDIO Bus: probed [    0.341116] PPP generic driver version 2.4.2 [    0.341422] tun: Universal TUN/TAP device driver, 1.6 [    0.341435] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> [    0.342068] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver [    0.342172] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver [    0.342232] uhci_hcd: USB Universal Host Controller Interface driver [    0.347571] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1 [    0.347591] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp [    0.348065] serio: i8042 KBD port at 0x60,0x64 irq 1 [    0.348888] mice: PS/2 mouse device common for all mice [    0.355257] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 [    0.355332] rtc0: alarms up to one day, 114 bytes nvram [    0.355857] device-mapper: uevent: version 1.0.3 [    0.356721] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com [    0.357206] device-mapper: multipath: version 1.1.0 loaded [    0.357221] device-mapper: multipath round-robin: version 1.0.0 loaded [    0.363819] EISA: Probing bus 0 at eisa.0 [    0.363855] Cannot allocate resource for EISA slot 1 [    0.363890] Cannot allocate resource for EISA slot 5 [    0.363901] Cannot allocate resource for EISA slot 6 [    0.363926] EISA: Detected 0 cards. [    0.364416] cpuidle: using governor ladder [    0.364430] cpuidle: using governor menu [    0.366603] TCP cubic registered [    0.367610] NET: Registered protocol family 10 [    0.369932] lo: Disabled Privacy Extensions [    0.376329] NET: Registered protocol family 17 [    0.376642] Using IPI No-Shortcut mode [    0.377155] PM: Resume from disk failed. [    0.377267] registered taskstats version 1 [    0.377845]   Magic number: 15:36:910 [    0.378066] rtc_cmos 00:03: setting system clock to 2011-06-30 23:51:55 UTC (1309477915) [    0.378082] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found [    0.378090] EDD information not available. [    0.958600] isapnp: No Plug & Play device found [    1.731572] Freeing initrd memory: 8501k freed [    1.772180] Freeing unused kernel memory: 684k freed [    1.775963] Write protecting the kernel text: 4828k [    1.776275] Write protecting the kernel read-only data: 1884k [    1.899350] udev: starting version 151 [    2.516400] pata_via 0000:00:07.1: version 0.3.4 [    2.523970] scsi0 : pata_via [    2.530361] scsi1 : pata_via [    2.531337] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xc000 irq 14 [    2.531355] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xc008 irq 15 [    2.617371] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI [    2.617392] e100: Copyright(c) 1999-2006 Intel Corporation [    2.617549] PCI: setting IRQ 11 as level-triggered [    2.617565] e100 0000:00:09.0: found PCI INT A -> IRQ 11 [    2.703576] e100 0000:00:09.0: PME# disabled [    2.759451] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) [    2.763135] e100: eth0: e100_probe: addr 0xd5021000, irq 11, MAC addr 00:10:c6:18:7b:e4 [    2.763272] 8139cp 0000:00:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too [    3.167443] ata1.00: ATA-5: TOSHIBA MK3017GAP, A0.02 H, max UDMA/100 [    3.167462] ata1.00: 58605120 sectors, multi 16: LBA  [    3.167772] ata1.01: ATA-6: ST920217A, 3.01, max UDMA/100 [    3.167787] ata1.01: 39070080 sectors, multi 16: LBA48  [    3.175482] ata1.00: configured for UDMA/100 [    3.183485] ata1.01: configured for UDMA/100 [    3.184097] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3017GA A0.0 PQ: 0 ANSI: 5 [    3.184960] sd 0:0:0:0: Attached scsi generic sg0 type 0 [    3.187070] scsi 0:0:1:0: Direct-Access     ATA      ST920217A        3.01 PQ: 0 ANSI: 5 [    3.189902] sd 0:0:1:0: Attached scsi generic sg1 type 0 [    3.190834] sd 0:0:0:0: [sda] 58605120 512-byte logical blocks: (30.0 GB/27.9 GiB) [    3.191325] ata2: port disabled. ignoring. [    3.191782] sd 0:0:1:0: [sdb] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB) [    3.191876] sd 0:0:0:0: [sda] Write Protect is off [    3.191892] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 [    3.192188] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA [    3.192742] sd 0:0:1:0: [sdb] Write Protect is off [    3.192761] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00 [    3.192906] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA [    3.194227]  sda: [    3.601129]  sdb: sda1 sda2 < sdb1 [    3.653088]  sda5 > [    3.657197] sd 0:0:1:0: [sdb] Attached SCSI disk [    3.657645] sd 0:0:0:0: [sda] Attached SCSI disk [    3.734134] 8139too Fast Ethernet driver 0.9.28 [    3.734330] PCI: setting IRQ 10 as level-triggered [    3.734345] 8139too 0000:00:08.0: found PCI INT A -> IRQ 10 [    3.738470] eth1: RealTek RTL8139 at 0xcc00, 00:10:c6:18:6d:e0, IRQ 10 [    5.117155] kjournald starting.  Commit interval 5 seconds [    5.117242] EXT3-fs: mounted filesystem with ordered data mode. [   30.224359] Adding 1241080k swap on /dev/mapper/magnia-swap_1.  Priority:-1 extents:1 across:1241080k  [   30.321235] EXT3 FS on dm-0, internal journal [   30.400147] udev: starting version 151 [   31.312073] udev: renamed network interface eth0 to eth1 [   31.324784] udev: renamed network interface eth1_rename to eth0 [   32.034513] Linux agpgart interface v0.103 [   32.205281] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 [   32.303626] parport_pc: VIA 686A/8231 detected [   32.303647] parport_pc: probing current configuration [   32.303678] parport_pc: Current parallel port base: 0x378 [   32.303752] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP] [   32.401764] parport_pc: VIA parallel port: io=0x378, irq=7 [   32.647216] type=1505 audit(1309477947.767:2):  operation="profile_load" pid=390 name="/usr/sbin/ntpd" [   32.680379] type=1505 audit(1309477947.799:3):  operation="profile_replace" pid=395 name="/usr/sbin/ntpd" [   32.756227] lp0: using parport0 (interrupt-driven). [   32.853947] agpgart: Detected VIA Apollo Pro 133 chipset [   32.893524] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xd0000000 [   33.007000] ppdev: user-space parallel port driver [   33.153126] yenta_cardbus 0000:00:0b.0: CardBus bridge found [3412:7856] [   33.153175] yenta_cardbus 0000:00:0b.0: O2: res at 0x94/0xD4: 00/ea [   33.153186] yenta_cardbus 0000:00:0b.0: O2: enabling read prefetch/write burst [   33.217615] i2c i2c-0: Transaction error! [   33.278553] yenta_cardbus 0000:00:0b.0: ISA IRQ mask 0x0200, PCI irq 12 [   33.278573] yenta_cardbus 0000:00:0b.0: Socket status: 30000411 [   33.550387] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 [   33.933611] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0 [   33.992234] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean. [   33.995218] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 [   33.996468] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean. [   34.013826] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean. [   34.015652] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean. [   34.016867] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean. [   34.202523] pcmcia 0.0: pcmcia: registering new device pcmcia0.0 [   34.396505] lib80211: common routines for IEEE802.11 drivers [   34.396529] lib80211_crypt: registered algorithm 'NULL' [   34.621742] kjournald starting.  Commit interval 5 seconds [   34.621818] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended [   34.622341] EXT3 FS on sdb1, internal journal [   34.622371] EXT3-fs: mounted filesystem with ordered data mode. [   35.258335] hostap_cs: setting Vcc=33 (constant) [   35.258449] Checking CFTABLE_ENTRY 0x01 (default 0x01) [   35.258460] IO window settings: cfg->io.nwin=1 dflt->io.nwin=1 [   35.258473] io->flags = 0x0046, io.base=0x0000, len=64 [   35.318786] hostap_cs: Registered netdevice wifi0 [   35.358730] hostap_cs: index 0x01: , irq 9, io 0x0100-0x013f [   35.573504] ip_tables: (C) 2000-2006 Netfilter Core Team [   35.644065] prism2_hw_init: initialized in 284 ms [   35.653793] wifi0: NIC: id=0x800c v1.0.0 [   35.657766] wifi0: PRI: id=0x15 v1.0.7 [   35.660227] wifi0: STA: id=0x1f v1.3.6 [   35.664264] wifi0: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS [   35.697739] wifi0: registered netdevice wlan0 [   36.802638] nf_conntrack version 0.5.0 (7952 buckets, 31808 max) [   36.820990] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use [   36.821016] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or [   36.821026] sysctl net.netfilter.nf_conntrack_acct=1 to enable it. [   37.885657] prism2: wlan0: operating mode changed 2 -> 3 [   37.885676] wlan0: defaulting to host-based encryption as a workaround for firmware bug in Host AP mode WEP [   38.017230] lib80211_crypt: registered algorithm 'WEP' [   38.584116] type=1505 audit(1309477991.600:4):  operation="profile_load" pid=904 name="/usr/sbin/named" [   38.740822] type=1505 audit(1309477991.756:5):  operation="profile_replace" pid=920 name="/usr/sbin/ntpd" [   38.818770] type=1505 audit(1309477991.836:6):  operation="profile_load" pid=937 name="/usr/sbin/tcpdump" [   44.526874] eth0: no IPv6 routers present [   46.402847] device eth0 entered promiscuous mode [   48.815891] RPC: Registered udp transport module. [   48.815911] RPC: Registered tcp transport module. [   48.815920] RPC: Registered tcp NFSv4.1 backchannel transport module. [   49.519700] wlan0: no IPv6 routers present [   50.072874] Installing knfsd (copyright (C) 1996 okir@monad.swb.de). [   52.156773] svc: failed to register lockdv1 RPC service (errno 97). [   52.194144] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory [   52.221049] NFSD: starting 90-second grace period [   58.258734] type=1505 audit(1309478011.275:7):  operation="profile_replace" pid=2417 name="/usr/sbin/named" [   58.315871] type=1505 audit(1309478011.331:8):  operation="profile_replace" pid=2420 name="/usr/sbin/ntpd" [   58.390554] type=1505 audit(1309478011.407:9):  operation="profile_replace" pid=2423 name="/usr/sbin/tcpdump" [  119.890709] aoe: AoE v47 initialised. [  119.890873] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2) [  179.897230] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2) [  239.907157] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2) [  299.917032] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2) [  359.926934] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
```

```
**lshw -C network**   *-network:0        description: Ethernet interface        product: RTL-8139/8139C/8139C+        vendor: Realtek Semiconductor Co., Ltd.        physical id: 8        bus info: pci@0000:00:08.0        logical name: eth0        version: 10        serial: 00:10:c6:18:6d:e0        size: 100MB/s        capacity: 100MB/s        width: 32 bits        clock: 33MHz        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.2 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s        resources: irq:10 ioport:cc00(size=256) memory:d5020000-d50200ff   *-network:1 DISABLED        description: Ethernet interface        product: 82557/8/9/0/1 Ethernet Pro 100        vendor: Intel Corporation        physical id: 9        bus info: pci@0000:00:09.0        logical name: eth1        version: 0d        serial: 00:10:c6:18:7b:e4        size: 10MB/s        capacity: 100MB/s        width: 32 bits        clock: 33MHz        capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s        resources: irq:11 memory:d5021000-d5021fff ioport:d000(size=64) memory:d5000000-d501ffff memory:28000000-2800ffff(prefetchable)   *-network        description: Card        product: ISL37300P        vendor: NETGEAR MA401RA Wireless PC        physical id: 0        version: Eval-RevA        slot: Socket 0        resources: irq:9   *-network        description: Wireless interface        physical id: 1        logical name: wlan0        serial: 00:09:5b:3b:1f:d5        capabilities: ethernet physical wireless        configuration: broadcast=yes driver=hostap firmware=1.3.6 ip=192.168.2.55 multicast=yes wireless=IEEE 802.11b
```

```
**iwlist scan** lo        Interface doesn't support scanning.  eth1      Interface doesn't support scanning.  eth0      Interface doesn't support scanning.  wifi0     No scan results  wlan0     No scan results
```

```
**uname -mr** 2.6.32-32-generic-pae i686
```

If there are any other codes needed please let me know!

Thank you!!!

---

### Post by nm_geo on 2011-06-30
Wow that one long code stuff is too difficult for me to wade through, how did you fo that..  But you have a wireless driver installed.  Just do a lsmod copy and paste ..

wlan0     IEEE 802.11b  ESSID:"MyTinyTown_B"  
Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5 
Bit Rate:11 Mb/s   Sensitivity=1/3    Retry short limit:8   RTS thr:off   Fragment thr:off
Encryption key:****-****-****-****-****-****-**     Security mode:restricted  
Power Management:off 
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:15   Missed beacon:0

It appears you are getting to you wireless Access Point. You might check from there out.

---

### Post by mytinytown on 2011-07-01
```
lsmod
Module                  Size  Used by
aoe                    22485  0
nfsd                  238874  11
lockd                  64849  1 nfsd
nfs_acl                 2245  1 nfsd
auth_rpcgss            33767  1 nfsd
sunrpc                193085  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3437  1 nfsd
arc4                    1153  2
lib80211_crypt_wep      2667  1
iptable_filter          1369  0
iptable_nat             3543  0
nf_nat                 15560  1 iptable_nat
nf_conntrack_ipv4      10346  3 iptable_nat,nf_nat
autofs4                22715  2
nf_conntrack           60943  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9899  2 iptable_filter,iptable_nat
hostap_cs              48580  3
x_tables               14175  2 iptable_nat,ip_tables
hostap                 99846  1 hostap_cs
lib80211                5046  3 lib80211_crypt_wep,hostap_cs,hostap
pcmcia                 30912  1 hostap_cs
lm80                   10573  0
yenta_socket           20536  3
rsrc_nonstatic         10559  1 yenta_socket
via686a                11082  0
via_agp                 5310  1
ppdev                   5259  0
lp                      7028  0
serio_raw               3978  0
pcmcia_core            32996  4 hostap_cs,pcmcia,yenta_socket,rsrc_nonstatic
i2c_viapro              5637  0
shpchp                 28899  0
agpgart                31788  1 via_agp
parport_pc             26250  1
parport                32635  3 ppdev,lp,parport_pc
8139too                18673  0
8139cp                 16602  0
e100                   28563  0
mii                     4381  3 8139too,8139cp,e100
pata_via                7272  3

```But none of the ports (eth0, eth1 or wlan0) have internet access. I can access from the network, but not internet. I do have it set up as an access point right now, I also had it set up with a bridge and was having internet issues with the bridge and no one offered help, so I removed the bridge to see if I can set it up that way and I am having similar issues.

As well I have no clue how or why the codes came up as a single line either. I will repost them all.

If there is anything else you need, please let me know. Thank you!

Edit:
I just connected to my server as an access point and my laptop has internet access, but the server does not. I have a feeling it may not be the network now? So how could a computer connected to the server have internet, but the server does not have internet?

Maybe this will narrow down the issues???

New Edit:
This laptop decided to dump the access pint and jump back to my router and I did not see this, so the mytinytown_b access point does not give internet or network connection.
Sorry for the confusion!

---

### Post by mytinytown on 2011-07-01
```
lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller

``````
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:c6:18:6d:e0
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::210:c6ff:fe18:6de0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9373689 (9.3 MB)  TX bytes:2354473 (2.3 MB)
          Interrupt:10 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2201976 (2.2 MB)  TX bytes:2201976 (2.2 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-09-5B-3B-1F-D5-30-30-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x100

wlan0     Link encap:Ethernet  HWaddr 00:09:5b:3b:1f:d5
          inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe3b:1fd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0x100

``````
iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"MyTinyTown_B"
          Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:"MyTinyTown_B"
          Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:15  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:1939   Missed beacon:0

``````
dmesg
[33074.659336] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33134.669542] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33194.679753] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33254.689987] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33314.700186] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33374.710388] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33434.720628] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33494.730848] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33554.741067] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33614.751258] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33674.761497] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33734.771699] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33794.781948] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33854.792160] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33914.802349] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[33974.812604] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34034.822802] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34094.833039] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34154.843245] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34214.853475] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34274.863694] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34334.873885] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34394.884108] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34454.894352] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34514.904544] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34574.914767] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34634.924976] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34694.935203] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34754.945416] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34814.955631] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34874.965892] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34934.976101] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[34994.986325] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35054.996540] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35115.006744] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35175.016969] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35235.027191] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35295.037467] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35355.047604] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35415.057815] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35475.068053] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35535.078266] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35595.088508] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35655.098725] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35715.108936] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35775.119162] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35835.129376] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35895.139607] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[35955.149786] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36015.160015] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36075.170249] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36135.180447] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36195.190659] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36255.200881] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36315.211132] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36375.221346] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36435.231565] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36495.241758] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36555.251981] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36615.262199] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36675.272457] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36735.282640] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36795.292860] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36855.303097] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36915.313290] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[36975.323509] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37035.333752] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37095.343952] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37155.354166] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37215.364409] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37275.374645] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37335.384844] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37395.395039] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37455.405284] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37515.415502] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37575.425718] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37635.435916] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37695.446163] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37755.456371] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37815.466575] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37875.476813] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37935.487006] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[37995.497246] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38055.507540] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38115.517674] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38175.527880] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38235.538116] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38295.548328] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38355.558563] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38415.568776] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38475.579013] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38535.589217] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38595.599451] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38655.609635] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38715.619870] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38775.630087] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38835.640301] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38895.650632] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[38955.660743] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39015.670960] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39075.681184] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39135.691399] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39195.701620] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39255.711857] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39315.722036] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39375.732253] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39435.742466] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39495.752688] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39555.762943] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39615.773129] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39675.783347] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39735.793564] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39795.803787] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39855.814006] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39915.824261] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[39975.834445] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40035.844682] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40095.854901] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40155.865117] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40215.875323] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40275.885558] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40335.895745] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40395.905968] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40455.916217] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40515.926411] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40575.936646] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40635.946866] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40695.957091] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40755.967285] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40815.977527] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40875.987752] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40935.997961] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[40996.008151] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41056.018390] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41116.028616] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41176.038824] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41236.049025] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41296.059257] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41356.069478] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41416.079687] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41476.089936] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41536.100168] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41596.110354] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41656.120622] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41716.130800] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41776.140996] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41836.151220] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41896.161456] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[41956.171834] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42016.181907] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42076.192142] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42136.202344] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42196.212579] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42256.222866] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42316.233021] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42376.243189] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42436.253407] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42496.263632] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42556.273861] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42616.284077] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42676.294311] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42736.304501] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42796.314729] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42856.324970] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42916.335166] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[42976.345402] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43036.355627] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43096.365865] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43156.376029] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43216.386257] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43276.396498] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43336.406706] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43396.416913] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43456.427129] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43516.437350] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43576.447570] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43636.457782] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43696.467999] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43756.478221] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43816.488435] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43876.498655] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43936.508901] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[43996.519094] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44056.529345] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44116.539554] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44176.549757] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44236.559969] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44296.570193] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44356.580404] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44416.590609] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44476.600867] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44536.611047] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44596.621280] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44656.631518] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44716.641746] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44776.651968] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44836.662184] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44896.672393] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[44956.682625] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45016.692815] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45076.703032] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45136.713249] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45196.723472] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45256.733765] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45316.743905] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45376.754145] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45436.764345] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45496.774560] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45556.784783] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45616.794990] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45676.805217] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45736.815446] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45796.825650] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45856.835869] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45916.846096] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[45976.856341] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46036.866536] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46096.876782] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46156.886988] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46216.897182] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46276.907425] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46336.917614] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46396.927827] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46456.938082] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46516.948284] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46576.958494] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46636.968737] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46696.978955] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46756.989185] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46816.999423] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46877.009586] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46937.019804] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[46997.030023] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47057.040275] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47117.050481] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47177.060710] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47237.070927] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47297.081125] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47357.091342] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47417.101561] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47477.111783] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47537.122003] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[47597.132222] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)

This is all I could get from puTTy, I used Webmin last time, this could be why it singled lined itself.

``````
lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 10
       serial: 00:10:c6:18:6d:e0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.2 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:10 ioport:cc00(size=256) memory:d5020000-d50200ff
  *-network:1 DISABLED
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 0d
       serial: 00:10:c6:18:7b:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:d5021000-d5021fff ioport:d000(size=64) memory:d5000000-d501ffff memory:28000000-2800ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:09:5b:3b:1f:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap firmware=1.3.6 ip=192.168.2.55 multicast=yes wireless=IEEE 802.11b

```

---

### Post by collisionystm on 2011-07-01
Can you ping 8.8.8.8 ?

---

### Post by mytinytown on 2011-07-01
```
 ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

```

Never made it past that point.

---

### Post by MooPi on 2011-07-01
From what I can see you have two connections in iwconfig for the same device. Which one if any did you manually set, wifi0 or wlan0 ? It may be as simple as removing one from the network manager config.
If you didn't set either could you run this command from terminal
```
rfkill list
``` This should let us know if your device is active or switched off.

---

### Post by mytinytown on 2011-07-01
I read the the wifi0 is the "main" port and the wlan0 is the virtual port and this is the way it works. I did not set it up that way. Not sure if it is right though.

```
 rfkill list

```
Gives me a new line like it did nothing?

---

### Post by mytinytown on 2011-07-01
OK I changed wlan0 to wifi0 in the network/interfaces file and get:
```
iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"MyTinyTown_B"
          Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off

wlan0     IEEE 802.11b  ESSID:"MyTinyTown_B"
          Mode:Master  Frequency:2.427 GHz  Access Point: 00:09:5B:3B:1F:D5
          Bit Rate:11 Mb/s   Sensitivity=1/3
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0

```

Same code and same results.

Please keep in mind, I do not have internet access from the server at all. Not even through eth0 or eth1.

Thank you :)

---

