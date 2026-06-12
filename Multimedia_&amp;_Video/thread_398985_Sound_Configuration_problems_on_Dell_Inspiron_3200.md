---
title: "Sound Configuration problems on Dell Inspiron 3200"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by Ralphfi on 2007-04-01
I'm making the cross from MS to Linux at long last,  but now realise that setting up Ubuntu and Xubuntu on a Dell Inspiron 3200 is not the easiest way to start.  Tough it's the only computer I can currently tinker with.  Being an old DOS boy, the terminal doesn't scare I'm just a bit lost with what to do to get the sound to work.

Dell Inspiron 3200XT (PII-233MMX), Snd = Crystal 4237b

I've been to ALSA website as per guide but do not see an entry for Crystal as a chipset manufacturer.  I read through I few other threads and here follows some info, what do I do now?  Got the list of sound modules installed, but out of the 151 on here, the closest where the 4232 and 4236.

Output of lspci

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
00:04.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
00:04.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)

Which led me to think that it isn't pci sound (that and it was built in 1999), but I don't know so much . So I ran dsmesg.

This looked right-ish for a snd card

[ 544.477818] pcmcia: registering new device pcmcia1.0
[ 545.004884] CS4232 WSS PnP manual resources are invalid, using auto config
[ 545.004916] CS4232 WSS PnP configure failed for WSS (out of resources?)
[ 545.004937] PnP BIOS detection failed for CS4232
[ 545.019205] pnp: Device 00:11 disabled.

But here it follows in full, can anyone help get sound running?

