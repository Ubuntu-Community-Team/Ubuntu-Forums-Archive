---
title: "Audigy2 not working anymore in Ubuntu Feisty Fawn"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by Nossie on 2007-06-10
Hi,

I use an Audigy 2 which works fine in Vista... and used to work fine in Feisty..

I had to reinstall the system and I'm not sure if I had sound after that but I certainly dont now.

here is my dmesg and at the top it will show my default card settings

```
ian@Jupiter-ubuntu:~$ sudo asoundconf list
Names of available sound cards:
V8237
Audigy2
ian@Jupiter-ubuntu:~$ sudo asoundconf set-default-card Audigy2
ian@Jupiter-ubuntu:~$ 

```



```
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x12000530 MSFT 0x00000097) @ 0x3ffc0040
[    0.000000] ACPI: DSDT (v001  A0036 A0036001 0x00000001 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:7 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[    0.000000] Detected 2403.432 MHz processor.
[   34.444991] Built 1 zonelists.  Total pages: 260017
[   34.444994] Kernel command line: root=UUID=6c4b2e70-65dc-4ffd-ae52-c065e8ec86c3 ro quiet splash
[   34.445098] mapped APIC to ffffd000 (fee00000)
[   34.445100] mapped IOAPIC to ffffc000 (fec00000)
[   34.445103] Enabling fast FPU save and restore... done.
[   34.445104] Enabling unmasked SIMD FPU exception support... done.
[   34.445110] Initializing CPU#0
[   34.445174] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   34.446877] Console: colour VGA+ 80x25
[   34.447187] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   34.447502] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   34.462380] Memory: 1028048k/1048256k available (1992k kernel code, 19492k reserved, 900k data, 328k init, 130752k highmem)
[   34.462388] virtual kernel memory layout:
[   34.462389]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   34.462390]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   34.462391]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   34.462392]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   34.462393]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   34.462394]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   34.462395]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   34.462397] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   34.541161] Calibrating delay using timer specific routine.. 4811.75 BogoMIPS (lpj=9623517)
[   34.541190] Security Framework v1.0.0 initialized
[   34.541195] SELinux:  Disabled at boot.
[   34.541206] Mount-cache hash table entries: 512
[   34.541301] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[   34.541307] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   34.541310] CPU: L2 Cache: 1024K (64 bytes/line)
[   34.541312] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[   34.541320] Compat vDSO mapped to ffffe000.
[   34.541323] Remapping vsyscall page to ffffe000
[   34.541330] Checking 'hlt' instruction... OK.
[   34.557246] SMP alternatives: switching to UP code
[   34.557378] Freeing SMP alternatives: 11k freed
[   34.557521] Early unpacking initramfs... done
[   34.789885] ACPI: Core revision 20060707
[   34.790207] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   34.791564] CPU0: AMD Athlon(tm) 64 FX-53 Processor stepping 0a
[   34.791580] Total of 1 processors activated (4811.75 BogoMIPS).
[   34.792081] ENABLING IO-APIC IRQs
[   34.792399] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   34.937102] Brought up 1 CPUs
[   34.937273] Booting paravirtualized kernel on bare hardware
[   34.937355] Time: 10:58:17  Date: 05/10/107
[   34.937372] NET: Registered protocol family 16
[   34.937423] EISA bus registered
[   34.937426] ACPI: bus type pci registered
[   34.937904] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   34.937905] PCI: Using configuration type 1
[   34.937907] Setting up standard PCI resources
[   34.947150] ACPI: Interpreter enabled
[   34.947152] ACPI: Using IOAPIC for interrupt routing
[   34.947898] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   34.947901] PCI: Probing PCI hardware (bus 00)
[   34.948773] PCI: enabled onboard AC97/MC97 devices
[   34.948929] Boot video device is 0000:01:00.0
[   34.948960] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   34.964471] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 14 15)
[   34.964658] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 14 15)
[   34.964842] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 14 15)
[   34.965026] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 14 15)
[   34.965223] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   34.965406] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   34.965590] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   34.965773] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   34.965851] Linux Plug and Play Support v0.97 (c) Adam Belay
[   34.965860] pnp: PnP ACPI init
[   34.969600] pnp: PnP ACPI: found 15 devices
[   34.969602] PnPBIOS: Disabled by ACPI PNP
[   34.969630] PCI: Using ACPI for IRQ routing
[   34.969632] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   34.974933] NET: Registered protocol family 8
[   34.974934] NET: Registered protocol family 20
[   34.975456] pnp: 00:09: ioport range 0x680-0x6ff has been reserved
[   34.975459] pnp: 00:09: ioport range 0x290-0x297 has been reserved
[   34.975613] PCI: Bridge: 0000:00:01.0
[   34.975615]   IO window: disabled.
[   34.975618]   MEM window: f9f00000-fbffffff
[   34.975621]   PREFETCH window: e0000000-f8ffffff
[   34.975633] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   34.975646] NET: Registered protocol family 2
[   35.013105] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   35.013209] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   35.013884] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   35.014157] TCP: Hash tables configured (established 131072 bind 65536)
[   35.014159] TCP reno registered
[   35.025151] checking if image is initramfs... it is
[   35.482377] Freeing initrd memory: 6791k freed
[   35.482651] audit: initializing netlink socket (disabled)
[   35.482660] audit(1181473098.116:1): initialized
[   35.482699] highmem bounce pool size: 64 pages
[   35.482736] VFS: Disk quotas dquot_6.5.1
[   35.482748] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   35.482779] io scheduler noop registered
[   35.482781] io scheduler anticipatory registered
[   35.482782] io scheduler deadline registered
[   35.482787] io scheduler cfq registered (default)
[   35.483009] isapnp: Scanning for PnP cards...
[   35.837035] isapnp: No Plug & Play device found
[   35.851122] Real Time Clock Driver v1.12ac
[   35.851151] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   35.851246] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.851348] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.851685] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   35.851829] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   35.851936] mice: PS/2 mouse device common for all mice
[   35.852246] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   35.852363] input: Macintosh mouse button emulation as /class/input/input0
[   35.852383] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.852385] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.852601] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   35.852979] serio: i8042 KBD port at 0x60,0x64 irq 1
[   35.852982] serio: i8042 AUX port at 0x60,0x64 irq 12
[   35.853050] EISA: Probing bus 0 at eisa.0
[   35.853057] Cannot allocate resource for EISA slot 1
[   35.853084] EISA: Detected 0 cards.
[   35.883199] TCP cubic registered
[   35.883206] NET: Registered protocol family 1
[   35.883219] Using IPI No-Shortcut mode
[   35.883264] ACPI: (supports S0 S1 S3 S4 S5)
[   35.883294]   Magic number: 11:252:982
[   35.883301]   hash matches device ttyc9
[   35.883592] Freeing unused kernel memory: 328k freed
[   35.884850] Time: tsc clocksource has been installed.
[   35.897751] input: AT Translated Set 2 keyboard as /class/input/input1
[   37.073567] Capability LSM initialized
[   37.103216] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   37.473780] ieee1394: Initialized config rom entry `ip1394'
[   37.474528] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.527327] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[f9500000-f95007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   37.532343] ACPI: PCI Interrupt 0000:00:0c.2[B] -> GSI 18 (level, low) -> IRQ 17
[   37.591210] SCSI subsystem initialized
[   37.594316] libata version 2.20 loaded.
[   37.616631] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f9c00000-f9c007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   37.633969] sata_via 0000:00:0f.0: version 2.1
[   37.633988] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 18
[   37.634003] sata_via 0000:00:0f.0: routed to hard irq line 11
[   37.634041] ata1: SATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d002 bmdma 0x0001c000 irq 18
[   37.667112] ata2: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001c402 bmdma 0x0001c008 irq 18
[   37.667130] scsi0 : sata_via
[   37.699357] usbcore: registered new interface driver usbfs
[   37.699372] usbcore: registered new interface driver hub
[   37.699388] usbcore: registered new device driver usb
[   37.699907] USB Universal Host Controller Interface driver v3.0
[   37.783160] Floppy drive(s): fd0 is 1.44M
[   37.825115] FDC 0 is a post-1991 82077
[   37.868486] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   38.035041] ATA: abnormal status 0x7F on port 0x0001d407
[   38.045616] ATA: abnormal status 0x7F on port 0x0001d407
[   38.054174] ata1.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   38.054178] ata1.00: ATA-7: Maxtor 7V300F0, VA111630, max UDMA/133
[   38.054181] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   38.061839] ata1.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   38.061841] ata1.00: configured for UDMA/133
[   38.061848] scsi1 : sata_via
[   38.264404] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   38.430958] ATA: abnormal status 0x7F on port 0x0001c807
[   38.441532] ATA: abnormal status 0x7F on port 0x0001c807
[   38.448791] ata2.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   38.448793] ata2.00: ATA-6: HDS722525VLSA80, V36OA60A, max UDMA/100
[   38.448795] ata2.00: 488397168 sectors, multi 16: LBA48 
[   38.456802] ata2.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   38.456804] ata2.00: configured for UDMA/100
[   38.456870] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 7V300F0   VA11 PQ: 0 ANSI: 5
[   38.457299] scsi 1:0:0:0: Direct-Access     ATA      HDS722525VLSA80  V36O PQ: 0 ANSI: 5
[   38.457706] sata_promise 0000:00:08.0: version 2.01
[   38.457720] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 17
[   38.457729] sata_promise PATA port found
[   38.465153] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[   38.465162] sda: Write Protect is off
[   38.465164] sda: Mode Sense: 00 3a 00 00
[   38.465174] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.465208] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[   38.465213] sda: Write Protect is off
[   38.465215] sda: Mode Sense: 00 3a 00 00
[   38.465223] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.465225]  sda:<6>ata3: SATA max UDMA/133 cmd 0xf8824200 ctl 0xf8824238 bmdma 0x00000000 irq 17
[   38.472403] ata4: SATA max UDMA/133 cmd 0xf8824280 ctl 0xf88242b8 bmdma 0x00000000 irq 17
[   38.472419] ata5: PATA max UDMA/133 cmd 0xf8824300 ctl 0xf8824338 bmdma 0x00000000 irq 17
[   38.472427] scsi2 : sata_promise
[   38.485755]  sda1 sda2 sda3
[   38.486065] sd 0:0:0:0: Attached scsi disk sda
[   38.486164] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   38.486170] sdb: Write Protect is off
[   38.486172] sdb: Mode Sense: 00 3a 00 00
[   38.486181] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.486203] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   38.486209] sdb: Write Protect is off
[   38.486210] sdb: Mode Sense: 00 3a 00 00
[   38.486219] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.486221]  sdb: sdb1 < sdb5 sdb6 sdb7 sdb8 sdb9 sdb10 >
[   38.539890] sd 1:0:0:0: Attached scsi disk sdb
[   38.542946] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   38.543049] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   38.784303] ata3: SATA link down (SStatus 0 SControl 300)
[   38.784316] scsi3 : sata_promise
[   38.808396] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800000d26a8]
[   38.820402] Attempting manual resume
[   38.820405] swsusp: Resume From Partition 8:26
[   38.820407] PM: Checking swsusp image.
[   38.820567] PM: Resume from disk failed.
[   38.838322] kjournald starting.  Commit interval 5 seconds
[   38.838330] EXT3-fs: mounted filesystem with ordered data mode.
[   39.080333] ieee1394: Host added: ID:BUS[1-01:1023]  GUID[00023c01410201ed]
[   39.252235] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   39.260653] ata4.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[   39.260657] ata4.00: ATA-7: ST3400832AS, 3.01, max UDMA/133
[   39.260659] ata4.00: 781422768 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   39.268599] ata4.00: ata_hpa_resize 1: sectors = 781422768, hpa_sectors = 781422768
[   39.268602] ata4.00: configured for UDMA/133
[   39.268608] scsi4 : sata_promise
[   39.424484] scsi 3:0:0:0: Direct-Access     ATA      ST3400832AS      3.01 PQ: 0 ANSI: 5
[   39.424525] SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
[   39.424533] sdc: Write Protect is off
[   39.424534] sdc: Mode Sense: 00 3a 00 00
[   39.424544] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.424572] SCSI device sdc: 781422768 512-byte hdwr sectors (400088 MB)
[   39.424578] sdc: Write Protect is off
[   39.424579] sdc: Mode Sense: 00 3a 00 00
[   39.424588] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   39.424590]  sdc: sdc1 sdc2 sdc3 sdc4 < sdc5 sdc6 >
[   39.476406] sd 3:0:0:0: Attached scsi disk sdc
[   39.476430] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   39.476940] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 19
[   39.476972] skge 1.9 addr 0xf9a00000 irq 19 chip Yukon-Lite rev 9
[   39.477048] skge eth0: addr 00:11:d8:82:c6:ac
[   39.477202] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 20
[   39.477211] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   39.477307] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   39.477330] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000d800
[   39.477408] usb usb1: configuration #1 chosen from 1 choice
[   39.477427] hub 1-0:1.0: USB hub found
[   39.477433] hub 1-0:1.0: 2 ports detected
[   39.580194] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 20
[   39.580200] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   39.580212] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   39.580228] uhci_hcd 0000:00:10.1: irq 20, io base 0x0000e000
[   39.580282] usb usb2: configuration #1 chosen from 1 choice
[   39.580295] hub 2-0:1.0: USB hub found
[   39.580300] hub 2-0:1.0: 2 ports detected
[   39.684151] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 20
[   39.684156] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   39.684167] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   39.684182] uhci_hcd 0000:00:10.2: irq 20, io base 0x0000e400
[   39.684235] usb usb3: configuration #1 chosen from 1 choice
[   39.684248] hub 3-0:1.0: USB hub found
[   39.684252] hub 3-0:1.0: 2 ports detected
[   39.788132] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 20
[   39.788137] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   39.788151] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   39.788166] uhci_hcd 0000:00:10.3: irq 20, io base 0x0000e800
[   39.788217] usb usb4: configuration #1 chosen from 1 choice
[   39.788230] hub 4-0:1.0: USB hub found
[   39.788234] hub 4-0:1.0: 2 ports detected
[   39.892224] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 20
[   39.892231] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   39.892247] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   39.892270] ehci_hcd 0000:00:10.4: irq 20, io mem 0xf9e00000
[   39.892276] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.892320] usb usb5: configuration #1 chosen from 1 choice
[   39.892336] hub 5-0:1.0: USB hub found
[   39.892341] hub 5-0:1.0: 8 ports detected
[   41.183810] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   41.422475] usb 2-1: configuration #1 chosen from 1 choice
[   44.957044] skge eth0: enabling interface
[   46.203284] Linux agpgart interface v0.102 (c) Dave Jones
[   46.307070] agpgart: Detected AGP bridge 0
[   46.311809] agpgart: AGP aperture is 128M @ 0xd0000000
[   46.379097] gameport: EMU10K1 is pci0000:00:0c.1/gameport0, io 0xb400, speed 1193kHz
[   46.587170] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   46.587186] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 18
[   46.587195] VP_IDE: chipset revision 6
[   46.587196] VP_IDE: not 100% native mode: will probe irqs later
[   46.587205] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   46.587212]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[   46.587221]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[   46.587226] Probing IDE interface ide0...
[   46.648106] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.656843] NET: Registered protocol family 17
[   46.685052] Linux video capture interface: v2.00
[   46.826783] skge eth0: Link is up at 100 Mbps, full duplex, flow control none
[   46.879019] input: PC Speaker as /class/input/input2
[   46.893695] parport: PnPBIOS parport detected.
[   46.893737] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   47.005514] ivtv:  ==================== START INIT IVTV ====================
[   47.005517] ivtv:  version 0.10.1 (tagged release) loading
[   47.005519] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   47.005520] ivtv:  In case of problems please include the debug info between
[   47.005522] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   47.005523] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   47.474626] hda: _NEC DVD_RW ND-3520A, ATAPI CD/DVD-ROM drive
[   47.643602] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   48.258463] hdb: JLMS XJ-HD166S, ATAPI CD/DVD-ROM drive
[   48.314791] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   48.316175] Probing IDE interface ide1...
[   48.883323] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.883341] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.883345] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com
[   48.883751] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   48.883788] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 21
[   48.883798] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   48.972786] nvidia: module license 'NVIDIA' taints kernel.
[   49.544559] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   49.564002] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   49.786076] ivtv0: Encoder revision: 0x02050032
[   49.786078] ivtv0: Recommended firmware version is 0x02060039.
[   49.794091] ivtv0: Decoder revision: 0x02020023
[   49.855025] tveeprom 1-0050: Hauppauge model 48135, rev I124, serial# 6186386
[   49.855028] tveeprom 1-0050: tuner model is Philips FM1246 (idx 24, type 1)
[   49.855031] tveeprom 1-0050: TV standards PAL(I) (eeprom 0x10)
[   49.855033] tveeprom 1-0050: audio processor is MSP4418 (idx 25)
[   49.855034] tveeprom 1-0050: decoder processor is SAA7115 (idx 19)
[   49.855036] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter
[   49.855039] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   49.874003] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   49.947935] saa7115 1-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   50.174407] saa7127 1-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[   50.199244] msp3400 1-0040: MSP4418G-A2 found @ 0x80 (ivtv i2c driver #0)
[   50.199247] msp3400 1-0040: MSP4418G-A2 supports nicam and radio, mode is autodetect and autoselect
[   50.200013] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   50.200137] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   50.200247] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   50.200294] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   50.200427] ivtv0: Registered device radio0 for encoder radio
[   50.200445] ivtv0: Registered device video16 for decoder MPEG (1 MB)
[   50.200479] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
[   50.200695] ivtv0: Registered device vbi16 for decoder VOUT
[   50.200713] ivtv0: Registered device video48 for decoder YUV (1 MB)
[   50.234258] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[   50.342009] tuner 1-0061: type set to 1 (Philips PAL_I (FI1246 and compatibles))
[   50.746877] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[   50.746895] ivtv:  ====================  END INIT IVTV  ====================
[   50.746970] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   50.746977] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[   51.497716] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   52.001799] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   52.001804] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   52.002552] PCI: Enabling device 0000:00:11.5 (0000 -> 0001)
[   52.002556] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   52.002685] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   52.530356] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 17 (level, low) -> IRQ 19
[   52.532607] Installing spdif_bug patch: Audigy 2 ZS [2001]
[   52.555498] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.555679] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   52.712491] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   52.712497] Uniform CD-ROM driver Revision: 3.20
[   52.714269] hdb: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   52.963312] fuse init (API version 7.8)
[   52.983282] lp0: using parport0 (interrupt-driven).
[   53.138461] Adding 1084284k swap on /dev/disk/by-uuid/17e7346f-e0e9-4811-a238-35f0fe7054e5.  Priority:-1 extents:1 across:1084284k
[   53.292033] EXT3 FS on sda3, internal journal
[   53.449633] NET: Registered protocol family 10
[   53.449704] lo: Disabled Privacy Extensions
[   64.307105] eth0: no IPv6 routers present
[   85.453564] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   85.525494] NTFS volume version 3.1.
[   85.570766] NTFS volume version 3.1.
[   85.603385] NTFS volume version 3.1.
[   85.624089] NTFS volume version 3.1.
[   85.641316] NTFS volume version 3.1.
[   85.664306] NTFS volume version 3.1.
[   85.700266] NTFS volume version 3.1.
[   85.746826] NTFS volume version 3.1.
[   85.792238] NTFS volume version 3.1.
[   85.827911] NTFS volume version 3.1.
[   85.862914] NTFS volume version 3.1.
[   91.987843] Using specific hotkey driver
[   92.055807] No dock devices found.
[   92.086538] input: Power Button (FF) as /class/input/input4
[   92.089887] ACPI: Power Button (FF) [PWRF]
[   92.114962] input: Power Button (CM) as /class/input/input5
[   92.118289] ACPI: Power Button (CM) [PWRB]
[   92.145191] input: Sleep Button (CM) as /class/input/input6
[   92.148452] ACPI: Sleep Button (CM) [SLPB]
[   92.155070] ibm_acpi: ec object not found
[   92.239852] pcc_acpi: loading...
[   92.409023] powernow-k8: Found 1 AMD Athlon(tm) 64 FX-53 Processor processors (version 2.00.00)
[   92.409049] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x2
[   92.409051] powernow-k8:    1 : fid 0x4 (1200 MHz), vid 0x12
[   97.393226] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[   97.393232] rt2500 EEPROM:  3  2  2  3  3  3  3  3  3  3  3  3  3  3  dBm Maximum
[   97.920705] ppdev: user-space parallel port driver
[   98.383331] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   98.383608] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   98.383888] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   99.632337] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   99.632354] apm: overridden by ACPI.
[   99.788503] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   99.872884] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   99.873313] NFSD: starting 90-second grace period
[   65.384000] Time: acpi_pm clocksource has been installed.
[   66.272000] Bluetooth: Core ver 2.11
[   66.272000] NET: Registered protocol family 31
[   66.272000] Bluetooth: HCI device and connection manager initialized
[   66.272000] Bluetooth: HCI socket layer initialized
[   66.344000] Bluetooth: L2CAP ver 2.8
[   66.344000] Bluetooth: L2CAP socket layer initialized
[   66.556000] Bluetooth: RFCOMM socket layer initialized
[   66.556000] Bluetooth: RFCOMM TTY layer initialized
[   66.556000] Bluetooth: RFCOMM ver 1.8
[   77.228000] eth0: no IPv6 routers present
ian@Jupiter-ubuntu:~$ 

