---
title: "Mount ipod and usb hdd?"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by d.liberate on 2008-01-10
Hi,

I'm experiencing a problem that goes something like this (using Xubuntu 7.10):

I plug in my ipod, and it is detected no problem.
I want to transfer some mp3's from my removable usb hard disk, so I plug this in.
The ipod is suddenly demounted and replaced by the hdd.

I'm assuming its because the auto-detect and mount function in ubuntu uses the same mount point for  any usb hdds, but I have no idea how to fix the problem.  Can anyone help?

Thanks.

---

### Post by manimal347 on 2008-01-10
I may not be able to help, but other probably can't either unless you post more info

Run a terminal emulator with cut and paste capabilities and type the command "dmesg". Post its output; that's your kernel log and will mention drive mount points and other pertinents, and may give relevant error messages. 

Also, post a copy of your /etc/fstab text file. Just open it in any text editor that you can copy text out of. Also, are you using Thunar as a file manager to work with your drives? Thunar has its own automounting routine that works even in systems where automounting otherwise isn't fully setup and may override wiser Ubuntu defaults (not sure on the details here).

Both tasks can be done as a normal (ie, not root/no sudo) user.

---

### Post by d.liberate on 2008-01-10
Thanks, the dmesg dump is here:
```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ef0000 - 0000000037eff000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eff000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 894MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 229104) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229104
[    0.000000]   HighMem    229104 ->   229104
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229104
[    0.000000] On node 0 totalpages: 229104
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1757 pages used for memmap
[    0.000000]   Normal zone: 223251 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7290 checksum 0
[    0.000000] ACPI: RSDP 000F7290, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 37EF8B70, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 37EFEE2B, 0074 (r1 ATI    Raptor    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 37EF8BA0, 628B (r1    ATI U1_M1535  6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 37EFFFC0, 0040
[    0.000000] ACPI: BOOT 37EFEE9F, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 37EFEEC7, 0139 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:c7fc0000)
[    0.000000] Built 1 zonelists.  Total pages: 227315
[    0.000000] Kernel command line: root=UUID=7d7140cc-94a7-4081-b03f-d230bde1f2af ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0170e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1788.898 MHz processor.
[   50.472133] Console: colour VGA+ 80x25
[   50.473258] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   50.474053] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   50.514923] Memory: 896908k/916416k available (2015k kernel code, 18888k reserved, 916k data, 364k init, 0k highmem)
[   50.514936] virtual kernel memory layout:
[   50.514937]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   50.514939]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   50.514940]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   50.514942]     lowmem  : 0xc0000000 - 0xf7ef0000   ( 894 MB)
[   50.514943]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   50.514945]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   50.514946]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   50.514950] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   50.515018] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   50.594993] Calibrating delay using timer specific routine.. 3579.80 BogoMIPS (lpj=7159619)
[   50.595043] Security Framework v1.0.0 initialized
[   50.595054] SELinux:  Disabled at boot.
[   50.595078] Mount-cache hash table entries: 512
[   50.595301] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[   50.595315] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   50.595318] CPU: L2 Cache: 512K (64 bytes/line)
[   50.595322] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
[   50.595338] Compat vDSO mapped to ffffe000.
[   50.595358] Checking 'hlt' instruction... OK.
[   50.611209] SMP alternatives: switching to UP code
[   50.611611] Freeing SMP alternatives: 11k freed
[   50.612088] Early unpacking initramfs... done
[   50.981997] ACPI: Core revision 20070126
[   50.982183] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   50.984452] ACPI: setting ELCR to 0200 (from 0e28)
[   50.986433] CPU0: AMD mobile AMD Athlon(tm) XP2400+ stepping 00
[   50.986441] SMP motherboard not detected.
[   50.986445] Local APIC not detected. Using dummy APIC emulation.
[   50.986516] Brought up 1 CPUs
[   50.986742] Booting paravirtualized kernel on bare hardware
[   50.986859] Time: 19:04:00  Date: 00/10/108
[   50.986899] NET: Registered protocol family 16
[   50.987050] EISA bus registered
[   50.987068] ACPI: bus type pci registered
[   50.999386] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=3
[   50.999389] PCI: Using configuration type 1
[   50.999391] Setting up standard PCI resources
[   51.001254] ACPI: EC: Look up EC in DSDT
[   51.002976] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   53.198447] ACPI: Interpreter enabled
[   53.198451] ACPI: (supports S0 S3 S4 S5)
[   53.198470] ACPI: Using PIC for interrupt routing
[   53.205616] ACPI: EC: GPE=0x18, ports=0x66, 0x62
[   53.205667] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   53.205680] PCI: Probing PCI hardware (bus 00)
[   53.206112] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[   53.206116] PCI quirk: region 8040-805f claimed by ali7101 SMB
[   53.206385] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   53.206470] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   53.208687] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[   53.208822] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[   53.208951] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *9
[   53.209081] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 *10)
[   53.209211] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[   53.209352] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 11) *10
[   53.209483] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[   53.209614] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[   53.209744] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[   53.209843] Linux Plug and Play Support v0.97 (c) Adam Belay
[   53.209861] pnp: PnP ACPI init
[   53.209875] ACPI: bus type pnp registered
[   53.213346] pnp: PnP ACPI: found 11 devices
[   53.213349] ACPI: ACPI bus type pnp unregistered
[   53.213355] PnPBIOS: Disabled by ACPI PNP
[   53.213437] PCI: Using ACPI for IRQ routing
[   53.213440] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   53.216539] NET: Registered protocol family 8
[   53.216542] NET: Registered protocol family 20
[   53.216651] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[   53.216655] pnp: 00:07: ioport range 0x480-0x48f has been reserved
[   53.216658] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   53.216661] pnp: 00:07: ioport range 0x4d6-0x4d6 has been reserved
[   53.216664] pnp: 00:07: ioport range 0x8000-0x807f could not be reserved
[   53.216668] pnp: 00:07: iomem range 0xd0400000-0xd0400fff has been reserved
[   53.217270] Time: tsc clocksource has been installed.
[   53.247070] PCI: Bridge: 0000:00:01.0
[   53.247073]   IO window: 9000-9fff
[   53.247078]   MEM window: d0100000-d01fffff
[   53.247082]   PREFETCH window: e0000000-efffffff
[   53.247087] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   53.247090]   IO window: 00001000-000010ff
[   53.247094]   IO window: 00001400-000014ff
[   53.247098]   PREFETCH window: 40000000-43ffffff
[   53.247101]   MEM window: 44000000-47ffffff
[   53.247105] PCI: Bus 6, cardbus bridge: 0000:00:0a.1
[   53.247107]   IO window: 00001800-000018ff
[   53.247111]   IO window: 00001c00-00001cff
[   53.247115]   PREFETCH window: 48000000-4bffffff
[   53.247119]   MEM window: 4c000000-4fffffff
[   53.247311] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   53.247316] PCI: setting IRQ 11 as level-triggered
[   53.247319] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[   53.247333] ACPI: PCI Interrupt 0000:00:0a.1[B] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[   53.247352] NET: Registered protocol family 2
[   53.285328] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   53.285655] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   53.290261] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   53.291974] TCP: Hash tables configured (established 131072 bind 65536)
[   53.291979] TCP reno registered
[   53.301451] checking if image is initramfs... it is
[   53.748966] Switched to high resolution mode on CPU 0
[   53.989001] Freeing initrd memory: 7043k freed
[   53.989200] Simple Boot Flag at 0x36 set to 0x1
[   53.989614] audit: initializing netlink socket (disabled)
[   53.989639] audit(1199991840.016:1): initialized
[   53.991949] VFS: Disk quotas dquot_6.5.1
[   53.992018] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   53.992142] io scheduler noop registered
[   53.992145] io scheduler anticipatory registered
[   53.992147] io scheduler deadline registered
[   53.992163] io scheduler cfq registered (default)
[   53.992179] ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb.
[   54.208512] Activating ISA DMA hang workarounds.
[   54.208529] Boot video device is 0000:01:05.0
[   54.208724] isapnp: Scanning for PnP cards...
[   54.475568] isapnp: No Plug & Play device found
[   54.505833] Real Time Clock Driver v1.12ac
[   54.505982] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   54.506117] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.506960] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.507453] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[   54.507458] PCI: setting IRQ 3 as level-triggered
[   54.507462] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKG] -> GSI 3 (level, low) -> IRQ 3
[   54.508659] 0000:00:08.0: ttyS1 at I/O 0x8828 (irq = 3) is a 8250
[   54.509204] 0000:00:08.0: ttyS2 at I/O 0x8840 (irq = 3) is a 8250
[   54.509572] 0000:00:08.0: ttyS3 at I/O 0x8850 (irq = 3) is a 8250
[   54.509658] Couldn't register serial port 0000:00:08.0: -28
[   54.510418] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   54.510743] input: Macintosh mouse button emulation as /class/input/input0
[   54.510847] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   54.513983] serio: i8042 KBD port at 0x60,0x64 irq 1
[   54.513993] serio: i8042 AUX port at 0x60,0x64 irq 12
[   54.514251] mice: PS/2 mouse device common for all mice
[   54.514405] EISA: Probing bus 0 at eisa.0
[   54.514419] Cannot allocate resource for EISA slot 1
[   54.514448] Cannot allocate resource for EISA slot 8
[   54.514450] EISA: Detected 0 cards.
[   54.514605] TCP cubic registered
[   54.514617] NET: Registered protocol family 1
[   54.514644] Using IPI No-Shortcut mode
[   54.514882]   Magic number: 8:248:91
[   54.515942] Freeing unused kernel memory: 364k freed
[   54.560348] input: AT Translated Set 2 keyboard as /class/input/input1
[   55.736031] AppArmor: AppArmor initialized<5>audit(1199991842.016:2):  type=1505 info="AppArmor initialized" pid=1150
[   55.746340] fuse init (API version 7.8)
[   55.752304] Failure registering capabilities with primary security module.
[   55.773271] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   55.776356] ACPI: Thermal Zone [THRM] (45 C)
[   56.590755] usbcore: registered new interface driver usbfs
[   56.590796] usbcore: registered new interface driver hub
[   56.590836] usbcore: registered new device driver usb
[   56.591750] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   56.592130] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[   56.592135] PCI: setting IRQ 10 as level-triggered
[   56.592139] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 10 (level, low) -> IRQ 10
[   56.592161] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   56.592481] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   56.592504] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0004000
[   56.661427] usb usb1: configuration #1 chosen from 1 choice
[   56.661472] hub 1-0:1.0: USB hub found
[   56.661488] hub 1-0:1.0: 4 ports detected
[   56.718918] SCSI subsystem initialized
[   56.725035] libata version 2.21 loaded.
[   56.746567] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[   56.746571]   originally by Donald Becker <becker@scyld.com>
[   56.746573]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[   56.764470] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   56.764480] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   56.814493] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0008000-d00087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   56.821371] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   56.821381] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   56.823156] natsemi eth0: NatSemi DP8381[56] at 0xd0009000 (0000:00:12.0), 00:0b:cd:87:16:9f, IRQ 11, port TP.
[   56.826675] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   56.826686] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   56.828058] alim15x3: ATI Radeon IGP Northbridge is not yet fully tested.
[   56.828062] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[   56.828090] ACPI: Unable to derive IRQ for device 0000:00:10.0
[   56.828093] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[   56.828108] ALI15X3: chipset revision 196
[   56.828111] ALI15X3: not 100% native mode: will probe irqs later
[   56.828129]     ide0: BM-DMA at 0x8080-0x8087, BIOS settings: hda:DMA, hdb:pio
[   56.828147]     ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:pio, hdd:pio
[   56.828160] Probing IDE interface ide0...
[   56.948644] Floppy drive(s): fd0 is 1.44M
[   56.983071] FDC 0 is a post-1991 82077
[    4.372000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.384000] Time: acpi_pm clocksource has been installed.
[    4.384000] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    4.428000] hda: IC25N040ATCS04-0, ATA DISK drive
[    4.640000] usb 1-2: configuration #1 chosen from 2 choices
[    4.656000] usbcore: registered new interface driver libusual
[    4.668000] Initializing USB Mass Storage driver...
[    4.668000] scsi0 : SCSI emulation for USB Mass Storage devices
[    4.668000] usb-storage: device found at 2
[    4.668000] usb-storage: waiting for device to settle before scanning
[    4.668000] usbcore: registered new interface driver usb-storage
[    4.668000] USB Mass Storage support registered.
[    5.100000] hda: selected mode 0x45
[    5.100000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.368000] Probing IDE interface ide1...
[    5.388000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000bcd009e86bf18]
[    6.104000] hdc: TOSHIBA DVD-ROM SD-R2312, ATAPI CD/DVD-ROM drive
[    6.776000] hdc: selected mode 0x22
[    6.784000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.804000] hda: max request size: 128KiB
[    6.816000] hda: 78140160 sectors (40007 MB) w/1768KiB Cache, CHS=65535/16/63, UDMA(100)
[    6.816000] hda: cache flushes not supported
[    6.816000]  hda: hda1 hda2 < hda5 >
[    6.860000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[    6.860000] Uniform CD-ROM driver Revision: 3.20
[    7.160000] Attempting manual resume
[    7.160000] swsusp: Resume From Partition 3:5
[    7.160000] PM: Checking swsusp image.
[    7.160000] PM: Resume from disk failed.
[    7.220000] kjournald starting.  Commit interval 5 seconds
[    7.220000] EXT3-fs: mounted filesystem with ordered data mode.
[    9.672000] usb-storage: device scan complete
[    9.680000] scsi 0:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   18.356000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.404000] Netfilter messages via NETLINK v0.30.
[   18.416000] nf_conntrack version 0.5.0 (7159 buckets, 57272 max)
[   21.232000] ieee80211_crypt: registered algorithm 'NULL'
[   21.524000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.544000] agpgart: Detected Ati IGP320/M chipset
[   21.552000] agpgart: AGP aperture is 64M @ 0xd4000000
[   21.568000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.572000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.592000] Yenta: CardBus bridge found at 0000:00:0a.0 [6933:0002]
[   21.592000] Yenta O2: res at 0x94/0xD4: ea/00
[   21.592000] Yenta O2: enabling read prefetch/write burst
[   21.632000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.632000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.720000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   21.720000] Socket status: 30000006
[   21.720000] Yenta: CardBus bridge found at 0000:00:0a.1 [6933:0002]
[   21.804000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   21.804000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   21.848000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   21.848000] Socket status: 30000006
[   21.848000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   21.848000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   21.848000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   22.216000] input: PC Speaker as /class/input/input2
[   22.348000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
[   22.384000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   22.388000] parport_pc 00:09: reported by Plug and Play ACPI
[   22.388000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   22.684000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   22.684000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   22.684000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   22.756000] sd 0:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[   22.764000] sd 0:0:0:0: [sda] Write Protect is off
[   22.764000] sd 0:0:0:0: [sda] Mode Sense: 68 00 00 08
[   22.764000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   22.796000] sd 0:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[   22.800000] sd 0:0:0:0: [sda] Write Protect is off
[   22.800000] sd 0:0:0:0: [sda] Mode Sense: 68 00 00 08
[   22.800000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   22.800000]  sda: sda1 sda2
[   22.816000] sd 0:0:0:0: [sda] Attached SCSI removable disk
[   22.920000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.940000] ieee80211_crypt: registered algorithm 'WEP'
[   23.144000] cs: IO port probe 0x100-0x3af: clean.
[   23.148000] cs: IO port probe 0x3e0-0x4ff: clean.
[   23.148000] cs: IO port probe 0x820-0x8ff: clean.
[   23.148000] cs: IO port probe 0xc00-0xcf7: clean.
[   23.148000] cs: IO port probe 0xa00-0xaff: clean.
[   23.152000] cs: IO port probe 0x100-0x3af: clean.
[   23.152000] cs: IO port probe 0x3e0-0x4ff: clean.
[   23.156000] cs: IO port probe 0x820-0x8ff: clean.
[   23.156000] cs: IO port probe 0xc00-0xcf7: clean.
[   23.156000] cs: IO port probe 0xa00-0xaff: clean.
[   23.300000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   23.300000] PCI: setting IRQ 5 as level-triggered
[   23.300000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[   24.576000] NET: Registered protocol family 17
[   26.008000] AC'97 1 does not respond - RESET
[   26.024000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   26.024000] ali mixer 1 creating error.
[   27.088000] lp0: using parport0 (interrupt-driven).
[   27.184000] Adding 1646620k swap on /dev/hda5.  Priority:-1 extents:1 across:1646620k
[   27.796000] EXT3 FS on hda1, internal journal
[   29.916000] NET: Registered protocol family 10
[   29.916000] lo: Disabled Privacy Extensions
[   30.928000] input: Power Button (FF) as /class/input/input4
[   30.936000] ACPI: Power Button (FF) [PWRF]
[   30.988000] input: Power Button (CM) as /class/input/input5
[   30.996000] ACPI: Power Button (CM) [PWRB]
[   31.032000] input: Lid Switch as /class/input/input6
[   31.032000] ACPI: Lid Switch [LID]
[   31.124000] ACPI: Battery Slot [BAT1] (battery present)
[   31.152000] ACPI: AC Adapter [ACAD] (on-line)
[   31.236000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.328000] No dock devices found.
[   31.648000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   31.656000] powernow: No PST tables match this cpuid (0x7a0)
[   31.656000] powernow: This is indicative of a broken BIOS.
[   31.656000] powernow: Trying ACPI perflib
[   31.656000] powernow: Minimum speed 530 MHz. Maximum speed 1788 MHz.
[   33.256000] ppdev: user-space parallel port driver
[   33.380000] eth0: DSPCFG accepted after 0 usec.
[   33.384000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.616000] audit(1199991875.504:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5052 profile="/usr/sbin/cupsd"
[   33.708000] apm: BIOS not found.
[   34.004000] Failure registering capabilities with primary security module.
[   34.544000] Clocksource tsc unstable (delta = -104309040 ns)
[   36.444000] [drm] Initialized drm 1.1.0 20060810
[   36.568000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   36.576000] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   38.212000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   38.212000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   38.212000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[   39.464000] [drm] Setting GART location based on new memory map
[   39.464000] [drm] writeback test succeeded in 1 usecs
[   40.720000] eth1: no IPv6 routers present
[  216.472000] usb 1-2: USB disconnect, address 2
[  231.204000] usb 1-1: new full speed USB device using ohci_hcd and address 3
[  231.432000] usb 1-1: configuration #1 chosen from 1 choice
[  231.440000] scsi1 : SCSI emulation for USB Mass Storage devices
[  231.440000] usb-storage: device found at 3
[  231.440000] usb-storage: waiting for device to settle before scanning
[  236.440000] usb-storage: device scan complete
[  236.448000] scsi 1:0:0:0: Direct-Access     WDC WD12 00UE-00KVT0      0000 PQ: 0 ANSI: 0
[  236.460000] sd 1:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  236.472000] sd 1:0:0:0: [sda] Write Protect is off
[  236.472000] sd 1:0:0:0: [sda] Mode Sense: 27 00 00 00
[  236.472000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[  236.484000] sd 1:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  236.500000] sd 1:0:0:0: [sda] Write Protect is off
[  236.500000] sd 1:0:0:0: [sda] Mode Sense: 27 00 00 00
[  236.500000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[  236.500000]  sda: sda1
[  236.540000] sd 1:0:0:0: [sda] Attached SCSI disk
[  236.540000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  980.764000] usb 1-1: USB disconnect, address 3
[  987.428000] usb 1-2: new full speed USB device using ohci_hcd and address 4
[  987.684000] usb 1-2: configuration #1 chosen from 2 choices
[  987.688000] scsi2 : SCSI emulation for USB Mass Storage devices
[  987.688000] usb-storage: device found at 4
[  987.688000] usb-storage: waiting for device to settle before scanning
[  992.692000] usb-storage: device scan complete
[  992.700000] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  992.712000] sd 2:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[  992.720000] sd 2:0:0:0: [sda] Write Protect is off
[  992.720000] sd 2:0:0:0: [sda] Mode Sense: 68 00 00 08
[  992.720000] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  992.736000] sd 2:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[  992.744000] sd 2:0:0:0: [sda] Write Protect is off
[  992.744000] sd 2:0:0:0: [sda] Mode Sense: 68 00 00 08
[  992.744000] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  992.744000]  sda: sda1 sda2
[  992.760000] sd 2:0:0:0: [sda] Attached SCSI removable disk
[  992.760000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[ 1485.256000] usb 1-2: USB disconnect, address 4
[ 1490.728000] usb 1-1: new full speed USB device using ohci_hcd and address 5
[ 1490.960000] usb 1-1: configuration #1 chosen from 1 choice
[ 1490.968000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1490.968000] usb-storage: device found at 5
[ 1490.972000] usb-storage: waiting for device to settle before scanning
[ 1495.972000] usb-storage: device scan complete
[ 1495.980000] scsi 3:0:0:0: Direct-Access     WDC WD12 00UE-00KVT0      0000 PQ: 0 ANSI: 0
[ 1496.000000] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[ 1496.012000] sd 3:0:0:0: [sdb] Write Protect is off
[ 1496.012000] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 1496.012000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1496.024000] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[ 1496.040000] sd 3:0:0:0: [sdb] Write Protect is off
[ 1496.040000] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 1496.040000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1496.040000]  sdb: sdb1
[ 1496.100000] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 1496.100000] sd 3:0:0:0: Attached scsi generic sg0 type 0

```
 Fstab follows: 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7d7140cc-94a7-4081-b03f-d230bde1f2af /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=49d15589-e794-449d-a952-a854eb088378 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

