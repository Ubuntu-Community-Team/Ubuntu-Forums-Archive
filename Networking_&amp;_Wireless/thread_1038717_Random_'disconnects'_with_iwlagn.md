---
title: "Random 'disconnects' with iwlagn"
date: 2009-01-13
forum: Networking &amp; Wireless
---

### Post by cdahmedeh on 2009-01-13
Hello,

I've noticed that on certain occasions, my network disconnects. The network managers thinks I'm still connected, however I cannot visits pages in the browser and I got server error messages with pidgin. This problem is fixed by reconnecting with the Network Manager Applet. However this is very annoying. This is dmesg output after a reconnect after a disconnect. I've installed linux-backports-modules-2.6.27-11-generic which fixed some kernel panics that I've had due to the wireless network card. However, it has not fixed the disconnect problem. The problem occurs around every hour/two hours.

Thanks

```
[    1.291324] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.291360] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.291394] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.291477] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.291527] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.291575] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.291609] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.291643] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.291748] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.291797] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.291846] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.291880] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.291913] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.292018] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.292068] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.292116] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.292149] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.292182] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.292482] isapnp: Scanning for PnP cards...
[    1.646478] isapnp: No Plug & Play device found
[    1.673949] hpet_resources: 0xfed00000 is busy
[    1.674041] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.675837] brd: module loaded
[    1.675897] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.675997] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.688763] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.688767] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.688988] mice: PS/2 mouse device common for all mice
[    1.689659] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.689689] rtc0: alarms up to one month, y3k, hpet irqs
[    1.689793] EISA: Probing bus 0 at eisa.0
[    1.689800] Cannot allocate resource for EISA slot 1
[    1.689830] EISA: Detected 0 cards.
[    1.689833] cpuidle: using governor ladder
[    1.689835] cpuidle: using governor menu
[    1.690272] TCP cubic registered
[    1.690295] Using IPI No-Shortcut mode
[    1.690437] registered taskstats version 1
[    1.690558]   Magic number: 9:103:401
[    1.690639] rtc_cmos 00:04: setting system clock to 2009-01-13 22:23:08 UTC (1231885388)
[    1.690642] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.690644] EDD information not available.
[    1.690860] Freeing unused kernel memory: 424k freed
[    1.690894] Write protecting the kernel text: 2580k
[    1.690917] Write protecting the kernel read-only data: 940k
[    1.726142] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.743235] vesafb: framebuffer at 0xf3000000, mapped to 0xf8880000, using 2560k, total 14336k
[    1.743238] vesafb: mode is 1280x1024x8, linelength=1280, pages=1
[    1.743240] vesafb: protected mode interface info at c000:ba10
[    1.743243] vesafb: pmi: set display start = c00cba73, set palette = c00cbace
[    1.743244] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    1.743257] vesafb: scrolling: redraw
[    1.743259] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
[    1.743408] Console: switching to colour frame buffer device 160x64
[    1.763807] fb0: VESA VGA frame buffer device
[    1.840388] fuse init (API version 7.9)
[    1.856722] ACPI: SSDT BFE72D38, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.857055] ACPI: SSDT BFE726CE, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.857398] Monitor-Mwait will be used to enter C-1 state
[    1.857401] Monitor-Mwait will be used to enter C-2 state
[    1.857403] Monitor-Mwait will be used to enter C-3 state
[    1.857561] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.857610] processor ACPI0007:00: registered as cooling_device0
[    1.857614] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.857925] ACPI: SSDT BFE72F7C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.858208] ACPI: SSDT BFE72CB3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.858682] Marking TSC unstable due to TSC halts in idle
[    1.858756] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.858800] processor ACPI0007:01: registered as cooling_device1
[    1.858804] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.861178] thermal LNXTHERM:01: registered as thermal_zone0
[    1.861380] ACPI: Thermal Zone [THM] (67 C)
[    2.094522] usbcore: registered new interface driver usbfs
[    2.094541] usbcore: registered new interface driver hub
[    2.094577] usbcore: registered new device driver usb
[    2.100138] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.100150] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.100154] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.100188] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.104083] ehci_hcd 0000:00:1a.7: debug port 1
[    2.104090] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.104102] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.109954] USB Universal Host Controller Interface driver v3.0
[    2.120016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.120126] usb usb1: configuration #1 chosen from 1 choice
[    2.120151] hub 1-0:1.0: USB hub found
[    2.120157] hub 1-0:1.0: 4 ports detected
[    2.153504] No dock devices found.
[    2.184345] SCSI subsystem initialized
[    2.223644] libata version 3.00 loaded.
[    2.332266] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.332276] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.332280] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.332310] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[    2.332346] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    2.332429] usb usb2: configuration #1 chosen from 1 choice
[    2.332453] hub 2-0:1.0: USB hub found
[    2.332458] hub 2-0:1.0: 2 ports detected
[    2.444024] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.536522] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.536533] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.536536] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.536559] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[    2.536594] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    2.536672] usb usb3: configuration #1 chosen from 1 choice
[    2.536695] hub 3-0:1.0: USB hub found
[    2.536700] hub 3-0:1.0: 2 ports detected
[    2.577409] usb 1-1: configuration #1 chosen from 1 choice
[    2.640595] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.640610] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.640613] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.640633] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    2.644543] ehci_hcd 0000:00:1d.7: debug port 1
[    2.644550] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.644555] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    2.700258] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.700386] usb usb4: configuration #1 chosen from 1 choice
[    2.700421] hub 4-0:1.0: USB hub found
[    2.700426] hub 4-0:1.0: 6 ports detected
[    2.908452] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.908459] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.908462] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.908488] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.908514] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    2.908588] usb usb5: configuration #1 chosen from 1 choice
[    2.908610] hub 5-0:1.0: USB hub found
[    2.908614] hub 5-0:1.0: 2 ports detected
[    3.000235] Clocksource tsc unstable (delta = -393009730 ns)
[    3.116461] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.116468] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.116472] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.116492] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.116518] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    3.116591] usb usb6: configuration #1 chosen from 1 choice
[    3.116613] hub 6-0:1.0: USB hub found
[    3.116617] hub 6-0:1.0: 2 ports detected
[    3.120237] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    3.292713] usb 2-2: configuration #1 chosen from 1 choice
[    3.324460] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.324467] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.324471] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.324491] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.324517] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    3.324593] usb usb7: configuration #1 chosen from 1 choice
[    3.324621] hub 7-0:1.0: USB hub found
[    3.324626] hub 7-0:1.0: 2 ports detected
[    3.404243] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    3.532861] ata_piix 0000:00:1f.1: version 2.12
[    3.532870] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.532907] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.533349] scsi0 : ata_piix
[    3.534116] scsi1 : ata_piix
[    3.534803] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    3.534806] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    3.558062] usb 4-1: configuration #1 chosen from 1 choice
[    3.712767] ata1.00: ATAPI: TEAC   DVD+/-RW DVW28SLC, A.06, max UDMA/33
[    3.745650] ata1.00: configured for UDMA/33
[    3.745721] ata2: port disabled. ignoring.
[    3.757001] scsi 0:0:0:0: CD-ROM            TEAC     DVD+-RW DVW28SLC A.06 PQ: 0 ANSI: 5
[    3.757205] ahci 0000:00:1f.2: version 3.0
[    3.757218] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.757326] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    3.757329] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    3.757335] ahci 0000:00:1f.2: setting latency timer to 64
[    3.757464] scsi2 : ahci
[    3.757519] scsi3 : ahci
[    3.757570] scsi4 : ahci
[    3.757829] ata3: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb900 irq 219
[    3.757831] ata4: DUMMY
[    3.757834] ata5: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffba00 irq 219
[    3.964240] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    4.076257] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.076829] ata3.00: ATA-8: FUJITSU MHW2160BJ FFS G2, 0085001C, max UDMA/100
[    4.076835] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    4.077646] ata3.00: configured for UDMA/100
[    4.137712] usb 6-1: configuration #1 chosen from 1 choice
[    4.384135] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    4.412254] ata5: SATA link down (SStatus 0 SControl 300)
[    4.428356] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 0085 PQ: 0 ANSI: 5
[    4.428494] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.428504] sky2 0000:09:00.0: setting latency timer to 64
[    4.428528] sky2 0000:09:00.0: v1.22 addr 0xf1ffc000 irq 16 Yukon-2 FE+ rev 0
[    4.429701] sky2 eth0: addr 00:21:9b:f8:ea:80
[    4.429741] ohci1394 0000:03:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.482436] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f1bff800-f1bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.512503] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.512536] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    4.549579] Driver 'sr' needs updating - please use bus_type methods
[    4.556193] Driver 'sd' needs updating - please use bus_type methods
[    4.578967] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    4.578972] Uniform CD-ROM driver Revision: 3.20
[    4.579098] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.581493] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.581508] sd 2:0:0:0: [sda] Write Protect is off
[    4.581511] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.581534] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.581591] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.581604] sd 2:0:0:0: [sda] Write Protect is off
[    4.581607] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.581630] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.581633]  sda:<6>usb 7-2: configuration #1 chosen from 1 choice
[    4.605645] hub 7-2:1.0: USB hub found
[    4.608179] hub 7-2:1.0: 3 ports detected
[    4.614933]  sda1 sda2 < sda5 >
[    4.642438] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.897604] usb 7-2.1: new full speed USB device using uhci_hcd and address 3
[    5.021691] usb 7-2.1: configuration #1 chosen from 1 choice
[    5.097604] usb 7-2.2: new full speed USB device using uhci_hcd and address 4
[    5.227702] usb 7-2.2: configuration #1 chosen from 1 choice
[    5.305604] usb 7-2.3: new full speed USB device using uhci_hcd and address 5
[    5.435691] usb 7-2.3: configuration #1 chosen from 1 choice
[    5.439634] usbcore: registered new interface driver hiddev
[    5.439672] usbcore: registered new interface driver libusual
[    5.445091] Initializing USB Mass Storage driver...
[    5.445697] scsi5 : SCSI emulation for USB Mass Storage devices
[    5.445764] usb-storage: device found at 2
[    5.445767] usb-storage: waiting for device to settle before scanning
[    5.452944] input: KYE OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input2
[    5.455714] input,hidraw0: USB HID v1.10 Mouse [KYE OPTICAL MOUSE] on usb-0000:00:1d.1-1
[    5.459886] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input3
[    5.460034] input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2
[    5.463952] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input4
[    5.464126] input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3
[    5.464150] usbcore: registered new interface driver usb-storage
[    5.464153] USB Mass Storage support registered.
[    5.464265] usbcore: registered new interface driver usbhid
[    5.464268] usbhid: v2.6:USB HID core driver
[    5.511965] PM: Starting manual resume from disk
[    5.511969] PM: Resume from partition 8:5
[    5.511970] PM: Checking hibernation image.
[    5.512112] PM: Resume from disk failed.
[    5.580415] kjournald starting.  Commit interval 5 seconds
[    5.580452] EXT3-fs: mounted filesystem with ordered data mode.
[    5.760195] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[314fc0000e22b1a1]
[   10.444354] usb-storage: device scan complete
[   10.448566] scsi 5:0:0:0: Direct-Access     ST332082 0AS                   PQ: 0 ANSI: 2
[   10.449779] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   10.452031] sd 5:0:0:0: [sdb] Write Protect is off
[   10.452036] sd 5:0:0:0: [sdb] Mode Sense: 38 00 00 00
[   10.452040] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   10.453192] sd 5:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   10.455543] sd 5:0:0:0: [sdb] Write Protect is off
[   10.455547] sd 5:0:0:0: [sdb] Mode Sense: 38 00 00 00
[   10.455551] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   10.455729]  sdb:<6>udevd version 124 started
[   11.945753] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.995345] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.084081] Linux agpgart interface v0.103
[   12.106757] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   12.250454] ACPI: Lid Switch [LID]
[   12.459321] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   12.489119] ACPI: Power Button (CM) [PBTN]
[   12.489205] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input7
[   12.521028] ACPI: Sleep Button (CM) [SBTN]
[   12.521281] ACPI: AC Adapter [AC] (on-line)
[   12.551817] ACPI: Battery Slot [BAT0] (battery present)
[   12.551961] ACPI: WMI: Mapper loaded
[   12.591037] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input8
[   12.608021] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   12.867782] nvidia: module license 'NVIDIA' taints kernel.
[   13.222751] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.222761] nvidia 0000:01:00.0: setting latency timer to 64
[   13.222909] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
[   13.224662] Linux video capture interface: v2.00
[   13.273090] cfg80211: Using static regulatory domain info
[   13.273093] cfg80211: Regulatory domain: US
[   13.273095] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.273097] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   13.273100] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.273102] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.273104] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.273107] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   13.273109] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   13.273111] cfg80211: Calling CRDA for country: US
[   13.315707] iTCO_vendor_support: vendor-support=0
[   13.323033] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.329013] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   13.329122] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.352098] Bluetooth: Core ver 2.13
[   13.357404] NET: Registered protocol family 31
[   13.357407] Bluetooth: HCI device and connection manager initialized
[   13.357410] Bluetooth: HCI socket layer initialized
[   13.430485] input: PC Speaker as /devices/platform/pcspkr/input/input9
[   13.440766] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.440769] ricoh-mmc: Copyright(c) Philip Langdale
[   13.441200] ricoh-mmc: Ricoh MMC controller found at 0000:03:09.2 [1180:0843] (rev 12)
[   13.441220] ricoh-mmc: Controller is now disabled.
[   13.455096] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   13.455184] usbcore: registered new interface driver btusb
[   13.589541] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   13.589930] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   13.590277] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   13.590469] uvcvideo: Failed to initialize the device (-5).
[   13.590821] usbcore: registered new interface driver uvcvideo
[   13.590824] USB Video Class driver (v0.1.0)
[   13.653313] sdhci: Secure Digital Host Controller Interface driver
[   13.653316] sdhci: Copyright(c) Pierre Ossman
[   13.733650] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 22)
[   13.733673] sdhci-pci 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   13.736730] mmc0: SDHCI controller on PCI [0000:03:09.1] using DMA
[   13.762773] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.762776] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.762873] iwlagn 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.762904] iwlagn 0000:0b:00.0: setting latency timer to 64
[   13.762934] iwlagn 0000:0b:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.805904] iwlagn 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.817987] iwlagn 0000:0b:00.0: PCI INT A disabled
[   13.818373] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.912666] mmc0: new SD card at address e624
[   14.106269] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[   14.169207] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.169231] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.177253] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   14.224700] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.291149] mmcblk0: mmc0:e624 SD01G 992000KiB 
[   14.291192]  mmcblk0: p1
[   15.436085] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x201f1500
[   15.601184]  sdb1
[   15.601308] sd 5:0:0:0: [sdb] Attached SCSI disk
[   15.601406] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   16.545669] lp: driver loaded but no devices found
[   16.718826] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k
[   17.053121] EXT3 FS on sda1, internal journal
[   17.570045] type=1505 audit(1231885404.174:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4508
[   17.715791] type=1505 audit(1231885404.319:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4513
[   17.715967] type=1505 audit(1231885404.319:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4513
[   17.895853] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.589927] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   21.298325] apm: BIOS not found.
[   21.501683] ppdev: user-space parallel port driver
[   26.351321] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   26.351334] vboxdrv: Successfully done.
[   26.351339] vboxdrv: Found 2 processor cores.
[   26.355603] vboxdrv: fAsync=0 offMin=0x478 offMax=0x1aa4
[   26.358621] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   26.358632] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
[   29.065133] Bluetooth: L2CAP ver 2.11
[   29.065145] Bluetooth: L2CAP socket layer initialized
[   29.103775] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.103789] Bluetooth: BNEP filters: protocol multicast
[   29.138552] Bluetooth: RFCOMM socket layer initialized
[   29.138582] Bluetooth: RFCOMM TTY layer initialized
[   29.138588] Bluetooth: RFCOMM ver 1.10
[   29.153732] Bridge firewalling registered
[   29.176246] Bluetooth: SCO (Voice Link) ver 0.6
[   29.176251] Bluetooth: SCO socket layer initialized
[   33.460276] sky2 eth0: enabling interface
[   33.464344] iwlagn 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   33.464598] iwlagn 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   33.465076] firmware: requesting lbm-iwlwifi-4965-2.ucode
[   33.523496] iwlagn 0000:0b:00.0: loaded firmware version 228.57.2.23
[   33.990046] Registered led device: iwl-phy0:radio
[   33.990450] Registered led device: iwl-phy0:assoc
[   33.990811] Registered led device: iwl-phy0:RX
[   33.991149] Registered led device: iwl-phy0:TX
[   34.116773] NET: Registered protocol family 17
[   35.790172] wlan0: authenticate with AP 00:1c:df:ab:34:19
[   35.796596] wlan0: authenticated
[   35.796605] wlan0: associate with AP 00:1c:df:ab:34:19
[   35.800573] wlan0: RX AssocResp from 00:1c:df:ab:34:19 (capab=0x1 status=0 aid=2)
[   35.800582] wlan0: associated
[   35.823602] wlan0: disassociating by local choice (reason=3)
[   40.415916] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input12
[   61.630541] wlan0: deauthenticated (Reason: 6)
[   77.857492] CPU0 attaching NULL sched-domain.
[   77.857501] CPU1 attaching NULL sched-domain.
[   77.859108] CPU0 attaching sched-domain:
[   77.859113]  domain 0: span 0-1 level MC
[   77.859117]   groups: 0 1
[   77.859123] CPU1 attaching sched-domain:
[   77.859126]  domain 0: span 0-1 level MC
[   77.859129]   groups: 1 0
[   85.989520] wlan0: authenticate with AP 00:1c:df:ab:34:19
[   85.992447] wlan0: authenticated
[   85.992460] wlan0: associate with AP 00:1c:df:ab:34:19
[   85.996347] wlan0: RX ReassocResp from 00:1c:df:ab:34:19 (capab=0x1 status=0 aid=2)
[   85.996362] wlan0: associated
[   86.054357] cfg80211: Calling CRDA for country: US
[   88.360049] NET: Registered protocol family 10
[   88.360591] lo: Disabled Privacy Extensions
[   88.361105] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   98.496103] wlan0: no IPv6 routers present
[  111.809052] CE: hpet increasing min_delta_ns to 15000 nsec
[  116.864114] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input13
[ 1592.766759] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input14
[ 1959.144076] CE: hpet increasing min_delta_ns to 22500 nsec
[ 2157.363125] CE: hpet increasing min_delta_ns to 33750 nsec
[ 4858.012375] CE: hpet increasing min_delta_ns to 50624 nsec
[ 8382.786744] iwlagn 0000:0b:00.0: Microcode SW error detected.  Restarting 0x82000000.
[ 8382.808258] iwlagn 0000:0b:00.0: No space for Tx
[ 8382.808271] iwlagn 0000:0b:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[ 8382.808277] iwlagn 0000:0b:00.0: SENSITIVITY_CMD failed
[ 8383.015491] Registered led device: iwl-phy0:radio
[ 8383.015860] Registered led device: iwl-phy0:assoc
[ 8383.016205] Registered led device: iwl-phy0:RX
[ 8383.016504] Registered led device: iwl-phy0:TX
[ 8612.784727] wlan0: disassociating by local choice (reason=3)
[ 8612.784751] HW problem - can not stop rx aggregation for tid 0
[ 8612.802476] wlan0: authenticate with AP 00:1c:df:ab:34:19
[ 8612.804603] wlan0: authenticated
[ 8612.804617] wlan0: associate with AP 00:1c:df:ab:34:19
[ 8612.809289] wlan0: RX AssocResp from 00:1c:df:ab:34:19 (capab=0x1 status=0 aid=2)
[ 8612.809302] wlan0: associated
[ 8612.832026] wlan0: disassociating by local choice (reason=3)
[ 8612.864064] wlan0: authenticate with AP 00:1c:df:ab:34:19
[ 8612.871054] wlan0: authenticate with AP 00:1c:df:ab:34:19
[ 8612.871092] wlan0: authenticated
[ 8612.871099] wlan0: associate with AP 00:1c:df:ab:34:19
[ 8612.877096] wlan0: RX ReassocResp from 00:1c:df:ab:34:19 (capab=0x1 status=0 aid=2)
[ 8612.877109] wlan0: associated
[ 9036.028319] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input15
[10546.525324] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input16
[12651.997047] iwlagn 0000:0b:00.0: Microcode SW error detected.  Restarting 0x82000000.
[12652.020137] iwlagn 0000:0b:00.0: No space for Tx
[12652.020151] iwlagn 0000:0b:00.0: Error sending SENSITIVITY_CMD: enqueue_hcmd failed: -28
[12652.020158] iwlagn 0000:0b:00.0: SENSITIVITY_CMD failed
[12652.233458] Registered led device: iwl-phy0:radio
[12652.234455] Registered led device: iwl-phy0:assoc
[12652.235409] Registered led device: iwl-phy0:RX
[12652.236299] Registered led device: iwl-phy0:TX
[12739.940677] wlan0: disassociating by local choice (reason=3)
[12739.940703] HW problem - can not stop rx aggregation for tid 0
[12739.952115] wlan0: authenticate with AP 00:1c:df:ab:34:19
[12739.956995] wlan0: authenticated
[12739.957010] wlan0: associate with AP 00:1c:df:ab:34:19
[12739.964430] wlan0: RX AssocResp from 00:1c:df:ab:34:19 (capab=0x1 status=0 aid=2)
[12739.964444] wlan0: associated
[12740.011284] wlan0: authenticate with AP 00:1c:df:ab:34:19
[12740.024837] wlan0: authenticate with AP 00:1c:df:ab:34:19
[12740.024879] wlan0: authenticated
[12740.024886] wlan0: associate with AP 00:1c:df:ab:34:19
[12740.030847] wlan0: RX ReassocResp from 00:1c:df:ab:34:19 (capab=0x1 status=0 aid=2)
[12740.030859] wlan0: associated
```

