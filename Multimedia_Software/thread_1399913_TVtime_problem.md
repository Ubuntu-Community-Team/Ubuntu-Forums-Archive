---
title: "TVtime problem"
date: 2010-02-06
forum: Multimedia Software
---

### Post by rapattack1 on 2010-02-06
I have installed TVtime and the tv pci card is a Pixelview Play tv pro Conexant bt878 chipset. I get an off image from it using either antenna or composite. No audio. I have read lots of sites and need a hand to get this to go further. I also want to capture but do not understand MythTV. I tried it maybe a year ago on a different install of Ubuntu but couldn't figure it out. I had a Hauppauge card then. The picture looks like this
[http://s273.photobucket.com/albums/jj202/rapattack_album/?action=view&current=mvi_0107.flv](http://s273.photobucket.com/albums/jj202/rapattack_album/?action=view&current=mvi_0107.flv)
and attached is a still image of it.
I typed dmesg and got this:
> 
[    0.181733] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.181759] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.181767] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.181774] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.181782] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.181789] pci 0000:00:1f.1: reg 20 io port: [0xfc00-0xfc0f]
[    0.181797] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.181831] pci 0000:00:1f.2: reg 10 io port: [0xefe0-0xefe7]
[    0.181838] pci 0000:00:1f.2: reg 14 io port: [0xefac-0xefaf]
[    0.181845] pci 0000:00:1f.2: reg 18 io port: [0xefa0-0xefa7]
[    0.181852] pci 0000:00:1f.2: reg 1c io port: [0xefa8-0xefab]
[    0.181859] pci 0000:00:1f.2: reg 20 io port: [0xef90-0xef9f]
[    0.181915] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.181968] pci 0000:00:1f.5: reg 10 io port: [0xe800-0xe8ff]
[    0.181976] pci 0000:00:1f.5: reg 14 io port: [0xee80-0xeebf]
[    0.181983] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfebffc00-0xfebffdff]
[    0.181991] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfebff400-0xfebff4ff]
[    0.182023] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.182028] pci 0000:00:1f.5: PME# disabled
[    0.182073] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.182080] pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.182087] pci 0000:01:00.0: reg 18 32bit mmio: [0xefd80000-0xefdfffff]
[    0.182104] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe9e0000-0xfe9fffff]
[    0.182165] pci 0000:00:01.0: bridge 32bit mmio: [0xfc900000-0xfe9fffff]
[    0.182170] pci 0000:00:01.0: bridge 32bit mmio pref: [0xdfd00000-0xefdfffff]
[    0.182212] pci 0000:02:03.0: reg 10 32bit mmio: [0xfeaff800-0xfeafffff]
[    0.182220] pci 0000:02:03.0: reg 14 io port: [0xdc00-0xdc7f]
[    0.182263] pci 0000:02:03.0: supports D2
[    0.182266] pci 0000:02:03.0: PME# supported from D2 D3hot D3cold
[    0.182270] pci 0000:02:03.0: PME# disabled
[    0.182305] pci 0000:02:04.0: reg 10 io port: [0xdf00-0xdf3f]
[    0.182313] pci 0000:02:04.0: reg 14 io port: [0xdfa0-0xdfaf]
[    0.182320] pci 0000:02:04.0: reg 18 io port: [0xd880-0xd8ff]
[    0.182328] pci 0000:02:04.0: reg 1c 32bit mmio: [0xfeafe000-0xfeafefff]
[    0.182335] pci 0000:02:04.0: reg 20 32bit mmio: [0xfeac0000-0xfeadffff]
[    0.182365] pci 0000:02:04.0: supports D1
[    0.182404] pci 0000:02:09.0: reg 10 32bit mmio: [0xfeafc000-0xfeafdfff]
[    0.182450] pci 0000:02:09.0: supports D1
[    0.182453] pci 0000:02:09.0: PME# supported from D3hot D3cold
[    0.182458] pci 0000:02:09.0: PME# disabled
[    0.182492] pci 0000:02:0a.0: reg 10 io port: [0xd400-0xd4ff]
[    0.182499] pci 0000:02:0a.0: reg 14 32bit mmio: [0xfeaff400-0xfeaff4ff]
[    0.182525] pci 0000:02:0a.0: reg 30 32bit mmio: [0xfeae0000-0xfeaeffff]
[    0.182544] pci 0000:02:0a.0: supports D1 D2
[    0.182547] pci 0000:02:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.182551] pci 0000:02:0a.0: PME# disabled
[    0.182592] pci 0000:02:0b.0: reg 10 32bit mmio: [0xefefe000-0xefefefff]
[    0.182681] pci 0000:02:0b.1: reg 10 32bit mmio: [0xefeff000-0xefefffff]
[    0.182768] pci 0000:00:1e.0: transparent bridge
[    0.182774] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.182779] pci 0000:00:1e.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.182784] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xefe00000-0xefefffff]
[    0.182798] pci_bus 0000:00: on NUMA node 0
[    0.182803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.182927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.190588] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.190713] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.190835] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.190957] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.191079] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.191202] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.191325] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.191448] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.191683] SCSI subsystem initialized
[    0.191727] libata version 3.00 loaded.
[    0.191727] usbcore: registered new interface driver usbfs
[    0.191727] usbcore: registered new interface driver hub
[    0.191727] usbcore: registered new device driver usb
[    0.192080] ACPI: WMI: Mapper loaded
[    0.192080] PCI: Using ACPI for IRQ routing
[    0.204013] Bluetooth: Core ver 2.15
[    0.204034] NET: Registered protocol family 31
[    0.204034] Bluetooth: HCI device and connection manager initialized
[    0.204034] Bluetooth: HCI socket layer initialized
[    0.204034] NetLabel: Initializing
[    0.204034] NetLabel:  domain hash size = 128
[    0.204034] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204050] NetLabel:  unlabeled traffic allowed by default
[    0.204166] hpet clockevent registered
[    0.204170] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.204176] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.204183] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.220017] pnp: PnP ACPI init
[    0.220046] ACPI: bus type pnp registered
[    0.225781] pnp: PnP ACPI: found 15 devices
[    0.225785] ACPI: ACPI bus type pnp unregistered
[    0.225791] ASUS P4P800 detected. Disabling PnPBIOS
[    0.225793] PnPBIOS: Disabled
[    0.225812] system 00:0b: ioport range 0x680-0x6ff has been reserved
[    0.225816] system 00:0b: ioport range 0x290-0x297 has been reserved
[    0.225825] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.225828] system 00:0c: ioport range 0x800-0x87f has been reserved
[    0.225832] system 00:0c: ioport range 0x480-0x4bf has been reserved
[    0.225836] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.225840] system 00:0c: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.225847] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.225851] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.225858] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.225862] system 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[    0.225866] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.225869] system 00:0e: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.225873] system 00:0e: iomem range 0xfff00000-0xffffffff has been reserved
[    0.260586] AppArmor: AppArmor Filesystem Enabled
[    0.260612] pci 0000:02:0a.0: BAR 6: address space collision on of device [0xfeae0000-0xfeaeffff]
[    0.260635] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.260638] pci 0000:00:01.0:   IO window: disabled
[    0.260643] pci 0000:00:01.0:   MEM window: 0xfc900000-0xfe9fffff
[    0.260648] pci 0000:00:01.0:   PREFETCH window: 0xdfd00000-0xefdfffff
[    0.260655] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.260659] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.260665] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff
[    0.260670] pci 0000:00:1e.0:   PREFETCH window: 0xefe00000-0xefefffff
[    0.260688] pci 0000:00:1e.0: setting latency timer to 64
[    0.260694] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.260698] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.260701] pci_bus 0000:01: resource 1 mem: [0xfc900000-0xfe9fffff]
[    0.260704] pci_bus 0000:01: resource 2 pref mem [0xdfd00000-0xefdfffff]
[    0.260707] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.260710] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.260713] pci_bus 0000:02: resource 2 pref mem [0xefe00000-0xefefffff]
[    0.260716] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.260719] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.260769] NET: Registered protocol family 2
[    0.260904] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.261623] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.262341] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.262857] TCP: Hash tables configured (established 131072 bind 65536)
[    0.262860] TCP reno registered
[    0.263033] NET: Registered protocol family 1
[    0.263140] Trying to unpack rootfs image as initramfs...
[    0.496199] Freeing initrd memory: 7711k freed
[    0.505054] cpufreq-nforce2: No nForce2 chipset.
[    0.505091] Scanning for low memory corruption every 60 seconds
[    0.505229] audit: initializing netlink socket (disabled)
[    0.505255] type=2000 audit(1265458839.504:1): initialized
[    0.513784] highmem bounce pool size: 64 pages
[    0.513792] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.515554] VFS: Disk quotas dquot_6.5.2
[    0.515629] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.516328] fuse init (API version 7.12)
[    0.516430] msgmni has been set to 1705
[    0.516712] alg: No test for stdrng (krng)
[    0.516733] io scheduler noop registered
[    0.516736] io scheduler anticipatory registered
[    0.516739] io scheduler deadline registered
[    0.516792] io scheduler cfq registered (default)
[    0.516903] pci 0000:01:00.0: Boot video device
[    0.517046] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.517078] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.517248] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.517253] ACPI: Power Button [PWRF]
[    0.517321] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.517325] ACPI: Power Button [PWRB]
[    0.517563] processor LNXCPU:00: registered as cooling_device0
[    0.517614] processor LNXCPU:01: registered as cooling_device1
[    0.520796] isapnp: Scanning for PnP cards...
[    0.705025] Switched to high resolution mode on CPU 1
[    0.708030] Switched to high resolution mode on CPU 0
[    0.874517] isapnp: No Plug & Play device found
[    0.875879] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.875988] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.876086] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.876398] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.876539] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.877919] brd: module loaded
[    0.878490] loop: module loaded
[    0.878591] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.878730] ata_piix 0000:00:1f.1: version 2.13
[    0.878746] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.878756]   alloc irq_desc for 18 on node -1
[    0.878759]   alloc kstat_irqs on node -1
[    0.878768] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.878825] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.878932] scsi0 : ata_piix
[    0.879050] scsi1 : ata_piix
[    0.880941] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    0.880946] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    0.880970] ata_piix 0000:00:1f.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.880977] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    0.881041] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.881321] scsi2 : ata_piix
[    0.881402] scsi3 : ata_piix
[    0.881450] ata3: SATA max UDMA/133 cmd 0xefe0 ctl 0xefac bmdma 0xef90 irq 18
[    0.881454] ata4: SATA max UDMA/133 cmd 0xefa0 ctl 0xefa8 bmdma 0xef98 irq 18
[    0.881506] sata_promise 0000:02:04.0: version 2.12
[    0.881519]   alloc irq_desc for 23 on node -1
[    0.881522]   alloc kstat_irqs on node -1
[    0.881528] sata_promise 0000:02:04.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.896088] scsi4 : sata_promise
[    0.896163] scsi5 : sata_promise
[    0.896236] scsi6 : sata_promise
[    0.896284] ata5: SATA max UDMA/133 mmio m4096@0xfeafe000 ata 0xfeafe200 irq 23
[    0.896288] ata6: SATA max UDMA/133 mmio m4096@0xfeafe000 ata 0xfeafe280 irq 23
[    0.896291] ata7: PATA max UDMA/133 mmio m4096@0xfeafe000 ata 0xfeafe300 irq 23
[    0.897412] Fixed MDIO Bus: probed
[    0.897461] PPP generic driver version 2.4.2
[    0.897600] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.897624] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.897637] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.897642] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.897712] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.901618] ehci_hcd 0000:00:1d.7: debug port 1
[    0.901626] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.901633] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebff800
[    0.916012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.916122] usb usb1: configuration #1 chosen from 1 choice
[    0.916167] hub 1-0:1.0: USB hub found
[    0.916180] hub 1-0:1.0: 8 ports detected
[    0.916271] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.916293] uhci_hcd: USB Universal Host Controller Interface driver
[    0.916343]   alloc irq_desc for 16 on node -1
[    0.916346]   alloc kstat_irqs on node -1
[    0.916354] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.916361] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.916366] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.916405] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.916436] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eec0
[    0.916534] usb usb2: configuration #1 chosen from 1 choice
[    0.916572] hub 2-0:1.0: USB hub found
[    0.916584] hub 2-0:1.0: 2 ports detected
[    0.916641]   alloc irq_desc for 19 on node -1
[    0.916644]   alloc kstat_irqs on node -1
[    0.916649] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.916656] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.916661] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.916698] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.916728] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ef00
[    0.916827] usb usb3: configuration #1 chosen from 1 choice
[    0.916861] hub 3-0:1.0: USB hub found
[    0.916872] hub 3-0:1.0: 2 ports detected
[    0.916936] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.916943] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.916947] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.916993] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.917016] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef20
[    0.917109] usb usb4: configuration #1 chosen from 1 choice
[    0.917142] hub 4-0:1.0: USB hub found
[    0.917151] hub 4-0:1.0: 2 ports detected
[    0.917209] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.917216] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.917220] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.917264] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.917286] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef40
[    0.917383] usb usb5: configuration #1 chosen from 1 choice
[    0.917416] hub 5-0:1.0: USB hub found
[    0.917425] hub 5-0:1.0: 2 ports detected
[    0.917562] PNP: No PS/2 controller found. Probing ports directly.
[    0.920236] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.920247] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.920353] mice: PS/2 mouse device common for all mice
[    0.920478] rtc_cmos 00:02: RTC can wake from S4
[    0.920521] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.920545] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.920677] device-mapper: uevent: version 1.0.3
[    0.920799] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.920899] device-mapper: multipath: version 1.1.0 loaded
[    0.920904] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.921063] EISA: Probing bus 0 at eisa.0
[    0.921101] EISA: Detected 0 cards.
[    0.921226] cpuidle: using governor ladder
[    0.921231] cpuidle: using governor menu
[    0.921965] TCP cubic registered
[    0.922125] NET: Registered protocol family 10
[    0.922738] lo: Disabled Privacy Extensions
[    0.923197] NET: Registered protocol family 17
[    0.923220] Bluetooth: L2CAP ver 2.13
[    0.923222] Bluetooth: L2CAP socket layer initialized
[    0.923226] Bluetooth: SCO (Voice Link) ver 0.6
[    0.923228] Bluetooth: SCO socket layer initialized
[    0.923273] Bluetooth: RFCOMM TTY layer initialized
[    0.923278] Bluetooth: RFCOMM socket layer initialized
[    0.923280] Bluetooth: RFCOMM ver 1.11
[    0.923324] Using IPI No-Shortcut mode
[    0.923407] PM: Resume from disk failed.
[    0.923425] registered taskstats version 1
[    0.923579]   Magic number: 14:965:328
[    0.923657] rtc_cmos 00:02: setting system clock to 2010-02-06 12:20:40 UTC (1265458840)
[    0.923662] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.923664] EDD information not available.
[    1.044556] ata3.00: ATA-6: ST380013AS, 8.12, max UDMA/133
[    1.044561] ata3.00: 156250000 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.045465] ata4.00: ATA-6: WDC WD360GD-00FLA2, 31.08F31, max UDMA/133
[    1.045469] ata4.00: 72303840 sectors, multi 16: LBA48 
[    1.060566] ata3.00: configured for UDMA/133
[    1.061589] ata4.00: configured for UDMA/133
[    1.220289] ata2.00: ATAPI: PIODATA DVD-RW DVR-108DX, 1.10, max UDMA/66
[    1.220333] ata2.01: ATAPI: LITE-ON DVD SOHD-16P9S, FS07, max UDMA/33
[    1.224024] ata5: SATA link down (SStatus 0 SControl 300)
[    1.236199] ata2.00: configured for UDMA/66
[    1.244184] ata2.01: configured for UDMA/33
[    1.256423] scsi 1:0:0:0: CD-ROM            PIODATA  DVD-RW DVR-108DX 1.10 PQ: 0 ANSI: 5
[    1.280015] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.280020] Uniform CD-ROM driver Revision: 3.20
[    1.280128] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.280198] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.280725] scsi 1:0:1:0: CD-ROM            LITE-ON  DVD SOHD-16P9S   FS07 PQ: 0 ANSI: 5
[    1.282508] sr1: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    1.282608] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.282658] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    1.282782] scsi 2:0:0:0: Direct-Access     ATA      ST380013AS       8.12 PQ: 0 ANSI: 5
[    1.282937] sd 2:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.282959] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.283044] sd 2:0:0:0: [sda] Write Protect is off
[    1.283050] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.283102] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.283116] scsi 3:0:0:0: Direct-Access     ATA      WDC WD360GD-00FL 31.0 PQ: 0 ANSI: 5
[    1.283314] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.283351]  sda:
[    1.283388] sd 3:0:0:0: [sdb] 72303840 512-byte logical blocks: (37.0 GB/34.4 GiB)
[    1.283520] sd 3:0:0:0: [sdb] Write Protect is off
[    1.283525] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.283559] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.283729]  sdb: sda1 sda2 < sdb1
[    1.293985] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.309684]  sda5 >
[    1.309979] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.604025] ata6: SATA link down (SStatus 0 SControl 300)
[    1.632014] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.760080] Freeing unused kernel memory: 540k freed
[    1.760671] Write protecting the kernel text: 4568k
[    1.760725] Write protecting the kernel read-only data: 1836k
[    1.808499] usb 2-1: configuration #1 chosen from 1 choice
[    1.911771] Linux agpgart interface v0.103
[    1.918179] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    1.948813] Floppy drive(s): fd0 is 1.44M
[    1.965089] FDC 0 is a post-1991 82077
[    1.972647] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[    2.055032] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.099545]   alloc irq_desc for 20 on node -1
[    2.099552]   alloc kstat_irqs on node -1
[    2.099564] ohci1394 0000:02:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.104672] 8139too Fast Ethernet driver 0.9.28
[    2.154064] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.159646]   alloc irq_desc for 22 on node -1
[    2.159652]   alloc kstat_irqs on node -1
[    2.159669] 8139too 0000:02:0a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.161024] eth0: RealTek RTL8139 at 0xd400, 00:04:e2:0d:f6:ca, IRQ 22
[    2.237697] usb 3-1: configuration #1 chosen from 1 choice
[    2.249917] usbcore: registered new interface driver hiddev
[    2.263906] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    2.264023] generic-usb 0003:045E:00DD.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.1-1/input0
[    2.287737] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input4
[    2.287919] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.1-1/input1
[    2.287943] usbcore: registered new interface driver usbhid
[    2.287947] usbhid: v2.6:USB HID core driver
[    2.489024] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    2.643785] usb 3-2: configuration #1 chosen from 1 choice
[    2.666788] input: HID 04b3:310b as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    2.666905] generic-usb 0003:04B3:310B.0003: input,hidraw2: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:1d.1-2/input0
[    2.832408] xor: automatically using best checksumming function: pIII_sse
[    2.852007]    pIII_sse  :  4860.000 MB/sec
[    2.852011] xor: using function: pIII_sse (4860.000 MB/sec)
[    2.855117] device-mapper: dm-raid45: initialized v0.2594b
[    3.176853] PM: Starting manual resume from disk
[    3.176859] PM: Resume from partition 8:5
[    3.176861] PM: Checking hibernation image.
[    3.177042] PM: Resume from disk failed.
[    3.200470] EXT4-fs (sda1): barriers enabled
[    3.219931] kjournald2 starting: pid 412, dev sda1:8, commit interval 5 seconds
[    3.219948] EXT4-fs (sda1): delayed allocation enabled
[    3.219953] EXT4-fs: file extents enabled
[    3.224865] EXT4-fs: mballoc enabled
[    3.224890] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.432244] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800000447d7]
[    3.933276] type=1505 audit(1265458843.509:2): operation="profile_load" pid=435 name=/usr/share/gdm/guest-session/Xsession
[    3.940871] type=1505 audit(1265458843.516:3): operation="profile_load" pid=436 name=/sbin/dhclient3
[    3.941566] type=1505 audit(1265458843.516:4): operation="profile_load" pid=436 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.941947] type=1505 audit(1265458843.516:5): operation="profile_load" pid=436 name=/usr/lib/connman/scripts/dhclient-script
[    4.003244] type=1505 audit(1265458843.576:6): operation="profile_load" pid=437 name=/usr/bin/evince
[    4.014671] type=1505 audit(1265458843.588:7): operation="profile_load" pid=437 name=/usr/bin/evince-previewer
[    4.021406] type=1505 audit(1265458843.596:8): operation="profile_load" pid=437 name=/usr/bin/evince-thumbnailer
[    4.041383] type=1505 audit(1265458843.616:9): operation="profile_load" pid=439 name=/usr/lib/cups/backend/cups-pdf
[    4.042190] type=1505 audit(1265458843.616:10): operation="profile_load" pid=439 name=/usr/sbin/cupsd
[   14.950833] udev: starting version 147
[   14.967011] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k 
[   15.101912] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.108230] parport_pc 00:08: reported by Plug and Play ACPI
[   15.108338] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   15.144177] intel_rng: FWH not detected
[   15.170425] lp: driver loaded but no devices found
[   15.209553] lp0: using parport0 (interrupt-driven).
[   15.219826] EXT4-fs (sda1): internal journal on sda1:8
[   15.454890] gameport: NS558 PnP Gameport is pnp00:09/gameport0, io 0x201, speed 817kHz
[   15.464858] ppdev: user-space parallel port driver
[   15.500954] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.535766]   alloc irq_desc for 17 on node -1
[   15.535772]   alloc kstat_irqs on node -1
[   15.535784] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.535821] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.709052] Linux video capture interface: v2.00
[   15.800155] kjournald starting.  Commit interval 5 seconds
[   15.800626] EXT3 FS on sdb1, internal journal
[   15.800636] EXT3-fs: mounted filesystem with writeback data mode.
[   15.856028] intel8x0_measure_ac97_clock: measured 53415 usecs (2574 samples)
[   15.856035] intel8x0: clocking to 48000
[   15.972069] __ratelimit: 6 callbacks suppressed
[   15.972075] type=1505 audit(1265458855.548:13): operation="profile_replace" pid=921 name=/usr/share/gdm/guest-session/Xsession
[   15.975036] type=1505 audit(1265458855.548:14): operation="profile_replace" pid=922 name=/sbin/dhclient3
[   15.975864] type=1505 audit(1265458855.548:15): operation="profile_replace" pid=922 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.976319] type=1505 audit(1265458855.552:16): operation="profile_replace" pid=922 name=/usr/lib/connman/scripts/dhclient-script
[   15.987304] type=1505 audit(1265458855.560:17): operation="profile_replace" pid=976 name=/usr/bin/evince
[   15.994891] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   16.003149] type=1505 audit(1265458855.576:18): operation="profile_replace" pid=976 name=/usr/bin/evince-previewer
[   16.010962] type=1505 audit(1265458855.584:19): operation="profile_replace" pid=976 name=/usr/bin/evince-thumbnailer
[   16.020767] bttv: driver version 0.9.18 loaded
[   16.020774] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   16.020876] bttv: Bt8xx card found (0).
[   16.020906] bttv 0000:02:0b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   16.020924] bttv0: Bt878 (rev 17) at 0000:02:0b.0, irq: 23, latency: 64, mmio: 0xefefe000
[   16.023035] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   16.023044] IRQ 23/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.023099] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   16.036410] tveeprom 0-0050: Huh, no eeprom present (err=-6)?
[   16.036418] bttv0: tuner type unset
[   16.036565] bttv0: registered device video0
[   16.036615] bttv0: registered device vbi0
[   16.062253] type=1505 audit(1265458855.636:20): operation="profile_replace" pid=996 name=/usr/lib/cups/backend/cups-pdf
[   16.063188] type=1505 audit(1265458855.636:21): operation="profile_replace" pid=996 name=/usr/sbin/cupsd
[   16.074079] type=1505 audit(1265458855.648:22): operation="profile_replace" pid=997 name=/usr/sbin/mysqld-akonadi
[   17.798374] CPU0 attaching NULL sched-domain.
[   17.798382] CPU1 attaching NULL sched-domain.
[   17.813074] CPU0 attaching sched-domain:
[   17.813080]  domain 0: span 0-1 level SIBLING
[   17.813084]   groups: 0 1
[   17.813089]   domain 1: span 0-1 level MC
[   17.813092]    groups: 0-1 (__cpu_power = 2048)
[   17.813099] CPU1 attaching sched-domain:
[   17.813101]  domain 0: span 0-1 level SIBLING
[   17.813105]   groups: 1 0
[   17.813109]   domain 1: span 0-1 level MC
[   17.813112]    groups: 0-1 (__cpu_power = 2048)
[   21.039619] CPU0 attaching NULL sched-domain.
[   21.039629] CPU1 attaching NULL sched-domain.
[   21.056122] CPU0 attaching sched-domain:
[   21.056131]  domain 0: span 0-1 level SIBLING
[   21.056138]   groups: 0 1
[   21.056150] CPU1 attaching sched-domain:
[   21.056154]  domain 0: span 0-1 level SIBLING
[   21.056159]   groups: 1 0
[   26.908012] eth0: no IPv6 routers present
[   93.444018] bttv0: timeout: drop=71 irq=1000/1000, risc=32e3f0cc, bits: HSYNC FDSR
[  145.512028] bttv0: timeout: drop=320 irq=3938/3938, risc=3308403c, bits: HSYNC
[ 1676.404012] bttv0: timeout: drop=441 irq=5349/5349, risc=32db910c, bits: HSYNC OFLOW FDSR
[ 5095.611013] bttv0: reset, reinitialize
[ 5655.072010] bttv0: timeout: drop=831 irq=37842/37842, risc=3308403c, bits: HSYNC OFLOW
[ 6067.552034] usb 5-2: new full speed USB device using uhci_hcd and address 2
[ 6067.749099] usb 5-2: configuration #1 chosen from 1 choice
[ 6123.536055] usb 5-2: USB disconnect, address 2
carla@carla-desktop:~$ 

