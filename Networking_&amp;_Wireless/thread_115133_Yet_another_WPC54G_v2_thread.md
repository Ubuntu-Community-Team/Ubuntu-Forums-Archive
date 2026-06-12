---
title: "Yet another WPC54G v2 thread"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by mohapi on 2006-01-09
Sorry to go over a topic so often discussed, but I too have a WPC54G version 2 card, and I'm also getting next-to-nothing out of it.

I've tried three different drivers.

net2220i.inf
lstinds.inf
lsbcmnds.inf

and gotten nothing out of any of them. I downloaded fresh drivers and used drivers from the original CD.

I've blocked acx_pci in the hotplugs listing. I've tried scanning it from the terminal and enabling it through the ndisgtk panel. I even rebuilt the system once, thinking it was something I had tweaked beyond recovery.

I'm beginning to think I'm doing something very wrong, since I don't even get power lights on the card. Of course, I didn't get power lights in Windows either, until I had completely rebooted.

Would anyone like to suggest something? I'm more than willing to take suggestions, particularly if you have this card and got it going.

Cheers, and thanks ahead of time. In the mean time, I'm going to continue to use the search function. :D

---

### Post by healychan on 2006-01-10
```
I've tried three different drivers.

net2220i.inf
lstinds.inf
lsbcmnds.inf
```

I assume that you are using ndiswrapper. I had that card once and I get it refunded since I found it doesn't work with ndiswrapper. I always hang when I tried to bring it up.

The chipset of this card should be Marvell, as far as I know, Marvell chipset doesn't work well with and Linux.

You can check the chipset by "lspci" command. I suggest you get another card if your card is Marvell chipset.

I believe that many people having the same problem as you and me. I also believe that Linux developer are working really hard to improve the compatibility of hardware. The biggest problem is vendors tend to provide Windows drivers only.

---

### Post by waldorf on 2006-01-10
My story is exactly the same! I've tried the same things and probably read all of the threads you did. Still no lights, no connection, no nothing.

Please someone help!

---

### Post by mohapi on 2006-01-10
[QUOTE=healychan]I assume that you are using ndiswrapper.[/QUOTE]

Yup, I've used ndiswrapper from the terminal and used the ndisgtk utility. Ndiswrapper will install the driver, but says the hardware is absent. Ndisgtk does the same, in it's own fashion.

Just for the record, here's the output of the lspci command.

```
0000:00:00.0 Host bridge: Intel Corp. 430TX - 82439TX MTXC (rev 01)
0000:00:01.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:01.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:01.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:01.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:00:08.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:0a.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
```

What's curious to me is there doesn't seem to be *anything* listed in the PCMCIA slots. I've tried booting with it inserted, booting then inserting and any variation thereof. But the fact that nothing even registers suggests to me that I've missed an important step.

