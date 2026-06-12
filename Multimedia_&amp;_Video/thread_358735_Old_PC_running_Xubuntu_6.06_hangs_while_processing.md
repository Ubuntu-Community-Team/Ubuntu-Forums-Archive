---
title: "Old PC running Xubuntu 6.06 hangs while processing sound"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by quigleydoor on 2007-02-11
I am running Xubuntu 6.06 on an old custom-built PC, vintage 1999.  This hardware used to run BeOS and serve as my TV, when I lived in a smaller apartment.

Under Xubuntu 6.06, it has trouble playing sound files, video files, and streaming sound and video.  The symptom is that the machine hangs.  The screen freezes and the PC does not respond to the keyboard, mouse, or even the on/off button.  (The reset button always works though.)  Sometimes when this happens, the sound output gets stuck repeating a loop of sound, where the loop is ~0.5 seconds long.

To be fair, this used to happen occasionally under BeOS R5, but it happens very frequently now under Xubuntu 6.06.  It happens with 100% probability when I play Ogg Vorbis files.  It happens rarely with MP3 and MPEG files.  It happens frequently with streaming video and audio in RealPlayer.

To try to fix this, I removed the TV card from the PC.  It is a Bt848 card manufactured by Pinnacle.  I did not change any IRQ settings.  Now the problem is even worse!

What should I do?  Is the hardware defective or the drivers?  Is it IRQ related?

Here is dmesg, in case it helps (after TV card was removed):

