---
title: "Cant connect to internet"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by JohnElway on 2010-06-13
I recently installed Xubuntu on an old Compaq Presario V2000 laptop and cannot connect to the internet wired or wirelessly. I have some experience with Ubuntu on a different computer but I never encountered any networking issues like this. I looked online for solutions but had difficulty implementing them, mainly because of the difficulty of obtaining packages without an internet connection.   

So hopefully someone with more experience with this stuff can help shed some light. At this point, I suspect that the drivers for the wired and wireless adapters are not supported, but I'm not even positive on this.  

Here's what I got after entering these commands in terminal:  

lspci
```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

```lsusb
```

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 08ec:0016 M-Systems Flash Disk Pioneers Kingston DataTraveler U3
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:16:36:33:ad:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5360 (5.3 KB)  TX bytes:5360 (5.3 KB)

```iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```lsmod
```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_atiixp_modem        9103  2 
snd_atiixp             12446  6 
snd_ac97_codec        100646  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  3 snd_pcm_oss
snd_pcm                70662  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674135  2 
snd_timer              19098  2 snd_pcm,snd_seq
pcmcia                 33024  0 
ttm                    49943  1 radeon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   157218  0 
drm_kms_helper         29297  1 radeon
joydev                  8708  0 
snd                    54148  23 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              204922  1 b43
yenta_socket           20408  1 
drm                   162471  4 radeon,ttm,drm_kms_helper
ati_agp                 5094  0 
i2c_piix4               8335  0 
i2c_algo_bit            5028  1 radeon
rsrc_nonstatic         10015  1 yenta_socket
soundcore               6620  3 snd
cfg80211              126485  2 b43,mac80211
agpgart                31724  3 ttm,drm,ati_agp
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc          7076  3 snd_atiixp_modem,snd_atiixp,snd_pcm
led_class               2864  1 b43
shpchp                 28820  0 
k8temp                  3024  0 
psmouse                63245  0 
video                  17375  0 
serio_raw               3978  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
8139too                18545  0 
8139cp                 16186  0 
usb_storage            39425  1 
mii                     4381  2 8139too,8139cp
ssb                    37336  1 b43
pata_atiixp             3148  1 

```dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ef0000 - 0000000017eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017eff000 - 0000000017f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x17ef0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-DFFFF write-protect
[    0.000000]   E0000-E3FFF write-back
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 base 0018000000 mask FFF8000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000017ef0000 (usable)
[    0.000000]  modified: 0000000017ef0000 - 0000000017eff000 (ACPI data)
[    0.000000]  modified: 0000000017eff000 - 0000000017f00000 (ACPI NVS)
[    0.000000]  modified: 0000000017f00000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000017ef0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0017c00000 page 2M
[    0.000000]  0017c00000 - 0017ef0000 page 4k
[    0.000000] kernel direct mapping tables up to 17ef0000 @ 7000-c000
[    0.000000] RAMDISK: 1178c000 - 11f73d7f
[    0.000000] ACPI: RSDP 000f8080 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 17ef8bc1 00034 (v01 HP     3097     20040224  LTP 00000000)
[    0.000000] ACPI: FACP 17efee2a 00074 (v01 HP     3097     20040224 PTL  0000005F)
[    0.000000] ACPI: DSDT 17ef8bf5 06235 (v01 HP     3091     20040224 MSFT 0100000E)
[    0.000000] ACPI: FACS 17efffc0 00040
[    0.000000] ACPI: SSDT 17efee9e 000D6 (v01 PTLTD  POWERNOW 20040224  LTP 00000001)
[    0.000000] ACPI: APIC 17efef74 00050 (v01 PTLTD  ? 3097   20040224  LTP 00000000)
[    0.000000] ACPI: MCFG 17efefc4 0003C (v01 PTLTD    MCFG   20040224  LTP 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 17ef0000
[    0.000000]   low ram: 0 - 17ef0000
[    0.000000]   node 0 low ram: 00000000 - 17ef0000
[    0.000000]   node 0 bootmap 00008000 - 0000afe0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0017ef0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [001178c000 - 0011f73d7f]          RAMDISK ==> [001178c000 - 0011f73d7f]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd108]              BRK ==> [00008da000 - 00008dd108]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000b000]          BOOTMAP ==> [0000008000 - 000000b000]
[    0.000000] found SMP MP-table at [c00f8130] f8130
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00017ef0
[    0.000000]   HighMem  0x00017ef0 -> 0x00017ef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00017ef0
[    0.000000] On node 0 totalpages: 97931
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 734 pages used for memmap
[    0.000000]   Normal zone: 93202 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x11
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 97165
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1960640 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 369748k/392128k available (4673k kernel code, 21640k reserved, 2122k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd86f0000 - 0xff7fe000   ( 625 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xd7ef0000   ( 382 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1794.738 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3589.47 BogoMIPS (lpj=7178952)
[    0.004028] Security Framework initialized
[    0.004055] AppArmor: AppArmor initialized
[    0.004064] Mount-cache hash table entries: 512
[    0.004202] Initializing cgroup subsys ns
[    0.004207] Initializing cgroup subsys cpuacct
[    0.004212] Initializing cgroup subsys memory
[    0.004222] Initializing cgroup subsys devices
[    0.004226] Initializing cgroup subsys freezer
[    0.004228] Initializing cgroup subsys net_cls
[    0.004250] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004253] CPU: L2 Cache: 128K (64 bytes/line)
[    0.004260] mce: CPU supports 5 MCE banks
[    0.004279] Performance Events: AMD PMU driver.
[    0.004294] ... version:                0
[    0.004297] ... bit width:              48
[    0.004299] ... generic registers:      4
[    0.004301] ... value mask:             0000ffffffffffff
[    0.004304] ... max period:             00007fffffffffff
[    0.004306] ... fixed-purpose events:   0
[    0.004308] ... event mask:             000000000000000f
[    0.004312] Checking 'hlt' instruction... OK.
[    0.020794] SMP alternatives: switching to UP code
[    0.027736] Freeing SMP alternatives: 19k freed
[    0.027766] ACPI: Core revision 20090903
[    0.038554] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.038560] ftrace: allocating 21771 entries in 43 pages
[    0.040123] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040348]   alloc irq_desc for 21 on node 0
[    0.040351]   alloc kstat_irqs on node 0
[    0.040495] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.081520] CPU0: Mobile AMD Sempron(tm) Processor 3000+ stepping 02
[    0.084001] Brought up 1 CPUs
[    0.084001] Total of 1 processors activated (3589.47 BogoMIPS).
[    0.084001] CPU0 attaching NULL sched-domain.
[    0.084001] devtmpfs: initialized
[    0.084001] regulator: core version 0.5
[    0.084001] Time: 16:01:57  Date: 06/12/10
[    0.084001] NET: Registered protocol family 16
[    0.084001] EISA bus registered
[    0.084001] ACPI: bus type pci registered
[    0.084001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.084001] PCI: Not using MMCONFIG.
[    0.084001] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=5
[    0.084001] PCI: Using configuration type 1 for base access
[    0.084001] bio: create slab <bio-0> at 0
[    0.084001] ACPI: EC: Look up EC in DSDT
[    0.085454] ACPI: Interpreter enabled
[    0.085466] ACPI: (supports S0 S3 S4 S5)
[    0.085488] ACPI: Using IOAPIC for interrupt routing
[    0.085622] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.086246] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.086246] PCI: Using MMCONFIG for extended config space
[    0.092573] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.092726] ACPI: No dock devices found.
[    0.093826] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.093992] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0000000-0xc0000fff]
[    0.094107] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0001000-0xc0001fff]
[    0.094233] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0002000-0xc0002fff]
[    0.094307] pci 0000:00:13.2: supports D1 D2
[    0.094310] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.094318] pci 0000:00:13.2: PME# disabled
[    0.094376] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
[    0.094386] pci 0000:00:14.0: reg 14 32bit mmio: [0xc0003000-0xc00033ff]
[    0.094426] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.094498] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.094509] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.094519] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
[    0.094529] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
[    0.094539] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
[    0.094743] pci 0000:00:14.5: reg 10 32bit mmio: [0xc0003400-0xc00034ff]
[    0.094854] pci 0000:00:14.6: reg 10 32bit mmio: [0xc0003800-0xc00038ff]
[    0.095039] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc8000000-0xcfffffff]
[    0.095045] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.095051] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.095063] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.095074] pci 0000:01:05.0: supports D1 D2
[    0.095092] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.095096] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.095102] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xcfffffff]
[    0.095160] pci 0000:05:00.0: reg 10 io port: [0xa000-0xa0ff]
[    0.095172] pci 0000:05:00.0: reg 14 32bit mmio: [0xc0208000-0xc02080ff]
[    0.095247] pci 0000:05:00.0: supports D1 D2
[    0.095250] pci 0000:05:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.095257] pci 0000:05:00.0: PME# disabled
[    0.095298] pci 0000:05:02.0: reg 10 32bit mmio: [0xc0204000-0xc0205fff]
[    0.096115] pci 0000:05:09.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.096151] pci 0000:05:09.0: supports D1 D2
[    0.096154] pci 0000:05:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.096161] pci 0000:05:09.0: PME# disabled
[    0.096233] pci 0000:00:14.4: transparent bridge
[    0.096243] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.096249] pci 0000:00:14.4: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.096297] pci_bus 0000:00: on NUMA node 0
[    0.096306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.096430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.096518] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.098602] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.098726] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.098844] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.098964] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.099081] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.099200] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.099318] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.099436] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.099582] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.099588] vgaarb: loaded
[    0.099727] SCSI subsystem initialized
[    0.099827] libata version 3.00 loaded.
[    0.099909] usbcore: registered new interface driver usbfs
[    0.099924] usbcore: registered new interface driver hub
[    0.099956] usbcore: registered new device driver usb
[    0.100171] ACPI: WMI: Mapper loaded
[    0.100176] PCI: Using ACPI for IRQ routing
[    0.100542] NetLabel: Initializing
[    0.100544] NetLabel:  domain hash size = 128
[    0.100547] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.100563] NetLabel:  unlabeled traffic allowed by default
[    0.100614] Switching to clocksource tsc
[    0.102764] AppArmor: AppArmor Filesystem Enabled
[    0.102795] pnp: PnP ACPI init
[    0.102823] ACPI: bus type pnp registered
[    0.104259] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.106186] pnp: PnP ACPI: found 10 devices
[    0.106189] ACPI: ACPI bus type pnp unregistered
[    0.106194] PnPBIOS: Disabled by ACPI PNP
[    0.106211] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.106215] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.106219] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.106229] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.106233] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.106236] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.106240] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.106243] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.106246] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.106250] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.106253] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.106257] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.106260] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.106264] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.106267] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.106271] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.106274] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.106278] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.106281] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.106285] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.106292] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.106295] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.141051] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.141055] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.141060] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.141064] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff
[    0.141076] pci 0000:05:09.0: CardBus bridge, secondary bus 0000:06
[    0.141079] pci 0000:05:09.0:   IO window: 0x00a400-0x00a4ff
[    0.141086] pci 0000:05:09.0:   IO window: 0x00a800-0x00a8ff
[    0.141093] pci 0000:05:09.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.141100] pci 0000:05:09.0:   MEM window: 0x24000000-0x27ffffff
[    0.141106] pci 0000:00:14.4: PCI bridge, secondary bus 0000:05
[    0.141111] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.141118] pci 0000:00:14.4:   MEM window: 0xc0200000-0xc02fffff
[    0.141124] pci 0000:00:14.4:   PREFETCH window: 0x20000000-0x23ffffff
[    0.141160]   alloc irq_desc for 17 on node -1
[    0.141162]   alloc kstat_irqs on node -1
[    0.141170] pci 0000:05:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.141177] pci 0000:05:09.0: setting latency timer to 64
[    0.141183] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.141186] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.141189] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.141192] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.141196] pci_bus 0000:01: resource 2 pref mem [0xc8000000-0xcfffffff]
[    0.141199] pci_bus 0000:05: resource 0 io:  [0xa000-0xafff]
[    0.141202] pci_bus 0000:05: resource 1 mem: [0xc0200000-0xc02fffff]
[    0.141205] pci_bus 0000:05: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.141208] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.141211] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.141214] pci_bus 0000:06: resource 0 io:  [0xa400-0xa4ff]
[    0.141217] pci_bus 0000:06: resource 1 io:  [0xa800-0xa8ff]
[    0.141220] pci_bus 0000:06: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.141223] pci_bus 0000:06: resource 3 mem: [0x24000000-0x27ffffff]
[    0.141267] NET: Registered protocol family 2
[    0.141379] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.141693] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.141807] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.141964] TCP: Hash tables configured (established 16384 bind 16384)
[    0.141967] TCP reno registered
[    0.142092] NET: Registered protocol family 1
[    0.142111] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.142117] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.807388] pci 0000:01:05.0: Boot video device
[    0.807613] cpufreq-nforce2: No nForce2 chipset.
[    0.807646] Scanning for low memory corruption every 60 seconds
[    0.807785] audit: initializing netlink socket (disabled)
[    0.807805] type=2000 audit(1276358517.807:1): initialized
[    0.819104] Trying to unpack rootfs image as initramfs...
[    0.831996] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.839793] VFS: Disk quotas dquot_6.5.2
[    0.839907] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.840604] fuse init (API version 7.13)
[    0.840703] msgmni has been set to 722
[    0.840982] alg: No test for stdrng (krng)
[    0.841074] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.841077] io scheduler noop registered
[    0.841080] io scheduler anticipatory registered
[    0.841082] io scheduler deadline registered
[    0.841132] io scheduler cfq registered (default)
[    0.841254] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.841278] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.843617] ACPI: AC Adapter [ACAD] (on-line)
[    0.843699] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.843704] ACPI: Power Button [PWRB]
[    0.843753] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.843756] ACPI: Sleep Button [SLPB]
[    0.843798] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.844606] ACPI: Lid Switch [LID]
[    0.844713] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.844717] ACPI: Power Button [PWRF]
[    0.844891] Marking TSC unstable due to TSC halts in idle
[    0.844992] processor LNXCPU:00: registered as cooling_device0
[    0.848860] thermal LNXTHERM:01: registered as thermal_zone0
[    0.848875] ACPI: Thermal Zone [THRM] (41 C)
[    0.850605] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.850954] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.850964] serial 0000:00:14.6: PCI INT B disabled
[    0.852033] brd: module loaded
[    0.852558] loop: module loaded
[    0.852690] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.852893]   alloc irq_desc for 16 on node -1
[    0.852897]   alloc kstat_irqs on node -1
[    0.852906] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.853001] Switching to clocksource acpi_pm
[    0.857555] isapnp: Scanning for PnP cards...
[    0.863198] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.863749] Fixed MDIO Bus: probed
[    0.863821] PPP generic driver version 2.4.2
[    0.863993] tun: Universal TUN/TAP device driver, 1.6
[    0.863996] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.864060] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] (20090903/evregion-424)
[    0.864069] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_.SMRD] (Node d78184c8), AE_TIME
[    0.864098] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.BAT1.UPBI] (Node d7818738), AE_TIME
[    0.864120] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.BAT1._BIF] (Node d7818708), AE_TIME
[    0.864145] ACPI Exception: AE_TIME, Evaluating _BIF (20090903/battery-363)
[    0.864179] ACPI: Battery Slot [BAT1] (battery present)
[    0.864296] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.864331]   alloc irq_desc for 19 on node -1
[    0.864334]   alloc kstat_irqs on node -1
[    0.864342] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.864369] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.864413] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.864487] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[    0.911875] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.912084] usb usb1: configuration #1 chosen from 1 choice
[    0.912120] hub 1-0:1.0: USB hub found
[    0.912133] hub 1-0:1.0: 8 ports detected
[    0.912230] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.912258] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.912282] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.912333] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.912358] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[    1.008248] usb usb2: configuration #1 chosen from 1 choice
[    1.008282] hub 2-0:1.0: USB hub found
[    1.008300] hub 2-0:1.0: 4 ports detected
[    1.008378] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.008403] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.008457] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    1.008489] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[    1.095977] usb usb3: configuration #1 chosen from 1 choice
[    1.100414] hub 3-0:1.0: USB hub found
[    1.100441] hub 3-0:1.0: 4 ports detected
[    1.100530] uhci_hcd: USB Universal Host Controller Interface driver
[    1.100643] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.102746] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.102762] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.102942] mice: PS/2 mouse device common for all mice
[    1.106205] rtc_cmos 00:04: RTC can wake from S4
[    1.106311] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.106350] rtc0: alarms up to one month, 114 bytes nvram
[    1.106493] device-mapper: uevent: version 1.0.3
[    1.106672] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.108434] device-mapper: multipath: version 1.1.0 loaded
[    1.108439] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.108678] EISA: Probing bus 0 at eisa.0
[    1.108689] Cannot allocate resource for EISA slot 1
[    1.108720] Cannot allocate resource for EISA slot 8
[    1.108722] EISA: Detected 0 cards.
[    1.112393] cpuidle: using governor ladder
[    1.112440] cpuidle: using governor menu
[    1.112957] TCP cubic registered
[    1.113119] NET: Registered protocol family 10
[    1.113614] lo: Disabled Privacy Extensions
[    1.113956] NET: Registered protocol family 17
[    1.114006] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[    1.114061] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
[    1.114065] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
[    1.114068] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
[    1.114118] Using IPI No-Shortcut mode
[    1.114232] PM: Resume from disk failed.
[    1.114247] registered taskstats version 1
[    1.114536]   Magic number: 14:558:34
[    1.114651] rtc_cmos 00:04: setting system clock to 2010-06-12 16:01:58 UTC (1276358518)
[    1.114657] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.114659] EDD information not available.
[    1.133687] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.280026] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.380153] Freeing initrd memory: 8095k freed
[    1.477475] isapnp: No Plug & Play device found
[    1.477499] Freeing unused kernel memory: 656k freed
[    1.478412] Write protecting the kernel text: 4676k
[    1.478451] Write protecting the kernel read-only data: 1840k
[    1.494401] usb 1-1: configuration #1 chosen from 1 choice
[    1.506885] udev: starting version 151
[    1.764858] scsi0 : pata_atiixp
[    1.765465] scsi1 : pata_atiixp
[    1.766750] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    1.766755] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    1.781472]   alloc irq_desc for 20 on node -1
[    1.781478]   alloc kstat_irqs on node -1
[    1.781487] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.781783] Initializing USB Mass Storage driver...
[    1.781924] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.782150] usbcore: registered new interface driver usb-storage
[    1.782156] USB Mass Storage support registered.
[    1.782311] usb-storage: device found at 2
[    1.782314] usb-storage: waiting for device to settle before scanning
[    1.840111] ssb: Sonics Silicon Backplane found on PCI device 0000:05:02.0
[    1.928636] ata1.00: ATA-6: ST960812A, 3.05, max UDMA/100
[    1.928642] ata1.00: 117210240 sectors, multi 16: LBA 
[    1.944587] ata1.00: configured for UDMA/100
[    1.944737] scsi 0:0:0:0: Direct-Access     ATA      ST960812A        3.05 PQ: 0 ANSI: 5
[    1.944941] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.945435] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.945490] sd 0:0:0:0: [sda] Write Protect is off
[    1.945494] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.945521] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.945711]  sda: sda1 sda2
[    1.955564] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.108630] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4082N, CQ04, max MWDMA2
[    2.124590] ata2.00: configured for MWDMA2
[    2.130418] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4082N CQ04 PQ: 0 ANSI: 5
[    2.142447] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.142453] Uniform CD-ROM driver Revision: 3.20
[    2.142850] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.143056] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.150997] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.151040] 8139cp 0000:05:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.158984] 8139too Fast Ethernet driver 0.9.28
[    2.159039]   alloc irq_desc for 18 on node -1
[    2.159041]   alloc kstat_irqs on node -1
[    2.159050] 8139too 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.162311] eth0: RealTek RTL8139 at 0xa000, 00:16:36:33:ad:e0, IRQ 18
[    2.924882] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    6.780396] usb-storage: device scan complete
[    6.780994] scsi 2:0:0:0: Direct-Access     Memorex  Mini TravelDrive 6.16 PQ: 0 ANSI: 0 CCS
[    6.781481] scsi 2:0:0:1: CD-ROM            Memorex  Mini TravelDrive 6.16 PQ: 0 ANSI: 0
[    6.783311] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.785478] sd 2:0:0:0: [sdb] 489983 512-byte logical blocks: (250 MB/239 MiB)
[    6.787719] sd 2:0:0:0: [sdb] Write Protect is off
[    6.787726] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    6.787729] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.788238] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[    6.788416] sr 2:0:0:1: Attached scsi CD-ROM sr1
[    6.788498] sr 2:0:0:1: Attached scsi generic sg3 type 5
[    6.791476] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.791484]  sdb: sdb1
[    6.795476] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.795481] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   12.148085] udev: starting version 151
[   13.083784] lp: driver loaded but no devices found
[   13.150196] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:0d/LNXVIDEO:00/input/input6
[   13.150448] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.577067] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.776691] Linux agpgart interface v0.103
[   13.925304] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   13.937792] cfg80211: Calling CRDA to update world regulatory domain
[   13.942127] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   13.975694] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   14.115740] yenta_cardbus 0000:05:09.0: CardBus bridge found [103c:3091]
[   14.115769] yenta_cardbus 0000:05:09.0: Enabling burst memory read transactions
[   14.115776] yenta_cardbus 0000:05:09.0: Using CSCINT to route CSC interrupts to PCI
[   14.115779] yenta_cardbus 0000:05:09.0: Routing CardBus interrupts to PCI
[   14.115787] yenta_cardbus 0000:05:09.0: TI: mfunc 0x01a01b22, devctl 0x66
[   14.117081] [drm] Initialized drm 1.1.0 20060810
[   14.344863] yenta_cardbus 0000:05:09.0: ISA IRQ mask 0x0ee8, PCI irq 17
[   14.344871] yenta_cardbus 0000:05:09.0: Socket status: 30000006
[   14.344876] pci_bus 0000:05: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   14.344890] yenta_cardbus 0000:05:09.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   14.344896] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: clean.
[   14.345174] yenta_cardbus 0000:05:09.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   14.345178] yenta_cardbus 0000:05:09.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   14.411931] type=1505 audit(1276383731.793:2):  operation=&quot;profile_load&quot; pid=524 name=&quot;/sbin/dhclient3&quot;
[   14.412311] type=1505 audit(1276383731.797:3):  operation=&quot;profile_load&quot; pid=524 name=&quot;/usr/lib/NetworkManager/nm-dhcp-client.action&quot;
[   14.412494] type=1505 audit(1276383731.797:4):  operation=&quot;profile_load&quot; pid=524 name=&quot;/usr/lib/connman/scripts/dhclient-script&quot;
[   14.442676] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   14.839804] cfg80211: World regulatory domain updated:
[   14.839813]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.839817]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.839820]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.839824]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.839827]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.839830]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.928985] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   14.931447] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   14.936641] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   14.937483] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   14.938388] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.947320] [drm] radeon defaulting to kernel modesetting.
[   14.947327] [drm] radeon kernel modesetting enabled.
[   14.947471] radeon 0000:01:05.0: power state changed by ACPI to D0
[   14.947483] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.968505] [drm] radeon: Initializing kernel modesetting.
[   14.971560] [drm] register mmio base: 0xC0100000
[   14.971565] [drm] register mmio size: 65536
[   14.971968] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   14.971996] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   14.972107] [drm] Generation 2 PCI interface, using max accessible memory
[   14.972111] [drm] radeon: VRAM 128M
[   14.972113] [drm] radeon: VRAM from 0x18000000 to 0x1FFFFFFF
[   14.972115] [drm] radeon: GTT 32M
[   14.972117] [drm] radeon: GTT from 0x20000000 to 0x21FFFFFF
[   14.972153] [drm] radeon: irq initialized.
[   14.972242] [drm] Detected VRAM RAM=128M, BAR=128M
[   14.972247] [drm] RAM width 128bits DDR
[   14.976810] [TTM] Zone  kernel: Available graphics memory: 189426 kiB.
[   14.976836] [drm] radeon: 128M of VRAM memory ready
[   14.976839] [drm] radeon: 32M of GTT memory ready.
[   14.976862] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   14.977781] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
[   14.977809] [drm] radeon: cp idle (0x10000C03)
[   14.977989] [drm] Loading R300 Microcode
[   14.978434] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   14.983770] phy0: Selected rate control algorithm 'minstrel'
[   14.984705] Registered led device: b43-phy0::radio
[   14.984809] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   15.027308] [drm] radeon: ring at 0x0000000020000000
[   15.027329] [drm] ring test succeeded in 1 usecs
[   15.044220] [drm] radeon: ib pool ready.
[   15.044308] [drm] ib test succeeded in 0 usecs
[   15.044368] [drm] Default TV standard: NTSC
[   15.044370] [drm] 14.318180000 MHz TV ref clk
[   15.044482] [drm] Panel ID String: QDS                     
[   15.044485] [drm] Panel Size 1280x768
[   15.044544] [drm] Default TV standard: NTSC
[   15.044546] [drm] 14.318180000 MHz TV ref clk
[   15.044578] [drm] Radeon Display Connectors
[   15.044580] [drm] Connector 0:
[   15.044581] [drm]   VGA
[   15.044585] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   15.044587] [drm]   Encoders:
[   15.044589] [drm]     CRT1: INTERNAL_DAC2
[   15.044590] [drm] Connector 1:
[   15.044592] [drm]   LVDS
[   15.044595] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   15.044597] [drm]   Encoders:
[   15.044599] [drm]     LCD1: INTERNAL_LVDS
[   15.044601] [drm] Connector 2:
[   15.044602] [drm]   S-video
[   15.044604] [drm]   Encoders:
[   15.044605] [drm]     TV1: INTERNAL_DAC2
[   15.297870] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.309033] [drm] fb mappable at 0xC8040000
[   15.309036] [drm] vram apper at 0xC8000000
[   15.309039] [drm] size 3932160
[   15.309041] [drm] fb depth is 24
[   15.309043] [drm]    pitch is 5120
[   15.321575] fb0: radeondrmfb frame buffer device
[   15.321579] registered panic notifier
[   15.321588] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   15.325093] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.344700] vga16fb: initializing
[   15.344707] vga16fb: mapped to 0xc00a0000
[   15.344713] vga16fb: not registering due to another framebuffer present
[   15.436091] MC'97 0 converters and GPIO not ready (0x1)
[   15.540884] Console: switching to colour frame buffer device 160x48
[   16.962269] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:3 across:44480688k 
[   17.818580] type=1505 audit(1276383735.201:5):  operation=&quot;profile_replace&quot; pid=766 name=&quot;/sbin/dhclient3&quot;
[   17.818942] type=1505 audit(1276383735.201:6):  operation=&quot;profile_replace&quot; pid=766 name=&quot;/usr/lib/NetworkManager/nm-dhcp-client.action&quot;
[   17.819144] type=1505 audit(1276383735.201:7):  operation=&quot;profile_replace&quot; pid=766 name=&quot;/usr/lib/connman/scripts/dhclient-script&quot;
[   18.115406] type=1505 audit(1276383735.497:8):  operation=&quot;profile_load&quot; pid=768 name=&quot;/usr/bin/evince&quot;
[   18.123630] type=1505 audit(1276383735.505:9):  operation=&quot;profile_load&quot; pid=768 name=&quot;/usr/bin/evince-previewer&quot;
[   18.126787] type=1505 audit(1276383735.509:10):  operation=&quot;profile_load&quot; pid=768 name=&quot;/usr/bin/evince-thumbnailer&quot;
[   18.285814] eth0: link down
[   18.285971] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.332113] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   18.335850] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   18.342786] b43-phy0 ERROR: Firmware file &quot;b43/ucode5.fw&quot; not found
[   18.342792] b43-phy0 ERROR: Firmware file &quot;b43-open/ucode5.fw&quot; not found
[   18.342796] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   18.345763] type=1505 audit(1276383735.729:11):  operation=&quot;profile_load&quot; pid=776 name=&quot;/usr/lib/cups/backend/cups-pdf&quot;
[   18.524098] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   18.533289] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   18.540522] b43-phy0 ERROR: Firmware file &quot;b43/ucode5.fw&quot; not found
[   18.540528] b43-phy0 ERROR: Firmware file &quot;b43-open/ucode5.fw&quot; not found
[   18.540532] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   19.845699] ppdev: user-space parallel port driver
[   24.665112] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.665118] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.665124] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.665129] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.665135] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 00 e0 00 00 02 00
[   24.665144] end_request: I/O error, dev sr1, sector 4195200
[   24.665150] __ratelimit: 6 callbacks suppressed
[   24.665154] Buffer I/O error on device sr1, logical block 524400
[   24.669488] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.669493] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.669497] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.669503] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.669508] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 00 e0 00 00 02 00
[   24.669518] end_request: I/O error, dev sr1, sector 4195200
[   24.669525] Buffer I/O error on device sr1, logical block 524400
[   24.673362] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.673368] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.673372] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.673377] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.673382] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 10 00 00 02 00
[   24.673391] end_request: I/O error, dev sr1, sector 4195392
[   24.673398] Buffer I/O error on device sr1, logical block 524424
[   24.677359] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.677365] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.677369] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.677376] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.677380] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 10 00 00 02 00
[   24.677390] end_request: I/O error, dev sr1, sector 4195392
[   24.677397] Buffer I/O error on device sr1, logical block 524424
[   24.683868] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.683874] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.683878] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.683884] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.683888] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.683898] end_request: I/O error, dev sr1, sector 4195400
[   24.683905] Buffer I/O error on device sr1, logical block 524425
[   24.687746] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.687752] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.687757] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.687762] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.687767] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.687777] end_request: I/O error, dev sr1, sector 4195400
[   24.687782] Buffer I/O error on device sr1, logical block 524425
[   24.691493] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.691498] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.691503] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.691508] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.691512] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.691522] end_request: I/O error, dev sr1, sector 4195400
[   24.691527] Buffer I/O error on device sr1, logical block 524425
[   24.695241] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.695246] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.695251] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.695256] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.695261] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.695270] end_request: I/O error, dev sr1, sector 4195400
[   24.695276] Buffer I/O error on device sr1, logical block 524425
[   24.700614] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.700621] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.700626] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.700630] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.700636] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.700647] end_request: I/O error, dev sr1, sector 4195400
[   24.700653] Buffer I/O error on device sr1, logical block 524425
[   24.704357] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.704362] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.704367] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.704372] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.704377] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.704386] end_request: I/O error, dev sr1, sector 4195400
[   24.704391] Buffer I/O error on device sr1, logical block 524425
[   24.708122] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.708127] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.708131] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.708137] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.708142] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.708151] end_request: I/O error, dev sr1, sector 4195400
[   24.711982] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.711988] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.711992] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.711997] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.712030] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 04 00 00 02 00
[   24.712039] end_request: I/O error, dev sr1, sector 4195344
[   24.715857] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.715862] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.715866] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.715871] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.715875] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 10 00 00 02 00
[   24.715886] end_request: I/O error, dev sr1, sector 4195392
[   24.719624] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.719629] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.719634] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.719639] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.719643] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.719654] end_request: I/O error, dev sr1, sector 4195400
[   24.723508] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.723513] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.723517] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.723522] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.723528] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.723538] end_request: I/O error, dev sr1, sector 4195400
[   24.727622] sr 2:0:0:1: [sr1] Unhandled sense code
[   24.727628] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   24.727633] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[   24.727638] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[   24.727643] sr 2:0:0:1: [sr1] CDB: Read(10): 28 00 00 10 01 12 00 00 02 00
[   24.727652] end_request: I/O error, dev sr1, sector 4195400
[   24.907718] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold

```sudo lshw -C network
```

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:33:ad:e0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:20 memory:c0204000-c0205fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:74:f7:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

```lsb_release -d
```

Description:    Ubuntu 10.04 LTS

```uname -mr
```

2.6.32-21-generic i686

```sudo /etc/init.d/networking restart
```

 * Reconfiguring network interfaces...                                  [ OK ] 

```

