---
title: "iPod won't mount"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by UbuntuniX on 2007-08-28
Until a few days ago, my iPod Nano was working fine with Amarok.
Now, for no apparent reason, it can't be found.

I get the "Do Not Disconnect" screen whenever it is connected to my computer, but it won't automount, and I haven't been able to mount it with gtkpod or anything else.

---

### Post by simonn on 2007-08-28
Plug in your ipod, wait a few seconds (10 or so) and then, what does the following return:

```

$ dmesg

```

I suspect that you initialized your ipod with a mac so it is HFS+ formatted and that you need to do a fsck... however we shall see...

---

### Post by UbuntuniX on 2007-08-28
> **simonn said:**
> Plug in your ipod, wait a few seconds (10 or so) and then, what does the following return:

```

$ dmesg

```

I suspect that you initialized your ipod with a mac so it is HFS+ formatted and that you need to do a fsck... however we shall see...

It was originally Windows formatted.

```
[    0.000000] ACPI: APIC 3FFF81C0, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD  1010101)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: OEM00000 Product ID: PROD00000000 APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:b0000000)
[    0.000000] Built 1 zonelists.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=01afcb1b-4f2a-4d5f-b08d-f010d0037214 ro quiet splash noapic
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2009.146 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 1027760k/1048512k available (2010k kernel code, 20008k reserved, 917k data, 364k init, 131008k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e1000 - 0xc043c000   ( 364 kB)
[    0.000000]       .data : 0xc02f69c6 - 0xc03dbe64   ( 917 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f69c6   (2010 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.084000] Calibrating delay using timer specific routine.. 4021.78 BogoMIPS (lpj=8043569)
[    0.084000] Security Framework v1.0.0 initialized
[    0.084000] SELinux:  Disabled at boot.
[    0.084000] Mount-cache hash table entries: 512
[    0.084000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.084000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.084000] CPU 0(2) -> Core 0
[    0.084000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.084000] Compat vDSO mapped to ffffe000.
[    0.084000] Checking 'hlt' instruction... OK.
[    0.100000] SMP alternatives: switching to UP code
[    0.100000] Early unpacking initramfs... done
[    0.388000] ACPI: Core revision 20070126
[    0.388000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.388000] ACPI: setting ELCR to 0200 (from 8c20)
[    0.392000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.392000] SMP alternatives: switching to SMP code
[    0.392000] Booting processor 1/1 eip 3000
[    0.400000] Initializing CPU#1
[    0.484000] Calibrating delay using timer specific routine.. 4018.58 BogoMIPS (lpj=8037177)
[    0.484000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.484000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.484000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.484000] CPU 1(2) -> Core 1
[    0.484000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.484000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.484000] Total of 2 processors activated (8040.37 BogoMIPS).
[    0.484000] Brought up 2 CPUs
[    0.548000] migration_cost=4000
[    0.548000] Booting paravirtualized kernel on bare hardware
[    0.548000] Time: 10:02:09  Date: 07/28/107
[    0.548000] NET: Registered protocol family 16
[    0.548000] EISA bus registered
[    0.548000] ACPI: bus type pci registered
[    0.552000] PCI: PCI BIOS revision 3.00 entry at 0xfb790, last bus=3
[    0.552000] PCI: Using configuration type 1
[    0.552000] Setting up standard PCI resources
[    0.556000] ACPI: EC: Look up EC in DSDT
[    0.564000] ACPI: Interpreter enabled
[    0.564000] ACPI: (supports S0 S1 S4 S5)
[    0.564000] ACPI: Using PIC for interrupt routing
[    0.572000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.572000] PCI: Probing PCI hardware (bus 00)
[    0.572000] PCI: Transparent bridge - 0000:00:0e.0
[    0.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.576000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.660000] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[    0.660000] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[    0.660000] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
[    0.660000] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.660000] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.660000] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 *10 11 14 15)
[    0.664000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 *15)
[    0.664000] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 *15)
[    0.664000] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[    0.664000] ACPI: PCI Interrupt Link [LMC1] (IRQs 5 7 9 10 *11 14 15)
[    0.664000] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 *15)
[    0.664000] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[    0.664000] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.664000] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.664000] ACPI: PCI Interrupt Link [LFID] (IRQs *5 7 9 10 11 14 15)
[    0.664000] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 *10 11 14 15)
[    0.664000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.664000] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [AMC1] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0, disabled.
[    0.668000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.668000] pnp: PnP ACPI init
[    0.668000] ACPI: bus type pnp registered
[    0.672000] pnp: PnP ACPI: found 14 devices
[    0.672000] ACPI: ACPI bus type pnp unregistered
[    0.672000] PnPBIOS: Disabled by ACPI PNP
[    0.672000] PCI: Using ACPI for IRQ routing
[    0.672000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.744000] NET: Registered protocol family 8
[    0.744000] NET: Registered protocol family 20
[    0.744000] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[    0.744000] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.744000] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[    0.744000] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.744000] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[    0.744000] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.744000] pnp: 00:0c: iomem range 0xf0000000-0xf7ffffff could not be reserved
[    0.744000] pnp: 00:0d: iomem range 0xd2800-0xd3fff has been reserved
[    0.744000] pnp: 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.744000] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.744000] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.772000] PCI: Bridge: 0000:00:0e.0
[    0.772000]   IO window: 6000-6fff
[    0.772000]   MEM window: fb000000-fb0fffff
[    0.772000]   PREFETCH window: disabled.
[    0.772000] PCI: Bridge: 0000:00:12.0
[    0.772000]   IO window: 7000-7fff
[    0.772000]   MEM window: f8000000-faffffff
[    0.772000]   PREFETCH window: e0000000-efffffff
[    0.772000] PCI: Bridge: 0000:00:15.0
[    0.772000]   IO window: 8000-9fff
[    0.772000]   MEM window: fb100000-fb1fffff
[    0.772000]   PREFETCH window: disabled.
[    0.772000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[    0.772000] PCI: Setting latency timer of device 0000:00:12.0 to 64
[    0.772000] PCI: Setting latency timer of device 0000:00:15.0 to 64
[    0.772000] NET: Registered protocol family 2
[    0.776000] Time: acpi_pm clocksource has been installed.
[    0.776000] Switched to high resolution mode on CPU 0
[    0.776000] Switched to high resolution mode on CPU 1
[    0.816000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.816000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.816000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.816000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.816000] TCP reno registered
[    0.828000] checking if image is initramfs... it is
[    1.396000] Freeing initrd memory: 7108k freed
[    1.396000] audit: initializing netlink socket (disabled)
[    1.396000] audit(1188295329.276:1): initialized
[    1.396000] highmem bounce pool size: 64 pages
[    1.396000] VFS: Disk quotas dquot_6.5.1
[    1.396000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.396000] io scheduler noop registered
[    1.396000] io scheduler anticipatory registered
[    1.396000] io scheduler deadline registered
[    1.396000] io scheduler cfq registered (default)
[    1.396000] Boot video device is 0000:02:00.0
[    1.396000] PCI: Setting latency timer of device 0000:00:12.0 to 64
[    1.396000] assign_interrupt_mode Found MSI capability
[    1.396000] Allocate Port Service[0000:00:12.0:pcie00]
[    1.396000] PCI: Setting latency timer of device 0000:00:15.0 to 64
[    1.396000] assign_interrupt_mode Found MSI capability
[    1.396000] Allocate Port Service[0000:00:15.0:pcie00]
[    1.400000] isapnp: Scanning for PnP cards...
[    1.752000] isapnp: No Plug & Play device found
[    1.772000] Real Time Clock Driver v1.12ac
[    1.772000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.772000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.776000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.776000] input: Macintosh mouse button emulation as /class/input/input0
[    1.776000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.776000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.776000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.776000] mice: PS/2 mouse device common for all mice
[    1.776000] EISA: Probing bus 0 at eisa.0
[    1.776000] Cannot allocate resource for EISA slot 1
[    1.776000] Cannot allocate resource for EISA slot 6
[    1.776000] Cannot allocate resource for EISA slot 7
[    1.776000] Cannot allocate resource for EISA slot 8
[    1.776000] EISA: Detected 0 cards.
[    1.776000] TCP cubic registered
[    1.776000] NET: Registered protocol family 1
[    1.776000] Using IPI No-Shortcut mode
[    1.776000]   Magic number: 3:138:23
[    1.776000]   hash matches device 0000:00:09.2
[    1.776000] Freeing unused kernel memory: 364k freed
[    1.808000] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.996000] AppArmor: AppArmor initialized
[    2.996000] audit(1188295330.776:2): AppArmor initialized
[    2.996000] 
[    3.000000] AppArmor: Registered secondary security module: capability.
[    3.000000] Capability LSM initialized as secondary
[    3.560000] usbcore: registered new interface driver usbfs
[    3.560000] usbcore: registered new interface driver hub
[    3.560000] usbcore: registered new device driver usb
[    3.560000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.560000] ACPI: PCI Interrupt Link [LUBA] enabled at IRQ 15
[    3.560000] PCI: setting IRQ 15 as level-triggered
[    3.560000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LUBA] -> GSI 15 (level, low) -> IRQ 15
[    3.560000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    3.560000] ohci_hcd 0000:00:0a.0: OHCI Host Controller
[    3.560000] ohci_hcd 0000:00:0a.0: new USB bus registered, assigned bus number 1
[    3.560000] ohci_hcd 0000:00:0a.0: irq 15, io mem 0xfb204000
[    3.580000] SCSI subsystem initialized
[    3.584000] libata version 2.21 loaded.
[    3.628000] usb usb1: configuration #1 chosen from 1 choice
[    3.628000] hub 1-0:1.0: USB hub found
[    3.628000] hub 1-0:1.0: 10 ports detected
[    3.644000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    3.712000] Floppy drive(s): fd0 is 1.44M
[    3.728000] FDC 0 is a post-1991 82077
[    3.732000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 5
[    3.732000] PCI: setting IRQ 5 as level-triggered
[    3.732000] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [LUB2] -> GSI 5 (level, low) -> IRQ 5
[    3.732000] PCI: Setting latency timer of device 0000:00:0a.1 to 64
[    3.732000] ehci_hcd 0000:00:0a.1: EHCI Host Controller
[    3.732000] ehci_hcd 0000:00:0a.1: new USB bus registered, assigned bus number 2
[    3.732000] ehci_hcd 0000:00:0a.1: debug port 1
[    3.732000] PCI: cache line size of 64 is not supported by device 0000:00:0a.1
[    3.732000] ehci_hcd 0000:00:0a.1: irq 5, io mem 0xfb205000
[    3.732000] ehci_hcd 0000:00:0a.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.732000] usb usb2: configuration #1 chosen from 1 choice
[    3.732000] hub 2-0:1.0: USB hub found
[    3.732000] hub 2-0:1.0: 10 ports detected
[    3.836000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 15
[    3.836000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LMAC] -> GSI 15 (level, low) -> IRQ 15
[    3.836000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[    3.836000] forcedeth: using HIGHDMA
[    3.844000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    3.844000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    4.132000] usb 2-7: new high speed USB device using ehci_hcd and address 2
[    4.356000] eth0: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:10.0
[    4.356000] ACPI: PCI Interrupt Link [LMC1] enabled at IRQ 11
[    4.356000] PCI: setting IRQ 11 as level-triggered
[    4.356000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LMC1] -> GSI 11 (level, low) -> IRQ 11
[    4.356000] PCI: Setting latency timer of device 0000:00:11.0 to 64
[    4.356000] forcedeth: using HIGHDMA
[    4.420000] usb 2-7: configuration #1 chosen from 1 choice
[    4.876000] eth1: forcedeth.c: subsystem: 01458:e000 bound to 0000:00:11.0
[    4.876000] ahci 0000:03:00.0: version 2.2
[    4.876000] ACPI: PCI Interrupt Link [LNK8] enabled at IRQ 15
[    4.876000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNK8] -> GSI 15 (level, low) -> IRQ 15
[    5.880000] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    5.880000] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    5.880000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    5.880000] scsi0 : ahci
[    5.880000] scsi1 : ahci
[    5.880000] ata1: SATA max UDMA/133 cmd 0xf8918100 ctl 0x00000000 bmdma 0x00000000 irq 15
[    5.880000] ata2: SATA max UDMA/133 cmd 0xf8918180 ctl 0x00000000 bmdma 0x00000000 irq 15
[    6.192000] ata1: SATA link down (SStatus 0 SControl 300)
[    6.504000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.504000] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[    6.504000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 10
[    6.504000] PCI: setting IRQ 10 as level-triggered
[    6.504000] ACPI: PCI Interrupt 0000:03:00.1[B] -> Link [LNK5] -> GSI 10 (level, low) -> IRQ 10
[    6.504000] PCI: Setting latency timer of device 0000:03:00.1 to 64
[    6.504000] scsi2 : pata_jmicron
[    6.504000] scsi3 : pata_jmicron
[    6.504000] ata3: PATA max UDMA/100 cmd 0x00018000 ctl 0x00018402 bmdma 0x00019000 irq 10
[    6.504000] ata4: PATA max UDMA/100 cmd 0x00018800 ctl 0x00018c02 bmdma 0x00019008 irq 10
[    6.824000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 10
[    6.824000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [LNK3] -> GSI 10 (level, low) -> IRQ 10
[    6.828000] NFORCE-MCP55: IDE controller at PCI slot 0000:00:0c.0
[    6.828000] NFORCE-MCP55: chipset revision 161
[    6.828000] NFORCE-MCP55: not 100% native mode: will probe irqs later
[    6.828000] NFORCE-MCP55: BIOS didn't set cable bits correctly. Enabling workaround.
[    6.828000] NFORCE-MCP55: 0000:00:0c.0 (rev a1) UDMA133 controller
[    6.828000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[    6.828000] Probing IDE interface ide0...
[    6.876000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[fb004000-fb0047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.116000] hda: HDT722525DLAT80, ATA DISK drive
[    7.564000] hdb: LITE-ON COMBO SOHC-5235K, ATAPI CD/DVD-ROM drive
[    7.620000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.632000] sata_nv 0000:00:0d.0: version 3.4
[    7.632000] ACPI: PCI Interrupt Link [LSID] enabled at IRQ 11
[    7.632000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LSID] -> GSI 11 (level, low) -> IRQ 11
[    7.632000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[    7.632000] scsi4 : sata_nv
[    7.632000] scsi5 : sata_nv
[    7.632000] ata5: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001a002 bmdma 0x0001ac00 irq 11
[    7.632000] ata6: SATA max UDMA/133 cmd 0x0001a400 ctl 0x0001a802 bmdma 0x0001ac08 irq 11
[    7.644000] hda: max request size: 512KiB
[    7.644000] hda: Host Protected Area detected.
[    7.644000]  current capacity is 488395055 sectors (250058 MB)
[    7.644000]  native  capacity is 488397168 sectors (250059 MB)
[    7.644000] hda: Host Protected Area disabled.
[    7.644000] hda: 488397168 sectors (250059 MB) w/7674KiB Cache, CHS=30401/255/63, UDMA(133)
[    7.644000] hda: cache flushes supported
[    7.644000]  hda: hda2 hda3
[    7.676000] hdb: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.676000] Uniform CD-ROM driver Revision: 3.20
[    7.944000] ata5: SATA link down (SStatus 0 SControl 300)
[    8.148000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0016e60000b79732]
[    8.264000] ata6: SATA link down (SStatus 0 SControl 300)
[    8.272000] ACPI: PCI Interrupt Link [LFID] enabled at IRQ 5
[    8.272000] ACPI: PCI Interrupt 0000:00:0d.1[B] -> Link [LFID] -> GSI 5 (level, low) -> IRQ 5
[    8.272000] PCI: Setting latency timer of device 0000:00:0d.1 to 64
[    8.272000] scsi6 : sata_nv
[    8.272000] scsi7 : sata_nv
[    8.272000] ata7: SATA max UDMA/133 cmd 0x0001b000 ctl 0x0001b402 bmdma 0x0001c000 irq 5
[    8.272000] ata8: SATA max UDMA/133 cmd 0x0001b800 ctl 0x0001bc02 bmdma 0x0001c008 irq 5
[    8.584000] ata7: SATA link down (SStatus 0 SControl 300)
[    8.608000] Attempting manual resume
[    8.608000] swsusp: Resume From Partition 3:3
[    8.608000] PM: Checking swsusp image.
[    8.608000] PM: Resume from disk failed.
[    8.644000] kjournald starting.  Commit interval 5 seconds
[    8.644000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.904000] ata8: SATA link down (SStatus 0 SControl 300)
[    8.912000] ACPI: PCI Interrupt Link [LSA2] enabled at IRQ 10
[    8.912000] ACPI: PCI Interrupt 0000:00:0d.2[C] -> Link [LSA2] -> GSI 10 (level, low) -> IRQ 10
[    8.912000] PCI: Setting latency timer of device 0000:00:0d.2 to 64
[    8.912000] scsi8 : sata_nv
[    8.912000] scsi9 : sata_nv
[    8.912000] ata9: SATA max UDMA/133 cmd 0x0001c400 ctl 0x0001c802 bmdma 0x0001d400 irq 10
[    8.912000] ata10: SATA max UDMA/133 cmd 0x0001cc00 ctl 0x0001d002 bmdma 0x0001d408 irq 10
[    9.224000] ata9: SATA link down (SStatus 0 SControl 300)
[    9.544000] ata10: SATA link down (SStatus 0 SControl 300)
[   17.060000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.068000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.096000] NET: Registered protocol family 17
[   17.136000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   17.136000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   17.368000] input: PC Speaker as /class/input/input2
[   17.484000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.556000] nvidia: module license 'NVIDIA' taints kernel.
[   17.812000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 10
[   17.812000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK7] -> GSI 10 (level, low) -> IRQ 10
[   17.812000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   17.812000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   17.956000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 15
[   17.956000] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [LAZA] -> GSI 15 (level, low) -> IRQ 15
[   17.956000] PCI: Setting latency timer of device 0000:00:0e.1 to 64
[   17.956000] input: PS2++ Logitech MX Mouse as /class/input/input3
[   17.960000] parport_pc 00:09: reported by Plug and Play ACPI
[   17.960000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   18.068000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   18.068000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNK1] -> GSI 5 (level, low) -> IRQ 5
[   18.068000] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   18.180000] wmaster0: Selected rate control algorithm 'simple'
[   18.236000] usbcore: registered new interface driver rt2500usb
[   18.520000] fuse init (API version 7.8)
[   18.552000] lp0: using parport0 (interrupt-driven).
[   18.624000] Adding 14370132k swap on /dev/hda3.  Priority:-1 extents:1 across:14370132k
[   18.888000] EXT3 FS on hda2, internal journal
[   19.380000] AppArmor: Unregistered secondary security module: capability
[   22.440000] input: Power Button (FF) as /class/input/input4
[   22.440000] ACPI: Power Button (FF) [PWRF]
[   22.440000] input: Power Button (CM) as /class/input/input5
[   22.440000] ACPI: Power Button (CM) [PWRB]
[   22.488000] No dock devices found.
[   22.768000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   22.768000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xa
[   22.768000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xc
[   22.768000] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   27.632000] ppdev: user-space parallel port driver
[   27.944000] audit(1188291756.343:3): REJECTING m access to /etc/passwd (cupsd(5392) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   27.944000] audit(1188291756.343:4): REJECTING m access to /etc/group (cupsd(5392) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   27.948000] audit(1188291756.343:5): REJECTING m access to /etc/group (cupsd(5392) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   28.136000] audit(1188291756.343:6): REJECTING w access to /dev/tty (cupsd(5392) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   30.440000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   30.440000] apm: disabled - APM is not SMP safe.
[   31.856000] AppArmor: Registered secondary security module: capability.
[   31.856000] Capability LSM initialized as secondary
[   32.272000] Clocksource tsc unstable (delta = -250013174 ns)
[   32.444000] Bluetooth: Core ver 2.11
[   32.444000] NET: Registered protocol family 31
[   32.444000] Bluetooth: HCI device and connection manager initialized
[   32.444000] Bluetooth: HCI socket layer initialized
[   32.464000] Bluetooth: L2CAP ver 2.8
[   32.464000] Bluetooth: L2CAP socket layer initialized
[   32.556000] Bluetooth: RFCOMM socket layer initialized
[   32.556000] Bluetooth: RFCOMM TTY layer initialized
[   32.556000] Bluetooth: RFCOMM ver 1.8
[  401.524000] audit(1188292129.865:7): REJECTING m access to /etc/passwd (cupsd(5392) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[  401.524000] audit(1188292129.865:8): REJECTING m access to /etc/group (cupsd(5392) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[  401.524000] audit(1188292129.865:9): REJECTING m access to /etc/group (cupsd(5392) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[  476.476000] cdrom: hdb: mrw address space DMA selected
[  478.344000] cdrom: hdb: mrw address space DMA selected
[  478.516000] UDF-fs: No VRS found
[  480.308000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  480.588000] ISO 9660 Extensions: RRIP_1991A
[ 6400.696000] usb 2-8: new high speed USB device using ehci_hcd and address 3
[ 6400.828000] usb 2-8: configuration #1 chosen from 2 choices
[ 6401.020000] usbcore: registered new interface driver libusual
[ 6401.096000] Initializing USB Mass Storage driver...
[ 6401.100000] scsi10 : SCSI emulation for USB Mass Storage devices
[ 6401.108000] usb-storage: device found at 3
[ 6401.108000] usb-storage: waiting for device to settle before scanning
[ 6401.108000] usbcore: registered new interface driver usb-storage
[ 6401.108000] USB Mass Storage support registered.
[ 6406.108000] usb-storage: device scan complete
[ 6406.108000] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 6406.152000] sd 10:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[ 6406.156000] sd 10:0:0:0: [sda] Write Protect is off
[ 6406.156000] sd 10:0:0:0: [sda] Mode Sense: 68 00 00 08
[ 6406.156000] sd 10:0:0:0: [sda] Assuming drive cache: write through
[ 6406.164000] sd 10:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[ 6406.164000] sd 10:0:0:0: [sda] Write Protect is off
[ 6406.164000] sd 10:0:0:0: [sda] Mode Sense: 68 00 00 08
[ 6406.164000] sd 10:0:0:0: [sda] Assuming drive cache: write through
[ 6406.164000]  sda: sda1 sda2
[ 6406.168000] sd 10:0:0:0: [sda] Attached SCSI removable disk
[ 6406.188000] sd 10:0:0:0: Attached scsi generic sg0 type 0
[ 7011.124000] usb 2-8: USB disconnect, address 3
[ 7026.880000] usb 2-8: new high speed USB device using ehci_hcd and address 4
[ 7027.012000] usb 2-8: configuration #1 chosen from 2 choices
[ 7027.012000] scsi11 : SCSI emulation for USB Mass Storage devices
[ 7027.012000] usb-storage: device found at 4
[ 7027.012000] usb-storage: waiting for device to settle before scanning
[ 7032.012000] usb-storage: device scan complete
[ 7032.012000] scsi 11:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 7032.016000] sd 11:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[ 7032.020000] sd 11:0:0:0: [sda] Write Protect is off
[ 7032.020000] sd 11:0:0:0: [sda] Mode Sense: 68 00 00 08
[ 7032.020000] sd 11:0:0:0: [sda] Assuming drive cache: write through
[ 7032.024000] sd 11:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[ 7032.024000] sd 11:0:0:0: [sda] Write Protect is off
[ 7032.024000] sd 11:0:0:0: [sda] Mode Sense: 68 00 00 08
[ 7032.024000] sd 11:0:0:0: [sda] Assuming drive cache: write through
[ 7032.024000]  sda: sda1 sda2
[ 7032.028000] sd 11:0:0:0: [sda] Attached SCSI removable disk
[ 7032.028000] sd 11:0:0:0: Attached scsi generic sg0 type 0
[ 7538.636000] usb 2-8: USB disconnect, address 4
[ 7555.068000] usb 2-8: new high speed USB device using ehci_hcd and address 5
[ 7555.200000] usb 2-8: configuration #1 chosen from 2 choices
[ 7555.200000] scsi12 : SCSI emulation for USB Mass Storage devices
[ 7555.200000] usb-storage: device found at 5
[ 7555.200000] usb-storage: waiting for device to settle before scanning
[ 7560.200000] usb-storage: device scan complete
[ 7560.200000] scsi 12:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 7560.204000] sd 12:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[ 7560.208000] sd 12:0:0:0: [sda] Write Protect is off
[ 7560.208000] sd 12:0:0:0: [sda] Mode Sense: 68 00 00 08
[ 7560.208000] sd 12:0:0:0: [sda] Assuming drive cache: write through
[ 7560.212000] sd 12:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[ 7560.212000] sd 12:0:0:0: [sda] Write Protect is off
[ 7560.212000] sd 12:0:0:0: [sda] Mode Sense: 68 00 00 08
[ 7560.212000] sd 12:0:0:0: [sda] Assuming drive cache: write through
[ 7560.212000]  sda: sda1 sda2
[ 7560.216000] sd 12:0:0:0: [sda] Attached SCSI removable disk
[ 7560.216000] sd 12:0:0:0: Attached scsi generic sg0 type 0
[12720.704000] usb 2-8: USB disconnect, address 5
[12730.532000] usb 2-8: new high speed USB device using ehci_hcd and address 6
[12731.448000] usb 2-8: new high speed USB device using ehci_hcd and address 7
[12731.580000] usb 2-8: configuration #1 chosen from 2 choices
[12731.580000] scsi13 : SCSI emulation for USB Mass Storage devices
[12731.580000] usb-storage: device found at 7
[12731.580000] usb-storage: waiting for device to settle before scanning
[12732.524000] usb 2-8: USB disconnect, address 7
[12734.056000] usb 2-8: new high speed USB device using ehci_hcd and address 8
[12734.188000] usb 2-8: configuration #1 chosen from 2 choices
[12734.188000] scsi14 : SCSI emulation for USB Mass Storage devices
[12734.188000] usb-storage: device found at 8
[12734.188000] usb-storage: waiting for device to settle before scanning
[12739.188000] usb-storage: device scan complete
[12739.188000] scsi 14:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[12739.744000] sd 14:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[12739.748000] sd 14:0:0:0: [sda] Write Protect is off
[12739.748000] sd 14:0:0:0: [sda] Mode Sense: 68 00 00 08
[12739.748000] sd 14:0:0:0: [sda] Assuming drive cache: write through
[12739.752000] sd 14:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[12739.752000] sd 14:0:0:0: [sda] Write Protect is off
[12739.752000] sd 14:0:0:0: [sda] Mode Sense: 68 00 00 08
[12739.752000] sd 14:0:0:0: [sda] Assuming drive cache: write through
[12739.752000]  sda: sda1 sda2
[12739.756000] sd 14:0:0:0: [sda] Attached SCSI removable disk
[12739.756000] sd 14:0:0:0: Attached scsi generic sg0 type 0
```

