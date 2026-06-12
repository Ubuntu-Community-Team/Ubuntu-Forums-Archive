---
title: "Jaunty 9.04 No Wireless Connection (USB Dongle Hawking HWU54G)"
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by ximhot on 2009-06-19
I am completely bewildered today:

I have this Compaq Presario 2100 installed with Ubuntu 9.04 for my son. There was absolutely no problem the first time I installed Ubuntu on this laptop and got the Hawking HWU54G working with a Netgear wireless router with no sweat. Yesterday I took the harddrive off to try another harddrive. After I put the harddrive back, the system had hard time restarting. I took the hard drive out and connect it to a Windows machine to scan the hard drive. It has been 20 hours and it is still scanning. I guess the hard drive is failing. Having talked 'bout this, here is the weird part: I installed a new hard drive and had a new installation of 9.04. Everything seemed to be very smooth until I tried wireless. 

BTW, I am using the same hardware except for the hard drive. And I used the same Ubuntu official CD-Rom.

The Hawking HWU54G that has been working with other two Ubuntu computers with no proble at all. I tried a PCMCIA wirless card and no wireless connect can be established, either. I have checked the wireless router and it works fine with the other computers. 

Here is lspci result:

00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

$ lsusb: 

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ lsmod | grep "wlan_module_name"No result.

Apparently the system can't find the USB dongle. 

Here is the detail system messages:

