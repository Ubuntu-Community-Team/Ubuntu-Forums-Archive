---
title: "Elgato EyeTV causing despair (not being recognized) on ibex"
date: 2008-12-18
forum: Multimedia Software
---

### Post by vapblack on 2008-12-18
I have [This DVB device]("http://www.elgato.com/elgato/na/mainmenu/products/hybrid/product1.en.html")

I'm using an x64 system with Ubuntu 8.10
I've searched the forum and come up with walkthroughts to getting it installed but I keep hitting a brick wall at the same point. Installing the em28xx driver.
> Before posting any error messages, reboot your machine here.

Now load the drivers:

$ sudo modprobe em28xx

I get the error 
> FATAL: Module em28xx not found.


I've followed the walkthrough about 3 times. and on 2 different pages to no avail. 
I'm still new to Ubuntu, so maybe I'm missing something very obvious. Please let me know
thanks for reading
peace.:confused:

---

### Post by vapblack on 2008-12-19
still trying to get this driver to work, to no avail
any help would be appreciated.

---

### Post by xc3RnbFO8P on 2008-12-19
In Terminal:
> lsusb
and
> dmesg
show the output.

---

### Post by vapblack on 2008-12-19
Issub gave me an error
bash: Isusb: command not found

that's dmesg


> [    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.492174] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[    0.492189] Brought up 2 CPUs
[    0.492192] Total of 2 processors activated (8016.62 BogoMIPS).
[    0.492280] CPU0 attaching sched-domain:
[    0.492283]  domain 0: span 0-1 level CPU
[    0.492286]   groups: 0 1
[    0.492290]   domain 1: span 0-1 level NODE
[    0.492292]    groups: 0-1
[    0.492297] CPU1 attaching sched-domain:
[    0.492299]  domain 0: span 0-1 level CPU
[    0.492301]   groups: 1 0
[    0.492304]   domain 1: span 0-1 level NODE
[    0.492306]    groups: 0-1
[    0.492400] net_namespace: 1552 bytes
[    0.492400] Booting paravirtualized kernel on bare hardware
[    0.492400] Time: 13:24:22  Date: 12/19/08
[    0.492425] NET: Registered protocol family 16
[    0.492450] node 0 link 0: io port [1000, ffff]
[    0.492450] TOM: 0000000040000000 aka 1024M
[    0.492450] node 0 link 0: mmio [a0000, bffff]
[    0.492450] node 0 link 0: mmio [40000000, efffffff]
[    0.492450] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.492450] node 0 link 0: mmio [f0000000, f02fffff]
[    0.492450] bus: [00,02] on node 0 link 0
[    0.492450] bus: 00 index 0 io port: [0, ffff]
[    0.492450] bus: 00 index 1 mmio: [a0000, bffff]
[    0.492450] bus: 00 index 2 mmio: [40000000, f3ffffff]
[    0.492450] bus: 00 index 3 mmio: [f4000000, fcffffffff]
[    0.492450] ACPI: bus type pci registered
[    0.492450] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.492450] PCI: MCFG area at f0000000 reserved in E820
[    0.496768] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.496771] PCI: Using configuration type 1 for base access
[    0.497529] ACPI: EC: Look up EC in DSDT
[    0.511048] ACPI: Interpreter enabled
[    0.511051] ACPI: (supports S0 S1 S3 S4 S5)
[    0.511071] ACPI: Using IOAPIC for interrupt routing
[    0.524282] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.524284] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524288] pci 0000:00:04.0: PME# disabled
[    0.524302] PCI: 0000:00:05.0 reg 10 32bit mmio: [fb000000, fbffffff]
[    0.524306] PCI: 0000:00:05.0 reg 14 32bit mmio: [e0000000, efffffff]
[    0.524313] PCI: 0000:00:05.0 reg 1c 64bit mmio: [fc000000, fcffffff]
[    0.524318] PCI: 0000:00:05.0 reg 30 32bit mmio: [0, 1ffff]
[    0.524524] PCI: 0000:00:0a.1 reg 20 io port: [4c00, 4c3f]
[    0.524529] PCI: 0000:00:0a.1 reg 24 io port: [4c40, 4c7f]
[    0.524548] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.524553] pci 0000:00:0a.1: PME# disabled
[    0.524609] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.524634] pci 0000:00:0b.0: supports D1
[    0.524636] pci 0000:00:0b.0: supports D2
[    0.524638] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524642] pci 0000:00:0b.0: PME# disabled
[    0.524663] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.524689] pci 0000:00:0b.1: supports D1
[    0.524691] pci 0000:00:0b.1: supports D2
[    0.524693] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524696] pci 0000:00:0b.1: PME# disabled
[    0.524728] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]
[    0.524763] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.524768] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.524772] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.524777] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.524781] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.524786] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]
[    0.524852] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe028000, fe02bfff]
[    0.524880] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.524884] pci 0000:00:10.1: PME# disabled
[    0.524909] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02c000, fe02cfff]
[    0.524914] PCI: 0000:00:14.0 reg 14 io port: [dc00, dc07]
[    0.524934] pci 0000:00:14.0: supports D1
[    0.524936] pci 0000:00:14.0: supports D2
[    0.524938] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524941] pci 0000:00:14.0: PME# disabled
[    0.525057] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
[    0.525060] PCI: bridge 0000:00:04.0 32bit mmio: [fdd00000, fddfffff]
[    0.525064] PCI: bridge 0000:00:04.0 64bit mmio pref: [fdc00000, fdcfffff]
[    0.525095] PCI: 0000:02:05.0 reg 10 32bit mmio: [fdbff000, fdbfffff]
[    0.525128] pci 0000:02:05.0: supports D1
[    0.525129] pci 0000:02:05.0: supports D2
[    0.525131] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot
[    0.525135] pci 0000:02:05.0: PME# disabled
[    0.525162] pci 0000:00:10.0: transparent bridge
[    0.525166] PCI: bridge 0000:00:10.0 io port: [c000, cfff]
[    0.525169] PCI: bridge 0000:00:10.0 32bit mmio: [fdb00000, fdbfffff]
[    0.525172] PCI: bridge 0000:00:10.0 32bit mmio pref: [fde00000, fdefffff]
[    0.525187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.525666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.632444] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    0.632582] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.632935] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.633206] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.633532] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.633883] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634236] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 *10 11 14 15)
[    0.634586] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634940] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.635290] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.636307] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 *7 9 10 11 14 15)
[    0.636660] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.637014] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.637365] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.637717] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.638070] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
[    0.638422] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.638773] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.639127] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.639540] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.639942] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.640353] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.640751] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.641149] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.641548] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.641945] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.642342] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.642740] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.643139] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.643538] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.643938] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.644349] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.644754] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.645157] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.645561] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.645964] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.646372] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.646775] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.647179] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.647289] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.647289] pnp: PnP ACPI init
[    0.647289] ACPI: bus type pnp registered
[    0.654239] pnp: PnP ACPI: found 11 devices
[    0.654239] ACPI: ACPI bus type pnp unregistered
[    0.654239] PCI: Using ACPI for IRQ routing
[    0.668041] NET: Registered protocol family 8
[    0.668043] NET: Registered protocol family 20
[    0.668075] NetLabel: Initializing
[    0.668077] NetLabel:  domain hash size = 128
[    0.668078] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.668094] NetLabel:  unlabeled traffic allowed by default
[    0.668162] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.668162] hpet0: 3 32-bit timers, 25000000 Hz
[    0.670462] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.670465]    actual entries 65586
[    0.670618] AppArmor: AppArmor Filesystem Enabled
[    0.670649] ACPI: RTC can wake from S4
[    0.672047] Switched to high resolution mode on CPU 0
[    0.672202] Switched to high resolution mode on CPU 1
[    0.684041] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.684045] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.684048] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.684050] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.684053] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.684056] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.684059] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.684062] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.684066] system 00:01: iomem range 0x38000000-0x3fffffff could not be reserved
[    0.684073] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.684076] system 00:02: ioport range 0x290-0x29f has been reserved
[    0.684088] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.684095] system 00:0a: iomem range 0xf0000-0xf3fff could not be reserved
[    0.684098] system 00:0a: iomem range 0xf4000-0xf7fff could not be reserved
[    0.684101] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.684104] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.684107] system 00:0a: iomem range 0xfefff000-0xfefff0ff could not be reserved
[    0.684110] system 00:0a: iomem range 0x37ef0000-0x37efffff could not be reserved
[    0.684113] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.684116] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.684119] system 00:0a: iomem range 0x100000-0x37eeffff could not be reserved
[    0.684122] system 00:0a: iomem range 0x37f00000-0x3fefffff could not be reserved
[    0.684125] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.684128] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.684131] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.684135] system 00:0a: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.684138] system 00:0a: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.684141] system 00:0a: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.689595] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.689598] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.689602] pci 0000:00:04.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.689605] pci 0000:00:04.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.689609] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.689612] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.689616] pci 0000:00:10.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.689619] pci 0000:00:10.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.689631] pci 0000:00:04.0: setting latency timer to 64
[    0.689636] pci 0000:00:10.0: setting latency timer to 64
[    0.689639] bus: 00 index 0 io port: [0, ffff]
[    0.689641] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.689643] bus: 01 index 0 io port: [b000, bfff]
[    0.689645] bus: 01 index 1 mmio: [fdd00000, fddfffff]
[    0.689647] bus: 01 index 2 mmio: [fdc00000, fdcfffff]
[    0.689650] bus: 01 index 3 mmio: [0, 0]
[    0.689652] bus: 02 index 0 io port: [c000, cfff]
[    0.689654] bus: 02 index 1 mmio: [fdb00000, fdbfffff]
[    0.689656] bus: 02 index 2 mmio: [fde00000, fdefffff]
[    0.689658] bus: 02 index 3 io port: [0, ffff]
[    0.689659] bus: 02 index 4 mmio: [0, ffffffffffffffff]
[    0.689675] NET: Registered protocol family 2
[    0.728105] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.728667] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.730092] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.730744] TCP: Hash tables configured (established 131072 bind 65536)
[    0.730748] TCP reno registered
[    0.740115] NET: Registered protocol family 1
[    0.740257] checking if image is initramfs... it is
[    1.475616] Freeing initrd memory: 8465k freed
[    1.482824] audit: initializing netlink socket (disabled)
[    1.482841] type=2000 audit(1229693062.481:1): initialized
[    1.488722] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.492242] VFS: Disk quotas dquot_6.5.1
[    1.492357] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.492487] msgmni has been set to 1747
[    1.492645] io scheduler noop registered
[    1.492648] io scheduler anticipatory registered
[    1.492650] io scheduler deadline registered
[    1.492813] io scheduler cfq registered (default)
[    1.492831] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.492875] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.492885] pci 0000:00:05.0: Boot video device
[    1.492907] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.524151] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.524161] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.524173] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.524345] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.524366] pcieport-driver 0000:00:04.0: found MSI capability
[    1.524396] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.524466] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.573206] hpet_resources: 0xfefff000 is busy
[    1.573325] Linux agpgart interface v0.103
[    1.573330] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.576201] brd: module loaded
[    1.576300] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.576459] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.576462] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.576638] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.592227] mice: PS/2 mouse device common for all mice
[    1.592418] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.592454] rtc0: alarms up to one year, y3k, hpet irqs
[    1.592515] cpuidle: using governor ladder
[    1.592518] cpuidle: using governor menu
[    1.593026] TCP cubic registered
[    1.593324] registered taskstats version 1
[    1.593470]   Magic number: 4:218:433
[    1.593648] rtc_cmos 00:05: setting system clock to 2008-12-19 13:24:23 UTC (1229693063)
[    1.593651] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.593653] EDD information not available.
[    1.593698] Freeing unused kernel memory: 536k freed
[    1.593997] Write protecting the kernel read-only data: 4348k
[    1.609479] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.788417] fuse init (API version 7.9)
[    1.886813] fan PNP0C0B:00: registered as cooling_device0
[    1.886822] ACPI: Fan [FAN] (on)
[    1.906707] processor

