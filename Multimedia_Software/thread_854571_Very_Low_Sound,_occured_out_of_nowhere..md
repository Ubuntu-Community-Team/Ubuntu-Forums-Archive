---
title: "Very Low Sound, occured out of nowhere."
date: 2008-07-09
forum: Multimedia Software
---

### Post by Opeth115 on 2008-07-09
Ok well i posted on the arch forums, but up to now i have no response, i hope it's ok if i post here to try to solve this.

Out of nowhere, the sound on my computer will only go to about 1/4 of the actual maximum volume, even when everything is turned up to max in alsamixer, and on my main module.  This occured out of nowhere one day, and i can't seem to find a solution to it anywhere.  Any advice?

Here's my dmesg and uname -a outputs:

dmesg :

```
[matt@Arch ~]$ dmesg
Linux version 2.6.25-ARCH (root@architect) (gcc version 4.3.1 20080626 (prerelease) (GCC) ) #1 SMP PREEMPT Thu Jul 3 20:29:23 CEST 2008
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
 BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000007de6d000 (usable)
 BIOS-e820: 000000007de6d000 - 000000007def1000 (ACPI NVS)
 BIOS-e820: 000000007def1000 - 000000007edfa000 (usable)
 BIOS-e820: 000000007edfa000 - 000000007ee07000 (reserved)
 BIOS-e820: 000000007ee07000 - 000000007eea9000 (usable)
 BIOS-e820: 000000007eea9000 - 000000007eeae000 (ACPI data)
 BIOS-e820: 000000007eeae000 - 000000007eef2000 (ACPI NVS)
 BIOS-e820: 000000007eef2000 - 000000007eef3000 (usable)
 BIOS-e820: 000000007eef3000 - 000000007eeff000 (ACPI data)
 BIOS-e820: 000000007eeff000 - 000000007ef00000 (usable)
 BIOS-e820: 000000007ef00000 - 000000007f000000 (reserved)
 BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
1135MB HIGHMEM available.
896MB LOWMEM available.
Scan SMP from c0000000 for 1024 bytes.
Scan SMP from c009fc00 for 1024 bytes.
Scan SMP from c00f0000 for 65536 bytes.
found SMP MP-table at [c00fe200] 000fe200
Entering add_active_range(0, 0, 519936) 0 entries of 256 used
Zone PFN ranges:
  DMA             0 ->     4096
  Normal       4096 ->   229376
  HighMem    229376 ->   519936
Movable zone start PFN for each node
early_node_map[1] active PFN ranges
    0:        0 ->   519936
On node 0 totalpages: 519936
  DMA zone: 32 pages used for memmap
  DMA zone: 0 pages reserved
  DMA zone: 4064 pages, LIFO batch:0
  Normal zone: 1760 pages used for memmap
  Normal zone: 223520 pages, LIFO batch:31
  HighMem zone: 2270 pages used for memmap
  HighMem zone: 288290 pages, LIFO batch:31
  Movable zone: 0 pages used for memmap
DMI 2.4 present.
ACPI: RSDP 000FE020, 0014 (r0 INTEL )
ACPI: RSDT 7EEFD038, 004C (r1 INTEL  DP965LT       697       1000013)
ACPI: FACP 7EEFC000, 0074 (r1 INTEL  DP965LT       697 MSFT  1000013)
ACPI: DSDT 7EEF7000, 40ED (r1 INTEL  DP965LT       697 MSFT  1000013)
ACPI: FACS 7EEAE000, 0040
ACPI: APIC 7EEF6000, 0078 (r1 INTEL  DP965LT       697 MSFT  1000013)
ACPI: WDDT 7EEF5000, 0040 (r1 INTEL  DP965LT       697 MSFT  1000013)
ACPI: MCFG 7EEF4000, 003C (r1 INTEL  DP965LT       697 MSFT  1000013)
ACPI: ASF! 7EEF3000, 00A6 (r32 INTEL  DP965LT       697 MSFT  1000013)
ACPI: SSDT 7EEAD000, 01BC (r1 INTEL     CpuPm      697 MSFT  1000013)
ACPI: SSDT 7EEAC000, 0175 (r1 INTEL   Cpu0Ist      697 MSFT  1000013)
ACPI: SSDT 7EEAB000, 0175 (r1 INTEL   Cpu1Ist      697 MSFT  1000013)
ACPI: SSDT 7EEAA000, 0175 (r1 INTEL   Cpu2Ist      697 MSFT  1000013)
ACPI: SSDT 7EEA9000, 0175 (r1 INTEL   Cpu3Ist      697 MSFT  1000013)
ACPI: PM-Timer IO Port: 0x408
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 6:15 APIC version 20
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Processor #1 6:15 APIC version 20
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 80000000 (gap: 7f000000:80f00000)
PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 515874
Kernel command line: root=/dev/sda1 ro
mapped APIC to ffffb000 (fee00000)
mapped IOAPIC to ffffa000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Detected 1864.857 MHz processor.
Console: colour VGA+ 80x25
console [tty0] enabled
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 2055804k/2079744k available (2083k kernel code, 21676k reserved, 711k data, 268k init, 1161320k highmem)
virtual kernel memory layout:
    fixmap  : 0xfff80000 - 0xfffff000   ( 508 kB)
    pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
    vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
    lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
      .init : 0xc03c1000 - 0xc0404000   ( 268 kB)
      .data : 0xc0308fe8 - 0xc03baea0   ( 711 kB)
      .text : 0xc0100000 - 0xc0308fe8   (2083 kB)
Checking if this processor honours the WP bit even in supervisor mode...Ok.
CPA: page pool initialized 1 of 1 pages preallocated
SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Calibrating delay using timer specific routine.. 3733.20 BogoMIPS (lpj=6219526)
Security Framework initialized
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 0
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
using mwait in idle threads.
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
ACPI: Core revision 20070126
ACPI: Checking initramfs for custom DSDT
CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
Booting processor 1/1 ip 4000
Initializing CPU#1
Calibrating delay using timer specific routine.. 3730.78 BogoMIPS (lpj=6215661)
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: Physical Processor ID: 0
CPU: Processor Core ID: 1
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
Total of 2 processors activated (7464.99 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Brought up 2 CPUs
net_namespace: 548 bytes
Booting paravirtualized kernel on bare hardware
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: BIOS Bug: MCFG area at f0000000 is not E820-reserved
PCI: Not using MMCONFIG.
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: EC: Look up EC in DSDT
ACPI: Interpreter enabled
ACPI: (supports S0 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp: PnP ACPI: found 12 devices
ACPI: ACPI bus type pnp unregistered
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
ACPI: RTC can wake from S4
system 00:01: iomem range 0xf0000000-0xf7ffffff has been reserved
system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
system 00:01: iomem range 0xc0000-0xdffff could not be reserved
system 00:01: iomem range 0xe0000-0xfffff could not be reserved
system 00:06: ioport range 0x500-0x53f has been reserved
system 00:06: ioport range 0x400-0x47f has been reserved
system 00:06: ioport range 0x680-0x6ff has been reserved
PCI: Failed to allocate mem resource #6:20000@90000000 for 0000:01:00.0
PCI: Bridge: 0000:00:01.0
  IO window: 2000-2fff
  MEM window: 0x90000000-0x92ffffff
  PREFETCH window: 0x0000000080000000-0x000000008fffffff
PCI: Bridge: 0000:00:1c.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:1c.1
  IO window: 1000-1fff
  MEM window: 0x93100000-0x931fffff
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:1c.2
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:1c.3
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:1c.4
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:1e.0
  IO window: disabled.
  MEM window: 0x93000000-0x930fffff
  PREFETCH window: disabled.
ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:01.0 to 64
ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1c.0 to 64
ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1c.1 to 64
ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1c.2 to 64
ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1c.3 to 64
ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1c.4 to 64
PCI: Setting latency timer of device 0000:00:1e.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
Unpacking initramfs... done
Freeing initrd memory: 545k freed
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: disabled - APM is not SMP safe.
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Block layer SCSI generic (bsg) driver version 0.4 loaded (major 254)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
pci 0000:01:00.0: Boot video device
PCI: Setting latency timer of device 0000:00:01.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:01.0:pcie00]
PCI: Setting latency timer of device 0000:00:1c.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:1c.0:pcie00]
Allocate Port Service[0000:00:1c.0:pcie02]
PCI: Setting latency timer of device 0000:00:1c.1 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:1c.1:pcie00]
Allocate Port Service[0000:00:1c.1:pcie02]
PCI: Setting latency timer of device 0000:00:1c.2 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:1c.2:pcie00]
Allocate Port Service[0000:00:1c.2:pcie02]
PCI: Setting latency timer of device 0000:00:1c.3 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:1c.3:pcie00]
Allocate Port Service[0000:00:1c.3:pcie02]
PCI: Setting latency timer of device 0000:00:1c.4 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:1c.4:pcie00]
Allocate Port Service[0000:00:1c.4:pcie02]
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing disabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
input: Macintosh mouse button emulation as /class/input/input0
PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
input: AT Translated Set 2 keyboard as /class/input/input1
cpuidle: using governor ladder
cpuidle: using governor menu
TCP cubic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
Using IPI No-Shortcut mode
registered taskstats version 1
Freeing unused kernel memory: 268k freed
No dock devices found.
SCSI subsystem initialized
libata version 3.00 loaded.
ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1f.2 to 64
ACPI: PCI interrupt for device 0000:00:1f.2 disabled
ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1f.5 to 64
ACPI: PCI interrupt for device 0000:00:1f.5 disabled
ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:03:00.0 to 64
ACPI: PCI interrupt for device 0000:03:00.0 disabled
ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:03:00.0 to 64
scsi0 : pata_marvell
scsi1 : pata_marvell
ata1: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 17
ata2: DUMMY
BAR5:00:00 01:7F 02:22 03:CA 04:00 05:00 06:00 07:00 08:00 09:00 0A:00 0B:00 0C:01 0D:00 0E:00 0F:00 
Switched to high resolution mode on CPU 1
Switched to high resolution mode on CPU 0
ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
ata1.01: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
ata1.00: configured for UDMA/66
ata1.01: configured for UDMA/33
scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
ata_piix 0000:00:1f.2: version 2.12
ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
PCI: Setting latency timer of device 0000:00:1f.2 to 64
scsi2 : ata_piix
scsi3 : ata_piix
ata3: SATA max UDMA/133 cmd 0x3438 ctl 0x344c bmdma 0x3410 irq 19
ata4: SATA max UDMA/133 cmd 0x3430 ctl 0x3448 bmdma 0x3418 irq 19
ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata3.00: ATA-7: WDC WD4000KS-00MNB0, 07.02E07, max UDMA/133
ata3.00: 781422768 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata3.00: configured for UDMA/133
ata4: SATA link down (SStatus 0 SControl 300)
scsi 2:0:0:0: Direct-Access     ATA      WDC WD4000KS-00M 07.0 PQ: 0 ANSI: 5
ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
PCI: Setting latency timer of device 0000:00:1f.5 to 64
scsi4 : ata_piix
scsi5 : ata_piix
ata5: SATA max UDMA/133 cmd 0x3428 ctl 0x3444 bmdma 0x30f0 irq 19
ata6: SATA max UDMA/133 cmd 0x3420 ctl 0x3440 bmdma 0x30f8 irq 19
ata5: SATA link down (SStatus 0 SControl 300)
ata6: SATA link down (SStatus 0 SControl 300)
Driver 'sr' needs updating - please use bus_type methods
sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 0:0:0:0: Attached scsi CD-ROM sr0
sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
sr 0:0:1:0: Attached scsi CD-ROM sr1
Driver 'sd' needs updating - please use bus_type methods
sd 2:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 2:0:0:0: [sda] 781422768 512-byte hardware sectors (400088 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 sda3 sda4
sd 2:0:0:0: [sda] Attached SCSI disk
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one month
Intel(R) PRO/1000 Network Driver - version 7.3.20-k2
Copyright (c) 1999-2006 Intel Corporation.
ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:1b.0 to 64
input: Power Button (FF) as /class/input/input2
ACPI: Power Button (FF) [PWRF]
input: Sleep Button (CM) as /class/input/input3
ACPI: Sleep Button (CM) [SLPB]
ACPI: ACPI0007:00 is registered as cooling_device0
ACPI: Processor [CPU0] (supports 8 throttling states)
ACPI: ACPI0007:01 is registered as cooling_device1
ACPI: Processor [CPU1] (supports 8 throttling states)
sr 0:0:0:0: Attached scsi generic sg0 type 5
sr 0:0:1:0: Attached scsi generic sg1 type 5
sd 2:0:0:0: Attached scsi generic sg2 type 0
e1000e: Intel(R) PRO/1000 Network Driver - 0.2.0
e1000e: Copyright (c) 1999-2007 Intel Corporation.
ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:19.0 to 64
Linux agpgart interface v0.103
eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:0a:4d:63
eth0: Intel(R) PRO/1000 Network Connection
eth0: MAC: 4, PHY: 6, PBA No: ffffff-0ff
nvidia: module license 'NVIDIA' taints kernel.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1a.0 to 64
uhci_hcd 0000:00:1a.0: UHCI Host Controller
uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:1a.0: irq 16, io base 0x000030a0
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1a.1[b] -> GSI 21 (level, low) -> IRQ 21
PCI: Setting latency timer of device 0000:00:1a.1 to 64
uhci_hcd 0000:00:1a.1: UHCI Host Controller
uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:1a.1: irq 21, io base 0x00003080
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
input: PC Speaker as /class/input/input4
ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1a.7 to 64
ehci_hcd 0000:00:1a.7: EHCI Host Controller
ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
ehci_hcd 0000:00:1a.7: debug port 1
PCI: cache line size of 32 is not supported by device 0000:00:1a.7
ehci_hcd 0000:00:1a.7: irq 18, io mem 0x93225400
ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 4 ports detected
lp: driver loaded but no devices found
PPP generic driver version 2.4.2
ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: EHCI Host Controller
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:1d.7: debug port 1
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: irq 23, io mem 0x93225000
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
ppdev: user-space parallel port driver
ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003060
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1f.3[b] -> GSI 21 (level, low) -> IRQ 21
ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:01:00.0 to 64
NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.09  Wed Jun  4 23:43:17 PDT 2008
ACPI: PCI Interrupt 0000:07:03.0[A] -> GSI 19 (level, low) -> IRQ 19
ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003040
usb usb6: configuration #1 chosen from 1 choice
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 2 ports detected
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[93004000-930047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
input: PS/2 Logitech Mouse as /class/input/input5
parport_pc 00:07: reported by Plug and Play ACPI
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: UHCI Host Controller
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003020
usb usb7: configuration #1 chosen from 1 choice
hub 7-0:1.0: USB hub found
hub 7-0:1.0: 2 ports detected
lp0: using parport0 (interrupt-driven).
EXT3 FS on sda1, internal journal
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Adding 1044216k swap on /dev/sda4.  Priority:-1 extents:1 across:1044216k
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270001d98f6c]
eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
eth0: 10/100 speed: disabling TSO
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
eth0: no IPv6 routers present
ACPI: PCI interrupt for device 0000:00:1b.0 disabled
ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:1b.0 to 64
```

