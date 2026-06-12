---
title: "alsamixer"
date: 2005-12-22
forum: Multimedia &amp; Video
---

### Post by Cprav on 2005-12-22
Hi all,
First of all a warning - I'm very much a newbie!

I've been having problems getting my soundcard to work and I think the problem is the alsamixer.  When I enter it in the terminal it basically says it doesn't exist and on startup and shutdown something starting with alsa 'fails'.  Is there somewhere I can download it?  I tried searching for it in add/remove programs but couldn't find it.

I found something here:
[http://www.stud.fit.vutbr.cz/~xhlavk00/AlsaMixer.app/](http://www.stud.fit.vutbr.cz/~xhlavk00/AlsaMixer.app/)
If this is something I should try, where do I download the files (do I download all three?)  where do I input all that code?

Thanks guys!  Can't wait to hear sound again! :)

---

### Post by gnu2tux on 2005-12-22
Hi,

 It's most likely that there is a problem with the driver, rather than the lack of the alsamixer program, which is not necessary for audio.

Can you type dmesg at the prompt and paste anything to do with alsa or sound back here.

If dmesg has nothing, have a look in /var/log/syslog and /var/log/messages (as root).

Finally, type lsmod and lspci and paste that back here.

explanations- 
* dmesg prints the output of the startup messages
* /var/log/* are the main system logs
* lsmod shows the list of all the drivers (or modules) that the kernel has loaded, we are looking for alsa and alsa-related drivers in this list.
* lspci shows the content of the pci bus (all cards), telling us what type of sound card you have.

Regards

---

### Post by Cprav on 2005-12-27
Thanks so much!  Sorry I haven't been on lately, it's been a while since I've had a chance to get on the computer.  Here is what came up when I entered that.

Thanks again!

justine@ubuntu:~$ dmesg
0 (01201000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 1010.354 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294668.929000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294668.930000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.948000] Memory: 251524k/262080k available (1415k kernel code, 9944k reserved, 763k data, 224k init, 0k highmem)
[4294668.948000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.949000] Calibrating delay loop... 2002.94 BogoMIPS (lpj=1001472)
[4294668.970000] Security Framework v1.0.0 initialized
[4294668.970000] SELinux:  Disabled at boot.
[4294668.970000] Mount-cache hash table entries: 512
[4294668.970000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[4294668.970000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[4294668.970000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294668.970000] CPU: L2 Cache: 256K (64 bytes/line)
[4294668.970000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000020 00000000 00000000 00000000
[4294668.970000] CPU: AMD Athlon(tm) Processor stepping 02
[4294668.970000] Enabling fast FPU save and restore... done.
[4294668.970000] Checking 'hlt' instruction... OK.
[4294668.974000] Checking for popad bug... OK.
[4294668.974000] checking if image is initramfs... it is
[4294669.729000] Freeing initrd memory: 4821k freed
[4294669.735000] ACPI: Looking for DSDT in initrd... not found!
[4294669.844000]  not found!
[4294669.851000] ACPI: setting ELCR to 0800 (from 0e20)
[4294669.852000] NET: Registered protocol family 16
[4294669.852000] EISA bus registered
[4294669.852000] ACPI: bus type pci registered
[4294669.867000] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[4294669.867000] PCI: Using configuration type 1
[4294669.867000] mtrr: v2.0 (20020519)
[4294669.868000] ACPI: Subsystem revision 20050729
[4294669.880000] ACPI: Interpreter enabled
[4294669.880000] ACPI: Using PIC for interrupt routing
[4294669.880000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.880000] PCI: Probing PCI hardware (bus 00)
[4294669.880000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.884000] Boot video device is 0000:01:05.0
[4294669.885000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.889000] ACPI: Power Resource [URP1] (off)
[4294669.889000] ACPI: Power Resource [URP2] (off)
[4294669.889000] ACPI: Power Resource [FDDP] (off)
[4294669.889000] ACPI: Power Resource [LPTP] (off)
[4294669.890000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[4294669.890000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[4294669.891000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[4294669.891000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[4294669.891000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.891000] pnp: PnP ACPI init
[4294669.896000] pnp: PnP ACPI: found 11 devices
[4294669.896000] PnPBIOS: Disabled by ACPI PNP
[4294669.896000] PCI: Using ACPI for IRQ routing
[4294669.896000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.898000] pnp: 00:00: ioport range 0xde00-0xde03 has been reserved
[4294669.899000] audit: initializing netlink socket (disabled)
[4294669.899000] audit: initialized
[4294669.899000] VFS: Disk quotas dquot_6.5.1
[4294669.900000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.900000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.900000] devfs: boot_options: 0x0
[4294669.900000] Initializing Cryptographic API
[4294669.900000] isapnp: Scanning for PnP cards...
[4294670.254000] isapnp: No Plug & Play device found
[4294670.284000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294670.286000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.286000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.286000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.286000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.287000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.290000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.290000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.290000] io scheduler noop registered
[4294670.290000] io scheduler anticipatory registered
[4294670.290000] io scheduler deadline registered
[4294670.290000] io scheduler cfq registered
[4294670.291000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.292000] EISA: Probing bus 0 at eisa.0
[4294670.292000] Cannot allocate resource for EISA slot 5
[4294670.292000] EISA: Detected 0 cards.
[4294670.292000] NET: Registered protocol family 2
[4294670.302000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294670.302000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294670.302000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.303000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.303000] NET: Registered protocol family 8
[4294670.303000] NET: Registered protocol family 20
[4294670.303000] ACPI wakeup devices:
[4294670.303000] PCI0 UAR1  USB
[4294670.303000] ACPI: (supports S0 S1 S4 S5)
[4294670.304000] Freeing unused kernel memory: 224k freed
[4294670.325000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.331000] vga16fb: initializing
[4294670.331000] vga16fb: mapped to 0xc00a0000
[4294670.469000] Console: switching to colour frame buffer device 80x30
[4294670.469000] fb0: VGA16 VGA frame buffer device
[4294671.633000] Capability LSM initialized
[4294671.654000] NET: Registered protocol family 1
[4294671.676000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.676000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.676000] ACPI: bus type ide registered
[4294671.684000] AMD7409: IDE controller at PCI slot 0000:00:07.1
[4294671.684000] AMD7409: chipset revision 7
[4294671.684000] AMD7409: not 100% native mode: will probe irqs later
[4294671.684000] AMD7409: 0000:00:07.1 (rev 07) UDMA66 controller
[4294671.685000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:pio
[4294671.685000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[4294671.685000] Probing IDE interface ide0...
[4294671.949000] hda: ST330630A, ATA DISK drive
[4294672.561000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.561000] Probing IDE interface ide1...
[4294673.233000] hdc: FX4830T, ATAPI CD/DVD-ROM drive
[4294673.947000] hdd: LITE-ON LTR-12101B, ATAPI CD/DVD-ROM drive
[4294673.998000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.998000] Probing IDE interface ide2...
[4294674.511000] Probing IDE interface ide3...
[4294675.023000] Probing IDE interface ide4...
[4294675.535000] Probing IDE interface ide5...
[4294676.054000] hda: max request size: 128KiB
[4294676.054000] hda: 58633344 sectors (30020 MB) w/2048KiB Cache, CHS=58168/16/63, UDMA(66)
[4294676.054000] hda: cache flushes not supported
[4294676.054000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 p4 < p5 >
[4294676.107000] hdc: ATAPI 48X CD-ROM drive, 128kB Cache
[4294676.107000] Uniform CD-ROM driver Revision: 3.20
[4294676.112000] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache
[4294676.707000] Attempting manual resume
[4294676.708000] swsusp: Suspend partition has wrong signature?
[4294676.798000] usbcore: registered new driver usbfs
[4294676.798000] usbcore: registered new driver hub
[4294676.800000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.800000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[4294676.800000] PCI: setting IRQ 5 as level-triggered
[4294676.800000] ACPI: PCI Interrupt 0000:00:07.4[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[4294676.800000] ohci_hcd 0000:00:07.4: Advanced Micro Devices [AMD] AMD-756 [Viper] USB
[4294676.801000] ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 1
[4294676.801000] ohci_hcd 0000:00:07.4: irq 5, io mem 0xeffcf000
[4294676.852000] hub 1-0:1.0: USB hub found
[4294676.852000] hub 1-0:1.0: 4 ports detected
[4294677.030000] usb 1-1: new full speed USB device using ohci_hcd and address 2[4294677.325000] usb 1-2: new full speed USB device using ohci_hcd and address 3[4294677.432000] hub 1-2:1.0: USB hub found
[4294677.435000] hub 1-2:1.0: 4 ports detected
[4294679.660000] ACPI: CPU0 (power states: C1[C1])
[4294679.663000] ACPI: Thermal Zone [THRM] (87 C)
[4294679.891000] Attempting manual resume
[4294679.892000] swsusp: Suspend partition has wrong signature?
[4294679.911000] kjournald starting.  Commit interval 5 seconds
[4294679.911000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.073000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.135000] Adding 393552k swap on /dev/hda5.  Priority:-1 extents:1
[4294686.404000] EXT3 FS on hda3, internal journal
[4294693.928000] parport: PnPBIOS parport detected.
[4294693.928000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294694.012000] parport0: Printer, EPSON Stylus COLOR 600
[4294694.024000] lp0: using parport0 (interrupt-driven).
[4294694.098000] mice: PS/2 mouse device common for all mice
[4294694.349000] logips2pp: Detected unknown logitech mouse model 89
[4294694.405000] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[4294694.919000] ts: Compaq touchscreen protocol output
[4294697.238000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294698.305000] cdrom: open failed.
[4294698.311000] cdrom: open failed.
[4294700.878000] Linux agpgart interface v0.101 (c) Dave Jones
[4294700.896000] agpgart: Detected AMD Irongate chipset
[4294700.896000] agpgart: AMD 751 chipset with NVidia GeForce detected. Forcing to 1X due to errata.
[4294700.924000] agpgart: AGP aperture is 64M @ 0xe8000000
[4294701.111000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294701.134000] shpchp: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
[4294701.134000] shpchp: shpc_init: cannot reserve MMIO region
[4294701.134000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294702.147000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[4294702.147000] PCI: setting IRQ 10 as level-triggered
[4294702.147000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[4294702.147000] ACPI: PCI interrupt for device 0000:00:0c.0 disabled
[4294702.147000] cannot allocate the port
[4294702.147000] CA0106: probe of 0000:00:0c.0 failed with error -16
[4294704.421000] pegasus: v0.6.12 (2005/01/13), Pegasus/Pegasus II USB Ethernet driver
[4294704.542000] pegasus 1-1:1.0: eth0, SMC 202 USB Ethernet, 00:e0:29:9e:21:3e
[4294704.542000] usbcore: registered new driver pegasus
[4294704.906000] Real Time Clock Driver v1.12
[4294705.042000] input: PC Speaker
[4294705.493000] Floppy drive(s): fd0 is 1.44M
[4294705.507000] FDC 0 is a post-1991 82077
[4294707.190000] NET: Registered protocol family 17
[4294712.252000] NET: Registered protocol family 10
[4294712.252000] Disabled Privacy Extensions on device c02eb280(lo)
[4294712.252000] IPv6 over IPv4 tunneling driver
[4294714.108000] ACPI: Power Button (FF) [PWRF]
[4294714.108000] ACPI: Sleep Button (FF) [SLPF]
[4294714.108000] ACPI: Power Button (CM) [PWRB]
[4294714.336000] ibm_acpi: ec object not found
[4294723.068000] eth0: no IPv6 routers present
[4294727.108000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294727.108000] apm: overridden by ACPI.
[4294727.622000] ip_tables: (C) 2000-2002 Netfilter core team
[4294727.676000] ip_conntrack version 2.1 (2047 buckets, 16376 max) - 248 bytes per conntrack
[4294729.035000] powernow: No powernow capabilities detected
[4294729.247000] Bluetooth: Core ver 2.7
[4294729.247000] NET: Registered protocol family 31
[4294729.247000] Bluetooth: HCI device and connection manager initialized
[4294729.247000] Bluetooth: HCI socket layer initialized
[4294729.282000] Bluetooth: L2CAP ver 2.7
[4294729.282000] Bluetooth: L2CAP socket layer initialized
[4294729.320000] Bluetooth: RFCOMM ver 1.5
[4294729.320000] Bluetooth: RFCOMM socket layer initialized
[4294729.320000] Bluetooth: RFCOMM TTY layer initialized
[4294731.335000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=36963 PROTO=UDP SPT=4154 DPT=137 LEN=58
[4294738.136000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=36964 PROTO=UDP SPT=4155 DPT=137 LEN=58
[4294742.295000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=36966 PROTO=UDP SPT=4155 DPT=137 LEN=58
[4294753.277000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=36972 PROTO=UDP SPT=4155 DPT=137 LEN=58
[4294763.455000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=36973 PROTO=UDP SPT=4156 DPT=137 LEN=58
[4294775.215000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=36974 PROTO=UDP SPT=4156 DPT=137 LEN=58
[4294786.202000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=36980 PROTO=UDP SPT=4156 DPT=137 LEN=58
[4294940.704000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37004 PROTO=UDP SPT=4157 DPT=137 LEN=58
[4294951.962000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37010 PROTO=UDP SPT=4157 DPT=137 LEN=58
[4294962.931000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37011 PROTO=UDP SPT=4157 DPT=137 LEN=58
[4294966.028000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37012 PROTO=UDP SPT=4158 DPT=137 LEN=58
[4294974.000000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37013 PROTO=UDP SPT=4158 DPT=137 LEN=58
[4294985.116000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37019 PROTO=UDP SPT=4158 DPT=137 LEN=58
[4294991.341000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37022 PROTO=UDP SPT=4160 DPT=137 LEN=58
[4294996.086000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37023 PROTO=UDP SPT=4160 DPT=137 LEN=58
[4295007.166000] Inbound IN=eth0 OUT= MAC=00:e0:29:9e:21:3e:00:11:50:8c:8c:96:08:00 SRC=192.168.2.1 DST=192.168.2.2 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=37025 PROTO=UDP SPT=4160 DPT=137 LEN=58
[4295032.756000] ibm_acpi: ec object not found

---

### Post by LiquidIQ on 2005-12-28
Doesn't look like it's finding any audio. Is audio enabled in the BIOS?

---

### Post by Cprav on 2006-01-01
Hi.  I looked around in the BIOS and the rest of the setup when starting the computer.  I didn't find anything about audio anywhere.  I do have audio in Windows.  My motherboard and all that is about 6 or seven years old.  Don't know if that matters. 

It did work in linux once for a couple of minutes.

Perhaps I'm just not destined to have audio.  :)

---

### Post by Cprav on 2006-01-16
Any help in this matter is still greatly appreciated! :)

---

### Post by Cprav on 2006-02-11
WEll, I'll try one last time to figure this out and then I'll give up! :)

Thanks!

---