That's what I got...:guitar:

---

### Post by xc3RnbFO8P on 2008-12-19
Just copy paste **lsusb** into Terminal.

---

### Post by vapblack on 2008-12-19
> **Ringi said:**
> Just copy paste **lsusb** into Terminal.

> Bus 002 Device 006: ID 2040:6513 Hauppauge 
Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 004: ID 15a9:0004  
Bus 002 Device 002: ID 08e4:013e Pioneer Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

heh............

---

### Post by xc3RnbFO8P on 2008-12-19
Read this:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950")

---

### Post by vapblack on 2008-12-19
> Download the windows driver with something like:

wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)

Extract the file hcw85bda.sys from the zip into the current dir:

unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys


check

when I get to the next step, I'm a little lost. 

> run the extract_xc3028.pl script found in linux/Documentation/video4linux:

./extract_xc3028.pl

copy the generated file so it can be picked up by the Linux kernel:

cp xc3028-v27.fw /lib/firmware


Okay, where is this script, and directory? :s
thanks for your help so far.

---

### Post by xc3RnbFO8P on 2008-12-19
In Places> Search Files
**xc3028.pl**
choose File System
you should get something like this:
/usr/src/linux-headers-2.6.27-9-generic/Documentation/video4linux

In Terminal:
cd /usr/src/linux-headers-2.6.27-9-generic/Documentation/video4linux
return
then
> ./extract_xc3028.pl
> cp xc3028-v27.fw /lib/firmware

