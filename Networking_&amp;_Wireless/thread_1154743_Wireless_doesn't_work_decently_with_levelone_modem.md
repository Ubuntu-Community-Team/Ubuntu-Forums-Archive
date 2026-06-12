---
title: "Wireless doesn't work decently with levelone modem/router"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by andlinux on 2009-05-10
Hi

I have bought a new wireless modem/router because the old one didn't work anymore. So I bought a level one wbr-3600 modem/router.

The problem is that I have problems to connect wireless to my router. I have this modem/router 5 days now and I was able to connect 2 times to it. 

I also checked if the problem could be the router but it works perfectly with my sisters laptop (WinXP). 
I have ubuntu 9.04 installed (64 bit).

dmesg
```
[    0.557552] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.557555] pci 0000:00:1c.1: setting latency timer to 64
[    0.557563] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.557566] pci 0000:00:1c.2: setting latency timer to 64
[    0.557573] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.557577] pci 0000:00:1c.3: setting latency timer to 64
[    0.557583] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.557587] pci 0000:00:1c.4: setting latency timer to 64
[    0.557592] pci 0000:00:1e.0: setting latency timer to 64
[    0.557595] bus: 00 index 0 io port: [0x00-0xffff]
[    0.557597] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.557598] bus: 01 index 0 io port: [0x2000-0x2fff]
[    0.557600] bus: 01 index 1 mmio: [0xcc000000-0xceffffff]
[    0.557601] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.557602] bus: 01 index 3 mmio: [0x0-0x0]
[    0.557604] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.557605] bus: 02 index 1 mmio: [0xf4000000-0xf5ffffff]
[    0.557607] bus: 02 index 2 mmio: [0xf0000000-0xf1ffffff]
[    0.557608] bus: 02 index 3 mmio: [0x0-0x0]
[    0.557609] bus: 08 index 0 mmio: [0x0-0x0]
[    0.557610] bus: 08 index 1 mmio: [0x0-0x0]
[    0.557611] bus: 08 index 2 mmio: [0x0-0x0]
[    0.557612] bus: 08 index 3 mmio: [0x0-0x0]
[    0.557613] bus: 0e index 0 mmio: [0x0-0x0]
[    0.557615] bus: 0e index 1 mmio: [0xf2100000-0xf21fffff]
[    0.557616] bus: 0e index 2 mmio: [0x0-0x0]
[    0.557617] bus: 0e index 3 mmio: [0x0-0x0]
[    0.557618] bus: 14 index 0 io port: [0x4000-0x4fff]
[    0.557620] bus: 14 index 1 mmio: [0x88000000-0x880fffff]
[    0.557621] bus: 14 index 2 mmio: [0xf2000000-0xf20fffff]
[    0.557622] bus: 14 index 3 mmio: [0x0-0x0]
[    0.557624] bus: 1a index 0 mmio: [0x0-0x0]
[    0.557625] bus: 1a index 1 mmio: [0xf2200000-0xf22fffff]
[    0.557627] bus: 1a index 2 mmio: [0x88100000-0x881fffff]
[    0.557628] bus: 1a index 3 mmio: [0x0-0x0]
[    0.557629] bus: 26 index 0 mmio: [0x0-0x0]
[    0.557630] bus: 26 index 1 mmio: [0x0-0x0]
[    0.557631] bus: 26 index 2 mmio: [0x0-0x0]
[    0.557633] bus: 26 index 3 io port: [0x00-0xffff]
[    0.557634] bus: 26 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.557641] NET: Registered protocol family 2
[    0.592040] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.592344] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.594110] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.594685] TCP: Hash tables configured (established 262144 bind 65536)
[    0.594688] TCP reno registered
[    0.604107] NET: Registered protocol family 1
[    0.604214] checking if image is initramfs... it is
[    1.193266] Freeing initrd memory: 7717k freed
[    1.196470] Simple Boot Flag at 0x36 set to 0x1
[    1.196739] audit: initializing netlink socket (disabled)
[    1.196761] type=2000 audit(1241939923.196:1): initialized
[    1.203964] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.204978] VFS: Disk quotas dquot_6.5.1
[    1.205026] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.205474] fuse init (API version 7.10)
[    1.205534] msgmni has been set to 3964
[    1.205671] alg: No test for stdrng (krng)
[    1.205679] io scheduler noop registered
[    1.205680] io scheduler anticipatory registered
[    1.205682] io scheduler deadline registered
[    1.205710] io scheduler cfq registered (default)
[    1.205883] pci 0000:01:00.0: Boot video device
[    1.244483] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.244510] pcieport-driver 0000:00:01.0: found MSI capability
[    1.244529] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.244536] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.244547] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.244556] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.244594] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.244631] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.244656] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.244668] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.244678] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.244687] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.244743] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.244780] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.244805] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.244817] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.244826] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.244838] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.244894] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.244931] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.244956] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.244968] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.244978] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.244987] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.245048] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.245085] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.245110] pcieport-driver 0000:00:1c.3: irq 2299 for MSI/MSI-X
[    1.245122] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.245132] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.245141] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.245202] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.245238] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.245264] pcieport-driver 0000:00:1c.4: irq 2298 for MSI/MSI-X
[    1.245276] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.245285] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.245294] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.245357] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.245503] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.246305] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.249578] ACPI: AC Adapter [ACAD] (off-line)
[    1.268459] ACPI: Battery Slot [BAT1] (battery present)
[    1.268519] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.268521] ACPI: Power Button (FF) [PWRF]
[    1.268561] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.268603] ACPI: Lid Switch [LID0]
[    1.268637] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.268639] ACPI: Power Button (CM) [PWRB]
[    1.269304] ACPI: SSDT 7FD1AC20, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.269705] ACPI: SSDT 7FD18620, 0549 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.271743] Monitor-Mwait will be used to enter C-1 state
[    1.271745] Monitor-Mwait will be used to enter C-2 state
[    1.271747] Monitor-Mwait will be used to enter C-3 state
[    1.271758] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.271777] processor ACPI_CPU:00: registered as cooling_device0
[    1.271780] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.272202] ACPI: SSDT 7FD19CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.272538] ACPI: SSDT 7FD19F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.273400] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.273414] processor ACPI_CPU:01: registered as cooling_device1
[    1.273417] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.317191] Linux agpgart interface v0.103
[    1.317198] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.317948] brd: module loaded
[    1.318187] loop: module loaded
[    1.318235] Fixed MDIO Bus: probed
[    1.318239] PPP generic driver version 2.4.2
[    1.318283] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.318304] Driver 'sd' needs updating - please use bus_type methods
[    1.318310] Driver 'sr' needs updating - please use bus_type methods
[    1.318341] ahci 0000:00:1f.2: version 3.0
[    1.318351] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.318380] ahci 0000:00:1f.2: irq 2297 for MSI/MSI-X
[    1.318451] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.318453] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    1.318457] ahci 0000:00:1f.2: setting latency timer to 64
[    1.318720] scsi0 : ahci
[    1.318785] scsi1 : ahci
[    1.318828] scsi2 : ahci
[    1.318870] scsi3 : ahci
[    1.318913] scsi4 : ahci
[    1.318954] scsi5 : ahci
[    1.318986] ata1: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504100 irq 2297
[    1.318989] ata2: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504180 irq 2297
[    1.318990] ata3: DUMMY
[    1.318991] ata4: DUMMY
[    1.318993] ata5: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504300 irq 2297
[    1.318995] ata6: SATA max UDMA/133 abar m2048@0xf2504000 port 0xf2504380 irq 2297
[    1.636013] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.712388] ata1.00: ATA-8: ST9250421AS, SD13, max UDMA/133
[    1.712390] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.756135] ata1.00: configured for UDMA/133
[    2.092012] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.105155] ata2.00: ATAPI: Slimtype DVD A  DS8A2L, 3P58, max UDMA/100
[    2.119431] ata2.00: configured for UDMA/100
[    2.456011] ata5: SATA link down (SStatus 0 SControl 300)
[    2.792010] ata6: SATA link down (SStatus 0 SControl 300)
[    2.808078] scsi 0:0:0:0: Direct-Access     ATA      ST9250421AS      SD13 PQ: 0 ANSI: 5
[    2.808146] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.808160] sd 0:0:0:0: [sda] Write Protect is off
[    2.808162] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.808183] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.808233] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.808247] sd 0:0:0:0: [sda] Write Protect is off
[    2.808249] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.808269] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.808272]  sda: sda1 sda2 < sda5 >
[    2.903738] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.903775] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.908540] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A2L    3P58 PQ: 0 ANSI: 5
[    2.917313] sr0: scsi3-mmc drive: 24x/6x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    2.917315] Uniform CD-ROM driver Revision: 3.20
[    2.917383] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.917410] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.917908] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.917924] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.917935] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.917938] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.917986] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.921890] ehci_hcd 0000:00:1a.7: debug port 1
[    2.921896] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.921907] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf2504800
[    2.936006] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.936055] usb usb1: configuration #1 chosen from 1 choice
[    2.936077] hub 1-0:1.0: USB hub found
[    2.936083] hub 1-0:1.0: 6 ports detected
[    2.936171] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.936180] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.936183] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.936212] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.940113] ehci_hcd 0000:00:1d.7: debug port 1
[    2.940118] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.940128] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf2504c00
[    2.956006] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.956046] usb usb2: configuration #1 chosen from 1 choice
[    2.956064] hub 2-0:1.0: USB hub found
[    2.956069] hub 2-0:1.0: 6 ports detected
[    2.956140] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.956151] uhci_hcd: USB Universal Host Controller Interface driver
[    2.956167] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.956172] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.956174] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.956209] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.956237] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    2.956297] usb usb3: configuration #1 chosen from 1 choice
[    2.956318] hub 3-0:1.0: USB hub found
[    2.956323] hub 3-0:1.0: 2 ports detected
[    2.956385] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.956390] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.956393] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.956430] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.956457] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    2.956513] usb usb4: configuration #1 chosen from 1 choice
[    2.956533] hub 4-0:1.0: USB hub found
[    2.956537] hub 4-0:1.0: 2 ports detected
[    2.956599] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.956604] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.956607] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.956636] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    2.956658] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    2.956714] usb usb5: configuration #1 chosen from 1 choice
[    2.956732] hub 5-0:1.0: USB hub found
[    2.956736] hub 5-0:1.0: 2 ports detected
[    2.956801] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.956806] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.956808] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.956838] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.956860] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    2.956917] usb usb6: configuration #1 chosen from 1 choice
[    2.956934] hub 6-0:1.0: USB hub found
[    2.956941] hub 6-0:1.0: 2 ports detected
[    2.957003] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.957008] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.957011] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.957047] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.957068] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    2.957122] usb usb7: configuration #1 chosen from 1 choice
[    2.957142] hub 7-0:1.0: USB hub found
[    2.957147] hub 7-0:1.0: 2 ports detected
[    2.957210] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.957215] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.957218] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.957251] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.957279] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    2.957344] usb usb8: configuration #1 chosen from 1 choice
[    2.957362] hub 8-0:1.0: USB hub found
[    2.957366] hub 8-0:1.0: 2 ports detected
[    2.957466] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.994033] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.994037] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.004029] mice: PS/2 mouse device common for all mice
[    3.052052] rtc_cmos 00:06: RTC can wake from S4
[    3.052078] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.052101] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.052143] device-mapper: uevent: version 1.0.3
[    3.052208] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.052259] device-mapper: multipath: version 1.0.5 loaded
[    3.052261] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.052379] cpuidle: using governor ladder
[    3.052467] cpuidle: using governor menu
[    3.052783] TCP cubic registered
[    3.052838] NET: Registered protocol family 10
[    3.053137] lo: Disabled Privacy Extensions
[    3.053358] NET: Registered protocol family 17
[    3.053374] Bluetooth: L2CAP ver 2.11
[    3.053375] Bluetooth: L2CAP socket layer initialized
[    3.053378] Bluetooth: SCO (Voice Link) ver 0.6
[    3.053379] Bluetooth: SCO socket layer initialized
[    3.053404] Marking TSC unstable due to TSC halts in idle
[    3.053405] Bluetooth: RFCOMM socket layer initialized
[    3.053411] Bluetooth: RFCOMM TTY layer initialized
[    3.053412] Bluetooth: RFCOMM ver 1.10
[    3.054055] registered taskstats version 1
[    3.054161]   Magic number: 9:754:318
[    3.054180] tty tty43: hash matches
[    3.054234] rtc_cmos 00:06: setting system clock to 2009-05-10 07:18:46 UTC (1241939926)
[    3.054237] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.054238] EDD information not available.
[    3.054299] Freeing unused kernel memory: 532k freed
[    3.054470] Write protecting the kernel read-only data: 6684k
[    3.085077] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.240913] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.240954] r8169 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.241046] r8169 0000:14:00.0: setting latency timer to 64
[    3.241373] r8169 0000:14:00.0: irq 2296 for MSI/MSI-X
[    3.241864] eth0: RTL8168c/8111c at 0xffffc2000007e000, 00:1e:ec:c9:9f:32, XID 3c4000c0 IRQ 2296
[    3.400033] usb 2-3: new high speed USB device using ehci_hcd and address 3
[    3.547282] PM: Starting manual resume from disk
[    3.547284] PM: Resume from partition 8:5
[    3.547286] PM: Checking hibernation image.
[    3.547616] PM: Resume from disk failed.
[    3.588796] kjournald starting.  Commit interval 5 seconds
[    3.588803] EXT3-fs: mounted filesystem with ordered data mode.
[    3.594259] usb 2-3: configuration #1 chosen from 1 choice
[    3.836011] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    4.011066] usb 6-2: configuration #1 chosen from 1 choice
[    9.627109] udev: starting version 141
[   10.163660] nvidia: module license 'NVIDIA' taints kernel.
[   10.415924] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.415945] nvidia 0000:01:00.0: setting latency timer to 64
[   10.416344] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   10.488079] cfg80211: Calling CRDA to update world regulatory domain
[   10.645007] sdhci: Secure Digital Host Controller Interface driver
[   10.645009] sdhci: Copyright(c) Pierre Ossman
[   10.683008] cfg80211: World regulatory domain updated:
[   10.683010] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.683012] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.683013] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.683015] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.683016] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.683018] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.726353] sdhci-pci 0000:1a:00.0: SDHCI controller found [197b:2382] (rev 0)
[   10.726370] sdhci-pci 0000:1a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.726438] sdhci-pci 0000:1a:00.0: setting latency timer to 64
[   10.726496] mmc0: SDHCI controller on PCI [0000:1a:00.0] using ADMA
[   10.726504] sdhci-pci 0000:1a:00.2: SDHCI controller found [197b:2381] (rev 0)
[   10.726517] sdhci-pci 0000:1a:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.726522] sdhci-pci 0000:1a:00.2: Refusing to bind to secondary interface.
[   10.726528] sdhci-pci 0000:1a:00.2: PCI INT A disabled
[   10.735876] iTCO_vendor_support: vendor-support=0
[   10.738315] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.738425] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[   10.738495] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.772242] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   10.826673] acpi device:03: registered as cooling_device2
[   10.826839] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[   10.836630] Linux video capture interface: v2.00
[   10.856139] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   10.936759] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:a115)
[   10.938585] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input7
[   10.952162] usbcore: registered new interface driver uvcvideo
[   10.952198] USB Video Class driver (v0.1.0)
[   11.088695] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.259776] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   11.259779] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   11.259886] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.259905] iwlagn 0000:0e:00.0: setting latency timer to 64
[   11.259984] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   11.302107] iwlagn: Tunable channels: 13 802.11bg, 19 802.11a channels
[   11.302176] iwlagn 0000:0e:00.0: irq 2295 for MSI/MSI-X
[   11.302914] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.418391] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.418455] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.450909] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   11.674259] lp: driver loaded but no devices found
[   11.865707] Adding 6024332k swap on /dev/sda5.  Priority:-1 extents:1 across:6024332k
[   11.879857] EXT3 FS on sda1, internal journal
[   11.930133] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   11.993018] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   12.365070] type=1505 audit(1241939935.809:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2105
[   12.394248] type=1505 audit(1241939935.837:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2109
[   12.394329] type=1505 audit(1241939935.837:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2109
[   12.394358] type=1505 audit(1241939935.837:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2109
[   12.394389] type=1505 audit(1241939935.837:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2109
[   12.476498] type=1505 audit(1241939935.921:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2114
[   12.476624] type=1505 audit(1241939935.921:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2114
[   12.494992] type=1505 audit(1241939935.937:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2118
[   16.500065] Clocksource tsc unstable (delta = -163499373 ns)
[   19.303514] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   19.303521] vboxdrv: Successfully done.
[   19.303525] vboxdrv: Found 2 processor cores.
[   19.305513] VBoxDrv: dbg - g_abExecMemory=ffffffffa0af9aa0
[   19.305552] vboxdrv: fAsync=0 offMin=0x473 offMax=0x1441
[   19.305642] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.305646] vboxdrv: Successfully loaded version 2.1.4 (interface 0x000a0009).
[   19.517672] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0c98940
[   20.828350] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.828356] Bluetooth: BNEP filters: protocol multicast
[   20.853806] Bridge firewalling registered
[   22.757291] ppdev: user-space parallel port driver
[   26.557241] r8169: eth0: link down
[   26.557603] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.558150] iwlagn 0000:0e:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   26.880580] Registered led device: iwl-phy0:radio
[   26.880600] Registered led device: iwl-phy0:assoc
[   26.880612] Registered led device: iwl-phy0:RX
[   26.880622] Registered led device: iwl-phy0:TX
[   27.083108] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.126597] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   29.324128] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   29.326845] wlan0: authenticated
[   29.326852] wlan0: associate with AP 00:11:6b:1c:c4:34
[   29.525044] wlan0: associate with AP 00:11:6b:1c:c4:34
[   29.527151] wlan0: deauthenticated
[   30.525259] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
[   30.724274] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 2
[   30.727419] wlan0 direct probe responded
[   30.727430] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   30.925201] wlan0: authentication with AP 00:11:6b:1c:c4:34 timed out
[   58.889250] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   58.895630] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   58.895659] wlan0: authenticated
[   58.895665] wlan0: associate with AP 00:11:6b:1c:c4:34
[   58.920071] wlan0: deauthenticated
[   59.916054] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
[   60.120736] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 2
[   60.123650] wlan0 direct probe responded
[   60.123658] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   60.320077] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   60.329070] wlan0: authenticated
[   60.329081] wlan0: associate with AP 00:11:6b:1c:c4:34
[   60.529061] wlan0: associate with AP 00:11:6b:1c:c4:34
[   60.531421] wlan0: deauthenticated
[   61.528103] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 3
[   61.732101] wlan0: direct probe to AP 00:11:6b:1c:c4:34 timed out
[   69.760789] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   69.765388] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   69.765423] wlan0: authenticated
[   69.765429] wlan0: associate with AP 00:11:6b:1c:c4:34
[   69.787875] wlan0: deauthenticated
[   70.785049] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
[   70.985280] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 2
[   70.988266] wlan0 direct probe responded
[   70.988277] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   71.184143] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   71.186538] wlan0: authenticated
[   71.186548] wlan0: associate with AP 00:11:6b:1c:c4:34
[   71.384081] wlan0: associate with AP 00:11:6b:1c:c4:34
[   71.386317] wlan0: deauthenticated
[   72.384187] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 3
[   72.585260] wlan0: direct probe to AP 00:11:6b:1c:c4:34 timed out
[   80.628306] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   80.636566] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   80.636600] wlan0: authenticated
[   80.636606] wlan0: associate with AP 00:11:6b:1c:c4:34
[   80.659393] wlan0: deauthenticated
[   81.656127] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
[   81.856064] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 2
[   81.858810] wlan0 direct probe responded
[   81.858817] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   82.056262] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   82.058813] wlan0: authenticated
[   82.058824] wlan0: associate with AP 00:11:6b:1c:c4:34
[   82.260079] wlan0: associate with AP 00:11:6b:1c:c4:34
[   82.262191] wlan0: deauthenticated
[   83.260034] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 3
[   83.464045] wlan0: direct probe to AP 00:11:6b:1c:c4:34 timed out
[   91.619951] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   91.624723] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   91.624754] wlan0: authenticated
[   91.624759] wlan0: associate with AP 00:11:6b:1c:c4:34
[   91.645522] wlan0: deauthenticated
[   92.644255] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
[   92.844259] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 2
[   92.847180] wlan0 direct probe responded
[   92.847189] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   93.044265] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[   93.046936] wlan0: authenticated
[   93.046947] wlan0: associate with AP 00:11:6b:1c:c4:34
[   93.244130] wlan0: associate with AP 00:11:6b:1c:c4:34
[   93.246343] wlan0: deauthenticated
[   94.244262] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 3
[   94.444265] wlan0: direct probe to AP 00:11:6b:1c:c4:34 timed out
[  102.495211] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  102.500671] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  102.500710] wlan0: authenticated
[  102.500716] wlan0: associate with AP 00:11:6b:1c:c4:34
[  102.523358] wlan0: deauthenticated
[  103.521057] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
[  103.720269] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 2
[  103.723311] wlan0 direct probe responded
[  103.723323] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  103.924262] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  103.926851] wlan0: authenticated
[  103.926861] wlan0: associate with AP 00:11:6b:1c:c4:34
[  104.124253] wlan0: associate with AP 00:11:6b:1c:c4:34
[  104.126623] wlan0: deauthenticated
[  105.124258] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 3
[  105.324265] wlan0: direct probe to AP 00:11:6b:1c:c4:34 timed out
[  113.486523] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  113.493324] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  113.493355] wlan0: authenticated
[  113.493360] wlan0: associate with AP 00:11:6b:1c:c4:34
[  113.516108] wlan0: deauthenticated
[  114.516081] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
[  114.716125] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 2
[  114.718922] wlan0 direct probe responded
[  114.718933] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  114.916266] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  114.918751] wlan0: authenticated
[  114.918761] wlan0: associate with AP 00:11:6b:1c:c4:34
[  115.116264] wlan0: associate with AP 00:11:6b:1c:c4:34
[  115.118523] wlan0: deauthenticated
[  116.117256] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 3
[  116.316260] wlan0: direct probe to AP 00:11:6b:1c:c4:34 timed out
[  118.573939] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  118.576142] wlan0: authenticated
[  118.576146] wlan0: associate with AP 00:11:6b:1c:c4:34
[  118.777044] wlan0: associate with AP 00:11:6b:1c:c4:34
[  118.779212] wlan0: deauthenticated
[  119.776054] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
[  119.976066] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 2
[  119.978855] wlan0 direct probe responded
[  119.978863] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  120.176097] wlan0: authenticate with AP 00:11:6b:1c:c4:34
[  120.178461] wlan0: authenticated
[  120.178471] wlan0: associate with AP 00:11:6b:1c:c4:34
[  120.377080] wlan0: association with AP 00:11:6b:1c:c4:34 timed out
[  168.162323] r8169: eth0: link up
[  168.163131] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  178.344059] eth0: no IPv6 routers present
[  727.845510] CE: hpet increasing min_delta_ns to 15000 nsec
[  727.845617] CE: hpet increasing min_delta_ns to 22500 nsec

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Honeypot_LNX"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:c9:9f:32  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fec9:9f32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:630895 (630.8 KB)  TX bytes:102516 (102.5 KB)
          Interrupt:248 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12392 (12.3 KB)  TX bytes:12392 (12.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:08:74:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-08-74-6F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

lsmod

```
Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
vboxnetflt            110316  0 
vboxdrv              1704748  1 vboxnetflt
input_polldev          12688  0 
joydev                 20864  0 
mxl5005s               50436  0 
dvb_usb                27148  0 
dvb_core              106924  1 dvb_usb
coretemp               15360  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557620  3 
arc4                   10240  2 
ecb                    11392  2 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99592  2 snd_hda_intel,snd_pcm_oss
iwlagn                114820  0 
iwlcore               106496  1 iwlagn
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class              13064  1 iwlcore
snd                    78792  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               69512  0 
mac80211              251528  2 iwlagn,iwlcore
psmouse                64028  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
video                  29204  6 
soundcore              16800  1 snd
serio_raw              14468  0 
pcspkr                 11136  0 
iTCO_wdt               21712  0 
iTCO_vendor_support    12420  1 iTCO_wdt
v4l1_compat            23940  2 uvcvideo,videodev
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
intel_agp              39408  0 
output                 11648  1 video
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
cfg80211               43552  3 iwlagn,iwlcore,mac80211
nvidia               8123768  29 
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```


Who can help me to fix this ?

EDIT: I discovered something, the laptop was just connected with a cable to my router and I'm standing next to it.
I unplugged the cable and I clicked on the networkmanager applet and selected my ssid because now that's the only one standing in the list (I'm in my basement) and it connected. Why isn't it possible to connect when I'm somewhere else in the house, it can't be the signal, that's strong enough ?

---

### Post by andlinux on 2009-05-10
Here is the code from dmesg after I unplugged the cable:

```
May 10 09:30:49 andy-laptop kernel: [  727.845510] CE: hpet increasing min_delta_ns to 15000 nsec
May 10 09:30:49 andy-laptop kernel: [  727.845617] CE: hpet increasing min_delta_ns to 22500 nsec
May 10 09:36:49 andy-laptop kernel: [ 1088.218980] r8169: eth0: link down
May 10 09:37:10 andy-laptop kernel: [ 1108.692818] wlan0: authenticate with AP 00:11:6b:1c:c4:34
May 10 09:37:10 andy-laptop kernel: [ 1108.697073] wlan0: authenticate with AP 00:11:6b:1c:c4:34
May 10 09:37:10 andy-laptop kernel: [ 1108.697106] wlan0: authenticated
May 10 09:37:10 andy-laptop kernel: [ 1108.697112] wlan0: associate with AP 00:11:6b:1c:c4:34
May 10 09:37:10 andy-laptop kernel: [ 1108.896301] wlan0: associate with AP 00:11:6b:1c:c4:34
May 10 09:37:10 andy-laptop kernel: [ 1108.898680] wlan0: deauthenticated
May 10 09:37:11 andy-laptop kernel: [ 1109.896302] wlan0: direct probe to AP 00:11:6b:1c:c4:34 try 1
May 10 09:37:11 andy-laptop kernel: [ 1109.899266] wlan0 direct probe responded
May 10 09:37:11 andy-laptop kernel: [ 1109.899278] wlan0: authenticate with AP 00:11:6b:1c:c4:34
May 10 09:37:11 andy-laptop kernel: [ 1109.902660] wlan0: authenticated
May 10 09:37:11 andy-laptop kernel: [ 1109.902671] wlan0: associate with AP 00:11:6b:1c:c4:34
May 10 09:37:11 andy-laptop kernel: [ 1109.953456] wlan0: RX AssocResp from 00:11:6b:1c:c4:34 (capab=0x421 status=0 aid=1)
May 10 09:37:11 andy-laptop kernel: [ 1109.953464] wlan0: associated
May 10 09:37:11 andy-laptop kernel: [ 1109.979960] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 10 09:37:21 andy-laptop kernel: [ 1120.348255] wlan0: no IPv6 routers present

```

---

### Post by andlinux on 2009-05-10
Bump

---

### Post by andlinux on 2009-08-10
Bought a linksys modem/router wag54g2 and it works without a problem. Even WPA2 works ;)

---

