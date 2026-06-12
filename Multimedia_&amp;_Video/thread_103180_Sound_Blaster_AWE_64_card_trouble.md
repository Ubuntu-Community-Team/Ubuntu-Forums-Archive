---
title: "Sound Blaster AWE 64 card trouble"
date: 2005-12-13
forum: Multimedia &amp; Video
---

### Post by nighttime on 2005-12-13
I'm running Ubuntu Breezy, with an AMD Athlon 1GHz processor (x86 compatible).

I've been trying to load the module for my SoundBlaster AWE 64 sound card (ISA PnP) but i can't seem to get it right... The correct module should be snd_sbawe, according to what I read. So I tried

```

sudo modprobe snd_sbawe

```

and all I get is:

```

FATAL: Error inserting snd_sbawe (/lib/modules/2.6.12-10-386/kernel/sound/isa/sb/snd-sbawe.ko): No such device
FATAL: Error running install command for snd_sbawe

```

I tried adding "snd_sbawe" at the end of /etc/modules but I've had no success with that. Here's the output of dmesg:

(Apparently the card is detected by isapnp, but at the very end It says something about "sbawe: AUDIO pnp configure failure")

```

[4294667.296000] Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Fri Nov 18 11:51:02 UTC2005
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
[4294667.296000] Detected 1000.268 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.680000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)[4294670.681000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.696000] Memory: 251140k/262080k available (1416k kernel code, 10296k reserved, 762k data, 224k init, 0k highmem)[4294670.696000] Checking if this processor honours the WP bit even in supervisor mode... Ok.[4294670.696000] Calibrating delay loop... 1982.46 BogoMIPS (lpj=991232)
[4294670.717000] Security Framework v1.0.0 initialized
[4294670.717000] SELinux:  Disabled at boot.
[4294670.717000] Mount-cache hash table entries: 512
[4294670.717000] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000[4294670.717000] CPU: After vendor identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000[4294670.717000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[4294670.717000] CPU: L2 Cache: 256K (64 bytes/line)
[4294670.717000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000020 00000000 00000000 00000000[4294670.717000] CPU: AMD Athlon(tm) Processor stepping 02
[4294670.717000] Enabling fast FPU save and restore... done.
[4294670.717000] Checking 'hlt' instruction... OK.
[4294670.721000] Checking for popad bug... OK.
[4294670.721000] checking if image is initramfs... it is
[4294671.523000] Freeing initrd memory: 5172k freed
[4294671.531000] ACPI: Looking for DSDT in initrd... not found!
[4294671.645000]  not found!
[4294671.651000] ACPI: setting ELCR to 0200 (from 0e20)
[4294671.654000] NET: Registered protocol family 16
[4294671.654000] EISA bus registered
[4294671.654000] ACPI: bus type pci registered
[4294671.671000] PCI: PCI BIOS revision 2.10 entry at 0xfb4b0, last bus=1
[4294671.671000] PCI: Using configuration type 1
[4294671.671000] mtrr: v2.0 (20020519)
[4294671.671000] ACPI: Subsystem revision 20050729
[4294671.685000] ACPI: Interpreter enabled
[4294671.685000] ACPI: Using PIC for interrupt routing
[4294671.686000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.686000] PCI: Probing PCI hardware (bus 00)
[4294671.686000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.686000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.689000] Boot video device is 0000:01:00.0
[4294671.712000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.713000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[4294671.714000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.[4294671.714000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[4294671.715000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[4294671.720000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.720000] pnp: PnP ACPI init
[4294671.725000] pnp: PnP ACPI: found 12 devices
[4294671.725000] PnPBIOS: Disabled by ACPI PNP
[4294671.725000] PCI: Using ACPI for IRQ routing
[4294671.725000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report[4294671.744000] audit: initializing netlink socket (disabled)
[4294671.744000] audit: initialized
[4294671.744000] VFS: Disk quotas dquot_6.5.1
[4294671.744000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.745000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.745000] devfs: boot_options: 0x0
[4294671.745000] Initializing Cryptographic API
[4294671.745000] Applying VIA southbridge workaround.
[4294671.745000] PCI: Disabling Via external APIC routing
[4294671.745000] isapnp: Scanning for PnP cards...
[4294671.868000] pnp: SB audio device quirk - increasing port range
[4294671.868000] pnp: AWE32 quirk - adding two ports
[4294671.868000] isapnp: Card 'Creative SB AWE64  PnP'
[4294671.868000] isapnp: 1 Plug & Play card detected total
[4294671.899000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12[4294671.900000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.900000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.900000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled[4294671.900000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.900000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.904000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.904000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.904000] io scheduler noop registered
[4294671.904000] io scheduler anticipatory registered
[4294671.904000] io scheduler deadline registered
[4294671.904000] io scheduler cfq registered
[4294671.905000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize[4294671.905000] EISA: Probing bus 0 at eisa.0
[4294671.905000] Cannot allocate resource for EISA slot 4
[4294671.905000] Cannot allocate resource for EISA slot 5
[4294671.905000] Cannot allocate resource for EISA slot 6
[4294671.905000] EISA: Detected 0 cards.
[4294671.905000] NET: Registered protocol family 2
[4294671.914000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294671.914000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)[4294671.914000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294671.915000] TCP: Hash tables configured (established 16384 bind 16384)
[4294671.915000] NET: Registered protocol family 8
[4294671.915000] NET: Registered protocol family 20
[4294671.915000] ACPI wakeup devices:
[4294671.915000] SLPB PCI0 USB0 USB1 MODM UAR1 UAR2
[4294671.915000] ACPI: (supports S0 S1 S4 S5)
[4294671.916000] Freeing unused kernel memory: 224k freed
[4294671.940000] vga16fb: initializing
[4294671.940000] vga16fb: mapped to 0xc00a0000
[4294672.061000] Console: switching to colour frame buffer device 80x30
[4294672.061000] fb0: VGA16 VGA frame buffer device
[4294672.066000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.199000] Capability LSM initialized
[4294673.220000] NET: Registered protocol family 1
[4294673.242000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.242000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx[4294673.242000] ACPI: bus type ide registered
[4294673.250000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[4294673.250000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[4294673.250000] VP_IDE: chipset revision 6
[4294673.250000] VP_IDE: not 100% native mode: will probe irqs later
[4294673.250000] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1[4294673.250000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:pio[4294673.250000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:pio, hdd:DMA[4294673.251000] Probing IDE interface ide0...
[4294673.634000] hda: WDC WD400EB-00CPF0, ATA DISK drive
[4294674.247000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.247000] Probing IDE interface ide1...
[4294675.294000] hdd: LG CD-ROM CRD-8521B, ATAPI CD/DVD-ROM drive
[4294675.345000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.345000] Probing IDE interface ide2...
[4294675.858000] Probing IDE interface ide3...
[4294676.370000] Probing IDE interface ide4...
[4294676.882000] Probing IDE interface ide5...
[4294677.400000] hda: max request size: 128KiB
[4294677.415000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)[4294677.415000] hda: cache flushes not supported
[4294677.415000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294677.464000] hdd: ATAPI 52X CD-ROM drive, 128kB Cache
[4294677.464000] Uniform CD-ROM driver Revision: 3.20
[4294677.860000] Attempting manual resume
[4294677.861000] swsusp: Suspend partition has wrong signature?
[4294677.933000] usbcore: registered new driver usbfs
[4294677.933000] usbcore: registered new driver hub
[4294677.935000] USB Universal Host Controller Interface driver v2.2
[4294677.936000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[4294677.936000] PCI: setting IRQ 5 as level-triggered
[4294677.936000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5[4294677.936000] uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller[4294677.998000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1[4294677.998000] uhci_hcd 0000:00:07.2: irq 5, io base 0x0000e400
[4294677.998000] hub 1-0:1.0: USB hub found
[4294677.998000] hub 1-0:1.0: 2 ports detected
[4294678.001000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5[4294678.001000] uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)[4294678.063000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2[4294678.063000] uhci_hcd 0000:00:07.3: irq 5, io base 0x0000e800
[4294678.063000] hub 2-0:1.0: USB hub found
[4294678.063000] hub 2-0:1.0: 2 ports detected
[4294678.109000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294678.110000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294678.110000] PCI: setting IRQ 11 as level-triggered
[4294678.110000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11[4294678.111000] tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.[4294678.114000] eth0: ADMtek Comet rev 17 at 0001ec00, 00:12:17:56:2C:9D, IRQ 11.[4294680.648000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294680.648000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294680.862000] Attempting manual resume
[4294680.862000] swsusp: Suspend partition has wrong signature?
[4294680.886000] kjournald starting.  Commit interval 5 seconds
[4294680.886000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.646000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.568000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1
[4294687.914000] EXT3 FS on hda1, internal journal
[4294696.317000] parport_pc: VIA 686A/8231 detected
[4294696.317000] parport_pc: probing current configuration
[4294696.317000] parport_pc: Current parallel port base: 0x378
[4294696.317000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[4294696.399000] parport_pc: VIA parallel port: io=0x378, irq=7
[4294696.409000] lp0: using parport0 (interrupt-driven).
[4294696.456000] mice: PS/2 mouse device common for all mice
[4294696.864000] pnp: Unable to assign resources to device 01:01.00.
[4294696.864000] sbawe: AUDIO pnp configure failure
[4294696.871000] Sound Blaster 16 soundcard not found or device busy
[4294696.871000] In case, if you have non-AWE card, try snd-sb16 module
[4294696.950000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294697.575000] ts: Compaq touchscreen protocol output
[4294699.886000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com[4294700.995000] cdrom: open failed.
[4294704.098000] Linux agpgart interface v0.101 (c) Dave Jones
[4294704.115000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[4294704.151000] agpgart: AGP aperture is 64M @ 0xd0000000
[4294704.334000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294704.345000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294704.345000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294706.925000] Real Time Clock Driver v1.12
[4294707.046000] input: PC Speaker
[4294707.304000] Floppy drive(s): fd0 is 1.44M
[4294707.318000] FDC 0 is a post-1991 82077
[4294707.857000] pnp: Device 01:01.01 activated.
[4294707.874000] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x200, speed 602kHz[4294710.137000] NET: Registered protocol family 17
[4294713.119000] 0000:00:09.0: tulip_stop_rxtx() failed
[4294713.119000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.[4294715.544000] NET: Registered protocol family 10
[4294715.544000] Disabled Privacy Extensions on device c02eb280(lo)
[4294715.544000] IPv6 over IPv4 tunneling driver
[4294720.967000] ACPI: Power Button (FF) [PWRF]
[4294720.967000] ACPI: Power Button (CM) [PWRB]
[4294720.967000] ACPI: Sleep Button (CM) [SLPB]
[4294721.171000] ibm_acpi: ec object not found
[4294725.729000] eth0: no IPv6 routers present
[4294733.085000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294733.085000] apm: overridden by ACPI.
[4294735.805000] powernow: No powernow capabilities detected
[4294736.066000] Bluetooth: Core ver 2.7
[4294736.066000] NET: Registered protocol family 31
[4294736.066000] Bluetooth: HCI device and connection manager initialized
[4294736.066000] Bluetooth: HCI socket layer initialized
[4294736.093000] Bluetooth: L2CAP ver 2.7
[4294736.093000] Bluetooth: L2CAP socket layer initialized
[4294736.135000] Bluetooth: RFCOMM ver 1.5
[4294736.135000] Bluetooth: RFCOMM socket layer initialized
[4294736.135000] Bluetooth: RFCOMM TTY layer initialized
[4296352.508000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).[4296352.508000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296379.083000] pnp: Unable to assign resources to device 01:01.00.
[4296379.083000] sbawe: AUDIO pnp configure failure
[4296379.086000] Sound Blaster 16 soundcard not found or device busy
[4296379.086000] In case, if you have non-AWE card, try snd-sb16 module

```

