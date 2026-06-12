---
title: "Wireless router Acer Aspire 5552"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by AlexBaranosky on 2011-08-07
Hello folks, 

I've purchased a new laptop and could use some help getting the router setup.

I downloaded the drivers and restarted.  When I went to my wireless routers, I saw none, and clearly cannot yet connect to the internet except via ethernet cable.

Here are my stats:
```
lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 42)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)

```

```
lspci | grep -i net
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
08:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)

```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:bf:71:b9  
          inet6 addr: fe80::1e75:8ff:febf:71b9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2859 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4703901 (4.7 MB)  TX bytes:477100 (477.1 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 88:9f:fa:34:9e:19  
          inet6 addr: fe80::8a9f:faff:fe34:9e19/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

Thanks in advance for any help you can give!

Alex

---

### Post by AlexBaranosky on 2011-08-08
Any scraps of help greatly appreciated :)

---

### Post by AlexBaranosky on 2011-08-08
Hello,

Are there any other pieces of information I could get from my Acer laptop, to help understand the problem?

Thanks,
Alex

---

### Post by AlexBaranosky on 2011-08-08
*bump*

---

### Post by AlexBaranosky on 2011-08-08
Is there no one who can give me a modicum of direction regarding this issue?  I've always had trouble with the wireless on every machine I've used Ubuntu on, but was always able to get it working with the help of folks at the forum.  

Thanks in advance for help.

---

### Post by AlexBaranosky on 2011-08-08
Hope this extra info can be of help:

sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:bf:71:b9
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb ip=192.168.1.45 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:f1100000-f110ffff
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 88:9f:fa:34:9e:19
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f1000000-f1003fff
```

rfkill list all
```
#no results for this command
```

lsmod
```
Module                  Size  Used by
usb_storage            50377  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_atihdmi     3023  1 
joydev                 11104  0 
snd_hda_codec_realtek   279008  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_dummy           1782  0 
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
lib80211_crypt_tkip     8676  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fglrx                2353486  31 
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
vga16fb                12757  1 
wl                   1964968  0 
psmouse                65040  0 
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
video                  20623  0 
vgastate                9857  1 vga16fb
output                  2503  1 video
lib80211                6151  2 lib80211_crypt_tkip,wl
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4918  0 
v4l2_compat_ioctl32    11892  1 videodev
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_piix4               9639  0 
edac_core              45423  0 
edac_mce_amd            9278  0 
led_class               3764  0 
shpchp                 33711  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
tg3                   122382  0 
ahci                   38030  2 
```

---

### Post by AlexBaranosky on 2011-08-08
dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-33-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 (Ubuntu 2.6.32-33.70-generic 2.6.32.41+drm33.18)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=3a72b8a2-44e3-48cb-bbec-c6da9dfd463c ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000de557000 (usable)
[    0.000000]  BIOS-e820: 00000000de557000 - 00000000de757000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000de757000 - 00000000dfd3f000 (usable)
[    0.000000]  BIOS-e820: 00000000dfd3f000 - 00000000dfdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000dfdbf000 - 00000000dfebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000dfebf000 - 00000000dfef7000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dfef7000 - 00000000dff00000 (usable)
[    0.000000]  BIOS-e820: 00000000dff00000 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f7000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000110000000 (usable)
[    0.000000]  BIOS-e820: 0000000110000000 - 0000000120000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] last_pfn = 0x110000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
[    0.000000]   3 base 0000FFE00000 mask FFFFFFE00000 write-protect
[    0.000000]   4 base 000100000000 mask FFFFF0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000120000000 aka 4608M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xdff00 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000de557000 (usable)
[    0.000000]  modified: 00000000de557000 - 00000000de757000 (ACPI NVS)
[    0.000000]  modified: 00000000de757000 - 00000000dfd3f000 (usable)
[    0.000000]  modified: 00000000dfd3f000 - 00000000dfdbf000 (reserved)
[    0.000000]  modified: 00000000dfdbf000 - 00000000dfebf000 (ACPI NVS)
[    0.000000]  modified: 00000000dfebf000 - 00000000dfef7000 (ACPI data)
[    0.000000]  modified: 00000000dfef7000 - 00000000dff00000 (usable)
[    0.000000]  modified: 00000000dff00000 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000f7000000 - 00000000f8000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec11000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000110000000 (usable)
[    0.000000]  modified: 0000000110000000 - 0000000120000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000dff00000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dff00000 page 4k
[    0.000000] kernel direct mapping tables up to dff00000 @ 8000-b000
[    0.000000] init_memory_mapping: 0000000100000000-0000000110000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0110000000 page 2M
[    0.000000] kernel direct mapping tables up to 110000000 @ a000-c000
[    0.000000] RAMDISK: 377f6000 - 37fefb7f
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 00000000dfef6120 0005C (v01 ACRSYS ACRPRDCT 00000003      01000013)
[    0.000000] ACPI: FACP 00000000dfef5000 000F4 (v04 ACRSYS ACRPRDCT 00000003 1025 01000013)
[    0.000000] ACPI: DSDT 00000000dfee6000 0B23D (v01 ACRSYS ACRPRDCT F0000000 1025 01000013)
[    0.000000] ACPI: FACS 00000000dfe99000 00040
[    0.000000] ACPI: HPET 00000000dfef4000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 00000000dfef3000 00084 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 00000000dfef2000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 00000000dfee5000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 00000000dfee4000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT 00000000dfee3000 00386 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000110000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000110000000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000031fff] pages 22
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0110000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a30a64]    TEXT DATA BSS ==> [0001000000 - 0001a30a64]
[    0.000000]   #3 [00377f6000 - 0037fefb7f]          RAMDISK ==> [00377f6000 - 0037fefb7f]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0001a31000 - 0001a311f7]              BRK ==> [0001a31000 - 0001a311f7]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000]  [ffffea0000000000-ffffea0003bfffff] PMD -> [ffff880028600000-ffff88002bbfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00110000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000de557
[    0.000000]     0: 0x000de757 -> 0x000dfd3f
[    0.000000]     0: 0x000dfef7 -> 0x000dff00
[    0.000000]     0: 0x00100000 -> 0x00110000
[    0.000000] On node 0 totalpages: 981730
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3836 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 897920 pages, LIFO batch:31
[    0.000000]   Normal zone: 896 pages used for memmap
[    0.000000]   Normal zone: 64640 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000de557000 - 00000000de757000
[    0.000000] PM: Registered nosave memory: 00000000dfd3f000 - 00000000dfdbf000
[    0.000000] PM: Registered nosave memory: 00000000dfdbf000 - 00000000dfebf000
[    0.000000] PM: Registered nosave memory: 00000000dfebf000 - 00000000dfef7000
[    0.000000] PM: Registered nosave memory: 00000000dff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f7000000
[    0.000000] PM: Registered nosave memory: 00000000f7000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:17000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u524288
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 966396
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=3a72b8a2-44e3-48cb-bbec-c6da9dfd463c ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 3786760k/4456448k available (5412k kernel code, 529528k absent, 140160k reserved, 2981k data, 888k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2194.401 MHz processor.
[    0.020006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4388.79 BogoMIPS (lpj=21943980)
[    0.020028] Security Framework initialized
[    0.020046] AppArmor: AppArmor initialized
[    0.020386] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.021913] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.022605] Mount-cache hash table entries: 256
[    0.022720] Initializing cgroup subsys ns
[    0.022724] Initializing cgroup subsys cpuacct
[    0.022728] Initializing cgroup subsys memory
[    0.022735] Initializing cgroup subsys devices
[    0.022737] Initializing cgroup subsys freezer
[    0.022739] Initializing cgroup subsys net_cls
[    0.022758] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.022760] CPU: L2 Cache: 512K (64 bytes/line)
[    0.022763] CPU 0/0x0 -> Node 0
[    0.022766] tseg: 00dff00000
[    0.022768] CPU: Physical Processor ID: 0
[    0.022770] CPU: Processor Core ID: 0
[    0.022772] mce: CPU supports 6 MCE banks
[    0.022782] using C1E aware idle routine
[    0.022784] Performance Events: AMD PMU driver.
[    0.022788] ... version:                0
[    0.022790] ... bit width:              48
[    0.022791] ... generic registers:      4
[    0.022793] ... value mask:             0000ffffffffffff
[    0.022795] ... max period:             00007fffffffffff
[    0.022797] ... fixed-purpose events:   0
[    0.022798] ... event mask:             000000000000000f
[    0.030272] ACPI: Core revision 20090903
[    0.050009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.050014] ftrace: allocating 22478 entries in 89 pages
[    0.056582] Setting APIC routing to flat
[    0.056911] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.158911] CPU0: AMD Athlon(tm) II P340 Dual-Core Processor stepping 03
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.030000] Initializing CPU#1
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.030000] CPU 1/0x1 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 1
[    0.310081] CPU1: AMD Athlon(tm) II P340 Dual-Core Processor stepping 03
[    0.310154] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320012] Brought up 2 CPUs
[    0.320014] Total of 2 processors activated (8777.85 BogoMIPS).
[    0.320019] System has AMD C1E enabled
[    0.320078] Switch to broadcast mode on CPU1
[    0.320383] CPU0 attaching sched-domain:
[    0.320388]  domain 0: span 0-1 level MC
[    0.320390]   groups: 0 1
[    0.320395] CPU1 attaching sched-domain:
[    0.320396]  domain 0: span 0-1 level MC
[    0.320398]   groups: 1 0
[    0.320475] Switch to broadcast mode on CPU0
[    0.320475] devtmpfs: initialized
[    0.320475] regulator: core version 0.5
[    0.320475] Time: 22:41:44  Date: 08/07/11
[    0.320475] NET: Registered protocol family 16
[    0.320475] node 0 link 0: io port [0, ffffff]
[    0.320475] TOM: 00000000e0000000 aka 3584M
[    0.320475] Fam 10h mmconf [f7000000, f7ffffff]
[    0.320475] node 0 link 0: mmio [a0000, bffff]
[    0.320475] node 0 link 0: mmio [e0000000, efffffff]
[    0.320475] node 0 link 0: mmio [f0000000, f20fffff]
[    0.320475] node 0 link 0: mmio [f2100000, f22fffff]
[    0.320475] node 0 link 0: mmio [f2300000, f6ffffff]
[    0.320475] node 0 link 0: mmio [f7000000, f7ffffff] ==> none
[    0.320475] node 0 link 0: mmio [f8000000, ffdfffff]
[    0.320475] TOM2: 0000000120000000 aka 4608M
[    0.320475] bus: [00,1f] on node 0 link 0
[    0.320475] bus: 00 index 0 io port: [0, ffff]
[    0.320475] bus: 00 index 1 mmio: [a0000, bffff]
[    0.320475] bus: 00 index 2 mmio: [e0000000, f6ffffff]
[    0.320475] bus: 00 index 3 mmio: [f8000000, ffffffff]
[    0.320475] bus: 00 index 4 mmio: [120000000, fcffffffff]
[    0.320475] ACPI: bus type pci registered
[    0.320475] PCI: MCFG configuration 0: base f7000000 segment 0 buses 0 - 15
[    0.320475] PCI: MCFG area at f7000000 reserved in E820
[    0.321083] PCI: Using MMCONFIG at f7000000 - f7ffffff
[    0.321085] PCI: Using configuration type 1 for base access
[    0.321105] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.321107] mtrr: probably your BIOS does not setup all CPUs.
[    0.321108] mtrr: corrected configuration.
[    0.321646] bio: create slab <bio-0> at 0
[    0.321646] Trying to unpack rootfs image as initramfs...
[    0.331090] ACPI: EC: Look up EC in DSDT
[    0.332903] ACPI: Executed 1 blocks of module-level executable AML code
[    0.337348] ACPI: BIOS _OSI(Linux) query ignored
[    0.352458] ACPI: Interpreter enabled
[    0.352463] ACPI: (supports S0 S1 S3 S4 S5)
[    0.352493] ACPI: Using IOAPIC for interrupt routing
[    0.497587] Freeing initrd memory: 8166k freed
[    0.530407] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.530697] ACPI: No dock devices found.
[    0.531670] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.531865] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.531869] pci 0000:00:04.0: PME# disabled
[    0.531907] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.531910] pci 0000:00:05.0: PME# disabled
[    0.532004] pci 0000:00:11.0: reg 10 io port: [0x7038-0x703f]
[    0.532010] pci 0000:00:11.0: reg 14 io port: [0x704c-0x704f]
[    0.532017] pci 0000:00:11.0: reg 18 io port: [0x7030-0x7037]
[    0.532023] pci 0000:00:11.0: reg 1c io port: [0x7048-0x704b]
[    0.532029] pci 0000:00:11.0: reg 20 io port: [0x7010-0x701f]
[    0.532036] pci 0000:00:11.0: reg 24 32bit mmio: [0xf2306000-0xf23063ff]
[    0.532094] pci 0000:00:12.0: reg 10 32bit mmio: [0xf2305000-0xf2305fff]
[    0.532161] pci 0000:00:12.2: reg 10 32bit mmio: [0xf2306500-0xf23065ff]
[    0.532208] pci 0000:00:12.2: supports D1 D2
[    0.532210] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.532214] pci 0000:00:12.2: PME# disabled
[    0.532247] pci 0000:00:13.0: reg 10 32bit mmio: [0xf2304000-0xf2304fff]
[    0.532313] pci 0000:00:13.2: reg 10 32bit mmio: [0xf2306400-0xf23064ff]
[    0.532360] pci 0000:00:13.2: supports D1 D2
[    0.532362] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.532366] pci 0000:00:13.2: PME# disabled
[    0.532455] pci 0000:00:14.2: reg 10 64bit mmio: [0xf2300000-0xf2303fff]
[    0.532494] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.532498] pci 0000:00:14.2: PME# disabled
[    0.532711] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xe0000000-0xefffffff]
[    0.532715] pci 0000:01:05.0: reg 14 io port: [0x6000-0x60ff]
[    0.532719] pci 0000:01:05.0: reg 18 32bit mmio: [0xf2200000-0xf220ffff]
[    0.532726] pci 0000:01:05.0: reg 24 32bit mmio: [0xf2100000-0xf21fffff]
[    0.532737] pci 0000:01:05.0: supports D1 D2
[    0.532755] pci 0000:01:05.1: reg 10 32bit mmio: [0xf2210000-0xf2213fff]
[    0.532775] pci 0000:01:05.1: supports D1 D2
[    0.532847] pci 0000:00:01.0: bridge io port: [0x6000-0x6fff]
[    0.532850] pci 0000:00:01.0: bridge 32bit mmio: [0xf2100000-0xf22fffff]
[    0.532854] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.532929] pci 0000:02:00.0: reg 10 64bit mmio: [0xf1100000-0xf110ffff]
[    0.532983] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.532987] pci 0000:02:00.0: PME# disabled
[    0.533048] pci 0000:00:04.0: bridge io port: [0x2000-0x5fff]
[    0.533051] pci 0000:00:04.0: bridge 32bit mmio: [0xf1100000-0xf20fffff]
[    0.533055] pci 0000:00:04.0: bridge 64bit mmio pref: [0xf0000000-0xf0ffffff]
[    0.533105] pci 0000:08:00.0: reg 10 64bit mmio: [0xf1000000-0xf1003fff]
[    0.533157] pci 0000:08:00.0: supports D1 D2
[    0.533159] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.533163] pci 0000:08:00.0: PME# disabled
[    0.533224] pci 0000:00:05.0: bridge 32bit mmio: [0xf1000000-0xf10fffff]
[    0.533279] pci 0000:00:14.4: transparent bridge
[    0.533301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.533516] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.533607] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.533700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.533856] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.544202] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.544453] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.544706] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.544992] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.545266] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.545429] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.545652] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.545873] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.546028] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.546032] vgaarb: loaded
[    0.546126] SCSI subsystem initialized
[    0.550042] libata version 3.00 loaded.
[    0.550077] usbcore: registered new interface driver usbfs
[    0.550077] usbcore: registered new interface driver hub
[    0.550077] usbcore: registered new device driver usb
[    0.550143] ACPI: WMI: Mapper loaded
[    0.550146] PCI: Using ACPI for IRQ routing
[    0.550330] NetLabel: Initializing
[    0.550331] NetLabel:  domain hash size = 128
[    0.550333] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.550344] NetLabel:  unlabeled traffic allowed by default
[    0.550392] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.550396] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.552427] Switching to clocksource tsc
[    0.552438] AppArmor: AppArmor Filesystem Enabled
[    0.552438] pnp: PnP ACPI init
[    0.552438] ACPI: bus type pnp registered
[    0.650886] pnp: PnP ACPI: found 10 devices
[    0.650890] ACPI: ACPI bus type pnp unregistered
[    0.650910] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.650913] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.650916] system 00:01: iomem range 0xf7000000-0xf7ffffff has been reserved
[    0.650925] system 00:08: ioport range 0x400-0x4cf has been reserved
[    0.650927] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.650929] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.650932] system 00:08: ioport range 0x550-0x550 has been reserved
[    0.650934] system 00:08: ioport range 0x680-0x6ff has been reserved
[    0.650936] system 00:08: ioport range 0x77a-0x77a has been reserved
[    0.650938] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.650940] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.650942] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.650944] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.650947] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.650949] system 00:08: ioport range 0xcd0-0xcdb has been reserved
[    0.650951] system 00:08: ioport range 0xfd60-0xfd63 has been reserved
[    0.650957] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.650959] system 00:09: iomem range 0xffe00000-0xffffffff has been reserved
[    0.656097] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.656100] pci 0000:00:01.0:   IO window: 0x6000-0x6fff
[    0.656103] pci 0000:00:01.0:   MEM window: 0xf2100000-0xf22fffff
[    0.656106] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.656111] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    0.656114] pci 0000:00:04.0:   IO window: 0x2000-0x5fff
[    0.656117] pci 0000:00:04.0:   MEM window: 0xf1100000-0xf20fffff
[    0.656120] pci 0000:00:04.0:   PREFETCH window: 0x000000f0000000-0x000000f0ffffff
[    0.656124] pci 0000:00:05.0: PCI bridge, secondary bus 0000:08
[    0.656126] pci 0000:00:05.0:   IO window: disabled
[    0.656129] pci 0000:00:05.0:   MEM window: 0xf1000000-0xf10fffff
[    0.656132] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.656136] pci 0000:00:14.4: PCI bridge, secondary bus 0000:09
[    0.656138] pci 0000:00:14.4:   IO window: disabled
[    0.656142] pci 0000:00:14.4:   MEM window: disabled
[    0.656146] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.656156] pci 0000:00:01.0: setting latency timer to 64
[    0.656164]   alloc irq_desc for 16 on node 0
[    0.656166]   alloc kstat_irqs on node 0
[    0.656171] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.656175] pci 0000:00:04.0: setting latency timer to 64
[    0.656179]   alloc irq_desc for 17 on node 0
[    0.656181]   alloc kstat_irqs on node 0
[    0.656184] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.656187] pci 0000:00:05.0: setting latency timer to 64
[    0.656195] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.656197] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.656200] pci_bus 0000:01: resource 0 io:  [0x6000-0x6fff]
[    0.656202] pci_bus 0000:01: resource 1 mem: [0xf2100000-0xf22fffff]
[    0.656205] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.656207] pci_bus 0000:02: resource 0 io:  [0x2000-0x5fff]
[    0.656210] pci_bus 0000:02: resource 1 mem: [0xf1100000-0xf20fffff]
[    0.656212] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf0ffffff]
[    0.656215] pci_bus 0000:08: resource 1 mem: [0xf1000000-0xf10fffff]
[    0.656217] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.656220] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.656252] NET: Registered protocol family 2
[    0.656404] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.657500] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.660412] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.660804] TCP: Hash tables configured (established 524288 bind 65536)
[    0.660807] TCP reno registered
[    0.660895] NET: Registered protocol family 1
[    0.810850] pci 0000:01:05.0: Boot video device
[    0.811658] PCI-DMA: Disabling AGP.
[    0.811744] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.811746] PCI-DMA: using GART IOMMU.
[    0.811749] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.812923] Simple Boot Flag at 0x44 set to 0x1
[    0.813111] Scanning for low memory corruption every 60 seconds
[    0.813215] audit: initializing netlink socket (disabled)
[    0.813225] type=2000 audit(1312756903.810:1): initialized
[    0.821556] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.822866] VFS: Disk quotas dquot_6.5.2
[    0.822923] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.823543] fuse init (API version 7.13)
[    0.823653] msgmni has been set to 7411
[    0.823922] alg: No test for stdrng (krng)
[    0.824006] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.824010] io scheduler noop registered
[    0.824011] io scheduler anticipatory registered
[    0.824013] io scheduler deadline registered
[    0.824045] io scheduler cfq registered (default)
[    0.824278]   alloc irq_desc for 24 on node 0
[    0.824281]   alloc kstat_irqs on node 0
[    0.824290] pcieport 0000:00:04.0: irq 24 for MSI/MSI-X
[    0.824296] pcieport 0000:00:04.0: setting latency timer to 64
[    0.824443]   alloc irq_desc for 25 on node 0
[    0.824445]   alloc kstat_irqs on node 0
[    0.824449] pcieport 0000:00:05.0: irq 25 for MSI/MSI-X
[    0.824453] pcieport 0000:00:05.0: setting latency timer to 64
[    0.824559] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.824582] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.840937] ACPI: AC Adapter [ACAD] (off-line)
[    0.841008] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.841011] ACPI: Power Button [PWRB]
[    0.841044] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.841046] ACPI: Sleep Button [SLPB]
[    0.841097] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.841224] ACPI: Lid Switch [LID]
[    0.841258] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.841261] ACPI: Power Button [PWRF]
[    0.841732] ACPI: processor limited to max C-state 1
[    0.841780] processor LNXCPU:00: registered as cooling_device0
[    0.841835] processor LNXCPU:01: registered as cooling_device1
[    0.921110] ACPI: Invalid active0 threshold
[    0.930929] thermal LNXTHERM:01: registered as thermal_zone0
[    0.930938] ACPI: Thermal Zone [THRM] (60 C)
[    0.931971] Linux agpgart interface v0.103
[    0.932001] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.932994] brd: module loaded
[    0.933347] loop: module loaded
[    0.933426] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.933751] Fixed MDIO Bus: probed
[    0.933777] PPP generic driver version 2.4.2
[    0.933803] tun: Universal TUN/TAP device driver, 1.6
[    0.933805] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.933865] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.933980] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.934004] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    0.934007] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.934039] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.934051] ehci_hcd 0000:00:12.2: QUIRK: Enable exception for AMD Hudson ASPM
[    0.934080] ehci_hcd 0000:00:12.2: debug port 1
[    0.934101] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf2306500
[    0.950844] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.950956] usb usb1: configuration #1 chosen from 1 choice
[    0.950981] hub 1-0:1.0: USB hub found
[    0.950988] hub 1-0:1.0: 5 ports detected
[    0.951154] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.951175] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    0.951179] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.951210] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.951229] ehci_hcd 0000:00:13.2: QUIRK: Enable exception for AMD Hudson ASPM
[    0.951249] ehci_hcd 0000:00:13.2: debug port 1
[    0.951263] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf2306400
[    0.970882] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.970992] usb usb2: configuration #1 chosen from 1 choice
[    0.971016] hub 2-0:1.0: USB hub found
[    0.971024] hub 2-0:1.0: 5 ports detected
[    0.971154] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.971232]   alloc irq_desc for 18 on node 0
[    0.971236]   alloc kstat_irqs on node 0
[    0.971242] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.971264] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    0.971268] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.971312] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.971339] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf2305000
[    1.034971] usb usb3: configuration #1 chosen from 1 choice
[    1.035002] hub 3-0:1.0: USB hub found
[    1.035047] hub 3-0:1.0: 5 ports detected
[    1.035182] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.035204] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    1.035207] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.035241] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.035298] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf2304000
[    1.084219] usb usb4: configuration #1 chosen from 1 choice
[    1.084243] hub 4-0:1.0: USB hub found
[    1.084288] hub 4-0:1.0: 5 ports detected
[    1.084386] uhci_hcd: USB Universal Host Controller Interface driver
[    1.084457] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.100570] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.100581] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.100675] mice: PS/2 mouse device common for all mice
[    1.100826] rtc_cmos 00:04: RTC can wake from S4
[    1.100858] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.100882] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.100986] device-mapper: uevent: version 1.0.3
[    1.101097] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.101245] device-mapper: multipath: version 1.1.0 loaded
[    1.101251] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.101518] cpuidle: using governor ladder
[    1.101520] cpuidle: using governor menu
[    1.101840] TCP cubic registered
[    1.101957] NET: Registered protocol family 10
[    1.102598] NET: Registered protocol family 17
[    1.102639] powernow-k8: Found 1 AMD Athlon(tm) II P340 Dual-Core Processor processors (2 cpu cores) (version 2.20.00)
[    1.102684] powernow-k8:    0 : pstate 0 (2200 MHz)
[    1.102686] powernow-k8:    1 : pstate 1 (1600 MHz)
[    1.102687] powernow-k8:    2 : pstate 2 (800 MHz)
[    1.102922] PM: Resume from disk failed.
[    1.102933] registered taskstats version 1
[    1.103303]   Magic number: 7:6:704
[    1.103424] rtc_cmos 00:04: setting system clock to 2011-08-07 22:41:45 UTC (1312756905)
[    1.103427] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.103428] EDD information not available.
[    1.103496] Freeing unused kernel memory: 888k freed
[    1.103750] Write protecting the kernel read-only data: 7688k
[    1.115982] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.125942] udev: starting version 151
[    1.217878] ahci 0000:00:11.0: version 3.0
[    1.217930]   alloc irq_desc for 19 on node 0
[    1.217932]   alloc kstat_irqs on node 0
[    1.217939] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.217994]   alloc irq_desc for 26 on node 0
[    1.217996]   alloc kstat_irqs on node 0
[    1.218005] ahci 0000:00:11.0: irq 26 for MSI/MSI-X
[    1.218067] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.218071] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.233793] scsi0 : ahci
[    1.236760] tg3.c:v3.102 (September 1, 2009)
[    1.236841] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.236961] tg3 0000:02:00.0: setting latency timer to 64
[    1.239862] scsi1 : ahci
[    1.240083] ata1: SATA max UDMA/133 abar m1024@0xf2306000 port 0xf2306100 irq 26
[    1.240118] ata2: SATA max UDMA/133 abar m1024@0xf2306000 port 0xf2306180 irq 26
[    1.251284] tg3 mdio bus: probed
[    1.273238] eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address 1c:75:08:bf:71:b9
[    1.273241] eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=200:01)
[    1.273244] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.273246] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.280144] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.594497] usb 2-1: configuration #1 chosen from 1 choice
[    1.771359] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.771388] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.772611] ata1.00: ATA-8: WDC WD2500BEVT-22A23T0, 01.01A01, max UDMA/133
[    1.772615] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.773993] ata2.00: ATAPI: HL-DT-STDVDRAM GT32N, 1.00, max UDMA/100
[    1.774052] ata1.00: configured for UDMA/133
[    1.777021] ata2.00: configured for UDMA/100
[    1.791563] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.791735] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.791838] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.791921] sd 0:0:0:0: [sda] Write Protect is off
[    1.791924] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.791954] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.792228]  sda:
[    1.794146] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT32N     1.00 PQ: 0 ANSI: 5
[    1.802163] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.802168] Uniform CD-ROM driver Revision: 3.20
[    1.802290] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.802343] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.828590]  sda1 sda2 <
[    1.861424] ACPI: Battery Slot [BAT1] (battery present)
[    1.861879]  sda5 >
[    1.862162] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.218129] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.336495] Adding 9936888k swap on /dev/sda5.  Priority:-1 extents:1 across:9936888k 
[    4.700410] udev: starting version 151
[    6.047654] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    6.047659] shpchp 0000:00:01.0: Cannot reserve MMIO region
[    6.047803] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.089247] EDAC MC: Ver: 2.1.0 Jul  7 2011
[    6.126370] acer-wmi: Acer Laptop ACPI-WMI Extras
[    6.129308] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    6.141890] EDAC amd64_edac:  Ver: 3.2.0 Jul  7 2011
[    6.142102] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[    6.142112] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    6.142113]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    6.142115]  (Note that use of the override may cause unknown side effects.)
[    6.142142] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    6.150302] acer-wmi: Unable to detect available WMID devices
[    6.252562] lib80211: common routines for IEEE802.11 drivers
[    6.252567] lib80211_crypt: registered algorithm 'NULL'
[    6.438554] Linux video capture interface: v2.00
[    6.465294] uvcvideo: Found UVC 1.00 device 1.3M HD WebCam (064e:c218)
[    6.473331] acpi device:01: registered as cooling_device2
[    6.473917] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input6
[    6.474079] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    6.484353] input: 1.3M HD WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input7
[    6.484399] usbcore: registered new interface driver uvcvideo
[    6.484402] USB Video Class driver (v0.1.0)
[    7.049905] elantech.c: assuming hardware version 2, firmware version 4.2.19
[    7.069753] lp: driver loaded but no devices found
[    7.109546] elantech.c: Synaptics capabilities query result 0x68, 0x18, 0x0c.
[    7.400128] elantech.c: retrying ps2 command 0xe6 (2).
[    7.421091] wl: module license 'MIXED/Proprietary' taints kernel.
[    7.421096] Disabling lock debugging due to kernel taint
[    7.426036] vga16fb: initializing
[    7.426039] vga16fb: mapped to 0xffff8800000a0000
[    7.426097] fb0: VGA16 VGA frame buffer device
[    7.426912] wl 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.426919] wl 0000:08:00.0: setting latency timer to 64
[    7.870850] [fglrx] Maximum main memory to use for locked dma buffers: 3548 MBytes.
[    7.870881] [fglrx]   vendor: 1002 device: 9712 count: 1
[    7.871158] [fglrx] ioport: bar 1, base 0x6000, size: 0x100
[    7.871173] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.871177] pci 0000:01:05.0: setting latency timer to 64
[    7.871481] [fglrx] Kernel PAT support is enabled
[    7.871501] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[    7.921364] elantech.c: retrying ps2 command 0xf8 (2).
[    8.223044] Console: switching to colour frame buffer device 80x30
[    8.298019] lib80211_crypt: registered algorithm 'TKIP'
[    8.298268] eth1: Broadcom BCM4357 802.11 Hybrid Wireless Controller 5.60.48.36 
[    8.630129] elantech.c: retrying ps2 command 0xf8 (1).
[    9.013632] type=1505 audit(1312771313.407:2):  operation="profile_load" pid=598 name="/sbin/dhclient3"
[    9.013656] type=1505 audit(1312771313.407:3):  operation="profile_replace" pid=560 name="/sbin/dhclient3"
[    9.013896] type=1505 audit(1312771313.407:4):  operation="profile_load" pid=598 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.013929] type=1505 audit(1312771313.407:5):  operation="profile_replace" pid=560 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.014047] type=1505 audit(1312771313.407:6):  operation="profile_load" pid=598 name="/usr/lib/connman/scripts/dhclient-script"
[    9.014087] type=1505 audit(1312771313.407:7):  operation="profile_replace" pid=560 name="/usr/lib/connman/scripts/dhclient-script"
[    9.014489] type=1505 audit(1312771313.407:8):  operation="profile_replace" pid=785 name="/sbin/dhclient3"
[    9.014759] type=1505 audit(1312771313.407:9):  operation="profile_replace" pid=785 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.014914] type=1505 audit(1312771313.407:10):  operation="profile_replace" pid=785 name="/usr/lib/connman/scripts/dhclient-script"
[    9.015377] type=1505 audit(1312771313.407:11):  operation="profile_replace" pid=812 name="/sbin/dhclient3"
[    9.020486] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.020586] HDA Intel 0000:00:14.2: setting latency timer to 64
[    9.205326] hda_codec: ALC272: BIOS auto-probing.
[    9.206469] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input8
[    9.211810] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input9
[    9.215052] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.215185] HDA Intel 0000:01:05.1: setting latency timer to 64
[   13.073303]   alloc irq_desc for 27 on node 0
[   13.073307]   alloc kstat_irqs on node 0
[   13.073321] tg3 0000:02:00.0: irq 27 for MSI/MSI-X
[   13.082732] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.291175] tg3: eth0: Link is down.
[   16.319399] ppdev: user-space parallel port driver
[   17.091688] [fglrx] ATIF platform detected with notification ID: 0x81
[   17.243265] [fglrx] GART Table is not in FRAME_BUFFER range 
[   17.243424]   alloc irq_desc for 28 on node 0
[   17.243427]   alloc kstat_irqs on node 0
[   17.243435] fglrx_pci 0000:01:05.0: irq 28 for MSI/MSI-X
[   17.243978] [fglrx] Firegl kernel thread PID: 1093
[   17.244318] [fglrx] IRQ 28 Enabled
[   17.869951] [fglrx] Gart USWC size:1157 M.
[   17.869955] [fglrx] Gart cacheable size:459 M.
[   17.869960] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   17.869962] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   18.582205] CPU0 attaching NULL sched-domain.
[   18.582212] CPU1 attaching NULL sched-domain.
[   18.640189] CPU0 attaching sched-domain:
[   18.640193]  domain 0: span 0-1 level MC
[   18.640196]   groups: 0 1
[   18.640199]   domain 1: span 0-1 level CPU
[   18.640201]    groups: 0-1 (cpu_power = 2048)
[   18.640206] CPU1 attaching sched-domain:
[   18.640208]  domain 0: span 0-1 level MC
[   18.640210]   groups: 1 0
[   18.640212]   domain 1: span 0-1 level CPU
[   18.640214]    groups: 0-1 (cpu_power = 2048)
[   23.531354] eth1: no IPv6 routers present
[   25.642968] CPU0 attaching NULL sched-domain.
[   25.642975] CPU1 attaching NULL sched-domain.
[   25.700184] CPU0 attaching sched-domain:
[   25.700188]  domain 0: span 0-1 level MC
[   25.700191]   groups: 0 1
[   25.700194]   domain 1: span 0-1 level CPU
[   25.700197]    groups: 0-1 (cpu_power = 2048)
[   25.700202] CPU1 attaching sched-domain:
[   25.700203]  domain 0: span 0-1 level MC
[   25.700205]   groups: 1 0
[   25.700208]   domain 1: span 0-1 level CPU
[   25.700209]    groups: 0-1 (cpu_power = 2048)
[   26.987163] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[ 2023.461228] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 2023.461236] tg3: eth0: Flow control is on for TX and on for RX.
[ 2023.462339] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2034.100157] eth0: no IPv6 routers present
[ 2609.481347] tg3: eth0: Link is down.
[ 2770.481263] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 2770.481271] tg3: eth0: Flow control is on for TX and on for RX.
[ 2854.756237] CPU0 attaching NULL sched-domain.
[ 2854.756250] CPU1 attaching NULL sched-domain.
[ 2854.821601] CPU0 attaching sched-domain:
[ 2854.821610]  domain 0: span 0-1 level MC
[ 2854.821617]   groups: 0 1
[ 2854.821630] CPU1 attaching sched-domain:
[ 2854.821635]  domain 0: span 0-1 level MC
[ 2854.821640]   groups: 1 0
[ 2856.336294] tg3 0000:02:00.0: PME# enabled
[ 2856.490150] tg3: eth0: Link is down.
[ 2858.481957] PM: Syncing filesystems ... done.
[ 2858.483090] PM: Preparing system for mem sleep
[ 2858.483094] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2858.483950] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2858.484013] PM: Entering mem sleep
[ 2858.484029] Suspending console(s) (use no_console_suspend to debug)
[ 2858.484255] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2858.484584] sd 0:0:0:0: [sda] Stopping disk
[ 2859.087085] PM: suspend of drv:sd dev:0:0:0:0 complete after 602.826 msecs
[ 2859.498457] PM: suspend of drv:psmouse dev:serio1 complete after 398.247 msecs
[ 2859.600133] PM: suspend of drv:atkbd dev:serio0 complete after 101.667 msecs
[ 2859.603534] wl 0000:08:00.0: PCI INT A disabled
[ 2859.730175] HDA Intel 0000:01:05.1: PCI INT B disabled
[ 2859.730193] ACPI handle has no context!
[ 2859.750133] PM: suspend of drv:HDA Intel dev:0000:01:05.1 complete after 129.926 msecs
[ 2859.750254] [fglrx] IRQ 28 Disabled
[ 2859.750280] [fglrx] Preparing suspend fglrx in kernel.
[ 2859.778803] [fglrx] Suspending fglrx in kernel completed.
[ 2859.778808] [fglrx] Power down the ASIC .
[ 2859.881175] HDA Intel 0000:00:14.2: PCI INT A disabled
[ 2859.900135] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 121.276 msecs
[ 2859.900149] ehci_hcd 0000:00:13.2: PCI INT B disabled
[ 2859.900157] ohci_hcd 0000:00:13.0: PCI INT A disabled
[ 2859.900163] ehci_hcd 0000:00:12.2: PCI INT B disabled
[ 2859.900169] ohci_hcd 0000:00:12.0: PCI INT A disabled
[ 2859.980230] PM: suspend of devices complete after 1495.992 msecs
[ 2859.980233] PM: suspend devices took 1.500 seconds
[ 2860.020204] PM: late suspend of devices complete after 39.964 msecs
[ 2860.020251] ACPI: Preparing to enter system sleep state S3
[ 2860.120355] Disabling non-boot CPUs ...
[ 2860.120375] CPU0 attaching NULL sched-domain.
[ 2860.120378] CPU1 attaching NULL sched-domain.
[ 2860.240137] CPU0 attaching NULL sched-domain.
[ 2860.241369] Broke affinity for irq 9
[ 2860.350143] CPU 1 is now offline
[ 2860.350146] SMP alternatives: switching to UP code
[ 2860.355207] Back to C!
[ 2860.355207] PCI-DMA: Resuming GART IOMMU
[ 2860.355207] PCI-DMA: Restoring GART aperture settings
[ 2860.355207] Enabling non-boot CPUs ...
[ 2860.355207] SMP alternatives: switching to SMP code
[ 2860.355207] Booting processor 1 APIC 0x1 ip 0x6000
[ 2860.355189] Initializing CPU#1
[ 2860.355189] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 2860.355189] CPU: L2 Cache: 512K (64 bytes/line)
[ 2860.355189] CPU 1/0x1 -> Node 0
[ 2860.355189] CPU: Physical Processor ID: 0
[ 2860.355189] CPU: Processor Core ID: 1
[ 2860.520040] CPU1: AMD Athlon(tm) II P340 Dual-Core Processor stepping 03
[ 2860.520047] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 2860.540126] Switch to broadcast mode on CPU1
[ 2860.540129] CPU0 attaching NULL sched-domain.
[ 2860.610098] CPU0 attaching sched-domain:
[ 2860.610102]  domain 0: span 0-1 level MC
[ 2860.610104]   groups: 0 1
[ 2860.610109] CPU1 attaching sched-domain:
[ 2860.610110]  domain 0: span 0-1 level MC
[ 2860.610112]   groups: 1 0
[ 2860.610455] CPU1 is up
[ 2860.610666] ACPI: Waking up from system sleep state S3
[ 2860.611153] pcieport 0000:00:04.0: restoring config space at offset 0x7 (was 0x20005121, writing 0x5121)
[ 2860.611159] pcieport 0000:00:04.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 2860.611162] pcieport 0000:00:04.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2860.611186] pcieport 0000:00:05.0: restoring config space at offset 0x7 (was 0x1f1, writing 0x200001f1)
[ 2860.611190] pcieport 0000:00:05.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 2860.611193] pcieport 0000:00:05.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2860.611231] ahci 0000:00:11.0: restoring config space at offset 0x1 (was 0x2300003, writing 0x2300407)
[ 2860.631373] ehci_hcd 0000:00:12.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00012)
[ 2860.650157] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00012)
[ 2860.650296] fglrx_pci 0000:01:05.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100403)
[ 2860.650321] HDA Intel 0000:01:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2860.650325] HDA Intel 0000:01:05.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
[ 2860.650450] wl 0000:08:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[ 2860.650504] PM: early resume of devices complete after 39.409 msecs
[ 2862.010276] PM: resume of drv:battery dev:PNP0C0A:00 complete after 1286.918 msecs
[ 2862.030241] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2862.060104] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2862.060118] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2862.090131] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2862.090146] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2862.090199] fglrx_pci 0000:01:05.0: setting latency timer to 64
[ 2862.093421] [fglrx] Power up the ASIC
[ 2862.093442] [fglrx] Preparing resume fglrx in kernel.
[ 2862.124856] [fglrx] Resuming fglrx in kernel completed.
[ 2862.125045] [fglrx] IRQ 28 Enabled
[ 2862.125061] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2862.125066] HDA Intel 0000:01:05.1: setting latency timer to 64
[ 2862.125099] wl 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2862.125103] wl 0000:08:00.0: setting latency timer to 64
[ 2862.310093] PM: resume of drv:usb dev:usb2 complete after 149.981 msecs
[ 2862.500136] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[ 2862.560079] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2862.563472] ata2.00: configured for UDMA/100
[ 2862.920076] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2862.942684] ata1.00: configured for UDMA/133
[ 2862.969595] PM: resume of drv:usb dev:2-1 complete after 656.394 msecs
[ 2862.969604] sd 0:0:0:0: [sda] Starting disk
[ 2862.982084] PM: resume of devices complete after 2331.523 msecs
[ 2862.982217] PM: resume devices took 2.330 seconds
[ 2862.982244] PM: Finishing wakeup.
[ 2862.982245] Restarting tasks ... done.
[ 2863.100148] usb 2-2: new high speed USB device using ehci_hcd and address 3
[ 2863.264260] usb 2-2: configuration #1 chosen from 1 choice
[ 2863.570939] tg3 0000:02:00.0: PME# disabled
[ 2863.571017] tg3 0000:02:00.0: irq 27 for MSI/MSI-X
[ 2863.581288] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2863.624588] Initializing USB Mass Storage driver...
[ 2863.626354] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2863.631362] usbcore: registered new interface driver usb-storage
[ 2863.631366] USB Mass Storage support registered.
[ 2863.631397] usb-storage: device found at 3
[ 2863.631400] usb-storage: waiting for device to settle before scanning
[ 2863.876591] CPU0 attaching NULL sched-domain.
[ 2863.876599] CPU1 attaching NULL sched-domain.
[ 2863.891421] elantech.c: retrying ps2 command 0xe6 (2).
[ 2863.941543] CPU0 attaching sched-domain:
[ 2863.941552]  domain 0: span 0-1 level MC
[ 2863.941560]   groups: 0 1
[ 2863.941569]   domain 1: span 0-1 level CPU
[ 2863.941574]    groups: 0-1 (cpu_power = 2048)
[ 2863.941587] CPU1 attaching sched-domain:
[ 2863.941592]  domain 0: span 0-1 level MC
[ 2863.941596]   groups: 1 0
[ 2863.941603]   domain 1: span 0-1 level CPU
[ 2863.941608]    groups: 0-1 (cpu_power = 2048)
[ 2864.410773] elantech.c: retrying ps2 command 0xf8 (2).
[ 2864.541069] tg3: eth0: Link is down.
[ 2865.120172] elantech.c: retrying ps2 command 0xf8 (1).
[ 2868.630718] usb-storage: device scan complete
[ 2868.634141] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[ 2868.635287] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 2868.649740] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 2870.541149] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 2870.541157] tg3: eth0: Flow control is on for TX and on for RX.
[ 2870.542264] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2871.114568] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input10
[ 2873.831279] eth1: no IPv6 routers present
[ 2880.770145] eth0: no IPv6 routers present
[ 2945.047378] CPU0 attaching NULL sched-domain.
[ 2945.047392] CPU1 attaching NULL sched-domain.
[ 2945.100309] CPU0 attaching sched-domain:
[ 2945.100318]  domain 0: span 0-1 level MC
[ 2945.100326]   groups: 0 1
[ 2945.100338] CPU1 attaching sched-domain:
[ 2945.100343]  domain 0: span 0-1 level MC
[ 2945.100348]   groups: 1 0
[ 2945.747407] tg3 0000:02:00.0: PME# enabled
[ 2946.560138] tg3: eth0: Link is down.
[ 2947.890851] PM: Syncing filesystems ... done.
[ 2947.892024] PM: Preparing system for mem sleep
[ 2947.892027] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2947.896299] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2947.896370] PM: Entering mem sleep
[ 2947.896386] Suspending console(s) (use no_console_suspend to debug)
[ 2947.911390] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2947.940139] sd 0:0:0:0: [sda] Stopping disk
[ 2948.542518] PM: suspend of drv:sd dev:0:0:0:0 complete after 631.128 msecs
[ 2948.957952] PM: suspend of drv:psmouse dev:serio1 complete after 397.826 msecs
[ 2949.060120] PM: suspend of drv:atkbd dev:serio0 complete after 102.158 msecs
[ 2949.063286] wl 0000:08:00.0: PCI INT A disabled
[ 2949.080196] HDA Intel 0000:01:05.1: PCI INT B disabled
[ 2949.080213] ACPI handle has no context!
[ 2949.100220] [fglrx] IRQ 28 Disabled
[ 2949.100248] [fglrx] Preparing suspend fglrx in kernel.
[ 2949.128605] [fglrx] Suspending fglrx in kernel completed.
[ 2949.128610] [fglrx] Power down the ASIC .
[ 2949.230465] HDA Intel 0000:00:14.2: PCI INT A disabled
[ 2949.250104] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 121.437 msecs
[ 2949.250118] ehci_hcd 0000:00:13.2: PCI INT B disabled
[ 2949.250125] ohci_hcd 0000:00:13.0: PCI INT A disabled
[ 2949.250132] ehci_hcd 0000:00:12.2: PCI INT B disabled
[ 2949.250138] ohci_hcd 0000:00:12.0: PCI INT A disabled
[ 2949.310252] PM: suspend of devices complete after 1413.659 msecs
[ 2949.310255] PM: suspend devices took 1.420 seconds
[ 2949.350193] PM: late suspend of devices complete after 39.931 msecs
[ 2949.350241] ACPI: Preparing to enter system sleep state S3
[ 2949.450341] Disabling non-boot CPUs ...
[ 2949.450360] CPU0 attaching NULL sched-domain.
[ 2949.450364] CPU1 attaching NULL sched-domain.
[ 2949.570103] CPU0 attaching NULL sched-domain.
[ 2949.571295] Broke affinity for irq 9
[ 2949.680093] CPU 1 is now offline
[ 2949.680096] SMP alternatives: switching to UP code
[ 2949.685119] Back to C!
[ 2949.685119] PCI-DMA: Resuming GART IOMMU
[ 2949.685119] PCI-DMA: Restoring GART aperture settings
[ 2949.685119] Enabling non-boot CPUs ...
[ 2949.685119] SMP alternatives: switching to SMP code
[ 2949.685119] Booting processor 1 APIC 0x1 ip 0x6000
[ 2949.685102] Initializing CPU#1
[ 2949.685102] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 2949.685102] CPU: L2 Cache: 512K (64 bytes/line)
[ 2949.685102] CPU 1/0x1 -> Node 0
[ 2949.685102] CPU: Physical Processor ID: 0
[ 2949.685102] CPU: Processor Core ID: 1
[ 2949.850075] CPU1: AMD Athlon(tm) II P340 Dual-Core Processor stepping 03
[ 2949.850117] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 2949.870206] CPU0 attaching NULL sched-domain.
[ 2949.870208] Switch to broadcast mode on CPU1
[ 2949.940112] CPU0 attaching sched-domain:
[ 2949.940116]  domain 0: span 0-1 level MC
[ 2949.940118]   groups: 0 1
[ 2949.940123] CPU1 attaching sched-domain:
[ 2949.940124]  domain 0: span 0-1 level MC
[ 2949.940126]   groups: 1 0
[ 2949.940465] CPU1 is up
[ 2949.940677] ACPI: Waking up from system sleep state S3
[ 2949.941147] pci 0000:00:01.0: restoring config space at offset 0x7 (was 0x2206161, writing 0x22206161)
[ 2949.941169] pcieport 0000:00:04.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 2949.941173] pcieport 0000:00:04.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2949.941197] pcieport 0000:00:05.0: restoring config space at offset 0x7 (was 0x1f1, writing 0x200001f1)
[ 2949.941201] pcieport 0000:00:05.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[ 2949.941204] pcieport 0000:00:05.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 2949.941242] ahci 0000:00:11.0: restoring config space at offset 0x1 (was 0x2300003, writing 0x2300407)
[ 2949.961374] ehci_hcd 0000:00:12.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00012)
[ 2949.980167] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00012)
[ 2949.980306] fglrx_pci 0000:01:05.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100403)
[ 2949.980331] HDA Intel 0000:01:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 2949.980334] HDA Intel 0000:01:05.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
[ 2949.980459] wl 0000:08:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[ 2949.980516] PM: early resume of devices complete after 39.410 msecs
[ 2951.340254] PM: resume of drv:battery dev:PNP0C0A:00 complete after 1286.900 msecs
[ 2951.360246] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2951.390108] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2951.390121] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2951.420146] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2951.420161] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2951.420216] fglrx_pci 0000:01:05.0: setting latency timer to 64
[ 2951.423437] [fglrx] Power up the ASIC
[ 2951.423459] [fglrx] Preparing resume fglrx in kernel.
[ 2951.454822] [fglrx] Resuming fglrx in kernel completed.
[ 2951.455006] [fglrx] IRQ 28 Enabled
[ 2951.455023] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2951.455027] HDA Intel 0000:01:05.1: setting latency timer to 64
[ 2951.455060] wl 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2951.455064] wl 0000:08:00.0: setting latency timer to 64
[ 2951.640097] PM: resume of drv:usb dev:usb2 complete after 149.982 msecs
[ 2951.830166] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[ 2951.890129] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2951.893558] ata2.00: configured for UDMA/100
[ 2952.250079] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2952.273189] ata1.00: configured for UDMA/133
[ 2952.299731] PM: resume of drv:usb dev:2-1 complete after 655.921 msecs
[ 2952.299739] sd 0:0:0:0: [sda] Starting disk
[ 2952.430166] usb 2-2: reset high speed USB device using ehci_hcd and address 3
[ 2952.589330] PM: resume of drv:usb dev:2-2 complete after 276.661 msecs
[ 2952.589358] PM: resume of devices complete after 2608.790 msecs
[ 2952.589499] PM: resume devices took 2.600 seconds
[ 2952.589526] PM: Finishing wakeup.
[ 2952.589527] Restarting tasks ... done.
[ 2953.078034] tg3 0000:02:00.0: PME# disabled
[ 2953.078096] tg3 0000:02:00.0: irq 27 for MSI/MSI-X
[ 2953.087391] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2953.417420] CPU0 attaching NULL sched-domain.
[ 2953.417427] CPU1 attaching NULL sched-domain.
[ 2953.470119] elantech.c: retrying ps2 command 0xe6 (2).
[ 2953.510228] CPU0 attaching sched-domain:
[ 2953.510237]  domain 0: span 0-1 level MC
[ 2953.510244]   groups: 0 1
[ 2953.510253]   domain 1: span 0-1 level CPU
[ 2953.510259]    groups: 0-1 (cpu_power = 2048)
[ 2953.510271] CPU1 attaching sched-domain:
[ 2953.510275]  domain 0: span 0-1 level MC
[ 2953.510280]   groups: 1 0
[ 2953.510287]   domain 1: span 0-1 level CPU
[ 2953.510291]    groups: 0-1 (cpu_power = 2048)
[ 2953.551285] tg3: eth0: Link is down.
[ 2954.000340] elantech.c: retrying ps2 command 0xf8 (2).
[ 2954.700171] elantech.c: retrying ps2 command 0xf8 (1).
[ 2959.641447] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input11
[ 2963.411406] eth1: no IPv6 routers present
[ 4065.551163] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 4065.551171] tg3: eth0: Flow control is on for TX and on for RX.
[ 4065.552266] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4075.920135] eth0: no IPv6 routers present

```

