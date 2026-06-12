---
title: "Jaunty Will not mount a commercial DVD movie"
date: 2009-06-10
forum: Multimedia Software
---

### Post by bullfroghrr on 2009-06-10
Help please, I am fairly new at this. I cannot get my laptop to mount a commercial DVD movie, I am running Ubuntu 9.04.  I have installed libdvdread4, libdvdcss, medibuntu, restricted packages, vlc. It seems like I have tried everything, I can mount a burned movie, a blank DVD, blank CD, a commercial audio cd, a burned data dvd(installed ubuntu from a dvd).  But no matter what I try I cannot get a commercial dvd movie to mount much less play.

---

### Post by reeseslover531 on 2009-06-10
What happens when you insert the disc? does nothing happen? Also it might be useful if you posted the last bit of dmesg after you insert a dvd.

---

### Post by bullfroghrr on 2009-06-10
The drive will spin and try to read for about 45 seconds then nothing. dmesg?
this is the whole thing
```

[    0.428001] EISA bus registered
[    0.428001] ACPI: bus type pci registered
[    0.428001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 13
[    0.428001] PCI: MCFG area at e0000000 reserved in E820
[    0.428001] PCI: Using MMCONFIG for extended config space
[    0.428001] PCI: Using configuration type 1 for base access
[    0.428001] ACPI: EC: Look up EC in DSDT
[    0.428001] ACPI: Interpreter enabled
[    0.428001] ACPI: (supports S0 S3 S4 S5)
[    0.428001] ACPI: Using IOAPIC for interrupt routing
[    0.430087] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.430211] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.430211] ACPI: EC: driver started in interrupt mode
[    0.430211] ACPI: No dock devices found.
[    0.430211] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.430211] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.430211] pci 0000:00:06.0: PME# disabled
[    0.430211] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0000000-0xc0000fff]
[    0.430211] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0001000-0xc0001fff]
[    0.430211] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0002000-0xc0002fff]
[    0.430211] pci 0000:00:13.2: supports D1 D2
[    0.430211] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.430211] pci 0000:00:13.2: PME# disabled
[    0.432037] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f]
[    0.432046] pci 0000:00:14.0: reg 14 32bit mmio: [0xc0003000-0xc00033ff]
[    0.432085] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.432137] pci 0000:00:14.1: reg 10 io port: [0x8430-0x8437]
[    0.432146] pci 0000:00:14.1: reg 14 io port: [0x8424-0x8427]
[    0.432154] pci 0000:00:14.1: reg 18 io port: [0x8428-0x842f]
[    0.432162] pci 0000:00:14.1: reg 1c io port: [0x8420-0x8423]
[    0.432171] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f]
[    0.432342] pci 0000:00:14.5: reg 10 32bit mmio: [0xc0003400-0xc00034ff]
[    0.432435] pci 0000:00:14.6: reg 10 32bit mmio: [0xc0003800-0xc00038ff]
[    0.432573] pci 0000:01:05.0: reg 10 32bit mmio: [0xc8000000-0xcfffffff]
[    0.432577] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.432580] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff]
[    0.432589] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.432595] pci 0000:01:05.0: supports D1 D2
[    0.432609] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.432613] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.432617] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xcfffffff]
[    0.432674] pci 0000:02:00.0: reg 10 64bit mmio: [0xc0200000-0xc0203fff]
[    0.432682] pci 0000:02:00.0: reg 18 io port: [0xa000-0xa0ff]
[    0.432716] pci 0000:02:00.0: supports D1 D2
[    0.432717] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.432722] pci 0000:02:00.0: PME# disabled
[    0.432783] pci 0000:00:06.0: bridge io port: [0xa000-0xafff]
[    0.432786] pci 0000:00:06.0: bridge 32bit mmio: [0xc0200000-0xc02fffff]
[    0.432852] pci 0000:08:05.0: reg 10 32bit mmio: [0xc0302000-0xc0302fff]
[    0.432867] pci 0000:08:05.0: supports D1 D2
[    0.432869] pci 0000:08:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.432875] pci 0000:08:05.0: PME# disabled
[    0.432911] pci 0000:08:07.0: reg 10 32bit mmio: [0xc0300000-0xc0301fff]
[    0.433030] pci 0000:08:0e.0: reg 10 32bit mmio: [0xc0303000-0xc03037ff]
[    0.433040] pci 0000:08:0e.0: reg 14 io port: [0xb000-0xb07f]
[    0.433095] pci 0000:08:0e.0: supports D2
[    0.433097] pci 0000:08:0e.0: PME# supported from D2 D3hot D3cold
[    0.433102] pci 0000:08:0e.0: PME# disabled
[    0.433147] pci 0000:00:14.4: transparent bridge
[    0.433155] pci 0000:00:14.4: bridge io port: [0xb000-0xbfff]
[    0.433161] pci 0000:00:14.4: bridge 32bit mmio: [0xc0300000-0xc03fffff]
[    0.433203] bus 00 -> node 0
[    0.433207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.433356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.433460] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.433560] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.435336] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.435430] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.435523] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.435616] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.435709] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.435802] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.435895] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.435988] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.436094] ACPI: WMI: Mapper loaded
[    0.436217] SCSI subsystem initialized
[    0.436249] libata version 3.00 loaded.
[    0.436290] usbcore: registered new interface driver usbfs
[    0.436303] usbcore: registered new interface driver hub
[    0.436324] usbcore: registered new device driver usb
[    0.436411] PCI: Using ACPI for IRQ routing
[    0.436507] Bluetooth: Core ver 2.13
[    0.436507] NET: Registered protocol family 31
[    0.436507] Bluetooth: HCI device and connection manager initialized
[    0.436507] Bluetooth: HCI socket layer initialized
[    0.436507] NET: Registered protocol family 8
[    0.436507] NET: Registered protocol family 20
[    0.436507] NetLabel: Initializing
[    0.436507] NetLabel:  domain hash size = 128
[    0.436507] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.436507] NetLabel:  unlabeled traffic allowed by default
[    0.436507] AppArmor: AppArmor Filesystem Enabled
[    0.436507] pnp: PnP ACPI init
[    0.436507] ACPI: bus type pnp registered
[    0.437784] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.437870] pnp: PnP ACPI: found 10 devices
[    0.437870] ACPI: ACPI bus type pnp unregistered
[    0.437870] PnPBIOS: Disabled by ACPI PNP
[    0.437870] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.437870] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.437870] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.437870] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.437870] system 00:08: ioport range 0x200-0x20f has been reserved
[    0.437870] system 00:08: ioport range 0x220-0x22f has been reserved
[    0.437870] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.437870] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.437870] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.437870] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.437870] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.437870] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.437870] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.437870] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.437870] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.437870] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.437870] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.437870] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.437870] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.437870] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.437870] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.437870] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.437870] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.473694] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.473697] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.473700] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.473703] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff
[    0.473707] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.473710] pci 0000:00:06.0:   IO window: 0xa000-0xafff
[    0.473713] pci 0000:00:06.0:   MEM window: 0xc0200000-0xc02fffff
[    0.473715] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.473720] pci 0000:08:05.0: CardBus bridge, secondary bus 0000:09
[    0.473722] pci 0000:08:05.0:   IO window: 0x00b400-0x00b4ff
[    0.473729] pci 0000:08:05.0:   IO window: 0x00b800-0x00b8ff
[    0.473734] pci 0000:08:05.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.473740] pci 0000:08:05.0:   MEM window: 0x54000000-0x57ffffff
[    0.473747] pci 0000:00:14.4: PCI bridge, secondary bus 0000:08
[    0.473750] pci 0000:00:14.4:   IO window: 0xb000-0xbfff
[    0.473757] pci 0000:00:14.4:   MEM window: 0xc0300000-0xc03fffff
[    0.473762] pci 0000:00:14.4:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.473777] pci 0000:00:06.0: setting latency timer to 64
[    0.473792] pci 0000:08:05.0: enabling device (0004 -> 0007)
[    0.473798] pci 0000:08:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.473805] bus: 00 index 0 io port: [0x00-0xffff]
[    0.473807] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.473809] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.473811] bus: 01 index 1 mmio: [0xc0100000-0xc01fffff]
[    0.473813] bus: 01 index 2 mmio: [0xc8000000-0xcfffffff]
[    0.473814] bus: 01 index 3 mmio: [0x0-0x0]
[    0.473816] bus: 02 index 0 io port: [0xa000-0xafff]
[    0.473818] bus: 02 index 1 mmio: [0xc0200000-0xc02fffff]
[    0.473820] bus: 02 index 2 mmio: [0x0-0x0]
[    0.473821] bus: 02 index 3 mmio: [0x0-0x0]
[    0.473823] bus: 08 index 0 io port: [0xb000-0xbfff]
[    0.473825] bus: 08 index 1 mmio: [0xc0300000-0xc03fffff]
[    0.473826] bus: 08 index 2 mmio: [0x50000000-0x53ffffff]
[    0.473828] bus: 08 index 3 io port: [0x00-0xffff]
[    0.473830] bus: 08 index 4 mmio: [0x000000-0xffffffff]
[    0.473832] bus: 09 index 0 io port: [0xb400-0xb4ff]
[    0.473833] bus: 09 index 1 io port: [0xb800-0xb8ff]
[    0.473835] bus: 09 index 2 mmio: [0x50000000-0x53ffffff]
[    0.473837] bus: 09 index 3 mmio: [0x54000000-0x57ffffff]
[    0.473844] NET: Registered protocol family 2
[    0.473937] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.474248] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.475283] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.475833] TCP: Hash tables configured (established 131072 bind 65536)
[    0.475836] TCP reno registered
[    0.475950] NET: Registered protocol family 1
[    0.476096] checking if image is initramfs... it is
[    0.975982] Switched to high resolution mode on CPU 0
[    1.005303] Freeing initrd memory: 7360k freed
[    1.005398] cpufreq: No nForce2 chipset.
[    1.005530] audit: initializing netlink socket (disabled)
[    1.005552] type=2000 audit(1244645911.004:1): initialized
[    1.012712] highmem bounce pool size: 64 pages
[    1.012717] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.013755] VFS: Disk quotas dquot_6.5.1
[    1.013804] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.014323] fuse init (API version 7.10)
[    1.014391] msgmni has been set to 1727
[    1.014552] alg: No test for stdrng (krng)
[    1.014561] io scheduler noop registered
[    1.014563] io scheduler anticipatory registered
[    1.014564] io scheduler deadline registered
[    1.014578] io scheduler cfq registered (default)
[    1.014584] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    1.680037] pci 0000:01:05.0: Boot video device
[    1.680114] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.680137] pcieport-driver 0000:00:06.0: found MSI capability
[    1.680139] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.680154] pci_express 0000:00:06.0:pcie01: allocate port service
[    1.681177] aer 0000:00:06.0:pcie01: AER service couldn't init device: no _OSC support
[    1.681186] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.681194] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.681934] ACPI: AC Adapter [AC] (on-line)
[    1.722210] ACPI: Battery Slot [BAT0] (battery present)
[    1.722271] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.722274] ACPI: Power Button (FF) [PWRF]
[    1.722309] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.722311] ACPI: Power Button (CM) [PWRB]
[    1.722345] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.722354] ACPI: Sleep Button (CM) [SLPB]
[    1.722392] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.722866] ACPI: Lid Switch [LID]
[    1.723001] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.723020] processor ACPI_CPU:00: registered as cooling_device0
[    1.723023] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.725164] isapnp: Scanning for PnP cards...
[    2.079455] isapnp: No Plug & Play device found
[    2.080387] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.080644] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.080652] serial 0000:00:14.6: PCI INT B disabled
[    2.081196] brd: module loaded
[    2.081453] loop: module loaded
[    2.081512] Fixed MDIO Bus: probed
[    2.081517] PPP generic driver version 2.4.2
[    2.081569] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.081590] Driver 'sd' needs updating - please use bus_type methods
[    2.081597] Driver 'sr' needs updating - please use bus_type methods
[    2.081813] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.081858] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    2.081949] scsi0 : pata_atiixp
[    2.082040] scsi1 : pata_atiixp
[    2.083089] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    2.083092] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    2.244765] ata1.00: ATA-7: FUJITSU MHV2100AT PL, 000000A0, max UDMA/100
[    2.244767] ata1.00: 195371568 sectors, multi 16: LBA 
[    2.260682] ata1.00: configured for UDMA/100
[    2.424554] ata2.00: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CG03, max UDMA/33
[    2.440530] ata2.00: configured for UDMA/33
[    2.442932] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2100A 0000 PQ: 0 ANSI: 5
[    2.443004] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.443018] sd 0:0:0:0: [sda] Write Protect is off
[    2.443020] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.443039] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.443087] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.443098] sd 0:0:0:0: [sda] Write Protect is off
[    2.443100] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.443118] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.443121]  sda: sda1 sda2 < sda5 sda6 >
[    2.502522] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.502561] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.506517] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CG03 PQ: 0 ANSI: 5
[    2.518108] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.518113] Uniform CD-ROM driver Revision: 3.20
[    2.518182] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.518213] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.518560] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.518578] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.518604] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.518662] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.518725] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[    2.528007] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.528090] usb usb1: configuration #1 chosen from 1 choice
[    2.528113] hub 1-0:1.0: USB hub found
[    2.528123] hub 1-0:1.0: 8 ports detected
[    2.528238] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.528251] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.528263] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.528295] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.528311] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[    2.588040] usb usb2: configuration #1 chosen from 1 choice
[    2.588060] hub 2-0:1.0: USB hub found
[    2.588070] hub 2-0:1.0: 4 ports detected
[    2.588151] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.588161] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.588194] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.588208] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[    2.648041] usb usb3: configuration #1 chosen from 1 choice
[    2.648066] hub 3-0:1.0: USB hub found
[    2.648076] hub 3-0:1.0: 4 ports detected
[    2.648154] uhci_hcd: USB Universal Host Controller Interface driver
[    2.648197] usbcore: registered new interface driver libusual
[    2.648225] usbcore: registered new interface driver usbserial
[    2.648235] USB Serial support registered for generic
[    2.648245] usbcore: registered new interface driver usbserial_generic
[    2.648248] usbserial: USB Serial Driver core
[    2.648282] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.650336] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.650340] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.650430] mice: PS/2 mouse device common for all mice
[    2.650574] rtc_cmos 00:04: RTC can wake from S4
[    2.650607] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.650635] rtc0: alarms up to one month, 114 bytes nvram
[    2.650687] device-mapper: uevent: version 1.0.3
[    2.650779] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.650822] device-mapper: multipath: version 1.0.5 loaded
[    2.650824] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.650888] EISA: Probing bus 0 at eisa.0
[    2.650897] Cannot allocate resource for EISA slot 1
[    2.650926] Cannot allocate resource for EISA slot 8
[    2.650927] EISA: Detected 0 cards.
[    2.650975] cpuidle: using governor ladder
[    2.651010] cpuidle: using governor menu
[    2.651425] TCP cubic registered
[    2.651509] NET: Registered protocol family 10
[    2.651839] lo: Disabled Privacy Extensions
[    2.652108] NET: Registered protocol family 17
[    2.652123] Bluetooth: L2CAP ver 2.11
[    2.652124] Bluetooth: L2CAP socket layer initialized
[    2.652127] Bluetooth: SCO (Voice Link) ver 0.6
[    2.652128] Bluetooth: SCO socket layer initialized
[    2.652147] Bluetooth: RFCOMM socket layer initialized
[    2.652152] Bluetooth: RFCOMM TTY layer initialized
[    2.652154] Bluetooth: RFCOMM ver 1.10
[    2.652172] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[    2.652205] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[    2.652207] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[    2.652209] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[    2.652211] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0xe
[    2.652213] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[    2.652245] Using IPI No-Shortcut mode
[    2.652300] registered taskstats version 1
[    2.652387]   Magic number: 13:676:990
[    2.652475] rtc_cmos 00:04: setting system clock to 2009-06-10 14:58:32 UTC (1244645912)
[    2.652478] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.652480] EDD information not available.
[    2.652995] Freeing unused kernel memory: 532k freed
[    2.653104] Write protecting the kernel text: 4128k
[    2.653142] Write protecting the kernel read-only data: 1532k
[    2.689981] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.990436] sky2 driver version 1.22
[    2.990487] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.990498] sky2 0000:02:00.0: setting latency timer to 64
[    2.990551] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    3.054199] sky2 0000:02:00.0: Marvell Yukon 88E8036 Fast Ethernet Controller
[    3.054201]  Part Number: Yukon 88E8036
[    3.054203]  Engineering Level: Rev. 1.3
[    3.054204]  Manufacturer: Marvell
[    3.057462] sky2 eth0: addr 00:03:25:35:1f:32
[    3.084803] b43-pci-bridge 0000:08:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.152075] ssb: Sonics Silicon Backplane found on PCI device 0000:08:07.0
[    3.152311] ohci1394 0000:08:0e.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.205073] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[c0303000-c03037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.210488] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    3.362463] Marking TSC unstable due to TSC halts in idle
[    3.425786] usb 3-2: configuration #1 chosen from 1 choice
[    3.530084] PM: Starting manual resume from disk
[    3.530088] PM: Resume from partition 8:5
[    3.530090] PM: Checking hibernation image.
[    3.530306] PM: Resume from disk failed.
[    3.572938] kjournald starting.  Commit interval 5 seconds
[    3.572946] EXT3-fs: mounted filesystem with ordered data mode.
[    4.504141] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000325215001ddd1]
[    9.924023] udev: starting version 141
[   10.035916] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   10.036054] usbcore: registered new interface driver btusb
[   10.084445] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.431529] Linux agpgart interface v0.103
[   10.680739] yenta_cardbus 0000:08:05.0: CardBus bridge found [107b:0506]
[   10.680770] yenta_cardbus 0000:08:05.0: Using CSCINT to route CSC interrupts to PCI
[   10.680772] yenta_cardbus 0000:08:05.0: Routing CardBus interrupts to PCI
[   10.680779] yenta_cardbus 0000:08:05.0: TI: mfunc 0x01001002, devctl 0x44
[   10.700341] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   10.772648] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   10.826249] cfg80211: Calling CRDA to update world regulatory domain
[   10.888092] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.913144] yenta_cardbus 0000:08:05.0: ISA IRQ mask 0x0cf8, PCI irq 22
[   10.913148] yenta_cardbus 0000:08:05.0: Socket status: 30000006
[   10.913153] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge I/O window: 0xb000 - 0xbfff
[   10.913156] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xb000-0xbfff: clean.
[   10.913322] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge Memory window: 0xc0300000 - 0xc03fffff
[   10.913324] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   10.943602] cfg80211: World regulatory domain updated:
[   10.943606] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.943608] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.943611] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.943613] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.943615] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.943617] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.182834] b43-phy0: Broadcom 4318 WLAN found
[   11.248846] phy0: Selected rate control algorithm 'pid'
[   11.286412] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.288734] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   11.289701] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.290492] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.291315] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.306783] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.326400] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.421716] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   11.436072] MC'97 0 converters and GPIO not ready (0x1)
[   11.557632] lp: driver loaded but no devices found
[   11.629953] Adding 2626588k swap on /dev/sda5.  Priority:-1 extents:1 across:2626588k
[   11.775099] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   11.811290] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   12.159478] EXT3 FS on sda1, internal journal
[   13.135175] kjournald starting.  Commit interval 5 seconds
[   13.135576] EXT3 FS on sda6, internal journal
[   13.135581] EXT3-fs: mounted filesystem with ordered data mode.
[   13.431416] type=1505 audit(1244645923.275:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1984
[   13.477669] type=1505 audit(1244645923.323:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1988
[   13.477822] type=1505 audit(1244645923.323:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1988
[   13.477874] type=1505 audit(1244645923.323:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1988
[   13.477915] type=1505 audit(1244645923.323:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1988
[   13.620192] type=1505 audit(1244645923.467:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1993
[   13.620423] type=1505 audit(1244645923.467:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1993
[   13.646808] type=1505 audit(1244645923.491:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1997
[   16.292641] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.292644] Bluetooth: BNEP filters: protocol multicast
[   16.324790] Bridge firewalling registered
[   17.424912] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.694549] [drm] Initialized drm 1.1.0 20060810
[   17.740675] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   17.916039] ppdev: user-space parallel port driver
[   18.246964] [drm] Setting GART location based on new memory map
[   18.247591] [drm] Loading R300 Microcode
[   18.247612] [drm] Num pipes: 2
[   18.247618] [drm] writeback test succeeded in 1 usecs
[   22.154668] sky2 eth0: enabling interface
[   22.154887] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.202614] input: b43-phy0 as /devices/virtual/input/input8
[   22.284075] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   22.487459] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   22.528684] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   22.560318] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   22.688067] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.729494] Registered led device: b43-phy0::tx
[   22.729514] Registered led device: b43-phy0::rx
[   22.729532] Registered led device: b43-phy0::radio
[   22.752677] b43-phy0: Radio turned on by software
[   22.753084] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.856243] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   23.856453] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.280298] wlan0: direct probe to AP 00:13:46:a9:a1:1c try 1
[   24.480043] wlan0: direct probe to AP 00:13:46:a9:a1:1c try 2
[   24.680044] wlan0: direct probe to AP 00:13:46:a9:a1:1c try 3
[   24.880042] wlan0: direct probe to AP 00:13:46:a9:a1:1c timed out
[   34.016035] eth0: no IPv6 routers present
[   79.472046] Clocksource tsc unstable (delta = -123250306 ns)
[   82.136305] wlan0: authenticate with AP 00:1b:2f:fd:8f:0e
[   82.140817] wlan0: authenticated
[   82.140822] wlan0: associate with AP 00:1b:2f:fd:8f:0e
[   82.143125] wlan0: RX AssocResp from 00:1b:2f:fd:8f:0e (capab=0x431 status=0 aid=1)
[   82.143129] wlan0: associated
[   82.144709] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.403823] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   87.406868] input: HP Bluetooth Laser Mobile Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:11/input9
[   87.428213] generic-bluetooth 0005:0D62:0558.0001: input,hidraw0: BLUETOOTH HID v1.1a Mouse [HP Bluetooth Laser Mobile Mouse] on 00:02:72:12:39:BE
[   92.968014] wlan0: no IPv6 routers present
[  144.142227] wlan0 direct probe responded
[  144.142240] wlan0: authenticate with AP 00:1b:2f:fd:8f:0e
[  144.144731] wlan0: authenticated
[  144.144740] wlan0: associate with AP 00:1b:2f:fd:8f:0e
[  144.146888] wlan0: RX ReassocResp from 00:1b:2f:fd:8f:0e (capab=0x431 status=0 aid=1)
[  144.146894] wlan0: associated
[  148.149872] wlan0: deauthenticated
[  149.148057] wlan0: direct probe to AP 00:1b:2f:fd:8f:0e try 1
[  149.153096] wlan0 direct probe responded
[  149.153105] wlan0: authenticate with AP 00:1b:2f:fd:8f:0e
[  149.154801] wlan0: authenticated
[  149.154808] wlan0: associate with AP 00:1b:2f:fd:8f:0e
[  149.157303] wlan0: RX ReassocResp from 00:1b:2f:fd:8f:0e (capab=0x431 status=0 aid=1)
[  149.157308] wlan0: associated
```

