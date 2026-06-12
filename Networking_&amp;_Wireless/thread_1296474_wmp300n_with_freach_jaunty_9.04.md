---
title: "wmp300n with freach jaunty 9.04"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by grower1331 on 2009-10-20
Just did a fresh install of Jaunty with the wmp300n wireless card. Wanting to use aircrack so ndiswrapper is not possible.Theres what I get:
$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:0a.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
01:0b.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub [8086:7124] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller [8086:7125] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02)
01:0a.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)
01:0b.0 VGA compatible controller [0300]: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] [10de:002d] (rev 15)

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:70:a8:14:97  
          inet6 addr: fe80::21a:70ff:fea8:1497/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4408 (4.4 KB)  TX bytes:4408 (4.4 KB)

$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.


$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            82880  1 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
psmouse                61972  0 
pcspkr                 10496  0 
ieee80211_crypt_tkip    16896  0 
serio_raw              13316  0 
wl                   1489748  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              34108  1 
shpchp                 40212  0 
intel_rng              12672  0 
agpgart                42696  1 intel_agp
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 00000000000e7800 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bef0000 (usable)
[    0.000000]  BIOS-e820: 000000000bef0000 - 000000000beffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000beffc00 - 000000000bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000bf00000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI not present or invalid.
[    0.000000] last_pfn = 0xbef0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e7800 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000bef0000 (usable)
[    0.000000]  modified: 000000000bef0000 - 000000000beffc00 (ACPI data)
[    0.000000]  modified: 000000000beffc00 - 000000000bf00000 (ACPI NVS)
[    0.000000]  modified: 000000000bf00000 - 000000000c000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to bef0000 @ 10000-16000
[    0.000000] RAMDISK: 0b7b1000 - 0bedf095
[    0.000000] ACPI: RSDP 000F7470, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0BEFCB89, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0BEFFB64, 0074 (r1 HP     Hawk      6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 0BEFCBB5, 2FAF (r1  INTEL  Whitney  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 0BEFFFC0, 0040
[    0.000000] ACPI: BOOT 0BEFFBD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 190MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0bef0000
[    0.000000]   low ram: 00000000 - 0bef0000
[    0.000000]   bootmap 00012000 - 000137e0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000bef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000b7b1000 - 000bedf095]          RAMDISK ==> [000b7b1000 - 000bedf095]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000bef0
[    0.000000]   HighMem  0x0000bef0 -> 0x0000bef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0000bef0
[    0.000000] On node 0 totalpages: 48757
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 350 pages used for memmap
[    0.000000]   Normal zone: 44434 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: c000000:f3f00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 48375
[    0.000000] Kernel command line: root=UUID=997fa4cd-eece-40f4-95de-6d391864f018 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: Using PIT calibration value
[    0.000000] Detected 668.137 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 977600 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 177056k/195520k available (4126k kernel code, 17828k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xcc6f0000 - 0xff3fe000   ( 813 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcbef0000   ( 190 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004028] Calibrating delay loop (skipped), value calculated using timer frequency.. 1336.27 BogoMIPS (lpj=2672548)
[    0.004101] Security Framework initialized
[    0.004133] SELinux:  Disabled at boot.
[    0.004213] AppArmor: AppArmor initialized
[    0.004243] Mount-cache hash table entries: 512
[    0.004742] Initializing cgroup subsys ns
[    0.004765] Initializing cgroup subsys cpuacct
[    0.004774] Initializing cgroup subsys memory
[    0.004789] Initializing cgroup subsys freezer
[    0.004844] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004854] CPU: L2 cache: 128K
[    0.004923] Checking 'hlt' instruction... OK.
[    0.021508] SMP alternatives: switching to UP code
[    0.616378] Freeing SMP alternatives: 18k freed
[    0.616723] weird, boot CPU (#0) not listedby the BIOS.
[    0.616736] SMP motherboard not detected.
[    0.616746] Local APIC not detected. Using dummy APIC emulation.
[    0.616753] SMP disabled
[    0.618272] Brought up 1 CPUs
[    0.618292] Total of 1 processors activated (1336.27 BogoMIPS).
[    0.618370] CPU0 attaching NULL sched-domain.
[    0.619716] net_namespace: 776 bytes
[    0.619741] Booting paravirtualized kernel on bare hardware
[    0.620777] Time: 14:25:50  Date: 01/01/88
[    0.620801] regulator: core version 0.5
[    0.620945] NET: Registered protocol family 16
[    0.621448] EISA bus registered
[    0.622722] PCI: PCI BIOS revision 2.10 entry at 0xfd99e, last bus=1
[    0.622733] PCI: Using configuration type 1 for base access
[    0.627253] ACPI: Interpreter disabled.
[    0.628136] SCSI subsystem initialized
[    0.628428] libata version 3.00 loaded.
[    0.628709] usbcore: registered new interface driver usbfs
[    0.628784] usbcore: registered new interface driver hub
[    0.628975] usbcore: registered new device driver usb
[    0.629588] PCI: Probing PCI hardware
[    0.629601] PCI: Probing PCI hardware (bus 00)
[    0.629814] pci 0000:00:01.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.629830] pci 0000:00:01.0: reg 14 32bit mmio: [0xf4000000-0xf407ffff]
[    0.630065] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.630077] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.630147] pci 0000:00:1f.1: reg 20 io port: [0x10a0-0x10af]
[    0.630255] pci 0000:00:1f.2: reg 20 io port: [0x1080-0x109f]
[    0.630346] pci 0000:00:1f.3: reg 20 io port: [0x10b0-0x10bf]
[    0.630445] pci 0000:01:0a.0: reg 10 32bit mmio: [0xf4100000-0xf4103fff]
[    0.630546] pci 0000:01:0b.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.630563] pci 0000:01:0b.0: reg 14 32bit mmio: [0xfc000000-0xfdffffff]
[    0.630606] pci 0000:01:0b.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.630670] pci 0000:00:1e.0: transparent bridge
[    0.630686] pci 0000:00:1e.0: bridge 32bit mmio: [0xf4100000-0xf5ffffff]
[    0.630700] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xfc000000-0xfdffffff]
[    0.631599] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086:2410]
[    0.632044] Bluetooth: Core ver 2.13
[    0.632351] NET: Registered protocol family 31
[    0.632360] Bluetooth: HCI device and connection manager initialized
[    0.632372] Bluetooth: HCI socket layer initialized
[    0.632381] NET: Registered protocol family 8
[    0.632387] NET: Registered protocol family 20
[    0.632438] NetLabel: Initializing
[    0.632444] NetLabel:  domain hash size = 128
[    0.632450] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.632525] NetLabel:  unlabeled traffic allowed by default
[    0.632840] AppArmor: AppArmor Filesystem Enabled
[    0.632852] pnp: PnP ACPI: disabled
[    0.632861] PnPBIOS: Scanning system for PnP BIOS support...
[    0.632958] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7490
[    0.632968] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9da9, dseg 0x400
[    0.634082] pnp 00:00: io resource (0x11b0-0x11bf) overlaps 0000:00:1f.0 BAR 8 (0x1180-0x11bf), disabling
[    0.634288] pnp 00:01: io resource (0x1000-0x105f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.634302] pnp 00:01: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.634315] pnp 00:01: io resource (0x1180-0x11af) overlaps 0000:00:1f.0 BAR 8 (0x1180-0x11bf), disabling
[    0.639390] PnPBIOS: 19 nodes reported by PnP BIOS; 19 recorded by driver
[    0.639446] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.639458] system 00:00: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.639484] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.639495] system 00:01: ioport range 0x1100-0x110f has been reserved
[    0.639519] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    0.639530] system 00:02: iomem range 0xe4000-0xfffff could not be reserved
[    0.639540] system 00:02: iomem range 0x100000-0xbfffbff could not be reserved
[    0.639569] system 00:0c: iomem range 0xe0000-0xe3fff has been reserved
[    0.640316] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.640329] pci 0000:00:1e.0:   IO window: disabled
[    0.640345] pci 0000:00:1e.0:   MEM window: 0xf4100000-0xf5ffffff
[    0.640358] pci 0000:00:1e.0:   PREFETCH window: 0x000000fc000000-0x000000fdffffff
[    0.640392] pci 0000:00:1e.0: setting latency timer to 64
[    0.640406] bus: 00 index 0 io port: [0x00-0xffff]
[    0.640414] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.640422] bus: 01 index 0 mmio: [0x0-0x0]
[    0.640429] bus: 01 index 1 mmio: [0xf4100000-0xf5ffffff]
[    0.640437] bus: 01 index 2 mmio: [0xfc000000-0xfdffffff]
[    0.640445] bus: 01 index 3 io port: [0x00-0xffff]
[    0.640452] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.640496] NET: Registered protocol family 2
[    0.641031] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.642002] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.642268] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.642535] TCP: Hash tables configured (established 8192 bind 8192)
[    0.642547] TCP reno registered
[    0.643120] NET: Registered protocol family 1
[    0.643637] checking if image is initramfs... it is
[    2.744198] Freeing initrd memory: 7352k freed
[    2.744346] Simple Boot Flag at 0x36 set to 0x1
[    2.744427] cpufreq: No nForce2 chipset.
[    2.744939] audit: initializing netlink socket (disabled)
[    2.745002] type=2000 audit(3723805551.743:1): initialized
[    2.770985] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.776396] VFS: Disk quotas dquot_6.5.1
[    2.776764] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.779607] fuse init (API version 7.10)
[    2.780119] msgmni has been set to 360
[    2.781137] alg: No test for stdrng (krng)
[    2.781221] io scheduler noop registered
[    2.781229] io scheduler anticipatory registered
[    2.781237] io scheduler deadline registered
[    2.781386] io scheduler cfq registered (default)
[    2.781517] pci 0000:01:0b.0: Boot video device
[    2.781787] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.781821] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.782183] isapnp: Scanning for PnP cards...
[    3.136462] isapnp: No Plug & Play device found
[    3.140973] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.141161] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.141337] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.142523] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.142868] 00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.146027] brd: module loaded
[    3.147480] loop: module loaded
[    3.147852] Fixed MDIO Bus: probed
[    3.147881] PPP generic driver version 2.4.2
[    3.148226] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.148371] Driver 'sd' needs updating - please use bus_type methods
[    3.148409] Driver 'sr' needs updating - please use bus_type methods
[    3.148673] ata_piix 0000:00:1f.1: version 2.12
[    3.148879] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.149285] scsi0 : ata_piix
[    3.149815] scsi1 : ata_piix
[    3.150001] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x10a0 irq 14
[    3.150012] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x10a8 irq 15
[    3.368647] ata1.00: ATA-6: ST3100011A, 3.02, max UDMA/100
[    3.368659] ata1.00: 195371568 sectors, multi 16: LBA48 
[    3.384603] ata1.00: configured for UDMA/66
[    3.564428] ata2.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P57, max UDMA/66
[    3.564510] ata2.00: limited to UDMA/33 due to 40-wire cable
[    3.596426] ata2.00: configured for UDMA/33
[    3.597601] scsi 0:0:0:0: Direct-Access     ATA      ST3100011A       3.02 PQ: 0 ANSI: 5
[    3.598127] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    3.598220] sd 0:0:0:0: [sda] Write Protect is off
[    3.598230] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.598366] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.598721] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    3.598805] sd 0:0:0:0: [sda] Write Protect is off
[    3.598815] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.598950] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.598970]  sda: sda1 sda2 < sda5 >
[    3.639339] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.639570] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.641046] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P57 PQ: 0 ANSI: 5
[    3.646826] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.646843] Uniform CD-ROM driver Revision: 3.20
[    3.647322] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.647526] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.649892] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.649979] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.650037] uhci_hcd: USB Universal Host Controller Interface driver
[    3.650236] PCI: setting IRQ 11 as level-triggered
[    3.650248] uhci_hcd 0000:00:1f.2: found PCI INT D -> IRQ 11
[    3.650293] uhci_hcd 0000:00:1f.2: sharing IRQ 11 with 0000:01:0b.0
[    3.650320] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    3.650332] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    3.650667] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    3.650734] uhci_hcd 0000:00:1f.2: irq 11, io base 0x00001080
[    3.651138] usb usb1: configuration #1 chosen from 1 choice
[    3.651281] hub 1-0:1.0: USB hub found
[    3.651324] hub 1-0:1.0: 2 ports detected
[    3.651903] usbcore: registered new interface driver libusual
[    3.652055] usbcore: registered new interface driver usbserial
[    3.652162] USB Serial support registered for generic
[    3.652213] usbcore: registered new interface driver usbserial_generic
[    3.652223] usbserial: USB Serial Driver core
[    3.652413] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    3.655472] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.655497] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.656019] mice: PS/2 mouse device common for all mice
[    3.656454] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.656505] rtc0: alarms up to one day, 114 bytes nvram
[    3.656883] device-mapper: uevent: version 1.0.3
[    3.657501] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    3.657814] device-mapper: multipath: version 1.0.5 loaded
[    3.657829] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.658342] EISA: Probing bus 0 at eisa.0
[    3.658367] Cannot allocate resource for EISA slot 1
[    3.658417] EISA: Detected 0 cards.
[    3.658617] cpuidle: using governor ladder
[    3.658627] cpuidle: using governor menu
[    3.660824] TCP cubic registered
[    3.661360] NET: Registered protocol family 10
[    3.663078] lo: Disabled Privacy Extensions
[    3.664383] NET: Registered protocol family 17
[    3.664523] Bluetooth: L2CAP ver 2.11
[    3.664530] Bluetooth: L2CAP socket layer initialized
[    3.664542] Bluetooth: SCO (Voice Link) ver 0.6
[    3.664549] Bluetooth: SCO socket layer initialized
[    3.664792] Bluetooth: RFCOMM socket layer initialized
[    3.664836] Bluetooth: RFCOMM TTY layer initialized
[    3.664843] Bluetooth: RFCOMM ver 1.10
[    3.665053] IO APIC resources could be not be allocated.
[    3.665143] Using IPI No-Shortcut mode
[    3.665501] registered taskstats version 1
[    3.665777]   Magic number: 8:904:433
[    3.665949] rtc_cmos 00:06: setting system clock to 1988-01-01 14:25:53 UTC (568045553)
[    3.665961] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.665968] EDD information not available.
[    3.669005] Freeing unused kernel memory: 532k freed
[    3.669470] Write protecting the kernel text: 4128k
[    3.669606] Write protecting the kernel read-only data: 1532k
[    3.690309] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    6.527434] PM: Starting manual resume from disk
[    6.527455] PM: Resume from partition 8:5
[    6.527461] PM: Checking hibernation image.
[    6.527906] PM: Resume from disk failed.
[    6.585692] kjournald starting.  Commit interval 5 seconds
[    6.585753] EXT3-fs: mounted filesystem with ordered data mode.
[   12.579812] udev: starting version 141
[   12.897687] Linux agpgart interface v0.103
[   12.909664] Intel 82802 RNG detected
[   12.924817] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.968748] agpgart-intel 0000:00:00.0: Intel i810 Chipset
[   12.980560] iTCO_vendor_support: vendor-support=0
[   12.990337] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.991043] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   12.991075] iTCO_wdt: No card detected
[   13.007517] pci 0000:00:01.0: detected 4MB dedicated video ram
[   13.012856] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   13.152375] ieee80211_crypt: registered algorithm 'NULL'
[   13.283436] wl: module license '' taints kernel.
[   13.330124] wl 0000:01:0a.0: enabling device (0100 -> 0102)
[   13.330157] PCI: setting IRQ 9 as level-triggered
[   13.330167] wl 0000:01:0a.0: assigned PCI INT A -> IRQ 9
[   13.602238] ieee80211_crypt: registered algorithm 'TKIP'
[   13.604789] eth0: Broadcom BCM4329 802.11 Wireless Controller 5.10.79.10
[   13.619665] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   13.739927] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.237571] psmouse serio1: ID: 10 00 64<6>input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   15.759267] lp: driver loaded but no devices found
[   16.168001] Adding 538136k swap on /dev/sda5.  Priority:-1 extents:1 across:538136k
[   16.858090] EXT3 FS on sda1, internal journal
[   19.126358] type=1505 audit(568045568.960:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1580
[   19.363130] type=1505 audit(568045569.196:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1584
[   19.364022] type=1505 audit(568045569.196:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1584
[   19.364469] type=1505 audit(568045569.196:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1584
[   19.364854] type=1505 audit(568045569.196:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1584
[   20.013649] type=1505 audit(568045569.844:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1589
[   20.015144] type=1505 audit(568045569.848:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1589
[   20.158082] type=1505 audit(568045569.988:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1593
[   27.265640] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.265653] Bluetooth: BNEP filters: protocol multicast
[   27.443349] Bridge firewalling registered
[   29.459481] ppdev: user-space parallel port driver
[   37.040286] eth0: no IPv6 routers present
[ 3221.392025] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 3221.560581] usb 1-1: configuration #1 chosen from 1 choice
[ 3222.117484] Initializing USB Mass Storage driver...
[ 3222.123016] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3222.128418] usbcore: registered new interface driver usb-storage
[ 3222.128438] USB Mass Storage support registered.
[ 3222.128911] usb-storage: device found at 2
[ 3222.128921] usb-storage: waiting for device to settle before scanning
[ 3227.133344] usb-storage: device scan complete
[ 3227.136494] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[ 3227.204872] sd 2:0:0:0: [sdb] 15745023 512-byte hardware sectors: (8.06 GB/7.50 GiB)
[ 3227.208457] sd 2:0:0:0: [sdb] Write Protect is off
[ 3227.208478] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 3227.208487] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3227.220501] sd 2:0:0:0: [sdb] 15745023 512-byte hardware sectors: (8.06 GB/7.50 GiB)
[ 3227.224549] sd 2:0:0:0: [sdb] Write Protect is off
[ 3227.224569] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 3227.224579] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3227.224700]  sdb: sdb1
[ 3227.236275] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 3227.236611] sd 2:0:0:0: Attached scsi generic sg2 type 0

