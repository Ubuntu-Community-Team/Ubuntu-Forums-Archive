---
title: "KDE3 and KDE4 Atheros AR242x Wireless Not Working/Working"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2009-05-01
On my laptop, when using Kubuntu 9.04 with KDE4, wireless works out of the box. When switched to Kubuntu 9.04 _Remix with KDE3_, wireless does not work.

How do I get my wireless to work in Kubuntu 9.04 Remix with KDE3? 

Looking at all the information, I can see that the biggest difference is the lshw -C network output.

KDE3 sudo lshw -C network
```

  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:36:a2:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.5 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:bb:8c:4d:30:b0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```


KDE4 sudo lshw -C network
```

  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:36:a2:b6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.5 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:3a:74:41:2d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:99:3a:17:b6:70
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```


```
 Machine Brand Info]
Brand  	HP
Series 	Pavilion
Model 	dv6815nr
Part# 	KN831UAR#ABA

```

This is the information that KDE3 sees.

KDE3 lspci
```

lspci
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
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

KDE4 lspci
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
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

 KDE3 lsusb
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

 KDE4 lsusb
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

 KDE3 lspci -nn | grep 'Wireless'
```

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

```

 KDE4 lspci -nn | grep 'Wireless'
```

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

```

KDE3 ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1e:68:36:a2:b6
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe36:a2b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:87773 (87.7 KB)  TX bytes:501555 (501.5 KB)
          Interrupt:252 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```

KDE4 ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1e:68:36:a2:b6
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe36:a2b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9566959 (9.5 MB)  TX bytes:326562 (326.5 KB)
          Interrupt:252 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1240 (1.2 KB)  TX bytes:1240 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:74:41:2d
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3A-74-41-2D-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

 KDE3 iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

 KDE4 iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

KDE3 can't scan the networks because no card appears to be available.

KDE3 lsmod
```

Module                  Size  Used by
binfmt_misc            18572  1
ppdev                  16904  0
bridge                 63904  0
stp                    11140  1 bridge
bnep                   22912  2
input_polldev          12688  0
dm_crypt               22792  0
joydev                 20864  0
lp                     19588  0
parport                49584  2 ppdev,lp
snd_hda_intel         557364  2
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0
snd_seq_oss            41984  0
snd_seq_midi           15744  0
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                64028  0
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci              16896  0
k8temp                 13440  0
serio_raw              14468  0
pcspkr                 11136  0
nvidia               8123768  28
ricoh_mmc              12544  0
sdhci                  27396  1 sdhci_pci
snd                    78792  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
video                  29204  5
output                 11648  1 video
ohci1394               42036  0
ieee1394              108288  1 ohci1394
forcedeth              68368  0
raid10                 31872  0
raid456               140064  0
async_xor              12160  1 raid456
async_memcpy           10752  1 raid456
async_tx               16636  3 raid456,async_xor,async_memcpy
xor                    13968  2 raid456,async_xor
raid1                  32512  0
raid0                  15488  0
multipath              16512  0
linear                 13440  0
fbcon                  49792  0
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
compcache              13808  1
lzo_decompress         11264  1 compcache
lzo_compress           11264  1 compcache
tlsf                   15392  1 compcache

```

 KDE3 lsmod
```

Module                  Size  Used by
ppdev                  16904  0
lp                     19588  0
parport                49584  2 ppdev,lp
bridge                 63904  0
stp                    11140  1 bridge
bnep                   22912  2
input_polldev          12688  0
snd_hda_intel         557364  2
snd_pcm_oss            52352  0
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0
snd_seq_oss            41984  0
snd_seq_midi           15744  0
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
arc4                   10240  2
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ecb                    11392  2
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 20864  0
ath5k                 116224  0
sdhci_pci              16896  0
snd                    78792  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              251144  1 ath5k
ricoh_mmc              12544  0
led_class              13064  1 ath5k
psmouse                64028  0
sdhci                  27396  1 sdhci_pci
soundcore              16800  1 snd
serio_raw              14468  0
pcspkr                 11136  0
k8temp                 13440  0
cfg80211               43168  2 ath5k,mac80211
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
video                  29204  0
output                 11648  1 video
squashfs               48656  1
aufs                  193384  1
exportfs               13440  1 aufs
nls_cp437              15104  1
isofs                  43688  1
forcedeth              68368  0
ohci1394               42036  0
ieee1394              108288  1 ohci1394
fbcon                  49792  0
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

KDE3+4 lsb_release -d
```

Description:    Ubuntu 9.04

```

 KDE3+4 uname -mr
```

2.6.28-11-generic x86_64

```

Dmesg output from both KDE4 and KDE3
[http://pastebin.ca/1409240](http://pastebin.ca/1409240)

KDE3 dmesg
```