---

### Post by reeseslover531 on 2009-06-10
hmm try and print out the last few lines of dmesg after you insert the dvd, hopefully it will show some sort of error.

---

### Post by bullfroghrr on 2009-06-10
this right after i put in a dvd  
```

  2.443087] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[    2.443098] sd 0:0:0:0: [sda] Write Protect is off
[    2.443100] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.443118] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.443121]  sda: sda1 sda2 < sda5 sda6 >
[    2.502522] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.502561] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.506517] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CG03 PQ: 0 ANSI: 5
[    2.518108] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.518113] Uniform CD-ROM driver Revision: 3.20
[    2.518182] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.518213] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.518560] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.518578] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.518604] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.518662] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.518725] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[    2.528007] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.528090] usb usb1: configuration #1 chosen from 1 choice
[    2.528113] hub 1-0:1.0: USB hub found
[    2.528123] hub 1-0:1.0: 8 ports detected
[    2.528238] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.528251] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.528263] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.528295] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.528311] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[    2.588040] usb usb2: configuration #1 chosen from 1 choice
[    2.588060] hub 2-0:1.0: USB hub found
[    2.588070] hub 2-0:1.0: 4 ports detected
[    2.588151] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.588161] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.588194] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.588208] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[    2.648041] usb usb3: configuration #1 chosen from 1 choice
[    2.648066] hub 3-0:1.0: USB hub found
[    2.648076] hub 3-0:1.0: 4 ports detected
[    2.648154] uhci_hcd: USB Universal Host Controller Interface driver
[    2.648197] usbcore: registered new interface driver libusual
[    2.648225] usbcore: registered new interface driver usbserial
[    2.648235] USB Serial support registered for generic
[    2.648245] usbcore: registered new interface driver usbserial_generic
[    2.648248] usbserial: USB Serial Driver core
[    2.648282] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.650336] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.650340] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.650430] mice: PS/2 mouse device common for all mice
[    2.650574] rtc_cmos 00:04: RTC can wake from S4
[    2.650607] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.650635] rtc0: alarms up to one month, 114 bytes nvram
[    2.650687] device-mapper: uevent: version 1.0.3
[    2.650779] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.650822] device-mapper: multipath: version 1.0.5 loaded
[    2.650824] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.650888] EISA: Probing bus 0 at eisa.0
[    2.650897] Cannot allocate resource for EISA slot 1
[    2.650926] Cannot allocate resource for EISA slot 8
[    2.650927] EISA: Detected 0 cards.
[    2.650975] cpuidle: using governor ladder
[    2.651010] cpuidle: using governor menu
[    2.651425] TCP cubic registered
[    2.651509] NET: Registered protocol family 10
[    2.651839] lo: Disabled Privacy Extensions
[    2.652108] NET: Registered protocol family 17
[    2.652123] Bluetooth: L2CAP ver 2.11
[    2.652124] Bluetooth: L2CAP socket layer initialized
[    2.652127] Bluetooth: SCO (Voice Link) ver 0.6
[    2.652128] Bluetooth: SCO socket layer initialized
[    2.652147] Bluetooth: RFCOMM socket layer initialized
[    2.652152] Bluetooth: RFCOMM TTY layer initialized
[    2.652154] Bluetooth: RFCOMM ver 1.10
[    2.652172] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[    2.652205] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[    2.652207] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[    2.652209] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[    2.652211] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0xe
[    2.652213] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[    2.652245] Using IPI No-Shortcut mode
[    2.652300] registered taskstats version 1
[    2.652387]   Magic number: 13:676:990
[    2.652475] rtc_cmos 00:04: setting system clock to 2009-06-10 14:58:32 UTC (1244645912)
[    2.652478] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.652480] EDD information not available.
[    2.652995] Freeing unused kernel memory: 532k freed
[    2.653104] Write protecting the kernel text: 4128k
[    2.653142] Write protecting the kernel read-only data: 1532k
[    2.689981] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.990436] sky2 driver version 1.22
[    2.990487] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.990498] sky2 0000:02:00.0: setting latency timer to 64
[    2.990551] sky2 0000:02:00.0: Yukon-2 FE chip revision 1
[    3.054199] sky2 0000:02:00.0: Marvell Yukon 88E8036 Fast Ethernet Controller
[    3.054201]  Part Number: Yukon 88E8036
[    3.054203]  Engineering Level: Rev. 1.3
[    3.054204]  Manufacturer: Marvell
[    3.057462] sky2 eth0: addr 00:03:25:35:1f:32
[    3.084803] b43-pci-bridge 0000:08:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.152075] ssb: Sonics Silicon Backplane found on PCI device 0000:08:07.0
[    3.152311] ohci1394 0000:08:0e.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.205073] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[c0303000-c03037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.210488] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    3.362463] Marking TSC unstable due to TSC halts in idle
[    3.425786] usb 3-2: configuration #1 chosen from 1 choice
[    3.530084] PM: Starting manual resume from disk
[    3.530088] PM: Resume from partition 8:5
[    3.530090] PM: Checking hibernation image.
[    3.530306] PM: Resume from disk failed.
[    3.572938] kjournald starting.  Commit interval 5 seconds
[    3.572946] EXT3-fs: mounted filesystem with ordered data mode.
[    4.504141] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000325215001ddd1]
[    9.924023] udev: starting version 141
[   10.035916] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   10.036054] usbcore: registered new interface driver btusb
[   10.084445] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.431529] Linux agpgart interface v0.103
[   10.680739] yenta_cardbus 0000:08:05.0: CardBus bridge found [107b:0506]
[   10.680770] yenta_cardbus 0000:08:05.0: Using CSCINT to route CSC interrupts to PCI
[   10.680772] yenta_cardbus 0000:08:05.0: Routing CardBus interrupts to PCI
[   10.680779] yenta_cardbus 0000:08:05.0: TI: mfunc 0x01001002, devctl 0x44
[   10.700341] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   10.772648] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[   10.826249] cfg80211: Calling CRDA to update world regulatory domain
[   10.888092] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.913144] yenta_cardbus 0000:08:05.0: ISA IRQ mask 0x0cf8, PCI irq 22
[   10.913148] yenta_cardbus 0000:08:05.0: Socket status: 30000006
[   10.913153] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge I/O window: 0xb000 - 0xbfff
[   10.913156] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xb000-0xbfff: clean.
[   10.913322] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge Memory window: 0xc0300000 - 0xc03fffff
[   10.913324] yenta_cardbus 0000:08:05.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   10.943602] cfg80211: World regulatory domain updated:
[   10.943606] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.943608] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.943611] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.943613] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.943615] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.943617] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.182834] b43-phy0: Broadcom 4318 WLAN found
[   11.248846] phy0: Selected rate control algorithm 'pid'
[   11.286412] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.288734] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   11.289701] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.290492] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.291315] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.306783] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.326400] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.421716] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   11.436072] MC'97 0 converters and GPIO not ready (0x1)
[   11.557632] lp: driver loaded but no devices found
[   11.629953] Adding 2626588k swap on /dev/sda5.  Priority:-1 extents:1 across:2626588k
[   11.775099] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   11.811290] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   12.159478] EXT3 FS on sda1, internal journal
[   13.135175] kjournald starting.  Commit interval 5 seconds
[   13.135576] EXT3 FS on sda6, internal journal
[   13.135581] EXT3-fs: mounted filesystem with ordered data mode.
[   13.431416] type=1505 audit(1244645923.275:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1984
[   13.477669] type=1505 audit(1244645923.323:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1988
[   13.477822] type=1505 audit(1244645923.323:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1988
[   13.477874] type=1505 audit(1244645923.323:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1988
[   13.477915] type=1505 audit(1244645923.323:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1988
[   13.620192] type=1505 audit(1244645923.467:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1993
[   13.620423] type=1505 audit(1244645923.467:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1993
[   13.646808] type=1505 audit(1244645923.491:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1997
[   16.292641] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.292644] Bluetooth: BNEP filters: protocol multicast
[   16.324790] Bridge firewalling registered
[   17.424912] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.694549] [drm] Initialized drm 1.1.0 20060810
[   17.740675] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   17.916039] ppdev: user-space parallel port driver
[   18.246964] [drm] Setting GART location based on new memory map
[   18.247591] [drm] Loading R300 Microcode
[   18.247612] [drm] Num pipes: 2
[   18.247618] [drm] writeback test succeeded in 1 usecs
[   22.154668] sky2 eth0: enabling interface
[   22.154887] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.202614] input: b43-phy0 as /devices/virtual/input/input8
[   22.284075] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   22.487459] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   22.528684] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   22.560318] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   22.688067] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.729494] Registered led device: b43-phy0::tx
[   22.729514] Registered led device: b43-phy0::rx
[   22.729532] Registered led device: b43-phy0::radio
[   22.752677] b43-phy0: Radio turned on by software
[   22.753084] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.856243] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   23.856453] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.280298] wlan0: direct probe to AP 00:13:46:a9:a1:1c try 1
[   24.480043] wlan0: direct probe to AP 00:13:46:a9:a1:1c try 2
[   24.680044] wlan0: direct probe to AP 00:13:46:a9:a1:1c try 3
[   24.880042] wlan0: direct probe to AP 00:13:46:a9:a1:1c timed out
[   34.016035] eth0: no IPv6 routers present
[   79.472046] Clocksource tsc unstable (delta = -123250306 ns)
[   82.136305] wlan0: authenticate with AP 00:1b:2f:fd:8f:0e
[   82.140817] wlan0: authenticated
[   82.140822] wlan0: associate with AP 00:1b:2f:fd:8f:0e
[   82.143125] wlan0: RX AssocResp from 00:1b:2f:fd:8f:0e (capab=0x431 status=0 aid=1)
[   82.143129] wlan0: associated
[   82.144709] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.403823] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   87.406868] input: HP Bluetooth Laser Mobile Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:11/input9
[   87.428213] generic-bluetooth 0005:0D62:0558.0001: input,hidraw0: BLUETOOTH HID v1.1a Mouse [HP Bluetooth Laser Mobile Mouse] on 00:02:72:12:39:BE
[   92.968014] wlan0: no IPv6 routers present
[  144.142227] wlan0 direct probe responded
[  144.142240] wlan0: authenticate with AP 00:1b:2f:fd:8f:0e
[  144.144731] wlan0: authenticated
[  144.144740] wlan0: associate with AP 00:1b:2f:fd:8f:0e
[  144.146888] wlan0: RX ReassocResp from 00:1b:2f:fd:8f:0e (capab=0x431 status=0 aid=1)
[  144.146894] wlan0: associated
[  148.149872] wlan0: deauthenticated
[  149.148057] wlan0: direct probe to AP 00:1b:2f:fd:8f:0e try 1
[  149.153096] wlan0 direct probe responded
[  149.153105] wlan0: authenticate with AP 00:1b:2f:fd:8f:0e
[  149.154801] wlan0: authenticated
[  149.154808] wlan0: associate with AP 00:1b:2f:fd:8f:0e
[  149.157303] wlan0: RX ReassocResp from 00:1b:2f:fd:8f:0e (capab=0x431 status=0 aid=1)
[  149.157308] wlan0: associated
[ 4508.756902] sky2 eth0: Link is down.
[ 5434.574754] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[ 5439.720685] input: HP Bluetooth Laser Mobile Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:11/input10
[ 5439.730024] generic-bluetooth 0005:0D62:0558.0002: input,hidraw1: BLUETOOTH HID v1.1a Mouse [HP Bluetooth Laser Mobile Mouse] on 00:02:72:12:39:BE
[ 6072.556152] input: HP Bluetooth Laser Mobile Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:11/input11
[ 6072.580190] generic-bluetooth 0005:0D62:0558.0003: input,hidraw2: BLUETOOTH HID v1.1a Mouse [HP Bluetooth Laser Mobile Mouse] on 00:02:72:12:39:BE
[11800.515603] input: HP Bluetooth Laser Mobile Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:11/input12
[11800.540234] generic-bluetooth 0005:0D62:0558.0004: input,hidraw3: BLUETOOTH HID v1.1a Mouse [HP Bluetooth Laser Mobile Mouse] on 00:02:72:12:39:BE
[13779.230747] input: HP Bluetooth Laser Mobile Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:11/input13
[13779.256202] generic-bluetooth 0005:0D62:0558.0005: input,hidraw4: BLUETOOTH HID v1.1a Mouse [HP Bluetooth Laser Mobile Mouse] on 00:02:72:12:39:BE
[15210.373062] input: HP Bluetooth Laser Mobile Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/bluetooth/hci0/hci0:11/input14
[15210.396194] generic-bluetooth 0005:0D62:0558.0006: input,hidraw5: BLUETOOTH HID v1.1a Mouse [HP Bluetooth Laser Mobile Mouse] on 00:02:72:12:39:BE
```