I am using Thunar, though again, I'm unsure how to check if it is its auto-mounting functionality that is causing the problem.

Thanks for your help though.

---

### Post by manimal347 on 2008-01-10
"[  236.448000] scsi 1:0:0:0: Direct-Access     WDC WD12 00UE-00KVT0      0000 PQ: 0 ANSI: 0
[  236.460000] sd 1:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  236.472000] sd 1:0:0:0: [sda] Write Protect is off
[  236.472000] sd 1:0:0:0: [sda] Mode Sense: 27 00 00 00
[  236.472000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[  236.484000] sd 1:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  236.500000] sd 1:0:0:0: [sda] Write Protect is off
[  236.500000] sd 1:0:0:0: [sda] Mode Sense: 27 00 00 00
[  236.500000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[  236.500000]  sda: sda1"

--------------
Okay, this is your external HD's first mounting attempt, as /dev/sda1"
--------------

"[ 1495.980000] scsi 3:0:0:0: Direct-Access     WDC WD12 00UE-00KVT0      0000 PQ: 0 ANSI: 0
[ 1496.000000] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[ 1496.012000] sd 3:0:0:0: [sdb] Write Protect is off
[ 1496.012000] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 1496.012000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1496.024000] sd 3:0:0:0: [sdb] 234441648 512-byte hardware sectors (120034 MB)
[ 1496.040000] sd 3:0:0:0: [sdb] Write Protect is off
[ 1496.040000] sd 3:0:0:0: [sdb] Mode Sense: 27 00 00 00
[ 1496.040000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 1496.040000]  sdb: sdb1"

