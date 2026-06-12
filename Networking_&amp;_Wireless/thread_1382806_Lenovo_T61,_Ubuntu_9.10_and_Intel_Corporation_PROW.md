---
title: "Lenovo T61, Ubuntu 9.10 and Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron]"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by MakOwner on 2010-01-16
Sorry for what is really a rant disguised as a question, but does anyone have this combination working?

My NetGear router shows the connection as allowed from the MAC address in the router logs, And I can see the network I want to join in the list of visible networks from the laptop, but dmesg shows Ubuntu disconnecting with 

WPA-PSK [TKIP] only:
wlan0: disassociating by local choice (reason=15)

WPA-PSK [TKIP] + WPA2-PSK [AES]
wlan0: disassociating by local choice (reason=3)


I'm sure there is a simple explantion that has been sufficiently buried somewhere but after several hours of googling and searching the forums here I can't find it.

Anyone want to help out an old man RTFM?


I'm getting really disappointed here lately - things are getting worse, not better.  

In my case in particular I have this laptop with supposedly open and supported drivers and they don't work, however, the exact same distributuon on a Dell D830 with a broadcom NIC does.  

And even worse, under 8.10 and 9.04 this worked out the box - just logged in, gave the PSK and away we went.



I can't see the attachment I just uploaded so to include the information requested in the "how to get help" post, I'll put it all here inline...


