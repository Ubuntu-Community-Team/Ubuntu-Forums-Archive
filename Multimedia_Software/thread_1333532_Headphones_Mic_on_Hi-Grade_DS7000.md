---
title: "Headphones/ Mic on Hi-Grade DS7000"
date: 2009-11-21
forum: Multimedia Software
---

### Post by &gt;:3 on 2009-11-21
G'day all, 

I've got a Hi-Grade Notino D7000, and I've had a history of sound problems [http://ubuntuforums.org/showpost.php?p=6452542&postcount=6]("http://ubuntuforums.org/showpost.php?p=6452542&postcount=6")

However, with the Wonderful 9.10, My sound works out of the main speakers, and I'm ecstatic, it's almost perfect! 

But: Headphone & Mic sockets produce/ register no sound. They both work fine under vista, so it's not a problem with the headphone/ microphone/ hardware. 

- Alsamixer has nothing muted
- No Combination under System > Prefs > Sound have any effect. 

So here's some terminal outputs :D

[B]aplay -l
[/B]```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

[B]find /lib/modules/`uname -r` | grep snd 
[/B]Gives a really big list. I can add it if necessary. 

[B] lspci -v 
[/B]```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fb000000-fb0fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fb304800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Rioworks Device 2073
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fb300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f8000000-f8ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000c00fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f9000000-f9ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: fa000000-faffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fb304c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Rioworks Device 2073
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Rioworks Device 2073
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fb304000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Rioworks Device 2073
	Flags: medium devsel, IRQ 10
	Memory at c0100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 2400 XT
	Subsystem: Rioworks Device 2073
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at fb000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fb020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
	Subsystem: Rioworks Device 2073
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fb010000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Rioworks Device 2073
	Flags: bus master, fast devsel, latency 0, IRQ 29
	I/O ports at 3000 [size=256]
	Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c0000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Intel Corporation Device 1001
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at f9000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945
```

**uname -a**
```
Linux Craptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```

** amixer **
```
 Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 42 [66%] [-16.50dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 253 [99%] [0.40dB]
  Front Right: Playback 253 [99%] [0.40dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2'
  Item0: 'Digital Playback'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [off]
  Front Right: Capture 15 [100%] [22.50dB] [off]
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1'
  Item0: 'Analog Inputs'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]

```

** dmesg**
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=e927eede-bd2e-4954-a650-91ecefe1bdad ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfedf000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfed0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  modified: 00000000bfed0000 - 00000000bfedf000 (ACPI NVS)
[    0.000000]  modified: 00000000bfedf000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bfed0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bfed0000 page 4k
[    0.000000] kernel direct mapping tables up to bfed0000 @ 8000-d000
[    0.000000] RAMDISK: 377df000 - 37fef1c7
[    0.000000] ACPI: RSDP 00000000000f7340 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 00000000bfed3a71 0008C (v01 higrad higraded 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 00000000bfedbbd2 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 00000000bfed5030 06B2E (v02 INTEL  CRESTLNE 06040000 INTL 20050624)
[    0.000000] ACPI: FACS 00000000bfedefc0 00040
[    0.000000] ACPI: APIC 00000000bfedbcc6 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 00000000bfedbd2e 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 00000000bfedbd66 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 00000000bfedbda2 00032 (v01 Intel   CRESTLN 06040000      00005A52)
[    0.000000] ACPI: TMOR 00000000bfedbdd4 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: SLIC 00000000bfedbdfa 00176 (v01 higrad higraded 06040000 Kevi 00000001)
[    0.000000] ACPI: APIC 00000000bfedbf70 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 00000000bfedbfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 00000000bfed4d53 002DD (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bfed4089 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bfed3fe3 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 00000000bfed3afd 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000bfed0000
[    0.000000] Bootmem setup node 0 0000000000000000-00000000bfed0000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000027fdf] pages 18
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00bfed0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [00377df000 - 0037fef1c7]          RAMDISK ==> [00377df000 - 0037fef1c7]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3198]              BRK ==> [00019e3000 - 00019e3198]
[    0.000000]   #6 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000f7370] f7370
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff880001e00000-ffff8800047fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfed0
[    0.000000] On node 0 totalpages: 786026
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3836 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10692 pages used for memmap
[    0.000000]   DMA32 zone: 771340 pages, LIFO batch:31
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880001a00000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 775176
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=e927eede-bd2e-4954-a650-91ecefe1bdad ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3082248k/3144512k available (5313k kernel code, 408k absent, 61856k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2394.044 MHz processor.
[    0.000930] Console: colour VGA+ 80x25
[    0.000933] console [tty0] enabled
[    0.010000] allocated 31457280 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.08 BogoMIPS (lpj=23940440)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring handled by SMI
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.017456] Setting APIC routing to flat
[    0.017804] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.117828] CPU0: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4787.97 BogoMIPS (lpj=23939877)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.271402] CPU1: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.271411] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280024] Brought up 2 CPUs
[    0.280026] Total of 2 processors activated (9576.06 BogoMIPS).
[    0.280079] CPU0 attaching sched-domain:
[    0.280082]  domain 0: span 0-1 level MC
[    0.280084]   groups: 0 1
[    0.280088] CPU1 attaching sched-domain:
[    0.280090]  domain 0: span 0-1 level MC
[    0.280092]   groups: 1 0
[    0.280161] Booting paravirtualized kernel on bare hardware
[    0.280161] regulator: core version 0.5
[    0.280161] Time: 14:52:22  Date: 11/21/09
[    0.280161] NET: Registered protocol family 16
[    0.280190] ACPI: bus type pci registered
[    0.280251] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.280253] PCI: MCFG area at e0000000 reserved in E820
[    0.284078] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.284080] PCI: Using configuration type 1 for base access
[    0.284781] bio: create slab <bio-0> at 0
[    0.284781] ACPI: EC: Look up EC in DSDT
[    0.284781] ACPI: BIOS _OSI(Linux) query ignored
[    0.291280] ACPI: Interpreter enabled
[    0.291282] ACPI: (supports S0 S3 S4 S5)
[    0.291299] ACPI: Using IOAPIC for interrupt routing
[    0.290016] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.310332] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.313452] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.313454] ACPI: EC: driver started in interrupt mode
[    0.313767] ACPI: No dock devices found.
[    0.314278] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.314372] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.314375] pci 0000:00:01.0: PME# disabled
[    0.314470] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.314539] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.314611] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfb304800-0xfb304bff]
[    0.314676] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.314681] pci 0000:00:1a.7: PME# disabled
[    0.314733] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfb300000-0xfb303fff]
[    0.314792] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.314796] pci 0000:00:1b.0: PME# disabled
[    0.314879] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.314883] pci 0000:00:1c.0: PME# disabled
[    0.314969] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.314974] pci 0000:00:1c.1: PME# disabled
[    0.315059] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.315064] pci 0000:00:1c.2: PME# disabled
[    0.315141] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]
[    0.315209] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]
[    0.315284] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]
[    0.315361] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfb304c00-0xfb304fff]
[    0.315427] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.315432] pci 0000:00:1d.7: PME# disabled
[    0.315594] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.315598] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.315601] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.315605] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
[    0.315659] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.315666] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.315673] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.315681] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.315688] pci 0000:00:1f.1: reg 20 io port: [0x18a0-0x18af]
[    0.315761] pci 0000:00:1f.2: reg 10 io port: [0x18d8-0x18df]
[    0.315767] pci 0000:00:1f.2: reg 14 io port: [0x18cc-0x18cf]
[    0.315775] pci 0000:00:1f.2: reg 18 io port: [0x18d0-0x18d7]
[    0.315782] pci 0000:00:1f.2: reg 1c io port: [0x18c8-0x18cb]
[    0.315789] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.315796] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfb304000-0xfb3047ff]
[    0.315836] pci 0000:00:1f.2: PME# supported from D3hot
[    0.315841] pci 0000:00:1f.2: PME# disabled
[    0.315871] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.315894] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.315946] pci 0000:01:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.315951] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.315957] pci 0000:01:00.0: reg 18 32bit mmio: [0xfb000000-0xfb00ffff]
[    0.315973] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.315992] pci 0000:01:00.0: supports D1 D2
[    0.316022] pci 0000:01:00.1: reg 10 32bit mmio: [0xfb010000-0xfb013fff]
[    0.316062] pci 0000:01:00.1: supports D1 D2
[    0.316121] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.316124] pci 0000:00:01.0: bridge 32bit mmio: [0xfb000000-0xfb0fffff]
[    0.316128] pci 0000:00:01.0: bridge 64bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.316199] pci 0000:02:00.0: reg 10 io port: [0x3000-0x30ff]
[    0.316227] pci 0000:02:00.0: reg 18 64bit mmio: [0xf8000000-0xf8000fff]
[    0.316255] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.316317] pci 0000:02:00.0: supports D1 D2
[    0.316318] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.316324] pci 0000:02:00.0: PME# disabled
[    0.316395] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.316399] pci 0000:00:1c.0: bridge 32bit mmio: [0xf8000000-0xf8ffffff]
[    0.316545] pci 0000:04:00.0: reg 10 32bit mmio: [0xf9000000-0xf9000fff]
[    0.316782] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.316795] pci 0000:04:00.0: PME# disabled
[    0.316902] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.316907] pci 0000:00:1c.1: bridge 32bit mmio: [0xf9000000-0xf9ffffff]
[    0.316967] pci 0000:00:1c.2: bridge io port: [0x5000-0x5fff]
[    0.316971] pci 0000:00:1c.2: bridge 32bit mmio: [0xfa000000-0xfaffffff]
[    0.317042] pci 0000:00:1e.0: transparent bridge
[    0.317083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.317262] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.317333] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.317397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.317458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.317546] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.325528] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.325615] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.325700] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.325784] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.325869] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.325954] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.326038] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.326123] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.326265] SCSI subsystem initialized
[    0.326282] libata version 3.00 loaded.
[    0.326282] usbcore: registered new interface driver usbfs
[    0.326282] usbcore: registered new interface driver hub
[    0.326282] usbcore: registered new device driver usb
[    0.326282] ACPI: WMI: Mapper loaded
[    0.326282] PCI: Using ACPI for IRQ routing
[    0.350008] Bluetooth: Core ver 2.15
[    0.350021] NET: Registered protocol family 31
[    0.350021] Bluetooth: HCI device and connection manager initialized
[    0.350021] Bluetooth: HCI socket layer initialized
[    0.350021] NetLabel: Initializing
[    0.350021] NetLabel:  domain hash size = 128
[    0.350021] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.350031] NetLabel:  unlabeled traffic allowed by default
[    0.350072] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.350076] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.390005] pnp: PnP ACPI init
[    0.390015] ACPI: bus type pnp registered
[    0.391763] pnp: PnP ACPI: found 10 devices
[    0.391765] ACPI: ACPI bus type pnp unregistered
[    0.391774] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.391776] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.391779] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.391781] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.391783] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.391786] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.391788] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.391790] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.391795] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.391801] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.391803] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.391805] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.391807] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.391810] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.391812] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.396462] AppArmor: AppArmor Filesystem Enabled
[    0.396522] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.396525] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.396528] pci 0000:00:01.0:   MEM window: 0xfb000000-0xfb0fffff
[    0.396531] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.396536] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.396539] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.396545] pci 0000:00:1c.0:   MEM window: 0xf8000000-0xf8ffffff
[    0.396549] pci 0000:00:1c.0:   PREFETCH window: 0xc0000000-0xc00fffff
[    0.396553] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.396556] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.396562] pci 0000:00:1c.1:   MEM window: 0xf9000000-0xf9ffffff
[    0.396566] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.396570] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.396573] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.396579] pci 0000:00:1c.2:   MEM window: 0xfa000000-0xfaffffff
[    0.396583] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.396588] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.396589] pci 0000:00:1e.0:   IO window: disabled
[    0.396594] pci 0000:00:1e.0:   MEM window: disabled
[    0.396598] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.396608]   alloc irq_desc for 16 on node 0
[    0.396610]   alloc kstat_irqs on node 0
[    0.396614] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.396617] pci 0000:00:01.0: setting latency timer to 64
[    0.396626]   alloc irq_desc for 17 on node 0
[    0.396627]   alloc kstat_irqs on node 0
[    0.396630] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.396634] pci 0000:00:1c.0: setting latency timer to 64
[    0.396642] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.396646] pci 0000:00:1c.1: setting latency timer to 64
[    0.396653]   alloc irq_desc for 18 on node 0
[    0.396655]   alloc kstat_irqs on node 0
[    0.396657] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.396662] pci 0000:00:1c.2: setting latency timer to 64
[    0.396669] pci 0000:00:1e.0: setting latency timer to 64
[    0.396673] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.396675] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.396677] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.396679] pci_bus 0000:01: resource 1 mem: [0xfb000000-0xfb0fffff]
[    0.396681] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.396683] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.396685] pci_bus 0000:02: resource 1 mem: [0xf8000000-0xf8ffffff]
[    0.396686] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xc00fffff]
[    0.396688] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.396690] pci_bus 0000:04: resource 1 mem: [0xf9000000-0xf9ffffff]
[    0.396692] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.396694] pci_bus 0000:06: resource 1 mem: [0xfa000000-0xfaffffff]
[    0.396696] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
[    0.396698] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.396724] NET: Registered protocol family 2
[    0.396869] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.398128] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.403282] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.403954] TCP: Hash tables configured (established 524288 bind 65536)
[    0.403957] TCP reno registered
[    0.404077] NET: Registered protocol family 1
[    0.404147] Trying to unpack rootfs image as initramfs...
[    0.501443] Switched to high resolution mode on CPU 1
[    0.510000] Switched to high resolution mode on CPU 0
[    0.569718] Freeing initrd memory: 8256k freed
[    0.573973] Simple Boot Flag at 0x36 set to 0x1
[    0.574138] Scanning for low memory corruption every 60 seconds
[    0.574273] audit: initializing netlink socket (disabled)
[    0.574290] type=2000 audit(1258815141.572:1): initialized
[    0.582705] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.583902] VFS: Disk quotas dquot_6.5.2
[    0.583949] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.584440] fuse init (API version 7.12)
[    0.584509] msgmni has been set to 6036
[    0.584685] alg: No test for stdrng (krng)
[    0.584693] io scheduler noop registered
[    0.584695] io scheduler anticipatory registered
[    0.584697] io scheduler deadline registered
[    0.584731] io scheduler cfq registered (default)
[    0.584869] pci 0000:01:00.0: Boot video device
[    0.584984]   alloc irq_desc for 24 on node 0
[    0.584985]   alloc kstat_irqs on node 0
[    0.584994] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.585000] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.585140]   alloc irq_desc for 25 on node 0
[    0.585141]   alloc kstat_irqs on node 0
[    0.585150] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.585160] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.585321]   alloc irq_desc for 26 on node 0
[    0.585323]   alloc kstat_irqs on node 0
[    0.585331] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.585341] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.585501]   alloc irq_desc for 27 on node 0
[    0.585502]   alloc kstat_irqs on node 0
[    0.585510] pcieport-driver 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.585521] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.585620] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.585727] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.586137] ACPI: AC Adapter [AC] (on-line)
[    0.586205] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.586208] ACPI: Power Button [PWRF]
[    0.586254] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.586551] ACPI: Lid Switch [LID0]
[    0.586590] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.586596] ACPI: Power Button [PWRB]
[    0.586630] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.586635] ACPI: Sleep Button [SLPB]
[    0.587233] ACPI: SSDT 00000000bfed49cf 002BC (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.587650] ACPI: SSDT 00000000bfed42e8 00662 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.589688] Monitor-Mwait will be used to enter C-1 state
[    0.589707] Monitor-Mwait will be used to enter C-2 state
[    0.589753] Monitor-Mwait will be used to enter C-3 state
[    0.589760] Marking TSC unstable due to TSC halts in idle
[    0.589781] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.589827] processor LNXCPU:00: registered as cooling_device0
[    0.589830] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.590151] ACPI: SSDT 00000000bfed4c8b 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.590407] ACPI: SSDT 00000000bfed494a 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.591269] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.591285] processor LNXCPU:01: registered as cooling_device1
[    0.591288] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.593504] ACPI: Invalid passive threshold
[    0.594187] thermal LNXTHERM:01: registered as thermal_zone0
[    0.594194] ACPI: Thermal Zone [TZ00] (57 C)
[    0.595153] Linux agpgart interface v0.103
[    0.595161] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.596157] brd: module loaded
[    0.596524] loop: module loaded
[    0.596586] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.596678] ahci 0000:00:1f.2: version 3.0
[    0.596693]   alloc irq_desc for 19 on node 0
[    0.596695]   alloc kstat_irqs on node 0
[    0.596700] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.596730]   alloc irq_desc for 28 on node 0
[    0.596731]   alloc kstat_irqs on node 0
[    0.596743] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    0.596839] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    0.596842] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    0.596849] ahci 0000:00:1f.2: setting latency timer to 64
[    0.596979] ACPI: Battery Slot [BAT0] (battery absent)
[    0.597087] scsi0 : ahci
[    0.597161] scsi1 : ahci
[    0.597211] scsi2 : ahci
[    0.597295] ata1: SATA max UDMA/133 abar m2048@0xfb304000 port 0xfb304100 irq 28
[    0.597298] ata2: SATA max UDMA/133 abar m2048@0xfb304000 port 0xfb304180 irq 28
[    0.597301] ata3: SATA max UDMA/133 abar m2048@0xfb304000 port 0xfb304200 irq 28
[    0.597406] ata_piix 0000:00:1f.1: version 2.13
[    0.597414] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.597445] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.597507] scsi3 : ata_piix
[    0.597555] scsi4 : ata_piix
[    0.598048] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.598050] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.598687] Fixed MDIO Bus: probed
[    0.598714] PPP generic driver version 2.4.2
[    0.598792] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.598831] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.598843] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.598846] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.598891] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.602800] ehci_hcd 0000:00:1a.7: debug port 1
[    0.602806] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.602817] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb304800
[    0.630024] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.630094] usb usb1: configuration #1 chosen from 1 choice
[    0.630117] hub 1-0:1.0: USB hub found
[    0.630124] hub 1-0:1.0: 4 ports detected
[    0.630201]   alloc irq_desc for 23 on node 0
[    0.630203]   alloc kstat_irqs on node 0
[    0.630207] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.630215] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.630218] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.630250] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.634139] ehci_hcd 0000:00:1d.7: debug port 1
[    0.634145] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.634156] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb304c00
[    0.660012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.660056] usb usb2: configuration #1 chosen from 1 choice
[    0.660078] hub 2-0:1.0: USB hub found
[    0.660083] hub 2-0:1.0: 6 ports detected
[    0.660138] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.660151] uhci_hcd: USB Universal Host Controller Interface driver
[    0.660222] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.660228] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.660231] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.660254] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.660287] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.660352] usb usb3: configuration #1 chosen from 1 choice
[    0.660374] hub 3-0:1.0: USB hub found
[    0.660380] hub 3-0:1.0: 2 ports detected
[    0.660453]   alloc irq_desc for 21 on node 0
[    0.660455]   alloc kstat_irqs on node 0
[    0.660458] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.660464] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.660467] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.660492] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.660525] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.660590] usb usb4: configuration #1 chosen from 1 choice
[    0.660609] hub 4-0:1.0: USB hub found
[    0.660615] hub 4-0:1.0: 2 ports detected
[    0.660683] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.660689] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.660692] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.660720] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.660746] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.660812] usb usb5: configuration #1 chosen from 1 choice
[    0.660832] hub 5-0:1.0: USB hub found
[    0.660837] hub 5-0:1.0: 2 ports detected
[    0.660908] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.660913] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.660916] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.660942] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.660975] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.661040] usb usb6: configuration #1 chosen from 1 choice
[    0.661060] hub 6-0:1.0: USB hub found
[    0.661066] hub 6-0:1.0: 2 ports detected
[    0.661131] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.661137] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.661140] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.661167] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.661193] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.661257] usb usb7: configuration #1 chosen from 1 choice
[    0.661279] hub 7-0:1.0: USB hub found
[    0.661284] hub 7-0:1.0: 2 ports detected
[    0.661367] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.663750] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.663754] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.663807] mice: PS/2 mouse device common for all mice
[    0.663913] rtc_cmos 00:07: RTC can wake from S4
[    0.663940] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.663970] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.664044] device-mapper: uevent: version 1.0.3
[    0.664110] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.664166] device-mapper: multipath: version 1.1.0 loaded
[    0.664169] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.664364] cpuidle: using governor ladder
[    0.664456] cpuidle: using governor menu
[    0.664772] TCP cubic registered
[    0.664877] NET: Registered protocol family 10
[    0.665223] lo: Disabled Privacy Extensions
[    0.665458] NET: Registered protocol family 17
[    0.665474] Bluetooth: L2CAP ver 2.13
[    0.665476] Bluetooth: L2CAP socket layer initialized
[    0.665479] Bluetooth: SCO (Voice Link) ver 0.6
[    0.665481] Bluetooth: SCO socket layer initialized
[    0.665509] Bluetooth: RFCOMM TTY layer initialized
[    0.665512] Bluetooth: RFCOMM socket layer initialized
[    0.665513] Bluetooth: RFCOMM ver 1.11
[    0.666062] PM: Resume from disk failed.
[    0.666073] registered taskstats version 1
[    0.666168]   Magic number: 1:433:890
[    0.666198] pci 0000:00:1f.3: hash matches
[    0.666256] rtc_cmos 00:07: setting system clock to 2009-11-21 14:52:22 UTC (1258815142)
[    0.666259] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.666260] EDD information not available.
[    0.695273] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.772893] ata4.00: ATAPI: TSSTcorp CDDVDW SN-S082H, SB01, max UDMA/33
[    0.810340] ata4.00: configured for UDMA/33
[    0.940063] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.940088] ata2: SATA link down (SStatus 0 SControl 300)
[    0.940111] ata3: SATA link down (SStatus 0 SControl 300)
[    0.943989] ACPI Warning: \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
[    0.943995] ata1.00: _GTF unexpected object type 0x1
[    0.945781] ata1.00: ATA-8: SAMSUNG HM250JI, HS100-08, max UDMA7
[    0.945785] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    0.951465] ata1.00: _GTF unexpected object type 0x1
[    0.953318] ata1.00: configured for UDMA/133
[    0.972716] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250JI  HS10 PQ: 0 ANSI: 5
[    0.972803] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.972840] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.972877] sd 0:0:0:0: [sda] Write Protect is off
[    0.972880] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.972899] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.973010]  sda:
[    0.976801] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-S082H  SB01 PQ: 0 ANSI: 5
[    0.991849] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.991853] Uniform CD-ROM driver Revision: 3.20
[    0.991964] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    0.991994] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    0.998496]  sda1 sda2 sda3 <
[    1.002538] Clocksource tsc unstable (delta = -252003594 ns)
[    1.013333]  sda5 sda6 sda7 >
[    1.049248] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.049291] Freeing unused kernel memory: 660k freed
[    1.049519] Write protecting the kernel read-only data: 7580k
[    1.072564] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.143946] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    1.152583] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.152609] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.152663] r8169 0000:02:00.0: setting latency timer to 64
[    1.152741]   alloc irq_desc for 29 on node 0
[    1.152743]   alloc kstat_irqs on node 0
[    1.152760] r8169 0000:02:00.0: irq 29 for MSI/MSI-X
[    1.153254] eth0: RTL8101e at 0xffffc90000674000, 00:03:25:5b:3b:6a, XID 34200000 IRQ 29
[    1.170870] acpi device:06: registered as cooling_device2
[    1.170990] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input6
[    1.171030] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.230127] usb 1-3: configuration #1 chosen from 1 choice
[    1.410083] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    1.573851] usb 2-4: configuration #1 chosen from 1 choice
[    1.579142] Initializing USB Mass Storage driver...
[    1.579309] scsi5 : SCSI emulation for USB Mass Storage devices
[    1.579405] usb-storage: device found at 3
[    1.579406] usb-storage: waiting for device to settle before scanning
[    1.579409] usbcore: registered new interface driver usb-storage
[    1.579412] USB Mass Storage support registered.
[    1.980106] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.004951] xor: automatically using best checksumming function: generic_sse
[    2.052520]    generic_sse:  9626.400 MB/sec
[    2.052522] xor: using function: generic_sse (9626.400 MB/sec)
[    2.068663] device-mapper: dm-raid45: initialized v0.2594b
[    2.181411] usb 3-2: configuration #1 chosen from 1 choice
[    2.269910] PM: Starting manual resume from disk
[    2.269913] PM: Resume from partition 8:6
[    2.269915] PM: Checking hibernation image.
[    2.270130] PM: Resume from disk failed.
[    2.293205] EXT4-fs (sda5): barriers enabled
[    2.304213] kjournald2 starting: pid 450, dev sda5:8, commit interval 5 seconds
[    2.304249] EXT4-fs (sda5): delayed allocation enabled
[    2.304255] EXT4-fs: file extents enabled
[    2.306411] EXT4-fs: mballoc enabled
[    2.306424] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.470079] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.664922] usb 5-1: configuration #1 chosen from 1 choice
[    2.673492] usbcore: registered new interface driver hiddev
[    2.706097] input: HID 04d9:1133 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input7
[    2.706167] generic-usb 0003:04D9:1133.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:1d.0-1/input0
[    2.706179] usbcore: registered new interface driver usbhid
[    2.706181] usbhid: v2.6:USB HID core driver
[    2.942716] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    3.044234] type=1505 audit(1258815144.873:2): operation="profile_load" pid=482 name=/usr/share/gdm/guest-session/Xsession
[    3.074406] type=1505 audit(1258815144.903:3): operation="profile_load" pid=483 name=/sbin/dhclient3
[    3.074982] type=1505 audit(1258815144.903:4): operation="profile_load" pid=483 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.075284] type=1505 audit(1258815144.903:5): operation="profile_load" pid=483 name=/usr/lib/connman/scripts/dhclient-script
[    3.123363] usb 7-2: configuration #1 chosen from 1 choice
[    3.145695] type=1505 audit(1258815144.976:6): operation="profile_load" pid=484 name=/usr/bin/evince
[    3.154647] type=1505 audit(1258815144.986:7): operation="profile_load" pid=484 name=/usr/bin/evince-previewer
[    3.159893] type=1505 audit(1258815144.986:8): operation="profile_load" pid=484 name=/usr/bin/evince-thumbnailer
[    3.183830] type=1505 audit(1258815145.016:9): operation="profile_load" pid=488 name=/usr/lib/cups/backend/cups-pdf
[    4.369183] Adding 5855652k swap on /dev/sda6.  Priority:-1 extents:1 across:5855652k 
[    5.317227] udev: starting version 147
[    5.547242] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    5.547245] Disabling lock debugging due to kernel taint
[    5.623366] [fglrx] Maximum main memory to use for locked dma buffers: 2872 MBytes.
[    5.623543] [fglrx]   vendor: 1002 device: 94c8 count: 1
[    5.623818] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[    5.623832] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.623837] pci 0000:01:00.0: setting latency timer to 64
[    5.623964] [fglrx] Kernel PAT support is enabled
[    5.623984] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[    5.641916] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    5.642027] usbcore: registered new interface driver btusb
[    5.662659] cfg80211: Calling CRDA to update world regulatory domain
[    6.424582] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.425597] lp: driver loaded but no devices found
[    6.580600] usb-storage: device scan complete
[    6.586892] scsi 5:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.587225] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    6.589972] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    6.626804] Linux video capture interface: v2.00
[    6.976156] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    6.976159] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[    6.976728] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.976742] iwl3945 0000:04:00.0: setting latency timer to 64
[    7.046227] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    7.046230] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    7.046377]   alloc irq_desc for 30 on node 0
[    7.046379]   alloc kstat_irqs on node 0
[    7.046412] iwl3945 0000:04:00.0: irq 30 for MSI/MSI-X
[    7.225386] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[    7.227991] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input8
[    7.228040] usbcore: registered new interface driver uvcvideo
[    7.228043] USB Video Class driver (v0.1.0)
[    7.276895] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input9
[    7.453774] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    7.653489] cfg80211: World regulatory domain updated:
[    7.653492] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.653494] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.653496] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.653498] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.653500] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.653502] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.094263]   alloc irq_desc for 22 on node 0
[    8.094265]   alloc kstat_irqs on node 0
[    8.094272] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.094305] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.261232] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[    8.340511] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    8.340572] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    8.341419] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    8.341452] HDA Intel 0000:01:00.1: setting latency timer to 64
[    9.172634] EXT4-fs (sda5): internal journal on sda5:8
[   12.299971] EXT4-fs (sda7): barriers enabled
[   12.302476] kjournald2 starting: pid 1025, dev sda7:8, commit interval 5 seconds
[   12.313109] EXT4-fs (sda7): internal journal on sda7:8
[   12.313115] EXT4-fs (sda7): delayed allocation enabled
[   12.313119] EXT4-fs: file extents enabled
[   12.315880] EXT4-fs: mballoc enabled
[   12.315894] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   13.319197] __ratelimit: 6 callbacks suppressed
[   13.319199] type=1505 audit(1258815155.146:12): operation="profile_replace" pid=1205 name=/usr/share/gdm/guest-session/Xsession
[   13.320540] type=1505 audit(1258815155.146:13): operation="profile_replace" pid=1206 name=/sbin/dhclient3
[   13.321086] type=1505 audit(1258815155.146:14): operation="profile_replace" pid=1206 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.321389] type=1505 audit(1258815155.146:15): operation="profile_replace" pid=1206 name=/usr/lib/connman/scripts/dhclient-script
[   13.324007] type=1505 audit(1258815155.156:16): operation="profile_replace" pid=1207 name=/usr/bin/evince
[   13.334004] type=1505 audit(1258815155.166:17): operation="profile_replace" pid=1207 name=/usr/bin/evince-previewer
[   13.339288] type=1505 audit(1258815155.166:18): operation="profile_replace" pid=1207 name=/usr/bin/evince-thumbnailer
[   13.346718] type=1505 audit(1258815155.176:19): operation="profile_replace" pid=1209 name=/usr/lib/cups/backend/cups-pdf
[   13.347356] type=1505 audit(1258815155.176:20): operation="profile_replace" pid=1209 name=/usr/sbin/cupsd
[   13.349232] type=1505 audit(1258815155.176:21): operation="profile_replace" pid=1210 name=/usr/sbin/tcpdump
[   14.332831] usplash:386 freeing invalid memtype fffffffff0000000-fffffffff1000000
[   15.209963] r8169: eth0: link down
[   15.210402] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.243751] iwl3945 0000:04:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   15.429936] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[   15.507944] Registered led device: iwl-phy0::radio
[   15.507961] Registered led device: iwl-phy0::assoc
[   15.508011] Registered led device: iwl-phy0::RX
[   15.508033] Registered led device: iwl-phy0::TX
[   15.563779] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.489350] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   17.961871]   alloc irq_desc for 31 on node 0
[   17.961874]   alloc kstat_irqs on node 0
[   17.961884] fglrx_pci 0000:01:00.0: irq 31 for MSI/MSI-X
[   17.962375] [fglrx] Firegl kernel thread PID: 1455
[   18.649288] [fglrx] Gart USWC size:942 M.
[   18.649291] [fglrx] Gart cacheable size:373 M.
[   18.649295] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   18.649298] [fglrx] Reserved FB block: Unshared offset:7d07000, size:2f5000 
[   18.649300] [fglrx] Reserved FB block: Unshared offset:7ffc000, size:4000 
[   18.689300] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.689303] Bluetooth: BNEP filters: protocol multicast
[   18.693657] Bridge firewalling registered
[   18.810437] ppdev: user-space parallel port driver
[   25.823555] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   34.595443] Intel AES-NI instructions are not detected.
[   34.633396] padlock: VIA PadLock not detected.
[   46.436770] wlan0: authenticate with AP 00:1d:68:ee:aa:75
[   46.439279] wlan0: authenticated
[   46.439282] wlan0: associate with AP 00:1d:68:ee:aa:75
[   46.442037] wlan0: RX AssocResp from 00:1d:68:ee:aa:75 (capab=0x411 status=0 aid=2)
[   46.442042] wlan0: associated
[   46.472995] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   57.382533] wlan0: no IPv6 routers present
[  601.444030] CE: hpet increasing min_delta_ns to 15000 nsec
[ 1454.009749] CE: hpet increasing min_delta_ns to 22500 nsec
[ 1663.605441] CE: hpet increasing min_delta_ns to 33750 nsec
[ 2110.770050] usb 2-2: new high speed USB device using ehci_hcd and address 5
[ 2110.931013] usb 2-2: configuration #1 chosen from 1 choice
[ 2110.932248] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2110.932345] usb-storage: device found at 5
[ 2110.932347] usb-storage: waiting for device to settle before scanning
[ 2115.920413] usb-storage: device scan complete
[ 2115.921026] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[ 2115.921889] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 2115.935354] sd 6:0:0:0: [sdc] 31355391 512-byte logical blocks: (16.0 GB/14.9 GiB)
[ 2115.937944] sd 6:0:0:0: [sdc] Write Protect is off
[ 2115.937954] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 2115.937960] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 2115.944539] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 2115.944549]  sdc: sdc1
[ 2115.947286] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 2115.947290] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 3332.186691] npviewer.bin[8138]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ffac729c error 14
[ 7762.413462] usb 2-2: USB disconnect, address 5
[13321.582196] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
[14051.040213] usb 5-1: USB disconnect, address 2
[14178.482778] usb 5-1: new low speed USB device using uhci_hcd and address 3
[14178.687694] usb 5-1: configuration #1 chosen from 1 choice
[14178.729015] input: HID 04d9:1133 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input13
[14178.729239] generic-usb 0003:04D9:1133.0002: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:1d.0-1/input0

```

** lsmod | grep snd**
```

snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_idt      72976  1 
snd_hda_intel          31880  1 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_hwdep               9352  1 snd_hda_codec
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  14 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm

```

---

### Post by &gt;:3 on 2009-11-21
Also: I forgot to mention, the headphones work for an instance *as* you plug in/ take out the jack, but gets immediately muted, along with the main sound.

---

### Post by &gt;:3 on 2010-07-24
Any News on this? Or any ideas where else I should report this? It still doesn't work under Lucid.

---

### Post by features on 2010-07-25
Hi,

Follow the instructions on this page ([https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")), particularly the bit entitled > Is ALSA using the correct model?

It's quite a busy page, and they haven't set up their section headings with anchor tags.  So just search for the text I've quoted above and you'll find it.

It'll be process of elimination to figure out which exact model will enable your headphone and mic jacks.

---

### Post by features on 2010-07-25
This page [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) may be more useful to you - it seems to mention SigmaTel cards specifically.

---

