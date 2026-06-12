---
title: "Wireless card problem - wlan0 has disappeared"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by rudeyallan on 2009-07-30
Ok well I'm quite new to ubuntu and I thought I'd install it on my new ASUS Eee PC 1000HE. Installation was fine and I upgraded to an eee kernel.

I then installed aircrack-ng. However, I keep getting an error, so I searched around and it seems I needed to put my wireless card into monitor mode. So I search around again and found a topic here saying to:

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
```then I tried aireplay (I didn't realise I forgot to up it :() and my netbook froze. Now wlan0 has disappeared and I don't even have wireless on my Windows XP partition as it has disappeared from there as well. I would really appreciate some help as I bought it yesterday and I'm going on holiday tomorrow!

Thanks in advance

---

### Post by jamest09 on 2009-07-30
Post the output of dmesg please

---

### Post by rudeyallan on 2009-07-30
This is what I get
```

[    0.616160]   domain 1: span 0-1 level CPU
[    0.616164]    groups: 0-1
[    0.616343] net_namespace: 840 bytes
[    0.616343] Booting paravirtualized kernel on bare hardware
[    0.616584] Time: 11:13:22  Date: 07/30/09
[    0.616637] NET: Registered protocol family 16
[    0.616681] ACPI: bus type pci registered
[    0.616681] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.616681] PCI: Not using MMCONFIG.
[    0.616681] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.616681] PCI: Using configuration type 1 for base access
[    0.622185] ACPI: EC: Look up EC in DSDT
[    0.639287] ACPI: Interpreter enabled
[    0.639296] ACPI: (supports S0 S1 S3 S4 S5)
[    0.639339] ACPI: Using IOAPIC for interrupt routing
[    0.639500] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.644825] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.644832] PCI: Using MMCONFIG for extended config space
[    0.660449] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.660449] ACPI: EC: driver started in poll mode
[    0.660478] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.660478] PCI: 0000:00:02.0 reg 10 32bit mmio: [f7f00000, f7f7ffff]
[    0.660478] PCI: 0000:00:02.0 reg 14 io port: [dc00, dc07]
[    0.660478] PCI: 0000:00:02.0 reg 18 32bit mmio: [d0000000, dfffffff]
[    0.660478] PCI: 0000:00:02.0 reg 1c 32bit mmio: [f7ec0000, f7efffff]
[    0.660478] PCI: 0000:00:02.1 reg 10 32bit mmio: [f7f80000, f7ffffff]
[    0.660478] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f7eb8000, f7ebbfff]
[    0.660478] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.660478] pci 0000:00:1b.0: PME# disabled
[    0.660483] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.660492] pci 0000:00:1c.0: PME# disabled
[    0.664046] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.664055] pci 0000:00:1c.1: PME# disabled
[    0.664138] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.664147] pci 0000:00:1c.3: PME# disabled
[    0.664207] PCI: 0000:00:1d.0 reg 20 io port: [d400, d41f]
[    0.664283] PCI: 0000:00:1d.1 reg 20 io port: [d480, d49f]
[    0.664358] PCI: 0000:00:1d.2 reg 20 io port: [d800, d81f]
[    0.664433] PCI: 0000:00:1d.3 reg 20 io port: [d880, d89f]
[    0.664512] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f7eb7c00, f7eb7fff]
[    0.664579] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.664588] pci 0000:00:1d.7: PME# disabled
[    0.664758] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.664766] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.664822] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[    0.664833] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[    0.664845] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[    0.664856] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[    0.664867] PCI: 0000:00:1f.2 reg 20 io port: [ffa0, ffaf]
[    0.664905] pci 0000:00:1f.2: PME# supported from D3hot
[    0.664913] pci 0000:00:1f.2: PME# disabled
[    0.665076] PCI: 0000:03:00.0 reg 10 64bit mmio: [fbfc0000, fbffffff]
[    0.665090] PCI: 0000:03:00.0 reg 18 io port: [ec00, ec7f]
[    0.665165] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.665174] pci 0000:03:00.0: PME# disabled
[    0.665234] PCI: bridge 0000:00:1c.1 io port: [e000, efff]
[    0.665242] PCI: bridge 0000:00:1c.1 32bit mmio: [fbf00000, fbffffff]
[    0.665323] PCI: bridge 0000:00:1c.3 32bit mmio: [f8000000, fbefffff]
[    0.665335] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f0000000, f6ffffff]
[    0.665405] pci 0000:00:1e.0: transparent bridge
[    0.665451] bus 00 -> node 0
[    0.665469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.666092] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.666362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.700383] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.700801] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.701212] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.701621] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.702031] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.702443] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.702855] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.704055] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.704238] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.704238] pnp: PnP ACPI init
[    0.704238] ACPI: bus type pnp registered
[    0.709165] pnp: PnP ACPI: found 13 devices
[    0.709171] ACPI: ACPI bus type pnp unregistered
[    0.712128] PCI: Using ACPI for IRQ routing
[    0.720055] NET: Registered protocol family 8
[    0.720061] NET: Registered protocol family 20
[    0.720097] NetLabel: Initializing
[    0.720097] NetLabel:  domain hash size = 128
[    0.720097] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.720104] NetLabel:  unlabeled traffic allowed by default
[    0.720118] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.720127] hpet0: 3 64-bit timers, 14318180 Hz
[    0.722276] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.722281]    actual entries 65620
[    0.722446] AppArmor: AppArmor Filesystem Enabled
[    0.722484] ACPI: RTC can wake from S4
[    0.724055] Switched to high resolution mode on CPU 0
[    0.724367] Switched to high resolution mode on CPU 1
[    0.728065] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.728089] system 00:08: ioport range 0x25c-0x25f has been reserved
[    0.728096] system 00:08: ioport range 0x380-0x383 has been reserved
[    0.728102] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.728108] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.728115] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.728121] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.728129] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved
[    0.728136] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.728143] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.728150] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.728157] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.728164] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.728179] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.728186] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.728200] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.728215] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.728221] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.728228] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.728235] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.764392] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.764400] pci 0000:00:1c.0:   IO window: disabled
[    0.764410] pci 0000:00:1c.0:   MEM window: disabled
[    0.764418] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.764430] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.764437] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.764447] pci 0000:00:1c.1:   MEM window: 0xfbf00000-0xfbffffff
[    0.764455] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.764466] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:01
[    0.764471] pci 0000:00:1c.3:   IO window: disabled
[    0.764481] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xfbefffff
[    0.764490] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff
[    0.764502] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.764507] pci 0000:00:1e.0:   IO window: disabled
[    0.764516] pci 0000:00:1e.0:   MEM window: disabled
[    0.764523] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.764555] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.764566] pci 0000:00:1c.0: setting latency timer to 64
[    0.764582] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.764591] pci 0000:00:1c.1: setting latency timer to 64
[    0.764606] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.764615] pci 0000:00:1c.3: setting latency timer to 64
[    0.764628] pci 0000:00:1e.0: setting latency timer to 64
[    0.764635] bus: 00 index 0 io port: [0, ffff]
[    0.764640] bus: 00 index 1 mmio: [0, ffffffff]
[    0.764645] bus: 04 index 0 mmio: [0, 0]
[    0.764649] bus: 04 index 1 mmio: [0, 0]
[    0.764653] bus: 04 index 2 mmio: [0, 0]
[    0.764657] bus: 04 index 3 mmio: [0, 0]
[    0.764661] bus: 03 index 0 io port: [e000, efff]
[    0.764666] bus: 03 index 1 mmio: [fbf00000, fbffffff]
[    0.764671] bus: 03 index 2 mmio: [0, 0]
[    0.764675] bus: 03 index 3 mmio: [0, 0]
[    0.764679] bus: 01 index 0 mmio: [0, 0]
[    0.764684] bus: 01 index 1 mmio: [f8000000, fbefffff]
[    0.764689] bus: 01 index 2 mmio: [f0000000, f6ffffff]
[    0.764693] bus: 01 index 3 mmio: [0, 0]
[    0.764698] bus: 05 index 0 mmio: [0, 0]
[    0.764702] bus: 05 index 1 mmio: [0, 0]
[    0.764706] bus: 05 index 2 mmio: [0, 0]
[    0.764710] bus: 05 index 3 io port: [0, ffff]
[    0.764715] bus: 05 index 4 mmio: [0, ffffffff]
[    0.764736] NET: Registered protocol family 2
[    0.776126] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.776653] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.777509] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.777958] TCP: Hash tables configured (established 131072 bind 65536)
[    0.777965] TCP reno registered
[    0.784185] NET: Registered protocol family 1
[    0.784392] checking if image is initramfs... it is
[    1.730165] Freeing initrd memory: 7655k freed
[    1.732734] audit: initializing netlink socket (disabled)
[    1.732764] type=2000 audit(1248952402.732:1): initialized
[    1.742392] highmem bounce pool size: 64 pages
[    1.742409] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.748710] VFS: Disk quotas dquot_6.5.1
[    1.748926] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.749184] msgmni has been set to 1762
[    1.749488] io scheduler noop registered
[    1.749494] io scheduler anticipatory registered
[    1.749499] io scheduler deadline registered
[    1.749531] io scheduler cfq registered (default)
[    1.749560] pci 0000:00:02.0: Boot video device
[    1.749909] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.749969] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.750032] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.750139] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.750251] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.750465] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.750523] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.750581] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.750679] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.750796] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.751000] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.751058] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.751115] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.751218] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.751330] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.855055] hpet_resources: 0xfed00000 is busy
[    1.855230] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.861023] brd: module loaded
[    1.861200] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.861504] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.894563] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.894577] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.896334] mice: PS/2 mouse device common for all mice
[    1.896702] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.896745] rtc0: alarms up to one month, hpet irqs
[    1.896843] cpuidle: using governor ladder
[    1.896851] cpuidle: using governor menu
[    1.898019] TCP cubic registered
[    1.898078] Using IPI No-Shortcut mode
[    1.898652] registered taskstats version 1
[    1.898866]   Magic number: 1:594:227
[    1.898914] tty ttyre: hash matches
[    1.898998] acpi PNP0200:00: hash matches
[    1.899049] rtc_cmos 00:03: setting system clock to 2009-07-30 11:13:23 UTC (1248952403)
[    1.899056] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.899060] EDD information not available.
[    1.899336] Freeing unused kernel memory: 332k freed
[    1.899473] Write protecting the kernel text: 2552k
[    1.899549] Write protecting the kernel read-only data: 928k
[    1.920976] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.211799] fuse init (API version 7.9)
[    2.353060] ACPI: SSDT 3F7AE180, 01FA (r1  PmRef  Cpu0Ist     3000 INTL 20060113)
[    2.354019] ACPI: SSDT 3F7AE410, 0724 (r1  PmRef  Cpu0Cst     3001 INTL 20060113)
[    2.355143] Monitor-Mwait will be used to enter C-1 state
[    2.355151] Monitor-Mwait will be used to enter C-2 state
[    2.368052] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.372062] processor ACPI0007:00: registered as cooling_device0
[    2.372075] ACPI: Processor [P001] (supports 8 throttling states)
[    2.372912] ACPI: SSDT 3F7AE0B0, 00CC (r1  PmRef  Cpu1Ist     3000 INTL 20060113)
[    2.373804] ACPI: SSDT 3F7AE380, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20060113)
[    2.376007] Marking TSC unstable due to TSC halts in idle
[    2.536403] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    2.536566] processor ACPI0007:01: registered as cooling_device1
[    2.536578] ACPI: Processor [P002] (supports 8 throttling states)
[    2.543515] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    2.562501] thermal LNXTHERM:01: registered as thermal_zone0
[    2.580330] ACPI: Thermal Zone [TZ00] (52 C)
[    2.882438] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.882465] ATL1E 0000:03:00.0: setting latency timer to 64
[    2.895733] usbcore: registered new interface driver usbfs
[    2.895793] usbcore: registered new interface driver hub
[    2.896524] usbcore: registered new device driver usb
[    2.900482] No dock devices found.
[    2.915894] USB Universal Host Controller Interface driver v3.0
[    2.937981] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.938009] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.938019] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.938118] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.942056] ehci_hcd 0000:00:1d.7: debug port 1
[    2.942070] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.942100] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    2.957166] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.957513] usb usb1: configuration #1 chosen from 1 choice
[    2.957600] hub 1-0:1.0: USB hub found
[    2.957622] hub 1-0:1.0: 8 ports detected
[    2.970710] SCSI subsystem initialized
[    3.075858] libata version 3.00 loaded.
[    3.165643] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.165665] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.165676] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.165757] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.165806] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    3.166182] usb usb2: configuration #1 chosen from 1 choice
[    3.166283] hub 2-0:1.0: USB hub found
[    3.166306] hub 2-0:1.0: 2 ports detected
[    3.269671] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.269694] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.269705] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.269796] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.269862] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    3.270213] usb usb3: configuration #1 chosen from 1 choice
[    3.270315] hub 3-0:1.0: USB hub found
[    3.270339] hub 3-0:1.0: 2 ports detected
[    3.374022] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.374045] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.374056] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.374157] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.374222] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    3.374639] usb usb4: configuration #1 chosen from 1 choice
[    3.374737] hub 4-0:1.0: USB hub found
[    3.374760] hub 4-0:1.0: 2 ports detected
[    3.389088] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    3.477643] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.477667] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.477678] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.477768] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.477833] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    3.478212] usb usb5: configuration #1 chosen from 1 choice
[    3.478311] hub 5-0:1.0: USB hub found
[    3.478339] hub 5-0:1.0: 2 ports detected
[    3.566109] usb 1-8: configuration #1 chosen from 1 choice
[    3.685704] ata_piix 0000:00:1f.2: version 2.12
[    3.685740] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.685753] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.685847] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.686029] scsi0 : ata_piix
[    3.686315] scsi1 : ata_piix
[    3.691685] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.691696] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.800090] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    3.852848] ata1.00: ATA-8: ST9160310AS, 0303, max UDMA/133
[    3.852860] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.868823] ata1.00: configured for UDMA/133
[    3.977661] usb 5-1: configuration #1 chosen from 1 choice
[    4.024434] scsi 0:0:0:0: Direct-Access     ATA      ST9160310AS      0303 PQ: 0 ANSI: 5
[    4.054255] Driver 'sd' needs updating - please use bus_type methods
[    4.054513] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.054573] sd 0:0:0:0: [sda] Write Protect is off
[    4.054582] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.054681] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.054887] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.054943] sd 0:0:0:0: [sda] Write Protect is off
[    4.054951] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.055054] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.055068]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    4.416543] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.427969] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.272573] PM: Starting manual resume from disk
[    5.272583] PM: Resume from partition 8:6
[    5.272587] PM: Checking hibernation image.
[    5.273689] PM: Resume from disk failed.
[    5.410010] kjournald starting.  Commit interval 5 seconds
[    5.410034] EXT3-fs: mounted filesystem with ordered data mode.
[   12.360827] udev: starting version 141
[   12.771896] Linux agpgart interface v0.103
[   12.886814] ACPI: AC Adapter [AC0] (on-line)
[   13.085985] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.100115] ACPI: Power Button (FF) [PWRF]
[   13.100401] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   13.107959] ACPI: Lid Switch [LID]
[   13.108227] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   13.134981] ACPI: Sleep Button (CM) [SLPB]
[   13.135467] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   13.140488] intel_rng: FWH not detected
[   13.157637] ACPI: Power Button (CM) [PWRB]
[   13.550495] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.755485] ACPI: Battery Slot [BAT0] (battery present)
[   14.423643] Bluetooth: Core ver 2.13
[   14.426391] NET: Registered protocol family 31
[   14.426401] Bluetooth: HCI device and connection manager initialized
[   14.426410] Bluetooth: HCI socket layer initialized
[   14.538444] asus_eee module requires i2c-i801 module at load time if you like to access pll via proc too
[   14.538491] asus_eee version 0.3 init sucessfully
[   14.538502] sys_init_module: 'asus_eee'->init suspiciously returned 1, it should follow 0/-E convention
[   14.538507] sys_init_module: loading module anyway...
[   14.538517] Pid: 2367, comm: modprobe Not tainted 2.6.27-8-eeepc #1
[   14.538524]  [<c03765c6>] ? printk+0x1d/0x1f
[   14.538551]  [<c015bde7>] sys_init_module+0x1a7/0x1b0
[   14.538572]  [<c0103f23>] sysenter_do_call+0x12/0x2f
[   14.538584]  [<c0370000>] ? sbs_exit+0x35/0x4f
[   14.538596]  =======================
[   14.588779] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input7
[   14.597616] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.614381] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   14.614627] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   14.640086] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.640651] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   14.645068] usbcore: registered new interface driver btusb
[   14.723478] iTCO_vendor_support: vendor-support=0
[   14.748703] eeepc: Eee PC Hotkey Driver
[   14.750744] eeepc: Hotkey init flags 0x41
[   14.751020] eeepc: Get control methods supported: 0x301713
[   14.751970] input: Asus EeePC extra buttons as /devices/virtual/input/input8
[   14.758975] Linux video capture interface: v2.00
[   14.784391] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.846491] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   14.863720] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input9
[   14.873537] usbcore: registered new interface driver uvcvideo
[   14.873615] USB Video Class driver (v0.1.0)
[   15.051754] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.051801] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.800594] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input10
[   15.814530] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   15.814779] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.350614] lp: driver loaded but no devices found
[   16.564936] Adding 2980016k swap on /dev/sda6.  Priority:-1 extents:1 across:2980016k
[   17.139948] EXT3 FS on sda5, internal journal
[   18.740062] type=1505 audit(1248948820.337:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4076
[   18.848410] type=1505 audit(1248948820.445:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=4080
[   18.848696] type=1505 audit(1248948820.445:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=4080
[   18.848828] type=1505 audit(1248948820.445:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=4080
[   18.848941] type=1505 audit(1248948820.445:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=4080
[   19.154492] type=1505 audit(1248948820.753:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4085
[   19.154921] type=1505 audit(1248948820.753:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4085
[   19.217454] type=1505 audit(1248948820.817:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=4089
[   20.409930] ACPI: WMI: Mapper loaded
[   26.345537] Bluetooth: L2CAP ver 2.11
[   26.345548] Bluetooth: L2CAP socket layer initialized
[   26.361839] Bluetooth: SCO (Voice Link) ver 0.6
[   26.361850] Bluetooth: SCO socket layer initialized
[   26.383721] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.383734] Bluetooth: BNEP filters: protocol multicast
[   26.401654] Bluetooth: RFCOMM socket layer initialized
[   26.403282] Bluetooth: RFCOMM TTY layer initialized
[   26.403299] Bluetooth: RFCOMM ver 1.10
[   26.445480] Bridge firewalling registered
[   26.447120] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   27.937364] ppdev: user-space parallel port driver
[   28.407782] NET: Registered protocol family 10
[   28.409321] lo: Disabled Privacy Extensions
[   29.271991] [drm] Initialized drm 1.1.0 20060810
[   29.321563] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.321581] pci 0000:00:02.0: setting latency timer to 64
[   29.321998] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   29.366874] [drm:i915_getparam] *ERROR* Unknown parameter 5
[   30.771934] [drm:i915_getparam] *ERROR* Unknown parameter 5
[   31.406270] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  212.417682] [drm:i915_getparam] *ERROR* Unknown parameter 5
[  422.232135] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  422.232919] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  422.493141] NET: Registered protocol family 17
[  432.980038] eth0: no IPv6 routers present
[ 1235.625143] [drm:i915_getparam] *ERROR* Unknown parameter 5
[ 1536.008112] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 1536.280694] usb 1-2: configuration #1 chosen from 1 choice
[ 1536.701129] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[ 1536.701155] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 1536.701329] usbcore: registered new interface driver rt2500usb
[ 1537.000683] phy1: Selected rate control algorithm 'pid'
[ 1537.085589] Registered led device: rt73usb-phy1:radio
[ 1537.085687] Registered led device: rt73usb-phy1:assoc
[ 1537.085784] Registered led device: rt73usb-phy1:quality
[ 1537.086836] usbcore: registered new interface driver rt73usb
[ 1537.258822] udev: renamed network interface wlan0 to wlan1
[ 1541.756980] firmware: requesting rt73.bin
[ 1541.938293] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1548.551644] wlan1: authenticate with AP 00:1f:9f:ea:e5:2d
[ 1548.553912] wlan1: authenticated
[ 1548.553935] wlan1: associate with AP 00:1f:9f:ea:e5:2d
[ 1548.556929] wlan1: RX AssocResp from 00:1f:9f:ea:e5:2d (capab=0x411 status=0 aid=4)
[ 1548.556946] wlan1: associated
[ 1548.559188] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1558.656051] wlan1: no IPv6 routers present
[ 1589.132547] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Down
[ 1645.256078] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 1645.776078] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[ 1645.776129] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.EBTS] (Node f74160f0), AE_TIME
[ 1645.776387] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.UBCS] (Node f7419f90), AE_TIME
[ 1645.776634] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.CBST] (Node f741a120), AE_TIME
[ 1645.776874] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.BAT0._BST] (Node f741a060), AE_TIME
[ 1645.777161] ACPI Exception (battery-0360): AE_TIME, Evaluating _BST [20080609]
[ 1744.663408] hpet1: lost 1 rtc interrupts
[ 3173.070282] usb 1-2: USB disconnect, address 4
[ 3173.073340] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -19.
[ 3173.073369] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -19.
[ 3173.073391] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3028 with error -19.
[ 3173.073411] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -19.
[ 3173.073432] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0c failed for offset 0x0000 with error -19.
[ 3173.073513] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 3173.074655] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 3173.076956] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[ 3173.077099] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
```

At the moment I'm using a usb wireless adapter (I think it takes wlan1) instead of the internal one which has stopped working

---

