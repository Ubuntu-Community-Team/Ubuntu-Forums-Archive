---
title: "Problems with Atheros AR928X Wireless Card on Ubuntu 9.04"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by marknit on 2009-10-18
Dear All,
 
My problem is that I have no wireless connection on Ubuntu 9.04. The wired connection works fine. I have a dual boot Vista/Ubuntu system installed on my Toshiba laptop. My laptop is a Satellite Pro P300-1CU (Part Number: PSPCDE-00U003IT). I have no problem with the wireless Internet on Vista.
 
The Ubuntu network manager can't find any wireless networks, even though the light on my computer indicating wireless activity is always on. I updated the system including the backports repository by using the wired connection (I used the command "sudo apt-get install linux-backports-modules-jaunty" and then restarted the system). Unfortunately, that didn't solve the wireless problem. Maybe I just have to install the correct drivers for my Atheros AR928X wireless card, but this is only my own supposition.
 
I googled the words "Atheros AR928X Ubuntu 9.04" and I found out that a lot of people are experiencing severe trouble with this wireless card on Ubuntu 9.04. I've spent a few days hunting around for a definitive solution but my search was not successful. The fact is that I need a wireless connection on Ubuntu for my work. So I hope someone here can help me.

After running a script for wireless troubleshooting I got the output reported below. Let me know if you need some more information about my system.
 
Thanks in advance.    