---

### Post by cdahmedeh on 2009-01-14
anyone willing to help ?

Also, my current network is not protected at all (other than MAC Address filtering).

---

### Post by cdahmedeh on 2009-01-15
Sorry for another bump.. but can anyone help, like is there other logs I need to post ? What kind of information can I put that might help..

---

### Post by wisefaiz on 2009-02-16
I take it no one responded? I have the same problem, except it disconnects every 10-15 minutes! I'm huddled on the stairs wired up to my router at the moment-if you figured it out I'd love to know how!

---

### Post by Jason_077 on 2009-03-02
Ok, I know it may sound stupid... but why not give it a try?

Try disabling the screen saver and in the Power Management uncheck "dim the display when idle".

Does it work?

---

### Post by grazzt_85 on 2009-03-13
[http://grazzt.blogspot.com/]("http://grazzt.blogspot.com/")

let me know if this works for you ;)

---

### Post by JanusDC on 2010-07-31
Same problem here. The blog posted before is no longer online.

```
janus@katu ~ $ lspci -vvv -s 0c:00.0 
0c:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1121
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 31
	Region 0: Memory at f1ffe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
```

---

### Post by SaintDanBert on 2010-08-11
> **grazzt_85 said:**
> [http://grazzt.blogspot.com/]("http://grazzt.blogspot.com/")

let me know if this works for you ;)