Probably have included too much but thought i would add this after this command was mentioned in another post!

---

### Post by xc3RnbFO8P on 2010-02-06
Try this:
> sudo gedit /etc/modprobe.conf
add this line:
> options bttv card=70 tuner=28 radio=1
save and restart the computer.

---

### Post by rapattack1 on 2010-02-06
Wow thanks so much. The picture is so good! No audio though. I am happy to make some progress as this has long eluded me. On the antenna how do you change channels? Or is it a matter of getting the remote to work with this?

Interesting. I just noticed when i used the remote it opened vlc ...didn't matter what i pressed. I know vlc can capture. I used to do some capturing a while back via a webcam.

---

### Post by xc3RnbFO8P on 2010-02-07
Show the output of:
> dmesg | grep bttv

---

### Post by rapattack1 on 2010-02-07
Here it is
> carla@carla-desktop:~$ dmesg | grep bttv
[   15.677535] bttv: driver version 0.9.18 loaded
[   15.677541] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   15.677651] bttv: Bt8xx card found (0).
[   15.677680] bttv 0000:02:0b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   15.677696] bttv0: Bt878 (rev 17) at 0000:02:0b.0, irq: 23, latency: 64, mmio: 0xefefe000
[   15.677831] bttv0: using: Prolink Pixelview PV-BT878P+ (Rev.4C,8E) [card=70,insmod option]
[   15.677837] IRQ 23/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   15.677969] bttv0: gpio: en=00000000, out=00000000 in=00ffc0ff [init]
[   15.681380] bttv0: tuner type=28
[   15.873589] bttv0: audio absent, no audio device found!
[   16.066780] bttv0: registered device video0
[   16.066832] bttv0: registered device vbi0
[   16.066878] bttv0: registered device radio0
[   16.066900] bttv0: PLL: 28636363 => 35468950 .. ok
[   16.096711] input: bttv IR (card=70) as /devices/pci0000:00/0000:00:1e.0/0000:02:0b.0/input/input6


