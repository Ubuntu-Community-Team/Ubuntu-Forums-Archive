---
title: "DWA-125 Wifi issue in 10.04 LTS"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by Terible1biker57 on 2010-04-29
D link DWA-125 Trouble please help

lo no Wireless extensions

eth0 no Wireless extensions

---

### Post by BrianIsNew on 2010-04-29
Try running **sudo ifconfig wlan0 up**
This tells your OS to turn your default wireless on.

---

### Post by Terible1biker57 on 2010-04-29
I get wlan0: ERROR while getting interface flags: No such device

---

### Post by BrianIsNew on 2010-04-29
Can we just verify what you have?
Post the output of **lspci**

---

### Post by chili555 on 2010-04-29
Please open a terminal and do:```
lsusb
lsmod | grep -e rt3 -e rt3
```Post the result.

---

### Post by Terible1biker57 on 2010-04-29
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 002 Device 004: ID 07d1:3c16 D-Link System  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 005: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive / Patriot Xporter 32GB (PEF32GUSB) Flash Drive Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

its says "ID 07d1:3c16 D-Link System" 4th line midway through.
Im guessing this is it

---

### Post by Terible1biker57 on 2010-04-29
by the way how do I post like you do with a code box like that.

---

### Post by chili555 on 2010-04-29
Here is your device:> ID 07d1:3c16 D-Link System And here is the fix: [http://ubuntuforums.org/showthread.php?t=1434630](http://ubuntuforums.org/showthread.php?t=1434630)

Proofread your file carefully and post back if you get stuck.

---

### Post by Terible1biker57 on 2010-04-29
thanks dude! Ill let you know how it works

---

### Post by Terible1biker57 on 2010-04-29
Ok so proof read a millions times and I did the reboot sequence.....didnt work. 

Then I copy pasted the code you wrote in the link you provided me and still no work. 

heres the wiconfig

lo no Wireless extensions

eth0 no Wireless extensions

---

### Post by chili555 on 2010-04-30
Let's have a look at:```
sudo modprobe rt3070sta
dmesg | grep rt3
```Thanks.

---

### Post by Terible1biker57 on 2010-05-01
**[SIZE="6"]sudo modprobe rt3070sta[/SIZE]**

**Resulted in this:**

new:WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.

WARNING: /etc/modprobe.d/blacklist.config line 1: ignoring bad line starting with 'Blacklist'

WARNING: /etc/modprobe.d/blacklist.config line 2: ignoring bad line starting with 'Blacklist'

WARNING: /etc/modprobe.d/blacklist.config line 3: ignoring bad line starting with 'Blacklist'

WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release.

WARNING: /etc/modprobe.d/blacklist.config line 1: ignoring bad line starting with 'Blacklist'

WARNING: /etc/modprobe.d/blacklist.config line 2: ignoring bad line starting with 'Blacklist'

WARNING: /etc/modprobe.d/blacklist.config line 3: ignoring bad line starting with 'Blacklist'

FATAL: Module rt3070sta not found.

sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent

FATAL: Error running install command for rt3070sta


**[SIZE="6"]dmesg | grep rt3 [/SIZE]**

**Resulted in this:**

[    0.686280] pci 0000:02:00.0: PME# disabled

[    0.686335] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]

[    0.686337] pci 0000:00:06.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]

[    0.686341] pci 0000:00:06.0: bridge 64bit mmio pref: [0xfda00000-0xfdafffff]

[    0.686395] pci 0000:00:14.4: transparent bridge

[    0.686399] pci 0000:00:14.4: bridge io port: [0xc000-0xcfff]

[    0.686403] pci 0000:00:14.4: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]

[    0.686407] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdb00000-0xfdbfffff]

[    0.686420] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    0.686632] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]

[    0.686698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]

[    0.686751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]

[    0.701339] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.

[    0.701422] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.

[    0.701499] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.

[    0.701575] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.

[    0.701652] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.

[    0.701729] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.

[    0.701805] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.

[    0.701885] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.

[    0.701984] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none

[    0.701987] vgaarb: loaded

[    0.702077] SCSI subsystem initialized

[    0.702138] libata version 3.00 loaded.

[    0.702138] usbcore: registered new interface driver usbfs

[    0.702138] usbcore: registered new interface driver hub

[    0.702138] usbcore: registered new device driver usb

[    0.702138] ACPI: WMI: Mapper loaded

[    0.702138] PCI: Using ACPI for IRQ routing

[    0.702138] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]

[    0.702138] pci 0000:00:00.0: BAR 3: can't allocate resource

[    0.702138] NetLabel: Initializing

[    0.702138] NetLabel:  domain hash size = 128

[    0.702138] NetLabel:  protocols = UNLABELED CIPSOv4

[    0.702138] NetLabel:  unlabeled traffic allowed by default

[    0.702138] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0

[    0.702138] hpet0: 4 comparators, 32-bit 14.318180 MHz counter

[    0.702235] Switching to clocksource tsc

[    0.704911] AppArmor: AppArmor Filesystem Enabled

[    0.704911] pnp: PnP ACPI init

[    0.704911] ACPI: bus type pnp registered

[    0.704911] pnp 00:0a: mem resource (0xcec00-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling

[    0.704911] pnp 00:0a: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling

[    0.704911] pnp 00:0a: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling

[    0.704911] pnp 00:0a: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling

[    0.704911] pnp 00:0a: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling

[    0.704911] pnp 00:0a: mem resource (0x100000-0x6fedffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling

[    0.704911] pnp: PnP ACPI: found 11 devices

[    0.704911] ACPI: ACPI bus type pnp unregistered

[    0.704911] system 00:01: ioport range 0x4d0-0x4d1 has been reserved

[    0.704911] system 00:01: ioport range 0x220-0x225 has been reserved

[    0.704911] system 00:01: ioport range 0x290-0x294 has been reserved

[    0.704911] system 00:02: ioport range 0x4100-0x411f has been reserved

[    0.704911] system 00:02: ioport range 0x228-0x22f has been reserved

[    0.704911] system 00:02: ioport range 0x40b-0x40b has been reserved

[    0.704911] system 00:02: ioport range 0x4d6-0x4d6 has been reserved

[    0.704911] system 00:02: ioport range 0xc00-0xc01 has been reserved

[    0.704911] system 00:02: ioport range 0xc14-0xc14 has been reserved

[    0.704911] system 00:02: ioport range 0xc50-0xc52 has been reserved

[    0.704911] system 00:02: ioport range 0xc6c-0xc6d has been reserved

[    0.704911] system 00:02: ioport range 0xc6f-0xc6f has been reserved

[    0.704911] system 00:02: ioport range 0xcd0-0xcd1 has been reserved

[    0.704911] system 00:02: ioport range 0xcd2-0xcd3 has been reserved

[    0.704911] system 00:02: ioport range 0xcd4-0xcdf has been reserved

[    0.704911] system 00:02: ioport range 0x4000-0x40fe has been reserved

[    0.704911] system 00:02: ioport range 0x4210-0x4217 has been reserved

[    0.704911] system 00:02: ioport range 0xb00-0xb0f has been reserved

[    0.704911] system 00:02: ioport range 0xb10-0xb1f has been reserved

[    0.704911] system 00:02: ioport range 0xb20-0xb3f has been reserved

[    0.704911] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved

[    0.704911] system 00:0a: iomem range 0x6fee0000-0x6fefffff could not be reserved

[    0.704911] system 00:0a: iomem range 0xffff0000-0xffffffff has been reserved

[    0.704911] system 00:0a: iomem range 0x6fff0000-0x7ffeffff could not be reserved

[    0.704911] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved

[    0.704911] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved

[    0.704911] system 00:0a: iomem range 0xfff80000-0xfffeffff has been reserved

[    0.708222] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01

[    0.708224] pci 0000:00:01.0:   IO window: 0xe000-0xefff

[    0.708227] pci 0000:00:01.0:   MEM window: 0xfde00000-0xfdffffff

[    0.708229] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff

[    0.708235] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02

[    0.708237] pci 0000:00:06.0:   IO window: 0xd000-0xdfff

[    0.708240] pci 0000:00:06.0:   MEM window: 0xfdd00000-0xfddfffff

[    0.708242] pci 0000:00:06.0:   PREFETCH window: 0x000000fda00000-0x000000fdafffff

[    0.708246] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03

[    0.708248] pci 0000:00:14.4:   IO window: 0xc000-0xcfff

[    0.708253] pci 0000:00:14.4:   MEM window: 0xfdc00000-0xfdcfffff

[    0.708257] pci 0000:00:14.4:   PREFETCH window: 0xfdb00000-0xfdbfffff

[    0.708272]   alloc irq_desc for 18 on node 0

[    0.708273]   alloc kstat_irqs on node 0

[    0.708281] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    0.708284] pci 0000:00:06.0: setting latency timer to 64

[    0.708291] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]

[    0.708294] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]

[    0.708296] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]

[    0.708298] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdffffff]

[    0.708300] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]

[    0.708302] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]

[    0.708304] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]

[    0.708306] pci_bus 0000:02: resource 2 pref mem [0xfda00000-0xfdafffff]

[    0.708308] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]

[    0.708310] pci_bus 0000:03: resource 1 mem: [0xfdc00000-0xfdcfffff]

[    0.708312] pci_bus 0000:03: resource 2 pref mem [0xfdb00000-0xfdbfffff]

[    0.708314] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]

[    0.708316] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]

[    0.708351] NET: Registered protocol family 2

[    0.708462] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)

[    0.709087] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)

[    0.710887] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)

[    0.711342] TCP: Hash tables configured (established 262144 bind 65536)

[    0.711344] TCP reno registered

[    0.711443] NET: Registered protocol family 1

[    0.855296] pci 0000:01:05.0: Boot video device

[    0.855681] Scanning for low memory corruption every 60 seconds

[    0.855785] audit: initializing netlink socket (disabled)

[    0.855794] type=2000 audit(1272682288.855:1): initialized

[    0.862457] HugeTLB registered 2 MB page size, pre-allocated 0 pages

[    0.863491] VFS: Disk quotas dquot_6.5.2

[    0.863534] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)

[    0.864029] fuse init (API version 7.13)

[    0.864086] msgmni has been set to 3491

[    0.864325] alg: No test for stdrng (krng)

[    0.864371] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)

[    0.864375] io scheduler noop registered

[    0.864376] io scheduler anticipatory registered

[    0.864378] io scheduler deadline registered

[    0.864405] io scheduler cfq registered (default)

[    0.864566]   alloc irq_desc for 25 on node 0

[    0.864568]   alloc kstat_irqs on node 0

[    0.864576] pcieport 0000:00:06.0: irq 25 for MSI/MSI-X

[    0.864581] pcieport 0000:00:06.0: setting latency timer to 64

[    0.864631] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[    0.864650] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

[    0.864728] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0

[    0.864733] ACPI: Power Button [PWRB]

[    0.864774] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1

[    0.864776] ACPI: Power Button [PWRF]

[    0.865046] processor LNXCPU:00: registered as cooling_device0

[    0.865078] processor LNXCPU:01: registered as cooling_device1

[    0.865114] processor LNXCPU:02: registered as cooling_device2

[    0.865149] processor LNXCPU:03: registered as cooling_device3

[    0.867585] Linux agpgart interface v0.103

[    0.867617] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled

[    0.867726] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    0.867977] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

[    0.868679] brd: module loaded

[    0.869005] loop: module loaded

[    0.869082] input: Macintosh mouse button emulation as /devices/virtual/input/input2

[    0.869309]   alloc irq_desc for 16 on node 0

[    0.869311]   alloc kstat_irqs on node 0

[    0.869321] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    0.869591] Fixed MDIO Bus: probed

[    0.869614] PPP generic driver version 2.4.2

[    0.869647] tun: Universal TUN/TAP device driver, 1.6

[    0.869648] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>

[    0.869715] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

[    0.869749]   alloc irq_desc for 17 on node 0

[    0.869750]   alloc kstat_irqs on node 0

[    0.869758] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17

[    0.869777] ehci_hcd 0000:00:12.2: EHCI Host Controller

[    0.869802] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1

[    0.869833] ehci_hcd 0000:00:12.2: debug port 1

[    0.869861] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000

[    0.878406] Freeing initrd memory: 8127k freed

[    0.885272] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00

[    0.885417] usb usb1: configuration #1 chosen from 1 choice

[    0.885438] hub 1-0:1.0: USB hub found

[    0.885444] hub 1-0:1.0: 6 ports detected

[    0.885552]   alloc irq_desc for 19 on node 0

[    0.885554]   alloc kstat_irqs on node 0

[    0.885562] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19

[    0.885579] ehci_hcd 0000:00:13.2: EHCI Host Controller

[    0.885607] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2

[    0.885633] ehci_hcd 0000:00:13.2: debug port 1

[    0.885662] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000

[    0.905280] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00

[    0.905405] usb usb2: configuration #1 chosen from 1 choice

[    0.905429] hub 2-0:1.0: USB hub found

[    0.905435] hub 2-0:1.0: 6 ports detected

[    0.905505] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver

[    0.905568] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    0.905584] ohci_hcd 0000:00:12.0: OHCI Host Controller

[    0.905612] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3

[    0.905644] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000

[    0.969363] usb usb3: configuration #1 chosen from 1 choice

[    0.969388] hub 3-0:1.0: USB hub found

[    0.969397] hub 3-0:1.0: 3 ports detected

[    0.969519] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    0.969534] ohci_hcd 0000:00:12.1: OHCI Host Controller

[    0.969563] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4

[    0.969581] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000

[    1.029367] usb usb4: configuration #1 chosen from 1 choice

[    1.029390] hub 4-0:1.0: USB hub found

[    1.029401] hub 4-0:1.0: 3 ports detected

[    1.029525] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    1.029542] ohci_hcd 0000:00:13.0: OHCI Host Controller

[    1.029570] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5

[    1.029605] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000

[    1.094156] usb usb5: configuration #1 chosen from 1 choice

[    1.094177] hub 5-0:1.0: USB hub found

[    1.094185] hub 5-0:1.0: 3 ports detected

[    1.094310] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    1.094327] ohci_hcd 0000:00:13.1: OHCI Host Controller

[    1.094359] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6

[    1.094378] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000

[    1.154146] usb usb6: configuration #1 chosen from 1 choice

[    1.154168] hub 6-0:1.0: USB hub found

[    1.154176] hub 6-0:1.0: 3 ports detected

[    1.154303] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[    1.154320] ohci_hcd 0000:00:14.5: OHCI Host Controller

[    1.154352] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7

[    1.154371] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000

[    1.210056] usb 1-1: new high speed USB device using ehci_hcd and address 2

[    1.214169] usb usb7: configuration #1 chosen from 1 choice

[    1.214189] hub 7-0:1.0: USB hub found

[    1.214197] hub 7-0:1.0: 2 ports detected

[    1.214256] uhci_hcd: USB Universal Host Controller Interface driver

[    1.214316] PNP: No PS/2 controller found. Probing ports directly.

[    1.247581] Failed to disable AUX port, but continuing anyway... Is this a SiS?

[    1.247583] If AUX port is really absent please use the 'i8042.noaux' option.

[    1.377766] usb 1-1: configuration #1 chosen from 1 choice

[    1.490047] usb 2-3: new high speed USB device using ehci_hcd and address 2

[    1.490157] serio: i8042 KBD port at 0x60,0x64 irq 1

[    1.490287] mice: PS/2 mouse device common for all mice

[    1.490365] rtc_cmos 00:05: RTC can wake from S4

[    1.490393] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0

[    1.490425] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs

[    1.490523] device-mapper: uevent: version 1.0.3

[    1.490634] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]

[    1.490724] device-mapper: multipath: version 1.1.0 loaded

[    1.490727] device-mapper: multipath round-robin: version 1.0.0 loaded

[    1.490926] cpuidle: using governor ladder

[    1.490928] cpuidle: using governor menu

[    1.491192] TCP cubic registered

[    1.491279] NET: Registered protocol family 10

[    1.491636] lo: Disabled Privacy Extensions

[    1.491841] NET: Registered protocol family 17

[    1.491907] powernow-k8: Found 1 AMD Athlon(tm) II X4 620 Processor processors (4 cpu cores) (version 2.20.00)

[    1.491945] powernow-k8:    0 : pstate 0 (2600 MHz)

[    1.491947] powernow-k8:    1 : pstate 1 (1900 MHz)

[    1.491948] powernow-k8:    2 : pstate 2 (1400 MHz)

[    1.491950] powernow-k8:    3 : pstate 3 (800 MHz)

[    1.492364] PM: Resume from disk failed.

[    1.492373] registered taskstats version 1

[    1.492655]   Magic number: 10:614:863

[    1.492745] rtc_cmos 00:05: setting system clock to 2010-05-01 02:51:30 UTC (1272682290)

[    1.492748] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    1.492749] EDD information not available.

[    1.492789] Freeing unused kernel memory: 876k freed

[    1.493066] Write protecting the kernel read-only data: 7680k

[    1.510923] udev: starting version 151

[    1.559709] scsi0 : pata_atiixp

[    1.567343] scsi1 : pata_atiixp

[    1.568422] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14

[    1.568426] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15

[    1.568558] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

[    1.568580] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[    1.568631] r8169 0000:02:00.0: setting latency timer to 64

[    1.568667]   alloc irq_desc for 26 on node 0

[    1.568669]   alloc kstat_irqs on node 0

[    1.568682] r8169 0000:02:00.0: irq 26 for MSI/MSI-X

[    1.569161] eth0: RTL8168d/8111d at 0xffffc90000340000, 6c:f0:49:2b:c9:4d, XID 083000c0 IRQ 26

[    1.606838] ahci 0000:00:11.0: version 3.0

[    1.606849]   alloc irq_desc for 22 on node 0

[    1.606850]   alloc kstat_irqs on node 0

[    1.606858] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22

[    1.606964] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode

[    1.606968] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 

[    1.607325] scsi2 : ahci

[    1.607465] scsi3 : ahci

[    1.607515] scsi4 : ahci

[    1.607565] scsi5 : ahci

[    1.607665] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22

[    1.607668] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22

[    1.607671] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22

[    1.607675] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22

[    1.649533] usb 2-3: configuration #1 chosen from 1 choice

[    1.655315] Initializing USB Mass Storage driver...

[    1.655465] scsi6 : SCSI emulation for USB Mass Storage devices

[    1.655542] usb-storage: device found at 2

[    1.655545] usb-storage: waiting for device to settle before scanning

[    1.655550] usbcore: registered new interface driver usb-storage

[    1.655553] USB Mass Storage support registered.

[    1.790485] ata1.00: ATA-7: ST3120213ACE, 3.ACF, max UDMA/100

[    1.790489] ata1.00: 234441648 sectors, multi 16: LBA48 

[    1.882066] ata1.00: configured for UDMA/100

[    1.882161] scsi 0:0:0:0: Direct-Access     ATA      ST3120213ACE     3.AC PQ: 0 ANSI: 5

[    1.882346] sd 0:0:0:0: Attached scsi generic sg0 type 0

[    1.882389] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)

[    1.882435] sd 0:0:0:0: [sda] Write Protect is off

[    1.882437] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    1.882451] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    1.882565]  sda: sda1 sda2 <

[    1.950056] ata6: SATA link down (SStatus 0 SControl 300)

[    1.950087] ata4: SATA link down (SStatus 0 SControl 300)

[    1.950131] ata5: SATA link down (SStatus 0 SControl 300)

[    1.978179]  sda5 >

[    1.978479] sd 0:0:0:0: [sda] Attached SCSI disk

[    2.030057] usb 6-1: new low speed USB device using ohci_hcd and address 2

[    2.130048] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

[    2.134179] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22LS50, TL02, max UDMA/100, ATAPI AN

[    2.138499] ata3.00: configured for UDMA/100

[    2.163447] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22LS50  TL02 PQ: 0 ANSI: 5

[    2.185144] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray

[    2.185148] Uniform CD-ROM driver Revision: 3.20

[    2.185279] sr 2:0:0:0: Attached scsi CD-ROM sr0

[    2.185334] sr 2:0:0:0: Attached scsi generic sg1 type 5

[    2.225125] usb 6-1: configuration #1 chosen from 1 choice

[    2.235054] usbcore: registered new interface driver hiddev

[    2.235181] usbcore: registered new interface driver usbhid

[    2.235183] usbhid: v2.6:USB HID core driver

[    2.241226] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.0/input/input3

[    2.241308] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:13.1-1/input0

[    2.249021] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor

[    2.249531] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.1/input/input4

[    2.249670] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-1/input1

[    2.650303] EXT4-fs (sda1): mounted filesystem with ordered data mode

[    6.650292] usb-storage: device scan complete

[    6.651275] scsi 6:0:0:0: Direct-Access     OCZ      DIESEL           PMAP PQ: 0 ANSI: 0 CCS

[    6.651602] sd 6:0:0:0: Attached scsi generic sg2 type 0

[    6.653005] sd 6:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)

[    6.653519] sd 6:0:0:0: [sdb] Write Protect is off

[    6.653523] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00

[    6.653525] sd 6:0:0:0: [sdb] Assuming drive cache: write through

[    6.655643] sd 6:0:0:0: [sdb] Assuming drive cache: write through

[    6.655648]  sdb: sdb1

[    6.658016] sd 6:0:0:0: [sdb] Assuming drive cache: write through

[    6.658020] sd 6:0:0:0: [sdb] Attached SCSI removable disk

[   13.336434] Adding 4805624k swap on /dev/sda5.  Priority:-1 extents:1 across:4805624k 

[   13.371408] udev: starting version 151

[   13.521545] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0

[   13.521553] shpchp 0000:00:01.0: Cannot reserve MMIO region

[   13.522141] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   13.532172] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]

[   13.532177] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

[   13.532669] EDAC MC: Ver: 2.1.0 Apr 16 2010

[   13.542549] type=1505 audit(1272707502.541:2):  operation="profile_load" pid=517 name="/sbin/dhclient3"

[   13.542771] type=1505 audit(1272707502.541:3):  operation="profile_load" pid=517 name="/usr/lib/NetworkManager/nm-dhcp-client.action"

[   13.542894] type=1505 audit(1272707502.541:4):  operation="profile_load" pid=517 name="/usr/lib/connman/scripts/dhclient-script"

[   13.555956] EDAC amd64_edac:  Ver: 3.2.0 Apr 16 2010

[   13.557142] lp: driver loaded but no devices found

[   13.575372] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).

[   13.575389] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.

[   13.575390]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.

[   13.575391]  (Note that use of the override may cause unknown side effects.)

[   13.575430] amd64_edac: probe of 0000:00:18.2 failed with error -22

[   13.580450] [drm] Initialized drm 1.1.0 20060810

[   13.614975] [drm] radeon defaulting to kernel modesetting.

[   13.614979] [drm] radeon kernel modesetting enabled.

[   13.615375] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18

[   13.615382] radeon 0000:01:05.0: setting latency timer to 64

[   13.619092] [drm] radeon: Initializing kernel modesetting.

[   13.621589] [drm] register mmio base: 0xFDFE0000

[   13.621592] [drm] register mmio size: 65536

[   13.621961] ATOM BIOS: B27732

[   13.621980] [drm] Clocks initialized !

[   13.622229] [drm] Detected VRAM RAM=256M, BAR=256M

[   13.622235] [drm] RAM width 32bits DDR

[   13.622603] [TTM] Zone  kernel: Available graphics memory: 898316 kiB.

[   13.622622] [drm] radeon: 256M of VRAM memory ready

[   13.622624] [drm] radeon: 512M of GTT memory ready.

[   13.622658] [drm] radeon: irq initialized.

[   13.622661] [drm] GART: num cpu pages 131072, num gpu pages 131072

[   13.623765] [drm] Loading RS780 Microcode

[   13.623770] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin

[   13.626266] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin

[   13.629624] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin

[   13.664567] [drm] ring test succeeded in 1 usecs

[   13.664647] [drm] radeon: ib pool ready.

[   13.664709] [drm] ib test succeeded in 0 usecs

[   13.664711] [drm] Enabling audio support

[   13.664855] [drm] Radeon Display Connectors

[   13.664857] [drm] Connector 0:

[   13.664858] [drm]   VGA

[   13.664861] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c

[   13.664862] [drm]   Encoders:

[   13.664863] [drm]     CRT1: INTERNAL_KLDSCP_DAC1

[   13.664864] [drm] Connector 1:

[   13.664865] [drm]   DVI-D

[   13.664866] [drm]   HPD1

[   13.664868] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c

[   13.664869] [drm]   Encoders:

[   13.664870] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA

[   13.680034] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[   13.777479] [drm] fb mappable at 0xD0141000

[   13.777480] [drm] vram apper at 0xD0000000

[   13.777482] [drm] size 8294400

[   13.777483] [drm] fb depth is 24

[   13.777484] [drm]    pitch is 7680

[   13.777555] fb0: radeondrmfb frame buffer device

[   13.777556] registered panic notifier

[   13.777562] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0

[   13.779098] vga16fb: initializing

[   13.779103] vga16fb: mapped to 0xffff8800000a0000

[   13.779110] vga16fb: not registering due to another framebuffer present

[   13.810357] Console: switching to colour frame buffer device 240x67

[   13.828041] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5

[   13.840512] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19

[   13.840542] HDA Intel 0000:01:05.1: setting latency timer to 64

[   14.122327] type=1505 audit(1272707503.121:5):  operation="profile_load" pid=845 name="/usr/share/gdm/guest-session/Xsession"

[   14.123924] type=1505 audit(1272707503.131:6):  operation="profile_replace" pid=846 name="/sbin/dhclient3"

[   14.124145] type=1505 audit(1272707503.131:7):  operation="profile_replace" pid=846 name="/usr/lib/NetworkManager/nm-dhcp-client.action"

[   14.124273] type=1505 audit(1272707503.131:8):  operation="profile_replace" pid=846 name="/usr/lib/connman/scripts/dhclient-script"

[   14.127249] type=1505 audit(1272707503.131:9):  operation="profile_load" pid=847 name="/usr/bin/evince"

[   14.130134] type=1505 audit(1272707503.131:10):  operation="profile_load" pid=847 name="/usr/bin/evince-previewer"

[   14.131932] type=1505 audit(1272707503.131:11):  operation="profile_load" pid=847 name="/usr/bin/evince-thumbnailer"

[   14.473575] r8169: eth0: link down

[   14.473963] ADDRCONF(NETDEV_UP): eth0: link is not ready

[   14.744095] ppdev: user-space parallel port driver

[   17.104804] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

[   92.283420] usb 2-3: USB disconnect, address 2

[  191.920094] usb 2-3: new high speed USB device using ehci_hcd and address 4

[  192.080808] usb 2-3: configuration #1 chosen from 1 choice

[  192.081164] scsi7 : SCSI emulation for USB Mass Storage devices

[  192.081346] usb-storage: device found at 4

[  192.081354] usb-storage: waiting for device to settle before scanning

[  197.080429] usb-storage: device scan complete

[  197.081583] scsi 7:0:0:0: Direct-Access     OCZ      DIESEL           PMAP PQ: 0 ANSI: 0 CCS

[  197.082416] sd 7:0:0:0: Attached scsi generic sg2 type 0

[  198.625602] sd 7:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)

[  198.626082] sd 7:0:0:0: [sdb] Write Protect is off

[  198.626089] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00

[  198.626095] sd 7:0:0:0: [sdb] Assuming drive cache: write through

[  198.629366] sd 7:0:0:0: [sdb] Assuming drive cache: write through

[  198.629379]  sdb: sdb1

[  198.632472] sd 7:0:0:0: [sdb] Assuming drive cache: write through

[  198.632483] sd 7:0:0:0: [sdb] Attached SCSI removable disk

thanks again dude.

---

### Post by chili555 on 2010-05-01
First of all, I don't know what the giant font in bold is all about; it's not needed. Second, this file:> new:WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config,Should be named .conf and not .config. Please do:```
sudo mv /etc/modprobe.d/blacklist.config /etc/modprobe.d/blacklist.conf
```Next, you need to edit the file to change every instance of [COLOR="Red"]B[/COLOR]lacklist to [COLOR="Red"]b[/COLOR]lacklist. It makes a difference.

May I know the files you blacklisted?

Also, I suggest you recheck your dmesg command. It was:```
dmesg | grep rt3
```Evidently the pipe symbol | was omitted; we were seeking only the lines that contain "rt3."

---

### Post by Terible1biker57 on 2010-05-01
sorry about the large type. it was simply differentiate between code. sorry. Ill try this now

---

### Post by Terible1biker57 on 2010-05-01
I forgot what i blacklisted ,also another question. wheres the "pipe" key on the keyboard

---

### Post by Terible1biker57 on 2010-05-01
nvm i found the pipe key. also I just did the dmesg and nothing came up.

---

### Post by Terible1biker57 on 2010-05-01
I did the sudo mv /etc/modprobe.d/blacklist.config /etc/modprobe.d/blacklist.conf 

and it just said they are the same file?

how do i get to the blacklist again? sorry

---

### Post by chili555 on 2010-05-01
> **Terible1biker57 said:**
> I did the sudo mv /etc/modprobe.d/blacklist.config /etc/modprobe.d/blacklist.conf 

and it just said they are the same file?

how do i get to the blacklist again? sorry```
cat /etc/modprobe.d/blacklist.conf
```To edit it:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Proofread carefully.

Please let us see:```
ls /etc/modprobe.d | grep black
```

---

### Post by Terible1biker57 on 2010-05-01
heres the black list file:
This file lists those modules which we don't want to be loaded by 
# alias expansion, usually so some other driver will be loaded for the 
# device instead. 

# evbug is a debug tool that should be loaded explicitly 
blacklist evbug 

# these drivers are very simple, the HID drivers are usually preferred 
blacklist usbmouse 
blacklist usbkbd 

# replaced by e100 
blacklist eepro100 

# replaced by tulip 
blacklist de4x5 

# causes no end of confusion by creating unexpected network interfaces 
blacklist eth1394 

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much 
# hardware on its own (Ubuntu bug #2011, #6810) 
blacklist snd_intel8x0m 

# Conflicts with dvb driver (which is better for handling this device) 
blacklist snd_aw2 

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306) 
blacklist i2c_i801 

# replaced by p54pci 
blacklist prism54 
blacklist rt2800usb 
blacklist rt2x00usb 
blacklist rt2x00lib 

# replaced by b43 and ssb. 
blacklist bcm43xx 

# most apps now use garmin usb driver directly (Ubuntu: #114565) 
blacklist garmin_gps 

# replaced by asus-laptop (Ubuntu: #184721) 
blacklist asus_acpi 

# low-quality, just noise when being used for sound playback, causes 
# hangs at desktop session start (Ubuntu: #246969) 
blacklist snd_pcsp 

# ugly and loud noise, getting on everyone's nerves; this should be done by a 
# nice pulseaudio bing (Ubuntu: #77010) 
blacklist pcspkr 

# EDAC driver for amd76x clashes with the agp driver preventing the aperture 
# from being initialised (Ubuntu: #297750). Blacklist so that the driver 
# continues to build and is installable for the few cases where its 
# really needed. 
blacklist amd76x_edac 

and heres what resulted after ls /etc/modprobe.d | grep black:

blacklist-ath_pci.conf 
blacklist.conf 
blacklist.config 
blacklist-firewire.conf 
blacklist-framebuffer.conf 
blacklist-modem.conf 
blacklist-oss.conf 
blacklist-watchdog.conf

---

### Post by chili555 on 2010-05-01
> and heres what resulted after ls /etc/modprobe.d | grep black:

blacklist-ath_pci.conf
blacklist.conf
blacklist.config
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf> I did the sudo mv /etc/modprobe.d/blacklist.config /etc/modprobe.d/blacklist.conf

and it just said they are the same file?Evidently they are *not* the same file, since you have a .conf file and a .config file. 

Please do:```
sudo rm /etc/modprobe.d/blacklist.config
```Please proofread carefully before you press the Enter button. We are removing .config and we are doing nothing yet to blacklist.conf.

---

### Post by Terible1biker57 on 2010-05-01
ok its removed.

---

### Post by chili555 on 2010-05-01
> FATAL: Module rt3070sta not found.Evidently rt3070sta was removed from Lucid 10.04. As there is no known simple solution, we are going to try an experiment. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove these lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib 
```Next, do:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Change the file as I have highlighted to remove rt3070sta and add in rt2800usb:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba [COLOR="Red"]rt2800usb[/COLOR]"

```Now do:```
sudo gedit etc/modprobe.d/network_drivers.conf
```Amend to:```
install [COLOR="Red"]rt2800usb[/COLOR] /sbin/modprobe --ignore-install [COLOR="Red"]rt2800usb[/COLOR] $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/[COLOR="Red"]rt2800[/COLOR]/new_id
```Proofread all changes carefully, being sure to click Save before you close gedit.

Reboot and let us know the outcome.

---

### Post by Terible1biker57 on 2010-05-01
this is really weird, So I got through most of the code. but right when I did sudo gedit etc/modprobe.d/network_drivers.conf it opened in gedit and their was nothing in the file, no text at all. so I proceed to enter "install rt2800usb /sbin/modprobe --ignore-install rt2800usb $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2800/new_id" and then press save. Well on the top it says "Could not find the file /home/net-op/etc/modprobe.d/network_drivers.conf." in Red. So I navigate through the explorer Home/net-op/etc/modprobe.d and in the modprobe.d folder their is "network_drivers.conf. Weird right.

---

### Post by chili555 on 2010-05-01
> "Could not find the file /home/net-op/etc/modprobe.d/network_drivers.conf."It is NOT supposed to be in  /home/net-op/etc/modprobe.d/network_drivers.conf. It is supposed to be in /etc/modprobe.d/network_drivers.conf. There is a difference. Please retrace your steps and make any needed corrections.

This is also incorrect: sudo gedit etc/modprobe.d/network_drivers.conf 

It is supposed to be sudo gedit [COLOR="Red"]/[/COLOR]etc/modprobe.d/network_drivers.conf 

Again, there is a crucial difference. Please proofread carefully.

---

### Post by bfh80 on 2010-05-05
ok so i tryed what you said to do here only dif is mine is 07d1:3c0d and i changed it in the line of code I fallowed you gidence chili for 9.10 and got my DWA 124 working but i still cant get it to work in 10.4

---

### Post by ario on 2010-10-02
Dear user, 
I read all this topic from start to the end.
I have the same adapter as you. I think you must completely demolished your systems default configuration by trying various commands and modification. But you can start a new approach by using Ubuntu 10.04 live CD and repeat all commands in it. Once you tried it, you may see the USB adapter will start blinking by defaut. If not, You can test it with a windows (I'm sorry but this may be last chance!) to see if it's really working or some chips are burnt in it! If it starts to blink, it means that 10.04 is recognized your adapter as a rt2800 thing.
Now we need to black list 2800 driver to prevent ubuntu recognize our adapter as a 2800 one.
The second problem is that Ubuntu has no other drivers for it!
Please tell me if you solve this issue.
Thanks

---

### Post by johnsuffer on 2010-10-02
**oct 2sd i,m stuck with my dwa-125 wifi usb dlink adaptor im on 10.o4 ubuntu im a real NEWBE my wireles connection is actived ok but shows the wrong ip address here what its says when i click on network manager applet when its conncted**
 
**INTERFACE 802.11 WIFI (WLAN0) OK**
**MAC ADDRESS HARDWARE ITS MINE OK**
**DRIVER RT2800USB WRONG MINE IS RTD2870 INSTALLED OK**
**SPEED UNKNOWN**
**IP ADDRESS 10.42.43.1 WRONG MINE IS 192....**
**BROADCAST IP 10.42.43.255 ...... WRONG MINE IS DIFFERENT 192....**
**SUBNETMASK 255.255.255.0 ----- OK**
 
**ALSO WHEN I COMMAND ON THE TERMINAL IPCONF ITS SAYS PCI SYS **
 
**TKS ! MY QUESTIONS HOW CAN I DESACTIVATE THE PCI LAN DRIVER INSTALL BY DEFAULT ON 10.04 UBUNTU **

---

### Post by johnsuffer on 2010-10-02
DEAR ARIO ! How can I black list this stupid rt2800 driver installed by default on the ubuntu 10.04 this driver is stopping me to activate correctly my dwa -125 usb adapter
rest is workink ok my dlink dwa 125- driver .inf is already installed with the ndisgtk app (When i ask the windows drivers install it shows my dwa-125 driver installed correctly so is it because my computer used to be connected with a pci ethernet card bcause i dont have any output plug-in for that ? many tks [EMAIL="johnc_del@hotmail.com"]johnc_del@hotmail.com[/EMAIL]

---

### Post by ario on 2010-10-03
> **johnsuffer said:**
> DEAR ARIO ! How can I black list this stupid rt2800 driver installed by default on the ubuntu 10.04 this driver is stopping me to activate correctly my dwa -125 usb adapter
rest is workink ok my dlink dwa 125- driver .inf is already installed with the ndisgtk app (When i ask the windows drivers install it shows my dwa-125 driver installed correctly so is it because my computer used to be connected with a pci ethernet card bcause i dont have any output plug-in for that ? many tks [EMAIL="johnc_del@hotmail.com"]johnc_del@hotmail.com[/EMAIL]

Wow man! I must first tell you that I tried ndiswrapper and the desired driver and it demolished my system!:D The original windows driver will not work on linux. You can see the resold of dmesg command for that.
Here I created a post for this problem and other problem too. 
In this address I finally figured out how to compile, install and modprobe the opensource driver downloaded from ralink website and sort it to work properly:
[http://ubuntuforums.org/showpost.php?p=9919406&postcount=12](http://ubuntuforums.org/showpost.php?p=9919406&postcount=12)

There I described to blacklist you must add those mentioned lines at the end of a file named /etc/modprobe.d/blacklist.conf not by entering commands directly. You can simply enter this command to open that file and write blacklists there:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
This is for the black list thing.
Now after compiling and installing the linux driver, the main problem is that Network-manager will not support WPA security. Which is the only really secure option for wireless in Ubuntu!
please let me now if you figured that out.

---