```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000fffc000 (usable)
[4294667.296000]  BIOS-e820: 000000000fffc000 - 000000000ffff000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000000ffff000 - 0000000010000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 255MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65532
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 61436 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.0 present.
[4294667.296000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f54e0
[4294667.296000] ACPI: RSDT (v001 ASUS   ME-99    0x00000000  0x00000000) @ 0x0fffc000
[4294667.296000] ACPI: FADT (v001 ASUS   ME-99    0x00000000  0x00000000) @ 0x0fffc080
[4294667.296000] ACPI: BOOT (v001 ASUS   ME-99    0x00000000  0x00000000) @ 0x0fffc040
[4294667.296000] ACPI: DSDT (v001   ASUS ME-99    0x00001000 MSFT 0x0100000a) @ 0x00000000
[4294667.296000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[4294667.296000] ACPI: Disabling ACPI support
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hdc1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01201000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 434.324 MHz processor.
[   22.057780] Using tsc for high-res timesource
[   22.060966] Console: colour VGA+ 80x25
[   22.064336] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.069693] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.127423] Memory: 248884k/262128k available (1976k kernel code, 12576k reserved, 606k data, 288k init, 0k highmem)
[   22.127442] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.186887] Calibrating delay using timer specific routine.. 869.95 BogoMIPS (lpj=434978)
[   22.187021] Security Framework v1.0.0 initialized
[   22.187058] SELinux:  Disabled at boot.
[   22.187118] Mount-cache hash table entries: 512
[   22.187580] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   22.187619] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   22.187661] CPU: L1 I cache: 16K, L1 D cache: 16K
[   22.187673] CPU: L2 cache: 128K
[   22.187687] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   22.187774] mtrr: v2.0 (20020519)
[   22.187795] CPU: Intel Celeron (Mendocino) stepping 05
[   22.187813] Enabling fast FPU save and restore... done.
[   22.187837] Checking 'hlt' instruction... OK.
[   22.191657] checking if image is initramfs... it is
[   26.021305] Freeing initrd memory: 6839k freed
[   26.119388] NET: Registered protocol family 16
[   26.119603] EISA bus registered
[   26.121638] PCI: PCI BIOS revision 2.10 entry at 0xf0500, last bus=1
[   26.121674] PCI: Using configuration type 1
[   26.123650] ACPI: Subsystem revision 20051216
[   26.123671] ACPI: Interpreter disabled.
[   26.123690] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.123784] pnp: PnP ACPI: disabled
[   26.123804] PnPBIOS: Scanning system for PnP BIOS support...
[   26.124490] PnPBIOS: Found PnP BIOS installation structure at 0xc00fca30
[   26.124507] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xca60, dseg 0xf0000
[   26.128715] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   26.128821] PCI: Probing PCI hardware
[   26.128845] PCI: Probing PCI hardware (bus 00)
[   26.129399] PCI: Ignoring BAR0-3 of IDE controller 0000:00:00.1
[   26.130007] Boot video device is 0000:00:0c.0
[   26.132171] PCI: Using IRQ router SIS [1039/0008] at 0000:00:01.0
[   26.156243] pnp: 00:0f: ioport range 0x290-0x297 has been reserved
[   26.156265] pnp: 00:0f: ioport range 0x3f0-0x3f1 has been reserved
[   26.156279] pnp: 00:0f: ioport range 0xec00-0xec3f has been reserved
[   26.156293] pnp: 00:0f: ioport range 0x480-0x48f has been reserved
[   26.157427] PCI: Bridge: 0000:00:02.0
[   26.157442]   IO window: disabled.
[   26.157458]   MEM window: disabled.
[   26.157470]   PREFETCH window: disabled.
[   26.157506] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   26.157861] Simple Boot Flag at 0x3a set to 0x1
[   26.160317] audit: initializing netlink socket (disabled)
[   26.160387] audit(1171136182.685:1): initialized
[   26.160952] VFS: Disk quotas dquot_6.5.1
[   26.161155] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.161462] Initializing Cryptographic API
[   26.161487] io scheduler noop registered
[   26.161514] io scheduler anticipatory registered
[   26.161535] io scheduler deadline registered
[   26.161581] io scheduler cfq registered
[   26.162684] isapnp: Scanning for PnP cards...
[   26.521766] isapnp: No Plug & Play device found
[   26.633152] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   26.634335] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.634596] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.634930] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   26.635369] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.636006] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.651063] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.652169] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   26.655534] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.655897] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.655919] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.656732] mice: PS/2 mouse device common for all mice
[   26.657529] EISA: Probing bus 0 at eisa.0
[   26.657626] EISA: Detected 0 cards.
[   26.657896] NET: Registered protocol family 2
[   26.667118] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   26.668010] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[   26.668671] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   26.669338] TCP: Hash tables configured (established 16384 bind 16384)
[   26.669357] TCP reno registered
[   26.670066] TCP bic registered
[   26.670143] NET: Registered protocol family 1
[   26.670196] NET: Registered protocol family 8
[   26.670207] NET: Registered protocol family 20
[   26.670318] Using IPI Shortcut mode
[   26.670528] Freeing unused kernel memory: 288k freed
[   26.681633] input: AT Translated Set 2 keyboard as /class/input/input0
[   26.981896] vga16fb: initializing
[   26.981928] vga16fb: mapped to 0xc00a0000
[   27.292956] Console: switching to colour frame buffer device 80x25
[   27.293017] fb0: VGA16 VGA frame buffer device
[   28.637217] Capability LSM initialized
[   32.307727] SIS5513: IDE controller at PCI slot 0000:00:00.1
[   32.307813] SIS5513: chipset revision 208
[   32.307824] SIS5513: not 100% native mode: will probe irqs later
[   32.307850] SIS5513: SiS620 ATA 66 controller
[   32.307971]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
[   32.308037]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:DMA
[   32.308081] Probing IDE interface ide0...
[   32.571325] hda: WDC WD136AA, ATA DISK drive
[   33.183727] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   33.184624] Probing IDE interface ide1...
[   33.447914] hdc: IC35L040AVER07-0, ATA DISK drive
[   34.161585] hdd: Hewlett-Packard CD-Writer Plus 9300, ATAPI CD/DVD-ROM drive
[   34.213196] ide1 at 0x170-0x177,0x376 on irq 15
[   34.269735] hda: max request size: 128KiB
[   34.285850] hda: 26564832 sectors (13601 MB) w/2048KiB Cache, CHS=26354/16/63, UDMA(33)
[   34.285887] hda: cache flushes not supported
[   34.286851]  hda: hda1
[   34.292302] hdc: max request size: 128KiB
[   34.304400] hdc: 80418240 sectors (41174 MB) w/1916KiB Cache, CHS=65535/16/63, UDMA(33)
[   34.304438] hdc: cache flushes not supported
[   34.305386]  hdc: hdc1
[   34.460661] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
[   34.460717] Uniform CD-ROM driver Revision: 3.20
[   34.881813] usbcore: registered new driver usbfs
[   34.884054] usbcore: registered new driver hub
[   34.894924] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   34.897222] PCI: Found IRQ 5 for device 0000:00:01.2
[   34.897346] ohci_hcd 0000:00:01.2: OHCI Host Controller
[   34.899762] ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[   34.899807] ohci_hcd 0000:00:01.2: irq 5, io mem 0xc7800000
[   34.953530] hub 1-0:1.0: USB hub found
[   34.953612] hub 1-0:1.0: 2 ports detected
[   35.262333] Attempting manual resume
[   35.325075] EXT3-fs: INFO: recovery required on readonly filesystem.
[   35.325106] EXT3-fs: write access will be enabled during recovery.
[   36.553502] EXT3-fs: recovery complete.
[   36.553638] kjournald starting.  Commit interval 5 seconds
[   36.554520] EXT3-fs: mounted filesystem with ordered data mode.
[   55.695012] parport: PnPBIOS parport detected.
[   55.695125] parport0: PC-style at 0x3bc (0x7bc), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   56.227187] sis630_smbus 0000:00:01.0: SIS630 comp. bus not detected, module not inserted.
[   56.811209] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   56.869427] Floppy drive(s): fd0 is 1.44M
[   56.899718] Linux agpgart interface v0.101 (c) Dave Jones
[   56.974076] FDC 0 is a post-1991 82077
[   57.157444] nvidia: module license 'NVIDIA' taints kernel.
[   57.204411] PCI: Found IRQ 11 for device 0000:00:0c.0
[   57.207361] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[   57.383346] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   57.520452] PCI: Found IRQ 9 for device 0000:00:0a.0
[   57.520539] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[   57.520568] 0000:00:0a.0: 3Com PCI 3c905B Cyclone 100baseTx at d08f8000. Vers LK1.1.19
[   57.579863] agpgart: Detected SiS 620 chipset
[   57.588295] agpgart: AGP aperture is 64M @ 0xc8000000
[   58.122915] Real Time Clock Driver v1.12
[   58.377206] input: ImPS/2 Generic Wheel Mouse as /class/input/input1
[   58.817533] input: PC Speaker as /class/input/input2
[   59.805293] PCI: Found IRQ 10 for device 0000:00:09.0
[   61.203759] PCI: Found IRQ 9 for device 0000:00:0a.0
[   61.341368] ts: Compaq touchscreen protocol output
[   62.424095] NET: Registered protocol family 17
[   62.962557] lp0: using parport0 (interrupt-driven).
[   63.651502] NET: Registered protocol family 10
[   63.652212] lo: Disabled Privacy Extensions
[   63.653060] IPv6 over IPv4 tunneling driver
[   63.676586] Adding 6658900k swap on /dev/hda1.  Priority:-1 extents:1 across:6658900k
[   64.111760] EXT3 FS on hdc1, internal journal
[   64.737127] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   64.737155] md: bitmap version 4.39
[   66.100903] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   67.396923] cdrom: open failed.
[   73.979215] eth0: no IPv6 routers present
[   91.575357] ppdev: user-space parallel port driver
[   92.717447] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  102.515945] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[  102.515985] hdd: drive_cmd: error=0x04 { AbortedCommand }
[  102.516000] ide: failed opcode was: 0xec

```

---

