---
title: "UVC Driver Error"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by amneziac on 2007-10-21
I was following the guide to i install the UVC driver for my quickcam fusion ([http://ubuntuforums.org/showthread.php?t=194793](http://ubuntuforums.org/showthread.php?t=194793)). I am using gutsy right now and the error I get when i am finished and type "dmesg" is this:
```
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32227 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6D90 checksum 0
[    0.000000] ACPI: RSDP 000F6D90, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 3FEE3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEE30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 3FEE3180, 7EE3 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 3FEE0000, 0040
[    0.000000] ACPI: MCFG 3FEEB180, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEEB0C0, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] Built 1 zonelists.  Total pages: 259811
[    0.000000] Kernel command line: root=UUID=a6bbca1f-c2b9-4372-af99-6bd4d1b1290c ro quiet splash noapic
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2010.313 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 1026688k/1047424k available (2015k kernel code, 20020k reserved, 916k data, 364k init, 129920k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.084000] Calibrating delay using timer specific routine.. 4023.19 BogoMIPS (lpj=8046387)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.388000] ACPI: Core revision 20070126
[    0.388000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.392000] ACPI: setting ELCR to 0200 (from 0828)
[    0.392000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ stepping 02
[    0.392000] SMP alternatives: switching to SMP code
[    0.392000] Booting processor 1/1 eip 3000
[    0.400000] Initializing CPU#1
[    0.484000] Calibrating delay using timer specific routine.. 4020.92 BogoMIPS (lpj=8041854)
[    0.484000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.484000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.484000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.484000] CPU 1(2) -> Core 1
[    0.484000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.484000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ stepping 02
[    0.484000] Total of 2 processors activated (8044.12 BogoMIPS).
[    0.484000] Brought up 2 CPUs
[    0.520000] migration_cost=0
[    0.520000] Booting paravirtualized kernel on bare hardware
[    0.520000] Time: 17:20:35  Date: 09/21/107
[    0.520000] NET: Registered protocol family 16
[    0.520000] EISA bus registered
[    0.520000] ACPI: bus type pci registered
[    0.524000] PCI: PCI BIOS revision 3.00 entry at 0xf1fa0, last bus=5
[    0.524000] PCI: Using configuration type 1
[    0.524000] Setting up standard PCI resources
[    0.528000] ACPI: EC: Look up EC in DSDT
[    0.536000] ACPI: Interpreter enabled
[    0.536000] ACPI: (supports S0 S1 S3 S4 S5)
[    0.536000] ACPI: Using PIC for interrupt routing
[    0.544000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.544000] PCI: Probing PCI hardware (bus 00)
[    0.544000] PCI: Transparent bridge - 0000:00:09.0
[    0.544000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.548000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.616000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LMAC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.616000] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.616000] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.620000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.620000] pnp: PnP ACPI init
[    0.620000] ACPI: bus type pnp registered
[    0.628000] pnp: PnP ACPI: found 13 devices
[    0.628000] ACPI: ACPI bus type pnp unregistered
[    0.628000] PnPBIOS: Disabled by ACPI PNP
[    0.628000] PCI: Using ACPI for IRQ routing
[    0.628000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.688000] NET: Registered protocol family 8
[    0.688000] NET: Registered protocol family 20
[    0.688000] pnp: 00:01: ioport range 0x4000-0x407f has been reserved
[    0.688000] pnp: 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.688000] pnp: 00:01: ioport range 0x4400-0x447f has been reserved
[    0.688000] pnp: 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.688000] pnp: 00:01: ioport range 0x4800-0x487f has been reserved
[    0.688000] pnp: 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.688000] pnp: 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.688000] pnp: 00:0c: iomem range 0xcca00-0xcffff has been reserved
[    0.688000] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.688000] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.688000] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.716000] PCI: Bridge: 0000:00:09.0
[    0.716000]   IO window: a000-afff
[    0.716000]   MEM window: fdf00000-fdffffff
[    0.716000]   PREFETCH window: disabled.
[    0.716000] PCI: Bridge: 0000:00:0b.0
[    0.716000]   IO window: disabled.
[    0.716000]   MEM window: disabled.
[    0.716000]   PREFETCH window: disabled.
[    0.716000] PCI: Bridge: 0000:00:0c.0
[    0.716000]   IO window: disabled.
[    0.716000]   MEM window: disabled.
[    0.716000]   PREFETCH window: disabled.
[    0.716000] PCI: Bridge: 0000:00:0d.0
[    0.716000]   IO window: disabled.
[    0.716000]   MEM window: disabled.
[    0.716000]   PREFETCH window: disabled.
[    0.716000] PCI: Bridge: 0000:00:0e.0
[    0.716000]   IO window: 9000-9fff
[    0.716000]   MEM window: f8000000-fbffffff
[    0.716000]   PREFETCH window: d0000000-dfffffff
[    0.716000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    0.716000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.716000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.716000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    0.716000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.716000] NET: Registered protocol family 2
[    0.720000] Time: acpi_pm clocksource has been installed.
[    0.720000] Switched to high resolution mode on CPU 0
[    0.720000] Switched to high resolution mode on CPU 1
[    0.760000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.760000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.760000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.760000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.760000] TCP reno registered
[    0.776000] checking if image is initramfs... it is
[    1.344000] Freeing initrd memory: 7115k freed
[    1.344000] audit: initializing netlink socket (disabled)
[    1.344000] audit(1192987236.220:1): initialized
[    1.344000] highmem bounce pool size: 64 pages
[    1.344000] VFS: Disk quotas dquot_6.5.1
[    1.344000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.344000] io scheduler noop registered
[    1.344000] io scheduler anticipatory registered
[    1.344000] io scheduler deadline registered
[    1.344000] io scheduler cfq registered (default)
[    1.364000] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[    1.364000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    1.364000] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[    1.364000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    1.364000] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[    1.364000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    1.364000] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[    1.364000] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[    1.364000] Boot video device is 0000:05:00.0
[    1.364000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    1.364000] assign_interrupt_mode Found MSI capability
[    1.364000] Allocate Port Service[0000:00:0b.0:pcie00]
[    1.364000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.364000] assign_interrupt_mode Found MSI capability
[    1.364000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.364000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    1.364000] assign_interrupt_mode Found MSI capability
[    1.364000] Allocate Port Service[0000:00:0d.0:pcie00]
[    1.364000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    1.364000] assign_interrupt_mode Found MSI capability
[    1.364000] Allocate Port Service[0000:00:0e.0:pcie00]
[    1.364000] isapnp: Scanning for PnP cards...
[    1.716000] isapnp: No Plug & Play device found
[    1.740000] Real Time Clock Driver v1.12ac
[    1.740000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.740000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.740000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.740000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.740000] input: Macintosh mouse button emulation as /class/input/input0
[    1.740000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.744000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.744000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.744000] mice: PS/2 mouse device common for all mice
[    1.744000] EISA: Probing bus 0 at eisa.0
[    1.744000] Cannot allocate resource for EISA slot 4
[    1.744000] EISA: Detected 0 cards.
[    1.744000] TCP cubic registered
[    1.744000] NET: Registered protocol family 1
[    1.744000] Using IPI No-Shortcut mode
[    1.744000]   Magic number: 11:676:340
[    1.744000]   hash matches device ttyzf
[    1.744000] Freeing unused kernel memory: 364k freed
[    1.772000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.968000] AppArmor: AppArmor initialized<5>audit(1192987237.720:2):  type=1505 info="AppArmor initialized" pid=1258
[    2.976000] fuse init (API version 7.8)
[    2.980000] Failure registering capabilities with primary security module.
[    3.016000] ACPI: Fan [FAN] (on)
[    3.020000] ACPI: Thermal Zone [THRM] (40 C)
[    3.572000] SCSI subsystem initialized
[    3.576000] libata version 2.21 loaded.
[    3.580000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.580000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    3.580000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[    3.580000] NFORCE-CK804: chipset revision 242
[    3.580000] NFORCE-CK804: not 100% native mode: will probe irqs later
[    3.580000] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[    3.580000]     ide0: BM-DMA at 0xe800-0xe807, BIOS settings: hda:DMA, hdb:DMA
[    3.580000]     ide1: BM-DMA at 0xe808-0xe80f, BIOS settings: hdc:DMA, hdd:DMA
[    3.580000] Probing IDE interface ide0...
[    3.612000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    3.664000] usbcore: registered new interface driver usbfs
[    3.664000] usbcore: registered new interface driver hub
[    3.664000] usbcore: registered new device driver usb
[    3.712000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.880000] hda: WDC WD2000JB-00GVC0, ATA DISK drive
[    4.552000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.572000] Probing IDE interface ide1...
[    5.308000] hdc: TOSHIBA ODD-DVD SD-R5272, ATAPI CD/DVD-ROM drive
[    5.980000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.992000] ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 11
[    5.992000] PCI: setting IRQ 11 as level-triggered
[    5.992000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUBA] -> GSI 11 (level, low) -> IRQ 11
[    5.992000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    5.992000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    5.992000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    5.992000] ohci_hcd 0000:00:02.0: irq 11, io mem 0xfe02f000
[    6.048000] usb usb1: configuration #1 chosen from 1 choice
[    6.048000] hub 1-0:1.0: USB hub found
[    6.048000] hub 1-0:1.0: 10 ports detected
[    6.152000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    6.152000] PCI: setting IRQ 10 as level-triggered
[    6.152000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[    6.204000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.212000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 3
[    6.212000] PCI: setting IRQ 3 as level-triggered
[    6.212000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LMAC] -> GSI 3 (level, low) -> IRQ 3
[    6.212000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    6.212000] forcedeth: using HIGHDMA
[    6.456000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    6.668000] usb 1-1: configuration #1 chosen from 1 choice
[    6.732000] eth0: forcedeth.c: subsystem: 01043:812a bound to 0000:00:0a.0
[    6.732000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
[    6.732000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 11 (level, low) -> IRQ 11
[    6.732000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    6.732000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    6.732000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    6.732000] ehci_hcd 0000:00:02.1: debug port 1
[    6.732000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    6.732000] ehci_hcd 0000:00:02.1: irq 11, io mem 0xfeb00000
[    6.732000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.732000] usb usb2: configuration #1 chosen from 1 choice
[    6.732000] hub 2-0:1.0: USB hub found
[    6.732000] hub 2-0:1.0: 10 ports detected
[    6.836000] sata_nv 0000:00:07.0: version 3.4
[    6.836000] ACPI: PCI Interrupt Link [LSID] enabled at IRQ 11
[    6.836000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LSID] -> GSI 11 (level, low) -> IRQ 11
[    6.836000] sata_nv 0000:00:07.0: Using ADMA mode
[    6.840000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    6.840000] scsi0 : sata_nv
[    6.840000] scsi1 : sata_nv
[    6.840000] ata1: SATA max UDMA/133 cmd 0xf8818480 ctl 0xf88184a0 bmdma 0x0001d400 irq 11
[    6.840000] ata2: SATA max UDMA/133 cmd 0xf8818580 ctl 0xf88185a0 bmdma 0x0001d408 irq 11
[    6.848000] hda: max request size: 512KiB
[    6.848000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.848000] Uniform CD-ROM driver Revision: 3.20
[    6.848000] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[    6.848000] hda: cache flushes supported
[    6.848000]  hda: hda1 hda2 < hda5 hda6 >
[    6.992000] usb 1-1: USB disconnect, address 2
[    7.152000] ata1: SATA link down (SStatus 0 SControl 300)
[    7.232000] Attempting manual resume
[    7.232000] swsusp: Resume From Partition 3:5
[    7.232000] PM: Checking swsusp image.
[    7.244000] PM: Resume from disk failed.
[    7.284000] kjournald starting.  Commit interval 5 seconds
[    7.284000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.464000] ata2: SATA link down (SStatus 0 SControl 300)
[    7.464000] ACPI: PCI Interrupt Link [LFID] enabled at IRQ 5
[    7.464000] PCI: setting IRQ 5 as level-triggered
[    7.464000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LFID] -> GSI 5 (level, low) -> IRQ 5
[    7.464000] sata_nv 0000:00:08.0: Using ADMA mode
[    7.464000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    7.464000] scsi2 : sata_nv
[    7.464000] scsi3 : sata_nv
[    7.464000] ata3: SATA max UDMA/133 cmd 0xf885a480 ctl 0xf885a4a0 bmdma 0x0001c000 irq 5
[    7.464000] ata4: SATA max UDMA/133 cmd 0xf885a580 ctl 0xf885a5a0 bmdma 0x0001c008 irq 5
[    7.484000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106000000413d]
[    7.600000] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    7.776000] ata3: SATA link down (SStatus 0 SControl 300)
[    7.888000] usb 2-4: configuration #1 chosen from 1 choice
[    8.088000] ata4: SATA link down (SStatus 0 SControl 300)
[    8.128000] usb 2-6: new high speed USB device using ehci_hcd and address 4
[    8.260000] usb 2-6: configuration #1 chosen from 1 choice
[    8.564000] usb 1-1: new full speed USB device using ohci_hcd and address 3
[    8.776000] usb 1-1: configuration #1 chosen from 1 choice
[   13.940000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.948000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.288000] input: PC Speaker as /class/input/input2
[   14.304000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   14.304000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   14.332000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1411
[   14.332000] usbcore: registered new interface driver usblp
[   14.332000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   14.364000] usbcore: registered new interface driver libusual
[   14.372000] Initializing USB Mass Storage driver...
[   14.372000] scsi4 : SCSI emulation for USB Mass Storage devices
[   14.372000] usbcore: registered new interface driver usb-storage
[   14.372000] USB Mass Storage support registered.
[   14.376000] usb-storage: device found at 4
[   14.376000] usb-storage: waiting for device to settle before scanning
[   14.388000] Linux video capture interface: v2.00
[   14.476000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.516000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ca)
[   14.528000] usbcore: registered new interface driver uvcvideo
[   14.528000] USB Video Class driver (v0.1.0)
[   14.560000] nvidia: module license 'NVIDIA' taints kernel.
[   14.816000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 5
[   14.816000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LNK3] -> GSI 5 (level, low) -> IRQ 5
[   14.816000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   14.816000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   14.892000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   14.892000] parport_pc 00:08: reported by Plug and Play ACPI
[   14.892000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   15.016000] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 3
[   15.016000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LACI] -> GSI 3 (level, low) -> IRQ 3
[   15.016000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   15.024000] usbcore: registered new interface driver snd-usb-audio
[   15.340000] intel8x0_measure_ac97_clock: measured 54681 usecs
[   15.340000] intel8x0: clocking to 46870
[   15.652000] lp0: using parport0 (interrupt-driven).
[   15.720000] Adding 2048248k swap on /dev/hda5.  Priority:-1 extents:1 across:2048248k
[   15.940000] EXT3 FS on hda6, internal journal
[   17.188000] No dock devices found.
[   17.252000] input: Power Button (FF) as /class/input/input4
[   17.252000] ACPI: Power Button (FF) [PWRF]
[   17.252000] input: Power Button (CM) as /class/input/input5
[   17.252000] ACPI: Power Button (CM) [PWRB]
[   17.556000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (version 2.00.00)
[   17.556000] powernow-k8: MP systems not supported by PSB BIOS structure
[   17.556000] powernow-k8: MP systems not supported by PSB BIOS structure
[   19.376000] usb-storage: device scan complete
[   19.376000] scsi 4:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[   19.408000] sd 4:0:0:0: [sda] Attached SCSI removable disk
[   19.520000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[   21.988000] ppdev: user-space parallel port driver
[   22.148000] audit(1193001657.150:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5284 profile="/usr/sbin/cupsd"
[   22.192000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   22.192000] apm: disabled - APM is not SMP safe.
[   22.464000] Failure registering capabilities with primary security module.
[   22.680000] Bluetooth: Core ver 2.11
[   22.680000] NET: Registered protocol family 31
[   22.680000] Bluetooth: HCI device and connection manager initialized
[   22.680000] Bluetooth: HCI socket layer initialized
[   22.700000] Bluetooth: L2CAP ver 2.8
[   22.700000] Bluetooth: L2CAP socket layer initialized
[   22.728000] Bluetooth: RFCOMM socket layer initialized
[   22.728000] Bluetooth: RFCOMM TTY layer initialized
[   22.728000] Bluetooth: RFCOMM ver 1.8
[   26.916000] NET: Registered protocol family 17
[   28.180000] NET: Registered protocol family 10
[   28.180000] lo: Disabled Privacy Extensions
[   38.212000] eth0: no IPv6 routers present
[ 2192.996000] usb 2-4: USB disconnect, address 3
[ 2197.620000] usb 2-4: new high speed USB device using ehci_hcd and address 5
[ 2197.896000] usb 2-4: configuration #1 chosen from 1 choice
[ 2197.896000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ca)
[15211.148000] uvcvideo: Failed to query (131) UVC control 4 (unit 1) : -32 (exp. 4).
[16299.700000] process `sysctl' is using deprecated sysctl (syscall) net.ipv6.neigh.default.retrans_time; Use net.ipv6.neigh.default.retrans_time_ms instead.
[16834.836000] usb 2-4: USB disconnect, address 5
[16837.468000] usb 2-4: new high speed USB device using ehci_hcd and address 6
[16837.740000] usb 2-4: configuration #1 chosen from 1 choice
[16837.740000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ca)
[17355.480000] uvcvideo: Failed to query (131) UVC control 1 (unit 0) : -32 (exp. 26).
[17720.264000] usb 2-4: USB disconnect, address 6
[17920.160000] usb 2-4: new high speed USB device using ehci_hcd and address 7
[17920.436000] usb 2-4: configuration #1 chosen from 1 choice
[17920.436000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ca)

```

this obviously isnt what is supposed to come up according to mscman. Can someone please help me get my quickcam fusion up and running?

---

### Post by amneziac on 2007-10-22
please can i get some help?

---

