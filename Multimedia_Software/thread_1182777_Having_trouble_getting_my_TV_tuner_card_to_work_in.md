---
title: "Having trouble getting my TV tuner card to work in ubuntu 9.04"
date: 2009-06-09
forum: Multimedia Software
---

### Post by turino on 2009-06-09
I recently switched over to ubuntu and am trying to get my tv tuner card to work to no avail. I ran lspci and ubuntu recognizes the hardware:


ubuntu@ubuntu-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0b.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV515 PRO [Radeon X1300/X1550 Series] (Secondary)

I've tried numerous tutorials on line and through books but cant get it to work.

---

### Post by steefjeqv on 2009-06-09
Hi,

What kind of TV card are you using (analog, digital, satellite,...).

You can check your dmesg output to see if your system fully loads all of the necessary modules.

lsmod output should also be helpful.

Greetings,
Steven

---

### Post by turino on 2009-06-10
I checked both and here are the results:


[    0.541240] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541244] pci 0000:00:10.2: PME# disabled
[    0.541271] pci 0000:00:10.3: reg 10 32bit mmio: [0xe8006000-0xe80060ff]
[    0.541300] pci 0000:00:10.3: supports D1 D2
[    0.541302] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541307] pci 0000:00:10.3: PME# disabled
[    0.541363] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.541371] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
[    0.541375] pci 0000:00:11.0: quirk: region 5000-500f claimed by vt8235 SMB
[    0.541424] pci 0000:00:11.1: reg 20 io port: [0xe400-0xe40f]
[    0.541473] pci 0000:00:12.0: reg 10 io port: [0xe800-0xe8ff]
[    0.541480] pci 0000:00:12.0: reg 14 32bit mmio: [0xe8007000-0xe80070ff]
[    0.541506] pci 0000:00:12.0: supports D1 D2
[    0.541508] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541512] pci 0000:00:12.0: PME# disabled
[    0.541578] pci 0000:01:00.0: reg 10 64bit mmio: [0xc0000000-0xcfffffff]
[    0.541588] pci 0000:01:00.0: reg 18 64bit mmio: [0xd1000000-0xd100ffff]
[    0.541594] pci 0000:01:00.0: reg 20 io port: [0xc000-0xc0ff]
[    0.541604] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.541613] pci 0000:01:00.0: supports D1 D2
[    0.541649] pci 0000:01:00.1: reg 10 64bit mmio: [0xd1010000-0xd101ffff]
[    0.541676] pci 0000:01:00.1: supports D1 D2
[    0.541711] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.541715] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xdfffffff]
[    0.541724] bus 00 -> node 0
[    0.541732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.563538] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[    0.563756] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 *10 11 12)
[    0.563976] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12)
[    0.564203] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *5
[    0.564393] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.564576] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.564758] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.564940] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.565187] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.565427] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.565690] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.565928] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.566261] ACPI: Power Resource [PFAN] (on)
[    0.566357] ACPI: WMI: Mapper loaded
[    0.566696] SCSI subsystem initialized
[    0.566764] libata version 3.00 loaded.
[    0.566835] usbcore: registered new interface driver usbfs
[    0.566858] usbcore: registered new interface driver hub
[    0.566896] usbcore: registered new device driver usb
[    0.567060] PCI: Using ACPI for IRQ routing
[    0.567178] Bluetooth: Core ver 2.13
[    0.567178] NET: Registered protocol family 31
[    0.567178] Bluetooth: HCI device and connection manager initialized
[    0.567178] Bluetooth: HCI socket layer initialized
[    0.567178] NET: Registered protocol family 8
[    0.567178] NET: Registered protocol family 20
[    0.567178] NetLabel: Initializing
[    0.567178] NetLabel:  domain hash size = 128
[    0.567178] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.567178] NetLabel:  unlabeled traffic allowed by default
[    0.567178] AppArmor: AppArmor Filesystem Enabled
[    0.567178] pnp: PnP ACPI init
[    0.567178] ACPI: bus type pnp registered
[    0.570908] pnp: PnP ACPI: found 12 devices
[    0.570910] ACPI: ACPI bus type pnp unregistered
[    0.570915] PnPBIOS: Disabled by ACPI PNP
[    0.570930] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[    0.570933] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[    0.570936] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.570939] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.570942] system 00:00: iomem range 0x3fef0000-0x3fefffff could not be reserved
[    0.570945] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.570948] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.570951] system 00:00: iomem range 0x100000-0x3feeffff could not be reserved
[    0.570954] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.570957] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.570960] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.570967] system 00:02: ioport range 0x4000-0x407f has been reserved
[    0.570970] system 00:02: ioport range 0x5000-0x500f has been reserved
[    0.570976] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.570978] system 00:03: ioport range 0x294-0x297 has been reserved
[    0.605738] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.605742] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.605748] pci 0000:00:01.0:   MEM window: 0xc0000000-0xdfffffff
[    0.605752] pci 0000:00:01.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
[    0.605769] pci 0000:00:01.0: setting latency timer to 64
[    0.605774] bus: 00 index 0 io port: [0x00-0xffff]
[    0.605777] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.605779] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.605781] bus: 01 index 1 mmio: [0xc0000000-0xdfffffff]
[    0.605783] bus: 01 index 2 mmio: [0x40000000-0x400fffff]
[    0.605785] bus: 01 index 3 mmio: [0x0-0x0]
[    0.605803] NET: Registered protocol family 2
[    0.605957] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.606458] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.608826] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.609990] TCP: Hash tables configured (established 131072 bind 65536)
[    0.609996] TCP reno registered
[    0.610191] NET: Registered protocol family 1
[    0.610400] checking if image is initramfs... it is
[    1.108059] Switched to high resolution mode on CPU 0
[    1.303957] Freeing initrd memory: 7501k freed
[    1.304133] cpufreq: No nForce2 chipset.
[    1.304364] audit: initializing netlink socket (disabled)
[    1.304400] type=2000 audit(1244626760.304:1): initialized
[    1.312236] highmem bounce pool size: 64 pages
[    1.312244] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.313657] VFS: Disk quotas dquot_6.5.1
[    1.313721] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.314390] fuse init (API version 7.10)
[    1.314479] msgmni has been set to 1724
[    1.314744] alg: No test for stdrng (krng)
[    1.314762] io scheduler noop registered
[    1.314764] io scheduler anticipatory registered
[    1.314767] io scheduler deadline registered
[    1.314784] io scheduler cfq registered (default)
[    1.314806] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.314893] pci 0000:01:00.0: Boot video device
[    1.318334] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.318345] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.318527] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.318531] ACPI: Power Button (FF) [PWRF]
[    1.318580] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.318583] ACPI: Power Button (CM) [PWRB]
[    1.318636] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.318645] ACPI: Sleep Button (CM) [SLPB]
[    1.319894] fan PNP0C0B:00: registered as cooling_device0
[    1.319900] ACPI: Fan [FAN] (on)
[    1.320164] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.320183] processor ACPI_CPU:00: registered as cooling_device1
[    1.323754] thermal LNXTHERM:01: registered as thermal_zone0
[    1.325888] ACPI: Transitioning device [FAN] to D3
[    1.327042] ACPI: Thermal Zone [THRM] (69 C)
[    1.327087] isapnp: Scanning for PnP cards...
[    1.680678] isapnp: No Plug & Play device found
[    1.682285] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.682393] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.682718] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.683627] brd: module loaded
[    1.683997] loop: module loaded
[    1.684160] Fixed MDIO Bus: probed
[    1.684168] PPP generic driver version 2.4.2
[    1.684242] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.684300] Driver 'sd' needs updating - please use bus_type methods
[    1.684311] Driver 'sr' needs updating - please use bus_type methods
[    1.684890] pata_via 0000:00:11.1: version 0.3.3
[    1.685387] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    1.685390] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    1.685405] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.685767] scsi0 : pata_via
[    1.685927] scsi1 : pata_via
[    1.687738] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    1.687742] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    1.848353] ata1.00: ATAPI: ATAPI   iHAP122   8, UL04, max UDMA/66
[    1.848381] ata1.01: ATAPI: CRD-8400C, 1.02, max MWDMA2
[    1.864232] ata1.00: configured for UDMA/66
[    1.880237] ata1.01: configured for MWDMA2
[    2.052462] ata2.00: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100
[    2.052465] ata2.00: 156301488 sectors, multi 16: LBA 
[    2.053406] ata2.01: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
[    2.053409] ata2.01: 78165360 sectors, multi 16: LBA 
[    2.060337] ata2.00: configured for UDMA/100
[    2.077140] ata2.01: configured for UDMA/100
[    2.078346] scsi 0:0:0:0: CD-ROM            ATAPI    iHAP122   8      UL04 PQ: 0 ANSI: 5
[    2.084773] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.084778] Uniform CD-ROM driver Revision: 3.20
[    2.084951] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.085032] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.085303] scsi 0:0:1:0: CD-ROM            LG       CD-ROM CRD-8400C 1.02 PQ: 0 ANSI: 5
[    2.087046] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[    2.087123] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    2.087167] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.087245] scsi 1:0:0:0: Direct-Access     ATA      WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5
[    2.087363] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.087385] sd 1:0:0:0: [sda] Write Protect is off
[    2.087388] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.087422] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.087496] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.087514] sd 1:0:0:0: [sda] Write Protect is off
[    2.087517] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.087548] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.087554]  sda: sda1
[    2.108038] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.108095] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    2.108181] scsi 1:0:1:0: Direct-Access     ATA      WDC WD400EB-11CP 06.0 PQ: 0 ANSI: 5
[    2.108282] sd 1:0:1:0: [sdb] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.108302] sd 1:0:1:0: [sdb] Write Protect is off
[    2.108305] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.108336] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.108400] sd 1:0:1:0: [sdb] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.108418] sd 1:0:1:0: [sdb] Write Protect is off
[    2.108421] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.108452] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.108457]  sdb: sdb1 sdb2 < sdb5 >
[    2.164481] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.164534] sd 1:0:1:0: Attached scsi generic sg3 type 0
[    2.164751] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.165232] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    2.165236] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    2.165248] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.165291] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    2.165370] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    2.165457] ehci_hcd 0000:00:10.3: irq 21, io mem 0xe8006000
[    2.176024] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    2.176127] usb usb1: configuration #1 chosen from 1 choice
[    2.176160] hub 1-0:1.0: USB hub found
[    2.176176] hub 1-0:1.0: 6 ports detected
[    2.176303] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.176334] uhci_hcd: USB Universal Host Controller Interface driver
[    2.176413] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.176423] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    2.176474] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    2.176496] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d800
[    2.176592] usb usb2: configuration #1 chosen from 1 choice
[    2.176618] hub 2-0:1.0: USB hub found
[    2.176631] hub 2-0:1.0: 2 ports detected
[    2.176736] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.176743] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    2.176790] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    2.176809] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
[    2.176901] usb usb3: configuration #1 chosen from 1 choice
[    2.176927] hub 3-0:1.0: USB hub found
[    2.176938] hub 3-0:1.0: 2 ports detected
[    2.177031] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    2.177038] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    2.177084] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    2.177103] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[    2.177199] usb usb4: configuration #1 chosen from 1 choice
[    2.177224] hub 4-0:1.0: USB hub found
[    2.177235] hub 4-0:1.0: 2 ports detected
[    2.177378] usbcore: registered new interface driver libusual
[    2.177423] usbcore: registered new interface driver usbserial
[    2.177436] USB Serial support registered for generic
[    2.177450] usbcore: registered new interface driver usbserial_generic
[    2.177453] usbserial: USB Serial Driver core
[    2.177509] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.177938] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.177948] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.178106] mice: PS/2 mouse device common for all mice
[    2.178301] rtc_cmos 00:05: RTC can wake from S4
[    2.178356] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.178405] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    2.178524] device-mapper: uevent: version 1.0.3
[    2.178697] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.178775] device-mapper: multipath: version 1.0.5 loaded
[    2.178779] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.178903] EISA: Probing bus 0 at eisa.0
[    2.178925] Cannot allocate resource for EISA slot 4
[    2.178927] Cannot allocate resource for EISA slot 5
[    2.178941] EISA: Detected 0 cards.
[    2.179017] cpuidle: using governor ladder
[    2.179067] cpuidle: using governor menu
[    2.179649] TCP cubic registered
[    2.179754] NET: Registered protocol family 10
[    2.180248] lo: Disabled Privacy Extensions
[    2.180594] NET: Registered protocol family 17
[    2.180621] Bluetooth: L2CAP ver 2.11
[    2.180623] Bluetooth: L2CAP socket layer initialized
[    2.180626] Bluetooth: SCO (Voice Link) ver 0.6
[    2.180629] Bluetooth: SCO socket layer initialized
[    2.180677] Bluetooth: RFCOMM socket layer initialized
[    2.180692] Bluetooth: RFCOMM TTY layer initialized
[    2.180694] Bluetooth: RFCOMM ver 1.10
[    2.180720] powernow-k8: Processor cpuid 681 not supported
[    2.180755] Using IPI No-Shortcut mode
[    2.180914] registered taskstats version 1
[    2.181066]   Magic number: 13:834:676
[    2.181246] rtc_cmos 00:05: setting system clock to 2009-06-10 09:39:21 UTC (1244626761)
[    2.181250] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.181253] EDD information not available.
[    2.182224] Freeing unused kernel memory: 532k freed
[    2.182364] Write protecting the kernel text: 4128k
[    2.182405] Write protecting the kernel read-only data: 1532k
[    2.221570] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.508044] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.649062] usb 1-1: configuration #1 chosen from 1 choice
[    2.658578] Initializing USB Mass Storage driver...
[    2.664927] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.666526] usbcore: registered new interface driver usb-storage
[    2.666534] USB Mass Storage support registered.
[    2.666698] usb-storage: device found at 2
[    2.666700] usb-storage: waiting for device to settle before scanning
[    2.693144] ohci1394 0000:00:09.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.743098] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[e8004000-e80047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.930094] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    2.930102] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    2.930588] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    2.930592] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    2.930607] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    2.935785] eth0: VIA Rhine II at 0xe8007000, 00:50:8d:4f:2f:d5, IRQ 23.
[    2.936487] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[    3.176067] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    3.356949] usb 3-1: configuration #1 chosen from 1 choice
[    3.532009] Marking TSC unstable due to TSC halts in idle
[    3.589879] PM: Starting manual resume from disk
[    3.589886] PM: Resume from partition 8:21
[    3.589887] PM: Checking hibernation image.
[    3.590130] PM: Resume from disk failed.
[    3.600065] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    3.650167] kjournald starting.  Commit interval 5 seconds
[    3.650197] EXT3-fs: mounted filesystem with ordered data mode.
[    3.724064] usb 4-1: device descriptor read/64, error -71
[    3.948056] usb 4-1: device descriptor read/64, error -71
[    4.084233] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c009106838a]
[    4.164054] usb 4-1: new full speed USB device using uhci_hcd and address 3
[    4.284062] usb 4-1: device descriptor read/64, error -71
[    4.508056] usb 4-1: device descriptor read/64, error -71
[    4.724051] usb 4-1: new full speed USB device using uhci_hcd and address 4
[    5.140043] usb 4-1: device not accepting address 4, error -71
[    5.252072] usb 4-1: new full speed USB device using uhci_hcd and address 5
[    5.660045] usb 4-1: device not accepting address 5, error -71
[    5.660082] hub 4-0:1.0: unable to enumerate USB device on port 1
[    7.664280] usb-storage: device scan complete
[    7.664854] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[    7.665827] sd 2:0:0:0: [sdc] 3913728 512-byte hardware sectors: (2.00 GB/1.86 GiB)
[    7.666321] sd 2:0:0:0: [sdc] Write Protect is off
[    7.666325] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    7.666328] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    7.667948] sd 2:0:0:0: [sdc] 3913728 512-byte hardware sectors: (2.00 GB/1.86 GiB)
[    7.668445] sd 2:0:0:0: [sdc] Write Protect is off
[    7.668448] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    7.668450] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    7.668455]  sdc: sdc1
[    7.669224] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[    7.669326] sd 2:0:0:0: Attached scsi generic sg4 type 0
[   13.264460] udev: starting version 141
[   13.415488] Linux agpgart interface v0.103
[   13.769950] parport_pc 00:09: reported by Plug and Play ACPI
[   13.770064] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   13.883497] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.243622] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   14.253677] agpgart-via 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   14.390439] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1074
[   14.390476] usbcore: registered new interface driver usblp
[   14.825872] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   14.913667] gameport: EMU10K1 is pci0000:00:09.1/gameport0, io 0xd400, speed 1217kHz
[   14.936734] irda_init()
[   14.936766] NET: Registered protocol family 23
[   14.949874] ppdev: user-space parallel port driver
[   15.071809] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   15.122246] Linux video capture interface: v2.00
[   15.352612] saa7130/34: v4l2 driver version 0.2.14 loaded
[   15.352927] saa7134 0000:00:0b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.352935] saa7133[0]: found at 0000:00:0b.0, rev: 16, irq: 19, latency: 32, mmio: 0xe8005000
[   15.352944] saa7133[0]: subsystem: 16be:0004, board: UNKNOWN/GENERIC [card=0,autodetected]
[   15.353077] saa7133[0]: board init: gpio is 0
[   15.516383] saa7133[0]: i2c eeprom 00: be 16 04 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   15.516395] saa7133[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0a c0 08 00 00 00 00 00
[   15.516404] saa7133[0]: i2c eeprom 20: 00 00 00 e1 ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516412] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516420] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516428] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516435] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516443] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516451] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516459] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516467] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516475] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516483] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516491] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516499] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.516507] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.517082] saa7133[0]: registered device video0 [v4l2]
[   15.517144] saa7133[0]: registered device vbi0
[   15.550092] saa7134 ALSA driver for DMA sound loaded
[   15.550144] saa7133[0]/alsa: saa7133[0] at 0xe8005000 irq 19 registered as card -2
[   15.596876] EMU10K1_Audigy 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.599327] Installing spdif_bug patch: Audigy 2 Platinum [SB0240P]
[   15.610014] psmouse serio1: ID: 10 00 64<4>Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback '
[   16.005102] lp0: using parport0 (interrupt-driven).
[   16.162044] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   16.213478] Adding 1646620k swap on /dev/sdb5.  Priority:-1 extents:1 across:1646620k
[   16.793932] EXT3 FS on sdb1, internal journal
[   19.555282] type=1505 audit(1244641178.870:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2263
[   19.634342] type=1505 audit(1244641178.950:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2267
[   19.634801] type=1505 audit(1244641178.950:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2267
[   19.634916] type=1505 audit(1244641178.950:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2267
[   19.635010] type=1505 audit(1244641178.950:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2267
[   19.857908] type=1505 audit(1244641179.174:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2272
[   19.858460] type=1505 audit(1244641179.174:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2272
[   19.908259] type=1505 audit(1244641179.226:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2276
[   21.174438] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   24.973879] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.973885] Bluetooth: BNEP filters: protocol multicast
[   24.988090] usb 4-1: new full speed USB device using uhci_hcd and address 6
[   25.032066] Bridge firewalling registered
[   25.112078] usb 4-1: device descriptor read/64, error -71
[   25.336058] usb 4-1: device descriptor read/64, error -71
[   25.552059] usb 4-1: new full speed USB device using uhci_hcd and address 7
[   25.677409] usb 4-1: device descriptor read/64, error -71
[   25.900063] usb 4-1: device descriptor read/64, error -71
[   26.116051] usb 4-1: new full speed USB device using uhci_hcd and address 8
[   26.524048] usb 4-1: device not accepting address 8, error -71
[   26.636072] usb 4-1: new full speed USB device using uhci_hcd and address 9
[   27.052037] usb 4-1: device not accepting address 9, error -71
[   27.052075] hub 4-0:1.0: unable to enumerate USB device on port 1
[   27.124406] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   27.812618] [drm] Initialized drm 1.1.0 20060810
[   28.060327] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   28.609368] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   28.609400] agpgart-via 0000:00:00.0: putting AGP V3 device into 4x mode
[   28.609464] pci 0000:01:00.0: putting AGP V3 device into 4x mode
[   28.697075] [drm] Setting GART location based on new memory map
[   28.697087] [drm] Loading R500 Microcode
[   28.697168] [drm] Num pipes: 1
[   28.697178] [drm] writeback test succeeded in 1 usecs
[   31.808016] eth0: no IPv6 routers present
[   32.572061] usb 4-1: new full speed USB device using uhci_hcd and address 10
[   32.696056] usb 4-1: device descriptor read/64, error -71
[   32.920070] usb 4-1: device descriptor read/64, error -71
[   33.144585] usb 4-1: new full speed USB device using uhci_hcd and address 11
[   33.268057] usb 4-1: device descriptor read/64, error -71
[   33.496059] usb 4-1: device descriptor read/64, error -71
[   33.712054] usb 4-1: new full speed USB device using uhci_hcd and address 12
[   34.124036] usb 4-1: device not accepting address 12, error -71
[   34.236051] usb 4-1: new full speed USB device using uhci_hcd and address 13
[   34.644040] usb 4-1: device not accepting address 13, error -71
[   34.644073] hub 4-0:1.0: unable to enumerate USB device on port 1
[   34.644313] ppdev0: registered pardevice
[   34.692396] ppdev0: unregistered pardevice
[ 8356.008056] usb 4-1: new full speed USB device using uhci_hcd and address 14
[ 8356.128056] usb 4-1: device descriptor read/64, error -71
[ 8356.352044] usb 4-1: device descriptor read/64, error -71
[ 8356.568040] usb 4-1: new full speed USB device using uhci_hcd and address 15
[ 8356.688031] usb 4-1: device descriptor read/64, error -71
[ 8356.912061] usb 4-1: device descriptor read/64, error -71
[ 8357.128034] usb 4-1: new full speed USB device using uhci_hcd and address 16
[ 8357.540039] usb 4-1: device not accepting address 16, error -71
[ 8357.652038] usb 4-1: new full speed USB device using uhci_hcd and address 17
[ 8358.060051] usb 4-1: device not accepting address 17, error -71
[ 8358.060086] hub 4-0:1.0: unable to enumerate USB device on port 1
[ 8814.230694] audacity[11283]: segfault at b5e69912 ip b5e69912 sp b1635170 error 4
ubuntu@ubuntu-desktop:~$ lsmod output
Usage: lsmod
ubuntu@ubuntu-desktop:~$ 

Its an analog tuner

---

### Post by steefjeqv on 2009-06-14
Hi,

Sorry for the late reply.

This is the problem :
[ 15.352944] saa7133[0]: subsystem: 16be:0004, board: UNKNOWN/GENERIC [card=0,autodetected]

Your card isn't properly detected (UNKNOWN/GENERIC).

Do you know the make of your TV card ?
Perhaps you'll be able to get it recognized by using the "card=xxx" option.

Greetings,
Steven

---