My lsmod output is:

```

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
analog                 10528  0
ns558                   5508  0
gameport               14472  3 analog,ns558
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
i2c_viapro              7696  0
via686a                17816  0
i2c_sensor              3456  1 via686a
i2c_core               19728  4 i2c_acpi_ec,i2c_viapro,via686a,i2c_sensor
pci_hotplug            24628  0
via_agp                 9472  1
agpgart                32328  1 via_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
snd_opl3_lib            9856  0
snd_sb16_dsp            9856  0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  2 snd_sb16_dsp,snd_pcm_oss
snd_timer              21764  2 snd_opl3_lib,snd_pcm
snd_page_alloc         10120  1 snd_pcm
snd_sb16_csp           18304  0
snd_sb_common          14336  2 snd_sb16_dsp,snd_sb16_csp
snd_hwdep               8608  2 snd_opl3_lib,snd_sb16_csp
snd_mpu401_uart         6784  0
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  2 snd_opl3_lib,snd_rawmidi
snd                    48644  12 snd_opl3_lib,snd_sb16_dsp,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_sb16_csp,snd_sb_common,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
tulip                  45088  0
uhci_hcd               28048  0
usbcore               104316  2 uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  556
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

There are some "snd" modules loaded but none is "snd-sbawe".

Also, I tried to run alsamixer, but I only get:

```

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