---

### Post by AlexBaranosky on 2011-08-08
iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

```

---

### Post by AlexBaranosky on 2011-08-09
iwlist scan wlan0
```

iwlist: unknown command `wlan0' (check 'iwlist --help').

```
lsb_release -d
```

Description:    Ubuntu 10.04.3 LTS

```uname -mr
```

2.6.32-33-generic x86_64

```sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                          
Ignoring unknown interface eth0=eth0.
```

---

### Post by nm_geo on 2011-08-09
removed info provided..

Try this one

```
sudo iwlist scanning
```

---

### Post by AlexBaranosky on 2011-08-09
sudo iwlist scanning
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:2A:7A:0D:EA
                    ESSID:"Near2Heaven"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-26 dBm  Noise level:-100 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: C0:3F:0E:86:C2:10
                    ESSID:"Danky"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:5/5  Signal level:-53 dBm  Noise level:-100 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD890050F204104A0001101044000102103B0001031047001000000000000010000000C03F0E86C2101021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F20400011011001A574E44523337303028576972656C6573732041502D322E344729100800020086103C000103
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:26:F2:C4:31:4E
                    ESSID:"real-Wireless"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-100 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 04 - Address: 00:12:0E:71:42:C1
                    ESSID:"07B403257828"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-100 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:14:6C:22:72:DA
                    ESSID:"Zero"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-62 dBm  Noise level:-98 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

```Thanks!

---

### Post by AlexBaranosky on 2011-08-09
So that last post's data made me realize that it was seeing the routers, and so I looked further and realized I was doing something dumb, and looking in the wrong spot for the connections.  I found my router and managed to connect to it, I got excited thinking I fixed it.

But now even though the router says it is connected, the internet still fails to load any of my web pages...

```
Server not found

Firefox can't find the server at help.ubuntu.com.
```

---

### Post by AlexBaranosky on 2011-08-09
Hmmmm... I rebooted and now it seems to work fine!  Great!

---

