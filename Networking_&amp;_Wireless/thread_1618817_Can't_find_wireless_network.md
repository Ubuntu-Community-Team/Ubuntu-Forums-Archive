---
title: "Can't find wireless network"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by Zeophlite on 2010-11-11
So I finally successfully installed Ubuntu 10.10, but I can't access my home wireless network.  I dual booted with Windows 7, and it detects my local wireless network, asks for the key and connects correctly.

In Ubuntu, I have to plug in an ethernet cable to access the internet (like I am now).  Ubuntu doesn't detect the network, and I tried "Create New Wireless Network..." up the top right, but it doesn't connect.

I'm using a Tenda W322P Wireless PCI adapter, on an Asrock P55Pro-USB3 board.

```

[SIZE=3]**daniel@Rincewind:~$ lspci**[/SIZE]
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 USB Controller: Device 1b73:1000 (rev 01)
05:00.0 Network controller: RaLink Device 3062
06:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5670]
06:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
[SIZE=3]**daniel@Rincewind:~$ lsusb**[/SIZE]
Bus 002 Device 004: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 002 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[SIZE=3]**daniel@Rincewind:~$ ifconfig **[/SIZE]
eth0      Link encap:Ethernet  HWaddr 00:25:22:68:a6:6d  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fe68:a66d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2901 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5696981 (5.6 MB)  TX bytes:381974 (381.9 KB)
          Interrupt:45 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr c8:3a:35:c6:47:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[SIZE=3]**daniel@Rincewind:~$ iwconfig **[/SIZE]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
[SIZE=3]**daniel@Rincewind:~$ lsmod**[/SIZE]
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   299533  1 
fglrx                2523725  85 
arc4                    1497  2 
rt2800pci              10233  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
rt2800lib              31970  1 rt2800pci
snd_seq_midi            5932  0 
rt2x00usb              11316  1 rt2800lib
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
rt2x00pci               6993  1 rt2800pci
snd_rawmidi            22207  1 snd_seq_midi
crc_ccitt               1699  1 rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
snd_seq_midi_event      7291  1 snd_seq_midi
mac80211              266657  3 rt2x00usb,rt2x00pci,rt2x00lib
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              170293  2 rt2x00lib,mac80211
psmouse                62080  0 
serio_raw               4910  0 
eeprom_93cx6            1789  1 rt2800pci
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
xhci_hcd               58578  0 
intel_agp              32080  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84678  1 usbhid
ahci                   21857  0 
r8169                  42222  0 
libahci                26167  4 ahci
mii                     5261  1 r8169
[SIZE=3]**daniel@Rincewind:~$ dmesg**[/SIZE]
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=e67fe9c7-528d-4591-9ebc-425f1825e0e6 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e400 (usable)
[    0.000000]  BIOS-e820: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cb770000 (usable)
[    0.000000]  BIOS-e820: 00000000cb770000 - 00000000cb780000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cb780000 - 00000000cb7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cb7d0000 - 00000000cb7e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000cb7eb400 - 00000000cc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000134000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x134000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-EBFFF write-through
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FE0000000 write-back
[    0.000000]   2 base 120000000 mask FF0000000 write-back
[    0.000000]   3 base 130000000 mask FFC000000 write-back
[    0.000000]   4 base 0CC000000 mask FFC000000 uncachable
[    0.000000]   5 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   6 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cc000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcb770 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e400 (usable)
[    0.000000]  modified: 000000000009e400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cb770000 (usable)
[    0.000000]  modified: 00000000cb770000 - 00000000cb780000 (ACPI data)
[    0.000000]  modified: 00000000cb780000 - 00000000cb7d0000 (ACPI NVS)
[    0.000000]  modified: 00000000cb7d0000 - 00000000cb7e0000 (reserved)
[    0.000000]  modified: 00000000cb7eb400 - 00000000cc000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffa00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000134000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000cb770000
[    0.000000]  0000000000 - 00cb600000 page 2M
[    0.000000]  00cb600000 - 00cb770000 page 4k
[    0.000000] kernel direct mapping tables up to cb770000 @ 16000-1c000
[    0.000000] init_memory_mapping: 0000000100000000-0000000134000000
[    0.000000]  0100000000 - 0134000000 page 2M
[    0.000000] kernel direct mapping tables up to 134000000 @ 1a000-20000
[    0.000000] RAMDISK: 37573000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fab00 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000cb770000 00044 (v01 081210 RSDT1047 20100812 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cb770200 00084 (v01 A_M_I  OEMFACP  12000601 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000cb770460 06FD1 (v01  AS385 AS385112 00000112 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cb780000 00040
[    0.000000] ACPI: APIC 00000000cb770390 0008C (v01 081210 APIC1047 20100812 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cb770420 0003C (v01 081210 OEMMCFG  20100812 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cb780040 00072 (v01 081210 OEMB1047 20100812 MSFT 00000097)
[    0.000000] ACPI: AAFT 00000000cb77a460 00027 (v01 081210 OEMAAFT  20100812 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cb77a490 00038 (v01 081210 OEMHPET  20100812 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000cb7800c0 02024 (v01 081210 GMCHSCI  20100812 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cb783830 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000134000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000134000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880100200000-ffff880103dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00134000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cb770
[    0.000000]     0: 0x00100000 -> 0x00134000
[    0.000000] On node 0 totalpages: 1046270
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3926 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 815016 pages, LIFO batch:31
[    0.000000]   Normal zone: 2912 pages used for memmap
[    0.000000]   Normal zone: 210080 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
[    0.000000] ACPI: IOAPIC (id[0x06] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 6, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [1b000 - 1b7ff]
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cb770000 - 00000000cb780000
[    0.000000] PM: Registered nosave memory: 00000000cb780000 - 00000000cb7d0000
[    0.000000] PM: Registered nosave memory: 00000000cb7d0000 - 00000000cb7e0000
[    0.000000] PM: Registered nosave memory: 00000000cb7e0000 - 00000000cb7ec000
[    0.000000] PM: Registered nosave memory: 00000000cb7ec000 - 00000000cc000000
[    0.000000] PM: Registered nosave memory: 00000000cc000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffa00000
[    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cc000000 (gap: cc000000:32e00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029022
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=e67fe9c7-528d-4591-9ebc-425f1825e0e6 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] early_res array is doubled to 128 at [23800 - 247ff]
[    0.000000] Subtract (57 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037573000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [000009e400 - 0000100000]   BIOS reserved
[    0.000000]   #4 [0001d18000 - 0001d18133]             BRK
[    0.000000]   #5 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #6 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #7 [0000016000 - 000001a000]         PGTABLE
[    0.000000]   #8 [000001a000 - 000001b000]         PGTABLE
[    0.000000]   #9 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #10 [0001d18140 - 0001d19140]         BOOTMEM
[    0.000000]   #11 [0001d17140 - 0001d17458]         BOOTMEM
[    0.000000]   #12 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #13 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #14 [0100200000 - 0103e00000]        MEMMAP 0
[    0.000000]   #15 [0001d17480 - 0001d17600]         BOOTMEM
[    0.000000]   #16 [0001d19140 - 0001d31140]         BOOTMEM
[    0.000000]   #17 [0001d31140 - 0001d37140]         BOOTMEM
[    0.000000]   #18 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #19 [0001d17600 - 0001d17641]         BOOTMEM
[    0.000000]   #20 [0001d17680 - 0001d176c3]         BOOTMEM
[    0.000000]   #21 [0001d17700 - 0001d179a0]         BOOTMEM
[    0.000000]   #22 [0001d179c0 - 0001d17a28]         BOOTMEM
[    0.000000]   #23 [0001d17a40 - 0001d17aa8]         BOOTMEM
[    0.000000]   #24 [0001d17ac0 - 0001d17b28]         BOOTMEM
[    0.000000]   #25 [0001d17b40 - 0001d17ba8]         BOOTMEM
[    0.000000]   #26 [0001d17bc0 - 0001d17c28]         BOOTMEM
[    0.000000]   #27 [0001d17c40 - 0001d17ca8]         BOOTMEM
[    0.000000]   #28 [0001d17cc0 - 0001d17d28]         BOOTMEM
[    0.000000]   #29 [0001d17d40 - 0001d17da8]         BOOTMEM
[    0.000000]   #30 [0001d17dc0 - 0001d17e28]         BOOTMEM
[    0.000000]   #31 [0001d17e40 - 0001d17ea8]         BOOTMEM
[    0.000000]   #32 [0001d17ec0 - 0001d17f28]         BOOTMEM
[    0.000000]   #33 [0001d17f40 - 0001d17f60]         BOOTMEM
[    0.000000]   #34 [0001d17f80 - 0001d17fa0]         BOOTMEM
[    0.000000]   #35 [0001d37140 - 0001d371aa]         BOOTMEM
[    0.000000]   #36 [0001d371c0 - 0001d3722a]         BOOTMEM
[    0.000000]   #37 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #38 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #39 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #40 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #41 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #42 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #43 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #44 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #45 [0001d17fc0 - 0001d17fc8]         BOOTMEM
[    0.000000]   #46 [0001d37240 - 0001d37248]         BOOTMEM
[    0.000000]   #47 [0001d37280 - 0001d372a0]         BOOTMEM
[    0.000000]   #48 [0001d372c0 - 0001d37300]         BOOTMEM
[    0.000000]   #49 [0001d37300 - 0001d37420]         BOOTMEM
[    0.000000]   #50 [0001d37440 - 0001d37488]         BOOTMEM
[    0.000000]   #51 [0001d374c0 - 0001d37508]         BOOTMEM
[    0.000000]   #52 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #53 [0001fde000 - 0005fde000]         BOOTMEM
[    0.000000]   #54 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #55 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #56 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 4032340k/5046272k available (5708k kernel code, 861192k absent, 152740k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:744
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 43253760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2944.331 MHz processor.
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5888.66 BogoMIPS (lpj=29443310)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000030] Security Framework initialized
[    0.000046] AppArmor: AppArmor initialized
[    0.000047] Yama: becoming mindful.
[    0.000424] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001273] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001601] Mount-cache hash table entries: 256
[    0.001702] Initializing cgroup subsys ns
[    0.001705] Initializing cgroup subsys cpuacct
[    0.001709] Initializing cgroup subsys memory
[    0.001716] Initializing cgroup subsys devices
[    0.001718] Initializing cgroup subsys freezer
[    0.001720] Initializing cgroup subsys net_cls
[    0.001740] CPU: Physical Processor ID: 0
[    0.001741] CPU: Processor Core ID: 0
[    0.001746] mce: CPU supports 9 MCE banks
[    0.001757] CPU0: Thermal monitoring enabled (TM1)
[    0.001764] using mwait in idle threads.
[    0.001766] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.001772] ... version:                3
[    0.001773] ... bit width:              48
[    0.001775] ... generic registers:      4
[    0.001776] ... value mask:             0000ffffffffffff
[    0.001777] ... max period:             000000007fffffff
[    0.001779] ... fixed-purpose events:   3
[    0.001780] ... event mask:             000000070000000f
[    0.003783] ACPI: Core revision 20100428
[    0.033832] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.033835] ftrace: allocating 22680 entries in 89 pages
[    0.040397] Setting APIC routing to flat
[    0.040726] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.140560] CPU0: Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz stepping 02
[    0.258727] Booting Node   0, Processors  #1 #2 #3
[    0.797444] Brought up 4 CPUs
[    0.797447] Total of 4 processors activated (23552.02 BogoMIPS).
[    0.798941] devtmpfs: initialized
[    0.799702] regulator: core version 0.5
[    0.799725] Time: 16:02:17  Date: 11/11/10
[    0.799749] NET: Registered protocol family 16
[    0.799822] Trying to unpack rootfs image as initramfs...
[    0.799830] ACPI: bus type pci registered
[    0.799884] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.799887] PCI: not using MMCONFIG
[    0.799888] PCI: Using configuration type 1 for base access
[    0.800406] bio: create slab <bio-0> at 0
[    0.801545] ACPI: EC: Look up EC in DSDT
[    0.803012] ACPI: Executed 1 blocks of module-level executable AML code
[    0.810971] ACPI: SSDT 00000000cb7820f0 01238 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.811288] ACPI: Dynamic OEM Table Load:
[    0.811290] ACPI: SSDT (null) 01238 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.811496] ACPI: SSDT 00000000cb783330 004F4 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    0.811783] ACPI: Dynamic OEM Table Load:
[    0.811785] ACPI: SSDT (null) 004F4 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    0.811906] ACPI: Interpreter enabled
[    0.811908] ACPI: (supports S0 S1 S3 S4 S5)
[    0.811924] ACPI: Using IOAPIC for interrupt routing
[    0.811971] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.813716] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.847591] ACPI: No dock devices found.
[    0.847594] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.847890] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.848154] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.848156] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.848158] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.848160] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.848162] pci_root PNP0A08:00: host bridge window [mem 0xcc000000-0xdfffffff]
[    0.848163] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfed8ffff]
[    0.848214] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.848216] pci 0000:00:01.0: PME# disabled
[    0.848262] pci 0000:00:1a.0: reg 10: [mem 0xfbcf8000-0xfbcf83ff]
[    0.848306] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.848310] pci 0000:00:1a.0: PME# disabled
[    0.848336] pci 0000:00:1b.0: reg 10: [mem 0xfbcf4000-0xfbcf7fff 64bit]
[    0.848368] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.848371] pci 0000:00:1b.0: PME# disabled
[    0.848420] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.848423] pci 0000:00:1c.0: PME# disabled
[    0.848472] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.848475] pci 0000:00:1c.1: PME# disabled
[    0.848589] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.848592] pci 0000:00:1c.2: PME# disabled
[    0.848643] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.848646] pci 0000:00:1c.4: PME# disabled
[    0.848682] pci 0000:00:1d.0: reg 10: [mem 0xfbcfa000-0xfbcfa3ff]
[    0.848726] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.848729] pci 0000:00:1d.0: PME# disabled
[    0.848862] pci 0000:00:1f.2: reg 10: [io  0xc880-0xc887]
[    0.848866] pci 0000:00:1f.2: reg 14: [io  0xc800-0xc803]
[    0.848870] pci 0000:00:1f.2: reg 18: [io  0xc480-0xc487]
[    0.848874] pci 0000:00:1f.2: reg 1c: [io  0xc400-0xc403]
[    0.848878] pci 0000:00:1f.2: reg 20: [io  0xc080-0xc09f]
[    0.848882] pci 0000:00:1f.2: reg 24: [mem 0xfbcfc000-0xfbcfc7ff]
[    0.848906] pci 0000:00:1f.2: PME# supported from D3hot
[    0.848908] pci 0000:00:1f.2: PME# disabled
[    0.848929] pci 0000:00:1f.3: reg 10: [mem 0xfbcffc00-0xfbcffcff 64bit]
[    0.848939] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.848985] pci 0000:06:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.848992] pci 0000:06:00.0: reg 18: [mem 0xfbfc0000-0xfbfdffff 64bit]
[    0.848996] pci 0000:06:00.0: reg 20: [io  0xe000-0xe0ff]
[    0.849002] pci 0000:06:00.0: reg 30: [mem 0xfbfa0000-0xfbfbffff pref]
[    0.849016] pci 0000:06:00.0: supports D1 D2
[    0.849038] pci 0000:06:00.1: reg 10: [mem 0xfbffc000-0xfbffffff 64bit]
[    0.849064] pci 0000:06:00.1: supports D1 D2
[    0.849089] pci 0000:00:01.0: PCI bridge to [bus 06-06]
[    0.849091] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.849093] pci 0000:00:01.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.849096] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.849127] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.849130] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.849133] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.849137] pci 0000:00:1c.0:   bridge window [mem 0xcff00000-0xcfffffff 64bit pref]
[    0.849193] pci 0000:02:00.0: reg 10: [mem 0xfbdf0000-0xfbdfffff]
[    0.849255] pci 0000:02:00.0: PME# supported from D0 D3hot
[    0.849259] pci 0000:02:00.0: PME# disabled
[    0.867170] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.867175] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.867178] pci 0000:00:1c.1:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.867183] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.867246] pci 0000:01:00.0: reg 10: [io  0xd800-0xd8ff]
[    0.867263] pci 0000:01:00.0: reg 18: [mem 0xcfdff000-0xcfdfffff 64bit pref]
[    0.867275] pci 0000:01:00.0: reg 20: [mem 0xcfdf8000-0xcfdfbfff 64bit pref]
[    0.867317] pci 0000:01:00.0: supports D1 D2
[    0.867318] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.867322] pci 0000:01:00.0: PME# disabled
[    0.887118] pci 0000:00:1c.2: PCI bridge to [bus 01-01]
[    0.887124] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.887127] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.887131] pci 0000:00:1c.2:   bridge window [mem 0xcfd00000-0xcfdfffff 64bit pref]
[    0.887167] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.887170] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.887173] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.887177] pci 0000:00:1c.4:   bridge window [mem 0xcfe00000-0xcfefffff 64bit pref]
[    0.887217] pci 0000:05:00.0: reg 10: [mem 0xfbef0000-0xfbefffff]
[    0.887294] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.887297] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.887300] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.887304] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.887306] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.887308] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.887310] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.887312] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.887314] pci 0000:00:1e.0:   bridge window [mem 0xcc000000-0xdfffffff] (subtractive decode)
[    0.887315] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfed8ffff] (subtractive decode)
[    0.887344] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.887513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.887570] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR1E._PRT]
[    0.887664] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR20._PRT]
[    0.887713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR21._PRT]
[    0.887759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR22._PRT]
[    0.887807] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR24._PRT]
[    0.898995] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.899095] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.899194] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.899291] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.899388] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 15) *0, disabled.
[    0.899486] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.899584] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.899681] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.899722] HEST: Table is not found!
[    0.899778] vgaarb: device added: PCI:0000:06:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.899781] vgaarb: loaded
[    0.899876] SCSI subsystem initialized
[    0.899970] libata version 3.00 loaded.
[    0.900006] usbcore: registered new interface driver usbfs
[    0.900013] usbcore: registered new interface driver hub
[    0.900036] usbcore: registered new device driver usb
[    0.900121] ACPI: WMI: Mapper loaded
[    0.900123] PCI: Using ACPI for IRQ routing
[    0.900125] PCI: pci_cache_line_size set to 64 bytes
[    0.900176] reserve RAM buffer: 000000000009e400 - 000000000009ffff 
[    0.900178] reserve RAM buffer: 00000000cb770000 - 00000000cbffffff 
[    0.900251] NetLabel: Initializing
[    0.900252] NetLabel:  domain hash size = 128
[    0.900253] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.900262] NetLabel:  unlabeled traffic allowed by default
[    0.900289] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.900294] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.902302] Switching to clocksource tsc
[    0.908095] AppArmor: AppArmor Filesystem Enabled
[    0.908108] pnp: PnP ACPI init
[    0.908124] ACPI: bus type pnp registered
[    0.911015] pnp: PnP ACPI: found 13 devices
[    0.911016] ACPI: ACPI bus type pnp unregistered
[    0.911026] system 00:01: [mem 0xfc000000-0xfcffffff] has been reserved
[    0.911028] system 00:01: [mem 0xfd000000-0xfdffffff] has been reserved
[    0.911030] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.911032] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.911037] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.911039] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.911041] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.911043] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.911044] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.911046] system 00:06: [mem 0xfed40000-0xfed8ffff] has been reserved
[    0.911052] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.911053] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.911057] system 00:0a: [io  0x0290-0x029f] has been reserved
[    0.911060] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.911063] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.911065] system 00:0c: [mem 0x000c0000-0x000cffff] has been reserved
[    0.911066] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.911068] system 00:0c: [mem 0x00100000-0xcbffffff] could not be reserved
[    0.911070] system 00:0c: [mem 0xfed90000-0xffffffff] could not be reserved
[    0.916460] pci 0000:00:1c.0: BAR 14: assigned [mem 0xcc000000-0xcc3fffff]
[    0.916462] pci 0000:00:1c.4: BAR 14: assigned [mem 0xcc400000-0xcc7fffff]
[    0.916464] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.916466] pci 0000:00:1c.4: BAR 13: assigned [io  0x2000-0x2fff]
[    0.916468] pci 0000:00:01.0: PCI bridge to [bus 06-06]
[    0.916470] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.916472] pci 0000:00:01.0:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.916475] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.916478] pci 0000:00:1c.0: PCI bridge to [bus 04-04]
[    0.916480] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.916484] pci 0000:00:1c.0:   bridge window [mem 0xcc000000-0xcc3fffff]
[    0.916486] pci 0000:00:1c.0:   bridge window [mem 0xcff00000-0xcfffffff 64bit pref]
[    0.916491] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.916492] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.916496] pci 0000:00:1c.1:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.916498] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.916503] pci 0000:00:1c.2: PCI bridge to [bus 01-01]
[    0.916505] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
[    0.916508] pci 0000:00:1c.2:   bridge window [mem disabled]
[    0.916511] pci 0000:00:1c.2:   bridge window [mem 0xcfd00000-0xcfdfffff 64bit pref]
[    0.916516] pci 0000:00:1c.4: PCI bridge to [bus 03-03]
[    0.916518] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    0.916521] pci 0000:00:1c.4:   bridge window [mem 0xcc400000-0xcc7fffff]
[    0.916524] pci 0000:00:1c.4:   bridge window [mem 0xcfe00000-0xcfefffff 64bit pref]
[    0.916529] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.916530] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.916533] pci 0000:00:1e.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.916536] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.916546]   alloc irq_desc for 16 on node -1
[    0.916547]   alloc kstat_irqs on node -1
[    0.916551] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.916554] pci 0000:00:01.0: setting latency timer to 64
[    0.916559] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.916562]   alloc irq_desc for 17 on node -1
[    0.916563]   alloc kstat_irqs on node -1
[    0.916566] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.916569] pci 0000:00:1c.0: setting latency timer to 64
[    0.916575] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.916578] pci 0000:00:1c.1: setting latency timer to 64
[    0.916584]   alloc irq_desc for 18 on node -1
[    0.916585]   alloc kstat_irqs on node -1
[    0.916587] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.916590] pci 0000:00:1c.2: setting latency timer to 64
[    0.916595] pci 0000:00:1c.4: enabling device (0106 -> 0107)
[    0.916598] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.916601] pci 0000:00:1c.4: setting latency timer to 64
[    0.916605] pci 0000:00:1e.0: setting latency timer to 64
[    0.916608] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.916610] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.916611] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.916613] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.916614] pci_bus 0000:00: resource 8 [mem 0xcc000000-0xdfffffff]
[    0.916616] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.916617] pci_bus 0000:06: resource 0 [io  0xe000-0xefff]
[    0.916618] pci_bus 0000:06: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.916620] pci_bus 0000:06: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.916622] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
[    0.916623] pci_bus 0000:04: resource 1 [mem 0xcc000000-0xcc3fffff]
[    0.916625] pci_bus 0000:04: resource 2 [mem 0xcff00000-0xcfffffff 64bit pref]
[    0.916627] pci_bus 0000:02: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.916628] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.916630] pci_bus 0000:01: resource 2 [mem 0xcfd00000-0xcfdfffff 64bit pref]
[    0.916632] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.916633] pci_bus 0000:03: resource 1 [mem 0xcc400000-0xcc7fffff]
[    0.916635] pci_bus 0000:03: resource 2 [mem 0xcfe00000-0xcfefffff 64bit pref]
[    0.916636] pci_bus 0000:05: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.916638] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.916639] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.916641] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.916642] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000dffff]
[    0.916643] pci_bus 0000:05: resource 8 [mem 0xcc000000-0xdfffffff]
[    0.916645] pci_bus 0000:05: resource 9 [mem 0xf0000000-0xfed8ffff]
[    0.916671] NET: Registered protocol family 2
[    0.916788] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.917591] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.919706] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.919960] TCP: Hash tables configured (established 524288 bind 65536)
[    0.919962] TCP reno registered
[    0.919969] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.919999] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.920103] NET: Registered protocol family 1
[    0.920178] pci 0000:06:00.0: Boot video device
[    0.920221] PCI: CLS 32 bytes, default 64
[    0.920223] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.920225] Placing 64MB software IO TLB between ffff880001fde000 - ffff880005fde000
[    0.920226] software IO TLB at phys 0x1fde000 - 0x5fde000
[    0.920444] Scanning for low memory corruption every 60 seconds
[    0.920533] audit: initializing netlink socket (disabled)
[    0.920542] type=2000 audit(1289491336.760:1): initialized
[    0.931644] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.932648] VFS: Disk quotas dquot_6.5.2
[    0.932688] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.933097] fuse init (API version 7.14)
[    0.933155] msgmni has been set to 7875
[    0.933468] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.933470] io scheduler noop registered
[    0.933472] io scheduler deadline registered
[    0.933498] io scheduler cfq registered (default)
[    0.933565] pcieport 0000:00:01.0: setting latency timer to 64
[    0.933582]   alloc irq_desc for 40 on node -1
[    0.933583]   alloc kstat_irqs on node -1
[    0.933591] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.933629] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.933652]   alloc irq_desc for 41 on node -1
[    0.933653]   alloc kstat_irqs on node -1
[    0.933658] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.933705] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.933728]   alloc irq_desc for 42 on node -1
[    0.933729]   alloc kstat_irqs on node -1
[    0.933733] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.933774] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.933797]   alloc irq_desc for 43 on node -1
[    0.933798]   alloc kstat_irqs on node -1
[    0.933803] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.933846] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.933869]   alloc irq_desc for 44 on node -1
[    0.933870]   alloc kstat_irqs on node -1
[    0.933875] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.933931] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.933946] Firmware did not grant requested _OSC control
[    0.933951] Firmware did not grant requested _OSC control
[    0.933962] Firmware did not grant requested _OSC control
[    0.933966] Firmware did not grant requested _OSC control
[    0.933970] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.934019] intel_idle: MWAIT substates: 0x1120
[    0.934021] intel_idle: v0.4 model 0x25
[    0.934022] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.934112] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.934116] ACPI: Power Button [PWRB]
[    0.934145] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.934147] ACPI: Power Button [PWRF]
[    0.934390] ACPI: acpi_idle yielding to intel_idle
[    0.937532] ERST: Table is not found!
[    0.937683] Linux agpgart interface v0.103
[    0.937695] Serial: 8250/16550 begin_of_the_skype_highlighting**************8250/16550******end_of_the_skype_highlighting begin_of_the_skype_highlighting**************8250/16550******end_of_the_skype_highlighting driver, 4 ports, IRQ sharing enabled
[    0.937784] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.938030] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.938697] brd: module loaded
[    0.939000] loop: module loaded
[    0.939272] Fixed MDIO Bus: probed
[    0.939291] PPP generic driver version 2.4.2
[    0.939313] tun: Universal TUN/TAP device driver, 1.6
[    0.939315] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.939358] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.939375] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.939388] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.939390] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.939414] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.939438] ehci_hcd 0000:00:1a.0: debug port 2
[    0.943325] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.943339] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbcf8000
[    0.967028] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.967140] hub 1-0:1.0: USB hub found
[    0.967144] hub 1-0:1.0: 6 ports detected
[    0.967206]   alloc irq_desc for 23 on node -1
[    0.967208]   alloc kstat_irqs on node -1
[    0.967214] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.967239] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.967241] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.967267] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.967288] ehci_hcd 0000:00:1d.0: debug port 2
[    0.971151] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    0.971166] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbcfa000
[    0.980672] Freeing initrd memory: 10740k freed
[    0.986981] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.987116] hub 2-0:1.0: USB hub found
[    0.987120] hub 2-0:1.0: 8 ports detected
[    0.987183] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.987194] uhci_hcd: USB Universal Host Controller Interface driver
[    0.987284] PNP: No PS/2 controller found. Probing ports directly.
[    0.989812] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.989818] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.989872] mice: PS/2 mouse device common for all mice
[    0.989946] rtc_cmos 00:03: RTC can wake from S4
[    0.989975] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.989999] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.990061] device-mapper: uevent: version 1.0.3
[    0.990140] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.990208] device-mapper: multipath: version 1.1.1 loaded
[    0.990210] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.990426] cpuidle: using governor ladder
[    0.990528] cpuidle: using governor menu
[    0.990721] TCP cubic registered
[    0.990803] NET: Registered protocol family 10
[    0.991046] lo: Disabled Privacy Extensions
[    0.991178] NET: Registered protocol family 17
[    0.992726] PM: Resume from disk failed.
[    0.992736] registered taskstats version 1
[    0.992987]   Magic number: 2:515:34
[    0.993074] rtc_cmos 00:03: setting system clock to 2010-11-11 16:02:17 UTC (1289491337)
[    0.993077] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.993078] EDD information not available.
[    0.993147] Freeing unused kernel memory: 908k freed
[    0.993314] Write protecting the kernel read-only data: 10240k
[    0.993467] Freeing unused kernel memory: 416k freed
[    0.993668] Freeing unused kernel memory: 1644k freed
[    1.005164] udev[98]: starting version 163
[    1.036192] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.036213] r8169 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.036260] r8169 0000:01:00.0: setting latency timer to 64
[    1.036265] r8169 0000:01:00.0: (unregistered net_device): unknown MAC, using family default
[    1.036303]   alloc irq_desc for 45 on node -1
[    1.036305]   alloc kstat_irqs on node -1
[    1.036319] r8169 0000:01:00.0: irq 45 for MSI/MSI-X
[    1.036801] r8169 0000:01:00.0: eth0: RTL8168b/8111b at 0xffffc9000067c000, 00:25:22:68:a6:6d, XID 0c200000 IRQ 45
[    1.038808] ahci 0000:00:1f.2: version 3.0
[    1.038822]   alloc irq_desc for 19 on node -1
[    1.038824]   alloc kstat_irqs on node -1
[    1.038831] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.038870]   alloc irq_desc for 46 on node -1
[    1.038872]   alloc kstat_irqs on node -1
[    1.038880] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.038908] ahci: SSS flag set, parallel bus scan disabled
[    1.056889] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.056894] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.056899] ahci 0000:00:1f.2: setting latency timer to 64
[    1.156645] scsi0 : ahci
[    1.156753] scsi1 : ahci
[    1.156808] scsi2 : ahci
[    1.156859] scsi3 : ahci
[    1.156912] scsi4 : ahci
[    1.156964] scsi5 : ahci
[    1.157125] ata1: SATA max UDMA/133 abar m2048@0xfbcfc000 port 0xfbcfc100 irq 46
[    1.157129] ata2: SATA max UDMA/133 abar m2048@0xfbcfc000 port 0xfbcfc180 irq 46
[    1.157131] ata3: SATA max UDMA/133 abar m2048@0xfbcfc000 port 0xfbcfc200 irq 46
[    1.157134] ata4: SATA max UDMA/133 abar m2048@0xfbcfc000 port 0xfbcfc280 irq 46
[    1.157137] ata5: SATA max UDMA/133 abar m2048@0xfbcfc000 port 0xfbcfc300 irq 46
[    1.157140] ata6: SATA max UDMA/133 abar m2048@0xfbcfc000 port 0xfbcfc380 irq 46
[    1.291554] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.443155] hub 1-1:1.0: USB hub found
[    1.443339] hub 1-1:1.0: 6 ports detected
[    1.512958] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.514220] ata1.00: ATA-8: WDC WD5000AADS-00S9B0, 01.00A01, max UDMA/133
[    1.514225] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.515615] ata1.00: configured for UDMA/133
[    1.531241] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AADS-0 01.0 PQ: 0 ANSI: 5
[    1.531413] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.531459] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.531490] sd 0:0:0:0: [sda] Write Protect is off
[    1.531492] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.531504] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.531603]  sda:
[    1.570914] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.601108]  sda1 sda2 sda3 sda4 sda5 sda6 sda7
[    1.601566] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.721333] hub 2-1:1.0: USB hub found
[    1.721549] hub 2-1:1.0: 8 ports detected
[    2.020098] usb 2-1.1: new low speed USB device using ehci_hcd and address 3
[    2.183412] usbcore: registered new interface driver hiddev
[    2.185992] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2
[    2.186074] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1.1/input0
[    2.191667] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input3
[    2.191771] generic-usb 0003:0603:00F2.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1.1/input1
[    2.191786] usbcore: registered new interface driver usbhid
[    2.191788] usbhid: USB HID core driver
[    2.209648] usb 2-1.2: new low speed USB device using ehci_hcd and address 4
[    2.279337] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.281031] ata2.00: ATAPI: Optiarc DVD RW AD-7240S, 1.03, max UDMA/100
[    2.283133] ata2.00: configured for UDMA/100
[    2.300621] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7240S  1.03 PQ: 0 ANSI: 5
[    2.305364] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.305370] Uniform CD-ROM driver Revision: 3.20
[    2.305508] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.305549] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.336860] input: HID 1241:1166 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4
[    2.336913] generic-usb 0003:1241:1166.0003: input,hidraw2: USB HID v1.00 Mouse [HID 1241:1166] on usb-0000:00:1d.0-1.2/input0
[    2.650386] ata3: SATA link down (SStatus 0 SControl 300)
[    3.017667] ata4: SATA link down (SStatus 0 SControl 300)
[    3.388699] ata5: SATA link down (SStatus 0 SControl 300)
[    3.755994] ata6: SATA link down (SStatus 0 SControl 300)
[    5.005439] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.682863] udev[401]: starting version 163
[   13.700485] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.700535] xhci_hcd 0000:02:00.0: setting latency timer to 64
[   13.700539] xhci_hcd 0000:02:00.0: xHCI Host Controller
[   13.700600] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 3
[   13.720331] lp: driver loaded but no devices found
[   13.771140] Adding 3999740k swap on /dev/sda5.  Priority:-1 extents:1 across:3999740k 
[   13.793589] cfg80211: Calling CRDA to update world regulatory domain
[   13.795884] type=1400 audit(1289462550.330:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=551 comm="apparmor_parser"
[   13.796339] type=1400 audit(1289462550.330:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=551 comm="apparmor_parser"
[   13.796579] type=1400 audit(1289462550.330:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=551 comm="apparmor_parser"
[   13.830059] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   13.830062] Disabling lock debugging due to kernel taint
[   13.832345] cfg80211: World regulatory domain updated:
[   13.832347]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.832350]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.832352]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.832355]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.832357]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.832359]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.833227] xhci_hcd 0000:02:00.0: irq 17, io mem 0xfbdf0000
[   13.833263] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   13.833452] xHCI xhci_add_endpoint called for root hub
[   13.833454] xHCI xhci_check_bandwidth called for root hub
[   13.833545] hub 3-0:1.0: USB hub found
[   13.833554] hub 3-0:1.0: 2 ports detected
[   13.916410]   alloc irq_desc for 22 on node -1
[   13.916413]   alloc kstat_irqs on node -1
[   13.916420] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.916485]   alloc irq_desc for 47 on node -1
[   13.916486]   alloc kstat_irqs on node -1
[   13.916494] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   13.916517] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.917814]   alloc irq_desc for 21 on node -1
[   13.917816]   alloc kstat_irqs on node -1
[   13.917821] rt2800pci 0000:05:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   13.924037] phy0: Selected rate control algorithm 'minstrel'
[   13.924450] Registered led device: rt2800pci-phy0::radio
[   13.924469] Registered led device: rt2800pci-phy0::assoc
[   13.924486] Registered led device: rt2800pci-phy0::quality
[   13.939452] [fglrx] Maximum main memory to use for locked dma buffers: 3789 MBytes.
[   13.939491] [fglrx]   vendor: 1002 device: 68d8 count: 1
[   13.939699] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   13.939711] pci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.939714] pci 0000:06:00.0: setting latency timer to 64
[   13.939907] [fglrx] Kernel PAT support is enabled
[   13.939919] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   14.013178] hda_codec: ALC892: BIOS auto-probing.
[   14.018920] Too many connections
[   14.020319] HDA Intel 0000:06:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.020383]   alloc irq_desc for 48 on node -1
[   14.020384]   alloc kstat_irqs on node -1
[   14.020394] HDA Intel 0000:06:00.1: irq 48 for MSI/MSI-X
[   14.020414] HDA Intel 0000:06:00.1: setting latency timer to 64
[   15.050838] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   15.230575] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   15.547588] r8169 0000:01:00.0: eth0: link up
[   15.547596] r8169 0000:01:00.0: eth0: link up
[   15.549446] type=1400 audit(1289462552.080:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1043 comm="apparmor_parser"
[   15.550047] type=1400 audit(1289462552.080:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1043 comm="apparmor_parser"
[   15.550323] type=1400 audit(1289462552.080:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1043 comm="apparmor_parser"
[   15.550332] type=1400 audit(1289462552.080:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1044 comm="apparmor_parser"
[   15.551163] type=1400 audit(1289462552.090:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1042 comm="apparmor_parser"
[   15.552159] type=1400 audit(1289462552.090:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1048 comm="apparmor_parser"
[   15.555371] type=1400 audit(1289462552.090:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1044 comm="apparmor_parser"
[   15.558879] ppdev: user-space parallel port driver
[   15.691184] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.949042]   alloc irq_desc for 49 on node -1
[   15.949045]   alloc kstat_irqs on node -1
[   15.949054] fglrx_pci 0000:06:00.0: irq 49 for MSI/MSI-X
[   15.949498] [fglrx] Firegl kernel thread PID: 1226
[   15.949724] [fglrx] IRQ 49 Enabled
[   16.186535] [fglrx] Gart USWC size:1236 M.
[   16.186538] [fglrx] Gart cacheable size:489 M.
[   16.186543] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   16.186544] [fglrx] Reserved FB block: Unshared offset:f921000, size:3df000 
[   16.186546] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   16.490570] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   16.493605] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   17.705354] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   17.709424] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   18.329200] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   25.824261] eth0: no IPv6 routers present
[SIZE=3]**daniel@Rincewind:~$ sudo lshw -C network**[/SIZE]
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:68:a6:6d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 ioport:d800(size=256) memory:cfdff000-cfdfffff memory:cfdf8000-cfdfbfff
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: c8:3a:35:c6:47:d3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic firmware=N/A latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:21 memory:fbef0000-fbefffff
[SIZE=3]**daniel@Rincewind:~$ iwlist scan**[/SIZE]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
[SIZE=3][B]
daniel@Rincewind:~$ lsb_release -d[/B][/SIZE]
Description:    Ubuntu 10.10
[SIZE=3]**daniel@Rincewind:~$ uname -mr**[/SIZE]
2.6.35-22-generic x86_64
[SIZE=3]**daniel@Rincewind:~$ sudo /etc/init.d/networking restart**[/SIZE]
 * Reconfiguring network interfaces...                                                                                                                 [ OK ] 

```

