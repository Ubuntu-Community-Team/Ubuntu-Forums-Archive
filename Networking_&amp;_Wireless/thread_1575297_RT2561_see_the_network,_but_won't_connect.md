---
title: "RT2561 see the network, but won't connect"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by DirtDart on 2010-09-15
Running XBMC (based off Ubuntu 9.10) and trying to get a RT2561-based card to connect to my wireless router.

From my understanding, this card should work right out of the box.

The driver is loaded, the card sees the router and the router can see the card, but the card can't/won't connect to the router.

Router is running DD-WRT, with **no** encryption (yet) or any type of MAC filtering and physically sits about 8' away from the XBMC machine.


Requested info:

**lspci**
```
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:0b.0 USB Controller: NEC Corporation USB (rev 43)
00:0b.1 USB Controller: NEC Corporation USB (rev 43)
00:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0c.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0f.0 RAID bus controller: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
```


**ifconfig wlan1**
```
wlan1     Link encap:Ethernet  HWaddr 00:1a:ef:11:d3:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


**iwconfig wlan1**
```
wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

[B]
lsmod[/B]
```
lsmod
Module                  Size  Used by
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  3 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
arc4                    1660  2 
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                     2524  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
rt61pci                20576  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
crc_itu_t               1852  1 rt61pci
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00pci               7900  1 rt61pci
snd_timer              22276  3 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              29756  2 rt61pci,rt2x00pci
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class               4096  1 rt2x00lib
nvidia               4704948  32 
soundcore               7264  1 snd
lp                      8964  0 
i2c_viapro              7312  0 
input_polldev           3716  1 rt2x00lib
lirc_mceusb            15520  1 
lirc_dev               10804  3 lirc_mceusb
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
mac80211              181076  2 rt2x00pci,rt2x00lib
ppdev                   6688  0 
parport_pc             31940  1 
parport                35340  3 lp,ppdev,parport_pc
shpchp                 32272  0 
cfg80211               93052  2 rt2x00lib,mac80211
psmouse                56500  0 
eeprom_93cx6            1916  1 rt61pci
serio_raw               5280  0 
usbhid                 38208  0 
floppy                 54916  0 
via_agp                 7932  1 
via_rhine              22212  0 
mii                     5212  1 via_rhine
agpgart                34988  2 nvidia,via_agp
sata_via                9184  0 
```


**modinfo rt61pci**
```

filename:       /lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     801A037A3E53BB7E7E9C627
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6,crc-itu-t
vermagic:       2.6.31-16-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)
root@xbmc:/home/tom/driver# modinfo rt2x00lib
filename:       /lib/modules/2.6.31-16-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8B748483F7C6F9AC8B75B63
depends:        mac80211,input-polldev,led-class,cfg80211
vermagic:       2.6.31-16-generic SMP mod_unload modversions 586 
```