---

### Post by simonn on 2007-08-28
Ipods usually have three partitions e.g. sda1, sda2 and sda3, and sda3 is the parition that files are written to.

You do not have an sda3. I find that a bit worrying. 

Can you try mounting sda1 and sda2 manually? What happens?

Is there anything in /var/log/kern.log or /var/log/messages?

You may need to reinitialize your ipod(?).

---

### Post by simonn on 2007-08-28
> **simonn said:**
> Ipods usually have three partitions e.g. sda1, sda2 and sda3, and sda3 is the parition that files are written to.

You do not have an sda3. I find that a bit worrying. 


Sorry, that appears to be for HFS+ ipods, not windows. Try the mounting as before.

---

### Post by UbuntuniX on 2007-08-28
> **simonn said:**
> Can you try mounting sda1 and sda2 manually? What happens?

What/How exactly do I mount?

> **simonn said:**
> Is there anything in /var/log/kern.log or /var/log/messages?

```
Aug 27 12:52:10 phrbot1 kernel: [11277.688000] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Aug 27 12:52:10 phrbot1 kernel: [11277.724000] sd 10:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
Aug 27 12:52:10 phrbot1 kernel: [11277.724000] sd 10:0:0:0: [sda] Write Protect is off
Aug 27 12:52:10 phrbot1 kernel: [11277.732000] sd 10:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
Aug 27 12:52:10 phrbot1 kernel: [11277.732000] sd 10:0:0:0: [sda] Write Protect is off
Aug 27 12:52:10 phrbot1 kernel: [11277.732000]  sda: sda1 sda2
Aug 27 12:52:10 phrbot1 kernel: [11277.736000] sd 10:0:0:0: [sda] Attached SCSI removable disk
Aug 27 12:52:10 phrbot1 kernel: [11277.748000] sd 10:0:0:0: Attached scsi generic sg0 type 0
Aug 27 12:52:48 phrbot1 kernel: [11316.404000] usb 1-10: USB disconnect, address 3
Aug 27 12:53:29 phrbot1 kernel: [11356.748000] usb 1-10: new high speed USB device using ehci_hcd and address 4
Aug 27 12:53:29 phrbot1 kernel: [11356.880000] usb 1-10: configuration #1 chosen from 2 choices
Aug 27 12:53:29 phrbot1 kernel: [11356.880000] scsi11 : SCSI emulation for USB Mass Storage devices
```