This is your USB hard disk again. It specifically mounted on /dev/sdb1, as noted on the bottom-most line. Yes, this is its second mounting.

As for your Ipod?

I see it referred to as 
" 992.700000] scsi 2:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  992.712000] sd 2:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[  992.720000] sd 2:0:0:0: [sda] Write Protect is off
[  992.720000] sd 2:0:0:0: [sda] Mode Sense: 68 00 00 08
[  992.720000] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  992.736000] sd 2:0:0:0: [sda] 3964928 2048-byte hardware sectors (8120 MB)
[  992.744000] sd 2:0:0:0: [sda] Write Protect is off
[  992.744000] sd 2:0:0:0: [sda] Mode Sense: 68 00 00 08
[  992.744000] sd 2:0:0:0: [sda] Assuming drive cache: write through
[  992.744000]  sda: sda1 sda2"

There's another entry, but the kernel is mounting it as sda1 and sda2 in both cases. I think that's because Ipod's have both a main and recovery partition. No clue which is which.

The multiple dmesg entries per device are probably from running Thunar (first from kernel mounting, second when Thunar does it again?), though that may not be your issue. Curiously, both drives also call to dev/sg0, and initially, to sda1 (though your Ipod will also respond to /dev/sda2). Your intuition is correct, as it does look like the Ipod and HD are conflicting on their mount points at /dev/sda1 and possibly with /dev/sg0.

