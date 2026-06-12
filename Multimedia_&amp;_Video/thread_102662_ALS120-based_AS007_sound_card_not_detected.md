---
title: "ALS120-based AS007 sound card not detected"
date: 2005-12-12
forum: Multimedia &amp; Video
---

### Post by nighttime on 2005-12-12
My system just won't detect my AS007 sound card (ALS120 based), I have tried lspci and I get nothing on "sound", It's an ISA PnP card, looks fine and the drivers got installed correctly under WinME so I suppose it's not a hardware problem.

I found what I think is the correct module for my card: snd-als100

So i tried

sudo modprobe snd-als100

but I only got

FATAL: Error inserting snd_als100 (/lib/modules/2.6.12-9-386/kernel/sound/isa/snd-als100.ko): No such device
FATAL: Error running install command for snd_als100

By the way, here'e what I got from dmesg:

```

[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 200 5
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000000fff3000 - 0000000010000000 (ACPI data)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 255MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65520
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 61424 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 VT8371                                ) @ 0x000f7e20[4294667.296000] ACPI: RSDT (v001 VT8371 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3000
[4294667.296000] ACPI: FADT (v001 VT8371 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3040
[4294667.296000] ACPI: DSDT (v001 VT8371 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x4008
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 10000000:efff0000)[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01201000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 1000.424 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294669.392000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294669.393000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.408000] Memory: 251524k/262080k available (1415k kernel code, 9944k reserved, 763k data, 224k init, 0k highmem)[4294669.408000] Checking if this processor honours the WP bit even in supervisor mode... Ok.[4294669.408000] Calibrating delay loop... 1982.46 BogoMIPS (lpj=991232)
[4294669.429000] Security Framework v1.0.0 initialized
[4294669.429000] SELinux:  Disabled at boot.
[4294669.429000] Mount-cache hash table entries: 512
[4294669.429000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000[4294669.429000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000[4294669.429000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[4294669.429000] CPU: L2 Cache: 256K (64 bytes/line)
[4294669.429000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000020 00000000 00000000 00000000[4294669.429000] CPU: AMD Athlon(tm) Processor stepping 02
[4294669.429000] Enabling fast FPU save and restore... done.
[4294669.429000] Checking 'hlt' instruction... OK.
[4294669.433000] Checking for popad bug... OK.
[4294669.433000] checking if image is initramfs... it is
[4294670.177000] Freeing initrd memory: 4821k freed
[4294670.185000] ACPI: Looking for DSDT in initrd... not found!
[4294670.291000]  not found!
[4294670.298000] ACPI: setting ELCR to 0200 (from 0e20)
[4294670.413000] NET: Registered protocol family 16
[4294670.413000] EISA bus registered
[4294670.413000] ACPI: bus type pci registered
[4294670.430000] PCI: PCI BIOS revision 2.10 entry at 0xfb4b0, last bus=1
[4294670.430000] PCI: Using configuration type 1
[4294670.430000] mtrr: v2.0 (20020519)
[4294670.430000] ACPI: Subsystem revision 20050729
[4294670.444000] ACPI: Interpreter enabled
[4294670.444000] ACPI: Using PIC for interrupt routing
[4294670.445000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.445000] PCI: Probing PCI hardware (bus 00)
[4294670.445000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294670.445000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.448000] Boot video device is 0000:01:00.0
[4294670.471000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.472000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[4294670.472000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.[4294670.473000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[4294670.474000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[4294670.479000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.479000] pnp: PnP ACPI init
[4294670.484000] pnp: PnP ACPI: found 12 devices
[4294670.484000] PnPBIOS: Disabled by ACPI PNP
[4294670.484000] PCI: Using ACPI for IRQ routing
[4294670.484000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report[4294670.503000] audit: initializing netlink socket (disabled)
[4294670.503000] audit: initialized
[4294670.503000] VFS: Disk quotas dquot_6.5.1
[4294670.503000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.503000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.503000] devfs: boot_options: 0x0
[4294670.503000] Initializing Cryptographic API
[4294670.503000] Applying VIA southbridge workaround.
[4294670.503000] PCI: Disabling Via external APIC routing
[4294670.503000] isapnp: Scanning for PnP cards...
[4294670.597000] isapnp: Card 'PnP Sound Chip'
[4294670.597000] isapnp: 1 Plug & Play card detected total
[4294670.627000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12[4294670.628000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.628000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.628000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled[4294670.628000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.628000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.631000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.632000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.632000] io scheduler noop registered
[4294670.632000] io scheduler anticipatory registered
[4294670.632000] io scheduler deadline registered
[4294670.632000] io scheduler cfq registered
[4294670.633000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize[4294670.633000] EISA: Probing bus 0 at eisa.0
[4294670.633000] Cannot allocate resource for EISA slot 4
[4294670.633000] Cannot allocate resource for EISA slot 5
[4294670.633000] Cannot allocate resource for EISA slot 6
[4294670.633000] EISA: Detected 0 cards.
[4294670.633000] NET: Registered protocol family 2
[4294670.643000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294670.643000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)[4294670.643000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.644000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.644000] NET: Registered protocol family 8
[4294670.644000] NET: Registered protocol family 20
[4294670.644000] ACPI wakeup devices:
[4294670.644000] SLPB PCI0 USB0 USB1 MODM UAR1 UAR2
[4294670.644000] ACPI: (supports S0 S1 S4 S5)
[4294670.645000] Freeing unused kernel memory: 224k freed
[4294670.670000] vga16fb: initializing
[4294670.670000] vga16fb: mapped to 0xc00a0000
[4294670.790000] Console: switching to colour frame buffer device 80x30
[4294670.790000] fb0: VGA16 VGA frame buffer device
[4294670.802000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.927000] Capability LSM initialized
[4294671.947000] NET: Registered protocol family 1
[4294671.968000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.968000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx[4294671.968000] ACPI: bus type ide registered
[4294671.977000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[4294671.977000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[4294671.977000] VP_IDE: chipset revision 6
[4294671.977000] VP_IDE: not 100% native mode: will probe irqs later
[4294671.977000] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1[4294671.977000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:pio[4294671.977000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:pio, hdd:DMA[4294671.977000] Probing IDE interface ide0...
[4294672.463000] hda: WDC WD400EB-00CPF0, ATA DISK drive
[4294673.076000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294673.076000] Probing IDE interface ide1...
[4294674.123000] hdd: LG CD-ROM CRD-8521B, ATAPI CD/DVD-ROM drive
[4294674.174000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.174000] Probing IDE interface ide2...
[4294674.687000] Probing IDE interface ide3...
[4294675.199000] Probing IDE interface ide4...
[4294675.711000] Probing IDE interface ide5...
[4294676.229000] hda: max request size: 128KiB
[4294676.243000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)[4294676.243000] hda: cache flushes not supported
[4294676.243000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294676.291000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache
[4294676.291000] Uniform CD-ROM driver Revision: 3.20
[4294676.689000] Attempting manual resume
[4294676.690000] swsusp: Suspend partition has wrong signature?
[4294676.762000] usbcore: registered new driver usbfs
[4294676.762000] usbcore: registered new driver hub
[4294676.764000] USB Universal Host Controller Interface driver v2.2
[4294676.765000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[4294676.765000] PCI: setting IRQ 5 as level-triggered
[4294676.765000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5[4294676.765000] uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller[4294676.827000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1[4294676.827000] uhci_hcd 0000:00:07.2: irq 5, io base 0x0000e400
[4294676.827000] hub 1-0:1.0: USB hub found
[4294676.827000] hub 1-0:1.0: 2 ports detected
[4294676.830000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5[4294676.830000] uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)[4294676.892000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2[4294676.892000] uhci_hcd 0000:00:07.3: irq 5, io base 0x0000e800
[4294676.892000] hub 2-0:1.0: USB hub found
[4294676.892000] hub 2-0:1.0: 2 ports detected
[4294676.939000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294676.940000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294676.940000] PCI: setting IRQ 11 as level-triggered
[4294676.940000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11[4294676.941000] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.[4294676.944000] eth0: ADMtek Comet rev 17 at 0001ec00, 00:12:17:56:2C:9D, IRQ 11.[4294679.486000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294679.486000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294679.690000] Attempting manual resume
[4294679.690000] swsusp: Suspend partition has wrong signature?
[4294679.714000] kjournald starting.  Commit interval 5 seconds
[4294679.714000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.400000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.322000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1
[4294686.657000] EXT3 FS on hda1, internal journal
[4294694.723000] parport_pc: VIA 686A/8231 detected
[4294694.723000] parport_pc: probing current configuration
[4294694.723000] parport_pc: Current parallel port base: 0x378
[4294694.723000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[4294694.805000] parport_pc: VIA parallel port: io=0x378, irq=7
[4294694.815000] lp0: using parport0 (interrupt-driven).
[4294694.862000] mice: PS/2 mouse device common for all mice
[4294695.429000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294695.888000] ts: Compaq touchscreen protocol output
[4294698.590000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com[4294699.770000] cdrom: open failed.
[4294702.961000] Linux agpgart interface v0.101 (c) Dave Jones
[4294702.978000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[4294703.001000] agpgart: AGP aperture is 64M @ 0xd0000000
[4294703.173000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294703.184000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294703.184000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294705.666000] Real Time Clock Driver v1.12
[4294705.835000] input: PC Speaker
[4294706.007000] Floppy drive(s): fd0 is 1.44M
[4294706.049000] FDC 0 is a post-1991 82077
[4294706.630000] pnp: Device 01:01.02 activated.
[4294706.648000] gameport: NS558 PnP Gameport is pnp01:01.02/gameport0, io 0x200, speed 602kHz[4294708.700000] NET: Registered protocol family 17
[4294711.681000] 0000:00:09.0: tulip_stop_rxtx() failed
[4294711.681000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.[4294712.898000] NET: Registered protocol family 10
[4294712.898000] Disabled Privacy Extensions on device c02eb280(lo)
[4294712.899000] IPv6 over IPv4 tunneling driver
[4294718.285000] ACPI: Power Button (FF) [PWRF]
[4294718.286000] ACPI: Power Button (CM) [PWRB]
[4294718.286000] ACPI: Sleep Button (CM) [SLPB]
[4294718.488000] ibm_acpi: ec object not found
[4294723.229000] eth0: no IPv6 routers present
[4294729.904000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294729.904000] apm: overridden by ACPI.
[4294731.203000] powernow: No powernow capabilities detected
[4294731.972000] Bluetooth: Core ver 2.7
[4294731.972000] NET: Registered protocol family 31
[4294731.972000] Bluetooth: HCI device and connection manager initialized
[4294731.972000] Bluetooth: HCI socket layer initialized
[4294732.705000] Bluetooth: L2CAP ver 2.7
[4294732.705000] Bluetooth: L2CAP socket layer initialized
[4294732.752000] Bluetooth: RFCOMM ver 1.5
[4294732.752000] Bluetooth: RFCOMM socket layer initialized
[4294732.752000] Bluetooth: RFCOMM TTY layer initialized
[4295684.401000] pnp: Unable to assign resources to device 01:01.00.
[4295684.401000] als100: AUDIO pnp configure failure
[4295684.410000] no ALS100 based soundcards found
[4295741.261000] pnp: Unable to assign resources to device 01:01.00.
[4295741.261000] als100: AUDIO pnp configure failure
[4295741.271000] no ALS100 based soundcards found

```
At the very end I see these messages about "no ALS100 based soundcards found", but I'm positive mine is ALS120 based, it says so on the chip and I've looked the card up in google... also at the ALSA webste it says ALSA supports ALS1x0 based cards so... I don't know what's wrong.

And from lsmod | grep "snd" i got...

```
snd_opl3_lib            9856  0
snd_hwdep               8608  1 snd_opl3_lib
snd_sb16_dsp            9856  0
snd_sb_common          14336  1 snd_sb16_dsp
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  2 snd_sb16_dsp,snd_pcm_oss
snd_timer              21764  2 snd_opl3_lib,snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_mpu401_uart         6784  0
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  2 snd_opl3_lib,snd_rawmidi
snd                    48644  11 snd_opl3_lib,snd_hwdep,snd_sb16_dsp,snd_sb_common,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
```

---

