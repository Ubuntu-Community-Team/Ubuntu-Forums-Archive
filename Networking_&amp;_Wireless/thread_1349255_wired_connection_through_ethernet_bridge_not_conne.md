---
title: "wired connection through ethernet bridge not connecting"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by Dionysian on 2009-12-08
i just installed 9.10 on my desktop and i'm not getting an internet connection.  i'm using an ethernet bridge (WET54G), which then goes to my router (WRT54G).  i've had both for a few years and i've become pretty accustomed to their workings.  in the past, i've run both xp and osx through both without any trouble, only having to make sure that each, the bridge and the router, were synced up, but after installing 9.10, i cannot get it to recognize an internet connection.

i've been looking through a number of the threads, and the 9.10 manual, and cannot seem to find anything that works.  in an effort to minimize damage, i will include the results of a few code results first off.


sudo /sbin/ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:50:37:bb  
          inet6 addr: fe80::213:d3ff:fe50:37bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48834 (48.8 KB)  TX bytes:2520 (2.5 KB)
          Interrupt:20 Base address:0xdd00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:50:37:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:dd00(size=256) memory:fcffe000-fcffe0ff memory:fde00000-fde0ffff(prefetchable)

```

dmesg
```
[    0.152613]   groups: 0 1
[    0.152619] CPU1 attaching sched-domain:
[    0.152621]  domain 0: span 0-1 level MC
[    0.152624]   groups: 1 0
[    0.152695] Booting paravirtualized kernel on bare hardware
[    0.152695] regulator: core version 0.5
[    0.152695] Time:  6:59:39  Date: 12/08/09
[    0.152695] NET: Registered protocol family 16
[    0.152695] EISA bus registered
[    0.152695] ACPI: bus type pci registered
[    0.152695] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.152695] PCI: MCFG area at e0000000 reserved in E820
[    0.152695] PCI: Using MMCONFIG for extended config space
[    0.152695] PCI: Using configuration type 1 for base access
[    0.153238] bio: create slab <bio-0> at 0
[    0.153238] ACPI: EC: Look up EC in DSDT
[    0.159138] ACPI: Interpreter enabled
[    0.159143] ACPI: (supports S0 S1 S3 S4 S5)
[    0.159166] ACPI: Using IOAPIC for interrupt routing
[    0.162518] ACPI: No dock devices found.
[    0.162620] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.162678] pci 0000:00:00.0: reg 18 io port: [0x4100-0x411f]
[    0.162686] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.162732] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.162736] pci 0000:00:02.0: PME# disabled
[    0.162819] pci 0000:00:12.0: reg 10 io port: [0xfe00-0xfe07]
[    0.162829] pci 0000:00:12.0: reg 14 io port: [0xfd00-0xfd03]
[    0.162838] pci 0000:00:12.0: reg 18 io port: [0xfc00-0xfc07]
[    0.162847] pci 0000:00:12.0: reg 1c io port: [0xfb00-0xfb03]
[    0.162856] pci 0000:00:12.0: reg 20 io port: [0xfa00-0xfa0f]
[    0.162866] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f1ff]
[    0.162875] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.162910] pci 0000:00:12.0: supports D1 D2
[    0.162961] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.163074] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.163196] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.163270] pci 0000:00:13.2: supports D1 D2
[    0.163272] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.163278] pci 0000:00:13.2: PME# disabled
[    0.163335] pci 0000:00:14.0: reg 10 io port: [0x500-0x50f]
[    0.163344] pci 0000:00:14.0: reg 14 32bit mmio: [0xfe02b000-0xfe02b3ff]
[    0.163383] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.163451] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.163460] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.163470] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.163479] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.163488] pci 0000:00:14.1: reg 20 io port: [0xf800-0xf80f]
[    0.163688] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe02a000-0xfe02a0ff]
[    0.163898] pci 0000:01:00.0: reg 10 32bit mmio: [0xf6000000-0xf6ffffff]
[    0.163908] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.163918] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf4000000-0xf5ffffff]
[    0.163924] pci 0000:01:00.0: reg 24 io port: [0xef00-0xef7f]
[    0.163931] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.164032] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.164036] pci 0000:00:02.0: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.164041] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.164109] pci 0000:02:00.0: reg 10 32bit mmio: [0xf9000000-0xf9ffffff]
[    0.164252] pci 0000:02:00.1: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.164385] pci 0000:02:00.2: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.164532] pci 0000:02:01.0: reg 10 32bit mmio: [0xfcfff000-0xfcfff0ff]
[    0.164543] pci 0000:02:01.0: reg 14 io port: [0xdf00-0xdf07]
[    0.164554] pci 0000:02:01.0: reg 18 io port: [0xde00-0xdeff]
[    0.164619] pci 0000:02:01.0: supports D2
[    0.164622] pci 0000:02:01.0: PME# supported from D2 D3hot D3cold
[    0.164628] pci 0000:02:01.0: PME# disabled
[    0.164688] pci 0000:02:03.0: reg 10 io port: [0xdd00-0xddff]
[    0.164699] pci 0000:02:03.0: reg 14 32bit mmio: [0xfcffe000-0xfcffe0ff]
[    0.164742] pci 0000:02:03.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.164775] pci 0000:02:03.0: supports D1 D2
[    0.164777] pci 0000:02:03.0: PME# supported from D1 D2 D3hot D3cold
[    0.164783] pci 0000:02:03.0: PME# disabled
[    0.164843] pci 0000:02:04.0: reg 10 32bit mmio: [0xfcffd000-0xfcffd7ff]
[    0.164854] pci 0000:02:04.0: reg 14 io port: [0xdc00-0xdc7f]
[    0.164929] pci 0000:02:04.0: supports D2
[    0.164931] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.164938] pci 0000:02:04.0: PME# disabled
[    0.165005] pci 0000:00:14.4: transparent bridge
[    0.165014] pci 0000:00:14.4: bridge io port: [0xd000-0xdfff]
[    0.165020] pci 0000:00:14.4: bridge 32bit mmio: [0xf9000000-0xfcffffff]
[    0.165027] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfde00000-0xfdefffff]
[    0.165040] pci_bus 0000:00: on NUMA node 0
[    0.165045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.165206] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.178761] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178851] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.178938] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.179026] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.179114] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[    0.179200] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[    0.179287] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
[    0.179374] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.179554] SCSI subsystem initialized
[    0.179599] libata version 3.00 loaded.
[    0.179599] usbcore: registered new interface driver usbfs
[    0.179599] usbcore: registered new interface driver hub
[    0.179599] usbcore: registered new device driver usb
[    0.179599] ACPI: WMI: Mapper loaded
[    0.179599] PCI: Using ACPI for IRQ routing
[    0.179599] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.179599] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.192008] Bluetooth: Core ver 2.15
[    0.192024] NET: Registered protocol family 31
[    0.192024] Bluetooth: HCI device and connection manager initialized
[    0.192024] Bluetooth: HCI socket layer initialized
[    0.192024] NetLabel: Initializing
[    0.192024] NetLabel:  domain hash size = 128
[    0.192024] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.192039] NetLabel:  unlabeled traffic allowed by default
[    0.204016] pnp: PnP ACPI init
[    0.204038] ACPI: bus type pnp registered
[    0.206423] pnp 00:0b: mem resource (0xf0000-0xf3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206427] pnp 00:0b: mem resource (0xf4000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206431] pnp 00:0b: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206435] pnp 00:0b: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206440] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206444] pnp 00:0b: mem resource (0x100000-0x7feeffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.206504] pnp: PnP ACPI: found 12 devices
[    0.206506] ACPI: ACPI bus type pnp unregistered
[    0.206510] PnPBIOS: Disabled by ACPI PNP
[    0.206523] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.206526] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.206530] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.206533] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.206536] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.206539] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.206543] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.206546] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.206549] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.206552] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.206555] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.206563] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.206566] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.206574] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.206580] system 00:0b: iomem range 0x7ff00000-0x7fffffff could not be reserved
[    0.206584] system 00:0b: iomem range 0x7fef0000-0x7fefffff could not be reserved
[    0.206587] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.206591] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.206595] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.206598] system 00:0b: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.241288] AppArmor: AppArmor Filesystem Enabled
[    0.241323] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.241326] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.241331] pci 0000:00:02.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.241335] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.241341] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.241345] pci 0000:00:14.4:   IO window: 0xd000-0xdfff
[    0.241352] pci 0000:00:14.4:   MEM window: 0xf9000000-0xfcffffff
[    0.241358] pci 0000:00:14.4:   PREFETCH window: 0xfde00000-0xfdefffff
[    0.241371] pci 0000:00:02.0: setting latency timer to 64
[    0.241382] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.241385] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.241388] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.241391] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xf7ffffff]
[    0.241394] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.241398] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.241400] pci_bus 0000:02: resource 1 mem: [0xf9000000-0xfcffffff]
[    0.241403] pci_bus 0000:02: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.241406] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.241409] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.241450] NET: Registered protocol family 2
[    0.241554] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.241933] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.242804] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.243288] TCP: Hash tables configured (established 131072 bind 65536)
[    0.243291] TCP reno registered
[    0.243406] NET: Registered protocol family 1
[    0.243481] Trying to unpack rootfs image as initramfs...
[    0.244034] Switched to high resolution mode on CPU 0
[    0.244570] Switched to high resolution mode on CPU 1
[    0.458044] Freeing initrd memory: 7450k freed
[    0.465140] cpufreq-nforce2: No nForce2 chipset.
[    0.465169] Scanning for low memory corruption every 60 seconds
[    0.465287] audit: initializing netlink socket (disabled)
[    0.465305] type=2000 audit(1260255579.464:1): initialized
[    0.474563] highmem bounce pool size: 64 pages
[    0.474569] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.476270] VFS: Disk quotas dquot_6.5.2
[    0.476333] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.476984] fuse init (API version 7.12)
[    0.477072] msgmni has been set to 1705
[    0.477350] alg: No test for stdrng (krng)
[    0.477375] io scheduler noop registered
[    0.477377] io scheduler anticipatory registered
[    0.477380] io scheduler deadline registered
[    0.477428] io scheduler cfq registered (default)
[    0.477437] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.532058] pci 0000:01:00.0: Boot video device
[    0.532161] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.532221] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.532246] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.532382] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.532386] ACPI: Power Button [PWRF]
[    0.532439] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.532442] ACPI: Power Button [PWRB]
[    0.532681] processor LNXCPU:00: registered as cooling_device0
[    0.532684] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.532797] processor LNXCPU:01: registered as cooling_device1
[    0.532803] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.534446] isapnp: Scanning for PnP cards...
[    0.888699] isapnp: No Plug & Play device found
[    0.889929] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.891225] brd: module loaded
[    0.891704] loop: module loaded
[    0.891778] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.891932] sata_sil 0000:00:12.0: version 2.4
[    0.891975]   alloc irq_desc for 22 on node -1
[    0.891977]   alloc kstat_irqs on node -1
[    0.891986] sata_sil 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.892106] scsi0 : sata_sil
[    0.892223] scsi1 : sata_sil
[    0.892339] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 22
[    0.892344] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 22
[    0.892528]   alloc irq_desc for 16 on node -1
[    0.892530]   alloc kstat_irqs on node -1
[    0.892534] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.892656] scsi2 : pata_atiixp
[    0.892731] scsi3 : pata_atiixp
[    0.893780] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf800 irq 14
[    0.893784] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf808 irq 15
[    0.894497] Fixed MDIO Bus: probed
[    0.894537] PPP generic driver version 2.4.2
[    0.894641] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.894660]   alloc irq_desc for 19 on node -1
[    0.894662]   alloc kstat_irqs on node -1
[    0.894667] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.894680] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.894738] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.894805] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[    0.904029] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.904127] usb usb1: configuration #1 chosen from 1 choice
[    0.904159] hub 1-0:1.0: USB hub found
[    0.904168] hub 1-0:1.0: 8 ports detected
[    0.904256] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.904271] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.904281] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.904313] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.904330] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[    0.964060] usb usb2: configuration #1 chosen from 1 choice
[    0.964088] hub 2-0:1.0: USB hub found
[    0.964100] hub 2-0:1.0: 4 ports detected
[    0.964163] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.964173] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.964212] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.964229] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[    1.020064] usb usb3: configuration #1 chosen from 1 choice
[    1.020095] hub 3-0:1.0: USB hub found
[    1.020106] hub 3-0:1.0: 4 ports detected
[    1.020172] uhci_hcd: USB Universal Host Controller Interface driver
[    1.020260] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.023265] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.023271] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.023334] mice: PS/2 mouse device common for all mice
[    1.023427] rtc_cmos 00:03: RTC can wake from S4
[    1.023463] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.023493] rtc0: alarms up to one month, 242 bytes nvram
[    1.023598] device-mapper: uevent: version 1.0.3
[    1.023712] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.023847] device-mapper: multipath: version 1.1.0 loaded
[    1.023850] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.024006] EISA: Probing bus 0 at eisa.0
[    1.024030] Cannot allocate resource for EISA slot 4
[    1.024050] EISA: Detected 0 cards.
[    1.024209] cpuidle: using governor ladder
[    1.024211] cpuidle: using governor menu
[    1.024718] TCP cubic registered
[    1.024890] NET: Registered protocol family 10
[    1.025368] lo: Disabled Privacy Extensions
[    1.025691] NET: Registered protocol family 17
[    1.025709] Bluetooth: L2CAP ver 2.13
[    1.025711] Bluetooth: L2CAP socket layer initialized
[    1.025714] Bluetooth: SCO (Voice Link) ver 0.6
[    1.025716] Bluetooth: SCO socket layer initialized
[    1.025758] Bluetooth: RFCOMM TTY layer initialized
[    1.025762] Bluetooth: RFCOMM socket layer initialized
[    1.025764] Bluetooth: RFCOMM ver 1.11
[    1.025785] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (2 cpu cores) (version 2.20.00)
[    1.025833] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x8
[    1.025835] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xa
[    1.025838] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[    1.025915] Using IPI No-Shortcut mode
[    1.026005] PM: Resume from disk failed.
[    1.026019] registered taskstats version 1
[    1.026160]   Magic number: 5:713:973
[    1.026268] rtc_cmos 00:03: setting system clock to 2009-12-08 06:59:40 UTC (1260255580)
[    1.026271] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.026273] EDD information not available.
[    1.042579] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.212060] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.220331] ata1.00: ATA-7: HDT722525DLA380, V44OA80A, max UDMA/100
[    1.220334] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.236327] ata1.00: configured for UDMA/100
[    1.236446] scsi 0:0:0:0: Direct-Access     ATA      HDT722525DLA380  V44O PQ: 0 ANSI: 5
[    1.236577] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.236616] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.236664] sd 0:0:0:0: [sda] Write Protect is off
[    1.236667] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.236691] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.236824]  sda: sda1 sda2 < sda5 >
[    1.277530] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.328031] usb 1-7: new high speed USB device using ehci_hcd and address 3
[    1.460988] usb 1-7: configuration #1 chosen from 1 choice
[    1.556042] ata2: SATA link down (SStatus 0 SControl 300)
[    1.728692] ata4.00: ATAPI: HP      DVD Writer 740b, ED24, max UDMA/33
[    1.728721] ata4.01: ATAPI: IDE-DVD DROM6216, HD08, max UDMA/100
[    1.728741] ata4.01: limited to UDMA/33 due to 40-wire cable
[    1.744618] ata4.00: configured for UDMA/33
[    1.760525] ata4.01: configured for UDMA/33
[    1.764169] scsi 3:0:0:0: CD-ROM            HP       DVD Writer 740b  ED24 PQ: 0 ANSI: 5
[    1.769453] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.769456] Uniform CD-ROM driver Revision: 3.20
[    1.769546] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.769591] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.770353] scsi 3:0:1:0: CD-ROM            IDE-DVD  DROM6216         HD08 PQ: 0 ANSI: 5
[    1.773951] sr1: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    1.774020] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    1.774062] sr 3:0:1:0: Attached scsi generic sg2 type 5
[    1.774106] Freeing unused kernel memory: 540k freed
[    1.774549] Write protecting the kernel text: 4568k
[    1.774591] Write protecting the kernel read-only data: 1836k
[    1.881165] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    1.901418] Linux agpgart interface v0.103
[    1.984132] ohci1394 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.988961] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.003432] Initializing USB Mass Storage driver...
[    2.003568] scsi4 : SCSI emulation for USB Mass Storage devices
[    2.003665] usbcore: registered new interface driver usb-storage
[    2.003670] USB Mass Storage support registered.
[    2.003812] usb-storage: device found at 3
[    2.003814] usb-storage: waiting for device to settle before scanning
[    2.046070] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fcffd000-fcffd7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.051458] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.054217] 8139too Fast Ethernet driver 0.9.28
[    2.054266]   alloc irq_desc for 20 on node -1
[    2.054268]   alloc kstat_irqs on node -1
[    2.054276] 8139too 0000:02:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.055872] eth0: RealTek RTL8139 at 0xdd00, 00:13:d3:50:37:bb, IRQ 20
[    2.098157] usb 2-2: configuration #1 chosen from 1 choice
[    2.108093] usbcore: registered new interface driver hiddev
[    2.112215] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input4
[    2.112309] generic-usb 0003:046D:C51A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-2/input0
[    2.121187] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.1/input/input5
[    2.121297] generic-usb 0003:046D:C51A.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-2/input1
[    2.121317] usbcore: registered new interface driver usbhid
[    2.121321] usbhid: v2.6:USB HID core driver
[    2.409032] usb 3-4: new full speed USB device using ohci_hcd and address 2
[    2.621154] usb 3-4: configuration #1 chosen from 1 choice
[    2.623340] scsi5 : SCSI emulation for USB Mass Storage devices
[    2.623630] usb-storage: device found at 2
[    2.623632] usb-storage: waiting for device to settle before scanning
[    3.123305] PM: Starting manual resume from disk
[    3.123310] PM: Resume from partition 8:5
[    3.123312] PM: Checking hibernation image.
[    3.123473] PM: Resume from disk failed.
[    3.162381] EXT4-fs (sda1): barriers enabled
[    3.187351] kjournald2 starting: pid 386, dev sda1:8, commit interval 5 seconds
[    3.187372] EXT4-fs (sda1): delayed allocation enabled
[    3.187376] EXT4-fs: file extents enabled
[    3.219423] EXT4-fs: mballoc enabled
[    3.219440] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.341293] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000b4cdcf]
[    3.761871] type=1505 audit(1260255583.234:2): operation="profile_load" pid=409 name=/usr/share/gdm/guest-session/Xsession
[    3.764334] type=1505 audit(1260255583.234:3): operation="profile_load" pid=410 name=/sbin/dhclient3
[    3.764636] type=1505 audit(1260255583.234:4): operation="profile_load" pid=410 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.764804] type=1505 audit(1260255583.234:5): operation="profile_load" pid=410 name=/usr/lib/connman/scripts/dhclient-script
[    3.794911] type=1505 audit(1260255583.266:6): operation="profile_load" pid=411 name=/usr/bin/evince
[    3.799933] type=1505 audit(1260255583.270:7): operation="profile_load" pid=411 name=/usr/bin/evince-previewer
[    3.802897] type=1505 audit(1260255583.274:8): operation="profile_load" pid=411 name=/usr/bin/evince-thumbnailer
[    3.818553] type=1505 audit(1260255583.290:9): operation="profile_load" pid=413 name=/usr/lib/cups/backend/cups-pdf
[    3.818922] type=1505 audit(1260255583.290:10): operation="profile_load" pid=413 name=/usr/sbin/cupsd
[    4.706881] Adding 6032368k swap on /dev/sda5.  Priority:-1 extents:1 across:6032368k 
[    4.956491] EXT4-fs (sda1): internal journal on sda1:8
[    5.755526] udev: starting version 147
[    6.954087] lp: driver loaded but no devices found
[    6.977871] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x500, revision 0
[    7.004211] usb-storage: device scan complete
[    7.004693] scsi 4:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
[    7.004885] Linux video capture interface: v2.00
[    7.005131] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    7.010436] sd 4:0:0:0: [sdb] 2048000 512-byte logical blocks: (1.04 GB/1000 MiB)
[    7.011436] sd 4:0:0:0: [sdb] Write Protect is off
[    7.011441] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[    7.011444] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.013440] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.013444]  sdb: sdb1
[    7.019828] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    7.019837] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.621148] usb-storage: device scan complete
[    7.627084] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    7.633081] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    7.639080] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    7.645079] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    7.645513] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    7.645622] sd 5:0:0:1: Attached scsi generic sg5 type 0
[    7.645726] sd 5:0:0:2: Attached scsi generic sg6 type 0
[    7.645838] sd 5:0:0:3: Attached scsi generic sg7 type 0
[    7.724909] nvidia: module license 'NVIDIA' taints kernel.
[    7.724915] Disabling lock debugging due to kernel taint
[    7.742096] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    7.752076] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[    7.783097] sd 5:0:0:2: [sde] Attached SCSI removable disk
[    7.803074] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[    7.981252]   alloc irq_desc for 18 on node -1
[    7.981256]   alloc kstat_irqs on node -1
[    7.981265] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.981274] nvidia 0000:01:00.0: setting latency timer to 64
[    7.981571] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.42  Tue Oct 20 20:18:32 PDT 2009
[    8.658097] parport_pc 00:07: reported by Plug and Play ACPI
[    8.658148] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[    8.753188] lp0: using parport0 (interrupt-driven).
[    8.893289] ppdev: user-space parallel port driver
[    8.982618] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.017365] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[    9.017755] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
[    9.017759] cx88[0]: TV tuner type 76, Radio tuner type -1
[    9.024266] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[    9.024366] psmouse serio1: ID: 10 00 64
[    9.097682] cx2388x alsa driver version 0.0.7 loaded
[    9.097766] logips2pp: Detected unknown logitech mouse model 127
[    9.324181]   alloc irq_desc for 17 on node -1
[    9.324186]   alloc kstat_irqs on node -1
[    9.324196] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.354985] tuner 1-0064: chip found @ 0xc8 (cx88[0])
[    9.514702] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[    9.573315] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input6
[    9.587065] xc5000 1-0064: creating new instance
[    9.588268] xc5000: Successfully identified at address 0x64
[    9.588270] xc5000: Firmware has not been loaded previously
[    9.588276] cx88[0]: Calling XC5000 callback
[    9.588348] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:14.4/0000:02:00.2/input/input7
[    9.588401] cx88[0]/2: cx2388x 8802 Driver Manager
[    9.588421] cx88-mpeg driver manager 0000:02:00.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    9.588434] cx88[0]/2: found at 0000:02:00.2, rev: 5, irq: 20, latency: 64, mmio: 0xfa000000
[    9.588441] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.589382] cx8800 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    9.589395] cx88[0]/0: found at 0000:02:00.0, rev: 5, irq: 20, latency: 64, mmio: 0xf9000000
[    9.589410] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.589474] cx88[0]/0: registered device video0 [v4l2]
[    9.589500] cx88[0]/0: registered device vbi0
[    9.591963] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[    9.591968] cx88-mpeg driver manager 0000:02:00.2: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[    9.790432] xc5000: firmware read 12401 bytes.
[    9.790436] xc5000: firmware uploading...
[    9.790440] cx88[0]: Calling XC5000 callback
[   10.007044] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   10.007048] cx88/2: registering cx8802 driver, type: dvb access: shared
[   10.007052] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   10.007056] cx88[0]/2: cx2388x based DVB/ATSC card
[   10.007058] cx8802_alloc_frontends() allocating 1 frontend(s)
[   11.547766] xc5000 1-0064: attaching existing instance
[   11.573728] xc5000: Successfully identified at address 0x64
[   11.573732] xc5000: Firmware has not been loaded previously
[   11.599496] cx88[0]: Calling XC5000 callback
[   11.600315] DVB: registering new adapter (cx88[0])
[   11.600319] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   12.380019] xc5000: firmware upload complete...
[   13.030481] cx88_audio 0000:02:00.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   13.030495] IRQ 20/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   13.030521] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   13.074937] __ratelimit: 3 callbacks suppressed
[   13.074942] type=1505 audit(1260255592.545:12): operation="profile_replace" pid=1103 name=/usr/share/gdm/guest-session/Xsession
[   13.079002] type=1505 audit(1260255592.549:13): operation="profile_replace" pid=1106 name=/sbin/dhclient3
[   13.079304] type=1505 audit(1260255592.549:14): operation="profile_replace" pid=1106 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   13.079475] type=1505 audit(1260255592.549:15): operation="profile_replace" pid=1106 name=/usr/lib/connman/scripts/dhclient-script
[   13.085139] type=1505 audit(1260255592.557:16): operation="profile_replace" pid=1107 name=/usr/bin/evince
[   13.091100] type=1505 audit(1260255592.561:17): operation="profile_replace" pid=1107 name=/usr/bin/evince-previewer
[   13.094282] type=1505 audit(1260255592.565:18): operation="profile_replace" pid=1107 name=/usr/bin/evince-thumbnailer
[   13.101877] type=1505 audit(1260255592.573:19): operation="profile_replace" pid=1115 name=/usr/lib/cups/backend/cups-pdf
[   13.102250] type=1505 audit(1260255592.573:20): operation="profile_replace" pid=1115 name=/usr/sbin/cupsd
[   13.104372] type=1505 audit(1260255592.577:21): operation="profile_replace" pid=1116 name=/usr/sbin/tcpdump
[   20.080024] eth0: no IPv6 routers present
[   78.744028] Clocksource tsc unstable (delta = -251318540 ns)
[ 1601.416077] usb 1-7: USB disconnect, address 3
[ 2436.556038] usb 1-7: new high speed USB device using ehci_hcd and address 5
[ 2436.686113] usb 1-7: configuration #1 chosen from 1 choice
[ 2436.700423] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2436.702515] usb-storage: device found at 5
[ 2436.702522] usb-storage: waiting for device to settle before scanning
[ 2441.700324] usb-storage: device scan complete
[ 2441.700862] scsi 6:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
[ 2441.701688] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 2441.710548] sd 6:0:0:0: [sdb] 2048000 512-byte logical blocks: (1.04 GB/1000 MiB)
[ 2441.712213] sd 6:0:0:0: [sdb] Write Protect is off
[ 2441.712223] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 2441.712229] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2441.717687] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2441.717699]  sdb: sdb1
[ 2441.723386] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2441.723399] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

Any help would be much appreciated. :confused:

---

### Post by bayvista on 2009-12-08
Go back to 9.04.
9.10 has a network bug.

---

### Post by Iowan on 2009-12-08
I'm not familiar with your bridge - so please forgive (or ignore) stupid questions/suggestions...
Does the bridge provide DHCP - or do you need to set up a fixed address?
The **lshw** results look kosher - unless the driver is a problem-child (dunno if it is...). You can try **sudo dhclient eth0** to see what happens.

---