I'm sorry this is so gory, but Linux drive mounting was never fun business and much of what works beneath that convenient automounting goes back to the days of Slackware and floppy disk installs. Essentially, it looks like both your USB  disks are trying to mount as the same device at some point. Try plugging and pulling the two drives, running dmesg each time a drive is pulled. You may glean useful data and learn more about how your system behaves with USB drives (/mounting points, EX: dev/sg0 or /dev/sda1 and /dev/sdb1, though the "/dev" half won't be explicitly mentioned as Linus Torvalds et. all assumed people know that. No, you don't have SCSI drives and the /dev/sg0 and mentions of SCSI mounting are really because USB drives are being emulated as SCSI because SCSI items have historically been able to be unplugged without a reboot, unlike the IDE drive interface you use. This is normal.

"4.640000] usb 1-2: configuration #1 chosen from 2 choices
[    4.656000] usbcore: registered new interface driver libusual
[    4.668000] Initializing USB Mass Storage driver...
[    4.668000] scsi0 : SCSI emulation for USB Mass Storage devices
[    4.668000] usb-storage: device found at 2"

Mass storage USB just means USB-based drives that store data, be it an external floppy or 1 terabyte HD, by the way. All looks fine.

I think your internal hard disk is /dev/hda (likely REALLY /dev/hda1 , so try both if ever relevant)
"4.428000] hda: IC25N040ATCS04-0, ATA DISK drive"