> **simonn said:**
> You may need to reinitialize your ipod(?).

Explain?

---

### Post by UbuntuniX on 2007-08-31
Bump. :(

---

### Post by TryMe on 2007-09-01
First your dmesg looks normal for a Windows formatted nano. :)

If you look in the /media folder without the ipod attached to the pc do you see an IPOD folder? (This folder should have the same name as your ipod) If you do delete it. Just make sure your ipod is NOT attached to the pc.

Also check your "Removable Drives and Media Prefrences" located in System -> Prefrences -> "Removable Drives and Media Prefrences" 

on the storage tab see if the mount removable drives and mount removable media options are checked.
on the multimedia tab disable the default command for portable music players.

If none of that helps can you mount any usb drive? Or is this only an issue with the iPod?

---

### Post by UbuntuniX on 2007-09-01
> **TryMe said:**
> First your dmesg looks normal for a Windows formatted nano. :)

It was originally used with iTunes on Windows.

> **TryMe said:**
> If you look in the /media folder without the ipod attached to the pc do you see an IPOD folder? (This folder should have the same name as your ipod) If you do delete it. Just make sure your ipod is NOT attached to the pc.

Nothing.

[> **TryMe said:**
> Also check your "Removable Drives and Media Prefrences" located in System -> Prefrences -> "Removable Drives and Media Prefrences" 

on the storage tab see if the mount removable drives and mount removable media options are checked.
on the multimedia tab disable the default command for portable music players.

All checked.

> **TryMe said:**
> If none of that helps can you mount any usb drive? Or is this only an issue with the iPod?

I don't have any other USB devices with storage to mount, so I can't be sure.
Other USB devices are working, though.

------------

Okay, I've formatted the iPod on a Windows PC with iTunes. Now it still won't mount, and I've got no music. Not good. :(

---

### Post by TryMe on 2007-09-01
1) it would be a good idea to get a usb thumbdrive or something just to test.
2) Check and make sure that you have put the ipod in disk mode with iTunes.
3) With the ipod connected on the ubuntu pc run the "mount" command in a shell and post the output please. 
If you don't see your ipod mounted you can try doing it manualy.
sudo mkdir /media/IPOD
sudo mount -t vfat /dev/sda2 /media/IPOD