---

### Post by xc3RnbFO8P on 2010-02-07
Can you show screenshot of:
1.
> alsamixer -V --view=all
maximize widow (picture 1)
2.
press F6, I can choose sound card 0 and 1 (picture 2)

---

### Post by rapattack1 on 2010-02-07
Did i capture this right?

---

### Post by xc3RnbFO8P on 2010-02-07
We need to see the rest of the sound card (it is only 50% I think),
use the right arrow key to get to far right and take a screenshot.
Then press F6, is there a option to choose between sound card 0 or 1,
if so choose 1, and take a screenshot.

---

### Post by rapattack1 on 2010-02-07
OK new screenshot is here. How do i see a difference when i press F6? Nothing is happening.

---

### Post by xc3RnbFO8P on 2010-02-08
> How do i see a difference when i press F6? Nothing is happening.
You dont have that option, to be sure try:
> alsamixer -c 1
You can try to use arrow keys to decrease volume and **M** to unmute (**MM** is muted, see picture).
If have audio jack on your TV card (green), you can connect
TV card **green jack** to the **blue jack** on the soundcard or use amplifier.

---

### Post by rapattack1 on 2010-02-08
> carla@carla-desktop:~$ alsamixer -c 1
No mixer elems found

carla@carla-desktop:~$
I don't have that one either?

