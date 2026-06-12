---
title: "Having problems setting up awus036NH, installed firmware + drivers. ( small prob )"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by SmileyTop on 2010-05-06
I am ttrying to get my wireless awus036NH running with the rt2800usb drivers, so far ive installed the firmware + drivers this is what ive got when i run airmon-ng
[PHP]
Interface       Chipset         Driver

wlan0           Unknown         rt2800usb - [phy1][/PHP]

this i thought was odd as its got the [phy1] next to the driver + its not its wlan0.




here is my Demsg
[PHP]Linux version 2.6.30.9 (root@dev) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Tue Dec 1 21:51:08 EST 2009
KERNEL supported cpus:
  Intel GenuineIntel
  AMD AuthenticAMD
  NSC Geode by NSC
  Cyrix CyrixInstead
  Centaur CentaurHauls
  Transmeta GenuineTMx86
  Transmeta TransmetaCPU
  UMC UMC UMC UMC
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
 BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
 BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
 BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
 BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
DMI 2.3 present.
AMI BIOS detected: BIOS may corrupt low RAM, working around it.
e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
last_pfn = 0x7ffb0 max_arch_pfn = 0x100000
MTRR default type: uncachable
MTRR fixed ranges enabled:
  00000-9FFFF write-back
  A0000-EFFFF uncachable
  F0000-FFFFF write-protect
MTRR variable ranges enabled:
  0 base 0000000000 mask FF80000000 write-back
  1 disabled
  2 disabled
  3 disabled
  4 disabled
  5 disabled
  6 disabled
  7 disabled
x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
init_memory_mapping: 0000000000000000-00000000377fe000
 0000000000 - 0000400000 page 4k
 0000400000 - 0037400000 page 2M
 0037400000 - 00377fe000 page 4k
kernel direct mapping tables up to 377fe000 @ 10000-15000
RAMDISK: 37afd000 - 37fef240
Allocated new RAMDISK: 009e9000 - 00edb240
Move RAMDISK from 0000000037afd000 - 0000000037fef23f to 009e9000 - 00edb23f
ACPI: RSDP 000f6840 00014 (v00 ACPIAM)
ACPI: RSDT 7ffb0000 00030 (v01 A M I  OEMRSDT  07000610 MSFT 00000097)
ACPI: FACP 7ffb0200 00084 (v02 A M I  OEMFACP  07000610 MSFT 00000097)
ACPI: DSDT 7ffb03f0 037DF (v01  K8UVM K8UVM000 00000000 INTL 02002026)
ACPI: FACS 7ffc0000 00040
ACPI: APIC 7ffb0390 0005C (v01 A M I  OEMAPIC  07000610 MSFT 00000097)
ACPI: OEMB 7ffc0040 00046 (v01 A M I  AMI_OEM  07000610 MSFT 00000097)
ACPI: Local APIC address 0xfee00000
1159MB HIGHMEM available.
887MB LOWMEM available.
  mapped low ram: 0 - 377fe000
  low ram: 0 - 377fe000
  node 0 low ram: 00000000 - 377fe000
  node 0 bootmap 00011000 - 00017f00
(9 early reservations) ==> bootmem [0000000000 - 00377fe000]
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
  #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
  #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
  #3 [0000100000 - 00009e4374]    TEXT DATA BSS ==> [0000100000 - 00009e4374]
  #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
  #5 [00009e5000 - 00009e80a9]              BRK ==> [00009e5000 - 00009e80a9]
  #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
  #7 [00009e9000 - 0000edb240]      NEW RAMDISK ==> [00009e9000 - 0000edb240]
  #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
found SMP MP-table at [c00ff780] ff780
Zone PFN ranges:
  DMA      0x00000010 -> 0x00001000
  Normal   0x00001000 -> 0x000377fe
  HighMem  0x000377fe -> 0x0007ffb0
Movable zone start PFN for each node
early_node_map[2] active PFN ranges
    0: 0x00000010 -> 0x0000009f
    0: 0x00000100 -> 0x0007ffb0