```

============ lspci ============
 00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
      Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
      Kernel driver in use: pcieport-driver
      Kernel modules: shpchp
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
      Kernel driver in use: uhci_hcd
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
      Kernel driver in use: uhci_hcd
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
      Kernel driver in use: uhci_hcd
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
      Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
      Kernel driver in use: HDA Intel
      Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
      Kernel driver in use: pcieport-driver
      Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
      Kernel driver in use: pcieport-driver
      Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
      Kernel driver in use: pcieport-driver
      Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
      Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
      Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
      Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
      Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
      Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
      Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
      Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]
01:00.1 Audio device [0403]: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] [1002:aa20]
      Kernel driver in use: HDA Intel
      Kernel modules: snd-hda-intel
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
      Kernel driver in use: ath9k
      Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:436c] (rev 16)
      Kernel driver in use: sky2
      Kernel modules: sky2
0a:01.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
      Kernel driver in use: ohci1394
      Kernel modules: firewire-ohci, ohci1394
0a:01.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
      Kernel driver in use: sdhci-pci
      Kernel modules: sdhci-pci
0a:01.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)

============ lsusb ============
Bus 002 Device 003: ID 04f2:b064 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

============ lsmod ============
Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96424  3 radeon
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
joydev                 18368  0 
snd_hda_intel         435252  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
ath9k                 282420  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               63368  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lbm_cw_mac80211       227492  1 ath9k
compat_ioctl32          9344  1 uvcvideo
snd                    62756  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class              12036  1 ath9k
videodev               41600  1 uvcvideo
intel_agp              34108  0 
soundcore              15200  1 snd
psmouse                61972  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
v4l1_compat            21764  2 uvcvideo,videodev
agpgart                42696  2 drm,intel_agp
usbhid                 42336  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
pcspkr                 10496  0 
serio_raw              13444  0 
input_polldev          11912  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
lbm_cw_cfg80211        73888  2 ath9k,lbm_cw_mac80211
video                  25872  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

============ dmesg-firmware ============

============ dmesg ============
[    0.000000] BIOS EBDA/lowmem at: 0009c400/0009c400
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 (Ubuntu 2.6.28-15.52-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8b1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8b1000 - 00000000bf8b7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8b7000 - 00000000bf9ba000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9ba000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd65000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd65000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfde1000 (usable)
[    0.000000]  BIOS-e820: 00000000bfde1000 - 00000000bfdfd000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdfd000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000008f400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf8b1000 (usable)
[    0.000000]  modified: 00000000bf8b1000 - 00000000bf8b7000 (reserved)
[    0.000000]  modified: 00000000bf8b7000 - 00000000bf9ba000 (usable)
[    0.000000]  modified: 00000000bf9ba000 - 00000000bfa0f000 (reserved)
[    0.000000]  modified: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  modified: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  modified: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  modified: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  modified: 00000000bfd1f000 - 00000000bfd65000 (usable)
[    0.000000]  modified: 00000000bfd65000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  modified: 00000000bfd9f000 - 00000000bfde1000 (usable)
[    0.000000]  modified: 00000000bfde1000 - 00000000bfdfd000 (ACPI data)
[    0.000000]  modified: 00000000bfdfd000 - 00000000bfe00000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bd000 - 37fefa0b
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fafa0b
[    0.000000] Move RAMDISK from 00000000378bd000 - 0000000037fefa0a to 0087d000 - 00fafa0a
[    0.000000] ACPI: RSDP 000F6F60, 0024 (r2 TOSQCI)
[    0.000000] ACPI: XSDT BFDF2AB4, 007C (r1 TOSQCI TOSQCI00  6040000  LTP        0)
[    0.000000] ACPI: FACP BFDE5000, 00F4 (r3 T0SQCI TOSQCI00  6040000 ALAN        1)
[    0.000000] ACPI: DSDT BFDE6000, 9DB1 (r2 TOSQCI CANTIGA   6040000 INTL 20061109)
[    0.000000] ACPI: FACS BFD9EFC0, 0040
[    0.000000] ACPI: APIC BFDFCD1E, 0068 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
[    0.000000] ACPI: HPET BFDFCD86, 0038 (r1 TOSQCI TOSQCI00  6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BFDFCDBE, 003C (r1 TOSQCI TOSQCI00  6040000 LOHR       5A)
[    0.000000] ACPI: APIC BFDFCDFA, 0068 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT BFDFCE62, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SLIC BFDFCE8A, 0176 (r1 TOSQCI TOSQCI00  6040000  LTP        0)
[    0.000000] ACPI: SSDT BFDF2B58, 02AD (r1 SataRe SataAhci     1000 INTL 20061109)
[    0.000000] ACPI: SSDT BFDE4000, 0655 (r1  PmRef    CpuPm     3000 INTL 20061109)
[    0.000000] ACPI: SSDT BFDE3000, 0259 (r1  PmRef  Cpu0Tst     3000 INTL 20061109)
[    0.000000] ACPI: SSDT BFDE2000, 020F (r1  PmRef    ApTst     3000 INTL 20061109)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2186MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009c400 - 0000100000]    BIOS reserved ==> [000009c400 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fafa0b]      NEW RAMDISK ==> [000087d000 - 0000fafa0b]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f7020] 000f7020
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000bfe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[10] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x0000008f
[    0.000000]     0: 0x00000100 -> 0x000bf8b1
[    0.000000]     0: 0x000bf8b7 -> 0x000bf9ba
[    0.000000]     0: 0x000bfa0f -> 0x000bfb08
[    0.000000]     0: 0x000bfd0f -> 0x000bfd18
[    0.000000]     0: 0x000bfd1f -> 0x000bfd65
[    0.000000]     0: 0x000bfd9f -> 0x000bfde1
[    0.000000]     0: 0x000bfdfd -> 0x000bfe00
[    0.000000] On node 0 totalpages: 785091
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3938 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4373 pages used for memmap
[    0.000000]   HighMem zone: 554542 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
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
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: bfe00000:40200000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778950
[    0.000000] Kernel command line: root=UUID=6ede18a8-adc9-4de2-9b70-b7132ce47846 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2394.141 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 15718400 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 3083520k/3143680k available (4116k kernel code, 55952k reserved, 2199k data, 532k init, 2235660k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.28 BogoMIPS (lpj=9576564)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018117] ACPI: Core revision 20080926
[    0.021294] ACPI: Checking initramfs for custom DSDT
[    0.276418] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.316322] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
[    0.320001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4787.96 BogoMIPS (lpj=9575923)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.404525] CPU1: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 06
[    0.404538] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.408029] Brought up 2 CPUs
[    0.408032] Total of 2 processors activated (9576.24 BogoMIPS).
[    0.408079] CPU0 attaching sched-domain:
[    0.408081]  domain 0: span 0-1 level MC
[    0.408083]   groups: 0 1
[    0.408088] CPU1 attaching sched-domain:
[    0.408089]  domain 0: span 0-1 level MC
[    0.408091]   groups: 1 0
[    0.408148] net_namespace: 776 bytes
[    0.408148] Booting paravirtualized kernel on bare hardware
[    0.408259] Time: 17:18:23  Date: 10/18/09
[    0.408259] regulator: core version 0.5
[    0.408259] NET: Registered protocol family 16
[    0.408259] EISA bus registered
[    0.408259] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.408259] ACPI: bus type pci registered
[    0.408259] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.408259] PCI: Not using MMCONFIG.
[    0.410211] PCI: PCI BIOS revision 3.00 entry at 0xfdc11, last bus=10
[    0.410213] PCI: Using configuration type 1 for base access
[    0.413033] ACPI: EC: Look up EC in DSDT
[    0.417388] ACPI: BIOS _OSI(Linux) query ignored
[    0.420687] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.920006] ACPI: EC: missing confirmations, switch off interrupt mode.
[    0.934801] ACPI: Interpreter enabled
[    0.934804] ACPI: (supports S0 S3 S4 S5)
[    0.934820] ACPI: Using IOAPIC for interrupt routing
[    0.934875] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.937310] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.937312] PCI: Using MMCONFIG for extended config space
[    0.942590] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.942592] ACPI: EC: driver started in poll mode
[    0.942724] ACPI: No dock devices found.
[    0.942797] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.942872] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.942874] pci 0000:00:01.0: PME# disabled
[    0.942965] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.943041] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.943118] pci 0000:00:1a.2: reg 20 io port: [0x1840-0x185f]
[    0.943199] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf8404800-0xf8404bff]
[    0.943243] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.943248] pci 0000:00:1a.7: PME# disabled
[    0.943302] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf8400000-0xf8403fff]
[    0.943340] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.943344] pci 0000:00:1b.0: PME# disabled
[    0.943406] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.943410] pci 0000:00:1c.0: PME# disabled
[    0.943477] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.943481] pci 0000:00:1c.1: PME# disabled
[    0.943547] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.943551] pci 0000:00:1c.3: PME# disabled
[    0.943629] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.943709] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.943800] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.943883] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf8404c00-0xf8404fff]
[    0.943928] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.943932] pci 0000:00:1d.7: PME# disabled
[    0.944151] pci 0000:00:1f.2: reg 10 io port: [0x18f0-0x18f7]
[    0.944159] pci 0000:00:1f.2: reg 14 io port: [0x18e4-0x18e7]
[    0.944166] pci 0000:00:1f.2: reg 18 io port: [0x18e8-0x18ef]
[    0.944173] pci 0000:00:1f.2: reg 1c io port: [0x18e0-0x18e3]
[    0.944181] pci 0000:00:1f.2: reg 20 io port: [0x18c0-0x18df]
[    0.944188] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf8404000-0xf84047ff]
[    0.944207] pci 0000:00:1f.2: PME# supported from D3hot
[    0.944210] pci 0000:00:1f.2: PME# disabled
[    0.944249] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.944267] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.944329] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.944342] pci 0000:01:00.0: reg 18 64bit mmio: [0xcfef0000-0xcfefffff]
[    0.944349] pci 0000:01:00.0: reg 20 io port: [0x2000-0x20ff]
[    0.944361] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.944371] pci 0000:01:00.0: supports D1 D2
[    0.944419] pci 0000:01:00.1: reg 10 64bit mmio: [0xcfeec000-0xcfeeffff]
[    0.944455] pci 0000:01:00.1: supports D1 D2
[    0.944520] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.944523] pci 0000:00:01.0: bridge 32bit mmio: [0xcfe00000-0xcfefffff]
[    0.944527] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.944588] pci 0000:02:00.0: reg 10 64bit mmio: [0x000000-0x00ffff]
[    0.944636] pci 0000:02:00.0: supports D1
[    0.944637] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.944642] pci 0000:02:00.0: PME# disabled
[    0.944711] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.944716] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.944723] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.944785] pci 0000:03:00.0: reg 10 64bit mmio: [0x000000-0x003fff]
[    0.944794] pci 0000:03:00.0: reg 18 io port: [0x00-0xff]
[    0.944825] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.944838] pci 0000:03:00.0: supports D1 D2
[    0.944839] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.944844] pci 0000:03:00.0: PME# disabled
[    0.944911] pci 0000:00:1c.1: bridge io port: [0x00-0xfff]
[    0.944916] pci 0000:00:1c.1: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.944923] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.944978] pci 0000:00:1c.3: bridge io port: [0x00-0xfff]
[    0.944981] pci 0000:00:1c.3: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.944989] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.945029] pci 0000:0a:01.0: reg 10 32bit mmio: [0xff501000-0xff501fff]
[    0.945036] pci 0000:0a:01.0: reg 14 32bit mmio: [0xf8100000-0xf81007ff]
[    0.945075] pci 0000:0a:01.0: supports D1 D2
[    0.945076] pci 0000:0a:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.945081] pci 0000:0a:01.0: PME# disabled
[    0.945126] pci 0000:0a:01.2: reg 10 32bit mmio: [0xf8100800-0xf81008ff]
[    0.945178] pci 0000:0a:01.2: supports D1 D2
[    0.945180] pci 0000:0a:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.945184] pci 0000:0a:01.2: PME# disabled
[    0.945229] pci 0000:0a:01.3: reg 10 32bit mmio: [0xf8102000-0xf8102fff]
[    0.945280] pci 0000:0a:01.3: supports D1 D2
[    0.945282] pci 0000:0a:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.945286] pci 0000:0a:01.3: PME# disabled
[    0.945350] pci 0000:00:1e.0: transparent bridge
[    0.945356] pci 0000:00:1e.0: bridge 32bit mmio: [0xf8100000-0xf81fffff]
[    0.945389] bus 00 -> node 0
[    0.945397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.945623] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.945735] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.945860] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.945991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.946104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.957593] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.957706] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.957817] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 *6 7 10 12 14 15)
[    0.957931] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.958042] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.958154] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.958267] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.958378] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.958722] ACPI: WMI: Mapper loaded
[    0.958746] SCSI subsystem initialized
[    0.958746] libata version 3.00 loaded.
[    0.958746] usbcore: registered new interface driver usbfs
[    0.958746] usbcore: registered new interface driver hub
[    0.958746] usbcore: registered new device driver usb
[    0.958746] PCI: Using ACPI for IRQ routing
[    0.958746] pci 0000:00:1c.0: BAR 7: can't allocate resource
[    0.958746] pci 0000:00:1c.0: BAR 8: can't allocate resource
[    0.958746] pci 0000:00:1c.0: BAR 9: can't allocate resource
[    0.958746] pci 0000:00:1c.1: BAR 7: can't allocate resource
[    0.958746] pci 0000:00:1c.1: BAR 8: can't allocate resource
[    0.958746] pci 0000:00:1c.1: BAR 9: can't allocate resource
[    0.958746] pci 0000:00:1c.3: BAR 7: can't allocate resource
[    0.958746] pci 0000:00:1c.3: BAR 8: can't allocate resource
[    0.958746] pci 0000:00:1c.3: BAR 9: can't allocate resource
[    0.960011] Bluetooth: Core ver 2.13
[    0.960014] NET: Registered protocol family 31
[    0.960014] Bluetooth: HCI device and connection manager initialized
[    0.960014] Bluetooth: HCI socket layer initialized
[    0.960016] NET: Registered protocol family 8
[    0.960017] NET: Registered protocol family 20
[    0.960026] NetLabel: Initializing
[    0.960027] NetLabel:  domain hash size = 128
[    0.960028] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.960038] NetLabel:  unlabeled traffic allowed by default
[    0.960050] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.960055] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.964053] AppArmor: AppArmor Filesystem Enabled
[    0.968010] Switched to high resolution mode on CPU 0
[    0.968569] Switched to high resolution mode on CPU 1
[    0.968576] pnp: PnP ACPI init
[    0.968582] ACPI: bus type pnp registered
[    0.969505] pnp 00:04: io resource (0x2e-0x2f) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969508] pnp 00:04: io resource (0x4e-0x4f) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969510] pnp 00:04: io resource (0x61-0x61) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969512] pnp 00:04: io resource (0x63-0x63) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969515] pnp 00:04: io resource (0x65-0x65) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969517] pnp 00:04: io resource (0x67-0x67) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969519] pnp 00:04: io resource (0x68-0x68) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969521] pnp 00:04: io resource (0x6c-0x6c) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969523] pnp 00:04: io resource (0x70-0x70) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969525] pnp 00:04: io resource (0x80-0x80) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969527] pnp 00:04: io resource (0x92-0x92) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.969529] pnp 00:04: io resource (0xb2-0xb3) overlaps 0000:03:00.0 BAR 2 (0x0-0xff), disabling
[    0.970755] pnp: PnP ACPI: found 9 devices
[    0.970757] ACPI: ACPI bus type pnp unregistered
[    0.970759] PnPBIOS: Disabled by ACPI PNP
[    0.970767] system 00:02: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.970772] system 00:04: ioport range 0x3e0-0x3e1 has been reserved
[    0.970774] system 00:04: ioport range 0x400-0x47f has been reserved
[    0.970776] system 00:04: ioport range 0x680-0x69f has been reserved
[    0.970778] system 00:04: ioport range 0x480-0x48f has been reserved
[    0.970780] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.970782] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.970784] system 00:04: ioport range 0x1180-0x11ff has been reserved
[    0.970786] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.970788] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.970794] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.970796] system 00:08: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.970798] system 00:08: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.970800] system 00:08: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.970802] system 00:08: iomem range 0xe0000000-0xefffffff has been reserved
[    0.970804] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.005487] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.005489] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    1.005492] pci 0000:00:01.0:   MEM window: 0xcfe00000-0xcfefffff
[    1.005495] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.005507] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.005508] pci 0000:00:1c.0:   IO window: disabled
[    1.005514] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc00fffff
[    1.005518] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.005537] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    1.005540] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    1.005545] pci 0000:00:1c.1:   MEM window: 0xc0100000-0xc01fffff
[    1.005550] pci 0000:00:1c.1:   PREFETCH window: 0x000000c0200000-0x000000c02fffff
[    1.005557] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    1.005558] pci 0000:00:1c.3:   IO window: disabled
[    1.005563] pci 0000:00:1c.3:   MEM window: disabled
[    1.005567] pci 0000:00:1c.3:   PREFETCH window: disabled
[    1.005574] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
[    1.005575] pci 0000:00:1e.0:   IO window: disabled
[    1.005580] pci 0000:00:1e.0:   MEM window: 0xf8100000-0xf81fffff
[    1.005584] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.005596] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.005599] pci 0000:00:01.0: setting latency timer to 64
[    1.005606] pci 0000:00:1c.0: enabling device (0000 -> 0002)
[    1.005609] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.005615] pci 0000:00:1c.0: setting latency timer to 64
[    1.005622] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    1.005627] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.005632] pci 0000:00:1c.1: setting latency timer to 64
[    1.005640] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.005646] pci 0000:00:1c.3: setting latency timer to 64
[    1.005653] pci 0000:00:1e.0: setting latency timer to 64
[    1.005656] bus: 00 index 0 io port: [0x00-0xffff]
[    1.005658] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.005660] bus: 01 index 0 io port: [0x2000-0x2fff]
[    1.005662] bus: 01 index 1 mmio: [0xcfe00000-0xcfefffff]
[    1.005663] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    1.005665] bus: 01 index 3 mmio: [0x0-0x0]
[    1.005666] bus: 02 index 0 mmio: [0x0-0xfff]
[    1.005668] bus: 02 index 1 mmio: [0xc0000000-0xc00fffff]
[    1.005669] bus: 02 index 2 mmio: [0x0-0xfffff]
[    1.005671] bus: 02 index 3 mmio: [0x0-0x0]
[    1.005672] bus: 03 index 0 io port: [0x3000-0x3fff]
[    1.005674] bus: 03 index 1 mmio: [0xc0100000-0xc01fffff]
[    1.005675] bus: 03 index 2 mmio: [0xc0200000-0xc02fffff]
[    1.005677] bus: 03 index 3 mmio: [0x0-0x0]
[    1.005678] bus: 05 index 0 mmio: [0x0-0xfff]
[    1.005680] bus: 05 index 1 mmio: [0x0-0xfffff]
[    1.005681] bus: 05 index 2 mmio: [0x0-0xfffff]
[    1.005683] bus: 05 index 3 mmio: [0x0-0x0]
[    1.005684] bus: 0a index 0 mmio: [0x0-0x0]
[    1.005686] bus: 0a index 1 mmio: [0xf8100000-0xf81fffff]
[    1.005687] bus: 0a index 2 mmio: [0x0-0x0]
[    1.005688] bus: 0a index 3 io port: [0x00-0xffff]
[    1.005690] bus: 0a index 4 mmio: [0x000000-0xffffffff]
[    1.005696] NET: Registered protocol family 2
[    1.017039] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.017216] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.017472] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.017605] TCP: Hash tables configured (established 131072 bind 65536)
[    1.017607] TCP reno registered
[    1.021048] NET: Registered protocol family 1
[    1.021137] checking if image is initramfs... it is
[    1.523953] Freeing initrd memory: 7370k freed
[    1.523985] Simple Boot Flag at 0x36 set to 0x1
[    1.524129] cpufreq: No nForce2 chipset.
[    1.524238] audit: initializing netlink socket (disabled)
[    1.524253] type=2000 audit(1255886303.524:1): initialized
[    1.530388] highmem bounce pool size: 64 pages
[    1.530392] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.531418] VFS: Disk quotas dquot_6.5.1
[    1.531463] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.531937] fuse init (API version 7.10)
[    1.532003] msgmni has been set to 1672
[    1.532138] alg: No test for stdrng (krng)
[    1.532147] io scheduler noop registered
[    1.532148] io scheduler anticipatory registered
[    1.532150] io scheduler deadline registered
[    1.532160] io scheduler cfq registered (default)
[    1.532304] pci 0000:01:00.0: Boot video device
[    1.534873] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.534903] pcieport-driver 0000:00:01.0: found MSI capability
[    1.534923] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.534931] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.534942] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.534952] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.534994] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.535039] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.535069] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.535084] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.535093] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.535102] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.535170] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.535215] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.535245] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.535260] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.535270] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.535280] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.535345] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.535389] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.535419] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.535434] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.535446] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.535456] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.535528] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.535662] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.536674] ACPI: AC Adapter [ACAD] (on-line)
[    1.536740] ACPI: Battery Slot [BAT1] (battery absent)
[    1.536794] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.536796] ACPI: Power Button (FF) [PWRF]
[    1.536836] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.536838] ACPI: Power Button (CM) [PWRB]
[    1.536872] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.537016] ACPI: Lid Switch [LID]
[    1.537619] ACPI: SSDT BFD1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20061109)
[    1.537999] ACPI: SSDT BFD18620, 0594 (r1  PmRef  Cpu0Cst     3001 INTL 20061109)
[    1.539947] Monitor-Mwait will be used to enter C-1 state
[    1.539949] Monitor-Mwait will be used to enter C-2 state
[    1.539952] Monitor-Mwait will be used to enter C-3 state
[    1.539963] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.539983] processor ACPI_CPU:00: registered as cooling_device0
[    1.539986] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.540357] ACPI: SSDT BFD19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20061109)
[    1.540744] ACPI: SSDT BFD19F20, 008D (r1  PmRef    ApCst     3000 INTL 20061109)
[    1.541775] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.541789] processor ACPI_CPU:01: registered as cooling_device1
[    1.541792] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.547138] thermal LNXTHERM:01: registered as thermal_zone0
[    1.549185] ACPI: Thermal Zone [THRM] (39 C)
[    1.549224] isapnp: Scanning for PnP cards...
[    1.903053] isapnp: No Plug & Play device found
[    1.909189] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.909968] brd: module loaded
[    1.910201] loop: module loaded
[    1.910251] Fixed MDIO Bus: probed
[    1.910255] PPP generic driver version 2.4.2
[    1.910301] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.910323] Driver 'sd' needs updating - please use bus_type methods
[    1.910331] Driver 'sr' needs updating - please use bus_type methods
[    1.910360] ahci 0000:00:1f.2: version 3.0
[    1.910370] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.910405] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.910484] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.910486] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ems 
[    1.910491] ahci 0000:00:1f.2: setting latency timer to 64
[    1.910729] scsi0 : ahci
[    1.910791] scsi1 : ahci
[    1.910834] scsi2 : ahci
[    1.910876] scsi3 : ahci
[    1.910919] scsi4 : ahci
[    1.910962] scsi5 : ahci
[    1.911071] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 2299
[    1.911074] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 2299
[    1.911076] ata3: DUMMY
[    1.911077] ata4: DUMMY
[    1.911079] ata5: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404300 irq 2299
[    1.911082] ata6: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404380 irq 2299
[    2.228018] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.228576] ACPI Warning (nspredef-0852): \_SB_.PCI0.SAT0.PRT0._GTF: Return type mismatch - found Integer, expected Buffer [20080926]
[    2.228581] ata1.00: _GTF unexpected object type 0x1
[    2.299898] ata1.00: ATA-8: TOSHIBA MK3252GSX, LV010M, max UDMA/100
[    2.299901] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.300792] ata1.00: _GTF unexpected object type 0x1
[    2.300905] ata1.00: configured for UDMA/100
[    2.620017] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.621682] ACPI Warning (nspredef-0852): \_SB_.PCI0.SAT0.PRT1._GTF: Return type mismatch - found Integer, expected Buffer [20080926]
[    2.621686] ata2.00: _GTF unexpected object type 0x1
[    2.621689] ata2.00: ATAPI: PIONEER DVD-RW  DVRTD08A, 1.50, max UDMA/33
[    2.623709] ata2.00: _GTF unexpected object type 0x1
[    2.623729] ata2.00: configured for UDMA/33
[    3.392016] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.821182] ata5.00: ATA-8: TOSHIBA MK3252GSX, LV010M, max UDMA/100
[    3.821184] ata5.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.822044] ata5.00: configured for UDMA/100
[    4.140015] ata6: SATA link down (SStatus 0 SControl 300)
[    4.140096] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    4.140167] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.140180] sd 0:0:0:0: [sda] Write Protect is off
[    4.140182] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.140202] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.140248] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.140259] sd 0:0:0:0: [sda] Write Protect is off
[    4.140261] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.140280] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.140283]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    4.268746] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.268781] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.301005] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVRTD08A 1.50 PQ: 0 ANSI: 5
[    4.419993] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.419996] Uniform CD-ROM driver Revision: 3.20
[    4.420063] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.420092] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.420150] scsi 4:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    4.420212] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.420224] sd 4:0:0:0: [sdb] Write Protect is off
[    4.420226] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.420245] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.420283] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.420294] sd 4:0:0:0: [sdb] Write Protect is off
[    4.420296] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.420315] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.420318]  sdb: sdb1 sdb2
[    4.505275] sd 4:0:0:0: [sdb] Attached SCSI disk
[    4.505303] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    4.505845] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.505860] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    4.505871] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.505874] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.505917] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.509806] ehci_hcd 0000:00:1a.7: debug port 1
[    4.509812] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.509825] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf8404800
[    4.524006] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.524053] usb usb1: configuration #1 chosen from 1 choice
[    4.524073] hub 1-0:1.0: USB hub found
[    4.524079] hub 1-0:1.0: 6 ports detected
[    4.524166] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.524175] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.524178] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.524212] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.528119] ehci_hcd 0000:00:1d.7: debug port 1
[    4.528124] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.528135] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
[    4.544008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.544054] usb usb2: configuration #1 chosen from 1 choice
[    4.544074] hub 2-0:1.0: USB hub found
[    4.544079] hub 2-0:1.0: 6 ports detected
[    4.544153] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.544166] uhci_hcd: USB Universal Host Controller Interface driver
[    4.544181] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.544186] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.544189] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.544223] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.544253] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    4.544309] usb usb3: configuration #1 chosen from 1 choice
[    4.544328] hub 3-0:1.0: USB hub found
[    4.544333] hub 3-0:1.0: 2 ports detected
[    4.544401] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.544406] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.544409] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.544441] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.544472] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    4.544529] usb usb4: configuration #1 chosen from 1 choice
[    4.544553] hub 4-0:1.0: USB hub found
[    4.544557] hub 4-0:1.0: 2 ports detected
[    4.544621] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    4.544626] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    4.544629] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    4.544661] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    4.544685] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    4.544741] usb usb5: configuration #1 chosen from 1 choice
[    4.544759] hub 5-0:1.0: USB hub found
[    4.544764] hub 5-0:1.0: 2 ports detected
[    4.544826] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.544832] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.544835] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.544867] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    4.544890] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    4.544946] usb usb6: configuration #1 chosen from 1 choice
[    4.544964] hub 6-0:1.0: USB hub found
[    4.544969] hub 6-0:1.0: 2 ports detected
[    4.545037] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.545042] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.545045] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.545077] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    4.545100] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    4.545155] usb usb7: configuration #1 chosen from 1 choice
[    4.545175] hub 7-0:1.0: USB hub found
[    4.545180] hub 7-0:1.0: 2 ports detected
[    4.545246] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.545252] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.545255] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.545286] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    4.545318] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    4.545374] usb usb8: configuration #1 chosen from 1 choice
[    4.545392] hub 8-0:1.0: USB hub found
[    4.545397] hub 8-0:1.0: 2 ports detected
[    4.545498] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2A] at 0x60,0x64 irq 1,12
[    4.547874] i8042.c: Detected active multiplexing controller, rev 1.1.
[    4.549913] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.549917] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.549919] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.549921] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.549923] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.556027] mice: PS/2 mouse device common for all mice
[    4.572058] rtc_cmos 00:05: RTC can wake from S4
[    4.572082] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    4.572110] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    4.572152] device-mapper: uevent: version 1.0.3
[    4.572224] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.572274] device-mapper: multipath: version 1.0.5 loaded
[    4.572276] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.572335] EISA: Probing bus 0 at eisa.0
[    4.572341] Cannot allocate resource for EISA slot 1
[    4.572343] Cannot allocate resource for EISA slot 2
[    4.572345] Cannot allocate resource for EISA slot 3
[    4.572364] EISA: Detected 0 cards.
[    4.572448] cpuidle: using governor ladder
[    4.572538] cpuidle: using governor menu
[    4.572925] TCP cubic registered
[    4.573000] NET: Registered protocol family 10
[    4.573322] lo: Disabled Privacy Extensions
[    4.573576] NET: Registered protocol family 17
[    4.573588] Bluetooth: L2CAP ver 2.11
[    4.573590] Bluetooth: L2CAP socket layer initialized
[    4.573592] Bluetooth: SCO (Voice Link) ver 0.6
[    4.573593] Bluetooth: SCO socket layer initialized
[    4.573619] Bluetooth: RFCOMM socket layer initialized
[    4.573621] Marking TSC unstable due to TSC halts in idle
[    4.573627] Bluetooth: RFCOMM TTY layer initialized
[    4.573628] Bluetooth: RFCOMM ver 1.10
[    4.574254] Using IPI No-Shortcut mode
[    4.574311] registered taskstats version 1
[    4.574398]   Magic number: 13:451:340
[    4.574454] rtc_cmos 00:05: setting system clock to 2009-10-18 17:18:27 UTC (1255886307)
[    4.574457] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.574458] EDD information not available.
[    4.574670] Freeing unused kernel memory: 532k freed
[    4.574767] Write protecting the kernel text: 4120k
[    4.574803] Write protecting the kernel read-only data: 1524k
[    4.601796] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.728357] sky2 driver version 1.22
[    4.728395] sky2 0000:03:00.0: enabling device (0000 -> 0003)
[    4.728403] sky2 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.728418] sky2 0000:03:00.0: setting latency timer to 64
[    4.728455] sky2 0000:03:00.0: Yukon-2 Extreme chip revision 2
[    4.728626] sky2 0000:03:00.0: irq 2298 for MSI/MSI-X
[    4.729179] sky2 eth0: addr 00:23:8b:3c:66:5f
[    4.831113] ohci1394 0000:0a:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.881884] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[ff501000-ff5017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.940073] usb 2-3: new high speed USB device using ehci_hcd and address 3
[    5.113637] usb 2-3: configuration #1 chosen from 1 choice
[    5.202867] PM: Starting manual resume from disk
[    5.202870] PM: Resume from partition 8:6
[    5.202871] PM: Checking hibernation image.
[    5.203031] PM: Resume from disk failed.
[    5.252951] kjournald starting.  Commit interval 5 seconds
[    5.252972] EXT3-fs: mounted filesystem with ordered data mode.
[    5.464133] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    5.500048] Clocksource tsc unstable (delta = -347894520 ns)
[    5.641038] usb 6-2: configuration #1 chosen from 1 choice
[    5.885227] usb 8-1: new full speed USB device using uhci_hcd and address 2
[    6.050443] usb 8-1: configuration #1 chosen from 1 choice
[    6.152320] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b2400014922de]
[   10.316742] udev: starting version 141
[   10.425833] acpi device:03: registered as cooling_device2
[   10.426100] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input5
[   10.432287] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.846316] iTCO_vendor_support: vendor-support=0
[   10.877071] cfg80211: Using static regulatory domain info
[   10.877074] cfg80211: Regulatory domain: US
[   10.877075]   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.877077]   (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   10.877079]   (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.877081]   (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.877082]   (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.877084]   (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.877086]   (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   10.877112] cfg80211: Calling CRDA for country: US
[   10.891859] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.892063] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[   10.892138] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.047700] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   11.068194] usbcore: registered new interface driver hiddev
[   11.083326] Linux agpgart interface v0.103
[   11.083543] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input7
[   11.088350] generic-usb 0003:046D:C050.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-2/input0
[   11.088371] usbcore: registered new interface driver usbhid
[   11.088389] usbhid: v2.6:USB HID core driver
[   11.100930] cfg80211: Regulatory domain changed to country: US
[   11.100933]   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.100935]   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   11.100936]   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   11.100938]   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.100940]   (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.100941]   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   11.147568] sdhci: Secure Digital Host Controller Interface driver
[   11.147570] sdhci: Copyright(c) Pierre Ossman
[   11.202489] sdhci-pci 0000:0a:01.2: SDHCI controller found [1217:7120] (rev 2)
[   11.202505] sdhci-pci 0000:0a:01.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.202542] mmc0: Unknown controller version (2). You may experience problems.
[   11.202603] mmc0: SDHCI controller on PCI [0000:0a:01.2] using DMA
[   11.348390] Linux video capture interface: v2.00
[   11.403141] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.699899] uvcvideo: Found UVC 1.00 device CNA7137 (04f2:b064)
[   11.701283] input: CNA7137 as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input8
[   11.704120] usbcore: registered new interface driver uvcvideo
[   11.704124] USB Video Class driver (v0.1.0)
[   11.730098] ath9k 0000:02:00.0: enabling device (0000 -> 0002)
[   11.730106] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.730120] ath9k 0000:02:00.0: setting latency timer to 64
[   11.869334] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.869385] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.934212] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.934249] HDA Intel 0000:01:00.1: setting latency timer to 64
[   12.008662] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input9
[   12.164596] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.182600] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input10
[   12.234919] Registered led device: ath9k-phy0::radio
[   12.234953] Registered led device: ath9k-phy0::assoc
[   12.234985] Registered led device: ath9k-phy0::tx
[   12.235016] Registered led device: ath9k-phy0::rx
[   12.235022] phy0: Atheros AR9280 MAC/BB Rev:2 AR5133 RF Rev:d0: mem=0xf8040000, irq=17
[   12.392061] lp: driver loaded but no devices found
[   12.445553] Adding 6305472k swap on /dev/sda6.  Priority:-1 extents:1 across:6305472k
[   13.019558] EXT3 FS on sda5, internal journal
[   14.067942] type=1505 audit(1255879116.989:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2233
[   14.101528] type=1505 audit(1255879117.025:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2237
[   14.101598] type=1505 audit(1255879117.025:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2237
[   14.101628] type=1505 audit(1255879117.025:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2237
[   14.101657] type=1505 audit(1255879117.025:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2237
[   14.194881] type=1505 audit(1255879117.118:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2242
[   14.195005] type=1505 audit(1255879117.118:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2242
[   14.215112] type=1505 audit(1255879117.137:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2246
[   16.629263] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.629265] Bluetooth: BNEP filters: protocol multicast
[   16.635583] Bridge firewalling registered
[   17.571892] pci 0000:01:00.0: power state changed by ACPI to D0
[   17.571901] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.670944] [drm] Initialized drm 1.1.0 20060810
[   17.691106] pci 0000:01:00.0: setting latency timer to 64
[   17.691247] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   17.692900] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   17.927899] ppdev: user-space parallel port driver
[   18.622610] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   18.622667] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   18.622705] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   18.666783] [drm] Setting GART location based on new memory map
[   18.683629] [drm] Loading RV635 CP Microcode
[   18.683874] [drm] Loading RV635 PFP Microcode
[   18.698803] [drm] Resetting GPU
[   18.698859] [drm] writeback test succeeded in 1 usecs
[   22.077019] sky2 eth0: enabling interface
[   22.077162] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.102342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.490168] irq 16: nobody cared (try booting with the "irqpoll" option)
[   26.490173] Pid: 0, comm: swapper Not tainted 2.6.28-15-generic #52-Ubuntu
[   26.490175] Call Trace:
[   26.490181]  [<c04fe166>] ? printk+0x18/0x1a
[   26.490184]  [<c017ff67>] __report_bad_irq+0x27/0x90
[   26.490191]  [<f845fc46>] ? radeon_driver_irq_handler+0x26/0x170 [radeon]
[   26.490194]  [<c018012e>] note_interrupt+0x15e/0x1a0
[   26.490197]  [<c017ecf9>] ? handle_IRQ_event+0x39/0x70
[   26.490200]  [<c01806f3>] handle_fasteoi_irq+0xa3/0xd0
[   26.490203]  [<c015b9a7>] ? tick_check_idle+0x17/0x30
[   26.490206]  [<c010684e>] do_IRQ+0x7e/0xa0
[   26.490208]  [<c01051f3>] common_interrupt+0x23/0x30
[   26.490212]  [<c031a15d>] ? acpi_idle_enter_simple+0x153/0x18e
[   26.490215]  [<c040c5bf>] cpuidle_idle_call+0x6f/0xd0
[   26.490217]  [<c010285d>] cpu_idle+0x6d/0xd0
[   26.490220]  [<c04fbd9e>] start_secondary+0xbe/0xf0
[   26.490221] handlers:
[   26.490222] [<c03b7c20>] (usb_hcd_irq+0x0/0x90)
[   26.490226] [<f7d01860>] (ohci_irq_handler+0x0/0x7b0 [ohci1394])
[   26.490237] [<f7dc5030>] (sdhci_irq+0x0/0x240 [sdhci])
[   26.490241] [<f845fc20>] (radeon_driver_irq_handler+0x0/0x170 [radeon])
[   26.490247] Disabling IRQ #16

============ dmesg-wlan0 ============
[   22.102342] ADDRCONF(NETDEV_UP): wlan0: link is not ready

============ kernel version ============
2.6.28-15-generic i686

============ ifconfig ============
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3c:66:5f  
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
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:a7:f0:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-A7-F0-FF-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


============ iwconfig ============
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


============ lshw -C network ============
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:21:63:a7:f0:ff
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 00:23:8b:3c:66:5f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:70:ab:48:7d:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

============ iwlist scan ============
wlan0     No scan results


============ ubuntu version ============
Description:     Ubuntu 9.04

============ restarting the network ============
 * Reconfiguring network interfaces...
   ...done.

============ wireless card state ============
1

```