```

I've tried alsamixer from terminal and it displays the mixer for the audigy with volumes at reasonable settings

Volume control for gnome also displays the same mixer settings....

does anyone know why I dont have audio anymore ?:(

ty Ian.

lspci
```
ian@Jupiter-ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0e.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GS] (rev a1)
ian@Jupiter-ubuntu:~$ 

```

lsmode
```
ian@Jupiter-ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  36284  0 
udf                    85252  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
powernow_k8            16064  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  1 
cpufreq_stats           7360  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
ac                      6020  0 
asus_acpi              17308  0 
button                  8720  0 
dock                   10268  0 
video                  16388  0 
battery                10756  0 
backlight               7040  1 asus_acpi
container               5248  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
nls_utf8                3072  11 
ntfs                  107764  11 
ipv6                  268960  12 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
msp3400                31648  0 
saa7127                12820  0 
saa7115                16400  0 
tuner                  61864  0 
nvidia               4713780  32 
generic                 5124  0 [permanent]
snd_emu10k1           121248  8 snd_emu10k1_synth
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_via82xx            29208  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_via82xx_modem      16008  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                38920  0 
serio_raw               7940  0 
ivtv                  134544  0 
snd_ac97_codec         98464  3 snd_emu10k1,snd_via82xx,snd_via82xx_modem
ac97_bus                3200  1 snd_ac97_codec
snd_mpu401_uart         9472  1 snd_via82xx
snd_rawmidi            25472  4 snd_seq_virmidi,snd_emu10k1,snd_seq_midi,snd_mpu401_uart
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
i2c_algo_bit            8712  1 ivtv
cx2341x                12804  1 ivtv
tveeprom               15888  1 ivtv
i2c_viapro             10132  0 
snd_pcm                79876  8 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_pcm_oss,snd_ac97_codec
snd_timer              23684  3 snd_emu10k1,snd_seq,snd_pcm
snd_page_alloc         10888  4 snd_emu10k1,snd_via82xx,snd_via82xx_modem,snd_pcm
rt2500                178276  1 
videodev               28160  1 ivtv
v4l2_common            25216  6 msp3400,saa7115,tuner,ivtv,cx2341x,videodev
v4l1_compat            15236  2 ivtv,videodev
i2c_core               22656  10 i2c_ec,msp3400,saa7127,saa7115,tuner,nvidia,ivtv,i2c_algo_bit,tveeprom,i2c_viapro
af_packet              23816  2 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
k8temp                  6656  0 
via82cxxx              10372  0 [permanent]
snd                    54020  27 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hwdep,snd_via82xx,snd_seq_oss,snd_via82xx_modem,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
sk98lin               156896  0 
soundcore               8672  1 snd
emu10k1_gp              4736  0 
gameport               16520  3 snd_via82xx,emu10k1_gp
amd64_agp              13700  1 
agpgart                35400  2 nvidia,amd64_agp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  17 
floppy                 59524  0 
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  3 ehci_hcd,uhci_hcd
ata_generic             9092  0 
sata_via               12548  9 
skge                   40848  0 
sata_promise           13316  5 
libata                125720  3 ata_generic,sata_via,sata_promise
scsi_mod              142348  4 sbp2,sg,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
ian@Jupiter-ubuntu:~$ 

