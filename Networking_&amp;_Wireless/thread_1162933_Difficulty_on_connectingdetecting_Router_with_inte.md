---
title: "Difficulty on connecting/detecting Router with intel3945 on Jaunty ubuntu 9.04"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by crazybuntu on 2009-05-18
Hi, i am a totally newbie on Linux, so this is my first time installing. I have difficulty on connecting to the router which uses WEP. 

It seems the laptop im using which detects the router instantly on Windows 7 / XP does not detect the router under Ubuntu jaunty. 

Things i did to fix this, but none of them solved my problem :

[LIST]
[*]I replaced network manager with WCID which connects much faster, but still it only detects the router from a close distance.
[*]I installed backports generic jaunty
[*]did rmmod iwl3945 then modprobe iwl3945
[*]Installed wifi-radar and it detected the router from a far distance  but cant connect. It will only connect with WICD.
[/LIST]

Here is my IWCONFIG :
[php]wlan0     IEEE 802.11abg  ESSID:"PROLINK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:1E:EA:06   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/php]I alsos did a dmesg , when its trying to detect wireless networks and it showed up :
```
[    0.972121] NetLabel:  unlabeled traffic allowed by default
[    0.972151] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.972163] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.976137] AppArmor: AppArmor Filesystem Enabled
[    0.980025] Switched to high resolution mode on CPU 0
[    0.981028] Switched to high resolution mode on CPU 1
[    0.984027] pnp: PnP ACPI init
[    0.984048] ACPI: bus type pnp registered
[    0.988791] pnp: PnP ACPI: found 11 devices
[    0.988797] ACPI: ACPI bus type pnp unregistered
[    0.988807] PnPBIOS: Disabled by ACPI PNP
[    0.988828] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.988836] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.988843] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.988850] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.988857] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.988865] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.988872] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.988879] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.988898] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.988905] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.988912] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.988919] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.988926] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.988940] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.988946] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    1.023935] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.023943] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    1.023955] pci 0000:00:1c.0:   MEM window: 0xd4000000-0xd5ffffff
[    1.023965] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000d1ffffff
[    1.023979] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    1.023987] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    1.023998] pci 0000:00:1c.1:   MEM window: 0xd6000000-0xd7ffffff
[    1.024016] pci 0000:00:1c.1:   PREFETCH window: 0x000000d2000000-0x000000d3ffffff
[    1.024042] pci 0000:05:07.0: CardBus bridge, secondary bus 0000:06
[    1.024048] pci 0000:05:07.0:   IO window: 0x004400-0x0044ff
[    1.024058] pci 0000:05:07.0:   IO window: 0x004800-0x0048ff
[    1.024068] pci 0000:05:07.0:   PREFETCH window: 0x50000000-0x53ffffff
[    1.024077] pci 0000:05:07.0:   MEM window: 0x58000000-0x5bffffff
[    1.024087] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.024095] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
[    1.024106] pci 0000:00:1e.0:   MEM window: 0xd8000000-0xd80fffff
[    1.024116] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000055ffffff
[    1.024146] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.024156] pci 0000:00:1c.0: setting latency timer to 64
[    1.024174] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.024184] pci 0000:00:1c.1: setting latency timer to 64
[    1.024195] pci 0000:00:1e.0: enabling device (0104 -> 0107)
[    1.024206] pci 0000:00:1e.0: setting latency timer to 64
[    1.024224] pci 0000:05:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.024234] pci 0000:05:07.0: setting latency timer to 64
[    1.024244] bus: 00 index 0 io port: [0x00-0xffff]
[    1.024250] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.024256] bus: 02 index 0 io port: [0x2000-0x2fff]
[    1.024262] bus: 02 index 1 mmio: [0xd4000000-0xd5ffffff]
[    1.024267] bus: 02 index 2 mmio: [0xd0000000-0xd1ffffff]
[    1.024273] bus: 02 index 3 mmio: [0x0-0x0]
[    1.024278] bus: 03 index 0 io port: [0x3000-0x3fff]
[    1.024284] bus: 03 index 1 mmio: [0xd6000000-0xd7ffffff]
[    1.024290] bus: 03 index 2 mmio: [0xd2000000-0xd3ffffff]
[    1.024295] bus: 03 index 3 mmio: [0x0-0x0]
[    1.024300] bus: 05 index 0 io port: [0x4000-0x4fff]
[    1.024306] bus: 05 index 1 mmio: [0xd8000000-0xd80fffff]
[    1.024312] bus: 05 index 2 mmio: [0x50000000-0x55ffffff]
[    1.024317] bus: 05 index 3 io port: [0x00-0xffff]
[    1.024322] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    1.024328] bus: 06 index 0 io port: [0x4400-0x44ff]
[    1.024333] bus: 06 index 1 io port: [0x4800-0x48ff]
[    1.024339] bus: 06 index 2 mmio: [0x50000000-0x53ffffff]
[    1.024345] bus: 06 index 3 mmio: [0x58000000-0x5bffffff]
[    1.024364] NET: Registered protocol family 2
[    1.036123] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.036677] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.038262] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.039050] TCP: Hash tables configured (established 131072 bind 65536)
[    1.039056] TCP reno registered
[    1.044152] NET: Registered protocol family 1
[    1.044433] checking if image is initramfs... it is
[    2.585271] Freeing initrd memory: 7376k freed
[    2.585347] Simple Boot Flag at 0x36 set to 0x1
[    2.585739] cpufreq: No nForce2 chipset.
[    2.586047] audit: initializing netlink socket (disabled)
[    2.586092] type=2000 audit(1242700329.585:1): initialized
[    2.604311] highmem bounce pool size: 64 pages
[    2.604323] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.607762] VFS: Disk quotas dquot_6.5.1
[    2.607907] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.609455] fuse init (API version 7.10)
[    2.609673] msgmni has been set to 1724
[    2.610078] alg: No test for stdrng (krng)
[    2.610107] io scheduler noop registered
[    2.610113] io scheduler anticipatory registered
[    2.610118] io scheduler deadline registered
[    2.610152] io scheduler cfq registered (default)
[    2.610176] pci 0000:00:02.0: Boot video device
[    2.614459] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.614532] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.614587] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    2.614613] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.614648] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.614679] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.614796] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    2.614866] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.614915] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    2.614940] pci_express 0000:00:1c.1:pcie00: allocate port service
[    2.614971] pci_express 0000:00:1c.1:pcie02: allocate port service
[    2.615001] pci_express 0000:00:1c.1:pcie03: allocate port service
[    2.615145] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.615301] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.824520] ACPI: AC Adapter [AC] (off-line)
[    2.833421] ACPI: Battery Slot [BAT0] (battery present)
[    2.833604] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.833611] ACPI: Power Button (FF) [PWRF]
[    2.833719] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.833726] ACPI: Power Button (CM) [PWB]
[    2.833832] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.833847] ACPI: Sleep Button (CM) [SLPB]
[    2.833952] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    2.834745] ACPI: Lid Switch [LID]
[    2.836183] ACPI: SSDT 3F68F751, 0213 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    2.837011] ACPI: SSDT 3F68F56E, 015E (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    2.840982] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.841041] processor ACPI_CPU:00: registered as cooling_device0
[    2.841050] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.841816] ACPI: SSDT 3F68F964, 007D (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    2.842602] ACPI: SSDT 3F68F6CC, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    2.843641] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.843689] processor ACPI_CPU:01: registered as cooling_device1
[    2.843699] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.851225] thermal LNXTHERM:01: registered as thermal_zone0
[    2.857098] ACPI: Thermal Zone [THRM] (43 C)
[    2.857236] isapnp: Scanning for PnP cards...
[    3.211691] isapnp: No Plug & Play device found
[    3.228552] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.230971] brd: module loaded
[    3.231772] loop: module loaded
[    3.231924] Fixed MDIO Bus: probed
[    3.231937] PPP generic driver version 2.4.2
[    3.232098] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    3.232165] Driver 'sd' needs updating - please use bus_type methods
[    3.232187] Driver 'sr' needs updating - please use bus_type methods
[    3.232361] ata_piix 0000:00:1f.1: version 2.12
[    3.232385] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.232454] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.232602] scsi0 : ata_piix
[    3.232799] scsi1 : ata_piix
[    3.234063] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.234071] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.420549] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, TI01, max UDMA/33
[    3.452532] ata1.00: configured for UDMA/33
[    3.460456] ata2: port disabled. ignoring.
[    3.476699] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D TI01 PQ: 0 ANSI: 5
[    3.540228] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.540236] Uniform CD-ROM driver Revision: 3.20
[    3.540449] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.540555] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    3.540595] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.540604] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
[    3.696046] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.696159] scsi2 : ata_piix
[    3.696301] scsi3 : ata_piix
[    3.698465] ata3: SATA max UDMA/133 cmd 0x18d0 ctl 0x18c4 bmdma 0x18b0 irq 19
[    3.698472] ata4: SATA max UDMA/133 cmd 0x18c8 ctl 0x18c0 bmdma 0x18b8 irq 19
[    3.860769] ata3.00: ATA-7: ST980811AS, 3.ALA, max UDMA/133
[    3.860776] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.877459] ata3.00: configured for UDMA/133
[    4.043725] scsi 2:0:0:0: Direct-Access     ATA      ST980811AS       3.AL PQ: 0 ANSI: 5
[    4.043944] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    4.043985] sd 2:0:0:0: [sda] Write Protect is off
[    4.043991] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.044076] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.044216] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    4.044255] sd 2:0:0:0: [sda] Write Protect is off
[    4.044261] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.044325] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.044334]  sda: sda1 sda2 < sda5 sda6 > sda3 sda4
[    4.193990] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.194088] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    4.195679] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.195720] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.195760] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.195767] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.195912] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.199856] ehci_hcd 0000:00:1d.7: debug port 1
[    4.199869] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.199896] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd8444000
[    4.212021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.212175] usb usb1: configuration #1 chosen from 1 choice
[    4.212242] hub 1-0:1.0: USB hub found
[    4.212259] hub 1-0:1.0: 8 ports detected
[    4.212514] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.212562] uhci_hcd: USB Universal Host Controller Interface driver
[    4.212615] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.212628] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.212635] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.212734] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.212773] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    4.212946] usb usb2: configuration #1 chosen from 1 choice
[    4.213009] hub 2-0:1.0: USB hub found
[    4.213027] hub 2-0:1.0: 2 ports detected
[    4.213223] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.213235] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.213243] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.213341] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.213378] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    4.213554] usb usb3: configuration #1 chosen from 1 choice
[    4.213616] hub 3-0:1.0: USB hub found
[    4.213630] hub 3-0:1.0: 2 ports detected
[    4.213822] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.213835] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.213843] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.213941] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.213991] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    4.214166] usb usb4: configuration #1 chosen from 1 choice
[    4.214230] hub 4-0:1.0: USB hub found
[    4.214247] hub 4-0:1.0: 2 ports detected
[    4.214452] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    4.214465] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.214472] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.214573] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.214622] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    4.214795] usb usb5: configuration #1 chosen from 1 choice
[    4.214856] hub 5-0:1.0: USB hub found
[    4.214870] hub 5-0:1.0: 2 ports detected
[    4.215167] usbcore: registered new interface driver libusual
[    4.215239] usbcore: registered new interface driver usbserial
[    4.215263] USB Serial support registered for generic
[    4.215299] usbcore: registered new interface driver usbserial_generic
[    4.215304] usbserial: USB Serial Driver core
[    4.215433] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.217473] i8042.c: Detected active multiplexing controller, rev 1.1.
[    4.218724] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.218738] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.218745] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.218751] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.218758] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.220092] mice: PS/2 mouse device common for all mice
[    4.240218] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    4.240262] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    4.240403] device-mapper: uevent: version 1.0.3
[    4.240623] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.240818] device-mapper: multipath: version 1.0.5 loaded
[    4.240825] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.241008] EISA: Probing bus 0 at eisa.0
[    4.241020] Cannot allocate resource for EISA slot 1
[    4.241026] Cannot allocate resource for EISA slot 2
[    4.241032] Cannot allocate resource for EISA slot 3
[    4.241038] Cannot allocate resource for EISA slot 4
[    4.241069] EISA: Detected 0 cards.
[    4.241353] cpuidle: using governor ladder
[    4.241641] cpuidle: using governor menu
[    4.242888] TCP cubic registered
[    4.243153] NET: Registered protocol family 10
[    4.244162] lo: Disabled Privacy Extensions
[    4.244969] NET: Registered protocol family 17
[    4.245011] Marking TSC unstable due to TSC halts in idle
[    4.245020] Bluetooth: L2CAP ver 2.11
[    4.245026] Bluetooth: L2CAP socket layer initialized
[    4.245036] Bluetooth: SCO (Voice Link) ver 0.6
[    4.245040] Bluetooth: SCO socket layer initialized
[    4.245146] Bluetooth: RFCOMM socket layer initialized
[    4.245158] Bluetooth: RFCOMM TTY layer initialized
[    4.245163] Bluetooth: RFCOMM ver 1.10
[    4.246289] Using IPI No-Shortcut mode
[    4.246396] registered taskstats version 1
[    4.246533]   Magic number: 9:108:511
[    4.246639] rtc_cmos 00:08: setting system clock to 2009-05-19 02:32:11 UTC (1242700331)
[    4.246643] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.246645] EDD information not available.
[    4.246986] Freeing unused kernel memory: 532k freed
[    4.247170] Write protecting the kernel text: 4128k
[    4.247239] Write protecting the kernel read-only data: 1532k
[    4.273323] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.541604] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.541680] r8169 0000:05:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.541884] r8169 0000:05:0b.0: no PCI Express capability
[    4.542642] eth0: RTL8169sb/8110sb at 0xf7cd2c00, 00:90:f5:55:3d:29, XID 10000000 IRQ 17
[    4.553063] ohci1394 0000:05:07.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.602863] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d8005000-d80057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.514974] PM: Starting manual resume from disk
[    5.514978] PM: Resume from partition 8:4
[    5.514980] PM: Checking hibernation image.
[    5.515164] PM: Resume from disk failed.
[    5.537598] EXT4-fs: barriers enabled
[    5.551140] kjournald2 starting.  Commit interval 5 seconds
[    5.551169] EXT4-fs: delayed allocation enabled
[    5.551172] EXT4-fs: file extents enabled
[    5.552256] EXT4-fs: mballoc enabled
[    5.552261] EXT4-fs: mounted filesystem with ordered data mode.
[   10.567711] udev: starting version 141
[   10.949897] cfg80211: Using static regulatory domain info
[   10.949902] cfg80211: Regulatory domain: US
[   10.949904]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.949907]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[   10.949910]     (5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.949937]     (5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.949940]     (5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.949943]     (5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[   10.949946]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[   10.951307] cfg80211: Calling CRDA for country: US
[   11.033692] cfg80211: Regulatory domain changed to country: US
[   11.033697]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.033700]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   11.033703]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   11.033706]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.033709]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.033712]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   11.176248] intel_rng: FWH not detected
[   11.461890] Linux agpgart interface v0.103
[   11.584963] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[   11.585619] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   11.588939] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   11.613999] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   11.683496] sdhci: Secure Digital Host Controller Interface driver
[   11.683500] sdhci: Copyright(c) Pierre Ossman
[   11.693831] sdhci-pci 0000:05:07.3: SDHCI controller found [104c:803c] (rev 0)
[   11.693852] sdhci-pci 0000:05:07.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.693977] mmc0: SDHCI controller on PCI [0000:05:07.3] using DMA
[   11.779518] yenta_cardbus 0000:05:07.0: CardBus bridge found [1558:5405]
[   11.779541] yenta_cardbus 0000:05:07.0: Enabling burst memory read transactions
[   11.779548] yenta_cardbus 0000:05:07.0: Using CSCINT to route CSC interrupts to PCI
[   11.779551] yenta_cardbus 0000:05:07.0: Routing CardBus interrupts to PCI
[   11.779558] yenta_cardbus 0000:05:07.0: TI: mfunc 0x00081b22, devctl 0x64
[   11.817425] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   11.817429] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   11.817689] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.817705] iwl3945 0000:02:00.0: setting latency timer to 64
[   11.847721] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input7
[   11.871597] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   11.871602] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.871734] iwl3945 0000:02:00.0: irq 2301 for MSI/MSI-X
[   11.872471] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   11.873827] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.906196] iTCO_vendor_support: vendor-support=0
[   11.908087] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.908255] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
[   11.908345] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.934673] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.991745] ACPI Exception (thermal-0538): AE_ERROR, ACPI thermal trip point state changed
[   11.991750] Please send acpidump to linux-acpi@vger.kernel.org
[   11.991752]  [20080926]
[   11.993799] APIC error on CPU1: 00(40)
[   12.013591] yenta_cardbus 0000:05:07.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   12.013596] yenta_cardbus 0000:05:07.0: Socket status: 30000006
[   12.013601] pci_bus 0000:05: Raising subordinate bus# of parent bus (#05) from #05 to #09
[   12.013610] yenta_cardbus 0000:05:07.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   12.013614] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: clean.
[   12.013897] yenta_cardbus 0000:05:07.0: pcmcia: parent PCI bridge Memory window: 0xd8000000 - 0xd80fffff
[   12.013901] yenta_cardbus 0000:05:07.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x55ffffff
[   12.015780] tifm_7xx1 0000:05:07.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.142522] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.142599] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.173783] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[   12.318844] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.321002] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   12.321908] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.322619] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.323612] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.389046] psmouse serio4: ID: 10 00 64<6>lp: driver loaded but no devices found
[   12.472292] elantech.c: assuming hardware version 1, firmware version 2.0
[   12.501024] Clocksource tsc unstable (delta = -154353404 ns)
[   12.502229] elantech.c: Synaptics capabilities query result 0x00, 0x02, 0x64.
[   12.542447] Adding 2056312k swap on /dev/sda4.  Priority:-1 extents:1 across:2056312k
[   12.560934] EXT4 FS on sda3, internal journal on sda3:8
[   12.669874] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input8
[   13.228398] type=1505 audit(1242675140.481:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1991
[   13.284458] type=1505 audit(1242675140.537:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1995
[   13.284589] type=1505 audit(1242675140.537:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1995
[   13.284644] type=1505 audit(1242675140.537:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1995
[   13.284693] type=1505 audit(1242675140.537:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1995
[   13.446605] type=1505 audit(1242675140.697:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2000
[   13.446831] type=1505 audit(1242675140.697:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2000
[   13.478891] type=1505 audit(1242675140.729:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2004
[   13.968056] iwl3945 0000:02:00.0: Radio Frequency Kill Switch is On:
[   13.968059] Kill switch must be turned off for wireless networking to work.
[   16.667674] iwl3945 0000:02:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   16.732734] iwl3945 0000:02:00.0: loaded firmware version 15.28.2.8
[   16.732940] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   16.756872] r8169: eth0: link down
[   16.757129] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.129768] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.129772] Bluetooth: BNEP filters: protocol multicast
[   17.171929] Bridge firewalling registered
[   18.178317] ppdev: user-space parallel port driver
[   19.072302] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   19.673588] [drm] Initialized drm 1.1.0 20060810
[   19.680590] pci 0000:00:02.0: power state changed by ACPI to D0
[   19.680600] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.680605] pci 0000:00:02.0: setting latency timer to 64
[   19.680802] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   19.900922] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio4/input/input9
[   23.087894] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   26.969911] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   30.969021] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   92.470838] Registered led device: iwl-phy0::radio
[   92.471303] Registered led device: iwl-phy0::assoc
[   92.473465] Registered led device: iwl-phy0::RX
[   92.473519] Registered led device: iwl-phy0::TX
[   92.478120] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  505.054726] iwl3945 0000:02:00.0: PCI INT A disabled
[  508.799861] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[  508.799870] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[  508.800004] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  508.800031] iwl3945 0000:02:00.0: setting latency timer to 64
[  508.841001] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[  508.841015] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  508.841173] iwl3945 0000:02:00.0: irq 2301 for MSI/MSI-X
[  508.843180] phy1: Selected rate control algorithm 'iwl-3945-rs'
[  566.023718] iwl3945 0000:02:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[  566.029177] iwl3945 0000:02:00.0: loaded firmware version 15.28.2.8
[  566.075855] Registered led device: iwl-phy1::radio
[  566.075876] Registered led device: iwl-phy1::assoc
[  566.075936] Registered led device: iwl-phy1::RX
[  566.075955] Registered led device: iwl-phy1::TX
[  566.089418] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  651.766247] Registered led device: iwl-phy1::radio
[  651.766336] Registered led device: iwl-phy1::assoc
[  651.766375] Registered led device: iwl-phy1::RX
[  651.766413] Registered led device: iwl-phy1::TX
[  651.774503] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  652.040954] wlan0: authenticate with AP da5286b8
[  652.040986] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  652.045963] wlan0: authenticate with AP da5286b8
[  652.045996] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[  652.046007] wlan0: authenticated
[  652.046012] wlan0: associate with AP da5286b8
[  652.046018] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[  652.118942] wlan0: authenticate with AP da5286b8
[  652.121826] wlan0: authenticate with AP da5286b8
[  652.121847] wlan0: authenticated
[  652.121852] wlan0: associate with AP da5286b8
[  652.127308] wlan0: RX AssocResp from da53e026 (capab=0x431 status=0 aid=2)
[  652.127316] wlan0: associated
[  652.130512] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  662.864117] wlan0: no IPv6 routers present
```Timed out 
and wlan0 link not ready ??

