---
title: "webcam stopped working after update then ok, now stopped"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by tommawat on 2007-12-20
Hi.  I am using a Dell Inspiron 1000 notebook running Ubuntu 7.10.  I have a webcam which worked fine under Feisty 7.04 but after upgrading to Gutsy 7.10 the camera is not detected.  Then somehow, it was detected and worked with camorama and skype beta 2.0 (I used it for a video call over 30 mins flawlessly!) but now it has somehow gone back to not working.  In Skype, I test the video, and it correctly identifies my webcam but the display is green where the video feed used to be.  

I have checked the forum, one post marked solved is in fact still unsolved (the answer was posted to buy a new camera...not exactly solving anything but changing the camera).

I added my username to the video group I think, but that still does nothing (maybe i did this incorrectly???).  Besides it worked before I did that anyway so I dont see why I should add it now.

When I type dmesg into the terminal, get this long output which identifies my camera, but still camorama and skype cannot use it.  I cannot find  the /dev/vid folder

Any suggestions where to go from here?  I dont really want to do a clean install of Gutsy, but I think I am leaning in that direction.  Ugh.  Any help would be really appreciated!  Thanks in advance...


thomas@groundhog:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d6000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004bdf0000 (usable)
[    0.000000]  BIOS-e820: 000000004bdf0000 - 000000004bdff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000004bdff000 - 000000004be00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004be00000 - 0000000050000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 317MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7ad0
[    0.000000] Entering add_active_range(0, 0, 310768) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   310768
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   310768
[    0.000000] On node 0 totalpages: 310768
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 635 pages used for memmap
[    0.000000]   HighMem zone: 80757 pages, LIFO batch:15
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7B90 checksum 0
[    0.000000] ACPI: RSDP 000F7B90, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 4BDFBE41, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 4BDFEF46, 0074 (r1 Dell   Ins 1000  6040000 MSTF  100000E)
[    0.000000] ACPI: DSDT 4BDFBE6D, 30D9 (r1    WIN Inspiron  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 4BDFFFC0, 0040
[    0.000000] ACPI: APIC 4BDFEFBA, 0046 (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] Built 1 zonelists.  Total pages: 308341
[    0.000000] Kernel command line: root=UUID=438fd025-3411-448d-a45a-623275ecd1b4 ro quiet splash vga=792
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2193.135 MHz processor.
[   18.009363] Console: colour dummy device 80x25
[   18.010286] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.011804] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.082109] Memory: 1220632k/1243072k available (2015k kernel code, 21528k reserved, 916k data, 364k init, 325568k highmem)
[   18.082124] virtual kernel memory layout:
[   18.082125]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   18.082127]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.082128]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.082131]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.082132]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   18.082134]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   18.082135]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   18.082139] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.082206] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   18.162016] Calibrating delay using timer specific routine.. 4386.21 BogoMIPS (lpj=8772434)
[   18.162067] Security Framework v1.0.0 initialized
[   18.162082] SELinux:  Disabled at boot.
[   18.162100] Mount-cache hash table entries: 512
[   18.162395] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   18.162412] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   18.162416] CPU: L2 cache: 256K
[   18.162420] CPU: Hyper-Threading is disabled
[   18.162423] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b080 00004400 00000000 00000000
[   18.162441] Compat vDSO mapped to ffffe000.
[   18.162464] Checking 'hlt' instruction... OK.
[   18.178152] SMP alternatives: switching to UP code
[   18.178609] Freeing SMP alternatives: 11k freed
[   18.179105] Early unpacking initramfs... done
[   18.610395] ACPI: Core revision 20070126
[   18.610478] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.613567] CPU0: Intel Mobile Intel(R) Celeron(R) CPU 2.20GHz stepping 09
[   18.613620] Total of 1 processors activated (4386.21 BogoMIPS).
[   18.613738] ENABLING IO-APIC IRQs
[   18.613939] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   18.760406] Brought up 1 CPUs
[   18.760602] Booting paravirtualized kernel on bare hardware
[   18.760706] Time:  6:43:17  Date: 11/20/107
[   18.760749] NET: Registered protocol family 16
[   18.760931] EISA bus registered
[   18.760955] ACPI: bus type pci registered
[   18.762743] PCI: PCI BIOS revision 2.10 entry at 0xfd9b6, last bus=1
[   18.762746] PCI: Using configuration type 1
[   18.762748] Setting up standard PCI resources
[   18.778224] ACPI: EC: Look up EC in DSDT
[   18.778750] ACPI: EC: GPE=0x1b, ports=0x66, 0x62
[   18.779911] ACPI: Interpreter enabled
[   18.779917] ACPI: (supports S0 S3 S4 S5)
[   18.779940] ACPI: Using IOAPIC for interrupt routing
[   18.787946] ACPI: EC: GPE=0x1b, ports=0x66, 0x62
[   18.788063] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.788081] PCI: Probing PCI hardware (bus 00)
[   18.788391] Enabling SiS 96x SMBus.
[   18.789346] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.795880] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 10)
[   18.796053] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10) *9
[   18.796145] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10)
[   18.796328] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 7 10)
[   18.796447] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10) *9
[   18.796539] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 *10)
[   18.796634] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10) *0, disabled.
[   18.796727] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10)
[   18.796972] ACPI: Power Resource [QFAN] (off)
[   18.796988] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.797012] pnp: PnP ACPI init
[   18.797038] ACPI: bus type pnp registered
[   18.799871] pnp: PnP ACPI: found 8 devices
[   18.799875] ACPI: ACPI bus type pnp unregistered
[   18.799882] PnPBIOS: Disabled by ACPI PNP
[   18.799989] PCI: Using ACPI for IRQ routing
[   18.799994] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.803504] NET: Registered protocol family 8
[   18.803507] NET: Registered protocol family 20
[   18.803658] pnp: 00:04: ioport range 0x8000-0x808f has been reserved
[   18.803664] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
[   18.803667] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   18.803671] pnp: 00:04: ioport range 0xfe00-0xfe00 has been reserved
[   18.803676] pnp: 00:04: iomem range 0xfee00000-0xfee00fff could not be reserved
[   18.803680] pnp: 00:04: iomem range 0xffee0000-0xffef5fff has been reserved
[   18.803684] pnp: 00:04: iomem range 0xffef6000-0xffefffff has been reserved
[   18.803687] pnp: 00:04: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   18.804226] Time: tsc clocksource has been installed.
[   18.834336] PCI: Bridge: 0000:00:01.0
[   18.834342]   IO window: 9000-9fff
[   18.834350]   MEM window: e4300000-e43fffff
[   18.834356]   PREFETCH window: e8000000-efffffff
[   18.834364] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   18.834367]   IO window: 00001c00-00001cff
[   18.834372]   IO window: 00002000-000020ff
[   18.834378]   PREFETCH window: 60000000-63ffffff
[   18.834384]   MEM window: 64000000-67ffffff
[   18.834426] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 16
[   18.834452] NET: Registered protocol family 2
[   18.872103] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.872358] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   18.875073] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.876075] TCP: Hash tables configured (established 131072 bind 65536)
[   18.876081] TCP reno registered
[   18.888254] checking if image is initramfs... it is
[   19.334745] Switched to high resolution mode on CPU 0
[   19.627155] Freeing initrd memory: 7118k freed
[   19.627840] audit: initializing netlink socket (disabled)
[   19.627864] audit(1198132997.120:1): initialized
[   19.627993] highmem bounce pool size: 64 pages
[   19.631587] VFS: Disk quotas dquot_6.5.1
[   19.631707] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.631907] io scheduler noop registered
[   19.631911] io scheduler anticipatory registered
[   19.631914] io scheduler deadline registered
[   19.631948] io scheduler cfq registered (default)
[   20.061713] Boot video device is 0000:01:00.0
[   20.062062] isapnp: Scanning for PnP cards...
[   20.415166] isapnp: No Plug & Play device found
[   20.512233] Real Time Clock Driver v1.12ac
[   20.512390] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.514417] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
[   20.514429] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   20.515577] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.516000] input: Macintosh mouse button emulation as /class/input/input0
[   20.516168] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.520228] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.520240] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.520625] mice: PS/2 mouse device common for all mice
[   20.520877] EISA: Probing bus 0 at eisa.0
[   20.520890] Cannot allocate resource for EISA slot 1
[   20.520893] Cannot allocate resource for EISA slot 2
[   20.520914] Cannot allocate resource for EISA slot 8
[   20.520917] EISA: Detected 0 cards.
[   20.521078] TCP cubic registered
[   20.521099] NET: Registered protocol family 1
[   20.521136] Using IPI No-Shortcut mode
[   20.521424]   Magic number: 3:857:721
[   20.522221] Freeing unused kernel memory: 364k freed
[   20.588194] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.003315] AppArmor: AppArmor initialized<5>audit(1198132999.620:2):  type=1505 info="AppArmor initialized" pid=1164
[   22.112196] fuse init (API version 7.8)
[   22.120740] Failure registering capabilities with primary security module.
[   22.236164] ACPI: Transitioning device [FAN] to D3
[   22.236170] ACPI: Transitioning device [FAN] to D3
[   22.236176] ACPI: Fan [FAN] (off)
[   22.329211] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   22.329221] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.528912] ACPI: Thermal Zone [THRM] (68 C)
[   24.331890] SCSI subsystem initialized
[   24.338760] libata version 2.21 loaded.
[   24.342977] pata_sis 0000:00:02.5: version 0.5.1
[   24.343028] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 18
[   24.343216] scsi0 : pata_sis
[   24.343308] scsi1 : pata_sis
[   24.343451] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00012800 irq 14
[   24.343456] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00012808 irq 15
[   24.433453] usbcore: registered new interface driver usbfs
[   24.433497] usbcore: registered new interface driver hub
[   24.433537] usbcore: registered new device driver usb
[   24.434775] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.469922] sis900.c: v1.08.10 Apr. 2 2006
[   24.505257] ata1.00: ATA-6: FUJITSU MHT2040AT, 0022, max UDMA/100
[   24.505263] ata1.00: 78140160 sectors, multi 16: LBA 
[   24.521271] ata1.00: configured for UDMA/100
[    6.480000] Marking TSC unstable due to: possible TSC halt in C2.
[    6.500000] Time: acpi_pm clocksource has been installed.
[    6.648000] Clocksource tsc unstable (delta = -94790853 ns)
[    6.668000] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW242C, UQ81, max UDMA/33
[    6.840000] ata2.00: configured for UDMA/33
[    6.840000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2040A 0022 PQ: 0 ANSI: 5
[    6.840000] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242C UQ81 PQ: 0 ANSI: 5
[    6.840000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 19
[    6.840000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    6.840000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    6.840000] ohci_hcd 0000:00:03.0: irq 19, io mem 0xe4000000
[    6.872000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    6.872000] sd 0:0:0:0: [sda] Write Protect is off
[    6.872000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.872000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.872000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    6.872000] sd 0:0:0:0: [sda] Write Protect is off
[    6.872000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.872000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.872000]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[    6.896000] hub 1-0:1.0: USB hub found
[    6.896000] hub 1-0:1.0: 3 ports detected
[    6.940000]  sda1 sda2 < sda5 >
[    6.976000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.984000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.984000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    7.000000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 20
[    7.000000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    7.000000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    7.000000] ohci_hcd 0000:00:03.1: irq 20, io mem 0xe4001000
[    7.004000] sr0: scsi3-mmc drive: 1x/24x writer cd/rw xa/form2 cdda tray
[    7.004000] Uniform CD-ROM driver Revision: 3.20
[    7.004000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.056000] usb usb2: configuration #1 chosen from 1 choice
[    7.056000] hub 2-0:1.0: USB hub found
[    7.056000] hub 2-0:1.0: 3 ports detected
[    7.160000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 21
[    7.160000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    7.172000] 0000:00:04.0: Using transceiver found at address 1 as default
[    7.176000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 21, 00:11:43:3c:b4:c6.
[    7.176000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 22
[    7.176000] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    7.176000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[    7.176000] PCI: cache line size of 128 is not supported by device 0000:00:03.2
[    7.176000] ehci_hcd 0000:00:03.2: irq 22, io mem 0xe4002000
[    7.304000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    7.304000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.304000] usb usb3: configuration #1 chosen from 1 choice
[    7.304000] hub 3-0:1.0: USB hub found
[    7.304000] hub 3-0:1.0: 6 ports detected
[    7.400000] Attempting manual resume
[    7.400000] swsusp: Resume From Partition 8:5
[    7.400000] PM: Checking swsusp image.
[    7.400000] PM: Resume from disk failed.
[    7.488000] kjournald starting.  Commit interval 5 seconds
[    7.488000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.352000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    8.556000] usb 1-1: configuration #1 chosen from 1 choice
[    8.860000] usb 1-2: new full speed USB device using ohci_hcd and address 4
[    9.068000] usb 1-2: configuration #1 chosen from 1 choice
[   22.136000] NET: Registered protocol family 10
[   22.136000] lo: Disabled Privacy Extensions
[   22.756000] eth0: Media Link On 100mbps full-duplex 
[   23.492000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.556000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[   23.720000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.768000] agpgart: Detected SiS chipset - id:1616
[   23.768000] agpgart: unable to determine aperture size.
[   23.768000] agpgart: agp_backend_initialize() failed.
[   23.768000] agpgart-sis: probe of 0000:00:00.0 failed with error -22
[   23.968000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.024000] Yenta: CardBus bridge found at 0000:00:0a.0 [1028:0195]
[   24.024000] Yenta: Enabling burst memory read transactions
[   24.024000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   24.024000] Yenta: Routing CardBus interrupts to PCI
[   24.024000] Yenta TI: socket 0000:00:0a.0, mfunc 0x012c1222, devctl 0x66
[   24.256000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   24.256000] Socket status: 30000020
[   24.296000] input: PC Speaker as /class/input/input2
[   24.608000] input: PS/2 Mouse as /class/input/input3
[   24.624000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   24.732000] usbcore: registered new interface driver hiddev
[   24.740000] input: HID 062a:0000 as /class/input/input5
[   24.740000] input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:03.0-1
[   24.740000] usbcore: registered new interface driver usbhid
[   24.740000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.760000] Linux video capture interface: v2.00
[   24.824000] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[   24.828000] usb 1-2: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613B)
[   24.892000] pccard: CardBus card inserted into slot 0
[   25.044000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   25.044000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[   25.044000] cs: IO port probe 0x820-0x8ff: clean.
[   25.044000] cs: IO port probe 0xc00-0xcf7: clean.
[   25.048000] cs: IO port probe 0xa00-0xaff: clean.
[   25.120000] ath_hal: module license 'Proprietary' taints kernel.
[   25.124000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   25.152000] usb 1-2: OV7660 image sensor detected
[   25.280000] wlan: 0.8.4.2 (0.9.3.2)
[   25.372000] ath_pci: 0.9.4.5 (0.9.3.2)
[   25.372000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   25.372000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   26.012000] ath_rate_sample: 1.2 (0.9.3.2)
[   26.048000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   26.048000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   26.048000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   26.048000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   26.048000] wifi0: mac 7.9 phy 4.5 radio 5.6
[   26.048000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   26.048000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   26.048000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   26.048000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   26.048000] wifi0: Use hw queue 8 for CAB traffic
[   26.048000] wifi0: Use hw queue 9 for beacons
[   26.192000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
[   26.196000] wifi0: Atheros 5212: mem=0x64000000, irq=16
[   26.560000] AC'97 0 analog subsections not ready
[   26.616000] NET: Registered protocol family 17
[   27.128000] intel8x0_measure_ac97_clock: measured 55418 usecs
[   27.128000] intel8x0: clocking to 48000
[   28.196000] usb 1-2: Initialization succeeded
[   28.200000] usb 1-2: V4L2 device registered as /dev/video0
[   28.200000] usb 1-2: Optional device control through 'sysfs' interface disabled
[   28.200000] usbcore: registered new interface driver sn9c102
[   28.316000] usbcore: registered new interface driver gspca
[   28.316000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   29.220000] lp: driver loaded but no devices found
[   29.304000] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   29.940000] EXT3 FS on sda1, internal journal
[   32.824000] eth0: no IPv6 routers present
[   34.036000] input: Power Button (FF) as /class/input/input6
[   34.044000] ACPI: Power Button (FF) [PWRF]
[   34.092000] input: Lid Switch as /class/input/input7
[   34.100000] ACPI: Lid Switch [LID]
[   34.148000] input: Power Button (CM) as /class/input/input8
[   34.156000] ACPI: Power Button (CM) [PWB]
[   34.372000] ACPI: Battery Slot [BAT1] (battery present)
[   34.484000] No dock devices found.
[   34.568000] ACPI: AC Adapter [ACAD] (off-line)
[   36.448000] ath0: no IPv6 routers present
[   36.768000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 17
[   42.304000] ppdev: user-space parallel port driver
[   44.520000] audit(1198133041.530:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4844 profile="/usr/sbin/cupsd"
[   44.808000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   44.808000] apm: overridden by ACPI.
[   46.692000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   46.832000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   46.844000] NFSD: starting 90-second grace period
[   50.304000] Failure registering capabilities with primary security module.
[   53.332000] /dev/vmmon[5395]: VMCI: Driver initialized.
[   53.332000] /dev/vmmon[5395]: Module vmmon: registered with major=10 minor=165
[   53.332000] /dev/vmmon[5395]: Module vmmon: initialized
[   53.472000] /dev/vmnet: open called by PID 5416 (vmnet-bridge)
[   53.472000] /dev/vmnet: hub 0 does not exist, allocating memory.
[   53.476000] /dev/vmnet: port on hub 0 successfully opened
[   53.476000] bridge-eth0: enabling the bridge
[   53.476000] bridge-eth0: up
[   53.476000] bridge-eth0: already up
[   53.476000] bridge-eth0: attached
[   53.780000] /dev/vmnet: open called by PID 5430 (vmnet-natd)
[   53.780000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   53.784000] /dev/vmnet: port on hub 8 successfully opened
[   64.160000] /dev/vmnet: open called by PID 5543 (vmnet-netifup)
[   64.160000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   64.160000] /dev/vmnet: port on hub 1 successfully opened
[   64.188000] /dev/vmnet: open called by PID 5544 (vmnet-netifup)
[   64.188000] /dev/vmnet: port on hub 8 successfully opened
[   67.188000] /dev/vmnet: open called by PID 5566 (vmnet-dhcpd)
[   67.188000] /dev/vmnet: port on hub 8 successfully opened
[   67.192000] /dev/vmnet: open called by PID 5567 (vmnet-dhcpd)
[   67.192000] /dev/vmnet: port on hub 1 successfully opened
[   74.684000] vmnet8: no IPv6 routers present
[   75.096000] vmnet1: no IPv6 routers present
[ 3727.924000] usb 1-2: USB disconnect, address 4
[ 3727.924000] usb 1-2: Disconnecting SN9C1xx PC Camera...
[ 3727.924000] usb 1-2: V4L2 device /dev/video0 deregistered
[ 3731.416000] usb 1-2: new full speed USB device using ohci_hcd and address 5
[ 3731.624000] usb 1-2: configuration #1 chosen from 1 choice
[ 3731.628000] usb 1-2: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613B)
[ 3731.940000] usb 1-2: OV7660 image sensor detected
[ 3734.332000] usb 1-2: Initialization succeeded
[ 3734.332000] usb 1-2: V4L2 device registered as /dev/video0
[ 3734.332000] usb 1-2: Optional device control through 'sysfs' interface disabled
[ 4457.944000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[ 4458.156000] usb 2-1: configuration #1 chosen from 1 choice
[ 4458.160000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[ 4478.896000] usb 2-1: USB disconnect, address 2
[ 4482.824000] usb 2-1: new full speed USB device using ohci_hcd and address 3
[ 4483.036000] usb 2-1: configuration #1 chosen from 1 choice
[ 4483.040000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[ 4483.836000] usb 1-2: USB disconnect, address 5
[ 4483.836000] usb 1-2: Disconnecting SN9C1xx PC Camera...
[ 4483.836000] usb 1-2: V4L2 device /dev/video0 deregistered
[ 5940.048000] usb 2-1: USB disconnect, address 3
[ 5946.532000] usb 1-2: new full speed USB device using ohci_hcd and address 6
[ 5946.740000] usb 1-2: configuration #1 chosen from 1 choice
[ 5946.744000] usb 1-2: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613B)
[ 5947.056000] usb 1-2: OV7660 image sensor detected
[ 5949.472000] usb 1-2: Initialization succeeded
[ 5949.472000] usb 1-2: V4L2 device registered as /dev/video0
[ 5949.472000] usb 1-2: Optional device control through 'sysfs' interface disabled
thomas@groundhog:~$

---

### Post by tommawat on 2007-12-20
As above, I got this info as well to add:

thomas@groundhog:~$ lsmod | grep videodev
videodev               29312  2 gspca,sn9c102
v4l1_compat            15364  1 videodev
v4l2_common            18432  2 sn9c102,videodev
thomas@groundhog:~$ 

related topics in the forum can be found here, but offer no solutions for me that I can tell...

[http://ubuntuforums.org/showthread.php?t=615560&highlight=webcam+cannot+work](http://ubuntuforums.org/showthread.php?t=615560&highlight=webcam+cannot+work)

[http://ubuntuforums.org/showthread.php?t=611816](http://ubuntuforums.org/showthread.php?t=611816)

[http://ubuntuforums.org/showthread.php?t=621815](http://ubuntuforums.org/showthread.php?t=621815)

---

### Post by tommawat on 2008-01-11
hi there again.  anyone have any suggestions about how to make a webcam work again?  i have some more info to add again. 

on my same notebook, i have run the live CD for 7.10, installed skype and it works with my camera.  however, on the same notebook with the 7.10 installed on the hard drive the camera wont work.  

skype shows different info from live to hard drive versions:
skype live detects Surfer Model sn-206 as the camera and works.
skype on my hard drive install detects SN9C1xx PC Camera and does not work.

dmesg into terminal on live system returns:
[COLOR="Red"][  149.972000] Linux video capture interface: v2.00
[  150.120000 ] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. SONIX JPEG (sn9c1xx)
[  150.124000] usbcore: registered new interface driver gspca
[  150.124000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22 /debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[  150.648000] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1: 1.44
[  150.648000] usbcore: registered new interface driver sn9c102[/COLOR]

dmesg on hard drive install returns:

[COLOR="Red"][   25.028000] Linux video capture interface: v2.00
[   25.104000] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[   25.108000] usb 2-1: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613B)
[   25.424000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   25.424000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[   25.424000] cs: IO port probe 0x820-0x8ff: clean.
[   25.428000] cs: IO port probe 0xc00-0xcf7: clean.
[   25.428000] cs: IO port probe 0xa00-0xaff: clean.
[   25.516000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 17
[   25.544000] usb 2-1: OV7660 image sensor detected
[   26.440000] intel8x0_measure_ac97_clock: measured 55442 usecs
[   26.440000] intel8x0: clocking to 48000
[   27.940000] usb 2-1: Initialization succeeded
[   27.940000] usb 2-1: V4L2 device registered as /dev/video0
[   27.940000] usb 2-1: Optional device control through 'sysfs' interface disabled
[   27.940000] usbcore: registered new interface driver sn9c102
[   28.052000] usbcore: registered new interface driver gspca
[   28.052000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   29.216000] lp: driver loaded but no devices found
[   29.296000] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[/COLOR]

is there any way to return my hard drive install to the settings found on the live cd?

---

### Post by tommawat on 2008-01-24
i just ended up reinstalling my whole system from a newly burned cd.  it must have used the old drivers or whatever, b/c now its recognized and works.

oh well, win some lose some.

next time.

---

