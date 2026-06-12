---
title: "Unstable Wireless connection"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by 912R on 2009-12-25
After 2 years without Linux I had to go back.. The reason I gave up last time was my unstable Wireless connection in my HP Pavilion laptop. This computer has the famous Broadcom card.
I was thinking that the newest Linux version maybe had fixed this.
I must say that it's more stable than last time. Now The network only crashes 2-3 times in one evening..:P
But still it irritates me enough to maybe force me back to windows..
I would love to find a fix for this problem. It's the only thing that making problem for me with Linux in my laptop.
Maybe some of you have any suggestion if you see a log from my computer or something?

---

### Post by hachre on 2009-12-25
What Broadcom chip exactly do you use? Did you install the "proprietary" driver that Ubuntu suggests?

I'm also interested in this because I also have a Broadcom chip in my MacBook Pro 5,1. The wireless is quite stable but the range is greatly reduced in comparison to Windows/Mac OS. Also the Pings are quite high and the data transfer rate is only 2-3 MB instead of 13-15 MB which I get in Mac OS.

This is the card I have according to "lspci":
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

---

### Post by 912R on 2009-12-25
My output says:

Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

I'm using the driver that the system suggested when I installed it.

And when I'm thinking about it, i seems like it crashes most when I'm away from the computer for a while.

Maybe it has something to do with stand by or something?

---

### Post by hachre on 2009-12-25
> **912R said:**
> My output says:

Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

I'm using the driver that the system suggested when I installed it.

And when I'm thinking about it, i seems like it crashes most when I'm away from the computer for a while.

Maybe it has something to do with stand by or something?

How far away are you from the access point? Maybe you are suffering from the same reduced range problem that I have and you are just close enough to make it barely work

---

### Post by 912R on 2009-12-25
Signal is superstrong.
Less than 10m away from the router..
The network can be seen. It's not possible to make the connection after it has been lost. Then I have to restart the computer and.. -voila works fine for a while.

---

### Post by hachre on 2009-12-25
Once you have lost the network again you can try 'sudo dmesg' and post the output here...

Maybe there's something interesting there.

---

### Post by 912R on 2009-12-27
Ok, here is the output..
If somebody can see something wrong here i would be happy for solutions.