but when i get closer to the router, it detects and connects normally.

Anybody , i have been trying to search for the fix in this forum but  its all  a dead end, with no success. :sad:

this is what happens to Link quality from 20/70 searching, i got closer to router , connected and go to first palce, its 50/70 when connected

---

### Post by crazybuntu on 2009-05-18
and its not the killswitch thing.. i can connect but to start the detection of the network i have to move closer to th AP /router . then i can go farther where i cant connect initially

---

### Post by chili555 on 2009-05-18
Is your router set to B only, G only or Auto? Does the behavior change if you do:```
sudo iwconfig wlan0 rate 54M auto
```

---

### Post by crazybuntu on 2009-05-18
> **chili555 said:**
> Is your router set to B only, G only or Auto? Does the behavior change if you do:```
sudo iwconfig wlan0 rate 54M auto
```

The router is set to B , and your suggestion didnt change anything.

This is what i get when i go from the room without signal to closer to the router and connects.
```
[   20.719093] r8169: eth0: link down
[   20.719350] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.720146] iwl3945 0000:02:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   20.855987] iwl3945 0000:02:00.0: loaded firmware version 15.28.2.8
[   20.856162] iwl3945 0000:02:00.0: Radio disabled by HW RF Kill switch
[   64.766412] Registered led device: iwl-phy0::radio
[   64.766433] Registered led device: iwl-phy0::assoc
[   64.766491] Registered led device: iwl-phy0::RX
[   64.766509] Registered led device: iwl-phy0::TX
[   64.771121] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  466.052916] Registered led device: iwl-phy0::radio
[  466.052939] Registered led device: iwl-phy0::assoc
[  466.052995] Registered led device: iwl-phy0::RX
[  466.053016] Registered led device: iwl-phy0::TX
[  476.712137] wlan0: no IPv6 routers present
[  508.653537] wlan0: Trigger new scan to find an IBSS to join
[  513.520141] wlan0: Trigger new scan to find an IBSS to join
[  514.390813] wlan0: Creating new IBSS network, BSSID f60d5ef2
[  515.557481] ip_tables: (C) 2000-2006 Netfilter Core Team
[  515.594261] nf_conntrack version 0.5.0 (16232 buckets, 64928 max)
[  515.594719] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[  515.594725] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[  515.594731] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  544.392179] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  575.284171] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  600.246557] Registered led device: iwl-phy0::radio
[  600.246645] Registered led device: iwl-phy0::assoc
[  600.246684] Registered led device: iwl-phy0::RX
[  600.246723] Registered led device: iwl-phy0::TX
[  600.254617] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  600.257471] wlan0: direct probe to AP f64596b8 try 1
[  600.456148] wlan0: direct probe to AP f64596b8 try 2
[  600.656150] wlan0: direct probe to AP f64596b8 try 3
[  600.856142] wlan0: direct probe to AP f64596b8 timed out
[  635.825132] CE: hpet increasing min_delta_ns to 15000 nsec
[  668.115282] wlan0: authenticate with AP f64596b8
[  668.118787] wlan0: authenticate with AP f64596b8
[  668.118809] wlan0: authenticated
[  668.118814] wlan0: associate with AP f64596b8
[  668.121657] wlan0: authenticate with AP f64596b8
[  668.121686] wlan0: authenticated
[  668.121691] wlan0: associate with AP f64596b8
[  668.125497] wlan0: RX AssocResp from db136026 (capab=0x431 status=0 aid=1)
[  668.125505] wlan0: associated
[  668.127574] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  679.096134] wlan0: no IPv6 routers present

```

