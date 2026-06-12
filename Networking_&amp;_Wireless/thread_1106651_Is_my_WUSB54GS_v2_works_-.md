---
title: "Is my WUSB54GS v2 works :-/"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by warzt on 2009-03-25
I bought WUSB54GS last week , after few days I looking for stuff, This is what i got when I type in terminal 
 cat /var/log/syslog

```
Mar 25 20:49:39 gary-laptop kernel: [    1.148480] pci 0000:00:1c.2:   PREFETCH window: 0x000000d4000000-0x000000d5ffffff
Mar 25 20:49:39 gary-laptop kernel: [    1.148505] pci 0000:0a:09.0: CardBus bridge, secondary bus 0000:0b
Mar 25 20:49:39 gary-laptop kernel: [    1.148512] pci 0000:0a:09.0:   IO window: 0x004000-0x0040ff
Mar 25 20:49:39 gary-laptop kernel: [    1.148523] pci 0000:0a:09.0:   IO window: 0x004400-0x0044ff
Mar 25 20:49:39 gary-laptop kernel: [    1.148534] pci 0000:0a:09.0:   PREFETCH window: 0x50000000-0x53ffffff
Mar 25 20:49:39 gary-laptop kernel: [    1.148545] pci 0000:0a:09.0:   MEM window: 0x54000000-0x57ffffff
Mar 25 20:49:39 gary-laptop kernel: [    1.148556] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a
Mar 25 20:49:39 gary-laptop kernel: [    1.148565] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
Mar 25 20:49:39 gary-laptop kernel: [    1.148577] pci 0000:00:1e.0:   MEM window: 0xdc000000-0xdc0fffff
Mar 25 20:49:39 gary-laptop kernel: [    1.148588] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
Mar 25 20:49:39 gary-laptop kernel: [    1.148619] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 25 20:49:39 gary-laptop kernel: [    1.148631] pci 0000:00:1c.0: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    1.148650] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Mar 25 20:49:39 gary-laptop kernel: [    1.148661] pci 0000:00:1c.1: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    1.148679] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 25 20:49:39 gary-laptop kernel: [    1.148690] pci 0000:00:1c.2: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    1.148706] pci 0000:00:1e.0: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    1.148725] pci 0000:0a:09.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar 25 20:49:39 gary-laptop kernel: [    1.148738] bus: 00 index 0 io port: [0, ffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148744] bus: 00 index 1 mmio: [0, ffffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148750] bus: 02 index 0 mmio: [0, 0]
Mar 25 20:49:39 gary-laptop kernel: [    1.148755] bus: 02 index 1 mmio: [0, 0]
Mar 25 20:49:39 gary-laptop kernel: [    1.148760] bus: 02 index 2 mmio: [0, 0]
Mar 25 20:49:39 gary-laptop kernel: [    1.148766] bus: 02 index 3 mmio: [0, 0]
Mar 25 20:49:39 gary-laptop kernel: [    1.148771] bus: 03 index 0 io port: [2000, 2fff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148777] bus: 03 index 1 mmio: [d8000000, d9ffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148783] bus: 03 index 2 mmio: [d2000000, d3ffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148789] bus: 03 index 3 mmio: [0, 0]
Mar 25 20:49:39 gary-laptop kernel: [    1.148795] bus: 05 index 0 io port: [3000, 3fff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148801] bus: 05 index 1 mmio: [da000000, dbffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148807] bus: 05 index 2 mmio: [d4000000, d5ffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148813] bus: 05 index 3 mmio: [0, 0]
Mar 25 20:49:39 gary-laptop kernel: [    1.148818] bus: 0a index 0 io port: [4000, 4fff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148824] bus: 0a index 1 mmio: [dc000000, dc0fffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148830] bus: 0a index 2 mmio: [50000000, 53ffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148836] bus: 0a index 3 io port: [0, ffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148842] bus: 0a index 4 mmio: [0, ffffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148848] bus: 0b index 0 io port: [4000, 40ff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148854] bus: 0b index 1 io port: [4400, 44ff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148859] bus: 0b index 2 mmio: [50000000, 53ffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148866] bus: 0b index 3 mmio: [54000000, 57ffffff]
Mar 25 20:49:39 gary-laptop kernel: [    1.148886] NET: Registered protocol family 2
Mar 25 20:49:39 gary-laptop kernel: [    1.160124] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 25 20:49:39 gary-laptop kernel: [    1.160671] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 25 20:49:39 gary-laptop kernel: [    1.161593] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 25 20:49:39 gary-laptop kernel: [    1.162052] TCP: Hash tables configured (established 131072 bind 65536)
Mar 25 20:49:39 gary-laptop kernel: [    1.162059] TCP reno registered
Mar 25 20:49:39 gary-laptop kernel: [    1.168172] NET: Registered protocol family 1
Mar 25 20:49:39 gary-laptop kernel: [    1.168442] checking if image is initramfs... it is
Mar 25 20:49:39 gary-laptop kernel: [    2.922986] Freeing initrd memory: 8014k freed
Mar 25 20:49:39 gary-laptop kernel: [    2.923607] Simple Boot Flag at 0x36 set to 0x1
Mar 25 20:49:39 gary-laptop kernel: [    2.925674] audit: initializing netlink socket (disabled)
Mar 25 20:49:39 gary-laptop kernel: [    2.925718] type=2000 audit(1238032152.924:1): initialized
Mar 25 20:49:39 gary-laptop kernel: [    2.941077] highmem bounce pool size: 64 pages
Mar 25 20:49:39 gary-laptop kernel: [    2.941092] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Mar 25 20:49:39 gary-laptop kernel: [    2.947281] VFS: Disk quotas dquot_6.5.1
Mar 25 20:49:39 gary-laptop kernel: [    2.947503] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 25 20:49:39 gary-laptop kernel: [    2.947742] msgmni has been set to 1761
Mar 25 20:49:39 gary-laptop kernel: [    2.948039] io scheduler noop registered
Mar 25 20:49:39 gary-laptop kernel: [    2.948046] io scheduler anticipatory registered
Mar 25 20:49:39 gary-laptop kernel: [    2.948053] io scheduler deadline registered
Mar 25 20:49:39 gary-laptop kernel: [    2.948085] io scheduler cfq registered (default)
Mar 25 20:49:39 gary-laptop kernel: [    2.948112] pci 0000:00:02.0: Boot video device
Mar 25 20:49:39 gary-laptop kernel: [    2.948521] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    2.948596] pcieport-driver 0000:00:1c.0: found MSI capability
Mar 25 20:49:39 gary-laptop kernel: [    2.948671] pci_express 0000:00:1c.0:pcie00: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.948778] pci_express 0000:00:1c.0:pcie02: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.948882] pci_express 0000:00:1c.0:pcie03: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.949107] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    2.949178] pcieport-driver 0000:00:1c.1: found MSI capability
Mar 25 20:49:39 gary-laptop kernel: [    2.949248] pci_express 0000:00:1c.1:pcie00: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.949356] pci_express 0000:00:1c.1:pcie02: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.949465] pci_express 0000:00:1c.1:pcie03: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.949670] pcieport-driver 0000:00:1c.2: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    2.949741] pcieport-driver 0000:00:1c.2: found MSI capability
Mar 25 20:49:39 gary-laptop kernel: [    2.949812] pci_express 0000:00:1c.2:pcie00: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.949915] pci_express 0000:00:1c.2:pcie02: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.950021] pci_express 0000:00:1c.2:pcie03: allocate port service
Mar 25 20:49:39 gary-laptop kernel: [    2.950821] isapnp: Scanning for PnP cards...
Mar 25 20:49:39 gary-laptop kernel: [    3.305312] isapnp: No Plug & Play device found
Mar 25 20:49:39 gary-laptop kernel: [    3.395739] hpet_resources: 0xfed00000 is busy
Mar 25 20:49:39 gary-laptop kernel: [    3.395904] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Mar 25 20:49:39 gary-laptop kernel: [    3.401447] brd: module loaded
Mar 25 20:49:39 gary-laptop kernel: [    3.401623] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Mar 25 20:49:39 gary-laptop kernel: [    3.401930] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 25 20:49:39 gary-laptop kernel: [    3.404392] i8042.c: Detected active multiplexing controller, rev 1.1.
Mar 25 20:49:39 gary-laptop kernel: [    3.407615] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 25 20:49:39 gary-laptop kernel: [    3.407628] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Mar 25 20:49:39 gary-laptop kernel: [    3.407636] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Mar 25 20:49:39 gary-laptop kernel: [    3.407643] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Mar 25 20:49:39 gary-laptop kernel: [    3.407650] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Mar 25 20:49:39 gary-laptop kernel: [    3.408514] mice: PS/2 mouse device common for all mice
Mar 25 20:49:39 gary-laptop kernel: [    3.408854] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Mar 25 20:49:39 gary-laptop kernel: [    3.408897] rtc0: alarms up to one month, y3k, hpet irqs
Mar 25 20:49:39 gary-laptop kernel: [    3.409216] EISA: Probing bus 0 at eisa.0
Mar 25 20:49:39 gary-laptop kernel: [    3.409229] Cannot allocate resource for EISA slot 1
Mar 25 20:49:39 gary-laptop kernel: [    3.409237] Cannot allocate resource for EISA slot 2
Mar 25 20:49:39 gary-laptop kernel: [    3.409243] Cannot allocate resource for EISA slot 3
Mar 25 20:49:39 gary-laptop kernel: [    3.409250] Cannot allocate resource for EISA slot 4
Mar 25 20:49:39 gary-laptop kernel: [    3.409281] EISA: Detected 0 cards.
Mar 25 20:49:39 gary-laptop kernel: [    3.409288] cpuidle: using governor ladder
Mar 25 20:49:39 gary-laptop kernel: [    3.409295] cpuidle: using governor menu
Mar 25 20:49:39 gary-laptop kernel: [    3.410565] TCP cubic registered
Mar 25 20:49:39 gary-laptop kernel: [    3.410620] Using IPI No-Shortcut mode
Mar 25 20:49:39 gary-laptop kernel: [    3.411068] registered taskstats version 1
Mar 25 20:49:39 gary-laptop kernel: [    3.411317]   Magic number: 1:824:812
Mar 25 20:49:39 gary-laptop kernel: [    3.411392] tty ptys6: hash matches
Mar 25 20:49:39 gary-laptop kernel: [    3.411497] rtc_cmos 00:08: setting system clock to 2009-03-26 01:49:14 UTC (1238032154)
Mar 25 20:49:39 gary-laptop kernel: [    3.411505] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Mar 25 20:49:39 gary-laptop kernel: [    3.411511] EDD information not available.
Mar 25 20:49:39 gary-laptop kernel: [    3.411949] Freeing unused kernel memory: 424k freed
Mar 25 20:49:39 gary-laptop kernel: [    3.412082] Write protecting the kernel text: 2580k
Mar 25 20:49:39 gary-laptop kernel: [    3.412154] Write protecting the kernel read-only data: 940k
Mar 25 20:49:39 gary-laptop kernel: [    3.422285] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Mar 25 20:49:39 gary-laptop kernel: [    3.788310] fuse init (API version 7.9)
Mar 25 20:49:39 gary-laptop kernel: [    3.862166] ACPI: SSDT 3F694CDA, 01EA (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Mar 25 20:49:39 gary-laptop kernel: [    3.863193] ACPI: SSDT 3F694A41, 0214 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Mar 25 20:49:39 gary-laptop kernel: [    3.864783] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Mar 25 20:49:39 gary-laptop kernel: [    3.864915] processor ACPI0007:00: registered as cooling_device0
Mar 25 20:49:39 gary-laptop kernel: [    3.865809] ACPI: SSDT 3F694EC4, 0089 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Mar 25 20:49:39 gary-laptop kernel: [    3.866786] ACPI: SSDT 3F694C55, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Mar 25 20:49:39 gary-laptop kernel: [    3.868471] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Mar 25 20:49:39 gary-laptop kernel: [    3.868585] processor ACPI0007:01: registered as cooling_device1
Mar 25 20:49:39 gary-laptop kernel: [    3.874627] Marking TSC unstable due to TSC halts in idle
Mar 25 20:49:39 gary-laptop kernel: [    3.877687] thermal LNXTHERM:01: registered as thermal_zone0
Mar 25 20:49:39 gary-laptop kernel: [    3.881117] ACPI: Thermal Zone [TZS0] (35 C)
Mar 25 20:49:39 gary-laptop kernel: [    3.883360] thermal LNXTHERM:02: registered as thermal_zone1
Mar 25 20:49:39 gary-laptop kernel: [    3.884791] ACPI: Thermal Zone [TZS1] (31 C)
Mar 25 20:49:39 gary-laptop kernel: [    4.852260] usbcore: registered new interface driver usbfs
Mar 25 20:49:39 gary-laptop kernel: [    4.852314] usbcore: registered new interface driver hub
Mar 25 20:49:39 gary-laptop kernel: [    4.906962] usbcore: registered new device driver usb
Mar 25 20:49:39 gary-laptop kernel: [    4.953115] No dock devices found.
Mar 25 20:49:39 gary-laptop kernel: [    4.958584] USB Universal Host Controller Interface driver v3.0
Mar 25 20:49:39 gary-laptop kernel: [    4.958675] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 25 20:49:39 gary-laptop kernel: [    4.958693] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    4.958702] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar 25 20:49:39 gary-laptop kernel: [    4.958795] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Mar 25 20:49:39 gary-laptop kernel: [    4.958852] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
Mar 25 20:49:39 gary-laptop kernel: [    4.959167] usb usb1: configuration #1 chosen from 1 choice
Mar 25 20:49:39 gary-laptop kernel: [    4.959237] hub 1-0:1.0: USB hub found
Mar 25 20:49:39 gary-laptop kernel: [    4.959254] hub 1-0:1.0: 2 ports detected
Mar 25 20:49:39 gary-laptop kernel: [    5.039915] SCSI subsystem initialized
Mar 25 20:49:39 gary-laptop kernel: [    5.040215] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
Mar 25 20:49:39 gary-laptop kernel: [    5.085221] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 25 20:49:39 gary-laptop kernel: [    5.085241] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    5.085251] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar 25 20:49:39 gary-laptop kernel: [    5.085326] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Mar 25 20:49:39 gary-laptop kernel: [    5.085387] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
Mar 25 20:49:39 gary-laptop kernel: [    5.085669] usb usb2: configuration #1 chosen from 1 choice
Mar 25 20:49:39 gary-laptop kernel: [    5.085740] hub 2-0:1.0: USB hub found
Mar 25 20:49:39 gary-laptop kernel: [    5.085757] hub 2-0:1.0: 2 ports detected
Mar 25 20:49:39 gary-laptop kernel: [    5.086739] libata version 3.00 loaded.
Mar 25 20:49:39 gary-laptop kernel: [    5.188521] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Mar 25 20:49:39 gary-laptop kernel: [    5.188541] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    5.188550] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar 25 20:49:39 gary-laptop kernel: [    5.188611] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Mar 25 20:49:39 gary-laptop kernel: [    5.188674] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
Mar 25 20:49:39 gary-laptop kernel: [    5.188900] usb usb3: configuration #1 chosen from 1 choice
Mar 25 20:49:39 gary-laptop kernel: [    5.188968] hub 3-0:1.0: USB hub found
Mar 25 20:49:39 gary-laptop kernel: [    5.188985] hub 3-0:1.0: 2 ports detected
Mar 25 20:49:39 gary-laptop kernel: [    5.292527] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Mar 25 20:49:39 gary-laptop kernel: [    5.292547] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    5.292556] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Mar 25 20:49:39 gary-laptop kernel: [    5.292617] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Mar 25 20:49:39 gary-laptop kernel: [    5.292675] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
Mar 25 20:49:39 gary-laptop kernel: [    5.292898] usb usb4: configuration #1 chosen from 1 choice
Mar 25 20:49:39 gary-laptop kernel: [    5.292971] hub 4-0:1.0: USB hub found
Mar 25 20:49:39 gary-laptop kernel: [    5.292986] hub 4-0:1.0: 2 ports detected
Mar 25 20:49:39 gary-laptop kernel: [    5.398755] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 25 20:49:39 gary-laptop kernel: [    5.398782] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    5.398791] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar 25 20:49:39 gary-laptop kernel: [    5.398864] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Mar 25 20:49:39 gary-laptop kernel: [    5.402787] ehci_hcd 0000:00:1d.7: debug port 1
Mar 25 20:49:39 gary-laptop kernel: [    5.402800] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Mar 25 20:49:39 gary-laptop kernel: [    5.402818] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdc444000
Mar 25 20:49:39 gary-laptop kernel: [    5.416089] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 25 20:49:39 gary-laptop kernel: [    5.416365] usb usb5: configuration #1 chosen from 1 choice
Mar 25 20:49:39 gary-laptop kernel: [    5.416437] hub 5-0:1.0: USB hub found
Mar 25 20:49:39 gary-laptop kernel: [    5.416455] hub 5-0:1.0: 8 ports detected
Mar 25 20:49:39 gary-laptop kernel: [    5.520572] b44 0000:0a:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Mar 25 20:49:39 gary-laptop kernel: [    5.520626] ata_piix 0000:00:1f.2: version 2.12
Mar 25 20:49:39 gary-laptop kernel: [    5.520646] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Mar 25 20:49:39 gary-laptop kernel: [    5.520656] ata_piix 0000:00:1f.2: MAP [ IDE IDE P1 P3 ]
Mar 25 20:49:39 gary-laptop kernel: [    5.520738] ata_piix 0000:00:1f.2: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [    5.521047] scsi0 : ata_piix
Mar 25 20:49:39 gary-laptop kernel: [    5.521250] scsi1 : ata_piix
Mar 25 20:49:39 gary-laptop kernel: [    5.524190] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
Mar 25 20:49:39 gary-laptop kernel: [    5.524198] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
Mar 25 20:49:39 gary-laptop kernel: [    5.580168] ssb: Sonics Silicon Backplane found on PCI device 0000:0a:07.0
Mar 25 20:49:39 gary-laptop kernel: [    5.580791] b44.c:v2.0
Mar 25 20:49:39 gary-laptop kernel: [    5.600834] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:16:d3:41:f5:69
Mar 25 20:49:39 gary-laptop kernel: [    5.864975] ata1.00: ATA-6: HTS541060G9AT00, MB3OA60A, max UDMA/100
Mar 25 20:49:39 gary-laptop kernel: [    5.864985] ata1.00: 117210240 sectors, multi 16: LBA48 
Mar 25 20:49:39 gary-laptop kernel: [    5.865053] ata1.01: ATAPI: Slimtype COMBO SSC-2485K, 5RK1, max UDMA/33
Mar 25 20:49:39 gary-laptop kernel: [    5.880977] ata1.00: configured for UDMA/100
Mar 25 20:49:39 gary-laptop kernel: [    5.888610] ata1.01: configured for UDMA/33
Mar 25 20:49:39 gary-laptop kernel: [    6.000143] Clocksource tsc unstable (delta = -148112416 ns)
Mar 25 20:49:39 gary-laptop kernel: [    6.055773] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3O PQ: 0 ANSI: 5
Mar 25 20:49:39 gary-laptop kernel: [    6.056699] scsi 0:0:1:0: CD-ROM            Slimtype COMBO SSC-2485K  5RK1 PQ: 0 ANSI: 5
Mar 25 20:49:39 gary-laptop kernel: [    6.090210] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Mar 25 20:49:39 gary-laptop kernel: [    6.090306] scsi 0:0:1:0: Attached scsi generic sg1 type 5
Mar 25 20:49:39 gary-laptop kernel: [    6.116963] Driver 'sd' needs updating - please use bus_type methods
Mar 25 20:49:39 gary-laptop kernel: [    6.117183] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Mar 25 20:49:39 gary-laptop kernel: [    6.117227] sd 0:0:0:0: [sda] Write Protect is off
Mar 25 20:49:39 gary-laptop kernel: [    6.117234] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 25 20:49:39 gary-laptop kernel: [    6.117306] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 25 20:49:39 gary-laptop kernel: [    6.117456] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Mar 25 20:49:39 gary-laptop kernel: [    6.117497] sd 0:0:0:0: [sda] Write Protect is off
Mar 25 20:49:39 gary-laptop kernel: [    6.117504] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 25 20:49:39 gary-laptop kernel: [    6.117576] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 25 20:49:39 gary-laptop kernel: [    6.117586]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Mar 25 20:49:39 gary-laptop kernel: [    6.140149]  sda1 sda2 < sda5 >
Mar 25 20:49:39 gary-laptop kernel: [    6.163693] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 25 20:49:39 gary-laptop kernel: [    6.173260] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
Mar 25 20:49:39 gary-laptop kernel: [    6.173270] Uniform CD-ROM driver Revision: 3.20
Mar 25 20:49:39 gary-laptop kernel: [    6.173484] sr 0:0:1:0: Attached scsi CD-ROM sr0
Mar 25 20:49:39 gary-laptop kernel: [    6.459192] PM: Starting manual resume from disk
Mar 25 20:49:39 gary-laptop kernel: [    6.459201] PM: Resume from partition 8:5
Mar 25 20:49:39 gary-laptop kernel: [    6.459206] PM: Checking hibernation image.
Mar 25 20:49:39 gary-laptop kernel: [    6.459411] PM: Resume from disk failed.
Mar 25 20:49:39 gary-laptop kernel: [    6.543119] kjournald starting.  Commit interval 5 seconds
Mar 25 20:49:39 gary-laptop kernel: [    6.543152] EXT3-fs: mounted filesystem with ordered data mode.
Mar 25 20:49:39 gary-laptop kernel: [   14.919413] udevd version 124 started
Mar 25 20:49:39 gary-laptop kernel: [   15.995088] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 25 20:49:39 gary-laptop kernel: [   16.142183] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 25 20:49:39 gary-laptop kernel: [   16.452292] Linux agpgart interface v0.103
Mar 25 20:49:39 gary-laptop kernel: [   16.540114] intel_rng: FWH not detected
Mar 25 20:49:39 gary-laptop kernel: [   16.584848] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
Mar 25 20:49:39 gary-laptop kernel: [   16.586066] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Mar 25 20:49:39 gary-laptop kernel: [   16.607104] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Mar 25 20:49:39 gary-laptop kernel: [   16.834729] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Mar 25 20:49:39 gary-laptop kernel: [   16.852048] ACPI: Power Button (FF) [PWRF]
Mar 25 20:49:39 gary-laptop kernel: [   16.852258] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Mar 25 20:49:39 gary-laptop kernel: [   16.857032] ACPI: Lid Switch [LID0]
Mar 25 20:49:39 gary-laptop kernel: [   16.857215] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
Mar 25 20:49:39 gary-laptop kernel: [   16.885819] ACPI: Sleep Button (CM) [SLPB]
Mar 25 20:49:39 gary-laptop kernel: [   16.973097] ACPI: WMI: Mapper loaded
Mar 25 20:49:39 gary-laptop kernel: [   17.044197] iTCO_vendor_support: vendor-support=0
Mar 25 20:49:39 gary-laptop kernel: [   17.057255] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Mar 25 20:49:39 gary-laptop kernel: [   17.058060] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
Mar 25 20:49:39 gary-laptop kernel: [   17.058314] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar 25 20:49:39 gary-laptop kernel: [   17.260441] input: PC Speaker as /devices/platform/pcspkr/input/input5
Mar 25 20:49:39 gary-laptop kernel: [   17.520330] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0093]
Mar 25 20:49:39 gary-laptop kernel: [   17.520372] Yenta: Using CSCINT to route CSC interrupts to PCI
Mar 25 20:49:39 gary-laptop kernel: [   17.520378] Yenta: Routing CardBus interrupts to PCI
Mar 25 20:49:39 gary-laptop kernel: [   17.520389] Yenta TI: socket 0000:0a:09.0, mfunc 0x01aa1b22, devctl 0x44
Mar 25 20:49:39 gary-laptop kernel: [   17.752890] Yenta: ISA IRQ mask 0x0cf8, PCI irq 22
Mar 25 20:49:39 gary-laptop kernel: [   17.752899] Socket status: 30000006
Mar 25 20:49:39 gary-laptop kernel: [   17.752907] Yenta: Raising subordinate bus# of parent bus (#0a) from #0a to #0e
Mar 25 20:49:39 gary-laptop kernel: [   17.752921] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
Mar 25 20:49:39 gary-laptop kernel: [   17.752928] cs: IO port probe 0x4000-0x4fff: clean.
Mar 25 20:49:39 gary-laptop kernel: [   17.753528] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
Mar 25 20:49:39 gary-laptop kernel: [   17.753535] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
Mar 25 20:49:39 gary-laptop kernel: [   18.507573] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input6
Mar 25 20:49:39 gary-laptop kernel: [   18.533037] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Mar 25 20:49:39 gary-laptop kernel: [   18.777340] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Mar 25 20:49:39 gary-laptop kernel: [   18.777349] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Mar 25 20:49:39 gary-laptop kernel: [   18.777458] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 25 20:49:39 gary-laptop kernel: [   18.777479] iwl3945 0000:03:00.0: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [   18.777511] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Mar 25 20:49:39 gary-laptop kernel: [   18.914338] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Mar 25 20:49:39 gary-laptop kernel: [   18.915784] phy0: Selected rate control algorithm 'iwl-3945-rs'
Mar 25 20:49:39 gary-laptop kernel: [   19.657969] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x204000
Mar 25 20:49:39 gary-laptop kernel: [   19.691957] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Mar 25 20:49:39 gary-laptop kernel: [   19.756420] iwl3945 0000:03:00.0: PCI INT A disabled
Mar 25 20:49:39 gary-laptop kernel: [   19.866959] acer-wmi: Acer Laptop ACPI-WMI Extras
Mar 25 20:49:39 gary-laptop kernel: [   19.970334] Registered led device: acer-wmi::mail
Mar 25 20:49:39 gary-laptop kernel: [   20.003537] ACPI: Battery Slot [BAT0] (battery present)
Mar 25 20:49:39 gary-laptop kernel: [   20.004495] ACPI: AC Adapter [ADP1] (on-line)
Mar 25 20:49:39 gary-laptop kernel: [   20.270958] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Mar 25 20:49:39 gary-laptop kernel: [   20.270979] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Mar 25 20:49:39 gary-laptop kernel: [   20.271019] HDA Intel 0000:00:1b.0: setting latency timer to 64
Mar 25 20:49:39 gary-laptop kernel: [   21.647232] cs: IO port probe 0x100-0x3af: clean.
Mar 25 20:49:39 gary-laptop kernel: [   21.649687] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Mar 25 20:49:39 gary-laptop kernel: [   21.650709] cs: IO port probe 0x820-0x8ff: clean.
Mar 25 20:49:39 gary-laptop kernel: [   21.651556] cs: IO port probe 0xc00-0xcf7: clean.
Mar 25 20:49:39 gary-laptop kernel: [   21.652785] cs: IO port probe 0xa00-0xaff: clean.
Mar 25 20:49:39 gary-laptop kernel: [   22.858521] lp: driver loaded but no devices found
Mar 25 20:49:39 gary-laptop kernel: [   23.196351] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k
Mar 25 20:49:39 gary-laptop kernel: [   23.791078] EXT3 FS on sda1, internal journal
Mar 25 20:49:39 gary-laptop kernel: [   25.257035] type=1505 audit(1238032176.706:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4113
Mar 25 20:49:39 gary-laptop kernel: [   25.393479] type=1505 audit(1238032176.842:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4118
Mar 25 20:49:39 gary-laptop kernel: [   25.851510] type=1505 audit(1238032177.298:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4122
Mar 25 20:49:39 gary-laptop kernel: [   25.851911] type=1505 audit(1238032177.298:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4122
Mar 25 20:49:39 gary-laptop kernel: [   26.135737] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 25 20:49:39 gary-laptop kernel: [   28.538686] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Mar 25 20:49:39 gary-laptop avahi-daemon[4731]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Mar 25 20:49:40 gary-laptop avahi-daemon[4731]: Successfully dropped root privileges.
Mar 25 20:49:40 gary-laptop avahi-daemon[4731]: avahi-daemon 0.6.23 starting up.
Mar 25 20:49:40 gary-laptop avahi-daemon[4731]: Successfully called chroot().
Mar 25 20:49:40 gary-laptop avahi-daemon[4731]: Successfully dropped remaining capabilities.
Mar 25 20:49:40 gary-laptop avahi-daemon[4731]: No service file found in /etc/avahi/services.
Mar 25 20:49:40 gary-laptop avahi-daemon[4731]: Network interface enumeration completed.
Mar 25 20:49:40 gary-laptop avahi-daemon[4731]: Registering HINFO record with values 'I686'/'LINUX'.
Mar 25 20:49:40 gary-laptop avahi-daemon[4731]: Server startup complete. Host name is gary-laptop.local. Local service cookie is 2704534654.
Mar 25 20:49:40 gary-laptop kernel: [   28.691260] apm: BIOS not found.
Mar 25 20:49:41 gary-laptop kernel: [   30.235593] ppdev: user-space parallel port driver
Mar 25 20:49:44 gary-laptop postfix/master[5154]: daemon started -- version 2.5.5, configuration /etc/postfix
Mar 25 20:49:46 gary-laptop kernel: [   34.559778] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Mar 25 20:49:46 gary-laptop kernel: [   34.559793] vboxdrv: Successfully done.
Mar 25 20:49:46 gary-laptop kernel: [   34.559799] vboxdrv: Found 2 processor cores.
Mar 25 20:49:46 gary-laptop kernel: [   34.563071] vboxdrv: fAsync=0 offMin=0x555 offMax=0x23cd
Mar 25 20:49:46 gary-laptop kernel: [   34.563093] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Mar 25 20:49:46 gary-laptop kernel: [   34.563100] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
Mar 25 20:49:46 gary-laptop kernel: [   35.415913] NET: Registered protocol family 10
Mar 25 20:49:46 gary-laptop kernel: [   35.418225] lo: Disabled Privacy Extensions
Mar 25 20:49:47 gary-laptop acpid: client connected from 5328[111:122] 
Mar 25 20:49:47 gary-laptop dhclient: isc-dhclient-V3.1.1
Mar 25 20:49:48 gary-laptop bluetoothd[5385]: Bluetooth daemon
Mar 25 20:49:48 gary-laptop kernel: [   36.892225] Bluetooth: Core ver 2.13
Mar 25 20:49:48 gary-laptop kernel: [   36.893134] NET: Registered protocol family 31
Mar 25 20:49:48 gary-laptop kernel: [   36.893143] Bluetooth: HCI device and connection manager initialized
Mar 25 20:49:48 gary-laptop kernel: [   36.893151] Bluetooth: HCI socket layer initialized
Mar 25 20:49:48 gary-laptop bluetoothd[5385]: Starting SDP server
Mar 25 20:49:48 gary-laptop kernel: [   36.953186] Bluetooth: L2CAP ver 2.11
Mar 25 20:49:48 gary-laptop kernel: [   36.953198] Bluetooth: L2CAP socket layer initialized
Mar 25 20:49:48 gary-laptop kernel: [   36.999177] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Mar 25 20:49:48 gary-laptop kernel: [   36.999185] Bluetooth: BNEP filters: protocol multicast
Mar 25 20:49:48 gary-laptop kernel: [   37.060570] Bridge firewalling registered
Mar 25 20:49:48 gary-laptop bluetoothd[5385]: bridge pan0 created
Mar 25 20:49:48 gary-laptop kernel: [   37.099094] Bluetooth: RFCOMM socket layer initialized
Mar 25 20:49:48 gary-laptop kernel: [   37.099564] Bluetooth: RFCOMM TTY layer initialized
Mar 25 20:49:48 gary-laptop kernel: [   37.099575] Bluetooth: RFCOMM ver 1.10
Mar 25 20:49:48 gary-laptop kernel: [   37.135609] Bluetooth: SCO (Voice Link) ver 0.6
Mar 25 20:49:48 gary-laptop kernel: [   37.135621] Bluetooth: SCO socket layer initialized
Mar 25 20:49:48 gary-laptop bluetoothd[5385]: Starting experimental netlink support
Mar 25 20:49:48 gary-laptop bluetoothd[5385]: Failed to find Bluetooth netlink family
Mar 25 20:49:48 gary-laptop bluetoothd[5385]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  starting... 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/iwl_wlan_switch 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  eth0: driver is 'NULL(info.linux.driver)'. 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_16_d3_41_f5_69 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  wlan0: driver is 'iwl3945'. 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_13_02_85_36_03 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  Trying to start the supplicant... 
Mar 25 20:49:48 gary-laptop NetworkManager: <info>  Trying to start the system settings daemon... 
Mar 25 20:49:48 gary-laptop nm-system-settings:    SCPlugin-Ifupdown: init!
Mar 25 20:49:48 gary-laptop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Mar 25 20:49:48 gary-laptop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Mar 25 20:49:48 gary-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_16_d3_41_f5_69, iface: eth0): not well known
Mar 25 20:49:48 gary-laptop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_13_02_85_36_03, iface: wlan0): not well known
Mar 25 20:49:48 gary-laptop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Mar 25 20:49:48 gary-laptop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 25 20:49:48 gary-laptop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 25 20:49:48 gary-laptop nm-system-settings:    SCPlugin-Ifupdown: (146538784) ... get_connections.
Mar 25 20:49:48 gary-laptop nm-system-settings:    SCPlugin-Ifupdown: (146538784) ... get_connections (managed=false): return empty list.
Mar 25 20:49:48 gary-laptop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Mar 25 20:49:49 gary-laptop NetworkManager: <info>  (wlan0): supplicant manager is now in state 1 (from 0). 
Mar 25 20:49:49 gary-laptop acpid: client connected from 5507[0:0] 
Mar 25 20:49:50 gary-laptop anacron[5553]: Anacron 2.3 started on 2009-03-25
Mar 25 20:49:50 gary-laptop anacron[5553]: Normal exit (0 jobs run)
Mar 25 20:49:50 gary-laptop /usr/sbin/cron[5596]: (CRON) INFO (pidfile fd = 3)
Mar 25 20:49:50 gary-laptop /usr/sbin/cron[5597]: (CRON) STARTUP (fork ok)
Mar 25 20:49:50 gary-laptop /usr/sbin/cron[5597]: (CRON) INFO (Running @reboot jobs)
Mar 25 20:49:52 gary-laptop kernel: [   40.732455] [drm] Initialized drm 1.1.0 20060810
Mar 25 20:49:52 gary-laptop kernel: [   40.747664] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 25 20:49:52 gary-laptop kernel: [   40.747683] pci 0000:00:02.0: setting latency timer to 64
Mar 25 20:49:52 gary-laptop kernel: [   40.747999] [drm] Initialized i915 1.6.0 20060119 on minor 0
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (eth0): bringing up device. 
Mar 25 20:49:52 gary-laptop kernel: [   41.317376] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (eth0): preparing device. 
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (wlan0): bringing up device. 
Mar 25 20:49:52 gary-laptop kernel: [   41.319921] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Mar 25 20:49:52 gary-laptop kernel: [   41.320085] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
Mar 25 20:49:52 gary-laptop kernel: [   41.321830] firmware: requesting iwlwifi-3945-1.ucode
Mar 25 20:49:52 gary-laptop nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_16_d3_41_f5_69
Mar 25 20:49:52 gary-laptop kernel: [   41.447301] Registered led device: iwl-phy0:radio
Mar 25 20:49:52 gary-laptop kernel: [   41.447328] Registered led device: iwl-phy0:assoc
Mar 25 20:49:52 gary-laptop kernel: [   41.447387] Registered led device: iwl-phy0:RX
Mar 25 20:49:52 gary-laptop kernel: [   41.447406] Registered led device: iwl-phy0:TX
Mar 25 20:49:52 gary-laptop kernel: [   41.460980] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (wlan0): preparing device. 
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Mar 25 20:49:52 gary-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Mar 25 20:49:53 gary-laptop kernel: [   41.567304] NET: Registered protocol family 17
Mar 25 20:49:53 gary-laptop NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Mar 25 20:49:55 gary-laptop kernel: [   44.325428] wlan0: authenticate with AP 00:1d:7e:df:c0:f3
Mar 25 20:49:55 gary-laptop kernel: [   44.327402] wlan0: authenticated
Mar 25 20:49:55 gary-laptop kernel: [   44.327416] wlan0: associate with AP 00:1d:7e:df:c0:f3
Mar 25 20:49:55 gary-laptop kernel: [   44.329999] wlan0: RX AssocResp from 00:1d:7e:df:c0:f3 (capab=0x401 status=0 aid=1)
Mar 25 20:49:55 gary-laptop kernel: [   44.330012] wlan0: associated
Mar 25 20:49:55 gary-laptop kernel: [   44.331350] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Mar 25 20:49:55 gary-laptop kernel: [   44.334395] wlan0: disassociating by local choice (reason=3)
Mar 25 20:49:56 gary-laptop avahi-daemon[4731]: Registering new address record for fe80::213:2ff:fe85:3603 on wlan0.*.
Mar 25 20:50:05 gary-laptop kernel: [   54.468078] wlan0: no IPv6 routers present
Mar 25 20:50:06 gary-laptop pulseaudio[5842]: ltdl-bind-now.c: Failed to find original dlopen loader.
Mar 25 20:50:06 gary-laptop pulseaudio[5844]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Mar 25 20:50:06 gary-laptop pulseaudio[5844]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 25 20:50:11 gary-laptop x-session-manager[5759]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 
Mar 25 20:50:16 gary-laptop kernel: [   65.211460] wlan0: associate with AP 00:1d:7e:df:c0:f3
Mar 25 20:50:16 gary-laptop kernel: [   65.215700] wlan0: RX ReassocResp from 00:1d:7e:df:c0:f3 (capab=0x401 status=0 aid=1)
Mar 25 20:50:16 gary-laptop kernel: [   65.215708] wlan0: associated
Mar 25 20:50:16 gary-laptop kernel: [   65.216581] wlan0: disassociating by local choice (reason=3)
Mar 25 20:50:22 gary-laptop x-session-manager[5759]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 
Mar 25 20:50:33 gary-laptop x-session-manager[5759]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Mar 25 20:50:33 gary-laptop x-session-manager[5759]: WARNING: Could not launch application 'Screenlets%20Daemon.desktop': Unable to start application: Failed to execute child process "/usr/share/screenlets-manager/screenlets-daemon.py" (No such file or directory) 
Mar 25 20:50:34 gary-laptop pulseaudio[5844]: module-x11-xsmp.c: X11 session manager not running.
Mar 25 20:50:34 gary-laptop pulseaudio[5844]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Mar 25 20:50:38 gary-laptop anacron[6114]: Anacron 2.3 started on 2009-03-25
Mar 25 20:50:38 gary-laptop anacron[6114]: Normal exit (0 jobs run)
Mar 25 20:50:39 gary-laptop kernel: [   87.662225] CPU0 attaching NULL sched-domain.
Mar 25 20:50:39 gary-laptop kernel: [   87.662245] CPU1 attaching NULL sched-domain.
Mar 25 20:50:39 gary-laptop kernel: [   87.692433] CPU0 attaching sched-domain:
Mar 25 20:50:39 gary-laptop kernel: [   87.692445]  domain 0: span 0-1 level MC
Mar 25 20:50:39 gary-laptop kernel: [   87.692452]   groups: 0 1
Mar 25 20:50:39 gary-laptop kernel: [   87.692466] CPU1 attaching sched-domain:
Mar 25 20:50:39 gary-laptop kernel: [   87.692471]  domain 0: span 0-1 level MC
Mar 25 20:50:39 gary-laptop kernel: [   87.692478]   groups: 1 0
Mar 25 20:50:46 gary-laptop kernel: [   95.229252] wlan0: associate with AP 00:1d:7e:df:c0:f3
Mar 25 20:50:46 gary-laptop kernel: [   95.235899] wlan0: RX ReassocResp from 00:1d:7e:df:c0:f3 (capab=0x401 status=0 aid=1)
Mar 25 20:50:46 gary-laptop kernel: [   95.235914] wlan0: associated
Mar 25 20:50:46 gary-laptop kernel: [   95.238599] wlan0: disassociating by local choice (reason=3)
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linksys' 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linksys' requires no security.  No secrets needed. 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Config: added 'ssid' value 'linksys' 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 25 20:51:00 gary-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 2 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Mar 25 20:51:02 gary-laptop kernel: [  110.698599] wlan0: authenticate with AP 00:1d:7e:df:c0:f3
Mar 25 20:51:02 gary-laptop kernel: [  110.700677] wlan0: authenticated
Mar 25 20:51:02 gary-laptop kernel: [  110.700693] wlan0: associate with AP 00:1d:7e:df:c0:f3
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'. 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Mar 25 20:51:02 gary-laptop kernel: [  110.703222] wlan0: RX ReassocResp from 00:1d:7e:df:c0:f3 (capab=0x401 status=0 aid=1)
Mar 25 20:51:02 gary-laptop kernel: [  110.703234] wlan0: associated
Mar 25 20:51:02 gary-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 25 20:51:02 gary-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 25 20:51:02 gary-laptop dhclient: All rights reserved.
Mar 25 20:51:02 gary-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 25 20:51:02 gary-laptop dhclient: 
Mar 25 20:51:02 gary-laptop dhclient: wmaster0: unknown hardware address type 801
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  dhclient started with pid 6153 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Mar 25 20:51:02 gary-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit 
Mar 25 20:51:02 gary-laptop dhclient: wmaster0: unknown hardware address type 801
Mar 25 20:51:02 gary-laptop dhclient: Listening on LPF/wlan0/00:13:02:85:36:03
Mar 25 20:51:02 gary-laptop dhclient: Sending on   LPF/wlan0/00:13:02:85:36:03
Mar 25 20:51:02 gary-laptop dhclient: Sending on   Socket/fallback
Mar 25 20:51:02 gary-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Mar 25 20:51:05 gary-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Mar 25 20:51:06 gary-laptop dhclient: DHCPOFFER of 192.168.1.104 from 192.168.1.1
Mar 25 20:51:06 gary-laptop dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Mar 25 20:51:12 gary-laptop dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Mar 25 20:51:28 gary-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Mar 25 20:51:29 gary-laptop dhclient: DHCPOFFER of 192.168.1.104 from 192.168.1.1
Mar 25 20:51:29 gary-laptop dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Mar 25 20:51:36 gary-laptop dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Mar 25 20:51:36 gary-laptop dhclient: DHCPACK of 192.168.1.104 from 192.168.1.1
Mar 25 20:51:36 gary-laptop dhclient: bound to 192.168.1.104 -- renewal in 33320 seconds.
Mar 25 20:51:36 gary-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>    address 192.168.1.104 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>    gateway 192.168.1.1 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>    nameserver '68.75.115.94' 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>    nameserver '206.141.192.60' 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Mar 25 20:51:36 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Mar 25 20:51:36 gary-laptop avahi-daemon[4731]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.104.
Mar 25 20:51:36 gary-laptop avahi-daemon[4731]: New relevant interface wlan0.IPv4 for mDNS.
Mar 25 20:51:36 gary-laptop avahi-daemon[4731]: Registering new address record for 192.168.1.104 on wlan0.IPv4.
Mar 25 20:51:37 gary-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Mar 25 20:51:37 gary-laptop NetworkManager: <info>  Policy set 'Auto linksys' (wlan0) as default for routing and DNS. 
Mar 25 20:51:37 gary-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Mar 25 20:51:37 gary-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 25 20:51:37 gary-laptop postfix/master[5154]: reload configuration /etc/postfix
Mar 25 20:51:44 gary-laptop ntpdate[6234]: adjust time server 91.189.94.4 offset 0.141169 sec
Mar 25 20:53:21 gary-laptop kernel: [  249.557078] CE: hpet increasing min_delta_ns to 15000 nsec
Mar 25 21:09:39 gary-laptop -- MARK --
Mar 25 21:13:35 gary-laptop kernel: [ 1464.488868] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Mar 25 21:13:35 gary-laptop kernel: [ 1464.538853] usbcore: registered new interface driver ndiswrapper
Mar 25 21:14:52 gary-laptop kernel: [ 1540.948172] usb 5-1: new high speed USB device using ehci_hcd and address 2
Mar 25 21:14:52 gary-laptop kernel: [ 1541.084862] usb 5-1: configuration #1 chosen from 1 choice
Mar 25 21:14:52 gary-laptop kernel: [ 1541.212197] usb 5-1: reset high speed USB device using ehci_hcd and address 2
Mar 25 21:14:52 gary-laptop kernel: [ 1541.401571] ndiswrapper: driver ndiswdm (Linksys, A Division of Cisco,10/09/2007,4.118.4.0) loaded
Mar 25 21:17:01 gary-laptop /USR/SBIN/CRON[7937]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 25 21:29:39 gary-laptop -- MARK --

```

Is it really work ?
The little light of my wusb just like never bright, it's never turn on. I don't why the light turn off, it turn off even when i try it on window xp in computer of my friend. It work on window, but the light just turn off :confused: 
Anyone can tell me my WUSB work or not ?

---

### Post by balloooza on 2009-03-25
It looks like it is working, from that log, can you run
```
dhclient
```
also the output of
```
ifconfig
```
and can you click the networking icon in the top right of the screen, and see if your network is there.

---

