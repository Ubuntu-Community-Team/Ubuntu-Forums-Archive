---
title: "Wireless not detected"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by sankpl on 2011-10-04
Hi ,

The other day i was browsing through the internet to know about the key ring and changing the password, I hit few forums and followed one direction, which tells to delete the existing default keyring and then restart the PC which will prompt for a keyring password and whatever that entered would be the password. There was direction for reseting the password, however i went ahead and deleted the default keyring and now my wireless is not detected.

Can somebody help me?

---

### Post by pdc on 2011-10-05
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

help others to help you

---

### Post by sankpl on 2011-10-05
Thank you PDC.

I will get it all info and paste it here..

---

### Post by sankpl on 2011-10-10
PDC,

Here is the info you asked for.


Script started on Mon 10 Oct 2011 10:26:11 AM CDT
]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ lsusb
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. 
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ lspci -nn |grep 'wireless Brand'
]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ lspci[K[K[K[K[Kifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:5a:f2:06  
          inet addr:10.40.160.202  Bcast:10.40.160.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe5a:f206/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:705 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1364195 (1.3 MB)  TX bytes:125772 (125.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ iwfo[K[Kconfig
lo        no wireless extensions.

eth0      no wireless extensions.

]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ iwconfig wlano[K0
wlan0     No such device

]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ lsmod
Module                  Size  Used by
md4                    12523  0 
ip6table_filter        12711  0 
ip6_tables             22545  1 ip6table_filter
iptable_filter         12706  0 
ip_tables              18125  1 iptable_filter
x_tables               21907  4 ip6table_filter,ip6_tables,iptable_filter,ip_tables
binfmt_misc            13213  1 
nls_utf8               12493  0 
cifs                  247650  0 
parport_pc             32111  0 
ppdev                  12849  0 
pcmcia                 39671  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  2 
wl                   2642531  0 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
dell_wmi               12601  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
sparse_keymap          13666  1 dell_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
serio_raw              12990  0 
lib80211               14570  1 wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
uvesafb                28311  0 
vesafb                 13449  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
i915                  451033  2 
drm_kms_helper         40745  1 i915
drm                   184164  3 i915,drm_kms_helper
tg3                   131476  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ lsmod |grep 'wlan_module_name'
]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ lsmod |grep 'wlan_module_name'[K"[1Pwlan_module_name""wlan_module_name"
]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic (buildd@zirconium) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 (Ubuntu 2.6.38-11.50-generic 2.6.38.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f681400 (usable)
[    0.000000]  BIOS-e820: 000000007f681400 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[    0.000000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Dell Inc. Latitude D620                   /0TD761, BIOS A10 05/16/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f681 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F800000 mask FFF800000 uncachable
[    0.000000]   2 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35dfc000 - 36ef6000
[    0.000000] ACPI: RSDP 000fc0c0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 7f68198a 00044 (v01 DELL    M07     27D80510 ASL  00000061)
[    0.000000] ACPI: FACP 7f682800 00074 (v01 DELL    M07     27D80510 ASL  00000061)
[    0.000000] ACPI: DSDT 7f683400 0519E (v01 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 7f691c00 00040
[    0.000000] ACPI: HPET 7f682f00 00038 (v01 DELL    M07     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 7f683000 00068 (v01 DELL    M07     27D80510 ASL  00000047)
[    0.000000] ACPI: ASF! 7f682c00 0005B (v16 DELL    M07     27D80510 ASL  00000061)
[    0.000000] ACPI: MCFG 7f682fc0 0003E (v16 DELL    M07     27D80510 ASL  00000061)
[    0.000000] ACPI: TCPA 7f683300 00032 (v01 DELL    M07     27D80510 ASL  00000061)
[    0.000000] ACPI: SLIC 7f68309c 00176 (v01 DELL    M07     27D80510 ASL  00000061)
[    0.000000] ACPI: SSDT 7f681a11 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f681
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f681
[    0.000000] On node 0 totalpages: 521744
[    0.000000] free_area_init_node: node 0, pgdat c1784180, node_mem_map f4e0c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292229 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:70000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517666
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.38-11-generic root=UUID=26e0f79e-db33-4b66-9ba9-5a84fa2714ba ro vga=792 splash quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10436820 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f681)
[    0.000000] Memory: 2032760k/2087428k available (5191k kernel code, 54216k reserved, 2537k data, 700k init, 1178124k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511e91 - 0xc178c500   (2537 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511e91   (5191 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2161.316 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4322.63 BogoMIPS (lpj=8645264)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004031] Security Framework initialized
[    0.004048] AppArmor: AppArmor initialized
[    0.004050] Yama: becoming mindful.
[    0.004110] Mount-cache hash table entries: 512
[    0.004260] Initializing cgroup subsys ns
[    0.004264] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004267] Initializing cgroup subsys cpuacct
[    0.004272] Initializing cgroup subsys memory
[    0.004281] Initializing cgroup subsys devices
[    0.004283] Initializing cgroup subsys freezer
[    0.004285] Initializing cgroup subsys net_cls
[    0.004287] Initializing cgroup subsys blkio
[    0.004326] CPU: Physical Processor ID: 0
[    0.004328] CPU: Processor Core ID: 0
[    0.004332] mce: CPU supports 6 MCE banks
[    0.004341] CPU0: Thermal monitoring enabled (TM2)
[    0.004345] using mwait in idle threads.
[    0.009026] ACPI: Core revision 20110112
[    0.012014] ftrace: allocating 23652 entries in 47 pages
[    0.016054] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016426] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.056765] CPU0: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz stepping 06
[    0.060003] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.060003] PEBS disabled due to CPU errata.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] CPU 1 irqstacks, hard=f40aa000 soft=f40ac000
[    0.060003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.148008] TSC synchronization [CPU#0 -> CPU#1]:
[    0.148008] Measured 4547752365 cycles TSC warp between CPUs, turning off TSC clock.
[    0.148008] Marking TSC unstable due to check_tsc_sync_source failed
[    0.148028] Brought up 2 CPUs
[    0.148031] Total of 2 processors activated (8645.17 BogoMIPS).
[    0.149358] devtmpfs: initialized
[    0.149358] print_constraints: dummy: 
[    0.149358] Time: 10:14:56  Date: 10/10/11
[    0.149358] NET: Registered protocol family 16
[    0.149358] Trying to unpack rootfs image as initramfs...
[    0.149388] EISA bus registered
[    0.149396] ACPI: bus type pci registered
[    0.149472] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.149475] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.149477] PCI: Using MMCONFIG for extended config space
[    0.149479] PCI: Using configuration type 1 for base access
[    0.149488] dmi type 0xB1 record - unknown flag
[    0.152286] bio: create slab <bio-0> at 0
[    0.153601] ACPI: EC: Look up EC in DSDT
[    0.162940] ACPI Warning: Incorrect checksum in table [TCPA] - 0x00, should be 0x9A (20110112/tbutils-314)
[    0.162949] ACPI: SSDT 7f6819ce 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.163223] ACPI: Dynamic OEM Table Load:
[    0.163226] ACPI: SSDT   (null) 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.163533] ACPI: SSDT 7f682138 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.163828] ACPI: Dynamic OEM Table Load:
[    0.163832] ACPI: SSDT   (null) 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.163955] ACPI: SSDT 7f681eed 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.164243] ACPI: Dynamic OEM Table Load:
[    0.164247] ACPI: SSDT   (null) 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.164509] ACPI: SSDT 7f68237c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.164797] ACPI: Dynamic OEM Table Load:
[    0.164801] ACPI: SSDT   (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.164911] ACPI: SSDT 7f6820b3 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.165189] ACPI: Dynamic OEM Table Load:
[    0.165192] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.165409] ACPI: Interpreter enabled
[    0.165415] ACPI: (supports S0 S3 S4 S5)
[    0.165435] ACPI: Using IOAPIC for interrupt routing
[    0.270753] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.270757] HEST: Table not found.
[    0.270762] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.276630] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.288373] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.288377] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.288380] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.288383] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.288386] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xefffffff]
[    0.288388] pci_root PNP0A03:00: host bridge window [mem 0xf4007000-0xf4007fff]
[    0.288391] pci_root PNP0A03:00: host bridge window [mem 0xf400c000-0xfebfffff]
[    0.288393] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff]
[    0.288396] pci_root PNP0A03:00: host bridge window [mem 0xfed00400-0xfed1ffff]
[    0.288398] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.288401] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xffafffff]
[    0.288425] pci 0000:00:00.0: [8086:27a0] type 0 class 0x000600
[    0.288478] pci 0000:00:02.0: [8086:27a2] type 0 class 0x000300
[    0.288491] pci 0000:00:02.0: reg 10: [mem 0xeff00000-0xeff7ffff]
[    0.288498] pci 0000:00:02.0: reg 14: [io  0xeff8-0xefff]
[    0.288505] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.288512] pci 0000:00:02.0: reg 1c: [mem 0xefec0000-0xefefffff]
[    0.288556] pci 0000:00:02.1: [8086:27a6] type 0 class 0x000380
[    0.288566] pci 0000:00:02.1: reg 10: [mem 0xeff80000-0xefffffff]
[    0.288675] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.288699] pci 0000:00:1b.0: reg 10: [mem 0xefebc000-0xefebffff 64bit]
[    0.288786] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.288791] pci 0000:00:1b.0: PME# disabled
[    0.288822] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.288913] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.288918] pci 0000:00:1c.0: PME# disabled
[    0.288950] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.289041] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.289046] pci 0000:00:1c.1: PME# disabled
[    0.289080] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.289170] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.289174] pci 0000:00:1c.2: PME# disabled
[    0.289210] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.289269] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
[    0.289310] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.289371] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
[    0.289413] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.289472] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
[    0.289513] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.289572] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
[    0.289627] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.289653] pci 0000:00:1d.7: reg 10: [mem 0xffa80000-0xffa803ff]
[    0.289747] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.289752] pci 0000:00:1d.7: PME# disabled
[    0.289779] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.289869] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.289988] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.289994] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.289999] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.290006] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.290057] pci 0000:00:1f.2: [8086:27c4] type 0 class 0x000101
[    0.290078] pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
[    0.290091] pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
[    0.290104] pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
[    0.290116] pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
[    0.290129] pci 0000:00:1f.2: reg 20: [io  0xbfa0-0xbfaf]
[    0.290177] pci 0000:00:1f.2: PME# supported from D3hot
[    0.290182] pci 0000:00:1f.2: PME# disabled
[    0.290200] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.290277] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
[    0.290388] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.290394] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.290399] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.290408] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.290498] pci 0000:0c:00.0: [14e4:4311] type 0 class 0x000280
[    0.290522] pci 0000:0c:00.0: reg 10: [mem 0xefdfc000-0xefdfffff]
[    0.290660] pci 0000:0c:00.0: supports D1 D2
[    0.290690] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.290704] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.290710] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.290716] pci 0000:00:1c.1:   bridge window [mem 0xefd00000-0xefdfffff]
[    0.290725] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.290855] pci 0000:09:00.0: [14e4:1600] type 0 class 0x000200
[    0.290888] pci 0000:09:00.0: reg 10: [mem 0xefcf0000-0xefcfffff 64bit]
[    0.291023] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.291029] pci 0000:09:00.0: PME# disabled
[    0.291052] pci 0000:09:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.291065] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.291070] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.291075] pci 0000:00:1c.2:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.291084] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.291136] pci 0000:03:01.0: [1217:6972] type 2 class 0x000607
[    0.291163] pci 0000:03:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.291193] pci 0000:03:01.0: supports D1 D2
[    0.291195] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.291201] pci 0000:03:01.0: PME# disabled
[    0.291269] pci 0000:00:1e.0: PCI bridge to [bus 03-04] (subtractive decode)
[    0.291275] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.291280] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.291289] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.291292] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.291294] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.291297] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.291300] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.291302] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xefffffff] (subtractive decode)
[    0.291305] pci 0000:00:1e.0:   bridge window [mem 0xf4007000-0xf4007fff] (subtractive decode)
[    0.291308] pci 0000:00:1e.0:   bridge window [mem 0xf400c000-0xfebfffff] (subtractive decode)
[    0.291310] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.291313] pci 0000:00:1e.0:   bridge window [mem 0xfed00400-0xfed1ffff] (subtractive decode)
[    0.291316] pci 0000:00:1e.0:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
[    0.291318] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xffafffff] (subtractive decode)
[    0.291372] pci_bus 0000:04: [bus 04-07] partially hidden behind transparent bridge 0000:03 [bus 03-04]
[    0.291403] pci_bus 0000:00: on NUMA node 0
[    0.291407] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.291746] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.291842] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.291902] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.291962] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
[    0.292004]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.303298] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.303383] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.303461] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    0.303526] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    0.303604] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.303686] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.303767] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.303848] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.303977] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.303992] vgaarb: loaded
[    0.304245] SCSI subsystem initialized
[    0.304319] libata version 3.00 loaded.
[    0.304371] usbcore: registered new interface driver usbfs
[    0.304384] usbcore: registered new interface driver hub
[    0.304414] usbcore: registered new device driver usb
[    0.304676] wmi: Mapper loaded
[    0.304678] PCI: Using ACPI for IRQ routing
[    0.304681] PCI: pci_cache_line_size set to 64 bytes
[    0.304782] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.304784] reserve RAM buffer: 000000007f681400 - 000000007fffffff 
[    0.304894] NetLabel: Initializing
[    0.304896] NetLabel:  domain hash size = 128
[    0.304898] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.304910] NetLabel:  unlabeled traffic allowed by default
[    0.304951] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.304958] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.304964] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.308236] Switching to clocksource hpet
[    0.311712] Switched to NOHz mode on CPU #0
[    0.311772] Switched to NOHz mode on CPU #1
[    0.316890] AppArmor: AppArmor Filesystem Enabled
[    0.316922] pnp: PnP ACPI init
[    0.316948] ACPI: bus type pnp registered
[    0.326866] pnp 00:00: [mem 0x00000000-0x0009fbff]
[    0.326870] pnp 00:00: [mem 0x0009fc00-0x0009ffff]
[    0.326872] pnp 00:00: [mem 0x000c0000-0x000cffff]
[    0.326875] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.326877] pnp 00:00: [mem 0x00100000-0x7f6813ff]
[    0.326879] pnp 00:00: [mem 0x7f681400-0x7f6fffff]
[    0.326882] pnp 00:00: [mem 0x7f700000-0x7f7fffff]
[    0.326884] pnp 00:00: [mem 0x7f700000-0x7fefffff]
[    0.326886] pnp 00:00: [mem 0xffb00000-0xffffffff]
[    0.326889] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
[    0.326891] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
[    0.326893] pnp 00:00: [mem 0xfed20000-0xfed3ffff]
[    0.326896] pnp 00:00: [mem 0xfed45000-0xfed9ffff]
[    0.326898] pnp 00:00: [mem 0xffa80000-0xffa83fff]
[    0.326900] pnp 00:00: [mem 0xf4000000-0xf4003fff]
[    0.326902] pnp 00:00: [mem 0xf4004000-0xf4004fff]
[    0.326904] pnp 00:00: [mem 0xf4005000-0xf4005fff]
[    0.326907] pnp 00:00: [mem 0xf4006000-0xf4006fff]
[    0.326909] pnp 00:00: [mem 0xf4008000-0xf400bfff]
[    0.326911] pnp 00:00: [mem 0xf0000000-0xf3ffffff]
[    0.327000] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.327004] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.327007] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.327010] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.327013] system 00:00: [mem 0x00100000-0x7f6813ff] could not be reserved
[    0.327016] system 00:00: [mem 0x7f681400-0x7f6fffff] has been reserved
[    0.327019] system 00:00: [mem 0x7f700000-0x7f7fffff] has been reserved
[    0.327022] system 00:00: [mem 0x7f700000-0x7fefffff] could not be reserved
[    0.327025] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.327028] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.327031] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.327034] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.327037] system 00:00: [mem 0xfed45000-0xfed9ffff] has been reserved
[    0.327040] system 00:00: [mem 0xffa80000-0xffa83fff] could not be reserved
[    0.327043] system 00:00: [mem 0xf4000000-0xf4003fff] has been reserved
[    0.327046] system 00:00: [mem 0xf4004000-0xf4004fff] has been reserved
[    0.327048] system 00:00: [mem 0xf4005000-0xf4005fff] has been reserved
[    0.327051] system 00:00: [mem 0xf4006000-0xf4006fff] has been reserved
[    0.327054] system 00:00: [mem 0xf4008000-0xf400bfff] has been reserved
[    0.327057] system 00:00: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.327061] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.332935] pnp 00:01: [bus 00-ff]
[    0.332939] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.332941] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.332944] pnp 00:01: [io  0x0d00-0xffff window]
[    0.332947] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.332949] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.332952] pnp 00:01: [mem 0x80000000-0xefffffff window]
[    0.332954] pnp 00:01: [mem 0xf4007000-0xf4007fff window]
[    0.332957] pnp 00:01: [mem 0xf400c000-0xfebfffff window]
[    0.332959] pnp 00:01: [mem 0xfec10000-0xfecfffff window]
[    0.332962] pnp 00:01: [mem 0xfed00400-0xfed1ffff window]
[    0.332967] pnp 00:01: [mem 0xfed40000-0xfed44fff window]
[    0.332970] pnp 00:01: [mem 0xfeda0000-0xfed9ffff window disabled]
[    0.332973] pnp 00:01: [mem 0xfee10000-0xffafffff window]
[    0.333072] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.333092] pnp 00:02: [io  0x0092]
[    0.333094] pnp 00:02: [io  0x00b2]
[    0.333096] pnp 00:02: [io  0x0020-0x0021]
[    0.333098] pnp 00:02: [io  0x00a0-0x00a1]
[    0.333101] pnp 00:02: [irq 0 disabled]
[    0.333103] pnp 00:02: [io  0x04d0-0x04d1]
[    0.333105] pnp 00:02: [io  0x1000-0x1005]
[    0.333107] pnp 00:02: [io  0x1008-0x100f]
[    0.333128] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.333131] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.333173] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.333177] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.333195] pnp 00:03: [io  0xf400-0xf4fe]
[    0.333197] pnp 00:03: [io  0x0086]
[    0.333199] pnp 00:03: [io  0x00b3]
[    0.333201] pnp 00:03: [io  0x1006-0x1007]
[    0.333203] pnp 00:03: [io  0x100a-0x1059]
[    0.333205] pnp 00:03: [io  0x1060-0x107f]
[    0.333207] pnp 00:03: [io  0x1080-0x10bf]
[    0.333209] pnp 00:03: [io  0x10c0-0x10df]
[    0.333211] pnp 00:03: [io  0x1010-0x102f]
[    0.333213] pnp 00:03: [io  0x0809]
[    0.333231] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.333234] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.333237] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.333241] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.333282] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.333285] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.333288] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.333291] system 00:03: [io  0x0809] has been reserved
[    0.333294] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.333328] pnp 00:04: [irq 12]
[    0.333366] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.333383] pnp 00:05: [io  0x0060]
[    0.333386] pnp 00:05: [io  0x0064]
[    0.333388] pnp 00:05: [io  0x0062]
[    0.333390] pnp 00:05: [io  0x0066]
[    0.333396] pnp 00:05: [irq 1]
[    0.333433] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.333449] pnp 00:06: [io  0x0070-0x0071]
[    0.333455] pnp 00:06: [irq 8]
[    0.333457] pnp 00:06: [io  0x0072-0x0077]
[    0.333490] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.333509] pnp 00:07: [io  0x0061]
[    0.333511] pnp 00:07: [io  0x0063]
[    0.333513] pnp 00:07: [io  0x0065]
[    0.333515] pnp 00:07: [io  0x0067]
[    0.333549] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.333566] pnp 00:08: [io  0x002e-0x002f]
[    0.333568] pnp 00:08: [io  0x0c80-0x0caf]
[    0.333571] pnp 00:08: [io  0x0cc0-0x0cff]
[    0.333573] pnp 00:08: [io  0x004e-0x004f]
[    0.333575] pnp 00:08: [io  0x0910-0x091f]
[    0.333577] pnp 00:08: [io  0x0920-0x092f]
[    0.333579] pnp 00:08: [io  0x0cbc-0x0cbf]
[    0.333581] pnp 00:08: [io  0x0930-0x097f]
[    0.333640] system 00:08: [io  0x0c80-0x0caf] has been reserved
[    0.333643] system 00:08: [io  0x0cc0-0x0cff] could not be reserved
[    0.333646] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.333648] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.333651] system 00:08: [io  0x0cbc-0x0cbf] has been reserved
[    0.333654] system 00:08: [io  0x0930-0x097f] has been reserved
[    0.333658] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.333678] pnp 00:09: [dma 4]
[    0.333680] pnp 00:09: [io  0x0000-0x000f]
[    0.333682] pnp 00:09: [io  0x0080-0x0085]
[    0.333684] pnp 00:09: [io  0x0087-0x008f]
[    0.333686] pnp 00:09: [io  0x00c0-0x00df]
[    0.333688] pnp 00:09: [io  0x0010-0x001f]
[    0.333690] pnp 00:09: [io  0x0090-0x0091]
[    0.333692] pnp 00:09: [io  0x0093-0x009f]
[    0.333727] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.333744] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.333750] pnp 00:0a: [irq 13]
[    0.333785] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.333834] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.333890] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.333894] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.340030] pnp 00:0c: [irq 4]
[    0.340033] pnp 00:0c: [io  0x03f8-0x03ff]
[    0.340108] pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.350079] pnp 00:0d: [mem 0xfed40000-0xfed44fff]
[    0.350082] pnp 00:0d: [io  0x0cb0-0x0cbb]
[    0.350145] system 00:0d: [io  0x0cb0-0x0cbb] has been reserved
[    0.350149] system 00:0d: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.350152] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.351434] pnp: PnP ACPI: found 14 devices
[    0.351436] ACPI: ACPI bus type pnp unregistered
[    0.351440] PnPBIOS: Disabled by ACPI PNP
[    0.388117] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.388123] pci 0000:00:1e.0: BAR 14: assigned [mem 0x84000000-0x89ffffff]
[    0.388126] pci 0000:00:1c.0: BAR 14: assigned [mem 0x8a000000-0x8a1fffff]
[    0.388130] pci 0000:00:1c.0: BAR 15: assigned [mem 0x8a200000-0x8a3fffff 64bit pref]
[    0.388134] pci 0000:00:1c.1: BAR 15: assigned [mem 0x8a400000-0x8a5fffff 64bit pref]
[    0.388138] pci 0000:00:1c.2: BAR 15: assigned [mem 0x8a600000-0x8a7fffff 64bit pref]
[    0.388142] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.388145] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.388149] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.388152] pci 0000:00:1e.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.388154] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.388158] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.388165] pci 0000:00:1c.0:   bridge window [mem 0x8a000000-0x8a1fffff]
[    0.388171] pci 0000:00:1c.0:   bridge window [mem 0x8a200000-0x8a3fffff 64bit pref]
[    0.388179] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.388183] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.388189] pci 0000:00:1c.1:   bridge window [mem 0xefd00000-0xefdfffff]
[    0.388195] pci 0000:00:1c.1:   bridge window [mem 0x8a400000-0x8a5fffff 64bit pref]
[    0.388203] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.388207] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.388214] pci 0000:00:1c.2:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.388219] pci 0000:00:1c.2:   bridge window [mem 0x8a600000-0x8a7fffff 64bit pref]
[    0.388229] pci 0000:03:01.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.388232] pci 0000:03:01.0: BAR 16: assigned [mem 0x84000000-0x87ffffff]
[    0.388235] pci 0000:03:01.0: BAR 0: assigned [mem 0x88000000-0x88000fff]
[    0.388242] pci 0000:03:01.0: BAR 0: set to [mem 0x88000000-0x88000fff] (PCI address [0x88000000-0x88000fff])
[    0.388245] pci 0000:03:01.0: BAR 13: assigned [io  0x5000-0x50ff]
[    0.388248] pci 0000:03:01.0: BAR 14: assigned [io  0x5400-0x54ff]
[    0.388250] pci 0000:03:01.0: CardBus bridge to [bus 04-07]
[    0.388253] pci 0000:03:01.0:   bridge window [io  0x5000-0x50ff]
[    0.388258] pci 0000:03:01.0:   bridge window [io  0x5400-0x54ff]
[    0.388264] pci 0000:03:01.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.388271] pci 0000:03:01.0:   bridge window [mem 0x84000000-0x87ffffff]
[    0.388277] pci 0000:00:1e.0: PCI bridge to [bus 03-04]
[    0.388280] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
[    0.388287] pci 0000:00:1e.0:   bridge window [mem 0x84000000-0x89ffffff]
[    0.388292] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.388334] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.388341] pci 0000:00:1c.0: setting latency timer to 64
[    0.388353] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.388359] pci 0000:00:1c.1: setting latency timer to 64
[    0.388370] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.388376] pci 0000:00:1c.2: setting latency timer to 64
[    0.388385] pci 0000:00:1e.0: setting latency timer to 64
[    0.388394] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.388399] pci 0000:03:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.388408] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.388411] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.388413] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.388416] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.388419] pci_bus 0000:00: resource 8 [mem 0x80000000-0xefffffff]
[    0.388421] pci_bus 0000:00: resource 9 [mem 0xf4007000-0xf4007fff]
[    0.388424] pci_bus 0000:00: resource 10 [mem 0xf400c000-0xfebfffff]
[    0.388426] pci_bus 0000:00: resource 11 [mem 0xfec10000-0xfecfffff]
[    0.388429] pci_bus 0000:00: resource 12 [mem 0xfed00400-0xfed1ffff]
[    0.388432] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.388434] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xffafffff]
[    0.388437] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.388439] pci_bus 0000:0b: resource 1 [mem 0x8a000000-0x8a1fffff]
[    0.388442] pci_bus 0000:0b: resource 2 [mem 0x8a200000-0x8a3fffff 64bit pref]
[    0.388445] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.388447] pci_bus 0000:0c: resource 1 [mem 0xefd00000-0xefdfffff]
[    0.388450] pci_bus 0000:0c: resource 2 [mem 0x8a400000-0x8a5fffff 64bit pref]
[    0.388453] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.388455] pci_bus 0000:09: resource 1 [mem 0xefc00000-0xefcfffff]
[    0.388458] pci_bus 0000:09: resource 2 [mem 0x8a600000-0x8a7fffff 64bit pref]
[    0.388461] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.388463] pci_bus 0000:03: resource 1 [mem 0x84000000-0x89ffffff]
[    0.388466] pci_bus 0000:03: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.388468] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.388471] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.388473] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.388476] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.388479] pci_bus 0000:03: resource 8 [mem 0x80000000-0xefffffff]
[    0.388481] pci_bus 0000:03: resource 9 [mem 0xf4007000-0xf4007fff]
[    0.388484] pci_bus 0000:03: resource 10 [mem 0xf400c000-0xfebfffff]
[    0.388486] pci_bus 0000:03: resource 11 [mem 0xfec10000-0xfecfffff]
[    0.388489] pci_bus 0000:03: resource 12 [mem 0xfed00400-0xfed1ffff]
[    0.388491] pci_bus 0000:03: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.388494] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xffafffff]
[    0.388497] pci_bus 0000:04: resource 0 [io  0x5000-0x50ff]
[    0.388499] pci_bus 0000:04: resource 1 [io  0x5400-0x54ff]
[    0.388502] pci_bus 0000:04: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.388505] pci_bus 0000:04: resource 3 [mem 0x84000000-0x87ffffff]
[    0.388548] NET: Registered protocol family 2
[    0.388629] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.388902] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.389460] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.389716] TCP: Hash tables configured (established 131072 bind 65536)
[    0.389719] TCP reno registered
[    0.389722] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.389733] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.389819] NET: Registered protocol family 1
[    0.389838] pci 0000:00:02.0: Boot video device
[    0.389984] PCI: CLS 64 bytes, default 64
[    0.390234] cpufreq-nforce2: No nForce2 chipset.
[    0.390381] audit: initializing netlink socket (disabled)
[    0.390393] type=2000 audit(1318241696.384:1): initialized
[    0.399648] highmem bounce pool size: 64 pages
[    0.399654] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.401651] VFS: Disk quotas dquot_6.5.2
[    0.401718] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.402441] fuse init (API version 7.16)
[    0.402541] msgmni has been set to 1669
[    0.402799] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.402827] io scheduler noop registered
[    0.402829] io scheduler deadline registered
[    0.402844] io scheduler cfq registered (default)
[    0.402979] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.403044] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.403131] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.403188] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.403275] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.403331] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.403443] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.403471] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.403533] intel_idle: MWAIT substates: 0x22220
[    0.403536] intel_idle: does not run on family 6 model 15
[    0.404136] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.404526] ACPI: AC Adapter [AC] (on-line)
[    0.404624] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.464020] ACPI: Lid Switch [LID]
[    0.464114] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.516018] ACPI: Power Button [PBTN]
[    0.516108] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.516114] ACPI: Sleep Button [SBTN]
[    0.516373] ACPI: acpi_idle registered with cpuidle
[    0.551922] thermal LNXTHERM:00: registered as thermal_zone0
[    0.551926] ACPI: Thermal Zone [THM] (76 C)
[    0.552017] ERST: Table is not found!
[    0.552112] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.577354] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.577361] ACPI: Battery Slot [BAT0] (battery present)
[    0.577388] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.577394] ACPI: Battery Slot [BAT1] (battery absent)
[    0.577432] isapnp: Scanning for PnP cards...
[    0.578198] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.658040] Freeing initrd memory: 17384k freed
[    0.931280] isapnp: No Plug & Play device found
[    1.005081] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.005432] Linux agpgart interface v0.103
[    1.005527] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.005587] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.006968] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.007097] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.008540] brd: module loaded
[    1.009203] loop: module loaded
[    1.009300] i2c-core: driver [adp5520] using legacy suspend method
[    1.009302] i2c-core: driver [adp5520] using legacy resume method
[    1.009415] ata_piix 0000:00:1f.2: version 2.13
[    1.009430] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.009436] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.009474] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.009860] scsi0 : ata_piix
[    1.009971] scsi1 : ata_piix
[    1.011451] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.011454] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.011866] Fixed MDIO Bus: probed
[    1.011908] PPP generic driver version 2.4.2
[    1.011951] tun: Universal TUN/TAP device driver, 1.6
[    1.011953] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.012067] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.012093] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.012108] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.012113] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.012158] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.012206] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.012220] ehci_hcd 0000:00:1d.7: debug port 1
[    1.016099] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.016116] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    1.032018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.032172] hub 1-0:1.0: USB hub found
[    1.032177] hub 1-0:1.0: 8 ports detected
[    1.032274] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.032289] uhci_hcd: USB Universal Host Controller Interface driver
[    1.032314] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.032321] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.032325] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.032371] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.032421] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    1.032560] hub 2-0:1.0: USB hub found
[    1.032565] hub 2-0:1.0: 2 ports detected
[    1.032646] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.032653] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.032656] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.032697] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.032755] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    1.032892] hub 3-0:1.0: USB hub found
[    1.032896] hub 3-0:1.0: 2 ports detected
[    1.032979] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.032986] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.032990] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.033030] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.036066] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    1.036204] hub 4-0:1.0: USB hub found
[    1.036208] hub 4-0:1.0: 2 ports detected
[    1.036287] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.036294] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.036297] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.036339] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.036398] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    1.036531] hub 5-0:1.0: USB hub found
[    1.036535] hub 5-0:1.0: 2 ports detected
[    1.036683] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.039590] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.039596] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.039726] mousedev: PS/2 mouse device common for all mice
[    1.039911] rtc_cmos 00:06: RTC can wake from S4
[    1.039984] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.040031] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.040121] device-mapper: uevent: version 1.0.3
[    1.040206] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    1.040287] device-mapper: multipath: version 1.2.0 loaded
[    1.040290] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.040367] EISA: Probing bus 0 at eisa.0
[    1.040369] EISA: Cannot allocate resource for mainboard
[    1.040371] Cannot allocate resource for EISA slot 1
[    1.040373] Cannot allocate resource for EISA slot 2
[    1.040375] Cannot allocate resource for EISA slot 3
[    1.040377] Cannot allocate resource for EISA slot 4
[    1.040379] Cannot allocate resource for EISA slot 5
[    1.040381] Cannot allocate resource for EISA slot 6
[    1.040383] Cannot allocate resource for EISA slot 7
[    1.040385] Cannot allocate resource for EISA slot 8
[    1.040387] EISA: Detected 0 cards.
[    1.040522] cpuidle: using governor ladder
[    1.040644] cpuidle: using governor menu
[    1.040951] TCP cubic registered
[    1.041089] NET: Registered protocol family 10
[    1.041728] NET: Registered protocol family 17
[    1.041746] Registering the dns_resolver key type
[    1.042529] Using IPI No-Shortcut mode
[    1.042627] PM: Hibernation image not present or could not be loaded.
[    1.042640] registered taskstats version 1
[    1.042956] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.043222]   Magic number: 15:3:224
[    1.043317] rtc_cmos 00:06: setting system clock to 2011-10-10 10:14:57 UTC (1318241697)
[    1.043320] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.043322] EDD information not available.
[    1.172523] ata1.00: ATA-7: Hitachi HTS721080G9SA00, MC4OC10H, max UDMA/100
[    1.172526] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.172638] ata2.00: ATAPI: PHILIPS DVD+/-RW SDVD8820, AD15, max UDMA/33
[    1.188501] ata1.00: configured for UDMA/100
[    1.188658] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72108 MC4O PQ: 0 ANSI: 5
[    1.188799] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.188823] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.188857] sd 0:0:0:0: [sda] Write Protect is off
[    1.188860] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.188896] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.220316] ata2.00: configured for UDMA/33
[    1.228360]  sda: sda1 sda2 sda3 sda4
[    1.228816] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.317550] scsi 1:0:0:0: CD-ROM            PHILIPS  DVD+-RW SDVD8820 AD15 PQ: 0 ANSI: 5
[    1.361752] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.361755] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.361851] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.361908] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.362028] Freeing unused kernel memory: 700k freed
[    1.362291] Write protecting the kernel text: 5192k
[    1.362348] Write protecting the kernel read-only data: 2148k
[    1.385858] <30>udev[70]: starting version 167
[    1.453491] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4
[    1.453554] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.453575] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    1.476790] tg3.c:v3.116 (December 3, 2010)
[    1.476808] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.476819] tg3 0000:09:00.0: setting latency timer to 64
[    1.501103] [drm] Initialized drm 1.1.0 20060810
[    1.540336] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address 00:15:c5:5a:f2:06
[    1.540341] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.540345] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.540348] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.553371] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.553377] i915 0000:00:02.0: setting latency timer to 64
[    1.567553] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.567556] [drm] Driver supports precise vblank timestamp query.
[    1.756029] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.782784] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.783152] [drm] initialized overlay support
[    1.907514] hub 2-2:1.0: USB hub found
[    1.909475] hub 2-2:1.0: 4 ports detected
[    2.152029] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.162370] fbcon: inteldrmfb (fb0) is primary device
[    2.162439] Console: switching to colour frame buffer device 180x56
[    2.162473] fb0: inteldrmfb frame buffer device
[    2.162475] drm: registered panic notifier
[    2.162594] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.364937] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input5
[    2.365060] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.3-1/input0
[    2.365075] usbcore: registered new interface driver usbhid
[    2.365076] usbhid: USB HID core driver
[    2.576038] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    2.753136] hub 4-2:1.0: USB hub found
[    2.754118] hub 4-2:1.0: 3 ports detected
[    2.833474] usb 2-2.3: new full speed USB device using uhci_hcd and address 3
[    2.963505] hub 2-2.3:1.0: USB hub found
[    2.965472] hub 2-2.3:1.0: 3 ports detected
[    3.045121] usb 4-2.1: new full speed USB device using uhci_hcd and address 3
[    3.204142] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2.1/4-2.1:1.0/input/input6
[    3.204237] generic-usb 0003:413C:2010.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.2-2.1/input0
[    3.213191] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2.1/4-2.1:1.1/input/input7
[    3.213274] generic-usb 0003:413C:2010.0003: input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1d.2-2.1/input1
[    3.289474] usb 2-2.3.2: new full speed USB device using uhci_hcd and address 4
[    3.857745] vesafb: framebuffer at 0xd0000000, mapped to 0xf8b00000, using 3072k, total 3072k
[    3.857749] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    3.857751] vesafb: scrolling: redraw
[    3.857754] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    3.857818] fb1: VESA VGA frame buffer device
[    4.441361] uvesafb: Intel Corporation, Intel(r) 82945GM Chipset Family Graphics Controller, Hardware Version 0.0, OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS, VBE v3.0
[    4.444969] uvesafb: VBIOS/hardware supports DDC2 transfers
[    4.457151] uvesafb: monitor limits: vf = 60 Hz, hf = 55 kHz, clk = 87 MHz
[    4.457241] uvesafb: scrolling: redraw
[    4.457245] uvesafb: cannot reserve video memory at 0xd0000000
[    4.457252] uvesafb: probe of uvesafb.0 failed with error -5
[    4.462850] xor: automatically using best checksumming function: pIII_sse
[    4.480016]    pIII_sse  :  7474.000 MB/sec
[    4.480018] xor: using function: pIII_sse (7474.000 MB/sec)
[    4.482640] device-mapper: dm-raid45: initialized v0.2594b
[    9.585786] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   30.927676] <30>udev[348]: starting version 167
[   30.977557] lp: driver loaded but no devices found
[   31.133549] lib80211: common routines for IEEE802.11 drivers
[   31.133553] lib80211_crypt: registered algorithm 'NULL'
[   31.163511] intel_rng: FWH not detected
[   31.241771] type=1400 audit(1318259727.695:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=593 comm="apparmor_parser"
[   31.242659] type=1400 audit(1318259727.695:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=593 comm="apparmor_parser"
[   31.243227] type=1400 audit(1318259727.695:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=593 comm="apparmor_parser"
[   31.289316] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   31.315055] leds_ss4200: no LED devices found
[   31.368843] wl: module license 'MIXED/Proprietary' taints kernel.
[   31.368846] Disabling lock debugging due to kernel taint
[   31.435373] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01c2]
[   31.435400] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   31.496660] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   31.524148] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   31.524215] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   31.524247] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   31.524823] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   31.524831] wl 0000:0c:00.0: setting latency timer to 64
[   31.527456] malloc in abgphy done
[   31.527593] eth%d: 5.100.82.38 driver failed with code 21
[   31.568935] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 18
[   31.568940] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   31.568944] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   31.568954] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   31.568957] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: excluding 0x5000-0x50ff 0x5400-0x54ff
[   31.577259] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x84000000-0x89ffffff]
[   31.577263] pcmcia_socket pcmcia_socket0: cs: memory probe 0x84000000-0x89ffffff: excluding 0x84000000-0x881fffff
[   31.577277] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   31.577280] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   31.600732] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   31.600955] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   31.804160] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input11
[   31.824567] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input12
[   31.911031] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   31.913285] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   31.914170] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   31.914869] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc80-0xcbf
[   31.915462] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   31.915530] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   31.915593] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   31.915663] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   41.749863] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   41.802999] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   41.869992] type=1400 audit(1318259738.323:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=840 comm="apparmor_parser"
[   41.875701] type=1400 audit(1318259738.327:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=841 comm="apparmor_parser"
[   41.878987] type=1400 audit(1318259738.331:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=841 comm="apparmor_parser"
[   41.879556] type=1400 audit(1318259738.331:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=841 comm="apparmor_parser"
[   41.894608] type=1400 audit(1318259738.347:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=846 comm="apparmor_parser"
[   41.897049] type=1400 audit(1318259738.351:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=855 comm="apparmor_parser"
[   41.898083] type=1400 audit(1318259738.351:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=855 comm="apparmor_parser"
[   41.901426] type=1400 audit(1318259738.355:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=856 comm="apparmor_parser"
[   41.909353] type=1400 audit(1318259738.363:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=846 comm="apparmor_parser"
[   41.923905] type=1400 audit(1318259738.375:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=846 comm="apparmor_parser"
[   41.935897] ppdev: user-space parallel port driver
[   41.975522] CIFS: Unknown mount option codepage
[   41.975526] CIFS: Unknown mount option unicode
[   42.015416] CIFS VFS: Error connecting to socket. Aborting operation
[   42.015424] CIFS VFS: cifs_mount failed w/return code = -101
[   42.068692] tg3 0000:09:00.0: irq 44 for MSI/MSI-X
[   42.102936] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.905984] CIFS: Unknown mount option codepage
[   42.905988] CIFS: Unknown mount option unicode
[   42.906017] CIFS VFS: Error connecting to socket. Aborting operation
[   42.906023] CIFS VFS: cifs_mount failed w/return code = -101
[   43.605425] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.796227] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   43.915647] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   43.974804] EXT4-fs (sda2): re-mounted. Opts: commit=0
[   45.345512] tg3 0000:09:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   45.345516] tg3 0000:09:00.0: eth0: Flow control is off for TX and off for RX
[   45.345679] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   45.924542] CIFS: Unknown mount option codepage
[   45.924547] CIFS: Unknown mount option unicode
[   45.924580] CIFS VFS: Error connecting to socket. Aborting operation
[   45.924586] CIFS VFS: cifs_mount failed w/return code = -101
[   49.200329] CIFS: Unknown mount option codepage
[   49.200334] CIFS: Unknown mount option unicode
[   49.375203] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[   49.375210] CIFS VFS: Send error in SessSetup = -13
[   49.375226] CIFS VFS: cifs_mount failed w/return code = -13
[   49.569978] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   49.889027] EXT4-fs (sda2): re-mounted. Opts: commit=0
[   53.104050] CE: hpet increased min_delta_ns to 20113 nsec
[   56.336032] eth0: no IPv6 routers present
]0;psanka@LT-SKumar: ~psanka@LT-SKumar:~$ sudo 1[Klshw -C netwrok[K[K[Korl[Kk
[sudo] password for psanka: 


DMI

   
SMP

   
PA-RISC

       
device-tree

           
SPD

   
memory

      
/proc/cpuinfo

             
CPUID

     
PCI (sysfs)

           
ISA PnP

       
PCMCIA

      
PCMCIA

      
kernel device tree (sysfs)

                          
USB

   
IDE

   
SCSI

    
Network interfaces

                  
Framebuffer devices

                   
Display

       
CPUFreq

       
ABI

   

  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:0

Please advice.

Thank you

---

