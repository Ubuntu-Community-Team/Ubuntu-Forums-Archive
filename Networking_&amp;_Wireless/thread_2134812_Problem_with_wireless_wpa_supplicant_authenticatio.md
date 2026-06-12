---
title: "Problem with wireless wpa_supplicant authentication &lt; I think?"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by paulrollings on 2013-04-12
Hello - Really sorry I am a noob and have spent quite awhile floundering trying various things from forum posts but I'm not sure I am really getting anywhere. I am trying to connect to wifi; I can see wireless access points but fail to attach, really can't understand why. In the syslog I see this [FONT=courier new]**nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed**[/FONT] also see [FONT=courier new]**wpa_supplicant[970]: Authentication with 00:00:00:00:00:00 timed out**[/FONT] in the syslog. Troubleshooting hand-holding support really appreciated.

Below are varous log info and copy of [syslog (text file hosted on Microsoft Skydrive)]("http://sdrv.ms/YtZagi")


```

$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:05.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 PCI bridge: PLX Technology, Inc. PEX 8609 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch with DMA (rev ba)
04:00.1 System peripheral: PLX Technology, Inc. PEX 8609 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch with DMA (rev ba)
05:01.0 PCI bridge: PLX Technology, Inc. PEX 8609 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch with DMA (rev ba)
05:05.0 PCI bridge: PLX Technology, Inc. PEX 8609 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch with DMA (rev ba)
05:07.0 PCI bridge: PLX Technology, Inc. PEX 8609 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch with DMA (rev ba)
05:09.0 PCI bridge: PLX Technology, Inc. PEX 8609 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch with DMA (rev ba)
06:00.0 RAID bus controller: HighPoint Technologies, Inc. Device 0640 (rev 01)
07:00.0 RAID bus controller: HighPoint Technologies, Inc. Device 0640 (rev 01)
0a:00.0 VGA compatible controller: nVidia Corporation Device 1201 (rev a1)
0a:00.1 Audio device: nVidia Corporation Device 0e0c (rev a1)
0b:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
0b:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
0d:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
```