---

### Post by vapblack on 2008-12-19
> **Ringi said:**
> In Places> Search Files
**xc3028.pl**
choose File System
you should get something like this:
/usr/src/linux-headers-2.6.27-9-generic/Documentation/video4linux

In Terminal:
cd /usr/src/linux-headers-2.6.27-9-generic/Documentation/video4linux
return
then

Yeah, the file is in there. When I try to run it I get this error:
> prince@PlaFamily:/usr/src/linux-headers-2.6.27-9-generic/Documentation/video4linux$ ./extract_xc3028.pl
bash: ./extract_xc3028.pl: Permission denied
prince@PlaFamily:/usr/src/linux-headers-2.6.27-9-generic/Documentation/video4linux$ sudo ./extract_xc3028.pl
sudo: ./extract_xc3028.pl: command not found



---

### Post by xc3RnbFO8P on 2008-12-20
Here is the driver:
[http://ubuntuforums.org/attachment.php?attachmentid=82736&d=1219665844]("http://ubuntuforums.org/attachment.php?attachmentid=82736&d=1219665844")
then open Terminal:
> cd /home/your folder/Desktop
> tar xvjf xc3028-v27.fw.tar.bz2
> sudo cp xc3028-v27.fw /lib/firmware
restat the computer.

Then do dmesg , see if the driver is loaded.

---

### Post by vapblack on 2008-12-20
[    0.524520] PCI: 0000:00:0a.1 reg 20 io port: [4c00, 4c3f]
[    0.524526] PCI: 0000:00:0a.1 reg 24 io port: [4c40, 4c7f]
[    0.524544] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.524550] pci 0000:00:0a.1: PME# disabled
[    0.524605] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.524631] pci 0000:00:0b.0: supports D1
[    0.524633] pci 0000:00:0b.0: supports D2
[    0.524635] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524638] pci 0000:00:0b.0: PME# disabled
[    0.524660] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.524686] pci 0000:00:0b.1: supports D1
[    0.524688] pci 0000:00:0b.1: supports D2
[    0.524690] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524693] pci 0000:00:0b.1: PME# disabled
[    0.524725] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]
[    0.524761] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.524766] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.524770] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.524775] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.524779] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.524784] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]
[    0.524851] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe028000, fe02bfff]
[    0.524879] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.524883] pci 0000:00:10.1: PME# disabled
[    0.524908] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02c000, fe02cfff]
[    0.524913] PCI: 0000:00:14.0 reg 14 io port: [dc00, dc07]
[    0.524933] pci 0000:00:14.0: supports D1
[    0.524935] pci 0000:00:14.0: supports D2
[    0.524937] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.524940] pci 0000:00:14.0: PME# disabled
[    0.525057] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
[    0.525060] PCI: bridge 0000:00:04.0 32bit mmio: [fdd00000, fddfffff]
[    0.525064] PCI: bridge 0000:00:04.0 64bit mmio pref: [fdc00000, fdcfffff]
[    0.525095] PCI: 0000:02:05.0 reg 10 32bit mmio: [fdbff000, fdbfffff]
[    0.525128] pci 0000:02:05.0: supports D1
[    0.525129] pci 0000:02:05.0: supports D2
[    0.525131] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot
[    0.525135] pci 0000:02:05.0: PME# disabled
[    0.525163] pci 0000:00:10.0: transparent bridge
[    0.525166] PCI: bridge 0000:00:10.0 io port: [c000, cfff]
[    0.525169] PCI: bridge 0000:00:10.0 32bit mmio: [fdb00000, fdbfffff]
[    0.525172] PCI: bridge 0000:00:10.0 32bit mmio pref: [fde00000, fdefffff]
[    0.525188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.525667] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.632101] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 *11 14 15)
[    0.632427] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.632777] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.633124] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.633473] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.633821] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634170] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 *10 11 14 15)
[    0.634517] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.634867] ACPI: PCI Interrupt Link [LUBA] (IRQs *5 7 9 10 11 14 15)
[    0.635214] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.635563] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 *7 9 10 11 14 15)
[    0.635917] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.636281] ACPI: PCI Interrupt Link [LAZA] (IRQs *5 7 9 10 11 14 15)
[    0.636629] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.636976] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.637326] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 *7 9 10 11 14 15)
[    0.637673] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[    0.638020] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.638370] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.638776] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.639175] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.639572] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.639969] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.640377] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.640774] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.641172] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.641568] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.641965] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.642363] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.642761] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.643160] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.643557] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.643961] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.644373] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.644772] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.645170] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.645574] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.645976] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.646379] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.646488] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.646488] pnp: PnP ACPI init
[    0.646488] ACPI: bus type pnp registered
[    0.653426] pnp: PnP ACPI: found 11 devices
[    0.653426] ACPI: ACPI bus type pnp unregistered
[    0.653426] PCI: Using ACPI for IRQ routing
[    0.668041] NET: Registered protocol family 8
[    0.668043] NET: Registered protocol family 20
[    0.668074] NetLabel: Initializing
[    0.668076] NetLabel:  domain hash size = 128
[    0.668078] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.668094] NetLabel:  unlabeled traffic allowed by default
[    0.668161] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.668161] hpet0: 3 32-bit timers, 25000000 Hz
[    0.670467] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.670470]    actual entries 65586
[    0.670621] AppArmor: AppArmor Filesystem Enabled
[    0.670652] ACPI: RTC can wake from S4
[    0.672047] Switched to high resolution mode on CPU 0
[    0.672202] Switched to high resolution mode on CPU 1
[    0.684041] system 00:01: ioport range 0x4000-0x407f has been reserved
[    0.684044] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.684047] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.684050] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.684053] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.684056] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.684059] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.684061] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.684065] system 00:01: iomem range 0x38000000-0x3fffffff could not be reserved
[    0.684073] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.684076] system 00:02: ioport range 0x290-0x29f has been reserved
[    0.684088] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.684095] system 00:0a: iomem range 0xf0000-0xf3fff could not be reserved
[    0.684098] system 00:0a: iomem range 0xf4000-0xf7fff could not be reserved
[    0.684101] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.684104] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.684108] system 00:0a: iomem range 0xfefff000-0xfefff0ff could not be reserved
[    0.684110] system 00:0a: iomem range 0x37ef0000-0x37efffff could not be reserved
[    0.684114] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.684116] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.684119] system 00:0a: iomem range 0x100000-0x37eeffff could not be reserved
[    0.684122] system 00:0a: iomem range 0x37f00000-0x3fefffff could not be reserved
[    0.684125] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.684128] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.684132] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved
[    0.684135] system 00:0a: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.684138] system 00:0a: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.684141] system 00:0a: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.689605] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.689608] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.689612] pci 0000:00:04.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.689615] pci 0000:00:04.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.689619] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.689622] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.689626] pci 0000:00:10.0:   MEM window: 0xfdb00000-0xfdbfffff
[    0.689629] pci 0000:00:10.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.689641] pci 0000:00:04.0: setting latency timer to 64
[    0.689646] pci 0000:00:10.0: setting latency timer to 64
[    0.689649] bus: 00 index 0 io port: [0, ffff]
[    0.689651] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.689653] bus: 01 index 0 io port: [b000, bfff]
[    0.689655] bus: 01 index 1 mmio: [fdd00000, fddfffff]
[    0.689657] bus: 01 index 2 mmio: [fdc00000, fdcfffff]
[    0.689659] bus: 01 index 3 mmio: [0, 0]
[    0.689661] bus: 02 index 0 io port: [c000, cfff]
[    0.689663] bus: 02 index 1 mmio: [fdb00000, fdbfffff]
[    0.689665] bus: 02 index 2 mmio: [fde00000, fdefffff]
[    0.689667] bus: 02 index 3 io port: [0, ffff]
[    0.689669] bus: 02 index 4 mmio: [0, ffffffffffffffff]
[    0.689685] NET: Registered protocol family 2
[    0.728107] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.728670] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.730113] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.730768] TCP: Hash tables configured (established 131072 bind 65536)
[    0.730772] TCP reno registered
[    0.740117] NET: Registered protocol family 1
[    0.740258] checking if image is initramfs... it is
[    1.477192] Freeing initrd memory: 8465k freed
[    1.484367] audit: initializing netlink socket (disabled)
[    1.484383] type=2000 audit(1229780794.481:1): initialized
[    1.490249] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.493507] VFS: Disk quotas dquot_6.5.1
[    1.493631] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.493756] msgmni has been set to 1747
[    1.493909] io scheduler noop registered
[    1.493911] io scheduler anticipatory registered
[    1.493913] io scheduler deadline registered
[    1.494078] io scheduler cfq registered (default)
[    1.494096] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.494139] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.494149] pci 0000:00:05.0: Boot video device
[    1.494172] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.528033] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.528043] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.528054] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.528213] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.528234] pcieport-driver 0000:00:04.0: found MSI capability
[    1.528264] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.528335] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.577203] hpet_resources: 0xfefff000 is busy
[    1.577336] Linux agpgart interface v0.103
[    1.577342] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.580266] brd: module loaded
[    1.580367] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.580528] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.580531] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.580711] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.596325] mice: PS/2 mouse device common for all mice
[    1.596515] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.596551] rtc0: alarms up to one year, y3k, hpet irqs
[    1.596616] cpuidle: using governor ladder
[    1.596618] cpuidle: using governor menu
[    1.597136] TCP cubic registered
[    1.597435] registered taskstats version 1
[    1.597583]   Magic number: 4:155:787
[    1.597681] tty ptyq9: hash matches
[    1.597763] rtc_cmos 00:05: setting system clock to 2008-12-20 13:46:35 UTC (1229780795)
[    1.597766] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.597768] EDD information not available.
[    1.597813] Freeing unused kernel memory: 536k freed
[    1.598111] Write protecting the kernel read-only data: 4348k
[    1.638771] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.800786] fuse init (API version 7.9)
[    1.816027] fan PNP0C0B:00: registered as cooling_device0
[    1.816035] ACPI: Fan [FAN] (on)
[    1.852273] processor ACPI0007:00: registered as cooling_device1
[    1.852368] processor ACPI0007:01: registered as cooling_device2
[    1.855418] thermal LNXTHERM:01: registered as thermal_zone0
[    1.855899] ACPI: Thermal Zone [THRM] (40 C)
[    2.331104] usbcore: registered new interface driver usbfs
[    2.331142] usbcore: registered new interface driver hub
[    2.331191] usbcore: registered new device driver usb
[    2.333179] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.333758] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    2.333772] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 23 (level, low) -> IRQ 23
[    2.333787] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.333790] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.333855] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.333888] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xfe02f000
[    2.359065] No dock devices found.
[    2.387554] SCSI subsystem initialized
[    2.399632] usb usb1: configuration #1 chosen from 1 choice
[    2.399662] hub 1-0:1.0: USB hub found
[    2.399676] hub 1-0:1.0: 8 ports detected
[    2.426924] libata version 3.00 loaded.
[    2.609410] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    2.609426] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    2.609442] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    2.609445] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    2.609476] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    2.609513] ehci_hcd 0000:00:0b.1: debug port 1
[    2.609517] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    2.609542] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfe02e000
[    2.624035] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.624368] usb usb2: configuration #1 chosen from 1 choice
[    2.624405] hub 2-0:1.0: USB hub found
[    2.624416] hub 2-0:1.0: 8 ports detected
[    2.832491] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.833082] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    2.833096] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 21 (level, low) -> IRQ 21
[    2.833102] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.833145] nv_probe: set workaround bit for reversed mac addr
[    3.353322] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 13, addr 00:1a:92:6a:7c:f8
[    3.353327] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    3.356040] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[    3.356056] ohci1394 0000:02:05.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    3.377042] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    3.407816] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fdbff000-fdbff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
[    3.421034] pata_amd 0000:00:0d.0: version 0.3.10
[    3.421093] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.421220] scsi0 : pata_amd
[    3.421414] scsi1 : pata_amd
[    3.422351] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    3.422353] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    3.511229] usb 2-3: configuration #1 chosen from 1 choice
[    3.604304] ata1.00: ATAPI: TSSTcorp CDW/DVD TS-H492C, HP06, max UDMA/33
[    3.604319] ata1: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    3.636237] ata1.00: configured for UDMA/33
[    3.636283] ata2: port disabled. ignoring.
[    3.636338] isa bounce pool size: 16 pages
[    3.636895] scsi 0:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-H492C HP06 PQ: 0 ANSI: 5
[    3.638637] sata_nv 0000:00:0e.0: version 3.5
[    3.639209] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    3.639223] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    3.639227] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.639399] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.641943] scsi2 : sata_nv
[    3.643675] scsi3 : sata_nv
[    3.643954] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[    3.643957] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[    3.680036] usb 2-6: new high speed USB device using ehci_hcd and address 4
[    4.007634] usb 2-6: configuration #1 chosen from 1 choice
[    4.116055] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    4.120041] usb 2-7: new high speed USB device using ehci_hcd and address 5
[    4.124175] ata3.00: ATA-7: WDC WD1600JS-60NCB1, 10.02E02, max UDMA/100
[    4.124178] ata3.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.132185] ata3.00: configured for UDMA/100
[    4.256722] usb 2-7: configuration #1 chosen from 1 choice
[    4.368054] usb 2-8: new high speed USB device using ehci_hcd and address 6
[    4.462493] ata4: SATA link down (SStatus 0 SControl 310)
[    4.462635] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600JS-60N 10.0 PQ: 0 ANSI: 5
[    4.473681] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.473728] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    4.494681] Driver 'sr' needs updating - please use bus_type methods
[    4.498083] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    4.498090] Uniform CD-ROM driver Revision: 3.20
[    4.498216] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.504306] Driver 'sd' needs updating - please use bus_type methods
[    4.504472] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.504494] sd 2:0:0:0: [sda] Write Protect is off
[    4.504496] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.504531] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.504613] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.504631] sd 2:0:0:0: [sda] Write Protect is off
[    4.504633] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.504665] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.504669]  sda:<6>usb 2-8: configuration #1 chosen from 1 choice
[    4.510317]  sda1 sda2 <<6>usbcore: registered new interface driver libusual
[    4.520416] Initializing USB Mass Storage driver...
[    4.542736]  sda5 >
[    4.542963] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.689220] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001269744]
[    4.776442] PM: Starting manual resume from disk
[    4.776446] PM: Resume from partition 8:5
[    4.776448] PM: Checking hibernation image.
[    4.776612] PM: Resume from disk failed.
[    4.813027] usb 1-4: new low speed USB device using ohci_hcd and address 2
[    4.850403] kjournald starting.  Commit interval 5 seconds
[    4.850429] EXT3-fs: mounted filesystem with ordered data mode.
[    5.027631] usb 1-4: configuration #1 chosen from 1 choice
[    5.030797] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.030923] usb-storage: device found at 2
[    5.030926] usb-storage: waiting for device to settle before scanning
[    5.031013] scsi5 : SCSI emulation for USB Mass Storage devices
[    5.031091] usb-storage: device found at 5
[    5.031093] usb-storage: waiting for device to settle before scanning
[    5.031115] usbcore: registered new interface driver usb-storage
[    5.031119] USB Mass Storage support registered.
[   10.029291] usb-storage: device scan complete
[   10.029788] usb-storage: device scan complete
[   10.030854] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   10.031469] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   10.031719] scsi 4:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-112  1.16 PQ: 0 ANSI: 0
[   10.032098] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   10.032719] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.033928] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   10.034067] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   10.034788] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[   10.034847] sd 5:0:0:1: Attached scsi generic sg3 type 0
[   10.035648] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[   10.035708] sd 5:0:0:2: Attached scsi generic sg4 type 0
[   10.036403] sd 5:0:0:3: [sde] Attached SCSI removable disk
[   10.036460] sd 5:0:0:3: Attached scsi generic sg5 type 0
[   10.060715] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   10.060789] sr 4:0:0:0: Attached scsi CD-ROM sr1
[   10.060848] sr 4:0:0:0: Attached scsi generic sg6 type 5
[   10.402717] udevd version 124 started
[   10.825924] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.858649] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.921029] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   10.953060] ACPI: Power Button (FF) [PWRF]
[   10.953213] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   10.962623] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   10.962646] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   10.981052] ACPI: Power Button (CM) [PWRB]
[   11.169906] nvidia: module license 'NVIDIA' taints kernel.
[   11.570325] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   11.570332] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   11.570338] nvidia 0000:00:05.0: setting latency timer to 64
[   11.580589] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   11.879852] usbcore: registered new interface driver hiddev
[   11.886873] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input4
[   11.913328] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-4
[   11.913362] usbcore: registered new interface driver usbhid
[   11.913384] usbhid: v2.6:USB HID core driver
[   12.548155] phy0: Selected rate control algorithm 'pid'
[   12.694101] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.819163] Registered led device: rt73usb-phy0:radio
[   12.819207] Registered led device: rt73usb-phy0:assoc
[   12.819242] Registered led device: rt73usb-phy0:quality
[   12.819724] usbcore: registered new interface driver rt73usb
[   12.983518] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   12.983526] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   12.983551] HDA Intel 0000:00:10.1: setting latency timer to 64
[   13.016016] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   14.972778] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   14.972784] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   14.972788] Info fld=0x0
[   14.972790] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[   14.972795] end_request: I/O error, dev sr0, sector 985040
[   14.972801] Buffer I/O error on device sr0, logical block 123130
[   15.551373] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   15.551376] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   15.551380] Info fld=0x0
[   15.551381] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[   15.551384] end_request: I/O error, dev sr0, sector 985040
[   15.551387] Buffer I/O error on device sr0, logical block 123130
[   17.322763] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   17.322766] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   17.322769] Info fld=0x0
[   17.322771] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[   17.322774] end_request: I/O error, dev sr0, sector 985040
[   17.322777] Buffer I/O error on device sr0, logical block 123130
[   18.098419] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   18.098423] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[   18.098426] Info fld=0x0
[   18.098428] sr 0:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[   18.098431] end_request: I/O error, dev sr0, sector 985040
[   18.098433] Buffer I/O error on device sr0, logical block 123130
[   19.364135] lp: driver loaded but no devices found
[   19.618602] Adding 2618552k swap on /dev/sda5.  Priority:-1 extents:1 across:2618552k
[   20.194922] EXT3 FS on sda1, internal journal
[   21.441082] type=1505 audit(1229780815.242:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4438
[   21.617980] type=1505 audit(1229780815.418:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4443
[   21.618222] type=1505 audit(1229780815.418:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4443
[   21.677270] type=1505 audit(1229780815.478:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4447
[   21.844794] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.483358] ACPI: WMI: Mapper loaded
[   22.853889] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[   22.853961] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
[   22.853965] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[   22.853968] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x16
[   23.720863] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   26.167021] ppdev: user-space parallel port driver
[   28.500045] Clocksource tsc unstable (delta = -120961489 ns)
[   33.513868] Bluetooth: Core ver 2.13
[   33.518149] NET: Registered protocol family 31
[   33.518162] Bluetooth: HCI device and connection manager initialized
[   33.518170] Bluetooth: HCI socket layer initialized
[   33.590200] Bluetooth: L2CAP ver 2.11
[   33.590213] Bluetooth: L2CAP socket layer initialized
[   33.621132] Bluetooth: RFCOMM socket layer initialized
[   33.623426] Bluetooth: RFCOMM TTY layer initialized
[   33.623439] Bluetooth: RFCOMM ver 1.10
[   33.649848] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.649861] Bluetooth: BNEP filters: protocol multicast
[   33.744048] Bridge firewalling registered
[   33.744542] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   33.771328] Bluetooth: SCO (Voice Link) ver 0.6
[   33.771344] Bluetooth: SCO socket layer initialized
[   37.897702] firmware: requesting rt73.bin
[   38.514551] NET: Registered protocol family 17
[  228.452909] UDF-fs: No VRS found
[  228.518892] ISO 9660 Extensions: Microsoft Joliet Level 1
[  228.544526] ISOFS: changing to secondary root
[  245.371671] wlan0: authenticate with AP 00:0f:66:91:fe:4e
[  245.373709] wlan0: authenticated
[  245.373724] wlan0: associate with AP 00:0f:66:91:fe:4e
[  245.376060] wlan0: RX AssocResp from 00:0f:66:91:fe:4e (capab=0x401 status=0 aid=4)
[  245.376072] wlan0: associated
[  273.003555] NET: Registered protocol family 10
[  273.004657] lo: Disabled Privacy Extensions
[  283.133017] eth0: no IPv6 routers present
[  283.901029] wlan0: no IPv6 routers present