The tv tuner is connected to the soundcard the way you described!

So is my aim to up the sound or unmute one of the audio things? Sorry i am not following.
I am still unused to the terms that i see like pcm, surround, lfe, center and Line. What does all that mean?

---

### Post by xc3RnbFO8P on 2010-02-08
> So is my aim to up the sound or unmute one of the audio things?
yes, start with Line and Aux.
> I am still unused to the terms that i see like pcm, surround, lfe, center and Line. What does all that mean?
> PCM stands for pulse code modulation. In the context of audio coding PCM encodes an audio waveform in the time domain as a series of amplitudes.
[http://en.wikipedia.org/wiki/Sound_card_mixer]("http://en.wikipedia.org/wiki/Sound_card_mixer")

---

### Post by rapattack1 on 2010-02-18
OK I upped Line and Aux.

I gave that wiki a look but i think it will take time for me to understand. I will read it a few more times and see how i go. I have read so many pages over the years and am finding it hard to grasp completely!

OK what should i do next?

---

### Post by rapattack1 on 2010-02-27
):P
No one? I am finding it hard to understand the whole sound issue. Can someone help?

---

### Post by Uncle Spellbinder on 2010-02-27
> **rapattack1 said:**
> No one? I am finding it hard to understand the whole sound issue. Can someone help?

