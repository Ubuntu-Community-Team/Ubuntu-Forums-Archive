---
title: "Can't open firewire capture device"
date: 2011-01-22
forum: Multimedia Software
---

### Post by GROwen on 2011-01-22
Hi all,

I'm trying to view the output of a dv firewire capture  device (advc-100) fullscreen through vlc. I've read of people being able  to do this but a detailed explanation of how eludes me.

I'm running Ubuntu 10.10 and VLC 1.1.4

The error message I'm given after trying to open through 'media>open capture device>play' is;

> Your input can't be opened:
VLC is unable to open the MRL 'v4l2:///dev/ffc1/'. Check the log for details.(and I can't find the log)

I'm not even sure if I've got the  device name right so I ran lspci from the command line which gave the  following output (and I still can't work out what it is);

> [    0.008410] ... event mask:             000000000003ffff

[    0.014418] ACPI: Core revision 20100428

[    0.020016] ftrace: converting mcount calls to 0f 1f 44 00 00

[    0.020023] ftrace: allocating 21756 entries in 43 pages

[    0.024077] Enabling APIC mode:  Flat.  Using 1 I/O APICs

[    0.025151] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1

[    0.067791] CPU0: Intel(R) Pentium(R) D CPU 3.40GHz stepping 04

[    0.068000] Booting Node   0, Processors  #1

[    0.012000] Initializing CPU#1

[    0.156016] Brought up 2 CPUs

[    0.156021] Total of 2 processors activated (13600.88 BogoMIPS).

[    0.156734] devtmpfs: initialized

[    0.157295] regulator: core version 0.5

[    0.157335] Time:  0:37:43  Date: 01/22/11

[    0.157385] NET: Registered protocol family 16

[    0.157426] Trying to unpack rootfs image as initramfs...

[    0.157582] EISA bus registered

[    0.157595] ACPI: bus type pci registered

[    0.167086] PCI: PCI BIOS revision 2.10 entry at 0xfb080, last bus=1

[    0.167089] PCI: Using configuration type 1 for base access

[    0.167114] mtrr: your CPUs had inconsistent fixed MTRR settings

[    0.167116] mtrr: probably your BIOS does not setup all CPUs.

[    0.167118] mtrr: corrected configuration.

[    0.176143] bio: create slab <bio-0> at 0

[    0.177309] ACPI: EC: Look up EC in DSDT

[    0.182378] ACPI: Interpreter enabled

[    0.182382] ACPI: (supports S0 S1 S4 S5)

[    0.182414] ACPI: Using IOAPIC for interrupt routing

[    0.188046] ACPI: No dock devices found.

[    0.188052] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug

[    0.188196] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])

[    0.188461] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)

[    0.188466] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)

[    0.188470] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)

[    0.188473] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff] (ignored)

[    0.188476] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xfebfffff] (ignored)

[    0.188505] pci 0000:00:00.0: reg 10: [mem 0xe0000000-0xe7ffffff pref]

[    0.188877] pci 0000:00:01.0: supports D1

[    0.188926] pci 0000:00:0a.0: reg 10: [mem 0xeb000000-0xebffffff]

[    0.189015] pci 0000:00:0a.2: reg 10: [mem 0xec000000-0xecffffff]

[    0.189122] pci 0000:00:0b.0: reg 10: [mem 0xed000000-0xed000fff]

[    0.189174] pci 0000:00:0b.0: supports D1 D2

[    0.189176] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot

[    0.189181] pci 0000:00:0b.0: PME# disabled

[    0.189220] pci 0000:00:0f.0: reg 10: [io  0x9000-0x9007]

[    0.189229] pci 0000:00:0f.0: reg 14: [io  0x9400-0x9403]

[    0.189237] pci 0000:00:0f.0: reg 18: [io  0x9800-0x9807]

[    0.189244] pci 0000:00:0f.0: reg 1c: [io  0x9c00-0x9c03]

[    0.189252] pci 0000:00:0f.0: reg 20: [io  0xa000-0xa00f]

