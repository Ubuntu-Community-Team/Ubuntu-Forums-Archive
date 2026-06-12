---
title: "EVDO mobile broadband"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by nakul123 on 2011-09-06
**I followed many threads and ended with no result of Using EVDO in unbuntu 9.04 **                                       as thread i followed i done follwing things
- I added information of my USB device "qualcomm" 05c6:2001" in menu.lst
- after that my device was detected in ./dev/ttyUSB0
I configure my Wvdial.conf as
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = #777
Modem = /dev/ttyUSB0
Username = xxxx
Password = xxxx
Baud = 460800
Stupid Mode = 1 

**and after "wvdial" command it shows**
nakul@nakul-laptop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> **Modem not responding.**

**also wvdialconf shows following**

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)


Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

**also "dmesg" shows following:**

[    0.606849] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.606853] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.606856] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.606865] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.606874] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.606877] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.606880] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.606884] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.606887] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.606891] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[    0.641677] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.641680] pci 0000:00:1c.0:   IO window: disabled
[    0.641688] pci 0000:00:1c.0:   MEM window: disabled
[    0.641693] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.641703] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.641705] pci 0000:00:1c.1:   IO window: disabled
[    0.641713] pci 0000:00:1c.1:   MEM window: 0xf0300000-0xf03fffff
[    0.641719] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.641729] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:04
[    0.641734] pci 0000:00:1c.5:   IO window: 0x2000-0x2fff
[    0.641742] pci 0000:00:1c.5:   MEM window: 0xf0200000-0xf02fffff
[    0.641748] pci 0000:00:1c.5:   PREFETCH window: 0x00000054000000-0x000000540fffff
[    0.641760] pci 0000:05:07.0: CardBus bridge, secondary bus 0000:06
[    0.641763] pci 0000:05:07.0:   IO window: 0x003000-0x0030ff
[    0.641769] pci 0000:05:07.0:   IO window: 0x003400-0x0034ff
[    0.641776] pci 0000:05:07.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.641783] pci 0000:05:07.0:   MEM window: 0x58000000-0x5bffffff
[    0.641790] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.641795] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.641802] pci 0000:00:1e.0:   MEM window: 0xf0400000-0xf04fffff
[    0.641808] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.641830] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.641837] pci 0000:00:1c.0: setting latency timer to 64
[    0.641849] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.641855] pci 0000:00:1c.1: setting latency timer to 64
[    0.641866] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.641872] pci 0000:00:1c.5: setting latency timer to 64
[    0.641882] pci 0000:00:1e.0: setting latency timer to 64
[    0.641895] pci 0000:05:07.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.641903] bus: 00 index 0 io port: [0x00-0xffff]
[    0.641906] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.641909] bus: 02 index 0 mmio: [0x0-0x0]
[    0.641911] bus: 02 index 1 mmio: [0x0-0x0]
[    0.641913] bus: 02 index 2 mmio: [0x0-0x0]
[    0.641915] bus: 02 index 3 mmio: [0x0-0x0]
[    0.641918] bus: 03 index 0 mmio: [0x0-0x0]
[    0.641920] bus: 03 index 1 mmio: [0xf0300000-0xf03fffff]
[    0.641923] bus: 03 index 2 mmio: [0x0-0x0]
[    0.641925] bus: 03 index 3 mmio: [0x0-0x0]
[    0.641928] bus: 04 index 0 io port: [0x2000-0x2fff]
[    0.641931] bus: 04 index 1 mmio: [0xf0200000-0xf02fffff]
[    0.641933] bus: 04 index 2 mmio: [0x54000000-0x540fffff]
[    0.641936] bus: 04 index 3 mmio: [0x0-0x0]
[    0.641938] bus: 05 index 0 io port: [0x3000-0x3fff]
[    0.641941] bus: 05 index 1 mmio: [0xf0400000-0xf04fffff]
[    0.641943] bus: 05 index 2 mmio: [0x50000000-0x53ffffff]
[    0.641946] bus: 05 index 3 io port: [0x00-0xffff]
[    0.641949] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    0.641951] bus: 06 index 0 io port: [0x3000-0x30ff]
[    0.641954] bus: 06 index 1 io port: [0x3400-0x34ff]
[    0.641956] bus: 06 index 2 mmio: [0x50000000-0x53ffffff]
[    0.641959] bus: 06 index 3 mmio: [0x58000000-0x5bffffff]
[    0.641969] NET: Registered protocol family 2
[    0.656066] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.656371] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.656783] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.656999] TCP: Hash tables configured (established 131072 bind 65536)
[    0.657002] TCP reno registered
[    0.664077] NET: Registered protocol family 1
[    0.664226] checking if image is initramfs... it is
[    1.464300] Freeing initrd memory: 7373k freed
[    1.464357] Simple Boot Flag at 0x36 set to 0x1
[    1.464571] cpufreq: No nForce2 chipset.
[    1.464749] audit: initializing netlink socket (disabled)
[    1.464778] type=2000 audit(1314924679.464:1): initialized
[    1.474060] highmem bounce pool size: 64 pages
[    1.474066] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.475767] VFS: Disk quotas dquot_6.5.1
[    1.475842] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.476609] fuse init (API version 7.10)
[    1.476717] msgmni has been set to 1724
[    1.476935] alg: No test for stdrng (krng)
[    1.476947] io scheduler noop registered
[    1.476950] io scheduler anticipatory registered
[    1.476953] io scheduler deadline registered
[    1.476970] io scheduler cfq registered (default)
[    1.476983] pci 0000:00:02.0: Boot video device
[    1.479693] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.479753] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.479797] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.479816] pci_express 0000:00:1c.0xxcie00: allocate port service
[    1.479833] pci_express 0000:00:1c.0xxcie02: allocate port service
[    1.479849] pci_express 0000:00:1c.0xxcie03: allocate port service
[    1.479938] pcieport-driver 0000:00:1xxc.1: setting latency timer to 64
[    1.479996] pcieport-driver 0000:00:1xxc.1: found MSI capability
[    1.480035] pcieport-driver 0000:00:1xxc.1: irq 2302 for MSI/MSI-X
[    1.480054] pci_express 0000:00:1c.1xxcie00: allocate port service
[    1.480070] pci_express 0000:00:1c.1xxcie02: allocate port service
[    1.480085] pci_express 0000:00:1c.1xxcie03: allocate port service
[    1.480172] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.480230] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.480269] pcieport-driver 0000:00:1c.5: irq 2301 for MSI/MSI-X
[    1.480288] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.480308] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.480323] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.480423] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.480756] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.481345] ACPI: AC Adapter [ACAD] (on-line)
[    1.499577] ACPI: Battery Slot [BAT0] (battery present)
[    1.499676] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.499679] ACPI: Power Button (FF) [PWRF]
[    1.499734] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.499795] ACPI: Lid Switch [LID]
[    1.499847] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.499851] ACPI: Power Button (CM) [PWRB]
[    1.500022] fan PNP0C0B:00: registered as cooling_device0
[    1.500030] ACPI: Fan [FAN2] (off)
[    1.500142] fan PNP0C0B:01: registered as cooling_device1
[    1.500149] ACPI: Fan [FAN0] (off)
[    1.500259] fan PNP0C0B:02: registered as cooling_device2
[    1.500266] ACPI: Fan [FAN1] (off)
[    1.500940] ACPI: SSDT 3F6D5274, 01B4 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.501457] ACPI: SSDT 3F6D4D45, 04AA (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.504276] Monitor-Mwait will be used to enter C-1 state
[    1.504280] Monitor-Mwait will be used to enter C-2 state
[    1.504284] Monitor-Mwait will be used to enter C-3 state
[    1.504301] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.504326] processor ACPI_CPU:00: registered as cooling_device3
[    1.504331] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.504760] ACPI: SSDT 3F6D5428, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.505223] ACPI: SSDT 3F6D51EF, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.506369] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.506393] processor ACPI_CPU:01: registered as cooling_device4
[    1.506398] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.510162] thermal LNXTHERM:01: registered as thermal_zone0
[    1.511579] ACPI: Thermal Zone [TZ00] (37 C)
[    1.512240] thermal LNXTHERM:02: registered as thermal_zone1
[    1.512479] ACPI: Thermal Zone [TZ01] (27 C)
[    1.512550] isapnp: Scanning for PnP cards...
[    1.866649] isapnp: No Plug & Play device found
[    1.873294] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.874573] brd: module loaded
[    1.874959] loop: module loaded
[    1.875038] Fixed MDIO Bus: probed
[    1.875045] PPP generic driver version 2.4.2
[    1.875123] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.875161] Driver 'sd' needs updating - please use bus_type methods
[    1.875173] Driver 'sr' needs updating - please use bus_type methods
[    1.875222] ahci 0000:00:1f.2: version 3.0
[    1.875240] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.875291] ahci 0000:00:1f.2: irq 2300 for MSI/MSI-X
[    1.875369] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.875373] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    1.875380] ahci 0000:00:1f.2: setting latency timer to 64
[    1.875659] scsi0 : ahci
[    1.875764] scsi1 : ahci
[    1.875837] scsi2 : ahci
[    1.875961] ata1: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704100 irq 2300
[    1.875965] ata2: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704180 irq 2300
[    1.875969] ata3: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704200 irq 2300
[    2.192023] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.192615] ACPI Warning (nspredef-0852): \_SB_.PCI0.SATA.PRT0._GTF:  Return type mismatch - found Integer, expected Buffer [20080926]
[    2.192624] ata1.00: _GTF unexpected object type 0x1
[    2.242504] ata1.00: ATA-7: WDC WD1600BEVS-00RST0, 04.01G04, max UDMA/133
[    2.242507] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.243377] ata1.00: _GTF unexpected object type 0x1
[    2.243538] ata1.00: configured for UDMA/133
[    2.576020] ata2: SATA link down (SStatus 0 SControl 300)
[    2.912021] ata3: SATA link down (SStatus 0 SControl 300)
[    2.928128] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 04.0 PQ: 0 ANSI: 5
[    2.928242] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.928263] sd 0:0:0:0: [sda] Write Protect is off
[    2.928266] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.928298] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.928375] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.928393] sd 0:0:0:0: [sda] Write Protect is off
[    2.928396] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.928428] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.928432]  sda: sda1 sda2 < sda5 >
[    2.999878] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.999930] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.999988] ata_piix 0000:00:1f.1: version 2.12
[    2.999997] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.000040] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.000121] scsi3 : ata_piix
[    3.000189] scsi4 : ata_piix
[    3.000978] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.000981] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.164438] ata4.00: ATAPI: Optiarc DVD RW AD-7530B, NX03, max UDMA/33
[    3.180381] ata4.00: configured for UDMA/33
[    3.348622] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX03 PQ: 0 ANSI: 5
[    3.358420] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.358424] Uniform CD-ROM driver Revision: 3.20
[    3.358534] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.358579] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.359409] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.359434] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.359451] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.359455] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.359524] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.363436] ehci_hcd 0000:00:1a.7: debug port 1
[    3.363444] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.363461] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0704800
[    3.376011] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.376094] usb usb1: configuration #1 chosen from 1 choice
[    3.376129] hub 1-0:1.0: USB hub found
[    3.376138] hub 1-0:1.0: 4 ports detected
[    3.376264] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.376277] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.376282] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.376336] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.380251] ehci_hcd 0000:00:1d.7: debug port 1
[    3.380259] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.380276] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0704c00
[    3.392011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.392077] usb usb2: configuration #1 chosen from 1 choice
[    3.392109] hub 2-0:1.0: USB hub found
[    3.392117] hub 2-0:1.0: 6 ports detected
[    3.392243] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.392264] uhci_hcd: USB Universal Host Controller Interface driver
[    3.392289] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.392297] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.392302] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.392352] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.392392] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    3.392483] usb usb3: configuration #1 chosen from 1 choice
[    3.392514] hub 3-0:1.0: USB hub found
[    3.392522] hub 3-0:1.0: 2 ports detected
[    3.392626] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.392634] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.392638] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.392691] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.392731] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    3.392821] usb usb4: configuration #1 chosen from 1 choice
[    3.392852] hub 4-0:1.0: USB hub found
[    3.392860] hub 4-0:1.0: 2 ports detected
[    3.392971] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.392981] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.392985] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.393044] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.393074] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    3.393161] usb usb5: configuration #1 chosen from 1 choice
[    3.393192] hub 5-0:1.0: USB hub found
[    3.393200] hub 5-0:1.0: 2 ports detected
[    3.393303] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.393311] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.393315] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.393365] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.393404] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    3.393498] usb usb6: configuration #1 chosen from 1 choice
[    3.393528] hub 6-0:1.0: USB hub found
[    3.393536] hub 6-0:1.0: 2 ports detected
[    3.393644] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.393653] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.393658] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.393715] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.393745] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    3.393831] usb usb7: configuration #1 chosen from 1 choice
[    3.393862] hub 7-0:1.0: USB hub found
[    3.393869] hub 7-0:1.0: 2 ports detected
[    3.394024] usbcore: registered new interface driver libusual
[    3.394061] usbcore: registered new interface driver usbserial
[    3.394074] USB Serial support registered for generic
[    3.394095] usbcore: registered new interface driver usbserial_generic
[    3.394097] usbserial: USB Serial Driver core
[    3.394162] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.408813] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.409473] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.409479] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.409483] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.409486] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.409489] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.413057] mice: PS/2 mouse device common for all mice
[    3.429085] rtc_cmos 00:07: RTC can wake from S4
[    3.429125] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.429160] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.429232] device-mapper: uevent: version 1.0.3
[    3.429331] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.429420] device-mapper: multipath: version 1.0.5 loaded
[    3.429423] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.429512] EISA: Probing bus 0 at eisa.0
[    3.429519] Cannot allocate resource for EISA slot 1
[    3.429523] Cannot allocate resource for EISA slot 2
[    3.429526] Cannot allocate resource for EISA slot 3
[    3.429552] EISA: Detected 0 cards.
[    3.429695] cpuidle: using governor ladder
[    3.429845] cpuidle: using governor menu
[    3.430490] TCP cubic registered
[    3.430613] NET: Registered protocol family 10
[    3.431147] lo: Disabled Privacy Extensions
[    3.431578] NET: Registered protocol family 17
[    3.431598] Bluetooth: L2CAP ver 2.11
[    3.431600] Bluetooth: L2CAP socket layer initialized
[    3.431604] Bluetooth: SCO (Voice Link) ver 0.6
[    3.431606] Bluetooth: SCO socket layer initialized
[    3.431642] Marking TSC unstable due to TSC halts in idle
[    3.431653] Bluetooth: RFCOMM socket layer initialized
[    3.431659] Bluetooth: RFCOMM TTY layer initialized
[    3.431661] Bluetooth: RFCOMM ver 1.10