Your DVD drive is HDC (/dev/hdc1 probably) if this ever comes up
"6.104000] hdc: TOSHIBA DVD-ROM SD-R2312, ATAPI CD/DVD-ROM drive"

How to fix this issue? I don't know, and don't feel like scouring Launchpad to check for bugs in Xubuntu and a preliminary Web search tells me little I don't know (just the basics.) A quick and dirty workaround is to just copy the data (music) from your external hard disk to your internal one, unmount and remove it, reinsert your Ipod, and then unmount the Ipod. Your /etc/fstab makes no mention of USB removable devices, just fixed ones. creating entries there may help you get the drives to mount correctly. Read "man fstab" and check the Ubuntu Wiki and other sources for help on this, as it is beyond our scope here. I'm assuming you've already tried rebooting your machine with the Ipod detached, the external HD detached, and both drives detached as this could present an easy solution or solve problems on its own (I know, Unix no-no; almost everything in Linux/Unix can be fixed with the system "live," or running...). I

If you don't want to reboot or it didn't help:
Unplug your USB HD too if it has unmounted (drive light should go out, dmesg will report, no Thunar icon). Thunar can unmount by left-clicking on the drive icon in the panel and clicking unmount.  If you still see it, run "sudo umount /dev/sdb1" , "sudo umount /dev/sda1" , and "sudo umount /dev/sg0".  Properly unmounting drives in Linux is vital, as I've seen many setups where data is only written to a drive after it is told to unmount. Yank the USB or power cord, and the data might never get written. If you KNOW your computer isn't like this, or haven't written any data to your USB drives, pulling the drives before unmounting works, but at your own peril (minor risk of file system/data corruption, though I've personally never witnessed it happen, and there are free Linux tools that *try* to fix this). It looks like the drive is still mounted though, so try accessing it. If you can't read it, you'll need to do this. I wrote this on the understanding that both drives had unmounted (sorry), but it will still prove helpful in working with your Ipod.