[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1794.396 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2290560 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 436148k/458176k available (4110k kernel code, 21336k reserved, 2197k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xdc770000 - 0xff3fe000   ( 556 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdbf70000   ( 447 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc05039df - 0xc0728e60   (2197 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05039df   (4110 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 3588.79 BogoMIPS (lpj=7177584)
[    0.004056] Security Framework initialized
[    0.004073] SELinux:  Disabled at boot.
[    0.004106] AppArmor: AppArmor initialized
[    0.004130] Mount-cache hash table entries: 512
[    0.004394] Initializing cgroup subsys ns
[    0.004404] Initializing cgroup subsys cpuacct
[    0.004409] Initializing cgroup subsys memory
[    0.004419] Initializing cgroup subsys freezer
[    0.004450] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004457] CPU: L2 cache: 512K
[    0.004463] CPU: Hyper-Threading is disabled
[    0.004492] Checking 'hlt' instruction... OK.
[    0.021423] SMP alternatives: switching to UP code
[    0.193233] Freeing SMP alternatives: 18k freed
[    0.193244] ACPI: Core revision 20080926
[    0.205398] ACPI: Checking initramfs for custom DSDT
[    0.682833] ACPI: setting ELCR to 0200 (from 0420)
[    0.684135] weird, boot CPU (#0) not listedby the BIOS.
[    0.684139] SMP motherboard not detected.
[    0.684145] Local APIC not detected. Using dummy APIC emulation.
[    0.684148] SMP disabled
[    0.684741] Brought up 1 CPUs
[    0.684749] Total of 1 processors activated (3588.79 BogoMIPS).
[    0.684780] CPU0 attaching NULL sched-domain.
[    0.685560] net_namespace: 776 bytes
[    0.685592] Booting paravirtualized kernel on bare hardware
[    0.686062] Time:  0:01:43  Date: 06/20/09
[    0.686076] regulator: core version 0.5
[    0.686158] NET: Registered protocol family 16
[    0.686436] EISA bus registered
[    0.686471] ACPI: bus type pci registered
[    0.686698] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[    0.686702] PCI: Using configuration type 1 for base access
[    0.690770] ACPI: EC: Look up EC in DSDT
[    0.704028] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.704194] ACPI: Interpreter enabled
[    0.704205] ACPI: (supports S0 S3 S4 S5)
[    0.704237] ACPI: Using PIC for interrupt routing
[    0.713979] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.713979] ACPI: EC: driver started in interrupt mode
[    0.716163] ACPI: No dock devices found.
[    0.716183] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.716268] pci 0000:00:00.0: reg 10 32bit mmio: [0xd4000000-0xd7ffffff]
[    0.716277] pci 0000:00:00.0: reg 14 32bit mmio: [0xd000a000-0xd000afff]
[    0.716363] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0000000-0xd0000fff]
[    0.716400] pci 0000:00:02.0: PME# supported from D3cold
[    0.716407] pci 0000:00:02.0: PME# disabled
[    0.716442] pci 0000:00:06.0: reg 10 io port: [0x1000-0x10ff]
[    0.716451] pci 0000:00:06.0: reg 14 32bit mmio: [0xd0001000-0xd0001fff]
[    0.716482] pci 0000:00:06.0: supports D1 D2
[    0.716485] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.716490] pci 0000:00:06.0: PME# disabled
[    0.716587] pci 0000:00:08.0: reg 10 32bit mmio: [0xd0002000-0xd0002fff]
[    0.716595] pci 0000:00:08.0: reg 14 io port: [0x1400-0x14ff]
[    0.716627] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.716632] pci 0000:00:08.0: PME# disabled
[    0.716667] pci 0000:00:0a.0: reg 10 32bit mmio: [0xd0003000-0xd0003fff]
[    0.716678] pci 0000:00:0a.0: supports D1 D2
[    0.716682] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.716687] pci 0000:00:0a.0: PME# disabled
[    0.716722] pci 0000:00:0c.0: reg 10 32bit mmio: [0xd0008000-0xd00087ff]
[    0.716730] pci 0000:00:0c.0: reg 14 32bit mmio: [0xd0004000-0xd0007fff]
[    0.716764] pci 0000:00:0c.0: supports D1 D2
[    0.716767] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot
[    0.716772] pci 0000:00:0c.0: PME# disabled
[    0.716823] pci 0000:00:10.0: reg 20 io port: [0x2000-0x200f]
[    0.716899] pci 0000:00:11.0: quirk: region 8000-803f claimed by ali7101 ACPI
[    0.716905] pci 0000:00:11.0: quirk: region 8040-805f claimed by ali7101 SMB
[    0.716939] pci 0000:00:12.0: reg 10 io port: [0x2400-0x24ff]
[    0.716948] pci 0000:00:12.0: reg 14 32bit mmio: [0xd0009000-0xd0009fff]
[    0.716974] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.716985] pci 0000:00:12.0: supports D1 D2
[    0.716988] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.716993] pci 0000:00:12.0: PME# disabled
[    0.717059] pci 0000:01:05.0: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.717067] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.717075] pci 0000:01:05.0: reg 18 32bit mmio: [0xd0300000-0xd030ffff]
[    0.717096] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.717108] pci 0000:01:05.0: supports D1 D2
[    0.717151] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.717157] pci 0000:00:01.0: bridge 32bit mmio: [0xd0300000-0xd03fffff]
[    0.717163] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd8000000-0xdfffffff]
[    0.717189] bus 00 -> node 0
[    0.717200] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.717331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    0.720447] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[    0.720731] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[    0.721013] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 10) *0, disabled.
[    0.721294] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 10) *0, disabled.
[    0.721576] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[    0.721858] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
[    0.722137] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[    0.722418] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[    0.722697] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 *10)
[    0.722938] ACPI: WMI: Mapper loaded
[    0.723387] SCSI subsystem initialized
[    0.723461] libata version 3.00 loaded.
[    0.723561] usbcore: registered new interface driver usbfs
[    0.723597] usbcore: registered new interface driver hub
[    0.723654] usbcore: registered new device driver usb
[    0.723874] PCI: Using ACPI for IRQ routing
[    0.724058] Bluetooth: Core ver 2.13
[    0.724110] NET: Registered protocol family 31
[    0.724114] Bluetooth: HCI device and connection manager initialized
[    0.724121] Bluetooth: HCI socket layer initialized
[    0.724126] NET: Registered protocol family 8
[    0.724129] NET: Registered protocol family 20
[    0.724160] NetLabel: Initializing
[    0.724164] NetLabel:  domain hash size = 128
[    0.724167] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.724193] NetLabel:  unlabeled traffic allowed by default
[    0.724365] AppArmor: AppArmor Filesystem Enabled
[    0.724384] pnp: PnP ACPI init
[    0.724384] ACPI: bus type pnp registered
[    0.727202] pnp 00:07: io resource (0x8004-0x8005) overlaps 0000:00:11.0 BAR 7 (0x8000-0x803f), disabling
[    0.732873] pnp: PnP ACPI: found 12 devices
[    0.732878] ACPI: ACPI bus type pnp unregistered
[    0.732887] PnPBIOS: Disabled by ACPI PNP
[    0.732914] system 00:07: ioport range 0x40b-0x40b has been reserved
[    0.732918] system 00:07: ioport range 0x480-0x48f has been reserved
[    0.732922] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.732926] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    0.732931] system 00:07: ioport range 0x8000-0x807f could not be reserved
[    0.732935] system 00:07: ioport range 0xff00-0xff01 has been reserved
[    0.732940] system 00:07: ioport range 0xfe00-0xfefe has been reserved
[    0.732946] system 00:07: iomem range 0xd000a000-0xd000afff has been reserved
[    0.767829] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.767835] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.767842] pci 0000:00:01.0:   MEM window: 0xd0300000-0xd03fffff
[    0.767847] pci 0000:00:01.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
[    0.767856] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.767860] pci 0000:00:0a.0:   IO window: 0x001800-0x0018ff
[    0.767865] pci 0000:00:0a.0:   IO window: 0x001c00-0x001cff
[    0.767871] pci 0000:00:0a.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.767877] pci 0000:00:0a.0:   MEM window: 0x34000000-0x37ffffff
[    0.767902] pci 0000:00:0a.0: enabling device (0000 -> 0003)
[    0.768306] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[    0.768311] PCI: setting IRQ 11 as level-triggered
[    0.768318] pci 0000:00:0a.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[    0.768328] bus: 00 index 0 io port: [0x00-0xffff]
[    0.768332] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.768336] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.768339] bus: 01 index 1 mmio: [0xd0300000-0xd03fffff]
[    0.768343] bus: 01 index 2 mmio: [0xd8000000-0xdfffffff]
[    0.768346] bus: 01 index 3 mmio: [0x0-0x0]
[    0.768349] bus: 02 index 0 io port: [0x1800-0x18ff]
[    0.768353] bus: 02 index 1 io port: [0x1c00-0x1cff]
[    0.768356] bus: 02 index 2 mmio: [0x30000000-0x33ffffff]
[    0.768359] bus: 02 index 3 mmio: [0x34000000-0x37ffffff]
[    0.768380] NET: Registered protocol family 2
[    0.768625] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.769049] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.769207] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.769357] TCP: Hash tables configured (established 16384 bind 16384)
[    0.769362] TCP reno registered
[    0.769535] NET: Registered protocol family 1
[    0.769791] checking if image is initramfs... it is
[    1.268063] Switched to high resolution mode on CPU 0
[    1.748229] Freeing initrd memory: 7360k freed
[    1.748343] Simple Boot Flag at 0x37 set to 0x1
[    1.748409] cpufreq: No nForce2 chipset.
[    1.748740] audit: initializing netlink socket (disabled)
[    1.748791] type=2000 audit(1245456104.748:1): initialized
[    1.759924] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.761998] VFS: Disk quotas dquot_6.5.1
[    1.762105] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.763257] fuse init (API version 7.10)
[    1.763398] msgmni has been set to 866
[    1.763779] alg: No test for stdrng (krng)
[    1.763807] io scheduler noop registered
[    1.763811] io scheduler anticipatory registered
[    1.763814] io scheduler deadline registered
[    1.763853] io scheduler cfq registered (default)
[    1.980084] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    1.980131] pci 0000:01:05.0: Boot video device
[    1.985565] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.985584] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.986049] ACPI: AC Adapter [ACAD] (on-line)
[    1.986331] ACPI: Battery Slot [BAT1] (battery absent)
[    1.986459] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.986464] ACPI: Power Button (FF) [PWRF]
[    1.986554] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.986559] ACPI: Power Button (CM) [PWRB]
[    1.986634] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.991302] ACPI: Lid Switch [LID]
[    1.991738] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.991789] processor ACPI_CPU:00: registered as cooling_device0
[    1.991796] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.996152] thermal LNXTHERM:01: registered as thermal_zone0
[    1.997921] ACPI: Thermal Zone [THRM] (50 C)
[    1.998006] isapnp: Scanning for PnP cards...
[    2.352330] isapnp: No Plug & Play device found
[    2.354471] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.354618] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.354756] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.355373] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.355473] serial 0000:00:08.0: enabling device (0000 -> 0003)
[    2.355991] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[    2.355997] PCI: setting IRQ 10 as level-triggered
[    2.356005] serial 0000:00:08.0: PCI INT A -> Link[LNK6] -> GSI 10 (level, low) -> IRQ 10
[    2.356055] serial 0000:00:08.0: PCI INT A disabled
[    2.357346] brd: module loaded
[    2.357952] loop: module loaded
[    2.358150] Fixed MDIO Bus: probed
[    2.358164] PPP generic driver version 2.4.2
[    2.358298] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.358369] Driver 'sd' needs updating - please use bus_type methods
[    2.358388] Driver 'sr' needs updating - please use bus_type methods
[    2.358804] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    2.359115] scsi0 : pata_ali
[    2.359324] scsi1 : pata_ali
[    2.359720] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[    2.359725] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[    2.520448] ata1.00: ATA-6: TOSHIBA MK4026GAX, PA102D, max UDMA/100
[    2.520453] ata1.00: 78140160 sectors, multi 16: LBA 
[    2.528398] ata1.00: configured for UDMA/100
[    2.804359] ata2.00: ATAPI: COMPAQ  CD-ROM SN-124, N100, max MWDMA2
[    2.804403] ata2.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    2.804407] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    2.820329] ata2.00: configured for MWDMA2
[    2.820770] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK4026GA PA10 PQ: 0 ANSI: 5
[    2.820988] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.821020] sd 0:0:0:0: [sda] Write Protect is off
[    2.821025] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.821072] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.821216] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.821242] sd 0:0:0:0: [sda] Write Protect is off
[    2.821247] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.821291] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.821298]  sda: sda1 sda2 < sda5 >
[    2.902410] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.902533] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.902987] scsi 1:0:0:0: CD-ROM            COMPAQ   CD-ROM SN-124    N100 PQ: 0 ANSI: 5
[    2.908218] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    2.908226] Uniform CD-ROM driver Revision: 3.20
[    2.908430] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.908528] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.909407] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.909443] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.909933] ACPI: PCI Interrupt Link [LNK8] enabled at IRQ 10
[    2.909942] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LNK8] -> GSI 10 (level, low) -> IRQ 10
[    2.909998] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.910149] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.910185] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[    2.970140] usb usb1: configuration #1 chosen from 1 choice
[    2.970193] hub 1-0:1.0: USB hub found
[    2.970213] hub 1-0:1.0: 4 ports detected
[    2.970429] uhci_hcd: USB Universal Host Controller Interface driver
[    2.970645] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.975758] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.975771] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.976002] mice: PS/2 mouse device common for all mice
[    2.976400] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.976434] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    2.976568] device-mapper: uevent: version 1.0.3
[    2.976787] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.976878] device-mapper: multipath: version 1.0.5 loaded
[    2.976884] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.977058] EISA: Probing bus 0 at eisa.0
[    2.977072] Cannot allocate resource for EISA slot 1
[    2.977076] Cannot allocate resource for EISA slot 2
[    2.977106] Cannot allocate resource for EISA slot 8
[    2.977109] EISA: Detected 0 cards.
[    2.977219] cpuidle: using governor ladder
[    2.977307] cpuidle: using governor menu
[    2.978211] TCP cubic registered
[    2.978341] NET: Registered protocol family 10
[    2.979026] lo: Disabled Privacy Extensions
[    2.979545] NET: Registered protocol family 17
[    2.979587] Bluetooth: L2CAP ver 2.11
[    2.979591] Bluetooth: L2CAP socket layer initialized
[    2.979596] Bluetooth: SCO (Voice Link) ver 0.6
[    2.979599] Bluetooth: SCO socket layer initialized
[    2.979676] Bluetooth: RFCOMM socket layer initialized
[    2.979698] Bluetooth: RFCOMM TTY layer initialized
[    2.979701] Bluetooth: RFCOMM ver 1.10
[    2.980275] IO APIC resources could be not be allocated.
[    2.980336] Using IPI No-Shortcut mode
[    2.980531] registered taskstats version 1
[    2.980706]   Magic number: 13:459:1
[    2.980903] rtc_cmos 00:02: setting system clock to 2009-06-20 00:01:48 UTC (1245456108)
[    2.980910] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.980913] EDD information not available.
[    2.981725] Freeing unused kernel memory: 532k freed
[    2.981943] Write protecting the kernel text: 4112k
[    2.982004] Write protecting the kernel read-only data: 1524k
[    3.030162] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.774522] Floppy drive(s): fd0 is 1.44M
[    3.791467] FDC 0 is a post-1991 82077
[    4.131155] ohci1394 0000:00:0c.0: enabling device (0010 -> 0012)
[    4.131175] ohci1394 0000:00:0c.0: PCI INT A -> Link[LNK5] -> GSI 11 (level, low) -> IRQ 11
[    4.181091] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[d0008000-d00087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.285758] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[    4.285762]   originally by Donald Becker <becker@scyld.com>
[    4.285764]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[    4.286334] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    4.286344] natsemi 0000:00:12.0: PCI INT A -> Link[LNK1] -> GSI 10 (level, low) -> IRQ 10
[    4.289335] natsemi eth0: NatSemi DP8381[56] at 0xd0009000 (0000:00:12.0), 00:0b:cd:a6:78:37, IRQ 10, port TP.
[    5.433443] Marking TSC unstable due to TSC halts in idle
[    5.492809] PM: Starting manual resume from disk
[    5.492818] PM: Resume from partition 8:5
[    5.492821] PM: Checking hibernation image.
[    5.493114] PM: Resume from disk failed.
[    5.529670] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000bcd719f89afb5]
[    5.584012] kjournald starting.  Commit interval 5 seconds
[    5.584081] EXT3-fs: mounted filesystem with ordered data mode.
[   11.764359] udev: starting version 141
[   12.007389] Linux agpgart interface v0.103
[   12.035106] agpgart-ati 0000:00:00.0: Ati IGP330/340/345/350/M chipset
[   12.045016] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xd4000000
[   12.066466] parport_pc 00:09: reported by Plug and Play ACPI
[   12.066544] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   12.094436] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.114557] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input5
[   12.148413] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.361567] yenta_cardbus 0000:00:0a.0: CardBus bridge found [103c:002a]
[   12.361596] yenta_cardbus 0000:00:0a.0: O2: res at 0x94/0xD4: 00/ea
[   12.361600] yenta_cardbus 0000:00:0a.0: O2: enabling read prefetch/write burst
[   12.489693] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 11
[   12.489702] yenta_cardbus 0000:00:0a.0: Socket status: 30000411
[   12.632479] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.759538] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.031103] ALI 5451 0000:00:06.0: enabling device (0005 -> 0007)
[   13.031577] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[   13.031584] PCI: setting IRQ 5 as level-triggered
[   13.031592] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNK7] -> GSI 5 (level, low) -> IRQ 5
[   13.148188] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   13.370134] ppdev: user-space parallel port driver
[   13.678032] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
[   13.712827] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   13.730966] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   13.733247] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   13.734158] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.735011] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.736201] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   13.737189] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   13.773706] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   13.924106] eth1: Xircom: port 0x300, irq 3, hwaddr 00:10:a4:ea:ea:7f
[   15.856042] AC'97 1 does not respond - RESET
[   15.872041] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   15.872053] ali mixer 1 creating error.
[   16.123391] lp0: using parport0 (interrupt-driven).
[   16.348258] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k
[   16.941278] EXT3 FS on sda1, internal journal
[   18.487845] type=1505 audit(1245456124.003:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1891
[   18.579178] type=1505 audit(1245456124.095:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1895
[   18.579626] type=1505 audit(1245456124.095:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1895
[   18.579745] type=1505 audit(1245456124.095:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1895
[   18.579839] type=1505 audit(1245456124.095:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1895
[   18.835218] type=1505 audit(1245456124.351:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1900
[   18.835769] type=1505 audit(1245456124.351:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1900
[   18.896191] type=1505 audit(1245456124.415:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1904
[   23.055565] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.055572] Bluetooth: BNEP filters: protocol multicast
[   23.083193] Bridge firewalling registered
[   24.710342] pci 0000:01:05.0: power state changed by ACPI to D0
[   24.710817] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[   24.710825] pci 0000:01:05.0: PCI INT A -> Link[LNK0] -> GSI 10 (level, low) -> IRQ 10
[   24.933961] [drm] Initialized drm 1.1.0 20060810
[   24.974853] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   25.643429] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   25.643464] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   25.643518] pci 0000:01:05.0: putting AGP V2 device into 4x mode
[   25.791358] [drm] Setting GART location based on new memory map
[   25.791375] [drm] Loading R100 Microcode
[   25.791429] [drm] writeback test succeeded in 1 usecs
[   28.482740] eth0: DSPCFG accepted after 0 usec.
[   28.482882] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.804449] eth1: autonegotiation failed; using 10mbs
[   33.804460] eth1: MII selected
[   33.828187] eth1: media 10BaseT, silicon revision 4
[   44.476054] eth1: no IPv6 routers present
[   81.000985] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   81.571467] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   82.050154] psmouse serio1: ID: 00 00 3c<6>input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input8
[   87.264065] Clocksource tsc unstable (delta = -150158703 ns)
[   97.516082] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   97.696083] usb 1-2: device descriptor read/64, error -62
[   97.980083] usb 1-2: device descriptor read/64, error -62
[   98.260081] usb 1-2: new full speed USB device using ohci_hcd and address 3
[   98.440083] usb 1-2: device descriptor read/64, error -62
[   98.728087] usb 1-2: device descriptor read/64, error -62
[   99.008082] usb 1-2: new full speed USB device using ohci_hcd and address 4
[   99.416134] usb 1-2: device not accepting address 4, error -62
[   99.592138] usb 1-2: new full speed USB device using ohci_hcd and address 5
[  100.000105] usb 1-2: device not accepting address 5, error -62
[  100.000158] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 1376.681592] ath_hal: module license 'Proprietary' taints kernel.
[ 1376.685921] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[ 1376.727726] wlan: 0.9.4
[ 1376.750005] ath_pci: 0.9.4
[ 3903.943561] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 3903.943571] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 3903.943576] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[ 3912.388109] usb 1-2: new full speed USB device using ohci_hcd and address 6
[ 3912.568082] usb 1-2: device descriptor read/64, error -62
[ 3912.852091] usb 1-2: device descriptor read/64, error -62
[ 3913.132099] usb 1-2: new full speed USB device using ohci_hcd and address 7
[ 3913.312094] usb 1-2: device descriptor read/64, error -62
[ 3913.600125] usb 1-2: device descriptor read/64, error -62
[ 3913.880082] usb 1-2: new full speed USB device using ohci_hcd and address 8
[ 3914.288126] usb 1-2: device not accepting address 8, error -62
[ 3914.464114] usb 1-2: new full speed USB device using ohci_hcd and address 9
[ 3914.872116] usb 1-2: device not accepting address 9, error -62
[ 3914.872167] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 4078.237266] eth0: remaining active for wake-on-lan
[ 4081.776879] eth0: DSPCFG accepted after 0 usec.
[ 4081.777042] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4086.104440] eth1: autonegotiation failed; using 10mbs
[ 4086.104453] eth1: MII selected
[ 4086.128093] eth1: media 10BaseT, silicon revision 4
[ 4096.572065] eth1: no IPv6 routers present
[ 4178.640089] usb 1-2: new full speed USB device using ohci_hcd and address 10
[ 4178.820101] usb 1-2: device descriptor read/64, error -62
[ 4179.104116] usb 1-2: device descriptor read/64, error -62
[ 4179.384149] usb 1-2: new full speed USB device using ohci_hcd and address 11
[ 4179.564157] usb 1-2: device descriptor read/64, error -62
[ 4179.848115] usb 1-2: device descriptor read/64, error -62
[ 4180.128108] usb 1-2: new full speed USB device using ohci_hcd and address 12
[ 4180.536103] usb 1-2: device not accepting address 12, error -62
[ 4180.712147] usb 1-2: new full speed USB device using ohci_hcd and address 13
[ 4181.120131] usb 1-2: device not accepting address 13, error -62
[ 4181.120184] hub 1-0:1.0: unable to enumerate USB device on port 2


Any suggestion?

---

