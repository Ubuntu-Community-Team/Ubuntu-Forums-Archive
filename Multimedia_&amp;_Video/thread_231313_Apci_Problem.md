---
title: "Apci Problem"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by lhds on 2006-08-07
hello .... ive installed it ... and it was working fine.... 
made a reinstall because of a disk failure ... on the same disk wich is working fine ... i got a surprise ... when kernel starts it throws biosbug timer not connected to io.apci 
than when i dmsg .....

```
(Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000037fd0000 (usable)
[4294667.296000]  BIOS-e820: 0000000037fd0000 - 0000000037fdf000 (ACPI data)
[4294667.296000]  BIOS-e820: 0000000037fdf000 - 0000000038000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 895MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 229328
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225232 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ATI board detected. Disabling timer routing over 8254.
[4294667.296000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f83c0
[4294667.296000] ACPI: RSDT (v001 A M I  OEMRSDT  0x08000529 MSFT 0x00000097) @ 0x37fd0000
[4294667.296000] ACPI: FADT (v001 A M I  OEMFACP  0x08000529 MSFT 0x00000097) @ 0x37fd0200
[4294667.296000] ACPI: MADT (v001 A M I  OEMAPIC  0x08000529 MSFT 0x00000097) @ 0x37fd0390
[4294667.296000] ACPI: SSDT (v001 OEM_ID OEMTBLID 0x00000001 INTL 0x02002026) @ 0x37fd5140
[4294667.296000] ACPI: OEMB (v001 A M I  AMI_OEM  0x08000529 MSFT 0x00000097) @ 0x37fdf040
[4294667.296000] ACPI: MCFG (v001 A M I  OEMMCFG  0x08000529 MSFT 0x00000097) @ 0x37fd51c0
[4294667.296000] ACPI: DSDT (v001  410M0 410M0829 0x00000829 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x4008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:4 APIC version 20
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: BIOS IRQ0 pin2 override ignored.
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 40000000 (gap: 38000000:c6e00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/sda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 3060.737 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.941000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.942000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.958000] Memory: 898612k/917312k available (1976k kernel code, 18128k reserved, 606k data, 288k init, 0k highmem)
[4294667.958000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.018000] Calibrating delay using timer specific routine.. 6126.17 BogoMIPS (lpj=3063088)
[4294668.018000] Security Framework v1.0.0 initialized
[4294668.018000] SELinux:  Disabled at boot.
[4294668.018000] Mount-cache hash table entries: 512
[4294668.018000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000000
[4294668.018000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000651d 00000000 00000000
[4294668.018000] monitor/mwait feature present.
[4294668.018000] using mwait in idle threads.
[4294668.018000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294668.018000] CPU: L2 cache: 1024K
[4294668.018000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000080 0000651d 00000000 00000000
[4294668.018000] mtrr: v2.0 (20020519)
[4294668.018000] CPU: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 01
[4294668.018000] Enabling fast FPU save and restore... done.
[4294668.018000] Enabling unmasked SIMD FPU exception support... done.
[4294668.018000] Checking 'hlt' instruction... OK.
[4294668.022000] checking if image is initramfs... it is
[4294668.570000] Freeing initrd memory: 6837k freed
[4294668.579000] ACPI: Looking for DSDT ... not found!
[4294668.582000] ENABLING IO-APIC IRQs
[4294668.582000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[4294668.582000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[4294668.582000] ...trying to set up timer (IRQ0) through the 8259A ...  failed.[4294668.582000] ...trying to set up timer as Virtual Wire IRQ... failed.
[4294668.593000] ...trying to set up timer as ExtINT IRQ... works.
[4294668.818000] NET: Registered protocol family 16
[4294668.818000] EISA bus registered
[4294668.818000] ACPI: bus type pci registered
[4294668.818000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=7
[4294668.818000] PCI: Using MMCONFIG
[4294668.820000] ACPI: Subsystem revision 20051216
[4294668.831000] ACPI: Interpreter enabled
[4294668.831000] ACPI: Using IOAPIC for interrupt routing
[4294668.832000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.832000] PCI: Probing PCI hardware (bus 00)
[4294668.838000] PCI quirk: region 4000-403f claimed by ali7101 ACPI
[4294668.839000] Boot video device is 0000:01:05.0
[4294668.840000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.855000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[4294668.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[4294668.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[4294668.856000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[4294668.857000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[4294668.857000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[4294668.857000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE2P._PRT]
[4294668.870000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
[4294668.871000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294668.871000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294668.871000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.872000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.872000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.872000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.874000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.874000] ACPI: PCI Interrupt Link [LNKP] (IRQs *3 4 5 6 7 10 11 12 14 15)
[4294668.874000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.874000] pnp: PnP ACPI init
[4294668.883000] pnp: PnP ACPI: found 14 devices
[4294668.883000] PnPBIOS: Disabled by ACPI PNP
[4294668.883000] PCI: Using ACPI for IRQ routing
[4294668.883000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.883000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[4294668.908000] pnp: 00:09: ioport range 0xa00-0xa0f has been reserved
[4294668.908000] pnp: 00:09: ioport range 0xa10-0xa1f has been reserved
[4294668.908000] pnp: 00:09: ioport range 0xa20-0xa2f has been reserved
[4294668.908000] pnp: 00:09: ioport range 0xa30-0xa3f has been reserved
[4294668.908000] PCI: Bridge: 0000:00:01.0
[4294668.908000]   IO window: b000-bfff
[4294668.908000]   MEM window: ff400000-ff4fffff
[4294668.908000]   PREFETCH window: bff00000-dfefffff
[4294668.908000] PCI: Bridge: 0000:00:02.0
[4294668.908000]   IO window: disabled.
[4294668.908000]   MEM window: disabled.
[4294668.908000]   PREFETCH window: disabled.
[4294668.908000] PCI: Bridge: 0000:00:04.0
[4294668.908000]   IO window: disabled.
[4294668.908000]   MEM window: disabled.
[4294668.908000]   PREFETCH window: disabled.
[4294668.908000] PCI: Bridge: 0000:00:05.0
[4294668.908000]   IO window: disabled.
[4294668.908000]   MEM window: disabled.
[4294668.908000]   PREFETCH window: disabled.
[4294668.908000] PCI: Bridge: 0000:00:06.0
[4294668.908000]   IO window: disabled.
[4294668.908000]   MEM window: disabled.
[4294668.908000]   PREFETCH window: disabled.
[4294668.908000] PCI: Bridge: 0000:00:07.0
[4294668.908000]   IO window: disabled.
[4294668.908000]   MEM window: disabled.
[4294668.908000]   PREFETCH window: disabled.
[4294668.908000] PCI: Bridge: 0000:00:19.0
[4294668.908000]   IO window: c000-cfff
[4294668.908000]   MEM window: ff500000-ff5fffff
[4294668.908000]   PREFETCH window: disabled.
[4294668.908000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294668.908000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294668.908000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[4294668.908000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294668.908000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[4294668.908000] PCI: Setting latency timer of device 0000:00:19.0 to 64
[4294668.909000] audit: initializing netlink socket (disabled)
[4294668.909000] audit(1154947490.908:1): initialized
[4294668.909000] VFS: Disk quotas dquot_6.5.1
[4294668.909000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.909000] Initializing Cryptographic API
[4294668.909000] io scheduler noop registered
[4294668.909000] io scheduler anticipatory registered
[4294668.909000] io scheduler deadline registered
[4294668.909000] io scheduler cfq registered
[4294674.409000] 0000:00:1c.3 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[4294674.409000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294674.409000] pcie_portdrv_probe->Dev[5a34:1002] has invalid IRQ. Check vendor BIOS
[4294674.409000] assign_interrupt_mode Found MSI capability
[4294674.409000] Allocate Port Service[pcie00]
[4294674.409000] Allocate Port Service[pcie01]
[4294674.409000] Allocate Port Service[pcie03]
[4294674.409000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[4294674.409000] pcie_portdrv_probe->Dev[5a36:1002] has invalid IRQ. Check vendor BIOS
[4294674.409000] assign_interrupt_mode Found MSI capability
[4294674.409000] Allocate Port Service[pcie00]
[4294674.409000] Allocate Port Service[pcie01]
[4294674.409000] Allocate Port Service[pcie03]
[4294674.409000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[4294674.409000] pcie_portdrv_probe->Dev[5a37:1002] has invalid IRQ. Check vendor BIOS
[4294674.409000] assign_interrupt_mode Found MSI capability
[4294674.409000] Allocate Port Service[pcie00]
[4294674.409000] Allocate Port Service[pcie01]
[4294674.409000] Allocate Port Service[pcie03]
[4294674.409000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[4294674.409000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
[4294674.409000] assign_interrupt_mode Found MSI capability
[4294674.409000] Allocate Port Service[pcie00]
[4294674.409000] Allocate Port Service[pcie01]
[4294674.409000] Allocate Port Service[pcie03]
[4294674.409000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[4294674.409000] pcie_portdrv_probe->Dev[5a39:1002] has invalid IRQ. Check vendor BIOS
[4294674.409000] assign_interrupt_mode Found MSI capability
[4294674.409000] Allocate Port Service[pcie00]
[4294674.409000] Allocate Port Service[pcie01]
[4294674.409000] Allocate Port Service[pcie03]
[4294674.410000] isapnp: Scanning for PnP cards...
[4294674.775000] isapnp: No Plug & Play device found
[4294674.793000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[4294674.793000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[4294674.795000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294674.795000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294674.795000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294674.795000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294674.798000] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294674.798000] 00:06: ttyS0 at I/O 0x3f8 (irq = 0) is a 16550A
[4294674.798000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294674.798000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294674.798000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294674.799000] mice: PS/2 mouse device common for all mice
[4294674.799000] EISA: Probing bus 0 at eisa.0
[4294674.799000] Cannot allocate resource for EISA slot 4
[4294674.799000] EISA: Detected 0 cards.
[4294674.799000] NET: Registered protocol family 2
[4294674.808000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294674.808000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[4294674.808000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294674.808000] TCP: Hash tables configured (established 131072 bind 65536)
[4294674.808000] TCP reno registered
[4294674.809000] TCP bic registered
[4294674.809000] NET: Registered protocol family 1
[4294674.809000] NET: Registered protocol family 8
[4294674.809000] NET: Registered protocol family 20
[4294674.809000] Using IPI Shortcut mode
[4294674.809000] ACPI wakeup devices:
[4294674.809000] PCE2 PCE3 PCE4 PCE5 PCE6 PCE7 PE2P SLT9 SLTA SLTD SLTE  LAN USB0 USB1 USB2 UB20 AC97 MC97 AZAL
[4294674.809000] ACPI: (supports S0 S1 S3 S4 S5)
[4294674.809000] Freeing unused kernel memory: 288k freed
[4294674.851000] vga16fb: initializing
[4294674.851000] vga16fb: mapped to 0xc00a0000
[4294674.953000] Console: switching to colour frame buffer device 80x25
[4294674.953000] fb0: VGA16 VGA frame buffer device
[4294674.992000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294676.018000] Capability LSM initialized
[4294676.154000] ACPI: Processor [CPU1] (supports 8 throttling states)
[4294676.593000] ALI15X3: IDE controller at PCI slot 0000:00:1f.0
[4294676.593000] ACPI: PCI Interrupt 0000:00:1f.0[A] -> GSI 21 (level, low) -> IRQ 225
[4294676.593000] ALI15X3: chipset revision 199
[4294676.593000] ALI15X3: not 100% native mode: will probe irqs later
[4294676.593000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[4294676.593000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:pio, hdd:pio
[4294676.593000] Probing IDE interface ide0...
[4294677.265000] hda: SAMSUNG CD-R/RW DRIVE SW-224B, ATAPI CD/DVD-ROM drive
[4294677.979000] hdb: HL-DT-ST RW/DVD GCC-4522B, ATAPI CD/DVD-ROM drive
[4294678.030000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294678.048000] Probing IDE interface ide1...
[4294678.579000] hda: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[4294678.579000] Uniform CD-ROM driver Revision: 3.20
[4294678.581000] hdb: ATAPI 40X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[4294678.628000] SCSI subsystem initialized
[4294678.630000] ACPI: bus type scsi registered
[4294678.630000] libata version 1.20 loaded.
[4294678.631000] sata_uli 0000:00:1f.1: version 0.5
[4294678.631000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 21 (level, low) -> IRQ 225
[4294678.631000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 225
[4294678.631000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 225
[4294678.631000] ata3: SATA max UDMA/133 cmd 0xEC08 ctl 0xE806 bmdma 0xDC10 irq 225
[4294678.631000] ata4: SATA max UDMA/133 cmd 0xE408 ctl 0xE006 bmdma 0xDC18 irq 225
[4294678.836000] ata1: dev 0 cfg 00:427a 49:2f00 82:7469 83:7f01 84:4023 85:7469 86:3c01 87:4023 88:407f 93:0000
[4294678.836000] ata1: dev 0 ATA-7, max UDMA/133, 156301488 sectors: LBA48
[4294678.837000] sata_get_dev_handle: SATA dev addr=0x1f0001, handle=0xdffe7f80
[4294678.846000] ata1: dev 0 configured for UDMA/133
[4294678.847000] sata_get_dev_handle: SATA dev addr=0x1f0001, handle=0xdffe7f80
[4294678.856000] scsi0 : sata_uli
[4294679.059000] ata2: no device found (phy stat 00000000)
[4294679.059000] scsi1 : sata_uli
[4294679.261000] ata3: no device found (phy stat 00000000)
[4294679.261000] scsi2 : sata_uli
[4294679.463000] ata4: no device found (phy stat 00000000)
[4294679.463000] scsi3 : sata_uli
[4294679.463000]   Vendor: ATA       Model: WDC WD800JD-22LS  Rev: 06.0
[4294679.463000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294679.469000] Driver 'sd' needs updating - please use bus_type methods
[4294679.469000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294679.470000] SCSI device sda: drive cache: write back
[4294679.472000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294679.472000] SCSI device sda: drive cache: write back
[4294679.472000]  sda: sda1 sda2 < sda5 >
[4294679.520000] sd 0:0:0:0: Attached scsi disk sda
[4294679.767000] usbcore: registered new driver usbfs
[4294679.767000] usbcore: registered new driver hub
[4294679.769000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294679.770000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 233
[4294679.770000] ohci_hcd 0000:00:1c.0: OHCI Host Controller
[4294680.227000] ieee1394: Initialized config rom entry `ip1394'
[4294680.238000] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 1
[4294680.238000] ohci_hcd 0000:00:1c.0: irq 233, io mem 0xff6ff000
[4294680.291000] hub 1-0:1.0: USB hub found
[4294680.291000] hub 1-0:1.0: 3 ports detected
[4294680.392000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 18 (level, low) -> IRQ 50
[4294680.392000] ohci_hcd 0000:00:1c.1: OHCI Host Controller
[4294680.414000] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 2
[4294680.414000] ohci_hcd 0000:00:1c.1: irq 50, io mem 0xff6fe000
[4294680.467000] hub 2-0:1.0: USB hub found
[4294680.467000] hub 2-0:1.0: 3 ports detected
[4294680.568000] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 19 (level, low) -> IRQ 58
[4294680.568000] ohci_hcd 0000:00:1c.2: OHCI Host Controller
[4294680.590000] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus number 3
[4294680.590000] ohci_hcd 0000:00:1c.2: irq 58, io mem 0xff6fd000
[4294680.643000] hub 3-0:1.0: USB hub found
[4294680.643000] hub 3-0:1.0: 3 ports detected
[4294680.745000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294680.745000] ACPI: PCI Interrupt 0000:07:16.0[A] -> GSI 23 (level, low) -> IRQ 66
[4294680.745000] PCI: Via IRQ fixup for 0000:07:16.0, from 5 to 2
[4294680.747000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 66
[4294680.747000] ehci_hcd 0000:00:1c.3: EHCI Host Controller
[4294680.747000] ehci_hcd 0000:00:1c.3: debug port 1
[4294680.747000] PCI: cache line size of 128 is not supported by device 0000:00:1c.3
[4294680.785000] usb 2-2: new low speed USB device using ohci_hcd and address 2
[4294680.787000] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 4
[4294680.787000] ehci_hcd 0000:00:1c.3: irq 66, io mem 0xff6fcc00
[4294680.787000] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294680.787000] hub 4-0:1.0: USB hub found
[4294680.787000] hub 4-0:1.0: 8 ports detected
[4294680.799000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[66]  MMIO=[ff53b800-ff53bfff]  Max Packet=[2048]
[4294680.905000] Probing IDE interface ide1...
[4294681.447000] Attempting manual resume
[4294681.460000] kjournald starting.  Commit interval 5 seconds
[4294681.460000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.583000] usb 2-2: new low speed USB device using ohci_hcd and address 3
[4294681.948000] usb 3-2: new full speed USB device using ohci_hcd and address 2[4294682.062000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff32caef][4294689.153000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294690.302000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294690.305000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294690.360000] Linux agpgart interface v0.101 (c) Dave Jones
[4294690.374000] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[4294690.374000] ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not inserted.
[4294690.381000] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
[4294690.381000] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
[4294690.487000] input: PC Speaker as /class/input/input1
[4294690.507000] ACPI: PCI Interrupt 0000:00:1d.0[C] -> GSI 22 (level, low) -> IRQ 74
[4294690.525000] Real Time Clock Driver v1.12
[4294690.593000] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[4294691.039000] Floppy drive(s): fd0 is 1.44M
[4294691.075000] parport: PnPBIOS parport detected.
[4294691.075000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294691.105000] FDC 0 is a post-1991 82077
[4294691.173000] ACPI: PCI Interrupt 0000:07:15.0[A] -> GSI 20 (level, low) -> IRQ 82
[4294691.173000] skge 1.3 addr 0xff53c000 irq 82 chip Yukon-Lite rev 9
[4294691.174000] skge eth0: addr 00:14:2a:17:41:46
[4294691.189000] Linux video capture interface: v1.00
[4294691.227000] Initializing USB Mass Storage driver...
[4294691.227000] scsi4 : SCSI emulation for USB Mass Storage devices
[4294691.227000] usb-storage: device found at 2
[4294691.227000] usb-storage: waiting for device to settle before scanning
[4294691.227000] usbcore: registered new driver usb-storage
[4294691.227000] USB Mass Storage support registered.
[4294691.239000] usbcore: registered new driver hiddev
[4294691.250000] input: Logitech Optical USB Mouse as /class/input/input2
[4294691.250000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1c.1-2
[4294691.250000] usbcore: registered new driver usbhid
[4294691.250000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294691.313000] ACPI: PCI Interrupt 0000:07:12.0[A] -> GSI 22 (level, low) -> IRQ 74
[4294691.347000] saa7134: Unknown parameter `mixer_nr'
[4294691.936000] ts: Compaq touchscreen protocol output
[4294692.196000] skge eth0: enabling interface
[4294692.337000] lp0: using parport0 (interrupt-driven).
[4294692.360000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294692.360000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)[4294692.360000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294692.410000] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
[4294692.562000] EXT3 FS on sda1, internal journal
[4294692.706000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294692.706000] md: bitmap version 4.39
[4294693.153000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294693.465000] NET: Registered protocol family 17
[4294694.738000] cdrom: open failed.
[4294694.786000] cdrom: hdb: mrw address space DMA selected
[4294695.186000] skge eth0: Link is up at 100 Mbps, full duplex, flow control tx and rx
[4294696.235000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[4294696.235000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294696.304000] sd 4:0:0:0: Attached scsi removable disk sdb
[4294696.304000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[4294696.311000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[4294696.311000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294696.380000] sd 4:0:0:1: Attached scsi removable disk sdc
[4294696.380000] sd 4:0:0:1: Attached scsi generic sg2 type 0
[4294696.387000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[4294696.387000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294696.456000] sd 4:0:0:2: Attached scsi removable disk sdd
[4294696.456000] sd 4:0:0:2: Attached scsi generic sg3 type 0
[4294696.463000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[4294696.463000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294696.532000] sd 4:0:0:3: Attached scsi removable disk sde
[4294696.532000] sd 4:0:0:3: Attached scsi generic sg4 type 0
[4294696.532000] usb-storage: device scan complete
[4294696.850000] NET: Registered protocol family 10
[4294696.851000] lo: Disabled Privacy Extensions
[4294696.851000] IPv6 over IPv4 tunneling driver
[4294700.720000] ACPI: Power Button (FF) [PWRF]
[4294700.720000] ACPI: Power Button (CM) [PWRB]
[4294700.812000] ibm_acpi: ec object not found
[4294700.831000] pcc_acpi: loading...
[4294704.006000] [drm] Initialized drm 1.0.1 20051102
[4294704.773000] ppdev: user-space parallel port driver
[4294705.099000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294705.099000] apm: overridden by ACPI.
[4294706.999000] eth0: no IPv6 routers present
[4294708.462000] Bluetooth: Core ver 2.8
[4294708.462000] NET: Registered protocol family 31
[4294708.462000] Bluetooth: HCI device and connection manager initialized
[4294708.463000] Bluetooth: HCI socket layer initialized
[4294708.532000] Bluetooth: L2CAP ver 2.8
[4294708.532000] Bluetooth: L2CAP socket layer initialized
[4294708.554000] Bluetooth: RFCOMM socket layer initialized
[4294708.554000] Bluetooth: RFCOMM TTY layer initialized
[4294708.554000] Bluetooth: RFCOMM ver 1.7
[4294726.115000] cdrom: hdb: mrw address space DMA selected
[4294726.281000] cdrom: hdb: mrw address space DMA selected
[4294726.435000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4294726.522000] ISO 9660 Extensions: RRIP_1991A
[4294908.861000] saa7134: Unknown parameter `mixer_nr'
[4294923.629000] saa7134: Unknown parameter `mixer_nr'
[4294923.712000] saa7134_alsa: Unknown symbol saa_dsp_writel
[4294923.712000] saa7134_alsa: Unknown symbol saa7134_devlist
[4294923.712000] saa7134_alsa: Unknown symbol saa7134_pgtable_alloc
[4294923.712000] saa7134_alsa: Unknown symbol saa7134_pgtable_build
[4294923.713000] saa7134_alsa: Unknown symbol saa7134_pgtable_free
[4294923.713000] saa7134_alsa: Unknown symbol dmasound_exit
[4294923.713000] saa7134_alsa: Unknown symbol dmasound_init
[4294923.713000] saa7134_alsa: Unknown symbol saa7134_set_dmabits

```

lspci-x 
```
lhds@lhds-desktop:~$ lspci -X
PCI:0:0:0 Host bridge: ATI Technologies Inc: Unknown device 5a33
PCI:0:1:0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
PCI:0:2:0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
PCI:0:4:0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
PCI:0:5:0 PCI bridge: ATI Technologies Inc: Unknown device 5a37
PCI:0:6:0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
PCI:0:7:0 PCI bridge: ATI Technologies Inc: Unknown device 5a39
PCI:0:25:0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
PCI:0:28:0 USB Controller: ALi Corporation USB 1.1 Controller
PCI:0:28:1 USB Controller: ALi Corporation USB 1.1 Controller
PCI:0:28:2 USB Controller: ALi Corporation USB 1.1 Controller
PCI:0:28:3 USB Controller: ALi Corporation USB 2.0 Controller
PCI:0:29:0 0403: ALi Corporation High Definition Audio/AC'97 Host Controller
PCI:0:30:0 ISA bridge: ALi Corporation PCI to LPC Controller
PCI:0:30:1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
PCI:0:31:0 IDE interface: ALi Corporation M5229 IDE
PCI:0:31:1 RAID bus controller: ALi Corporation ULi 5287 SATA
PCI:1:5:0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a61
PCI:7:17:0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder
PCI:7:18:0 Multimedia audio controller: C-Media Electronics Inc CM8738
PCI:7:21:0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller
PCI:7:22:0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller

```

please get me out of this... i went to bios .. turned off apci pc freezed on ubuntu startup turned it back on ... did not solve the problem 
reverted to factory settings still ....
whats wrong?
when i modprobe my tv card it works but than when i insert the modules 
in /etc/modules and etc/modprobe.conf/options ... saa in dmsg disapears
i load the module again ...
```
 sudo modprobe saa7134
FATAL: Error inserting saa7134 (/lib/modules/2.6.15-23-386/kernel/drivers/media/video/saa7134/saa7134.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for saa7134

```
used to work when i last inserted them in the config files in /etc aswell........

---

### Post by lhds on 2006-08-07
come on guys ... what am i supposed to do here? i am getting nervous

---

### Post by jaimz on 2006-08-07
well I'm still a linux noob
since I've only been on ubuntu for the past month or two

but I remember at first I used to get those acpi problems
so I tried this when installing and it worked (when you have to press f6 for more options or whatever)

> irq poll=noacpi noapic nolapic acpi=offand I never got an acpi problem again

edit - +I use the alt cd, Idk if you're using hte desktop one or not, but the alt cd is better imo, takes you straight to the install.

---

### Post by lhds on 2006-08-08
well thats what i did and acpi were off aswell as my motherboad's sound card . but no problem as long as i have another one hooked in a pci slot. 
but i have my tv card hooked. and it cannot read in the dmesg ... 
thats my problem .... and still when i try to modbrobe the card it gets me the error .. fatal error....

what to do ?

---

### Post by lhds on 2006-08-08
do you advise me to install the latest kernel so that i might fix the acpi problems?

---

### Post by tseliot on 2006-08-08
> **lhds said:**
> hello .... ive installed it ... and it was working fine.... 
made a reinstall because of a disk failure ... on the same disk wich is working fine ... i got a surprise ... when kernel starts it throws biosbug timer not connected to io.apci 
That error does not prevent your system from working properly.

Or is it causing any problem?

---

### Post by lhds on 2006-08-08
no its working fine i am loading it ...
but you know i have a acpi problem and dmesg cannot read my tv card
and who doesnt like to have a fully working os that runs its damn pci cards !!!!;) ;)  well thats why i am strugglin to make it work. 
now i have downloaded with synaptic  linux source and i made make menuconfig.
inside there were some switches i had toturn on concerning acpi and the saa7134 module was not marked. i did mark it 
i think that this is where i have to fix things to make it work.

but when i am copiling i get an error i have to fix....
i have entred this command : 
sudo make-kpkg  --append-to-version=2.6.15-26-386 kernel_image kernel_headers
following [http://ubuntuforums.org/archive/index.php/t-24853.html](http://ubuntuforums.org/archive/index.php/t-24853.html) 


```
drivers/net/wireless/airo.c:94:2: warning: #warning MIC support requires Crypto API
drivers/net/wireless/airo.c: In function ‘flashcard’:
drivers/net/wireless/airo.c:7458: warning: implicit declaration of function ‘flashpchar’
drivers/net/wireless/airo.c: At top level:
drivers/net/wireless/airo.c:7538: error: static declaration of ‘flashpchar’ follows non-static declaration
drivers/net/wireless/airo.c:7458: error: previous implicit declaration of ‘flashpchar’ was here
make[4]: *** [drivers/net/wireless/airo.o] Error 1
make[3]: *** [drivers/net/wireless] Error 2
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [stamp-build] Error 2

```

what's up how to fix that .... after i fix this i have a feeling that everything will work fine ...

ps: ubuntu is the best distro so far ... i thank you and your team for this amaizing :-({|=

---

### Post by lhds on 2006-08-08
i have read that its important to make-kpkg clean before recompiling in ubuntuforums. well that is what i did but still i get the same error.
i am about to install the new linux kernel from kernel.org. 2.6.17.7
it seems that they have solved the cpu timer problem in the .17.x version

---

### Post by tseliot on 2006-08-08
> **lhds said:**
> i have read that its important to make-kpkg clean before recompiling in ubuntuforums. well that is what i did but still i get the same error.
i am about to install the new linux kernel from kernel.org. 2.6.17.7
it seems that they have solved the cpu timer problem in the .17.x version

If I'm not wrong they solved the problem because the timer is disabled by default.

Anyhow I doubt that solving that *problem* would help you with your tv card. You need a driver for that.

---

### Post by lhds on 2006-08-08
i have downloaded the linux kernel 2.6.17.7 from kernel.org 
went for install and it throwed after the compile :

make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2
[stamp-build] Error 2
when i first installed ubuntu i didnt have anything under /usr/src
in the install doc [http://www.ubuntuforums.org/showthread.php?t=217657&highlight=2.6.17](http://www.ubuntuforums.org/showthread.php?t=217657&highlight=2.6.17)

they speak about a linux folder i have to link to but i dont have but the headers of 2.6.15

/usr/src# ls
linux-2.6.17.7          linux-headers-2.6.15-26      linux-source-2.6.15
linux-2.6.17.7.tar.bz2  linux-headers-2.6.15-26-386  linux-source-2.6.15.tar

i have clearly entered make-kpkg clean
before i compile : make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image
and still got that [stamp-build] Error 2

i need suggestions please

---

### Post by lhds on 2006-08-09
its ok its allright . 
did a kernel compile with the acpi elements enabled 
and the saa7134 module loaded aswell .  
followed this 
and everything worked fine .... and i am set . thanx alot

---