**dmesg**
```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-16-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 (Ubuntu 2.6.31-16.53-generic)
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
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  modified: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  modified: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37841000 - 37fef40a
[    0.000000] Allocated new RAMDISK: 008ad000 - 0105b40a
[    0.000000] Move RAMDISK from 0000000037841000 - 0000000037fef409 to 008ad000 - 0105b409
[    0.000000] ACPI: RSDP 000f7e20 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 7ffb0000 00034 (v01 A M I  OEMRSDT  02000826 MSFT 00000097)
[    0.000000] ACPI: FACP 7ffb0200 00084 (v02 A M I  OEMFACP  02000826 MSFT 00000097)
[    0.000000] ACPI: DSDT 7ffb0450 04AED (v01  75D8U 75D8U302 00000302 INTL 02002026)
[    0.000000] ACPI: FACS 7ffc0000 00040
[    0.000000] ACPI: APIC 7ffb0390 00078 (v01 A M I  OEMAPIC  02000826 MSFT 00000097)
[    0.000000] ACPI: MCFG 7ffb0410 0003C (v01 A M I  OEMMCFG  02000826 MSFT 00000097)
[    0.000000] ACPI: OEMB 7ffc0040 00051 (v01 A M I  AMI_OEM  02000826 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac123]              BRK ==> [00008a9000 - 00008ac123]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 000105b40a]      NEW RAMDISK ==> [00008ad000 - 000105b40a]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffb0
[    0.000000] On node 0 totalpages: 524095
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c105c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294562 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, version 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 48
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:7ee00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2066000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
[    0.000000] Kernel command line: root=UUID=f10ef1cd-94d4-4618-ad9b-22edb759ce70 ro quiet splash  xbmc=autostart,nodiskmount,setvolume loglevel=0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10483840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffb0)
[    0.000000] Memory: 2051992k/2096832k available (4566k kernel code, 43428k reserved, 2142k data, 540k init, 1187528k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:848
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2410.855 MHz processor.
[    0.001629] Console: colour VGA+ 80x25
[    0.001633] console [tty0] enabled
[    0.001687] Calibrating delay loop (skipped), value calculated using timer frequency.. 4821.71 BogoMIPS (lpj=9643420)
[    0.001709] Security Framework initialized
[    0.001742] AppArmor: AppArmor initialized
[    0.001750] Mount-cache hash table entries: 512
[    0.001913] Initializing cgroup subsys ns
[    0.001920] Initializing cgroup subsys cpuacct
[    0.001924] Initializing cgroup subsys memory
[    0.001931] Initializing cgroup subsys freezer
[    0.001934] Initializing cgroup subsys net_cls
[    0.001950] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001952] CPU: L2 cache: 1024K
[    0.001955] CPU: Physical Processor ID: 0
[    0.001956] CPU: Processor Core ID: 0
[    0.001960] mce: CPU supports 6 MCE banks
[    0.001970] CPU0: Thermal monitoring enabled (TM1)
[    0.001974] using mwait in idle threads.
[    0.001983] Performance Counters: Core2 events, Intel PMU driver.
[    0.001993] ... version:                 2
[    0.001994] ... bit width:               40
[    0.001995] ... generic counters:        2
[    0.001997] ... value mask:              000000ffffffffff
[    0.001998] ... max period:              000000007fffffff
[    0.002000] ... fixed-purpose counters:  3
[    0.002001] ... counter mask:            0000000700000003
[    0.002007] Checking 'hlt' instruction... OK.
[    0.018420] ACPI: Core revision 20090521
[    0.028584] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070232] CPU0: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz stepping 0d
[    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4821.85 BogoMIPS (lpj=9643700)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.157619] CPU1: Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz stepping 0d
[    0.157636] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.160030] Brought up 2 CPUs
[    0.160032] Total of 2 processors activated (9643.56 BogoMIPS).
[    0.160104] CPU0 attaching sched-domain:
[    0.160107]  domain 0: span 0-1 level MC
[    0.160109]   groups: 0 1
[    0.160114] CPU1 attaching sched-domain:
[    0.160116]  domain 0: span 0-1 level MC
[    0.160118]   groups: 1 0
[    0.160199] Booting paravirtualized kernel on bare hardware
[    0.160199] regulator: core version 0.5
[    0.160199] Time: 22:45:09  Date: 09/13/10
[    0.160199] NET: Registered protocol family 16
[    0.160217] EISA bus registered
[    0.160227] ACPI: bus type pci registered
[    0.160297] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.160300] PCI: Not using MMCONFIG.
[    0.160432] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=128
[    0.160434] PCI: Using configuration type 1 for base access
[    0.161322] bio: create slab <bio-0> at 0
[    0.164226] ACPI: EC: Look up EC in DSDT
[    0.170247] ACPI: Interpreter enabled
[    0.170254] ACPI: (supports S0 S1 S3 S4 S5)
[    0.170275] ACPI: Using IOAPIC for interrupt routing
[    0.170318] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.174301] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.174303] PCI: Using MMCONFIG for extended config space
[    0.180818] ACPI Warning: Incorrect checksum in table [OEMB] - 55, should be 48 20090521 tbutils-246
[    0.180920] ACPI: No dock devices found.
[    0.181194] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.181247] pci 0000:00:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.181718] pci 0000:00:01.0: supports D1
[    0.181786] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.181790] pci 0000:00:02.0: PME# disabled
[    0.181848] pci 0000:00:0b.0: reg 10 32bit mmio: [0xfebfd000-0xfebfdfff]
[    0.181899] pci 0000:00:0b.0: supports D1 D2
[    0.181901] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot
[    0.181905] pci 0000:00:0b.0: PME# disabled
[    0.181942] pci 0000:00:0b.1: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]
[    0.181994] pci 0000:00:0b.1: supports D1 D2
[    0.181995] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot
[    0.182000] pci 0000:00:0b.1: PME# disabled
[    0.182037] pci 0000:00:0b.2: reg 10 32bit mmio: [0xfebff400-0xfebff4ff]
[    0.182088] pci 0000:00:0b.2: supports D1 D2
[    0.182090] pci 0000:00:0b.2: PME# supported from D0 D1 D2 D3hot
[    0.182094] pci 0000:00:0b.2: PME# disabled
[    0.182140] pci 0000:00:0c.0: reg 10 32bit mmio: [0xfebf0000-0xfebf7fff]
[    0.182233] pci 0000:00:0f.0: reg 10 io port: [0xec00-0xec07]
[    0.182240] pci 0000:00:0f.0: reg 14 io port: [0xe880-0xe883]
[    0.182248] pci 0000:00:0f.0: reg 18 io port: [0xe800-0xe807]
[    0.182255] pci 0000:00:0f.0: reg 1c io port: [0xe480-0xe483]
[    0.182262] pci 0000:00:0f.0: reg 20 io port: [0xe400-0xe40f]
[    0.182270] pci 0000:00:0f.0: reg 24 io port: [0xe000-0xe0ff]
[    0.182355] pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.182455] pci 0000:00:10.0: reg 20 io port: [0xd080-0xd09f]
[    0.182486] pci 0000:00:10.0: supports D1 D2
[    0.182488] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182492] pci 0000:00:10.0: PME# disabled
[    0.182549] pci 0000:00:10.1: reg 20 io port: [0xd400-0xd41f]
[    0.182581] pci 0000:00:10.1: supports D1 D2
[    0.182582] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182587] pci 0000:00:10.1: PME# disabled
[    0.182644] pci 0000:00:10.2: reg 20 io port: [0xd480-0xd49f]
[    0.182675] pci 0000:00:10.2: supports D1 D2
[    0.182677] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182682] pci 0000:00:10.2: PME# disabled
[    0.182739] pci 0000:00:10.3: reg 20 io port: [0xdc00-0xdc1f]
[    0.182770] pci 0000:00:10.3: supports D1 D2
[    0.182772] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182776] pci 0000:00:10.3: PME# disabled
[    0.182813] pci 0000:00:10.4: reg 10 32bit mmio: [0xfebff800-0xfebff8ff]
[    0.182865] pci 0000:00:10.4: supports D1 D2
[    0.182867] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182871] pci 0000:00:10.4: PME# disabled
[    0.183077] pci 0000:00:12.0: reg 10 io port: [0xd800-0xd8ff]
[    0.183084] pci 0000:00:12.0: reg 14 32bit mmio: [0xfebffc00-0xfebffcff]
[    0.183133] pci 0000:00:12.0: supports D1 D2
[    0.183134] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183139] pci 0000:00:12.0: PME# disabled
[    0.183280] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.183287] pci 0000:01:00.0: reg 14 32bit mmio: [0xc0000000-0xc7ffffff]
[    0.183309] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe8e0000-0xfe8fffff]
[    0.183378] pci 0000:00:01.0: bridge 32bit mmio: [0xfc800000-0xfe8fffff]
[    0.183383] pci 0000:00:01.0: bridge 32bit mmio pref: [0xbff00000-0xcfefffff]
[    0.183444] pci 0000:00:02.0: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.183460] pci_bus 0000:00: on NUMA node 0
[    0.183464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.183675] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[    0.183762] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.194502] ACPI: PCI Root Bridge [PCI1] (0000:80)
[    0.194564] pci 0000:80:01.0: reg 10 64bit mmio: [0xfeafc000-0xfeafffff]
[    0.194616] pci 0000:80:01.0: PME# supported from D0 D3hot D3cold
[    0.194620] pci 0000:80:01.0: PME# disabled
[    0.194677] pci_bus 0000:80: on NUMA node 0
[    0.194681] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.194831] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.194924] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.195014] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.195104] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.195196] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.195286] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.195376] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.195466] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.195631] SCSI subsystem initialized
[    0.195667] libata version 3.00 loaded.
[    0.195667] usbcore: registered new interface driver usbfs
[    0.195667] usbcore: registered new interface driver hub
[    0.195667] usbcore: registered new device driver usb
[    0.195667] ACPI: WMI: Mapper loaded
[    0.195667] PCI: Using ACPI for IRQ routing
[    0.212007] Bluetooth: Core ver 2.15
[    0.212021] NET: Registered protocol family 31
[    0.212021] Bluetooth: HCI device and connection manager initialized
[    0.212021] Bluetooth: HCI socket layer initialized
[    0.212021] NetLabel: Initializing
[    0.212021] NetLabel:  domain hash size = 128
[    0.212021] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.212032] NetLabel:  unlabeled traffic allowed by default
[    0.224024] pnp: PnP ACPI init
[    0.224054] ACPI: bus type pnp registered
[    0.228040] pnp: PnP ACPI: found 15 devices
[    0.228042] ACPI: ACPI bus type pnp unregistered
[    0.228046] PnPBIOS: Disabled by ACPI PNP
[    0.228061] system 00:07: ioport range 0x295-0x296 has been reserved
[    0.228064] system 00:07: ioport range 0x3e0-0x3e7 has been reserved
[    0.228067] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.228069] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.228071] system 00:07: ioport range 0x400-0x41f has been reserved
[    0.228075] system 00:07: iomem range 0xfeafc000-0xfeafffff has been reserved
[    0.228078] system 00:07: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.228083] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.228085] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.228091] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.228101] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.228104] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.228106] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.228108] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[    0.228111] system 00:0d: iomem range 0xfff80000-0xffffffff has been reserved
[    0.262768] AppArmor: AppArmor Filesystem Enabled
[    0.262801] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.262803] pci 0000:00:01.0:   IO window: disabled
[    0.262809] pci 0000:00:01.0:   MEM window: 0xfc800000-0xfe8fffff
[    0.262813] pci 0000:00:01.0:   PREFETCH window: 0xbff00000-0xcfefffff
[    0.262818] pci 0000:00:02.0: PCI bridge, secondary bus 0000:02
[    0.262819] pci 0000:00:02.0:   IO window: disabled
[    0.262825] pci 0000:00:02.0:   MEM window: 0xfe900000-0xfe9fffff
[    0.262829] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.262846] pci 0000:00:01.0: setting latency timer to 64
[    0.262858]   alloc irq_desc for 27 on node -1
[    0.262860]   alloc kstat_irqs on node -1
[    0.262866] pci 0000:00:02.0: PCI INT A -> GSI 27 (level, low) -> IRQ 27
[    0.262871] pci 0000:00:02.0: setting latency timer to 64
[    0.262877] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.262879] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.262881] pci_bus 0000:01: resource 1 mem: [0xfc800000-0xfe8fffff]
[    0.262883] pci_bus 0000:01: resource 2 pref mem [0xbff00000-0xcfefffff]
[    0.262885] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.262888] pci_bus 0000:80: resource 0 io:  [0x00-0xffff]
[    0.262890] pci_bus 0000:80: resource 1 mem: [0x000000-0xffffffff]
[    0.262931] NET: Registered protocol family 2
[    0.263036] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.263341] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.263978] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.264470] TCP: Hash tables configured (established 131072 bind 65536)
[    0.264474] TCP reno registered
[    0.264652] NET: Registered protocol family 1
[    0.264734] Trying to unpack rootfs image as initramfs...
[    0.474185] Freeing initrd memory: 7865k freed
[    0.479317] cpufreq-nforce2: No nForce2 chipset.
[    0.479352] Scanning for low memory corruption every 60 seconds
[    0.479475] audit: initializing netlink socket (disabled)
[    0.479501] type=2000 audit(1284417908.476:1): initialized
[    0.486744] highmem bounce pool size: 64 pages
[    0.486751] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.488019] VFS: Disk quotas dquot_6.5.2
[    0.488077] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.488555] fuse init (API version 7.12)
[    0.488627] msgmni has been set to 1705
[    0.488820] alg: No test for stdrng (krng)
[    0.488833] io scheduler noop registered
[    0.488835] io scheduler anticipatory registered
[    0.488836] io scheduler deadline registered
[    0.488872] io scheduler cfq registered (default)
[    0.488891] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.489002] pci 0000:01:00.0: Boot video device
[    0.489161]   alloc irq_desc for 48 on node -1
[    0.489163]   alloc kstat_irqs on node -1
[    0.489178] pcieport-driver 0000:00:02.0: irq 48 for MSI/MSI-X
[    0.489189] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.489523] aer 0000:00:02.0:pcie02: service driver aer loaded
[    0.489531] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.489539] Firmware did not grant requested _OSC control
[    0.489565] Firmware did not grant requested _OSC control
[    0.489577] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.489710] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.489714] ACPI: Power Button [PWRF]
[    0.489765] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.489768] ACPI: Power Button [PWRB]
[    0.490308] processor LNXCPU:00: registered as cooling_device0
[    0.490561] processor LNXCPU:01: registered as cooling_device1
[    0.493254] isapnp: Scanning for PnP cards...
[    0.761674] Switched to high resolution mode on CPU 1
[    0.764006] Switched to high resolution mode on CPU 0
[    0.847277] isapnp: No Plug & Play device found
[    0.848193] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.848291] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.848678] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.849580] brd: module loaded
[    0.849966] loop: module loaded
[    0.850033] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.850601] pata_via 0000:00:0f.1: version 0.3.4
[    0.850766] scsi0 : pata_via
[    0.850861] scsi1 : pata_via
[    0.852443] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.852446] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.852765] Fixed MDIO Bus: probed
[    0.852797] PPP generic driver version 2.4.2
[    0.852885] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.852907]   alloc irq_desc for 17 on node -1
[    0.852909]   alloc kstat_irqs on node -1
[    0.852916] ehci_hcd 0000:00:0b.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.852933] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[    0.852988] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 1
[    0.876028] ehci_hcd 0000:00:0b.2: irq 17, io mem 0xfebff400
[    0.888006] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00
[    0.888082] usb usb1: configuration #1 chosen from 1 choice
[    0.888111] hub 1-0:1.0: USB hub found
[    0.888117] hub 1-0:1.0: 5 ports detected
[    0.888179]   alloc irq_desc for 21 on node -1
[    0.888181]   alloc kstat_irqs on node -1
[    0.888185] ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.888194] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.888223] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 2
[    0.888258] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfebff800
[    0.900007] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
[    0.900061] usb usb2: configuration #1 chosen from 1 choice
[    0.900083] hub 2-0:1.0: USB hub found
[    0.900089] hub 2-0:1.0: 8 ports detected
[    0.900144] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.900162]   alloc irq_desc for 19 on node -1
[    0.900163]   alloc kstat_irqs on node -1
[    0.900168] ohci_hcd 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.900176] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.900205] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 3
[    0.900223] ohci_hcd 0000:00:0b.0: irq 19, io mem 0xfebfd000
[    0.985821] usb usb3: configuration #1 chosen from 1 choice
[    0.985843] hub 3-0:1.0: USB hub found
[    0.985850] hub 3-0:1.0: 3 ports detected
[    0.985890]   alloc irq_desc for 16 on node -1
[    0.985892]   alloc kstat_irqs on node -1
[    0.985896] ohci_hcd 0000:00:0b.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.985903] ohci_hcd 0000:00:0b.1: OHCI Host Controller
[    0.985933] ohci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 4
[    0.985951] ohci_hcd 0000:00:0b.1: irq 16, io mem 0xfebfe000
[    1.025936] ata1.00: ATA-7: Maxtor 6L200P0, BAJ41G20, max UDMA/133
[    1.025938] ata1.00: 398297088 sectors, multi 16: LBA48 
[    1.025967] ata1.01: ATAPI: HITACHI DVD-ROM GD-5000, 0212, max MWDMA2
[    1.070107] usb usb4: configuration #1 chosen from 1 choice
[    1.070130] hub 4-0:1.0: USB hub found
[    1.070136] hub 4-0:1.0: 2 ports detected
[    1.070179] uhci_hcd: USB Universal Host Controller Interface driver
[    1.070221]   alloc irq_desc for 20 on node -1
[    1.070223]   alloc kstat_irqs on node -1
[    1.070229] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.070236] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    1.070269] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 5
[    1.070299] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000d080
[    1.070366] usb usb5: configuration #1 chosen from 1 choice
[    1.070388] hub 5-0:1.0: USB hub found
[    1.070394] hub 5-0:1.0: 2 ports detected
[    1.070440]   alloc irq_desc for 22 on node -1
[    1.070442]   alloc kstat_irqs on node -1
[    1.070447] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.070452] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    1.070479] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 6
[    1.070507] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000d400
[    1.070571] usb usb6: configuration #1 chosen from 1 choice
[    1.070592] hub 6-0:1.0: USB hub found
[    1.070597] hub 6-0:1.0: 2 ports detected
[    1.070639] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.070645] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    1.070674] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 7
[    1.070693] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d480
[    1.070763] usb usb7: configuration #1 chosen from 1 choice
[    1.070784] hub 7-0:1.0: USB hub found
[    1.070790] hub 7-0:1.0: 2 ports detected
[    1.070831]   alloc irq_desc for 23 on node -1
[    1.070833]   alloc kstat_irqs on node -1
[    1.070837] uhci_hcd 0000:00:10.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.070843] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    1.070868] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 8
[    1.070898] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000dc00
[    1.070960] usb usb8: configuration #1 chosen from 1 choice
[    1.070982] hub 8-0:1.0: USB hub found
[    1.070987] hub 8-0:1.0: 2 ports detected
[    1.071078] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.071441] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.071446] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.071500] mice: PS/2 mouse device common for all mice
[    1.071617] rtc_cmos 00:02: RTC can wake from S4
[    1.071650] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.071683] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.071782] device-mapper: uevent: version 1.0.3
[    1.071846] ata1.00: configured for UDMA/133
[    1.072030] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.072086] device-mapper: multipath: version 1.1.0 loaded
[    1.072088] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.072201] EISA: Probing bus 0 at eisa.0
[    1.072240] EISA: Detected 0 cards.
[    1.072315] cpuidle: using governor ladder
[    1.072317] cpuidle: using governor menu
[    1.072764] TCP cubic registered
[    1.072895] NET: Registered protocol family 10
[    1.073310] lo: Disabled Privacy Extensions
[    1.073597] NET: Registered protocol family 17
[    1.073614] Bluetooth: L2CAP ver 2.13
[    1.073616] Bluetooth: L2CAP socket layer initialized
[    1.073618] Bluetooth: SCO (Voice Link) ver 0.6
[    1.073620] Bluetooth: SCO socket layer initialized
[    1.073653] Bluetooth: RFCOMM TTY layer initialized
[    1.073656] Bluetooth: RFCOMM socket layer initialized
[    1.073659] Bluetooth: RFCOMM ver 1.11
[    1.073704] Using IPI No-Shortcut mode
[    1.073765] PM: Resume from disk failed.
[    1.073785] registered taskstats version 1
[    1.073912]   Magic number: 10:565:805
[    1.074019] rtc_cmos 00:02: setting system clock to 2010-09-13 22:45:10 UTC (1284417910)
[    1.074022] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.074023] EDD information not available.
[    1.089485] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.100274] ata1.01: configured for MWDMA2
[    1.107305] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L200P0   BAJ4 PQ: 0 ANSI: 5
[    1.107418] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.108651] sd 0:0:0:0: [sda] 398297088 512-byte logical blocks: (203 GB/189 GiB)
[    1.110196] scsi 0:0:1:0: CD-ROM            HITACHI  DVD-ROM GD-5000  0212 PQ: 0 ANSI: 5
[    1.110211] sd 0:0:0:0: [sda] Write Protect is off
[    1.110213] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.110233] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.118575] sr0: scsi3-mmc drive: 14x/40x cd/rw xa/form2 cdda tray
[    1.118578] Uniform CD-ROM driver Revision: 3.20
[    1.118601]  sda:
[    1.118660] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.118705] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.139868]  sda1 sda2 sda3 < sda5 >
[    1.158337] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.326504] ata2.00: ATA-7: ST3160812A, 3.AAJ, max UDMA/100
[    1.326506] ata2.00: 312581808 sectors, multi 16: LBA48 
[    1.393027] ata2.00: configured for UDMA/100
[    1.393107] scsi 1:0:0:0: Direct-Access     ATA      ST3160812A       3.AA PQ: 0 ANSI: 5
[    1.393211] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    1.393240] sd 1:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.393277] sd 1:0:0:0: [sdb] Write Protect is off
[    1.393279] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.393299] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.393403]  sdb: sdb1
[    1.441052] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.441070] Freeing unused kernel memory: 540k freed
[    1.441375] Write protecting the kernel text: 4568k
[    1.441412] Write protecting the kernel read-only data: 1836k
[    1.539170] sata_via 0000:00:0f.0: version 2.4
[    1.539205] sata_via 0000:00:0f.0: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.539256] sata_via 0000:00:0f.0: routed to hard irq line 5
[    1.544803] Linux agpgart interface v0.103
[    1.547344] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.553758] scsi2 : sata_via
[    1.553876] scsi3 : sata_via
[    1.555236] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 21
[    1.555240] ata4: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 21
[    1.563741] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    1.565372] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.566022] eth0: VIA Rhine II at 0xfebffc00, 00:13:8f:aa:9d:ab, IRQ 23.
[    1.566728] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link cde1.
[    1.568482] agpgart: Detected VIA PT880 Ultra chipset
[    1.617649] FDC 0 is a post-1991 82077
[    1.623563] agpgart-via 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.760512] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    1.784851] usb 3-2: configuration #1 chosen from 1 choice
[    1.793926] usbcore: registered new interface driver hiddev
[    1.806008] input: SILITEK USB Keyboard and Mouse as /devices/pci0000:00/0000:00:0b.0/usb3/3-2/3-2:1.0/input/input4
[    1.806077] generic-usb 0003:047B:0002.0001: input,hidraw0: USB HID v1.00 Keyboard [SILITEK USB Keyboard and Mouse] on usb-0000:00:0b.0-2/input0
[    1.826821] input: SILITEK USB Keyboard and Mouse as /devices/pci0000:00/0000:00:0b.0/usb3/3-2/3-2:1.1/input/input5
[    1.826904] generic-usb 0003:047B:0002.0002: input,hidraw1: USB HID v1.00 Mouse [SILITEK USB Keyboard and Mouse] on usb-0000:00:0b.0-2/input1
[    1.826922] usbcore: registered new interface driver usbhid
[    1.826925] usbhid: v2.6:USB HID core driver
[    1.972011] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    2.096023] usb 4-2: new full speed USB device using ohci_hcd and address 2
[    2.316626] usb 4-2: config 1 interface 0 altsetting 0 endpoint 0x1 has an invalid bInterval 0, changing to 32
[    2.316630] usb 4-2: config 1 interface 0 altsetting 0 endpoint 0x82 has an invalid bInterval 0, changing to 32
[    2.328726] usb 4-2: configuration #1 chosen from 1 choice
[    2.695465] EXT4-fs (sda1): barriers enabled
[    2.706029] kjournald2 starting: pid 371, dev sda1:8, commit interval 5 seconds
[    2.706050] EXT4-fs (sda1): delayed allocation enabled
[    2.706054] EXT4-fs: file extents enabled
[    2.706112] EXT4-fs: mballoc enabled
[    2.706127] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.798725] Adding 1959920k swap on /dev/sda2.  Priority:-1 extents:1 across:1959920k 
[    3.920652] udev: starting version 147
[    4.512194] EXT4-fs (sda1): internal journal on sda1:8
[    4.795634] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.796725] cfg80211: Calling CRDA to update world regulatory domain
[    4.813763] parport_pc 00:06: reported by Plug and Play ACPI
[    4.813881] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    4.824195] ppdev: user-space parallel port driver
[    4.855603] psmouse serio1: ID: 10 00 64
[    4.943742] cfg80211: World regulatory domain updated:
[    4.943746]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.943748]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.943751]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.943753]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.943755]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.943757]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.039834] lirc_dev: IR Remote Control driver registered, major 61 
[    5.042310] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[    5.042314] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[    5.108562] lp0: using parport0 (interrupt-driven).
[    5.216032] usb 4-2: reset full speed USB device using ohci_hcd and address 2
[    5.264743] nvidia: module license 'NVIDIA' taints kernel.
[    5.264748] Disabling lock debugging due to kernel taint
[    5.422644] lirc_dev: lirc_register_driver: sample_rate: 0
[    5.428633] lirc_mceusb[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb4:2
[    5.428667] usbcore: registered new interface driver lirc_mceusb
[    5.440206] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input6
[    5.517070] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.517225] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.14  Sun Nov  8 18:08:53 PST 2009
[    5.607632] EXT4-fs (sdb1): barriers enabled
[    5.629078] kjournald2 starting: pid 685, dev sdb1:8, commit interval 5 seconds
[    5.629237] EXT4-fs (sdb1): internal journal on sdb1:8
[    5.629240] EXT4-fs (sdb1): delayed allocation enabled
[    5.629243] EXT4-fs: file extents enabled
[    5.630672] EXT4-fs: mballoc enabled
[    5.630687] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    5.765980] rt61pci 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.874631] phy0: Selected rate control algorithm 'minstrel'
[    5.875282] Registered led device: rt61pci-phy0::radio
[    5.875297] Registered led device: rt61pci-phy0::assoc
[    5.881951] udev: renamed network interface wlan0 to wlan1
[    6.057580] HDA Intel 0000:80:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.057622] HDA Intel 0000:80:01.0: setting latency timer to 64
[    6.057627] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
[    6.162300] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[    6.162503] input: HDA Digital PCBeep as /devices/pci0000:80/0000:80:01.0/input/input7
[   13.077974] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   13.077999] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   13.078125] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   15.019058] rt61pci 0000:00:0c.0: firmware: requesting rt2561s.bin
[   15.208625] input: rt61pci as /devices/pci0000:00/0000:00:0c.0/input/input8
[   15.241999] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   15.781337] CPU0 attaching NULL sched-domain.
[   15.781343] CPU1 attaching NULL sched-domain.
[   15.796061] CPU0 attaching sched-domain:
[   15.796064]  domain 0: span 0-1 level MC
[   15.796067]   groups: 0 1
[   15.796071]   domain 1: span 0-1 level CPU
[   15.796073]    groups: 0-1 (__cpu_power = 2048)
[   15.796077] CPU1 attaching sched-domain:
[   15.796079]  domain 0: span 0-1 level MC
[   15.796081]   groups: 1 0
[   15.796084]   domain 1: span 0-1 level CPU
[   15.796086]    groups: 0-1 (__cpu_power = 2048)
[   20.775904] eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   22.912922] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   23.068694] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   23.093634] EXT4-fs (sda5): barriers enabled
[   23.111790] kjournald2 starting: pid 1586, dev sda5:8, commit interval 5 seconds
[   23.111988] EXT4-fs (sda5): internal journal on sda5:8
[   23.111991] EXT4-fs (sda5): delayed allocation enabled
[   23.111994] EXT4-fs: file extents enabled
[   23.112385] EXT4-fs: mballoc enabled
[   23.112403] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   23.454052] eth0: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   33.756006] eth0: no IPv6 routers present
```


