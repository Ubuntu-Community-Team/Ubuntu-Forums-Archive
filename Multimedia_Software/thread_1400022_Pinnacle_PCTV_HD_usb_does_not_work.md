---
title: "Pinnacle PCTV HD usb does not work"
date: 2010-02-06
forum: Multimedia Software
---

### Post by Thomas Garman on 2010-02-06
I followed the instructions here:

[http://www.linuxtv.org/wiki/index.ph...Making_it_Work]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_%28801e%29#Making_it_Work")

And my system would not pick up a signal at all or show any channels after scanning.  But, just as proof that the system detects the device, my Virtualbox shows this device (it's name and the fact that it is a tv tuner) as one of the available USB devices when it is plugged in.  (I am not saying I want to use the usb stick with Virtualbox but only that the computer recognizes it and knows what it is and can even name it correctly).

I have followed the instructions on every help forum I have found and never gotten even the slightest response from the usb stick.  There is never any picture or channels scanned.  This is true whether I am using tvtime or kaffeine or me tv.

Both tvtime and me tv say that only dvb is supported when I try to scan for channels.

So, anyway, using the link that I gave above, I got to the point where I downloaded the drivers from here:

[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

and what I got was a tarball.  So I extracted it to my desktop and then changed directories in a terminal to the folder that was on my desktop and then I ran make and then I ran make install.  And then I rebooted.

Well...  still nothing.  Neither Kaffeine nor tvtime nor me tv will detect any channels nor will any picture appear and they all say that I am lacking some kind of dvb support/driver whatever.

Can anyone provide any insight into this problem?

---

### Post by xc3RnbFO8P on 2010-02-06
In the Terminal show the output of:
> lsusb
and
> dmesg

---

### Post by Thomas Garman on 2010-02-06
Here is what appears with lsusb

[B]Bus 001 Device 005: ID 2304:023b Pinnacle Systems, Inc. [hex] 
Bus 001 Device 004: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[B]And here is what appears as a result of dmesg (if you look at what it says at the bottom, it knows that the Pinnacle USB stick is there)

[/B][/B][    0.388455] pci 0000:00:0c.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]
[    0.388462] bus 00 -> node 0
[    0.388468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.388737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.424970] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 *10 11 14 15)
[    0.425120] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.425269] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.425417] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.425566] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.425714] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.425863] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.426012] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 *10 11 14 15)
[    0.426161] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.426309] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.426462] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[    0.426612] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[    0.426774] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.426922] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.427071] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.427221] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.427369] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.427519] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.427667] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.427851] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.428040] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.428398] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.428581] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.428759] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.428937] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.429116] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0
[    0.429294] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0, disabled.
[    0.429474] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    0.429657] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    0.429837] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
[    0.430017] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
[    0.430196] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
[    0.430376] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    0.430555] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    0.430735] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    0.430915] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
[    0.431093] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0, disabled.
[    0.431252] ACPI: WMI: Mapper loaded
[    0.431315] SCSI subsystem initialized
[    0.431315] libata version 3.00 loaded.
[    0.431315] usbcore: registered new interface driver usbfs
[    0.431315] usbcore: registered new interface driver hub
[    0.431315] usbcore: registered new device driver usb
[    0.431315] PCI: Using ACPI for IRQ routing
[    0.436009] Bluetooth: Core ver 2.13
[    0.436025] NET: Registered protocol family 31
[    0.436025] Bluetooth: HCI device and connection manager initialized
[    0.436025] Bluetooth: HCI socket layer initialized
[    0.436025] NET: Registered protocol family 8
[    0.436025] NET: Registered protocol family 20
[    0.436029] NetLabel: Initializing
[    0.436030] NetLabel:  domain hash size = 128
[    0.436031] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.436046] NetLabel:  unlabeled traffic allowed by default
[    0.436060] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.436064] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.440071] AppArmor: AppArmor Filesystem Enabled
[    0.444015] Switched to high resolution mode on CPU 0
[    0.444214] Switched to high resolution mode on CPU 1
[    0.448014] pnp: PnP ACPI init
[    0.448023] ACPI: bus type pnp registered
[    0.451983] pnp: PnP ACPI: found 12 devices
[    0.451985] ACPI: ACPI bus type pnp unregistered
[    0.451988] PnPBIOS: Disabled by ACPI PNP
[    0.452012] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.452014] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.452016] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.452018] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.452020] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.452023] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.452025] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.452027] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.452030] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.452036] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.452040] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.452042] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.452044] system 00:02: ioport range 0x290-0x297 has been reserved
[    0.452051] system 00:0a: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.452055] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.452057] system 00:0b: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.452060] system 00:0b: iomem range 0xbfee0000-0xbfefffff could not be reserved
[    0.452062] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.452065] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.452067] system 00:0b: iomem range 0x100000-0xbfedffff could not be reserved
[    0.452069] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.452072] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.452074] system 00:0b: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.452076] system 00:0b: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.452079] system 00:0b: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.452081] system 00:0b: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.486744] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.486746] pci 0000:00:04.0:   IO window: 0xc000-0xcfff
[    0.486750] pci 0000:00:04.0:   MEM window: 0xfde00000-0xfdefffff
[    0.486753] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.486759] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.486761] pci 0000:00:09.0:   IO window: 0xb000-0xbfff
[    0.486763] pci 0000:00:09.0:   MEM window: 0xf8000000-0xfbffffff
[    0.486766] pci 0000:00:09.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.486768] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.486770] pci 0000:00:0b.0:   IO window: 0xa000-0xafff
[    0.486773] pci 0000:00:0b.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.486775] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.486778] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.486780] pci 0000:00:0c.0:   IO window: 0x9000-0x9fff
[    0.486783] pci 0000:00:0c.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.486785] pci 0000:00:0c.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff
[    0.486793] pci 0000:00:04.0: setting latency timer to 64
[    0.486798] pci 0000:00:09.0: setting latency timer to 64
[    0.486801] pci 0000:00:0b.0: setting latency timer to 64
[    0.486805] pci 0000:00:0c.0: setting latency timer to 64
[    0.486808] bus: 00 index 0 io port: [0x00-0xffff]
[    0.486809] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.486811] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.486813] bus: 01 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.486815] bus: 01 index 2 mmio: [0xfdf00000-0xfdffffff]
[    0.486816] bus: 01 index 3 io port: [0x00-0xffff]
[    0.486818] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.486820] bus: 02 index 0 io port: [0xb000-0xbfff]
[    0.486821] bus: 02 index 1 mmio: [0xf8000000-0xfbffffff]
[    0.486823] bus: 02 index 2 mmio: [0xe0000000-0xefffffff]
[    0.486825] bus: 02 index 3 mmio: [0x0-0x0]
[    0.486826] bus: 03 index 0 io port: [0xa000-0xafff]
[    0.486828] bus: 03 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.486830] bus: 03 index 2 mmio: [0xfdc00000-0xfdcfffff]
[    0.486831] bus: 03 index 3 mmio: [0x0-0x0]
[    0.486833] bus: 04 index 0 io port: [0x9000-0x9fff]
[    0.486834] bus: 04 index 1 mmio: [0xfdb00000-0xfdbfffff]
[    0.486836] bus: 04 index 2 mmio: [0xfda00000-0xfdafffff]
[    0.486838] bus: 04 index 3 mmio: [0x0-0x0]
[    0.486847] NET: Registered protocol family 2
[    0.500056] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.500314] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.501031] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.501410] TCP: Hash tables configured (established 131072 bind 65536)
[    0.501413] TCP reno registered
[    0.508084] NET: Registered protocol family 1
[    0.508196] checking if image is initramfs... it is
[    0.973975] Freeing initrd memory: 7370k freed
[    0.974166] cpufreq: No nForce2 chipset.
[    0.974279] audit: initializing netlink socket (disabled)
[    0.974296] type=2000 audit(1265447952.972:1): initialized
[    0.980722] highmem bounce pool size: 64 pages
[    0.980727] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.981751] VFS: Disk quotas dquot_6.5.1
[    0.981806] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.982433] fuse init (API version 7.10)
[    0.982505] msgmni has been set to 1672
[    0.982679] alg: No test for stdrng (krng)
[    0.982690] io scheduler noop registered
[    0.982691] io scheduler anticipatory registered
[    0.982693] io scheduler deadline registered
[    0.982705] io scheduler cfq registered (default)
[    0.982736] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.997050] pci 0000:00:04.0: Enabling HT MSI Mapping
[    0.997065] pci 0000:00:05.0: Enabling HT MSI Mapping
[    0.997091] pci 0000:00:07.0: Enabling HT MSI Mapping
[    0.997104] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.997118] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.997132] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    0.997146] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    0.997168] pci 0000:02:00.0: Boot video device
[    1.001946] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    1.001967] pcieport-driver 0000:00:09.0: found MSI capability
[    1.001982] pcieport-driver 0000:00:09.0: irq 2303 for MSI/MSI-X
[    1.002027] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.002046] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.002055] pcieport-driver 0000:00:0b.0: irq 2302 for MSI/MSI-X
[    1.002099] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.002117] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.002127] pcieport-driver 0000:00:0c.0: irq 2301 for MSI/MSI-X
[    1.002181] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.002188] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.002307] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.002309] ACPI: Power Button (FF) [PWRF]
[    1.002344] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.002346] ACPI: Power Button (CM) [PWRB]
[    1.002394] fan PNP0C0B:00: registered as cooling_device0
[    1.002399] ACPI: Fan [FAN] (on)
[    1.002669] processor ACPI_CPU:00: registered as cooling_device1
[    1.002694] processor ACPI_CPU:01: registered as cooling_device2
[    1.006024] thermal LNXTHERM:01: registered as thermal_zone0
[    1.006313] ACPI: Thermal Zone [THRM] (40 C)
[    1.006353] isapnp: Scanning for PnP cards...
[    1.358971] isapnp: No Plug & Play device found
[    1.365207] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.365991] brd: module loaded
[    1.366248] loop: module loaded
[    1.366308] Fixed MDIO Bus: probed
[    1.366313] PPP generic driver version 2.4.2
[    1.366361] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.366384] Driver 'sd' needs updating - please use bus_type methods
[    1.366394] Driver 'sr' needs updating - please use bus_type methods
[    1.366534] sata_nv 0000:00:08.0: version 3.5
[    1.366843] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.366854] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.366908] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.366980] scsi0 : sata_nv
[    1.367079] scsi1 : sata_nv
[    1.367210] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    1.367213] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    1.832034] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.840117] ata1.00: ATAPI: TSSTcorp CDDVDW TS-H653Z, 4403, max UDMA/33
[    1.856124] ata1.00: configured for UDMA/33
[    2.324034] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.332115] ata2.00: ATA-7: SAMSUNG HD251HJ, 1AC01114, max UDMA7
[    2.332117] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.340122] ata2.00: configured for UDMA/133
[    2.340744] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-H653Z  4403 PQ: 0 ANSI: 5
[    2.345337] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.345339] Uniform CD-ROM driver Revision: 3.20
[    2.345433] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.345471] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.345523] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD251HJ  1AC0 PQ: 0 ANSI: 5
[    2.345601] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.345614] sd 1:0:0:0: [sda] Write Protect is off
[    2.345616] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.345635] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.345686] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.345696] sd 1:0:0:0: [sda] Write Protect is off
[    2.345697] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.345714] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.345717]  sda: sda1 sda2 sda3 sda4
[    2.379582] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.379609] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.379681] pata_amd 0000:00:06.0: version 0.3.10
[    2.379720] pata_amd 0000:00:06.0: setting latency timer to 64
[    2.379804] scsi2 : pata_amd
[    2.379864] scsi3 : pata_amd
[    2.380346] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.380348] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.546936] ata4: port disabled. ignoring.
[    2.547316] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.547598] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    2.547608] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    2.547625] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.547627] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.547675] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    2.547701] ehci_hcd 0000:00:02.1: debug port 1
[    2.547704] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.547721] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    2.556016] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    2.556086] usb usb1: configuration #1 chosen from 1 choice
[    2.556108] hub 1-0:1.0: USB hub found
[    2.556116] hub 1-0:1.0: 10 ports detected
[    2.556207] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.556482] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    2.556489] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    2.556497] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.556499] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.556533] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.556553] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[    2.614034] usb usb2: configuration #1 chosen from 1 choice
[    2.614053] hub 2-0:1.0: USB hub found
[    2.614060] hub 2-0:1.0: 10 ports detected
[    2.614139] uhci_hcd: USB Universal Host Controller Interface driver
[    2.614214] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.614558] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.614562] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.617039] mice: PS/2 mouse device common for all mice
[    2.629066] rtc_cmos 00:05: RTC can wake from S4
[    2.629099] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.629138] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.629185] device-mapper: uevent: version 1.0.3
[    2.629274] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.629391] device-mapper: multipath: version 1.0.5 loaded
[    2.629393] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.629481] EISA: Probing bus 0 at eisa.0
[    2.629486] Cannot allocate resource for EISA slot 1
[    2.629489] Cannot allocate resource for EISA slot 2
[    2.629503] EISA: Detected 0 cards.
[    2.629578] cpuidle: using governor ladder
[    2.629580] cpuidle: using governor menu
[    2.629986] TCP cubic registered
[    2.630072] NET: Registered protocol family 10
[    2.630392] lo: Disabled Privacy Extensions
[    2.630632] NET: Registered protocol family 17
[    2.630646] Bluetooth: L2CAP ver 2.11
[    2.630647] Bluetooth: L2CAP socket layer initialized
[    2.630649] Bluetooth: SCO (Voice Link) ver 0.6
[    2.630651] Bluetooth: SCO socket layer initialized
[    2.630690] Bluetooth: RFCOMM socket layer initialized
[    2.630696] Bluetooth: RFCOMM TTY layer initialized
[    2.630698] Bluetooth: RFCOMM ver 1.10
[    2.630743] powernow-k8: Found 1 AMD Athlon(tm) Dual Core Processor 4850e processors (2 cpu cores) (version 2.20.00)
[    2.630809] powernow-k8:    0 : fid 0x11 (2500 MHz), vid 0xe
[    2.630811] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xf
[    2.630813] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0x11
[    2.630814] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0x13
[    2.630816] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x15
[    2.630818] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x16
[    2.630871] Using IPI No-Shortcut mode
[    2.630960] registered taskstats version 1
[    2.631073]   Magic number: 14:647:322
[    2.631104] tty tty47: hash matches
[    2.631127] ehci_hcd 0000:00:02.1: hash matches
[    2.631190] rtc_cmos 00:05: setting system clock to 2010-02-06 09:19:15 UTC (1265447955)
[    2.631193] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.631195] EDD information not available.
[    2.631551] Freeing unused kernel memory: 532k freed
[    2.631675] Write protecting the kernel text: 4120k
[    2.631716] Write protecting the kernel read-only data: 1524k
[    2.647349] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.798311] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.798642] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    2.798654] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    2.798659] forcedeth 0000:00:07.0: setting latency timer to 64
[    2.869095] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.002308] usb 1-1: configuration #1 chosen from 1 choice
[    3.113022] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    3.247089] usb 1-2: configuration #1 chosen from 1 choice
[    3.247412] hub 1-2:1.0: USB hub found
[    3.247944] hub 1-2:1.0: 4 ports detected
[    3.316931] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:21:97:c3:02:a4
[    3.316935] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    3.362737] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    3.424764] PM: Starting manual resume from disk
[    3.424767] PM: Resume from partition 8:3
[    3.424769] PM: Checking hibernation image.
[    3.424900] PM: Resume from disk failed.
[    3.447558] EXT4-fs: barriers enabled
[    3.459007] kjournald2 starting.  Commit interval 5 seconds
[    3.459015] EXT4-fs: delayed allocation enabled
[    3.459016] EXT4-fs: file extents enabled
[    3.463634] EXT4-fs: mballoc enabled
[    3.463638] EXT4-fs: mounted filesystem with ordered data mode.
[    3.675819] usb 1-4: configuration #1 chosen from 1 choice
[    7.059450] udev: starting version 141
[    7.236147] cfg80211: Calling CRDA to update world regulatory domain
[    7.532751] cfg80211: World regulatory domain updated:
[    7.532755]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.532757]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.532759]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.532761]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.532763]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.532765]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.789057] dib0700: loaded with support for 8 different device-types
[    7.789268] dvb-usb: found a 'Pinnacle PCTV HD USB Stick' in cold state, will try to load a firmware
[    7.789272] usb 1-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[    7.833799] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    7.842168] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[    7.842184] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
[    7.862089] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[    7.907415] Linux agpgart interface v0.103
[    8.039517] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    8.079632] dib0700: firmware started successfully.
[    8.100842] nvidia: module license 'NVIDIA' taints kernel.
[    8.300242] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[    8.300247] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[    8.300290] usbcore: registered new interface driver rt2500usb
[    8.354664] ACPI: PCI Interrupt Link [APC8] enabled at IRQ 16
[    8.354677] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[    8.354684] nvidia 0000:02:00.0: setting latency timer to 64
[    8.355136] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    8.366551] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[    8.366557] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[    8.366598] HDA Intel 0000:00:05.0: setting latency timer to 64
[    8.503696] psmouse serio1: ID: 10 00 64<6>dvb-usb: found a 'Pinnacle PCTV HD USB Stick' in warm state.
[    8.580093] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.580390] DVB: registering new adapter (Pinnacle PCTV HD USB Stick)
[    8.604937] phy1: Selected rate control algorithm 'pid'
[    8.648158] Registered led device: rt73usb-phy1:radio
[    8.648190] Registered led device: rt73usb-phy1:assoc
[    8.648222] Registered led device: rt73usb-phy1:quality
[    8.648760] usbcore: registered new interface driver rt73usb
[    8.756016] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.023956] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[    9.170992] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[    9.193482] xc5000 2-0064: creating new instance
[    9.193990] xc5000: Successfully identified at address 0x64
[    9.193992] xc5000: Firmware has not been loaded previously
[    9.194069] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:02.1/usb1/1-1/input/input6
[    9.201832] dvb-usb: schedule remote query interval to 50 msecs.
[    9.201837] dvb-usb: Pinnacle PCTV HD USB Stick successfully initialized and connected.
[    9.202036] usbcore: registered new interface driver dvb_usb_dib0700
[    9.317674] lp: driver loaded but no devices found
[    9.382240] Adding 2281220k swap on /dev/sda3.  Priority:-1 extents:1 across:2281220k
[    9.913800] EXT4 FS on sda2, internal journal on sda2:8
[   10.817185] type=1505 audit(1265469563.684:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2019
[   10.860155] type=1505 audit(1265469563.725:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2023
[   10.860288] type=1505 audit(1265469563.725:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2023
[   10.860335] type=1505 audit(1265469563.725:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2023
[   10.860375] type=1505 audit(1265469563.725:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2023
[   10.985166] type=1505 audit(1265469563.852:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2028
[   10.985354] type=1505 audit(1265469563.852:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2028
[   11.010949] type=1505 audit(1265469563.877:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2032
[   13.084924] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   13.084927] vboxdrv: Successfully done.
[   13.084929] vboxdrv: Found 2 processor cores.
[   13.085008] vboxdrv: fAsync=1 offMin=0x2dd985 offMax=0x2dd985
[   13.085576] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   13.085578] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   13.768331] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.768334] Bluetooth: BNEP filters: protocol multicast
[   13.807099] Bridge firewalling registered
[   15.455156] ppdev: user-space parallel port driver
[   19.132513] forcedeth 0000:00:07.0: irq 2300 for MSI/MSI-X
[   19.132717] eth0: no link during initialization.
[   19.133154] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.134012] rt73usb 1-4:1.0: firmware: requesting rt73.bin
[   19.231301] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.063496] wlan0: authenticate with AP 00:22:a4:2a:f5:e9
[   61.068371] wlan0: authenticated
[   61.068373] wlan0: associate with AP 00:22:a4:2a:f5:e9
[   61.070626] wlan0: RX AssocResp from 00:22:a4:2a:f5:e9 (capab=0x431 status=0 aid=1)
[   61.070628] wlan0: associated
[   61.073457] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.169012] wlan0: no IPv6 routers present
[   78.500023] Clocksource tsc unstable (delta = -101752496 ns)
[ 2363.890146] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 2435.796337] xc5000 2-0064: destroying instance
[ 2435.796704] dvb-usb: Pinnacle PCTV HD USB Stick successfully deinitialized and disconnected.
[ 2458.197461] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[ 2458.329380] usb 1-1: device firmware changed
[ 2458.329573] usb 1-1: USB disconnect, address 2
[ 2458.448695] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 2458.582651] usb 1-1: configuration #1 chosen from 1 choice
[ 2458.582999] dvb-usb: found a 'Pinnacle PCTV HD USB Stick' in warm state.
[ 2458.583053] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 2458.583396] DVB: registering new adapter (Pinnacle PCTV HD USB Stick)
[ 2459.170878] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[ 2459.174571] xc5000 2-0064: creating new instance
[ 2459.175122] xc5000: Successfully identified at address 0x64
[ 2459.175126] xc5000: Firmware has not been loaded previously
[ 2459.175269] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:02.1/usb1/1-1/input/input7
[ 2459.206074] dvb-usb: schedule remote query interval to 50 msecs.
[ 2459.206086] dvb-usb: Pinnacle PCTV HD USB Stick successfully initialized and connected.

