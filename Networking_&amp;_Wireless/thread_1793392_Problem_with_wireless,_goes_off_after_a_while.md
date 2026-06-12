---
title: "Problem with wireless, goes off after a while"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by zvisar on 2011-06-29
I have a big problem with the wireless, it goes down after a while. I have no problem with wired network, nor the problem is with the wireless network (since I can connect with my mobile, while the laptop connection goes down).
These is my information:
Laptop: Fujitsu-Siemens Amilo Pi 2550

```
lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```


```
lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:3d17 Hewlett-Packard LaserJet P1005
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:8d:bb:b3  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe8d:bbb3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80059799 (80.0 MB)  TX bytes:3368643 (3.3 MB)
          Interrupt:45 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2160 (2.1 KB)  TX bytes:2160 (2.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:67:46:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Cauchy"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```


```
lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
snd_hda_codec_si3054    12924  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
iwl3945                72015  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
usblp                  17827  0 
iwl_legacy             70426  1 iwl3945
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              265166  2 iwl3945,iwl_legacy
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
fglrx                2434640  129 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              165555  3 iwl3945,iwl_legacy,mac80211
video                  18951  0 
psmouse                73312  0 
lirc_ite8709           13136  0 
lirc_dev               18720  1 lirc_ite8709
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
r8169                  42534  0 
ahci                   21591  3 
libahci                25548  1 ahci

```