```

Machine Brand and Model (PC/Laptop): Lenovo R61
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
eth0      Link encap:Ethernet  HWaddr 00:1c:25:b6:a0:a0  
          inet addr:192.168.0.9  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21c:25ff:feb6:a0a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27625341 (27.6 MB)  TX bytes:1191763 (1.1 MB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:7c:a9:9b  
          inet6 addr: fe80::21f:3bff:fe7c:a99b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6885 (6.8 KB)  TX bytes:7679 (7.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-7C-A9-9B-37-63-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     IEEE 802.11abgn  Mode:Managed  Frequency:2.437 GHz  
          Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11abgn  Mode:Managed  Frequency:2.437 GHz  
          Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Module                  Size  Used by
nvidia               9586440  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
snd_hda_codec_analog    59292  1 
arc4                    1660  2 
ecb                     2524  2 
pcmcia                 36808  0 
iptable_filter          3100  0 
snd_hda_intel          26920  3 
snd_hda_codec          75708  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
btusb                  11856  2 
iwlagn                109052  0 
iwlcore               112540  1 iwlagn
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
mac80211              181076  2 iwlagn,iwlcore
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
psmouse                56500  0 
serio_raw               5280  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
ricoh_mmc               3676  0 
sdhci_pci               7100  0 
sdhci                  17472  1 sdhci_pci
yenta_socket           24200  1 
rsrc_nonstatic         11644  1 yenta_socket
snd_rawmidi            22208  1 snd_seq_midi
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               93052  3 iwlagn,iwlcore,mac80211
snd                    59204  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
thinkpad_acpi          67108  0 
led_class               4096  3 iwlcore,sdhci,thinkpad_acpi
nvram                   7528  1 thinkpad_acpi
lp                      8964  0 
parport                35340  2 ppdev,lp
video                  19380  0 
output                  2780  1 video
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
e1000e                122124  0 
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfeb0000 - 00000000bfecc000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfecc000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfeb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 13C000000 mask FFC000000 uncachable
[    0.000000]   2 base 000000000 mask F00000000 write-back
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009d800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfeb0000 (usable)
[    0.000000]  modified: 00000000bfeb0000 - 00000000bfecc000 (ACPI data)
[    0.000000]  modified: 00000000bfecc000 - 00000000bff00000 (ACPI NVS)
[    0.000000]  modified: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a6000 - 37fefa9a
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff6a9a
[    0.000000] Move RAMDISK from 00000000378a6000 - 0000000037fefa99 to 008ad000 - 00ff6a99
[    0.000000] ACPI: RSDP 000f68d0 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT bfebb77f 00094 (v01 LENOVO TP-7L    00002190  LTP 00000000)
[    0.000000] ACPI: FACP bfebb900 000F4 (v03 LENOVO TP-7L    00002190 LNVO 00000001)
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 20090521 tbfadt-527
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 000000000000102C/0 20090521 tbfadt-558
[    0.000000] ACPI: DSDT bfebbd1d 0FED1 (v01 LENOVO TP-7L    00002190 MSFT 03000000)
[    0.000000] ACPI: FACS bfee4000 00040
[    0.000000] ACPI: SSDT bfebbab4 00269 (v01 LENOVO TP-7L    00002190 MSFT 03000000)
[    0.000000] ACPI: ECDT bfecbbee 00052 (v01 LENOVO TP-7L    00002190 LNVO 00000001)
[    0.000000] ACPI: TCPA bfecbc40 00032 (v02 LENOVO TP-7L    00002190 LNVO 00000001)
[    0.000000] ACPI: APIC bfecbc72 00068 (v01 LENOVO TP-7L    00002190 LNVO 00000001)
[    0.000000] ACPI: MCFG bfecbcda 0003C (v01 LENOVO TP-7L    00002190 LNVO 00000001)
[    0.000000] ACPI: HPET bfecbd16 00038 (v01 LENOVO TP-7L    00002190 LNVO 00000001)
[    0.000000] ACPI: SLIC bfecbdf0 00176 (v01 LENOVO TP-7L    00002190  LTP 00000000)
[    0.000000] ACPI: BOOT bfecbf66 00028 (v01 LENOVO TP-7L    00002190  LTP 00000001)
[    0.000000] ACPI: ASF! bfecbf8e 00072 (v16 LENOVO TP-7L    00002190 PTL  00000001)
[    0.000000] ACPI: SSDT bfee26d9 0025F (v01 LENOVO TP-7L    00002190 INTL 20050513)
[    0.000000] ACPI: SSDT bfee2938 000A6 (v01 LENOVO TP-7L    00002190 INTL 20050513)
[    0.000000] ACPI: SSDT bfee29de 004F7 (v01 LENOVO TP-7L    00002190 INTL 20050513)
[    0.000000] ACPI: SSDT bfee2ed5 001D8 (v01 LENOVO TP-7L    00002190 INTL 20050513)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad T61
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2182MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac138]              BRK ==> [00008a9000 - 00008ac138]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000ff6a9a]      NEW RAMDISK ==> [00008ad000 - 0000ff6a9a]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f6900] f6900
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfeb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bfeb0
[    0.000000] On node 0 totalpages: 785993
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4366 pages used for memmap
[    0.000000]   HighMem zone: 554404 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2810000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779851
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=ebe72ecd-7ee7-48a6-8b97-2ae02e0ae774 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15721920 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfeb0)
[    0.000000] Memory: 3086808k/3144384k available (4566k kernel code, 56252k reserved, 2142k data, 540k init, 2235080k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575bb4 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575bb4   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2094.861 MHz processor.
[    0.002682] Console: colour VGA+ 80x25
[    0.002690] console [tty0] enabled
[    0.002923] hpet clockevent registered
[    0.002932] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002945] Calibrating delay loop (skipped), value calculated using timer frequency.. 4189.72 BogoMIPS (lpj=8379444)
[    0.002980] Security Framework initialized
[    0.003019] AppArmor: AppArmor initialized
[    0.003034] Mount-cache hash table entries: 512
[    0.003286] Initializing cgroup subsys ns
[    0.003295] Initializing cgroup subsys cpuacct
[    0.003305] Initializing cgroup subsys memory
[    0.003318] Initializing cgroup subsys freezer
[    0.003323] Initializing cgroup subsys net_cls
[    0.003353] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003359] CPU: L2 cache: 3072K
[    0.003364] CPU: Physical Processor ID: 0
[    0.003368] CPU: Processor Core ID: 0
[    0.003376] mce: CPU supports 6 MCE banks
[    0.003393] CPU0: Thermal monitoring enabled (TM2)
[    0.003400] using mwait in idle threads.
[    0.003413] Performance Counters: Core2 events, Intel PMU driver.
[    0.003431] ... version:                 2
[    0.003435] ... bit width:               40
[    0.003439] ... generic counters:        2
[    0.003443] ... value mask:              000000ffffffffff
[    0.003447] ... max period:              000000007fffffff
[    0.003451] ... fixed-purpose counters:  3
[    0.003455] ... counter mask:            0000000700000003
[    0.003464] Checking 'hlt' instruction... OK.
[    0.020009] ACPI: Core revision 20090521
[    0.068577] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.108632] CPU0: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz stepping 06
[    0.112001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4189.53 BogoMIPS (lpj=8379062)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.199286] CPU1: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz stepping 06
[    0.199317] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.200001] Measured 1082466 cycles TSC warp between CPUs, turning off TSC clock.
[    0.200001] Marking TSC unstable due to check_tsc_sync_source failed
[    0.200037] Brought up 2 CPUs
[    0.200043] Total of 2 processors activated (8379.25 BogoMIPS).
[    0.200121] CPU0 attaching sched-domain:
[    0.200127]  domain 0: span 0-1 level MC
[    0.200133]   groups: 0 1
[    0.200145] CPU1 attaching sched-domain:
[    0.200150]  domain 0: span 0-1 level MC
[    0.200156]   groups: 1 0
[    0.204056] Booting paravirtualized kernel on bare hardware
[    0.204493] regulator: core version 0.5
[    0.204493] Time: 21:05:45  Date: 01/03/10
[    0.204493] NET: Registered protocol family 16
[    0.204493] EISA bus registered
[    0.204493] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.204493] ACPI: bus type pci registered
[    0.204635] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.204642] PCI: MCFG area at f0000000 reserved in E820
[    0.204646] PCI: Using MMCONFIG for extended config space
[    0.204651] PCI: Using configuration type 1 for base access
[    0.207029] bio: create slab <bio-0> at 0
[    0.211534] ACPI: EC: EC description table is found, configuring boot EC
[    0.226830] ACPI: BIOS _OSI(Linux) query honored via DMI
[    0.228042] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.249148] ACPI: Interpreter enabled
[    0.249160] ACPI: (supports S0 S3 S4 S5)
[    0.249213] ACPI: Using IOAPIC for interrupt routing
[    0.277828] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[    0.277835] ACPI: EC: driver started in interrupt mode
[    0.280168] ACPI: Power Resource [PUBS] (on)
[    0.288028] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.288936] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.289185] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.289193] pci 0000:00:01.0: PME# disabled
[    0.289451] pci 0000:00:19.0: reg 10 32bit mmio: [0xfe200000-0xfe21ffff]
[    0.289476] pci 0000:00:19.0: reg 14 32bit mmio: [0xfe225000-0xfe225fff]
[    0.289501] pci 0000:00:19.0: reg 18 io port: [0x1840-0x185f]
[    0.289664] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.289678] pci 0000:00:19.0: PME# disabled
[    0.289844] pci 0000:00:1a.0: reg 20 io port: [0x1860-0x187f]
[    0.290048] pci 0000:00:1a.1: reg 20 io port: [0x1880-0x189f]
[    0.290243] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe226c00-0xfe226fff]
[    0.290425] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.290439] pci 0000:00:1a.7: PME# disabled
[    0.290600] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe220000-0xfe223fff]
[    0.290796] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.290810] pci 0000:00:1b.0: PME# disabled
[    0.291085] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.291099] pci 0000:00:1c.0: PME# disabled
[    0.291382] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.291396] pci 0000:00:1c.1: PME# disabled
[    0.291680] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.291694] pci 0000:00:1c.2: PME# disabled
[    0.291977] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.292005] pci 0000:00:1c.3: PME# disabled
[    0.292290] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.292304] pci 0000:00:1c.4: PME# disabled
[    0.292510] pci 0000:00:1d.0: reg 20 io port: [0x18a0-0x18bf]
[    0.292719] pci 0000:00:1d.1: reg 20 io port: [0x18c0-0x18df]
[    0.292923] pci 0000:00:1d.2: reg 20 io port: [0x18e0-0x18ff]
[    0.293141] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe227000-0xfe2273ff]
[    0.293341] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.293356] pci 0000:00:1d.7: PME# disabled
[    0.293844] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.293855] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.293865] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 1600 (mask 007f)
[    0.293877] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 15e0 (mask 000f)
[    0.293887] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 1680 (mask 001f)
[    0.294039] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.294063] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.294086] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.294111] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.294135] pci 0000:00:1f.1: reg 20 io port: [0x1830-0x183f]
[    0.294367] pci 0000:00:1f.2: reg 10 io port: [0x1c48-0x1c4f]
[    0.294391] pci 0000:00:1f.2: reg 14 io port: [0x1c1c-0x1c1f]
[    0.294415] pci 0000:00:1f.2: reg 18 io port: [0x1c40-0x1c47]
[    0.294439] pci 0000:00:1f.2: reg 1c io port: [0x1c18-0x1c1b]
[    0.294463] pci 0000:00:1f.2: reg 20 io port: [0x1c20-0x1c3f]
[    0.294487] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe226000-0xfe2267ff]
[    0.294623] pci 0000:00:1f.2: PME# supported from D3hot
[    0.294637] pci 0000:00:1f.2: PME# disabled
[    0.294738] pci 0000:00:1f.3: reg 10 32bit mmio: [0xfe227400-0xfe2274ff]
[    0.294818] pci 0000:00:1f.3: reg 20 io port: [0x1c60-0x1c7f]
[    0.294987] pci 0000:01:00.0: reg 10 32bit mmio: [0xd6000000-0xd6ffffff]
[    0.295013] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.295039] pci 0000:01:00.0: reg 1c 64bit mmio: [0xd4000000-0xd5ffffff]
[    0.295055] pci 0000:01:00.0: reg 24 io port: [0x2000-0x207f]
[    0.295072] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.295310] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.295319] pci 0000:00:01.0: bridge 32bit mmio: [0xd4000000-0xd6ffffff]
[    0.295331] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.295512] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.295526] pci 0000:00:1c.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.295550] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf8000000-0xf80fffff]
[    0.295863] pci 0000:03:00.0: reg 10 64bit mmio: [0xdf2fe000-0xdf2fffff]
[    0.296286] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.296326] pci 0000:03:00.0: PME# disabled
[    0.296575] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.296589] pci 0000:00:1c.1: bridge 32bit mmio: [0xdc100000-0xdf2fffff]
[    0.296613] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xdfd00000-0xdfdfffff]
[    0.296797] pci 0000:00:1c.2: bridge io port: [0x5000-0x5fff]
[    0.296811] pci 0000:00:1c.2: bridge 32bit mmio: [0xd8000000-0xd9ffffff]
[    0.296835] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xdfa00000-0xdfafffff]
[    0.297018] pci 0000:00:1c.3: bridge io port: [0x6000-0x6fff]
[    0.297033] pci 0000:00:1c.3: bridge 32bit mmio: [0xd0000000-0xd1ffffff]
[    0.297057] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xdf700000-0xdf7fffff]
[    0.297239] pci 0000:00:1c.4: bridge io port: [0x7000-0x7fff]
[    0.297254] pci 0000:00:1c.4: bridge 32bit mmio: [0xcc000000-0xcdffffff]
[    0.297278] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xdf400000-0xdf4fffff]
[    0.297415] pci 0000:15:00.0: reg 10 32bit mmio: [0xf8100000-0xf8100fff]
[    0.297493] pci 0000:15:00.0: supports D1 D2
[    0.297498] pci 0000:15:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.297512] pci 0000:15:00.0: PME# disabled
[    0.297649] pci 0000:15:00.1: reg 10 32bit mmio: [0xf8101000-0xf81017ff]
[    0.297848] pci 0000:15:00.1: supports D1 D2
[    0.297853] pci 0000:15:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.297868] pci 0000:15:00.1: PME# disabled
[    0.298003] pci 0000:15:00.2: reg 10 32bit mmio: [0xf8101800-0xf81018ff]
[    0.298204] pci 0000:15:00.2: supports D1 D2
[    0.298209] pci 0000:15:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.298223] pci 0000:15:00.2: PME# disabled
[    0.298360] pci 0000:15:00.3: reg 10 32bit mmio: [0xf8101c00-0xf8101cff]
[    0.298560] pci 0000:15:00.3: supports D1 D2
[    0.298565] pci 0000:15:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.298580] pci 0000:15:00.3: PME# disabled
[    0.298716] pci 0000:15:00.4: reg 10 32bit mmio: [0xf8102000-0xf81020ff]
[    0.298916] pci 0000:15:00.4: supports D1 D2
[    0.298921] pci 0000:15:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.298936] pci 0000:15:00.4: PME# disabled
[    0.299072] pci 0000:15:00.5: reg 10 32bit mmio: [0xf8102400-0xf81024ff]
[    0.299272] pci 0000:15:00.5: supports D1 D2
[    0.299277] pci 0000:15:00.5: PME# supported from D0 D1 D2 D3hot D3cold
[    0.299292] pci 0000:15:00.5: PME# disabled
[    0.299485] pci 0000:00:1e.0: transparent bridge
[    0.299499] pci 0000:00:1e.0: bridge io port: [0x8000-0xbfff]
[    0.299514] pci 0000:00:1e.0: bridge 32bit mmio: [0xf8100000-0xfbffffff]
[    0.299538] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xf4000000-0xf7ffffff]
[    0.299725] pci_bus 0000:00: on NUMA node 0
[    0.299737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.300126] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.300306] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.300472] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.300637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.300802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.300984] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.301165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.315396] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[    0.315852] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.316321] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.316774] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.317231] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.317681] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.318130] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.318579] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.319050] SCSI subsystem initialized
[    0.319094] libata version 3.00 loaded.
[    0.319094] usbcore: registered new interface driver usbfs
[    0.319094] usbcore: registered new interface driver hub
[    0.319094] usbcore: registered new device driver usb
[    0.319094] ACPI: WMI: Mapper loaded
[    0.319094] PCI: Using ACPI for IRQ routing
[    0.332022] Bluetooth: Core ver 2.15
[    0.332053] NET: Registered protocol family 31
[    0.332053] Bluetooth: HCI device and connection manager initialized
[    0.332053] Bluetooth: HCI socket layer initialized
[    0.332053] NetLabel: Initializing
[    0.332053] NetLabel:  domain hash size = 128
[    0.332053] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.332077] NetLabel:  unlabeled traffic allowed by default
[    0.332145] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.332157] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.340029] Switched to high resolution mode on CPU 0
[    0.343394] Switched to high resolution mode on CPU 1
[    0.352041] pnp: PnP ACPI init
[    0.352061] ACPI: bus type pnp registered
[    0.362478] pnp: PnP ACPI: found 11 devices
[    0.362484] ACPI: ACPI bus type pnp unregistered
[    0.362491] PnPBIOS: Disabled by ACPI PNP
[    0.362514] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.362522] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.362529] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.362536] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.362543] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.362550] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.362557] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.362564] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.362571] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.362578] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.362585] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.362592] system 00:00: iomem range 0x100000-0xbfffffff could not be reserved
[    0.362600] system 00:00: iomem range 0xfec00000-0xfed3ffff could not be reserved
[    0.362608] system 00:00: iomem range 0xfed4c000-0xffffffff could not be reserved
[    0.362626] system 00:02: ioport range 0x164e-0x164f has been reserved
[    0.362633] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.362640] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.362647] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.362654] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.362661] system 00:02: ioport range 0x1600-0x165f could not be reserved
[    0.362669] system 00:02: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.362677] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.362684] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.362692] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.362699] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.362707] system 00:02: iomem range 0xfed45000-0xfed4bfff has been reserved
[    0.397612] AppArmor: AppArmor Filesystem Enabled
[    0.397859] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xf0000000-0xefffffff]
[    0.397866] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.397874] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.397883] pci 0000:00:01.0:   MEM window: 0xd4000000-0xd6ffffff
[    0.397892] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.397904] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.397914] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.397933] pci 0000:00:1c.0:   MEM window: 0xfc000000-0xfdffffff
[    0.397947] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8000000-0x000000f80fffff
[    0.397971] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.397980] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.397999] pci 0000:00:1c.1:   MEM window: 0xdc100000-0xdf2fffff
[    0.398013] pci 0000:00:1c.1:   PREFETCH window: 0x000000dfd00000-0x000000dfdfffff
[    0.398037] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.398046] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.398065] pci 0000:00:1c.2:   MEM window: 0xd8000000-0xd9ffffff
[    0.398079] pci 0000:00:1c.2:   PREFETCH window: 0x000000dfa00000-0x000000dfafffff
[    0.398103] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.398113] pci 0000:00:1c.3:   IO window: 0x6000-0x6fff
[    0.398131] pci 0000:00:1c.3:   MEM window: 0xd0000000-0xd1ffffff
[    0.398145] pci 0000:00:1c.3:   PREFETCH window: 0x000000df700000-0x000000df7fffff
[    0.398169] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.398178] pci 0000:00:1c.4:   IO window: 0x7000-0x7fff
[    0.398197] pci 0000:00:1c.4:   MEM window: 0xcc000000-0xcdffffff
[    0.398211] pci 0000:00:1c.4:   PREFETCH window: 0x000000df400000-0x000000df4fffff
[    0.398241] pci 0000:15:00.0: CardBus bridge, secondary bus 0000:16
[    0.398247] pci 0000:15:00.0:   IO window: 0x008000-0x0080ff
[    0.398263] pci 0000:15:00.0:   IO window: 0x008400-0x0084ff
[    0.398278] pci 0000:15:00.0:   PREFETCH window: 0xf4000000-0xf7ffffff
[    0.398294] pci 0000:15:00.0:   MEM window: 0xc0000000-0xc3ffffff
[    0.398310] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:15
[    0.398319] pci 0000:00:1e.0:   IO window: 0x8000-0xbfff
[    0.398338] pci 0000:00:1e.0:   MEM window: 0xf8100000-0xfbffffff
[    0.398352] pci 0000:00:1e.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    0.398388]   alloc irq_desc for 16 on node -1
[    0.398392]   alloc kstat_irqs on node -1
[    0.398403] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.398412] pci 0000:00:01.0: setting latency timer to 64
[    0.398434]   alloc irq_desc for 20 on node -1
[    0.398438]   alloc kstat_irqs on node -1
[    0.398447] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.398461] pci 0000:00:1c.0: setting latency timer to 64
[    0.398485]   alloc irq_desc for 21 on node -1
[    0.398489]   alloc kstat_irqs on node -1
[    0.398498] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.398512] pci 0000:00:1c.1: setting latency timer to 64
[    0.398536]   alloc irq_desc for 22 on node -1
[    0.398540]   alloc kstat_irqs on node -1
[    0.398548] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.398563] pci 0000:00:1c.2: setting latency timer to 64
[    0.398587]   alloc irq_desc for 23 on node -1
[    0.398591]   alloc kstat_irqs on node -1
[    0.398599] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.398613] pci 0000:00:1c.3: setting latency timer to 64
[    0.398638] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.398652] pci 0000:00:1c.4: setting latency timer to 64
[    0.398667] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    0.398686] pci 0000:00:1e.0: setting latency timer to 64
[    0.398713] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.398730] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.398736] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.398743] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.398749] pci_bus 0000:01: resource 1 mem: [0xd4000000-0xd6ffffff]
[    0.398755] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.398762] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.398768] pci_bus 0000:02: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.398774] pci_bus 0000:02: resource 2 pref mem [0xf8000000-0xf80fffff]
[    0.398780] pci_bus 0000:03: resource 0 io:  [0x4000-0x4fff]
[    0.398786] pci_bus 0000:03: resource 1 mem: [0xdc100000-0xdf2fffff]
[    0.398793] pci_bus 0000:03: resource 2 pref mem [0xdfd00000-0xdfdfffff]
[    0.398799] pci_bus 0000:04: resource 0 io:  [0x5000-0x5fff]
[    0.398805] pci_bus 0000:04: resource 1 mem: [0xd8000000-0xd9ffffff]
[    0.398811] pci_bus 0000:04: resource 2 pref mem [0xdfa00000-0xdfafffff]
[    0.398817] pci_bus 0000:05: resource 0 io:  [0x6000-0x6fff]
[    0.398823] pci_bus 0000:05: resource 1 mem: [0xd0000000-0xd1ffffff]
[    0.398829] pci_bus 0000:05: resource 2 pref mem [0xdf700000-0xdf7fffff]
[    0.398835] pci_bus 0000:0d: resource 0 io:  [0x7000-0x7fff]
[    0.398841] pci_bus 0000:0d: resource 1 mem: [0xcc000000-0xcdffffff]
[    0.398847] pci_bus 0000:0d: resource 2 pref mem [0xdf400000-0xdf4fffff]
[    0.398853] pci_bus 0000:15: resource 0 io:  [0x8000-0xbfff]
[    0.398859] pci_bus 0000:15: resource 1 mem: [0xf8100000-0xfbffffff]
[    0.398865] pci_bus 0000:15: resource 2 pref mem [0xf4000000-0xf7ffffff]
[    0.398871] pci_bus 0000:15: resource 3 io:  [0x00-0xffff]
[    0.398877] pci_bus 0000:15: resource 4 mem: [0x000000-0xffffffff]
[    0.398884] pci_bus 0000:16: resource 0 io:  [0x8000-0x80ff]
[    0.398889] pci_bus 0000:16: resource 1 io:  [0x8400-0x84ff]
[    0.398895] pci_bus 0000:16: resource 2 pref mem [0xf4000000-0xf7ffffff]
[    0.398901] pci_bus 0000:16: resource 3 mem: [0xc0000000-0xc3ffffff]
[    0.398982] NET: Registered protocol family 2
[    0.399186] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.399865] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.400695] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.401165] TCP: Hash tables configured (established 131072 bind 65536)
[    0.401171] TCP reno registered
[    0.401320] NET: Registered protocol family 1
[    0.401441] Trying to unpack rootfs image as initramfs...
[    0.868962] Freeing initrd memory: 7462k freed
[    0.875979] Simple Boot Flag at 0x35 set to 0x1
[    0.876385] cpufreq-nforce2: No nForce2 chipset.
[    0.876447] Scanning for low memory corruption every 60 seconds
[    0.876679] audit: initializing netlink socket (disabled)
[    0.876711] type=2000 audit(1262552745.873:1): initialized
[    0.898258] highmem bounce pool size: 64 pages
[    0.898271] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.901894] VFS: Disk quotas dquot_6.5.2
[    0.902036] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.903346] fuse init (API version 7.12)
[    0.903548] msgmni has been set to 1679
[    0.904094] alg: No test for stdrng (krng)
[    0.904121] io scheduler noop registered
[    0.904127] io scheduler anticipatory registered
[    0.904132] io scheduler deadline registered
[    0.904231] io scheduler cfq registered (default)
[    0.904574] pci 0000:01:00.0: Boot video device
[    0.904885]   alloc irq_desc for 24 on node -1
[    0.904890]   alloc kstat_irqs on node -1
[    0.904909] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.904924] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.905297]   alloc irq_desc for 25 on node -1
[    0.905301]   alloc kstat_irqs on node -1
[    0.905327] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.905360] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.905816]   alloc irq_desc for 26 on node -1
[    0.905821]   alloc kstat_irqs on node -1
[    0.905847] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.905879] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.906335]   alloc irq_desc for 27 on node -1
[    0.906340]   alloc kstat_irqs on node -1
[    0.906365] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.906398] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.906846]   alloc irq_desc for 28 on node -1
[    0.906851]   alloc kstat_irqs on node -1
[    0.906876] pcieport-driver 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.906908] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.907369]   alloc irq_desc for 29 on node -1
[    0.907373]   alloc kstat_irqs on node -1
[    0.907399] pcieport-driver 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.907431] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.907724] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.908802] pciehp: Using ACPI for slot detection.
[    0.909094] pciehp 0000:00:1c.3:pcie04: HPC vendor_id 8086 device_id 2845 ss_vid 0 ss_did 0
[    0.909214] pciehp 0000:00:1c.3:pcie04: service driver pciehp loaded
[    0.909259] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.910161] ACPI: AC Adapter [AC] (off-line)
[    0.910313] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.910321] ACPI: Power Button [PWRF]
[    0.910445] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.911047] ACPI: Lid Switch [LID]
[    0.911158] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.911171] ACPI: Sleep Button [SLPB]
[    0.912737] ACPI: SSDT bfee1b32 002C4 (v01  PmRef  Cpu0Ist 00000100 INTL 20050513)
[    0.914479] ACPI: SSDT bfee1e7b 0085E (v01  PmRef  Cpu0Cst 00000100 INTL 20050513)
[    0.921209] Monitor-Mwait will be used to enter C-1 state
[    0.921284] Monitor-Mwait will be used to enter C-2 state
[    0.921352] Monitor-Mwait will be used to enter C-3 state
[    0.921407] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.921463] processor LNXCPU:00: registered as cooling_device0
[    0.921472] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.922229] ACPI: SSDT bfee1a6a 000C8 (v01  PmRef  Cpu1Ist 00000100 INTL 20050513)
[    0.923412] ACPI: SSDT bfee1df6 00085 (v01  PmRef  Cpu1Cst 00000100 INTL 20050513)
[    0.927119] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.927166] processor LNXCPU:01: registered as cooling_device1
[    0.927176] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.941342] thermal LNXTHERM:01: registered as thermal_zone0
[    0.941362] ACPI: Thermal Zone [THM0] (32 C)
[    0.944367] thermal LNXTHERM:02: registered as thermal_zone1
[    0.944386] ACPI: Thermal Zone [THM1] (30 C)
[    0.944518] isapnp: Scanning for PnP cards...
[    0.996378] ACPI: Battery Slot [BAT0] (battery present)
[    1.303498] isapnp: No Plug & Play device found
[    1.306073] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.309173] brd: module loaded
[    1.310247] loop: module loaded
[    1.310403] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.310571] ahci 0000:00:1f.2: version 3.0
[    1.310603] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.310690]   alloc irq_desc for 30 on node -1
[    1.310694]   alloc kstat_irqs on node -1
[    1.310722] ahci 0000:00:1f.2: irq 30 for MSI/MSI-X
[    1.310849] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x5 impl SATA mode
[    1.310858] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    1.310873] ahci 0000:00:1f.2: setting latency timer to 64
[    1.311214] scsi0 : ahci
[    1.311401] scsi1 : ahci
[    1.311528] scsi2 : ahci
[    1.311691] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 30
[    1.311697] ata2: DUMMY
[    1.311705] ata3: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 30
[    1.311826] ata_piix 0000:00:1f.1: version 2.13
[    1.311845] ata_piix 0000:00:1f.1: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    1.311928] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.312071] scsi3 : ata_piix
[    1.312198] scsi4 : ata_piix
[    1.313774] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1830 irq 14
[    1.313781] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1838 irq 15
[    1.314170] ata5: port disabled. ignoring.
[    1.315950] Fixed MDIO Bus: probed
[    1.316030] PPP generic driver version 2.4.2
[    1.316216] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.317005] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    1.317025] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.317052] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.317062] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.317166] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.321114] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.321146] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfe226c00
[    1.336050] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.336205] usb usb1: configuration #1 chosen from 1 choice
[    1.336272] hub 1-0:1.0: USB hub found
[    1.336288] hub 1-0:1.0: 4 ports detected
[    1.337203] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    1.337222]   alloc irq_desc for 19 on node -1
[    1.337226]   alloc kstat_irqs on node -1
[    1.337237] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.337262] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.337272] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.337351] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.341313] ehci_hcd 0000:00:1d.7: debug port 1
[    1.341332] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.341362] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe227000
[    1.356051] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.356195] usb usb2: configuration #1 chosen from 1 choice
[    1.356265] hub 2-0:1.0: USB hub found
[    1.356279] hub 2-0:1.0: 6 ports detected
[    1.356426] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.356468] uhci_hcd: USB Universal Host Controller Interface driver
[    1.356514] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.356532] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.356541] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.356619] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.356695] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    1.356892] usb usb3: configuration #1 chosen from 1 choice
[    1.356954] hub 3-0:1.0: USB hub found
[    1.356969] hub 3-0:1.0: 2 ports detected
[    1.357847] uhci_hcd 0000:00:1a.1: power state changed by ACPI to D0
[    1.357862] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.357879] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.357888] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.357969] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.358042] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    1.358230] usb usb4: configuration #1 chosen from 1 choice
[    1.358293] hub 4-0:1.0: USB hub found
[    1.358308] hub 4-0:1.0: 2 ports detected
[    1.359221] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.359236] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.359253] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.359262] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.359336] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.359408] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    1.359590] usb usb5: configuration #1 chosen from 1 choice
[    1.359671] hub 5-0:1.0: USB hub found
[    1.359686] hub 5-0:1.0: 2 ports detected
[    1.359794]   alloc irq_desc for 17 on node -1
[    1.359799]   alloc kstat_irqs on node -1
[    1.359810] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.359827] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.359837] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.359916] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.359989] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    1.360215] usb usb6: configuration #1 chosen from 1 choice
[    1.360281] hub 6-0:1.0: USB hub found
[    1.360295] hub 6-0:1.0: 2 ports detected
[    1.361067] uhci_hcd 0000:00:1d.2: power state changed by ACPI to D0
[    1.361080]   alloc irq_desc for 18 on node -1
[    1.361084]   alloc kstat_irqs on node -1
[    1.361094] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.361111] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.361121] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.361193] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.361265] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    1.361448] usb usb7: configuration #1 chosen from 1 choice
[    1.361514] hub 7-0:1.0: USB hub found
[    1.361529] hub 7-0:1.0: 2 ports detected
[    1.361750] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.369555] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.369568] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.369704] mice: PS/2 mouse device common for all mice
[    1.369950] rtc_cmos 00:07: RTC can wake from S4
[    1.370020] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.370078] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.370308] device-mapper: uevent: version 1.0.3
[    1.370519] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.370728] device-mapper: multipath: version 1.1.0 loaded
[    1.370734] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.371008] EISA: Probing bus 0 at eisa.0
[    1.371021] Cannot allocate resource for EISA slot 1
[    1.371026] Cannot allocate resource for EISA slot 2
[    1.371031] Cannot allocate resource for EISA slot 3
[    1.371036] Cannot allocate resource for EISA slot 4
[    1.371041] Cannot allocate resource for EISA slot 5
[    1.371046] Cannot allocate resource for EISA slot 6
[    1.371051] Cannot allocate resource for EISA slot 7
[    1.371056] Cannot allocate resource for EISA slot 8
[    1.371061] EISA: Detected 0 cards.
[    1.371460] cpuidle: using governor ladder
[    1.371742] cpuidle: using governor menu
[    1.372910] TCP cubic registered
[    1.373297] NET: Registered protocol family 10
[    1.374364] lo: Disabled Privacy Extensions
[    1.374764] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.375161] NET: Registered protocol family 17
[    1.375203] Bluetooth: L2CAP ver 2.13
[    1.375207] Bluetooth: L2CAP socket layer initialized
[    1.375214] Bluetooth: SCO (Voice Link) ver 0.6
[    1.375217] Bluetooth: SCO socket layer initialized
[    1.375321] Bluetooth: RFCOMM TTY layer initialized
[    1.375328] Bluetooth: RFCOMM socket layer initialized
[    1.375332] Bluetooth: RFCOMM ver 1.11
[    1.376783] Using IPI No-Shortcut mode
[    1.376835] PM: Resume from disk failed.
[    1.376845] registered taskstats version 1
[    1.376963]   Magic number: 10:932:94
[    1.377064] rtc_cmos 00:07: setting system clock to 2010-01-03 21:05:47 UTC (1262552747)
[    1.377067] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.377069] EDD information not available.
[    1.476721] ata4.00: ATAPI: MATSHITADVD-RAM UJ-862, RB01, max UDMA/33
[    1.492395] ata4.00: configured for UDMA/33
[    1.500076] Clocksource tsc unstable (delta = -113699605 ns)
[    1.628108] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.628134] ata3: SATA link down (SStatus 0 SControl 300)
[    1.629311] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    1.629316] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.629321] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.664033] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    1.664038] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.666655] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    1.666662] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.666667] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.668658] ata1.00: configured for UDMA/133
[    1.688533] ata1.00: configured for UDMA/133
[    1.688537] ata1: EH complete
[    1.688719] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    1.688827] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.688858] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.688897] sd 0:0:0:0: [sda] Write Protect is off
[    1.688899] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.688919] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.689022]  sda:
[    1.691241] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-862   RB01 PQ: 0 ANSI: 5
[    1.694220]  sda1 sda2 sda3
[    1.696148] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.696153] Uniform CD-ROM driver Revision: 3.20
[    1.696245] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.696276] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.725022] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.725063] Freeing unused kernel memory: 540k freed
[    1.725412] Write protecting the kernel text: 4568k
[    1.725474] Write protecting the kernel read-only data: 1836k
[    1.823518] Linux agpgart interface v0.103
[    1.841001] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    1.841004] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.841070] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.841077] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb
[    1.841087] e1000e 0000:00:19.0: setting latency timer to 64
[    1.841283]   alloc irq_desc for 31 on node -1
[    1.841285]   alloc kstat_irqs on node -1
[    1.841310] e1000e 0000:00:19.0: irq 31 for MSI/MSI-X
[    1.883079] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.897996] acpi device:08: registered as cooling_device2
[    1.898158] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06/device:07/input/input5
[    1.898200] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.942067] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.005111] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.106659] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:25:b6:a0:a0
[    2.106661] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.106698] 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1008ff-0ff
[    2.168854] usb 3-1: configuration #1 chosen from 1 choice
[    2.480078] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    2.722852] usb 3-2: configuration #1 chosen from 1 choice
[    2.980452] PM: Starting manual resume from disk
[    2.980456] PM: Resume from partition 8:2
[    2.980458] PM: Checking hibernation image.
[    2.980773] PM: Resume from disk failed.
[    3.048064] kjournald starting.  Commit interval 5 seconds
[    3.048078] EXT3-fs: mounted filesystem with writeback data mode.
[    3.217722] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c000060e55e]
[    3.674943] type=1505 audit(1262552749.796:2): operation="profile_load" pid=463 name=/usr/share/gdm/guest-session/Xsession
[    3.685958] type=1505 audit(1262552749.808:3): operation="profile_load" pid=464 name=/sbin/dhclient3
[    3.686607] type=1505 audit(1262552749.808:4): operation="profile_load" pid=464 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.686973] type=1505 audit(1262552749.808:5): operation="profile_load" pid=464 name=/usr/lib/connman/scripts/dhclient-script
[    3.721493] type=1505 audit(1262552749.843:6): operation="profile_load" pid=465 name=/usr/bin/evince
[    3.731634] type=1505 audit(1262552749.851:7): operation="profile_load" pid=465 name=/usr/bin/evince-previewer
[    3.737677] type=1505 audit(1262552749.859:8): operation="profile_load" pid=465 name=/usr/bin/evince-thumbnailer
[    3.752257] type=1505 audit(1262552749.872:9): operation="profile_load" pid=467 name=/usr/lib/cups/backend/cups-pdf
[   13.368697] udev: starting version 147
[   13.369929] Adding 2996112k swap on /dev/sda2.  Priority:-1 extents:1 across:2996112k 
[   13.396062] Non-volatile memory driver v1.3
[   13.404566] lp: driver loaded but no devices found
[   13.409000] thinkpad_acpi: ThinkPad ACPI Extras v0.23
[   13.409003] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   13.409005] thinkpad_acpi: ThinkPad BIOS 7LETB9WW (2.19 ), EC 7KHT24WW-1.08
[   13.409007] thinkpad_acpi: Lenovo ThinkPad T61, model 6460DWU
[   13.410508] thinkpad_acpi: ACPI backlight control delay disabled
[   13.411148] thinkpad_acpi: radio switch found; radios are enabled
[   13.411242] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   13.411246] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   13.498815] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   13.501218] sdhci: Secure Digital Host Controller Interface driver
[   13.501221] sdhci: Copyright(c) Pierre Ossman
[   13.505688] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.505690] ricoh-mmc: Copyright(c) Philip Langdale
[   13.518918] Registered led device: tpacpi::thinklight
[   13.518958] Registered led device: tpacpi::power
[   13.518972] Registered led device: tpacpi::standby
[   13.518987] Registered led device: tpacpi::thinkvantage
[   13.543913] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   13.544271] input: ThinkPad Extra Buttons as /devices/virtual/input/input6
[   13.576213] cfg80211: Calling CRDA to update world regulatory domain
[   13.592555] EXT3 FS on sda3, internal journal
[   13.610822] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.625833] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   13.625840] yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   13.625845] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   13.625849] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x8000-0xbfff: clean.
[   13.626718] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   13.626721] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   13.632041] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[   13.632069] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.633103] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   13.633114] sdhci-pci 0000:15:00.2: setting latency timer to 64
[   13.634149] Registered led device: mmc0::
[   13.635179] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[   13.635216] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   13.635254] ricoh-mmc: Controller is now disabled.
[   13.658991] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.658997] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.659093] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.659125] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.659190] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.712042] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   13.712146] usbcore: registered new interface driver btusb
[   13.712793] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.712878]   alloc irq_desc for 32 on node -1
[   13.712880]   alloc kstat_irqs on node -1
[   13.712903] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[   13.713942] cfg80211: World regulatory domain updated:
[   13.713944] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.713947] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.713950] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.713952] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.713955] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.713957] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.731642] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.731646] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   13.731677] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.748001] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.817244] psmouse serio1: ID: 10 00 64
[   14.032047] __ratelimit: 6 callbacks suppressed
[   14.032050] type=1505 audit(1262574360.151:12): operation="profile_replace" pid=995 name=/usr/share/gdm/guest-session/Xsession
[   14.033500] type=1505 audit(1262574360.155:13): operation="profile_replace" pid=996 name=/sbin/dhclient3
[   14.034127] type=1505 audit(1262574360.155:14): operation="profile_replace" pid=996 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.034512] type=1505 audit(1262574360.155:15): operation="profile_replace" pid=996 name=/usr/lib/connman/scripts/dhclient-script
[   14.037814] type=1505 audit(1262574360.159:16): operation="profile_replace" pid=997 name=/usr/bin/evince
[   14.049520] type=1505 audit(1262574360.171:17): operation="profile_replace" pid=997 name=/usr/bin/evince-previewer
[   14.056653] type=1505 audit(1262574360.175:18): operation="profile_replace" pid=997 name=/usr/bin/evince-thumbnailer
[   14.065627] type=1505 audit(1262574360.187:19): operation="profile_replace" pid=999 name=/usr/lib/cups/backend/cups-pdf
[   14.066384] type=1505 audit(1262574360.187:20): operation="profile_replace" pid=999 name=/usr/sbin/cupsd
[   14.068546] type=1505 audit(1262574360.187:21): operation="profile_replace" pid=1000 name=/usr/sbin/tcpdump
[   14.079268] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   14.082272] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   14.083102] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   14.083774] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   14.084594] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.139074] e1000e 0000:00:19.0: irq 31 for MSI/MSI-X
[   14.163293] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[   14.171817] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   14.196669] e1000e 0000:00:19.0: irq 31 for MSI/MSI-X
[   14.196962] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.198605] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   14.198791] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input8
[   14.238983] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24
[   14.377672] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.377675] Bluetooth: BNEP filters: protocol multicast
[   14.385259] Bridge firewalling registered
[   14.455881] ppdev: user-space parallel port driver
[   14.463659] Registered led device: iwl-phy0::radio
[   14.463679] Registered led device: iwl-phy0::assoc
[   14.463694] Registered led device: iwl-phy0::RX
[   14.463709] Registered led device: iwl-phy0::TX
[   14.509780] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.110905] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[   17.111244] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.034639] wlan0: authenticate with AP 00:24:b2:c3:59:3a
[   23.038439] wlan0: authenticated
[   23.038444] wlan0: associate with AP 00:24:b2:c3:59:3a
[   23.040977] wlan0: RX AssocResp from 00:24:b2:c3:59:3a (capab=0x411 status=0 aid=2)
[   23.040982] wlan0: associated
[   23.061263] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.740048] eth0: no IPv6 routers present
[   31.049843] wlan0: deauthenticated (Reason: 15)
[   32.048067] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 1
[   32.248053] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 2
[   32.448052] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 3
[   32.452347] wlan0 direct probe responded
[   32.452351] wlan0: authenticate with AP 00:24:b2:c3:59:3a
[   32.455774] wlan0: authenticated
[   32.455779] wlan0: associate with AP 00:24:b2:c3:59:3a
[   32.458186] wlan0: RX ReassocResp from 00:24:b2:c3:59:3a (capab=0x411 status=0 aid=2)
[   32.458191] wlan0: associated
[   33.104052] wlan0: no IPv6 routers present
[   40.584552] wlan0: deauthenticated (Reason: 15)
[   41.584062] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 1
[   41.588364] wlan0 direct probe responded
[   41.588366] wlan0: authenticate with AP 00:24:b2:c3:59:3a
[   41.590352] wlan0: authenticated
[   41.590356] wlan0: associate with AP 00:24:b2:c3:59:3a
[   41.592857] wlan0: RX ReassocResp from 00:24:b2:c3:59:3a (capab=0x411 status=0 aid=2)
[   41.592862] wlan0: associated
[   49.599461] wlan0: deauthenticated (Reason: 15)
[   50.596180] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 1
[   50.600503] wlan0 direct probe responded
[   50.600506] wlan0: authenticate with AP 00:24:b2:c3:59:3a
[   50.602881] wlan0: authenticated
[   50.602884] wlan0: associate with AP 00:24:b2:c3:59:3a
[   50.605402] wlan0: RX ReassocResp from 00:24:b2:c3:59:3a (capab=0x411 status=0 aid=2)
[   50.605406] wlan0: associated
[   58.619454] wlan0: deauthenticated (Reason: 15)
[   59.616098] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 1
[   59.620391] wlan0 direct probe responded
[   59.620394] wlan0: authenticate with AP 00:24:b2:c3:59:3a
[   59.622264] wlan0: authenticated
[   59.622271] wlan0: associate with AP 00:24:b2:c3:59:3a
[   59.624687] wlan0: RX ReassocResp from 00:24:b2:c3:59:3a (capab=0x411 status=0 aid=2)
[   59.624690] wlan0: associated
[   67.619562] wlan0: deauthenticated (Reason: 15)
[   68.616139] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 1
[   68.620530] wlan0 direct probe responded
[   68.620535] wlan0: authenticate with AP 00:24:b2:c3:59:3a
[   68.622452] wlan0: authenticated
[   68.622456] wlan0: associate with AP 00:24:b2:c3:59:3a
[   68.624986] wlan0: RX ReassocResp from 00:24:b2:c3:59:3a (capab=0x411 status=0 aid=2)
[   68.624991] wlan0: associated
[   76.615388] wlan0: deauthenticated (Reason: 15)
[   77.612110] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 1
[   77.812322] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 2
[   78.012271] wlan0: direct probe to AP 00:24:b2:c3:59:3a try 3
[   78.021921] wlan0 direct probe responded
[   78.021931] wlan0: authenticate with AP 00:24:b2:c3:59:3a
[   78.023953] wlan0: authenticated
[   78.023959] wlan0: associate with AP 00:24:b2:c3:59:3a
[   78.028694] wlan0: RX ReassocResp from 00:24:b2:c3:59:3a (capab=0x411 status=0 aid=2)
[   78.028702] wlan0: associated
[   78.879585] CE: hpet increasing min_delta_ns to 15000 nsec
[   80.882329] wlan0: disassociating by local choice (reason=3)
[  300.773114] nvidia: module license 'NVIDIA' taints kernel.
[  300.773118] Disabling lock debugging due to kernel taint
[  301.025802] nvidia 0000:01:00.0: power state changed by ACPI to D0
[  301.025814] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  301.025823] nvidia 0000:01:00.0: setting latency timer to 64
[  301.025962] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
  *-network
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:b6:a0:a0
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.3-0 ip=192.168.0.9 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:31 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:7c:a9:9b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:df2fe000-df2fffff
wlan0     No scan results

Description:	Ubuntu 9.10
2.6.31-16-generic i686

```