uname -a :

```
[matt@Arch ~]$ uname -a
Linux Arch 2.6.25-ARCH #1 SMP PREEMPT Thu Jul 3 20:29:23 CEST 2008 i686 Intel(R) Core(TM)2 CPU 6300 @ 1.86GHz GenuineIntel GNU/Linux
```

hwdetect --show-modules

```
[matt@Arch ~]$ hwdetect --show-modules
AGP    : agpgart intel-agp 
ACPI   : button dock processor thermal 
PATA   : pata_acpi pata_marvell ata_generic 
SCSI   : scsi_mod sd_mod sr_mod 
SATA   : ata_piix 
USB    : usbcore ehci-hcd uhci-hcd 
FW     : firewire-core firewire-ohci firewire-core firewire-ohci ieee1394 ohci1394 
NET    : e1000e ppp_generic slhc 
INPUT  : evdev pcspkr psmouse serio_raw 
SOUND  : snd-mixer-oss snd-pcm-oss snd-hwdep snd-page-alloc snd-pcm snd-timer snd snd-hda-intel soundcore 
VIDEO  : nvidia 
OTHER  : cdrom lp ppdev i2c-i801 i2c-core parport parport_pc pci_hotplug shpchp rtc-cmos rtc-core rtc-lib crc-itu-t
```