---

### Post by garvinrick4 on 2010-06-13
You did right click on applet on panel and enable your connections? Just checking.

---

### Post by JohnElway on 2010-06-13
Yes. I believe they're enabled by default.

---

### Post by purelinuxuser on 2010-06-13
Well, since you lack an Ethernet connection, your only option is to install the firmware for the native b43 driver in the Linux kernel (your wireless card is supported, but you need an Internet connection to fully activate the driver :( ).

[LIST=1]
[*] Download the following packages and place them onto your Desktop folder:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
[*]Run the following commands in the terminal:
```
sudo b43-fwcutter -w /lib/firmware ~/Desktop/wl_apsta-3.130.20.0.o
tar xvf ~/Desktop/broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware ~/Desktop/broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
```
[*]You can now safely remove any files from your desktop
[*]Reboot
[/LIST]
Good luck :)

---

### Post by JohnElway on 2010-06-13
Thanks purelinuxuser! Your solution got my wireless card working great.

Just in case someone else follows these same instructions, I should mention that installing the Broadcom drivers causes the top and bottom panel to disappear for some people. The solution is to hit ALT+F2 to bring up the Run dialog. Type 'xfce4-panel' and hit the Run button. Everything should work fine after that.

---

### Post by purelinuxuser on 2010-06-13
You're welcome!  Don't forget the [SOLVED] tag ;)

---