---

### Post by sukharevd on 2010-11-11
Maybe this can help you:
[http://ubuntuforums.org/showpost.php?p=10099497&postcount=5](http://ubuntuforums.org/showpost.php?p=10099497&postcount=5)

---

### Post by Zeophlite on 2010-11-13
Sorry sukharevd, that's a bit beyond me.

I've noticed that lspci gives:
05:00.0 Network controller: RaLink Device 3062

So I went to RaLink's website, looked for 3062 drivers and found:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Which lists RT3062PCI.

I downloaded it, but I don't know how to install it!  It has some .dat files, such as RT2860STA.dat, but I'm not sure what to do with it.

---

### Post by uncaspi on 2010-11-13
The driver file has the extension .ko

---

### Post by grahammechanical on 2010-11-13
ifconfig indicates that you are connected by ethernet.do you notice that eth0 is listed as UP and also as RUNNING, but wlan0 is only listed as UP?


The listing for iwconfig is exactly the same as the listing for my machine. Notice that you have Tx-Power=20 dBm. This means that the system knows that you have a wireless network card but it is not connected to a Internet access point such as an ISP otherwise the ESSID would be different. It would show the name of the wireless network you were connected to.

lshw -C network shows that your wireless device is recognised.

When you left click the network manager icon do you see a list of Available networks? Type in a terminal rfkill list

Does the listing show Yes for soft blocked or hard blocked? If so then your wireless device is switched off either by software or by hardware? Is wireless networking enabled? Right click the icon. Try disabling and enabling networking to see if the wireless device switches on and detects available wireless networks.

Regards

---

### Post by Scallyph on 2010-11-13
Hi,

If sukharevd suggestion is to much, I suppose you dont want to try this:  [http://ubuntuforums.org/showpost.php...97&postcount=5](http://ubuntuforums.org/showpost.php...97&postcount=5) or:  [http://www.linuxforums.org/forum/wireless-internet/167373-ubuntu-tenda-w322p-pci-card-problems.html](http://www.linuxforums.org/forum/wireless-internet/167373-ubuntu-tenda-w322p-pci-card-problems.html).
They end up almost the same as they started

My search words are/were : Tenda W322P Wireless PCI adapter linux solved gave me just 41 hits.
If I had this card I would sell it and buy an new one, after I checked:  [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported). But  that 's just me.

hope those links wil help you anyway.

---

### Post by savastux on 2010-11-13
Hello grahammechanical, I have the same problem Zeophlite is having.

in my rfkill list, i have:

```

$sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Any suggestions?

Thanks,
Savastux

---