**lshw -C network**
```
*-network:0
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wmaster0
       version: 00
       serial: 00:1a:ef:11:d3:6f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:febf0000-febf7fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:13:8f:aa:9d:ab
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.201 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
```


**iwscan wlan1**
```
wlan1     Scan completed :
          Cell 01 - Address: 00:1D:73:D4:6F:4C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"dd-wrt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002459d6398f
                    Extra: Last beacon: 1048ms ago
                    IE: Unknown: 000664642D777274
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500002A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706444520010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000

```



**lsb_release -d**
```
Description:	Ubuntu 9.10
```


**uname -mr**
```
2.6.31-16-generic i686
```



**/init.d/networking restart**
 ```
* Reconfiguring network interfaces...
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:13:8f:aa:9d:ab
Sending on   LPF/eth0/00:13:8f:aa:9d:ab
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.201 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.201 from 192.168.1.1
bound to 192.168.1.201 -- renewal in 862910748 seconds.
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:1a:ef:11:d3:6f
Sending on   LPF/wlan1/00:1a:ef:11:d3:6f
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
   ...done.

```

---

### Post by DirtDart on 2010-09-16
Fixed this problem by replacing the default drivers with the drivers from RaLink ([http://www.ralinktech.com/](http://www.ralinktech.com/))

Steps used:

[LIST=1]
[*]Remove the rt61pci, rt2x00pci, and rt2x00lib modules that were installed by default ```
sudo rmmod rt61pci rt2x00pci rt2x00lib
```
[*]Download the **RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661)** drivers from the [*RaLink website*](http://www.ralinktech.com/).

[*]Compile the driver, ***_following the directions listed in the README file included with the driver_***.  The only modification to what the README states was I had to use the option listed in [*this thread*](http://ubuntuforums.org/showthread.php?t=1574114&highlight=KBUILD_NOPEDANTIC=1).
```
sudo KBUILD_NOPEDANTIC=1 make all install
```

[*]Once that was done, I modified the */etc/Wireless/RT61STA/rt61sta.dat* file to suit my local network.

[*]A quick */etc/init.d/networking restart* and I was in business!

[*]After confirming it worked with no encryption, I re-enabled the encryption (WPA2-AES) and MAC filtering.  Restarted network services and I was still going!
[/LIST]

I did not compile the WPA_Supplicant, as I already had it installed.

---