```

---

### Post by Nossie on 2007-06-10
RESOLVED...

quoting from another forum....

> once you open alsamixer from the command line you will see a mixer panel.

there will be several slider bars and in between the slider bars some little boxes with sideways looking mm in it.
those little boxes with mm in them are switches to turn features on and off.
By using your arrow key -> you can move over to the proper switch to turn it on.

if its black with mm in it then it is presently turned off it will turn green when it is on.
you turn it on by moving cursor over till you are on it then type M
You will need to find the switch for analog/digital.
because if you are wired to analog and its set to digital you will get no sound.

Don't be fooled into thinking you are seeing all the switches keep pressing your arrow key to keep moving over till you find the analog switch.

I also had to switch for the Oss mixer too you can get an idea what it is going to be labled by going to sound control in your system tools. on the file menu there is an option to change mixers alsa or Oss and see what its calling the oss I think mine said audigy2 sigtel or something like that?


so hopefully not to confusing easiest way is to put in a cd and start it.
toggle a switch in alsamixer if you get sound that was the right one if you don't toggle it off again and move over to next switch.
mine were almost all the way over to the right just keep pressing that arrow key over till you see them.

gl; dan

---

### Post by dragonwings on 2007-06-19
try this it got mine going         sudo asoundconf set-default-card Audigy2

---