On node 0 totalpages: 524095
free_area_init_node: node 0, pgdat c08e7b40, node_mem_map c1000200
  DMA zone: 32 pages used for memmap
  DMA zone: 0 pages reserved
  DMA zone: 3951 pages, LIFO batch:0
  Normal zone: 1744 pages used for memmap
  Normal zone: 221486 pages, LIFO batch:31
  HighMem zone: 2320 pages used for memmap
  HighMem zone: 294562 pages, LIFO batch:31
Using APIC driver default
Detected use of extended apic ids on hypertransport bus
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
SMP: Allowing 2 CPUs, 1 hotplug CPUs
nr_irqs_gsi: 24
PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Allocating PCI resources starting at 88000000 (gap: 80000000:7f780000)
NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
PERCPU: Embedded 11 pages at c200a000, static data 23068 bytes
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519999
Kernel command line: root=UUID=8e5f9526-b360-4fc2-b9b4-c886e7edd731 ro quiet splash
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
NR_IRQS:512
PID hash table entries: 4096 (order: 12, 16384 bytes)
Fast TSC calibration using PIT
Detected 2004.545 MHz processor.
Console: colour VGA+ 80x25
console [tty0] enabled
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Initializing HighMem for node 0 (000377fe:0007ffb0)
Memory: 2063912k/2096832k available (6103k kernel code, 31588k reserved, 2103k data, 432k init, 1187528k highmem)
virtual kernel memory layout:
    fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
    pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
    vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
    lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
      .init : 0xc090d000 - 0xc0979000   ( 432 kB)
      .data : 0xc06f5dad - 0xc0903a44   (2103 kB)
      .text : 0xc0100000 - 0xc06f5dad   (6103 kB)
Checking if this processor honours the WP bit even in supervisor mode...Ok.
SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Calibrating delay loop (skipped), value calculated using timer frequency.. 4010.13 BogoMIPS (lpj=6681816)
Security Framework initialized
Mount-cache hash table entries: 512
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 128K (64 bytes/line)
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
ACPI: Core revision 20090320
..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
CPU0: AMD Sempron(tm) Processor 3300+ stepping 02
Brought up 1 CPUs
Total of 1 processors activated (4010.13 BogoMIPS).
net_namespace: 980 bytes
xor: automatically using best checksumming function: pIII_sse
   pIII_sse  :  5956.800 MB/sec