this is my iwlist wlan0 scanning :
```
wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:1E:EA:06
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"PROLINK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000018f0357c92
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 000750524F4C494E4B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101

```

---

### Post by chili555 on 2009-05-18
> The router is set to BWould you please try setting it to Auto? You might also avoid the usual microwave and cordless phone interference with channel 11.

---

### Post by crazybuntu on 2009-05-18
> **chili555 said:**
> Would you please try setting it to Auto? You might also avoid the usual microwave and cordless phone interference with channel 11.


There is no automatic , but there is b+g which shows in iwlist :

```
wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:1E:EA:06
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"PROLINK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000515f99b
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 000750524F4C494E4B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

```But still cant connect from where i can with windows, and theres no microwave /phone between the router and the laptop .. i guess its just bad driver + hardware combination

---

### Post by crazybuntu on 2009-05-19
I had it working once from startup, but now its back to nothing... 

```
wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:1E:EA:06
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"PROLINK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000086880e70d
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000750524F4C494E4B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

```

i think the problem is when QUALITY is in the 20s below , it cannot make connection with router, but once i got it  connected by going close to the router, the QUALITY stays around 40 and once in a while to 20's without disconnection / drop . 

So far i have done :

[LIST]
[*]Changed Router to G
[*]Change Rate to 54M (sudo iwconfig rate 54M auto) as above
[*]Change the Router channel from 1 -> 11
[/LIST]