---

### Post by reeseslover531 on 2009-06-10
haha wow that gives me no information, I was expecting there to be some sort of error. hmmmmm so you can't mount it at all right?

---

### Post by damis648 on 2009-06-10
Try mounting it manually:
```
sudo mkdir /media/dvd
sudo mount -t udf /dev/cdrom /media/dvd
```
If it goes an error when mounting, try this instead:
```
sudo mount -t udf -o force /dev/cdrom /media/dvd
```
and then before ejecting it, unmount via
```
sudo umount /media/dvd
sudo rmdir /media/dvd
```

---

### Post by bullfroghrr on 2009-06-10
this is what i get, if it's a commercial movie dvd it doesn't mount
> jeremy@Athlon:~$ sudo mkdir /media/dvd
[sudo] password for jeremy: 
jeremy@Athlon:~$ sudo mount -t udf /dev/cdrom /media/dvd
mount: no medium found on /dev/sr0
jeremy@Athlon:~$ sudo mount -t udf -o force /dev/cdrom /media/dvd
mount: no medium found on /dev/sr0
jeremy@Athlon:~$ sudo mkdir /media/dvd
mkdir: cannot create directory `/media/dvd': File exists
jeremy@Athlon:~$ sudo mount -t udf /dev/cdrom /media/dvd
mount: no medium found on /dev/sr0
jeremy@Athlon:~$ sudo mount -t udf -o force /dev/cdrom /media/dvd
mount: no medium found on /dev/sr0
jeremy@Athlon:~$

---

### Post by damis648 on 2009-06-10
Unfortunately, this looks like it is reporting that there is actually no media in the drive...

All I can think of is perhaps that the DVD Drive's region code setting is set to something other than the DVDs you are trying to play. Do you happen to have Windows installed on this machine?

---

### Post by bullfroghrr on 2009-06-10
I don't have Windows on this machine any more however when i was using 8.10 it had no problems reading dvd's
CORRECTION:
it does read some dvds, i found one that did work and checked the region code, it is correct.

---

### Post by reeseslover531 on 2009-06-11
hmmmm have you tried doing in with a liveCD? maybe your install has gotten messed up in some way.

---

### Post by pauna on 2009-06-11
> **bullfroghrr said:**
> I don't have Windows on this machine any more however when i was using 8.10 it had no problems reading dvd's
CORRECTION:
it does read some dvds, i found one that did work and checked the region code, it is correct.

That is interesting. I'm having similar random DVD issues with my 8.04 based Mythbuntu box as shown in this [message]("http://ubuntuforums.org/showthread.php?t=1148774"). The problem still persists and has gotten progressively worse.

---

### Post by lukeiamyourfather on 2009-06-11
If its getting progressively worse and happens randomly then it sounds like the disc drive is faulty or on its way out the door. Try another drive if you can. Cheers!

---

### Post by pauna on 2009-06-15
> **lukeiamyourfather said:**
> If its getting progressively worse and happens randomly then it sounds like the disc drive is faulty or on its way out the door. Try another drive if you can. Cheers!

Well, that's basically the first thing I did. It didn't help... :(

---

### Post by uaneme on 2009-11-26
I 'm having a similair issue with Koala.

First i installed UDF that fixed it for a few disks,

Then i discovered CDDE that took it to a next stage (i can now see the disk getting mounted instead of being hidden) But it is still not playing the DVD due to DRM clippled crap.

Does anyone know what i need next to be able to play those DVD's?  

some codec probably.... I will go grab whatever codec i find ...

i hope this is usefull to the next person who runs into this issue.


:popcorn:

---

### Post by ItalOz on 2009-11-26
I think that all the problems we are reading about commercial DVDs are related to the region issue, try to launch vlc from terminal ```
vlc &
```
and then open the DVD and see if you get something similar to what I get [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1338259")

Till I fixed the scrambling issue in my 8.04 installation I was having all sort of problems when inserting DVDs in the reader, sometimes it did not mount just like yours.

what you guys think?

---