Note: Repetitive messages from SELinux removed.
[    0.000000] BIOS EBDA/lowmem at: 0009e000/0009e000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=ba5fe699-8c31-4ea6-ac55-4374aa82be2d ro quiet splash apparmor.enabled=0 selinux=1
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
[    0.000000] last_pfn = 0xbbf50 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000091000 (usable)
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
[    0.000000] init_memory_mapping: 0000000000000000-00000000bbf50000
[    0.000000]  0000000000 - 00bbe00000 page 2M
[    0.000000]  00bbe00000 - 00bbf50000 page 4k
[    0.000000] kernel direct mapping tables up to bbf50000 @ 10000-15000
[    0.000000] last_map_addr: bbf50000 end: bbf50000
[    0.000000] RAMDISK: 37774000 - 37fefc02
[    0.000000] ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BBF5C0CE, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP BBF649BA, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT BBF5C13A, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS BBF65FC0, 0040
[    0.000000] ACPI: TCPA BBF64AAE, 0032 (r1 Phoeni  x        6040000  TL         0)
[    0.000000] ACPI: SRAT BBF64AE0, 00A0 (r1 AMD    HAMMER    6040000 AMD         1)
[    0.000000] ACPI: SSDT BBF64B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG BBF64D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET BBF64DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC BBF64DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BBF64E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC BBF64E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 00bbf50000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [0037774000 - 0037fefc02]          RAMDISK ==> [0037774000 - 0037fefc02]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000f8220] 000f8220
[    0.000000]  [ffffe20000000000-ffffe200029fffff] PMD -> [ffff880001200000-ffff880003bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000091
[    0.000000]     0: 0x00000100 -> 0x000bbf50
[    0.000000] On node 0 totalpages: 769748
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2543 pages reserved
[    0.000000]   DMA zone: 1373 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10470 pages used for memmap
[    0.000000]   DMA32 zone: 755306 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 756679
[    0.000000] Kernel command line: root=UUID=ba5fe699-8c31-4ea6-ac55-4374aa82be2d ro quiet splash apparmor.enabled=0 selinux=1
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2000.112 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 31457280 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 100000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 2979660k/3079488k available (4760k kernel code, 496k absent, 98652k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.22 BogoMIPS (lpj=8000448)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Initializing.
[    0.004000] SELinux:  Starting in permissive mode
[    0.004000] AppArmor: AppArmor disabled by boottime parameter
[    0.004000]
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] tseg: 00bbf80000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] ACPI: Core revision 20080926
[    0.004802] ACPI: Checking initramfs for custom DSDT
[    0.328057] Setting APIC routing to flat
[    0.328602] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.369519] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.372001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4000.39 BogoMIPS (lpj=8000785)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] System has AMD C1E enabled
[    0.004000] Switch to broadcast mode on CPU1
[    0.456219] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.456237] Brought up 2 CPUs
[    0.456239] Total of 2 processors activated (8000.61 BogoMIPS).
[    0.456325] CPU0 attaching sched-domain:
[    0.456328]  domain 0: span 0-1 level CPU
[    0.456330]   groups: 0 1
[    0.456335] CPU1 attaching sched-domain:
[    0.456336]  domain 0: span 0-1 level CPU
[    0.456338]   groups: 1 0
[    0.456405] Switch to broadcast mode on CPU0
[    0.456405] net_namespace: 1400 bytes
[    0.456405] Booting paravirtualized kernel on bare hardware
[    0.456405] Time:  5:44:16  Date: 05/01/09
[    0.456405] regulator: core version 0.5
[    0.456405] NET: Registered protocol family 16
[    0.456405] node 0 link 0: io port [1000, fffff]
[    0.456405] TOM: 00000000c0000000 aka 3072M
[    0.456405] node 0 link 0: mmio [a0000, bffff]
[    0.456405] node 0 link 0: mmio [c0000000, dfffffff]
[    0.456405] node 0 link 0: mmio [e0000000, efffffff]
[    0.456405] node 0 link 0: mmio [f0000000, fe0bffff]
[    0.456405] bus: [00,ff] on node 0 link 0
[    0.456405] bus: 00 index 0 io port: [0, ffff]
[    0.456405] bus: 00 index 1 mmio: [a0000, bffff]
[    0.456405] bus: 00 index 2 mmio: [c0000000, fcffffffff]
[    0.456405] ACPI: bus type pci registered
[    0.456405] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.456405] PCI: MCFG area at e0000000 reserved in E820
[    0.456588] PCI: Using MMCONFIG at e0000000 - e04fffff
[    0.456590] PCI: Using configuration type 1 for base access
[    0.457190] ACPI: EC: Look up EC in DSDT
[    0.461728] ACPI: BIOS _OSI(Linux) query ignored
[    0.462666] ACPI: Interpreter enabled
[    0.462669] ACPI: (supports S0 S3 S4 S5)
[    0.462686] ACPI: Using IOAPIC for interrupt routing
[    0.460023] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.468771] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.468774] ACPI: EC: driver started in interrupt mode
[    0.468990] ACPI: No dock devices found.
[    0.469000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.469184] pci 0000:00:01.1: reg 10 io port: [0x3080-0x30bf]
[    0.469194] pci 0000:00:01.1: reg 20 io port: [0x3040-0x307f]
[    0.469198] pci 0000:00:01.1: reg 24 io port: [0x3000-0x303f]
[    0.469209] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.469214] pci 0000:00:01.1: PME# disabled
[    0.469266] pci 0000:00:01.3: reg 10 32bit mmio: [0xf6200000-0xf627ffff]
[    0.469338] pci 0000:00:02.0: reg 10 32bit mmio: [0xf6486000-0xf6486fff]
[    0.469356] pci 0000:00:02.0: supports D1 D2
[    0.469358] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469361] pci 0000:00:02.0: PME# disabled
[    0.469382] pci 0000:00:02.1: reg 10 32bit mmio: [0xf6489000-0xf64890ff]
[    0.469401] pci 0000:00:02.1: supports D1 D2
[    0.469403] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469406] pci 0000:00:02.1: PME# disabled
[    0.469430] pci 0000:00:04.0: reg 10 32bit mmio: [0xf6487000-0xf6487fff]
[    0.469447] pci 0000:00:04.0: supports D1 D2
[    0.469449] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469452] pci 0000:00:04.0: PME# disabled
[    0.469473] pci 0000:00:04.1: reg 10 32bit mmio: [0xf6489400-0xf64894ff]
[    0.469492] pci 0000:00:04.1: supports D1 D2
[    0.469494] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469497] pci 0000:00:04.1: PME# disabled
[    0.469531] pci 0000:00:06.0: reg 20 io port: [0x30c0-0x30cf]
[    0.469563] pci 0000:00:07.0: reg 10 32bit mmio: [0xf6480000-0xf6483fff]
[    0.469581] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.469584] pci 0000:00:07.0: PME# disabled
[    0.469635] pci 0000:00:09.0: reg 10 io port: [0x30f0-0x30f7]
[    0.469639] pci 0000:00:09.0: reg 14 io port: [0x30e4-0x30e7]
[    0.469642] pci 0000:00:09.0: reg 18 io port: [0x30e8-0x30ef]
[    0.469645] pci 0000:00:09.0: reg 1c io port: [0x30e0-0x30e3]
[    0.469649] pci 0000:00:09.0: reg 20 io port: [0x30d0-0x30df]
[    0.469652] pci 0000:00:09.0: reg 24 32bit mmio: [0xf6484000-0xf6485fff]
[    0.469688] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf6488000-0xf6488fff]
[    0.469692] pci 0000:00:0a.0: reg 14 io port: [0x30f8-0x30ff]
[    0.469695] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf6489c00-0xf6489cff]
[    0.469699] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf6489800-0xf648980f]
[    0.469710] pci 0000:00:0a.0: supports D1 D2
[    0.469712] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469716] pci 0000:00:0a.0: PME# disabled
[    0.469741] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469743] pci 0000:00:0c.0: PME# disabled
[    0.469766] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469769] pci 0000:00:0d.0: PME# disabled
[    0.469789] pci 0000:00:12.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.469793] pci 0000:00:12.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.469798] pci 0000:00:12.0: reg 1c 64bit mmio: [0xf4000000-0xf4ffffff]
[    0.469803] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.469896] pci 0000:02:05.0: reg 10 32bit mmio: [0x000000-0x0007ff]
[    0.469922] pci 0000:02:05.0: supports D1 D2
[    0.469924] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469927] pci 0000:02:05.0: PME# disabled
[    0.469950] pci 0000:02:05.1: reg 10 32bit mmio: [0xf6100800-0xf61008ff]
[    0.469975] pci 0000:02:05.1: supports D1 D2
[    0.469977] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.469980] pci 0000:02:05.1: PME# disabled
[    0.470003] pci 0000:02:05.2: reg 10 32bit mmio: [0xf6100c00-0xf6100cff]
[    0.470029] pci 0000:02:05.2: supports D1 D2
[    0.470030] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470034] pci 0000:02:05.2: PME# disabled
[    0.470057] pci 0000:02:05.3: reg 10 32bit mmio: [0xf6101000-0xf61010ff]
[    0.470082] pci 0000:02:05.3: supports D1 D2
[    0.470084] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470087] pci 0000:02:05.3: PME# disabled
[    0.470113] pci 0000:02:05.4: reg 10 32bit mmio: [0xf6101400-0xf61014ff]
[    0.470138] pci 0000:02:05.4: supports D1 D2
[    0.470140] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.470143] pci 0000:02:05.4: PME# disabled
[    0.470173] pci 0000:00:08.0: transparent bridge
[    0.470177] pci 0000:00:08.0: bridge 32bit mmio: [0xf6100000-0xf61fffff]
[    0.470212] pci 0000:00:0c.0: bridge io port: [0x4000-0x4fff]
[    0.470215] pci 0000:00:0c.0: bridge 32bit mmio: [0xf2000000-0xf3ffffff]
[    0.470218] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.470252] pci 0000:03:00.0: reg 10 64bit mmio: [0xf6000000-0xf600ffff]
[    0.470318] pci 0000:00:0d.0: bridge 32bit mmio: [0xf6000000-0xf60fffff]
[    0.470327] bus 00 -> node 0
[    0.470333] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.470439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.470464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.470501] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.504385] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.504617] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.504852] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.505082] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.505311] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.505541] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.505769] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.505998] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.506226] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.506454] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.506683] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.506919] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.507148] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.507377] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.507605] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.507835] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.508076] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.508310] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.508544] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.508789] ACPI: WMI: Mapper loaded
[    0.512114] SCSI subsystem initialized
[    0.512121] libata version 3.00 loaded.
[    0.512121] usbcore: registered new interface driver usbfs
[    0.512121] usbcore: registered new interface driver hub
[    0.512121] usbcore: registered new device driver usb
[    0.512121] PCI: Using ACPI for IRQ routing
[    0.524010] Bluetooth: Core ver 2.13
[    0.528014] NET: Registered protocol family 31
[    0.528014] Bluetooth: HCI device and connection manager initialized
[    0.528017] Bluetooth: HCI socket layer initialized
[    0.528019] NET: Registered protocol family 8
[    0.528020] NET: Registered protocol family 20
[    0.528033] NetLabel: Initializing
[    0.528034] NetLabel:  domain hash size = 128
[    0.528036] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.528050] NetLabel:  unlabeled traffic allowed by default
[    0.528216] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.528220] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.540021] Switched to high resolution mode on CPU 0
[    0.540032] Switched to high resolution mode on CPU 1
[    0.545024] pnp: PnP ACPI init
[    0.545035] ACPI: bus type pnp registered
[    0.549397] pnp: PnP ACPI: found 12 devices
[    0.549399] ACPI: ACPI bus type pnp unregistered
[    0.549409] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.549415] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.549418] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.549420] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.549422] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.549425] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.549427] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.549433] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.549435] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.549447] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.549450] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.549452] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.549455] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.549457] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.554166] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.554168] pci 0000:00:08.0:   IO window: disabled
[    0.554172] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.554174] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.554178] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.554180] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.554183] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.554186] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.554189] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.554191] pci 0000:00:0d.0:   IO window: disabled
[    0.554194] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.554196] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.554204] pci 0000:00:08.0: setting latency timer to 64
[    0.554209] pci 0000:00:0c.0: setting latency timer to 64
[    0.554213] pci 0000:00:0d.0: setting latency timer to 64
[    0.554216] bus: 00 index 0 io port: [0x00-0xffff]
[    0.554218] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.554221] bus: 02 index 0 mmio: [0x0-0x0]
[    0.554222] bus: 02 index 1 mmio: [0xf6100000-0xf61fffff]
[    0.554224] bus: 02 index 2 mmio: [0x0-0x0]
[    0.554226] bus: 02 index 3 io port: [0x00-0xffff]
[    0.554228] bus: 02 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.554230] bus: 04 index 0 io port: [0x4000-0x4fff]
[    0.554231] bus: 04 index 1 mmio: [0xf2000000-0xf3ffffff]
[    0.554234] bus: 04 index 2 mmio: [0xf0000000-0xf1ffffff]
[    0.554235] bus: 04 index 3 mmio: [0x0-0x0]
[    0.554237] bus: 03 index 0 mmio: [0x0-0x0]
[    0.554239] bus: 03 index 1 mmio: [0xf6000000-0xf60fffff]
[    0.554240] bus: 03 index 2 mmio: [0x0-0x0]
[    0.554242] bus: 03 index 3 mmio: [0x0-0x0]
[    0.554253] NET: Registered protocol family 2
[    0.593074] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.594020] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.597258] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.598045] TCP: Hash tables configured (established 262144 bind 65536)
[    0.598048] TCP reno registered
[    0.609125] NET: Registered protocol family 1
[    0.609268] checking if image is initramfs... it is
[    1.273603] Freeing initrd memory: 8687k freed
[    1.280058] Simple Boot Flag at 0x36 set to 0x80
[    1.280392] audit: initializing netlink socket (disabled)
[    1.280409] type=2000 audit(1241156656.280:1): initialized
[    1.288573] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.289926] VFS: Disk quotas dquot_6.5.1
[    1.289990] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.290619] fuse init (API version 7.10)
[    1.290700] msgmni has been set to 5837
[    1.290790] SELinux:  Registering netfilter hooks
[    1.291012] alg: No test for stdrng (krng)
[    1.291026] io scheduler noop registered
[    1.291028] io scheduler anticipatory registered
[    1.291030] io scheduler deadline registered
[    1.291076] io scheduler cfq registered (default)
[    1.291106] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.291277] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.291291] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.291307] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.291323] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.291338] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.291353] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.291367] pci 0000:00:12.0: Boot video device
[    1.297594] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.297618] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.297634] pcieport-driver 0000:00:0c.0: irq 2303 for MSI/MSI-X
[    1.297641] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.297658] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.297701] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.297721] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.297733] pcieport-driver 0000:00:0d.0: irq 2302 for MSI/MSI-X
[    1.297739] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.297752] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.297799] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.297808] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.299165] ACPI: AC Adapter [ACAD] (on-line)
[    1.576930] ACPI: Battery Slot [BAT0] (battery present)
[    1.577021] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.577024] ACPI: Power Button (FF) [PWRF]
[    1.577068] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.577071] ACPI: Sleep Button (CM) [SLPB]
[    1.577123] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.578203] ACPI: Lid Switch [LID]
[    1.578265] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.578267] ACPI: Power Button (CM) [PWRB]
[    1.578605] ACPI: processor limited to max C-state 1
[    1.578629] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.578663] processor ACPI_CPU:00: registered as cooling_device0
[    1.578667] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.578767] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.578790] processor ACPI_CPU:01: registered as cooling_device1
[    1.578794] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.843536] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.877275] Linux agpgart interface v0.103
[    1.877285] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.878255] brd: module loaded
[    1.878607] loop: module loaded
[    1.878694] Fixed MDIO Bus: probed
[    1.878700] PPP generic driver version 2.4.2
[    1.878757] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.878790] Driver 'sd' needs updating - please use bus_type methods
[    1.878799] Driver 'sr' needs updating - please use bus_type methods
[    1.878845] ahci 0000:00:09.0: version 3.0
[    1.879240] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    1.879252] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    1.879304] ahci 0000:00:09.0: irq 2301 for MSI/MSI-X
[    1.879385] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.879389] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part
[    1.879392] ahci 0000:00:09.0: setting latency timer to 64
[    1.879890] scsi0 : ahci
[    1.880060] scsi1 : ahci
[    1.880142] scsi2 : ahci
[    1.880218] scsi3 : ahci
[    1.880325] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 2301
[    1.880328] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 2301
[    1.880330] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 2301
[    1.880333] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 2301
[    2.584031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.584915] ata1.00: ATA-7: HITACHI HTS541680J9SA00, SB2IC7UP, max UDMA/100
[    2.584917] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.585962] ata1.00: configured for UDMA/100
[    2.904026] ata2: SATA link down (SStatus 0 SControl 300)
[    3.224025] ata3: SATA link down (SStatus 0 SControl 300)
[    3.544025] ata4: SATA link down (SStatus 0 SControl 300)
[    3.544131] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54168 SB2I PQ: 0 ANSI: 5
[    3.544235] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    3.544252] sd 0:0:0:0: [sda] Write Protect is off
[    3.544254] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.544279] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.544364] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    3.544378] sd 0:0:0:0: [sda] Write Protect is off
[    3.544380] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.544404] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.544408]  sda: sda1 sda2 sda3 < sda5 >
[    3.949681] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.949731] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.949966] pata_amd 0000:00:06.0: version 0.3.10
[    3.950013] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.950117] scsi4 : pata_amd
[    3.950199] scsi5 : pata_amd
[    3.950570] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    3.950572] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    4.112303] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[    4.112323] ata5: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    4.128247] ata5.00: configured for MWDMA2
[    4.130517] ata6: port disabled. ignoring.
[    4.130551] isa bounce pool size: 16 pages
[    4.133560] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[    4.144415] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.144418] Uniform CD-ROM driver Revision: 3.20
[    4.144525] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    4.144572] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    4.145020] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.145410] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    4.145420] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    4.145439] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    4.145442] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.145519] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    4.145560] ehci_hcd 0000:00:02.1: debug port 1
[    4.145564] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    4.145587] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    4.156028] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    4.156098] usb usb1: configuration #1 chosen from 1 choice
[    4.156124] hub 1-0:1.0: USB hub found
[    4.156133] hub 1-0:1.0: 7 ports detected
[    4.156587] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    4.156590] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    4.156600] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.156603] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.156647] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    4.156676] ehci_hcd 0000:00:04.1: debug port 1
[    4.156679] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    4.156684] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    4.168026] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.168086] usb usb2: configuration #1 chosen from 1 choice
[    4.168113] hub 2-0:1.0: USB hub found
[    4.168120] hub 2-0:1.0: 2 ports detected
[    4.168206] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.168558] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    4.168566] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    4.168578] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.168580] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.168626] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    4.168650] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    4.226064] usb usb3: configuration #1 chosen from 1 choice
[    4.226090] hub 3-0:1.0: USB hub found
[    4.226099] hub 3-0:1.0: 7 ports detected
[    4.226516] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    4.226519] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    4.226529] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.226532] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.226581] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.226592] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    4.282063] usb usb4: configuration #1 chosen from 1 choice
[    4.282086] hub 4-0:1.0: USB hub found
[    4.282095] hub 4-0:1.0: 2 ports detected
[    4.282175] uhci_hcd: USB Universal Host Controller Interface driver
[    4.282254] usbcore: registered new interface driver libusual
[    4.282288] usbcore: registered new interface driver usbserial
[    4.282299] USB Serial support registered for generic
[    4.282312] usbcore: registered new interface driver usbserial_generic
[    4.282314] usbserial: USB Serial Driver core
[    4.282356] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.309317] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.309323] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.321050] mice: PS/2 mouse device common for all mice
[    4.381094] rtc_cmos 00:07: RTC can wake from S4
[    4.381135] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    4.381172] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.381233] device-mapper: uevent: version 1.0.3
[    4.381347] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.381521] device-mapper: multipath: version 1.0.5 loaded
[    4.381524] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.381766] cpuidle: using governor ladder
[    4.381828] cpuidle: using governor menu
[    4.382236] TCP cubic registered
[    4.382304] NET: Registered protocol family 10
[    4.382674] lo: Disabled Privacy Extensions
[    4.382942] NET: Registered protocol family 17
[    4.382962] Bluetooth: L2CAP ver 2.11
[    4.382964] Bluetooth: L2CAP socket layer initialized
[    4.382966] Bluetooth: SCO (Voice Link) ver 0.6
[    4.382968] Bluetooth: SCO socket layer initialized
[    4.383028] Bluetooth: RFCOMM socket layer initialized
[    4.383036] Bluetooth: RFCOMM TTY layer initialized
[    4.383038] Bluetooth: RFCOMM ver 1.10
[    4.383084] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[    4.383138] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x11
[    4.383141] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[    4.383143] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[    4.383144] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    4.383285] registered taskstats version 1
[    4.383462]   Magic number: 9:279:718
[    4.383575] rtc_cmos 00:07: setting system clock to 2009-05-01 05:44:20 UTC (1241156660)
[    4.383578] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.383579] EDD information not available.
[    4.383623] Freeing unused kernel memory: 536k freed
[    4.383899] Write protecting the kernel read-only data: 6708k
[    4.398575] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.462387] compcache: Compressed swap size set to: 747392 KB
[    4.464664] TLSF: pool: ffffc2000007a000, init_size=16384, max_size=0, grow_size=16384
[    4.554067] md: linear personality registered for level -1
[    4.556775] md: multipath personality registered for level -4
[    4.559171] md: raid0 personality registered for level 0
[    4.562663] md: raid1 personality registered for level 1
[    4.565000] xor: automatically using best checksumming function: generic_sse
[    4.581003]    generic_sse:  5979.000 MB/sec
[    4.581005] xor: using function: generic_sse (5979.000 MB/sec)
[    4.582175] async_tx: api initialized (async)
[    4.653011] raid6: int64x1   1645 MB/s
[    4.721021] raid6: int64x2   2271 MB/s
[    4.789034] raid6: int64x4   1822 MB/s
[    4.857018] raid6: int64x8   1697 MB/s
[    4.925015] raid6: sse2x1    2774 MB/s
[    4.993014] raid6: sse2x2    3706 MB/s
[    5.061008] raid6: sse2x4    3863 MB/s
[    5.061009] raid6: using algorithm sse2x4 (3863 MB/s)
[    5.061014] md: raid6 personality registered for level 6
[    5.061015] md: raid5 personality registered for level 5
[    5.061017] md: raid4 personality registered for level 4
[    5.069106] md: raid10 personality registered for level 10
[    5.416469] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    5.416896] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    5.416908] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    5.416913] forcedeth 0000:00:0a.0: setting latency timer to 64
[    5.433039] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[    5.433455] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    5.433469] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    5.485257] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.595723] Adding 747388k swap on /dev/ramzswap0.  Priority:100 extents:1 across:747388k
[    5.937036] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:36:a2:b6
[    5.937040] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    6.126096] PM: Starting manual resume from disk
[    6.126100] PM: Resume from partition 8:5
[    6.126102] PM: Checking hibernation image.
[    6.126264] PM: Resume from disk failed.
[    6.147037] EXT4-fs: barriers enabled
[    6.159745] kjournald2 starting.  Commit interval 5 seconds
[    6.159756] EXT4-fs: delayed allocation enabled
[    6.159758] EXT4-fs: file extents enabled
[    6.160962] EXT4-fs: mballoc enabled
[    6.160966] EXT4-fs: mounted filesystem with ordered data mode.
[    6.620466] SELinux: 8192 avtab hash slots, 22937 rules.
[    6.623691] SELinux: 8192 avtab hash slots, 22937 rules.
[    6.623991] SELinux:  6 users, 7 roles, 1122 types, 35 bools, 1 sens, 256 cats
[    6.623995] SELinux:  74 classes, 22937 rules
[    6.624901] SELinux:  Completing initialization.
[    6.624903] SELinux:  Setting up existing superblocks.
[    6.624913] SELinux: initialized (dev sda1, type ext4), uses xattr
[    6.624966] SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
[    6.626557] SELinux: initialized (dev usbfs, type usbfs), uses genfs_contexts
[    6.626569] SELinux: initialized (dev selinuxfs, type selinuxfs), uses genfs_contexts
[    6.626605] SELinux: initialized (dev mqueue, type mqueue), uses transition SIDs
[    6.626613] SELinux: initialized (dev hugetlbfs, type hugetlbfs), uses genfs_contexts
[    6.626618] SELinux: initialized (dev devpts, type devpts), uses transition SIDs
[    6.626625] SELinux: initialized (dev inotifyfs, type inotifyfs), uses genfs_contexts
[    6.626629] SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
[    6.626636] SELinux: initialized (dev anon_inodefs, type anon_inodefs), uses genfs_contexts
[    6.626640] SELinux: initialized (dev pipefs, type pipefs), uses task SIDs
[    6.626646] SELinux: initialized (dev debugfs, type debugfs), uses genfs_contexts
[    6.626706] SELinux: initialized (dev sockfs, type sockfs), uses task SIDs
[    6.626714] SELinux: initialized (dev proc, type proc), uses genfs_contexts
[    6.626726] SELinux: initialized (dev bdev, type bdev), uses genfs_contexts
[    6.626732] SELinux: initialized (dev rootfs, type rootfs), uses genfs_contexts
[    6.627055] SELinux: initialized (dev sysfs, type sysfs), uses genfs_contexts
[    6.663174] type=1403 audit(1241156662.777:2): policy loaded auid=4294967295 ses=4294967295
[    6.765472] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00ce0ecb00]
[    7.761390] SELinux: initialized (dev fusectl, type fusectl), uses genfs_contexts
[   11.360844] udev: starting version 141
[   11.687853] acpi device:25: registered as cooling_device2
[   11.688167] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
[   11.721207] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   12.225088] sdhci: Secure Digital Host Controller Interface driver
[   12.225092] sdhci: Copyright(c) Pierre Ossman
[   12.241898] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.241902] ricoh-mmc: Copyright(c) Philip Langdale
[   12.241946] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   12.241961] ricoh-mmc: Controller is now disabled.
[   12.641820] nvidia: module license 'NVIDIA' taints kernel.
[   12.811459] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   12.857603] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   12.858036] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   12.858049] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   12.861282] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   12.901069] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   12.901083] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   12.901090] nvidia 0000:00:12.0: setting latency timer to 64
[   12.901982] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   13.061001] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.073610] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   13.073623] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   13.073720] HDA Intel 0000:00:07.0: setting latency timer to 64
[   13.571429] SELinux: initialized (dev tmpfs, type tmpfs), uses transition SIDs
[   13.720916] lp: driver loaded but no devices found
[   13.831242] Adding 1004020k swap on /dev/sda5.  Priority:-1 extents:1 across:1004020k
[   14.110699] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   14.185926] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   14.393218] EXT4 FS on sda1, internal journal on sda1:8
[   15.438401] kjournald starting.  Commit interval 5 seconds
[   15.438570] EXT3 FS on sda2, internal journal
[   15.438575] EXT3-fs: mounted filesystem with ordered data mode.
[   15.455013] SELinux: initialized (dev sda2, type ext3), uses xattr
[   17.209052] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1b6
[   20.500028] Clocksource tsc unstable (delta = -299173557 ns)
[   22.406712] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1ff
[   22.508485] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.508493] Bluetooth: BNEP filters: protocol multicast
[   22.567513] Bridge firewalling registered
[   23.239567] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1b6
[   23.347026] ppdev: user-space parallel port driver
[   24.911388] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1b6
[   25.300568] SELinux: initialized (dev binfmt_misc, type binfmt_misc), uses genfs_contexts
[   26.275651] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1b6
[   26.886090] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
[   26.977505] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1b6
[   34.249934] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1b6
[   34.459951] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1b6
[   38.612025] eth0: no IPv6 routers present
[   53.964166] SELinux: WARNING: inside open_file_mask_to_av with unknown mode:c1ff