[highlight]The named blog reference is a DEAD LINK[/highlight]
~~~ 0;-< Dan

---

### Post by MSwal2846 on 2010-08-20
I have this same issue on my Lenovo x200 running lucid.  

Did the above suggestion work (Try disabling the screen saver and in the Power Management uncheck "dim the display when idle")? 

In my case, I do not have a screen saver, I have it set to just blank out.  And I do not have "dim the display when idle" checked while plugged in ... and I have this same problem regardless if plugged in or not.

Also, this occurs with my home network, my work network, and hotel networks ... so doesn't seem to be the network "infrastructure" but my machine.  And the duration at which all will be fine varies ... sometimes minutes, sometimes hours, sometimes days.

---

### Post by MSwal2846 on 2010-08-20
Also, I would encourage all impacted to indicate so in this bug report:

[https://bugs.launchpad.net/ubuntu/+bug/583210/](https://bugs.launchpad.net/ubuntu/+bug/583210/)

If we get enough people to reach a critical mass, the better it will be for all of us...

---

### Post by zeltak on 2010-08-21
Hi

I have the same issues with the x200 and kubuntu 10.04..i thought i was going mad..im glad i found this thread :)

i would love to try any solutions that may work for you guys

thx

Zeltak

---

### Post by MSwal2846 on 2010-08-21
One of the things suggested was to install "linux-backports-modules-wireless-lucid-generic".  So I am trying this.  So far so good....