---

### Post by xc3RnbFO8P on 2010-02-06
It looks OK,
see if you got these drivers installed
[B]dvb-fe-xc5000-1.1.fw 
dvb-usb-dib0700-1.20.fw[/B]
in /lib/firmware
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Stick_(801eSE)]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Stick_(801eSE)")

---

### Post by Thomas Garman on 2010-02-06
[SIZE=2]About

dvb-fe-xc5000-1.1.fw 
dvb-usb-dib0700-1.20.fw

I looked in my lib/firmware and I discovered that I do not have dvb-fe-xc5000-1.1.fw in my lib/firmware folder but I do have a dvb-fe-xc5000-1.6.114.fw file and it is in there as a picture or image file.  It is not like the other files that look like a text files but rather my copy of the  dvb-fe-xc5000-1.6.114.fw file looks like what would it would look like if it was a jpeg or png.  Why is it different from the others?  I don't know.  I suspect that this difference has something to do with the reason tv never works.  I got that file in there by using the wget and cp commands in the terminal just like what it says to do on the wiki page you link to.

As for the dvb-usb-dib0700-1.20.fw file:  yes it is in the lib/firmare folder.[/SIZE]

---

### Post by xc3RnbFO8P on 2010-02-13
Note that only ATSC support is working. **Analog support is not implemented**.