There's a much more comprehensive thread on the TVTime sound issue (with many workarounds) here: [http://ubuntuforums.org/showthread.php?t=1320515](http://ubuntuforums.org/showthread.php?t=1320515)

A bug has been filed here: [https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770?comments=all](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770?comments=all)

Nothing has worked for me in Karmic at all. Simply cannot get sound. I'm going to try in Lucid soon and see if anything has changed in that regard.

---

### Post by gordintoronto on 2010-02-27
Re: installing Mythtv
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by rapattack1 on 2010-02-27
Uncle! OK will give that thread a read when i have more time. What is Lucid? I just id a google search...so it is a theme. How does it make a difference to getting video capturing happening? Well audio in our case?

gordintoronto-Does MythTV also capture? That is ultimately what i want to do. I looked that page and couldn't see anything about capturing. I think i have had MythTV installed before and found it hard to get happening. I think i had a different machine and the card was a Hauppauge then.

---

### Post by Uncle Spellbinder on 2010-02-27
> **rapattack1 said:**
> What is Lucid?

The next version of Ubuntu: [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

As far as MythTV, it's a MAJOR CHORE to get going. A waste of time, as I have the same issue on Karmic with MythTV. No Sound. Both MythTV and TVTime worked fine in Jaunty and previous versions.

---

### Post by rapattack1 on 2010-02-27
Hi Uncle i am not interested in the next version of Ubuntu. I just installed this one a few weeks ago and i had to get it from someone that has more internet usage than myself. Anyway i would rather wait for a while so people get the bugs ironed out a bit.

Yeah that is my experience with MythTV too but then again i don't know crap yet when it comes to Linux. 2.5 years and i still struggle. I can't be down on myself though as i have a neurological condition and am doing much better than expected!

---

### Post by stefcep on 2010-02-28
I installed Kaffeine and my USB tuner worked straight away.  With TvTime I got nothing.  So I'd recommend Kaffeine.  In fact I'd recommend Kaffeine as your all-in-one media playback and audio cd burner.  brilliant

---

### Post by rapattack1 on 2010-02-28
Hmmmmm looks interesting but i can't see anything about capturing . I know vlc does it but i don't know how.

---

### Post by lukem on 2010-02-28
Rapattack1
I hope you find some help with this.  I would like to do some video capture also (mostly a lot of old family VHS tapes) and I don't know what hardware or software to use.  I want to do it with Ubuntu of course.
Good luck.

---

### Post by rapattack1 on 2010-02-28
Hi yes i got overexcited because for a long time i wasn't able to get a picture let alone sound. So i thought wow i can get this done.

Fortunately i do also run a separate machine with windows on it and have a video capture card on that. I transferred all the vhs tapes onto the machine and burnt them on dvd's. Ultimately Linux is my future and most tasks i do on it but i am not put off so i will persist.
Hope you get your goal too!

---

### Post by rapattack1 on 2010-05-29
Sorry I gave up and took the vid capture card out. Too time consuming especially now i have to spend time on video editing. Ah well it is not like i am going to record many tv shows anyway:P

---

