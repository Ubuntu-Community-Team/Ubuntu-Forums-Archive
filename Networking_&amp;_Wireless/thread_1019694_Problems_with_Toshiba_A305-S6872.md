---
title: "Problems with Toshiba A305-S6872"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by mikesol on 2008-12-23
Hi everybody, I'm a very nob with this things.:confused:

I have a Toshiba A305-S6872, with Ubuntu 8.10 and Vista(:-&).

Well, I can connect correctly to internet in Vista via LAN in the University, but when I try it in ubuntu it doesn't work.

All the information is:

Wireless Brand, Model and Wireless Chipset:
```
$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03) 
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03) 
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) 
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03) 
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03) 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev ff) 
03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232] 
04:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) 
04:06.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) 
04:06.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12) 
04:06.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12) 
```


```
$ lsusb
Bus 003 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 

```


check interface:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:66:c4:80  
          inet6 addr: fe80::21e:33ff:fe66:c480/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:94489280490 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:4856 (4.8 KB)  TX bytes:4856 (4.8 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:21:5d:67:1f:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5D-67-1F-A4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```

```
$ iwconfig
lo        no wireless extensions. 
 
eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 
```

Check for modules:

```
$ lsmod
Module                  Size  Used by 
ipv6                  314312  14 
af_packet              29568  3 
i915                   44544  2 
drm                   110304  3 i915 
binfmt_misc            18700  1 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge 
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep 
bluetooth              70820  6 rfcomm,sco,bnep,l2cap 
ppdev                  16904  0 
acpi_cpufreq           16400  1 
cpufreq_powersave      10368  0 
cpufreq_userspace      12420  0 
cpufreq_conservative    16392  0 
cpufreq_ondemand       16400  1 
cpufreq_stats          14468  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats 
wmi                    15808  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs 
container              12288  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter 
x_tables               31752  1 ip_tables 
sbp2                   32652  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp 
joydev                 20736  0 
serio_raw              14596  0 
pcspkr                 11136  0 
psmouse                51612  0 
arc4                   10368  2 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb 
sdhci_pci              17024  0 
sdhci                  27396  1 sdhci_pci 
mmc_core               67168  1 sdhci 
evdev                  20512  11 
iwlagn                113668  0 
iwlcore               105540  1 iwlagn 
uvcvideo               68616  0 
compat_ioctl32         18176  1 uvcvideo 
videodev               46720  2 uvcvideo,compat_ioctl32 
v4l1_compat            24580  2 uvcvideo,videodev 
snd_hda_intel         489264  3 
rfkill                 19364  2 iwlcore 
led_class              13192  1 iwlcore 
snd_pcm_oss            52608  0 
mac80211              253440  2 iwlagn,iwlcore 
snd_mixer_oss          25088  1 snd_pcm_oss 
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss 
cfg80211               37136  3 iwlagn,iwlcore,mac80211 
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi 
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
video                  28948  0 
output                 11776  1 video 
snd_timer              34320  2 snd_pcm,snd_seq 
battery                21128  0 
button                 15904  0 
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
ac                     13448  0 
intel_agp              39280  1 
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              16800  1 snd 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp 
ext3                  150544  1 
jbd                    66472  1 ext3 
mbcache                17924  1 ext3 
sr_mod                 24644  1 
cdrom                  47784  1 sr_mod 
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod 
sg                     45408  0 
usbhid                 39776  0 
hid                    59072  1 usbhid 
ahci                   43148  4 
ehci_hcd               48908  0 
ohci1394               41524  0 
libata                200160  1 ahci 
scsi_mod              183160  5 sbp2,sr_mod,sd_mod,sg,libata 
ieee1394              110592  2 sbp2,ohci1394 
dock                   18464  1 libata 
uhci_hcd               34336  0 
r8169                  40196  0 
usbcore               175376  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd 
thermal                27424  0 
processor              47800  4 acpi_cpufreq,thermal 
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon 
font                   17152  1 fbcon 
bitblit                14592  1 fbcon 
softcursor             10496  1 bitblit 
fuse                   68288  5 
```


Kernel boot messages
```
dmesg
[    0.000000] Initializing cgroup subsys cpuset 
[    0.000000] Initializing cgroup subsys cpu 
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic) 
[    0.000000] Command line: root=UUID=28eedc04-2914-47ae-9c8d-6b7db2f1b74f ro quiet splash 
[    0.000000] KERNEL supported cpus: 
[    0.000000]   Intel GenuineIntel 
[    0.000000]   AMD AuthenticAMD 
[    0.000000]   Centaur CentaurHauls 
[    0.000000] BIOS-provided physical RAM map: 
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable) 
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved) 
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved) 
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7b6c000 (usable) 
[    0.000000]  BIOS-e820: 00000000b7b6c000 - 00000000b7bbf000 (reserved) 
[    0.000000]  BIOS-e820: 00000000b7bbf000 - 00000000b7c86000 (usable) 
[    0.000000]  BIOS-e820: 00000000b7c86000 - 00000000b7cbf000 (ACPI NVS) 
[    0.000000]  BIOS-e820: 00000000b7cbf000 - 00000000b7cee000 (usable) 
[    0.000000]  BIOS-e820: 00000000b7cee000 - 00000000b7cff000 (ACPI data) 
[    0.000000]  BIOS-e820: 00000000b7cff000 - 00000000b7d00000 (usable) 
[    0.000000]  BIOS-e820: 00000000b7d00000 - 00000000c0000000 (reserved) 
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved) 
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved) 
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable) 
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x3ffffffff 
[    0.000000] last_pfn = 0xb7d00 max_arch_pfn = 0x3ffffffff 
[    0.000000] init_memory_mapping 
[    0.000000]  0000000000 - 00b7c00000 page 2M 
[    0.000000]  00b7c00000 - 00b7d00000 page 4k 
[    0.000000] kernel direct mapping tables up to b7d00000 @ 8000-d000 
[    0.000000] last_map_addr: b7d00000 end: b7d00000 
[    0.000000] init_memory_mapping 
[    0.000000]  0100000000 - 0140000000 page 2M 
[    0.000000] kernel direct mapping tables up to 140000000 @ b000-11000 
[    0.000000] last_map_addr: 140000000 end: 140000000 
[    0.000000] RAMDISK: 377ac000 - 37fefb5b 
[    0.000000] DMI 2.4 present. 
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 TOSINV) 
[    0.000000] ACPI: XSDT B7CFE120, 0064 (r1 TOSINV TOSINV00        1       1000013) 
[    0.000000] ACPI: FACP B7CFD000, 00F4 (r4 TOSINV TOSINV00        1 MSFT  1000013) 
[    0.000000] ACPI: DSDT B7CF1000, 775B (r1 TOSINV TOSINV00        1 MSFT  1000013) 
[    0.000000] ACPI: FACS B7C93000, 0040 
[    0.000000] ACPI: HPET B7CFC000, 0038 (r1 TOSINV TOSINV00        1 MSFT  1000013) 
[    0.000000] ACPI: APIC B7CFB000, 006C (r2 TOSINV TOSINV00        1 MSFT  1000013) 
[    0.000000] ACPI: MCFG B7CFA000, 003C (r1 TOSINV TOSINV00        1 MSFT  1000013) 
[    0.000000] ACPI: ASF! B7CF9000, 00A5 (r32 TOSINV TOSINV00        1 MSFT  1000013) 
[    0.000000] ACPI: SLIC B7CF0000, 0176 (r1 TOSINV TOSINV00        1 MSFT  1000013) 
[    0.000000] ACPI: BOOT B7CEF000, 0028 (r1 TOSINV TOSINV00        1 MSFT  1000013) 
[    0.000000] ACPI: SSDT B7CEE000, 0655 (r1  PmRef    CpuPm     3000 INTL 20051117) 
[    0.000000] ACPI: DMI detected: Toshiba 
[    0.000000] No NUMA configuration found 
[    0.000000] Faking a node at 0000000000000000-0000000140000000 
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000 
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff] 
[    0.000000]   bootmap [000000000000c000 -  0000000000033fff] pages 28 
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0140000000] 
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000] 
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000] 
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c] 
[    0.000000]   #3 [00377ac000 - 0037fefb5b]          RAMDISK ==> [00377ac000 - 0037fefb5b] 
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000] 
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000] 
[    0.000000]   #6 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000] 
[    0.000000]  [ffffe20000000000-ffffe20004ffffff] PMD -> [ffff880028200000-ffff88002bffffff] on node 0 
[    0.000000] Zone PFN ranges: 
[    0.000000]   DMA      0x00000000 -> 0x00001000 
[    0.000000]   DMA32    0x00001000 -> 0x00100000 
[    0.000000]   Normal   0x00100000 -> 0x00140000 
[    0.000000] Movable zone start PFN for each node 
[    0.000000] early_node_map[6] active PFN ranges 
[    0.000000]     0: 0x00000000 -> 0x0000009e 
[    0.000000]     0: 0x00000100 -> 0x000b7b6c 
[    0.000000]     0: 0x000b7bbf -> 0x000b7c86 
[    0.000000]     0: 0x000b7cbf -> 0x000b7cee 
[    0.000000]     0: 0x000b7cff -> 0x000b7d00 
[    0.000000]     0: 0x00100000 -> 0x00140000 
[    0.000000] On node 0 totalpages: 1014785 
[    0.000000]   DMA zone: 2109 pages, LIFO batch:0 
[    0.000000]   DMA32 zone: 732323 pages, LIFO batch:31 
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31 
[    0.000000] ACPI: PM-Timer IO Port: 0x408 
[    0.000000] ACPI: Local APIC address 0xfee00000 
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled) 
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled) 
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0]) 
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl) 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level) 
[    0.000000] ACPI: IRQ0 used by override. 
[    0.000000] ACPI: IRQ2 used by override. 
[    0.000000] ACPI: IRQ9 used by override. 
[    0.000000] Setting APIC routing to flat 
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs 
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000 
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000 
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000 
[    0.000000] PM: Registered nosave memory: 00000000b7b6c000 - 00000000b7bbf000 
[    0.000000] PM: Registered nosave memory: 00000000b7c86000 - 00000000b7cbf000 
[    0.000000] PM: Registered nosave memory: 00000000b7cee000 - 00000000b7cff000 
[    0.000000] PM: Registered nosave memory: 00000000b7d00000 - 00000000c0000000 
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f8000000 
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000 
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000 
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000 
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000 
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000 
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000 
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000 
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000 
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000 
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000 
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000 
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000 
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000 
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:38000000) 
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data 
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 992480 
[    0.000000] Policy zone: Normal 
[    0.000000] Kernel command line: root=UUID=28eedc04-2914-47ae-9c8d-6b7db2f1b74f ro quiet splash 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes) 
[    0.000000] TSC: PIT calibration confirmed by PMTIMER. 
[    0.000000] TSC: using PIT calibration value 
[    0.000000] Detected 1995.218 MHz processor. 
[    0.004000] Console: colour VGA+ 80x25 
[    0.004000] console [tty0] enabled 
[    0.004000] Checking aperture... 
[    0.004000] No AGP bridge found 
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area 
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing! 
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB) 
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000 
[    0.004000] Memory: 3913840k/5242880k available (3112k kernel code, 145300k reserved, 1575k data, 536k init) 
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated 
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1 
[    0.004000] hpet clockevent registered 
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.43 BogoMIPS (lpj=7980872) 
[    0.004000] Security Framework initialized 
[    0.004000] SELinux:  Disabled at boot. 
[    0.004000] AppArmor: AppArmor initialized 
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes) 
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes) 
[    0.004139] Mount-cache hash table entries: 256 
[    0.004358] Initializing cgroup subsys ns 
[    0.004364] Initializing cgroup subsys cpuacct 
[    0.004367] Initializing cgroup subsys memory 
[    0.004384] CPU: L1 I cache: 32K, L1 D cache: 32K 
[    0.004386] CPU: L2 cache: 2048K 
[    0.004389] CPU 0/0 -> Node 0 
[    0.004391] CPU: Physical Processor ID: 0 
[    0.004392] CPU: Processor Core ID: 0 
[    0.004400] CPU0: Thermal monitoring enabled (TM2) 
[    0.004402] using mwait in idle threads. 
[    0.006657] ACPI: Core revision 20080609 
[    0.009402] ACPI: Checking initramfs for custom DSDT 
[    0.400480] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1 
[    0.440257] CPU0: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d 
[    0.440262] Using local APIC timer interrupts. 
[    0.444029] APIC timer calibration result 12470146 
[    0.444030] Detected 12.470 MHz APIC timer. 
[    0.444162] Booting processor 1/1 ip 6000 
[    0.004000] Initializing CPU#1 
[    0.004000] Calibrating delay using timer specific routine.. 3990.47 BogoMIPS (lpj=7980943) 
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K 
[    0.004000] CPU: L2 cache: 2048K 
[    0.004000] CPU 1/1 -> Node 0 
[    0.004000] CPU: Physical Processor ID: 0 
[    0.004000] CPU: Processor Core ID: 1 
[    0.004000] CPU1: Thermal monitoring enabled (TM2) 
[    0.532448] CPU1: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz stepping 0d 
[    0.532473] checking TSC synchronization [CPU#0 -> CPU#1]: passed. 
[    0.536068] Brought up 2 CPUs 
[    0.536071] Total of 2 processors activated (7980.90 BogoMIPS). 
[    0.536120] CPU0 attaching sched-domain: 
[    0.536122]  domain 0: span 0-1 level MC 
[    0.536125]   groups: 0 1 
[    0.536129]   domain 1: span 0-1 level NODE 
[    0.536130]    groups: 0-1 
[    0.536135] CPU1 attaching sched-domain: 
[    0.536137]  domain 0: span 0-1 level MC 
[    0.536138]   groups: 1 0 
[    0.536141]   domain 1: span 0-1 level NODE 
[    0.536143]    groups: 0-1 
[    0.536236] net_namespace: 1552 bytes 
[    0.536236] Booting paravirtualized kernel on bare hardware 
[    0.536303] Time: 11:46:33  Date: 12/23/08 
[    0.536335] NET: Registered protocol family 16 
[    0.536352] ACPI: bus type pci registered 
[    0.536352] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63 
[    0.536352] PCI: MCFG area at f8000000 reserved in E820 
[    0.540250] PCI: Using MMCONFIG at f8000000 - fbffffff 
[    0.540252] PCI: Using configuration type 1 for base access 
[    0.541385] ACPI: EC: Look up EC in DSDT 
[    0.546993] ACPI: BIOS _OSI(Linux) query ignored via DMI 
[    0.547986] ACPI: Interpreter enabled 
[    0.547989] ACPI: (supports S0 S3 S4 S5) 
[    0.548013] ACPI: Using IOAPIC for interrupt routing 
[    0.548108] ACPI: EC: non-query interrupt received, switching to interrupt mode 
[    0.604045] ACPI: EC: non-query interrupt received, switching to interrupt mode 
[    0.705448] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62 
[    0.705448] ACPI: EC: driver started in interrupt mode 
[    0.705448] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    0.705448] PCI: 0000:00:02.0 reg 10 64bit mmio: [d0000000, d03fffff] 
[    0.705448] PCI: 0000:00:02.0 reg 18 32bit mmio: [c0000000, cfffffff] 
[    0.705448] PCI: 0000:00:02.0 reg 20 io port: [5110, 5117] 
[    0.705448] PCI: 0000:00:02.1 reg 10 64bit mmio: [d3500000, d35fffff] 
[    0.705448] PCI: 0000:00:1a.0 reg 20 io port: [50e0, 50ff] 
[    0.705448] PCI: 0000:00:1a.1 reg 20 io port: [50c0, 50df] 
[    0.705448] PCI: 0000:00:1a.7 reg 10 32bit mmio: [d6805c00, d6805fff] 
[    0.705448] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold 
[    0.705448] pci 0000:00:1a.7: PME# disabled 
[    0.705448] PCI: 0000:00:1b.0 reg 10 64bit mmio: [d6800000, d6803fff] 
[    0.705448] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
[    0.705448] pci 0000:00:1b.0: PME# disabled 
[    0.705448] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold 
[    0.705448] pci 0000:00:1c.0: PME# disabled 
[    0.705448] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold 
[    0.705448] pci 0000:00:1c.1: PME# disabled 
[    0.705448] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold 
[    0.705448] pci 0000:00:1c.4: PME# disabled 
[    0.705448] PCI: 0000:00:1d.0 reg 20 io port: [50a0, 50bf] 
[    0.705448] PCI: 0000:00:1d.1 reg 20 io port: [5080, 509f] 
[    0.705448] PCI: 0000:00:1d.2 reg 20 io port: [5060, 507f] 
[    0.705448] PCI: 0000:00:1d.3 reg 20 io port: [5040, 505f] 
[    0.705448] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d6805800, d6805bff] 
[    0.705462] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold 
[    0.705467] pci 0000:00:1d.7: PME# disabled 
[    0.708192] PCI: 0000:00:1f.2 reg 10 io port: [5108, 510f] 
[    0.708199] PCI: 0000:00:1f.2 reg 14 io port: [511c, 511f] 
[    0.708207] PCI: 0000:00:1f.2 reg 18 io port: [5100, 5107] 
[    0.708214] PCI: 0000:00:1f.2 reg 1c io port: [5118, 511b] 
[    0.708222] PCI: 0000:00:1f.2 reg 20 io port: [5020, 503f] 
[    0.708229] PCI: 0000:00:1f.2 reg 24 32bit mmio: [d6805000, d68057ff] 
[    0.708261] pci 0000:00:1f.2: PME# supported from D3hot 
[    0.708265] pci 0000:00:1f.2: PME# disabled 
[    0.708290] PCI: 0000:00:1f.3 reg 10 64bit mmio: [d6806000, d68060ff] 
[    0.708308] PCI: 0000:00:1f.3 reg 20 io port: [5000, 501f] 
[    0.708485] PCI: 0000:02:00.0 reg 10 io port: [3000, 30ff] 
[    0.708532] PCI: 0000:02:00.0 reg 18 32bit mmio: [d0410000, d0410fff] 
[    0.708584] PCI: 0000:02:00.0 reg 20 32bit mmio: [d0400000, d040ffff] 
[    0.708738] pci 0000:02:00.0: unsupported PM cap regs version (7) 
[    0.708828] PCI: bridge 0000:00:1c.0 io port: [3000, 4fff] 
[    0.708833] PCI: bridge 0000:00:1c.0 32bit mmio: [d5800000, d67fffff] 
[    0.708840] PCI: bridge 0000:00:1c.0 64bit mmio pref: [d0400000, d14fffff] 
[    0.708971] PCI: 0000:03:00.0 reg 10 64bit mmio: [d4700000, d4701fff] 
[    0.709070] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold 
[    0.709081] pci 0000:03:00.0: PME# disabled 
[    0.709131] PCI: bridge 0000:00:1c.1 io port: [2000, 2fff] 
[    0.709136] PCI: bridge 0000:00:1c.1 32bit mmio: [d4700000, d57fffff] 
[    0.709143] PCI: bridge 0000:00:1c.1 64bit mmio pref: [d1500000, d24fffff] 
[    0.709201] PCI: bridge 0000:00:1c.4 io port: [1000, 1fff] 
[    0.709206] PCI: bridge 0000:00:1c.4 32bit mmio: [d3700000, d46fffff] 
[    0.709214] PCI: bridge 0000:00:1c.4 64bit mmio pref: [d2500000, d34fffff] 
[    0.709268] PCI: 0000:04:06.0 reg 10 32bit mmio: [d3600000, d36007ff] 
[    0.709325] pci 0000:04:06.0: supports D1 
[    0.709326] pci 0000:04:06.0: supports D2 
[    0.709328] pci 0000:04:06.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.709333] pci 0000:04:06.0: PME# disabled 
[    0.709369] PCI: 0000:04:06.1 reg 10 32bit mmio: [d3600a00, d3600aff] 
[    0.709425] pci 0000:04:06.1: supports D1 
[    0.709427] pci 0000:04:06.1: supports D2 
[    0.709429] pci 0000:04:06.1: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.709434] pci 0000:04:06.1: PME# disabled 
[    0.709470] PCI: 0000:04:06.2 reg 10 32bit mmio: [d3600900, d36009ff] 
[    0.709527] pci 0000:04:06.2: supports D1 
[    0.709529] pci 0000:04:06.2: supports D2 
[    0.709530] pci 0000:04:06.2: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.709536] pci 0000:04:06.2: PME# disabled 
[    0.709572] PCI: 0000:04:06.3 reg 10 32bit mmio: [d3600800, d36008ff] 
[    0.709629] pci 0000:04:06.3: supports D1 
[    0.709630] pci 0000:04:06.3: supports D2 
[    0.709632] pci 0000:04:06.3: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.709637] pci 0000:04:06.3: PME# disabled 
[    0.709685] pci 0000:00:1e.0: transparent bridge 
[    0.709691] PCI: bridge 0000:00:1e.0 32bit mmio: [d3600000, d36fffff] 
[    0.709733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.710336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT] 
[    0.710573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT] 
[    0.710802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT] 
[    0.711036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT] 
[    0.716271] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12) 
[    0.716357] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12) 
[    0.716539] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12) 
[    0.716721] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12) 
[    0.716902] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled. 
[    0.717085] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12) 
[    0.717265] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12) 
[    0.717447] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12) 
[    0.717558] ACPI: Power Resource [FN00] (on) 
[    0.717558] Linux Plug and Play Support v0.97 (c) Adam Belay 
[    0.717558] pnp: PnP ACPI init 
[    0.717558] ACPI: bus type pnp registered 
[    0.720401] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.4 BAR 7 (0x1000-0x1fff), disabling 
[    0.720423] pnp: PnP ACPI: found 8 devices 
[    0.720423] ACPI: ACPI bus type pnp unregistered 
[    0.720423] PCI: Using ACPI for IRQ routing 
[    0.740041] NET: Registered protocol family 8 
[    0.740042] NET: Registered protocol family 20 
[    0.740066] NetLabel: Initializing 
[    0.740066] NetLabel:  domain hash size = 128 
[    0.740066] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.740066] NetLabel:  unlabeled traffic allowed by default 
[    0.740073] PCI-GART: No AMD northbridge found. 
[    0.740079] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0 
[    0.740083] hpet0: 4 64-bit timers, 14318180 Hz 
[    0.744039] Switched to high resolution mode on CPU 0 
[    0.743768] tracer: 1286 pages allocated for 65536 entries of 80 bytes 
[    0.743770]    actual entries 65586 
[    0.743879] AppArmor: AppArmor Filesystem Enabled 
[    0.743902] ACPI: RTC can wake from S4 
[    0.744502] Switched to high resolution mode on CPU 1 
[    0.760520] system 00:01: ioport range 0x800-0x80f has been reserved 
[    0.760522] system 00:01: ioport range 0x810-0x817 has been reserved 
[    0.760525] system 00:01: ioport range 0x820-0x823 has been reserved 
[    0.760527] system 00:01: ioport range 0x400-0x47f has been reserved 
[    0.760529] system 00:01: ioport range 0x500-0x57f has been reserved 
[    0.760533] system 00:01: iomem range 0xf8000000-0xfbffffff could not be reserved 
[    0.760535] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved 
[    0.760538] system 00:01: iomem range 0xfed10000-0xfed13fff could not be reserved 
[    0.760541] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved 
[    0.760543] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved 
[    0.760546] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.760548] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved 
[    0.760551] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved 
[    0.760553] system 00:01: iomem range 0xff800000-0xffffffff could not be reserved 
[    0.765598] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02 
[    0.765602] pci 0000:00:1c.0:   IO window: 0x3000-0x4fff 
[    0.765609] pci 0000:00:1c.0:   MEM window: 0xd5800000-0xd67fffff 
[    0.765614] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0400000-0x000000d14fffff 
[    0.765622] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03 
[    0.765625] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff 
[    0.765631] pci 0000:00:1c.1:   MEM window: 0xd4700000-0xd57fffff 
[    0.765636] pci 0000:00:1c.1:   PREFETCH window: 0x000000d1500000-0x000000d24fffff 
[    0.765643] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06 
[    0.765647] pci 0000:00:1c.4:   IO window: 0x1000-0x1fff 
[    0.765652] pci 0000:00:1c.4:   MEM window: 0xd3700000-0xd46fffff 
[    0.765657] pci 0000:00:1c.4:   PREFETCH window: 0x000000d2500000-0x000000d34fffff 
[    0.765665] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04 
[    0.765667] pci 0000:00:1e.0:   IO window: disabled 
[    0.765673] pci 0000:00:1e.0:   MEM window: 0xd3600000-0xd36fffff 
[    0.765677] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    0.765697] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    0.765702] pci 0000:00:1c.0: setting latency timer to 64 
[    0.765710] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16 
[    0.765715] pci 0000:00:1c.1: setting latency timer to 64 
[    0.765724] pci 0000:00:1c.4: enabling device (0000 -> 0003) 
[    0.765728] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    0.765733] pci 0000:00:1c.4: setting latency timer to 64 
[    0.765741] pci 0000:00:1e.0: setting latency timer to 64 
[    0.765744] bus: 00 index 0 io port: [0, ffff] 
[    0.765746] bus: 00 index 1 mmio: [0, ffffffffffffffff] 
[    0.765748] bus: 02 index 0 io port: [3000, 4fff] 
[    0.765750] bus: 02 index 1 mmio: [d5800000, d67fffff] 
[    0.765751] bus: 02 index 2 mmio: [d0400000, d14fffff] 
[    0.765753] bus: 02 index 3 mmio: [0, 0] 
[    0.765755] bus: 03 index 0 io port: [2000, 2fff] 
[    0.765756] bus: 03 index 1 mmio: [d4700000, d57fffff] 
[    0.765758] bus: 03 index 2 mmio: [d1500000, d24fffff] 
[    0.765760] bus: 03 index 3 mmio: [0, 0] 
[    0.765761] bus: 06 index 0 io port: [1000, 1fff] 
[    0.765763] bus: 06 index 1 mmio: [d3700000, d46fffff] 
[    0.765765] bus: 06 index 2 mmio: [d2500000, d34fffff] 
[    0.765766] bus: 06 index 3 mmio: [0, 0] 
[    0.765768] bus: 04 index 0 mmio: [0, 0] 
[    0.765770] bus: 04 index 1 mmio: [d3600000, d36fffff] 
[    0.765771] bus: 04 index 2 mmio: [0, 0] 
[    0.765773] bus: 04 index 3 io port: [0, ffff] 
[    0.765774] bus: 04 index 4 mmio: [0, ffffffffffffffff] 
[    0.765785] NET: Registered protocol family 2 
[    0.804671] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.806128] TCP established hash table entries: 524288 (order: 11, 8388608 bytes) 
[    0.810616] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[    0.811174] TCP: Hash tables configured (established 524288 bind 65536) 
[    0.811177] TCP reno registered 
[    0.820634] NET: Registered protocol family 1 
[    0.820756] checking if image is initramfs... it is 
[    1.596976] Freeing initrd memory: 8462k freed 
[    1.601307] Simple Boot Flag value 0x5 read from CMOS RAM was invalid 
[    1.601311] Simple Boot Flag at 0x44 set to 0x1 
[    1.602262] audit: initializing netlink socket (disabled) 
[    1.602278] type=2000 audit(1230032793.600:1): initialized 
[    1.608383] HugeTLB registered 2 MB page size, pre-allocated 0 pages 
[    1.610736] VFS: Disk quotas dquot_6.5.1 
[    1.610820] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[    1.610921] msgmni has been set to 7660 
[    1.611040] io scheduler noop registered 
[    1.611042] io scheduler anticipatory registered 
[    1.611044] io scheduler deadline registered 
[    1.611157] io scheduler cfq registered (default) 
[    1.611171] pci 0000:00:02.0: Boot video device 
[    9.608008] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001 
[   17.608007] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001 
[   17.608245] pcieport-driver 0000:00:1c.0: setting latency timer to 64 
[   17.608293] pcieport-driver 0000:00:1c.0: found MSI capability 
[   17.608344] pci_express 0000:00:1c.0:pcie00: allocate port service 
[   17.608384] pci_express 0000:00:1c.0:pcie02: allocate port service 
[   17.608422] pci_express 0000:00:1c.0:pcie03: allocate port service 
[   17.608533] pcieport-driver 0000:00:1c.1: setting latency timer to 64 
[   17.608582] pcieport-driver 0000:00:1c.1: found MSI capability 
[   17.608629] pci_express 0000:00:1c.1:pcie00: allocate port service 
[   17.608665] pci_express 0000:00:1c.1:pcie02: allocate port service 
[   17.608700] pci_express 0000:00:1c.1:pcie03: allocate port service 
[   17.608808] pcieport-driver 0000:00:1c.4: setting latency timer to 64 
[   17.608855] pcieport-driver 0000:00:1c.4: found MSI capability 
[   17.608902] pci_express 0000:00:1c.4:pcie00: allocate port service 
[   17.608937] pci_express 0000:00:1c.4:pcie02: allocate port service 
[   17.608972] pci_express 0000:00:1c.4:pcie03: allocate port service 
[   17.638953] hpet_resources: 0xfed00000 is busy 
[   17.639024] Linux agpgart interface v0.103 
[   17.639028] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[   17.641081] brd: module loaded 
[   17.641152] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[   17.641266] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12 
[   17.670656] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   17.670662] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   17.688104] mice: PS/2 mouse device common for all mice 
[   17.688221] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 
[   17.688253] rtc0: alarms up to one month, hpet irqs 
[   17.688295] cpuidle: using governor ladder 
[   17.688297] cpuidle: using governor menu 
[   17.688663] TCP cubic registered 
[   17.688850] registered taskstats version 1 
[   17.688992]   Magic number: 4:168:783 
[   17.689075] tty ptyq5: hash matches 
[   17.689143] rtc_cmos 00:03: setting system clock to 2008-12-23 11:46:51 UTC (1230032811) 
[   17.689146] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[   17.689148] EDD information not available. 
[   17.689212] Freeing unused kernel memory: 536k freed 
[   17.689411] Write protecting the kernel read-only data: 4348k 
[   17.722552] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[   17.847151] fuse init (API version 7.9) 
[   17.860314] fan PNP0C0B:00: registered as cooling_device0 
[   17.860320] ACPI: Fan [FAN] (on) 
[   17.887248] ACPI: SSDT B7B77C18, 026B (r1  PmRef  Cpu0Ist     3000 INTL 20051117) 
[   17.887882] ACPI: SSDT B7B75598, 0537 (r1  PmRef  Cpu0Cst     3001 INTL 20051117) 
[   17.888489] Monitor-Mwait will be used to enter C-1 state 
[   17.888492] Monitor-Mwait will be used to enter C-2 state 
[   17.918291] ACPI: CPU0 (power states: C1[C1] C2[C2]) 
[   17.918347] processor ACPI0007:00: registered as cooling_device1 
[   17.918351] ACPI: Processor [CPU0] (supports 8 throttling states) 
[   17.918959] ACPI: SSDT B7B76E18, 01CF (r1  PmRef    ApIst     3000 INTL 20051117) 
[   17.919550] ACPI: SSDT B7B77F18, 008D (r1  PmRef    ApCst     3000 INTL 20051117) 
[   17.920368] Marking TSC unstable due to TSC halts in idle 
[   17.920470] ACPI: CPU1 (power states: C1[C1] C2[C2]) 
[   17.920542] processor ACPI0007:01: registered as cooling_device2 
[   17.920545] ACPI: Processor [CPU1] (supports 8 throttling states) 
[   17.923120] thermal LNXTHERM:01: registered as thermal_zone0 
[   17.923453] ACPI: Transitioning device [FAN] to D3 
[   17.923606] ACPI: Thermal Zone [THRM] (0 C) 
[   18.238660] usbcore: registered new interface driver usbfs 
[   18.238683] usbcore: registered new interface driver hub 
[   18.274818] usbcore: registered new device driver usb 
[   18.287424] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[   18.287451] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   18.287511] r8169 0000:02:00.0: setting latency timer to 64 
[   18.287534] r8169 0000:02:00.0: unknown MAC (37a00000) 
[   18.288047] eth0: RTL8169 at 0xffffc2000063e000, 00:1e:33:66:c4:80, XID 34a00000 IRQ 2300 
[   18.352117] USB Universal Host Controller Interface driver v3.0 
[   18.353640] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   18.353653] uhci_hcd 0000:00:1a.0: setting latency timer to 64 
[   18.353657] uhci_hcd 0000:00:1a.0: UHCI Host Controller 
[   18.353798] No dock devices found. 
[   18.356581] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1 
[   18.356625] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000050e0 
[   18.356777] usb usb1: configuration #1 chosen from 1 choice 
[   18.356802] hub 1-0:1.0: USB hub found 
[   18.356809] hub 1-0:1.0: 2 ports detected 
[   18.373295] SCSI subsystem initialized 
[   18.390655] libata version 3.00 loaded. 
[   18.564883] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[   18.564895] uhci_hcd 0000:00:1a.1: setting latency timer to 64 
[   18.564899] uhci_hcd 0000:00:1a.1: UHCI Host Controller 
[   18.564924] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2 
[   18.564966] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000050c0 
[   18.565065] usb usb2: configuration #1 chosen from 1 choice 
[   18.565092] hub 2-0:1.0: USB hub found 
[   18.565099] hub 2-0:1.0: 2 ports detected 
[   18.676618] usb 1-2: new full speed USB device using uhci_hcd and address 2 
[   18.925867] usb 1-2: configuration #1 chosen from 1 choice 
[   19.000059] Clocksource tsc unstable (delta = -144411507 ns) 
[   19.158246] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19 
[   19.158262] ehci_hcd 0000:00:1a.7: setting latency timer to 64 
[   19.158266] ehci_hcd 0000:00:1a.7: EHCI Host Controller 
[   19.158301] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3 
[   19.162206] ehci_hcd 0000:00:1a.7: debug port 1 
[   19.162213] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported 
[   19.162230] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd6805c00 
[   19.176595] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   19.176768] usb usb3: configuration #1 chosen from 1 choice 
[   19.176795] hub 3-0:1.0: USB hub found 
[   19.176802] hub 3-0:1.0: 4 ports detected 
[   19.248638] usb 1-2: USB disconnect, address 2 
[   19.384729] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[   19.384739] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[   19.384743] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[   19.384767] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4 
[   19.384806] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000050a0 
[   19.384893] usb usb4: configuration #1 chosen from 1 choice 
[   19.384917] hub 4-0:1.0: USB hub found 
[   19.384924] hub 4-0:1.0: 2 ports detected 
[   19.496051] usb 3-2: new high speed USB device using ehci_hcd and address 2 
[   19.592265] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[   19.592274] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[   19.592278] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[   19.592301] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5 
[   19.592329] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005080 
[   19.592418] usb usb5: configuration #1 chosen from 1 choice 
[   19.592442] hub 5-0:1.0: USB hub found 
[   19.592449] hub 5-0:1.0: 2 ports detected 
[   19.671604] usb 3-2: configuration #1 chosen from 1 choice 
[   19.696748] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16 
[   19.696757] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[   19.696760] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[   19.696784] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6 
[   19.696815] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00005060 
[   19.696900] usb usb6: configuration #1 chosen from 1 choice 
[   19.696924] hub 6-0:1.0: USB hub found 
[   19.696931] hub 6-0:1.0: 2 ports detected 
[   19.784099] usb 4-1: new low speed USB device using uhci_hcd and address 2 
[   19.800335] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18 
[   19.800344] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
[   19.800348] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[   19.800370] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 7 
[   19.800405] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00005040 
[   19.800493] usb usb7: configuration #1 chosen from 1 choice 
[   19.800526] hub 7-0:1.0: USB hub found 
[   19.800533] hub 7-0:1.0: 2 ports detected 
[   19.904915] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23 
[   19.904931] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[   19.904934] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[   19.904957] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8 
[   19.908867] ehci_hcd 0000:00:1d.7: debug port 1 
[   19.908873] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[   19.908879] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd6805800 
[   19.924593] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   19.924716] usb usb8: configuration #1 chosen from 1 choice 
[   19.924761] hub 8-0:1.0: USB hub found 
[   19.924775] hub 8-0:1.0: 8 ports detected 
[   19.935867] usb 4-1: device descriptor read/all, error -71 
[   19.992144] hub 4-0:1.0: unable to enumerate USB device on port 1 
[   20.132387] ahci 0000:00:1f.2: version 3.0 
[   20.132400] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19 
[   20.132535] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode 
[   20.132538] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ems 
[   20.132543] ahci 0000:00:1f.2: setting latency timer to 64 
[   20.132867] scsi0 : ahci 
[   20.133288] scsi1 : ahci 
[   20.133375] scsi2 : ahci 
[   20.133450] scsi3 : ahci 
[   20.133611] scsi4 : ahci 
[   20.133685] scsi5 : ahci 
[   20.133816] ata1: SATA max UDMA/133 abar m2048@0xd6805000 port 0xd6805100 irq 2299 
[   20.133820] ata2: SATA max UDMA/133 abar m2048@0xd6805000 port 0xd6805180 irq 2299 
[   20.133822] ata3: DUMMY 
[   20.133823] ata4: DUMMY 
[   20.133826] ata5: SATA max UDMA/133 abar m2048@0xd6805000 port 0xd6805300 irq 2299 
[   20.133829] ata6: SATA max UDMA/133 irq_stat 0x00000040, connection status changed irq 2299 
[   20.480100] usb 4-1: new low speed USB device using uhci_hcd and address 4 
[   20.616124] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[   20.655625] usb 4-1: configuration #1 chosen from 1 choice 
[   20.679353] usbcore: registered new interface driver hiddev 
[   20.693276] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/input/input2 
[   20.716241] input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.0-1 
[   20.716270] usbcore: registered new interface driver usbhid 
[   20.716276] usbhid: v2.6:USB HID core driver 
[   20.915079] ata1.00: ATA-8: WDC WD2500BEVS-26UST0, 01.01A01, max UDMA/133 
[   20.915084] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32) 
[   20.915996] ata1.00: configured for UDMA/133 
[   21.248120] ata2: SATA link down (SStatus 0 SControl 300) 
[   21.584119] ata5: SATA link down (SStatus 0 SControl 300) 
[   22.488104] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300) 
[   22.489580] ata6.00: ATAPI: MATSHITADVD-RAM UJ880ES, 1.90, max UDMA/33 
[   22.491275] ata6.00: configured for UDMA/33 
[   22.504272] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5 
[   22.506544] scsi 5:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ880ES  1.90 PQ: 0 ANSI: 5 
[   22.506722] ohci1394 0000:04:06.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[   22.506729] ohci1394 0000:04:06.0: setting latency timer to 64 
[   22.559447] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d3600000-d36007ff]  Max Packet=[2048]  IR/IT contexts=[4/4] 
[   22.573879] scsi 0:0:0:0: Attached scsi generic sg0 type 0 
[   22.573915] scsi 5:0:0:0: Attached scsi generic sg1 type 5 
[   22.608364] Driver 'sd' needs updating - please use bus_type methods 
[   22.608479] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB) 
[   22.608513] sd 0:0:0:0: [sda] Write Protect is off 
[   22.608515] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   22.608551] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   22.608634] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB) 
[   22.608653] sd 0:0:0:0: [sda] Write Protect is off 
[   22.608656] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   22.608690] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   22.608694]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[   22.661304]  sda1 sda2 sda3 sda4 < sda5 sda6 > 
[   22.707045] sd 0:0:0:0: [sda] Attached SCSI disk 
[   23.702337] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray 
[   23.702344] Uniform CD-ROM driver Revision: 3.20 
[   23.702499] sr 5:0:0:0: Attached scsi CD-ROM sr0 
[   23.836270] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080d1e3366c480] 
[   26.745206] PM: Starting manual resume from disk 
[   26.745210] PM: Resume from partition 8:6 
[   26.745211] PM: Checking hibernation image. 
[   26.745380] PM: Resume from disk failed. 
[   26.811333] kjournald starting.  Commit interval 5 seconds 
[   26.811366] EXT3-fs: mounted filesystem with ordered data mode. 
[   34.808955] udevd version 124 started 
[   35.078058] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   35.136317] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   35.268530] agpgart-intel 0000:00:00.0: Intel Mobile Intel? GM45 Express Chipset 
[   35.269121] agpgart-intel 0000:00:00.0: detected 131068K stolen memory 
[   35.276219] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000 
[   35.276686] ACPI: AC Adapter [ADP0] (on-line) 
[   35.343179] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3 
[   35.368552] ACPI: Power Button (FF) [PWRF] 
[   35.368762] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4 
[   35.400521] ACPI: Power Button (CM) [PWRB] 
[   35.400618] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5 
[   35.404147] ACPI: Lid Switch [LID0] 
[   35.405560] ACPI: Battery Slot [BAT0] (battery present) 
[   35.461628] acpi device:05: registered as cooling_device3 
[   35.462016] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6 
[   35.480538] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no) 
[   35.866150] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[   35.866182] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[   35.898635] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS... 
[   35.925656] Linux video capture interface: v2.00 
[   35.954730] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070) 
[   35.970524] input: CNF7051 as /devices/pci0000:00/0000:00:1a.7/usb3/3-2/3-2:1.0/input/input7 
[   35.970574] usbcore: registered new interface driver uvcvideo 
[   35.970589] USB Video Class driver (v0.1.0) 
[   36.031480] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks 
[   36.031483] iwlagn: Copyright(c) 2003-2008 Intel Corporation 
[   36.031672] iwlagn 0000:03:00.0: power state changed by ACPI to D0 
[   36.031712] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   36.031748] iwlagn 0000:03:00.0: setting latency timer to 64 
[   36.031833] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54 
[   36.061541] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels 
[   36.080361] iwlagn 0000:03:00.0: PCI INT A disabled 
[   36.081228] phy0: Selected rate control algorithm 'iwl-agn-rs' 
[   36.175680] sdhci: Secure Digital Host Controller Interface driver 
[   36.175683] sdhci: Copyright(c) Pierre Ossman 
[   36.288026] sdhci-pci 0000:04:06.1: SDHCI controller found [1180:0822] (rev 22) 
[   36.288043] sdhci-pci 0000:04:06.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17 
[   36.289059] sdhci-pci 0000:04:06.1: Will use DMA mode even though HW doesn't fully claim to support it. 
[   36.291128] mmc0: SDHCI controller on PCI [0000:04:06.1] using DMA 
[   36.303020] input: PC Speaker as /devices/platform/pcspkr/input/input8 
[   37.152396] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1e0b1, caps: 0xd04711/0xa00000 
[   37.229426] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9 
[   41.783801] lp: driver loaded but no devices found 
[   41.971006] Adding 979924k swap on /dev/sda6.  Priority:-1 extents:1 across:979924k 
[   73.095102] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended 
[   73.095317] EXT3 FS on sda5, internal journal 
[   74.116697] type=1505 audit(1230054467.513:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4537 
[   74.256189] type=1505 audit(1230054467.653:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4542 
[   74.256370] type=1505 audit(1230054467.653:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4542 
[   74.383015] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   75.043579] ACPI: WMI: Mapper loaded 
[   76.040855] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[   76.246763] ppdev: user-space parallel port driver 
[   83.193525] Bluetooth: Core ver 2.13 
[   83.195835] NET: Registered protocol family 31 
[   83.195846] Bluetooth: HCI device and connection manager initialized 
[   83.195853] Bluetooth: HCI socket layer initialized 
[   83.219114] Bluetooth: L2CAP ver 2.11 
[   83.219125] Bluetooth: L2CAP socket layer initialized 
[   83.236371] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   83.236387] Bluetooth: BNEP filters: protocol multicast 
[   83.275651] Bridge firewalling registered 
[   83.275973] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature. 
[   83.291467] Bluetooth: SCO (Voice Link) ver 0.6 
[   83.291479] Bluetooth: SCO socket layer initialized 
[   83.433095] Bluetooth: RFCOMM socket layer initialized 
[   83.433132] Bluetooth: RFCOMM TTY layer initialized 
[   83.433136] Bluetooth: RFCOMM ver 1.10 
[   87.683399] [drm] Initialized drm 1.1.0 20060810 
[   87.690200] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   87.690215] pci 0000:00:02.0: setting latency timer to 64 
[   87.693364] [drm] Initialized i915 1.6.0 20060119 on minor 0 
[   88.428167] r8169: eth0: link up 
[   88.432483] iwlagn 0000:03:00.0: power state changed by ACPI to D0 
[   88.432516] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   88.432628] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006) 
[   88.432864] firmware: requesting iwlwifi-5000-1.ucode 
[   88.511317] iwlagn: Radio disabled by HW RF Kill switch 
[   88.634888] NET: Registered protocol family 17 
[   88.667255] set status page addr 0x07fff000 
[  120.976752] CPU0 attaching NULL sched-domain. 
[  120.976771] CPU1 attaching NULL sched-domain. 
[  120.996257] CPU0 attaching sched-domain: 
[  120.996271]  domain 0: span 0-1 level MC 
[  120.996276]   groups: 0 1 
[  120.996286]   domain 1: span 0-1 level NODE 
[  120.996291]    groups: 0-1 
[  120.996302] CPU1 attaching sched-domain: 
[  120.996306]  domain 0: span 0-1 level MC 
[  120.996311]   groups: 1 0 
[  120.996318]   domain 1: span 0-1 level NODE 
[  120.996323]    groups: 0-1 
[  216.089617] NET: Registered protocol family 10 
[  216.090813] lo: Disabled Privacy Extensions 
[  216.096671] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  226.988132] eth0: no IPv6 routers present
```

Network configuration

```
$ sudo lshw -C network
  *-generic               
       description: Ethernet interface 
       product: Illegal Vendor ID 
       vendor: Illegal Vendor ID 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: ff 
       serial: 00:1e:33:66:c4:80 
       size: 1GB/s 
       capacity: 1GB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s 
  *-network 
       description: Wireless interface 
       product: Wireless WiFi Link 5100 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wmaster0 
       version: 00 
       serial: 00:21:5d:67:1f:a4 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 02:34:e5:a8:eb:36 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
```

Scan for networks:


```
iwlist scan
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     No scan results 

pan0      Interface doesn't support scanning. 
```

Kernel/architecture (including 32 vs. 64 bit): 
```
$ uname -mr
2.6.27-9-generic x86_64 
```

Restarting the network:

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...  
```


I hope you can help with that, Thanks

PD: Sorry for my English.

---

### Post by rfbaum on 2009-02-15
I also have a Toshiba with the same problems, I tryed 9.04 beta 4 and it worked from the CD. Installed 9,04 with kvm and windows xp (works good except the cam)
Richard Baum

---

### Post by mikesol on 2009-03-03
Men i don't know what happened there, so I installed **Linux Mint** [http://www.linuxmint.com/]("http://www.linuxmint.com/"), runs perfect with my Toshiba, 0% of problems. I recommend you..

Greetings

---