xor: using function: pIII_sse (5956.800 MB/sec)
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
PCI: Using configuration type 1 for base access
bio: create slab <bio-0> at 0
ACPI: EC: Look up EC in DSDT
ACPI: Interpreter enabled
ACPI: (supports S0 S1 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI Warning (tbutils-0246): Incorrect checksum in table [OEMB] - 98, should be 8A [20090320]
ACPI: No dock devices found.
ACPI: PCI Root Bridge [PCI0] (0000:00)
pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
pci 0000:00:01.0: supports D1
pci 0000:00:0a.0: reg 10 io port: [0xbc00-0xbc1f]
pci 0000:00:0a.0: supports D1 D2
pci 0000:00:0a.1: reg 10 io port: [0xec00-0xec07]
pci 0000:00:0a.1: supports D1 D2
pci 0000:00:0f.0: reg 10 io port: [0xe800-0xe807]
pci 0000:00:0f.0: reg 14 io port: [0xe400-0xe403]
pci 0000:00:0f.0: reg 18 io port: [0xe000-0xe007]
pci 0000:00:0f.0: reg 1c io port: [0xdc00-0xdc03]
pci 0000:00:0f.0: reg 20 io port: [0xd800-0xd80f]
pci 0000:00:0f.0: reg 24 io port: [0xd400-0xd4ff]
pci 0000:00:0f.1: reg 20 io port: [0xfc00-0xfc0f]
pci 0000:00:10.0: reg 20 io port: [0xc000-0xc01f]
pci 0000:00:10.0: supports D1 D2
pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:10.0: PME# disabled
pci 0000:00:10.1: reg 20 io port: [0xc400-0xc41f]
pci 0000:00:10.1: supports D1 D2
pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:10.1: PME# disabled
pci 0000:00:10.2: reg 20 io port: [0xc800-0xc81f]
pci 0000:00:10.2: supports D1 D2
pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:10.2: PME# disabled
pci 0000:00:10.3: reg 20 io port: [0xcc00-0xcc1f]
pci 0000:00:10.3: supports D1 D2
pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:10.3: PME# disabled
pci 0000:00:10.4: reg 10 32bit mmio: [0xf7fff800-0xf7fff8ff]
pci 0000:00:10.4: supports D1 D2
pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:10.4: PME# disabled
HPET not enabled in BIOS. You might try hpet=force boot option
pci 0000:00:12.0: reg 10 io port: [0xd000-0xd0ff]
pci 0000:00:12.0: reg 14 32bit mmio: [0xf7fffc00-0xf7fffcff]
pci 0000:00:12.0: supports D1 D2
pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
pci 0000:00:12.0: PME# disabled
pci 0000:01:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xefffffff]
pci 0000:01:00.0: reg 18 32bit mmio: [0xf5000000-0xf5ffffff]
pci 0000:01:00.0: reg 30 32bit mmio: [0xf7ee0000-0xf7efffff]
pci 0000:00:01.0: bridge 32bit mmio: [0xf3e00000-0xf7efffff]
pci 0000:00:01.0: bridge 32bit mmio pref: [0xd3d00000-0xf3cfffff]
pci_bus 0000:00: on NUMA node 0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
SCSI subsystem initialized
libata version 3.00 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
raid6: int32x1    944 MB/s
raid6: int32x2    837 MB/s
raid6: int32x4    698 MB/s
raid6: int32x8    550 MB/s
raid6: mmxx1     1632 MB/s
raid6: mmxx2     2995 MB/s
raid6: sse1x1    1488 MB/s
raid6: sse1x2    2582 MB/s
raid6: sse2x1    2548 MB/s
raid6: sse2x2    3255 MB/s
raid6: using algorithm sse2x2 (3255 MB/s)
PCI: Using ACPI for IRQ routing
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp: PnP ACPI: found 14 devices
ACPI: ACPI bus type pnp unregistered
system 00:08: ioport range 0x295-0x296 has been reserved
system 00:08: ioport range 0x3e0-0x3e7 has been reserved
system 00:08: ioport range 0x4d0-0x4d1 has been reserved
system 00:08: ioport range 0x800-0x87f has been reserved
system 00:08: ioport range 0x400-0x41f has been reserved
system 00:08: iomem range 0xfff80000-0xffffffff has been reserved
system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
system 00:0d: iomem range 0x0-0x9ffff could not be reserved
system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
pci 0000:00:01.0:   IO window: disabled
pci 0000:00:01.0:   MEM window: 0xf3e00000-0xf7efffff
pci 0000:00:01.0:   PREFETCH window: 0x000000d3d00000-0x000000f3cfffff
pci 0000:00:01.0: setting latency timer to 64
pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
pci_bus 0000:01: resource 1 mem: [0xf3e00000-0xf7efffff]
pci_bus 0000:01: resource 2 pref mem [0xd3d00000-0xf3cfffff]
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Switched to high resolution mode on CPU 0
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
NET: Registered protocol family 1
Trying to unpack rootfs image as initramfs...
Freeing initrd memory: 5064k freed
apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
apm: overridden by ACPI.
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.2
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
NTFS driver 2.1.29 [Flags: R/O].
msgmni has been set to 1723
alg: No test for stdrng (krng)
async_tx: api initialized (sync-only)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
pci 0000:00:01.0: disabling DAC on VIA PCI bridge
pci 0000:01:00.0: Boot video device
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
input: Power Button as /class/input/input0
ACPI: Power Button [PWRF]
input: Power Button as /class/input/input1
ACPI: Power Button [PWRB]
processor ACPI_CPU:00: registered as cooling_device0
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
brd: module loaded
loop: module loaded
Compaq SMART2 Driver (v 2.6.0)
HP CISS Driver (v 3.6.20)
input: Macintosh mouse button emulation as /class/input/input2
Uniform Multi-Platform E-IDE driver
via82cxxx 0000:00:0f.1: VIA vt8237 (rev 00) IDE UDMA133
via82cxxx 0000:00:0f.1: IDE controller (0x1106:0x0571 rev 0x06)
pci 0000:00:0f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
via82cxxx 0000:00:0f.1: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xfc00-0xfc07
    ide1: BM-DMA at 0xfc08-0xfc0f
