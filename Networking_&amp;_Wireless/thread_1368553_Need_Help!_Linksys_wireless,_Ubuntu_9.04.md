---
title: "Need Help! Linksys wireless, Ubuntu 9.04"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by Tholley on 2009-12-30
I may have messed things up myself, trying to configure the WMP54G Ver 4.1 adapter, when all I _may_ have needed to do was reset the WRT54G router. 
I tried to install ndiswrapper, and then the .inf file directly from the setup cd, but then read that the adapter should work right out of the box with the Linux drivers.

Here is some of my info...

Desktop Computer     width: 32 bits     capabilities: smbios-2.2 dmi-2.2 smp     configuration: boot=normal chassis=desktop                   id:core
          description: Motherboard        product: nVidia-nForce        physical id: 0
      
                          id:firmware
             description: BIOS           vendor: Phoenix Technologies, LTD           physical id: 0
           version: 6.00 PG (10/02/2003)           size: 128KiB           capacity: 192KiB           capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot         
        
                          id:cpu
             description: CPU           product: AMD Athlon(tm)           vendor: Advanced Micro Devices [AMD]           physical id: 4
           bus info: cpu@0
           version: 6.10.0           slot: Socket A           size: 1100MHz           capacity: 1100MHz           width: 32 bits           clock: 100MHz           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up cpufreq