```
  21.913286] iwl3945 0000:02:00.0: loaded firmware version 15.28.2.8
[   21.958377] Registered led device: iwl-phy0::radio
[   21.958665] Registered led device: iwl-phy0::assoc
[   21.959490] Registered led device: iwl-phy0::RX
[   21.959524] Registered led device: iwl-phy0::TX
[   21.963108] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.563674] wlan0: direct probe to AP f601e6b8 try 1
[   48.764058] wlan0: direct probe to AP f601e6b8 try 2
[   48.969029] wlan0: direct probe to AP f601e6b8 try 3
[   48.971032] wlan0 direct probe responded
[   48.971036] wlan0: authenticate with AP f601e6b8
[   49.169032] wlan0: authenticate with AP f601e6b8
[   49.369043] wlan0: authenticate with AP f601e6b8
[   49.571005] wlan0: authentication with AP f601e6b8 timed out
[   64.216980] wlan0: direct probe to AP f601e6b8 try 1
[   64.218830] wlan0: direct probe to AP f601e6b8 try 1
[   64.416563] wlan0: direct probe to AP f601e6b8 try 2
[   64.616065] wlan0: direct probe to AP f601e6b8 try 3
[   64.816139] wlan0: direct probe to AP f601e6b8 timed out
[   78.464536] wlan0: direct probe to AP f601e6b8 try 1
[   78.466508] wlan0: direct probe to AP f601e6b8 try 1
[   78.664135] wlan0: direct probe to AP f601e6b8 try 2
[   78.864146] wlan0: direct probe to AP f601e6b8 try 3
[   78.866292] wlan0 direct probe responded
[   78.866300] wlan0: authenticate with AP f601e6b8
[   79.064148] wlan0: authenticate with AP f601e6b8
[   79.264153] wlan0: authenticate with AP f601e6b8
[   79.464144] wlan0: authentication with AP f601e6b8 timed out
[   94.156799] wlan0: direct probe to AP f601e6b8 try 1
[   94.158715] wlan0: direct probe to AP f601e6b8 try 1
[   94.356199] wlan0: direct probe to AP f601e6b8 try 2
[   94.563994] wlan0: direct probe to AP f601e6b8 try 3
[   94.760083] wlan0: direct probe to AP f601e6b8 timed out
[  115.981413] wlan0: direct probe to AP f601e6b8 try 1
[  115.983203] wlan0: direct probe to AP f601e6b8 try 1
[  116.180060] wlan0: direct probe to AP f601e6b8 try 2
[  116.380429] wlan0: direct probe to AP f601e6b8 try 3
[  116.580052] wlan0: direct probe to AP f601e6b8 timed out
[  128.424799] wlan0: direct probe to AP f601e6b8 try 1
[  128.426717] wlan0: direct probe to AP f601e6b8 try 1
[  128.624146] wlan0: direct probe to AP f601e6b8 try 2
[  128.626291] wlan0 direct probe responded
[  128.626300] wlan0: authenticate with AP f601e6b8
[  128.824175] wlan0: authenticate with AP f601e6b8
[  128.839944] wlan0: authenticated
[  128.839952] wlan0: associate with AP f601e6b8
[  128.849991] wlan0: RX AssocResp from ee4e9026 (capab=0x431 status=0 aid=1)
[  128.849999] wlan0: associated
[  128.855226] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  129.112233] usb 2-1: USB disconnect, address 2
[  139.756108] wlan0: no IPv6 routers present

```There is still a problem that annoys me, the NM-APPLET  always asks KEYRING password on startup and when detecting networks it asks WEP key each time even if its already there i have to click OK.