If you need more help unmounting, read: "man umount" -yes the command really is umount, not unmount.

Plug in your hard disk first and mount that if it wasn't already working and you skipped the above. Try opening Thunar on it and see if it appears. If not, you'll have to mount it manually.The mounting place may be very different from that in the above dmesg lists, so you'll need to run dmesg again, scour the END of the data for a 120 gigabyte (~120000MB) drive, and note its mount point. If nothing new has appeared in the log, something's wrong and your computer didn't see the drive. You also need to know what kind of partition it has, and have a place to mount it. If you don't have a place for drives to mount ("ls /media" to check) run "sudo mkdir /media/usbhd" and "sudo mkdir /media/ipod". Then, read "man mount" and mount it. It will look something like this... "sudo mount /dev/sda1 -T vfat /media/usbhd" 

You'll have to know what /dev/*.* (wildcard to show it could be anything) file your drive is known to by the kernel from scouring the dmesg kernel log, and you'll have to enter your partition type as named in "man mount" (tells you the name "mount" expects for a given type of partition) after the "-T" 

Read the error messages and re-run dmesg if things go wrong; it'll tell you why the drive wouldn't mount and give you hints. Don't worry, this process doesn't alter any configuration files or pose any (known) risk to your system integrity or hardware.

Sorry, if this is obtuse, but think, before the days of Mandrake Linux and automounting, this is how people mounted and unmounted every single floppy disk and CD-ROM, every time.