```

KDE4 dmesg
```

[    0.000000] BIOS EBDA/lowmem at: 0009e000/0009e000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
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
[    0.000000] last_pfn = 0xbbf50 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000008000 (usable)
[    0.000000]  modified: 0000000000008000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000091000 (usable)
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
[    0.000000] init_memory_mapping: 0000000000000000-00000000bbf50000
[    0.000000]  0000000000 - 00bbe00000 page 2M
[    0.000000]  00bbe00000 - 00bbf50000 page 4k
[    0.000000] kernel direct mapping tables up to bbf50000 @ 10000-15000
[    0.000000] last_map_addr: bbf50000 end: bbf50000
[    0.000000] RAMDISK: 7f836000 - 7ffffae5
[    0.000000] ACPI: RSDP 000F8250, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BBF5C0CE, 006C (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP BBF649BA, 00F4 (r3 NVIDIA MCP67-M   6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT BBF5C13A, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS BBF65FC0, 0040
[    0.000000] ACPI: TCPA BBF64AAE, 0032 (r1 Phoeni  x        6040000  TL         0)
[    0.000000] ACPI: SRAT BBF64AE0, 00A0 (r1 AMD    HAMMER    6040000 AMD         1)
[    0.000000] ACPI: SSDT BBF64B80, 0206 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: MCFG BBF64D86, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: HPET BBF64DC2, 0038 (r1 PTLTD  HPETTBL   6040000  LTP        1)
[    0.000000] ACPI: APIC BBF64DFA, 0068 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BBF64E62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC BBF64E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 00bbf50000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [007f836000 - 007ffffae5]          RAMDISK ==> [007f836000 - 007ffffae5]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000f8220] 000f8220
[    0.000000]  [ffffe20000000000-ffffe200029fffff] PMD -> [ffff880001200000-ffff880003bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x00000008
[    0.000000]     0: 0x00000010 -> 0x00000091
[    0.000000]     0: 0x00000100 -> 0x000bbf50
[    0.000000] On node 0 totalpages: 769748
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2543 pages reserved
[    0.000000]   DMA zone: 1373 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10470 pages used for memmap
[    0.000000]   DMA32 zone: 755306 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000008000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 756679
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/kubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2000.080 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 31457280 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 100000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 2980428k/3079488k available (4760k kernel code, 496k absent, 97940k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.16 BogoMIPS (lpj=8000320)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] tseg: 00bbf80000
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using C1E aware idle routine
[    0.004000] ACPI: Core revision 20080926
[    0.004776] ACPI: Checking initramfs for custom DSDT
[    0.304056] Setting APIC routing to flat
[    0.304601] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.345842] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.348001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4000.38 BogoMIPS (lpj=8000775)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] System has AMD C1E enabled
[    0.004000] Switch to broadcast mode on CPU1
[    0.432214] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.432227] Brought up 2 CPUs
[    0.432229] Total of 2 processors activated (8000.54 BogoMIPS).
[    0.432315] CPU0 attaching sched-domain:
[    0.432317]  domain 0: span 0-1 level CPU
[    0.432319]   groups: 0 1
[    0.432324] CPU1 attaching sched-domain:
[    0.432326]  domain 0: span 0-1 level CPU
[    0.432327]   groups: 1 0
[    0.432395] Switch to broadcast mode on CPU0
[    0.432395] net_namespace: 1400 bytes
[    0.432395] Booting paravirtualized kernel on bare hardware
[    0.432395] Time:  6:53:28  Date: 05/01/09
[    0.432395] regulator: core version 0.5
[    0.432395] NET: Registered protocol family 16
[    0.432395] node 0 link 0: io port [1000, fffff]
[    0.432395] TOM: 00000000c0000000 aka 3072M
[    0.432395] node 0 link 0: mmio [a0000, bffff]
[    0.432395] node 0 link 0: mmio [c0000000, dfffffff]
[    0.432395] node 0 link 0: mmio [e0000000, efffffff]
[    0.432395] node 0 link 0: mmio [f0000000, fe0bffff]
[    0.432395] bus: [00,ff] on node 0 link 0
[    0.432395] bus: 00 index 0 io port: [0, ffff]
[    0.432395] bus: 00 index 1 mmio: [a0000, bffff]
[    0.432395] bus: 00 index 2 mmio: [c0000000, fcffffffff]
[    0.432395] ACPI: bus type pci registered
[    0.432395] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 4
[    0.432395] PCI: MCFG area at e0000000 reserved in E820
[    0.432581] PCI: Using MMCONFIG at e0000000 - e04fffff
[    0.432583] PCI: Using configuration type 1 for base access
[    0.433173] ACPI: EC: Look up EC in DSDT
[    0.437657] ACPI: BIOS _OSI(Linux) query ignored
[    0.438591] ACPI: Interpreter enabled
[    0.438594] ACPI: (supports S0 S3 S4 S5)
[    0.438611] ACPI: Using IOAPIC for interrupt routing
[    0.436023] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.444328] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.444331] ACPI: EC: driver started in interrupt mode
[    0.444547] ACPI: No dock devices found.
[    0.444557] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.444742] pci 0000:00:01.1: reg 10 io port: [0x3080-0x30bf]
[    0.444752] pci 0000:00:01.1: reg 20 io port: [0x3040-0x307f]
[    0.444756] pci 0000:00:01.1: reg 24 io port: [0x3000-0x303f]
[    0.444766] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.444772] pci 0000:00:01.1: PME# disabled
[    0.444824] pci 0000:00:01.3: reg 10 32bit mmio: [0xf6200000-0xf627ffff]
[    0.444897] pci 0000:00:02.0: reg 10 32bit mmio: [0xf6486000-0xf6486fff]
[    0.444914] pci 0000:00:02.0: supports D1 D2
[    0.444916] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444919] pci 0000:00:02.0: PME# disabled
[    0.444940] pci 0000:00:02.1: reg 10 32bit mmio: [0xf6489000-0xf64890ff]
[    0.444959] pci 0000:00:02.1: supports D1 D2
[    0.444961] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444964] pci 0000:00:02.1: PME# disabled
[    0.444988] pci 0000:00:04.0: reg 10 32bit mmio: [0xf6487000-0xf6487fff]
[    0.445006] pci 0000:00:04.0: supports D1 D2
[    0.445007] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445010] pci 0000:00:04.0: PME# disabled
[    0.445032] pci 0000:00:04.1: reg 10 32bit mmio: [0xf6489400-0xf64894ff]
[    0.445051] pci 0000:00:04.1: supports D1 D2
[    0.445053] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445056] pci 0000:00:04.1: PME# disabled
[    0.445090] pci 0000:00:06.0: reg 20 io port: [0x30c0-0x30cf]
[    0.445121] pci 0000:00:07.0: reg 10 32bit mmio: [0xf6480000-0xf6483fff]
[    0.445139] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.445142] pci 0000:00:07.0: PME# disabled
[    0.445194] pci 0000:00:09.0: reg 10 io port: [0x30f0-0x30f7]
[    0.445197] pci 0000:00:09.0: reg 14 io port: [0x30e4-0x30e7]
[    0.445201] pci 0000:00:09.0: reg 18 io port: [0x30e8-0x30ef]
[    0.445204] pci 0000:00:09.0: reg 1c io port: [0x30e0-0x30e3]
[    0.445207] pci 0000:00:09.0: reg 20 io port: [0x30d0-0x30df]
[    0.445211] pci 0000:00:09.0: reg 24 32bit mmio: [0xf6484000-0xf6485fff]
[    0.445247] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf6488000-0xf6488fff]
[    0.445251] pci 0000:00:0a.0: reg 14 io port: [0x30f8-0x30ff]
[    0.445254] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf6489c00-0xf6489cff]
[    0.445258] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf6489800-0xf648980f]
[    0.445269] pci 0000:00:0a.0: supports D1 D2
[    0.445271] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445275] pci 0000:00:0a.0: PME# disabled
[    0.445301] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445303] pci 0000:00:0c.0: PME# disabled
[    0.445326] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445328] pci 0000:00:0d.0: PME# disabled
[    0.445348] pci 0000:00:12.0: reg 10 32bit mmio: [0xf5000000-0xf5ffffff]
[    0.445353] pci 0000:00:12.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.445358] pci 0000:00:12.0: reg 1c 64bit mmio: [0xf4000000-0xf4ffffff]
[    0.445362] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.445456] pci 0000:02:05.0: reg 10 32bit mmio: [0x000000-0x0007ff]
[    0.445482] pci 0000:02:05.0: supports D1 D2
[    0.445484] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445487] pci 0000:02:05.0: PME# disabled
[    0.445510] pci 0000:02:05.1: reg 10 32bit mmio: [0xf6100800-0xf61008ff]
[    0.445536] pci 0000:02:05.1: supports D1 D2
[    0.445537] pci 0000:02:05.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445541] pci 0000:02:05.1: PME# disabled
[    0.445564] pci 0000:02:05.2: reg 10 32bit mmio: [0xf6100c00-0xf6100cff]
[    0.445589] pci 0000:02:05.2: supports D1 D2
[    0.445591] pci 0000:02:05.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445595] pci 0000:02:05.2: PME# disabled
[    0.445618] pci 0000:02:05.3: reg 10 32bit mmio: [0xf6101000-0xf61010ff]
[    0.445644] pci 0000:02:05.3: supports D1 D2
[    0.445645] pci 0000:02:05.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445649] pci 0000:02:05.3: PME# disabled
[    0.445674] pci 0000:02:05.4: reg 10 32bit mmio: [0xf6101400-0xf61014ff]
[    0.445700] pci 0000:02:05.4: supports D1 D2
[    0.445701] pci 0000:02:05.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445705] pci 0000:02:05.4: PME# disabled
[    0.445734] pci 0000:00:08.0: transparent bridge
[    0.445738] pci 0000:00:08.0: bridge 32bit mmio: [0xf6100000-0xf61fffff]
[    0.445773] pci 0000:00:0c.0: bridge io port: [0x4000-0x4fff]
[    0.445776] pci 0000:00:0c.0: bridge 32bit mmio: [0xf2000000-0xf3ffffff]
[    0.445779] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.445813] pci 0000:03:00.0: reg 10 64bit mmio: [0xf6000000-0xf600ffff]
[    0.445879] pci 0000:00:0d.0: bridge 32bit mmio: [0xf6000000-0xf60fffff]
[    0.445888] bus 00 -> node 0
[    0.445894] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.445997] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.446023] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.446060] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.479914] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *10
[    0.480158] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[    0.480393] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *0, disabled.
[    0.480623] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[    0.480852] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[    0.481081] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[    0.481310] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *0, disabled.
[    0.481538] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *10
[    0.481767] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[    0.481995] ACPI: PCI Interrupt Link [LUS0] (IRQs 18) *11
[    0.482224] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[    0.482459] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *11
[    0.482688] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *10
[    0.482918] ACPI: PCI Interrupt Link [LGPU] (IRQs 16) *10
[    0.483146] ACPI: PCI Interrupt Link [LPID] (IRQs 22) *0, disabled.
[    0.483376] ACPI: PCI Interrupt Link [LSI0] (IRQs 23) *11
[    0.483605] ACPI: PCI Interrupt Link [Z018] (IRQs 18) *5
[    0.483840] ACPI: PCI Interrupt Link [Z019] (IRQs 22) *10
[    0.484087] ACPI: PCI Interrupt Link [LPMU] (IRQs *11)
[    0.484335] ACPI: WMI: Mapper loaded
[    0.488112] SCSI subsystem initialized
[    0.488120] libata version 3.00 loaded.
[    0.488120] usbcore: registered new interface driver usbfs
[    0.488120] usbcore: registered new interface driver hub
[    0.488120] usbcore: registered new device driver usb
[    0.488120] PCI: Using ACPI for IRQ routing
[    0.500010] Bluetooth: Core ver 2.13
[    0.504013] NET: Registered protocol family 31
[    0.504014] Bluetooth: HCI device and connection manager initialized
[    0.504017] Bluetooth: HCI socket layer initialized
[    0.504019] NET: Registered protocol family 8
[    0.504020] NET: Registered protocol family 20
[    0.504033] NetLabel: Initializing
[    0.504034] NetLabel:  domain hash size = 128
[    0.504036] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.504050] NetLabel:  unlabeled traffic allowed by default
[    0.504218] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.504222] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.508082] AppArmor: AppArmor Filesystem Enabled
[    0.516021] Switched to high resolution mode on CPU 0
[    0.516034] Switched to high resolution mode on CPU 1
[    0.521025] pnp: PnP ACPI init
[    0.521035] ACPI: bus type pnp registered
[    0.525837] pnp: PnP ACPI: found 12 devices
[    0.525839] ACPI: ACPI bus type pnp unregistered
[    0.525849] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.525855] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.525857] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.525860] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.525862] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.525865] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.525867] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.525872] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.525875] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.525883] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.525885] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.525888] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.525890] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.525893] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.530596] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.530599] pci 0000:00:08.0:   IO window: disabled
[    0.530602] pci 0000:00:08.0:   MEM window: 0xf6100000-0xf61fffff
[    0.530605] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.530609] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.530611] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.530614] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.530616] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.530620] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.530621] pci 0000:00:0d.0:   IO window: disabled
[    0.530624] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.530626] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.530634] pci 0000:00:08.0: setting latency timer to 64
[    0.530639] pci 0000:00:0c.0: setting latency timer to 64
[    0.530644] pci 0000:00:0d.0: setting latency timer to 64
[    0.530647] bus: 00 index 0 io port: [0x00-0xffff]
[    0.530649] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.530651] bus: 02 index 0 mmio: [0x0-0x0]
[    0.530652] bus: 02 index 1 mmio: [0xf6100000-0xf61fffff]
[    0.530654] bus: 02 index 2 mmio: [0x0-0x0]
[    0.530656] bus: 02 index 3 io port: [0x00-0xffff]
[    0.530658] bus: 02 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.530660] bus: 04 index 0 io port: [0x4000-0x4fff]
[    0.530662] bus: 04 index 1 mmio: [0xf2000000-0xf3ffffff]
[    0.530664] bus: 04 index 2 mmio: [0xf0000000-0xf1ffffff]
[    0.530665] bus: 04 index 3 mmio: [0x0-0x0]
[    0.530667] bus: 03 index 0 mmio: [0x0-0x0]
[    0.530669] bus: 03 index 1 mmio: [0xf6000000-0xf60fffff]
[    0.530671] bus: 03 index 2 mmio: [0x0-0x0]
[    0.530672] bus: 03 index 3 mmio: [0x0-0x0]
[    0.530684] NET: Registered protocol family 2
[    0.569074] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.570024] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.573261] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.574049] TCP: Hash tables configured (established 262144 bind 65536)
[    0.574052] TCP reno registered
[    0.585122] NET: Registered protocol family 1
[    0.585259] checking if image is initramfs... it is
[    1.194803] Freeing initrd memory: 7974k freed
[    1.200605] Simple Boot Flag at 0x36 set to 0x80
[    1.200922] audit: initializing netlink socket (disabled)
[    1.200935] type=2000 audit(1241160808.200:1): initialized
[    1.209110] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.210399] VFS: Disk quotas dquot_6.5.1
[    1.210453] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.211044] fuse init (API version 7.10)
[    1.211121] msgmni has been set to 5837
[    1.211323] alg: No test for stdrng (krng)
[    1.211337] io scheduler noop registered
[    1.211339] io scheduler anticipatory registered
[    1.211341] io scheduler deadline registered
[    1.211382] io scheduler cfq registered (default)
[    1.211413] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.211580] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.211595] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.211611] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.211627] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.211642] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.211657] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.211672] pci 0000:00:12.0: Boot video device
[    1.218573] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.218597] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.218614] pcieport-driver 0000:00:0c.0: irq 2303 for MSI/MSI-X
[    1.218620] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.218635] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.218674] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.218695] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.218707] pcieport-driver 0000:00:0d.0: irq 2302 for MSI/MSI-X
[    1.218713] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.218724] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.218769] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.218778] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.220859] ACPI: AC Adapter [ACAD] (on-line)
[    1.501822] ACPI: Battery Slot [BAT0] (battery present)
[    1.501904] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.501906] ACPI: Power Button (FF) [PWRF]
[    1.501950] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.501952] ACPI: Sleep Button (CM) [SLPB]
[    1.502003] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.503084] ACPI: Lid Switch [LID]
[    1.503145] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.503147] ACPI: Power Button (CM) [PWRB]
[    1.503484] ACPI: processor limited to max C-state 1
[    1.503506] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.503539] processor ACPI_CPU:00: registered as cooling_device0
[    1.503543] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.503646] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.503667] processor ACPI_CPU:01: registered as cooling_device1
[    1.503672] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.767193] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.801275] Linux agpgart interface v0.103
[    1.801285] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.802192] brd: module loaded
[    1.802508] loop: module loaded
[    1.802592] Fixed MDIO Bus: probed
[    1.802597] PPP generic driver version 2.4.2
[    1.802650] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.802682] Driver 'sd' needs updating - please use bus_type methods
[    1.802690] Driver 'sr' needs updating - please use bus_type methods
[    1.802733] ahci 0000:00:09.0: version 3.0
[    1.803134] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    1.803145] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    1.803192] ahci 0000:00:09.0: irq 2301 for MSI/MSI-X
[    1.803275] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.803278] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part
[    1.803281] ahci 0000:00:09.0: setting latency timer to 64
[    1.803780] scsi0 : ahci
[    1.803934] scsi1 : ahci
[    1.804022] scsi2 : ahci
[    1.804095] scsi3 : ahci
[    1.804191] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 2301
[    1.804194] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 2301
[    1.804197] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 2301
[    1.804199] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 2301
[    2.284034] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.284916] ata1.00: ATA-7: HITACHI HTS541680J9SA00, SB2IC7UP, max UDMA/100
[    2.284919] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.285963] ata1.00: configured for UDMA/100
[    2.604026] ata2: SATA link down (SStatus 0 SControl 300)
[    2.924025] ata3: SATA link down (SStatus 0 SControl 300)
[    3.244025] ata4: SATA link down (SStatus 0 SControl 300)
[    3.244127] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54168 SB2I PQ: 0 ANSI: 5
[    3.244224] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    3.244241] sd 0:0:0:0: [sda] Write Protect is off
[    3.244243] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.244266] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.244346] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    3.244359] sd 0:0:0:0: [sda] Write Protect is off
[    3.244361] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.244383] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.244388]  sda: sda1 sda2 sda3 < sda5 >
[    3.653295] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.653343] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.653564] pata_amd 0000:00:06.0: version 0.3.10
[    3.653607] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.653710] scsi4 : pata_amd
[    3.653791] scsi5 : pata_amd
[    3.654156] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    3.654159] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    3.816303] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[    3.816324] ata5: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    3.832247] ata5.00: configured for MWDMA2
[    3.834548] ata6: port disabled. ignoring.
[    3.834577] isa bounce pool size: 16 pages
[    3.838372] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[    3.842198] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.842201] Uniform CD-ROM driver Revision: 3.20
[    3.842303] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    3.842347] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.842772] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.843157] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    3.843168] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    3.843188] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.843191] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.843262] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.843295] ehci_hcd 0000:00:02.1: debug port 1
[    3.843299] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.843322] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    3.852032] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    3.852101] usb usb1: configuration #1 chosen from 1 choice
[    3.852128] hub 1-0:1.0: USB hub found
[    3.852136] hub 1-0:1.0: 7 ports detected
[    3.852589] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    3.852592] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    3.852602] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    3.852605] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    3.852647] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    3.852676] ehci_hcd 0000:00:04.1: debug port 1
[    3.852680] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    3.852684] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    3.864026] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    3.864086] usb usb2: configuration #1 chosen from 1 choice
[    3.864113] hub 2-0:1.0: USB hub found
[    3.864120] hub 2-0:1.0: 2 ports detected
[    3.864205] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.864555] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    3.864564] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    3.864574] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.864576] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.864627] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    3.864651] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    3.922066] usb usb3: configuration #1 chosen from 1 choice
[    3.922092] hub 3-0:1.0: USB hub found
[    3.922101] hub 3-0:1.0: 7 ports detected
[    3.922520] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    3.922523] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    3.922533] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    3.922536] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    3.922578] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    3.922590] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    3.978062] usb usb4: configuration #1 chosen from 1 choice
[    3.978085] hub 4-0:1.0: USB hub found
[    3.978094] hub 4-0:1.0: 2 ports detected
[    3.978178] uhci_hcd: USB Universal Host Controller Interface driver
[    3.978262] usbcore: registered new interface driver libusual
[    3.978296] usbcore: registered new interface driver usbserial
[    3.978306] USB Serial support registered for generic
[    3.978318] usbcore: registered new interface driver usbserial_generic
[    3.978320] usbserial: USB Serial Driver core
[    3.978361] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.004927] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.004937] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.013051] mice: PS/2 mouse device common for all mice
[    4.073084] rtc_cmos 00:07: RTC can wake from S4
[    4.073122] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    4.073159] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.073224] device-mapper: uevent: version 1.0.3
[    4.073328] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.073463] device-mapper: multipath: version 1.0.5 loaded
[    4.073466] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.073659] cpuidle: using governor ladder
[    4.073718] cpuidle: using governor menu
[    4.074132] TCP cubic registered
[    4.074199] NET: Registered protocol family 10
[    4.074573] lo: Disabled Privacy Extensions
[    4.074839] NET: Registered protocol family 17
[    4.074860] Bluetooth: L2CAP ver 2.11
[    4.074861] Bluetooth: L2CAP socket layer initialized
[    4.074864] Bluetooth: SCO (Voice Link) ver 0.6
[    4.074865] Bluetooth: SCO socket layer initialized
[    4.074918] Bluetooth: RFCOMM socket layer initialized
[    4.074927] Bluetooth: RFCOMM TTY layer initialized
[    4.074929] Bluetooth: RFCOMM ver 1.10
[    4.074982] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 processors (2 cpu cores) (version 2.20.00)
[    4.075037] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x11
[    4.075040] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[    4.075042] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[    4.075044] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    4.075179] registered taskstats version 1
[    4.075355]   Magic number: 9:41:872
[    4.075467] rtc_cmos 00:07: setting system clock to 2009-05-01 06:53:31 UTC (1241160811)
[    4.075470] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.075472] EDD information not available.
[    4.075519] Freeing unused kernel memory: 536k freed
[    4.075794] Write protecting the kernel read-only data: 6708k
[    4.092060] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.615178] ohci1394 0000:02:05.0: enabling device (0100 -> 0102)
[    4.615598] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    4.615611] ohci1394 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    4.618394] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.618813] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.618825] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    4.618830] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.667375] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f6100000-f61007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.137033] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:36:a2:b6
[    5.137038] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    5.307041] ISO 9660 Extensions: Microsoft Joliet Level 3
[    5.358522] ISO 9660 Extensions: RRIP_1991A
[    5.754849] aufs 20080922
[    5.953270] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00ce0ecb00]
[    6.059552] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   62.226058] udev: starting version 141
[   62.556903] acpi device:25: registered as cooling_device2
[   62.557196] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
[   62.592166] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   63.329062] cfg80211: Calling CRDA to update world regulatory domain
[   63.447599] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   63.693400] sdhci: Secure Digital Host Controller Interface driver
[   63.693403] sdhci: Copyright(c) Pierre Ossman
[   63.767790] ricoh-mmc: Ricoh MMC Controller disabling driver
[   63.767793] ricoh-mmc: Copyright(c) Philip Langdale
[   63.767839] ricoh-mmc: Ricoh MMC controller found at 0000:02:05.2 [1180:0843] (rev 12)
[   63.767854] ricoh-mmc: Controller is now disabled.
[   63.842825] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   64.853733] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[   64.854213] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   64.854225] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[   64.857405] mmc0: SDHCI controller on PCI [0000:02:05.1] using PIO
[   64.891790] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   64.968421] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   65.422167] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   65.422181] ath5k_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   65.422190] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   65.422257] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   65.462762] phy0: Selected rate control algorithm 'pid'
[   66.233671] cfg80211: World regulatory domain updated:
[   66.233676] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   66.233679] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.233681] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   66.233683] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   66.233685] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.233687] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.517331] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   66.778150] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   66.778164] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   66.778261] HDA Intel 0000:00:07.0: setting latency timer to 64
[   69.452574] Adding 1004020k swap on /dev/sda5.  Priority:-1 extents:1 across:1004020k
[   80.475794] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   80.475797] Bluetooth: BNEP filters: protocol multicast
[   80.772701] Bridge firewalling registered
[   89.575983] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
[   89.809766] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   91.407128] lp: driver loaded but no devices found
[   91.845744] ppdev: user-space parallel port driver
[   98.826755] mtrr: no MTRR for d0000000,4000000 found
[  100.340013] eth0: no IPv6 routers present
[  164.000027] Clocksource tsc unstable (delta = -300460785 ns)

```

---

### Post by t0mppa on 2009-05-01
Woah! That was quite a bit of info, you're the first user I've seen that read that post and actually went ahead with providing all the info. :)

Now, to the problem at hand. Your card is supported by the ath5k driver nicely on the KDE4, but on the KDE3 case, there is no ath5k or any other wireless driver present and that's why the wireless clearly doesn't work.

That's a bit strange, since Jaunty is supposed to have ath5k by default. You should be able to remedy this by enabling the backports module though. [Here's]("http://nuclear-imaging.info/site_content/2009/01/30/atheros-5007eg-now-works-in-jaunty-jackalope/") a tutorial about it.

---