---

### Post by crazybuntu on 2009-05-20
buump.... just wondering if anyone is in the same situation ?

---

### Post by crazybuntu on 2009-05-23
anyone ? why is the signal quality lower in UBUNTU Than WINDOWS ?????? 

if its so hard to install a driver, this os shouldnt even be released in first place.

---

### Post by chili555 on 2009-05-25
> if its so hard to install a driver, this os shouldnt even be released in first place.Your driver is installed now. Otherwise it would not scan or connect under any circumstance. If we wait to release a newer version of an operating system until every problem is fixed, and every piece of hardware ever invented works perfectly, then why did we see XP or Vista?

Some things to try:```
sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo ifup wlan0
```Do not reboot. Try to connect. Is there any difference in your ability to connect?

Also try:```
sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe iwl3945 antenna=1
sudo ifup wlan0
```Do not reboot. Any improvement?

---

### Post by capybaron on 2009-05-25
I am having a similar problem to crazybuntu in that I cannot connect to any router with the Intel3945 on my Leveno T60 running Ubuntu 9.04.

Unlike crazybuntu, when I try
```

sudo rmmod -f iwl3945

```I get a kernel panic, so I cannot even try reloading the iwl3945 driver.

I should note that in my case, I can get the system to connect wirelessly under Ubuntu 8.04 (8.04 has other problems, though) and that scanning with iwlist also works.