---

### Post by xc3RnbFO8P on 2008-12-20
Try to change USB port and do dmesg.
Just show the part with v4l, dvb, ?????.fw if you see it.

---

### Post by vapblack on 2008-12-20
I used the usb ports in the back and tried dmesg and still no luck. I put the output into a txt document and searched but did not find either v4l or dvb.

---

### Post by xc3RnbFO8P on 2008-12-20
now try **sudo modprobe em28xx**
then **dmesg**

---

### Post by vapblack on 2008-12-20
> **Ringi said:**
> now try **sudo modprobe em28xx**

then **dmesg**
FATAL: Module em28xx not found.

---

### Post by vapblack on 2008-12-21
Okay, the computer is recognizing it. Is there a special driver I need to access s-video? I'd like to connect my console to the computer and be able to record it.

---

### Post by xc3RnbFO8P on 2008-12-21
Search **em28xx** in Places> Search For Files (File system)

If nothing shows up , make a fresh install of Intrepid Ibex.

---

### Post by vapblack on 2008-12-22
> **Ringi said:**
> Search **em28xx** in Places> Search For Files (File system)

If nothing shows up , make a fresh install of Intrepid Ibex.

It's there, and I was able to install em28xx. It just returned a prompt without saying anything. Now the programs see it. I don't know what fixed it but thanks for the help, whichever step it was.


Now I want to view and record s-video. None of my programs are showing that option.

---

### Post by vapblack on 2008-12-22
Actually everything works. Good work dude. I went back and went over everything. Installed the driver again and dmesg and it was there. Then I found a little app called 'tvtime' and it's great. 
So..................thanks.

---

