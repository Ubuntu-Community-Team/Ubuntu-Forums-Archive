---
title: "No sound, help the noob"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Lone-wolf on 2006-06-08
I just installed Ubuntu 6.06 for the first time, and I'm getting kind of flustrated... First the serial mouse didn't work, had to go edit some files, that was easy enough, except I killed the monitor for a while.. had to configure it manually. Then I had no Internet working even when I ran dhclient... but that was a DNS problem and I figured it out with help from my good friend google. Now I can't get sound working... (among other things) and google is no help. I have onboard sound, the chip says "Sound Pro" Ht1869v+ PCI" and Linux doesn't seem to detect it at all. I don't know enough about Linux to even try and figure out how to fix this... Help! :(

---

### Post by Lone-wolf on 2006-06-08
wolf@wolf:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 41)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.3 Bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
0000:00:08.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 04)

wolf@wolf:~$ dmesg
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000008000000 (usable)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 128MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 32768
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 28672 pages, LIFO batch:7
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI not present.
[4294667.296000] ACPI: Unable to locate RSDP
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7ff0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] No local APIC present or hardware disabled
[4294667.296000] mapped APIC to ffffd000 (01101000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 451.066 MHz processor.
[   48.921752] Using tsc for high-res timesource
[   48.922789] Console: colour VGA+ 80x25
[   48.924628] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   48.926039] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   48.942607] Memory: 119224k/131072k available (1976k kernel code, 11360k reserved, 606k data, 288k init, 0k highmem)
[   48.942624] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   49.002261] Calibrating delay using timer specific routine.. 903.17 BogoMIPS (lpj=451585)
[   49.002456] Security Framework v1.0.0 initialized
[   49.002501] SELinux:  Disabled at boot.
[   49.002583] Mount-cache hash table entries: 512
[   49.003241] CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[   49.003316] CPU: After vendor identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[   49.003350] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)
[   49.003362] CPU: After all inits, caps: 008021bf 808029bf 00000000 00000002 00000000 00000000 00000000
[   49.003467] mtrr: v2.0 (20020519)
[   49.003477] CPU: AMD-K6(tm) 3D processor stepping 0c
[   49.003499] Checking 'hlt' instruction... OK.
[   49.007991] checking if image is initramfs... it is
[   52.442775] Freeing initrd memory: 6837k freed
[   52.531086] NET: Registered protocol family 16
[   52.531321] EISA bus registered
[   52.547369] PCI: PCI BIOS revision 2.10 entry at 0xfb000, last bus=1
[   52.547395] PCI: Using configuration type 1
[   52.548780] ACPI: Subsystem revision 20051216
[   52.548792] ACPI: Interpreter disabled.
[   52.548806] Linux Plug and Play Support v0.97 (c) Adam Belay
[   52.548838] pnp: PnP ACPI: disabled
[   52.548848] PnPBIOS: Scanning system for PnP BIOS support...
[   52.549320] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbc10
[   52.549341] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbc38, dseg 0xf0000
[   52.554390] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   52.554500] PCI: Probing PCI hardware
[   52.554516] PCI: Probing PCI hardware (bus 00)
[   52.554979] PCI quirk: region 5000-50ff claimed by vt82c586 ACPI
[   52.555361] Boot video device is 0000:01:00.0
[   52.557483] PCI: Using IRQ router VIA [1106/0586] at 0000:00:07.0
[   52.587178] pnp: 00:0a: ioport range 0x208-0x20f has been reserved
[   52.588529] PCI: Bridge: 0000:00:01.0
[   52.588547]   IO window: d000-dfff
[   52.588559]   MEM window: e4000000-e7ffffff
[   52.588571]   PREFETCH window: e8000000-e9ffffff
[   52.588596] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   52.591553] audit: initializing netlink socket (disabled)
[   52.591603] audit(1149811892.283:1): initialized
[   52.592192] VFS: Disk quotas dquot_6.5.1
[   52.592298] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   52.592588] Initializing Cryptographic API
[   52.592613] io scheduler noop registered
[   52.592641] io scheduler anticipatory registered
[   52.592682] io scheduler deadline registered
[   52.592734] io scheduler cfq registered
[   52.592757] Activating ISA DMA hang workarounds.
[   52.593623] isapnp: Scanning for PnP cards...
[   52.690360] pnp: CMI8330 quirk - fixing interrupts and dma
[   52.690592] isapnp: Card 'CMI8330. Audio Adapter'
[   52.690606] isapnp: 1 Plug & Play card detected total
[   52.813232] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   52.813249] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   52.813731] serio: i8042 AUX port at 0x60,0x64 irq 12
[   52.813982] serio: i8042 KBD port at 0x60,0x64 irq 1
[   52.814285] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   52.814713] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   52.815164] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   52.829669] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   52.830571] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   52.833912] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   52.834265] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   52.834285] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   52.835079] mice: PS/2 mouse device common for all mice
[   52.835761] EISA: Probing bus 0 at eisa.0
[   52.835813] Cannot allocate resource for EISA slot 5
[   52.835842] EISA: Detected 0 cards.
[   52.836121] NET: Registered protocol family 2
[   52.846298] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   52.847128] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[   52.847468] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   52.847868] TCP: Hash tables configured (established 8192 bind 8192)
[   52.847882] TCP reno registered
[   52.848363] TCP bic registered
[   52.848406] NET: Registered protocol family 1
[   52.848436] NET: Registered protocol family 8
[   52.848445] NET: Registered protocol family 20
[   52.848536] Using IPI Shortcut mode
[   52.848696] Freeing unused kernel memory: 288k freed
[   52.888760] input: AT Translated Set 2 keyboard as /class/input/input0
[   53.139544] vga16fb: initializing
[   53.139571] vga16fb: mapped to 0xc00a0000
[   53.199755] Console: switching to colour frame buffer device 80x25
[   53.199782] fb0: VGA16 VGA frame buffer device
[   54.337204] Capability LSM initialized
[   57.054002] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   57.054063] VP_IDE: chipset revision 6
[   57.054073] VP_IDE: not 100% native mode: will probe irqs later
[   57.054103] VP_IDE: VIA vt82c586b (rev 41) IDE UDMA33 controller on pci0000:00:07.1
[   57.054136]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[   57.054198]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[   57.054253] Probing IDE interface ide0...
[   57.439614] hda: Maxtor 91369U3, ATA DISK drive
[   57.847514] hdb: CD-532E-B, ATAPI CD/DVD-ROM drive
[   57.899485] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   57.900703] Probing IDE interface ide1...
[   58.447454] hda: max request size: 128KiB
[   58.489959] hda: 26754336 sectors (13698 MB) w/2048KiB Cache, CHS=26542/16/63, UDMA(33)
[   58.489994] hda: cache flushes not supported
[   58.490746]  hda: hda1 hda2 < hda5 >
[   58.521304] hdb: ATAPI 32X CD-ROM drive, 128kB Cache, DMA
[   58.521340] Uniform CD-ROM driver Revision: 3.20
[   59.091185] Probing IDE interface ide1...
[   59.711048] Attempting manual resume
[   59.785109] EXT3-fs: mounted filesystem with ordered data mode.
[   59.804817] kjournald starting.  Commit interval 5 seconds
[   85.714519] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   85.757624] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   86.011543] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[   86.011751] PCI: Found IRQ 11 for device 0000:00:08.0
[   86.056241] eth0: VIA Rhine at 0x1e800, 00:50:ba:07:3f:78, IRQ 11.
[   86.104392] eth0: MII PHY found at address 8, status 0x782d advertising 05e1 Link 41e1.
[   87.628465] Linux agpgart interface v0.101 (c) Dave Jones
[   87.644735] agpgart: Detected VIA Apollo MVP3 chipset
[   87.647414] agpgart: AGP aperture is 64M @ 0xe0000000
[   89.085844] input: PC Speaker as /class/input/input1
[   89.102183] Real Time Clock Driver v1.12
[   89.492993] parport: PnPBIOS parport detected.
[   89.493120] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   89.514955] Driver for 1-wire Dallas network protocol.
[   89.518854] matrox_w1 0000:01:00.0: Matrox G400 GPIO transport layer for 1-wire.
[   89.547708] Floppy drive(s): fd0 is 1.44M
[   89.562848] FDC 0 is a post-1991 82077
[   90.339879] pnp: Device 01:01.02 activated.
[   90.356913] gameport: NS558 PnP Gameport is pnp01:01.02/gameport0, io 0x200, speed 710kHz
[   91.320662] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   92.494846] NET: Registered protocol family 17
[   92.601941] lp0: using parport0 (interrupt-driven).
[   92.912625] Adding 369452k swap on /dev/hda5.  Priority:-1 extents:1 across:369452k
[   93.119572] EXT3 FS on hda1, internal journal
[   93.773527] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   93.773548] md: bitmap version 4.39
[   95.159315] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   96.166073] cdrom: open failed.
[   99.765095] NET: Registered protocol family 10
[   99.765758] lo: Disabled Privacy Extensions
[   99.766482] IPv6 over IPv4 tunneling driver
[  110.293254] eth0: no IPv6 routers present
[  122.617399] ppdev: user-space parallel port driver
[  124.657954] [drm] Initialized drm 1.0.1 20051102
[  124.696575] [drm] Initialized mga 3.2.1 20051102 on minor 0
[  124.700922] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[  124.700969] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[  124.700996] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[  124.790678] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  132.232431] hdb: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  132.232465] hdb: drive_cmd: error=0x04 { AbortedCommand }
[  132.232479] ide: failed opcode was: 0xec
[  137.629331] Bluetooth: Core ver 2.8
[  137.629359] NET: Registered protocol family 31
[  137.629369] Bluetooth: HCI device and connection manager initialized
[  137.629414] Bluetooth: HCI socket layer initialized
[  137.717054] Bluetooth: L2CAP ver 2.8
[  137.717079] Bluetooth: L2CAP socket layer initialized
[  137.858761] Bluetooth: RFCOMM socket layer initialized
[  137.858849] Bluetooth: RFCOMM TTY layer initialized
[  137.858860] Bluetooth: RFCOMM ver 1.7

---

### Post by garijon on 2006-06-11
I have the exact same problem, have you been able to solve it ?
I solved it once by doing :

sudo modprobe snd-cmi8330

but when I try it now I get this error:

FATAL: Error inserting snd_cmi8330 (/lib/modules/2.6.15-23-386/kernel/sound/isa/snd-cmi8330.ko): No such device


G.

---

### Post by Ozitraveller on 2006-06-11
I had sound working when I first installed, but then I did a reboot and now it says that it can't find the soundcard. I have a sound blaster vibra16.

FATAL: Error inserting snd_sb16 (/lib/modules/2.6.15-23-386/kernel/sound/isa/sb/snd-sb16.ko): No such device

I tried both Kubuntu and Xubuntu live cd's and the sound works!

This is what I get when I save changes to /etc/modules

ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

---