---

### Post by Thomas Garman on 2010-02-13
I am not trying to run it as analog device.  Is there something in the dmesg you are seeing that says "analog"?

---

### Post by xc3RnbFO8P on 2010-02-13
Check if have /dev/dvb/adapter0 if so
> kaffeine /dev/dvb/adapter0
if it still dosent work
> sudo kaffeine /dev/dvb/adapter0
You also use Me-tv
> me-tv /dev/dvb/adapter0
> rig@rig-desktop:~$ me-tv /dev/dvb/adapter0
Me TV 1.1.2
2010-02-13 17:42:58: Using /dev/dvb/adapter0/frontend0
2010-02-13 17:42:58: Device: 'Philips TDA10046H DVB-T' (DVB-T)
2010-02-13 17:42:59: Changing channel to 'DR2'
2010-02-13 17:42:59: Frontend::tune_to(506000000)
2010-02-13 17:42:59: Waiting for signal lock ...
2010-02-13 17:43:01: Got signal lock
2010-02-13 17:43:01: Channel changed to DR2

---

### Post by Thomas Garman on 2010-02-13
There is a dev/dvb/adapter0 object and this is what I get running the code in terminal...

thomas@thomas-desktop:~$ sudo kaffeine /dev/dvb/adapter0
[sudo] password for thomas: 
kbuildsycoca running...
/dev/dvb/adapter0/frontend0 : opened ( Samsung S5H1411 QAM/8VSB Frontend )
0 EPG plugins loaded for device 0:0.
 HDIO_GET_DMA failed: Inappropriate ioctl for device