---

### Post by DanglingPointer on 2009-10-25
I'm interested in this as well.
I've got an AR922X with similar problem.

BUMP

---

### Post by Jguy on 2009-10-25
I am also experiencing troubles with this card. 

I can connect (barely) to any wireless network, but with some times, it takes either a REALLY long time or several tries to connect, or both, especially for WEP enabled networks. The window will come up that says to enter my WEP key, I do correctly and it fails to connect, sometimes I enter it again and then it works, sometimes I enter it 50 times and it works. Either that or it takes up to three minutes or more to connect to a network with over 50% signal strength.

Once I get connected, the speed is remarkable and non-problematic, but every 5 or so minutes, even with me bring right next to my router, the connection will time out, enough for aMSN and my FTP to disconnect from the server and reconnect. It isn't the router becuase my desktop (farther away from my router) does not have this problem. It is running Windows 7 though.

This laptop is running Ubuntu 9.04 32-bit. Please, any help that anyone can provide is most appreciated. I've already tried using madwifi and no luck.

Thanks.

---

### Post by zerosource on 2009-10-27
I'm having problem with this card too. :popcorn:

---

### Post by DanglingPointer on 2009-11-20
Come on experts, say something.  Thousands are suffering!

BUMP

---

### Post by jeannacav on 2009-11-20
> **DanglingPointer said:**
> Come on experts, say something.  Thousands are suffering!