[    0.194211] pci 0000:00:03.0: PME# disabled
[    0.194231] pci 0000:00:05.0: reg 10 32bit mmio: [0xc2000000-0xc2ffffff]
[    0.194238] pci 0000:00:05.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.194245] pci 0000:00:05.0: reg 1c 64bit mmio: [0xc1000000-0xc1ffffff]
[    0.194252] pci 0000:00:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.194462] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.194509] pci 0000:00:0a.1: reg 20 io port: [0x3040-0x307f]
[    0.194516] pci 0000:00:0a.1: reg 24 io port: [0x3000-0x303f]
[    0.194543] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.194549] pci 0000:00:0a.1: PME# disabled
[    0.194585] pci 0000:00:0a.3: reg 10 32bit mmio: [0xc0040000-0xc007ffff]
[    0.194799] pci 0000:00:0b.0: reg 10 32bit mmio: [0xc0004000-0xc0004fff]
[    0.194837] pci 0000:00:0b.0: supports D1 D2
[    0.194840] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194845] pci 0000:00:0b.0: PME# disabled
[    0.194880] pci 0000:00:0b.1: reg 10 32bit mmio: [0xc0005000-0xc00050ff]
[    0.194917] pci 0000:00:0b.1: supports D1 D2
[    0.194920] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.194924] pci 0000:00:0b.1: PME# disabled
[    0.194967] pci 0000:00:0d.0: reg 20 io port: [0x3080-0x308f]
[    0.195016] pci 0000:00:0e.0: reg 10 io port: [0x30b0-0x30b7]
[    0.195022] pci 0000:00:0e.0: reg 14 io port: [0x30a4-0x30a7]
[    0.195028] pci 0000:00:0e.0: reg 18 io port: [0x30a8-0x30af]
[    0.195035] pci 0000:00:0e.0: reg 1c io port: [0x30a0-0x30a3]
[    0.195041] pci 0000:00:0e.0: reg 20 io port: [0x3090-0x309f]
[    0.195047] pci 0000:00:0e.0: reg 24 32bit mmio: [0xc0006000-0xc0006fff]
[    0.195144] pci 0000:00:10.1: reg 10 32bit mmio: [0xc0000000-0xc0003fff]
[    0.195181] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.195186] pci 0000:00:10.1: PME# disabled
[    0.195224] pci 0000:00:14.0: reg 10 32bit mmio: [0xc0007000-0xc0007fff]
[    0.195230] pci 0000:00:14.0: reg 14 io port: [0x30b8-0x30bf]
[    0.195258] pci 0000:00:14.0: supports D1 D2
[    0.195261] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195265] pci 0000:00:14.0: PME# disabled
[    0.195390] pci 0000:01:00.0: reg 10 32bit mmio: [0xc3000000-0xc3003fff]
[    0.195439] pci 0000:01:00.0: supports D1 D2
[    0.195489] pci 0000:00:02.0: bridge 32bit mmio: [0xc3000000-0xc30fffff]
[    0.195533] pci 0000:00:03.0: bridge io port: [0x4000-0x4fff]
[    0.195537] pci 0000:00:03.0: bridge 32bit mmio: [0xc8000000-0xc87fffff]
[    0.195579] pci 0000:03:09.0: reg 10 32bit mmio: [0xc3100000-0xc31007ff]
[    0.195618] pci 0000:03:09.0: supports D1 D2
[    0.195621] pci 0000:03:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195626] pci 0000:03:09.0: PME# disabled
[    0.195656] pci 0000:03:09.1: reg 10 32bit mmio: [0xc3100800-0xc31008ff]
[    0.195695] pci 0000:03:09.1: supports D1 D2
[    0.195698] pci 0000:03:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195703] pci 0000:03:09.1: PME# disabled
[    0.195732] pci 0000:03:09.2: reg 10 32bit mmio: [0xc3100c00-0xc3100cff]
[    0.195771] pci 0000:03:09.2: supports D1 D2
[    0.195774] pci 0000:03:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195779] pci 0000:03:09.2: PME# disabled
[    0.195809] pci 0000:03:09.3: reg 10 32bit mmio: [0xc3101000-0xc31010ff]
[    0.195848] pci 0000:03:09.3: supports D1 D2
[    0.195851] pci 0000:03:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195855] pci 0000:03:09.3: PME# disabled
[    0.195890] pci 0000:00:10.0: transparent bridge
[    0.195895] pci 0000:00:10.0: bridge 32bit mmio: [0xc3100000-0xc31fffff]
[    0.195906] pci_bus 0000:00: on NUMA node 0
[    0.195912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.196065] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.196119] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.196159] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[    0.325580] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.325784] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.325984] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 *11 14 15)
[    0.326120] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.326120] ACPI: PCI Interrupt Link [LK1E] (IRQs 20) *0, disabled.
[    0.326120] ACPI: PCI Interrupt Link [LK2E] (IRQs 19) *10
[    0.326120] ACPI: PCI Interrupt Link [LK3E] (IRQs 21) *10
[    0.326120] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.326120] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[    0.326120] ACPI: PCI Interrupt Link [LSMU] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.326120] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.326120] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[    0.326120] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *11
[    0.326120] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.326254] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.326455] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.326655] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[    0.326865] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *5
[    0.327074] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0
[    0.327299] SCSI subsystem initialized
[    0.328030] libata version 3.00 loaded.
[    0.328061] usbcore: registered new interface driver usbfs
[    0.328061] usbcore: registered new interface driver hub
[    0.328066] usbcore: registered new device driver usb
[    0.328092] ACPI: WMI: Mapper loaded
[    0.328095] PCI: Using ACPI for IRQ routing
[    0.340011] Bluetooth: Core ver 2.15
[    0.344016] NET: Registered protocol family 31
[    0.344019] Bluetooth: HCI device and connection manager initialized
[    0.344022] Bluetooth: HCI socket layer initialized
[    0.344025] NetLabel: Initializing
[    0.344027] NetLabel:  domain hash size = 128
[    0.344030] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.344045] NetLabel:  unlabeled traffic allowed by default
[    0.356016] pnp: PnP ACPI init
[    0.356037] ACPI: bus type pnp registered
[    0.360908] pnp: PnP ACPI: found 11 devices
[    0.360911] ACPI: ACPI bus type pnp unregistered
[    0.360915] PnPBIOS: Disabled by ACPI PNP
[    0.360929] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.360934] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.360938] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.360946] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.360954] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.360958] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.360962] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.360966] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.360970] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.360974] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.360978] system 00:03: ioport range 0x3040-0x307f has been reserved
[    0.360985] system 00:03: ioport range 0x3000-0x303f has been reserved
[    0.360989] system 00:03: ioport range 0x2000-0x203f has been reserved
[    0.360997] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.361001] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.394485] AppArmor: AppArmor Filesystem Enabled
[    0.394537] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.394540] pci 0000:00:02.0:   IO window: disabled
[    0.394545] pci 0000:00:02.0:   MEM window: 0xc3000000-0xc30fffff
[    0.394549] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.394553] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.394556] pci 0000:00:03.0:   IO window: 0x4000-0x4fff
[    0.394561] pci 0000:00:03.0:   MEM window: 0xc8000000-0xc87fffff
[    0.394564] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.394568] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.394571] pci 0000:00:10.0:   IO window: disabled
[    0.394576] pci 0000:00:10.0:   MEM window: 0xc3100000-0xc31fffff
[    0.394580] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.394590] pci 0000:00:02.0: setting latency timer to 64
[    0.394596] pci 0000:00:03.0: setting latency timer to 64
[    0.394602] pci 0000:00:10.0: setting latency timer to 64
[    0.394608] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.394612] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.394616] pci_bus 0000:01: resource 1 mem: [0xc3000000-0xc30fffff]
[    0.394620] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.394624] pci_bus 0000:02: resource 1 mem: [0xc8000000-0xc87fffff]
[    0.394627] pci_bus 0000:03: resource 1 mem: [0xc3100000-0xc31fffff]
[    0.394631] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.394634] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.394679] NET: Registered protocol family 2
[    0.394794] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.395188] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.400034] Switched to high resolution mode on CPU 0
[    0.400054] Switched to high resolution mode on CPU 1
[    0.400080] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.400511] TCP: Hash tables configured (established 131072 bind 65536)
[    0.400515] TCP reno registered
[    0.400625] NET: Registered protocol family 1
[    0.400695] Trying to unpack rootfs image as initramfs...
[    0.678437] Freeing initrd memory: 8011k freed
[    0.684836] Simple Boot Flag at 0x36 set to 0x1
[    0.685096] cpufreq-nforce2: No nForce2 chipset.
[    0.685127] Scanning for low memory corruption every 60 seconds
[    0.685240] audit: initializing netlink socket (disabled)
[    0.685254] type=2000 audit(1261751419.685:1): initialized
[    0.696709] highmem bounce pool size: 64 pages
[    0.696716] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.698528] VFS: Disk quotas dquot_6.5.2
[    0.698608] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.699321] fuse init (API version 7.12)
[    0.699426] msgmni has been set to 1733
[    0.699786] alg: No test for stdrng (krng)
[    0.699805] io scheduler noop registered
[    0.699808] io scheduler anticipatory registered
[    0.699811] io scheduler deadline registered
[    0.699864] io scheduler cfq registered (default)
[    0.699922] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.699950] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.699958] pci 0000:00:05.0: Boot video device
[    0.916148] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.916206] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.916267] pci 0000:00:09.0: Found enabled HT MSI Mapping
[    0.916423]   alloc irq_desc for 24 on node -1
[    0.916427]   alloc kstat_irqs on node -1
[    0.916436] pcieport-driver 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.916443] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.916528]   alloc irq_desc for 25 on node -1
[    0.916531]   alloc kstat_irqs on node -1
[    0.916537] pcieport-driver 0000:00:03.0: irq 25 for MSI/MSI-X
[    0.916542] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.916615] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.916647] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.918583] ACPI: AC Adapter [ADP1] (on-line)
[    0.918666] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.918671] ACPI: Power Button [PWRF]
[    0.918733] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.920481] ACPI: Lid Switch [LID0]
[    0.920536] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.920543] ACPI: Sleep Button [SLPB]
[    0.920598] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    0.920602] ACPI: Power Button [PWRB]
[    0.920937] ACPI: processor limited to max C-state 1
[    0.920990] processor LNXCPU:00: registered as cooling_device0
[    0.920996] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.921095] processor LNXCPU:01: registered as cooling_device1
[    0.921101] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.948018] thermal LNXTHERM:01: registered as thermal_zone0
[    0.948027] ACPI: Thermal Zone [TZS0] (63 C)
[    0.955067] thermal LNXTHERM:02: registered as thermal_zone1
[    0.955077] ACPI: Thermal Zone [TZS1] (66 C)
[    0.955143] isapnp: Scanning for PnP cards...
[    0.994571] ACPI: EC: GPE storm detected, transactions will use polling mode
[    1.308567] isapnp: No Plug & Play device found
[    1.310038] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.311578] brd: module loaded
[    1.312181] loop: module loaded
[    1.312283] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.312566] sata_nv 0000:00:0e.0: version 3.5
[    1.312579] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)
[    1.312938] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[    1.312943]   alloc irq_desc for 23 on node -1
[    1.312946]   alloc kstat_irqs on node -1
[    1.312958] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23
[    1.312962] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.313050] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.313236] scsi0 : sata_nv
[    1.313385] scsi1 : sata_nv
[    1.313562] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 23
[    1.313567] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 23
[    1.313695] pata_amd 0000:00:0d.0: version 0.4.1
[    1.313743] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.313847] scsi2 : pata_amd
[    1.313943] scsi3 : pata_amd
[    1.314575] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    1.314579] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    1.315541] Fixed MDIO Bus: probed
[    1.315585] PPP generic driver version 2.4.2
[    1.315705] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.316062] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    1.316067]   alloc irq_desc for 22 on node -1
[    1.316070]   alloc kstat_irqs on node -1
[    1.316082] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22
[    1.316099] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    1.316103] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    1.316166] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    1.316199] ehci_hcd 0000:00:0b.1: debug port 1
[    1.316204] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    1.316229] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xc0005000
[    1.328068] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    1.328174] usb usb1: configuration #1 chosen from 1 choice
[    1.328213] hub 1-0:1.0: USB hub found
[    1.328223] hub 1-0:1.0: 8 ports detected
[    1.328310] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.328663] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[    1.328668]   alloc irq_desc for 21 on node -1
[    1.328670]   alloc kstat_irqs on node -1
[    1.328681] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 21 (level, high) -> IRQ 21
[    1.328694] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    1.328698] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    1.328747] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    1.328783] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xc0004000
[    1.386142] usb usb2: configuration #1 chosen from 1 choice
[    1.386177] hub 2-0:1.0: USB hub found
[    1.386189] hub 2-0:1.0: 8 ports detected
[    1.386278] uhci_hcd: USB Universal Host Controller Interface driver
[    1.386385] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.386714] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.386800] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.386808] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.386812] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.386816] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.386821] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.386912] mice: PS/2 mouse device common for all mice
[    1.387098] rtc_cmos 00:07: RTC can wake from S4
[    1.387141] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.387177] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.387305] device-mapper: uevent: version 1.0.3
[    1.387443] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.387630] device-mapper: multipath: version 1.1.0 loaded
[    1.387634] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.387844] EISA: Probing bus 0 at eisa.0
[    1.387851] Cannot allocate resource for EISA slot 1
[    1.387854] Cannot allocate resource for EISA slot 2
[    1.387857] Cannot allocate resource for EISA slot 3
[    1.387860] Cannot allocate resource for EISA slot 4
[    1.387875] EISA: Detected 0 cards.
[    1.388103] cpuidle: using governor ladder
[    1.388106] cpuidle: using governor menu
[    1.388726] TCP cubic registered
[    1.388962] NET: Registered protocol family 10
[    1.389539] lo: Disabled Privacy Extensions
[    1.389636] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.389976] NET: Registered protocol family 17
[    1.390002] Bluetooth: L2CAP ver 2.13
[    1.390004] Bluetooth: L2CAP socket layer initialized
[    1.390007] Bluetooth: SCO (Voice Link) ver 0.6
[    1.390010] Bluetooth: SCO socket layer initialized
[    1.390064] Bluetooth: RFCOMM TTY layer initialized
[    1.390068] Bluetooth: RFCOMM socket layer initialized
[    1.390071] Bluetooth: RFCOMM ver 1.11
[    1.390094] powernow-k8: Found 1 AMD Turion(tm) 64 X2  processors (2 cpu cores) (version 2.20.00)
[    1.390137] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[    1.390141] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    1.390231] Using IPI No-Shortcut mode
[    1.390316] PM: Resume from disk failed.
[    1.390331] registered taskstats version 1
[    1.390498]   Magic number: 5:877:536
[    1.390514] bdi 1:14: hash matches
[    1.390613] rtc_cmos 00:07: setting system clock to 2009-12-25 14:30:20 UTC (1261751420)
[    1.390617] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.390619] EDD information not available.
[    1.468099] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.479506] ata1.00: ATA-7: WDC WD800BEVS-60LAT0, 01.06M01, max UDMA/100
[    1.479510] ata1.00: 156301488 sectors, multi 16: LBA48 
[    1.492315] ata1.00: configured for UDMA/100
[    1.888077] usb 2-5: new low speed USB device using ohci_hcd and address 2
[    1.980208] ACPI: Battery Slot [BAT0] (battery present)
[    1.980437] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVS-60 01.0 PQ: 0 ANSI: 5
[    1.980597] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.980639] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.980693] sd 0:0:0:0: [sda] Write Protect is off
[    1.980697] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.980725] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.980871]  sda:
[    1.991595] ata2: SATA link down (SStatus 0 SControl 300)
[    2.033579]  sda1 sda2 < sda5 >
[    2.068751] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.102214] usb 2-5: configuration #1 chosen from 1 choice
[    2.176368] ata4.00: ATAPI: SONY     DVD RW DW-G520A, GPSD, max MWDMA2
[    2.176399] ata4: nv_mode_filter: 0x39f&0xfff9f->0x39f, BIOS=0x0 (0x0) ACPI=0x1 (600:600:0x10)
[    2.216321] ata4.00: configured for MWDMA2
[    2.219386] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DW-G520A  GPSD PQ: 0 ANSI: 5
[    2.228896] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.228900] Uniform CD-ROM driver Revision: 3.20
[    2.229029] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.229097] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.229145] Freeing unused kernel memory: 540k freed
[    2.229636] Write protecting the kernel text: 4568k
[    2.229687] Write protecting the kernel read-only data: 1836k
[    2.422271] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.422649] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    2.422656]   alloc irq_desc for 20 on node -1
[    2.422659]   alloc kstat_irqs on node -1
[    2.422672] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    2.422678] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.422724] nv_probe: set workaround bit for reversed mac addr
[    2.428298] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/input/input6
[    2.428342] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.501939] usbcore: registered new interface driver hiddev
[    2.533501] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    2.533509]   alloc irq_desc for 19 on node -1
[    2.533512]   alloc kstat_irqs on node -1
[    2.533525] ohci1394 0000:03:09.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, high) -> IRQ 19
[    2.534469] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/input/input7
[    2.534571] generic-usb 0003:046D:C521.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:0b.0-5/input0
[    2.548260] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.1/input/input8
[    2.548381] generic-usb 0003:046D:C521.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:0b.0-5/input1
[    2.548404] usbcore: registered new interface driver usbhid
[    2.548409] usbhid: v2.6:USB HID core driver
[    2.590092] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[c3100000-c31007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.942060] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:16:d3:07:39:f1
[    2.942066] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    3.563082] xor: automatically using best checksumming function: pIII_sse
[    3.581017]    pIII_sse  :  4870.000 MB/sec
[    3.581021] xor: using function: pIII_sse (4870.000 MB/sec)
[    3.584428] device-mapper: dm-raid45: initialized v0.2594b
[    3.854828] PM: Starting manual resume from disk
[    3.854834] PM: Resume from partition 8:5
[    3.854837] PM: Checking hibernation image.
[    3.855059] PM: Resume from disk failed.
[    3.873383] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[06e40a002a145029]
[    3.885654] EXT4-fs (sda1): barriers enabled
[    3.911373] kjournald2 starting: pid 420, dev sda1:8, commit interval 5 seconds
[    3.911390] EXT4-fs (sda1): delayed allocation enabled
[    3.911394] EXT4-fs: file extents enabled
[    3.920457] EXT4-fs: mballoc enabled
[    3.920476] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.846588] Adding 2811332k swap on /dev/sda5.  Priority:-1 extents:1 across:2811332k 
[    6.393132] EXT4-fs (sda1): internal journal on sda1:8
[    7.262873] udev: starting version 147
[    8.861030] Linux agpgart interface v0.103
[   10.364835] nvidia: module license 'NVIDIA' taints kernel.
[   10.364842] Disabling lock debugging due to kernel taint
[   10.373891] lib80211: common routines for IEEE802.11 drivers
[   10.373896] lib80211_crypt: registered algorithm 'NULL'
[   10.374825] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.439714] sdhci: Secure Digital Host Controller Interface driver
[   10.439719] sdhci: Copyright(c) Pierre Ossman
[   10.449723] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 19)
[   10.450080] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[   10.450086]   alloc irq_desc for 18 on node -1
[   10.450089]   alloc kstat_irqs on node -1
[   10.450102] sdhci-pci 0000:03:09.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, high) -> IRQ 18
[   10.452171] Registered led device: mmc0::
[   10.453233] mmc0: SDHCI controller on PCI [0000:03:09.1] using PIO
[   10.622014] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
[   10.622023] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 21 (level, high) -> IRQ 21
[   10.622030] nvidia 0000:00:05.0: setting latency timer to 64
[   10.622325] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.13  Thu Jun 25 18:42:21 PDT 2009
[   10.627759] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   10.627786] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   10.707708] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.784301] lp: driver loaded but no devices found
[   11.256650] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
[   11.256659] wl 0000:01:00.0: PCI INT A -> Link[LK2E] -> GSI 19 (level, high) -> IRQ 19
[   11.256666] wl 0000:01:00.0: setting latency timer to 64
[   11.289072] lib80211_crypt: registered algorithm 'TKIP'
[   11.289248] eth1: Broadcom BCM4312 802.11 Wireless Controller 5.10.91.9
[   11.297287] udev: renamed network interface eth1 to eth2
[   11.881834] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   11.913882] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   14.134931] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   14.134939]   alloc irq_desc for 17 on node -1
[   14.134942]   alloc kstat_irqs on node -1
[   14.134955] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 17 (level, high) -> IRQ 17
[   14.135006] HDA Intel 0000:00:10.1: setting latency timer to 64
[   14.492018] eth0: no link during initialization.
[   14.492561] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.349057] eth2: no IPv6 routers present
[   26.189054] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x012f000c
[   27.093017] ppdev: user-space parallel port driver
[   34.996064] ACPI: EC: missing confirmations, switch off interrupt mode.
[   91.397055] Clocksource tsc unstable (delta = -184927917 ns)
[17672.588125] usb 1-6: new high speed USB device using ehci_hcd and address 3
[17672.827636] usb 1-6: configuration #1 chosen from 1 choice
[17673.619348] Initializing USB Mass Storage driver...
[17673.620147] scsi4 : SCSI emulation for USB Mass Storage devices
[17673.620408] usbcore: registered new interface driver usb-storage
[17673.620417] USB Mass Storage support registered.
[17673.620677] usb-storage: device found at 3
[17673.620682] usb-storage: waiting for device to settle before scanning
[17674.543831] usb 1-6: USB disconnect, address 3
[17674.925097] usb 1-6: new high speed USB device using ehci_hcd and address 4
[17675.162400] usb 1-6: configuration #1 chosen from 1 choice
[17675.165535] scsi5 : SCSI emulation for USB Mass Storage devices
[17675.165838] usb-storage: device found at 4
[17675.165845] usb-storage: waiting for device to settle before scanning
[17690.164337] usb-storage: device scan complete
[17690.166011] scsi 5:0:0:0: Direct-Access     WDC WD50 00AAKS-00YGA0    12.0 PQ: 0 ANSI: 0
[17690.167267] sd 5:0:0:0: Attached scsi generic sg2 type 0
[17690.172374] sd 5:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[17690.181859] sd 5:0:0:0: [sdb] Write Protect is off
[17690.181872] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[17690.181880] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[17690.185808] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[17690.185833]  sdb: sdb1
[17690.199809] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[17690.199824] sd 5:0:0:0: [sdb] Attached SCSI disk
[18301.548658] usb 1-6: USB disconnect, address 4
[75693.192544] hda-intel: Too big adjustment 32
[75693.254090] hda-intel: Too big adjustment 32
[117534.246503] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

---

