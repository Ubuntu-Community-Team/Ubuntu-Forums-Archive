---
title: "Can't Use  USB modem &quot;YOTA 4g&quot; .."
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by phelun on 2009-11-02
Hello people.>!! Im quite new to Ubuntu and im running 9.04,and i NEED to use a USB modem (YOTA 4g, by samsung) on my pc but i havent been able to use it..Anyone out here with to help..??Please!will sincerely appreciate!:( What do i have to do..
here is my mail,either u reply here or u can reach me in my mail 
[EMAIL="incras52@gmail.com"]incras52@gmail.com[/EMAIL]

---

### Post by pdc on 2009-11-02
perhaps you try and see if it is your lucky day (as Clint Eastwood might say)

so go to "Create a Mobile Network COnnection"

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

and see if you can identify the country you live in, and the network you want to connect to: 

if no joy, 

if you can work out how to open a terminal on Ubuntu: 

and then:

with the modem plugged into the computer type in 

> lsusb and hit the enter key

and then type in 

> dmesg

copy and paste the results back here:

if you select the text in the terminal, there are menus on the top line to select for copy

---

### Post by paingsoe on 2010-11-23
after typing dmesg ;
i received this __
but yota still inactive



[    0.012189] CPU: L2 cache: 2048K
[    0.012193] CPU 0/0x0 -> Node 0
[    0.012195] CPU: Physical Processor ID: 0
[    0.012197] CPU: Processor Core ID: 0
[    0.012201] mce: CPU supports 4 MCE banks
[    0.012213] CPU0: Thermal monitoring enabled (TM2)
[    0.012219] using mwait in idle threads.
[    0.012222] Performance Events: no PMU driver, software events only.
[    0.020617] ACPI: Core revision 20090903
[    0.028609] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028615] ftrace: allocating 22529 entries in 89 pages
[    0.030069] Setting APIC routing to flat
[    0.030387] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.131280] CPU0: Intel(R) Pentium(R) 4 CPU 3.60GHz stepping 04
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.020000] CPU: L2 cache: 2048K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 0
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.290071] CPU1: Intel(R) Pentium(R) 4 CPU 3.60GHz stepping 04
[    0.290081] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300023] Brought up 2 CPUs
[    0.300028] Total of 2 processors activated (14469.49 BogoMIPS).
[    0.300454] CPU0 attaching sched-domain:
[    0.300459]  domain 0: span 0-1 level SIBLING
[    0.300463]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.300469]   domain 1: span 0-1 level MC
[    0.300472]    groups: 0-1 (cpu_power = 1178)
[    0.300480] CPU1 attaching sched-domain:
[    0.300482]  domain 0: span 0-1 level SIBLING
[    0.300484]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.300490]   domain 1: span 0-1 level MC
[    0.300492]    groups: 0-1 (cpu_power = 1178)
[    0.300618] devtmpfs: initialized
[    0.300618] regulator: core version 0.5
[    0.300618] Time: 20:11:43  Date: 11/23/10
[    0.300618] NET: Registered protocol family 16
[    0.300618] Trying to unpack rootfs image as initramfs...
[    0.300618] ACPI: bus type pci registered
[    0.300618] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.300618] PCI: MCFG area at f0000000 reserved in E820
[    0.302016] PCI: Using MMCONFIG at f0000000 - f3ffffff
[    0.302020] PCI: Using configuration type 1 for base access
[    0.303471] bio: create slab <bio-0> at 0
[    0.304302] ACPI: EC: Look up EC in DSDT
[    0.313753] ACPI: Interpreter enabled
[    0.313764] ACPI: (supports S0 S1 S4 S5)
[    0.313800] ACPI: Using IOAPIC for interrupt routing
[    0.321308] ACPI: No dock devices found.
[    0.321456] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.321637] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe6000000-0xe6003fff]
[    0.321689] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.321695] pci 0000:00:1b.0: PME# disabled
[    0.321772] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.321778] pci 0000:00:1c.0: PME# disabled
[    0.321844] pci 0000:00:1d.0: reg 20 io port: [0xbc00-0xbc1f]
[    0.321904] pci 0000:00:1d.1: reg 20 io port: [0xb000-0xb01f]
[    0.321962] pci 0000:00:1d.2: reg 20 io port: [0xb400-0xb41f]
[    0.322022] pci 0000:00:1d.3: reg 20 io port: [0xb800-0xb81f]
[    0.322080] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe6004000-0xe60043ff]
[    0.322283] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.322289] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.322294] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.322300] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.322359] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.322367] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.322375] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.322382] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.322390] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.322419] pci 0000:00:1f.2: PME# supported from D3hot
[    0.322425] pci 0000:00:1f.2: PME# disabled
[    0.322478] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.322556] pci 0000:01:00.0: reg 10 32bit mmio: [0xe2000000-0xe2ffffff]
[    0.322574] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.322588] pci 0000:01:00.0: reg 1c 64bit mmio: [0xe0000000-0xe1ffffff]
[    0.322598] pci 0000:01:00.0: reg 24 io port: [0x9000-0x907f]
[    0.322608] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
[    0.322702] pci 0000:00:1c.0: bridge io port: [0x9000-0x9fff]
[    0.322708] pci 0000:00:1c.0: bridge 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.322716] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.322767] pci 0000:02:05.0: reg 10 io port: [0xa000-0xa0ff]
[    0.322777] pci 0000:02:05.0: reg 14 32bit mmio: [0xe5000000-0xe50000ff]
[    0.322807] pci 0000:02:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.322830] pci 0000:02:05.0: supports D1 D2
[    0.322833] pci 0000:02:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.322839] pci 0000:02:05.0: PME# disabled
[    0.322885] pci 0000:00:1e.0: transparent bridge
[    0.322890] pci 0000:00:1e.0: bridge io port: [0xa000-0xafff]
[    0.322896] pci 0000:00:1e.0: bridge 32bit mmio: [0xe4000000-0xe5ffffff]
[    0.322918] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.323131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.323240] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.335975] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.336130] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.336284] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.336435] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.336582] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.336735] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.336886] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.337034] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.337222] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.337228] vgaarb: loaded
[    0.337405] SCSI subsystem initialized
[    0.337528] libata version 3.00 loaded.
[    0.337659] usbcore: registered new interface driver usbfs
[    0.337678] usbcore: registered new interface driver hub
[    0.337719] usbcore: registered new device driver usb
[    0.337936] ACPI: WMI: Mapper loaded
[    0.337939] PCI: Using ACPI for IRQ routing
[    0.338145] NetLabel: Initializing
[    0.338149] NetLabel:  domain hash size = 128
[    0.338151] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.338175] NetLabel:  unlabeled traffic allowed by default
[    0.338235] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.338243] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.350160] Switching to clocksource tsc
[    0.352926] AppArmor: AppArmor Filesystem Enabled
[    0.352948] pnp: PnP ACPI init
[    0.352971] ACPI: bus type pnp registered
[    0.357609] pnp: PnP ACPI: found 15 devices
[    0.357613] ACPI: ACPI bus type pnp unregistered
[    0.357630] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.357636] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.357641] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.357646] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.357652] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.357669] system 00:0b: ioport range 0x400-0x4bf could not be reserved
[    0.357679] system 00:0c: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.357689] system 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
[    0.357693] system 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
[    0.357697] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.357702] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.357706] system 00:0d: iomem range 0x7fff0000-0x7fffffff could not be reserved
[    0.357711] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.357715] system 00:0d: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.357720] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.357724] system 00:0d: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.357728] system 00:0d: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.357733] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.357737] system 00:0d: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.357741] system 00:0d: iomem range 0xfff00000-0xffffffff has been reserved
[    0.357746] system 00:0d: iomem range 0xe0000-0xeffff has been reserved
[    0.362604] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.362610] pci 0000:00:1c.0:   IO window: 0x9000-0x9fff
[    0.362617] pci 0000:00:1c.0:   MEM window: 0xe0000000-0xe3ffffff
[    0.362623] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.362632] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.362637] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.362644] pci 0000:00:1e.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.362650] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x800fffff
[    0.362670]   alloc irq_desc for 16 on node -1
[    0.362674]   alloc kstat_irqs on node -1
[    0.362682] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362689] pci 0000:00:1c.0: setting latency timer to 64
[    0.362698] pci 0000:00:1e.0: setting latency timer to 64
[    0.362705] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.362709] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.362713] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.362717] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xe3ffffff]
[    0.362720] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.362724] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.362728] pci_bus 0000:02: resource 1 mem: [0xe4000000-0xe5ffffff]
[    0.362732] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x800fffff]
[    0.362736] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.362739] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.362801] NET: Registered protocol family 2
[    0.363033] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.364331] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.366520] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.367088] TCP: Hash tables configured (established 262144 bind 65536)
[    0.367092] TCP reno registered
[    0.367232] NET: Registered protocol family 1
[    0.367383] pci 0000:01:00.0: Boot video device
[    0.367683] Scanning for low memory corruption every 60 seconds
[    0.367901] audit: initializing netlink socket (disabled)
[    0.367916] type=2000 audit(1290543103.359:1): initialized
[    0.377846] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.380277] VFS: Disk quotas dquot_6.5.2
[    0.380372] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.381401] fuse init (API version 7.13)
[    0.381538] msgmni has been set to 3998
[    0.381857] alg: No test for stdrng (krng)
[    0.381942] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.381948] io scheduler noop registered
[    0.381952] io scheduler anticipatory registered
[    0.381956] io scheduler deadline registered
[    0.382019] io scheduler cfq registered (default)
[    0.382207]   alloc irq_desc for 24 on node -1
[    0.382211]   alloc kstat_irqs on node -1
[    0.382225] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.382236] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.382362] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.382454] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.382589] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.382594] ACPI: Power Button [PWRB]
[    0.382677] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.382682] ACPI: Power Button [PWRF]
[    0.383095] processor LNXCPU:00: registered as cooling_device0
[    0.383391] ACPI: SSDT 000000007fff7240 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.383708] processor LNXCPU:01: registered as cooling_device1
[    0.387181] Linux agpgart interface v0.103
[    0.387219] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.387326] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.387423] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.387720] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.387859] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.389052] brd: module loaded
[    0.389580] loop: module loaded
[    0.389770] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.389904] ata_piix 0000:00:1f.2: version 2.13
[    0.389924]   alloc irq_desc for 19 on node -1
[    0.389927]   alloc kstat_irqs on node -1
[    0.389936] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.389943] ata_piix 0000:00:1f.2: MAP [ IDE IDE P1 P3 ]
[    0.390000] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.390107] scsi0 : ata_piix
[    0.390221] scsi1 : ata_piix
[    0.391405] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.391410] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.391980] Fixed MDIO Bus: probed
[    0.392038] PPP generic driver version 2.4.2
[    0.392098] tun: Universal TUN/TAP device driver, 1.6
[    0.392102] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.392226] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.392256]   alloc irq_desc for 23 on node -1
[    0.392260]   alloc kstat_irqs on node -1
[    0.392267] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.392287] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.392292] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.392346] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.392374] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.396258] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.396281] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe6004000
[    0.419722] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.419896] usb usb1: configuration #1 chosen from 1 choice
[    0.419945] hub 1-0:1.0: USB hub found
[    0.419960] hub 1-0:1.0: 8 ports detected
[    0.420070] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.420095] uhci_hcd: USB Universal Host Controller Interface driver
[    0.420149] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.420162] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.420167] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.420231] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.420275] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000bc00
[    0.420414] usb usb2: configuration #1 chosen from 1 choice
[    0.420465] hub 2-0:1.0: USB hub found
[    0.420474] hub 2-0:1.0: 2 ports detected
[    0.420552] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.420561] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.420566] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.420625] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.420666] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b000
[    0.420796] usb usb3: configuration #1 chosen from 1 choice
[    0.420843] hub 3-0:1.0: USB hub found
[    0.420853] hub 3-0:1.0: 2 ports detected
[    0.420926]   alloc irq_desc for 18 on node -1
[    0.420930]   alloc kstat_irqs on node -1
[    0.420939] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.420947] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.420952] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.421008] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.421044] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[    0.421178] usb usb4: configuration #1 chosen from 1 choice
[    0.421217] hub 4-0:1.0: USB hub found
[    0.421226] hub 4-0:1.0: 2 ports detected
[    0.421293] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.421301] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.421305] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.421362] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.421398] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[    0.421524] usb usb5: configuration #1 chosen from 1 choice
[    0.421563] hub 5-0:1.0: USB hub found
[    0.421573] hub 5-0:1.0: 2 ports detected
[    0.421718] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.421722] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.421868] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.421993] mice: PS/2 mouse device common for all mice
[    0.422156] rtc_cmos 00:03: RTC can wake from S4
[    0.422219] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.422253] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.422459] device-mapper: uevent: version 1.0.3
[    0.422624] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.422715] device-mapper: multipath: version 1.1.0 loaded
[    0.422720] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.422946] cpuidle: using governor ladder
[    0.422951] cpuidle: using governor menu
[    0.423548] TCP cubic registered
[    0.423756] NET: Registered protocol family 10
[    0.424452] lo: Disabled Privacy Extensions
[    0.424927] NET: Registered protocol family 17
[    0.426182] PM: Resume from disk failed.
[    0.426200] registered taskstats version 1
[    0.426477]   Magic number: 2:498:195
[    0.426583] rtc_cmos 00:03: setting system clock to 2010-11-23 20:11:44 UTC (1290543104)
[    0.426589] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.426592] EDD information not available.
[    0.440602] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.568205] Freeing initrd memory: 9962k freed
[    0.580269] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    0.619984] ata1.00: configured for UDMA/33
[    0.643522] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    0.655962] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.655968] Uniform CD-ROM driver Revision: 3.20
[    0.656098] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.656171] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.779934] ata2.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[    0.779939] ata2.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[    0.779942] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.848633] ata2.00: configured for UDMA/133
[    0.848741] scsi 1:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    0.848881] sd 1:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.848900] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    0.848965] sd 1:0:0:0: [sda] Write Protect is off
[    0.848970] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.849005] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.849161]  sda: sda1 sda2 < sda5 sda6
[    0.919902] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    0.922485]  sda7 sda8 sda9 sda10 sda11 sda12 >
[    0.989318] sd 1:0:0:0: [sda] Attached SCSI disk
[    0.989343] Freeing unused kernel memory: 880k freed
[    0.989758] Write protecting the kernel read-only data: 7696k
[    1.008758] udev[79]: starting version 163
[    1.070983] usb 1-7: configuration #1 chosen from 1 choice
[    1.183535] Floppy drive(s): fd0 is 1.44M
[    1.190310] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.190344]   alloc irq_desc for 21 on node -1
[    1.190349]   alloc kstat_irqs on node -1
[    1.190361] r8169 0000:02:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.190396] r8169 0000:02:05.0: no PCI Express capability
[    1.191356] eth0: RTL8169sc/8110sc at 0xffffc90000332000, 00:1a:4d:27:13:e2, XID 18000000 IRQ 21
[    1.196990] Initializing USB Mass Storage driver...
[    1.197164] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.197461] usbcore: registered new interface driver usb-storage
[    1.197466] USB Mass Storage support registered.
[    1.197867] usb-storage: device found at 4
[    1.197871] usb-storage: waiting for device to settle before scanning
[    1.203726] FDC 0 is a post-1991 82077
[    1.350039] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.528233] usb 4-1: configuration #1 chosen from 1 choice
[    1.556275] usbcore: registered new interface driver hiddev
[    1.570311] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4
[    1.570424] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.2-1/input0
[    1.570452] usbcore: registered new interface driver usbhid
[    1.570456] usbhid: v2.6:USB HID core driver
[    1.820455] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    2.021244] usb 4-2: configuration #1 chosen from 1 choice
[    2.145251] EXT4-fs (loop0): INFO: recovery required on readonly filesystem
[    2.145260] EXT4-fs (loop0): write access will be enabled during recovery
[    3.261063] EXT4-fs (loop0): orphan cleanup on readonly fs
[    3.261075] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 261180
[    3.261154] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 73
[    3.261220] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 120
[    3.261244] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 118
[    3.261266] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 127
[    3.261288] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 61
[    3.261337] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 169
[    3.261362] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 137
[    3.261384] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 123
[    3.261406] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 175
[    3.261428] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 37
[    3.261452] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 121
[    3.261473] EXT4-fs (loop0): 12 orphan inodes deleted
[    3.261478] EXT4-fs (loop0): recovery complete
[    3.263273] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    6.107535] udev[346]: starting version 163
[    6.196375] usb-storage: device scan complete
[    6.196850] scsi 2:0:0:0: CD-ROM            Samsung  Install Disk     0.10 PQ: 0 ANSI: 0 CCS
[    6.202342] sr1: scsi3-mmc drive: 0x/0x caddy
[    6.202540] sr 2:0:0:0: Attached scsi CD-ROM sr1
[    6.202664] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    6.300709] sr1: Hmm, seems the drive doesn't support multisession CD's
[    6.307715] sr1: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
[    6.308340] sr: Sense Key : Hardware Error [current] 
[    6.308347] sr: Add. Sense: No additional sense information
[    7.471952] lp: driver loaded but no devices found
[    7.507045] intel_rng: FWH not detected
[    7.539126] parport_pc 00:09: reported by Plug and Play ACPI
[    7.539182] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.551425] vga16fb: initializing
[    7.551431] vga16fb: mapped to 0xffff8800000a0000
[    7.551527] fb0: VGA16 VGA frame buffer device
[    7.610585] ppdev: user-space parallel port driver
[    7.620331] lp0: using parport0 (interrupt-driven).
[    7.809787] Linux video capture interface: v2.00
[   10.257776] nvidia: module license 'NVIDIA' taints kernel.
[   10.257781] Disabling lock debugging due to kernel taint
[   11.249256] gspca: main v2.7.0 registered
[   11.493953] gspca: probing 0ac8:303b
[   11.515553] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.515567] nvidia 0000:01:00.0: setting latency timer to 64
[   11.515578] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.516975] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   11.584612] Console: switching to colour frame buffer device 80x30
[   11.874807] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.874849] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.973315] zc3xx: probe sensor -> 000a
[   11.973320] zc3xx: Find Sensor PB0330. Chip revision 0
[   11.977415] gspca: probe ok
[   11.977456] usbcore: registered new interface driver zc3xx
[   11.977462] zc3xx: registered
[   12.039995] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   13.841943] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261112k 
[   14.918851] type=1505 audit(1290561118.985:2):  operation="profile_load" pid=865 name="/usr/share/gdm/guest-session/Xsession"
[   14.939593] type=1505 audit(1290561119.005:3):  operation="profile_load" pid=866 name="/sbin/dhclient3"
[   14.939718] type=1505 audit(1290561119.005:4):  operation="profile_load" pid=866 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.939788] type=1505 audit(1290561119.005:5):  operation="profile_load" pid=866 name="/usr/lib/connman/scripts/dhclient-script"
[   15.420906] type=1505 audit(1290561119.493:6):  operation="profile_load" pid=871 name="/usr/lib/cups/backend/cups-pdf"
[   15.421116] type=1505 audit(1290561119.493:7):  operation="profile_load" pid=871 name="/usr/sbin/cupsd"
[   15.599597] type=1505 audit(1290561119.665:8):  operation="profile_load" pid=886 name="/usr/sbin/tcpdump"
[   16.118122] r8169: eth0: link up
[   20.900103] type=1505 audit(1290561124.973:9):  operation="profile_load" pid=868 name="/usr/bin/evince"
[   20.901508] type=1505 audit(1290561124.973:10):  operation="profile_load" pid=868 name="/usr/bin/evince-previewer"
[   20.902560] type=1505 audit(1290561124.973:11):  operation="profile_load" pid=868 name="/usr/bin/evince-thumbnailer"
[   22.923844] CPU0 attaching NULL sched-domain.
[   22.923852] CPU1 attaching NULL sched-domain.
[   22.990123] CPU0 attaching sched-domain:
[   22.990128]  domain 0: span 0-1 level SIBLING
[   22.990132]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   22.990138]   domain 1: span 0-1 level MC
[   22.990141]    groups: 0-1 (cpu_power = 1178)
[   22.990148] CPU1 attaching sched-domain:
[   22.990150]  domain 0: span 0-1 level SIBLING
[   22.990152]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   22.990158]   domain 1: span 0-1 level MC
[   22.990160]    groups: 0-1 (cpu_power = 1178)
[   23.660597] CPU0 attaching NULL sched-domain.
[   23.660604] CPU1 attaching NULL sched-domain.
[   23.710382] CPU0 attaching sched-domain:
[   23.710387]  domain 0: span 0-1 level SIBLING
[   23.710390]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   23.710397]   domain 1: span 0-1 level MC
[   23.710399]    groups: 0-1 (cpu_power = 1178)
[   23.710406] CPU1 attaching sched-domain:
[   23.710408]  domain 0: span 0-1 level SIBLING
[   23.710411]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   23.710416]   domain 1: span 0-1 level MC
[   23.710419]    groups: 0-1 (cpu_power = 1178)
[   26.300007] eth0: no IPv6 routers present
[   33.050014] wimax0: no IPv6 routers present
[  201.229296] NET: Registered protocol family 24

---

