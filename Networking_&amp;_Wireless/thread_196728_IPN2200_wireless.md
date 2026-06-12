---
title: "IPN2200 wireless"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by sagerion on 2006-06-14
Is it possible to get my IPN2200 to work with Ubuntu?  I don't even see the card listed in my dmesg.  I know it works and I do have it turned on.  I can see the bluetooh portion of my mini-pcmcia card in my dmesg:

```

[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000003bf40000 (usable)
[4294667.296000]  BIOS-e820: 000000003bf40000 - 000000003bf50000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000003bf50000 - 000000003c000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000003c000000 - 0000000040000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 63MB HIGHMEM available.
[4294667.296000] 896MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 245568
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 225280 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 16192 pages, LIFO batch:3
[4294667.296000] DMI 2.3 present.
[4294667.296000] ATI board detected. Disabling timer routing over 8254.
[4294667.296000] ACPI: RSDP (v000 MSI                                   ) @ 0x000f83d0
[4294667.296000] ACPI: RSDT (v001 MSI    1013     0x01092006 MSFT 0x00000097) @ 0x3bf40000
[4294667.296000] ACPI: FADT (v002 MSI    1013     0x01092006 MSFT 0x00000097) @ 0x3bf40200
[4294667.296000] ACPI: MADT (v001 MSI    OEMAPIC  0x01092006 MSFT 0x00000097) @ 0x3bf40300
[4294667.296000] ACPI: WDRT (v001 MSI    MSI_OEM  0x01092006 MSFT 0x00000097) @ 0x3bf40360
[4294667.296000] ACPI: MCFG (v001 MSI    OEMMCFG  0x01092006 MSFT 0x00000097) @ 0x3bf403b0
[4294667.296000] ACPI: SSDT (v001 OEM_ID OEMTBLID 0x00000001 INTL 0x02002026) @ 0x3bf43750
[4294667.296000] ACPI: OEMB (v001 MSI    MSI_OEM  0x01092006 MSFT 0x00000097) @ 0x3bf50040
[4294667.296000] ACPI: DSDT (v001    MSI     1013 0x01092006 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x4008
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:4 APIC version 16
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: BIOS IRQ0 pin2 override ignored.
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[4294667.296000] Detected 1592.486 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.402000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294668.402000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.423000] Memory: 963060k/982272k available (1976k kernel code, 18636k reserved, 606k data, 288k init, 64768k highmem)
[4294668.423000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.483000] Calibrating delay using timer specific routine.. 3187.33 BogoMIPS (lpj=1593667)
[4294668.483000] Security Framework v1.0.0 initialized
[4294668.483000] SELinux:  Disabled at boot.
[4294668.483000] Mount-cache hash table entries: 512
[4294668.483000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294668.483000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[4294668.483000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294668.483000] CPU: L2 Cache: 1024K (64 bytes/line)
[4294668.483000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000010 00000001 00000000 00000001
[4294668.483000] mtrr: v2.0 (20020519)
[4294668.483000] CPU: AMD Turion(tm) 64 Mobile Technology MT-30 stepping 02
[4294668.483000] Enabling fast FPU save and restore... done.
[4294668.483000] Enabling unmasked SIMD FPU exception support... done.
[4294668.483000] Checking 'hlt' instruction... OK.
[4294668.487000] checking if image is initramfs... it is
[4294669.124000] Freeing initrd memory: 6836k freed
[4294669.131000] ACPI: Looking for DSDT ... not found!
[4294669.133000] ENABLING IO-APIC IRQs
[4294669.133000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[4294669.244000] NET: Registered protocol family 16
[4294669.244000] EISA bus registered
[4294669.244000] ACPI: bus type pci registered
[4294669.244000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[4294669.244000] PCI: Using MMCONFIG
[4294669.245000] ACPI: Subsystem revision 20051216
[4294669.248000] ACPI: Interpreter enabled
[4294669.248000] ACPI: Using IOAPIC for interrupt routing
[4294669.249000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.249000] PCI: Probing PCI hardware (bus 00)
[4294669.250000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[4294669.250000] Boot video device is 0000:01:05.0
[4294669.251000] PCI: Transparent bridge - 0000:00:14.4
[4294669.251000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.258000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[4294669.258000] ACPI: Embedded Controller [EC] (gpe 6) interrupt mode.
[4294669.265000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP2._PRT]
[4294669.267000] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.267000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.267000] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.268000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.268000] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.268000] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.268000] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.268000] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 6 7 10 11 12 14 15) *0, disabled.
[4294669.269000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.269000] pnp: PnP ACPI init
[4294669.272000] pnp: PnP ACPI: found 10 devices
[4294669.272000] PnPBIOS: Disabled by ACPI PNP
[4294669.272000] PCI: Using ACPI for IRQ routing
[4294669.272000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.276000] PCI: Device 0000:02:03.0 not found by BIOS
[4294669.276000] PCI: Device 0000:02:04.0 not found by BIOS
[4294669.276000] PCI: Device 0000:02:04.1 not found by BIOS
[4294669.276000] PCI: Device 0000:02:04.2 not found by BIOS
[4294669.276000] PCI: Device 0000:02:09.0 not found by BIOS
[4294669.277000] PCI: Bridge: 0000:00:01.0
[4294669.277000]   IO window: d000-dfff
[4294669.277000]   MEM window: fbe00000-fbefffff
[4294669.277000]   PREFETCH window: f0000000-faffffff
[4294669.277000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[4294669.277000]   IO window: 0000e000-0000e0ff
[4294669.277000]   IO window: 0000ec00-0000ecff
[4294669.277000]   PREFETCH window: 50000000-51ffffff
[4294669.277000]   MEM window: 56000000-57ffffff
[4294669.277000] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[4294669.277000]   IO window: 00001000-000010ff
[4294669.277000]   IO window: 00001400-000014ff
[4294669.277000]   PREFETCH window: 52000000-53ffffff
[4294669.277000]   MEM window: 58000000-59ffffff
[4294669.277000] PCI: Bridge: 0000:00:14.4
[4294669.277000]   IO window: e000-efff
[4294669.277000]   MEM window: fbf00000-fbffffff
[4294669.277000]   PREFETCH window: 50000000-54ffffff
[4294669.277000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 19 (level, low) -> IRQ 185
[4294669.277000] ACPI: PCI Interrupt 0000:02:04.1[B] -> GSI 20 (level, low) -> IRQ 193
[4294669.277000] audit: initializing netlink socket (disabled)
[4294669.277000] audit(1150301878.276:1): initialized
[4294669.277000] highmem bounce pool size: 64 pages
[4294669.278000] VFS: Disk quotas dquot_6.5.1
[4294669.278000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.278000] Initializing Cryptographic API
[4294669.278000] io scheduler noop registered
[4294669.278000] io scheduler anticipatory registered
[4294669.278000] io scheduler deadline registered
[4294669.278000] io scheduler cfq registered
[4294669.278000] isapnp: Scanning for PnP cards...
[4294669.635000] isapnp: No Plug & Play device found
[4294669.648000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294669.649000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294669.649000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294669.649000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294669.649000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294669.649000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294669.649000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.649000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.650000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 201
[4294669.650000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[4294669.651000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.651000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.651000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.651000] mice: PS/2 mouse device common for all mice
[4294669.651000] EISA: Probing bus 0 at eisa.0
[4294669.651000] Cannot allocate resource for EISA slot 1
[4294669.651000] Cannot allocate resource for EISA slot 4
[4294669.651000] EISA: Detected 0 cards.
[4294669.651000] NET: Registered protocol family 2
[4294669.661000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.661000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[4294669.661000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294669.662000] TCP: Hash tables configured (established 131072 bind 65536)
[4294669.662000] TCP reno registered
[4294669.662000] TCP bic registered
[4294669.662000] NET: Registered protocol family 1
[4294669.662000] NET: Registered protocol family 8
[4294669.662000] NET: Registered protocol family 20
[4294669.662000] Using IPI Shortcut mode
[4294669.662000] ACPI wakeup devices:
[4294669.662000] POP2  RTL USB1 USB2 EUSB AC97 MC97
[4294669.662000] ACPI: (supports S0 S1 S3 S4 S5)
[4294669.662000] Freeing unused kernel memory: 288k freed
[4294669.716000] vga16fb: initializing
[4294669.716000] vga16fb: mapped to 0xc00a0000
[4294669.806000] Console: switching to colour frame buffer device 80x25
[4294669.806000] fb0: VGA16 VGA frame buffer device
[4294670.257000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294670.915000] Capability LSM initialized
[4294670.952000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294670.956000] ACPI: Thermal Zone [THRM] (53 C)
[4294671.474000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[4294671.474000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 209
[4294671.474000] ATIIXP: chipset revision 0
[4294671.474000] ATIIXP: not 100% native mode: will probe irqs later
[4294671.474000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
[4294671.474000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
[4294671.474000] Probing IDE interface ide0...
[4294671.738000] hda: ST96812A, ATA DISK drive
[4294672.350000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.350000] Probing IDE interface ide1...
[4294673.022000] hdc: HL-DT-ST DVD-RW GCA-4080N, ATAPI CD/DVD-ROM drive
[4294673.328000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.337000] hda: max request size: 1024KiB
[4294673.344000] hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[4294673.345000] hda: cache flushes supported
[4294673.345000]  hda: hda1 hda2 < hda5 >
[4294673.384000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294673.385000] Uniform CD-ROM driver Revision: 3.20
[4294673.627000] ieee1394: Initialized config rom entry `ip1394'
[4294673.628000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[4294673.628000] ACPI: PCI Interrupt 0000:02:04.2[C] -> GSI 21 (level, low) -> IRQ 177
[4294673.669000] usbcore: registered new driver usbfs
[4294673.669000] usbcore: registered new driver hub
[4294673.670000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294673.670000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 185
[4294673.670000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[4294673.692000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[4294673.692000] ohci_hcd 0000:00:13.0: irq 185, io mem 0xfbdfd000
[4294673.747000] hub 1-0:1.0: USB hub found
[4294673.747000] hub 1-0:1.0: 4 ports detected
[4294673.757000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[177]  MMIO=[fbfff000-fbfff7ff]  Max Packet=[2048]
[4294673.848000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 185
[4294673.848000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[4294673.869000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[4294673.869000] ohci_hcd 0000:00:13.1: irq 185, io mem 0xfbdfe000
[4294673.924000] hub 2-0:1.0: USB hub found
[4294673.924000] hub 2-0:1.0: 4 ports detected
[4294674.026000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 185
[4294674.026000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[4294674.026000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[4294674.026000] ehci_hcd 0000:00:13.2: irq 185, io mem 0xfbdff000
[4294674.026000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294674.026000] hub 3-0:1.0: USB hub found
[4294674.026000] hub 3-0:1.0: 8 ports detected
[4294674.171000] Attempting manual resume
[4294674.204000] EXT3-fs: mounted filesystem with ordered data mode.
[4294674.224000] kjournald starting.  Commit interval 5 seconds
[4294674.742000] usb 2-2: new full speed USB device using ohci_hcd and address 2[4294675.022000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000a85fe8][4294685.553000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294685.558000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294686.294000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 19 (level, low) -> IRQ 185
[4294686.295000] Yenta: CardBus bridge found at 0000:02:04.0 [1462:0131]
[4294686.340000] input: PC Speaker as /class/input/input1
[4294686.349000] Real Time Clock Driver v1.12
[4294686.386000] Bluetooth: Core ver 2.8
[4294686.386000] NET: Registered protocol family 31
[4294686.386000] Bluetooth: HCI device and connection manager initialized
[4294686.386000] Bluetooth: HCI socket layer initialized
[4294686.424000] Linux agpgart interface v0.101 (c) Dave Jones
[4294686.426000] Yenta: ISA IRQ mask 0x06b8, PCI irq 185
[4294686.426000] Socket status: 30000006
[4294686.426000] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #06
[4294686.426000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[4294686.426000] cs: IO port probe 0xe000-0xefff: clean.
[4294686.427000] pcmcia: parent PCI bridge Memory window: 0xfbf00000 - 0xfbffffff
[4294686.427000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x54ffffff
[4294686.427000] ACPI: PCI Interrupt 0000:02:04.1[B] -> GSI 20 (level, low) -> IRQ 193
[4294686.427000] Yenta: CardBus bridge found at 0000:02:04.1 [1462:0131]
[4294686.457000] 8139too Fast Ethernet driver 0.9.27
[4294686.457000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 18 (level, low) -> IRQ 217
[4294686.458000] eth0: RealTek RTL8139 at 0xf89f8c00, 00:10:dc:e8:94:a5, IRQ 217[4294686.458000] eth0:  Identified 8139 chip type 'RTL-8101'
[4294686.536000] Bluetooth: HCI USB driver ver 2.9
[4294686.548000] logips2pp: Detected unknown logitech mouse model 99
[4294686.549000] usbcore: registered new driver hci_usb
[4294686.551000] Yenta: ISA IRQ mask 0x06b8, PCI irq 193
[4294686.551000] Socket status: 30000006
[4294686.551000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[4294686.551000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[4294686.551000] cs: IO port probe 0xe000-0xefff: clean.
[4294686.551000] pcmcia: parent PCI bridge Memory window: 0xfbf00000 - 0xfbffffff
[4294686.551000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x54ffffff
[4294686.590000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[4294686.621000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[4294686.699000] ts: Compaq touchscreen protocol output
[4294686.755000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 201
[4294687.235000] cs: IO port probe 0x100-0x3af: clean.
[4294687.238000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[4294687.239000] cs: IO port probe 0x820-0x8ff: clean.
[4294687.240000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294687.241000] cs: IO port probe 0xa00-0xaff: clean.
[4294687.243000] cs: IO port probe 0x100-0x3af: clean.
[4294687.246000] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[4294687.248000] cs: IO port probe 0x820-0x8ff: clean.
[4294687.249000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[4294687.250000] cs: IO port probe 0xa00-0xaff: clean.
[4294687.271000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 201
[4294687.583000] eth0: link down
[4294687.860000] lp: driver loaded but no devices found
[4294687.894000] SCSI subsystem initialized
[4294687.905000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294687.905000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)[4294687.905000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294687.962000] Adding 2409708k swap on /dev/hda5.  Priority:-1 extents:1 across:2409708k
[4294688.085000] EXT3 FS on hda1, internal journal
[4294688.228000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294688.228000] md: bitmap version 4.39
[4294688.668000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294688.864000] NET: Registered protocol family 17
[4294689.470000] cdrom: open failed.
[4294695.626000] ACPI: AC Adapter [ADP1] (on-line)
[4294695.675000] ACPI: Battery Slot [BAT1] (battery present)
[4294695.726000] ACPI: Power Button (FF) [PWRF]
[4294695.726000] ACPI: Lid Switch [LID0]
[4294695.726000] ACPI: Sleep Button (CM) [SLPB]
[4294695.726000] ACPI: Power Button (CM) [PWRB]
[4294695.813000] ibm_acpi: ec object not found
[4294695.832000] pcc_acpi: loading...
[4294696.329000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[4294696.337000] powernow-k8:    0 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[4294696.337000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xa (1300 mV)
[4294696.337000] cpu_init done, current fid 0x8, vid 0x8
[4294696.337000] powernow-k8: ph2 null fid transition 0x8
[4294699.930000] [drm] Initialized drm 1.0.1 20051102
[4294701.148000] ppdev: user-space parallel port driver
[4294701.657000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294701.657000] apm: overridden by ACPI.
[4294704.552000] Bluetooth: L2CAP ver 2.8
[4294704.552000] Bluetooth: L2CAP socket layer initialized
[4294704.557000] Bluetooth: RFCOMM socket layer initialized
[4294704.557000] Bluetooth: RFCOMM TTY layer initialized
[4294704.557000] Bluetooth: RFCOMM ver 1.7
[4295152.216000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[4295158.263000] NET: Registered protocol family 10
[4295158.264000] lo: Disabled Privacy Extensions
[4295158.264000] IPv6 over IPv4 tunneling driver
[4295168.545000] eth0: no IPv6 routers present
[4295186.586000] psmouse.c: Wheel Mouse at isa0060/serio2/input0 lost synchronization, throwing 1 bytes away.
[4295205.250000] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[4295215.551000] eth0: no IPv6 routers present


```

---

### Post by qb4ever on 2006-06-23
I have my wpc54g V4 working under dapper/breezy that also uses the ipn2200.

Is it showing up in lspci ?

---