$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: eth0
       version: 01
       serial: 00:1a:70:a8:14:97
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=64 module=wl multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:7e:09:e7:a1:da
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
$ lsb_release -d
Description:    Ubuntu 9.04

$ uname -mr
2.6.28-11-generic i686

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]



I apologize in advance if this is too much info.
My problems is that I cant see any option to connect to my wireless.
ty for your help.

---

### Post by Cuba71 on 2009-10-21
If you look at the sticky at the top of this section, it indicates that the current drivers don't support that PCI adapter, but I'm not sure how up to date that information is,perhaps there's a way to make it work


```

Linksys 	 802.11g/n 	 WMP300N 	 man: 14e4 dev: 4329 	 PCI 	 Broadcom 	 Bcm43xx 	 red  	 http://bcm43xx.berlios.de/ ; does not work with current drivers 

```
 
Look here, it looks that someone got it to work using ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=539208]("http://ubuntuforums.org/showthread.php?t=539208")

Good luck

---

### Post by grower1331 on 2009-10-21
Guess I'll have to find another adapter then, seeing how ndiswrapper doesn't work with aircrack. Any suggestions? Preferably something cheap and readily available in the US.

---

### Post by Evilness45 on 2009-12-01
I followed their instruction and I think I managed to install the driver. However, even after setting the correct wireless settings, it won't connect. I think it's not even trying to.
When I open the Windows Driver manager, it tells me that he can't find any configuration tools, yet he still list the driver and say that the hardware is there.
I don't know what to do.

Also, when I followed their instruction, they said that I had to add something at the end of that "blacklist" file. There's nothing in that file. Is that normal?

---