Probing IDE interface ide0...
hda: FUJITSU MPE3273AT, ATA DISK drive
hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
hda: drive side 80-wire cable detection failed, limiting max speed to UDMA33
hda: UDMA/33 mode selected
Probing IDE interface ide1...
hdc: LITE-ON COMBO LTC-48161H, ATAPI CD/DVD-ROM drive
hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO4
hdc: UDMA/33 mode selected
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ide1 at 0x170-0x177,0x376 on irq 15
ide_generic: please use "probe_mask=0x3f" module parameter for probing all legacy ISA IDE ports
ide-gd driver 1.18
hda: max request size: 128KiB
hda: 53377152 sectors (27329 MB) w/2048KiB Cache, CHS=52953/16/63
hda: cache flushes not supported
 hda: hda1 hda2 < hda5 >
ide-cd driver 5.00
ide-cd: hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
Loading iSCSI transport class v2.0-870.
iscsi: registered transport (tcp)
Loading Adaptec I2O RAID: Version 2.4 Build 5go
Detecting Adaptec I2O RAID controllers...
Adaptec aacraid driver 1.1-5[2461]-ms
aic94xx: Adaptec aic94xx SAS/SATA driver version 1.0.3 loaded
scsi: <fdomain> Detection failed (no card)
sym53c416.c: Version 1.0.0-ac
qlogicfas: no cards were found, please specify I/O address and IRQ using iobase= and irq= options<6>QLogic Fibre Channel HBA Driver: 8.03.01-k1
iscsi: registered transport (qla4xxx)
QLogic iSCSI HBA Driver
Emulex LightPulse Fibre Channel SCSI driver 8.3.1
Copyright(c) 2004-2009 Emulex.  All rights reserved.
Failed initialization of WD-7000 SCSI card!
DC390: clustering now enabled by default. If you get problems load
       with "disable_clustering=1" and report to maintainers