BUMP

I am wondering if they are here this week:

----
The Ubuntu Developers Summit for Lucid Lynx will be held the week of 16-Nov-2009 till 20-Nov-2009 in Dallas, TX USA. Visit the the Ubuntu wiki for more information about UDS and how to participate remotely. 
-----
I have been checking back hourly to see if someone answered my calls for help yet.

I got an answer or 2 that repeated other things, but nothing that has worked yet.

Mine gets ready to turn on and the light blinks until the ubuntu boot is completed, then it shuts off.
Thankfully the wired network started to work with the update. Too bad it was the update that turned the wireless off!

jeanna

---

### Post by edkwok on 2009-11-20
Folks, I'm no expert but I did have similar problem with wireless but now I got it going on my new samgsung netbook running kubuntu 9.10 (latest release).

Here are some check steps to troubleshoot:
1- make sure your wireless card are up using ifconfig. ifconfig should return a list of interface current working. My wireless card came up under Wlan0. If ifconfig are not showing wlan0 than do a "ifconfig wlan0 up" not sure the syntax is correct, check the man page of ifconfig.
2- make sure you turn off all security lock down on your access point for trouble shooting. broadcast your SSID, do not lockdown MAC address, and no security encryption key use. Make it as easy as possible for your access point to be attach your wireless card.
3- login to your access point and make sure your wireless card and the access point are talking on the same channel.  This should be auto detect, but you never now when troubleshooting. To do this on your access point, switch the channel one at a time to see if you got some connection on your laptop, even see your SSID broadcasting is great start.
4-create a network connection on your desktop system tray for wireless profile. If you already have wire connection you should have and icon in your desktop system tray showing wire is not connected. Right click on it see if you can create a profile.
5-if you are working on a laptop, take your laptop to a internet cafe cite to see if you can join there wireless, or at least see their SSID broadcast.