[    0.004133] Mount-cache hash table entries: 512
[    0.004392] Initializing cgroup subsys ns
[    0.004399] Initializing cgroup subsys cpuacct
[    0.004404] Initializing cgroup subsys memory
[    0.004413] Initializing cgroup subsys freezer
[    0.004435] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004440] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004465] Checking 'hlt' instruction... OK.
[    0.020724] SMP alternatives: switching to UP code
[    0.300830] Freeing SMP alternatives: 18k freed
[    0.300839] ACPI: Core revision 20080926
[    0.304154] ACPI: Checking initramfs for custom DSDT
[    0.840710] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.880853] CPU0: AMD Athlon(tm)  stepping 00
[    0.884002] Brought up 1 CPUs
[    0.884002] Total of 1 processors activated (2188.37 BogoMIPS).
[    0.884002] CPU0 attaching NULL sched-domain.
[    0.884002] net_namespace: 776 bytes
[    0.884002] Booting paravirtualized kernel on bare hardware
[    0.884002] Time: 13:24:32  Date: 12/30/09
[    0.884002] regulator: core version 0.5
[    0.884002] NET: Registered protocol family 16
[    0.884002] EISA bus registered
[    0.884002] ACPI: bus type pci registered
[    0.918146] PCI: PCI BIOS revision 2.10 entry at 0xfb5a0, last bus=2
[    0.918151] PCI: Using configuration type 1 for base access
[    0.921221] ACPI: EC: Look up EC in DSDT
[    0.932181] ACPI: Interpreter enabled
[    0.932188] ACPI: (supports S0 S1 S4 S5)
[    0.932226] ACPI: Using IOAPIC for interrupt routing
[    0.944665] ACPI: No dock devices found.
[    0.944689] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.944771] pci 0000:00:00.0: reg 10 32bit mmio: [0xc0000000-0xc7ffffff]
[    0.944799] pci 0000:00:00.0: nForce2 C1 Halt Disconnect fixup
[    0.945082] pci 0000:00:01.1: reg 10 io port: [0xd000-0xd01f]
[    0.945125] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.945133] pci 0000:00:01.1: PME# disabled
[    0.945175] pci 0000:00:02.0: reg 10 32bit mmio: [0xe1003000-0xe1003fff]
[    0.945217] pci 0000:00:02.0: supports D1 D2
[    0.945220] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.945227] pci 0000:00:02.0: PME# disabled
[    0.945262] pci 0000:00:02.1: reg 10 32bit mmio: [0xe1004000-0xe1004fff]
[    0.945303] pci 0000:00:02.1: supports D1 D2
[    0.945307] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.945313] pci 0000:00:02.1: PME# disabled
[    0.945356] pci 0000:00:02.2: reg 10 32bit mmio: [0xe1005000-0xe10050ff]
[    0.945400] pci 0000:00:02.2: supports D1 D2
[    0.945403] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.945410] pci 0000:00:02.2: PME# disabled
[    0.945455] pci 0000:00:04.0: reg 10 32bit mmio: [0xe1000000-0xe1000fff]
[    0.945465] pci 0000:00:04.0: reg 14 io port: [0xd400-0xd407]
[    0.945500] pci 0000:00:04.0: supports D1 D2
[    0.945504] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.945510] pci 0000:00:04.0: PME# disabled
[    0.945547] pci 0000:00:06.0: reg 10 io port: [0xd800-0xd8ff]
[    0.945556] pci 0000:00:06.0: reg 14 io port: [0xdc00-0xdc7f]
[    0.945565] pci 0000:00:06.0: reg 18 32bit mmio: [0xe1001000-0xe1001fff]
[    0.945596] pci 0000:00:06.0: supports D1 D2
[    0.945681] pci 0000:00:09.0: reg 20 io port: [0xf000-0xf00f]
[    0.945809] pci 0000:01:04.0: reg 10 32bit mmio: [0xe0000000-0xe0007fff]
[    0.945918] pci 0000:00:08.0: bridge 32bit mmio: [0xe0000000-0xe0ffffff]
[    0.945967] pci 0000:02:00.0: reg 10 32bit mmio: [0xd8000000-0xd8ffffff]
[    0.945977] pci 0000:02:00.0: reg 14 32bit mmio: [0xc8000000-0xcfffffff]
[    0.945986] pci 0000:02:00.0: reg 18 32bit mmio: [0xd0000000-0xd007ffff]
[    0.946010] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.946071] pci 0000:00:1e.0: bridge 32bit mmio: [0xd8000000-0xdfffffff]
[    0.946078] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xc8000000-0xd7ffffff]
[    0.946093] bus 00 -> node 0
[    0.946116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.946474] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.946964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    1.016913] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.017208] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.017498] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.017789] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    1.018076] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.018367] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    1.018664] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    1.018959] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.019247] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.019538] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.019826] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.020131] ACPI: PCI Interrupt Link [LSMB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    1.020429] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    1.020723] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.021013] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.021302] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    1.021561] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
[    1.021794] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[    1.022027] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[    1.022259] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[    1.022489] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    1.022825] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[    1.023160] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[    1.023493] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[    1.023824] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[    1.024174] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[    1.024511] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[    1.024747] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[    1.025078] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[    1.025410] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[    1.025742] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[    1.026075] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[    1.026319] ACPI: WMI: Mapper loaded
[    1.026716] SCSI subsystem initialized
[    1.026812] libata version 3.00 loaded.
[    1.026926] usbcore: registered new interface driver usbfs
[    1.026962] usbcore: registered new interface driver hub
[    1.027024] usbcore: registered new device driver usb
[    1.027257] PCI: Using ACPI for IRQ routing
[    1.027414] Bluetooth: Core ver 2.13
[    1.027414] NET: Registered protocol family 31
[    1.027414] Bluetooth: HCI device and connection manager initialized
[    1.027414] Bluetooth: HCI socket layer initialized
[    1.027414] NET: Registered protocol family 8
[    1.027414] NET: Registered protocol family 20
[    1.027414] NetLabel: Initializing
[    1.027414] NetLabel:  domain hash size = 128
[    1.027414] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.027414] NetLabel:  unlabeled traffic allowed by default
[    1.027414] AppArmor: AppArmor Filesystem Enabled
[    1.027414] pnp: PnP ACPI init
[    1.027414] ACPI: bus type pnp registered
[    1.035600] pnp: PnP ACPI: found 14 devices
[    1.035605] ACPI: ACPI bus type pnp unregistered
[    1.035612] PnPBIOS: Disabled by ACPI PNP
[    1.035630] system 00:00: ioport range 0x4000-0x407f has been reserved
[    1.035636] system 00:00: ioport range 0x4080-0x40ff has been reserved
[    1.035641] system 00:00: ioport range 0x4400-0x447f has been reserved
[    1.035647] system 00:00: ioport range 0x4480-0x44ff has been reserved
[    1.035651] system 00:00: ioport range 0x4200-0x427f has been reserved
[    1.035656] system 00:00: ioport range 0x4280-0x42ff has been reserved
[    1.035667] system 00:01: ioport range 0x5000-0x503f has been reserved
[    1.035684] system 00:01: ioport range 0x5100-0x513f has been reserved
[    1.035694] system 00:02: iomem range 0xcbc00-0xcbfff has been reserved
[    1.035700] system 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[    1.035705] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[    1.035710] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[    1.035716] system 00:02: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    1.035721] system 00:02: iomem range 0xffff0000-0xffffffff has been reserved
[    1.035727] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[    1.035732] system 00:02: iomem range 0x100000-0x1ffeffff could not be reserved
[    1.035738] system 00:02: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.035743] system 00:02: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.035754] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    1.035759] system 00:04: ioport range 0x800-0x805 has been reserved
[    1.070651] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    1.070656] pci 0000:00:08.0:   IO window: disabled
[    1.070665] pci 0000:00:08.0:   MEM window: 0xe0000000-0xe0ffffff
[    1.070672] pci 0000:00:08.0:   PREFETCH window: disabled
[    1.070685] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    1.070689] pci 0000:00:1e.0:   IO window: disabled
[    1.070696] pci 0000:00:1e.0:   MEM window: 0xd8000000-0xdfffffff
[    1.070703] pci 0000:00:1e.0:   PREFETCH window: 0x000000c8000000-0x000000d7ffffff
[    1.070724] pci 0000:00:08.0: setting latency timer to 64
[    1.070736] bus: 00 index 0 io port: [0x00-0xffff]
[    1.070740] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.070744] bus: 01 index 0 mmio: [0x0-0x0]
[    1.070748] bus: 01 index 1 mmio: [0xe0000000-0xe0ffffff]
[    1.070752] bus: 01 index 2 mmio: [0x0-0x0]
[    1.070756] bus: 01 index 3 mmio: [0x0-0x0]
[    1.070759] bus: 02 index 0 mmio: [0x0-0x0]
[    1.070763] bus: 02 index 1 mmio: [0xd8000000-0xdfffffff]
[    1.070767] bus: 02 index 2 mmio: [0xc8000000-0xd7ffffff]
[    1.070771] bus: 02 index 3 mmio: [0x0-0x0]
[    1.070789] NET: Registered protocol family 2
[    1.071008] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.071500] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.071810] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.072122] TCP: Hash tables configured (established 16384 bind 16384)
[    1.072127] TCP reno registered
[    1.072257] NET: Registered protocol family 1
[    1.072502] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.599174]  it is
[    2.218183] Freeing initrd memory: 7384k freed
[    2.218382] cpufreq: Detected nForce2 chipset revision C1
[    2.218387] cpufreq: FSB changing is maybe unstable and can lead to crashes and data loss.
[    2.218408] cpufreq: FSB currently at 99 MHz, FID 11.0
[    2.218447] Marking TSC unstable due to cpufreq changes
[    2.220467] audit: initializing netlink socket (disabled)
[    2.220501] type=2000 audit(1262179473.220:1): initialized
[    2.234447] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.236906] VFS: Disk quotas dquot_6.5.1
[    2.237016] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.238188] fuse init (API version 7.10)
[    2.238346] msgmni has been set to 994
[    2.238692] alg: No test for stdrng (krng)
[    2.238716] io scheduler noop registered
[    2.238720] io scheduler anticipatory registered
[    2.238724] io scheduler deadline registered
[    2.238753] io scheduler cfq registered (default)
[    2.239038] pci 0000:02:00.0: Boot video device
[    2.246970] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.246987] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.247257] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.247263] ACPI: Power Button (FF) [PWRF]
[    2.247341] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.247346] ACPI: Power Button (CM) [PWRB]
[    2.247448] fan PNP0C0B:00: registered as cooling_device0
[    2.247459] ACPI: Fan [FAN] (on)
[    2.247976] processor ACPI_CPU:00: registered as cooling_device1
[    2.253414] thermal LNXTHERM:01: registered as thermal_zone0
[    2.253967] ACPI: Thermal Zone [THRM] (40 C)
[    2.254051] isapnp: Scanning for PnP cards...
[    2.606680] isapnp: No Plug & Play device found
[    2.609078] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.609217] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.609736] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.611214] brd: module loaded
[    2.611853] loop: module loaded
[    2.611986] Fixed MDIO Bus: probed
[    2.611999] PPP generic driver version 2.4.2
[    2.612129] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.612179] Driver 'sd' needs updating - please use bus_type methods
[    2.612197] Driver 'sr' needs updating - please use bus_type methods
[    2.612631] pata_amd 0000:00:09.0: version 0.3.10
[    2.612741] pata_amd 0000:00:09.0: setting latency timer to 64
[    2.612933] scsi0 : pata_amd
[    2.613122] scsi1 : pata_amd
[    2.614453] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.614459] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.804374] ata1.00: HPA unlocked: 66055244 -> 80293248, native 80293248
[    2.804384] ata1.00: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/133
[    2.804389] ata1.00: 80293248 sectors, multi 16: LBA 
[    2.804434] ata1: nv_mode_filter: 0x7f39f&0x7f01f->0x7f01f, BIOS=0x7f000 (0xc7000000) ACPI=0x7f01f (15:600:0x13)
[    2.820491] ata1.00: configured for UDMA/133
[    2.984390] ata2.00: ATAPI: LG      CD-ROM CRD-8521B, 2.00, max MWDMA2
[    2.984431] ata2: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc7000000) ACPI=0x39f (120:600:0x12)
[    2.992341] ata2.00: configured for MWDMA2
[    2.992772] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    2.992959] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
[    2.992997] sd 0:0:0:0: [sda] Write Protect is off
[    2.993003] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.993057] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.993189] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
[    2.993220] sd 0:0:0:0: [sda] Write Protect is off
[    2.993225] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.993277] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.993285]  sda: sda1 sda2 < sda5 >
[    3.017267] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.017360] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.017667] scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8521B 2.00 PQ: 0 ANSI: 5
[    3.020638] sr0: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
[    3.020644] Uniform CD-ROM driver Revision: 3.20
[    3.020829] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.020891] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.021714] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.022289] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    3.022306] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
[    3.022355] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    3.022362] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    3.022482] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    3.022540] ehci_hcd 0000:00:02.2: debug port 1
[    3.022549] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    3.022580] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe1005000
[    3.032032] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    3.032163] usb usb1: configuration #1 chosen from 1 choice
[    3.032217] hub 1-0:1.0: USB hub found
[    3.032238] hub 1-0:1.0: 6 ports detected
[    3.032416] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.032920] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    3.032931] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
[    3.032951] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.032957] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.033037] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    3.033073] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe1003000
[    3.090111] usb usb2: configuration #1 chosen from 1 choice
[    3.090157] hub 2-0:1.0: USB hub found
[    3.090176] hub 2-0:1.0: 3 ports detected
[    3.090787] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[    3.090797] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
[    3.090817] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    3.090822] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    3.090906] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    3.090940] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe1004000
[    3.146102] usb usb3: configuration #1 chosen from 1 choice
[    3.146160] hub 3-0:1.0: USB hub found
[    3.146178] hub 3-0:1.0: 3 ports detected
[    3.146319] uhci_hcd: USB Universal Host Controller Interface driver
[    3.146477] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.149354] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.149365] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.149565] mice: PS/2 mouse device common for all mice
[    3.149822] rtc_cmos 00:06: RTC can wake from S4
[    3.149910] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.149944] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    3.150053] device-mapper: uevent: version 1.0.3
[    3.150283] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.150399] device-mapper: multipath: version 1.0.5 loaded
[    3.150405] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.150546] EISA: Probing bus 0 at eisa.0
[    3.150576] Cannot allocate resource for EISA slot 4
[    3.150581] Cannot allocate resource for EISA slot 5
[    3.150600] EISA: Detected 0 cards.
[    3.150679] cpuidle: using governor ladder
[    3.150684] cpuidle: using governor menu
[    3.151615] TCP cubic registered
[    3.151800] NET: Registered protocol family 10
[    3.152600] lo: Disabled Privacy Extensions
[    3.153226] NET: Registered protocol family 17
[    3.153259] Bluetooth: L2CAP ver 2.11
[    3.153263] Bluetooth: L2CAP socket layer initialized
[    3.153269] Bluetooth: SCO (Voice Link) ver 0.6
[    3.153272] Bluetooth: SCO socket layer initialized
[    3.153326] Bluetooth: RFCOMM socket layer initialized
[    3.153342] Bluetooth: RFCOMM TTY layer initialized
[    3.153346] Bluetooth: RFCOMM ver 1.10
[    3.153384] powernow-k8: Processor cpuid 6a0 not supported
[    3.153410] Using IPI No-Shortcut mode
[    3.153551] registered taskstats version 1
[    3.153767]   Magic number: 5:46:434
[    3.153933] rtc_cmos 00:06: setting system clock to 2009-12-30 13:24:35 UTC (1262179475)
[    3.153939] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.153943] EDD information not available.
[    3.154943] Freeing unused kernel memory: 532k freed
[    3.155167] Write protecting the kernel text: 4120k
[    3.155242] Write protecting the kernel read-only data: 1524k
[    3.194885] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.732128] Floppy drive(s): fd0 is 1.44M
[    3.751984] FDC 0 is a post-1991 82077
[    3.886721] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.887341] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    3.887352] forcedeth 0000:00:04.0: PCI INT A -> Link[APCH] -> GSI 22 (level, high) -> IRQ 22
[    3.887363] forcedeth 0000:00:04.0: setting latency timer to 64
[    3.887473] nv_probe: set workaround bit for reversed mac addr
[    4.405458] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x4063 @ 1, addr 00:0d:87:48:c0:aa
[    4.405468] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[    4.694596] PM: Starting manual resume from disk
[    4.694604] PM: Resume from partition 8:5
[    4.694607] PM: Checking hibernation image.
[    4.694906] PM: Resume from disk failed.
[    4.721370] EXT4-fs: barriers enabled
[    4.735265] kjournald2 starting.  Commit interval 5 seconds
[    4.735287] EXT4-fs: delayed allocation enabled
[    4.735291] EXT4-fs: file extents enabled
[    4.745410] EXT4-fs: mballoc enabled
[    4.745419] EXT4-fs: mounted filesystem with ordered data mode.
[    9.307382] udev: starting version 141
[    9.534419] Linux agpgart interface v0.103
[    9.596796] agpgart: Detected NVIDIA nForce2 chipset
[    9.612002] agpgart-nvidia 0000:00:00.0: AGP aperture is 128M @ 0xc0000000
[    9.642553] parport_pc 00:0b: reported by Plug and Play ACPI
[    9.642662] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    9.688340] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    9.688436] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[    9.993525] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.120427] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   10.428967] nvidia: module license 'NVIDIA' taints kernel.
[   10.704007] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   10.835781] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.847849] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   10.847871] nvidia 0000:02:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, high) -> IRQ 19
[   10.849040] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.10  Sat Jan 24 19:49:38 PST 2009
[   10.971751] ndiswrapper: driver rt61 (Linksys, A Division of Cisco Systems, Inc.,10/18/2005, 1.00.03.0000) loaded
[   10.972558] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   10.972579] ndiswrapper 0000:01:04.0: PCI INT A -> Link[APC1] -> GSI 16 (level, high) -> IRQ 16
[   10.988971] ndiswrapper: using IRQ 16
[   11.189251] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[   11.189265] Intel ICH 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 21 (level, high) -> IRQ 21
[   11.189375] Intel ICH 0000:00:06.0: setting latency timer to 64
[   11.224233] ppdev: user-space parallel port driver
[   11.261683] wlan0: ethernet device 00:25:9c:7a:4f:32 using serialized NDIS driver: rt61, version: 0x0, NDIS version: 0x500, vendor: 'Linksys Wireless-G PCI Adapter', 1814:0301.5.conf
[   11.261729] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   11.261932] usbcore: registered new interface driver ndiswrapper
[   11.327878] psmouse serio1: ID: 10 00 64<6>ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   11.336735] udev: renamed network interface wlan0 to wlan1
[   11.512027] intel8x0_measure_ac97_clock: measured 54552 usecs
[   11.512035] intel8x0: clocking to 47466
[   11.707497] lp0: using parport0 (interrupt-driven).
[   11.866092] Adding 1494004k swap on /dev/sda5.  Priority:-1 extents:1 across:1494004k
[   11.891688] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   12.472886] EXT4 FS on sda1, internal journal on sda1:8
[   13.788977] type=1505 audit(1262179486.134:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1919
[   13.898129] type=1505 audit(1262179486.242:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1923
[   13.898503] type=1505 audit(1262179486.242:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1923
[   13.898634] type=1505 audit(1262179486.242:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1923
[   13.898748] type=1505 audit(1262179486.242:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1923
[   14.227839] type=1505 audit(1262179486.570:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1928
[   14.228383] type=1505 audit(1262179486.574:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1928
[   14.293621] type=1505 audit(1262179486.638:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1932
[   18.054747] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.054754] Bluetooth: BNEP filters: protocol multicast
[   18.091810] Bridge firewalling registered
[   19.946083] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
[   19.946109] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode
[   19.946188] nvidia 0000:02:00.0: putting AGP V2 device into 4x mode
[   22.480304] ndiswrapper: device wlan1 removed
[   22.480436] ndiswrapper 0000:01:04.0: PCI INT A disabled
[   22.480597] usbcore: deregistering interface driver ndiswrapper
[   33.820022] eth0: no IPv6 routers present
[   81.882561] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[  130.522513] eth0: link down.
[  275.105605] eth0: link up.
kaylen@kaylen-desktop:~$ sudo lshw -C network
[sudo] password for kaylen: 
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:0d:87:48:c0:aa
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.103 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:01:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 42:83:d4:fc:e3:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
kaylen@kaylen-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

kaylen@kaylen-desktop:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
kaylen@kaylen-desktop:~$ iwlist scan wlan1
iwlist: unknown command `wlan1' (check 'iwlist --help').
kaylen@kaylen-desktop:~$ lsb_release -d
Description:    Ubuntu 9.04
kaylen@kaylen-desktop:~$ uname -mr
2.6.28-17-generic i686
kaylen@kaylen-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
kaylen@kaylen-desktop:~$

---

### Post by Bucky Ball on 2009-12-30
Have you plugged in an ethernet cable and got all updates?

---

### Post by Tholley on 2009-12-30
> **Bucky Ball said:**
> Have you plugged in an ethernet cable and got all updates?

Yes... I am wire connected right now.

---

### Post by Bucky Ball on 2009-12-30
System->Administration->Hardware Drivers. Anything there?

---

### Post by Tholley on 2009-12-30
> **Bucky Ball said:**
> System->Administration->Hardware Drivers. Anything there?

Just the Nvidia graphics driver.

---

### Post by Tholley on 2009-12-31
bump... 

help?

---

### Post by bkratz on 2009-12-31
> **Tholley said:**
> bump... 

help?




Might be interesting---he does't give a version number on his card. Hopefully some help.

[http://ubuntuforums.org/showthread.php?t=1233448&highlight=wmp54gs](http://ubuntuforums.org/showthread.php?t=1233448&highlight=wmp54gs)

---

### Post by Tholley on 2009-12-31
Thanks... I'm reading thru your link now.

I hope it works!

---

### Post by Tholley on 2009-12-31
Well I'm thinking all that might work, but now how do I "turn on" wireless networking?

I am missing "enable wireless networking" option on the icon at the top.

It used to be there before... :(

---

### Post by Tholley on 2009-12-31
ok I ran this... 
sudo pccardctl ident

and it came up blank, so reading from here

 [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network)

it says "**If you get no output then the memory on the card cannot be read. **Now we need to open a configuration file and add this information to it: "

This I need help with please...

---

### Post by bkratz on 2009-12-31
> **Tholley said:**
> ok I ran this... 
sudo pccardctl ident

and it came up blank, so reading from here

 [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network)

it says "**If you get no output then the memory on the card cannot be read. **Now we need to open a configuration file and add this information to it: "

This I need help with please...



Not really sure why you are doing that ( I am not familiar with that command anyway ) it is in the section labeled "non recognized card).  According to your first post your card is

description: Network controller
product: RT2561/RT61 802.11g PCI
vendor: RaLink

a Ralink device.  I would search for the RT2561 in the search function above.

---

### Post by bkratz on 2009-12-31
Could be interesting reading

[http://ubuntuforums.org/showthread.php?t=1327561&highlight=RT2561](http://ubuntuforums.org/showthread.php?t=1327561&highlight=RT2561)

---

### Post by Tholley on 2009-12-31
> **bkratz said:**
> Not really sure why you are doing that ( I am not familiar with that command anyway ) it is in the section labeled "non recognized card).  According to your first post your card is

description: Network controller
product: RT2561/RT61 802.11g PCI
vendor: RaLink

a Ralink device.  I would search for the RT2561 in the search function above.

Just trying to do some trouble shooting on my own. 
I'm probably making matters worse, but I really need somebody to walk me thru the troubleshooting and fixing stuff.

---

### Post by Tholley on 2009-12-31
> **bkratz said:**
> Could be interesting reading

[http://ubuntuforums.org/showthread.php?t=1327561&highlight=RT2561](http://ubuntuforums.org/showthread.php?t=1327561&highlight=RT2561)


Read it... I have RT61 driver installed, so the rest I'm not seeing a solution.

I un-installed it thinking that I didn't need it since it is a Windows .inf driver, and that is when my "enable wireless" option went away. Re-installed it, and have my wireless option back, added all the ssis and pass phrase info, but still wont connect.

I might take the wireless adapter out of my other computer that I know works, and see if I get any change.

wish me luck!

---

### Post by bkratz on 2009-12-31
> **Tholley said:**
> Read it... I have RT61 driver installed, so the rest I'm not seeing a solution.

I un-installed it thinking that I didn't need it since it is a Windows .inf driver, and that is when my "enable wireless" option went away. Re-installed it, and have my wireless option back, added all the ssis and pass phrase info, but still wont connect.

I might take the wireless adapter out of my other computer that I know works, and see if I get any change.

wish me luck!



Went to this link and it says that particular card should have worked out of the box in any version later that Intrepid

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI)

I looked through some of your other threads and it looks like you have tried to compile drivers--install ndiswrapper with Windows drivers.  Since it reports unclaimed that means it has no driver associated. I'm afraid that so much has been done that it is above my level of competency and may end requiring a reload. Perhaps someone else who knows more can help.

---

### Post by Tholley on 2009-12-31
> **bkratz said:**
> Went to this link and it says that particular card should have worked out of the box in any version later that Intrepid

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI)

I looked through some of your other threads and it looks like you have tried to compile drivers--install ndiswrapper with Windows drivers.  Since it reports unclaimed that means it has no driver associated. I'm afraid that so much has been done that it is above my level of competency and may end requiring a reload. Perhaps someone else who knows more can help.

I saw exactly the same thing, so that is why i am at my wits end! I changed out adapters and no difference. 

Thanks for trying, but that is why I said I need someone to walk me thru step by step.

---