megaraid cmm: 2.20.2.7 (Release Date: Sun Jul 16 00:01:03 EST 2006)
megaraid: 2.20.5.1 (Release Date: Thu Nov 16 15:32:35 EST 2006)
megasas: 00.00.04.01 Thu July 24 11:41:51 PST 2008
GDT-HA: Storage RAID Controller Driver. Version: 3.05
3ware Storage Controller device driver for Linux v1.26.02.002.
3ware 9000 Storage Controller device driver for Linux v2.26.02.012.
nsp32: loading...
ipr: IBM Power RAID SCSI Device Driver version: 2.4.2 (January 21, 2009)
RocketRAID 3xxx/4xxx Controller driver v1.3 (071203)
st: Version 20081215, fixed bufsize 32768, s/g segs 256
Driver 'st' needs updating - please use bus_type methods
Driver 'sd' needs updating - please use bus_type methods
Driver 'sr' needs updating - please use bus_type methods
sata_via 0000:00:0f.0: version 2.4
sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
sata_via 0000:00:0f.0: routed to hard irq line 11
scsi2 : sata_via
scsi3 : sata_via
ata1: SATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 20
ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 20
Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
Copyright (c) 1999-2006 Intel Corporation.
Atheros(R) L2 Ethernet Driver - version 2.2.3
Copyright (c) 2007 Atheros Corporation.
jme: JMicron JMC2XX ethernet driver version 1.0.4
pcnet32.c:v1.35 21.Apr.2008 tsbogend@alpha.franken.de
e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
e100: Copyright(c) 1999-2006 Intel Corporation
I2O subsystem v1.325
i2o: max drivers = 8
I2O Configuration OSM v1.323
I2O Bus Adapter OSM v1.317
I2O Block Device OSM v1.325
I2O SCSI Peripheral OSM v1.316
I2O ProcFS OSM v1.316
Fusion MPT base driver 3.04.07
Copyright (c) 1999-2008 LSI Corporation
Fusion MPT SPI Host driver 3.04.07
Fusion MPT FC Host driver 3.04.07
Fusion MPT SAS Host driver 3.04.07
ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
ehci_hcd 0000:00:10.4: PCI INT C -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: EHCI Host Controller
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:10.4: irq 21, io mem 0xf7fff800
ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 8 ports detected
116x: driver isp116x-hcd, 03 Nov 2005
ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
uhci_hcd: USB Universal Host Controller Interface driver
uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: UHCI Host Controller
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c000
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
uhci_hcd 0000:00:10.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: UHCI Host Controller
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:10.1: irq 21, io base 0x0000c400
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
uhci_hcd 0000:00:10.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: UHCI Host Controller
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c800
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
uhci_hcd 0000:00:10.3: PCI INT B -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: UHCI Host Controller
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
uhci_hcd 0000:00:10.3: irq 21, io base 0x0000cc00
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
sl811: driver sl811-hcd, 19 May 2005
Initializing USB Mass Storage driver...
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
usbcore: registered new interface driver ums-alauda
usbcore: registered new interface driver ums-datafab
usbcore: registered new interface driver ums-freecom
usbcore: registered new interface driver ums-isd200
usbcore: registered new interface driver ums-jumpshot
usbcore: registered new interface driver ums-karma
usbcore: registered new interface driver ums-sddr09
usbcore: registered new interface driver ums-sddr55
usbcore: registered new interface driver ums-usbat
PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
md: linear personality registered for level -1
md: raid0 personality registered for level 0
md: raid1 personality registered for level 1
md: raid10 personality registered for level 10
md: raid6 personality registered for level 6
md: raid5 personality registered for level 5
md: raid4 personality registered for level 4
md: multipath personality registered for level -4
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
cpuidle: using governor ladder
cpuidle: using governor menu
usbcore: registered new interface driver hiddev
usbcore: registered new interface driver usbhid
usbhid: v2.6:USB HID core driver
TCP cubic registered
Initializing XFRM netlink socket
NET: Registered protocol family 17
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
Using IPI No-Shortcut mode
input: AT Translated Set 2 keyboard as /class/input/input3
ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
usb 1-7: new high speed USB device using ehci_hcd and address 2
ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
Freeing unused kernel memory: 432k freed
usb 1-7: configuration #1 chosen from 1 choice
fuse init (API version 7.11)
via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
eth0: VIA Rhine II at 0xf7fffc00, 00:13:8f:27:bf:9b, IRQ 23.
eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
PM: Starting manual resume from disk
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: hda1: orphan cleanup on readonly fs
ext3_orphan_cleanup: deleting unreferenced inode 27294
EXT3-fs: hda1: 1 orphan inode deleted
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with writeback data mode.
udevd version 124 started
Linux agpgart interface v0.103
agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204]
agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
gameport: EMU10K1 is pci0000:00:0a.1/gameport0, io 0xec00, speed 1065kHz
parport_pc 00:06: reported by Plug and Play ACPI
parport0: PC-style at 0x378 (0x778), irq 7 [PCSPP,TRISTATE,EPP]
rtc_cmos 00:02: RTC can wake from S4
rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
rtc0: alarms up to one year, y3k, 114 bytes nvram
gameport: NS558 PnP Gameport is pnp00:07/gameport0, io 0x200, speed 795kHz
EMU10K1_Audigy 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
lp0: using parport0 (interrupt-driven).
lp0: console ready
input: ImExPS/2 Generic Explorer Mouse as /class/input/input4
Adding 1148608k swap on /dev/hda5.  Priority:-1 extents:1 across:1148608k
EXT3 FS on hda1, internal journal
ip_tables: (C) 2000-2006 Netfilter Core Team
powernow-k8: Found 1 AMD Sempron(tm) Processor 3300+ processors (1 cpu cores) (version 2.20.00)
[Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
eth0: no IPv6 routers present
usb 1-7: USB disconnect, address 2
usb 1-7: new high speed USB device using ehci_hcd and address 3
usb 1-7: configuration #1 chosen from 1 choice
cfg80211: Using static regulatory domain info
cfg80211: Regulatory domain: US
        (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
        (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
        (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
cfg80211: Calling CRDA for country: US
cfg80211: Regulatory domain changed to country: US
        (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
        (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
        (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
        (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
        (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
        (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
phy0: Selected rate control algorithm 'minstrel'
Registered led device: rt2800usb-phy0::radio
Registered led device: rt2800usb-phy0::assoc
Registered led device: rt2800usb-phy0::quality
usbcore: registered new interface driver rt2800usb
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
phy0 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
eth0: no IPv6 routers present
usbcore: deregistering interface driver rt2800usb
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xdd5b4063
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xdd5b4063
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xdd5b4063
cfg80211: Using static regulatory domain info
cfg80211: Regulatory domain: US
        (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
        (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
        (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
cfg80211: Calling CRDA for country: US
cfg80211: Regulatory domain changed to country: US
        (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
        (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
        (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
        (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
        (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
        (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
phy0: Selected rate control algorithm 'minstrel'
Registered led device: rt2800usb-phy0::radio
Registered led device: rt2800usb-phy0::assoc
Registered led device: rt2800usb-phy0::quality
usbcore: registered new interface driver rt2800usb
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
ADDRCONF(NETDEV_UP): wlan0: link is not ready
usb 1-7: USB disconnect, address 3
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0208 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1204 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157dbc
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1400 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1400 with error -19.
usb 1-7: new high speed USB device using ehci_hcd and address 4
usb 1-7: configuration #1 chosen from 1 choice
phy1: Selected rate control algorithm 'minstrel'
Registered led device: rt2800usb-phy1::radio
Registered led device: rt2800usb-phy1::assoc
Registered led device: rt2800usb-phy1::quality
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
device wlan0 entered promiscuous mode
usb 1-7: USB disconnect, address 4
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0208 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1204 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157dbc
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy1 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
device wlan0 left promiscuous mode
__dev_addr_discard: address leakage! da_users=1
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1400 with error -19.
phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1400 with error -19.
usb 1-7: new high speed USB device using ehci_hcd and address 5
usb 1-7: configuration #1 chosen from 1 choice
phy2: Selected rate control algorithm 'minstrel'
Registered led device: rt2800usb-phy2::radio
Registered led device: rt2800usb-phy2::assoc
Registered led device: rt2800usb-phy2::quality
usbcore: deregistering interface driver rt2800usb
phy2 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xdd5b40e3
phy2 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xdd5b40e3
phy2 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xdd5b40e3
cfg80211: Using static regulatory domain info
cfg80211: Regulatory domain: US
        (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
        (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
        (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
        (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
cfg80211: Calling CRDA for country: US
cfg80211: Regulatory domain changed to country: US
        (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
        (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
        (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
        (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
        (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
        (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
phy0: Selected rate control algorithm 'minstrel'
Registered led device: rt2800usb-phy0::radio
Registered led device: rt2800usb-phy0::assoc
Registered led device: rt2800usb-phy0::quality
usbcore: registered new interface driver rt2800usb
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
ADDRCONF(NETDEV_UP): wlan0: link is not ready
usb 1-7: USB disconnect, address 5
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0208 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1004 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1204 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1328 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0208 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157dbc
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xf7157db8
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1400 with error -19.
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x1400 with error -19.
usb 1-7: new high speed USB device using ehci_hcd and address 6
usb 1-7: configuration #1 chosen from 1 choice
phy1: Selected rate control algorithm 'minstrel'
Registered led device: rt2800usb-phy1::radio
Registered led device: rt2800usb-phy1::assoc
Registered led device: rt2800usb-phy1::quality
rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
device wlan0 entered promiscuous mode
device mon2 entered promiscuous mode
device wlan0 left promiscuous mode
device wlan0 entered promiscuous mode
device mon5 entered promiscuous mode[/PHP]

any help would be appriciated , thanks.

---