```

$ lsusb
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 14:da:e9:43:d9:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7ae0000-f7b00000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1916 (1.9 KB)  TX bytes:1916 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:13:01:c6:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:9 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


```
$ iwconfig
wlan0     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
$ lsmod
Module                  Size  Used by
nls_utf8               12557  1
isofs                  40283  1
binfmt_misc            17565  1
sco                    18131  2
bnep                   18308  2
l2cap                  53570  3 bnep
parport_pc             36959  0
ppdev                  17113  0
vesafb                 13761  1
snd_hda_codec_hdmi     28103  4
8712u                 345700  0
snd_hda_codec_realtek   336693  1
snd_hda_intel          33211  2
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
btusb                  18600  2
bluetooth              72448  8 sco,bnep,l2cap,btusb
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
r8712u                307592  0
psmouse                73535  0
nvidia              11919147  40
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i7core_edac            27903  0
soundcore              12680  1 snd
edac_core              53845  1 i7core_edac
serio_raw              13166  0
rr64x                 233293  3
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
xhci_hcd               77643  0
asus_atk0110           17976  0
lp                     17825  0
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0
firewire_ohci          40370  0
hid                    91020  1 usbhid
ahci                   25951  2
e1000e                159096  0
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_jmicron           12747  0
libahci                26642  1 ahci
```


```
$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=4b4e9404-12b2-458c-b621-c16eed777e1b ro ramdisk_size=2097152 quiet splash vt.handoff=7
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000096000 (usable)
[    0.000000]  BIOS-e820: 0000000000096000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf780000 (usable)
[    0.000000]  BIOS-e820: 00000000bf780000 - 00000000bf798000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf798000 - 00000000bf7dc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7dc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000640000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.5 present.
[    0.000000] DMI: System manufacturer System Product Name/Rampage III Extreme, BIOS 1401    05/12/2011
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x640000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-E7FFF write-through
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask E00000000 write-back
[    0.000000]   2 base 600000000 mask FC0000000 write-back
[    0.000000]   3 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   4 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bf800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbf780 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000bf780000
[    0.000000]  0000000000 - 0080000000 page 1G
[    0.000000]  0080000000 - 00bf600000 page 2M
[    0.000000]  00bf600000 - 00bf780000 page 4k
[    0.000000] kernel direct mapping tables up to bf780000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000640000000
[    0.000000]  0100000000 - 0640000000 page 1G
[    0.000000] kernel direct mapping tables up to 640000000 @ bf77f000-bf780000
[    0.000000] RAMDISK: 366e4000 - 3736a000
[    0.000000] ACPI: RSDP 00000000000fb200 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000bf780100 0005C (v01 051211 XSDT1500 20110512 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bf780290 000F4 (v03 051211 FACP1500 20110512 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bf7804b0 0D8B5 (v01  A1545 A1545000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 00000000bf798000 00040
[    0.000000] ACPI: APIC 00000000bf780390 000D8 (v01 051211 APIC1500 20110512 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bf780470 0003C (v01 051211 OEMMCFG  20110512 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bf798040 00072 (v01 051211 OEMB1500 20110512 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bf78f4b0 00038 (v01 051211 OEMHPET  20110512 MSFT 00000097)
[    0.000000] ACPI: OSFR 00000000bf78f4f0 000B0 (v01 051211 OEMOSFR  20110512 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bf79ba40 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000640000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000640000000
[    0.000000]   NODE_DATA [000000063fffb000 - 000000063fffffff]
[    0.000000]  [ffffea0000000000-ffffea0015dfffff] PMD -> [ffff880627e00000-ffff88063cdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00640000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000096
[    0.000000]     0: 0x00000100 -> 0x000bf780
[    0.000000]     0: 0x00100000 -> 0x00640000
[    0.000000] On node 0 totalpages: 6289158
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3912 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 765880 pages, LIFO batch:31
[    0.000000]   Normal zone: 75264 pages used for memmap
[    0.000000]   Normal zone: 5429760 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
[    0.000000] ACPI: IOAPIC (id[0x06] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 6, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec8a000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 7, version 32, address 0xfec8a000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 16 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] PM: Registered nosave memory: 0000000000096000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf780000 - 00000000bf798000
[    0.000000] PM: Registered nosave memory: 00000000bf798000 - 00000000bf7dc000
[    0.000000] PM: Registered nosave memory: 00000000bf7dc000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800bf400000 s84416 r8192 d22080 u131072
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 6199552
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=4b4e9404-12b2-458c-b621-c16eed777e1b ro ramdisk_size=2097152 quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 24718380k/26214400k available (5940k kernel code, 1057768k absent, 438252k reserved, 5017k data, 956k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:1216 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 251658240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 3337.602 MHz processor.
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6675.20 BogoMIPS (lpj=33376020)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000038] AppArmor: AppArmor initialized
[    0.000039] Yama: becoming mindful.
[    0.002176] Dentry cache hash table entries: 4194304 (order: 13, 33554432 bytes)
[    0.009036] Inode-cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.011977] Mount-cache hash table entries: 256
[    0.012077] Initializing cgroup subsys ns
[    0.012080] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.012081] Initializing cgroup subsys cpuacct
[    0.012085] Initializing cgroup subsys memory
[    0.012091] Initializing cgroup subsys devices
[    0.012093] Initializing cgroup subsys freezer
[    0.012094] Initializing cgroup subsys net_cls
[    0.012095] Initializing cgroup subsys blkio
[    0.012121] CPU: Physical Processor ID: 0
[    0.012122] CPU: Processor Core ID: 0
[    0.012126] mce: CPU supports 9 MCE banks
[    0.012140] CPU0: Thermal monitoring enabled (TM1)
[    0.012149] using mwait in idle threads.
[    0.013818] ACPI: Core revision 20110112
[    0.045586] ftrace: allocating 24314 entries in 96 pages
[    0.051413] Setting APIC routing to physical flat
[    0.051827] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.176526] CPU0: Intel(R) Core(TM) i7 CPU         980  @ 3.33GHz stepping 02
[    0.288691] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.288697] ... version:                3
[    0.288698] ... bit width:              48
[    0.288698] ... generic registers:      4
[    0.288699] ... value mask:             0000ffffffffffff
[    0.288701] ... max period:             000000007fffffff
[    0.288701] ... fixed-purpose events:   3
[    0.288702] ... event mask:             000000070000000f
[    0.289125] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 #8 #9 #10 #11
[    2.263529] Brought up 12 CPUs
[    2.263532] Total of 12 processors activated (80100.20 BogoMIPS).
[    2.272110] devtmpfs: initialized
[    2.272780] print_constraints: dummy:
[    2.272801] Time:  9:16:49  Date: 04/12/13
[    2.272827] NET: Registered protocol family 16
[    2.272895] Trying to unpack rootfs image as initramfs...
[    2.272906] ACPI: bus type pci registered
[    2.272954] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    2.272956] PCI: not using MMCONFIG
[    2.272957] PCI: Using configuration type 1 for base access
[    2.273465] bio: create slab <bio-0> at 0
[    2.274508] ACPI: EC: Look up EC in DSDT
[    2.275498] ACPI: Executed 1 blocks of module-level executable AML code
[    2.480389] Freeing initrd memory: 12824k freed
[    2.492916] ACPI: SSDT 00000000bf7980c0 03978 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    2.493281] ACPI: Dynamic OEM Table Load:
[    2.493283] ACPI: SSDT           (null) 03978 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
[    2.493459] ACPI: Interpreter enabled
[    2.493461] ACPI: (supports S0 S1 S3 S4 S5)
[    2.493477] ACPI: Using IOAPIC for interrupt routing
[    2.493495] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    2.494305] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    2.520921] ACPI: No dock devices found.
[    2.520923] HEST: Table not found.
[    2.520925] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    2.520982] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    2.521095] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    2.521096] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    2.521098] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    2.521099] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    2.521101] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    2.521102] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    2.521113] pci 0000:00:00.0: [8086:3405] type 0 class 0x000600
[    2.521148] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    2.521150] pci 0000:00:00.0: PME# disabled
[    2.521167] pci 0000:00:01.0: [8086:3408] type 1 class 0x000604
[    2.521201] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    2.521203] pci 0000:00:01.0: PME# disabled
[    2.521218] pci 0000:00:02.0: [8086:3409] type 1 class 0x000604
[    2.521252] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    2.521254] pci 0000:00:02.0: PME# disabled
[    2.521269] pci 0000:00:03.0: [8086:340a] type 1 class 0x000604
[    2.521303] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    2.521305] pci 0000:00:03.0: PME# disabled
[    2.521321] pci 0000:00:05.0: [8086:340c] type 1 class 0x000604
[    2.521354] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    2.521357] pci 0000:00:05.0: PME# disabled
[    2.521372] pci 0000:00:07.0: [8086:340e] type 1 class 0x000604
[    2.521407] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    2.521410] pci 0000:00:07.0: PME# disabled
[    2.521429] pci 0000:00:14.0: [8086:342e] type 0 class 0x000800
[    2.521476] pci 0000:00:14.1: [8086:3422] type 0 class 0x000800
[    2.521522] pci 0000:00:14.2: [8086:3423] type 0 class 0x000800
[    2.521565] pci 0000:00:14.3: [8086:3438] type 0 class 0x000800
[    2.521614] pci 0000:00:19.0: [8086:10ce] type 0 class 0x000200
[    2.521629] pci 0000:00:19.0: reg 10: [mem 0xf7ae0000-0xf7afffff]
[    2.521636] pci 0000:00:19.0: reg 14: [mem 0xf7adf000-0xf7adffff]
[    2.521642] pci 0000:00:19.0: reg 18: [io  0x8c00-0x8c1f]
[    2.521683] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    2.521685] pci 0000:00:19.0: PME# disabled
[    2.521700] pci 0000:00:1a.0: [8086:3a37] type 0 class 0x000c03
[    2.521735] pci 0000:00:1a.0: reg 20: [io  0x8480-0x849f]
[    2.521771] pci 0000:00:1a.1: [8086:3a38] type 0 class 0x000c03
[    2.521806] pci 0000:00:1a.1: reg 20: [io  0x8800-0x881f]
[    2.521842] pci 0000:00:1a.2: [8086:3a39] type 0 class 0x000c03
[    2.521877] pci 0000:00:1a.2: reg 20: [io  0x8880-0x889f]
[    2.521921] pci 0000:00:1a.7: [8086:3a3c] type 0 class 0x000c03
[    2.521938] pci 0000:00:1a.7: reg 10: [mem 0xf7ade000-0xf7ade3ff]
[    2.522000] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    2.522003] pci 0000:00:1a.7: PME# disabled
[    2.522021] pci 0000:00:1b.0: [8086:3a3e] type 0 class 0x000403
[    2.522034] pci 0000:00:1b.0: reg 10: [mem 0xf7ad8000-0xf7adbfff 64bit]
[    2.522078] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    2.522081] pci 0000:00:1b.0: PME# disabled
[    2.522097] pci 0000:00:1c.0: [8086:3a40] type 1 class 0x000604
[    2.522141] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    2.522144] pci 0000:00:1c.0: PME# disabled
[    2.522163] pci 0000:00:1c.4: [8086:3a48] type 1 class 0x000604
[    2.522207] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    2.522210] pci 0000:00:1c.4: PME# disabled
[    2.522229] pci 0000:00:1d.0: [8086:3a34] type 0 class 0x000c03
[    2.522265] pci 0000:00:1d.0: reg 20: [io  0x8000-0x801f]
[    2.522300] pci 0000:00:1d.1: [8086:3a35] type 0 class 0x000c03
[    2.522336] pci 0000:00:1d.1: reg 20: [io  0x8080-0x809f]
[    2.522371] pci 0000:00:1d.2: [8086:3a36] type 0 class 0x000c03
[    2.522407] pci 0000:00:1d.2: reg 20: [io  0x8400-0x841f]
[    2.522450] pci 0000:00:1d.7: [8086:3a3a] type 0 class 0x000c03
[    2.522468] pci 0000:00:1d.7: reg 10: [mem 0xf7add000-0xf7add3ff]
[    2.522530] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    2.522533] pci 0000:00:1d.7: PME# disabled
[    2.522548] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    2.522594] pci 0000:00:1f.0: [8086:3a16] type 0 class 0x000601
[    2.522664] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    2.522696] pci 0000:00:1f.2: [8086:3a20] type 0 class 0x000101
[    2.522708] pci 0000:00:1f.2: reg 10: [io  0x6c00-0x6c07]
[    2.522718] pci 0000:00:1f.2: reg 14: [io  0x6880-0x6883]
[    2.522724] pci 0000:00:1f.2: reg 18: [io  0x6800-0x6807]
[    2.522731] pci 0000:00:1f.2: reg 1c: [io  0x6480-0x6483]
[    2.522737] pci 0000:00:1f.2: reg 20: [io  0x6400-0x640f]
[    2.522743] pci 0000:00:1f.2: reg 24: [io  0x6080-0x608f]
[    2.522772] pci 0000:00:1f.3: [8086:3a30] type 0 class 0x000c05
[    2.522784] pci 0000:00:1f.3: reg 10: [mem 0xf7adc000-0xf7adc0ff 64bit]
[    2.522802] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    2.522828] pci 0000:00:1f.5: [8086:3a26] type 0 class 0x000101
[    2.522840] pci 0000:00:1f.5: reg 10: [io  0x7c00-0x7c07]
[    2.522846] pci 0000:00:1f.5: reg 14: [io  0x7880-0x7883]
[    2.522853] pci 0000:00:1f.5: reg 18: [io  0x7800-0x7807]
[    2.522859] pci 0000:00:1f.5: reg 1c: [io  0x7480-0x7483]
[    2.522865] pci 0000:00:1f.5: reg 20: [io  0x7400-0x740f]
[    2.522871] pci 0000:00:1f.5: reg 24: [io  0x7080-0x708f]
[    2.522932] pci 0000:01:00.0: [1b4b:91a3] type 0 class 0x000101
[    2.522940] pci 0000:01:00.0: reg 10: [io  0x9c00-0x9c07]
[    2.522947] pci 0000:01:00.0: reg 14: [io  0x9880-0x9883]
[    2.522953] pci 0000:01:00.0: reg 18: [io  0x9800-0x9807]
[    2.522959] pci 0000:01:00.0: reg 1c: [io  0x9480-0x9483]
[    2.522965] pci 0000:01:00.0: reg 20: [io  0x9400-0x940f]
[    2.522971] pci 0000:01:00.0: reg 24: [mem 0xf7bff800-0xf7bfffff]
[    2.522977] pci 0000:01:00.0: reg 30: [mem 0xf7be0000-0xf7beffff pref]
[    2.522994] pci 0000:01:00.0: PME# supported from D3hot
[    2.522997] pci 0000:01:00.0: PME# disabled
[    2.542676] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.542681] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    2.542685] pci 0000:00:01.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    2.542691] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.542748] pci 0000:02:00.0: [1033:0194] type 0 class 0x000c03
[    2.542762] pci 0000:02:00.0: reg 10: [mem 0xf7cfe000-0xf7cfffff 64bit]
[    2.542817] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    2.542820] pci 0000:02:00.0: PME# disabled
[    2.562623] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    2.562627] pci 0000:00:02.0:   bridge window [io  0xf000-0x0000] (disabled)
[    2.562631] pci 0000:00:02.0:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    2.562637] pci 0000:00:02.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.562676] pci 0000:00:03.0: PCI bridge to [bus 03-03]
[    2.562680] pci 0000:00:03.0:   bridge window [io  0xf000-0x0000] (disabled)
[    2.562685] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.562693] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.562729] pci 0000:04:00.0: [10b5:8609] type 1 class 0x000604
[    2.562738] pci 0000:04:00.0: reg 10: [mem 0xf7dc0000-0xf7ddffff]
[    2.562773] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    2.562775] pci 0000:04:00.0: PME# disabled
[    2.562799] pci 0000:04:00.1: [10b5:8609] type 0 class 0x000880
[    2.562808] pci 0000:04:00.1: reg 10: [mem 0xf7de0000-0xf7dfffff]
[    2.582567] pci 0000:00:05.0: PCI bridge to [bus 04-09]
[    2.582571] pci 0000:00:05.0:   bridge window [io  0xa000-0xbfff]
[    2.582575] pci 0000:00:05.0:   bridge window [mem 0xf7d00000-0xf7ffffff]
[    2.582581] pci 0000:00:05.0:   bridge window [mem 0xd3e00000-0xd3ffffff 64bit pref]
[    2.582640] pci 0000:05:01.0: [10b5:8609] type 1 class 0x000604
[    2.582683] pci 0000:05:01.0: PME# supported from D0 D3hot D3cold
[    2.582685] pci 0000:05:01.0: PME# disabled
[    2.582710] pci 0000:05:05.0: [10b5:8609] type 1 class 0x000604
[    2.582753] pci 0000:05:05.0: PME# supported from D0 D3hot D3cold
[    2.582755] pci 0000:05:05.0: PME# disabled
[    2.582778] pci 0000:05:07.0: [10b5:8609] type 1 class 0x000604
[    2.582821] pci 0000:05:07.0: PME# supported from D0 D3hot D3cold
[    2.582823] pci 0000:05:07.0: PME# disabled
[    2.582846] pci 0000:05:09.0: [10b5:8609] type 1 class 0x000604
[    2.582889] pci 0000:05:09.0: PME# supported from D0 D3hot D3cold
[    2.582891] pci 0000:05:09.0: PME# disabled
[    2.582921] pci 0000:04:00.0: PCI bridge to [bus 05-09]
[    2.582925] pci 0000:04:00.0:   bridge window [io  0xa000-0xbfff]
[    2.582928] pci 0000:04:00.0:   bridge window [mem 0xf7e00000-0xf7ffffff]
[    2.582932] pci 0000:04:00.0:   bridge window [mem 0xd3e00000-0xd3ffffff 64bit pref]
[    2.582977] pci 0000:06:00.0: [1103:0640] type 0 class 0x000104
[    2.582988] pci 0000:06:00.0: reg 10: [io  0xac00-0xac07]
[    2.582997] pci 0000:06:00.0: reg 14: [io  0xa880-0xa883]
[    2.583005] pci 0000:06:00.0: reg 18: [io  0xa800-0xa807]
[    2.583013] pci 0000:06:00.0: reg 1c: [io  0xa480-0xa483]
[    2.583021] pci 0000:06:00.0: reg 20: [io  0xa400-0xa40f]
[    2.583029] pci 0000:06:00.0: reg 24: [mem 0xf7eff800-0xf7efffff]
[    2.583037] pci 0000:06:00.0: reg 30: [mem 0xf7ee0000-0xf7eeffff pref]
[    2.583060] pci 0000:06:00.0: PME# supported from D3hot
[    2.583063] pci 0000:06:00.0: PME# disabled
[    2.602515] pci 0000:05:01.0: PCI bridge to [bus 06-06]
[    2.602522] pci 0000:05:01.0:   bridge window [io  0xa000-0xafff]
[    2.602526] pci 0000:05:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    2.602533] pci 0000:05:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.602596] pci 0000:07:00.0: [1103:0640] type 0 class 0x000104
[    2.602607] pci 0000:07:00.0: reg 10: [io  0xbc00-0xbc07]
[    2.602615] pci 0000:07:00.0: reg 14: [io  0xb880-0xb883]
[    2.602623] pci 0000:07:00.0: reg 18: [io  0xb800-0xb807]
[    2.602631] pci 0000:07:00.0: reg 1c: [io  0xb480-0xb483]
[    2.602639] pci 0000:07:00.0: reg 20: [io  0xb400-0xb40f]
[    2.602648] pci 0000:07:00.0: reg 24: [mem 0xf7fff800-0xf7ffffff]
[    2.602656] pci 0000:07:00.0: reg 30: [mem 0xf7fe0000-0xf7feffff pref]
[    2.602678] pci 0000:07:00.0: PME# supported from D3hot
[    2.602682] pci 0000:07:00.0: PME# disabled
[    2.622463] pci 0000:05:05.0: PCI bridge to [bus 07-07]
[    2.622469] pci 0000:05:05.0:   bridge window [io  0xb000-0xbfff]
[    2.622474] pci 0000:05:05.0:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    2.622480] pci 0000:05:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.622526] pci 0000:05:07.0: PCI bridge to [bus 08-08]
[    2.622536] pci 0000:05:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    2.622539] pci 0000:05:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.622544] pci 0000:05:07.0:   bridge window [mem 0xd3e00000-0xd3efffff 64bit pref]
[    2.622577] pci 0000:05:09.0: PCI bridge to [bus 09-09]
[    2.622582] pci 0000:05:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    2.622584] pci 0000:05:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.622589] pci 0000:05:09.0:   bridge window [mem 0xd3f00000-0xd3ffffff 64bit pref]
[    2.622640] pci 0000:0a:00.0: [10de:1201] type 0 class 0x000300
[    2.622648] pci 0000:0a:00.0: reg 10: [mem 0xf8000000-0xf9ffffff]
[    2.622657] pci 0000:0a:00.0: reg 14: [mem 0xd8000000-0xdfffffff 64bit pref]
[    2.622665] pci 0000:0a:00.0: reg 1c: [mem 0xd4000000-0xd7ffffff 64bit pref]
[    2.622671] pci 0000:0a:00.0: reg 24: [io  0xcc00-0xcc7f]
[    2.622677] pci 0000:0a:00.0: reg 30: [mem 0xfbc00000-0xfbc7ffff pref]
[    2.622713] pci 0000:0a:00.1: [10de:0e0c] type 0 class 0x000403
[    2.622721] pci 0000:0a:00.1: reg 10: [mem 0xfbcfc000-0xfbcfffff]
[    2.642411] pci 0000:00:07.0: PCI bridge to [bus 0a-0a]
[    2.642416] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
[    2.642420] pci 0000:00:07.0:   bridge window [mem 0xf8000000-0xfbcfffff]
[    2.642426] pci 0000:00:07.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    2.642469] pci 0000:00:1c.0: PCI bridge to [bus 0c-0c]
[    2.642476] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    2.642479] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    2.642484] pci 0000:00:1c.0:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    2.642530] pci 0000:0b:00.0: [197b:2363] type 0 class 0x000101
[    2.642610] pci 0000:0b:00.0: reg 24: [mem 0xfbdfe000-0xfbdfffff]
[    2.642649] pci 0000:0b:00.0: PME# supported from D3hot
[    2.642653] pci 0000:0b:00.0: PME# disabled
[    2.642679] pci 0000:0b:00.1: [197b:2363] type 0 class 0x000101
[    2.642701] pci 0000:0b:00.1: reg 10: [io  0xdc00-0xdc07]
[    2.642713] pci 0000:0b:00.1: reg 14: [io  0xd880-0xd883]
[    2.642725] pci 0000:0b:00.1: reg 18: [io  0xd800-0xd807]
[    2.642737] pci 0000:0b:00.1: reg 1c: [io  0xd480-0xd483]
[    2.642748] pci 0000:0b:00.1: reg 20: [io  0xd400-0xd40f]
[    2.642812] pci 0000:0b:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    2.642823] pci 0000:00:1c.4: PCI bridge to [bus 0b-0b]
[    2.642825] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    2.642828] pci 0000:00:1c.4:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    2.642833] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.642860] pci 0000:0d:02.0: [1106:3044] type 0 class 0x000c00
[    2.642875] pci 0000:0d:02.0: reg 10: [mem 0xfbeff000-0xfbeff7ff]
[    2.642884] pci 0000:0d:02.0: reg 14: [io  0xec00-0xec7f]
[    2.642936] pci 0000:0d:02.0: supports D2
[    2.642937] pci 0000:0d:02.0: PME# supported from D2 D3hot D3cold
[    2.642940] pci 0000:0d:02.0: PME# disabled
[    2.642976] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d] (subtractive decode)
[    2.642978] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    2.642981] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    2.642985] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    2.642987] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    2.642988] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    2.642990] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    2.642991] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    2.642993] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    2.642994] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    2.643018] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    2.643175] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE5._PRT]
[    2.643201] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    2.643246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    2.643272] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE1._PRT]
[    2.643290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE2._PRT]
[    2.643310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE3._PRT]
[    2.643329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE7._PRT]
[    2.643354] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    2.643374]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    2.652125] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    2.652155] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    2.652182] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12 *14 15)
[    2.652210] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    2.652241] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 *15)
[    2.652269] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 6 7 10 11 12 14 15)
[    2.652298] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    2.652326] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    2.652404] vgaarb: device added: PCI:0000:0a:00.0,decodes=io+mem,owns=io+mem,locks=none
[    2.652407] vgaarb: loaded
[    2.652515] SCSI subsystem initialized
[    2.652556] libata version 3.00 loaded.
[    2.652584] usbcore: registered new interface driver usbfs
[    2.652589] usbcore: registered new interface driver hub
[    2.652607] usbcore: registered new device driver usb
[    2.652697] wmi: Mapper loaded
[    2.652698] PCI: Using ACPI for IRQ routing
[    2.652700] PCI: pci_cache_line_size set to 64 bytes
[    2.652798] reserve RAM buffer: 0000000000096000 - 000000000009ffff
[    2.652800] reserve RAM buffer: 00000000bf780000 - 00000000bfffffff
[    2.652861] NetLabel: Initializing
[    2.652862] NetLabel:  domain hash size = 128
[    2.652863] NetLabel:  protocols = UNLABELED CIPSOv4
[    2.652869] NetLabel:  unlabeled traffic allowed by default
[    2.652896] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    2.652898] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    2.654910] Switching to clocksource hpet
[    2.658853] AppArmor: AppArmor Filesystem Enabled
[    2.658864] pnp: PnP ACPI init
[    2.658871] ACPI: bus type pnp registered
[    2.658931] pnp 00:00: [bus 00-ff]
[    2.658933] pnp 00:00: [io  0x0cf8-0x0cff]
[    2.658934] pnp 00:00: [io  0x0000-0x0cf7 window]
[    2.658935] pnp 00:00: [io  0x0d00-0xffff window]
[    2.658937] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    2.658938] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    2.658939] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    2.658940] pnp 00:00: [mem 0xf0000000-0xfed8ffff window]
[    2.658972] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    2.658978] pnp 00:01: [mem 0xfbf00000-0xfbffffff]
[    2.658979] pnp 00:01: [mem 0xfc000000-0xfcffffff]
[    2.658980] pnp 00:01: [mem 0xfd000000-0xfdffffff]
[    2.658982] pnp 00:01: [mem 0xfe000000-0xfebfffff]
[    2.658983] pnp 00:01: [mem 0xfec8a000-0xfec8afff]
[    2.658984] pnp 00:01: [mem 0xfed10000-0xfed10fff]
[    2.659022] system 00:01: [mem 0xfbf00000-0xfbffffff] has been reserved
[    2.659024] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    2.659025] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    2.659027] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    2.659029] system 00:01: [mem 0xfec8a000-0xfec8afff] could not be reserved
[    2.659030] system 00:01: [mem 0xfed10000-0xfed10fff] has been reserved
[    2.659032] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.659058] pnp 00:02: [dma 4]
[    2.659059] pnp 00:02: [io  0x0000-0x000f]
[    2.659060] pnp 00:02: [io  0x0081-0x0083]
[    2.659061] pnp 00:02: [io  0x0087]
[    2.659062] pnp 00:02: [io  0x0089-0x008b]
[    2.659063] pnp 00:02: [io  0x008f]
[    2.659064] pnp 00:02: [io  0x00c0-0x00df]
[    2.659080] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    2.659087] pnp 00:03: [io  0x0070-0x0071]
[    2.659095] pnp 00:03: [irq 8]
[    2.659114] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    2.659120] pnp 00:04: [io  0x0061]
[    2.659135] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    2.659140] pnp 00:05: [io  0x00f0-0x00ff]
[    2.659144] pnp 00:05: [irq 13]
[    2.659161] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    2.659271] pnp 00:06: [io  0x0000-0xffffffffffffffff disabled]
[    2.659273] pnp 00:06: [io  0x0000-0xffffffffffffffff disabled]
[    2.659274] pnp 00:06: [io  0x0290-0x029f]
[    2.659312] system 00:06: [io  0x0290-0x029f] has been reserved
[    2.659314] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.659406] pnp 00:07: [io  0x0010-0x001f]
[    2.659407] pnp 00:07: [io  0x0022-0x003f]
[    2.659408] pnp 00:07: [io  0x0044-0x004d]
[    2.659409] pnp 00:07: [io  0x0050-0x005f]
[    2.659410] pnp 00:07: [io  0x0062-0x0063]
[    2.659412] pnp 00:07: [io  0x0065-0x006f]
[    2.659413] pnp 00:07: [io  0x0072-0x007f]
[    2.659414] pnp 00:07: [io  0x0080]
[    2.659415] pnp 00:07: [io  0x0084-0x0086]
[    2.659416] pnp 00:07: [io  0x0088]
[    2.659417] pnp 00:07: [io  0x008c-0x008e]
[    2.659418] pnp 00:07: [io  0x0090-0x009f]
[    2.659420] pnp 00:07: [io  0x00a2-0x00bf]
[    2.659421] pnp 00:07: [io  0x00e0-0x00ef]
[    2.659422] pnp 00:07: [io  0x04d0-0x04d1]
[    2.659423] pnp 00:07: [io  0x0800-0x087f]
[    2.659424] pnp 00:07: [io  0x0400-0x03ff disabled]
[    2.659425] pnp 00:07: [io  0x0500-0x057f]
[    2.659427] pnp 00:07: [mem 0xfed1c000-0xfed1ffff]
[    2.659428] pnp 00:07: [mem 0xfed20000-0xfed3ffff]
[    2.659429] pnp 00:07: [mem 0xfed40000-0xfed8ffff]
[    2.659497] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    2.659500] system 00:07: [io  0x0800-0x087f] has been reserved
[    2.659501] system 00:07: [io  0x0500-0x057f] has been reserved
[    2.659503] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    2.659504] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    2.659506] system 00:07: [mem 0xfed40000-0xfed8ffff] has been reserved
[    2.659508] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.659552] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    2.659571] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
[    2.659602] pnp 00:09: [mem 0xffa00000-0xffbfffff]
[    2.659603] pnp 00:09: [mem 0xffe00000-0xffffffff]
[    2.659623] pnp 00:09: Plug and Play ACPI device, IDs INT0800 (active)
[    2.659649] pnp 00:0a: [mem 0xffc00000-0xffdfffff]
[    2.659686] system 00:0a: [mem 0xffc00000-0xffdfffff] has been reserved
[    2.659688] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.659739] pnp 00:0b: [io  0x0060]
[    2.659740] pnp 00:0b: [io  0x0064]
[    2.659741] pnp 00:0b: [mem 0xfec00000-0xfec00fff]
[    2.659743] pnp 00:0b: [mem 0xfee00000-0xfee00fff]
[    2.659783] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    2.659785] system 00:0b: [mem 0xfee00000-0xfee00fff] has been reserved
[    2.659787] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.659832] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    2.659870] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    2.659872] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    2.659982] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    2.659983] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    2.659984] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    2.659985] pnp 00:0d: [mem 0x00100000-0xbfffffff]
[    2.659986] pnp 00:0d: [mem 0xfed90000-0xffffffff]
[    2.660036] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    2.660038] system 00:0d: [mem 0x000c0000-0x000cffff] has been reserved
[    2.660039] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    2.660041] system 00:0d: [mem 0x00100000-0xbfffffff] could not be reserved
[    2.660043] system 00:0d: [mem 0xfed90000-0xffffffff] could not be reserved
[    2.660045] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    2.660128] pnp: PnP ACPI: found 14 devices
[    2.660129] ACPI: ACPI bus type pnp unregistered
[    2.662349] Switched to NOHz mode on CPU #0
[    2.662396] Switched to NOHz mode on CPU #9
[    2.662402] Switched to NOHz mode on CPU #2
[    2.662419] Switched to NOHz mode on CPU #7
[    2.662427] Switched to NOHz mode on CPU #6
[    2.662438] Switched to NOHz mode on CPU #10
[    2.662446] Switched to NOHz mode on CPU #1
[    2.662455] Switched to NOHz mode on CPU #3
[    2.662462] Switched to NOHz mode on CPU #11
[    2.662463] Switched to NOHz mode on CPU #4
[    2.662476] Switched to NOHz mode on CPU #5
[    2.662484] Switched to NOHz mode on CPU #8
[    2.665772] pci 0000:00:1c.0: BAR 14: assigned [mem 0xc0000000-0xc03fffff]
[    2.665774] pci 0000:00:1c.4: BAR 15: assigned [mem 0xc0400000-0xc05fffff 64bit pref]
[    2.665776] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    2.665778] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    2.665779] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    2.665782] pci 0000:00:01.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    2.665785] pci 0000:00:01.0:   bridge window [mem pref disabled]
[    2.665788] pci 0000:00:02.0: PCI bridge to [bus 02-02]
[    2.665789] pci 0000:00:02.0:   bridge window [io  disabled]
[    2.665792] pci 0000:00:02.0:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    2.665795] pci 0000:00:02.0:   bridge window [mem pref disabled]
[    2.665798] pci 0000:00:03.0: PCI bridge to [bus 03-03]
[    2.665799] pci 0000:00:03.0:   bridge window [io  disabled]
[    2.665802] pci 0000:00:03.0:   bridge window [mem disabled]
[    2.665804] pci 0000:00:03.0:   bridge window [mem pref disabled]
[    2.665808] pci 0000:05:01.0: PCI bridge to [bus 06-06]
[    2.665810] pci 0000:05:01.0:   bridge window [io  0xa000-0xafff]
[    2.665813] pci 0000:05:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    2.665816] pci 0000:05:01.0:   bridge window [mem pref disabled]
[    2.665820] pci 0000:05:05.0: PCI bridge to [bus 07-07]
[    2.665822] pci 0000:05:05.0:   bridge window [io  0xb000-0xbfff]
[    2.665825] pci 0000:05:05.0:   bridge window [mem 0xf7f00000-0xf7ffffff]
[    2.665828] pci 0000:05:05.0:   bridge window [mem pref disabled]
[    2.665832] pci 0000:05:07.0: PCI bridge to [bus 08-08]
[    2.665833] pci 0000:05:07.0:   bridge window [io  disabled]
[    2.665836] pci 0000:05:07.0:   bridge window [mem disabled]
[    2.665839] pci 0000:05:07.0:   bridge window [mem 0xd3e00000-0xd3efffff 64bit pref]
[    2.665843] pci 0000:05:09.0: PCI bridge to [bus 09-09]
[    2.665844] pci 0000:05:09.0:   bridge window [io  disabled]
[    2.665847] pci 0000:05:09.0:   bridge window [mem disabled]
[    2.665850] pci 0000:05:09.0:   bridge window [mem 0xd3f00000-0xd3ffffff 64bit pref]
[    2.665854] pci 0000:04:00.0: PCI bridge to [bus 05-09]
[    2.665856] pci 0000:04:00.0:   bridge window [io  0xa000-0xbfff]
[    2.665859] pci 0000:04:00.0:   bridge window [mem 0xf7e00000-0xf7ffffff]
[    2.665862] pci 0000:04:00.0:   bridge window [mem 0xd3e00000-0xd3ffffff 64bit pref]
[    2.665866] pci 0000:00:05.0: PCI bridge to [bus 04-09]
[    2.665868] pci 0000:00:05.0:   bridge window [io  0xa000-0xbfff]
[    2.665871] pci 0000:00:05.0:   bridge window [mem 0xf7d00000-0xf7ffffff]
[    2.665873] pci 0000:00:05.0:   bridge window [mem 0xd3e00000-0xd3ffffff 64bit pref]
[    2.665877] pci 0000:00:07.0: PCI bridge to [bus 0a-0a]
[    2.665879] pci 0000:00:07.0:   bridge window [io  0xc000-0xcfff]
[    2.665882] pci 0000:00:07.0:   bridge window [mem 0xf8000000-0xfbcfffff]
[    2.665884] pci 0000:00:07.0:   bridge window [mem 0xd4000000-0xdfffffff 64bit pref]
[    2.665888] pci 0000:00:1c.0: PCI bridge to [bus 0c-0c]
[    2.665890] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    2.665893] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc03fffff]
[    2.665896] pci 0000:00:1c.0:   bridge window [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    2.665900] pci 0000:00:1c.4: PCI bridge to [bus 0b-0b]
[    2.665902] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    2.665906] pci 0000:00:1c.4:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    2.665908] pci 0000:00:1c.4:   bridge window [mem 0xc0400000-0xc05fffff 64bit pref]
[    2.665913] pci 0000:00:1e.0: PCI bridge to [bus 0d-0d]
[    2.665915] pci 0000:00:1e.0:   bridge window [io  0xe000-0xefff]
[    2.665918] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    2.665921] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    2.665929] pci 0000:00:01.0: setting latency timer to 64
[    2.665933] pci 0000:00:02.0: setting latency timer to 64
[    2.665937] pci 0000:00:03.0: setting latency timer to 64
[    2.665941] pci 0000:00:05.0: setting latency timer to 64
[    2.665952] pci 0000:04:00.0: PCI INT A -> GSI 26 (level, low) -> IRQ 26
[    2.665954] pci 0000:04:00.0: setting latency timer to 64
[    2.665962] pci 0000:05:01.0: PCI INT A -> GSI 25 (level, low) -> IRQ 25
[    2.665965] pci 0000:05:01.0: setting latency timer to 64
[    2.665969] pci 0000:05:05.0: PCI INT A -> GSI 25 (level, low) -> IRQ 25
[    2.665972] pci 0000:05:05.0: setting latency timer to 64
[    2.665979] pci 0000:05:07.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
[    2.665982] pci 0000:05:07.0: setting latency timer to 64
[    2.665986] pci 0000:05:09.0: PCI INT A -> GSI 25 (level, low) -> IRQ 25
[    2.665988] pci 0000:05:09.0: setting latency timer to 64
[    2.665993] pci 0000:00:07.0: setting latency timer to 64
[    2.665996] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    2.666001] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.666004] pci 0000:00:1c.0: setting latency timer to 64
[    2.666008] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.666011] pci 0000:00:1c.4: setting latency timer to 64
[    2.666015] pci 0000:00:1e.0: setting latency timer to 64
[    2.666017] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    2.666019] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    2.666020] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    2.666021] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    2.666023] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff]
[    2.666024] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    2.666025] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    2.666027] pci_bus 0000:01: resource 1 [mem 0xf7b00000-0xf7bfffff]
[    2.666028] pci_bus 0000:02: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    2.666029] pci_bus 0000:04: resource 0 [io  0xa000-0xbfff]
[    2.666031] pci_bus 0000:04: resource 1 [mem 0xf7d00000-0xf7ffffff]
[    2.666032] pci_bus 0000:04: resource 2 [mem 0xd3e00000-0xd3ffffff 64bit pref]
[    2.666033] pci_bus 0000:05: resource 0 [io  0xa000-0xbfff]
[    2.666035] pci_bus 0000:05: resource 1 [mem 0xf7e00000-0xf7ffffff]
[    2.666036] pci_bus 0000:05: resource 2 [mem 0xd3e00000-0xd3ffffff 64bit pref]
[    2.666037] pci_bus 0000:06: resource 0 [io  0xa000-0xafff]
[    2.666039] pci_bus 0000:06: resource 1 [mem 0xf7e00000-0xf7efffff]
[    2.666040] pci_bus 0000:07: resource 0 [io  0xb000-0xbfff]
[    2.666041] pci_bus 0000:07: resource 1 [mem 0xf7f00000-0xf7ffffff]
[    2.666043] pci_bus 0000:08: resource 2 [mem 0xd3e00000-0xd3efffff 64bit pref]
[    2.666044] pci_bus 0000:09: resource 2 [mem 0xd3f00000-0xd3ffffff 64bit pref]
[    2.666045] pci_bus 0000:0a: resource 0 [io  0xc000-0xcfff]
[    2.666047] pci_bus 0000:0a: resource 1 [mem 0xf8000000-0xfbcfffff]
[    2.666048] pci_bus 0000:0a: resource 2 [mem 0xd4000000-0xdfffffff 64bit pref]
[    2.666049] pci_bus 0000:0c: resource 0 [io  0x1000-0x1fff]
[    2.666051] pci_bus 0000:0c: resource 1 [mem 0xc0000000-0xc03fffff]
[    2.666052] pci_bus 0000:0c: resource 2 [mem 0xf6f00000-0xf6ffffff 64bit pref]
[    2.666053] pci_bus 0000:0b: resource 0 [io  0xd000-0xdfff]
[    2.666055] pci_bus 0000:0b: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    2.666056] pci_bus 0000:0b: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    2.666057] pci_bus 0000:0d: resource 0 [io  0xe000-0xefff]
[    2.666059] pci_bus 0000:0d: resource 1 [mem 0xfbe00000-0xfbefffff]
[    2.666060] pci_bus 0000:0d: resource 4 [io  0x0000-0x0cf7]
[    2.666061] pci_bus 0000:0d: resource 5 [io  0x0d00-0xffff]
[    2.666063] pci_bus 0000:0d: resource 6 [mem 0x000a0000-0x000bffff]
[    2.666064] pci_bus 0000:0d: resource 7 [mem 0x000d0000-0x000dffff]
[    2.666065] pci_bus 0000:0d: resource 8 [mem 0xc0000000-0xdfffffff]
[    2.666067] pci_bus 0000:0d: resource 9 [mem 0xf0000000-0xfed8ffff]
[    2.666085] NET: Registered protocol family 2
[    2.666347] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    2.667291] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.668351] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.668472] TCP: Hash tables configured (established 524288 bind 65536)
[    2.668474] TCP reno registered
[    2.668505] UDP hash table entries: 16384 (order: 7, 524288 bytes)
[    2.668603] UDP-Lite hash table entries: 16384 (order: 7, 524288 bytes)
[    2.668741] NET: Registered protocol family 1
[    2.668938] pci 0000:0a:00.0: Boot video device
[    2.668953] PCI: CLS 256 bytes, default 64
[    2.668955] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.668956] Placing 64MB software IO TLB between ffff8800bb37c000 - ffff8800bf37c000
[    2.668957] software IO TLB at phys 0xbb37c000 - 0xbf37c000
[    2.669506] audit: initializing netlink socket (disabled)
[    2.669511] type=2000 audit(1365758209.400:1): initialized
[    2.678928] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.680044] VFS: Disk quotas dquot_6.5.2
[    2.680083] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.680483] fuse init (API version 7.16)
[    2.680544] msgmni has been set to 32768
[    2.680695] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    2.680715] io scheduler noop registered
[    2.680716] io scheduler deadline registered
[    2.680742] io scheduler cfq registered (default)
[    2.680943] pcieport 0000:00:1c.0: setting latency timer to 64
[    2.680977] pcieport 0000:00:1c.0: irq 64 for MSI/MSI-X
[    2.681022] pcieport 0000:00:1c.4: setting latency timer to 64
[    2.681052] pcieport 0000:00:1c.4: irq 65 for MSI/MSI-X
[    2.681096] pcieport 0000:04:00.0: setting latency timer to 64
[    2.681126] pcieport 0000:04:00.0: irq 66 for MSI/MSI-X
[    2.681171] pcieport 0000:05:01.0: setting latency timer to 64
[    2.681201] pcieport 0000:05:01.0: irq 67 for MSI/MSI-X
[    2.681245] pcieport 0000:05:05.0: setting latency timer to 64
[    2.681275] pcieport 0000:05:05.0: irq 68 for MSI/MSI-X
[    2.681318] pcieport 0000:05:07.0: setting latency timer to 64
[    2.681348] pcieport 0000:05:07.0: irq 69 for MSI/MSI-X
[    2.681394] pcieport 0000:05:09.0: setting latency timer to 64
[    2.681425] pcieport 0000:05:09.0: irq 70 for MSI/MSI-X
[    2.681481] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.681494] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.681521] intel_idle: MWAIT substates: 0x1120
[    2.681522] intel_idle: v0.4 model 0x2C
[    2.681523] intel_idle: lapic_timer_reliable_states 0xffffffff
[    2.681634] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    2.681637] ACPI: Power Button [PWRB]
[    2.681664] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    2.681665] ACPI: Power Button [PWRF]
[    2.681802] ACPI: acpi_idle yielding to intel_idle
[    2.682895] ERST: Table is not found!
[    2.682930] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.925659] Linux agpgart interface v0.103
[    2.926387] brd: module loaded
[    2.926709] loop: module loaded
[    2.926761] i2c-core: driver [adp5520] using legacy suspend method
[    2.926762] i2c-core: driver [adp5520] using legacy resume method
[    2.926810] ata_piix 0000:00:1f.2: version 2.13
[    2.926824] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.926827] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    2.926854] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.927029] scsi0 : ata_piix
[    2.927084] scsi1 : ata_piix
[    2.927722] ata1: SATA max UDMA/133 cmd 0x6c00 ctl 0x6880 bmdma 0x6400 irq 20
[    2.927726] ata2: SATA max UDMA/133 cmd 0x6800 ctl 0x6480 bmdma 0x6408 irq 20
[    2.927740] ata_piix 0000:00:1f.5: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.927743] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.927768] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.927894] scsi2 : ata_piix
[    2.927934] scsi3 : ata_piix
[    2.928492] ata3: SATA max UDMA/133 cmd 0x7c00 ctl 0x7880 bmdma 0x7400 irq 20
[    2.928495] ata4: SATA max UDMA/133 cmd 0x7800 ctl 0x7480 bmdma 0x7408 irq 20
[    2.928536] pata_acpi 0000:01:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    2.928552] pata_acpi 0000:01:00.0: setting latency timer to 64
[    2.928560] pata_acpi 0000:01:00.0: PCI INT A disabled
[    2.928571] pata_acpi 0000:0b:00.1: enabling device (0000 -> 0001)
[    2.928575] pata_acpi 0000:0b:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.928589] pata_acpi 0000:0b:00.1: setting latency timer to 64
[    2.928597] pata_acpi 0000:0b:00.1: PCI INT B disabled
[    2.928764] Fixed MDIO Bus: probed
[    2.928780] PPP generic driver version 2.4.2
[    2.928805] tun: Universal TUN/TAP device driver, 1.6
[    2.928807] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.928860] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.928875] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.928897] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.928900] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.928927] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.928965] ehci_hcd 0000:00:1a.7: debug port 1
[    2.932840] ehci_hcd 0000:00:1a.7: cache line size of 256 is not supported
[    2.932850] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf7ade000
[    2.954139] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.954254] hub 1-0:1.0: USB hub found
[    2.954257] hub 1-0:1.0: 6 ports detected
[    2.954312] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.954322] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.954324] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.954349] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.954386] ehci_hcd 0000:00:1d.7: debug port 1
[    2.958252] ehci_hcd 0000:00:1d.7: cache line size of 256 is not supported
[    2.958262] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7add000
[    2.974088] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.974192] hub 2-0:1.0: USB hub found
[    2.974195] hub 2-0:1.0: 6 ports detected
[    2.974245] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.974252] uhci_hcd: USB Universal Host Controller Interface driver
[    2.974288] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.974293] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.974295] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.974319] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.974364] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00008480
[    2.974448] hub 3-0:1.0: USB hub found
[    2.974450] hub 3-0:1.0: 2 ports detected
[    2.974498] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.974502] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.974504] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.974528] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.974570] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00008800
[    2.974651] hub 4-0:1.0: USB hub found
[    2.974654] hub 4-0:1.0: 2 ports detected
[    2.974701] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.974705] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.974707] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.974732] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    2.984108] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00008880
[    2.984195] hub 5-0:1.0: USB hub found
[    2.984197] hub 5-0:1.0: 2 ports detected
[    2.984242] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.984246] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.984248] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.984272] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.984308] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00008000
[    2.984390] hub 6-0:1.0: USB hub found
[    2.984392] hub 6-0:1.0: 2 ports detected
[    2.984439] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.984443] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.984445] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.984467] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.984502] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00008080
[    2.984581] hub 7-0:1.0: USB hub found
[    2.984583] hub 7-0:1.0: 2 ports detected
[    2.984626] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.984630] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.984632] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.984659] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.984696] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008400
[    2.984776] hub 8-0:1.0: USB hub found
[    2.984778] hub 8-0:1.0: 2 ports detected
[    2.984852] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.987373] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.987377] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.987453] mousedev: PS/2 mouse device common for all mice
[    2.987529] rtc_cmos 00:03: RTC can wake from S4
[    2.987573] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.987595] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.987655] device-mapper: uevent: version 1.0.3
[    2.987707] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.987748] device-mapper: multipath: version 1.2.0 loaded
[    2.987749] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.987988] cpuidle: using governor ladder
[    2.988259] cpuidle: using governor menu
[    2.988416] TCP cubic registered
[    2.988491] NET: Registered protocol family 10
[    2.988828] NET: Registered protocol family 17
[    2.988837] Registering the dns_resolver key type
[    2.996689] PM: Hibernation image not present or could not be loaded.
[    2.996696] registered taskstats version 1
[    2.997104]   Magic number: 9:560:272
[    2.997372] rtc_cmos 00:03: setting system clock to 2013-04-12 09:16:50 UTC (1365758210)
[    2.997374] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.997375] EDD information not available.
[    3.284014] ata3: SATA link down (SStatus 0 SControl 300)
[    3.294694] ata4: SATA link down (SStatus 0 SControl 300)
[    3.393028] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    3.633171] ata1.00: SATA link down (SStatus 0 SControl 300)
[    3.633182] ata1.01: SATA link down (SStatus 0 SControl 300)
[    3.662306] Refined TSC clocksource calibration: 3337.499 MHz.
[    3.662311] Switching to clocksource tsc
[    3.782033] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.782047] ata2.01: SATA link down (SStatus 0 SControl 300)
[    3.782059] ata2.01: link offline, clearing class 3 to NONE
[    3.802056] ata2.00: ATAPI: ATAPI   iHOS104, WL0D, max UDMA/100
[    3.821881] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.841951] ata2.00: configured for UDMA/100
[    3.876127] scsi 1:0:0:0: CD-ROM            ATAPI    iHOS104          WL0D PQ: 0 ANSI: 5
[    3.909066] sr0: scsi3-mmc drive: 62x/62x cd/rw xa/form2 cdda tray
[    3.909070] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.909197] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.909232] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    3.911188] Freeing unused kernel memory: 956k freed
[    3.911298] Write protecting the kernel read-only data: 10240k
[    3.912894] Freeing unused kernel memory: 184k freed
[    3.917194] Freeing unused kernel memory: 1444k freed
[    3.933871] <30>udev[102]: starting version 167
[    3.959274] pata_jmicron 0000:0b:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.959301] pata_jmicron 0000:0b:00.1: setting latency timer to 64
[    3.959593] scsi4 : pata_jmicron
[    3.959653] scsi5 : pata_jmicron
[    3.959924] ata5: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 17
[    3.959925] ata6: PATA max UDMA/100 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 17
[    3.967115] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-k2
[    3.967117] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    3.967131] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.967137] e1000e 0000:00:19.0: setting latency timer to 64
[    3.967212] e1000e 0000:00:19.0: irq 71 for MSI/MSI-X
[    3.969262] ahci 0000:01:00.0: version 3.0
[    3.969269] ahci 0000:01:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    3.969306] ahci 0000:01:00.0: irq 72 for MSI/MSI-X
[    3.969314] ahci 0000:01:00.0: controller can do FBS, turning on CAP_FBS
[    3.981521] ahci 0000:01:00.0: AHCI 0001.0200 32 slots 8 ports 6 Gbps 0xff impl IDE mode
[    3.981526] ahci 0000:01:00.0: flags: 64bit ncq fbs pio
[    3.981532] ahci 0000:01:00.0: setting latency timer to 64
[    3.982353] scsi6 : ahci
[    3.982604] scsi7 : ahci
[    3.982861] scsi8 : ahci
[    3.983117] scsi9 : ahci
[    3.983381] scsi10 : ahci
[    3.983662] scsi11 : ahci
[    3.983898] scsi12 : ahci
[    3.984068] scsi13 : ahci
[    3.984136] ata7: SATA max UDMA/133 abar m2048@0xf7bff800 port 0xf7bff900 irq 72
[    3.984140] ata8: SATA max UDMA/133 abar m2048@0xf7bff800 port 0xf7bff980 irq 72
[    3.984144] ata9: SATA max UDMA/133 abar m2048@0xf7bff800 port 0xf7bffa00 irq 72
[    3.984149] ata10: SATA max UDMA/133 abar m2048@0xf7bff800 port 0xf7bffa80 irq 72
[    3.984151] ata11: SATA max UDMA/133 abar m2048@0xf7bff800 port 0xf7bffb00 irq 72
[    3.984153] ata12: SATA max UDMA/133 abar m2048@0xf7bff800 port 0xf7bffb80 irq 72
[    3.984154] ata13: SATA max UDMA/133 abar m2048@0xf7bff800 port 0xf7bffc00 irq 72
[    3.984156] ata14: SATA max UDMA/133 abar m2048@0xf7bff800 port 0xf7bffc80 irq 72
[    3.984174] ahci 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.001461] ahci 0000:0b:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    4.001466] ahci 0000:0b:00.0: flags: 64bit ncq pm led clo pmp pio slum part
[    4.001473] ahci 0000:0b:00.0: setting latency timer to 64
[    4.001841] scsi14 : ahci
[    4.002131] scsi15 : ahci
[    4.002258] ata15: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 16
[    4.002262] ata16: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 16
[    4.280673] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    4.320593] ata9: SATA link down (SStatus 0 SControl 300)
[    4.330553] ata11: SATA link down (SStatus 0 SControl 300)
[    4.330573] ata13: SATA link down (SStatus 0 SControl 300)
[    4.330593] ata10: SATA link down (SStatus 0 SControl 300)
[    4.330613] ata14: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.330631] ata12: SATA link down (SStatus 0 SControl 300)
[    4.330647] ata8: SATA link down (SStatus 0 SControl 300)
[    4.330759] ata14.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    4.330988] ata14.00: configured for UDMA/66
[    4.340503] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.340533] ata16: SATA link down (SStatus 0 SControl 300)
[    4.350530] ata15: SATA link down (SStatus 0 SControl 300)
[    4.404946] ata7.00: ATA-8: OCZ-AGILITY3, 2.11, max UDMA/133
[    4.404951] ata7.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.414829] ata7.00: configured for UDMA/133
[    4.414954] scsi 6:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.11 PQ: 0 ANSI: 5
[    4.415133] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    4.415182] sd 6:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
[    4.415274] sd 6:0:0:0: [sda] Write Protect is off
[    4.415277] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.415315] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.415460] scsi 13:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    4.415541] scsi 13:0:0:0: Attached scsi generic sg2 type 3
[    4.415902]  sda: sda1 sda2 < sda5 >
[    4.416208] sd 6:0:0:0: [sda] Attached SCSI disk
[    4.419919] firewire_ohci 0000:0d:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.443736] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.500117] firewire_ohci: Added fw-ohci device 0000:0d:02.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    4.540085] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
[    4.540142] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1/input0
[    4.553302] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3
[    4.553356] generic-usb 0003:093A:2510.0002: input,hidraw1: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1a.0-2/input0
[    4.553365] usbcore: registered new interface driver usbhid
[    4.553366] usbhid: USB HID core driver
[    4.641908] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 14:da:e9:43:d9:bf
[    4.641910] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    4.641932] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
[    4.879089] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    4.998823] firewire_core: created device fw0: GUID 001fc60000175955, S400
[    5.058107] <30>udev[354]: starting version 167
[    5.077560] lp: driver loaded but no devices found
[    5.087354] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
[    5.087375] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    5.087379] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    5.087475] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    5.090695] rr64x: module license 'Proprietary' taints kernel.
[    5.090698] Disabling lock debugging due to kernel taint
[    5.094443] rr64x:RocketRAID 64x SATA controller driver v1.0 (Nov  4 2011 17:06:03)
[    5.094464] pci 0000:06:00.0: PCI INT A -> GSI 25 (level, low) -> IRQ 25
[    5.094469] pci 0000:06:00.0: setting latency timer to 64
[    5.094490] rr64x:adapter at PCI 6:0:0, IRQ 25
[    5.094507] pci 0000:07:00.0: PCI INT A -> GSI 25 (level, low) -> IRQ 25
[    5.094511] pci 0000:07:00.0: setting latency timer to 64
[    5.099570] EDAC MC: Ver: 2.1.0 Apr 11 2011
[    5.123082] EDAC i7core: Driver loaded.
[    5.196415] nvidia 0000:0a:00.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
[    5.196421] nvidia 0000:0a:00.0: setting latency timer to 64
[    5.196425] vgaarb: device changed decodes: PCI:0000:0a:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    5.196682] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011
[    5.205597] type=1400 audit(1365758212.701:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=543 comm="apparmor_parser"
[    5.205603] type=1400 audit(1365758212.701:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=493 comm="apparmor_parser"
[    5.206092] type=1400 audit(1365758212.701:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=493 comm="apparmor_parser"
[    5.206112] type=1400 audit(1365758212.701:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=543 comm="apparmor_parser"
[    5.206410] type=1400 audit(1365758212.701:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=493 comm="apparmor_parser"
[    5.206443] type=1400 audit(1365758212.701:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=543 comm="apparmor_parser"
[    5.207090] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    5.210336] r8712u: DriverVersion: v7_0.20100831
[    5.210346] r8712u: register rtl8712_netdev_ops to netdev_ops
[    5.210348] r8712u: USB_SPEED_HIGH with 4 endpoints
[    5.210825] r8712u: Boot from EFUSE: Autoload OK
[    5.216243] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    5.218021] Bluetooth: Core ver 2.15
[    5.218039] NET: Registered protocol family 31
[    5.218040] Bluetooth: HCI device and connection manager initialized
[    5.218042] Bluetooth: HCI socket layer initialized
[    5.221303] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    5.221413] usbcore: registered new interface driver btusb
[    5.255496] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    5.262567] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.262608] HDA Intel 0000:00:1b.0: irq 73 for MSI/MSI-X
[    5.262625] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.310943] rr64x:adapter at PCI 7:0:0, IRQ 25
[    5.609681] r8712u: CustomerID = 0x0000
[    5.609683] r8712u: MAC Address from efuse = 00:23:13:01:c6:2e
[    5.610031] usbcore: registered new interface driver r8712u
[    5.740945] rr64x:[0 0  ] start port.
[    5.740946] rr64x:[0 0  ] start port hard reset (probe 1).
[    5.940436] rr64x:[0 1  ] start port.
[    5.940437] rr64x:[0 1  ] start port hard reset (probe 1).
[    6.139926] rr64x:[1 0  ] start port.
[    6.139927] rr64x:[1 0  ] start port hard reset (probe 1).
[    6.339416] rr64x:[1 1  ] start port.
[    6.339417] rr64x:[1 1  ] start port hard reset (probe 1).
[    6.541122] hda_codec: ALC889: BIOS auto-probing.
[    6.544911] xhci_hcd 0000:02:00.0: irq 29, io mem 0xf7cfe000
[    6.545042] xhci_hcd 0000:02:00.0: irq 74 for MSI/MSI-X
[    6.545046] xhci_hcd 0000:02:00.0: irq 75 for MSI/MSI-X
[    6.545049] xhci_hcd 0000:02:00.0: irq 76 for MSI/MSI-X
[    6.545052] xhci_hcd 0000:02:00.0: irq 77 for MSI/MSI-X
[    6.545056] xhci_hcd 0000:02:00.0: irq 78 for MSI/MSI-X
[    6.545059] xhci_hcd 0000:02:00.0: irq 79 for MSI/MSI-X
[    6.545063] xhci_hcd 0000:02:00.0: irq 80 for MSI/MSI-X
[    6.545066] xhci_hcd 0000:02:00.0: irq 81 for MSI/MSI-X
[    6.546945] usbcore: registered new interface driver r871x_usb_drv
[    6.548255] usb usb9: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    6.548338] xHCI xhci_add_endpoint called for root hub
[    6.548340] xHCI xhci_check_bandwidth called for root hub
[    6.548360] hub 9-0:1.0: USB hub found
[    6.548364] hub 9-0:1.0: 4 ports detected
[    6.549681] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    6.549820] HDA Intel 0000:0a:00.1: PCI INT B -> GSI 37 (level, low) -> IRQ 37
[    6.549822] hda_intel: Disable MSI for Nvidia chipset
[    6.550104] HDA Intel 0000:0a:00.1: setting latency timer to 64
[    8.948232] rr64x:[0 0  ] start port soft reset (probe 1).
[    9.656331] rr64x:[0 1  ] start port soft reset (probe 1).
[   10.307041] rr64x:[1 0  ] start port soft reset (probe 1).
[   10.962362] rr64x:[0 0  ] port started successfully.
[   10.962363] rr64x:[0 0 0] device probed successfully.
[   11.007402] rr64x:[0 1  ] port started successfully.
[   11.007403] rr64x:[0 1 0] device probed successfully.
[   11.050440] rr64x:[1 0  ] port started successfully.
[   11.050441] rr64x:[1 0 0] device probed successfully.
[   14.333817] rr64x:[1 1  ] failed to hard reset.
[   14.333826] rr64x:[1 1  ] failed to perform port hard reset.
[   14.337088] scsi16 : rr64x
[   14.337618] scsi 16:0:0:0: Direct-Access     HPT      DISK_16_0        4.00 PQ: 0 ANSI: 5
[   14.337663] scsi 16:0:1:0: Direct-Access     HPT      DISK_16_1        4.00 PQ: 0 ANSI: 5
[   14.337704] scsi 16:0:2:0: Direct-Access     HPT      DISK_16_2        4.00 PQ: 0 ANSI: 5
[   14.338462] sd 16:0:0:0: Attached scsi generic sg3 type 0
[   14.338540] sd 16:0:0:0: [sdb] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.338571] sd 16:0:1:0: Attached scsi generic sg4 type 0
[   14.338578] sd 16:0:0:0: [sdb] Write Protect is off
[   14.338581] sd 16:0:0:0: [sdb] Mode Sense: 2f 00 00 00
[   14.338601] sd 16:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   14.338648] sd 16:0:1:0: [sdc] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.338686] sd 16:0:1:0: [sdc] Write Protect is off
[   14.338688] sd 16:0:1:0: [sdc] Mode Sense: 2f 00 00 00
[   14.338709] sd 16:0:1:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   14.338731] sd 16:0:2:0: [sdd] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.338738] sd 16:0:0:0: [sdb] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.338756] sd 16:0:2:0: [sdd] Write Protect is off
[   14.338758] sd 16:0:2:0: [sdd] Mode Sense: 2f 00 00 00
[   14.338774] sd 16:0:2:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   14.338802] sd 16:0:2:0: Attached scsi generic sg5 type 0
[   14.338884] sd 16:0:2:0: [sdd] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.338920] sd 16:0:1:0: [sdc] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.349444] vesafb: framebuffer at 0xd5000000, mapped to 0xffffc90016900000, using 5120k, total 5120k
[   14.349446] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   14.349447] vesafb: scrolling: redraw
[   14.349449] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   14.349542] Console: switching to colour frame buffer device 160x64
[   14.349559] fb0: VESA VGA frame buffer device
[   14.361660]  sdb: unknown partition table
[   14.361837] sd 16:0:0:0: [sdb] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.361874] sd 16:0:0:0: [sdb] Attached SCSI disk
[   14.365046]  sdc: unknown partition table
[   14.365399] sd 16:0:1:0: [sdc] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.365452] sd 16:0:1:0: [sdc] Attached SCSI disk
[   14.366151]  sdd: unknown partition table
[   14.366507] sd 16:0:2:0: [sdd] 732545024 4096-byte logical blocks: (3.00 TB/2.72 TiB)
[   14.366548] sd 16:0:2:0: [sdd] Attached SCSI disk
[   14.822287] EXT4-fs (sdb): mounted filesystem with ordered data mode. Opts: (null)
[   14.936783] EXT4-fs (sdd): mounted filesystem with ordered data mode. Opts: (null)
[   15.044429] EXT4-fs (sdc): mounted filesystem with ordered data mode. Opts: (null)
[   15.067807] type=1400 audit(1365758222.591:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=842 comm="apparmor_parser"
[   15.067834] type=1400 audit(1365758222.591:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=848 comm="apparmor_parser"
[   15.068088] type=1400 audit(1365758222.591:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=844 comm="apparmor_parser"
[   15.068365] type=1400 audit(1365758222.591:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=847 comm="apparmor_parser"
[   15.068587] type=1400 audit(1365758222.591:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=844 comm="apparmor_parser"
[   15.068861] type=1400 audit(1365758222.591:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=847 comm="apparmor_parser"
[   15.068867] type=1400 audit(1365758222.591:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=844 comm="apparmor_parser"
[   15.069824] ppdev: user-space parallel port driver
[   15.072099] type=1400 audit(1365758222.601:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=845 comm="apparmor_parser"
[   15.077275] type=1400 audit(1365758222.601:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=864 comm="apparmor_parser"
[   15.077797] type=1400 audit(1365758222.601:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=864 comm="apparmor_parser"
[   15.126547] Bluetooth: L2CAP ver 2.15
[   15.126548] Bluetooth: L2CAP socket layer initialized
[   15.131021] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.131023] Bluetooth: BNEP filters: protocol multicast
[   15.136637] Bluetooth: SCO (Voice Link) ver 0.6
[   15.136639] Bluetooth: SCO socket layer initialized
[   15.234128] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   15.236109] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   15.237692] EXT4-fs (sdb): re-mounted. Opts: commit=0
[   15.240404] EXT4-fs (sdd): re-mounted. Opts: commit=0
[   15.242903] EXT4-fs (sdc): re-mounted. Opts: commit=0
[   16.770882] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.772608] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   16.774073] EXT4-fs (sdb): re-mounted. Opts: commit=0
[   16.775639] EXT4-fs (sdd): re-mounted. Opts: commit=0
[   16.777045] EXT4-fs (sdc): re-mounted. Opts: commit=0
[   19.775645] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   23.819023] ISO 9660 Extensions: Microsoft Joliet Level 3
[   23.822471] ISO 9660 Extensions: IEEE_1282
[   30.949627] e1000e 0000:00:19.0: irq 71 for MSI/MSI-X
[   31.009368] e1000e 0000:00:19.0: irq 71 for MSI/MSI-X
[   31.010275] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.767773] r8712u: 1 RCR=0x153f00e
[   31.768511] r8712u: 2 RCR=0x553f00e
[   31.888092] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  446.022074] e1000e 0000:00:19.0: irq 71 for MSI/MSI-X
[  446.081750] e1000e 0000:00:19.0: irq 71 for MSI/MSI-X
[  446.083549] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  446.193430] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1051.817284] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1537.591072] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1698.270365] e1000e 0000:00:19.0: irq 71 for MSI/MSI-X
[ 1698.330074] e1000e 0000:00:19.0: irq 71 for MSI/MSI-X
[ 1698.331874] ADDRCONF(NETDEV_UP): eth0: link is not ready
```


```
$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82567V-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 00
       serial: 14:da:e9:43:d9:bf
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=1.8-5 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:71 memory:f7ae0000-f7afffff memory:f7adf000-f7adffff ioport:8c00(size=32)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:23:13:01:c6:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated
```


```
$ iwlist scan wlan0
wlan0     No scan results
```

```
$ lsb_release -d
Description:    Ubuntu 11.04
```
```

$ uname -mr
2.6.38-8-generic x86_64
```


```
$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.
```

---

### Post by fr2632 on 2013-04-13
Try here:
[http://ubuntuforums.org/showthread.php?t=1397309](http://ubuntuforums.org/showthread.php?t=1397309)

---

### Post by paulrollings on 2013-04-17
Thanks, I tried the driver install , still with no luck.  

I decided to give up on my 11.04 install and did a fresh install of 12.04, which works.  So I think this must due to something funky with my 11.04 install.  

Thanks

---