[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000] BIOS-e820: 00000000000f0400 - 0000000000100000 (reserved)
[17179569.184000] BIOS-e820: 0000000000100000 - 000000000b000000 (usable)
[17179569.184000] BIOS-e820: 00000000ffff0400 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 176MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 45056
[17179569.184000] DMA zone: 4096 pages, LIFO batch:0
[17179569.184000] Normal zone: 40960 pages, LIFO batch:7
[17179569.184000] DMI not present or invalid.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0b000000:f4ff0400)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01169000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[ 0.000000] Detected 232.128 MHz processor.
[ 484.635524] Using tsc for high-res timesource
[ 484.637707] Console: colour VGA+ 80x25
[ 484.638950] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 484.640154] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 484.679745] Memory: 168956k/180224k available (1911k kernel code, 10724k reserved, 1073k data, 308k init, 0k highmem)
[ 484.679777] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 484.759327] Calibrating delay using timer specific routine.. 465.33 BogoMIPS (lpj=930673)
[ 484.759635] Security Framework v1.0.0 initialized
[ 484.759688] SELinux: Disabled at boot.
[ 484.759814] Mount-cache hash table entries: 512
[ 484.760743] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[ 484.760807] CPU: After vendor identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[ 484.760880] CPU: L1 I cache: 16K, L1 D cache: 16K
[ 484.760903] CPU: L2 cache: 512K
[ 484.760925] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[ 484.761066] Checking 'hlt' instruction... OK.
[ 484.775490] SMP alternatives: switching to UP code
[ 484.776188] Freeing SMP alternatives: 16k freed
[ 484.777054] checking if image is initramfs... it is
[ 488.840065] Freeing initrd memory: 5325k freed
[ 488.840108] CPU0: Intel Pentium II (Deschutes) stepping 00
[ 488.840149] SMP motherboard not detected.
[ 488.840169] Local APIC not detected. Using dummy APIC emulation.
[ 488.840594] Brought up 1 CPUs
[ 488.840723] migration_cost=0
[ 488.842941] NET: Registered protocol family 16
[ 488.843139] EISA bus registered
[ 488.843796] PCI: PCI BIOS revision 2.10 entry at 0xfda13, last bus=0
[ 488.843833] PCI: Using configuration type 1
[ 488.843849] Setting up standard PCI resources
[ 488.850230] ACPI: Interpreter disabled.
[ 488.850263] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 488.850325] pnp: PnP ACPI: disabled
[ 488.850345] PnPBIOS: Scanning system for PnP BIOS support...
[ 488.850439] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6850
[ 488.850469] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb144, dseg 0x400
[ 488.871504] PnPBIOS: Unknown tag '0x82', length '6'.
[ 488.872869] PnPBIOS: Unknown tag '0x82', length '4'.
[ 488.877010] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[ 488.877325] PCI: Probing PCI hardware
[ 488.877351] PCI: Probing PCI hardware (bus 00)
[ 488.877980] Boot video device is 0000:00:02.0
[ 488.878356] PCI: Ignoring BAR0-3 of IDE controller 0000:00:07.1
[ 488.878613] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[ 488.878640] PCI quirk: region 2180-218f claimed by PIIX4 SMB
[ 488.878667] PIIX4 devres B PIO at 0530-0537
[ 488.878688] PIIX4 devres C PIO at 0388-038b
[ 488.878709] PIIX4 devres G PIO at 0f00-0f07
[ 488.882527] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[ 488.882589] PCI: Found IRQ 11 for device 0000:00:04.0
[ 488.882644] PCI: Found IRQ 11 for device 0000:00:04.1
[ 488.884708] pnp: 00:04: ioport range 0x401-0x407 has been reserved
[ 488.884790] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[ 488.884817] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[ 488.884844] pnp: 00:0a: ioport range 0x2180-0x218f has been reserved
[ 488.887099] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[ 488.887195] PCI: Bus 1, cardbus bridge: 0000:00:04.0
[ 488.887217] IO window: 00001000-000010ff
[ 488.887240] IO window: 00001400-000014ff
[ 488.887265] PREFETCH window: 10000000-11ffffff
[ 488.887290] MEM window: 12000000-13ffffff
[ 488.887312] PCI: Bus 5, cardbus bridge: 0000:00:04.1
[ 488.887331] IO window: 00001800-000018ff
[ 488.887353] IO window: 00001c00-00001cff
[ 488.887377] PREFETCH window: 14000000-15ffffff
[ 488.887401] MEM window: 16000000-17ffffff
[ 488.887446] PCI: Found IRQ 11 for device 0000:00:04.0
[ 488.887515] PCI: Found IRQ 11 for device 0000:00:04.1
[ 488.887711] NET: Registered protocol family 2
[ 488.927375] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 488.928108] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[ 488.928654] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[ 488.928928] TCP: Hash tables configured (established 8192 bind 4096)
[ 488.928951] TCP reno registered
[ 488.934664] audit: initializing netlink socket (disabled)
[ 488.934736] audit(1175337430.480:1): initialized
[ 488.935818] VFS: Disk quotas dquot_6.5.1
[ 488.935971] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 488.936369] Initializing Cryptographic API
[ 488.936406] io scheduler noop registered
[ 488.936462] io scheduler anticipatory registered
[ 488.936514] io scheduler deadline registered
[ 488.936622] io scheduler cfq registered (default)
[ 488.936655] Limiting direct PCI/PCI transfers.
[ 488.938086] isapnp: Scanning for PnP cards...
[ 489.292462] isapnp: No Plug & Play device found
[ 489.554376] Real Time Clock Driver v1.12ac
[ 489.554984] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 489.555519] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 489.556333] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 489.560609] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 489.562762] mice: PS/2 mouse device common for all mice
[ 489.568530] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 489.569541] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 489.569574] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 489.570776] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[ 489.576076] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 489.576492] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 489.578098] EISA: Probing bus 0 at eisa.0
[ 489.578143] Cannot allocate resource for EISA slot 1
[ 489.578223] Cannot allocate resource for EISA slot 8
[ 489.578241] EISA: Detected 0 cards.
[ 489.578921] TCP bic registered
[ 489.578988] NET: Registered protocol family 1
[ 489.579034] NET: Registered protocol family 8
[ 489.579052] NET: Registered protocol family 20
[ 489.579202] Using IPI No-Shortcut mode
[ 489.581944] Freeing unused kernel memory: 308k freed
[ 489.603313] input: AT Translated Set 2 keyboard as /class/input/input0
[ 491.462900] Capability LSM initialized
[ 494.852833] PIIX4: IDE controller at PCI slot 0000:00:07.1
[ 494.852911] PIIX4: chipset revision 1
[ 494.852930] PIIX4: not 100% native mode: will probe irqs later
[ 494.852972] ide0: BM-DMA at 0xfcd0-0xfcd7, BIOS settings: hdaMA, hdbio
[ 494.853039] ide1: BM-DMA at 0xfcd8-0xfcdf, BIOS settings: hdcio, hddio
[ 494.853091] Probing IDE interface ide0...
[ 495.142246] hda: FUJITSU MHC2040AT, ATA DISK drive
[ 495.819211] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[ 495.820447] Probing IDE interface ide1...
[ 496.218116] hdc: TOSHIBA CD-ROM XM-1702BC, ATAPI CD/DVD-ROM drive
[ 496.553966] hdc: Disabling (U)DMA for TOSHIBA CD-ROM XM-1702BC (blacklisted)
[ 496.554097] ide1 at 0x170-0x177,0x376 on irq 15
[ 496.634079] hda: max request size: 128KiB
[ 496.634115] hda: 8007552 sectors (4099 MB), CHS=7944/16/63, UDMA(33)
[ 496.634342] hda: hda1 hda2 < hda5 >
[ 497.106303] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[ 497.106352] Uniform CD-ROM driver Revision: 3.20
[ 498.265191] usbcore: registered new driver usbfs
[ 498.268793] usbcore: registered new driver hub
[ 498.288674] USB Universal Host Controller Interface driver v3.0
[ 498.288971] PCI: setting IRQ 10 as level-triggered
[ 498.288996] PCI: Assigned IRQ 10 for device 0000:00:07.2
[ 498.289083] uhci_hcd 0000:00:07.2: UHCI Host Controller
[ 498.289775] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[ 498.289869] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000fce0
[ 498.290533] usb usb1: configuration #1 chosen from 1 choice
[ 498.290735] hub 1-0:1.0: USB hub found
[ 498.290808] hub 1-0:1.0: 2 ports detected
[ 498.601758] Attempting manual resume
[ 498.817060] kjournald starting. Commit interval 5 seconds
[ 498.817141] EXT3-fs: mounted filesystem with ordered data mode.
[ 537.576334] PCI: Found IRQ 11 for device 0000:00:04.0
[ 537.576420] Yenta: CardBus bridge found at 0000:00:04.0 [1028:007e]
[ 537.701915] Yenta: ISA IRQ mask 0x02d8, PCI irq 11
[ 537.701943] Socket status: 30000010
[ 538.076451] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[ 538.078788] PCI: Found IRQ 11 for device 0000:00:04.1
[ 538.078874] Yenta: CardBus bridge found at 0000:00:04.1 [1028:007e]
[ 538.205711] Yenta: ISA IRQ mask 0x02d8, PCI irq 11
[ 538.205739] Socket status: 30000010
[ 538.908935] pccard: PCMCIA card inserted into slot 0
[ 539.012786] pccard: PCMCIA card inserted into slot 1
[ 541.562212] input: PC Speaker as /class/input/input1
[ 541.797706] irda_init()
[ 541.797790] NET: Registered protocol family 23
[ 542.053836] parport: PnPBIOS parport detected.
[ 542.053909] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[ 542.055437] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x148a1, caps: 0x0/0x0
[ 542.100593] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[ 544.210195] ts: Compaq touchscreen protocol output
[ 544.465047] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x388-0x38f
[ 544.466643] cs: IO port probe 0x3e0-0x4ff: clean.
[ 544.467447] cs: IO port probe 0x820-0x8ff: clean.
[ 544.468239] cs: IO port probe 0xc00-0xcf7: clean.
[ 544.469742] cs: IO port probe 0xa00-0xaff: clean.
[ 544.470542] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[ 544.477818] pcmcia: registering new device pcmcia1.0
[ 545.004884] CS4232 WSS PnP manual resources are invalid, using auto config
[ 545.004916] CS4232 WSS PnP configure failed for WSS (out of resources?)
[ 545.004937] PnP BIOS detection failed for CS4232
[ 545.019205] pnp: Device 00:11 disabled.
[ 545.019234] cs4232-pnpbios: probe of 00:11 failed with error -16
[ 545.019380] CS4232 soundcard not found or device busy
[ 546.137047] cs: IO port probe 0x100-0x3af: clean.
[ 546.138624] cs: IO port probe 0x3e0-0x4ff: clean.
[ 546.139419] cs: IO port probe 0x820-0x8ff: clean.
[ 546.504391] cs: IO port probe 0xc00-0xcf7: clean.
[ 546.505901] cs: IO port probe 0xa00-0xaff: clean.
[ 546.506701] cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa00fffff
[ 546.515643] pcmcia: registering new device pcmcia0.0
[ 547.578339] 1.0: ttyS2 at I/O 0x3e8 (irq = 3) is a 16550A
[ 547.912430] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 547.939767] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 548.027886] eth0: Hardware identity xxx
[ 548.028020] eth0: Station identity xxx
[ 548.028046] eth0: Firmware determined as Lucent/Agere 8.36
[ 548.028065] eth0: Ad-hoc demo mode supported
[ 548.028082] eth0: IEEE standard IBSS ad-hoc mode supported
[ 548.028099] eth0: WEP supported, 104-bit key
[ 548.028203] eth0: MAC address xxx
[ 548.028315] eth0: Station name "HERMES I"
[ 548.028796] eth0: ready
[ 548.030420] eth0: index 0x01: , irq 4, io 0x0100-0x013f
[ 548.795869] lp0: using parport0 (interrupt-driven).
[ 549.021458] Adding 200772k swap on /dev/disk/by-uuid/d48263d0-cbde-4bab-bdf1-2d9071bbc64b. Priority:-1 extents:1 across:200772k
[ 549.247296] EXT3 FS on hda1, internal journal
[ 549.741751] NET: Registered protocol family 17
[ 550.020453] eth0: New link status: Connected (0001)
[ 553.472044] NET: Registered protocol family 10
[ 553.472693] lo: Disabled Privacy Extensions
[ 553.473928] IPv6 over IPv4 tunneling driver
[ 563.625706] eth0: no IPv6 routers present
[ 577.847034] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[ 586.919961] setup_irq: irq handler mismatch
[ 586.920055] <c01497d7> setup_irq+0x127/0x140 <c023e750> serial8250_interrupt+0x0/0x100
[ 586.920201] <c0149889> request_irq+0x99/0xb0 <c023e68f> serial8250_startup+0x44f/0x480
[ 586.920325] <c0239c49> uart_startup+0x49/0x150 <c0239e21> uart_open+0xd1/0x470
[ 586.920457] <c02246c4> check_tty_count+0x14/0xb0 <c02285a4> tty_open+0x164/0x330
[ 586.920580] <c0228440> tty_open+0x0/0x330 <c0173cfc> chrdev_open+0xac/0x190
[ 586.920700] <c0173c50> chrdev_open+0x0/0x190 <c0168c56> __dentry_open+0xb6/0x1e0
[ 586.920809] <c0168e35> nameidata_to_filp+0x35/0x40 <c0168e90> do_filp_open+0x50/0x60
[ 586.920960] <c0168b33> get_unused_fd+0x53/0xc0 <c0168eea> do_sys_open+0x4a/0xe0
[ 586.921082] <c0168fbc> sys_open+0x1c/0x20 <c0102fbb> sysenter_past_esp+0x54/0x79
[ 598.201751] Bluetooth: Core ver 2.8
[ 598.201787] NET: Registered protocol family 31
[ 598.201805] Bluetooth: HCI device and connection manager initialized
[ 598.201886] Bluetooth: HCI socket layer initialized
[ 598.382363] Bluetooth: L2CAP ver 2.8
[ 598.382393] Bluetooth: L2CAP socket layer initialized
[ 598.419239] Bluetooth: RFCOMM socket layer initialized
[ 598.419335] Bluetooth: RFCOMM TTY layer initialized
[ 598.419356] Bluetooth: RFCOMM ver 1.7

---