[    0.189260] pci 0000:00:0f.0: reg 24: [io  0xa400-0xa4ff]

[    0.189343] pci 0000:00:0f.1: reg 20: [io  0xa800-0xa80f]

[    0.189438] pci 0000:00:10.0: reg 20: [io  0xac00-0xac1f]

[    0.189469] pci 0000:00:10.0: supports D1 D2

[    0.189472] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.189477] pci 0000:00:10.0: PME# disabled

[    0.189546] pci 0000:00:10.1: reg 20: [io  0xb000-0xb01f]

[    0.189580] pci 0000:00:10.1: supports D1 D2

[    0.189583] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold

[    0.189588] pci 0000:00:10.1: PME# disabled

[    0.189641] pci 0000:00:10.2: reg 20: [io  0xb400-0xb41f]

[    0.189673] pci 0000:00:10.2: supports D1 D2

[    0.189675] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold

[    0.189680] pci 0000:00:10.2: PME# disabled

[    0.189734] pci 0000:00:10.3: reg 20: [io  0xb800-0xb81f]

[    0.189766] pci 0000:00:10.3: supports D1 D2

[    0.189768] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold

[    0.189773] pci 0000:00:10.3: PME# disabled

[    0.189807] pci 0000:00:10.4: reg 10: [mem 0xed001000-0xed0010ff]

[    0.189868] pci 0000:00:10.4: supports D1 D2

[    0.189871] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold

[    0.189877] pci 0000:00:10.4: PME# disabled

[    0.189957] HPET not enabled in BIOS. You might try hpet=force boot option

[    0.190017] pci 0000:00:11.5: reg 10: [io  0xbc00-0xbcff]

[    0.190071] pci 0000:00:11.5: supports D1 D2

[    0.190110] pci 0000:00:13.0: reg 10: [io  0xc000-0xc0ff]

[    0.190119] pci 0000:00:13.0: reg 14: [mem 0xed002000-0xed0020ff]

[    0.190166] pci 0000:00:13.0: supports D1 D2

[    0.190168] pci 0000:00:13.0: PME# supported from D1 D2 D3hot D3cold

[    0.190175] pci 0000:00:13.0: PME# disabled

[    0.190272] pci 0000:01:00.0: reg 10: [mem 0xe8000000-0xe8ffffff]

[    0.190281] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff pref]

[    0.190289] pci 0000:01:00.0: reg 18: [mem 0xe9000000-0xe9ffffff]

[    0.190312] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]

[    0.190382] pci 0000:00:01.0: PCI bridge to [bus 01-01]

[    0.190388] pci 0000:00:01.0:   bridge window [io  0xf000-0x0000] (disabled)

[    0.190393] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xeaffffff]

[    0.190399] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]

[    0.190409] pci_bus 0000:00: on NUMA node 0

[    0.190414] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    0.230532] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)

[    0.230743] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5

[    0.230966] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)

[    0.231179] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 *12)

[    0.231368] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.

[    0.231540] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.

[    0.231710] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.

[    0.231892] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.

[    0.232176] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0

[    0.232451] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0

[    0.232758] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0

[    0.233041] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0

[    0.233101] HEST: Table is not found!

[    0.233204] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none

[    0.233207] vgaarb: loaded

[    0.233420] SCSI subsystem initialized

[    0.233516] libata version 3.00 loaded.

[    0.233588] usbcore: registered new interface driver usbfs

[    0.233606] usbcore: registered new interface driver hub

[    0.233636] usbcore: registered new device driver usb

[    0.233800] ACPI: WMI: Mapper loaded

[    0.233803] PCI: Using ACPI for IRQ routing

[    0.233808] PCI: pci_cache_line_size set to 64 bytes

[    0.233917] reserve RAM buffer: 0000000000002000 - 000000000000ffff 

[    0.233920] reserve RAM buffer: 000000000009f800 - 000000000009ffff 

[    0.233923] reserve RAM buffer: 000000003fff0000 - 000000003fffffff 

