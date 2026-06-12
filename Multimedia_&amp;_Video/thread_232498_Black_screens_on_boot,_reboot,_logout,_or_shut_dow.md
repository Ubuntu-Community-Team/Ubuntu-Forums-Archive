---
title: "Black screens on boot, reboot, logout, or shut down"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by Kalinda on 2006-08-08
After a clean install of Dapper (never isntalled before on Dad's compy), rebooting/logout/shutdown took me to a blank screen and the monitor went into sleep mode.

The video card is an ATI All-in-Wonder Radeon 8500, but Kubuntu has it as an "ATI Radeon (fglrx)". Changing it to ATI All-in-Wonder did not help.

On boot, I got a "MP-BIOS bug: 8254 timer not connected to IO-APIC"

I used [this post]("http://ubuntuforums.org/showpost.php?p=1145317&postcount=3") to fix it. I was able to reboot once without issue and then everything got a lot worse.

Now I can't even boot up half the time, it just goes to a blank screen after GRUB. I have to hope and pray that it will boot, because sometimes it works and sometimes it doesn't.

Here is my dmesg:
```

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 262064
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32688 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000face0
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x09000423 MSFT 0x00000097) @ 0x3ffb0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x09000423 MSFT 0x00000097) @ 0x3ffb0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000423 MSFT 0x00000097) @ 0x3ffb0390
[17179569.184000] ACPI: OEMB (v001 A M I  OEMBIOS  0x09000423 MSFT 0x00000097) @ 0x3ffc0040
[17179569.184000] ACPI: DSDT (v001  A0094 A0094038 0x00000038 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:3 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 15:3 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[17179569.184000] Using ACPI for processor (LAPIC) configuration information
[17179569.184000] Intel MultiProcessor Specification v1.4
[17179569.184000]     Virtual Wire compatibility mode.
[17179569.184000] OEM ID: ASUSTeK  Product ID:  APIC at: 0xFEE00000
[17179569.184000] I/O APIC #2 Version 32 at 0xFEC00000.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Processors: 1
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash noapic
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3199.261 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.600000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.600000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.620000] Memory: 1028564k/1048256k available (1976k kernel code, 18928k reserved, 606k data, 288k init, 130752k highmem)
[17179571.620000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.700000] Calibrating delay using timer specific routine.. 6403.04 BogoMIPS (lpj=12806095)
[17179571.700000] Security Framework v1.0.0 initialized
[17179571.700000] SELinux:  Disabled at boot.
[17179571.700000] Mount-cache hash table entries: 512
[17179571.700000] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179571.700000] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000
[17179571.700000] monitor/mwait feature present.
[17179571.700000] using mwait in idle threads.
[17179571.700000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[17179571.700000] CPU: L2 cache: 1024K
[17179571.700000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 0000441d 00000000 00000000
[17179571.700000] mtrr: v2.0 (20020519)
[17179571.700000] CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 04
[17179571.700000] Enabling fast FPU save and restore... done.
[17179571.700000] Enabling unmasked SIMD FPU exception support... done.
[17179571.700000] Checking 'hlt' instruction... OK.
[17179571.716000] checking if image is initramfs... it is
[17179572.192000] Freeing initrd memory: 6614k freed
[17179572.196000] ACPI: Looking for DSDT ... not found!
[17179572.196000] ACPI: setting ELCR to 0200 (from 0820)
[17179572.312000] NET: Registered protocol family 16
[17179572.312000] EISA bus registered
[17179572.312000] ACPI: bus type pci registered
[17179572.312000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[17179572.312000] PCI: Using configuration type 1
[17179572.312000] ACPI: Subsystem revision 20051216
[17179572.324000] ACPI: Interpreter enabled
[17179572.324000] ACPI: Using PIC for interrupt routing
[17179572.324000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.324000] PCI: Probing PCI hardware (bus 00)
[17179572.328000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179572.328000] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[17179572.328000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.328000] Boot video device is 0000:01:00.0
[17179572.328000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.336000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[17179572.344000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.344000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.344000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.344000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.344000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.344000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.344000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.344000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.344000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.344000] pnp: PnP ACPI init
[17179572.352000] pnp: PnP ACPI: found 16 devices
[17179572.352000] PnPBIOS: Disabled by ACPI PNP
[17179572.352000] PCI: Using ACPI for IRQ routing
[17179572.352000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.364000] pnp: 00:09: ioport range 0x290-0x297 has been reserved
[17179572.364000] PCI: Bridge: 0000:01:00.1
[17179572.364000]   IO window: d000-dfff
[17179572.364000]   MEM window: fbe00000-fbefffff
[17179572.364000]   PREFETCH window: disabled.
[17179572.364000] PCI: Bridge: 0000:00:01.0
[17179572.364000]   IO window: c000-dfff
[17179572.364000]   MEM window: fbd00000-fbefffff
[17179572.364000]   PREFETCH window: f0000000-faffffff
[17179572.364000] PCI: Bridge: 0000:00:1e.0
[17179572.364000]   IO window: e000-efff
[17179572.364000]   MEM window: fbf00000-fbffffff
[17179572.364000]   PREFETCH window: 50000000-500fffff
[17179572.364000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.364000] audit: initializing netlink socket (disabled)
[17179572.364000] audit(1155064902.364:1): initialized
[17179572.364000] highmem bounce pool size: 64 pages
[17179572.364000] VFS: Disk quotas dquot_6.5.1
[17179572.364000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.364000] Initializing Cryptographic API
[17179572.364000] io scheduler noop registered
[17179572.364000] io scheduler anticipatory registered
[17179572.364000] io scheduler deadline registered
[17179572.364000] io scheduler cfq registered
[17179572.364000] isapnp: Scanning for PnP cards...
[17179575.512000] isapnp: No Plug & Play device found
[17179575.528000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179575.528000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179575.532000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179575.532000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179575.532000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179575.532000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.532000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.532000] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.532000] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.536000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179575.536000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179575.536000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179575.536000] mice: PS/2 mouse device common for all mice
[17179575.536000] EISA: Probing bus 0 at eisa.0
[17179575.536000] EISA: Detected 0 cards.
[17179575.536000] NET: Registered protocol family 2
[17179575.572000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179575.572000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179575.572000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179575.572000] TCP: Hash tables configured (established 262144 bind 65536)
[17179575.572000] TCP reno registered
[17179575.572000] TCP bic registered
[17179575.572000] NET: Registered protocol family 1
[17179575.572000] NET: Registered protocol family 8
[17179575.572000] NET: Registered protocol family 20
[17179575.572000] Using IPI Shortcut mode
[17179575.572000] ACPI wakeup devices: 
[17179575.572000] P0P4 MC97 USB1 USB2 USB3 USB4 EUSB PS2K ILAN PWRB 
[17179575.572000] ACPI: (supports S0 S1 S3 S4 S5)
[17179575.572000] Freeing unused kernel memory: 288k freed
[17179575.584000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.612000] vga16fb: initializing
[17179575.612000] vga16fb: mapped to 0xc00a0000
[17179575.752000] Console: switching to colour frame buffer device 80x25
[17179575.752000] fb0: VGA16 VGA frame buffer device
[17179576.860000] Capability LSM initialized
[17179577.368000] ICH5: IDE controller at PCI slot 0000:00:1f.1
[17179577.368000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179577.368000] **** SET: Misaligned resource pointer: df82d0c2 Type 07 Len 0
[17179577.368000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179577.368000] PCI: setting IRQ 11 as level-triggered
[17179577.368000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179577.368000] ICH5: chipset revision 2
[17179577.368000] ICH5: not 100% native mode: will probe irqs later
[17179577.368000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[17179577.368000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[17179577.368000] Probing IDE interface ide0...
[17179578.104000] hda: PIONEER DVD-RW DVR-108, ATAPI CD/DVD-ROM drive
[17179578.776000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.776000] Probing IDE interface ide1...
[17179579.356000] hda: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[17179579.356000] Uniform CD-ROM driver Revision: 3.20
[17179579.416000] SCSI subsystem initialized
[17179579.416000] ACPI: bus type scsi registered
[17179579.416000] libata version 1.20 loaded.
[17179579.416000] ata_piix 0000:00:1f.2: version 1.05
[17179579.416000] ata_pci_init_one: pci_dev class+intf: 0x1018f
[17179579.416000] ata_pci_init_one: NO_LEGACY == 0
[17179579.416000] ACPI: PCI Interrupt 0000:00:1f.2[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179579.416000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179579.416000] ata1: PATA max UDMA/133 cmd 0xAC00 ctl 0xA882 bmdma 0xA400 irq 11
[17179579.416000] ata2: PATA max UDMA/133 cmd 0xA800 ctl 0xA482 bmdma 0xA408 irq 11
[17179579.580000] ata1: dev 0 cfg 00:0c5a 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:207f 93:0000
[17179579.580000] ata1: dev 0 ATA-6, max UDMA/133, 156301488 sectors: LBA48
[17179579.580000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffea7e0
[17179579.584000] ata1: dev 0 configured for UDMA/133
[17179579.584000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffea7e0
[17179579.592000] scsi0 : ata_piix
[17179579.756000] ata2: dev 0 cfg 00:0040 49:2f00 82:746b 83:7f01 84:4023 85:7469 86:3c01 87:4023 88:20ff 93:0000
[17179579.756000] ata2: dev 0 ATA-7, max UDMA7, 390721968 sectors: LBA48
[17179579.756000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffea7e0
[17179579.760000] ata2: dev 0 configured for UDMA/133
[17179579.760000] sata_get_dev_handle: SATA dev addr=0x1f0002, handle=0xdffea7e0
[17179579.768000] scsi1 : ata_piix
[17179579.768000]   Vendor: ATA       Model: ST380817AS        Rev: 3.42
[17179579.768000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179579.768000]   Vendor: ATA       Model: SAMSUNG SP2004C   Rev: VM10
[17179579.768000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179579.776000] Driver 'sd' needs updating - please use bus_type methods
[17179579.776000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179579.776000] SCSI device sda: drive cache: write back
[17179579.780000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179579.780000] SCSI device sda: drive cache: write back
[17179579.780000]  sda: sda1 sda2 sda3
[17179579.792000] sd 0:0:0:0: Attached scsi disk sda
[17179579.792000] SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
[17179579.796000] SCSI device sdb: drive cache: write back
[17179579.800000] SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
[17179579.804000] SCSI device sdb: drive cache: write back
[17179579.804000]  sdb: sdb1
[17179579.812000] sd 1:0:0:0: Attached scsi disk sdb
[17179580.028000] usbcore: registered new driver usbfs
[17179580.028000] usbcore: registered new driver hub
[17179580.028000] USB Universal Host Controller Interface driver v2.3
[17179580.028000] **** SET: Misaligned resource pointer: dfa47cc2 Type 07 Len 0
[17179580.028000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179580.028000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179580.028000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179580.028000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179580.032000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179580.032000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000b480
[17179580.032000] hub 1-0:1.0: USB hub found
[17179580.032000] hub 1-0:1.0: 2 ports detected
[17179580.096000] ieee1394: Initialized config rom entry `ip1394'
[17179580.136000] **** SET: Misaligned resource pointer: dfa477c2 Type 07 Len 0
[17179580.136000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179580.136000] PCI: setting IRQ 5 as level-triggered
[17179580.136000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179580.136000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179580.136000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179580.136000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179580.136000] uhci_hcd 0000:00:1d.1: irq 5, io base 0x0000b800
[17179580.136000] hub 2-0:1.0: USB hub found
[17179580.136000] hub 2-0:1.0: 2 ports detected
[17179580.240000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179580.240000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179580.240000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179580.240000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179580.240000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000b880
[17179580.240000] hub 3-0:1.0: USB hub found
[17179580.240000] hub 3-0:1.0: 2 ports detected
[17179580.344000] ACPI: PCI Interrupt 0000:00:1d.3[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179580.344000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179580.344000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179580.344000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179580.344000] uhci_hcd 0000:00:1d.3: irq 11, io base 0x0000bc00
[17179580.344000] hub 4-0:1.0: USB hub found
[17179580.344000] hub 4-0:1.0: 2 ports detected
[17179580.376000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179580.448000] **** SET: Misaligned resource pointer: dfaeae02 Type 07 Len 0
[17179580.448000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[17179580.448000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[17179580.448000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179580.448000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179580.448000] ehci_hcd 0000:00:1d.7: debug port 1
[17179580.448000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179580.448000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179580.448000] ehci_hcd 0000:00:1d.7: irq 5, io mem 0xfbcffc00
[17179580.452000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.452000] hub 5-0:1.0: USB hub found
[17179580.452000] hub 5-0:1.0: 8 ports detected
[17179580.556000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179580.556000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179580.556000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[17179580.608000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[fbeff000-fbeff7ff]  Max Packet=[2048]
[17179580.660000] Probing IDE interface ide1...
[17179580.900000] usb 1-1: device not accepting address 2, error -71
[17179581.252000] Attempting manual resume
[17179581.260000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179581.260000] EXT3-fs: write access will be enabled during recovery.
[17179581.452000] usb 5-1: new high speed USB device using ehci_hcd and address 2
[17179581.604000] Initializing USB Mass Storage driver...
[17179581.836000] usb 5-2: new high speed USB device using ehci_hcd and address 3
[17179581.888000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0006bb00160520d1]
[17179581.968000] hub 5-2:1.0: USB hub found
[17179581.968000] hub 5-2:1.0: 7 ports detected
[17179582.256000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179582.256000] usb-storage: device found at 2
[17179582.256000] usb-storage: waiting for device to settle before scanning
[17179582.256000] usbcore: registered new driver usb-storage
[17179582.256000] USB Mass Storage support registered.
[17179582.472000] usb 5-2.1: new low speed USB device using ehci_hcd and address 5
[17179582.576000] EXT3-fs: recovery complete.
[17179582.576000] kjournald starting.  Commit interval 5 seconds
[17179582.592000] EXT3-fs: mounted filesystem with ordered data mode.
[17179582.800000] usb 5-2.4: new low speed USB device using ehci_hcd and address 6
[17179583.152000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179587.256000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9139
[17179587.256000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179587.452000] SCSI device sdc: 503808 512-byte hdwr sectors (258 MB)
[17179587.452000] sdc: Write Protect is off
[17179587.452000] sdc: Mode Sense: 02 00 00 00
[17179587.452000] sdc: assuming drive cache: write through
[17179587.456000] SCSI device sdc: 503808 512-byte hdwr sectors (258 MB)
[17179587.460000] sdc: Write Protect is off
[17179587.460000] sdc: Mode Sense: 02 00 00 00
[17179587.460000] sdc: assuming drive cache: write through
[17179587.460000]  sdc: sdc1
[17179587.460000] sd 2:0:0:0: Attached scsi removable disk sdc
[17179587.460000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9139
[17179587.460000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179587.468000] sd 2:0:0:1: Attached scsi removable disk sdd
[17179587.468000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9139
[17179587.468000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179587.476000] sd 2:0:0:2: Attached scsi removable disk sde
[17179587.476000]   Vendor: Generic   Model: STORAGE DEVICE    Rev: 9139
[17179587.476000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179587.480000] sd 2:0:0:3: Attached scsi removable disk sdf
[17179587.480000] usb-storage: device scan complete
[17179589.856000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179589.856000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[17179589.856000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[17179589.856000] sd 2:0:0:1: Attached scsi generic sg3 type 0
[17179589.856000] sd 2:0:0:2: Attached scsi generic sg4 type 0
[17179589.856000] sd 2:0:0:3: Attached scsi generic sg5 type 0
[17179591.560000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.564000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.588000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.604000] hw_random hardware driver 1.0.0 loaded
[17179591.612000] Real Time Clock Driver v1.12
[17179591.644000] agpgart: Detected an Intel 865 Chipset.
[17179591.644000] agpgart: AGP aperture is 64M @ 0xec000000
[17179591.756000] input: PC Speaker as /class/input/input1
[17179591.836000] **** SET: Misaligned resource pointer: f782dbc2 Type 07 Len 0
[17179591.836000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179591.836000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179591.836000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179591.920000] Floppy drive(s): fd0 is 1.44M
[17179591.936000] FDC 0 is a post-1991 82077
[17179592.120000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x001B
[17179592.120000] usbcore: registered new driver usblp
[17179592.120000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179592.148000] parport: PnPBIOS parport detected.
[17179592.148000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179592.196000] AC'97 0 analog subsections not ready
[17179592.264000] intel8x0_measure_ac97_clock: measured 54860 usecs
[17179592.264000] intel8x0: clocking to 48000
[17179592.264000] **** SET: Misaligned resource pointer: f78266c2 Type 07 Len 0
[17179592.264000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[17179592.264000] ACPI: PCI Interrupt 0000:03:05.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[17179592.264000] skge 1.3 addr 0xfbffc000 irq 11 chip Yukon-Lite rev 7
[17179592.264000] skge eth0: addr 00:11:2f:c9:d4:a3
[17179592.416000] usbcore: registered new driver hiddev
[17179592.420000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[17179592.420000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-2.4
[17179592.420000] usbcore: registered new driver usbhid
[17179592.420000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.096000] ts: Compaq touchscreen protocol output
[17179593.560000] input: X10 Wireless Technology Inc USB Receiver as /class/input/input3
[17179593.560000] usbcore: registered new driver ati_remote
[17179593.560000] drivers/usb/input/ati_remote.c: Registered USB driver ATI/X10 RF USB Remote Control v. 2.2.1
[17179593.568000] drivers/usb/input/ati_remote.c: Weird data, len=1 ff 00 00 00 00 00 ...
[17179593.704000] skge eth0: enabling interface
[17179593.960000] lp0: using parport0 (interrupt-driven).
[17179593.988000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179593.988000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179593.988000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.040000] Adding 2104472k swap on /dev/sda1.  Priority:-1 extents:1 across:2104472k
[17179594.168000] EXT3 FS on sda2, internal journal
[17179594.280000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179594.280000] md: bitmap version 4.39
[17179594.852000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179594.932000] NET: Registered protocol family 17
[17179595.812000] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[17179596.272000] kjournald starting.  Commit interval 5 seconds
[17179596.272000] EXT3 FS on sda3, internal journal
[17179596.272000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.392000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179596.424000] NTFS volume version 3.1.
[17179598.728000] NET: Registered protocol family 10
[17179598.728000] lo: Disabled Privacy Extensions
[17179598.728000] IPv6 over IPv4 tunneling driver

```

My GRUB menu.list, with the fix applied from the link I gave above:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
default		0

## timeout sec
#timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

[snip: unimportant stuff]

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# **defoptions=quiet splash noapic**

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
[snip: more unimportant stuff; I think]

```

I suppose I should note that I also installed the modified ATI stuff for TV out with GATOS following [this guide]("http://ubuntuforums.org/showthread.php?t=215763") (it doesn't work, but that's for another thread). I backed up my drivers before doing it, though. Also the problem was there beforehand, but I figured it was worth mentioning anyway.

Changing my resolution also causes a lockup, which might be related to the new drivers, I don't know..

Anyway, I hope that helps. Thanks :)

---

### Post by computergroove on 2006-08-09
Can you successfully boot into the ubuntu desktop install screen everytime you try from your install cd? Try it like 10 times. If you can't boot successfully every time then you probally have some bad hardware (namely your video card, power supply, or main board). Post your results.

---

### Post by tseliot on 2006-08-10
Try the boot parameters in this guide:
[http://www.ubuntuforums.org/showthread.php?t=75281](http://www.ubuntuforums.org/showthread.php?t=75281)

look for the section which begins with:
```
OTHERWISE

b) If you have installed Ubuntu...
```

---