And yes, I know it to be working. I was using it under Windows until last week, when I started my quest for Ubuntu. 8-[ 

Here's the output of an lsmod command, if it's of any interest. I've seen them posted in other threads, so I thought it might be helpful.

```
Module                  Size  Used by
nls_utf8                2176  1 
nls_cp437               5888  1 
vfat                   12288  1 
fat                    46492  1 vfat
ipv6                  217408  6 
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
pcmcia                 24584  4 
apm                    19308  1 
af_packet              20232  0 
analog                 10528  0 
ns558                   5508  0 
gameport               14472  3 analog,ns558
irtty_sir               7808  0 
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
pcspkr                  3652  0 
rtc                    11832  0 
yenta_socket           22540  2 
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               8336  0 
i2c_core               19728  1 i2c_piix4
dm_mod                 50364  1 
joydev                  9280  0 
tsdev                   7616  0 
evdev                   9088  1 
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
sd_mod                 17424  2 
md                     40656  0 
ext3                  115976  1 
jbd                    48536  1 ext3
processor              23100  0 
usb_storage            64704  2 
scsi_mod              124872  2 sd_mod,usb_storage
uhci_hcd               28048  0 
usbcore               104188  3 usb_storage,uhci_hcd
ide_cd                 36996  0 
cdrom                  33952  1 ide_cd
ide_disk               16128  3 
ide_generic             1664  0 
piix                    9476  1 
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,piix
unix                   24624  600 
fbcon                  34176  0 
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0 
cfbcopyarea             4480  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
softcursor              2432  1 vesafb
capability              5000  0 
commoncap               6784  1 capability
```

And here's a dmesg command: 

```
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e801: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e801: 0000000000100000 - 0000000008000000 (usable)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 128MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 32768
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 28672 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI not present.
[4294667.296000] ACPI: Unable to locate RSDP
[4294667.296000] Allocating PCI resources starting at 08000000 (gap: 08000000:f8000000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash
[4294667.296000] No local APIC present or hardware disabled
[4294667.296000] mapped APIC to ffffd000 (01101000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 232.150 MHz processor.
[19524.579227] Using tsc for high-res timesource
[19524.580762] Console: colour VGA+ 80x25
[19524.585315] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[19524.587189] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[19524.616363] Memory: 121860k/131072k available (1415k kernel code, 8696k reserved, 763k data, 224k init, 0k highmem)
[19524.616398] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[19524.616907] Calibrating delay loop... 457.72 BogoMIPS (lpj=228864)
[19524.633764] Security Framework v1.0.0 initialized
[19524.633807] SELinux:  Disabled at boot.
[19524.633921] Mount-cache hash table entries: 512
[19524.634780] CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[19524.634839] CPU: After vendor identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[19524.634899] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)
[19524.634924] CPU: After all inits, caps: 008021bf 808029bf 00000000 00000002 00000000 00000000 00000000
[19524.634970] CPU: AMD-K6(tm) 3D processor stepping 0c
[19524.635005] Checking 'hlt' instruction... OK.
[19524.638520] Checking for popad bug... OK.
[19524.639491] checking if image is initramfs... it is
[19528.482292] Freeing initrd memory: 4791k freed
[19528.486934] NET: Registered protocol family 16
[19528.487233] EISA bus registered
[19528.487721] PCI: PCI BIOS revision 2.10 entry at 0xeb360, last bus=0
[19528.487760] PCI: Using configuration type 1
[19528.487783] mtrr: v2.0 (20020519)
[19528.489765] ACPI: Subsystem revision 20050729
[19528.489785] ACPI: Interpreter disabled.
[19528.489811] Linux Plug and Play Support v0.97 (c) Adam Belay
[19528.489917] pnp: PnP ACPI: disabled
[19528.489939] PnPBIOS: Scanning system for PnP BIOS support...
[19528.490744] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[19528.490783] PnPBIOS: PnP BIOS version 1.0, entry 0xec000:0x230d, dseg 0xec000
[19528.499121] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[19528.499542] PCI: Probing PCI hardware
[19528.499566] PCI: Probing PCI hardware (bus 00)
[19528.501146] Boot video device is 0000:00:08.0
[19528.505337] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:01.0
[19528.505396] PCI: IRQ 0 for device 0000:00:01.2 doesn't match PIRQ mask - try pci=usepirqmask
[19528.505444] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[19528.505481] PCI: IRQ 0 for device 0000:00:0a.1 doesn't match PIRQ mask - try pci=usepirqmask
[19528.508423] pnp: 00:01: ioport range 0xcf8-0xcff could not be reserved
[19528.508453] pnp: 00:01: ioport range 0x4d0-0x4d1 has been reserved
[19528.508481] pnp: 00:01: ioport range 0x398-0x399 has been reserved
[19528.508509] pnp: 00:01: ioport range 0x3f0-0x3f1 has been reserved
[19528.508536] pnp: 00:01: ioport range 0x3f3-0x3f3 has been reserved
[19528.508564] pnp: 00:01: ioport range 0x3f7-0x3f7 has been reserved
[19528.508593] pnp: 00:01: ioport range 0x1000-0x107f could not be reserved
[19528.514551] audit: initializing netlink socket (disabled)
[19528.514599] audit: initialized
[19528.515629] VFS: Disk quotas dquot_6.5.1
[19528.515803] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[19528.516179] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[19528.516243] devfs: boot_options: 0x0
[19528.516526] Initializing Cryptographic API
[19528.516566] Limiting direct PCI/PCI transfers.
[19528.517405] isapnp: Scanning for PnP cards...
[19528.614824] isapnp: Card 'ESS ES1869 Plug and Play AudioDrive'
[19528.614852] isapnp: 1 Plug & Play card detected total
[19528.927655] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[19528.929923] serio: i8042 AUX port at 0x60,0x64 irq 12
[19528.930017] serio: i8042 KBD port at 0x60,0x64 irq 1
[19528.930068] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[19528.930611] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[19528.931398] ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[19528.965876] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[19528.967473] io scheduler noop registered
[19528.967568] io scheduler anticipatory registered
[19528.967613] io scheduler deadline registered
[19528.967700] io scheduler cfq registered
[19528.972692] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[19528.973788] EISA: Probing bus 0 at eisa.0
[19528.973831] Cannot allocate resource for EISA slot 1
[19528.973927] EISA: Detected 0 cards.
[19528.974226] NET: Registered protocol family 2
[19528.984545] IP: routing cache hash table of 1024 buckets, 8Kbytes
[19528.985800] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[19528.986611] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[19528.987103] TCP: Hash tables configured (established 8192 bind 8192)
[19528.987955] NET: Registered protocol family 8
[19528.988000] NET: Registered protocol family 20
[19528.991125] Freeing unused kernel memory: 224k freed
[19529.013174] input: AT Translated Set 2 keyboard on isa0060/serio0
[19529.342712] Capability LSM initialized
[19529.497442] NET: Registered protocol family 1
[19529.630427] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[19529.630500] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[19529.690822] PIIX4: IDE controller at PCI slot 0000:00:01.1
[19529.690895] PIIX4: chipset revision 1
[19529.690914] PIIX4: not 100% native mode: will probe irqs later
[19529.690960]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[19529.691034]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:pio, hdd:pio
[19529.691103] Probing IDE interface ide0...
[19529.954279] hda: TOSHIBA MK2104MAV, ATA DISK drive
[19530.566552] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[19530.567022] Probing IDE interface ide1...
[19531.238433] hdc: CD-ROM CDR_U241, ATAPI CD/DVD-ROM drive
[19531.544497] ide1 at 0x170-0x177,0x376 on irq 15
[19531.545425] Probing IDE interface ide2...
[19532.058440] Probing IDE interface ide3...
[19532.571499] Probing IDE interface ide4...
[19533.084562] Probing IDE interface ide5...
[19533.637996] hda: max request size: 128KiB
[19533.949801] hda: 4233600 sectors (2167 MB), CHS=4200/16/63, DMA
[19533.949839] hda: cache flushes not supported
[19533.950377]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
[19534.027836] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[19534.027882] Uniform CD-ROM driver Revision: 3.20
[19537.493225] Attempting manual resume
[19537.493954] swsusp: Suspend partition has wrong signature?
[19537.862523] usbcore: registered new driver usbfs
[19537.862820] usbcore: registered new driver hub
[19537.872439] USB Universal Host Controller Interface driver v2.2
[19537.872896] PCI: IRQ 0 for device 0000:00:01.2 doesn't match PIRQ mask - try pci=usepirqmask
[19537.872937] PCI: setting IRQ 11 as level-triggered
[19537.872960] PCI: Assigned IRQ 11 for device 0000:00:01.2
[19537.873048] uhci_hcd 0000:00:01.2: Intel Corporation 82371AB/EB/MB PIIX4 USB
[19537.935613] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[19537.935669] uhci_hcd 0000:00:01.2: irq 11, io base 0x00001040
[19537.937046] hub 1-0:1.0: USB hub found
[19537.937197] hub 1-0:1.0: 2 ports detected
[19538.109209] usb 1-1: new full speed USB device using uhci_hcd and address 2
[19538.227029] hub 1-1:1.0: USB hub found
[19538.230522] hub 1-1:1.0: 1 port detected
[19538.471440] usb 1-1.1: new full speed USB device using uhci_hcd and address 3
[19540.601153] SCSI subsystem initialized
[19540.616404] Initializing USB Mass Storage driver...
[19540.619284] scsi0 : SCSI emulation for USB Mass Storage devices
[19540.623254] usb-storage: device found at 3
[19540.623275] usb-storage: waiting for device to settle before scanning
[19540.623742] usbcore: registered new driver usb-storage
[19540.623799] USB Mass Storage support registered.
[19544.966059] Attempting manual resume
[19544.994623] swsusp: Suspend partition has wrong signature?
[19545.128432] kjournald starting.  Commit interval 5 seconds
[19545.128523] EXT3-fs: mounted filesystem with ordered data mode.
[19545.628004]   Vendor:           Model:                   Rev:     
[19545.628330]   Type:   Direct-Access                      ANSI SCSI revision: 00
[19545.834898] usb-storage: device scan complete
[19550.899614] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[19551.366141] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[19551.366278] sda: assuming drive cache: write through
[19551.565335] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[19551.565408] sda: assuming drive cache: write through
[19551.565591]  /dev/scsi/host0/bus0/target0/lun0: p1
[19551.757980] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[19568.836634] Adding 120920k swap on /dev/hda5.  Priority:-1 extents:1
[19569.865183] EXT3 FS on hda2, internal journal
[19607.461411] pnp: Device 00:0c activated.
[19607.461444] parport: PnPBIOS parport detected.
[19607.461530] parport0: PC-style at 0x378, irq 7 [PCSPP]
[19607.594461] lp0: using parport0 (interrupt-driven).
[19607.982421] mice: PS/2 mouse device common for all mice
[19608.949173] Synaptics Touchpad, model: 1, fw: 4.1, id: 0x148a1, caps: 0x0/0x0
[19608.969823] input: SynPS/2 Synaptics TouchPad on isa0060/serio1
[19610.930392] ts: Compaq touchscreen protocol output
[19617.614951] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[19620.828695] cdrom: open failed.
[19632.505251] piix4_smbus 0000:00:01.3: Found 0000:00:01.3 device
[19633.607435] Linux Kernel Card Services
[19633.607468]   options:  [pci] [cardbus] [pm]
[19633.738429] PCI: IRQ 0 for device 0000:00:0a.0 doesn't match PIRQ mask - try pci=usepirqmask
[19633.738480] PCI: setting IRQ 9 as level-triggered
[19633.738502] PCI: Assigned IRQ 9 for device 0000:00:0a.0
[19633.738614] Yenta: CardBus bridge found at 0000:00:0a.0 [0000:0000]
[19633.859398] Yenta: ISA IRQ mask 0x0000, PCI irq 9
[19633.859419] Socket status: 00000000
[19633.944682] PCI: IRQ 0 for device 0000:00:0a.1 doesn't match PIRQ mask - try pci=usepirqmask
[19633.944738] PCI: Assigned IRQ 9 for device 0000:00:0a.1
[19633.944881] Yenta: CardBus bridge found at 0000:00:0a.1 [0000:0000]
[19634.065421] Yenta: ISA IRQ mask 0x0000, PCI irq 9
[19634.065441] Socket status: 00000000
[19643.596373] Real Time Clock Driver v1.12
[19644.323211] input: PC Speaker
[19646.185952] Floppy drive(s): fd0 is 1.44M
[19646.186221] floppy0: Floppy io-port 0x03f2 in use
[19647.822611] irda_init()
[19647.822737] NET: Registered protocol family 23
[19649.605513] pnp: Device 01:01.02 activated.
[19649.676765] gameport: NS558 PnP Gameport is pnp01:01.02/gameport0, io 0x201, speed 817kHz
[19655.418917] NET: Registered protocol family 17
[19689.911852] mtrr: no more MTRRs available
[19689.913710] mtrr: no more MTRRs available
[19703.890578] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[19710.308235] cs: IO port probe 0x100-0x4ff: clean.
[19710.311145] cs: IO port probe 0x100-0x4ff: clean.
[19710.316894] cs: IO port probe 0xc00-0xcf7: clean.
[19710.317782] cs: IO port probe 0xc00-0xcf7: clean.
[19710.320768] cs: IO port probe 0xa00-0xaff: clean.
[19710.321653] cs: IO port probe 0xa00-0xaff: clean.
[19714.510634] Bluetooth: Core ver 2.7
[19714.510692] NET: Registered protocol family 31
[19714.510712] Bluetooth: HCI device and connection manager initialized
[19714.510786] Bluetooth: HCI socket layer initialized
[19714.769273] Bluetooth: L2CAP ver 2.7
[19714.769310] Bluetooth: L2CAP socket layer initialized
[19714.914294] Bluetooth: RFCOMM ver 1.5
[19714.914365] Bluetooth: RFCOMM socket layer initialized
[19714.914443] Bluetooth: RFCOMM TTY layer initialized
[19758.102690] NET: Registered protocol family 10
[19758.103883] Disabled Privacy Extensions on device c02eb280(lo)
[19758.104558] IPv6 over IPv4 tunneling driver
[19809.558280] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

I don't know that those are of any help, but I thought I would list them. Thanks again in advance. :(

---

### Post by healychan on 2006-01-10
After looking to your result of "lsmod". I found that tha ndiswrapper modules wasn't there. I guess the problem is you installed the driver but you didn't load the module into the kernel.

You can do this by "sudo modprobe ndiswrapper".

And if you want to load tha module at boot time, do "ndiswrapper -m" or edit your "/etc/modules" file, add the word ndiswrapper to the end of that file.

Good luck!!!

---

### Post by healychan on 2006-01-10
One more thing, I can't remember what is the chipset of WPC54G v2.

The one I had was WPC54G v5 and the chipset is Marvell.

And a bad news the people who are using WPC54G v2. I just check the wiki and it saids
```
 Linksys
WPC54G (Ver.2)
Texas Instruments ACX111
No
No
Haven't managed to get it working yet!
```

I also found this on wiki. You can give it a try if you cannot find any solutions.

```
# Card: Linksys #[WPC54G v2], 54Mbps -- [link here|List#WPC54G v2]

    * Chipset: Texas Instruments ACX 111
    * pciid: 104c:9066
    * Driver: Linksys ftp://ftp.linksys.com/pub/network/wpc54gv2_driver_utility_v2.02.zip
    * Other: linux-2.6.8-gentoo kernel, ndiswrapper 0.10.Kept having kernel panic (interrupt-related) upon module load until I set CONFIG_PCI_MSI=y (and unset CONFIG_4KSTACKS, just in case.) 
Also, used "ndiswrapper -i LSTINDS.INF" (NOT lsbcmnds.inf). Works with 64 and 128-bit WEP. Sometimes need to repeat config info (and commit) repeatedly, else driver & card will ignore requested setup. 
Also works with Gentoo 2.6.9-r9, ndiswrapper 0.12 and drivers that came from CD.
    * NEW USER NOTE 12/30/05 by -JSK-: I had lots of problems getting the settings to take with this card and the above Windows driver. 
I finally found that the settings were timing and order dependent. Here is how I got the card to stick in Managed mode with 128 bit WEP and open authentication:
    * ifconfig wlan0 essid $ESSID mode ad-hoc
    * sleep 1
    * iwconfig wlan0 key $KEY open
    * sleep 1
    * iwconfig wlan0 key open
    * iwconfig wlan0 key on
    * sleep 3
    * iwconfig wlan0 essid $ESSID mode managed
    * sleep 1
    * iwconfig wlan0 key $KEY open
    * sleep 1
    * iwconfig wlan0 key open
    * sleep 15
    * ifconfig $DESIRED_IP_MASK_BROADCAST_ETC up
    * I know it's a hack, but this script works every single time for me. Before, life was miserable. 
On debian, you can put this in a shell script and add a "pre-up" line in your interfaces file instead of using the "wireless" options. YMMV. 


```

---

### Post by mohapi on 2006-01-10
I think I'm just stuck. I rebooted after the *sudo modprobe ndiswrapper* and I can see ndiswrapper in the lsmod output, but still no lights, no action and nothing listed under lspci. 

No harm done. I'll poke around with it for a little while longer, and see if I can come up with anything. I'd love to get Ubuntu running on this little laptop, but it's not going to be worth it without Internet access.

---

### Post by method on 2006-01-10
Have you tried 'sudo rmmod acx_pci' (in Dapper, acx)? There's a ACX chipset driver in the kernel which blocks ndiswrapper.

---

### Post by mohapi on 2006-01-10
No, but I did block acx_pci in the hotplugs list. Would that have the same effect? I have rebooted several times since then, and I thought blocking it through the hotplugs list would prevent it from loading on startup.

---

### Post by healychan on 2006-01-10
Please check you /etc/ndiswrapper/wpc54g directory do see if you have any files with .sys extension. If not, remove the driver and install it again.

When you install a driver with ndiswrapper, you need both .inf and .sys file in the same directory. You need to install just the .inf file.

Make sure you have both files when doing "ndiswrapper -i"

---

### Post by waldorf on 2006-01-10
[QUOTE=healychan]After looking to your result of "lsmod". I found that tha ndiswrapper modules wasn't there. I guess the problem is you installed the driver but you didn't load the module into the kernel.

You can do this by "sudo modprobe ndiswrapper".

And if you want to load tha module at boot time, do "ndiswrapper -m" or edit your "/etc/modules" file, add the word ndiswrapper to the end of that file.

Good luck!!![/QUOTE]

Aha! the sudo modprobe ndiswrapper did it for me.

The card used to work but then stopped. I wonder if it got messed up when I updated the kernel and then I needed to load the module again.

Many many thanks!

---

### Post by mohapi on 2006-01-10
I'll double check my .inf and .sys files next. I am rebuilding the system with WinXP, just so I can be doubly sure that the card hasn't suddenly stopped working. After that, I'll reinstall from scratch and step through the process again. Thanks a bunch for the help, folks.

---

### Post by mohapi on 2006-01-10
Well, the card works perfectly. It immediately turned itself on when WinXP had the drivers. Both lights, online and browsing.

I'm going to reinstall Ubuntu now, and see if I can find my error.

---

### Post by mohapi on 2006-01-12
Well, no dice. I tried everything all over again and I still have no lights, no connection and not even acknowledgement of the hardware.

No matter. This little laptop's role is strictly to play the BBC World Service across the Internet, and occasionally download a torrent. I can forgive myself for going back to my extremely abbreviated version of WinXP and listening from there.

And either way, it's not worth buying another $50 wireless card.

Thanks for all the help, folks. I still have Ubuntu on the big machine, so you'll still see me around.

Cheers.

---

