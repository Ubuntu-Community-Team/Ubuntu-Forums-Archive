---
title: "Creative Sound Blaster Audigy"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by SuperSizeMe on 2005-11-08
Hi All,

I am a Linux newbie, and last night I installed Ubuntu 5.10 on my machine (see config below).  Today after playing around with my PC I have noticed that when I play certain games such as [ThinkTanks]("http://www.planetthinktanks.com/about-overview.asp"), and run flash websites such as [NINJAI ]("http://www.ninjai.com") I get no sound at all.  Funnily enough when I boot Ubuntu I get the default music as the distro loads up.

When I click Applications>Sound&Video>Volume Control this is the setting options I see in File>Change Device:-
        
        0. SiS S17012 (Alsa Mixer)
        1. CA0106 (Alsa Mixer)
        2. Realtek ALC655 rev0 (OSS Mixer)

I have also addressed this issue "SDL and OpenAL audio will default to OSS output, which may cause [audio output issues]("http://bugzilla.ubuntu.com/show_bug.cgi?id=16444") To work around this, install the libsdl1.2debian-alsa package from         universe." Taken from [Ubuntu ]("http://www.ubuntulinux.org/support/releasenotes510#3.0")

Here is a summary of my desktop hardware:-

        P4 3.2 Ghz 800MMH 2MBCache
        1MB of RAM
        Sound card - Creative - Sound Blaster Audigy 24bit-HD EAX
        Advanced HD
        7.1 (inclusive 5.1 and 6.1)
        Gigabyte Motherboard P4 Titan - GA-8S661FXM-775 (SiS 661FX
        chipset)

This is also the results from dmesg:- 