---

### Post by keyrun78in on 2010-01-16
Hi 

I am new to Ubuntu and I have Ubuntu 9.10--the Karmic Koala on my HP dv6139us laptop. But was not able to get my build in webcam work. I have tried running the above commands but got the errors as shown below. Please help me to get my webcam working

code
laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Output of the commands in this blog:::
kiran@kiran-laptop:~$ svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) ~/r5u870
A    /home/kiran/r5u870/r5u870_183a.fw
A    /home/kiran/r5u870/r5u870_183b.fw
A    /home/kiran/r5u870/r5u870_1870_1.fw
A    /home/kiran/r5u870/r5u870_183e.fw
A    /home/kiran/r5u870/AUTHORS
A    /home/kiran/r5u870/ChangeLog
A    /home/kiran/r5u870/r5u870.c
A    /home/kiran/r5u870/recode-fw.scm
A    /home/kiran/r5u870/debug.mk
A    /home/kiran/r5u870/README
A    /home/kiran/r5u870/r5u870_1810.fw
A    /home/kiran/r5u870/r5u870_1812.fw
A    /home/kiran/r5u870/r5u870_1830.fw
A    /home/kiran/r5u870/r5u870_1841.fw
A    /home/kiran/r5u870/r5u870_1832.fw
A    /home/kiran/r5u870/r5u870_1833.fw
A    /home/kiran/r5u870/r5u870_1834.fw
A    /home/kiran/r5u870/r5u870_1870.fw
A    /home/kiran/r5u870/r5u870_1835.fw
A    /home/kiran/r5u870/r5u870_1836.fw
A    /home/kiran/r5u870/COPYING
A    /home/kiran/r5u870/r5u870_1839.fw
A    /home/kiran/r5u870/MAINTAINERS
A    /home/kiran/r5u870/Kbuild
A    /home/kiran/r5u870/usbcam
A    /home/kiran/r5u870/usbcam/usbcam.h
A    /home/kiran/r5u870/usbcam/usbcam_priv.h
A    /home/kiran/r5u870/usbcam/usbcam_fops.c
A    /home/kiran/r5u870/usbcam/usbcam_buf.c
A    /home/kiran/r5u870/usbcam/usbcam_util.c
A    /home/kiran/r5u870/usbcam/usbcam_dev.c
A    /home/kiran/r5u870/usbcam/usbcam_skel.c
A    /home/kiran/r5u870/usbcam/Makefile
A    /home/kiran/r5u870/NEWS
A    /home/kiran/r5u870/Makefile
Checked out revision 109.
kiran@kiran-laptop:~$ cd ~/r5u870
kiran@kiran-laptop:~/r5u870$ sudo make
[sudo] password for kiran: 
Sorry, try again.
[sudo] password for kiran: 
make -C /lib/modules/2.6.31-14-generic/build M=/home/kiran/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/kiran/r5u870/r5u870.o
/home/kiran/r5u870/r5u870.c:872:1: warning: "V4L2_CID_PRIVACY" redefined
In file included from include/linux/videodev.h:17,
                 from /home/kiran/r5u870/usbcam/usbcam.h:38,
                 from /home/kiran/r5u870/r5u870.c:59:
include/linux/videodev2.h:1148:1: warning: this is the location of the previous definition
/home/kiran/r5u870/r5u870.c:874:1: warning: "V4L2_CID_LASTP1" redefined
include/linux/videodev2.h:904:1: warning: this is the location of the previous definition
  CC [M]  /home/kiran/r5u870/usbcam/usbcam_dev.o
/home/kiran/r5u870/usbcam/usbcam_dev.c: In function &#8216;usbcam_register_mod&#8217;:
/home/kiran/r5u870/usbcam/usbcam_dev.c:535: warning: assignment from incompatible pointer type
  CC [M]  /home/kiran/r5u870/usbcam/usbcam_fops.o
/home/kiran/r5u870/usbcam/usbcam_fops.c: In function &#8216;usbcam_v4l_vidioc_querycap&#8217;:
/home/kiran/r5u870/usbcam/usbcam_fops.c:522: error: &#8216;struct device&#8217; has no member named &#8216;bus_id&#8217;
/home/kiran/r5u870/usbcam/usbcam_fops.c: In function &#8216;usbcam_v4l_ioctl&#8217;:
/home/kiran/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 1 of &#8216;video_usercopy&#8217; from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected &#8216;struct file *&#8217; but argument is of type &#8216;struct inode *&#8217;
/home/kiran/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 2 of &#8216;video_usercopy&#8217; makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected &#8216;unsigned int&#8217; but argument is of type &#8216;struct file *&#8217;
/home/kiran/r5u870/usbcam/usbcam_fops.c:1170: warning: passing argument 4 of &#8216;video_usercopy&#8217; makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected &#8216;v4l2_kioctl&#8217; but argument is of type &#8216;long unsigned int&#8217;
/home/kiran/r5u870/usbcam/usbcam_fops.c:1170: error: too many arguments to function &#8216;video_usercopy&#8217;
/home/kiran/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 1 of &#8216;video_ioctl2&#8217; from incompatible pointer type
include/media/v4l2-ioctl.h:302: note: expected &#8216;struct file *&#8217; but argument is of type &#8216;struct inode *&#8217;
/home/kiran/r5u870/usbcam/usbcam_fops.c:1174: warning: passing argument 2 of &#8216;video_ioctl2&#8217; makes integer from pointer without a cast
include/media/v4l2-ioctl.h:302: note: expected &#8216;unsigned int&#8217; but argument is of type &#8216;struct file *&#8217;
/home/kiran/r5u870/usbcam/usbcam_fops.c:1174: error: too many arguments to function &#8216;video_ioctl2&#8217;
/home/kiran/r5u870/usbcam/usbcam_fops.c:1162: warning: unused variable &#8216;udp&#8217;
make[3]: *** [/home/kiran/r5u870/usbcam/usbcam_fops.o] Error 1
make[2]: *** [/home/kiran/r5u870/usbcam] Error 2
make[1]: *** [_module_/home/kiran/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
kiran@kiran-laptop:~/r5u870$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.31-14-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
kiran@kiran-laptop:~/r5u870$ sudo apt-get install xawtv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xawtv is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 184 not upgraded.
kiran@kiran-laptop:~/r5u870$ xawtv /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.31-14-generic)
xinerama 0: 1280x800+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

---