And finally my lspci output (with nothing on "sound", I might add):

```

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RL/VR AGP

```

By the way: The card worked fine under windows, so it's not a hardware problem.

I hope you can help me. Thanks in advance.

---

### Post by Zimmer on 2005-12-13
Is that just a typing error, the module is snd-sbawe

a dash, not an underscore...

Does that help ??

Zimmer

---

### Post by nighttime on 2005-12-13
No, it says in the modprobe man page that it doesn't make any difference.

Besides, I've already tried with both dash and unserscore already heh... thanks anyway man.

---

### Post by Zimmer on 2005-12-13
Ok,
you may find a few clues here:
[http://www.alsa-project.org/](http://www.alsa-project.org/)

if you have not already tried there...
and I found this info reference the driver loading by module :

 5.2.8.  Soundblaster 16``(*)''

  16-bit SoundBlaster cards (SoundBlaster 16 (PnP), SoundBlaster AWE 32
  (PnP), SoundBlaster AWE 64 (PnP). Please note: this module does not
  support the SoundBlaster VibraX16 soundcard.
[B]
  modprobe snd-card-sb16[/B]


at 
[http://www.charmed.com/txt/Alsa-sound.txt](http://www.charmed.com/txt/Alsa-sound.txt)

Does that work ????


Zimmer

---

### Post by nighttime on 2005-12-13
Yeah, I've been to the ALSA project website, but It only mentioned the "snd-sb16" module, I read about the "snd-sbawe" module in my dmesg output, at the very end it said something like "If you have an AWE card you may want to try 'snd-sbawe'."

I've also tried loading the "snd-card-sb16" module, but it doesn't find it, I guess it's cause of what it says in the mini-how-to:

 >  
For all 16-bit Soundblaster-cards (SoundBlaster 16 (PnP), SoundBlaster
  AWE 32 (PnP), SoundBlaster AWE 64 (PnP):


       /sbin/modprobe snd-card-sb16


  However, if you have a 0.3.0-pre4 package, the GUS Classic driver is
  called ``snd-gusclassic'' [B]and the SoundBlaster 16 module is called
  ``snd-sb16'' (so, without the ``card'' part).[/B]


(yes, I know it's "modprobe" without the "/sbin/" part :P)

I have also tried loading "snd-sb16" and I have tried adding "snd-sb16" to /etc/modules *sighs* I think it's a deeper problem...

And it's allways the same two "FATAL: Error..." messages every time I try to "modprobe" a module:

```

FATAL: Error inserting snd_sbawe (/lib/modules/2.6.12-10-386/kernel/sound/isa/sb/*<module name>*.ko): No such device
FATAL: Error running install command for *<module name>*

```

Would "recompilig the kernel" (whatever THAT is) help at all? I've read a great deal of that regarding modules, though I haven't found any clear guide on how to do it.

---

### Post by Zimmer on 2005-12-14
May have found you a solution..
[http://forums.fedoraforum.org/showthread.php?t=44691](http://forums.fedoraforum.org/showthread.php?t=44691)
Scroll down to the post #9 which gives details of BIOS settings for the IRQ settings......
..if not, maybe reading the rest of the posts will shed some light, 

Good Luck.


Zimmer

---

### Post by nighttime on 2005-12-14
Man! You're awesome! I worked :) 

Thank you so much! you made that trip to the flea market worth while heh I was allready checking out prices for a new PCI sound card.

I guess I could have looked harder for an answer... how did you find a post with the exact same problem? any solution-hunting techniques you wanna share?

---

### Post by Zimmer on 2005-12-15
I usually google the exact error message from the terminal/log. Can pull a large list, so it is a matter of sorting from there.. 

:)

Merry Christmas ...

Zimmer

---

### Post by nighttime on 2005-12-15
Thanks for everything man, you're the best.

---

### Post by henriquemaia on 2006-06-21
I reply on this thread because it helped me out now. I'm setting an old computer for a friend and his computer has a soundblaster AWE64 isa. The instruction here provided (pointing to the Fedora forum) was very useful. Thanks Zimmer.

---

### Post by Zimmer on 2006-06-22
I am glad my "Searching" abilities are of some use !  Even though my technical knowledge is a bit patchy, to say the least.

---

### Post by LivingSouL on 2006-10-22
i have the same probelem and the same soundcard, i've already tried what you have suggested to do, and unluckily, it doesnt work.. :( what should i do next?](*,)

---

### Post by keithu on 2006-10-29
> **Zimmer said:**
> May have found you a solution..
[http://forums.fedoraforum.org/showthread.php?t=44691](http://forums.fedoraforum.org/showthread.php?t=44691)
Scroll down to the post #9 which gives details of BIOS settings for the IRQ settings......

Zimmer

Thanks for this post.

Changing the BIOS settings from Available to Reserved on IRQ 5 and 11 did the trick.  I needed a subsequent "modprobe snd-sbawe" which brought things up.  This was under 6.10 Edgy Eft with an old PII 333mhz box.  Soundblaster AWE64 ISA card.  Says model CT4500 on the PCB.

HOWEVER, my PCI 3Com card stopped working after I made that change.

Reserving JUST IRQ 5 fixed the problem.

Thanks.

Keith

---

### Post by Zimmer on 2006-10-29
We will be wishing this thread a happy birthday soon!
Thanks for posting a detail answer, Keith, I was about to copy the text of the Fedora link here in case it 'disappeared' !

---

### Post by 88200034 on 2007-06-12
Perfect! The Zimmer solution has been running all right on my P II 350, ubuntu feisty with SB AWE 64 ISA.

tip for beginners: to modify "/etc/modules" file you need enter as root on a shell and use an editor, I did it with "editor"... simply to use... ;)

Thank's Zimmer!:D

---

### Post by Zimmer on 2007-06-12
> **88200034 said:**
> Perfect! The Zimmer solution has been running all right on my P II 350, ubuntu feisty with SB AWE 64 ISA.

tip for beginners: to modify "/etc/modules" file you need enter as root on a shell and use an editor, I did it with "editor"... simply to use... ;)

Thank's Zimmer!:D

This thread keeps popping back to life like a Zombie... I had to re read it to find out what it was all about!
I *have* now copied the Fedora post #9 to a text file on my PC...... just in case...
:)..

---