The channel got me, it took awhile for me catch that. Hope this help.....

---

### Post by neoanderthal on 2009-11-21
have you folks seen this thread? 
[http://ubuntuforums.org/showthread.php?t=1332317](http://ubuntuforums.org/showthread.php?t=1332317)

I've got a Toshiba NB205 that uses the Atheros AR9285 wireless radio, and it's given me fits for every Linux distro. I followed the instructions, and I'm testing it right now. It seems to work fine.

neo

---

### Post by DanglingPointer on 2009-11-21
Thanks Edkwok and Neoanderthal.  I've given up with the AR922x and Jaunty working consistently!  I'm currently installing Karmic on a new disc and will give it another go with the new version.

Seriously, Canonical should invest some serious time on straightening out the wireless issues everyone is having.  It should just be plug and play and significantly less problem prone like the wired counterpart.

---

### Post by dave_r on 2009-11-21
How I made my AR922X work:

I have a D-Link DWA-552 with the Atheros AR922X chipset. It would not work with Ubuntu 9.10 (Karmic) until I followed the instructions on this page:

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

This page will have you download and install the latest kernel drivers. I followed the instructions to make and install the kernel modules, rebooted, waited for a minute, and things came up normally. I am posting this message using the card now.

I followed the instructions on 21 November 2009. The code changes daily, so things may be different for you.

My problem was that the card would be recognized but could not find any networks. Running "iwlist scanning" found no networks. lspci showed an AR922X chipset.

I hope someone finds this helpful.

Regards,
Dave Revell

---

### Post by X1R1 on 2009-11-25
Pretty weird, everyone has problems here with jaunty and I had this exact same card and had no troubles at all. Worked out of the box for me. Driver used is ath9k.

---

### Post by jeannacav on 2009-11-25
> **X1R1 said:**
> Pretty weird, everyone has problems here with jaunty and I had this exact same card and had no troubles at all. Worked out of the box for me. Driver used is ath9k.

I wish someone could help and make it clear withOUT things like
"...but you better make sure your ... are in order before you do this..."

eesh.
I like this os a lot and I like the community a lot too, but this seems like big trouble and I do not want to compile some sketchy business. I am way too new to do this manually.

I would sure love to get some step by step or really I would love it to be in synaptic.:D

jeanna

---