```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fedc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fedc000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: FUJITSU SIEMENS AMILO Pi 2550/F45                             , BIOS 1.11C 03/05/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f8030] f8030
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3677a000 - 373b5000
[    0.000000] ACPI: RSDP 000f8000 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7fed259c 0007C (v01 FSC    PC       06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fed8c6c 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7fed3ae1 05117 (v02 ECS    F45      06040000 INTL 20050624)
[    0.000000] ACPI: FACS 7fedbfc0 00040
[    0.000000] ACPI: HPET 7fed8d60 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fed8d98 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 7fed8dd4 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7fed8dfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7fed8e62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7fed8e8a 00176 (v01 FSC    PC       06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7fed3804 002DD (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed2bd4 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed2b2e 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fed2618 00516 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fed0
[    0.000000] On node 0 totalpages: 523871
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f577a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294340 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519777
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=4c775be1-2adc-4e82-ab1b-4bcb43e8f386 ro vga=792 splash quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fed0)
[    0.000000] Memory: 2046024k/2095936k available (5188k kernel code, 49460k reserved, 2540k data, 700k init, 1186632k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1828.604 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.20 BogoMIPS (lpj=7314416)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004036] Security Framework initialized
[    0.004054] AppArmor: AppArmor initialized
[    0.004056] Yama: becoming mindful.
[    0.004122] Mount-cache hash table entries: 512
[    0.004280] Initializing cgroup subsys ns
[    0.004285] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004288] Initializing cgroup subsys cpuacct
[    0.004294] Initializing cgroup subsys memory
[    0.004304] Initializing cgroup subsys devices
[    0.004307] Initializing cgroup subsys freezer
[    0.004309] Initializing cgroup subsys net_cls
[    0.004312] Initializing cgroup subsys blkio
[    0.004354] CPU: Physical Processor ID: 0
[    0.004356] CPU: Processor Core ID: 0
[    0.004359] mce: CPU supports 6 MCE banks
[    0.004369] CPU0: Thermal monitoring enabled (TM2)
[    0.004373] using mwait in idle threads.
[    0.008737] ACPI: Core revision 20110112
[    0.015558] ftrace: allocating 23640 entries in 47 pages
[    0.016062] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016423] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059685] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
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
[    0.148027] Brought up 2 CPUs
[    0.148030] Total of 2 processors activated (7314.72 BogoMIPS).
[    0.148589] devtmpfs: initialized
[    0.149382] print_constraints: dummy: 
[    0.149417] Time: 16:42:04  Date: 06/29/11
[    0.149461] NET: Registered protocol family 16
[    0.149493] Trying to unpack rootfs image as initramfs...
[    0.149606] EISA bus registered
[    0.149615] ACPI: bus type pci registered
[    0.149704] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149708] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.149711] PCI: Using MMCONFIG for extended config space
[    0.149713] PCI: Using configuration type 1 for base access
[    0.164432] bio: create slab <bio-0> at 0
[    0.165965] ACPI: EC: Look up EC in DSDT
[    0.169327] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.170242] ACPI: SSDT 7fed34c4 00278 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.170666] ACPI: Dynamic OEM Table Load:
[    0.170670] ACPI: SSDT   (null) 00278 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.170862] ACPI: SSDT 7fed2e33 0060C (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.171261] ACPI: Dynamic OEM Table Load:
[    0.171265] ACPI: SSDT   (null) 0060C (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.171593] ACPI: SSDT 7fed373c 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.172017] ACPI: Dynamic OEM Table Load:
[    0.172021] ACPI: SSDT   (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.172156] ACPI: SSDT 7fed343f 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.172556] ACPI: Dynamic OEM Table Load:
[    0.172560] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.252082] ACPI: Interpreter enabled
[    0.252094] ACPI: (supports S0 S3 S4 S5)
[    0.252127] ACPI: Using IOAPIC for interrupt routing
[    0.299215] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.299460] ACPI: No dock devices found.
[    0.299462] HEST: Table not found.
[    0.299467] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.299915] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.300802] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.300806] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.300810] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.300813] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.300817] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.300820] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.300823] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.300826] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.300846] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.300907] pci 0000:00:01.0: [8086:2a01] type 1 class 0x000604
[    0.300954] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.300958] pci 0000:00:01.0: PME# disabled
[    0.301019] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.301083] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.301128] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.301193] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.301255] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.301283] pci 0000:00:1a.7: reg 10: [mem 0xf0404800-0xf0404bff]
[    0.301384] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.301390] pci 0000:00:1a.7: PME# disabled
[    0.301424] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.301450] pci 0000:00:1b.0: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.301548] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.301553] pci 0000:00:1b.0: PME# disabled
[    0.301585] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.301684] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.301690] pci 0000:00:1c.0: PME# disabled
[    0.301727] pci 0000:00:1c.2: [8086:2843] type 1 class 0x000604
[    0.301828] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.301833] pci 0000:00:1c.2: PME# disabled
[    0.301869] pci 0000:00:1c.3: [8086:2845] type 1 class 0x000604
[    0.301969] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.301974] pci 0000:00:1c.3: PME# disabled
[    0.302012] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.302079] pci 0000:00:1d.0: reg 20: [io  0x1840-0x185f]
[    0.302126] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.302192] pci 0000:00:1d.1: reg 20: [io  0x1860-0x187f]
[    0.302236] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.302301] pci 0000:00:1d.2: reg 20: [io  0x1880-0x189f]
[    0.302361] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.302389] pci 0000:00:1d.7: reg 10: [mem 0xf0404c00-0xf0404fff]
[    0.302490] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.302497] pci 0000:00:1d.7: PME# disabled
[    0.302525] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.302624] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.302743] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.302751] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.302757] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0068 (mask 0007)
[    0.302762] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0260 (mask 0003)
[    0.302813] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.302832] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.302846] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.302860] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.302874] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.302887] pci 0000:00:1f.1: reg 20: [io  0x18a0-0x18af]
[    0.302946] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
[    0.302977] pci 0000:00:1f.2: reg 10: [io  0x18d8-0x18df]
[    0.302991] pci 0000:00:1f.2: reg 14: [io  0x18cc-0x18cf]
[    0.303006] pci 0000:00:1f.2: reg 18: [io  0x18d0-0x18d7]
[    0.303020] pci 0000:00:1f.2: reg 1c: [io  0x18c8-0x18cb]
[    0.303034] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.303048] pci 0000:00:1f.2: reg 24: [mem 0xf0404000-0xf04047ff]
[    0.303103] pci 0000:00:1f.2: PME# supported from D3hot
[    0.303108] pci 0000:00:1f.2: PME# disabled
[    0.303133] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.303152] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.303201] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.303298] pci 0000:01:00.0: [1002:94c9] type 0 class 0x000300
[    0.303325] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.303346] pci 0000:01:00.0: reg 18: [mem 0xcfef0000-0xcfefffff 64bit]
[    0.303360] pci 0000:01:00.0: reg 20: [io  0x2000-0x20ff]
[    0.303385] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.303421] pci 0000:01:00.0: supports D1 D2
[    0.308037] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.308042] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.308047] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.308053] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.308127] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.308133] pci 0000:00:1c.0:   bridge window [io  0xf000-0xffff]
[    0.308139] pci 0000:00:1c.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.308148] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.308278] pci 0000:04:00.0: [8086:4222] type 0 class 0x000280
[    0.308334] pci 0000:04:00.0: reg 10: [mem 0xf0200000-0xf0200fff]
[    0.308677] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.308691] pci 0000:04:00.0: PME# disabled
[    0.308762] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.308803] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.308810] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.308816] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.308826] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.308928] pci 0000:05:00.0: [10ec:8136] type 0 class 0x000200
[    0.308955] pci 0000:05:00.0: reg 10: [io  0x3000-0x30ff]
[    0.309001] pci 0000:05:00.0: reg 18: [mem 0xf0300000-0xf0300fff 64bit]
[    0.309054] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.309121] pci 0000:05:00.0: supports D1 D2
[    0.309124] pci 0000:05:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.309131] pci 0000:05:00.0: PME# disabled
[    0.309162] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.309177] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.309183] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.309189] pci 0000:00:1c.3:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.309198] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.309296] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.309303] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.309309] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.309318] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.309321] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.309325] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.309328] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.309331] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.309334] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.309338] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.309341] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.309344] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.309378] pci_bus 0000:00: on NUMA node 0
[    0.309386] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.309662] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.309743] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.309819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.309892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.310005] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.310067]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.317636] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.317706] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.317773] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.317838] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.317905] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.317972] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.318038] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.318104] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.318249] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.318254] vgaarb: loaded
[    0.318522] SCSI subsystem initialized
[    0.318601] libata version 3.00 loaded.
[    0.318665] usbcore: registered new interface driver usbfs
[    0.318680] usbcore: registered new interface driver hub
[    0.318715] usbcore: registered new device driver usb
[    0.318992] wmi: Mapper loaded
[    0.318995] PCI: Using ACPI for IRQ routing
[    0.318998] PCI: pci_cache_line_size set to 64 bytes
[    0.319128] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.319132] reserve RAM buffer: 000000007fed0000 - 000000007fffffff 
[    0.319263] NetLabel: Initializing
[    0.319265] NetLabel:  domain hash size = 128
[    0.319267] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.319281] NetLabel:  unlabeled traffic allowed by default
[    0.319324] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.319331] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.319337] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.328087] Switching to clocksource hpet
[    0.331714] Switched to NOHz mode on CPU #0
[    0.331792] Switched to NOHz mode on CPU #1
[    0.337986] AppArmor: AppArmor Filesystem Enabled
[    0.338025] pnp: PnP ACPI init
[    0.338056] ACPI: bus type pnp registered
[    0.356498] pnp 00:00: [bus 00-ff]
[    0.356503] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.356506] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.356509] pnp 00:00: [io  0x0d00-0xffff window]
[    0.356512] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.356515] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.356518] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.356521] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.356524] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.356527] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.356530] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.356533] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.356536] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.356539] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.356547] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.356550] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.356553] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.356556] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.356559] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.356562] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.356565] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.356695] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.356801] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.356804] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.356807] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.356810] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.356812] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.356815] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.356818] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.356820] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.356897] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.356901] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.356904] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.356908] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.356911] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.356915] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.356918] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.356922] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.356926] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.357235] pnp 00:02: [io  0x0068]
[    0.357238] pnp 00:02: [io  0x006c]
[    0.357241] pnp 00:02: [io  0x0260-0x0261]
[    0.357255] pnp 00:02: [irq 10]
[    0.357322] pnp 00:02: Plug and Play ACPI device, IDs ITE8709 (active)
[    0.357337] pnp 00:03: [io  0x0000-0x001f]
[    0.357339] pnp 00:03: [io  0x0081-0x0091]
[    0.357342] pnp 00:03: [io  0x0093-0x009f]
[    0.357344] pnp 00:03: [io  0x00c0-0x00df]
[    0.357347] pnp 00:03: [dma 4]
[    0.357416] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.357428] pnp 00:04: [mem 0xff000000-0xffffffff]
[    0.357493] pnp 00:04: Plug and Play ACPI device, IDs INT0800 (active)
[    0.357582] pnp 00:05: [mem 0xfed00000-0xfed003ff]
[    0.357675] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.357680] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.357695] pnp 00:06: [io  0x00f0]
[    0.357703] pnp 00:06: [irq 13]
[    0.357771] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.357786] pnp 00:07: [io  0x002e-0x002f]
[    0.357789] pnp 00:07: [io  0x004e-0x004f]
[    0.357791] pnp 00:07: [io  0x0061]
[    0.357794] pnp 00:07: [io  0x0063]
[    0.357796] pnp 00:07: [io  0x0065]
[    0.357799] pnp 00:07: [io  0x0067]
[    0.357801] pnp 00:07: [io  0x0080]
[    0.357803] pnp 00:07: [io  0x0092]
[    0.357806] pnp 00:07: [io  0x00b2-0x00b3]
[    0.357808] pnp 00:07: [io  0x0680-0x069f]
[    0.357811] pnp 00:07: [io  0x0800-0x080f]
[    0.357814] pnp 00:07: [io  0x1000-0x107f]
[    0.357816] pnp 00:07: [io  0x1180-0x11bf]
[    0.357818] pnp 00:07: [io  0x1640-0x164f]
[    0.357821] pnp 00:07: [io  0xfe00]
[    0.357837] pnp 00:07: disabling [io  0xfe00] because it overlaps 0000:00:1c.0 BAR 13 [io  0xf000-0xffff]
[    0.357936] system 00:07: [io  0x0680-0x069f] has been reserved
[    0.357940] system 00:07: [io  0x0800-0x080f] has been reserved
[    0.357943] system 00:07: [io  0x1000-0x107f] has been reserved
[    0.357947] system 00:07: [io  0x1180-0x11bf] has been reserved
[    0.357950] system 00:07: [io  0x1640-0x164f] has been reserved
[    0.357954] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.357967] pnp 00:08: [io  0x0070-0x0077]
[    0.357973] pnp 00:08: [irq 8]
[    0.358041] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.358111] pnp 00:09: [io  0x0060]
[    0.358114] pnp 00:09: [io  0x0064]
[    0.358121] pnp 00:09: [irq 1]
[    0.358192] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.358208] pnp 00:0a: [irq 12]
[    0.358284] pnp 00:0a: Plug and Play ACPI device, IDs SYN0804 SYN0800 PNP0f13 (active)
[    0.358315] pnp: PnP ACPI: found 11 devices
[    0.358317] ACPI: ACPI bus type pnp unregistered
[    0.358322] PnPBIOS: Disabled by ACPI PNP
[    0.395306] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.395312] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.395318] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80400000-0x805fffff pref]
[    0.395322] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.395327] pci 0000:00:1f.3: BAR 0: assigned [mem 0x80600000-0x806000ff]
[    0.395335] pci 0000:00:1f.3: BAR 0: set to [mem 0x80600000-0x806000ff] (PCI address [0x80600000-0x806000ff])
[    0.395340] pci 0000:01:00.0: BAR 6: assigned [mem 0xcfe00000-0xcfe1ffff pref]
[    0.395343] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.395347] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.395352] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.395356] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.395363] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.395367] pci 0000:00:1c.0:   bridge window [io  0xf000-0xffff]
[    0.395375] pci 0000:00:1c.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.395381] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.395391] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.395395] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.395402] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.395408] pci 0000:00:1c.2:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.395419] pci 0000:05:00.0: BAR 6: assigned [mem 0x80400000-0x8041ffff pref]
[    0.395422] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.395426] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.395433] pci 0000:00:1c.3:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.395439] pci 0000:00:1c.3:   bridge window [mem 0x80400000-0x805fffff pref]
[    0.395448] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.395451] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.395458] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.395464] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.395498] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.395504] pci 0000:00:01.0: setting latency timer to 64
[    0.395519] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.395525] pci 0000:00:1c.0: setting latency timer to 64
[    0.395538] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.395544] pci 0000:00:1c.2: setting latency timer to 64
[    0.395557] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.395563] pci 0000:00:1c.3: setting latency timer to 64
[    0.395573] pci 0000:00:1e.0: setting latency timer to 64
[    0.395578] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.395581] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.395584] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.395587] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.395589] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.395592] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.395595] pci_bus 0000:00: resource 10 [mem 0x80000000-0xdfffffff]
[    0.395598] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.395601] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.395604] pci_bus 0000:01: resource 1 [mem 0xcfe00000-0xcfefffff]
[    0.395608] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.395611] pci_bus 0000:02: resource 0 [io  0xf000-0xffff]
[    0.395614] pci_bus 0000:02: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.395617] pci_bus 0000:02: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.395620] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.395623] pci_bus 0000:04: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.395626] pci_bus 0000:04: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.395629] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.395632] pci_bus 0000:05: resource 1 [mem 0xf0300000-0xf03fffff]
[    0.395635] pci_bus 0000:05: resource 2 [mem 0x80400000-0x805fffff pref]
[    0.395638] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.395641] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.395644] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.395647] pci_bus 0000:06: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.395650] pci_bus 0000:06: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.395653] pci_bus 0000:06: resource 9 [mem 0x000dc000-0x000dffff]
[    0.395656] pci_bus 0000:06: resource 10 [mem 0x80000000-0xdfffffff]
[    0.395659] pci_bus 0000:06: resource 11 [mem 0xf0000000-0xfebfffff]
[    0.395711] NET: Registered protocol family 2
[    0.395804] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.396138] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.396687] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.396975] TCP: Hash tables configured (established 131072 bind 65536)
[    0.396978] TCP reno registered
[    0.396982] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.396994] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.397108] NET: Registered protocol family 1
[    0.397311] pci 0000:01:00.0: Boot video device
[    0.397328] PCI: CLS 64 bytes, default 64
[    0.397359] Simple Boot Flag at 0x36 set to 0x1
[    0.397611] cpufreq-nforce2: No nForce2 chipset.
[    0.397785] audit: initializing netlink socket (disabled)
[    0.397798] type=2000 audit(1309365723.392:1): initialized
[    0.409056] highmem bounce pool size: 64 pages
[    0.409063] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.411364] VFS: Disk quotas dquot_6.5.2
[    0.411445] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.412316] fuse init (API version 7.16)
[    0.412433] msgmni has been set to 1678
[    0.412730] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.412761] io scheduler noop registered
[    0.412764] io scheduler deadline registered
[    0.412782] io scheduler cfq registered (default)
[    0.412927] pcieport 0000:00:01.0: setting latency timer to 64
[    0.412975] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.413046] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.413110] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.413206] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.413270] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.413366] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.413430] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.413555] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.413590] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.413668] intel_idle: MWAIT substates: 0x22220
[    0.413670] intel_idle: does not run on family 6 model 15
[    0.414120] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.414626] ACPI: AC Adapter [AC0] (on-line)
[    0.414729] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.414751] ACPI: Lid Switch [LID0]
[    0.414808] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.414813] ACPI: Power Button [PWRB]
[    0.414871] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.414875] ACPI: Sleep Button [SLPB]
[    0.414951] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.414955] ACPI: Power Button [PWRF]
[    0.415189] ACPI: acpi_idle registered with cpuidle
[    0.428031] Monitor-Mwait will be used to enter C-1 state
[    0.428079] Monitor-Mwait will be used to enter C-3 state
[    0.428088] Marking TSC unstable due to TSC halts in idle
[    0.450533] thermal LNXTHERM:00: registered as thermal_zone0
[    0.450537] ACPI: Thermal Zone [THRM] (71 C)
[    0.450564] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.450657] ERST: Table is not found!
[    0.450792] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.451199] isapnp: Scanning for PnP cards...
[    0.486451] Freeing initrd memory: 12524k freed
[    0.501271] ACPI: Battery Slot [BAT0] (battery present)
[    0.805649] isapnp: No Plug & Play device found
[    0.836638] Linux agpgart interface v0.103
[    0.838499] brd: module loaded
[    0.839277] loop: module loaded
[    0.839395] i2c-core: driver [adp5520] using legacy suspend method
[    0.839398] i2c-core: driver [adp5520] using legacy resume method
[    0.839523] ata_piix 0000:00:1f.1: version 2.13
[    0.839539] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.839587] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.840051] scsi0 : ata_piix
[    0.840168] scsi1 : ata_piix
[    0.840694] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.840698] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.841174] Fixed MDIO Bus: probed
[    0.841232] PPP generic driver version 2.4.2
[    0.841280] tun: Universal TUN/TAP device driver, 1.6
[    0.841282] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.841387] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.841406] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.841420] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.841425] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.841472] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.841536] ehci_hcd 0000:00:1a.7: debug port 1
[    0.845417] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.845437] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0404800
[    0.860019] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.860168] hub 1-0:1.0: USB hub found
[    0.860174] hub 1-0:1.0: 4 ports detected
[    0.860281] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.860294] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.860299] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.860350] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.860411] ehci_hcd 0000:00:1d.7: debug port 1
[    0.864309] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.864327] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0404c00
[    0.880019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.880154] hub 2-0:1.0: USB hub found
[    0.880159] hub 2-0:1.0: 6 ports detected
[    0.880259] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.880276] uhci_hcd: USB Universal Host Controller Interface driver
[    0.880304] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.880311] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.880316] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.880365] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.880426] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.880582] hub 3-0:1.0: USB hub found
[    0.880587] hub 3-0:1.0: 2 ports detected
[    0.880685] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.880693] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.880697] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.880752] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.880813] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.880974] hub 4-0:1.0: USB hub found
[    0.880978] hub 4-0:1.0: 2 ports detected
[    0.881069] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.881077] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.881081] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.881126] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.884056] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.884211] hub 5-0:1.0: USB hub found
[    0.884216] hub 5-0:1.0: 2 ports detected
[    0.884303] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.884311] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.884315] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.884363] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.884424] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.884579] hub 6-0:1.0: USB hub found
[    0.884584] hub 6-0:1.0: 2 ports detected
[    0.884683] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.884691] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.884695] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.884742] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.884794] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.884945] hub 7-0:1.0: USB hub found
[    0.884950] hub 7-0:1.0: 2 ports detected
[    0.885115] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.887261] i8042: Detected active multiplexing controller, rev 1.1
[    0.889089] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.889096] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.889136] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.889170] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.889202] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.889355] mousedev: PS/2 mouse device common for all mice
[    0.889664] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.889699] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.889792] device-mapper: uevent: version 1.0.3
[    0.889894] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.889975] device-mapper: multipath: version 1.2.0 loaded
[    0.889979] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.890064] EISA: Probing bus 0 at eisa.0
[    0.890067] EISA: Cannot allocate resource for mainboard
[    0.890070] Cannot allocate resource for EISA slot 1
[    0.890073] Cannot allocate resource for EISA slot 2
[    0.890075] Cannot allocate resource for EISA slot 3
[    0.890077] Cannot allocate resource for EISA slot 4
[    0.890079] Cannot allocate resource for EISA slot 5
[    0.890082] Cannot allocate resource for EISA slot 6
[    0.890084] Cannot allocate resource for EISA slot 7
[    0.890086] Cannot allocate resource for EISA slot 8
[    0.890088] EISA: Detected 0 cards.
[    0.890232] cpuidle: using governor ladder
[    0.890360] cpuidle: using governor menu
[    0.890721] TCP cubic registered
[    0.890890] NET: Registered protocol family 10
[    0.891623] NET: Registered protocol family 17
[    0.891642] Registering the dns_resolver key type
[    0.925596] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.932114] Using IPI No-Shortcut mode
[    0.932228] PM: Hibernation image not present or could not be loaded.
[    0.932248] registered taskstats version 1
[    0.932659]   Magic number: 15:560:743
[    0.932773] rtc_cmos 00:08: setting system clock to 2011-06-29 16:42:04 UTC (1309365724)
[    0.932776] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.932778] EDD information not available.
[    1.028404] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, fs03, max UDMA/33
[    1.060284] ata1.00: configured for UDMA/33
[    1.064665] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  fs03 PQ: 0 ANSI: 5
[    1.071238] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.071241] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.071371] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.071447] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.071607] Freeing unused kernel memory: 700k freed
[    1.071931] Write protecting the kernel text: 5192k
[    1.072016] Write protecting the kernel read-only data: 2148k
[    1.100482] <30>udev[71]: starting version 167
[    1.246043] ahci 0000:00:1f.2: version 3.0
[    1.246061] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.246128] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.246209] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.246213] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.246221] ahci 0000:00:1f.2: setting latency timer to 64
[    1.252061] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    1.253894] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.253921] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.253982] r8169 0000:05:00.0: setting latency timer to 64
[    1.254084] r8169 0000:05:00.0: irq 45 for MSI/MSI-X
[    1.254759] r8169 0000:05:00.0: eth0: RTL8101e at 0xf8024000, 00:03:0d:8d:bb:b3, XID 94200000 IRQ 45
[    1.256144] scsi2 : ahci
[    1.258391] scsi3 : ahci
[    1.260141] scsi4 : ahci
[    1.260357] ata3: SATA max UDMA/133 abar m2048@0xf0404000 port 0xf0404100 irq 44
[    1.260362] ata4: SATA max UDMA/133 abar m2048@0xf0404000 port 0xf0404180 irq 44
[    1.260366] ata5: SATA max UDMA/133 abar m2048@0xf0404000 port 0xf0404200 irq 44
[    1.580060] ata5: SATA link down (SStatus 0 SControl 300)
[    1.580089] ata4: SATA link down (SStatus 0 SControl 300)
[    1.580118] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.580653] ata3.00: unexpected _GTF length (8)
[    1.628952] ata3.00: ATA-8: WDC WD2500BEVS-22UST0, 01.01A01, max UDMA/133
[    1.628956] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.629722] ata3.00: unexpected _GTF length (8)
[    1.629964] ata3.00: configured for UDMA/133
[    1.630134] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
[    1.630351] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.630386] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.630460] sd 2:0:0:0: [sda] Write Protect is off
[    1.630464] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.630497] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.644897]  sda: sda1 < sda5 sda6 > sda3
[    1.645322] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.648033] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.831642] input: HID 062a:0000 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input5
[    1.831794] generic-usb 0003:062A:0000.0001: input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.0-1/input0
[    1.831813] usbcore: registered new interface driver usbhid
[    1.831815] usbhid: USB HID core driver
[    1.978017] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.776845] Adding 1999868k swap on /dev/sda5.  Priority:-1 extents:1 across:1999868k 
[   15.830676] <30>udev[326]: starting version 167
[   15.872265] lp: driver loaded but no devices found
[   16.035254] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   16.035260] Disabling lock debugging due to kernel taint
[   16.098452] lirc_dev: IR Remote Control driver registered, major 250 
[   16.098571] lirc_ite8709: module is from the staging directory, the quality is unknown, you have been warned.
[   16.108539] lirc_ite8709 00:02: lirc_dev: driver lirc_ite8709 registered at minor = 0
[   16.111977] lirc_ite8709: device found : irq=10 io=0x260
[   16.114062] type=1400 audit(1309358539.678:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=524 comm="apparmor_parser"
[   16.115103] type=1400 audit(1309358539.678:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=524 comm="apparmor_parser"
[   16.115761] type=1400 audit(1309358539.678:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=524 comm="apparmor_parser"
[   16.241269] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   16.362552] cfg80211: Calling CRDA to update world regulatory domain
[   16.375040] acpi device:04: registered as cooling_device2
[   16.375069] ACPI: Cant attach device
[   16.375200] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input6
[   16.375309] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   16.508370] cfg80211: World regulatory domain updated:
[   16.508375] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.508379] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.508382] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.508385] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.508388] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.508391] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.535546] [fglrx] Maximum main memory to use for locked dma buffers: 1883 MBytes.
[   16.536078] [fglrx]   vendor: 1002 device: 94c9 count: 1
[   16.536938] [fglrx] ioport: bar 4, base 0x2000, size: 0x100
[   16.536956] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.536963] pci 0000:01:00.0: setting latency timer to 64
[   16.537351] [fglrx] Kernel PAT support is enabled
[   16.537377] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   16.547522] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3D17
[   16.547550] usbcore: registered new interface driver usblp
[   16.570486] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   16.570491] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   16.570565] iwl3945 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.570581] iwl3945 0000:04:00.0: setting latency timer to 64
[   16.614835] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.614932] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   16.614991] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.626291] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   16.626295] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   16.626448] iwl3945 0000:04:00.0: irq 47 for MSI/MSI-X
[   16.626703] Registered led device: phy0-led
[   16.626743] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   16.630673] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   16.670089] hda_codec: ALC883: SKU not ready 0x598301f0
[   16.686339] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   17.010291] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000/0x0
[   17.047503] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   17.821119] type=1400 audit(1309358541.386:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=791 comm="apparmor_parser"
[   17.823816] type=1400 audit(1309358541.386:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=790 comm="apparmor_parser"
[   17.833243] type=1400 audit(1309358541.398:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=791 comm="apparmor_parser"
[   17.833920] type=1400 audit(1309358541.398:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=791 comm="apparmor_parser"
[   17.856389] type=1400 audit(1309358541.422:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=792 comm="apparmor_parser"
[   17.863752] type=1400 audit(1309358541.426:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=802 comm="apparmor_parser"
[   17.877253] type=1400 audit(1309358541.442:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=802 comm="apparmor_parser"
[   17.919095] r8169 0000:05:00.0: eth0: link down
[   17.919103] r8169 0000:05:00.0: eth0: link down
[   17.919342] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.729948] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   19.550880] r8169 0000:05:00.0: eth0: link up
[   19.551082] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.711385] vesafb: framebuffer at 0xd0000000, mapped to 0xf9880000, using 3072k, total 3072k
[   19.711389] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   19.711392] vesafb: scrolling: redraw
[   19.711395] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   19.711584] Console: switching to colour frame buffer device 128x48
[   19.711612] fb0: VESA VGA frame buffer device
[   19.722511] ppdev: user-space parallel port driver
[   20.160116] fglrx_pci 0000:01:00.0: irq 48 for MSI/MSI-X
[   20.161044] [fglrx] Firegl kernel thread PID: 1156
[   20.161155] [fglrx] Firegl kernel thread PID: 1157
[   20.161262] [fglrx] Firegl kernel thread PID: 1158
[   20.161533] [fglrx] IRQ 48 Enabled
[   20.205154] usblp0: removed
[   20.726507] [fglrx] Gart USWC size:628 M.
[   20.726511] [fglrx] Gart cacheable size:247 M.
[   20.726517] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   20.726520] [fglrx] Reserved FB block: Unshared offset:fe03000, size:1f9000 
[   20.726523] [fglrx] Reserved FB block: Unshared offset:fffc000, size:4000 
[   23.608041] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   29.848041] eth0: no IPv6 routers present
[   33.584038] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
[   33.584806] CPU0: Core temperature/speed normal
[  169.028651] exe (2169): /proc/2169/oom_adj is deprecated, please use /proc/2169/oom_score_adj instead.
[  179.555720] ISO 9660 Extensions: Microsoft Joliet Level 3
[  179.575677] ISOFS: changing to secondary root
[  299.988025] [Hardware Error]: Machine check events logged
[  357.107102] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1546)
[  357.107881] CPU0: Core temperature/speed normal
[  449.988047] [Hardware Error]: Machine check events logged
[  657.105177] CPU0: Core temperature above threshold, cpu clock throttled (total events = 135662)
[  674.988067] [Hardware Error]: Machine check events logged
[  957.104925] CPU0: Core temperature above threshold, cpu clock throttled (total events = 155817)
[  957.105706] CPU0: Core temperature/speed normal
[ 1199.988095] [Hardware Error]: Machine check events logged
[ 1273.913445] CPU0: Core temperature above threshold, cpu clock throttled (total events = 157103)
[ 1273.914227] CPU0: Core temperature/speed normal
[ 1349.988055] [Hardware Error]: Machine check events logged
[ 1352.740775] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[ 1352.810937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1360.175751] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 1)
[ 1360.197599] wlan0: authenticated
[ 1360.197634] wlan0: associate with 00:25:9c:b0:c6:73 (try 1)
[ 1360.400071] wlan0: associate with 00:25:9c:b0:c6:73 (try 2)
[ 1360.600726] wlan0: associate with 00:25:9c:b0:c6:73 (try 3)
[ 1360.800048] wlan0: association with 00:25:9c:b0:c6:73 timed out
[ 1373.768969] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1373.968068] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1374.168085] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1374.368079] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1387.360967] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1387.560051] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1387.760076] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1387.960057] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1400.963271] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 1)
[ 1401.160103] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 2)
[ 1401.360075] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 3)
[ 1401.560080] wlan0: authentication with 00:25:9c:b0:c6:73 timed out
[ 1414.557760] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1414.756121] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1414.956088] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1415.156126] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1425.916387] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 1)
[ 1426.116077] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 2)
[ 1426.316098] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 3)
[ 1426.516071] wlan0: authentication with 00:25:9c:b0:c6:73 timed out
[ 1439.510722] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1439.708104] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1439.908087] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1440.108075] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1461.707429] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1461.904082] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1462.104047] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1462.304065] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1475.311089] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 1)
[ 1475.508050] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 2)
[ 1475.580075] wlan0: authenticated
[ 1475.580140] wlan0: associate with 00:25:9c:b0:c6:73 (try 1)
[ 1475.780084] wlan0: associate with 00:25:9c:b0:c6:73 (try 2)
[ 1475.980085] wlan0: associate with 00:25:9c:b0:c6:73 (try 3)
[ 1476.180108] wlan0: association with 00:25:9c:b0:c6:73 timed out
[ 1495.666959] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1495.864085] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1496.064089] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1496.264089] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1509.262883] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1509.460075] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1509.660106] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1509.860104] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1522.851060] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1523.048072] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1523.248089] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1523.448126] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1536.451621] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1536.573463] wlan0: direct probe responded
[ 1536.588066] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 1)
[ 1536.670714] wlan0: authenticated
[ 1536.670778] wlan0: associate with 00:25:9c:b0:c6:73 (try 1)
[ 1536.868102] wlan0: associate with 00:25:9c:b0:c6:73 (try 2)
[ 1537.068105] wlan0: associate with 00:25:9c:b0:c6:73 (try 3)
[ 1537.268102] wlan0: association with 00:25:9c:b0:c6:73 timed out
[ 1550.055760] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1550.252091] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1550.452057] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1550.652088] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1566.249485] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1566.321367] wlan0: direct probe responded
[ 1566.323429] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 1)
[ 1566.520074] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 2)
[ 1566.720126] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 3)
[ 1566.920059] wlan0: authentication with 00:25:9c:b0:c6:73 timed out
[ 1578.647308] CPU0: Core temperature above threshold, cpu clock throttled (total events = 157303)
[ 1578.648097] CPU0: Core temperature/speed normal
[ 1579.855017] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1580.054409] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1580.256054] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1580.456125] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1593.452101] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1593.652054] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1593.852054] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1594.052043] wlan0: direct probe to 00:25:9c:b0:c6:73 timed out
[ 1607.030754] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 1/3)
[ 1607.228079] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 2/3)
[ 1607.428123] wlan0: direct probe to 00:25:9c:b0:c6:73 (try 3/3)
[ 1607.558047] wlan0: direct probe responded
[ 1607.568152] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 1)
[ 1607.768072] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 2)
[ 1607.968110] wlan0: authenticate with 00:25:9c:b0:c6:73 (try 3)
[ 1608.168049] wlan0: authentication with 00:25:9c:b0:c6:73 timed out
[ 1800.000047] [Hardware Error]: Machine check events logged
[ 1912.280122] CPU0: Core temperature above threshold, cpu clock throttled (total events = 157408)
[ 1912.280898] CPU0: Core temperature/speed normal
[ 1950.000080] [Hardware Error]: Machine check events logged

```