---

### Post by mgmiller on 2008-07-09
Sometimes problems like this are purely hardware related.  Have you tried removing the mini jacks from the back of your computer sound output area and cleaning them?  Sometimes just unplugging and replugging them back in a few times will clean off a little corrosion and make them work normally again.  Same thing if you have mini jacks and plugs at the speakers.  I live on an island surrounded by salt water and this is a fairly common problem for me for lots of electrical things.  I often use special corrosion inhibitor sprays to fix electronic things that start to act up.

The other thing that just occurred to me is the volume control on your speakers them selves.  If that's turned down, you will get the same effect.  My wife has done this to me on more than one occasion.

---

### Post by Opeth115 on 2008-07-10
I tried cleaning the jacks and that didn't help, iw isdh i twould be that simple =(.  All the volume controls are turned all the way up and i get maybe 1/3 of the volume level i should be getting.

---

### Post by mgmiller on 2008-07-10
I know you said you tried alsamixer.  Are you sure both the master and PCM volumes are turned up?

I see you are using OSS sound.  In Ubuntu, I can switch between ALSA, OSS, ESD and Pulse.  Each behaves a little differently.  Have you tried trying a different sound daemon?

Unfortunately I don't know how to tell you how to do that in arch.

Is there a live CD for arch?  If there is, try booting off it and see if your sound returns to normal.