Once mounted, copy the files you want onto your fixed hard-disk (drag and drop  with two Thunar windows?), and then I guess unmount your removable HD through whichever method is easiest (Thunar, if possible).

Then, go through the same process to mount your USB Ipod and copy the data over, unmounting through whichever method works (ideally Thunar). Your Ipod is probably just plain "vfat" partition type, or "hfsplus" if it's a "Macintosh-only" billed Ipod. Yes, those are the exact partition types the mount command looks for after the "-T" switch. 

[http://gentoo-wiki.com/HOWTO_Using_an_iPod_With_Gentoo_Linux](http://gentoo-wiki.com/HOWTO_Using_an_iPod_With_Gentoo_Linux)

This document may prove helpful, as Gentoo and Ubuntu don't differ much in basics like mounting drives. I presume, come to think about it, that your Ipod listed both /dev/sda1 and /dev/sda2, as many (all?) models have both a recovery/firmware partition (32 megs?) and a main one.

Again, sorry for such a mediocre solution and late reply, but at least you'll learn to fish in the process, and won't be at the mercy of your drives autodetecting correctly from now on. Once you get some slamming tunes on your Ipod, you can look over and revise your /etc/fstab file; I think that might help but am not entirely sure. Also, something may be up with hal (hardware abstraction layer)... which for some reason never occurred to me, as well as dbus. Both facilitate automounting by helping your hardware talk together and/or report to the kernel. It's a possible lead, I guess.

Check this thread, too:
[http://ubuntuforums.org/showthread.php?t=421427](http://ubuntuforums.org/showthread.php?t=421427)

---

### Post by d.liberate on 2008-01-12
Thanks again for the detailed reply and advice.  I'll have a go at troubleshooting this over the weekend and post a solution if I manage to figure one out!

---

