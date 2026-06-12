---
title: "HP Omnibook 3000CTX Sound Problem"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by Dange on 2007-04-05
I have just finished installing Xubuntu 6.10 on an old HP Omnibook 3000CTX laptop.  Almost everything seems to be working well, however I am unable to get the sound card working.  I believe the sound card in the laptop is based on the Crystal Audio CS4232 chip, and I think it is an ISA card.  This is pretty much all I know at the moment unfortunately.

Dmesg gives me the following after boot:

```

[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000005000000 (usable)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 80MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 20480
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 16384 pages, LIFO batch:3
[17179569.184000] DMI not present or invalid.
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 05000000:faff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash acpi=off pnpbios=no pci=noacpi
[17179569.184000] No local APIC present or hardware disabled
[17179569.184000] mapped APIC to ffffd000 (010a9000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 512 (order: 9, 2048 bytes)
[    0.000000] Detected 267.325 MHz processor.
[ 9623.006240] Using tsc for high-res timesource
[ 9623.008225] Console: colour VGA+ 80x25
[ 9623.009213] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 9623.010407] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[ 9623.029018] Memory: 71628k/81920k available (1910k kernel code, 9840k reserved, 1070k data, 308k init, 0k highmem)
[ 9623.029064] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 9623.106007] Calibrating delay using timer specific routine.. 535.69 BogoMIPS (lpj=1071382)
[ 9623.106458] Security Framework v1.0.0 initialized
[ 9623.106536] SELinux:  Disabled at boot.
[ 9623.106697] Mount-cache hash table entries: 512
[ 9623.108411] CPU: After generic identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[ 9623.108485] CPU: After vendor identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[ 9623.108549] Intel Pentium with F0 0F bug - workaround enabled.
[ 9623.108575] 
[ 9623.108596] CPU: After all inits, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[ 9623.108777] Checking 'hlt' instruction... OK.
[ 9623.122196] SMP alternatives: switching to UP code
[ 9623.122648] Freeing SMP alternatives: 16k freed
[ 9623.124017] checking if image is initramfs... it is
[ 9629.412710] Freeing initrd memory: 5318k freed
[ 9629.412766] CPU0: Intel Mobile Pentium MMX stepping 01
[ 9629.412810] SMP motherboard not detected.
[ 9629.412835] Local APIC not detected. Using dummy APIC emulation.
[ 9629.413443] Brought up 1 CPUs
[ 9629.413632] migration_cost=0
[ 9629.417022] NET: Registered protocol family 16
[ 9629.417479] EISA bus registered
[ 9629.418601] PCI: PCI BIOS revision 2.10 entry at 0xfda1a, last bus=0
[ 9629.418650] PCI: Using configuration type 1
[ 9629.418670] Setting up standard PCI resources
[ 9629.429549] ACPI: Interpreter disabled.
[ 9629.429590] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 9629.429784] pnp: PnP ACPI: disabled
[ 9629.429809] PnPBIOS: Scanning system for PnP BIOS support...
[ 9629.430164] PnPBIOS: Found PnP BIOS installation structure at 0xc00f70a0
[ 9629.430206] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xb975, dseg 0x400
[ 9629.531287] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[ 9629.531922] PCI: Probing PCI hardware
[ 9629.531953] PCI: Probing PCI hardware (bus 00)
[ 9629.533083] PCI: Ignoring BAR0-3 of IDE controller 0000:00:01.1
[ 9629.533344] PCI quirk: region 8000-803f claimed by PIIX4 ACPI
[ 9629.533376] PCI quirk: region 2180-218f claimed by PIIX4 SMB
[ 9629.533412] PIIX4 devres E PIO at 0f00-0f07
[ 9629.533549] Boot video device is 0000:00:02.0
[ 9629.540045] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:01.0
[ 9629.541890] pnp: 00:00: ioport range 0x401-0x407 has been reserved
[ 9629.542013] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[ 9629.542046] pnp: 00:0a: ioport range 0x8000-0x803f has been reserved
[ 9629.542080] pnp: 00:0a: ioport range 0x2180-0x218f has been reserved
[ 9629.545656] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[ 9629.545766] PCI: Bus 1, cardbus bridge: 0000:00:04.0
[ 9629.545792]   IO window: 00001000-000010ff
[ 9629.545818]   IO window: 00001400-000014ff
[ 9629.545845]   PREFETCH window: 10000000-11ffffff
[ 9629.545872]   MEM window: 12000000-13ffffff
[ 9629.545896] PCI: Bus 5, cardbus bridge: 0000:00:04.1
[ 9629.545919]   IO window: 00001800-000018ff
[ 9629.545943]   IO window: 00001c00-00001cff
[ 9629.545969]   PREFETCH window: 14000000-15ffffff
[ 9629.545996]   MEM window: 16000000-17ffffff
[ 9629.546051] PCI: setting IRQ 11 as level-triggered
[ 9629.546076] PCI: Assigned IRQ 11 for device 0000:00:04.0
[ 9629.546156] PCI: Assigned IRQ 11 for device 0000:00:04.1
[ 9629.546350] NET: Registered protocol family 2
[ 9629.585071] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[ 9629.586188] TCP established hash table entries: 4096 (order: 3, 32768 bytes)
[ 9629.586785] TCP bind hash table entries: 2048 (order: 2, 16384 bytes)
[ 9629.587096] TCP: Hash tables configured (established 4096 bind 2048)
[ 9629.587124] TCP reno registered
[ 9629.596681] audit: initializing netlink socket (disabled)
[ 9629.596775] audit(1175798755.708:1): initialized
[ 9629.598364] VFS: Disk quotas dquot_6.5.1
[ 9629.598576] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 9629.599136] Initializing Cryptographic API
[ 9629.599183] io scheduler noop registered
[ 9629.599244] io scheduler anticipatory registered
[ 9629.599303] io scheduler deadline registered
[ 9629.599427] io scheduler cfq registered (default)
[ 9629.599462] Limiting direct PCI/PCI transfers.
[ 9629.601810] isapnp: Scanning for PnP cards...
[ 9629.955365] isapnp: No Plug & Play device found
[ 9630.495564] Real Time Clock Driver v1.12ac
[ 9630.496545] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 9630.505585] mice: PS/2 mouse device common for all mice
[ 9630.514980] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 9630.516584] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 9630.516629] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 9630.518291] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[ 9630.524200] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 9630.524573] serio: i8042 KBD port at 0x60,0x64 irq 1
[B][ 9630.528487] EISA: Probing bus 0 at eisa.0
[ 9630.528555] Cannot allocate resource for EISA slot 1
[ 9630.528705] Cannot allocate resource for EISA slot 8
[ 9630.528725] EISA: Detected 0 cards.[/B]
[ 9630.529539] TCP bic registered
[ 9630.529603] NET: Registered protocol family 1
[ 9630.529666] NET: Registered protocol family 8
[ 9630.529687] NET: Registered protocol family 20
[ 9630.529871] Using IPI No-Shortcut mode
[ 9630.534132] Freeing unused kernel memory: 308k freed
[ 9630.556970] input: AT Translated Set 2 keyboard as /class/input/input0
[ 9632.704648] Capability LSM initialized
[ 9638.497333] PIIX4: IDE controller at PCI slot 0000:00:01.1
[ 9638.497440] PIIX4: chipset revision 1
[ 9638.497462] PIIX4: not 100% native mode: will probe irqs later
[ 9638.497513]     ide0: BM-DMA at 0xfcf0-0xfcf7, BIOS settings: hda:pio, hdb:pio
[ 9638.497608]     ide1: BM-DMA at 0xfcf8-0xfcff, BIOS settings: hdc:pio, hdd:pio
[ 9638.497740] Probing IDE interface ide0...
[ 9638.785749] hda: TOSHIBA MK2018GAP, ATA DISK drive
[ 9639.457853] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[ 9639.459711] Probing IDE interface ide1...
[ 9640.093517] hda: max request size: 128KiB
[ 9640.633997] hda: 39070080 sectors (20003 MB), CHS=38760/16/63, UDMA(33)
[ 9640.634222] hda: cache flushes supported
[ 9640.634517]  hda: hda1 hda2 hda3
[ 9641.752079] usbcore: registered new driver usbfs
[ 9641.756347] usbcore: registered new driver hub
[ 9641.775603] USB Universal Host Controller Interface driver v3.0
[ 9641.779842] PCI: Enabling device 0000:00:01.2 (0000 -> 0001)
[ 9641.779897] PCI: setting IRQ 10 as level-triggered
[ 9641.779921] PCI: Assigned IRQ 10 for device 0000:00:01.2
[ 9641.780029] uhci_hcd 0000:00:01.2: UHCI Host Controller
[ 9641.783057] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[ 9641.783182] uhci_hcd 0000:00:01.2: irq 10, io base 0x0000fcc0
[ 9641.785875] usb usb1: configuration #1 chosen from 1 choice
[ 9641.787615] hub 1-0:1.0: USB hub found
[ 9641.787787] hub 1-0:1.0: 2 ports detected
[ 9642.102654] Probing IDE interface ide1...
[ 9642.863622] Attempting manual resume
[ 9643.057775] kjournald starting.  Commit interval 5 seconds
[ 9643.057910] EXT3-fs: mounted filesystem with ordered data mode.
[ 9668.003951] piix4_smbus 0000:00:01.3: Found 0000:00:01.3 device
[ 9668.797302] PCI: Found IRQ 11 for device 0000:00:04.0
[ 9668.797403] Yenta: CardBus bridge found at 0000:00:04.0 [0000:0000]
[ 9668.926075] Yenta: ISA IRQ mask 0x02b8, PCI irq 11
[ 9668.926106] Socket status: 30000020
[ 9669.038222] PCI: Found IRQ 11 for device 0000:00:04.1
[ 9669.038331] Yenta: CardBus bridge found at 0000:00:04.1 [0000:0000]
[ 9669.166049] Yenta: ISA IRQ mask 0x02b8, PCI irq 11
[ 9669.166079] Socket status: 30000006
[ 9669.709135] pccard: CardBus card inserted into slot 0
[ 9674.342400] input: PC Speaker as /class/input/input1
[ 9676.166532] Floppy drive(s): fd0 is 1.44M
[ 9676.276084] FDC 0 is a post-1991 82077
[ 9676.690561] Synaptics Touchpad, model: 1, fw: 3.4, id: 0x12881, caps: 0x0/0x0
[ 9676.738809] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[ 9678.192636] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
[ 9678.192722] RT61: Vendor = 0x1814, Product = 0x0301 
[ 9678.195277] PCI: Setting latency timer of device 0000:01:00.0 to 64
[ 9678.266271] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x377
[ 9678.267903] cs: IO port probe 0x3e0-0x4ff: clean.
[ 9678.268758] cs: IO port probe 0x820-0x8ff: clean.
[ 9678.269525] cs: IO port probe 0xc00-0xcf7: clean.
[ 9678.271711] cs: IO port probe 0xa00-0xaff: clean.
[ 9678.309928] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x377
[ 9678.311364] cs: IO port probe 0x3e0-0x4ff: clean.
[ 9678.312189] cs: IO port probe 0x820-0x8ff: clean.
[ 9678.312961] cs: IO port probe 0xc00-0xcf7: clean.
[ 9678.587504] cs: IO port probe 0xa00-0xaff: clean.
[ 9679.612323] ts: Compaq touchscreen protocol output
[B][ 9680.326678] pnp: Device 00:11 activated.
[ 9680.326785] CS4232 WSS PnP manual resources are invalid, using auto config
[ 9680.326819] CS4232 WSS PnP configure failed for WSS (out of resources?)
[ 9680.326844] PnP BIOS detection failed for CS4232
[ 9680.383464] pnp: Device 00:11 disabled.
[ 9680.383500] cs4232-pnpbios: probe of 00:11 failed with error -16
[ 9680.383709] CS4232 soundcard not found or device busy[/B]
[ 9680.658288] ra0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[ 9683.440899] RT61: RfIcType= 3
[ 9684.655689] NET: Registered protocol family 17
[ 9685.065410] lp: driver loaded but no devices found
[ 9685.467889] Adding 498004k swap on /dev/disk/by-uuid/01b9dbae-9483-471f-b87e-c4f178c82baa.  Priority:-1 extents:1 across:498004k
[ 9685.780904] EXT3 FS on hda2, internal journal
[ 9686.509065] ac:f6:74:98:12:ab:06:90:b1:ee:a4:d7:bf:e1:b1:fa:
[ 9686.509146] d6:24:28:1f:47:ab:23:75:
[ 9686.509185] 4c:9e:b0:a2:31:df:34:11:
[ 9687.528225] db:45:e1:7c:6c:64:55:3d:7b:d6:b1:3c:a4:8c:b0:2d:
[ 9687.528350] d8:3d:25:c9:1d:dd:65:39:
[ 9687.528390] 2e:eb:8a:2a:8b:e7:63:b2:
[ 9693.703456] NET: Registered protocol family 10
[ 9693.704403] lo: Disabled Privacy Extensions
[ 9693.705974] IPv6 over IPv4 tunneling driver
[ 9704.655181] ra0: no IPv6 routers present
[ 9716.221162] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

```

I bolded the lines which seem to me to be of relevance.  I have trawled the net trying to find a solution but unfortunately I couldn't find anything which helped.  Does anyone here know of a way I can get my sound card working?

---