[    3.432402] Using IPI No-Shortcut mode
[    3.432488] registered taskstats version 1
[    3.432631]   Magic number: 11:502:859
[    3.432739] rtc_cmos 00:07: setting system clock to 2011-09-02 00:51:22 UTC (1314924682)
[    3.432743] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.432745] EDD information not available.
[    3.433101] Freeing unused kernel memory: 532k freed
[    3.433298] Write protecting the kernel text: 4128k
[    3.433374] Write protecting the kernel read-only data: 1532k
[    3.467806] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.689028] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.693855] sky2 driver version 1.22
[    3.693910] sky2 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.693925] sky2 0000:04:00.0: setting latency timer to 64
[    3.693983] sky2 0000:04:00.0: Yukon-2 EC Ultra chip revision 3
[    3.725983] sky2 0000:04:00.0: Marvell Yukon 88E8055 Gigabit Ethernet Controller
[    3.725987]  Part Number: Yukon 88E8055
[    3.725990]  Engineering Level: Rev. 1.2
[    3.725992]  Manufacturer: Marvell
[    3.726078] sky2 0000:04:00.0: irq 2299 for MSI/MSI-X
[    3.728734] sky2 eth0: addr 00:14:0b:35:27:e3
[    3.826342] usb 1-2: configuration #1 chosen from 1 choice
[    4.070448] PM: Starting manual resume from disk
[    4.070452] PM: Resume from partition 8:5
[    4.070455] PM: Checking hibernation image.
[    4.070627] PM: Resume from disk failed.
[    4.094391] kjournald starting.  Commit interval 5 seconds
[    4.094402] EXT3-fs: mounted filesystem with ordered data mode.
[   10.240885] udev: starting version 141
[   10.355839] Linux agpgart interface v0.103
[   10.371853] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   10.372757] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   10.376029] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   10.380508] acpi device:05: registered as cooling_device5
[   10.381202] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input5
[   10.405121] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.461829] iTCO_vendor_support: vendor-support=0
[   10.463682] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.463872] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   10.463975] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.546568] cfg80211: Calling CRDA to update world regulatory domain
[   10.563748] Linux video capture interface: v2.00
[   10.573503] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   10.587783] yenta_cardbus 0000:05:07.0: CardBus bridge found [1509:2f02]
[   10.587815] yenta_cardbus 0000:05:07.0: Using CSCINT to route CSC interrupts to PCI
[   10.587818] yenta_cardbus 0000:05:07.0: Routing CardBus interrupts to PCI
[   10.587825] yenta_cardbus 0000:05:07.0: TI: mfunc 0x01021002, devctl 0x44
[   10.714294] uvcvideo: Found UVC 1.00 device USB 2.0 PC Cam (090c:b370)
[   10.750757] cfg80211: World regulatory domain updated:
[   10.750762]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.750765]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.750768]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.750771]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.750774]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.750777]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.756086] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.818744] input: USB 2.0 PC Cam as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input7
[   10.821458] yenta_cardbus 0000:05:07.0: ISA IRQ mask 0x0cf8, PCI irq 17
[   10.821463] yenta_cardbus 0000:05:07.0: Socket status: 30000006
[   10.821467] pci_bus 0000:05: Raising subordinate bus# of parent bus (#05) from #06 to #09
[   10.821475] yenta_cardbus 0000:05:07.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   10.821479] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   10.821804] yenta_cardbus 0000:05:07.0: pcmcia: parent PCI bridge Memory window: 0xf0400000 - 0xf04fffff
[   10.821808] yenta_cardbus 0000:05:07.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   10.821978] usbcore: registered new interface driver uvcvideo
[   10.822009] USB Video Class driver (v0.1.0)
[   10.907242] iwl3945: Intel® PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   10.907247] iwl3945: Copyright© 2003-2008 Intel Corporation
[   10.907330] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.907346] iwl3945 0000:03:00.0: setting latency timer to 64
[   10.907416] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   10.907610] iwl3945 0000:03:00.0: irq 2298 for MSI/MSI-X
[   10.964200] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.965324] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   11.169466] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.169556] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.203253] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   11.224207] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.226360] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   11.227278] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.228053] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.229027] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.597432] lp: driver loaded but no devices found
[   11.630186] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b1, caps: 0xa04713/0x204000
[   11.684442] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   11.694812] Adding 2980016k swap on /dev/sda5.  Priority:-1 extents:1 across:2980016k
[   12.245118] EXT3 FS on sda1, internal journal
[   12.500066] Clocksource tsc unstable (delta = -194615612 ns)
[   13.116062] iwl3945: Radio Frequency Kill Switch is On:
[   13.116065] Kill switch must be turned off for wireless networking to work.
[   13.504722] type=1505 audit(1314924692.568:2):  operation="profile_load" name="/usr/share/gdm/guest-session/Xsession"  name2="default" pid=2058
[   13.563312] type=1505 audit(1314924692.628:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2062
[   13.563435] type=1505 audit(1314924692.628:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2062
[   13.563487] type=1505 audit(1314924692.628:5):  operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default"  pid=2062
[   13.563534] type=1505 audit(1314924692.628:6):  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  name2="default" pid=2062
[   13.727488] type=1505 audit(1314924692.792:7):  operation="profile_load" name="/usr/lib/cups/backend/cups-pdf"  name2="default" pid=2067
[   13.727695] type=1505 audit(1314924692.792:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2067
[   13.762736] type=1505 audit(1314924692.828:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2071
[   16.008595] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.008599] Bluetooth: BNEP filters: protocol multicast
[   16.023523] Bridge firewalling registered
[   17.358818] ppdev: user-space parallel port driver
[   18.480200] [drm] Initialized drm 1.1.0 20060810
[   18.493596] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.493602] pci 0000:00:02.0: setting latency timer to 64
[   18.493781] pci 0000:00:02.0: irq 2297 for MSI/MSI-X
[   18.493880] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   18.495473] [drm:i915_setparam] *ERROR* unknown parameter 4
[   20.936784] sky2 eth0: enabling interface
[   20.937058] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.937890] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   21.004992] iwl3945: Radio disabled by HW RF Kill switch
[  184.868090] usb 6-1: new full speed USB device using uhci_hcd and address 2
[  185.026669] usb 6-1: configuration #1 chosen from 1 choice
[  185.029473] usbserial_generic 6-1:1.0: generic converter detected
[  185.029578] usb 6-1: generic converter now attached to ttyUSB0
[  185.106930] Initializing USB Mass Storage driver...
[  185.107039] usbcore: registered new interface driver usb-storage
[  185.107045] USB Mass Storage support registered.
[  205.248151] usb 6-1: USB disconnect, address 2
[  205.248539] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[  205.248562] usbserial_generic 6-1:1.0: device disconnected
[  214.680075] usb 5-2: new full speed USB device using uhci_hcd and address 2
[  214.841295] usb 5-2: configuration #1 chosen from 1 choice
[  214.843234] usbserial_generic 5-2:1.0: generic converter detected
[  214.843491] usb 5-2: generic converter now attached to ttyUSB0
[  509.224118] usb 2-1: new high speed USB device using ehci_hcd and address 4
[  509.359639] usb 2-1: configuration #1 chosen from 1 choice
[  509.361501] scsi5 : SCSI emulation for USB Mass Storage devices
[  509.361648] usb-storage: device found at 4
[  509.361652] usb-storage: waiting for device to settle before scanning
[  514.360376] usb-storage: device scan complete
[  515.251096] scsi 5:0:0:0: Direct-Access     HP       v165w            1100 PQ: 0 ANSI: 0 CCS
[  515.263774] sd 5:0:0:0: [sdb] 7831552 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[  515.266505] sd 5:0:0:0: [sdb] Write Protect is off
[  515.266511] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  515.266517] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  515.271147] sd 5:0:0:0: [sdb] 7831552 512-byte hardware sectors: (4.00 GB/3.73 GiB)
[  515.272446] sd 5:0:0:0: [sdb] Write Protect is off
[  515.272452] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  515.272457] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  515.272464]  sdb: sdb1
[  515.273716] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  515.273828] sd 5:0:0:0: Attached scsi generic sg2 type 0
nakul@nakul-laptop:~$

---

### Post by nakul123 on 2011-09-25
If any guys are following same problem use ubuntu 11.04 and get connected happily through mobile broadband wizard :guitar:

---

### Post by mörgæs on 2011-09-25
Good, please mark the thread 'solved'.

---