---

### Post by UbuntuniX on 2007-09-01
> **TryMe said:**
> 1) it would be a good idea to get a usb thumbdrive or something just to test.
2) Check and make sure that you have put the ipod in disk mode with iTunes.
3) With the ipod connected on the ubuntu pc run the "mount" command in a shell and post the output please. 
If you don't see your ipod mounted you can try doing it manualy.
sudo mkdir /media/IPOD
sudo mount -t vfat /dev/sda2 /media/IPOD

Worked! Much love! <3


Any idea why this is though?
```
Media Device: failed to create lockfile on iPod mounted at /media/ubiPod: Permission denied
```

I get it when trying to connect to it in Amarok.

---

### Post by TryMe on 2007-09-01
Progress :).

maybe permissions
try
sudo mkdir /media/ubiPod
chmod 655 /media/ubiPod
sudo mount -t vfat /dev/sda2 /media/ubiPod

and remember to unmount your ipod before removal
sudo eject -m /dev/sda2 

don't use umount on an ipod

for automatic eject from amaork
you might try editing the PostDisconnectCommand option for your ipod in the amarok config file
/home/<user name>/.kde/share/config/amarokrc

something like this should work:
PostDisconnectCommand=echo "<your password>" | sudo -S eject -m %d

I have found the editing the option through the 1.4.5 GUI does not work.

