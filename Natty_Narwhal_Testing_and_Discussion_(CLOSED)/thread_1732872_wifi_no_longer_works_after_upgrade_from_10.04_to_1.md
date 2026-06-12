---
title: "wifi no longer works after upgrade from 10.04 to 11.04 - Dell Latitude D820"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by p1tbool on 2011-04-18
Hello,

I recently upgraded my ubuntu 64bit version, to get an eye on whats coming next.

It looks great, except that the wifi is not working at all.
I tried to change the drivers like other threads are recommending, but it doesn t see; to work.

Below is some information, that I hope will help to solve this issue.


LSPCI :
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

LSUSB :
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 003 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci -nn | grep 'Wireless Brand' 
returns nothing. I guess that the answer is Broadcom Corporation BCM4311

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:58:cd:8e  
          inet adr:192.168.2.100  Bcast:192.168.2.255  Masque:255.255.255.0
          adr inet6: fe80::219:b9ff:fe58:cd8e/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:27135 erreurs:0 :0 overruns:0 frame:0
          TX packets:19948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:32928042 (32.9 MB) Octets transmis:1848921 (1.8 MB)
          Interruption:18 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:48 erreurs:0 :0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:4570 (4.5 KB) Octets transmis:4570 (4.5 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lsmod
Module                  Size  Used by
isofs                  40283  1 
udf                    93525  0 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_idt      71137  1 
joydev                 17606  0 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
pcmcia                 49166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  514985  3 
dell_wmi               12681  0 
sparse_keymap          13898  1 dell_wmi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
yenta_socket           27846  0 
pcmcia_rsrc            18372  1 yenta_socket
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13827  0 
drm_kms_helper         42136  1 i915
wl                   2568244  0 
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
dcdbas                 14438  1 dell_laptop
psmouse                73535  0 
drm                   227495  4 i915,drm_kms_helper
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14991  1 wl
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  2 udf,firewire_core
tg3                   141750  0 

lsmod | grep "wlan_module_name" ---- returns nothing


```
dmesg :

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=d675664e-ade9-4b9e-a1aa-2ae9257eeb07 ro splash vga=789 quiet splash vt.handoff=7
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
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Dell Inc. Latitude D820                   /0GF470, BIOS A05 12/18/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x7f681 max_arch_pfn = 0x400000000
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
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007f681000
[    0.000000]  0000000000 - 007f600000 page 2M
[    0.000000]  007f600000 - 007f681000 page 4k
[    0.000000] kernel direct mapping tables up to 7f681000 @ 1fffc000-20000000
[    0.000000] RAMDISK: 366e2000 - 37369000
[    0.000000] ACPI: RSDP 00000000000fc070 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000000007f6819cc 00044 (v01 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: FACP 000000007f682800 00074 (v01 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: DSDT 000000007f683400 05495 (v01 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 000000007f691c00 00040
[    0.000000] ACPI: HPET 000000007f682f00 00038 (v01 DELL    M07     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 000000007f683000 00068 (v01 DELL    M07     27D60C12 ASL  00000047)
[    0.000000] ACPI: ASF! 000000007f682c00 0005B (v16 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: MCFG 000000007f682fc0 0003E (v16 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: SLIC 000000007f68309c 00176 (v01 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: TCPA 000000007f683300 00032 (v01 DELL    M07     27D60C12 ASL  00000061)
[    0.000000] ACPI: SSDT 000000007f681a53 004DC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007f681000
[    0.000000] Initmem setup node 0 0000000000000000-000000007f681000
[    0.000000]   NODE_DATA [000000007f67c000 - 000000007f680fff]
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff88007ce00000-ffff88007e9fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f681
[    0.000000] On node 0 totalpages: 521744
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7079 pages used for memmap
[    0.000000]   DMA32 zone: 510682 pages, LIFO batch:31
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
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007f400000 s84416 r8192 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514603
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=d675664e-ade9-4b9e-a1aa-2ae9257eeb07 ro splash vga=789 quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2031784k/2087428k available (5940k kernel code, 452k absent, 55192k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 20971520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1828.828 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.65 BogoMIPS (lpj=18288280)
[    0.010010] pid_max: default: 32768 minimum: 301
[    0.010045] Security Framework initialized
[    0.010069] AppArmor: AppArmor initialized
[    0.010071] Yama: becoming mindful.
[    0.010385] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011778] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.012636] Mount-cache hash table entries: 256
[    0.012827] Initializing cgroup subsys ns
[    0.012833] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.012837] Initializing cgroup subsys cpuacct
[    0.012842] Initializing cgroup subsys memory
[    0.012854] Initializing cgroup subsys devices
[    0.012857] Initializing cgroup subsys freezer
[    0.012859] Initializing cgroup subsys net_cls
[    0.012862] Initializing cgroup subsys blkio
[    0.012911] CPU: Physical Processor ID: 0
[    0.012913] CPU: Processor Core ID: 0
[    0.012916] mce: CPU supports 6 MCE banks
[    0.012927] CPU0: Thermal monitoring enabled (TM2)
[    0.012933] using mwait in idle threads.
[    0.016092] ACPI: Core revision 20110112
[    0.023217] ftrace: allocating 24314 entries in 96 pages
[    0.030078] Setting APIC routing to flat
[    0.030456] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.138217] CPU0: Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz stepping 06
[    0.140000] Performance Events: PEBS fmt0-, Core2 events, Intel PMU driver.
[    0.140000] PEBS disabled due to CPU errata.
[    0.140000] ... version:                2
[    0.140000] ... bit width:              40
[    0.140000] ... generic registers:      2
[    0.140000] ... value mask:             000000ffffffffff
[    0.140000] ... max period:             000000007fffffff
[    0.140000] ... fixed-purpose events:   3
[    0.140000] ... event mask:             0000000700000003
[    0.140000] Booting Node   0, Processors  #1 Ok.
[    0.300000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.300000] Measured 3946860742 cycles TSC warp between CPUs, turning off TSC clock.
[    0.300000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.300024] Brought up 2 CPUs
[    0.300028] Total of 2 processors activated (7315.18 BogoMIPS).
[    0.300617] devtmpfs: initialized
[    0.301048] print_constraints: dummy: 
[    0.301083] Time: 14:21:56  Date: 04/18/11
[    0.301125] NET: Registered protocol family 16
[    0.301161] Trying to unpack rootfs image as initramfs...
[    0.301277] ACPI: bus type pci registered
[    0.301359] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.301363] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.308551] PCI: Using configuration type 1 for base access
[    0.308563] dmi type 0xB1 record - unknown flag
[    0.320320] bio: create slab <bio-0> at 0
[    0.321481] ACPI: EC: Look up EC in DSDT
[    0.329651] ACPI Warning: Incorrect checksum in table [TCPA] - 0x00, should be 0x93 (20110112/tbutils-314)
[    0.329659] ACPI: SSDT 000000007f681a10 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.330116] ACPI: Dynamic OEM Table Load:
[    0.330120] ACPI: SSDT           (null) 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.330440] ACPI: SSDT 000000007f68217a 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.330734] ACPI: Dynamic OEM Table Load:
[    0.330738] ACPI: SSDT           (null) 00202 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.330856] ACPI: SSDT 000000007f681f2f 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.331132] ACPI: Dynamic OEM Table Load:
[    0.331136] ACPI: SSDT           (null) 001C6 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.331392] ACPI: SSDT 000000007f68237c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.331679] ACPI: Dynamic OEM Table Load:
[    0.331683] ACPI: SSDT           (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.331789] ACPI: SSDT 000000007f6820f5 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.332070] ACPI: Dynamic OEM Table Load:
[    0.332074] ACPI: SSDT           (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.332295] ACPI: Interpreter enabled
[    0.332299] ACPI: (supports S0 S3 S4 S5)
[    0.332321] ACPI: Using IOAPIC for interrupt routing
[    0.455917] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.455924] HEST: Table not found.
[    0.455930] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.461512] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.472589] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.472594] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.472597] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.472600] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.472603] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xefffffff] (ignored)
[    0.472606] pci_root PNP0A03:00: host bridge window [mem 0xf4007000-0xf4007fff] (ignored)
[    0.472609] pci_root PNP0A03:00: host bridge window [mem 0xf400c000-0xfebfffff] (ignored)
[    0.472612] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff] (ignored)
[    0.472615] pci_root PNP0A03:00: host bridge window [mem 0xfed00400-0xfed1ffff] (ignored)
[    0.472618] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
[    0.472621] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xffafffff] (ignored)
[    0.472638] pci 0000:00:00.0: [8086:27a0] type 0 class 0x000600
[    0.472694] pci 0000:00:02.0: [8086:27a2] type 0 class 0x000300
[    0.472707] pci 0000:00:02.0: reg 10: [mem 0xeff00000-0xeff7ffff]
[    0.472715] pci 0000:00:02.0: reg 14: [io  0xeff8-0xefff]
[    0.472722] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.472730] pci 0000:00:02.0: reg 1c: [mem 0xefec0000-0xefefffff]
[    0.472775] pci 0000:00:02.1: [8086:27a6] type 0 class 0x000380
[    0.472786] pci 0000:00:02.1: reg 10: [mem 0xeff80000-0xefffffff]
[    0.472900] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.472924] pci 0000:00:1b.0: reg 10: [mem 0xefebc000-0xefebffff 64bit]
[    0.473011] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.473017] pci 0000:00:1b.0: PME# disabled
[    0.473052] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.473143] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.473149] pci 0000:00:1c.0: PME# disabled
[    0.473183] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.473273] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.473278] pci 0000:00:1c.1: PME# disabled
[    0.473311] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.473403] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.473409] pci 0000:00:1c.2: PME# disabled
[    0.473442] pci 0000:00:1c.3: [8086:27d6] type 1 class 0x000604
[    0.473531] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.473537] pci 0000:00:1c.3: PME# disabled
[    0.473571] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.473633] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
[    0.473677] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.473736] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
[    0.473778] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.473838] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
[    0.473881] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.473940] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
[    0.473998] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.474025] pci 0000:00:1d.7: reg 10: [mem 0xffa80000-0xffa803ff]
[    0.474119] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.474125] pci 0000:00:1d.7: PME# disabled
[    0.474150] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.474242] pci 0000:00:1f.0: [8086:27b9] type 0 class 0x000601
[    0.474361] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.474369] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.474374] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.474380] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.474432] pci 0000:00:1f.2: [8086:27c4] type 0 class 0x000101
[    0.474455] pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
[    0.474468] pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
[    0.474481] pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
[    0.474494] pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
[    0.474506] pci 0000:00:1f.2: reg 20: [io  0xbfa0-0xbfaf]
[    0.474554] pci 0000:00:1f.2: PME# supported from D3hot
[    0.474560] pci 0000:00:1f.2: PME# disabled
[    0.474580] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.474657] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
[    0.474769] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.474775] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.474781] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.474791] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.474928] pci 0000:0c:00.0: [14e4:4311] type 0 class 0x000280
[    0.474995] pci 0000:0c:00.0: reg 10: [mem 0xefdfc000-0xefdfffff]
[    0.475385] pci 0000:0c:00.0: supports D1 D2
[    0.475469] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.475498] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.475503] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.475509] pci 0000:00:1c.1:   bridge window [mem 0xefd00000-0xefdfffff]
[    0.475518] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.475648] pci 0000:09:00.0: [14e4:1600] type 0 class 0x000200
[    0.475682] pci 0000:09:00.0: reg 10: [mem 0xefcf0000-0xefcfffff 64bit]
[    0.475817] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.475823] pci 0000:09:00.0: PME# disabled
[    0.475846] pci 0000:09:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.475859] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.475865] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.475871] pci 0000:00:1c.2:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.475879] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.475946] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.475951] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.475957] pci 0000:00:1c.3:   bridge window [mem 0xefa00000-0xefbfffff]
[    0.475966] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.476018] pci 0000:03:01.0: [1217:7135] type 2 class 0x000607
[    0.476045] pci 0000:03:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.476075] pci 0000:03:01.0: supports D1 D2
[    0.476078] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.476084] pci 0000:03:01.0: PME# disabled
[    0.476117] pci 0000:03:01.4: [1217:00f7] type 0 class 0x000c00
[    0.476139] pci 0000:03:01.4: reg 10: [mem 0xef9ff000-0xef9fffff]
[    0.476152] pci 0000:03:01.4: reg 14: [mem 0xef9fe800-0xef9fefff]
[    0.476230] pci 0000:03:01.4: supports D1 D2
[    0.476232] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.476238] pci 0000:03:01.4: PME# disabled
[    0.476308] pci 0000:00:1e.0: PCI bridge to [bus 03-04] (subtractive decode)
[    0.476314] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.476320] pci 0000:00:1e.0:   bridge window [mem 0xef900000-0xef9fffff]
[    0.476329] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.476332] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.476335] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.476390] pci_bus 0000:04: [bus 04-07] partially hidden behind transparent bridge 0000:03 [bus 03-04]
[    0.476432] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.476731] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.476816] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.476871] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.476924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PXP0._PRT]
[    0.476958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.477016]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.490261] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.490346] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.490427] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    0.490506] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.490586] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.490669] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.490751] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.490834] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.491000] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.491018] vgaarb: loaded
[    0.491255] SCSI subsystem initialized
[    0.491343] libata version 3.00 loaded.
[    0.491406] usbcore: registered new interface driver usbfs
[    0.491419] usbcore: registered new interface driver hub
[    0.491454] usbcore: registered new device driver usb
[    0.491738] wmi: Mapper loaded
[    0.491740] PCI: Using ACPI for IRQ routing
[    0.491744] PCI: pci_cache_line_size set to 64 bytes
[    0.491860] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.491863] reserve RAM buffer: 000000007f681400 - 000000007fffffff 
[    0.491999] NetLabel: Initializing
[    0.492001] NetLabel:  domain hash size = 128
[    0.492003] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.492018] NetLabel:  unlabeled traffic allowed by default
[    0.492061] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.492068] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.492073] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.510124] Switching to clocksource hpet
[    0.519487] Switched to NOHz mode on CPU #0
[    0.519616] Switched to NOHz mode on CPU #1
[    0.520049] AppArmor: AppArmor Filesystem Enabled
[    0.520095] pnp: PnP ACPI init
[    0.520118] ACPI: bus type pnp registered
[    0.529099] pnp 00:00: [mem 0x00000000-0x0009fbff]
[    0.529103] pnp 00:00: [mem 0x0009fc00-0x0009ffff]
[    0.529106] pnp 00:00: [mem 0x000c0000-0x000cffff]
[    0.529108] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.529111] pnp 00:00: [mem 0x00100000-0x7f6813ff]
[    0.529113] pnp 00:00: [mem 0x7f681400-0x7f6fffff]
[    0.529116] pnp 00:00: [mem 0x7f700000-0x7f7fffff]
[    0.529123] pnp 00:00: [mem 0x7f700000-0x7fefffff]
[    0.529126] pnp 00:00: [mem 0xffb00000-0xffffffff]
[    0.529128] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
[    0.529131] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
[    0.529133] pnp 00:00: [mem 0xfed20000-0xfed3ffff]
[    0.529136] pnp 00:00: [mem 0xfed45000-0xfed9ffff]
[    0.529138] pnp 00:00: [mem 0xffa80000-0xffa83fff]
[    0.529140] pnp 00:00: [mem 0xf4000000-0xf4003fff]
[    0.529143] pnp 00:00: [mem 0xf4004000-0xf4004fff]
[    0.529145] pnp 00:00: [mem 0xf4005000-0xf4005fff]
[    0.529148] pnp 00:00: [mem 0xf4006000-0xf4006fff]
[    0.529151] pnp 00:00: [mem 0xf4008000-0xf400bfff]
[    0.529153] pnp 00:00: [mem 0xf0000000-0xf3ffffff]
[    0.529265] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.529269] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.529272] system 00:00: [mem 0x000c0000-0x000cffff] has been reserved
[    0.529275] system 00:00: [mem 0x000e0000-0x000fffff] has been reserved
[    0.529278] system 00:00: [mem 0x00100000-0x7f6813ff] could not be reserved
[    0.529281] system 00:00: [mem 0x7f681400-0x7f6fffff] has been reserved
[    0.529285] system 00:00: [mem 0x7f700000-0x7f7fffff] has been reserved
[    0.529288] system 00:00: [mem 0x7f700000-0x7fefffff] could not be reserved
[    0.529291] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.529294] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.529298] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.529301] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.529304] system 00:00: [mem 0xfed45000-0xfed9ffff] has been reserved
[    0.529307] system 00:00: [mem 0xffa80000-0xffa83fff] could not be reserved
[    0.529310] system 00:00: [mem 0xf4000000-0xf4003fff] has been reserved
[    0.529313] system 00:00: [mem 0xf4004000-0xf4004fff] has been reserved
[    0.529316] system 00:00: [mem 0xf4005000-0xf4005fff] has been reserved
[    0.529320] system 00:00: [mem 0xf4006000-0xf4006fff] has been reserved
[    0.529323] system 00:00: [mem 0xf4008000-0xf400bfff] has been reserved
[    0.529326] system 00:00: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.529331] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.534924] pnp 00:01: [bus 00-ff]
[    0.534929] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.534931] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.534934] pnp 00:01: [io  0x0d00-0xffff window]
[    0.534937] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.534940] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.534942] pnp 00:01: [mem 0x80000000-0xefffffff window]
[    0.534945] pnp 00:01: [mem 0xf4007000-0xf4007fff window]
[    0.534948] pnp 00:01: [mem 0xf400c000-0xfebfffff window]
[    0.534950] pnp 00:01: [mem 0xfec10000-0xfecfffff window]
[    0.534953] pnp 00:01: [mem 0xfed00400-0xfed1ffff window]
[    0.534956] pnp 00:01: [mem 0xfed40000-0xfed44fff window]
[    0.534958] pnp 00:01: [mem 0xfeda0000-0xfed9ffff window disabled]
[    0.534961] pnp 00:01: [mem 0xfee10000-0xffafffff window]
[    0.535059] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.535083] pnp 00:02: [io  0x0092]
[    0.535085] pnp 00:02: [io  0x00b2]
[    0.535087] pnp 00:02: [io  0x0020-0x0021]
[    0.535090] pnp 00:02: [io  0x00a0-0x00a1]
[    0.535092] pnp 00:02: [irq 0 disabled]
[    0.535095] pnp 00:02: [io  0x04d0-0x04d1]
[    0.535097] pnp 00:02: [io  0x1000-0x1005]
[    0.535099] pnp 00:02: [io  0x1008-0x100f]
[    0.535129] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.535133] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.535180] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.535185] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.535205] pnp 00:03: [io  0xf400-0xf4fe]
[    0.535207] pnp 00:03: [io  0x0086]
[    0.535209] pnp 00:03: [io  0x00b3]
[    0.535212] pnp 00:03: [io  0x1006-0x1007]
[    0.535214] pnp 00:03: [io  0x100a-0x1059]
[    0.535216] pnp 00:03: [io  0x1060-0x107f]
[    0.535218] pnp 00:03: [io  0x1080-0x10bf]
[    0.535224] pnp 00:03: [io  0x10c0-0x10df]
[    0.535227] pnp 00:03: [io  0x1010-0x102f]
[    0.535229] pnp 00:03: [io  0x0809]
[    0.535249] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.535253] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.535257] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.535260] pnp 00:03: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.535308] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.535312] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.535315] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.535318] system 00:03: [io  0x0809] has been reserved
[    0.535322] system 00:03: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.535356] pnp 00:04: [irq 12]
[    0.535389] pnp 00:04: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.535408] pnp 00:05: [io  0x0060]
[    0.535411] pnp 00:05: [io  0x0064]
[    0.535413] pnp 00:05: [io  0x0062]
[    0.535415] pnp 00:05: [io  0x0066]
[    0.535421] pnp 00:05: [irq 1]
[    0.535458] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.535477] pnp 00:06: [io  0x0070-0x0071]
[    0.535484] pnp 00:06: [irq 8]
[    0.535487] pnp 00:06: [io  0x0072-0x0077]
[    0.535520] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.535541] pnp 00:07: [io  0x0061]
[    0.535543] pnp 00:07: [io  0x0063]
[    0.535546] pnp 00:07: [io  0x0065]
[    0.535548] pnp 00:07: [io  0x0067]
[    0.535587] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.535608] pnp 00:08: [io  0x002e-0x002f]
[    0.535611] pnp 00:08: [io  0x0c80-0x0caf]
[    0.535613] pnp 00:08: [io  0x0cc0-0x0cff]
[    0.535616] pnp 00:08: [io  0x004e-0x004f]
[    0.535618] pnp 00:08: [io  0x0910-0x091f]
[    0.535620] pnp 00:08: [io  0x0920-0x092f]
[    0.535622] pnp 00:08: [io  0x0cbc-0x0cbf]
[    0.535625] pnp 00:08: [io  0x0930-0x097f]
[    0.535684] system 00:08: [io  0x0c80-0x0caf] has been reserved
[    0.535688] system 00:08: [io  0x0cc0-0x0cff] could not be reserved
[    0.535691] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.535694] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.535697] system 00:08: [io  0x0cbc-0x0cbf] has been reserved
[    0.535700] system 00:08: [io  0x0930-0x097f] has been reserved
[    0.535704] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.535726] pnp 00:09: [dma 4]
[    0.535728] pnp 00:09: [io  0x0000-0x000f]
[    0.535730] pnp 00:09: [io  0x0080-0x0085]
[    0.535732] pnp 00:09: [io  0x0087-0x008f]
[    0.535735] pnp 00:09: [io  0x00c0-0x00df]
[    0.535737] pnp 00:09: [io  0x0010-0x001f]
[    0.535739] pnp 00:09: [io  0x0090-0x0091]
[    0.535741] pnp 00:09: [io  0x0093-0x009f]
[    0.535777] pnp 00:09: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.535802] pnp 00:0a: [io  0x00f0-0x00ff]
[    0.535809] pnp 00:0a: [irq 13]
[    0.535845] pnp 00:0a: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.535901] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
[    0.535961] system 00:0b: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.535966] system 00:0b: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.541023] pnp 00:0c: [irq 4]
[    0.541026] pnp 00:0c: [io  0x03f8-0x03ff]
[    0.541112] pnp 00:0c: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.549232] pnp 00:0d: [mem 0xfed40000-0xfed44fff]
[    0.549235] pnp 00:0d: [io  0x0cb0-0x0cbb]
[    0.549310] system 00:0d: [io  0x0cb0-0x0cbb] has been reserved
[    0.549315] system 00:0d: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.549319] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.550726] pnp: PnP ACPI: found 14 devices
[    0.550729] ACPI: ACPI bus type pnp unregistered
[    0.557549] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.557554] pci 0000:00:1c.0: BAR 14: assigned [mem 0x84000000-0x841fffff]
[    0.557559] pci 0000:00:1c.0: BAR 15: assigned [mem 0x84200000-0x843fffff 64bit pref]
[    0.557563] pci 0000:00:1c.1: BAR 15: assigned [mem 0x84400000-0x845fffff 64bit pref]
[    0.557568] pci 0000:00:1c.2: BAR 15: assigned [mem 0x84600000-0x847fffff 64bit pref]
[    0.557572] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.557576] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.557579] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.557583] pci 0000:00:1e.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.557586] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.557590] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.557597] pci 0000:00:1c.0:   bridge window [mem 0x84000000-0x841fffff]
[    0.557603] pci 0000:00:1c.0:   bridge window [mem 0x84200000-0x843fffff 64bit pref]
[    0.557612] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.557616] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.557623] pci 0000:00:1c.1:   bridge window [mem 0xefd00000-0xefdfffff]
[    0.557628] pci 0000:00:1c.1:   bridge window [mem 0x84400000-0x845fffff 64bit pref]
[    0.557637] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.557641] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.557648] pci 0000:00:1c.2:   bridge window [mem 0xefc00000-0xefcfffff]
[    0.557654] pci 0000:00:1c.2:   bridge window [mem 0x84600000-0x847fffff 64bit pref]
[    0.557663] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.557667] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.557674] pci 0000:00:1c.3:   bridge window [mem 0xefa00000-0xefbfffff]
[    0.557680] pci 0000:00:1c.3:   bridge window [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.557690] pci 0000:03:01.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.557694] pci 0000:03:01.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.557697] pci 0000:03:01.0: BAR 0: assigned [mem 0xef900000-0xef900fff]
[    0.557705] pci 0000:03:01.0: BAR 0: set to [mem 0xef900000-0xef900fff] (PCI address [0xef900000-0xef900fff])
[    0.557708] pci 0000:03:01.0: BAR 13: assigned [io  0x5000-0x50ff]
[    0.557711] pci 0000:03:01.0: BAR 14: assigned [io  0x5400-0x54ff]
[    0.557714] pci 0000:03:01.0: CardBus bridge to [bus 04-07]
[    0.557717] pci 0000:03:01.0:   bridge window [io  0x5000-0x50ff]
[    0.557723] pci 0000:03:01.0:   bridge window [io  0x5400-0x54ff]
[    0.557729] pci 0000:03:01.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.557735] pci 0000:03:01.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.557741] pci 0000:00:1e.0: PCI bridge to [bus 03-04]
[    0.557745] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
[    0.557752] pci 0000:00:1e.0:   bridge window [mem 0xef900000-0xef9fffff]
[    0.557758] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.557791] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.557798] pci 0000:00:1c.0: setting latency timer to 64
[    0.557814] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.557820] pci 0000:00:1c.1: setting latency timer to 64
[    0.557831] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.557837] pci 0000:00:1c.2: setting latency timer to 64
[    0.557848] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.557854] pci 0000:00:1c.3: setting latency timer to 64
[    0.557863] pci 0000:00:1e.0: setting latency timer to 64
[    0.557873] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.557878] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.557887] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.557890] pci_bus 0000:00: resource 1 [mem 0x00000000-0xfffffffff]
[    0.557893] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.557896] pci_bus 0000:0b: resource 1 [mem 0x84000000-0x841fffff]
[    0.557899] pci_bus 0000:0b: resource 2 [mem 0x84200000-0x843fffff 64bit pref]
[    0.557902] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.557904] pci_bus 0000:0c: resource 1 [mem 0xefd00000-0xefdfffff]
[    0.557907] pci_bus 0000:0c: resource 2 [mem 0x84400000-0x845fffff 64bit pref]
[    0.557910] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.557913] pci_bus 0000:09: resource 1 [mem 0xefc00000-0xefcfffff]
[    0.557916] pci_bus 0000:09: resource 2 [mem 0x84600000-0x847fffff 64bit pref]
[    0.557919] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
[    0.557921] pci_bus 0000:0d: resource 1 [mem 0xefa00000-0xefbfffff]
[    0.557924] pci_bus 0000:0d: resource 2 [mem 0xe0000000-0xe01fffff 64bit pref]
[    0.557927] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    0.557930] pci_bus 0000:03: resource 1 [mem 0xef900000-0xef9fffff]
[    0.557933] pci_bus 0000:03: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.557935] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.557938] pci_bus 0000:03: resource 5 [mem 0x00000000-0xfffffffff]
[    0.557941] pci_bus 0000:04: resource 0 [io  0x5000-0x50ff]
[    0.557943] pci_bus 0000:04: resource 1 [io  0x5400-0x54ff]
[    0.557946] pci_bus 0000:04: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.557949] pci_bus 0000:04: resource 3 [mem 0x88000000-0x8bffffff]
[    0.558001] NET: Registered protocol family 2
[    0.558149] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.559036] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.561880] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.562685] TCP: Hash tables configured (established 262144 bind 65536)
[    0.562688] TCP reno registered
[    0.562702] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.562735] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.562910] NET: Registered protocol family 1
[    0.562943] pci 0000:00:02.0: Boot video device
[    0.563115] PCI: CLS 64 bytes, default 64
[    0.563590] audit: initializing netlink socket (disabled)
[    0.563610] type=2000 audit(1303136515.560:1): initialized
[    0.579420] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.581726] VFS: Disk quotas dquot_6.5.2
[    0.581796] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.582574] fuse init (API version 7.16)
[    0.582677] msgmni has been set to 3968
[    0.582967] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.582997] io scheduler noop registered
[    0.583000] io scheduler deadline registered
[    0.583046] io scheduler cfq registered (default)
[    0.583193] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.583261] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.583350] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.583410] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.583501] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.583559] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.583644] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.583701] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.583816] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.583844] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.583897] intel_idle: MWAIT substates: 0x22220
[    0.583899] intel_idle: does not run on family 6 model 15
[    0.584392] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.584830] ACPI: AC Adapter [AC] (on-line)
[    0.584939] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.661711] Freeing initrd memory: 12828k freed
[    0.670048] ACPI: Lid Switch [LID]
[    0.670180] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.700047] ACPI: Power Button [PBTN]
[    0.700113] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.700118] ACPI: Sleep Button [SBTN]
[    0.700399] ACPI: acpi_idle registered with cpuidle
[    0.716940] thermal LNXTHERM:00: registered as thermal_zone0
[    0.716943] ACPI: Thermal Zone [THM] (25 C)
[    0.716966] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.716984] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.717108] ERST: Table is not found!
[    0.717545] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.730559] ACPI: Battery Slot [BAT1] (battery absent)
[    0.736526] ACPI: Battery Slot [BAT0] (battery present)
[    0.740899] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.764279] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.764583] Linux agpgart interface v0.103
[    0.764671] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    0.764765] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.765367] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.765523] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.766925] brd: module loaded
[    0.767568] loop: module loaded
[    0.767677] i2c-core: driver [adp5520] using legacy suspend method
[    0.767679] i2c-core: driver [adp5520] using legacy resume method
[    0.767801] ata_piix 0000:00:1f.2: version 2.13
[    0.767817] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.767824] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.767866] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.768282] scsi0 : ata_piix
[    0.768400] scsi1 : ata_piix
[    0.769838] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.769842] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.770261] Fixed MDIO Bus: probed
[    0.770296] PPP generic driver version 2.4.2
[    0.770343] tun: Universal TUN/TAP device driver, 1.6
[    0.770346] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.770444] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.770472] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.770490] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.770494] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.770539] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.770600] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.770614] ehci_hcd 0000:00:1d.7: debug port 1
[    0.774506] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.774525] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.790019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.790188] hub 1-0:1.0: USB hub found
[    0.790194] hub 1-0:1.0: 8 ports detected
[    0.790299] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.790314] uhci_hcd: USB Universal Host Controller Interface driver
[    0.790377] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.790386] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.790390] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.790433] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.790492] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.790640] hub 2-0:1.0: USB hub found
[    0.790645] hub 2-0:1.0: 2 ports detected
[    0.790732] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.790743] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.790747] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.790803] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.790871] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.791015] hub 3-0:1.0: USB hub found
[    0.791020] hub 3-0:1.0: 2 ports detected
[    0.791103] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.791112] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.791116] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.791158] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.791229] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.791370] hub 4-0:1.0: USB hub found
[    0.791375] hub 4-0:1.0: 2 ports detected
[    0.791458] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.791466] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.791470] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.791517] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.791589] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.791733] hub 5-0:1.0: USB hub found
[    0.791738] hub 5-0:1.0: 2 ports detected
[    0.791885] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.795269] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.795277] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.795423] mousedev: PS/2 mouse device common for all mice
[    0.795603] rtc_cmos 00:06: RTC can wake from S4
[    0.795686] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.795719] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.795841] device-mapper: uevent: version 1.0.3
[    0.795938] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.796032] device-mapper: multipath: version 1.2.0 loaded
[    0.796035] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.796274] cpuidle: using governor ladder
[    0.796384] cpuidle: using governor menu
[    0.796676] TCP cubic registered
[    0.796820] NET: Registered protocol family 10
[    0.797412] NET: Registered protocol family 17
[    0.797437] Registering the dns_resolver key type
[    0.798265] PM: Hibernation image not present or could not be loaded.
[    0.798280] registered taskstats version 1
[    0.798388] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.798917]   Magic number: 7:646:384
[    0.798924] usb usb2: hash matches
[    0.799059] rtc_cmos 00:06: setting system clock to 2011-04-18 14:21:56 UTC (1303136516)
[    0.799063] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.799065] EDD information not available.
[    0.950535] ata1.00: ATA-8: WDC WD1600BEKT-00F3T0, 11.01A11, max UDMA/133
[    0.950541] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    0.960495] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE03, max UDMA/33
[    0.970543] ata1.00: configured for UDMA/133
[    0.970797] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEKT-0 11.0 PQ: 0 ANSI: 5
[    0.971044] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.971049] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.971136] sd 0:0:0:0: [sda] Write Protect is off
[    0.971140] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.971203] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.020296] ata2.00: configured for UDMA/33
[    1.036368]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.036896] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.061503] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE03 PQ: 0 ANSI: 5
[    1.128715] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.128719] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.128833] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.128898] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.131116] Freeing unused kernel memory: 956k freed
[    1.131466] Write protecting the kernel read-only data: 10240k
[    1.132443] Freeing unused kernel memory: 184k freed
[    1.138673] Freeing unused kernel memory: 1444k freed
[    1.162832] <30>udev[69]: starting version 167
[    1.286791] tg3.c:v3.116 (December 3, 2010)
[    1.286814] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.286827] tg3 0000:09:00.0: setting latency timer to 64
[    1.308107] firewire_ohci 0000:03:01.4: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.360159] firewire_ohci: Added fw-ohci device 0000:03:01.4, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x0
[    1.454955] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address 00:19:b9:58:cd:8e
[    1.454961] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.454965] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.454968] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.570076] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.702939] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    1.702943] EXT4-fs (sda6): write access will be enabled during recovery
[    1.750985] hub 3-1:1.0: USB hub found
[    1.752929] hub 3-1:1.0: 3 ports detected
[    1.860248] firewire_core: created device fw0: GUID 374fc000109d4561, S400
[    2.040089] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    2.199643] hub 2-2:1.0: USB hub found
[    2.201552] hub 2-2:1.0: 4 ports detected
[    2.281935] usb 3-1.2: new full speed USB device using uhci_hcd and address 3
[    3.318258] EXT4-fs (sda6): orphan cleanup on readonly fs
[    3.318269] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 44
[    3.318302] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 33
[    3.318313] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 26
[    3.318323] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 22
[    3.318333] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 19
[    3.318341] EXT4-fs (sda6): 5 orphan inodes deleted
[    3.318343] EXT4-fs (sda6): recovery complete
[    3.755132] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.335540] <30>udev[310]: starting version 167
[   15.410773] Adding 2988052k swap on /dev/sda7.  Priority:-1 extents:1 across:2988052k 
[   15.444731] lp: driver loaded but no devices found
[   15.509048] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4
[   15.509194] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   15.509231] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   15.564016] lib80211: common routines for IEEE802.11 drivers
[   15.564020] lib80211_crypt: registered algorithm 'NULL'
[   15.575928] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   15.632357] intel_rng: FWH not detected
[   15.697926] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.697932] Disabling lock debugging due to kernel taint
[   15.739965] type=1400 audit(1303136531.426:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=534 comm="apparmor_parser"
[   15.741041] type=1400 audit(1303136531.436:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=534 comm="apparmor_parser"
[   15.741281] type=1400 audit(1303136531.436:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=546 comm="apparmor_parser"
[   15.741702] type=1400 audit(1303136531.436:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=534 comm="apparmor_parser"
[   15.742327] type=1400 audit(1303136531.436:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=546 comm="apparmor_parser"
[   15.742997] type=1400 audit(1303136531.436:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=546 comm="apparmor_parser"
[   15.786844] leds_ss4200: no LED devices found
[   15.974800] type=1400 audit(1303136531.666:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=642 comm="apparmor_parser"
[   15.983265] type=1400 audit(1303136531.676:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
[   15.983945] type=1400 audit(1303136531.676:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=642 comm="apparmor_parser"
[   15.986243] type=1400 audit(1303136531.676:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=641 comm="apparmor_parser"
[   16.079250] [drm] Initialized drm 1.1.0 20060810
[   16.112057] tg3 0000:09:00.0: irq 44 for MSI/MSI-X
[   16.113391] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.113400] wl 0000:0c:00.0: setting latency timer to 64
[   16.116012] malloc in abgphy done
[   16.116183] eth%d: 5.100.82.38 driver failed with code 21
[   16.123738] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.182974] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.187201] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01cc]
[   16.187228] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   16.335479] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   16.335484] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   16.335489] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   16.348669] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   16.348676] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xef900000-0xef9fffff]
[   16.348681] pcmcia_socket pcmcia_socket0: cs: memory probe 0xef900000-0xef9fffff: excluding 0xef900000-0xef90ffff 0xef9f0000-0xef9fffff
[   16.348701] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   16.348704] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   16.355968] input: Dell WMI hotkeys as /devices/virtual/input/input5
[   16.358605] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.358612] i915 0000:00:02.0: setting latency timer to 64
[   16.429174] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.429178] [drm] Driver supports precise vblank timestamp query.
[   16.494931] composite sync not supported
[   16.513397] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   16.513466] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   16.513534] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   16.648696] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.649064] [drm] initialized overlay support
[   16.784310] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input6
[   16.804844] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input7
[   16.887311] composite sync not supported
[   17.060952] Console: switching to colour frame buffer device 160x50
[   17.060987] fb0: inteldrmfb frame buffer device
[   17.060989] drm: registered panic notifier
[   17.061154] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.061222] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.061227] hda_intel: position_fix set to 1 for device 1028:01cc
[   17.061310] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   17.061349] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.190774] composite sync not supported
[   17.242234] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   17.242514] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.462399] ppdev: user-space parallel port driver
[   17.750651] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   17.750656] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   17.751143] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.872250] composite sync not supported
[   18.247360] composite sync not supported
[   20.001755] composite sync not supported
[   20.369437] composite sync not supported
[   20.743627] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   20.762537] composite sync not supported
[   21.128885] composite sync not supported
[   23.110957] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   28.470096] eth0: no IPv6 routers present
[  754.823003] composite sync not supported
[  755.319798] composite sync not supported
[  755.860487] composite sync not supported
[  758.224307] composite sync not supported
[  758.761884] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  763.197507] composite sync not supported
[  764.778959] composite sync not supported
[ 1052.486658] composite sync not supported
[ 5636.415923] composite sync not supported
[ 9460.613861] UDF-fs: No VRS found
[ 9460.613868] UDF-fs: No partition found (1)
[ 9460.737594] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 9460.892873] ISOFS: changing to secondary root
[ 9738.317278] composite sync not supported
[10949.112807] composite sync not supported

lshw -C network

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
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:58:cd:8e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.19 ip=192.168.2.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:efcf0000-efcfffff
```


iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


lsb_release -d
Description:	Ubuntu Natty (development branch)

uname -mr
2.6.38-8-generic x86_64


sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                   Ignoring unknown interface eth0=eth0.

---

### Post by Iowan on 2011-04-18
Moved to Natty Narwhal Testing and Discussion.

---

### Post by ikt on 2011-04-18
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/732677)

known issue.

---

### Post by p1tbool on 2011-04-19
Thanks to the link above, I have been able to solve the issue.

The solution from Chris Hermansen worked :

[I]My Dell Inspiron 1501 apparently has the same problem with the STA driver, and I can confirm that the workaround proposed by jejbarr for duplicate bug 732038 works for me. Of course this uses the B43 driver, not the STA driver....

What I did:

· used the additional drivers GUI to deactivate the STA driver;
· sudo apt-get install firmware-b43-installer
[/I]

I tried to recompile the drivers, but got a init_MUTEX error. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Thank you for your precious help.

---

