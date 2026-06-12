---
title: "pvr usb2 problems"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by mackandall on 2007-07-12
I have a Hauppauge PVR-USB2 that I am trying to get running alongside my Pinnacle HD pro usb stick. The problem is that I can get only one to work at a time both in Mythtv and in Feisty. I am starting to wonder if the problem has to do with trying to use two usb based tv capture devices. The pvr usb2 works by default in Feisty but as soon as I install the driver for the Pinnacle hd usb stick problems start. For one thing there is only one device (/dev/video0) and the Pinnacle hijacks this so it starts working and the pvr usb2 just goes dead and can no longer be detected this is what a dmesg gives after I install the driver for the Pinnacle 

> [    0.000000] Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Thu Jun 7 20:16:13 UTC 2007 (Ubuntu 2.6.20-16.29-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fef0000 end: 000000007fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007fff0000 size: 0000000000003000 end: 000000007fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000007fff3000 size: 000000000000d000 end: 0000000080000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5050
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f69c0
[    0.000000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x7fff3000
[    0.000000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x7fff3040
[    0.000000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x7fff6e40
[    0.000000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Detected 3457.941 MHz processor.
[   36.036910] Built 1 zonelists.  Total pages: 520177
[   36.036911] Kernel command line: root=UUID=11c4660c-acf0-4b4d-995f-718b06d910d8 ro quiet splash
[   36.037038] mapped APIC to ffffd000 (fee00000)
[   36.037040] mapped IOAPIC to ffffc000 (fec00000)
[   36.037043] Enabling fast FPU save and restore... done.
[   36.037045] Enabling unmasked SIMD FPU exception support... done.
[   36.037056] Initializing CPU#0
[   36.037133] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   36.039016] Console: colour VGA+ 80x25
[   36.039695] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   36.040370] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.096303] Memory: 2068284k/2097088k available (1917k kernel code, 27480k reserved, 868k data, 328k init, 1179584k highmem)
[   36.096312] virtual kernel memory layout:
[   36.096313]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[   36.096314]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.096315]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   36.096316]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   36.096316]       .init : 0xc03bc000 - 0xc040e000   ( 328 kB)
[   36.096317]       .data : 0xc02df423 - 0xc03b8434   ( 868 kB)
[   36.096318]       .text : 0xc0100000 - 0xc02df423   (1917 kB)
[   36.096320] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.173081] Calibrating delay using timer specific routine.. 6920.05 BogoMIPS (lpj=13840104)
[   36.173112] Security Framework v1.0.0 initialized
[   36.173123] SELinux:  Disabled at boot.
[   36.173133] Mount-cache hash table entries: 512
[   36.173243] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   36.173252] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   36.173254] CPU: L2 cache: 512K
[   36.173256] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   36.173265] Compat vDSO mapped to ffffe000.
[   36.173270] Remapping vsyscall page to ffffe000
[   36.173278] CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   36.173284] Checking 'hlt' instruction... OK.
[   36.189489] Early unpacking initramfs... done
[   36.409424] ACPI: Core revision 20060707
[   36.414402] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   36.418041] ENABLING IO-APIC IRQs
[   36.418208] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   36.565066] Booting paravirtualized kernel on bare hardware
[   36.565128] Time: 22:11:52  Date: 06/12/107
[   36.565153] NET: Registered protocol family 16
[   36.565225] EISA bus registered
[   36.565229] ACPI: bus type pci registered
[   36.588902] PCI: PCI BIOS revision 2.10 entry at 0xfb040, last bus=2
[   36.588904] PCI: Using configuration type 1
[   36.588905] Setting up standard PCI resources
[   36.601936] ACPI: Interpreter enabled
[   36.601939] ACPI: Using IOAPIC for interrupt routing
[   36.602344] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.602348] PCI: Probing PCI hardware (bus 00)
[   36.602810] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   36.602813] PCI quirk: region 1080-10bf claimed by ICH4 GPIO
[   36.602956] Boot video device is 0000:01:00.0
[   36.603143] PCI: Transparent bridge - 0000:00:1e.0
[   36.603165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   36.607965] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   36.610703] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   36.610893] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   36.611083] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   36.611271] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   36.611461] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   36.611653] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   36.611844] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   36.612035] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   36.612161] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.612170] pnp: PnP ACPI init
[   36.614868] pnp: PnP ACPI: found 13 devices
[   36.614874] PnPBIOS: Disabled by ACPI PNP
[   36.614915] PCI: Using ACPI for IRQ routing
[   36.614918] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.627550] NET: Registered protocol family 8
[   36.627552] NET: Registered protocol family 20
[   36.628114] PCI: Bridge: 0000:00:01.0
[   36.628116]   IO window: disabled.
[   36.628120]   MEM window: f8000000-faffffff
[   36.628122]   PREFETCH window: e0000000-efffffff
[   36.628126] PCI: Bridge: 0000:00:1e.0
[   36.628128]   IO window: 9000-9fff
[   36.628132]   MEM window: fb000000-fcffffff
[   36.628135]   PREFETCH window: 88000000-880fffff
[   36.628149] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   36.628170] NET: Registered protocol family 2
[   36.664921] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   36.665085] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[   36.665434] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   36.665755] TCP: Hash tables configured (established 131072 bind 65536)
[   36.665757] TCP reno registered
[   36.677007] checking if image is initramfs... it is
[   37.113569] Freeing initrd memory: 6761k freed
[   37.113899] audit: initializing netlink socket (disabled)
[   37.113913] audit(1184278313.160:1): initialized
[   37.113967] highmem bounce pool size: 64 pages
[   37.114009] VFS: Disk quotas dquot_6.5.1
[   37.114027] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.114069] io scheduler noop registered
[   37.114071] io scheduler anticipatory registered
[   37.114073] io scheduler deadline registered
[   37.114080] io scheduler cfq registered (default)
[   37.114303] isapnp: Scanning for PnP cards...
[   37.467831] isapnp: No Plug & Play device found
[   37.487334] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   37.487436] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.487592] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.488142] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.488408] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.488650] mice: PS/2 mouse device common for all mice
[   37.489042] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   37.489225] input: Macintosh mouse button emulation as /class/input/input0
[   37.489250] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   37.489254] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   37.489450] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   37.489452] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   37.493058] serio: i8042 KBD port at 0x60,0x64 irq 1
[   37.493064] serio: i8042 AUX port at 0x60,0x64 irq 12
[   37.493192] EISA: Probing bus 0 at eisa.0
[   37.493200] Cannot allocate resource for EISA slot 1
[   37.493223] EISA: Detected 0 cards.
[   37.523290] TCP cubic registered
[   37.523295] NET: Registered protocol family 1
[   37.523313] Using IPI Shortcut mode
[   37.523362] ACPI: (supports S0 S1 S4 S5)
[   37.523401]   Magic number: 15:856:198
[   37.523471]   hash matches device ttypd
[   37.523900] Freeing unused kernel memory: 328k freed
[   37.524528] Time: tsc clocksource has been installed.
[   37.541840] input: AT Translated Set 2 keyboard as /class/input/input1
[   38.713535] Capability LSM initialized
[   38.743016] ACPI: Fan [FAN] (on)
[   38.746950] ACPI: Thermal Zone [THRM] (22 C)
[   39.165990] usbcore: registered new interface driver usbfs
[   39.166009] usbcore: registered new interface driver hub
[   39.166027] usbcore: registered new device driver usb
[   39.166691] USB Universal Host Controller Interface driver v3.0
[   39.166738] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   39.166748] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   39.166751] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   39.166890] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   39.166912] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ac00
[   39.166999] usb usb1: configuration #1 chosen from 1 choice
[   39.167021] hub 1-0:1.0: USB hub found
[   39.167027] hub 1-0:1.0: 2 ports detected
[   39.212402] SCSI subsystem initialized
[   39.231991] libata version 2.20 loaded.
[   39.267948] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   39.267959] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   39.267962] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   39.267979] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   39.268002] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000a000
[   39.268075] usb usb2: configuration #1 chosen from 1 choice
[   39.268095] hub 2-0:1.0: USB hub found
[   39.268102] hub 2-0:1.0: 2 ports detected
[   39.320286] Floppy drive(s): fd0 is 1.44M
[   39.350459] FDC 0 is a post-1991 82077
[   39.371983] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   39.371995] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   39.371998] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   39.372019] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   39.372041] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a400
[   39.372117] usb usb3: configuration #1 chosen from 1 choice
[   39.372138] hub 3-0:1.0: USB hub found
[   39.372145] hub 3-0:1.0: 2 ports detected
[   39.475824] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   39.475836] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   39.475839] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   39.475860] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   39.475881] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000a800
[   39.475959] usb usb4: configuration #1 chosen from 1 choice
[   39.475980] hub 4-0:1.0: USB hub found
[   39.475987] hub 4-0:1.0: 2 ports detected
[   39.581528] ata_piix 0000:00:1f.1: version 2.10ac1
[   39.581548] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   39.581564] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   39.581631] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   39.581664] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   39.581681] scsi0 : ata_piix
[   39.611698] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   39.751983] ata1.00: ata_hpa_resize 1: sectors = 156247887, hpa_sectors = 156250000
[   39.751987] ata1.00: Host Protected Area detected.
[   39.751988]      current size : 156247887 sectors (79998 MB)
[   39.751989]      native  size : 156250000 sectors (80000 MB)
[   39.791853] usb 2-2: configuration #1 chosen from 1 choice
[   39.791863] ata1.00: Native size increased to 156250000 sectors
[   39.791866] ata1.00: ATA-7: Maxtor 6Y080L0, YAR41BW0, max UDMA/133
[   39.791868] ata1.00: 156250000 sectors, multi 16: LBA 
[   39.813472] ata1.01: ata_hpa_resize 1: sectors = 30033360, hpa_sectors = 30033360
[   39.813476] ata1.01: ATA-4: IBM-DJNA-351520, J56OA30K, max UDMA/66
[   39.813479] ata1.01: 30033360 sectors, multi 16: LBA 
[   39.813487] ata1.01: limited to UDMA/33 due to 40-wire cable
[   39.819973] ata1.00: ata_hpa_resize 1: sectors = 156250000, hpa_sectors = 156250000
[   39.819977] ata1.00: configured for UDMA/133
[   39.835425] ata1.01: ata_hpa_resize 1: sectors = 30033360, hpa_sectors = 30033360
[   39.835430] ata1.01: configured for UDMA/33
[   39.835443] scsi1 : ata_piix
[   40.051490] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   40.234590] usb 3-1: configuration #1 chosen from 1 choice
[   40.319606] ata2.00: ATAPI, max UDMA/33
[   40.319610] ata2.01: ATAPI, max UDMA/66
[   40.475395] usb 3-2: new full speed USB device using uhci_hcd and address 3
[   40.483520] ata2.00: configured for UDMA/33
[   40.643336] usb 3-2: configuration #1 chosen from 1 choice
[   40.647493] ata2.01: configured for UDMA/66
[   40.649293] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[   40.651268] scsi 0:0:1:0: Direct-Access     ATA      IBM-DJNA-351520  J56O PQ: 0 ANSI: 5
[   40.651971] scsi 1:0:0:0: CD-ROM            PLEXTOR  DVDR   PX-708A   1.04 PQ: 0 ANSI: 5
[   40.653214] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-ROM DVD-116R 1.15 PQ: 0 ANSI: 5
[   40.655758] r8169 Gigabit Ethernet driver 2.2LK loaded
[   40.655780] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 19
[   40.655881] eth0: RTL8169s/8110s at 0xf88a0000, 00:14:85:b1:ee:bc, IRQ 19
[   40.659037] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[   40.659044] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   40.659048] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   40.659071] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   40.659100] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   40.659109] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfd000000
[   40.662991] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.663062] usb usb5: configuration #1 chosen from 1 choice
[   40.663084] hub 5-0:1.0: USB hub found
[   40.663090] hub 5-0:1.0: 8 ports detected
[   40.675320] SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
[   40.675331] sda: Write Protect is off
[   40.675333] sda: Mode Sense: 00 3a 00 00
[   40.675344] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.675394] SCSI device sda: 156250000 512-byte hdwr sectors (80000 MB)
[   40.675400] sda: Write Protect is off
[   40.675402] sda: Mode Sense: 00 3a 00 00
[   40.675411] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.675414]  sda: sda1 sda2
[   40.708050] sd 0:0:0:0: Attached scsi disk sda
[   40.708171] SCSI device sdb: 30033360 512-byte hdwr sectors (15377 MB)
[   40.708180] sdb: Write Protect is off
[   40.708182] sdb: Mode Sense: 00 3a 00 00
[   40.708193] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.708226] SCSI device sdb: 30033360 512-byte hdwr sectors (15377 MB)
[   40.708232] sdb: Write Protect is off
[   40.708234] sdb: Mode Sense: 00 3a 00 00
[   40.708243] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.708245]  sdb: sdb1 sdb2 < sdb5 >
[   40.733261] sd 0:0:1:0: Attached scsi disk sdb
[   40.737754] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   40.737836] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   40.737918] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   40.737999] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   40.749519] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   40.749524] Uniform CD-ROM driver Revision: 3.20
[   40.749734] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   40.769044] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[   40.769192] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   40.803234] usb 3-1: USB disconnect, address 2
[   40.931141] usb 3-2: USB disconnect, address 3
[   41.366291] Attempting manual resume
[   41.366294] swsusp: Resume From Partition 8:21
[   41.366296] PM: Checking swsusp image.
[   41.383652] PM: Resume from disk failed.
[   41.421391] kjournald starting.  Commit interval 5 seconds
[   41.421400] EXT3-fs: mounted filesystem with ordered data mode.
[   41.666829] usb 5-6: new high speed USB device using ehci_hcd and address 4
[   41.801124] usb 5-6: configuration #1 chosen from 1 choice
[   42.038679] usb 5-7: new high speed USB device using ehci_hcd and address 5
[   42.178887] usb 5-7: configuration #1 chosen from 1 choice
[   42.179045] usb 2-2: USB disconnect, address 2
[   42.179164] usbcore: registered new interface driver hiddev
[   42.418525] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   42.598997] usb 2-2: configuration #1 chosen from 1 choice
[   42.858354] usb 3-1: new low speed USB device using uhci_hcd and address 4
[   43.041816] usb 3-1: configuration #1 chosen from 1 choice
[   43.059722] input: Philips RCS USB IR Combo Device as /class/input/input2
[   43.059734] input: USB HID v1.00 Keyboard [Philips RCS USB IR Combo Device] on usb-0000:00:1d.1-2
[   43.089677] input: Philips RCS USB IR Combo Device as /class/input/input3
[   43.089704] input,hiddev96: USB HID v1.00 Device [Philips RCS USB IR Combo Device] on usb-0000:00:1d.1-2
[   43.122781] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A as /class/input/input4
[   43.122797] input: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A] on usb-0000:00:1d.2-1
[   43.122806] usbcore: registered new interface driver usbhid
[   43.122809] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   57.341784] r8169: eth0: link up
[   58.873808] NET: Registered protocol family 17
[   58.943018] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   58.964061] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   58.977363] intel_rng: FWH not detected
[   59.014413] iTCO_vendor_support: vendor-support=0
[   59.015559] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   59.015632] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x1060)
[   59.015663] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   59.173846] Linux agpgart interface v0.102 (c) Dave Jones
[   59.294725] agpgart: Detected an Intel 865 Chipset.
[   59.298997] agpgart: AGP aperture is 128M @ 0xf0000000
[   59.329948] Real Time Clock Driver v1.12ac
[   59.560773] input: PC Speaker as /class/input/input5
[   59.653425] gameport: EMU10K1 is pci0000:02:03.1/gameport0, io 0x9400, speed 1104kHz
[   59.829386] parport: PnPBIOS parport detected.
[   59.829409] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   60.136513] Linux video capture interface: v2.00
[   60.978199] nvidia: module license 'NVIDIA' taints kernel.
[   61.233130] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.233399] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
[   61.319555] em28xx v4l2 driver version 0.0.1 loaded
[   61.367390] usbcore: registered new interface driver pvrusb2
[   61.367395] /lib/firmware/v4l-dvb-experimental/v4l/pvrusb2-main.c: Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner : V4L in-tree version
[   61.367397] /lib/firmware/v4l-dvb-experimental/v4l/pvrusb2-main.c: Debug mask is 15 (0xf)
[   61.482711] usb 5-6: reset high speed USB device using ehci_hcd and address 4
[   61.528771] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.666787] em28xx new video device (2304:0227): interface 0, class 255
[   61.666792] em28xx: device is attached to a USB 2.0 bus
[   61.666794] em28xx: you're using the experimental/unstable tree from mcentral.de
[   61.666795] em28xx: there's also a stable tree available but which is limited to
[   61.666797] em28xx: linux <=2.6.19.2
[   61.666798] em28xx: it's fine to use this driver but keep in mind that it will move
[   61.666799] em28xx: to [http://mcentral.de/hg/~mrec/v4l-dvb-kernel](http://mcentral.de/hg/~mrec/v4l-dvb-kernel) as soon as it's
[   61.666801] em28xx: proved to be stable
[   61.666804] em28xx #0: Alternate settings: 8
[   61.666806] em28xx #0: Alternate setting 0, max size= 0
[   61.666807] em28xx #0: Alternate setting 1, max size= 0
[   61.666809] em28xx #0: Alternate setting 2, max size= 1448
[   61.666811] em28xx #0: Alternate setting 3, max size= 2048
[   61.666812] em28xx #0: Alternate setting 4, max size= 2304
[   61.666814] em28xx #0: Alternate setting 5, max size= 2580
[   61.666816] em28xx #0: Alternate setting 6, max size= 2892
[   61.666817] em28xx #0: Alternate setting 7, max size= 3072
[   61.775696] pvrusb2: ***WARNING*** Device encoder firmware seems to be missing.
[   61.775699] pvrusb2: Did you install the pvrusb2 firmware files in their proper location?
[   61.775702] pvrusb2: request_firmware unable to locate encoder file v4l-cx2341x-enc.fw
[   61.775705] pvrusb2: device unstable!!
[   61.775707] pvrusb2: ***WARNING*** pvrusb2 device hardware appears to be jammed and I can't clear it.
[   61.775709] pvrusb2: You might need to power cycle the pvrusb2 device in order to recover.
[   62.054537] input: em2880/em2870 remote control as /class/input/input6
[   62.054571] em28xx-input.c: remote control handler attached
[   62.055486] attach_inform: eeprom detected.
[   62.084138] em28xx #0: i2c eeprom 00: 1a eb 67 95 04 23 27 02 d0 12 5c 03 8e 16 a4 1c
[   62.084145] em28xx #0: i2c eeprom 10: 6a 24 27 57 46 07 01 00 00 00 00 00 00 00 00 00
[   62.084151] em28xx #0: i2c eeprom 20: 46 00 01 00 f0 10 02 00 b8 00 00 00 5b 1c 00 00
[   62.084156] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 00 00 00 00 00 00
[   62.084161] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   62.084165] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   62.084170] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 24 03 50 00 69 00
[   62.084175] em28xx #0: i2c eeprom 70: 6e 00 6e 00 61 00 63 00 6c 00 65 00 20 00 53 00
[   62.084180] em28xx #0: i2c eeprom 80: 79 00 73 00 74 00 65 00 6d 00 73 00 00 00 16 03
[   62.084184] em28xx #0: i2c eeprom 90: 50 00 43 00 54 00 56 00 20 00 38 00 30 00 30 00
[   62.084189] em28xx #0: i2c eeprom a0: 65 00 00 00 1c 03 30 00 36 00 30 00 38 00 30 00
[   62.084194] em28xx #0: i2c eeprom b0: 31 00 30 00 30 00 32 00 39 00 39 00 35 00 00 00
[   62.084199] em28xx #0: i2c eeprom c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   62.084204] em28xx #0: i2c eeprom d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   62.084208] em28xx #0: i2c eeprom e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   62.084213] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   62.084218] EEPROM ID= 0x9567eb1a
[   62.084219] Vendor/Product ID= 2304:0227
[   62.084220] AC97 audio (5 sample rates)
[   62.084221] 500mA max power
[   62.084223] Table at 0x27, strings=0x168e, 0x1ca4, 0x246a
[   62.086764] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[   62.086824] attach inform (default): detected I2C address c2
[   62.086829] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[   62.086830] tuner 0x61: Configuration acknowledged
[   62.086832] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: setting tuner callback
[   62.086885] /lib/firmware/v4l-dvb-experimental/v4l/xc3028-tuner.c: attach request!
[   62.086887] /lib/firmware/v4l-dvb-experimental/v4l/tuner-core.c: xc3028 tuner successfully loaded
[   62.093187] attach_inform: tvp5150 detected.
[   62.154843] tvp5150 0-005c: tvp5150am1 detected.
[   62.245284] Loading base firmware: xc3028_init0.i2c.fw
[   63.187450] Loading default analogue TV settings: xc3028_BG_PAL_A2_A.i2c.fw
[   63.226783] xc3028-tuner.c: firmware 2.7
[   63.226788] ANALOG TV REQUEST
[   63.237402] em28xx #0: V4L2 device registered as /dev/video0
[   63.237406] em28xx #0: Found Pinnacle PCTV HD Pro
[   63.237419] usbcore: registered new interface driver em28xx
[   63.359085] em28xx-audio.c: probing for em28x1 non standard usbaudio
[   63.359089] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger
[   63.359285] Em28xx: Initialized (Em28xx Audio Extension) extension
[   63.501168] em2880-dvb.c: DVB Init
[   63.501177] Loading base firmware: xc3028_8MHz_init0.i2c.fw
[   64.559705] Loading default dtv settings: xc3028_DTV8_2633.i2c.fw
[   64.584296] xc3028-tuner.c: firmware 2.7
[   64.584301] Sending extra call for Digital TV!
[   64.725416] /lib/firmware/v4l-dvb-experimental/v4l/xc3028-tuner.c: attach request!
[   64.725421] DVB: registering new adapter (em2880 DVB-T)
[   64.725424] DVB: registering frontend 0 (LG Electronics LGDT3303 VSB/QAM Frontend)...
[   64.725608] Em28xx: Initialized (Em2880 DVB Extension) extension
[   65.375620] lp0: using parport0 (interrupt-driven).
[   65.402700] Adding 674688k swap on /dev/disk/by-uuid/80019811-2377-4337-b423-01fd7ab23bc1.  Priority:-1 extents:1 across:674688k
[   65.580259] EXT3 FS on sdb1, internal journal
[   65.840713] NET: Registered protocol family 10
[   65.840780] lo: Disabled Privacy Extensions
[   66.588192] Using specific hotkey driver
[   66.777593] ibm_acpi: ec object not found
[   66.831343] input: Power Button (FF) as /class/input/input7
[   66.835059] ACPI: Power Button (FF) [PWRF]
[   66.860972] input: Power Button (CM) as /class/input/input8
[   66.864708] ACPI: Power Button (CM) [PWRB]
[   66.875124] No dock devices found.
[   66.923441] pcc_acpi: loading...
[   75.450547] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   75.450561] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   75.450582] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   77.085938] ppdev: user-space parallel port driver
[   83.518542] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   83.518547] apm: overridden by ACPI.
[   86.604359] eth0: no IPv6 routers present
[   96.823442] Bluetooth: Core ver 2.11
[   96.823739] NET: Registered protocol family 31
[   96.823741] Bluetooth: HCI device and connection manager initialized
[   96.823744] Bluetooth: HCI socket layer initialized
[   97.193537] Bluetooth: L2CAP ver 2.8
[   97.193542] Bluetooth: L2CAP socket layer initialized
[   97.382948] Bluetooth: RFCOMM socket layer initialized
[   97.382960] Bluetooth: RFCOMM TTY layer initialized
[   97.382962] Bluetooth: RFCOMM ver 1.8
[  100.503063] em28xx-video.c: Switching device from DVB-T to analogue mode
[  100.503157] Loading base firmware: xc3028_init0.i2c.fw
[  101.486501] Loading default analogue TV settings: xc3028_BG_PAL_A2_A.i2c.fw
[  101.511339] xc3028-tuner.c: firmware 2.7
[  101.578548] tvp5150 0-005c: tvp5150am1 detected.
[  101.688103] ANALOG TV REQUEST
[  251.528622] usb 5-6: USB disconnect, address 4
[  269.401253] usb 5-6: new high speed USB device using ehci_hcd and address 6
[  269.535562] usb 5-6: configuration #1 chosen from 1 choice
[  270.534754] pvrusb2: ***WARNING*** Device fx2 controller firmware seems to be missing.
[  270.534758] pvrusb2: Did you install the pvrusb2 firmware files in their proper location?
[  270.534760] pvrusb2: request_firmware unable to locate fx2 controller file v4l-pvrusb2-24xxx-01.fw
[  270.534763] pvrusb2: Failure uploading firmware1
[  270.534765] pvrusb2: Device initialization was not successful.
[  270.534766] pvrusb2: Giving up since device microcontroller firmware appears to be missing.
[  306.210304] ANALOG TV REQUEST
[  306.210310] xc3028_tuner_set_params, Loading specific configuration for requested mode xc3028_MN_NTSCPAL_A2.i2c.fw
[  306.549836] ANALOG TV REQUEST
[  306.905847] ANALOG TV REQUEST
[  313.547117] ANALOG TV REQUEST
[  313.938957] ANALOG TV REQUEST
[  315.626330] ANALOG TV REQUEST
mackandall@ubuntu:~$ 



I have been at this for like a week now and I cant get both of them to work at the same time. I have tired mknod and the device created just doesnt run. It seems as if both devices might be battling for /dev/video0 or something. Any help would be greatly appreciated.

---