Another thing you can try is going into your BIOS and disabling the on board sound card, letting it cycle through 1 boot sequence that way.  Then shut it off.  Then reboot and re enable the sound and see if it resets something in hardware on the mobo.

---

### Post by erikthedrink on 2009-09-08
Also, click on the Audio icon to bring up the mixer and select controls. Choose Auto Gain and then return to the mixer.  Select the Switches tab and make sure the Auto Gain box is checked.  Otherwise, your speakers were overstressed, or someone got liquid on them.:lolflag:

---

### Post by moshuptrail on 2009-10-11
I've got the same problem on a Dell Inspiron 1525.  I'm pretty sure there was change in one of the upgrades along the way between Gutsy and Hardy.   had this problem once before on another PC, also between Gutsy and Hardy, and there was fix posted.  Now I can't find it.

mgmiller - please take the OP seriously.  He's obviously done some troubleshooting.

---

### Post by mgmiller on 2009-10-11
> mgmiller - please take the OP seriously.  He's obviously done some troubleshooting.

I assure you I am taking him seriously.  I don't respond to posts unless I genuinely believe I can be of some help.  

Everything I suggested in the 2 answers I gave are things that I have personally experienced on pc's I have worked on.

Since we have not heard from the OP in almost a year and a half, I would like to think something I said here helped him.

---

### Post by fishbulb1022 on 2009-12-14
this'll probably sound stupid here, but my brother had a similar problem. He dual boots with windows and it took him a few months to figure it out, but if he had the volume muted when he shut down windows, it would be really low in ubuntu. If you dual boot, this might be worth a shot. Good luck.

---