```
sudo lshw -C network
[sudo] password for visar: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:67:46:25
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f0200000-f0200fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:8d:bb:b3
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:3000(size=256) memory:f0300000-f0300fff memory:80400000-8041ffff

```

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```

```
lsb_release -d
Description:	Ubuntu 11.04

```

```
uname -mr
2.6.38-8-generic i686

```

```
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                        Ignoring unknown interface eth0=eth0.
                                                                                                                                                       [ OK ]
```

---

### Post by poolet on 2011-06-30
your loading  r8169 mod, can you black list  the r8169 mod and load r8168 to see what happen??
Also do not use network manager, remove it and install the wicd,
maybe solved your problem without any other configuration.

---

### Post by zvisar on 2011-07-01
> **poolet said:**
> your loading  r8169 mod, can you black list  the r8169 mod and load r8168 to see what happen??
Also do not use network manager, remove it and install the wicd,
maybe solved your problem without any other configuration.

Well, it blocked my wired connection (and wireless, too).
I installed wicd, no use. I'm turning back to network manager (it lets me connect to both wired and wireless).

---

### Post by varunendra on 2011-07-02
> **poolet said:**
> your loading  r8169 mod, can you black list  the r8169 mod and load r8168 to see what happen??
@poolet,
this fix is associated with ethernet interface that uses RTL8168B chip. Also, wicd is good for simplicity, but NM is more advanced. Although changing to wicd does solve wifi problems sometimes, but MN has more options for customization.

@zvisar,
while you are connected through wifi, do some browsing, then, before it disconnects, run **ifconfig **and post its output again. Also post the contents of **/var/log/syslog** file after the wifi disconnects.

Is the signal strength good where you are having this problem? As per your dmesg log it seems the adapter has to try hard to get authenticated for the connection.

<snip>

---

### Post by varunendra on 2011-07-02
Posting a possible solution in a new post to avoid clutter:-

It seems this better explains the reason for your problem, with a suggested fix: [http://www.dotkam.com/2008/11/17/con...ver-on-ubuntu/]("http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/")
> Before, ( e.g. Feisty and earlier ) &#8220;**ipw3945**&#8221; driver was used   instead, and worked beautifully with Intel cards. However the active   development of this driver has stopped a couple of years ago, which   means that security risks that were identified in the last couple of   years were not patched. Therefore Ubuntu community switched to a more   recent and supported &#8220;[iwl3945]("http://linuxwireless.org/en/users/Drivers/iwl3945")&#8221; driver.
 However that created a problem with [NetworkManager]("http://projects.gnome.org/NetworkManager/") that is used as a default network user interface in (Gnome) Ubuntu. It appears that in order &#8220;*to   be compatible with NetworkManager, a wireless driver must support both   hardware and software scanning. Currently, hardware scanning is faster   and more reliable and so is recommended for use with NetworkManager*&#8220;. But unfortunately &#8220;iwl3945&#8243; driver does not support hardware scanning very well, however *it is* a default behaviour that NetworkManager expects. The suggested fix in the above article is to disable 'Hardware scan' in iwl3945 driver and replace NetworkManager with wicd:

1) Add these lines to **/etc/modprobe.d/iwl3945** (create it if it doesn't already exist):
[COLOR=DarkRed]alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1[/COLOR]

2) Remove NetworkManager and install wicd instead.

3) Restart to load the driver with new parameters
(or simply reload the module using **sudo modprobe -r iwl3945** then **sudo modprobe iwl3945 **commands)

Although the above fix was suggested during the time of Intrepid Ibex,  if the nature of this driver is still same I hope it should work in  Natty too.

---

### Post by poolet on 2011-07-02
[varunendra]("http://ubuntuforums.org/member.php?u=1043629")

Thank you for your reply and for your useful informations....

---

### Post by varunendra on 2011-07-02
It's my pleasure!

Actually I'm keen to know how it goes with your system. If it doesn't work, then post back the stuff as I asked in my first post.

---