---

### Post by zeltak on 2010-08-25
> **MSwal2846 said:**
> One of the things suggested was to install "linux-backports-modules-wireless-lucid-generic".  So I am trying this.  So far so good....


anything to report? how is it working?

thx

zeltak

---

### Post by MSwal2846 on 2010-08-25
Ok, so I've been running with the backport with NO drops and reconnects upon un-suspending.  It's been working great!

---

### Post by SaintDanBert on 2010-08-26
I had this problem on Intrepid and again on Lucid.  Hardy and Jaunty did not seem to have troubles (for me). I skipped Karmic use completely.

I have thought that some part of power management was killing things for me.  I've run streaming audio for hours without a cough, but if I let the box go idle, the driver "crashes".  I have not been able to nail down a time frame.

Does someone know how to disable power management completely ...
Actually, I want it off completely when connected to AC mains ...
... but I'll turn it off completely for tests.

There has been some complaint about [b]iwlagn[b] for some time without any effort to fix it. I think that a bug was closed recently because there had been no effort on it for too long.

---

### Post by MSwal2846 on 2010-08-27
So I want to sum up my 1 week experience with the backport installed packages.

I'm:
- running Ubuntu 10.04 Lucid 
- on a Lenovo X200 
- with 2.9G of Memory (according to the System Monitor)
- with a 320G harddrive at 67% full
- connection driver is iwlagn
- connect at work (using WEP), home (using WPA2), and various airports, hotels, coffee shops.

Prior to installing the backport files, I would EVERY DAY loose my wireless network connection ... sometimes in a few minutes and sometimes a few hours into the day.  Reconnecting was virtually impossible.  If I suspended, there was a 50/50 chance that it would connect upon waking up.  USUALLY (but not always) a reboot would fix the problem.

Last Friday, I installed from Synaptic Package Manager:
 - linux-backports-modules-wireless-lucid-generic
 - linux-backports-modules-wireless-2.6.32-24-generic

Results:
- I did NOT have a single drop all week
- I was able to reconnect from suspend EVERY time
- I've not rebooted at all since I rebooted after install the above packages last Friday (1 week ago)

I'm a VERY happy camper!!

---

### Post by zeltak on 2010-08-27
cool

my x200 is in the shop (ram issues..) but cant wait to try it when i get it back (god willing before the weekend ;-))

thx for the report

Zeltak

---