[    0.234044] NetLabel: Initializing

[    0.234048] NetLabel:  domain hash size = 128

[    0.234049] NetLabel:  protocols = UNLABELED CIPSOv4

[    0.234068] NetLabel:  unlabeled traffic allowed by default

[    0.234128] Switching to clocksource tsc

[    0.246748] AppArmor: AppArmor Filesystem Enabled

[    0.246771] pnp: PnP ACPI init

[    0.246796] ACPI: bus type pnp registered

[    0.250743] pnp: PnP ACPI: found 12 devices

[    0.250746] ACPI: ACPI bus type pnp unregistered

[    0.250751] PnPBIOS: Disabled by ACPI PNP

[    0.250767] system 00:00: [mem 0x000cde00-0x000cffff] has been reserved

[    0.250771] system 00:00: [mem 0x000f0000-0x000f7fff] could not be reserved

[    0.250775] system 00:00: [mem 0x000f8000-0x000fbfff] could not be reserved

[    0.250778] system 00:00: [mem 0x000fc000-0x000fffff] could not be reserved

[    0.250782] system 00:00: [mem 0x3fff0000-0x3fffffff] could not be reserved

[    0.250786] system 00:00: [mem 0xffff0000-0xffffffff] has been reserved

[    0.250789] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved

[    0.250793] system 00:00: [mem 0x00100000-0x3ffeffff] could not be reserved

[    0.250797] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved

[    0.250800] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved

[    0.250804] system 00:00: [mem 0xfff80000-0xfffeffff] has been reserved

[    0.250812] system 00:02: [io  0x4000-0x407f] has been reserved

[    0.250816] system 00:02: [io  0x0500-0x050f] has been reserved

[    0.250823] system 00:03: [io  0x04d0-0x04d1] has been reserved

[    0.250827] system 00:03: [io  0x0294-0x0297] has been reserved

[    0.250830] system 00:03: [io  0x0880-0x088f] has been reserved

[    0.287519] pci 0000:01:00.0: BAR 6: assigned [mem 0xea000000-0xea01ffff pref]

[    0.287524] pci 0000:00:01.0: PCI bridge to [bus 01-01]

[    0.287526] pci 0000:00:01.0:   bridge window [io  disabled]

[    0.287533] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xeaffffff]

[    0.287538] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff pref]

[    0.287558] pci 0000:00:01.0: setting latency timer to 64

[    0.287563] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]

[    0.287566] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]

[    0.287570] pci_bus 0000:01: resource 1 [mem 0xe8000000-0xeaffffff]

[    0.287573] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff pref]

[    0.287622] NET: Registered protocol family 2

[    0.287718] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    0.288158] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[    0.289368] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[    0.289930] TCP: Hash tables configured (established 131072 bind 65536)

[    0.289934] TCP reno registered

[    0.289939] UDP hash table entries: 512 (order: 2, 16384 bytes)

[    0.289956] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)

[    0.290075] NET: Registered protocol family 1

[    0.290111] pci 0000:00:01.0: disabling DAC on VIA PCI bridge

[    0.290228] pci 0000:00:11.0: Bypassing VIA 8237 APIC De-Assert Message

[    0.290252] pci 0000:01:00.0: Boot video device

[    0.290257] PCI: CLS 32 bytes, default 64

[    0.290488] cpufreq-nforce2: No nForce2 chipset.

[    0.290528] Scanning for low memory corruption every 60 seconds

[    0.290751] audit: initializing netlink socket (disabled)

[    0.290764] type=2000 audit(1295656662.288:1): initialized

[    0.299710] highmem bounce pool size: 64 pages

[    0.299718] HugeTLB registered 4 MB page size, pre-allocated 0 pages

[    0.301624] VFS: Disk quotas dquot_6.5.2

[    0.301704] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[    0.302513] fuse init (API version 7.14)

[    0.302628] msgmni has been set to 1709

[    0.303035] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)

[    0.303039] io scheduler noop registered

[    0.303041] io scheduler deadline registered