I am not sure how to capture information during a kernel panic (aside from the tedious transcription from what I see on the screen), but I would be appreciate help with this problem.

> **chili555 said:**
> 
Some things to try:```
sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo ifup wlan0
```Do not reboot. Try to connect. Is there any difference in your ability to connect?

Also try:```
sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe iwl3945 antenna=1
sudo ifup wlan0
```Do not reboot. Any improvement?

---

### Post by chili555 on 2009-05-26
> I get a kernel panicIf you get a kernel panic when you simply try to remove a module, then you have an underlying issue that is much bigger than trying to connect wirelessly. Usually clues are found in */var/log/messages*. You will note that it is timestamped, so you can browse for messages thrown at the time of the kernel panic. Check with:```
sudo less /var/log/messages
```Copy and paste any suspicious messages into a text document so you can post them here.

---

### Post by capybaron on 2009-05-26
As far as the kernel panic was concerned, I was able to avoid the panic by turning off **wlan0** using **ifconfig wlan0 down **.  For whatever reason, **ifdown** was not working properly.

Basically, the **antenna=1** and **disable_hw_scan=1** options had no effect on my inability to connect to a wireless access point (keep in mind that I can connect with the same T60 using a live Ubuntu 8.04 CD).  I would appreciate advice on what to try next.


> **chili555 said:**
> If you get a kernel panic when you simply try to remove a module, then you have an underlying issue that is much bigger than trying to connect wirelessly. Usually clues are found in */var/log/messages*. You will note that it is timestamped, so you can browse for messages thrown at the time of the kernel panic. Check with:```
sudo less /var/log/messages
```Copy and paste any suspicious messages into a text document so you can post them here.

---

### Post by crazybuntu on 2009-05-31
Finally got it to work directly on startup and plays youtube videos without buffering / drop... i dont know which fixed it though, the things i did before it worked :

1. try adding this by doing : sudo gedit /etc/rc.local

rmmod drivername
modprobe drivername

before the last line
then reboot... 

had the same problem but with iwl3945 card, and now works..
Hope it solves your problem

The drivername can be checked with : lshw -C network


2. I updated to kernel Linux JANGKRIK 2.6.29-02062903-generic
and added disable.ipv6=1 in the boot option of the kernel in GRUB 
(sudo gedit /boot/grub/menu.lst)

if you're asking for explanation what i just did .. dont ask me cuz i dont have a clue..

---

