---
title: "Can't figure out how to connect to the internet"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by hradford5 on 2011-05-16
I'm trying Ubuntu 10.04 but I can't figure out how to connect to the internet. I've run lspci -k & sudo lshw -C. This is the result:

zeke@burntable:~$ lspci -k
 

 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
 

     Kernel driver in use: agpgart-intel
 

     Kernel modules: intel-agp
 

 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 

     Kernel modules: i915
 

 00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
 

     Kernel driver in use: uhci_hcd
 

 00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
 

     Kernel driver in use: uhci_hcd
 

 00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
 

     Kernel driver in use: uhci_hcd
 

 00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
 

     Kernel driver in use: ehci_hcd
 

 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
 

     Kernel modules: shpchp
 

 00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
 

     Kernel modules: iTCO_wdt, intel-rng
 

 00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
 

     Kernel driver in use: ata_piix
 

 00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
 

     Kernel modules: i2c-i801
 

 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
 

     Kernel driver in use: Intel ICH
 

     Kernel modules: snd-intel8x0
 

 01:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
 

     Kernel driver in use: yenta_cardbus
 

     Kernel modules: yenta_socket
 

 01:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
 

     Kernel driver in use: yenta_cardbus
 

     Kernel modules: yenta_socket
 

 01:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
 

     Kernel driver in use: ohci1394
 

     Kernel modules: firewire-ohci, ohci1394
 

 01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)
 

     Kernel driver in use: e100
 

     Kernel modules: e100
 

 [COLOR=#000080]_zeke@burntable_[/COLOR]:~$
 

 

 sudo lshw -C network
 

 [sudo] password for zeke:  
 

   *-network                
 

        description: Ethernet interface
 

        product: 82801DB PRO/100 VE (LOM) Ethernet Controller
 

        vendor: Intel Corporation
 

        physical id: 8
 

        bus info: pci@0000:01:08.0
 

        logical name: eth0
 

        version: 82
 

        serial: 00:40:ca:a7:64:e6
 

        size: 10MB/s
 

        capacity: 100MB/s
 

        width: 32 bits
 

        clock: 33MHz
 

        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
 

        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
 

        resources: irq:20 memory:e800b000-e800bfff ioport:c000(size=64)
 

 zeke@burntable:~$  
 

 Can anyone help me her?
We have a LAN, out other boxes (Windows) show automatic DHCP

---

### Post by theteju on 2011-05-16
Can we see?

dmesg

thanks.

---

### Post by hradford5 on 2011-05-16
> **theteju said:**
> Can we see?

dmesg

thanks.
  See what??

---

### Post by hradford5 on 2011-05-16
Sorry, I didn't notice the dmesg request. Here it is:

[    0.044024] ftrace: allocating 21796 entries in 43 pages
 

 [    0.048150] Enabling APIC mode:  Flat.  Using 1 I/O APICs
 

 [    0.048460] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
 

 [    0.090495] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 09
 

 [    0.092001] Brought up 1 CPUs
 

 [    0.092001] Total of 1 processors activated (4781.96 BogoMIPS).
 

 [    0.092001] CPU0 attaching NULL sched-domain.
 

 [    0.092001] devtmpfs: initialized
 

 [    0.092001] regulator: core version 0.5
 

 [    0.092001] Time: 11:16:49  Date: 05/16/11
 

 [    0.092001] NET: Registered protocol family 16
 

 [    0.092001] EISA bus registered
 

 [    0.092001] ACPI: bus type pci registered
 

 [    0.113563] PCI: PCI BIOS revision 2.10 entry at 0xfb2b0, last bus=3
 

 [    0.113566] PCI: Using configuration type 1 for base access
 

 [    0.114963] bio: create slab <bio-0> at 0
 

 [    0.115660] ACPI: EC: Look up EC in DSDT
 

 [    0.120898] ACPI: Interpreter enabled
 

 [    0.120907] ACPI: (supports S0 S3 S4 S5)
 

 [    0.120940] ACPI: Using IOAPIC for interrupt routing
 

 [    0.125981] ACPI: No dock devices found.
 

 [    0.126124] ACPI: PCI Root Bridge [PCI0] (0000:00)
 

 [    0.126188] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
 

 [    0.126273] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xe0000000-0xe7ffffff]
 

 [    0.126281] pci 0000:00:02.0: reg 14 32bit mmio: [0xe8100000-0xe817ffff]
 

 [    0.126397] pci 0000:00:1d.0: reg 20 io port: [0xd800-0xd81f]
 

 [    0.126458] pci 0000:00:1d.1: reg 20 io port: [0xd000-0xd01f]
 

 [    0.126518] pci 0000:00:1d.2: reg 20 io port: [0xd400-0xd41f]
 

 [    0.126578] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe8180000-0xe81803ff]
 

 [    0.126634] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
 

 [    0.126641] pci 0000:00:1d.7: PME# disabled
 

 [    0.126699] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
 

 [    0.126701] * this clock source is slow. If you are sure your timer does not have
 

 [    0.126703] * this bug, please use "acpi_pm_good" to disable the workaround
 

 [    0.126750] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
 

 [    0.126755] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
 

 [    0.126784] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
 

 [    0.126792] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
 

 [    0.126800] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
 

 [    0.126808] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
 

 [    0.126816] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
 

 [    0.126825] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
 

 [    0.126882] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
 

 [    0.126932] pci 0000:00:1f.5: reg 10 io port: [0xe000-0xe0ff]
 

 [    0.126940] pci 0000:00:1f.5: reg 14 io port: [0xe400-0xe43f]
 

 [    0.126948] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe8181000-0xe81811ff]
 

 [    0.126956] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe8182000-0xe81820ff]
 

 [    0.126989] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
 

 [    0.126994] pci 0000:00:1f.5: PME# disabled
 

 [    0.127050] pci 0000:01:07.0: reg 10 32bit mmio: [0xe8000000-0xe8000fff]
 

 [    0.127070] pci 0000:01:07.0: supports D1 D2
 

 [    0.127073] pci 0000:01:07.0: PME# supported from D0 D1 D2 D3hot D3cold
 

 [    0.127078] pci 0000:01:07.0: PME# disabled
 

 [    0.127115] pci 0000:01:07.1: reg 10 32bit mmio: [0xe8005000-0xe8005fff]
 

 [    0.127134] pci 0000:01:07.1: supports D1 D2
 

 [    0.127138] pci 0000:01:07.1: PME# supported from D0 D1 D2 D3hot D3cold
 

 [    0.127143] pci 0000:01:07.1: PME# disabled
 

 [    0.127179] pci 0000:01:07.2: reg 10 32bit mmio: [0xe800a000-0xe800a7ff]
 

 [    0.127226] pci 0000:01:07.2: PME# supported from D0 D3hot D3cold
 

 [    0.127232] pci 0000:01:07.2: PME# disabled
 

 [    0.127276] pci 0000:01:08.0: reg 10 32bit mmio: [0xe800b000-0xe800bfff]
 

 [    0.127284] pci 0000:01:08.0: reg 14 io port: [0xc000-0xc03f]
 

 [    0.127325] pci 0000:01:08.0: supports D1 D2
 

 [    0.127327] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
 

 [    0.127332] pci 0000:01:08.0: PME# disabled
 

 [    0.127369] pci 0000:00:1e.0: transparent bridge
 

 [    0.127374] pci 0000:00:1e.0: bridge io port: [0xa000-0xcfff]
 

 [    0.127380] pci 0000:00:1e.0: bridge 32bit mmio: [0xe8000000-0xe80fffff]
 

 [    0.127424] pci_bus 0000:00: on NUMA node 0
 

 [    0.127431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
 

 [    0.127598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
 

 [    0.145840] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
 

 [    0.145985] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
 

 [    0.146128] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
 

 [    0.146272] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11 12 14 15)
 

 [    0.146414] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 *15)
 

 [    0.146555] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
 

 [    0.146698] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
 

 [    0.146841] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 *15)
 

 [    0.147008] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
 

 [    0.147019] vgaarb: loaded
 

 [    0.147208] SCSI subsystem initialized
 

 [    0.147322] libata version 3.00 loaded.
 

 [    0.147436] usbcore: registered new interface driver usbfs
 

 [    0.147455] usbcore: registered new interface driver hub
 

 [    0.147492] usbcore: registered new device driver usb
 

 [    0.147688] ACPI: WMI: Mapper loaded
 

 [    0.147691] PCI: Using ACPI for IRQ routing
 

 [    0.147898] NetLabel: Initializing
 

 [    0.147901] NetLabel:  domain hash size = 128
 

 [    0.147903] NetLabel:  protocols = UNLABELED CIPSOv4
 

 [    0.147926] NetLabel:  unlabeled traffic allowed by default
 

 [    0.147993] Switching to clocksource tsc
 

 [    0.150834] AppArmor: AppArmor Filesystem Enabled
 

 [    0.150866] pnp: PnP ACPI init
 

 [    0.150902] ACPI: bus type pnp registered
 

 [    0.154331] pnp: PnP ACPI: found 15 devices
 

 [    0.154335] ACPI: ACPI bus type pnp unregistered
 

 [    0.154342] PnPBIOS: Disabled by ACPI PNP
 

 [    0.154362] system 00:00: ioport range 0x280-0x287 has been reserved
 

 [    0.154373] system 00:01: iomem range 0xcba00-0xcbfff has been reserved
 

 [    0.154378] system 00:01: iomem range 0xf0000-0xf7fff could not be reserved
 

 [    0.154382] system 00:01: iomem range 0xf8000-0xfbfff could not be reserved
 

 [    0.154386] system 00:01: iomem range 0xfc000-0xfffff could not be reserved
 

 [    0.154391] system 00:01: iomem range 0x3f7f0000-0x3f7fffff could not be reserved
 

 [    0.154395] system 00:01: iomem range 0x0-0x9ffff could not be reserved
 

 [    0.154399] system 00:01: iomem range 0x100000-0x3f7effff could not be reserved
 

 [    0.154403] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
 

 [    0.154407] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
 

 [    0.154417] system 00:01: iomem range 0xffb00000-0xffb7ffff has been reserved
 

 [    0.154422] system 00:01: iomem range 0xfff00000-0xffffffff has been reserved
 

 [    0.154426] system 00:01: iomem range 0xe0000-0xeffff has been reserved
 

 [    0.154436] system 00:04: ioport range 0x400-0x4bf could not be reserved
 

 [    0.154446] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
 

 [    0.154450] system 00:05: ioport range 0x800-0x87f has been reserved
 

 [    0.189310] pci 0000:01:07.0: CardBus bridge, secondary bus 0000:02
 

 [    0.189314] pci 0000:01:07.0:   IO window: 0x00a000-0x00a0ff
 

 [    0.189320] pci 0000:01:07.0:   IO window: 0x00a400-0x00a4ff
 

 [    0.189325] pci 0000:01:07.0:   PREFETCH window: 0x40000000-0x43ffffff
 

 [    0.189331] pci 0000:01:07.0:   MEM window: 0x4c000000-0x4fffffff
 

 [    0.189336] pci 0000:01:07.1: CardBus bridge, secondary bus 0000:03
 

 [    0.189339] pci 0000:01:07.1:   IO window: 0x00a800-0x00a8ff
 

 [    0.189344] pci 0000:01:07.1:   IO window: 0x00ac00-0x00acff
 

 [    0.189349] pci 0000:01:07.1:   PREFETCH window: 0x44000000-0x47ffffff
 

 [    0.189354] pci 0000:01:07.1:   MEM window: 0x50000000-0x53ffffff
 

 [    0.189359] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
 

 [    0.189364] pci 0000:00:1e.0:   IO window: 0xa000-0xcfff
 

 [    0.189370] pci 0000:00:1e.0:   MEM window: 0xe8000000-0xe80fffff
 

 [    0.189376] pci 0000:00:1e.0:   PREFETCH window: 0x40000000-0x47ffffff
 

 [    0.189394] pci 0000:00:1e.0: setting latency timer to 64
 

 [    0.189409]   alloc irq_desc for 18 on node -1
 

 [    0.189412]   alloc kstat_irqs on node -1
 

 [    0.189421] pci 0000:01:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
 

 [    0.189433]   alloc irq_desc for 19 on node -1
 

 [    0.189437]   alloc kstat_irqs on node -1
 

 [    0.189443] pci 0000:01:07.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
 

 [    0.189451] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
 

 [    0.189455] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
 

 [    0.189458] pci_bus 0000:01: resource 0 io:  [0xa000-0xcfff]
 

 [    0.189462] pci_bus 0000:01: resource 1 mem: [0xe8000000-0xe80fffff]
 

 [    0.189465] pci_bus 0000:01: resource 2 pref mem [0x40000000-0x47ffffff]
 

 [    0.189469] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
 

 [    0.189472] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
 

 [    0.189476] pci_bus 0000:02: resource 0 io:  [0xa000-0xa0ff]
 

 [    0.189479] pci_bus 0000:02: resource 1 io:  [0xa400-0xa4ff]
 

 [    0.189483] pci_bus 0000:02: resource 2 pref mem [0x40000000-0x43ffffff]
 

 [    0.189486] pci_bus 0000:02: resource 3 mem: [0x4c000000-0x4fffffff]
 

 [    0.189490] pci_bus 0000:03: resource 0 io:  [0xa800-0xa8ff]
 

 [    0.189493] pci_bus 0000:03: resource 1 io:  [0xac00-0xacff]
 

 [    0.189497] pci_bus 0000:03: resource 2 pref mem [0x44000000-0x47ffffff]
 

 [    0.189500] pci_bus 0000:03: resource 3 mem: [0x50000000-0x53ffffff]
 

 [    0.189553] NET: Registered protocol family 2
 

 [    0.189694] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
 

 [    0.190262] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
 

 [    0.191712] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
 

 [    0.192784] TCP: Hash tables configured (established 131072 bind 65536)
 

 [    0.192792] TCP reno registered
 

 [    0.193003] NET: Registered protocol family 1
 

 [    0.193042] pci 0000:00:02.0: Boot video device
 

 [    0.193153] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
 

 [    0.193487] cpufreq-nforce2: No nForce2 chipset.
 

 [    0.193532] Scanning for low memory corruption every 60 seconds
 

 [    0.193691] audit: initializing netlink socket (disabled)
 

 [    0.193712] type=2000 audit(1305544608.191:1): initialized
 

 [    0.203191] Trying to unpack rootfs image as initramfs...
 

 [    0.216073] highmem bounce pool size: 64 pages
 

 [    0.216090] HugeTLB registered 4 MB page size, pre-allocated 0 pages
 

 [    0.218204] VFS: Disk quotas dquot_6.5.2
 

 [    0.218294] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
 

 [    0.219188] fuse init (API version 7.13)
 

 [    0.219315] msgmni has been set to 1716
 

 [    0.224510] alg: No test for stdrng (krng)
 

 [    0.224666] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
 

 [    0.224671] io scheduler noop registered
 

 [    0.224674] io scheduler anticipatory registered
 

 [    0.224677] io scheduler deadline registered
 

 [    0.224734] io scheduler cfq registered (default)
 

 [    0.224907] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
 

 [    0.224943] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
 

 [    0.225087] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
 

 [    0.225094] ACPI: Power Button [PWRB]
 

 [    0.225174] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
 

 [    0.225178] ACPI: Power Button [PWRF]
 

 [    0.225576] processor LNXCPU:00: registered as cooling_device0
 

 [    0.264640] thermal LNXTHERM:01: registered as thermal_zone0
 

 [    0.264658] ACPI: Thermal Zone [THRM] (56 C)
 

 [    0.267097] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
 

 [    0.267228] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 

 [    0.267759] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 

 [    0.269306] brd: module loaded
 

 [    0.270002] loop: module loaded
 

 [    0.270156] input: Macintosh mouse button emulation as /devices/virtual/input/input2
 

 [    0.270321] ata_piix 0000:00:1f.1: version 2.13
 

 [    0.270351] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
 

 [    0.270437] ata_piix 0000:00:1f.1: setting latency timer to 64
 

 [    0.272206] isapnp: Scanning for PnP cards...
 

 [    0.280271] scsi0 : ata_piix
 

 [    0.284016] scsi1 : ata_piix
 

 [    0.285158] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
 

 [    0.285162] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
 

 [    0.285765] Fixed MDIO Bus: probed
 

 [    0.285821] PPP generic driver version 2.4.2
 

 [    0.285945] tun: Universal TUN/TAP device driver, 1.6
 

 [    0.285949] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
 

 [    0.286084] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
 

 [    0.286131]   alloc irq_desc for 23 on node -1
 

 [    0.286135]   alloc kstat_irqs on node -1
 

 [    0.286148] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
 

 [    0.286174] ehci_hcd 0000:00:1d.7: setting latency timer to 64
 

 [    0.286179] ehci_hcd 0000:00:1d.7: EHCI Host Controller
 

 [    0.286232] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
 

 [    0.290155] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
 

 [    0.333963] ata2: port disabled. ignoring.
 

 [    0.336191] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8180000
 

 [    0.356165] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
 

 [    0.356382] usb usb1: configuration #1 chosen from 1 choice
 

 [    0.356441] hub 1-0:1.0: USB hub found
 

 [    0.356459] hub 1-0:1.0: 6 ports detected
 

 [    0.356557] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
 

 [    0.356584] uhci_hcd: USB Universal Host Controller Interface driver
 

 [    0.356673]   alloc irq_desc for 16 on node -1
 

 [    0.356677]   alloc kstat_irqs on node -1
 

 [    0.356689] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 

 [    0.356703] uhci_hcd 0000:00:1d.0: setting latency timer to 64
 

 [    0.356708] uhci_hcd 0000:00:1d.0: UHCI Host Controller
 

 [    0.356777] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
 

 [    0.356821] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
 

 [    0.356961] usb usb2: configuration #1 chosen from 1 choice
 

 [    0.357001] hub 2-0:1.0: USB hub found
 

 [    0.357013] hub 2-0:1.0: 2 ports detected
 

 [    0.357072] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
 

 [    0.357081] uhci_hcd 0000:00:1d.1: setting latency timer to 64
 

 [    0.357086] uhci_hcd 0000:00:1d.1: UHCI Host Controller
 

 [    0.357134] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
 

 [    0.357169] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d000
 

 [    0.357300] usb usb3: configuration #1 chosen from 1 choice
 

 [    0.357339] hub 3-0:1.0: USB hub found
 

 [    0.357353] hub 3-0:1.0: 2 ports detected
 

 [    0.357410] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
 

 [    0.357418] uhci_hcd 0000:00:1d.2: setting latency timer to 64
 

 [    0.357422] uhci_hcd 0000:00:1d.2: UHCI Host Controller
 

 [    0.357467] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
 

 [    0.357503] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
 

 [    0.357644] usb usb4: configuration #1 chosen from 1 choice
 

 [    0.357682] hub 4-0:1.0: USB hub found
 

 [    0.357702] hub 4-0:1.0: 2 ports detected
 

 [    0.357853] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
 

 [    0.365047] serio: i8042 KBD port at 0x60,0x64 irq 1
 

 [    0.365064] serio: i8042 AUX port at 0x60,0x64 irq 12
 

 [    0.365330] mice: PS/2 mouse device common for all mice
 

 [    0.365533] rtc_cmos 00:07: RTC can wake from S4
 

 [    0.365605] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
 

 [    0.365632] rtc0: alarms up to one month, 242 bytes nvram
 

 [    0.365821] device-mapper: uevent: version 1.0.3
 

 [    0.366015] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
 

 [    0.368231] device-mapper: multipath: version 1.1.0 loaded
 

 [    0.368237] device-mapper: multipath round-robin: version 1.0.0 loaded
 

 [    0.369213] EISA: Probing bus 0 at eisa.0
 

 [    0.369256] EISA: Detected 0 cards.
 

 [    0.371882] cpuidle: using governor ladder
 

 [    0.371888] cpuidle: using governor menu
 

 [    0.372655] TCP cubic registered
 

 [    0.372865] NET: Registered protocol family 10
 

 [    0.373499] lo: Disabled Privacy Extensions
 

 [    0.373951] NET: Registered protocol family 17
 

 [    0.374050] Using IPI No-Shortcut mode
 

 [    0.374214] PM: Resume from disk failed.
 

 [    0.374235] registered taskstats version 1
 

 [    0.374494]   Magic number: 11:81:277
 

 [    0.374537] tty tty14: hash matches
 

 [    0.374603] rtc_cmos 00:07: setting system clock to 2011-05-16 11:16:49 UTC (1305544609)
 

 [    0.374608] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
 

 [    0.374610] EDD information not available.
 

 [    0.391047] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
 

 [    0.460639] ata1.00: ATA-4: SAMSUNG SV1022D, MK100-37, max UDMA/66
 

 [    0.460644] ata1.00: 19931184 sectors, multi 16: LBA  
 

 [    0.460694] ata1.01: ATAPI: SONY    CD-ROM CDU5215, 7YS1, max UDMA/33
 

 [    0.468527] ata1.00: configured for UDMA/66
 

 [    0.476703] ata1.01: configured for UDMA/33
 

 [    0.807706] Freeing initrd memory: 7783k freed
 

 [    0.911366] isapnp: No Plug & Play device found
 

 [    0.911649] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SV1022D  MK10 PQ: 0 ANSI: 5
 

 [    0.911951] sd 0:0:0:0: Attached scsi generic sg0 type 0
 

 [    0.912360] sd 0:0:0:0: [sda] 19931184 512-byte logical blocks: (10.2 GB/9.50 GiB)
 

 [    0.912429] sd 0:0:0:0: [sda] Write Protect is off
 

 [    0.912434] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
 

 [    0.912468] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 

 [    0.912686]  sda:
 

 [    0.912822] scsi 0:0:1:0: CD-ROM            SONY     CD-ROM CDU5215   7YS1 PQ: 0 ANSI: 5
 

 [    0.934922]  sda1 sda2 < sda5 >
 

 [    0.962452] sd 0:0:0:0: [sda] Attached SCSI disk
 

 [    0.964078] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
 

 [    0.964083] Uniform CD-ROM driver Revision: 3.20
 

 [    0.964210] sr 0:0:1:0: Attached scsi CD-ROM sr0
 

 [    0.964300] sr 0:0:1:0: Attached scsi generic sg1 type 5
 

 [    0.964381] Freeing unused kernel memory: 660k freed
 

 [    0.965548] Write protecting the kernel text: 4688k
 

 [    0.965583] Write protecting the kernel read-only data: 1844k
 

 [    1.000860] udev: starting version 151
 

 [    1.350870] Floppy drive(s): fd0 is 1.44M
 

 [    1.357693] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
 

 [    1.357700] e100: Copyright(c) 1999-2006 Intel Corporation
 

 [    1.357774]   alloc irq_desc for 20 on node -1
 

 [    1.357778]   alloc kstat_irqs on node -1
 

 [    1.357789] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
 

 [    1.381587] e100 0000:01:08.0: PME# disabled
 

 [    1.384211] e100: eth0: e100_probe: addr 0xe800b000, irq 20, MAC addr 00:40:ca:a7:64:e6
 

 [    1.384257] ohci1394 0000:01:07.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
 

 [    1.386786] FDC 0 is a post-1991 82077
 

 [    1.442035] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[e800a000-e800a7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
 

 [    1.799363] EXT4-fs (sda1): mounted filesystem with ordered data mode
 

 [    2.720219] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040ca070301ee88]
 

 [   16.516377] Adding 473080k swap on /dev/sda5.  Priority:-1 extents:1 across:473080k  
 

 [   16.553770] udev: starting version 151
 

 [   16.895532] lp: driver loaded but no devices found
 

 [   16.941773] Linux agpgart interface v0.103
 

 [   16.944227] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
 

 [   17.000815] intel_rng: FWH not detected
 

 [   17.037777] parport_pc 00:0c: reported by Plug and Play ACPI
 

 [   17.037833] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
 

 [   17.153529] agpgart-intel 0000:00:00.0: Intel 830M Chipset
 

 [   17.153762] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
 

 [   17.155626] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
 

 [   17.155854] lp0: using parport0 (interrupt-driven).
 

 [   17.370129] [drm] Initialized drm 1.1.0 20060810
 

 [   17.453259] ppdev: user-space parallel port driver
 

 [   17.470950] yenta_cardbus 0000:01:07.0: CardBus bridge found [1509:9051]
 

 [   17.471121] type=1505 audit(1305559026.593:2):  operation="profile_load" pid=485 name="/sbin/dhclient3"
 

 [   17.471844] type=1505 audit(1305559026.593:3):  operation="profile_load" pid=485 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
 

 [   17.479333] type=1505 audit(1305559026.601:4):  operation="profile_load" pid=485 name="/usr/lib/connman/scripts/dhclient-script"
 

 [   17.585046] psmouse serio1: ID: 10 00 64
 

 [   17.596612] yenta_cardbus 0000:01:07.0: ISA IRQ mask 0x0c38, PCI irq 18
 

 [   17.596618] yenta_cardbus 0000:01:07.0: Socket status: 30000006
 

 [   17.596631] yenta_cardbus 0000:01:07.0: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xcfff
 

 [   17.596637] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xcfff: clean.
 

 [   17.597325] yenta_cardbus 0000:01:07.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xe80fffff
 

 [   17.597330] yenta_cardbus 0000:01:07.0: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
 

 [   17.608501] yenta_cardbus 0000:01:07.1: CardBus bridge found [1509:9051]
 

 [   17.627196] [drm] i915 disabling kernel modesetting for known bad device.
 

 [   17.627232] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
 

 [   17.627239] pci 0000:00:02.0: setting latency timer to 64
 

 [   17.663565] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
 

 [   17.704355] vga16fb: initializing
 

 [   17.704366] vga16fb: mapped to 0xc00a0000
 

 [   17.704872] fb0: VGA16 VGA frame buffer device
 

 [   17.736811] yenta_cardbus 0000:01:07.1: ISA IRQ mask 0x0c38, PCI irq 19
 

 [   17.736818] yenta_cardbus 0000:01:07.1: Socket status: 30000006
 

 [   17.736824] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #03 to #06
 

 [   17.736842] yenta_cardbus 0000:01:07.1: pcmcia: parent PCI bridge I/O window: 0xa000 - 0xcfff
 

 [   17.736847] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa000-0xcfff: clean.
 

 [   17.737569] yenta_cardbus 0000:01:07.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xe80fffff
 

 [   17.737574] yenta_cardbus 0000:01:07.1: pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x47ffffff
 

 [   17.883524] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
 

 [   17.885474] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
 

 [   17.885746] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
 

 [   17.886170] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
 

 [   17.887082] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
 

 [   18.009888]   alloc irq_desc for 17 on node -1
 

 [   18.009892]   alloc kstat_irqs on node -1
 

 [   18.009903] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
 

 [   18.009959] Intel ICH 0000:00:1f.5: setting latency timer to 64
 

 [   18.014527] Console: switching to colour frame buffer device 80x30
 

 [   18.160347] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
 

 [   18.340078] intel8x0_measure_ac97_clock: measured 54356 usecs (2619 samples)
 

 [   18.340084] intel8x0: clocking to 48000
 

 [   18.381713] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
 

 [   18.383613] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
 

 [   18.383887] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
 

 [   18.403793] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
 

 [   18.404759] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
 

 [   18.514158] type=1505 audit(1305559027.637:5):  operation="profile_load" pid=650 name="/usr/share/gdm/guest-session/Xsession"
 

 [   18.527507] type=1505 audit(1305559027.649:6):  operation="profile_replace" pid=656 name="/sbin/dhclient3"
 

 [   18.557652] type=1505 audit(1305559027.681:7):  operation="profile_replace" pid=656 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
 

 [   18.558074] type=1505 audit(1305559027.681:8):  operation="profile_replace" pid=656 name="/usr/lib/connman/scripts/dhclient-script"
 

 [   18.657232] type=1505 audit(1305559027.781:9):  operation="profile_load" pid=663 name="/usr/bin/evince"
 

 [   18.709983] ADDRCONF(NETDEV_UP): eth0: link is not ready
 

 [   18.719383] type=1505 audit(1305559027.841:10):  operation="profile_load" pid=663 name="/usr/bin/evince-previewer"
 

 [   18.761104] type=1505 audit(1305559027.885:11):  operation="profile_load" pid=663 name="/usr/bin/evince-thumbnailer"
 

 [  327.790219] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
 

 [  327.790226] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
 

 [  327.790230] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
 

 [  410.932060] usb 1-2: new high speed USB device using ehci_hcd and address 2
 

 [  411.065834] usb 1-2: configuration #1 chosen from 1 choice
 

 [  411.131835] Initializing USB Mass Storage driver...
 

 [  411.132291] scsi2 : SCSI emulation for USB Mass Storage devices
 

 [  411.132627] usbcore: registered new interface driver usb-storage
 

 [  411.132633] USB Mass Storage support registered.
 

 [  411.141346] usb-storage: device found at 2
 

 [  411.141352] usb-storage: waiting for device to settle before scanning
 

 [  416.140212] usb-storage: device scan complete
 

 [  416.140916] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           1.00 PQ: 0 ANSI: 2
 

 [  416.145188] sd 2:0:0:0: Attached scsi generic sg2 type 0
 

 [  416.158166] sd 2:0:0:0: [sdb] 15625216 512-byte logical blocks: (8.00 GB/7.45 GiB)
 

 [  416.159537] sd 2:0:0:0: [sdb] Write Protect is off
 

 [  416.159542] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
 

 [  416.159546] sd 2:0:0:0: [sdb] Assuming drive cache: write through
 

 [  416.163755] sd 2:0:0:0: [sdb] Assuming drive cache: write through
 

 [  416.163772]  sdb: sdb1
 

 [  416.173198] sd 2:0:0:0: [sdb] Assuming drive cache: write through
 

 [  416.173212] sd 2:0:0:0: [sdb] Attached SCSI removable disk
 

 [  528.896031] end_request: I/O error, dev fd0, sector 0
 

 [ 1577.871453] usb 1-2: USB disconnect, address 2
 

 [ 2017.000150] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
 

 [ 2017.000404] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
 

 [ 2027.216037] eth0: no IPv6 routers present
 

 [ 2251.000320] e100: eth0 NIC Link is Down
 

 [ 3007.000162] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
 

 [ 3081.256024] usb 1-2: new high speed USB device using ehci_hcd and address 3
 

 [ 3081.389931] usb 1-2: configuration #1 chosen from 1 choice
 

 [ 3081.407216] scsi3 : SCSI emulation for USB Mass Storage devices
 

 [ 3081.411352] usb-storage: device found at 3
 

 [ 3081.411357] usb-storage: waiting for device to settle before scanning
 

 [ 3086.408251] usb-storage: device scan complete
 

 [ 3086.408955] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer           1.00 PQ: 0 ANSI: 2
 

 [ 3086.414108] sd 3:0:0:0: Attached scsi generic sg2 type 0
 

 [ 3086.427343] sd 3:0:0:0: [sdb] 15625216 512-byte logical blocks: (8.00 GB/7.45 GiB)
 

 [ 3086.428839] sd 3:0:0:0: [sdb] Write Protect is off
 

 [ 3086.428885] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
 

 [ 3086.428890] sd 3:0:0:0: [sdb] Assuming drive cache: write through
 

 [ 3086.432574] sd 3:0:0:0: [sdb] Assuming drive cache: write through
 

 [ 3086.432588]  sdb: sdb1
 

 [ 3086.441471] sd 3:0:0:0: [sdb] Assuming drive cache: write through
 

 [ 3086.441484] sd 3:0:0:0: [sdb] Attached SCSI removable disk
 

 [ 3149.593854] usb 1-2: USB disconnect, address 3
 

 [ 3153.812023] usb 1-2: new high speed USB device using ehci_hcd and address 4
 

 [ 3153.945886] usb 1-2: configuration #1 chosen from 1 choice
 

 [ 3153.960765] scsi4 : SCSI emulation for USB Mass Storage devices
 

 [ 3153.967457] usb-storage: device found at 4
 

 [ 3153.967462] usb-storage: waiting for device to settle before scanning
 

 [ 3158.964220] usb-storage: device scan complete
 

 [ 3158.964927] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer           1.00 PQ: 0 ANSI: 2
 

 [ 3158.969147] sd 4:0:0:0: Attached scsi generic sg2 type 0
 

 [ 3158.982056] sd 4:0:0:0: [sdb] 15625216 512-byte logical blocks: (8.00 GB/7.45 GiB)
 

 [ 3158.983420] sd 4:0:0:0: [sdb] Write Protect is off
 

 [ 3158.983426] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
 

 [ 3158.983430] sd 4:0:0:0: [sdb] Assuming drive cache: write through
 

 [ 3158.990474] sd 4:0:0:0: [sdb] Assuming drive cache: write through
 

 [ 3158.990490]  sdb: sdb1
 

 [ 3158.999186] sd 4:0:0:0: [sdb] Assuming drive cache: write through
 

 [ 3158.999198] sd 4:0:0:0: [sdb] Attached SCSI removable disk
 

 zeke@burntable:~$

---