[    0.303059] io scheduler cfq registered (default)

[    0.303237] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[    0.303266] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

[    0.303509] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0

[    0.303516] ACPI: Power Button [PWRB]

[    0.303589] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1

[    0.303594] ACPI: Power Button [PWRF]

[    0.303888] ACPI: acpi_idle registered with cpuidle

[    0.306291] ERST: Table is not found!

[    0.306428] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled

[    0.306549] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    0.306693] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

[    0.307106] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    0.307264] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

[    0.308780] brd: module loaded

[    0.309501] loop: module loaded

[    0.310120] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20

[    0.310124] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20

[    0.310131]   alloc irq_desc for 20 on node -1

[    0.310133]   alloc kstat_irqs on node -1

[    0.310147] pata_acpi 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20

[    0.310232] pata_acpi 0000:00:0f.0: PCI INT B disabled

[    0.310253] pata_acpi 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20

[    0.310282] pata_acpi 0000:00:0f.1: PCI INT A disabled

[    0.310703] Fixed MDIO Bus: probed

[    0.310748] PPP generic driver version 2.4.2

[    0.310806] tun: Universal TUN/TAP device driver, 1.6

[    0.310809] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>

[    0.310909] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

[    0.311269] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21

[    0.311272] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21

[    0.311276]   alloc irq_desc for 21 on node -1

[    0.311278]   alloc kstat_irqs on node -1

[    0.311284] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21

[    0.311302] ehci_hcd 0000:00:10.4: EHCI Host Controller

[    0.311351] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1

[    0.311425] ehci_hcd 0000:00:10.4: irq 21, io mem 0xed001000

[    0.311483] isapnp: Scanning for PnP cards...

[    0.360627] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00

[    0.360786] hub 1-0:1.0: USB hub found

[    0.360793] hub 1-0:1.0: 8 ports detected

[    0.360891] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver

[    0.360910] uhci_hcd: USB Universal Host Controller Interface driver

[    0.360946] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21

[    0.360954] uhci_hcd 0000:00:10.0: UHCI Host Controller

[    0.361007] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2

[    0.361030] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000ac00

[    0.361183] hub 2-0:1.0: USB hub found

[    0.361189] hub 2-0:1.0: 2 ports detected

[    0.361266] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21

[    0.361274] uhci_hcd 0000:00:10.1: UHCI Host Controller

[    0.361318] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3

[    0.361345] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b000

[    0.361496] hub 3-0:1.0: USB hub found

[    0.361502] hub 3-0:1.0: 2 ports detected

[    0.361581] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21

[    0.361589] uhci_hcd 0000:00:10.2: UHCI Host Controller

[    0.361630] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4

[    0.361657] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b400

[    0.361849] hub 4-0:1.0: USB hub found

[    0.361855] hub 4-0:1.0: 2 ports detected

[    0.361943] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21

[    0.361950] uhci_hcd 0000:00:10.3: UHCI Host Controller

[    0.361994] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5

[    0.362018] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000b800

[    0.362179] hub 5-0:1.0: USB hub found

[    0.362184] hub 5-0:1.0: 2 ports detected

[    0.362335] PNP: No PS/2 controller found. Probing ports directly.

[    0.478090] Freeing initrd memory: 10504k freed

[    0.624199] serio: i8042 KBD port at 0x60,0x64 irq 1

[    0.624280] mice: PS/2 mouse device common for all mice

[    0.624403] rtc_cmos 00:05: RTC can wake from S4

[    0.624449] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0

[    0.624501] rtc0: alarms up to one year, y3k, 242 bytes nvram

[    0.624629] device-mapper: uevent: version 1.0.3

[    0.654120] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]

[    0.654255] device-mapper: multipath: version 1.1.1 loaded

[    0.654259] device-mapper: multipath round-robin: version 1.0.0 loaded

[    0.654454] EISA: Probing bus 0 at eisa.0

[    0.654482] Cannot allocate resource for EISA slot 4

[    0.654501] EISA: Detected 0 cards.