.0 initialized
[4294669.074000] SELinux:  Disabled at boot.
[4294669.074000] Mount-cache hash table entries: 512
[4294669.074000] CPU: After generic identify, caps: bfebfbff 20100000
00000000 00000000 0000649d 00000000 00000000
[4294669.074000] CPU: After vendor identify, caps: bfebfbff 20100000
00000000 00000000 0000649d 00000000 00000000
[4294669.074000] monitor/mwait feature present.
[4294669.074000] using mwait in idle threads.
[4294669.074000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[4294669.074000] CPU: L2 cache: 2048K
[4294669.074000] CPU: After all inits, caps: bfebfbff 20100000 00000000
00000080 0000649d 00000000 00000000
[4294669.074000] CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[4294669.074000] Enabling fast FPU save and restore... done.
[4294669.074000] Enabling unmasked SIMD FPU exception support... done.
[4294669.074000] Checking 'hlt' instruction... OK.
[4294669.078000] Checking for popad bug... OK.
[4294669.078000] checking if image is initramfs... it is
[4294669.435000] Freeing initrd memory: 4821k freed
[4294669.440000] ACPI: Looking for DSDT in initrd... not found!
[4294669.475000]  not found!
[4294669.481000] ENABLING IO-APIC IRQs
[4294669.482000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294669.593000] NET: Registered protocol family 16
[4294669.593000] EISA bus registered
[4294669.593000] ACPI: bus type pci registered
[4294669.604000] PCI: PCI BIOS revision 2.10 entry at 0xfb740, last
bus=1
[4294669.604000] PCI: Using configuration type 1
[4294669.604000] mtrr: v2.0 (20020519)
[4294669.604000] ACPI: Subsystem revision 20050729
[4294669.613000] ACPI: Interpreter enabled
[4294669.613000] ACPI: Using IOAPIC for interrupt routing
[4294669.614000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.614000] PCI: Probing PCI hardware (bus 00)
[4294669.614000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.614000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294669.615000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[4294669.616000] Boot video device is 0000:01:00.0
[4294669.633000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.634000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11
*12 14 15)
[4294669.634000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10
*11 12 14 15)
[4294669.634000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10
11 12 14 15)
[4294669.635000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10
11 12 14 15)
[4294669.635000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11
*12 14 15)
[4294669.635000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10
11 12 14 15)
[4294669.635000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10
*11 12 14 15)
[4294669.636000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10
11 12 14 15)
[4294669.638000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.638000] pnp: PnP ACPI init
[4294669.640000] pnp: PnP ACPI: found 11 devices
[4294669.640000] PnPBIOS: Disabled by ACPI PNP
[4294669.640000] PCI: Using ACPI for IRQ routing
[4294669.640000] PCI: If a device doesn't work, try "pci=routeirq".  If
it helps, post a report
[4294669.649000] audit: initializing netlink socket (disabled)
[4294669.649000] audit: initialized
[4294669.649000] highmem bounce pool size: 64 pages
[4294669.649000] VFS: Disk quotas dquot_6.5.1
[4294669.649000] Dquot-cache hash table entries: 1024 (order 0, 4096
bytes)
[4294669.649000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.649000] devfs: boot_options: 0x0
[4294669.649000] Initializing Cryptographic API
[4294669.649000] isapnp: Scanning for PnP cards...
[4294670.001000] isapnp: No Plug & Play device found
[4294670.018000] PNP: PS/2 controller doesn't have AUX irq; using
default 0xc
[4294670.018000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq
112
[4294670.021000] Failed to disable AUX port, but continuing anyway... Is
this a SiS?
[4294670.021000] If AUX port is really absent please use the
'i8042.noaux' option.
[4294670.024000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.024000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.024000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports,
IRQ sharing enabled
[4294670.024000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.024000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.026000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.026000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.026000] io scheduler noop registered
[4294670.026000] io scheduler anticipatory registered
[4294670.026000] io scheduler deadline registered
[4294670.026000] io scheduler cfq registered
[4294670.027000] RAMDISK driver initialized: 16 RAM disks of 65536K size
1024 blocksize
[4294670.027000] EISA: Probing bus 0 at eisa.0
[4294670.027000] Cannot allocate resource for EISA slot 1
[4294670.027000] EISA: Detected 0 cards.
[4294670.027000] NET: Registered protocol family 2
[4294670.036000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294670.036000] TCP established hash table entries: 262144 (order: 9,
2097152 bytes)
[4294670.038000] TCP bind hash table entries: 65536 (order: 6, 262144
bytes)
[4294670.038000] TCP: Hash tables configured (established 262144 bind
65536)
[4294670.038000] NET: Registered protocol family 8
[4294670.038000] NET: Registered protocol family 20
[4294670.038000] ACPI wakeup devices:
[4294670.038000] PCI0 USB0 USB1 USB2 MAC0 AMR0 UAR1 UAR2
[4294670.038000] ACPI: (supports S0 S1 S4 S5)
[4294670.038000] Freeing unused kernel memory: 224k freed
[4294670.053000] vga16fb: initializing
[4294670.053000] vga16fb: mapped to 0xc00a0000
[4294670.183000] Console: switching to colour frame buffer device 80x30
[4294670.183000] fb0: VGA16 VGA frame buffer device
[4294670.445000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.466000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.295000] Capability LSM initialized
[4294671.304000] NET: Registered protocol family 1
[4294671.313000] Uniform Multi-Platform E-IDE driver Revision:
7.00alpha2
[4294671.313000] ide: Assuming 33MHz system bus speed for PIO modes;
override with idebus=xx
[4294671.313000] ACPI: bus type ide registered
[4294671.320000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[4294671.320000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level,
low) -> IRQ 16
[4294671.320000] SIS5513: chipset revision 1
[4294671.320000] SIS5513: not 100% native mode: will probe irqs later
[4294671.320000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[4294671.320000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings:
hda:DMA, hdb:pio
[4294671.320000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings:
hdc:DMA, hdd:pio
[4294671.320000] Probing IDE interface ide0...
[4294671.992000] hda: HL-DT-ST RW/DVD GCC-4520B, ATAPI CD/DVD-ROM drive
[4294672.604000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.604000] Probing IDE interface ide1...
[4294672.868000] hdc: ST380011A, ATA DISK drive
[4294673.480000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.480000] Probing IDE interface ide2...
[4294673.993000] Probing IDE interface ide3...
[4294674.505000] Probing IDE interface ide4...
[4294675.017000] Probing IDE interface ide5...
[4294675.532000] hda: ATAPI 52X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294675.532000] Uniform CD-ROM driver Revision: 3.20
[4294675.536000] hdc: max request size: 1024KiB
[4294675.536000] hdc: 156301488 sectors (80026 MB) w/2048KiB Cache,
CHS=16383/255/63, UDMA(100)
[4294675.536000] hdc: cache flushes supported
[4294675.537000]  /dev/ide/host0/bus1/target0/lun0: p1 p2 < p5 >
[4294675.805000] Attempting manual resume
[4294675.806000] swsusp: Suspend partition has wrong signature?
[4294675.841000] usbcore: registered new driver usbfs
[4294675.841000] usbcore: registered new driver hub
[4294675.842000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller
(OHCI) Driver (PCI)
[4294675.842000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level,
low) -> IRQ 20
[4294675.842000] ohci_hcd 0000:00:03.0: Silicon Integrated Systems [SiS]
USB 1.0 Controller
[4294675.842000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned
bus number 1
[4294675.842000] ohci_hcd 0000:00:03.0: irq 20, io mem 0xe7004000
[4294675.895000] hub 1-0:1.0: USB hub found
[4294675.895000] hub 1-0:1.0: 3 ports detected
[4294675.898000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level,
low) -> IRQ 21
[4294675.898000] ohci_hcd 0000:00:03.1: Silicon Integrated Systems [SiS]
USB 1.0 Controller (#2)
[4294675.898000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned
bus number 2
[4294675.898000] ohci_hcd 0000:00:03.1: irq 21, io mem 0xe7000000
[4294675.951000] hub 2-0:1.0: USB hub found
[4294675.951000] hub 2-0:1.0: 3 ports detected
[4294675.954000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level,
low) -> IRQ 22
[4294675.954000] ohci_hcd 0000:00:03.2: Silicon Integrated Systems [SiS]
USB 1.0 Controller (#3)
[4294675.954000] ohci_hcd 0000:00:03.2: new USB bus registered, assigned
bus number 3
[4294675.954000] ohci_hcd 0000:00:03.2: irq 22, io mem 0xe7001000
[4294676.007000] hub 3-0:1.0: USB hub found
[4294676.007000] hub 3-0:1.0: 2 ports detected
[4294676.027000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level,
low) -> IRQ 23
[4294676.027000] ehci_hcd 0000:00:03.3: Silicon Integrated Systems [SiS]
USB 2.0 Controller
[4294676.027000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned
bus number 4
[4294676.027000] ehci_hcd 0000:00:03.3: irq 23, io mem 0xe7002000
[4294676.027000] PCI: cache line size of 128 is not supported by device
0000:00:03.3
[4294676.027000] ehci_hcd 0000:00:03.3: USB 2.0 initialized, EHCI 1.00,
driver 10 Dec 2004
[4294676.027000] hub 4-0:1.0: USB hub found
[4294676.027000] hub 4-0:1.0: 8 ports detected
[4294676.054000] sis900.c: v1.08.08 Jan. 22 2005
[4294676.054000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level,
low) -> IRQ 19
[4294676.055000] 0000:00:04.0: ICS LAN PHY transceiver found at address
1.
[4294676.066000] 0000:00:04.0: Using transceiver found at address 1 as
default
[4294676.066000] eth0: SiS 900 PCI Fast Ethernet at 0xc800, IRQ 19,
00:14:85:86:9b:1f.
[4294676.074000] SCSI subsystem initialized
[4294676.075000] libata version 1.11 loaded.
[4294676.076000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level,
low) -> IRQ 17
[4294676.076000] ata1: SATA max UDMA/133 cmd 0xCC00 ctl 0xD002 bmdma
0xDC00 irq 17
[4294676.076000] ata2: SATA max UDMA/133 cmd 0xD400 ctl 0xD802 bmdma
0xDC08 irq 17
[4294676.244000] usb 4-1: new high speed USB device using ehci_hcd and
address 2[4294676.278000] ata1: no device found (phy stat 00000000)
[4294676.278000] scsi0 : sata_sis
[4294676.318000] hub 4-1:1.0: USB hub found
[4294676.318000] hub 4-1:1.0: 7 ports detected
[4294676.479000] ata2: no device found (phy stat 00000000)
[4294676.479000] scsi1 : sata_sis
[4294676.561000] usb 4-1.2: new full speed USB device using ehci_hcd and
address 3
[4294676.745000] usb 4-1.3: new low speed USB device using ehci_hcd and
address 4
[4294676.933000] usb 4-1.7: new low speed USB device using ehci_hcd and
address 5
[4294678.527000] usbcore: registered new driver hiddev
[4294678.529000] input: USB HID v1.10 Keyboard [Honey Bee  Nostromo
SpeedPad2 ] on usb-0000:00:03.3-1.3
[4294678.532000] input: USB HID v1.10 Mouse [Honey Bee  Nostromo
SpeedPad2 ] on usb-0000:00:03.3-1.3
[4294678.536000] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical
Mouse] on usb-0000:00:03.3-1.7
[4294678.536000] usbcore: registered new driver usbhid
[4294678.536000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294678.872000] ACPI: CPU0 (power states: C1[C1])
[4294679.018000] Attempting manual resume
[4294679.018000] swsusp: Suspend partition has wrong signature?
[4294679.031000] kjournald starting.  Commit interval 5 seconds
[4294679.031000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.332000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.172000] Adding 3036244k swap on /dev/hdc5.  Priority:-1
extents:1
[4294683.445000] EXT3 FS on hdc1, internal journal
[4294688.111000] parport: PnPBIOS parport detected.
[4294688.111000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3
[PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294688.197000] lp0: using parport0 (interrupt-driven).
[4294688.227000] mice: PS/2 mouse device common for all mice
[4294688.263000] atkbd.c: Spurious ACK on isa0060/serio0. Some program,
like XFree86, might be trying access hardware directly.
[4294688.283000] Linux agpgart interface v0.101 (c) Dave Jones
[4294688.304000] nvidia: module license 'NVIDIA' taints kernel.
[4294688.363000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level,
low) -> IRQ 16
[4294688.363000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module
1.0-7667 Fri Jun 17 07:01:04 PDT 2005
[4294692.117000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised:
[email]dm-devel@redhat.com[/email]
[4294692.890000] cdrom: open failed.
[4294695.120000] agpgart: Detected SiS 661 chipset
[4294695.138000] agpgart: AGP aperture is 64M @ 0xe0000000
[4294695.199000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294695.203000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294695.203000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294695.412000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level,
low) -> IRQ 18
[4294695.721000] intel8x0_measure_ac97_clock: measured 49714 usecs
[4294695.721000] intel8x0: clocking to 48000
[4294696.386000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level,
low) -> IRQ 18
[4294696.386000] Model 100a Rev 00000000 Serial 100a1102
[4294698.106000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional
printer dev 3 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1617
[4294698.110000] usbcore: registered new driver usblp
[4294698.110000] drivers/usb/class/usblp.c: v0.13: USB Printer Device
Class driver
[4294698.403000] Real Time Clock Driver v1.12

[4294698.435000] input: PC Speaker
[4294698.486000] Floppy drive(s): fd0 is 1.44M
[4294698.557000] FDC 0 is a post-1991 82077
[4294699.152000] ts: Compaq touchscreen protocol output
[4294700.643000] NET: Registered protocol family 17
[4294702.635000] eth0: Media Link On 100mbps full-duplex
[4294706.236000] NET: Registered protocol family 10
[4294706.236000] Disabled Privacy Extensions on device c02eb280(lo)
[4294706.236000] IPv6 over IPv4 tunneling driver
[4294708.511000] ACPI: Power Button (FF) [PWRF]
[4294708.512000] ACPI: Power Button (CM) [PWRB]
[4294708.597000] ibm_acpi: ec object not found
[4294714.006000] agpgart: Found an AGP 3.5 compliant device at
0000:00:00.0.
[4294714.006000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x
mode
[4294714.007000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x
mode
[4294714.218000] agpgart: Found an AGP 3.5 compliant device at
0000:00:00.0.
[4294714.218000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x
mode
[4294714.218000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x
mode
[4294716.437000] eth0: no IPv6 routers present
[4294717.429000] apm: BIOS version 1.2 Flags 0x07 (Driver version
1.16ac)
[4294717.429000] apm: overridden by ACPI.
[4294718.594000] acpi-cpufreq: CPU0 - ACPI performance management
activated.
[4294718.735000] Bluetooth: Core ver 2.7
[4294718.735000] NET: Registered protocol family 31
[4294718.735000] Bluetooth: HCI device and connection manager
initialized
[4294718.735000] Bluetooth: HCI socket layer initialized
[4294718.763000] Bluetooth: L2CAP ver 2.7
[4294718.763000] Bluetooth: L2CAP socket layer initialized
[4294718.797000] Bluetooth: RFCOMM ver 1.5
[4294718.797000] Bluetooth: RFCOMM socket layer initialized
[4294718.797000] Bluetooth: RFCOMM TTY layer initialized

Sorry for the long thread, but I am trying to be as detailed as possible in the hope that someone might be able to help me.

Thanks,

SSMe - Linux Newbie

---

