---
title: "Need help with Ubuntu wireless connection"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by X3B on 2009-12-28
Hello,

I can't get wireless to work. Here are all my outputs: 

Machine brand and model: ```
HP Pavillion dv6000
```

Wireless brand/chipset: ```
Sweex LW053/ Ralink Technology, Corp. RT2501USB
```

Iwconfig: ```
wlan1     IEEE 802.11bg  Mode:Managed  Frequency:2.462 GHz  
          Access Point: Not-Associated   Tx-Power=8 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

ifconfig: ```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:31:a1:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:16:0a:23:96:33  
          inet6 addr: fe80::216:aff:fe23:9633/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:675 (675.0 B)  TX bytes:729 (729.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-0A-23-96-33-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

lsmod: ```
benjamin@benjamin:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_conexant    25376  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
arc4                    2144  2 
snd_mixer_oss          18976  1 snd_pcm_oss
ecb                     3296  2 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
rt73usb                29092  0 
crc_itu_t               2336  1 rt73usb
snd_seq_midi            8192  0 
rt2500usb              23364  0 
rt2x00usb              13600  2 rt73usb,rt2500usb
snd_rawmidi            27360  1 snd_seq_midi
sdhci_pci               8928  0 
rt2x00lib              34624  3 rt73usb,rt2500usb,rt2x00usb
amd64_edac_mod         26688  0 
input_polldev           4720  1 rt2x00lib
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
joydev                 13088  0 
lp                     11908  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
mac80211              210104  2 rt2x00usb,rt2x00lib
sdhci                  20484  1 sdhci_pci
ricoh_mmc               4480  0 
edac_core              48876  1 amd64_edac_mod
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
k8temp                  5504  0 
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               5256  2 rt2x00lib,sdhci
cfg80211              109144  2 rt2x00lib,mac80211
parport                40528  2 ppdev,lp
i2c_nforce2             8168  0 
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
psmouse                57124  0 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
serio_raw               6596  0 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
forcedeth              61292  0 
video                  23612  0 
output                  3680  1 video

```

dmesg: ```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=064e3c2a-403c-49c6-bc44-f4614751a1fe ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff00000 (usable)
[    0.000000]  BIOS-e820: 000000007ff00000 - 000000007ff15000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff15000 - 000000007ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff80000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7ff00 max_arch_pfn = 0x400000000
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
[    0.000000]  modified: 0000000000006000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ff00000 (usable)
[    0.000000]  modified: 000000007ff00000 - 000000007ff15000 (ACPI data)
[    0.000000]  modified: 000000007ff15000 - 000000007ff80000 (ACPI NVS)
[    0.000000]  modified: 000000007ff80000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007ff00000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007ff00000 page 4k
[    0.000000] kernel direct mapping tables up to 7ff00000 @ 8000-c000
[    0.000000] RAMDISK: 3786c000 - 37fef53c
[    0.000000] ACPI: RSDP 00000000000f88f0 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 000000007ff0bb67 00040 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 000000007ff14b58 00074 (v01 HP     MCP51M   06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT 000000007ff0bba7 08FB1 (v01 HP       MCP51M 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 000000007ff15fc0 00040
[    0.000000] ACPI: SSDT 000000007ff14bcc 001C4 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG 000000007ff14d90 0003C (v01 HP       MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 000000007ff14dcc 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 000000007ff14e04 0005E (v01 HP     	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 000000007ff14e62 00028 (v01     HP $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 000000007ff14e8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ff00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ff00000
[    0.000000]   NODE_DATA [000000000000a000 - 000000000000efff]
[    0.000000]   bootmap [000000000000f000 -  000000000001efdf] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007ff00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786c000 - 0037fef53c]          RAMDISK ==> [003786c000 - 0037fef53c]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e317c]              BRK ==> [00019e3000 - 00019e317c]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000f8920] f8920
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007ff00
[    0.000000] On node 0 totalpages: 523928
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 103 pages reserved
[    0.000000]   DMA zone: 3833 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7109 pages used for memmap
[    0.000000]   DMA32 zone: 512827 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f4000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 516660
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=064e3c2a-403c-49c6-bc44-f4614751a1fe ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 184000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 2048808k/2096128k available (5313k kernel code, 416k absent, 46904k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1808.412 MHz processor.
[    0.000015] spurious 8259A interrupt: IRQ7.
[    0.002144] Console: colour VGA+ 80x25
[    0.002148] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3616.82 BogoMIPS (lpj=18084120)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] tseg: 007ff80000
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 5 MCE banks
[    0.010000] using C1E aware idle routine
[    0.010000] Performance Counters: AMD PMU driver.
[    0.010000] ... version:                 0
[    0.010000] ... bit width:               48
[    0.010000] ... generic counters:        4
[    0.010000] ... value mask:              0000ffffffffffff
[    0.010000] ... max period:              00007fffffffffff
[    0.010000] ... fixed-purpose counters:  0
[    0.010000] ... counter mask:            000000000000000f
[    0.010000] ACPI: Core revision 20090521
[    0.020076] Setting APIC routing to flat
[    0.020606] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.121663] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3616.50 BogoMIPS (lpj=18082546)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 5 MCE banks
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.010000] System has AMD C1E enabled
[    0.010000] Switch to broadcast mode on CPU1
[    0.280482] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[    0.280496] Brought up 2 CPUs
[    0.280500] Total of 2 processors activated (7233.33 BogoMIPS).
[    0.280639] CPU0 attaching sched-domain:
[    0.280643]  domain 0: span 0-1 level MC
[    0.280646]   groups: 0 1
[    0.280651] CPU1 attaching sched-domain:
[    0.280654]  domain 0: span 0-1 level MC
[    0.280656]   groups: 1 0
[    0.280736] Switch to broadcast mode on CPU0
[    0.280736] Booting paravirtualized kernel on bare hardware
[    0.280736] regulator: core version 0.5
[    0.280736] Time: 11:28:58  Date: 12/28/09
[    0.280736] NET: Registered protocol family 16
[    0.280736] node 0 link 0: io port [1000, fffff]
[    0.280736] TOM: 0000000080000000 aka 2048M
[    0.280736] node 0 link 0: mmio [e0000000, efffffff]
[    0.280736] node 0 link 0: mmio [a0000, bffff]
[    0.280736] node 0 link 0: mmio [80000000, fe0bffff]
[    0.280736] bus: [00,ff] on node 0 link 0
[    0.280736] bus: 00 index 0 io port: [0, ffff]
[    0.280736] bus: 00 index 1 mmio: [80000000, fcffffffff]
[    0.280736] bus: 00 index 2 mmio: [a0000, bffff]
[    0.280736] ACPI: bus type pci registered
[    0.280736] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6
[    0.280736] PCI: MCFG area at e0000000 reserved in E820
[    0.280736] PCI: Using MMCONFIG at e0000000 - e06fffff
[    0.280736] PCI: Using configuration type 1 for base access
[    0.281463] bio: create slab <bio-0> at 0
[    0.281463] ACPI: EC: Look up EC in DSDT
[    0.283545] ACPI: BIOS _OSI(Linux) query ignored
[    0.283939] ACPI: Interpreter enabled
[    0.283943] ACPI: (supports S0 S3 S4 S5)
[    0.283965] ACPI: Using IOAPIC for interrupt routing
[    0.281463] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.325631] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.325634] ACPI: EC: driver started in interrupt mode
[    0.325901] ACPI: No dock devices found.
[    0.326042] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.326378] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.326382] pci 0000:00:02.0: PME# disabled
[    0.326424] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.326428] pci 0000:00:03.0: PME# disabled
[    0.326469] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.326472] pci 0000:00:04.0: PME# disabled
[    0.326686] pci 0000:00:0a.0: reg 10 io port: [0x1d00-0x1d7f]
[    0.326771] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.326779] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.326810] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.326817] pci 0000:00:0a.1: PME# disabled
[    0.326857] pci 0000:00:0a.3: reg 10 32bit mmio: [0xc0040000-0xc007ffff]
[    0.326971] pci 0000:00:0b.0: reg 10 32bit mmio: [0xc0004000-0xc0004fff]
[    0.327019] pci 0000:00:0b.0: supports D1 D2
[    0.327022] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.327028] pci 0000:00:0b.0: PME# disabled
[    0.327069] pci 0000:00:0b.1: reg 10 32bit mmio: [0xc0005000-0xc00050ff]
[    0.327119] pci 0000:00:0b.1: supports D1 D2
[    0.327121] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.327126] pci 0000:00:0b.1: PME# disabled
[    0.327184] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.327249] pci 0000:00:0e.0: reg 10 io port: [0x30c0-0x30c7]
[    0.327256] pci 0000:00:0e.0: reg 14 io port: [0x30b4-0x30b7]
[    0.327263] pci 0000:00:0e.0: reg 18 io port: [0x30b8-0x30bf]
[    0.327270] pci 0000:00:0e.0: reg 1c io port: [0x30b0-0x30b3]
[    0.327277] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.327283] pci 0000:00:0e.0: reg 24 32bit mmio: [0xc0006000-0xc0006fff]
[    0.327419] pci 0000:00:10.1: reg 10 32bit mmio: [0xc0000000-0xc0003fff]
[    0.327469] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.327474] pci 0000:00:10.1: PME# disabled
[    0.327523] pci 0000:00:14.0: reg 10 32bit mmio: [0xc0008000-0xc0008fff]
[    0.327530] pci 0000:00:14.0: reg 14 io port: [0x30e0-0x30e7]
[    0.327565] pci 0000:00:14.0: supports D1 D2
[    0.327568] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.327572] pci 0000:00:14.0: PME# disabled
[    0.327711] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]
[    0.327715] pci 0000:00:02.0: bridge 32bit mmio: [0xc2000000-0xc3ffffff]
[    0.327721] pci 0000:00:02.0: bridge 64bit mmio pref: [0xc8200000-0xc83fffff]
[    0.327776] pci 0000:00:03.0: bridge io port: [0x5000-0x5fff]
[    0.327779] pci 0000:00:03.0: bridge 32bit mmio: [0xc4000000-0xc5ffffff]
[    0.327784] pci 0000:00:03.0: bridge 64bit mmio pref: [0xc8400000-0xc85fffff]
[    0.327811] pci 0000:05:00.0: reg 10 32bit mmio: [0xc7000000-0xc7ffffff]
[    0.327820] pci 0000:05:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.327829] pci 0000:05:00.0: reg 1c 64bit mmio: [0xc6000000-0xc6ffffff]
[    0.327837] pci 0000:05:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.327912] pci 0000:00:04.0: bridge 32bit mmio: [0xc6000000-0xc7ffffff]
[    0.327916] pci 0000:00:04.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.327961] pci 0000:07:05.0: reg 10 32bit mmio: [0xc8000000-0xc80007ff]
[    0.328011] pci 0000:07:05.0: supports D1 D2
[    0.328013] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.328018] pci 0000:07:05.0: PME# disabled
[    0.328055] pci 0000:07:05.1: reg 10 32bit mmio: [0xc8000800-0xc80008ff]
[    0.328104] pci 0000:07:05.1: supports D1 D2
[    0.328107] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.328112] pci 0000:07:05.1: PME# disabled
[    0.328148] pci 0000:07:05.2: reg 10 32bit mmio: [0xc8000c00-0xc8000cff]
[    0.328198] pci 0000:07:05.2: supports D1 D2
[    0.328200] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.328205] pci 0000:07:05.2: PME# disabled
[    0.328242] pci 0000:07:05.3: reg 10 32bit mmio: [0xc8001000-0xc80010ff]
[    0.328292] pci 0000:07:05.3: supports D1 D2
[    0.328294] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.328299] pci 0000:07:05.3: PME# disabled
[    0.328335] pci 0000:07:05.4: reg 10 32bit mmio: [0xc8001400-0xc80014ff]
[    0.328385] pci 0000:07:05.4: supports D1 D2
[    0.328388] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.328393] pci 0000:07:05.4: PME# disabled
[    0.328442] pci 0000:00:10.0: transparent bridge
[    0.328448] pci 0000:00:10.0: bridge 32bit mmio: [0xc8000000-0xc80fffff]
[    0.328466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.328578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.328614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[    0.328652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.328688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.353127] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[    0.353333] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.353532] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[    0.353730] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.353928] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *11
[    0.354125] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.354324] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.354522] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[    0.354721] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.354919] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[    0.355117] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[    0.355324] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.355522] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[    0.355721] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[    0.355921] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[    0.356120] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[    0.356320] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[    0.356528] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[    0.356734] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[    0.356955] SCSI subsystem initialized
[    0.360026] libata version 3.00 loaded.
[    0.360053] usbcore: registered new interface driver usbfs
[    0.360053] usbcore: registered new interface driver hub
[    0.360053] usbcore: registered new device driver usb
[    0.360077] ACPI: WMI: Mapper loaded
[    0.360080] PCI: Using ACPI for IRQ routing
[    0.390008] Bluetooth: Core ver 2.15
[    0.400015] NET: Registered protocol family 31
[    0.400018] Bluetooth: HCI device and connection manager initialized
[    0.400021] Bluetooth: HCI socket layer initialized
[    0.400024] NetLabel: Initializing
[    0.400025] NetLabel:  domain hash size = 128
[    0.400027] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400043] NetLabel:  unlabeled traffic allowed by default
[    0.400254] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.400260] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.430027] Switched to high resolution mode on CPU 0
[    0.430058] Switched to high resolution mode on CPU 1
[    0.442556] pnp: PnP ACPI init
[    0.442576] ACPI: bus type pnp registered
[    0.446453] pnp: PnP ACPI: found 13 devices
[    0.446455] ACPI: ACPI bus type pnp unregistered
[    0.446468] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.446475] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.446479] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.446482] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.446486] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.446492] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved
[    0.446499] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.446502] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.446506] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.446509] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.446513] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.446516] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.446519] system 00:04: ioport range 0x2000-0x203f has been reserved
[    0.446525] system 00:05: ioport range 0x360-0x361 has been reserved
[    0.446528] system 00:05: ioport range 0x380-0x383 has been reserved
[    0.446536] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.451253] AppArmor: AppArmor Filesystem Enabled
[    0.451304] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.451308] pci 0000:00:02.0:   IO window: 0x4000-0x4fff
[    0.451312] pci 0000:00:02.0:   MEM window: 0xc2000000-0xc3ffffff
[    0.451317] pci 0000:00:02.0:   PREFETCH window: 0x000000c8200000-0x000000c83fffff
[    0.451322] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03
[    0.451326] pci 0000:00:03.0:   IO window: 0x5000-0x5fff
[    0.451330] pci 0000:00:03.0:   MEM window: 0xc4000000-0xc5ffffff
[    0.451334] pci 0000:00:03.0:   PREFETCH window: 0x000000c8400000-0x000000c85fffff
[    0.451342] pci 0000:05:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.451346] pci 0000:00:04.0: PCI bridge, secondary bus 0000:05
[    0.451348] pci 0000:00:04.0:   IO window: disabled
[    0.451352] pci 0000:00:04.0:   MEM window: 0xc6000000-0xc7ffffff
[    0.451356] pci 0000:00:04.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.451362] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.451364] pci 0000:00:10.0:   IO window: disabled
[    0.451369] pci 0000:00:10.0:   MEM window: 0xc8000000-0xc80fffff
[    0.451373] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.451385] pci 0000:00:02.0: setting latency timer to 64
[    0.451391] pci 0000:00:03.0: setting latency timer to 64
[    0.451396] pci 0000:00:04.0: setting latency timer to 64
[    0.451402] pci 0000:00:10.0: setting latency timer to 64
[    0.451407] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.451410] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.451414] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]
[    0.451417] pci_bus 0000:01: resource 1 mem: [0xc2000000-0xc3ffffff]
[    0.451420] pci_bus 0000:01: resource 2 pref mem [0xc8200000-0xc83fffff]
[    0.451424] pci_bus 0000:03: resource 0 io:  [0x5000-0x5fff]
[    0.451427] pci_bus 0000:03: resource 1 mem: [0xc4000000-0xc5ffffff]
[    0.451430] pci_bus 0000:03: resource 2 pref mem [0xc8400000-0xc85fffff]
[    0.451433] pci_bus 0000:05: resource 1 mem: [0xc6000000-0xc7ffffff]
[    0.451436] pci_bus 0000:05: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.451439] pci_bus 0000:07: resource 1 mem: [0xc8000000-0xc80fffff]
[    0.451443] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.451446] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.451491] NET: Registered protocol family 2
[    0.451639] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.452719] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.455644] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.456347] TCP: Hash tables configured (established 262144 bind 65536)
[    0.456351] TCP reno registered
[    0.456463] NET: Registered protocol family 1
[    0.456537] Trying to unpack rootfs image as initramfs...
[    0.674219] Freeing initrd memory: 7693k freed
[    0.679551] Simple Boot Flag at 0x36 set to 0x1
[    0.679782] Scanning for low memory corruption every 60 seconds
[    0.679943] audit: initializing netlink socket (disabled)
[    0.679961] type=2000 audit(1261999737.672:1): initialized
[    0.690456] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.692132] VFS: Disk quotas dquot_6.5.2
[    0.692195] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.692944] fuse init (API version 7.12)
[    0.693043] msgmni has been set to 4016
[    0.693348] alg: No test for stdrng (krng)
[    0.693364] io scheduler noop registered
[    0.693367] io scheduler anticipatory registered
[    0.693369] io scheduler deadline registered
[    0.693416] io scheduler cfq registered (default)
[    0.693441] pci 0000:00:00.0: Found disabled HT MSI Mapping
[    0.693447] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.693487] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.693513] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.693542] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.912645] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.912700] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.912758] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.912782] pci 0000:05:00.0: Boot video device
[    0.913145]   alloc irq_desc for 24 on node 0
[    0.913148]   alloc kstat_irqs on node 0
[    0.913157] pcieport-driver 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.913163] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.913313]   alloc irq_desc for 25 on node 0
[    0.913315]   alloc kstat_irqs on node 0
[    0.913321] pcieport-driver 0000:00:03.0: irq 25 for MSI/MSI-X
[    0.913326] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.913463]   alloc irq_desc for 26 on node 0
[    0.913465]   alloc kstat_irqs on node 0
[    0.913471] pcieport-driver 0000:00:04.0: irq 26 for MSI/MSI-X
[    0.913475] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    0.913566] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.913595] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.914611] ACPI: AC Adapter [ACAD] (on-line)
[    0.914699] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.914704] ACPI: Power Button [PWRF]
[    0.914759] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.914762] ACPI: Power Button [PWRB]
[    0.914806] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.914809] ACPI: Sleep Button [SLPB]
[    0.914859] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.915933] ACPI: Lid Switch [LID]
[    0.916255] ACPI: processor limited to max C-state 1
[    0.916291] processor LNXCPU:00: registered as cooling_device0
[    0.916334] processor LNXCPU:01: registered as cooling_device1
[    0.921150] thermal LNXTHERM:01: registered as thermal_zone0
[    0.921159] ACPI: Thermal Zone [THRM] (59 C)
[    0.922611] Linux agpgart interface v0.103
[    0.922616] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.923906] brd: module loaded
[    0.924394] loop: module loaded
[    0.924484] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.924794] sata_nv 0000:00:0e.0: version 3.5
[    0.924806] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    0.925163] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    0.925167]   alloc irq_desc for 23 on node 0
[    0.925169]   alloc kstat_irqs on node 0
[    0.925181] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    0.925184] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.925246] sata_nv 0000:00:0e.0: setting latency timer to 64
[    0.925464] scsi0 : sata_nv
[    0.925591] scsi1 : sata_nv
[    0.925752] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23
[    0.925756] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23
[    0.925998] pata_amd 0000:00:0d.0: version 0.4.1
[    0.926050] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.926137] scsi2 : pata_amd
[    0.926342] scsi3 : pata_amd
[    0.927032] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    0.927035] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    0.927883] Fixed MDIO Bus: probed
[    0.927920] PPP generic driver version 2.4.2
[    0.928068] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.928584] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.928589]   alloc irq_desc for 22 on node 0
[    0.928592]   alloc kstat_irqs on node 0
[    0.928604] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    0.928623] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.928627] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.928719] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.928763] ehci_hcd 0000:00:0b.1: debug port 1
[    0.928769] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.928796] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[    0.940038] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.940126] usb usb1: configuration #1 chosen from 1 choice
[    0.940157] hub 1-0:1.0: USB hub found
[    0.940170] hub 1-0:1.0: 8 ports detected
[    0.940286] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.940690] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[    0.940695] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22
[    0.940709] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.940712] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.940750] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.940771] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xc0004000
[    1.002130] usb usb2: configuration #1 chosen from 1 choice
[    1.002158] hub 2-0:1.0: USB hub found
[    1.002170] hub 2-0:1.0: 8 ports detected
[    1.002261] uhci_hcd: USB Universal Host Controller Interface driver
[    1.002398] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.020161] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.020167] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.020247] mice: PS/2 mouse device common for all mice
[    1.020391] rtc_cmos 00:09: RTC can wake from S4
[    1.020433] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    1.020477] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.020586] device-mapper: uevent: version 1.0.3
[    1.020704] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.020777] device-mapper: multipath: version 1.1.0 loaded
[    1.020781] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.020954] cpuidle: using governor ladder
[    1.020956] cpuidle: using governor menu
[    1.021448] TCP cubic registered
[    1.021595] NET: Registered protocol family 10
[    1.022092] lo: Disabled Privacy Extensions
[    1.022411] NET: Registered protocol family 17
[    1.022438] Bluetooth: L2CAP ver 2.13
[    1.022440] Bluetooth: L2CAP socket layer initialized
[    1.022444] Bluetooth: SCO (Voice Link) ver 0.6
[    1.022446] Bluetooth: SCO socket layer initialized
[    1.022483] Bluetooth: RFCOMM TTY layer initialized
[    1.022486] Bluetooth: RFCOMM socket layer initialized
[    1.022488] Bluetooth: RFCOMM ver 1.11
[    1.022532] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[    1.022581] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[    1.022583] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15
[    1.022586] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[    1.022739] PM: Resume from disk failed.
[    1.022753] registered taskstats version 1
[    1.022945]   Magic number: 5:234:480
[    1.023060] rtc_cmos 00:09: setting system clock to 2009-12-28 11:28:59 UTC (1261999739)
[    1.023063] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.023065] EDD information not available.
[    1.033981] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.080071] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.100834] ata3.00: ATAPI: MATSHITADVD-RAM UJ-851S, 1.50, max MWDMA2
[    1.100863] ata3: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    1.101014] ata1.00: ATA-7: WDC WD1600BEVS-60RST0, 04.01G04, max UDMA/100
[    1.101018] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.140783] ata3.00: configured for MWDMA2
[    1.140891] ata1.00: configured for UDMA/100
[    1.191296] ACPI: Battery Slot [BAT0] (battery present)
[    1.191461] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-6 04.0 PQ: 0 ANSI: 5
[    1.191616] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.202671] ata2: SATA link down (SStatus 0 SControl 300)
[    1.202676] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.202735] sd 0:0:0:0: [sda] Write Protect is off
[    1.202739] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.202763] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.202953]  sda:
[    1.204503] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-851S  1.50 PQ: 0 ANSI: 5
[    1.208801] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.208804] Uniform CD-ROM driver Revision: 3.20
[    1.208902] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.208945] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.208981] ata4: port disabled. ignoring.
[    1.253216]  sda1 sda2 sda3 <
[    1.260040] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.274092]  sda5 sda6 >
[    1.295147] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.422027] usb 1-4: configuration #1 chosen from 1 choice
[    1.450821] Freeing unused kernel memory: 660k freed
[    1.451150] Write protecting the kernel read-only data: 7580k
[    1.542667] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.663512] acpi device:2a: registered as cooling_device2
[    1.663684] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:27/device:28/input/input6
[    1.663733] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.668951] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.669370] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.669377]   alloc irq_desc for 20 on node 0
[    1.669379]   alloc kstat_irqs on node 0
[    1.669394] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    1.669400] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.669462] nv_probe: set workaround bit for reversed mac addr
[    1.697100] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    1.697120] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5
[    1.762073] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[c8000000-c80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.855938] usb 1-6: configuration #1 chosen from 1 choice
[    2.191249] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:31:a1:ca
[    2.191255] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    2.973357] PM: Starting manual resume from disk
[    2.973363] PM: Resume from partition 8:6
[    2.973365] PM: Checking hibernation image.
[    2.973582] PM: Resume from disk failed.
[    3.022913] EXT4-fs (sda5): barriers enabled
[    3.047936] kjournald2 starting: pid 430, dev sda5:8, commit interval 5 seconds
[    3.047951] EXT4-fs (sda5): delayed allocation enabled
[    3.047955] EXT4-fs: file extents enabled
[    3.059014] EXT4-fs: mballoc enabled
[    3.059036] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.092686] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0010671900]
[    3.856779] type=1505 audit(1261999742.329:2): operation="profile_load" pid=453 name=/usr/share/gdm/guest-session/Xsession
[    3.997666] type=1505 audit(1261999742.466:3): operation="profile_load" pid=454 name=/sbin/dhclient3
[    3.997748] type=1505 audit(1261999742.466:4): operation="profile_load" pid=454 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.997801] type=1505 audit(1261999742.466:5): operation="profile_load" pid=454 name=/usr/lib/connman/scripts/dhclient-script
[   14.321343] type=1505 audit(1261999752.789:6): operation="profile_load" pid=455 name=/usr/bin/evince
[   14.322120] type=1505 audit(1261999752.789:7): operation="profile_load" pid=455 name=/usr/bin/evince-previewer
[   14.322970] type=1505 audit(1261999752.799:8): operation="profile_load" pid=455 name=/usr/bin/evince-thumbnailer
[   14.601925] type=1505 audit(1261999753.069:9): operation="profile_load" pid=457 name=/usr/lib/cups/backend/cups-pdf
[   14.602074] type=1505 audit(1261999753.069:10): operation="profile_load" pid=457 name=/usr/sbin/cupsd
[   14.681010] type=1505 audit(1261999753.149:11): operation="profile_load" pid=458 name=/usr/sbin/tcpdump
[   15.851810] Adding 2963952k swap on /dev/sda6.  Priority:-1 extents:1 across:2963952k 
[   16.273264] EXT4-fs (sda5): internal journal on sda5:8
[   16.534369] udev: starting version 147
[   18.349075] Linux video capture interface: v2.00
[   18.402178] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   18.404203] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4:1.0/input/input7
[   18.404257] usbcore: registered new interface driver uvcvideo
[   18.404260] USB Video Class driver (v0.1.0)
[   18.810136] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   18.810161] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   19.032625] cfg80211: Calling CRDA to update world regulatory domain
[   19.060725] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   19.425764] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   19.487367] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   19.690043] EDAC MC: Ver: 2.1.0 Oct 16 2009
[   19.690752] ricoh-mmc: Ricoh MMC Controller disabling driver
[   19.690755] ricoh-mmc: Copyright(c) Philip Langdale
[   19.691687] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   19.691711] ricoh-mmc: Controller is now disabled.
[   19.789266] sdhci: Secure Digital Host Controller Interface driver
[   19.789270] sdhci: Copyright(c) Pierre Ossman
[   19.893010] lp: driver loaded but no devices found
[   19.953939] cfg80211: World regulatory domain updated:
[   19.953944] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.953948] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.953951] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.953954] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.953957] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.953960] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.131893] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.515138] type=1505 audit(1261996158.989:12): operation="profile_replace" pid=842 name=/usr/share/gdm/guest-session/Xsession
[   20.544661] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[   20.556440] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   20.556448] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   20.556452] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   20.556454]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   20.556455]     Might be a BIOS bug, if BIOS says ECC is enabled
[   20.556456]     Use of the override can cause unknown side effects.
[   20.556640] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   20.600684] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   20.601090] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   20.601107] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7
[   20.601227] Registered led device: mmc0::
[   20.601274] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO
[   20.676553] type=1505 audit(1261996159.149:13): operation="profile_replace" pid=843 name=/sbin/dhclient3
[   20.676718] type=1505 audit(1261996159.149:14): operation="profile_replace" pid=843 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   20.676812] type=1505 audit(1261996159.149:15): operation="profile_replace" pid=843 name=/usr/lib/connman/scripts/dhclient-script
[   20.791830] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   20.791837] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   20.791895] usbcore: registered new interface driver rt2500usb
[   21.457208] phy1: Selected rate control algorithm 'minstrel'
[   21.458019] Registered led device: rt73usb-phy1::radio
[   21.458038] Registered led device: rt73usb-phy1::assoc
[   21.458058] Registered led device: rt73usb-phy1::quality
[   21.458603] usbcore: registered new interface driver rt73usb
[   21.595118] udev: renamed network interface wlan0 to wlan1
[   21.710434] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   21.710441]   alloc irq_desc for 21 on node 0
[   21.710444]   alloc kstat_irqs on node 0
[   21.710459] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21
[   21.710511] HDA Intel 0000:00:10.1: setting latency timer to 64
[   24.627703] rt73usb 1-6:1.0: firmware: requesting rt73.bin
[   25.018499] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   25.059224] eth0: no link during initialization.
[   25.059941] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.928700] usplash:393 freeing invalid memtype ffffffffd0000000-ffffffffd4000000
[   31.475633] type=1505 audit(1261996169.946:16): operation="profile_replace" pid=847 name=/usr/bin/evince
[   31.477321] type=1505 audit(1261996169.946:17): operation="profile_replace" pid=847 name=/usr/bin/evince-previewer
[   31.478702] type=1505 audit(1261996169.946:18): operation="profile_replace" pid=847 name=/usr/bin/evince-thumbnailer
[   31.785719] type=1505 audit(1261996170.256:19): operation="profile_replace" pid=1241 name=/usr/lib/cups/backend/cups-pdf
[   31.785964] type=1505 audit(1261996170.256:20): operation="profile_replace" pid=1241 name=/usr/sbin/cupsd
[   31.868291] type=1505 audit(1261996170.336:21): operation="profile_replace" pid=1260 name=/usr/sbin/tcpdump
[   32.833869] ppdev: user-space parallel port driver
[   95.000041] Clocksource tsc unstable (delta = -160687070 ns)
[  157.800472] wlan1: authenticate with AP 00:17:3f:91:be:81
[  157.802486] wlan1: authenticated
[  157.802494] wlan1: associate with AP 00:17:3f:91:be:81
[  157.808235] wlan1: RX AssocResp from 00:17:3f:91:be:81 (capab=0x11 status=0 aid=3)
[  157.808243] wlan1: associated
[  157.823762] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  167.820745] wlan1: disassociating by local choice (reason=3)
[  167.976720] wlan1: authenticate with AP 00:17:3f:91:be:81
[  167.978481] wlan1: authenticated
[  167.978487] wlan1: associate with AP 00:17:3f:91:be:81
[  168.037483] wlan1: RX AssocResp from 00:17:3f:91:be:81 (capab=0x11 status=0 aid=3)
[  168.037491] wlan1: associated
[  168.290039] wlan1: no IPv6 routers present
[  178.051641] wlan1: disassociating by local choice (reason=3)
[  179.545714] wlan1: authenticate with AP 00:17:3f:91:be:81
[  179.547480] wlan1: authenticated
[  179.547486] wlan1: associate with AP 00:17:3f:91:be:81
[  179.550721] wlan1: RX AssocResp from 00:17:3f:91:be:81 (capab=0x11 status=0 aid=3)
[  179.550729] wlan1: associated
[  189.564859] wlan1: disassociating by local choice (reason=3)
[  191.063472] wlan1: authenticate with AP 00:17:3f:91:be:81
[  191.065490] wlan1: authenticated
[  191.065496] wlan1: associate with AP 00:17:3f:91:be:81
[  191.079976] wlan1: RX AssocResp from 00:17:3f:91:be:81 (capab=0x11 status=0 aid=3)
[  191.079984] wlan1: associated
[  201.090885] wlan1: disassociating by local choice (reason=3)
[  202.574223] wlan1: authenticate with AP 00:17:3f:91:be:81
[  202.576489] wlan1: authenticated
[  202.576495] wlan1: associate with AP 00:17:3f:91:be:81
[  202.581346] wlan1: RX AssocResp from 00:17:3f:91:be:81 (capab=0x11 status=0 aid=3)
[  202.581354] wlan1: associated
[  212.593533] wlan1: disassociating by local choice (reason=3)
[  214.084471] wlan1: authenticate with AP 00:17:3f:91:be:81
[  214.086359] wlan1: authenticated
[  214.086365] wlan1: associate with AP 00:17:3f:91:be:81
[  214.119475] wlan1: RX AssocResp from 00:17:3f:91:be:81 (capab=0x11 status=0 aid=3)
[  214.119483] wlan1: associated
[  216.530291] wlan1: disassociating by local choice (reason=3)
```

iwlist scan: ```
wlan1 No scan results
```

lsb_release -d: ```
Ubuntu 9.10
```

uname -r: ```
2.6.31-14-generic
```

sudo /etc/init.d/networking restart:
```
 * Reconfiguring network interfaces...
   ...done.

```

Please I really need help with this problem.

---

### Post by SuperEngineer on 2009-12-28
This has got many others as well as myself out of the same problem....

Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.

for origin see a bug I reported 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492990)

and eventually found the above in a similar bug report [and many thanks to the reporter]..
                 Workaround discussed in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323) has provided a fix

Fixed with:
 Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.
 Connectivity now working as per Jaunty.

---

### Post by X3B on 2009-12-28
> **SuperEngineer said:**
> This has got many others as well as myself out of the same problem....

Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.

for origin see a bug I reported 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492990)

and eventually found the above in a similar bug report [and many thanks to the reporter]..
                 Workaround discussed in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323) has provided a fix

Fixed with:
 Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.
 Connectivity now working as per Jaunty.

Thanks for the fast answer. I added the lines to blacklist.conf and /etc/modules. Rebooted. But it doesn't work. Ubuntu 9.10 keeps asking for my authentication for the network. Which I gave a hundred times. It's a really weird issue.

---

### Post by X3B on 2009-12-30
Does anybody has a familiar problem? Where Ubuntu keeps asking for the WPA password but you already gave it?

I don't know if this is an problem with the driver. Please help as I cannot use Ubuntu with wireless problems.

---