[    0.654602] cpuidle: using governor ladder

[    0.654606] cpuidle: using governor menu

[    0.655069] TCP cubic registered

[    0.655237] NET: Registered protocol family 10

[    0.655750] lo: Disabled Privacy Extensions

[    0.656069] NET: Registered protocol family 17

[    0.656154] Using IPI No-Shortcut mode

[    0.656253] PM: Resume from disk failed.

[    0.656269] registered taskstats version 1

[    0.656566]   Magic number: 11:199:608

[    0.656701] rtc_cmos 00:05: setting system clock to 2011-01-22 00:37:43 UTC (1295656663)

[    0.656705] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    0.656707] EDD information not available.

[    0.667479] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2

[    0.668371] isapnp: No Plug & Play device found

[    0.668400] Freeing unused kernel memory: 688k freed

[    0.669257] Write protecting the kernel text: 4932k

[    0.669309] Write protecting the kernel read-only data: 1980k

[    0.691393] udev[75]: starting version 163

[    0.792497] pata_via 0000:00:0f.1: version 0.3.4

[    0.792518] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20

[    0.799639] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

[    0.806725] scsi0 : pata_via

[    0.827112] scsi1 : pata_via

[    0.827199] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xa800 irq 14

[    0.827204] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xa808 irq 15

[    0.827274] 8139cp 0000:00:13.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too

[    0.827308] sata_via 0000:00:0f.0: version 2.6

[    0.827336] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20

[    0.827394] sata_via 0000:00:0f.0: routed to hard irq line 11

[    0.828189] scsi2 : sata_via

[    0.828481] scsi3 : sata_via

[    0.828506] Floppy drive(s): fd0 is 1.44M

[    0.828534] ata3: SATA max UDMA/133 cmd 0x9000 ctl 0x9400 bmdma 0xa000 irq 20

[    0.828538] ata4: SATA max UDMA/133 cmd 0x9800 ctl 0x9c00 bmdma 0xa008 irq 20

[    0.845684] FDC 0 is a post-1991 82077

[    0.917828] usb 4-1: new low speed USB device using uhci_hcd and address 2

[    1.029951] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

[    1.123683] usbcore: registered new interface driver hiddev

[    1.138304] input: Riitek Micro Keyboard as /devices/pci0000:00/0000:00:10.2/usb4/4-1/4-1:1.0/input/input3

[     1.138478] generic-usb 0003:1997:0409.0001: input,hidraw0: USB HID  v1.11 Keyboard [Riitek Micro Keyboard] on usb-0000:00:10.2-1/input0

[    1.154370] ata2.00: ATAPI: PIONEER DVD-RW  DVR-111D, 1.29, max UDMA/66

[    1.159660] input: Riitek Micro Keyboard as /devices/pci0000:00/0000:00:10.2/usb4/4-1/4-1:1.1/input/input4

[     1.159871] generic-usb 0003:1997:0409.0002: input,hidraw1: USB HID  v1.11 Mouse [Riitek Micro Keyboard] on usb-0000:00:10.2-1/input1

[    1.159958] usbcore: registered new interface driver usbhid

[    1.159961] usbhid: USB HID core driver

[    1.172806] ata2.00: configured for UDMA/66

[    1.185584] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.29 PQ: 0 ANSI: 5

[    1.196843] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133

[    1.196859] ata3.00: 488397168 sectors, multi 16: LBA48 

[    1.204357] ata3.00: configured for UDMA/133

[    1.211123] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray

[    1.211126] Uniform CD-ROM driver Revision: 3.20

[    1.211261] sr 1:0:0:0: Attached scsi CD-ROM sr0

[    1.211342] sr 1:0:0:0: Attached scsi generic sg0 type 5

[    1.211564] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5

[    1.211803] sd 2:0:0:0: Attached scsi generic sg1 type 0

[    1.211817] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)

[    1.211924] sd 2:0:0:0: [sda] Write Protect is off

[    1.211928] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    1.211961] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.212254]  sda: sda1 sda2 < sda5 sda6 >