kbuildsycoca running...
Reusing existing ksycoca
DvbCam::probe(): /dev/dvb/adapter0/ca0: : No such file or directory


NO.  And then when I try Kaffeine...  nothing.  No device.

Looking over the dmesg material from earlier has led me to the following conclusion:

The device is hooked to usb that derives from a pci card installed on my motherboard.  So, neither tvtime, nor kaffeine, nor me-tv (they all have the same problem for me) is able to look first at the pci card and then find the usb tv tuner.

Is that true?  Does anyone know?

Please do not suggest ME-TV since I already know that the exact same issue exists there.  NO tv package is able to detect the usb device because all of my usb devices come through a pci card installed in my motherboard.  Anyway, that's the theory I believe now.

---

### Post by Thomas Garman on 2010-02-23
My Pinnacle PCTV usb tv stcik now works.  I followed all of the steps in these two links:

[http://www.linuxtv.org/wiki/index.ph...Making_it_Work]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_%28801e%29#Making_it_Work")
[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

But these steps never worked for me in Ubuntu 9.04.  I recently upgraded to Ubuntu 9.10 and in the course of re-installing my nvidia drivers using System --> Administration --> Hardware Drivers I was presented with the option of installing DVB drivers.  This option never appeared in 9.04 before.  So, I activated the driver.

Me TV and tvtime still would not work.  Why?  Me Tv is not able to find an initial channel.conf file.  tvtime looks in the wrong place for a device.  Neither will scan for channels.

So, installed Kaffeine, which does actually scan for channels...  AND IT WORKED!  Kaffeine picked up all of the broadcast channels and plays them with audio.

The only problem I have is that the channels that come from NBC, CBS ABC are all very delayed and choppy.  The picture that shows for these channels is a still image that refreshes very slowly and the audio comes in an out.  But Public Television and all the Spanish language channels play just fine as well as a few weird ones that get broadcast in Chicago.

---

