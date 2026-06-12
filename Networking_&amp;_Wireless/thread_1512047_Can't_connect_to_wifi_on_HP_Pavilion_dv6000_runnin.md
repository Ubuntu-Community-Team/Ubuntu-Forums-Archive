---
title: "Can't connect to wifi on HP Pavilion dv6000 running Ubuntu 10.04"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by JohnElway on 2010-06-17
I recently upgraded from 9.04 to 10.04 and can no longer connect to the internet, even after enabling wireless networking in the Network Manager. This happened to me on a different laptop recently, but someone here linked me to the proper drivers and solved my problem. I'm not quite sure how to search for the proper drivers, but I'm hoping someone here could point me in the right direction.

lspci
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
```lsusb
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:b7:e8:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)
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
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_conexant    28745  1 
joydev                 11072  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
arc4                    1473  2 
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
b43                   174953  0 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               515131  2 
mac80211              238128  1 b43
uvcvideo               62403  0 
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
sdhci_pci               6700  0 
snd                    70978  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ricoh_mmc               3416  0 
videodev               40486  1 uvcvideo
sdhci                  17928  1 sdhci_pci
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
cfg80211              148386  2 b43,mac80211
led_class               3732  2 b43,sdhci
drm                   198770  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
k8temp                  3912  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
psmouse                64608  0 
serio_raw               4918  0 
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
ssb                    43517  1 b43
ieee1394               94675  1 ohci1394
forcedeth              55592  0 
ahci                   37646  1 
pata_amd               11962  0
```dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bf50000 (usable)
[    0.000000]  BIOS-e820: 000000007bf50000 - 000000007bf65000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bf65000 - 000000007bf66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bf66000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7bf50 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007bf50000 (usable)
[    0.000000]  modified: 000000007bf50000 - 000000007bf65000 (ACPI data)
[    0.000000]  modified: 000000007bf65000 - 000000007bf66000 (ACPI NVS)
[    0.000000]  modified: 000000007bf66000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007bf50000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 007be00000 page 2M
[    0.000000]  007be00000 - 007bf50000 page 4k
[    0.000000] kernel direct mapping tables up to 7bf50000 @ 8000-c000
[    0.000000] RAMDISK: 377b1000 - 37fefe27
[    0.000000] ACPI: RSDP 00000000000f8250 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 000000007bf5c5e6 0006C (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 000000007bf649ba 000F4 (v03 NVIDIA MCP67-M  06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT 000000007bf5c652 082F4 (v01 NVIDIA    MCP67 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 000000007bf65fc0 00040
[    0.000000] ACPI: TCPA 000000007bf64aae 00032 (v01 Phoeni  x       06040000  TL  00000000)
[    0.000000] ACPI: SRAT 000000007bf64ae0 000A0 (v01 AMD    HAMMER   06040000 AMD  00000001)
[    0.000000] ACPI: SSDT 000000007bf64b80 00206 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG 000000007bf64d86 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 000000007bf64dc2 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 000000007bf64dfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 000000007bf64e62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 000000007bf64e8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-80000000
[    0.000000] NUMA: Allocated memnodemap from a000 - b040
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-000000007bf50000
[    0.000000]   NODE_DATA [000000000000b040 - 000000000001003f]
[    0.000000]   bootmap [0000000000011000 -  00000000000207ef] pages 10
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 007bf50000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [00377b1000 - 0037fefe27]          RAMDISK ==> [00377b1000 - 0037fefe27]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a1a0]              BRK ==> [0001a2a000 - 0001a2a1a0]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b040]       MEMNODEMAP ==> [000000a000 - 000000b040]
[    0.000000] found SMP MP-table at [ffff8800000f8220] f8220
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880002000000-ffff880003bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x0007bf50
[    0.000000] On node 0 totalpages: 507625
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 104 pages reserved
[    0.000000]   DMA zone: 3833 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6886 pages used for memmap
[    0.000000]   DMA32 zone: 496746 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u1048576
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 500579
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ e040000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 1982548k/2030912k available (5409k kernel code, 412k absent, 47952k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 20971520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1900.130 MHz processor.
[    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3800.26 BogoMIPS (lpj=19001300)
[    0.010037] Security Framework initialized
[    0.010060] AppArmor: AppArmor initialized
[    0.010271] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011409] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.011954] Mount-cache hash table entries: 256
[    0.012113] Initializing cgroup subsys ns
[    0.012117] Initializing cgroup subsys cpuacct
[    0.012122] Initializing cgroup subsys memory
[    0.012131] Initializing cgroup subsys devices
[    0.012134] Initializing cgroup subsys freezer
[    0.012136] Initializing cgroup subsys net_cls
[    0.012159] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.012161] CPU: L2 Cache: 512K (64 bytes/line)
[    0.012164] CPU 0/0x0 -> Node 0
[    0.012166] tseg: 007bf80000
[    0.012168] CPU: Physical Processor ID: 0
[    0.012170] CPU: Processor Core ID: 0
[    0.012173] mce: CPU supports 5 MCE banks
[    0.012186] using C1E aware idle routine
[    0.012188] Performance Events: AMD PMU driver.
[    0.012193] ... version:                0
[    0.012195] ... bit width:              48
[    0.012197] ... generic registers:      4
[    0.012199] ... value mask:             0000ffffffffffff
[    0.012201] ... max period:             00007fffffffffff
[    0.012203] ... fixed-purpose events:   0
[    0.012205] ... event mask:             000000000000000f
[    0.014102] ACPI: Core revision 20090903
[    0.030009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030015] ftrace: allocating 22518 entries in 89 pages
[    0.040102] Setting APIC routing to flat
[    0.040572] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.142796] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] System has AMD C1E enabled
[    0.020000] Switch to broadcast mode on CPU1
[    0.300060] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-58 stepping 01
[    0.300081] Brought up 2 CPUs
[    0.300083] Total of 2 processors activated (7600.64 BogoMIPS).
[    0.300306] CPU0 attaching sched-domain:
[    0.300309]  domain 0: span 0-1 level MC
[    0.300312]   groups: 0 1
[    0.300318] CPU1 attaching sched-domain:
[    0.300320]  domain 0: span 0-1 level MC
[    0.300322]   groups: 1 0
[    0.300419] Switch to broadcast mode on CPU0
[    0.300419] devtmpfs: initialized
[    0.300419] regulator: core version 0.5
[    0.300419] Time:  5:25:42  Date: 06/17/10
[    0.300419] NET: Registered protocol family 16
[    0.300419] Trying to unpack rootfs image as initramfs...
[    0.300419] node 0 link 0: io port [1000, fffff]
[    0.300419] TOM: 0000000080000000 aka 2048M
[    0.300419] node 0 link 0: mmio [a0000, bffff]
[    0.300419] node 0 link 0: mmio [80000000, dfffffff]
[    0.300419] node 0 link 0: mmio [e0000000, efffffff]
[    0.300419] node 0 link 0: mmio [f0000000, fe0bffff]
[    0.300419] bus: [00,ff] on node 0 link 0
[    0.300419] bus: 00 index 0 io port: [0, ffff]
[    0.300419] bus: 00 index 1 mmio: [a0000, bffff]
[    0.300419] bus: 00 index 2 mmio: [80000000, fcffffffff]
[    0.300419] ACPI: bus type pci registered
[    0.300419] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.300419] PCI: MCFG area at e0000000 reserved in E820
[    0.300530] PCI: Using MMCONFIG at e0000000 - e04fffff
[    0.300532] PCI: Using configuration type 1 for base access
[    0.310134] bio: create slab <bio-0> at 0
[    0.310891] ACPI: EC: Look up EC in DSDT
[    0.314071] ACPI: BIOS _OSI(Linux) query ignored
[    0.314988] ACPI: Interpreter enabled
[    0.314995] ACPI: (supports S0 S3 S4 S5)
[    0.315017] ACPI: Using IOAPIC for interrupt routing
[    0.323672] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.324057] ACPI: No dock devices found.
[    0.324346] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.324574] pci 0000:00:01.1: reg 10 io port: [0x3080-0x30bf]
[    0.324585] pci 0000:00:01.1: reg 20 io port: [0x3040-0x307f]
[    0.324590] pci 0000:00:01.1: reg 24 io port: [0x3000-0x303f]
[    0.324610] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.324615] pci 0000:00:01.1: PME# disabled
[    0.324674] pci 0000:00:01.3: reg 10 32bit mmio: [0xf6200000-0xf627ffff]
[    0.324755] pci 0000:00:02.0: reg 10 32bit mmio: [0xf6486000-0xf6486fff]
[    0.324779] pci 0000:00:02.0: supports D1 D2
[    0.324781] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.324784] pci 0000:00:02.0: PME# disabled
[    0.324809] pci 0000:00:02.1: reg 10 32bit mmio: [0xf6489000-0xf64890ff]
[    0.324838] pci 0000:00:02.1: supports D1 D2
[    0.324840] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.324843] pci 0000:00:02.1: PME# disabled
[    0.324871] pci 0000:00:04.0: reg 10 32bit mmio: [0xf6487000-0xf6487fff]
[    0.324895] pci 0000:00:04.0: supports D1 D2
[    0.324897] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.324901] pci 0000:00:04.0: PME# disabled
[    0.324929] pci 0000:00:04.1: reg 10 32bit mmio: [0xf6489400-0xf64894ff]
[    0.324957] pci 0000:00:04.1: supports D1 D2
[    0.324959] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.324963] pci 0000:00:04.1: PME# disabled
[    0.324999] pci 0000:00:06.0: reg 20 io port: [0x30c0-0x30cf]
[    0.325040] pci 0000:00:07.0: reg 10 32bit mmio: [0xf6480000-0xf6483fff]
[    0.325068] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.325071] pci 0000:00:07.0: PME# disabled
[    0.325138] pci 0000:00:09.0: reg 10 io port: [0x30f0-0x30f7]
[    0.325142] pci 0000:00:09.0: reg 14 io port: [0x30e4-0x30e7]
[    0.325147] pci 0000:00:09.0: reg 18 io port: [0x30e8-0x30ef]
[    0.325151] pci 0000:00:09.0: reg 1c io port: [0x30e0-0x30e3]
[    0.325155] pci 0000:00:09.0: reg 20 io port: [0x30d0-0x30df]
[    0.325159] pci 0000:00:09.0: reg 24 32bit mmio: [0xf6484000-0xf6485fff]
[    0.325208] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf6488000-0xf6488fff]
[    0.325213] pci 0000:00:0a.0: reg 14 io port: [0x30f8-0x30ff]
[    0.325217] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf6489c00-0xf6489cff]
[    0.325222] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf6489800-0xf648980f]
[    0.325244] pci 0000:00:0a.0: supports D1 D2
[    0.325246] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325250] pci 0000:00:0a.0: PME# disabled
[    0.325293] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325296] pci 0000:00:0c.0: PME# disabled
[    0.325336] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325338] pci 0000:00:0d.0: PME# disabled
[    0.325366] pci 0000:00:12.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.325372] pci 0000:00:12.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.325377] pci 0000:00:12.0: reg 1c 64bit mmio: [0xf4000000-0xf4ffffff]
[    0.325383] pci 0000:00:12.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.325509] pci 0000:02:05.0: reg 10 32bit mmio: [0xf6100000-0xf61007ff]
[    0.325542] pci 0000:02:05.0: supports D1 D2
[    0.325545] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325549] pci 0000:02:05.0: PME# disabled
[    0.325575] pci 0000:02:05.1: reg 10 32bit mmio: [0xf6100800-0xf61008ff]
[    0.325608] pci 0000:02:05.1: supports D1 D2
[    0.325610] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325614] pci 0000:02:05.1: PME# disabled
[    0.325640] pci 0000:02:05.2: reg 10 32bit mmio: [0xf6100c00-0xf6100cff]
[    0.325674] pci 0000:02:05.2: supports D1 D2
[    0.325676] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325680] pci 0000:02:05.2: PME# disabled
[    0.325708] pci 0000:02:05.3: reg 10 32bit mmio: [0xf6101000-0xf61010ff]
[    0.325742] pci 0000:02:05.3: supports D1 D2
[    0.325745] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325748] pci 0000:02:05.3: PME# disabled
[    0.325774] pci 0000:02:05.4: reg 10 32bit mmio: [0xf6101400-0xf61014ff]
[    0.325808] pci 0000:02:05.4: supports D1 D2
[    0.325810] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325814] pci 0000:02:05.4: PME# disabled
[    0.325847] pci 0000:00:08.0: transparent bridge
[    0.325852] pci 0000:00:08.0: bridge 32bit mmio: [0xf6100000-0xf61fffff]
[    0.325893] pci 0000:00:0c.0: bridge io port: [0x4000-0x4fff]
[    0.325897] pci 0000:00:0c.0: bridge 32bit mmio: [0xf2000000-0xf3ffffff]
[    0.325901] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.325943] pci 0000:03:00.0: reg 10 64bit mmio: [0xf6000000-0xf6003fff]
[    0.325991] pci 0000:03:00.0: supports D1 D2
[    0.326044] pci 0000:00:0d.0: bridge 32bit mmio: [0xf6000000-0xf60fffff]
[    0.326058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.326163] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.326193] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.326232] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.371054] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.371317] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.371577] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.371837] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.372098] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.372358] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.372617] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.372876] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.373135] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.373403] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.373666] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.373926] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.374187] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.374447] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.374707] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.374967] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.375226] ACPI: PCI Interrupt Link [Z015] (IRQs 18) *5
[    0.375487] ACPI: PCI Interrupt Link [Z016] (IRQs 22) *10
[    0.375748] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.375899] vgaarb: device added: PCI:0000:00:12.0,decodes=io+mem,owns=io+mem,locks=none
[    0.375908] vgaarb: loaded
[    0.376032] SCSI subsystem initialized
[    0.376161] libata version 3.00 loaded.
[    0.376239] usbcore: registered new interface driver usbfs
[    0.376252] usbcore: registered new interface driver hub
[    0.376282] usbcore: registered new device driver usb
[    0.376485] ACPI: WMI: Mapper loaded
[    0.376487] PCI: Using ACPI for IRQ routing
[    0.376677] NetLabel: Initializing
[    0.376680] NetLabel:  domain hash size = 128
[    0.376681] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.376697] NetLabel:  unlabeled traffic allowed by default
[    0.376743] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.376749] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.390005] Switching to clocksource hpet
[    0.392049] AppArmor: AppArmor Filesystem Enabled
[    0.392076] pnp: PnP ACPI init
[    0.392098] ACPI: bus type pnp registered
[    0.395785] pnp: PnP ACPI: found 12 devices
[    0.395788] ACPI: ACPI bus type pnp unregistered
[    0.395803] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.395810] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.395813] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.395817] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.395820] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.395823] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.395827] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.395833] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.395836] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.395844] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.395848] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.395852] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.395855] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.395859] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.400638] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.400641] pci 0000:00:08.0:   IO window: disabled
[    0.400645] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.400648] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.400653] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.400656] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.400659] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.400663] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.400667] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.400669] pci 0000:00:0d.0:   IO window: disabled
[    0.400672] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.400675] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.400685] pci 0000:00:08.0: setting latency timer to 64
[    0.400691] pci 0000:00:0c.0: setting latency timer to 64
[    0.400696] pci 0000:00:0d.0: setting latency timer to 64
[    0.400701] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.400704] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.400707] pci_bus 0000:02: resource 1 mem: [0xf6100000-0xf61fffff]
[    0.400710] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.400713] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.400716] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.400719] pci_bus 0000:04: resource 1 mem: [0xf2000000-0xf3ffffff]
[    0.400722] pci_bus 0000:04: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.400725] pci_bus 0000:03: resource 1 mem: [0xf6000000-0xf60fffff]
[    0.400770] NET: Registered protocol family 2
[    0.400932] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.401994] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.404237] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.404820] TCP: Hash tables configured (established 262144 bind 65536)
[    0.404823] TCP reno registered
[    0.404944] NET: Registered protocol family 1
[    0.405110] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.405163] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.405222] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.405287] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.405356] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.405430] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.405437] pci 0000:00:12.0: Boot video device
[    0.405669] Simple Boot Flag at 0x36 set to 0x1
[    0.405886] Scanning for low memory corruption every 60 seconds
[    0.406055] audit: initializing netlink socket (disabled)
[    0.406067] type=2000 audit(1276752342.399:1): initialized
[    0.416109] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.417737] VFS: Disk quotas dquot_6.5.2
[    0.417803] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.418597] fuse init (API version 7.13)
[    0.418698] msgmni has been set to 3872
[    0.418971] alg: No test for stdrng (krng)
[    0.419044] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.419048] io scheduler noop registered
[    0.419050] io scheduler anticipatory registered
[    0.419052] io scheduler deadline registered
[    0.419089] io scheduler cfq registered (default)
[    0.419275]   alloc irq_desc for 24 on node 0
[    0.419278]   alloc kstat_irqs on node 0
[    0.419288] pcieport 0000:00:0c.0: irq 24 for MSI/MSI-X
[    0.419294] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.419409]   alloc irq_desc for 25 on node 0
[    0.419411]   alloc kstat_irqs on node 0
[    0.419416] pcieport 0000:00:0d.0: irq 25 for MSI/MSI-X
[    0.419421] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.419490] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.419515] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.420136] ACPI: AC Adapter [ACAD] (on-line)
[    0.420236] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.420240] ACPI: Sleep Button [SLPB]
[    0.420287] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.420600] ACPI: Lid Switch [LID]
[    0.420665] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.420668] ACPI: Power Button [PWRB]
[    0.420712] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.420715] ACPI: Power Button [PWRF]
[    0.421113] ACPI: processor limited to max C-state 1
[    0.421145] processor LNXCPU:00: registered as cooling_device0
[    0.421185] processor LNXCPU:01: registered as cooling_device1
[    0.424959] ACPI Exception: AE_OK, No or invalid critical threshold (20090903/thermal-386)
[    0.426650] Linux agpgart interface v0.103
[    0.426696] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.428059] brd: module loaded
[    0.428588] loop: module loaded
[    0.428702] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.428985] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.429459] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    0.429465]   alloc irq_desc for 23 on node 0
[    0.429468]   alloc kstat_irqs on node 0
[    0.429480] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    0.429510] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.429519] pata_acpi 0000:00:09.0: PCI INT A disabled
[    0.429920] Fixed MDIO Bus: probed
[    0.429960] PPP generic driver version 2.4.2
[    0.430040] tun: Universal TUN/TAP device driver, 1.6
[    0.430042] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.430149] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.430588] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.430591]   alloc irq_desc for 22 on node 0
[    0.430593]   alloc kstat_irqs on node 0
[    0.430602] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    0.430621] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.430624] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.430668] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.430698] ehci_hcd 0000:00:02.1: debug port 1
[    0.430706] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.430731] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    0.450049] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.450148] usb usb1: configuration #1 chosen from 1 choice
[    0.450181] hub 1-0:1.0: USB hub found
[    0.450190] hub 1-0:1.0: 7 ports detected
[    0.450793] ACPI: PCI Interrupt Link [Z016] enabled at IRQ 22
[    0.450797] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z016] -> GSI 22 (level, low) -> IRQ 22
[    0.450811] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.450814] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.450859] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.450889] ehci_hcd 0000:00:04.1: debug port 1
[    0.450897] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.450904] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    0.470030] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.470117] usb usb2: configuration #1 chosen from 1 choice
[    0.470147] hub 2-0:1.0: USB hub found
[    0.470156] hub 2-0:1.0: 2 ports detected
[    0.470222] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.470667] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    0.470671]   alloc irq_desc for 18 on node 0
[    0.470674]   alloc kstat_irqs on node 0
[    0.470683] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    0.470698] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.470702] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.470743] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.470774] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    0.532104] usb usb3: configuration #1 chosen from 1 choice
[    0.532133] hub 3-0:1.0: USB hub found
[    0.532142] hub 3-0:1.0: 7 ports detected
[    0.532641] ACPI: PCI Interrupt Link [Z015] enabled at IRQ 18
[    0.532646] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z015] -> GSI 18 (level, low) -> IRQ 18
[    0.532657] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.532660] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.532709] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.532723] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    0.534250] Freeing initrd memory: 8443k freed
[    0.592123] usb usb4: configuration #1 chosen from 1 choice
[    0.592156] hub 4-0:1.0: USB hub found
[    0.592166] hub 4-0:1.0: 2 ports detected
[    0.592242] uhci_hcd: USB Universal Host Controller Interface driver
[    0.592333] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.614612] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.614618] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.614768] mice: PS/2 mouse device common for all mice
[    0.616153] rtc_cmos 00:07: RTC can wake from S4
[    0.616203] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.616243] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.616387] device-mapper: uevent: version 1.0.3
[    0.616536] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.616652] device-mapper: multipath: version 1.1.0 loaded
[    0.616655] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.616905] cpuidle: using governor ladder
[    0.616907] cpuidle: using governor menu
[    0.617322] TCP cubic registered
[    0.617466] NET: Registered protocol family 10
[    0.618007] lo: Disabled Privacy Extensions
[    0.618376] NET: Registered protocol family 17
[    0.618420] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[    0.618470] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x11
[    0.618472] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[    0.618475] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[    0.618477] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    0.618622] PM: Resume from disk failed.
[    0.618637] registered taskstats version 1
[    0.619032]   Magic number: 14:179:416
[    0.619141] rtc_cmos 00:07: setting system clock to 2010-06-17 05:25:43 UTC (1276752343)
[    0.619145] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.619146] EDD information not available.
[    0.635231] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.700416] ACPI: Battery Slot [BAT0] (battery present)
[    0.790045] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    0.950422] Freeing unused kernel memory: 876k freed
[    0.950876] Write protecting the kernel read-only data: 7680k
[    0.954174] usb 2-2: configuration #1 chosen from 1 choice
[    0.973715] udev: starting version 151
[    1.127113] pata_amd 0000:00:06.0: version 0.4.1
[    1.127172] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.131755] scsi0 : pata_amd
[    1.134015] scsi1 : pata_amd
[    1.134502] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    1.134506] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    1.135597] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.137844] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.137853]   alloc irq_desc for 20 on node 0
[    1.137856]   alloc kstat_irqs on node 0
[    1.137868] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.137875] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.146556] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[    1.146563]   alloc irq_desc for 19 on node 0
[    1.146565]   alloc kstat_irqs on node 0
[    1.146577] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[    1.146586] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    1.270089] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.310358] ata1.00: ATAPI: PIONEER DVDRW   DVR-K17B, 1.02, max MWDMA2
[    1.310387] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.350299] ata1.00: configured for MWDMA2
[    1.363549] scsi 0:0:0:0: CD-ROM            PIONEER  DVDRW   DVR-K17B 1.02 PQ: 0 ANSI: 5
[    1.386751] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.386755] Uniform CD-ROM driver Revision: 3.20
[    1.386884] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.386960] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.387058] ata2: port disabled. ignoring.
[    1.391283] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    1.391300] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    1.452069] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.661113] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:b7:e8:15
[    1.661117] forcedeth 0000:00:0a.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.661331] ahci 0000:00:09.0: version 3.0
[    1.661346] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    1.661391]   alloc irq_desc for 26 on node 0
[    1.661394]   alloc kstat_irqs on node 0
[    1.661403] ahci 0000:00:09.0: irq 26 for MSI/MSI-X
[    1.661410] ahci 0000:00:09.0: controller can do NCQ, turning on CAP_NCQ
[    1.661473] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.661477] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio slum part 
[    1.661482] ahci 0000:00:09.0: setting latency timer to 64
[    1.661889] scsi2 : ahci
[    1.662023] scsi3 : ahci
[    1.662117] scsi4 : ahci
[    1.662196] scsi5 : ahci
[    1.662352] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 26
[    1.662356] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 26
[    1.662359] ata5: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 26
[    1.662362] ata6: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 26
[    2.010039] ata4: SATA link down (SStatus 0 SControl 300)
[    2.010064] ata5: SATA link down (SStatus 0 SControl 300)
[    2.010073] ata6: SATA link down (SStatus 0 SControl 300)
[    2.190042] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.190420] ata3.00: ATA-8: FUJITSU MHY2250BH, 890B, max UDMA/100
[    2.190424] ata3.00: 488397168 sectors, multi 16: LBA48 
[    2.190941] ata3.00: configured for UDMA/100
[    2.191052] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHY2250B 890B PQ: 0 ANSI: 5
[    2.191255] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.191292] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.191374] sd 2:0:0:0: [sda] Write Protect is off
[    2.191377] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.191402] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.191562]  sda: sda1 sda2
[    2.216713] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.770176] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00da316f00]
[    3.045882] EXT4-fs (loop0): mounted filesystem with ordered data mode
[   15.699406] udev: starting version 151
[   15.832131] lp: driver loaded but no devices found
[   15.997508] acpi device:23: registered as cooling_device2
[   15.997684] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   15.997750] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   16.040433] EDAC MC: Ver: 2.1.0 Apr 16 2010
[   16.114114] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   16.114139] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   16.159746] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   16.222818] type=1505 audit(1276777559.100:2):  operation="profile_load" pid=718 name="/sbin/dhclient3"
[   16.223226] type=1505 audit(1276777559.100:3):  operation="profile_load" pid=718 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.223395] type=1505 audit(1276777559.100:4):  operation="profile_load" pid=718 name="/usr/lib/connman/scripts/dhclient-script"
[   16.251613] [drm] Initialized drm 1.1.0 20060810
[   16.269298] sdhci: Secure Digital Host Controller Interface driver
[   16.269302] sdhci: Copyright(c) Pierre Ossman
[   16.274273] Linux video capture interface: v2.00
[   16.274771] ricoh-mmc: Ricoh MMC Controller disabling driver
[   16.274775] ricoh-mmc: Copyright(c) Philip Langdale
[   16.277453] EDAC amd64_edac:  Ver: 3.2.0 Apr 16 2010
[   16.283902] cfg80211: Calling CRDA to update world regulatory domain
[   16.309508] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b015)
[   16.309647] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   16.309668] ricoh-mmc: Controller is now disabled.
[   16.309709] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   16.309720] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   16.309721]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   16.309723]  (Note that use of the override may cause unknown side effects.)
[   16.309750] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   16.325938] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   16.326361] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   16.326376] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   16.330305] input: HP Webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input7
[   16.330387] usbcore: registered new interface driver uvcvideo
[   16.330391] USB Video Class driver (v0.1.0)
[   16.351377] Registered led device: mmc0::
[   16.352460] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   16.356276] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   16.356286]   alloc irq_desc for 16 on node 0
[   16.356289]   alloc kstat_irqs on node 0
[   16.356303] nouveau 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   16.356310] nouveau 0000:00:12.0: setting latency timer to 64
[   16.364897] [drm] nouveau 0000:00:12.0: failed to evaluate _DSM: 5
[   16.367980] [drm] nouveau 0000:00:12.0: Detected an NV40 generation card (0x067000a1)
[   16.368440] [drm] nouveau 0000:00:12.0: Attempting to load BIOS image from PROM
[   16.368445] [drm] nouveau 0000:00:12.0: ... BIOS signature not found
[   16.368447] [drm] nouveau 0000:00:12.0: Attempting to load BIOS image from PRAMIN
[   16.411104] [drm] nouveau 0000:00:12.0: ... appears to be valid
[   16.411109] [drm] nouveau 0000:00:12.0: BIT BIOS found
[   16.411112] [drm] nouveau 0000:00:12.0: Bios version 05.67.32.16
[   16.411115] [drm] nouveau 0000:00:12.0: TMDS table script pointers not stubbed
[   16.411118] [drm] nouveau 0000:00:12.0: BIT table 'd' not found
[   16.411121] [drm] nouveau 0000:00:12.0: Found Display Configuration Block version 3.0
[   16.411125] [drm] nouveau 0000:00:12.0: DCB connector table: VHER 0x30 5 10 2
[   16.411128] [drm] nouveau 0000:00:12.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   16.411131] [drm] nouveau 0000:00:12.0:   1: 0x00001161: type 0x61 idx 1 tag 0x07
[   16.411134] [drm] nouveau 0000:00:12.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   16.411137] [drm] nouveau 0000:00:12.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   16.411140] [drm] nouveau 0000:00:12.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   16.411143] [drm] nouveau 0000:00:12.0:   5: 0x00000340: type 0x40 idx 3 tag 0xff
[   16.411146] [drm] nouveau 0000:00:12.0: Raw DCB entry 0: 03015323 00000004
[   16.411150] [drm] nouveau 0000:00:12.0: Raw DCB entry 1: 01000310 00000023
[   16.411152] [drm] nouveau 0000:00:12.0: Raw DCB entry 2: 020223f1 0040c080
[   16.411159] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 0 at offset 0xE333
[   16.411179] [drm] nouveau 0000:00:12.0: ======= misaligned reg 0x001020FB =======
[   16.411240] [drm] nouveau 0000:00:12.0: ======= misaligned reg 0x001020FB =======
[   16.411321] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 1 at offset 0xE484
[   16.411324] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 2 at offset 0xE485
[   16.411354] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 3 at offset 0xE607
[   16.411362] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 4 at offset 0xE687
[   16.417659] cfg80211: World regulatory domain updated:
[   16.417663]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.417667]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.417670]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.417672]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.417675]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.417678]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.422226] [TTM] Zone  kernel: Available graphics memory: 995934 kiB.
[   16.422240] [drm] nouveau 0000:00:12.0: 64 MiB VRAM
[   16.423103] [drm] nouveau 0000:00:12.0: 64 MiB GART (aperture)
[   16.423601] [drm] nouveau 0000:00:12.0: Allocating FIFO number 0
[   16.423892] [drm] nouveau 0000:00:12.0: nouveau_channel_alloc: initialised FIFO 0
[   16.423899] [drm] nouveau 0000:00:12.0: Initial CRTC_OWNER is 0
[   16.423905] [drm] nouveau 0000:00:12.0: Saving VGA fonts
[   16.470479] b43-phy0: Broadcom 4311 WLAN found (core revision 13)
[   16.492227] [drm] nouveau 0000:00:12.0: Detected a LVDS connector
[   16.601380] [drm] nouveau 0000:00:12.0: Detected a VGA connector
[   16.601614] [drm] nouveau 0000:00:12.0: Detected a TV connector
[   16.609012] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on lvds encoder (output 0)
[   16.609018] [drm] nouveau 0000:00:12.0: Calling LVDS script 6:
[   16.609022] [drm] nouveau 0000:00:12.0: 0xD680: Parsing digital output script table
[   16.609031] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on vga encoder (output 1)
[   16.609035] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on TV encoder (output 2)
[   16.684742] phy0: Selected rate control algorithm 'minstrel'
[   16.685549] Registered led device: b43-phy0::tx
[   16.685571] Registered led device: b43-phy0::rx
[   16.685590] Registered led device: b43-phy0::radio
[   16.685676] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   16.750022] [drm] nouveau 0000:00:12.0: Load detected on output B
[   16.750216] [drm] nouveau 0000:00:12.0: allocated 1280x800 fb: 0x49000, bo ffff88004d5f1800
[   16.750336] fb0: nouveaufb frame buffer device
[   16.750338] registered panic notifier
[   16.750345] [drm] Initialized nouveau 0.0.15 20090420 for 0000:00:12.0 on minor 0
[   16.752704] vga16fb: initializing
[   16.752710] vga16fb: mapped to 0xffff8800000a0000
[   16.752719] vga16fb: not registering due to another framebuffer present
[   16.756180] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   16.756187]   alloc irq_desc for 21 on node 0
[   16.756189]   alloc kstat_irqs on node 0
[   16.756200] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   16.756205] hda_intel: Disable MSI for Nvidia chipset
[   16.756250] HDA Intel 0000:00:07.0: setting latency timer to 64
[   16.778529] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
[   16.778534] [drm] nouveau 0000:00:12.0: Calling LVDS script 2:
[   16.778538] [drm] nouveau 0000:00:12.0: 0xD6D8: Parsing digital output script table
[   16.960024] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on lvds encoder (output 0)
[   16.960028] [drm] nouveau 0000:00:12.0: Calling LVDS script 5:
[   16.960032] [drm] nouveau 0000:00:12.0: 0xD676: Parsing digital output script table
[   16.960037] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
[   17.071052] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on TV encoder (output 2)
[   17.071056] [drm] nouveau 0000:00:12.0: Output TV-1 is running on CRTC 1 using output B
[   17.172894] Console: switching to colour frame buffer device 90x36
[   17.239353] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   17.407185] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   17.725456] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:7 across:220116960k 
[   17.922407] CE: hpet increasing min_delta_ns to 15000 nsec
[   18.034956] type=1505 audit(1276777560.913:5):  operation="profile_load" pid=909 name="/usr/share/gdm/guest-session/Xsession"
[   18.038142] type=1505 audit(1276777560.913:6):  operation="profile_replace" pid=911 name="/sbin/dhclient3"
[   18.038456] type=1505 audit(1276777560.913:7):  operation="profile_replace" pid=911 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.038633] type=1505 audit(1276777560.913:8):  operation="profile_replace" pid=911 name="/usr/lib/connman/scripts/dhclient-script"
[   18.043154] type=1505 audit(1276777560.923:9):  operation="profile_load" pid=913 name="/usr/bin/evince"
[   18.048798] type=1505 audit(1276777560.923:10):  operation="profile_load" pid=913 name="/usr/bin/evince-previewer"
[   18.051980] type=1505 audit(1276777560.923:11):  operation="profile_load" pid=913 name="/usr/bin/evince-thumbnailer"
[   18.106233]   alloc irq_desc for 27 on node 0
[   18.106239]   alloc kstat_irqs on node 0
[   18.106249] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   18.106462] eth0: no link during initialization.
[   18.107196] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.223057] b43 ssb0:0: firmware: requesting b43/ucode13.fw
[   18.242788] b43 ssb0:0: firmware: requesting b43-open/ucode13.fw
[   18.257207] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
[   18.257213] b43-phy0 ERROR: Firmware file "b43-open/ucode13.fw" not found
[   18.257216] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   18.299037] ppdev: user-space parallel port driver
[   18.320099] b43 ssb0:0: firmware: requesting b43/ucode13.fw
[   18.322263] b43 ssb0:0: firmware: requesting b43-open/ucode13.fw
[   18.324679] b43-phy0 ERROR: Firmware file "b43/ucode13.fw" not found
[   18.324685] b43-phy0 ERROR: Firmware file "b43-open/ucode13.fw" not found
[   18.324689] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   18.460095] [drm] nouveau 0000:00:12.0: Load detected on output B
[   18.660026] [drm] nouveau 0000:00:12.0: Load detected on output B
[   18.663867] [drm] nouveau 0000:00:12.0: Allocating FIFO number 1
[   18.664160] [drm] nouveau 0000:00:12.0: nouveau_channel_alloc: initialised FIFO 1
[   18.675863] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on lvds encoder (output 0)
[   18.675869] [drm] nouveau 0000:00:12.0: Calling LVDS script 6:
[   18.675873] [drm] nouveau 0000:00:12.0: 0xD680: Parsing digital output script table
[   18.696126] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
[   18.696130] [drm] nouveau 0000:00:12.0: Calling LVDS script 2:
[   18.696133] [drm] nouveau 0000:00:12.0: 0xD6D8: Parsing digital output script table
[   18.870031] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on lvds encoder (output 0)
[   18.870034] [drm] nouveau 0000:00:12.0: Calling LVDS script 5:
[   18.870037] [drm] nouveau 0000:00:12.0: 0xD676: Parsing digital output script table
[   18.870041] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
[   18.870232] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on TV encoder (output 2)
[   18.907520] CE: hpet increasing min_delta_ns to 22500 nsec
[   18.907520] CE: hpet increasing min_delta_ns to 33750 nsec
[   18.907520] CE: hpet increasing min_delta_ns to 50624 nsec
[   18.940947] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on TV encoder (output 2)
[   18.940951] [drm] nouveau 0000:00:12.0: Output TV-1 is running on CRTC 1 using output B
[   20.680030] [drm] nouveau 0000:00:12.0: Load detected on output B
[   20.860030] [drm] nouveau 0000:00:12.0: Load detected on output B
[   21.040041] [drm] nouveau 0000:00:12.0: Load detected on output B
[   35.490031] [drm] nouveau 0000:00:12.0: Load detected on output B
[   35.670030] [drm] nouveau 0000:00:12.0: Load detected on output B
[   35.850030] [drm] nouveau 0000:00:12.0: Load detected on output B
[   41.350032] [drm] nouveau 0000:00:12.0: Load detected on output B
[   79.012562] Clocksource tsc unstable (delta = -209440654 ns)
[  529.250053] [drm] nouveau 0000:00:12.0: Load detected on output B
[  529.553501] CE: hpet increasing min_delta_ns to 75936 nsec
[  529.873542] CE: hpet increasing min_delta_ns to 113904 nsec
[  530.060998] CE: hpet increasing min_delta_ns to 170856 nsec
[  530.060998] CE: hpet increasing min_delta_ns to 256284 nsec
[  530.060998] CE: hpet increasing min_delta_ns to 384426 nsec
[  530.236808] CE: hpet increasing min_delta_ns to 576638 nsec
[  530.236808] CE: hpet increasing min_delta_ns to 864956 nsec
[  530.259115] CE: hpet increasing min_delta_ns to 1297434 nsec
[  530.284588] CE: hpet increasing min_delta_ns to 1946150 nsec
[  530.446966] CE: hpet increasing min_delta_ns to 2919224 nsec
```sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:b7:e8:15
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:27 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f6000000-f6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:c2:11:d8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
```lsb_release -d
```
Description:    Ubuntu 10.04 LTS[lsb_release -d
```]

uname -mr
```
2.6.32-21-generic x86_64
```sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                                                                [ OK ]
```

---

### Post by lidex on 2010-06-17
I believe you need this package:
```
sudo apt-get install b43-fwcutter
```
Check here first though:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/4#wireless")

---

### Post by JohnElway on 2010-06-18
That sounds easy enough, but I would need to be online in order to do that and I can't get a wired connection to work either. Perhaps I could get my wired internet working and then fix my wireless. Any ideas on how to do that?

---

### Post by JohnElway on 2010-06-18
Alright so I was able to manually setup an ethernet connection through terminal, which allowed me to install the b43-fwcutter package. After a reboot my wifi worked flawlessly! So I guess I could mark this thread as solved right now. Although while I'm at it, I would also like to configure my ethernet connection so that it works too, should I ever have to use it. Like I said, I was able to connect through terminal with someone elses instructions, but if I try to connect by clicking the "Auto eth0" option in the network manager, I'm immediately disconnected. 

Anyone have any suggestions on this?

---