[    1.258261] sd 2:0:0:0: [sda] Attached SCSI disk

[    1.412017] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

[    1.616204] ata4.00: HPA unlocked: 1953523055 -> 1953525168, native 1953525168

[    1.616210] ata4.00: ATA-8: ST31000528AS, CC38, max UDMA/133

[    1.616213] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)

[    1.632422] ata4.00: configured for UDMA/133

[    1.632527] scsi 3:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5

[    1.632673] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)

[    1.632693] sd 3:0:0:0: Attached scsi generic sg2 type 0

[    1.632777] sd 3:0:0:0: [sdb] Write Protect is off

[    1.632780] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00

[    1.632812] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.632996]  sdb: sdb1 sdb2 sdb3

[    1.659620] sd 3:0:0:0: [sdb] Attached SCSI disk

[    1.668356]   alloc irq_desc for 19 on node -1

[    1.668361]   alloc kstat_irqs on node -1

[    1.668371] firewire_ohci 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[    1.669356] 8139too: 8139too Fast Ethernet driver 0.9.28

[    1.740539] firewire_ohci: isochronous cycle inconsistent

[    1.756527] firewire_ohci: Added fw-ohci device 0000:00:0b.0, OHCI v1.0, 8 IR + 8 IT contexts, quirks 0x0

[    1.756591]   alloc irq_desc for 18 on node -1

[    1.756596]   alloc kstat_irqs on node -1

[    1.756607] 8139too 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    1.757811] 8139too 0000:00:13.0: eth0: RealTek RTL8139 at 0xc000, 00:16:e6:53:04:29, IRQ 18

[    2.052327] EXT4-fs (sda1): INFO: recovery required on readonly filesystem

[    2.052334] EXT4-fs (sda1): write access will be enabled during recovery

[    2.248127] firewire_core: created device fw0: GUID 0000010000000050, S400

[    2.255919] firewire_core: created device fw1: GUID 00201101010018c9, S400

[    2.255925] firewire_core: phy config: card 0, new root=ffc1, gap_count=5

[    2.272010] firewire_core: IRM is not 1394a compliant, making local node (ffc0) root.

[    2.272014] firewire_core: phy config: card 0, new root=ffc0, gap_count=5

[    2.563105] EXT4-fs (sda1): recovery complete

[    2.563474] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

[   14.448712] udev[326]: starting version 163

[   14.558029] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   14.560387] Adding 1201148k swap on /dev/sda6.  Priority:-1 extents:1 across:1201148k 

[   14.590446] Linux video capture interface: v2.00

[   14.595520] parport_pc 00:0b: reported by Plug and Play ACPI

[   14.595573] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]

[   14.639690] Linux agpgart interface v0.103

[   14.642568] agpgart: Detected VIA VT3314 chipset

[   14.721207] lp: driver loaded but no devices found

[   14.748747] lp0: using parport0 (interrupt-driven).

[   14.755907] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xe0000000

[   14.777686] ppdev: user-space parallel port driver

[   14.777885] IR NEC protocol handler initialized

[    14.786347] type=1400 audit(1295656677.624:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient3" pid=530  comm="apparmor_parser"

[   14.787009] type=1400  audit(1295656677.624:3): apparmor="STATUS" operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=530  comm="apparmor_parser"

[   14.787368] type=1400  audit(1295656677.624:4): apparmor="STATUS" operation="profile_load"  name="/usr/lib/connman/scripts/dhclient-script" pid=530  comm="apparmor_parser"

[   14.807218] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded

[    14.814647] type=1400 audit(1295656677.652:5): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/ntpd" pid=569  comm="apparmor_parser"

[   14.820100] IR RC5(x) protocol handler initialized

[   14.824187] cx88[0]: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected], frontend(s): 1

[   14.824192] cx88[0]: TV tuner type 4, Radio tuner type -1

[   14.825862] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded

[   14.833950] IR RC6 protocol handler initialized

[   14.843002] IR JVC protocol handler initialized