---

### Post by UbuntuniX on 2007-09-07
> **TryMe said:**
> maybe permissions
try
sudo mkdir /media/ubiPod
chmod 655 /media/ubiPod
sudo mount -t vfat /dev/sda2 /media/ubiPod

Didn't work; I ever tried 777, but no luck.



Nothing seems to work. I've got no portable tunes now! :(

---

### Post by TryMe on 2007-09-08
make sure you put the ipod in disk mode with iTunes.

add this to bottom of /etc/fstab
/dev/sda2 /media/ubiPod vfat  auto rw,users,gid=plugdev,umask=0002,defaults

then run on cli 
killall gnome-volume-manager
gnome-volume-manager
then plug in the ipod

if that does not work try manual mount
sudo mount -t vfat /dev/sda2 /media/ubiPod
while ipod is mounted post output of dmesg , mount and the contents of /etc/mount and /etc/fstab

oh and are you running Gusty Gibbon?

---

### Post by UbuntuniX on 2007-09-14
Hmm, checked a camera (USB) and it's not mounting either.

---

### Post by lvleph on 2007-12-02
In fstab I used
UUID=B2C2-D250 /media/iPod vfat rw,users,gid=plugdev,umask=0002,defaults

I used UUID instead of /dev/sd?2 because using sd?2 will not always work. There is not guaranty that this is the correct device. So I mounted the iPod manually once, then used the GUI right click the device>>properties volume tab and you will see the UUID for that device.

---

### Post by John Azelvandre on 2007-12-17
> **TryMe said:**
> make sure you put the ipod in disk mode with iTunes.



Hey guys, I'm a noob at trying to use my ipod with Linux.  I have a similar problem as has been described here -- the ipod will only mount read-only.  It is formatted HSF+.  I previously used it on a Mac which I NO LONGER have. I don't have access to a Windows version of iTunes either.   I have only Ubuntu.  So I cannot put it into disk mode, whatever that means.

So, what are my options?  How can I get this to work with Linux?  Any help would be appreciated.

---

