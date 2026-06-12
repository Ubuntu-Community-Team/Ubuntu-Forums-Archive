---
title: "hp 6700 wifi issues AR5001 ath0"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by borderblu on 2010-12-01
**ba-bump

I'm lost with all this wifi stuff. Followed the info. retrieval sticky in this forum, here's my info, maybe somebody can help, plz?? All the commands are listed in the code posting.
Also, I had at least one card working in scan mode yesterday, but I can't figure out where the GUI network manager is that will let me enter my name and password to my secure router, which is using WAP. I tried command line but special characters weren't accepted.

 thnx!!


```


03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1e:68:43:c0:77  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe43:c077/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:256955 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:353314274 (353.3 MB)  TX bytes:18227474 (18.2 MB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1920 (1.9 KB)  TX bytes:1920 (1.9 KB)

ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

vboxnet0  no wireless extensions.

$ lsmod


Module                  Size  Used by
nls_iso8859_1           5264  1 
nls_cp437               6960  1 
vfat                   13232  1 
fat                    59696  1 vfat
binfmt_misc            10300  1 
ppdev                   8504  0 
vboxnetadp              6528  0 
vboxnetflt             14832  0 
vboxdrv              1778028  2 vboxnetadp,vboxnetflt
joydev                 13056  0 
snd_hda_codec_conexant    25552  1 
wlan_scan_sta          16144  0 
ath_rate_sample        14352  1 
snd_hda_intel          31432  4 
snd_hda_codec          87984  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               9560  1 snd_hda_codec
snd_pcm_oss            44928  0 
snd_mixer_oss          19664  1 snd_pcm_oss
snd_pcm                91704  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3540  0 
snd_seq_oss            33856  0 
snd_seq_midi            8448  0 
snd_rawmidi            27296  1 snd_seq_midi
snd_seq_midi_event      8688  2 snd_seq_oss,snd_seq_midi
snd_seq                61664  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26872  2 snd_pcm,snd_seq
snd_seq_device          8388  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
amd64_edac_mod         26944  0 
snd                    79240  20 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                58100  0 
soundcore              10080  1 snd
serio_raw               6772  0 
edac_core              49884  1 amd64_edac_mod
k8temp                  5648  0 
nvidia              11090656  30 
i2c_nforce2             8344  0 
snd_page_alloc         11008  2 snd_hda_intel,snd_pcm
ath_pci               197584  0 
wlan                  253024  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               432128  3 ath_rate_sample,ath_pci
sbp2                   27580  0 
lp                     12644  0 
parport                41548  2 ppdev,lp
video                  23596  0 
output                  3792  1 video
mmc_block              13080  2 
sdhci_pci               9104  0 
sdhci                  20500  1 sdhci_pci
ohci1394               34564  0 
led_class               5272  1 sdhci
ricoh_mmc               4432  0 
ieee1394              101984  2 sbp2,ohci1394
forcedeth              59772  0 


$ dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-11-rt (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #154-Ubuntu SMP PREEMPT RT Wed Jun 9 13:40:34 UTC 2010 (Ubuntu 2.6.31-11.154-rt)
[    0.000000] Command line: root=/dev/mapper/lacey-root ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bbf50000 (usable)
[    0.000000]  BIOS-e820: 00000000bbf50000 - 00000000bbf65000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bbf65000 - 00000000bbf66000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bbf66000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbbf50 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFC0000000 write-back
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
[    0.000000]  modified: 0000000000100000 - 00000000bbf50000 (usable)
[    0.000000]  modified: 00000000bbf50000 - 00000000bbf65000 (ACPI data)
[    0.000000]  modified: 00000000bbf65000 - 00000000bbf66000 (ACPI NVS)
[    0.000000]  modified: 00000000bbf66000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bbf50000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bbe00000 page 2M
[    0.000000]  00bbe00000 - 00bbf50000 page 4k
[    0.000000] kernel direct mapping tables up to bbf50000 @ 8000-d000
[    0.000000] RAMDISK: 37666000 - 37fef18d
[    0.000000] ACPI: RSDP 00000000000f8250 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000bbf5c0ce 0006C (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bbf649ba 000F4 (v03 NVIDIA MCP67-M  06040000 PTL_ 000F4240)
[    0.000000] ACPI: DSDT 00000000bbf5c13a 0880C (v01 NVIDIA    MCP67 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000bbf65fc0 00040
[    0.000000] ACPI: TCPA 00000000bbf64aae 00032 (v01 Phoeni  x       06040000  TL  00000000)
[    0.000000] ACPI: SRAT 00000000bbf64ae0 000A0 (v01 AMD    HAMMER   06040000 AMD  00000001)
[    0.000000] ACPI: SSDT 00000000bbf64b80 00206 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG 00000000bbf64d86 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 00000000bbf64dc2 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: APIC 00000000bbf64dfa 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bbf64e62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 00000000bbf64e8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-c0000000
[    0.000000] NUMA: Allocated memnodemap from b000 - c840
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-00000000bbf50000
[    0.000000]   NODE_DATA [000000000000c840 - 000000000001183f]
[    0.000000]   bootmap [0000000000012000 -  00000000000297ef] pages 18
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 00bbf50000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001b18e00]    TEXT DATA BSS ==> [0001000000 - 0001b18e00]
[    0.000000]   #3 [0037666000 - 0037fef18d]          RAMDISK ==> [0037666000 - 0037fef18d]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0001b19000 - 0001b191a0]              BRK ==> [0001b19000 - 0001b191a0]
[    0.000000]   #6 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000]   #7 [000000b000 - 000000c840]       MEMNODEMAP ==> [000000b000 - 000000c840]
[    0.000000] found SMP MP-table at [ffff8800000f8220] f8220
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff880002000000-ffff8800049fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000bbf50
[    0.000000] On node 0 totalpages: 769769
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3832 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10470 pages used for memmap
[    0.000000]   DMA32 zone: 755306 pages, LIFO batch:31
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
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 26 pages at ffff880001b66000, static data 76228 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 759138
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/mapper/lacey-root ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 1b0000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Memory: 3014304k/3079488k available (5420k kernel code, 412k absent, 64772k reserved, 3680k data, 640k init)
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Preemptible RCU implementation.
[    0.000000] NR_IRQS:2304
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1999.828 MHz processor.
[    0.000015] spurious 8259A interrupt: IRQ7.
[    0.000999] Console: colour VGA+ 80x25
[    0.000999] console [tty0] enabled
[    0.000999] allocated 75497472 bytes of page_cgroup
[    0.000999] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000999] hpet clockevent registered
[    0.000999] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000999] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.65 BogoMIPS (lpj=1999828)
[    0.000999] Security Framework initialized
[    0.000999] AppArmor: AppArmor initialized
[    0.000999] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003935] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.005573] Mount-cache hash table entries: 256
[    0.005750] Initializing cgroup subsys ns
[    0.005754] Initializing cgroup subsys cpuacct
[    0.005759] Initializing cgroup subsys memory
[    0.005772] Initializing cgroup subsys freezer
[    0.005775] Initializing cgroup subsys net_cls
[    0.005793] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.005795] CPU: L2 Cache: 512K (64 bytes/line)
[    0.005798] CPU 0/0x0 -> Node 0
[    0.005800] tseg: 00bbf80000
[    0.005802] CPU: Physical Processor ID: 0
[    0.005804] CPU: Processor Core ID: 0
[    0.005807] mce: CPU supports 5 MCE banks
[    0.005818] using C1E aware idle routine
[    0.005820] Performance Counters: AMD PMU driver.
[    0.005825] ... version:                 0
[    0.005826] ... bit width:               48
[    0.005828] ... generic counters:        4
[    0.005830] ... value mask:              0000ffffffffffff
[    0.005831] ... max period:              00007fffffffffff
[    0.005833] ... fixed-purpose counters:  0
[    0.005835] ... counter mask:            000000000000000f
[    0.006021] ACPI: Core revision 20090521
[    0.018082] Setting APIC routing to flat
[    0.019464] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.029475] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.029999] Booting processor 1 APIC 0x1 ip 0x6000
[    0.029999] Initializing CPU#1
[    0.029999] Calibrating delay using timer specific routine.. 4000.06 BogoMIPS (lpj=2000033)
[    0.029999] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.029999] CPU: L2 Cache: 512K (64 bytes/line)
[    0.029999] CPU 1/0x1 -> Node 0
[    0.029999] CPU: Physical Processor ID: 0
[    0.029999] CPU: Processor Core ID: 1
[    0.029999] mce: CPU supports 5 MCE banks
[    0.029999] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.100446] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.100580] Brought up 2 CPUs
[    0.100583] Total of 2 processors activated (7999.72 BogoMIPS).
[    0.100579] System has AMD C1E enabled
[    0.100579] Switch to broadcast mode on CPU1
[    0.100676] CPU0 attaching sched-domain:
[    0.100679]  domain 0: span 0-1 level MC
[    0.100681]   groups: 0 1
[    0.100687] CPU1 attaching sched-domain:
[    0.100690]  domain 0: span 0-1 level MC
[    0.100692]   groups: 1 0
[    0.100773] Switch to broadcast mode on CPU0
[    0.100773] Booting paravirtualized kernel on bare hardware
[    0.100773] regulator: core version 0.5
[    0.101091] Time:  2:18:36  Date: 12/01/10
[    0.101187] NET: Registered protocol family 16
[    0.101857] node 0 link 0: io port [1000, fffff]
[    0.101861] TOM: 00000000c0000000 aka 3072M
[    0.101864] node 0 link 0: mmio [a0000, bffff]
[    0.101868] node 0 link 0: mmio [c0000000, dfffffff]
[    0.101871] node 0 link 0: mmio [e0000000, efffffff]
[    0.101873] node 0 link 0: mmio [f0000000, fe0bffff]
[    0.101876] bus: [00,ff] on node 0 link 0
[    0.101879] bus: 00 index 0 io port: [0, ffff]
[    0.101881] bus: 00 index 1 mmio: [a0000, bffff]
[    0.101884] bus: 00 index 2 mmio: [c0000000, fcffffffff]
[    0.101898] ACPI: bus type pci registered
[    0.102122] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.102125] PCI: MCFG area at e0000000 reserved in E820
[    0.102261] PCI: Using MMCONFIG at e0000000 - e04fffff
[    0.102263] PCI: Using configuration type 1 for base access
[    0.113100] bio: create slab <bio-0> at 0
[    0.120558] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.120558] ACPI: EC: Look up EC in DSDT
[    0.124076] ACPI: BIOS _OSI(Linux) query ignored
[    0.124450] ACPI: Interpreter enabled
[    0.124456] ACPI: (supports S0 S3 S4 S5)
[    0.124482] ACPI: Using IOAPIC for interrupt routing
[    0.126712] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.142670] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.142674] ACPI: EC: driver started in interrupt mode
[    0.142797] ACPI: No dock devices found.
[    0.142797] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.143227] pci 0000:00:01.1: reg 10 io port: [0x3080-0x30bf]
[    0.144024] pci 0000:00:01.1: reg 20 io port: [0x3040-0x307f]
[    0.144029] pci 0000:00:01.1: reg 24 io port: [0x3000-0x303f]
[    0.144049] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.144055] pci 0000:00:01.1: PME# disabled
[    0.144113] pci 0000:00:01.3: reg 10 32bit mmio: [0xf6200000-0xf627ffff]
[    0.144193] pci 0000:00:02.0: reg 10 32bit mmio: [0xf6486000-0xf6486fff]
[    0.144216] pci 0000:00:02.0: supports D1 D2
[    0.144218] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144222] pci 0000:00:02.0: PME# disabled
[    0.144245] pci 0000:00:02.1: reg 10 32bit mmio: [0xf6489000-0xf64890ff]
[    0.144273] pci 0000:00:02.1: supports D1 D2
[    0.144275] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144278] pci 0000:00:02.1: PME# disabled
[    0.144306] pci 0000:00:04.0: reg 10 32bit mmio: [0xf6487000-0xf6487fff]
[    0.144329] pci 0000:00:04.0: supports D1 D2
[    0.144331] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144334] pci 0000:00:04.0: PME# disabled
[    0.144358] pci 0000:00:04.1: reg 10 32bit mmio: [0xf6489400-0xf64894ff]
[    0.144385] pci 0000:00:04.1: supports D1 D2
[    0.144388] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144391] pci 0000:00:04.1: PME# disabled
[    0.144427] pci 0000:00:06.0: reg 20 io port: [0x30c0-0x30cf]
[    0.144465] pci 0000:00:07.0: reg 10 32bit mmio: [0xf6480000-0xf6483fff]
[    0.144492] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.144495] pci 0000:00:07.0: PME# disabled
[    0.144558] pci 0000:00:09.0: reg 10 io port: [0x30f0-0x30f7]
[    0.144562] pci 0000:00:09.0: reg 14 io port: [0x30e4-0x30e7]
[    0.144566] pci 0000:00:09.0: reg 18 io port: [0x30e8-0x30ef]
[    0.144570] pci 0000:00:09.0: reg 1c io port: [0x30e0-0x30e3]
[    0.144574] pci 0000:00:09.0: reg 20 io port: [0x30d0-0x30df]
[    0.144578] pci 0000:00:09.0: reg 24 32bit mmio: [0xf6484000-0xf6485fff]
[    0.144626] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf6488000-0xf6488fff]
[    0.144630] pci 0000:00:0a.0: reg 14 io port: [0x30f8-0x30ff]
[    0.144635] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf6489c00-0xf6489cff]
[    0.144639] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf6489800-0xf648980f]
[    0.144660] pci 0000:00:0a.0: supports D1 D2
[    0.144662] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144667] pci 0000:00:0a.0: PME# disabled
[    0.144703] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144706] pci 0000:00:0c.0: PME# disabled
[    0.144740] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144743] pci 0000:00:0d.0: PME# disabled
[    0.144766] pci 0000:00:12.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.144771] pci 0000:00:12.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.144777] pci 0000:00:12.0: reg 1c 64bit mmio: [0xf4000000-0xf4ffffff]
[    0.144782] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.144899] pci 0000:02:05.0: reg 10 32bit mmio: [0x000000-0x0007ff]
[    0.144932] pci 0000:02:05.0: supports D1 D2
[    0.144934] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.144938] pci 0000:02:05.0: PME# disabled
[    0.144963] pci 0000:02:05.1: reg 10 32bit mmio: [0xf6100800-0xf61008ff]
[    0.145007] pci 0000:02:05.1: supports D1 D2
[    0.145009] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.145012] pci 0000:02:05.1: PME# disabled
[    0.145041] pci 0000:02:05.2: reg 10 32bit mmio: [0xf6100c00-0xf6100cff]
[    0.145074] pci 0000:02:05.2: supports D1 D2
[    0.145076] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.145080] pci 0000:02:05.2: PME# disabled
[    0.145105] pci 0000:02:05.3: reg 10 32bit mmio: [0xf6101000-0xf61010ff]
[    0.145138] pci 0000:02:05.3: supports D1 D2
[    0.145140] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.145144] pci 0000:02:05.3: PME# disabled
[    0.145170] pci 0000:02:05.4: reg 10 32bit mmio: [0xf6101400-0xf61014ff]
[    0.145203] pci 0000:02:05.4: supports D1 D2
[    0.145205] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.145209] pci 0000:02:05.4: PME# disabled
[    0.145241] pci 0000:00:08.0: transparent bridge
[    0.145245] pci 0000:00:08.0: bridge 32bit mmio: [0xf6100000-0xf61fffff]
[    0.145283] pci 0000:00:0c.0: bridge io port: [0x4000-0x4fff]
[    0.145286] pci 0000:00:0c.0: bridge 32bit mmio: [0xf2000000-0xf3ffffff]
[    0.145290] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.145326] pci 0000:03:00.0: reg 10 64bit mmio: [0xf6000000-0xf600ffff]
[    0.145413] pci 0000:00:0d.0: bridge 32bit mmio: [0xf6000000-0xf60fffff]
[    0.145428] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.145554] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.145585] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.145630] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.186754] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.187041] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.187274] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.187504] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.187733] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.187961] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.188203] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.188433] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.188663] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.188892] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.189140] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.189369] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.189598] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.189828] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.190069] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.190301] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.190532] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.190771] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.191013] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.191539] SCSI subsystem initialized
[    0.197015] libata version 3.00 loaded.
[    0.197068] usbcore: registered new interface driver usbfs
[    0.197080] usbcore: registered new interface driver hub
[    0.197080] usbcore: registered new device driver usb
[    0.198241] ACPI: WMI: Mapper loaded
[    0.198243] PCI: Using ACPI for IRQ routing
[    0.207035] Bluetooth: Core ver 2.15
[    0.207057] NET: Registered protocol family 31
[    0.207057] Bluetooth: HCI device and connection manager initialized
[    0.207057] Bluetooth: HCI socket layer initialized
[    0.207057] NetLabel: Initializing
[    0.207057] NetLabel:  domain hash size = 128
[    0.207057] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.207060] NetLabel:  unlabeled traffic allowed by default
[    0.207156] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.207161] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.221297] pnp: PnP ACPI init
[    0.221323] ACPI: bus type pnp registered
[    0.228077] pnp: PnP ACPI: found 12 devices
[    0.228080] ACPI: ACPI bus type pnp unregistered
[    0.228097] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.228104] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.228108] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.228111] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.228115] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.228118] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.228121] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.228131] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.228135] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.228146] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.228149] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.228153] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.228156] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.228160] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.233570] AppArmor: AppArmor Filesystem Enabled
[    0.233627] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.233630] pci 0000:00:08.0:   IO window: disabled
[    0.233634] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.233637] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.233641] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.233644] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.233647] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.233651] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.233655] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.233658] pci 0000:00:0d.0:   IO window: disabled
[    0.233661] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.233664] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.233673] pci 0000:00:08.0: setting latency timer to 64
[    0.233679] pci 0000:00:0c.0: setting latency timer to 64
[    0.233684] pci 0000:00:0d.0: setting latency timer to 64
[    0.233689] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.233692] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.233695] pci_bus 0000:02: resource 1 mem: [0xf6100000-0xf61fffff]
[    0.233698] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.233700] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.233703] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.233706] pci_bus 0000:04: resource 1 mem: [0xf2000000-0xf3ffffff]
[    0.233709] pci_bus 0000:04: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.233712] pci_bus 0000:03: resource 1 mem: [0xf6000000-0xf60fffff]
[    0.233791] NET: Registered protocol family 2
[    0.234007] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.236357] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.243363] TCP bind hash table entries: 65536 (order: 10, 4194304 bytes)
[    0.246544] TCP: Hash tables configured (established 524288 bind 65536)
[    0.246548] TCP reno registered
[    0.246733] NET: Registered protocol family 1
[    0.246815] Trying to unpack rootfs image as initramfs...
[    0.508176] Freeing initrd memory: 9764k freed
[    0.515942] Simple Boot Flag at 0x36 set to 0x1
[    0.517077] Scanning for low memory corruption every 60 seconds
[    0.517549] audit: initializing netlink socket (disabled)
[    0.517572] type=2000 audit(1291169915.516:1): initialized
[    0.521949] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.522120] VFS: Disk quotas dquot_6.5.2
[    0.522163] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.522714] fuse init (API version 7.12)
[    0.522845] msgmni has been set to 5906
[    0.523132] alg: No test for stdrng (krng)
[    0.523148] io scheduler noop registered
[    0.523150] io scheduler anticipatory registered
[    0.523152] io scheduler deadline registered
[    0.523174] io scheduler cfq registered (default)
[    0.523341] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.523394] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.523453] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.523517] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.523585] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.523658] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.523665] pci 0000:00:12.0: Boot video device
[    0.523938] pcieport-driver 0000:00:0c.0: irq 24 for MSI/MSI-X
[    0.523945] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    0.524215] pcieport-driver 0000:00:0d.0: irq 25 for MSI/MSI-X
[    0.524219] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    0.524484] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.524625] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.528035] ACPI: AC Adapter [ACAD] (on-line)
[    0.528284] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.528288] ACPI: Power Button [PWRF]
[    0.528395] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.528399] ACPI: Sleep Button [SLPB]
[    0.528499] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.531298] ACPI: Lid Switch [LID]
[    0.531441] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    0.531446] ACPI: Power Button [PWRB]
[    0.532017] ACPI: processor limited to max C-state 1
[    0.532101] processor LNXCPU:00: registered as cooling_device0
[    0.532107] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.532232] processor LNXCPU:01: registered as cooling_device1
[    0.532239] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.541732] ACPI Exception: AE_OK, No or invalid critical threshold 20090521 thermal-384
[    0.547614] Linux agpgart interface v0.103
[    0.547619] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.550993] brd: module loaded
[    0.552899] loop: module loaded
[    0.553146] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.553478] ahci 0000:00:09.0: version 3.0
[    0.553956] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    0.553969] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    0.554043] ahci 0000:00:09.0: irq 26 for MSI/MSI-X
[    0.554049] ahci 0000:00:09.0: controller can do NCQ, turning on CAP_NCQ
[    0.554117] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    0.554121] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio slum part 
[    0.554124] ahci 0000:00:09.0: setting latency timer to 64
[    0.555107] scsi0 : ahci
[    0.555861] scsi1 : ahci
[    0.556070] scsi2 : ahci
[    0.556387] scsi3 : ahci
[    0.556649] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 26
[    0.556652] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 26
[    0.556655] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 26
[    0.556658] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 26
[    0.557760] pata_amd 0000:00:06.0: version 0.4.1
[    0.557821] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.557952] scsi4 : pata_amd
[    0.558521] scsi5 : pata_amd
[    0.559145] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    0.559148] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    0.564196] Fixed MDIO Bus: probed
[    0.564417] PPP generic driver version 2.4.2
[    0.564708] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.565192] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.565206] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    0.565230] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.565234] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.565395] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.565436] ehci_hcd 0000:00:02.1: debug port 1
[    0.565440] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.565505] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    0.572096] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.572268] usb usb1: configuration #1 chosen from 1 choice
[    0.572365] hub 1-0:1.0: USB hub found
[    0.572376] hub 1-0:1.0: 7 ports detected
[    0.572937] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    0.572942] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    0.572962] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.572965] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.573085] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.573123] ehci_hcd 0000:00:04.1: debug port 1
[    0.573127] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.573155] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    0.579021] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.579747] usb usb2: configuration #1 chosen from 1 choice
[    0.580023] hub 2-0:1.0: USB hub found
[    0.580034] hub 2-0:1.0: 2 ports detected
[    0.580319] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.581246] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    0.581259] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    0.581282] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.581286] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.581416] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.581487] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    0.635169] usb usb3: configuration #1 chosen from 1 choice
[    0.635257] hub 3-0:1.0: USB hub found
[    0.635268] hub 3-0:1.0: 7 ports detected
[    0.635769] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    0.635774] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    0.635792] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.635795] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.635909] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.635962] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    0.689157] usb usb4: configuration #1 chosen from 1 choice
[    0.689248] hub 4-0:1.0: USB hub found
[    0.689259] hub 4-0:1.0: 2 ports detected
[    0.689396] uhci_hcd: USB Universal Host Controller Interface driver
[    0.689619] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.711770] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.711777] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.712081] mice: PS/2 mouse device common for all mice
[    0.712510] rtc_cmos 00:07: RTC can wake from S4
[    0.712597] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.713063] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.713174] device-mapper: uevent: version 1.0.3
[    0.713979] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.714083] device-mapper: multipath: version 1.1.0 loaded
[    0.714086] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.714282] cpuidle: using governor ladder
[    0.714285] cpuidle: using governor menu
[    0.714328] ata5.00: ATAPI: Optiarc DVD RW AD-7560A, DH10, max MWDMA2
[    0.714354] ata5: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    0.714988] TCP cubic registered
[    0.715055] NET: Registered protocol family 10
[    0.715612] lo: Disabled Privacy Extensions
[    0.715957] NET: Registered protocol family 17
[    0.716066] Bluetooth: L2CAP ver 2.13
[    0.716068] Bluetooth: L2CAP socket layer initialized
[    0.716072] Bluetooth: SCO (Voice Link) ver 0.6
[    0.716073] Bluetooth: SCO socket layer initialized
[    0.716118] Bluetooth: RFCOMM TTY layer initialized
[    0.716121] Bluetooth: RFCOMM socket layer initialized
[    0.716123] Bluetooth: RFCOMM ver 1.11
[    0.716146] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[    0.716204] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x11
[    0.716207] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[    0.716209] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[    0.716211] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    0.716645] PM: Resume from disk failed.
[    0.716661] registered taskstats version 1
[    0.716853]   Magic number: 6:590:307
[    0.716889] tty tty36: hash matches
[    0.716982] rtc_cmos 00:07: setting system clock to 2010-12-01 02:18:37 UTC (1291169917)
[    0.716985] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.716987] EDD information not available.
[    0.721262] ata5.00: configured for MWDMA2
[    0.733334] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.844388] ACPI: Battery Slot [BAT0] (battery present)
[    0.862030] ata3: SATA link down (SStatus 0 SControl 300)
[    0.862051] ata2: SATA link down (SStatus 0 SControl 300)
[    0.862064] ata4: SATA link down (SStatus 0 SControl 300)
[    1.014278] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.014664] ata1.00: ATA-8: WDC WD1200BEVS-60UST0, 01.01A01, max UDMA/100
[    1.014667] ata1.00: 234441648 sectors, multi 16: LBA48 
[    1.015133] ata1.00: configured for UDMA/100
[    1.015287] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
[    1.015585] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.015643] sd 0:0:0:0: [sda] Write Protect is off
[    1.015646] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.015674] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.015678] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.015952]  sda:
[    1.016735] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560A  DH10 PQ: 0 ANSI: 5
[    1.021775] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.021779] Uniform CD-ROM driver Revision: 3.20
[    1.022019] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.022182] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.022227] ata6: port disabled. ignoring.
[    1.065633]  sda1 sda2 < sda5 >
[    1.074281] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.107985] Freeing unused kernel memory: 640k freed
[    1.108400] Write protecting the kernel read-only data: 7696k
[    1.223138] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.223634] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.223649] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.223655] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.271705] ricoh-mmc: Ricoh MMC Controller disabling driver
[    1.271709] ricoh-mmc: Copyright(c) Philip Langdale
[    1.283650] sdhci: Secure Digital Host Controller Interface driver
[    1.283654] sdhci: Copyright(c) Pierre Ossman
[    1.287569] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[    1.287586] ricoh-mmc: Controller is now disabled.
[    1.288156] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[    1.288548] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    1.288561] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    1.342131] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.346546] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[    1.347075] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[    1.347089] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[    1.348134] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.349241] Registered led device: mmc0::
[    1.350285] mmc0: SDHCI controller on PCI [0000:02:05.1] using DMA
[    1.744280] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:43:c0:77
[    1.744285] forcedeth 0000:00:0a.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.767030] mmc0: new high speed SDHC card at address b368
[    1.770758] mmcblk0: mmc0:b368 SDC   14.9 GiB 
[    1.770840]  mmcblk0: p1
[    1.799719] EXT3-fs: INFO: recovery required on readonly filesystem.
[    1.799724] EXT3-fs: write access will be enabled during recovery.
[    2.604193] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b005093d500]
[    2.936667] kjournald starting.  Commit interval 5 seconds
[    2.936694] EXT3-fs: dm-0: orphan cleanup on readonly fs
[    2.936701] ext3_orphan_cleanup: deleting unreferenced inode 5808145
[    2.939156] ext3_orphan_cleanup: deleting unreferenced inode 6317162
[    2.939186] ext3_orphan_cleanup: deleting unreferenced inode 5808141
[    2.939204] ext3_orphan_cleanup: deleting unreferenced inode 5808139
[    2.939221] ext3_orphan_cleanup: deleting unreferenced inode 5808138
[    2.939239] ext3_orphan_cleanup: deleting unreferenced inode 5808132
[    2.939250] ext3_orphan_cleanup: deleting unreferenced inode 5808131
[    2.939279] ext3_orphan_cleanup: deleting unreferenced inode 5808130
[    2.939298] ext3_orphan_cleanup: deleting unreferenced inode 6357007
[    2.939337] ext3_orphan_cleanup: deleting unreferenced inode 6357006
[    2.939356] EXT3-fs: dm-0: 10 orphan inodes deleted
[    2.939358] EXT3-fs: recovery complete.
[    2.964471] EXT3-fs: mounted filesystem with writeback data mode.
[   25.202945] Adding 4796408k swap on /dev/mapper/lacey-swap_1.  Priority:-1 extents:1 across:4796408k 
[   25.209210] udev: starting version 151
[   25.348041] lp: driver loaded but no devices found
[   25.391956] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   25.391972] ath_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   25.391981] ath_pci 0000:03:00.0: setting latency timer to 64
[   25.518450] ACPI Warning: _BQC returned an invalid level 20090521 video-629
[   25.562862] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   25.562888] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   25.576984] acpi device:25: registered as cooling_device2
[   25.577208] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
[   25.577473] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   25.622296] EXT3 FS on dm-0, internal journal
[   25.714650] type=1505 audit(1291169942.496:2): operation="profile_load" pid=3655 name=/sbin/dhclient3
[   25.720632] type=1505 audit(1291169942.502:3): operation="profile_load" pid=3655 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   25.720799] type=1505 audit(1291169942.502:4): operation="profile_load" pid=3655 name=/usr/lib/connman/scripts/dhclient-script
[   25.820710] nvidia: module license 'NVIDIA' taints kernel.
[   25.820715] Disabling lock debugging due to kernel taint
[   25.872987] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   25.895151] EDAC MC: Ver: 2.1.0 Jun  9 2010
[   25.974020] EDAC amd64_edac:  Ver: 3.2.0 Jun  9 2010
[   25.976042] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   25.976049] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   25.976053] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   25.976054]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   25.976056]     Might be a BIOS bug, if BIOS says ECC is enabled
[   25.976057]     Use of the override can cause unknown side effects.
[   25.976369] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   26.171569] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   26.258503] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   26.258519] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   26.260042] HDA Intel 0000:00:07.0: setting latency timer to 64
[   26.272942] MadWifi: ath_attach: Switching rfkill capability off.
[   26.275314] kjournald starting.  Commit interval 5 seconds
[   26.276029] EXT3 FS on sda1, internal journal
[   26.276036] EXT3-fs: mounted filesystem with writeback data mode.
[   26.282885] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[   26.305334] ath_pci: wifi0: Atheros 5424/2424: mem=0xf6000000, irq=19
[   26.492131] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input7
[   26.492225] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input8
[   26.501477] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   26.501493] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   26.501501] nvidia 0000:00:12.0: setting latency timer to 64
[   26.501921] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  256.52  Wed Aug 25 14:13:02 PDT 2010
[   26.640342] type=1505 audit(1291169943.422:5): operation="profile_load" pid=4033 name=/usr/share/gdm/guest-session/Xsession
[   26.642932] type=1505 audit(1291169943.424:6): operation="profile_replace" pid=4034 name=/sbin/dhclient3
[   26.643221] type=1505 audit(1291169943.424:7): operation="profile_replace" pid=4034 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   26.643450] type=1505 audit(1291169943.425:8): operation="profile_replace" pid=4034 name=/usr/lib/connman/scripts/dhclient-script
[   26.648343] type=1505 audit(1291169943.430:9): operation="profile_load" pid=4035 name=/usr/bin/evince
[   26.652243] type=1505 audit(1291169943.433:10): operation="profile_load" pid=4035 name=/usr/bin/evince-previewer
[   26.654658] type=1505 audit(1291169943.436:11): operation="profile_load" pid=4035 name=/usr/bin/evince-thumbnailer
[   26.864572] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   26.967384] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   28.071181] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   28.071185] vboxdrv: Successfully done.
[   28.071188] vboxdrv: Found 2 processor cores.
[   28.072438] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d32380
[   28.072460] vboxdrv: fAsync=1 offMin=0x2161b3 offMax=0x2161b3
[   28.072530] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   28.072533] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[   29.071860] ppdev: user-space parallel port driver
[   30.000282] Clocksource tsc unstable (delta = -73749651 ns)
[   36.801286] eth0: no IPv6 routers present
[11604.699263] CE: hpet increasing min_delta_ns to 15000 nsec
[12050.463544] eth0: link down.
[12054.606049] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[12054.606498] eth0: no link during initialization.
[12054.608863] ADDRCONF(NETDEV_UP): eth0: link is not ready
[12054.787762] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[12054.788182] eth0: no link during initialization.
[12054.790563] ADDRCONF(NETDEV_UP): eth0: link is not ready
[12057.513284] eth0: link up.
[12057.515403] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[12059.282734] eth0: link down.
[12063.783855] eth0: link up.
[12064.180126] eth0: link down.
[12067.744294] eth0: no IPv6 routers present
[12070.012628] eth0: link up.
[12070.188949] eth0: link down.
[12071.732363] eth0: link up.
[12072.097500] eth0: link down.
[12079.513060] eth0: link up.
[12079.679240] eth0: link down.
[12081.211840] eth0: link up.
[12081.713651] eth0: link down.
[12085.154792] eth0: link up.
[12085.331466] eth0: link down.
[12086.884704] eth0: link up.
[12089.043695] eth0: link down.
[12090.586764] eth0: link up.
[12091.769984] eth0: link down.
[12096.857474] eth0: link up.
[12097.254387] eth0: link down.
[12098.818121] eth0: link up.
[12099.100344] eth0: link down.
[12102.771575] eth0: link up.
[12103.116376] eth0: link down.
[12108.287467] eth0: link up.
[12108.443786] eth0: link down.
[12118.930782] eth0: link up.
[12120.628931] eth0: link down.
[12124.478129] eth0: link up.
[12127.508293] eth0: link down.
[12130.790784] eth0: link up.
[12131.283417] eth0: link down.
[12132.814372] eth0: link up.
[12135.131979] eth0: link down.
[12136.641958] eth0: link up.
[12137.502004] eth0: link down.
[12165.195751] eth0: link up.
[12170.031212] eth0: link down.
[12173.218002] eth0: link up.
[12174.026600] eth0: link down.
[12223.216165] eth0: link up.
[12251.526053] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[12251.670587] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[12253.754850] __ratelimit: 18 callbacks suppressed
[12253.754864] type=1503 audit(1291182157.357:18): operation="open" pid=8576 parent=8560 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[12261.719036] eth0: no IPv6 routers present
[12324.864732] eth0: link down.
[12327.602016] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[12327.602439] eth0: no link during initialization.
[12327.604824] ADDRCONF(NETDEV_UP): eth0: link is not ready
[12327.815976] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[12327.816411] eth0: no link during initialization.
[12327.818738] ADDRCONF(NETDEV_UP): eth0: link is not ready
[12338.847601] eth0: link up.
[12338.849689] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[12349.576290] eth0: no IPv6 routers present
[12350.721439] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[12350.838913] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[12352.899479] type=1503 audit(1291182256.502:19): operation="open" pid=8697 parent=8681 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[12361.606045] eth0: no IPv6 routers present
[12709.678847] eth0: link down.
[12712.942354] eth0: link up.
[13826.924527] eth0: link down.
[13828.611748] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[13828.612167] eth0: no link during initialization.
[13828.614955] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13828.836921] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[13828.837346] eth0: no link during initialization.
[13828.839634] ADDRCONF(NETDEV_UP): eth0: link is not ready
[13834.566703] eth0: link up.
[13834.568801] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[13834.672427] eth0: link down.
[13843.343323] eth0: link up.
[13844.837294] eth0: no IPv6 routers present
[13845.170926] eth0: link down.
[13848.555035] eth0: link up.
[13849.827090] eth0: link down.
[13854.605813] eth0: link up.
[13855.070255] eth0: link down.
[13856.618927] eth0: link up.
[13868.215119] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[13868.388797] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[13870.492228] type=1503 audit(1291183774.094:20): operation="open" pid=9292 parent=9276 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[13879.207027] eth0: no IPv6 routers present
[13899.495968] type=1503 audit(1291183803.098:21): operation="open" pid=5944 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[13944.072333] type=1503 audit(1291183847.675:22): operation="open" pid=5944 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[14266.511529] type=1503 audit(1291184170.114:23): operation="open" pid=5944 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[14445.585740] type=1503 audit(1291184349.188:24): operation="open" pid=9484 parent=9457 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/tty"
[14445.940665] type=1503 audit(1291184349.543:25): operation="open" pid=9484 parent=9457 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/sys_vendor"
[14445.940745] type=1503 audit(1291184349.543:26): operation="open" pid=9484 parent=9457 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/board_vendor"
[14445.940808] type=1503 audit(1291184349.543:27): operation="open" pid=9484 parent=9457 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/bios_vendor"
[14445.942142] type=1503 audit(1291184349.544:28): operation="capable" pid=9484 parent=9457 profile="/usr/lib/firefox-3.6.12/firefox-*bin" name="sys_ptrace"
[14445.942168] type=1503 audit(1291184349.544:29): operation="ptrace" pid=9484 parent=9457 profile="/usr/lib/firefox-3.6.12/firefox-*bin" tracer=9484 tracee=9466
[14446.315922] type=1503 audit(1291184349.918:30): operation="open" pid=9486 parent=9469 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/tty"
[14446.676514] type=1503 audit(1291184350.279:31): operation="open" pid=9486 parent=9469 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/sys_vendor"
[14446.676590] type=1503 audit(1291184350.279:32): operation="open" pid=9486 parent=9469 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/board_vendor"
[14446.676649] type=1503 audit(1291184350.279:33): operation="open" pid=9486 parent=9469 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/bios_vendor"
[14488.070151] __ratelimit: 24 callbacks suppressed
[14488.070157] type=1503 audit(1291184391.672:42): operation="open" pid=5944 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[14996.869220] type=1503 audit(1291184900.471:43): operation="open" pid=9572 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[15038.441620] type=1503 audit(1291184942.044:44): operation="open" pid=9572 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[15170.496856] type=1503 audit(1291185074.099:45): operation="open" pid=9572 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[15568.273715] type=1503 audit(1291185471.876:46): operation="open" pid=9572 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[15955.721379] type=1503 audit(1291185859.324:47): operation="open" pid=9572 parent=5902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[15960.086283] type=1503 audit(1291185863.689:48): operation="open" pid=9897 parent=9886 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/tty"
[15960.501476] type=1503 audit(1291185864.104:49): operation="open" pid=9897 parent=9886 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/sys_vendor"
[15960.501514] type=1503 audit(1291185864.104:50): operation="open" pid=9897 parent=9886 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/board_vendor"
[15960.501546] type=1503 audit(1291185864.104:51): operation="open" pid=9897 parent=9886 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/bios_vendor"
[15960.517188] type=1503 audit(1291185864.119:52): operation="open" pid=9897 parent=9886 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/udev/udev.conf"
[15960.519843] type=1503 audit(1291185864.122:53): operation="open" pid=9897 parent=9886 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/pci0000:00/0000:00:07.0/sound/card0/uevent"
[15960.519902] type=1503 audit(1291185864.122:54): operation="open" pid=9897 parent=9886 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/.udev/db/sound:card0"
[15960.530981] type=1503 audit(1291185864.133:55): operation="file_lock" pid=9897 parent=9886 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="wk::" denied_mask="k::" fsuid=1000 ouid=1000 name="/home/lacey/.esd_auth"
[15960.860552] __ratelimit: 3 callbacks suppressed
[15960.860558] type=1503 audit(1291185864.463:57): operation="open" pid=9917 parent=9910 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/tty"
[15961.013392] type=1503 audit(1291185864.616:58): operation="open" pid=9917 parent=9910 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/sys_vendor"
[15961.013424] type=1503 audit(1291185864.616:59): operation="open" pid=9917 parent=9910 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/board_vendor"
[15961.013449] type=1503 audit(1291185864.616:60): operation="open" pid=9917 parent=9910 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/bios_vendor"
[15961.765900] type=1503 audit(1291185865.368:61): operation="open" pid=9922 parent=9902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/tty"
[15961.948498] type=1503 audit(1291185865.551:62): operation="open" pid=9922 parent=9902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/sys_vendor"
[15961.948529] type=1503 audit(1291185865.551:63): operation="open" pid=9922 parent=9902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/board_vendor"
[15961.948553] type=1503 audit(1291185865.551:64): operation="open" pid=9922 parent=9902 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/virtual/dmi/id/bios_vendor"
[55206.709623] npviewer.bin[18901]: segfault at f541e04c ip 00000000f61c2ee7 sp 00000000fff1e9b0 error 4 in libflashplayer.so[f5e23000+b2e000]
[79533.259429] type=1503 audit(1291249436.862:65): operation="open" pid=25258 parent=25147 profile="/usr/lib/firefox-3.6.12/firefox-*bin" requested_mask="::rw" denied_mask="::rw" fsuid=1000 ouid=0 name="/dev/nvidiactl"
[81762.683114] eth0: link down.
[81763.623915] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[81763.624367] eth0: no link during initialization.
[81763.626714] ADDRCONF(NETDEV_UP): eth0: link is not ready
[81763.821491] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[81763.821905] eth0: no link during initialization.
[81763.824175] ADDRCONF(NETDEV_UP): eth0: link is not ready
[81764.366430] eth0: link up.
[81764.368235] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[81764.665222] eth0: link down.
[81766.232889] eth0: link up.
[81766.289282] eth0: link down.
[81768.644553] eth0: link up.
[81769.587241] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[81769.692593] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[81771.775591] type=1503 audit(1291251675.378:66): operation="open" pid=26554 parent=26538 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[81780.542285] eth0: no IPv6 routers present

$ sudo lshw -C network  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:43:c0:77
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.101 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:94:93:40
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11b
       resources: irq:19 memory:f6000000-f600ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Interface doesn't support scanning : Network is down

vboxnet0  Interface doesn't support scanning.

$ iwlist scan ath0
iwlist: unknown command `ath0' (check 'iwlist --help').

$ iwlist scan wifi0
iwlist: unknown command `ath0' (check 'iwlist --help').

$ iwlist scan wlan0
iwlist: unknown command `ath0' (check 'iwlist --help').

$ lsb_release -d
Description:	Ubuntu 10.04.1 LTS

$ uname -mr
2.6.31-11-rt x86_64



```

---

### Post by uncaspi on 2010-12-02
Network manager icon is located in upper right panel. Do you see it? If you don't look in <System><Administration><Startup app or something about startup. Click it and scroll down to you see network-manager and check it.
reboot and see if the icon shows up. From here you can setup your network.

---

### Post by borderblu on 2010-12-02
I don't have network-manager. When i alt-f2, and type "network" the only completion is "network-admin". I've been through its controls and nowhere does it have essid options. 

There are actually two network admin options in Sys > Administration, "Network" and "Network Tools". Neither have options to enter and save my essid or router password.

Is ubuntu dying?? Never had wifi problems until recently. Now I'll get wifi workign only to have to redo it over and over again after an upgrade. What gives?? I wish there was some kind of script that would completely wipe my network admin stuff, all the wireless, and I could just start from scratch using command line only. There seems to be a lot of cruft.

---