[   14.868545] IR Sony protocol handler initialized

[   14.869348] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

[   14.902574] lirc_dev: IR Remote Control driver registered, major 249 

[   14.904473] IR LIRC bridge handler initialized

[   14.939007] nvidia: module license 'NVIDIA' taints kernel.

[   14.939013] Disabling lock debugging due to kernel taint

[   15.023755] cx88[0]/2: cx2388x 8802 Driver Manager

[   15.023778] cx88-mpeg driver manager 0000:00:0a.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[   15.023789] cx88[0]/2: found at 0000:00:0a.2, rev: 5, irq: 18, latency: 32, mmio: 0xec000000

[   15.023893] cx8800 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[   15.023901] cx88[0]/0: found at 0000:00:0a.0, rev: 5, irq: 18, latency: 32, mmio: 0xeb000000

[   15.024018] cx88[0]/0: registered device video0 [v4l2]

[   15.024056] cx88[0]/0: registered device vbi0

[   15.075285] cx88/2: cx2388x dvb driver version 0.0.8 loaded

[   15.075290] cx88/2: registering cx8802 driver, type: dvb access: shared

[   15.075294] cx88[0]/2: subsystem: 18ac:db10, board: DViCO FusionHDTV DVB-T Plus [card=21]

[   15.075298] cx88[0]/2: cx2388x based DVB/ATSC card

[   15.075300] cx8802_alloc_frontends() allocating 1 frontend(s)

[   15.076024] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22

[   15.076028] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22

[   15.076034]   alloc irq_desc for 22 on node -1

[   15.076037]   alloc kstat_irqs on node -1

[   15.076047] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22

[   15.076213] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64

[   15.082621] DVB: registering new adapter (cx88[0])

[   15.082627] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...

[   16.097030]   alloc irq_desc for 16 on node -1

[   16.097035]   alloc kstat_irqs on node -1

[   16.097045] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[   16.097057] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem

[   16.097332] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010

[   16.135305] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)

[   16.611646] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)

[   16.689323] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)

[   16.720705] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)

[    16.953076] type=1400 audit(1295656679.792:6): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient3" pid=871  comm="apparmor_parser"

[   16.953742] type=1400  audit(1295656679.792:7): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=871  comm="apparmor_parser"

[   16.954103] type=1400  audit(1295656679.792:8): apparmor="STATUS" operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=871  comm="apparmor_parser"

[   16.954506] type=1400  audit(1295656679.792:9): apparmor="STATUS" operation="profile_load"  name="/usr/lib/cups/backend/cups-pdf" pid=873 comm="apparmor_parser"

[    16.955346] type=1400 audit(1295656679.792:10): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/cupsd" pid=873  comm="apparmor_parser"

[   16.957335] type=1400  audit(1295656679.796:11): apparmor="STATUS" operation="profile_load"  name="/usr/share/gdm/guest-session/Xsession" pid=870  comm="apparmor_parser"

[   17.039198] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

[   17.561523] agpgart-via 0000:00:00.0: AGP 3.5 bridge

[   17.561550] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode

[   17.561668] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode

[   20.874716] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0

[   21.676405] EXT4-fs (sda5): re-mounted. Opts: commit=0

[   21.884435] EXT4-fs (sdb1): re-mounted. Opts: commit=0

[   21.934572] EXT4-fs (sdb2): re-mounted. Opts: commit=0

[   21.979863] EXT4-fs (sdb3): re-mounted. Opts: commit=0

[   27.984008] eth0: no IPv6 routers present
I know the device is working because I can view the output through Kino's capture mode.

I hope someone can help me out with this, it would be greatly appreciated.

Thanks,

---

### Post by GROwen on 2011-01-24
It looks like it might not be as straight forward as I thought.

Is anyone able to offer an alternative to VLC to view a firewire feed at fullscreen (without any lag)?

What I'd ideally like to be able to do is use my current setup to play video games on a computer monitor.

Thanks in advance for any help any one can provide me with this.

---

