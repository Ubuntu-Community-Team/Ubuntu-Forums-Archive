---
title: "Sound device not detected"
date: 2005-10-28
forum: Multimedia &amp; Video
---

### Post by BrianR on 2005-10-28
To start off I am a newbie at Linux...

I've installed Ubuntu 5.10 on an HP Vectra VLi8 SF (model D7850E) and everything seems to work except the sound. The sound device is onboard.
I didn't see any sound information in the output of dmesg. Any help would be much appreciated.

Here's my dmesg output:

[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5
20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000ea800 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[4294667.296000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 255MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65520
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 61424 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.2 present.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00
0f6f20
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x00000001  LTP 0x00000000) @
0x0fffb822
[4294667.296000] ACPI: FADT (v001 HP     HolmesHZ 0x00000001 PTL  0x00000001) @
0x0fffb84e
[4294667.296000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x00000001  LTP 0x00000001) @ 0x0ffffbd9
[4294667.296000] ACPI: DSDT (v001     HP HolmesHZ 0x00000001 MSFT 0x01000007) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x8008
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 10000000:eff80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01201000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 451.055 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.055000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294670.056000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.090000] Memory: 251140k/262080k available (1415k kernel code, 10288k reserved, 763k data, 224k init, 0k highmem)
[4294670.090000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.090000] Calibrating delay loop... 894.97 BogoMIPS (lpj=447488)
[4294670.110000] Security Framework v1.0.0 initialized
[4294670.110000] SELinux:  Disabled at boot.
[4294670.110000] Mount-cache hash table entries: 512
[4294670.110000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.110000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.110000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294670.110000] CPU: L2 cache: 512K
[4294670.110000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294670.110000] CPU: Intel Pentium III (Katmai) stepping 02
[4294670.110000] Enabling fast FPU save and restore... done.
[4294670.110000] Enabling unmasked SIMD FPU exception support... done.
[4294670.110000] Checking 'hlt' instruction... OK.
[4294670.114000] Checking for popad bug... OK.
[4294670.114000] checking if image is initramfs... it is
[4294671.911000] Freeing initrd memory: 5165k freed
[4294671.914000] ACPI: Looking for DSDT in initrd... not found!
[4294672.194000]  not found!
[4294672.212000] ACPI: setting ELCR to 0200 (from 0e00)
[4294672.214000] NET: Registered protocol family 16
[4294672.214000] EISA bus registered
[4294672.214000] ACPI: bus type pci registered
[4294672.215000] PCI: PCI BIOS revision 2.10 entry at 0xfd9a3, last bus=1
[4294672.215000] PCI: Using configuration type 1
[4294672.215000] mtrr: v2.0 (20020519)
[4294672.216000] ACPI: Subsystem revision 20050729
[4294672.257000] ACPI: Interpreter enabled
[4294672.257000] ACPI: Using PIC for interrupt routing
[4294672.258000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294672.258000] PCI: Probing PCI hardware (bus 00)
[4294672.258000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294672.293000] Boot video device is 0000:01:00.0
[4294672.297000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294672.352000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[4294672.353000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[4294672.354000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[4294672.355000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 9 10 *11 14 15)
[4294672.356000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294672.356000] pnp: PnP ACPI init
[4294672.443000] pnp: PnP ACPI: found 13 devices
[4294672.443000] PnPBIOS: Disabled by ACPI PNP
[4294672.443000] PCI: Using ACPI for IRQ routing
[4294672.443000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294672.447000] Simple Boot Flag value 0xff read from CMOS RAM was invalid
[4294672.447000] Simple Boot Flag at 0x3b set to 0x1
[4294672.448000] audit: initializing netlink socket (disabled)
[4294672.448000] audit: initialized
[4294672.449000] VFS: Disk quotas dquot_6.5.1
[4294672.449000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294672.449000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294672.449000] devfs: boot_options: 0x0
[4294672.449000] Initializing Cryptographic API
[4294672.449000] Limiting direct PCI/PCI transfers.
[4294672.449000] isapnp: Scanning for PnP cards...
[4294672.804000] isapnp: No Plug & Play device found
[4294672.908000] pnp: Device 00:02 activated.
[4294672.908000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PSM] at 0x60,0x64 irq 1,12
[4294672.911000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294672.911000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294672.911000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294672.911000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.912000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294672.922000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294672.923000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294672.924000] io scheduler noop registered
[4294672.924000] io scheduler anticipatory registered
[4294672.924000] io scheduler deadline registered
[4294672.924000] io scheduler cfq registered
[4294672.926000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294672.927000] EISA: Probing bus 0 at eisa.0
[4294672.927000] Cannot allocate resource for EISA slot 1
[4294672.927000] Cannot allocate resource for EISA slot 8
[4294672.927000] EISA: Detected 0 cards.
[4294672.927000] NET: Registered protocol family 2
[4294672.937000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294672.937000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294672.938000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294672.938000] TCP: Hash tables configured (established 16384 bind 16384)
[4294672.938000] NET: Registered protocol family 8
[4294672.938000] NET: Registered protocol family 20
[4294672.939000] ACPI wakeup devices:
[4294672.939000] PCI0 COMA  USB
[4294672.939000] ACPI: (supports S0 S1 S4 S5)
[4294672.940000] Freeing unused kernel memory: 224k freed
[4294672.955000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.007000] vga16fb: initializing
[4294673.007000] vga16fb: mapped to 0xc00a0000
[4294673.073000] Console: switching to colour frame buffer device 80x30
[4294673.073000] fb0: VGA16 VGA frame buffer device
[4294674.220000] Capability LSM initialized
[4294674.272000] NET: Registered protocol family 1
[4294674.325000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294674.325000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294674.326000] ACPI: bus type ide registered
[4294674.346000] PIIX4: IDE controller at PCI slot 0000:00:04.1
[4294674.346000] PIIX4: chipset revision 1
[4294674.346000] PIIX4: not 100% native mode: will probe irqs later
[4294674.346000]     ide0: BM-DMA at 0x1020-0x1027, BIOS settings: hda:DMA, hdb:pio
[4294674.346000]     ide1: BM-DMA at 0x1028-0x102f, BIOS settings: hdc:DMA, hdd:pio
[4294674.346000] Probing IDE interface ide0...
[4294674.610000] hda: ST320011A, ATA DISK drive
[4294674.916000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.916000] Probing IDE interface ide1...
[4294675.588000] hdc: CD-224E, ATAPI CD/DVD-ROM drive
[4294676.200000] ide1 at 0x170-0x177,0x376 on irq 15
[4294676.200000] Probing IDE interface ide2...
[4294676.713000] Probing IDE interface ide3...
[4294677.226000] Probing IDE interface ide4...
[4294677.739000] Probing IDE interface ide5...
[4294678.270000] hda: max request size: 128KiB
[4294678.270000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(33)
[4294678.270000] hda: cache flushes not supported
[4294678.270000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294678.332000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[4294678.332000] Uniform CD-ROM driver Revision: 3.20
[4294679.408000] Attempting manual resume
[4294679.408000] swsusp: Suspend partition has wrong signature?
[4294679.577000] usbcore: registered new driver usbfs
[4294679.577000] usbcore: registered new driver hub
[4294679.583000] USB Universal Host Controller Interface driver v2.2
[4294679.584000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294679.585000] PCI: setting IRQ 11 as level-triggered
[4294679.585000] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294679.585000] uhci_hcd 0000:00:04.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[4294679.647000] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[4294679.647000] uhci_hcd 0000:00:04.2: irq 11, io base 0x00001000
[4294679.647000] hub 1-0:1.0: USB hub found
[4294679.647000] hub 1-0:1.0: 2 ports detected
[4294679.722000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294679.722000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294679.722000] 0000:00:0b.0: 3Com PCI 3c905B Cyclone 100baseTx at 0x1080. Vers LK1.1.19
[4294682.924000] ACPI: CPU0 (power states: C1[C1])
[4294683.090000] Attempting manual resume
[4294683.091000] swsusp: Suspend partition has wrong signature?
[4294683.133000] kjournald starting.  Commit interval 5 seconds
[4294683.133000] EXT3-fs: mounted filesystem with ordered data mode.
[4294685.168000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294691.071000] Adding 369452k swap on /dev/hda5.  Priority:-1 extents:1
[4294691.305000] EXT3 FS on hda1, internal journal
[4294699.680000] parport: PnPBIOS parport detected.
[4294699.680000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294699.782000] lp0: using parport0 (interrupt-driven).
[4294699.888000] mice: PS/2 mouse device common for all mice
[4294700.297000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294701.374000] ts: Compaq touchscreen protocol output
[4294705.406000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294706.324000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294706.324000] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294706.324000] ide: failed opcode was: unknown
[4294706.324000] cdrom: open failed.
[4294708.607000] Linux agpgart interface v0.101 (c) Dave Jones
[4294708.635000] agpgart: Detected an Intel 440BX Chipset.
[4294708.703000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294709.047000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294709.126000] shpchp: shpc_init : shpc_cap_offset == 0
[4294709.126000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294710.088000] piix4_smbus 0000:00:04.3: Found 0000:00:04.3 device
[4294712.410000] Floppy drive(s): fd0 is 1.44M
[4294712.424000] FDC 0 is a National Semiconductor PC87306
[4294713.346000] Real Time Clock Driver v1.12
[4294713.632000] input: PC Speaker
[4294715.605000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294719.519000] NET: Registered protocol family 10
[4294719.520000] Disabled Privacy Extensions on device c02eb280(lo)
[4294719.521000] IPv6 over IPv4 tunneling driver
[4294721.991000] ACPI: Power Button (FF) [PWRF]
[4294722.418000] ibm_acpi: ec object not found
[4294729.668000] eth0: no IPv6 routers present
[4294734.335000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294734.335000] apm: overridden by ACPI.
[4294738.105000] Bluetooth: Core ver 2.7
[4294738.105000] NET: Registered protocol family 31
[4294738.105000] Bluetooth: HCI device and connection manager initialized
[4294738.105000] Bluetooth: HCI socket layer initialized
[4294738.182000] Bluetooth: L2CAP ver 2.7
[4294738.182000] Bluetooth: L2CAP socket layer initialized
[4294738.255000] Bluetooth: RFCOMM ver 1.5
[4294738.255000] Bluetooth: RFCOMM socket layer initialized
[4294738.255000] Bluetooth: RFCOMM TTY layer initialized

---

### Post by Kyral on 2005-10-28
Could you paste the output from lspci please?

---

### Post by fezzik on 2005-10-28
I am not that other person but here is my lspci.  I can't get sound working on here yet on this computer.  I don't know where to look.  The driver doesn't seem to be recognized.

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

---

### Post by BrianR on 2005-12-01
Sorry this has taken me so long to respond to. I've had other fires to put out.

Here's my lspci listing:

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:04.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:04.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:04.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200 AGP (rev 03)

---

