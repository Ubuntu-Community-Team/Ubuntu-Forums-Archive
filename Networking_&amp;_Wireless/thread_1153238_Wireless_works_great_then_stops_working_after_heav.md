---
title: "Wireless works great then stops working after heavy usage Juanty 9.04"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Dr. Feelgood on 2009-05-08
My wireless in Jaunty will work incredibly fast for a while and then once it hits a certain amount of data transfered it just stops working altogether and I have to reboot to get it to work again.  It still says I'm connected, it still shows networks, it just doesn't transfer an data.  If i don't download anything big it will stay working indefinitely, but when the megabytes start flying it tanks... religiously.  Here are my specs.  I'm using a a Compaq Presario 700 laptop with a fresh install of Jaunty 9.04.  My PCMCIA card is an older Microsoft MN-520 using the orinoco_cs driver.  Here are my settings before the wireless crashes:

```

ryan@tashtego:~$ lspcmcia
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.0)
Socket 0 Device 0:	[orinoco_cs]		(bus ID: 0.0)
ryan@tashtego:~$ sudo lshw -C network
[sudo] password for ryan: 
  *-network               
       description: Wireless Notebook Adapter MN-520
       vendor: Microsoft
       physical id: 0
       version: 1.0.3
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:08:02:04:d9:a1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0d:3a:23:1c:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.9 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:07:37:8f:b4:ec
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ryan@tashtego:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:04:d9:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x1400 

eth1      Link encap:Ethernet  HWaddr 00:0d:3a:23:1c:41  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:3aff:fe23:1c41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2773941 (2.7 MB)  TX bytes:679437 (679.4 KB)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
ryan@tashtego:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"docjp"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:BB:E2:E9   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/92  Signal level=-28 dBm  Noise level=-141 dBm
          Rx invalid nwid:0  Rx invalid crypt:1930  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Here is the dmseg after I crash the wireless by downloading a large file:

```

[    0.792455] ACPI: EC: GPE = 0x6, I/O: command/status = 0x66, data = 0x62
[    0.792460] ACPI: EC: driver started in interrupt mode
[    0.792616] ACPI: No dock devices found.
[    0.792634] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.792718] pci 0000:00:00.0: reg 10 32bit mmio: [0xec000000-0xefffffff]
[    0.792751] pci 0000:00:00.0: Disabling VIA memory write queue (PCI ID 0305, rev 80): [55] 3c & 1f -> 1c
[    0.792797] pci 0000:00:01.0: supports D1
[    0.792904] pci 0000:00:07.1: reg 20 io port: [0x1840-0x184f]
[    0.792965] pci 0000:00:07.2: reg 20 io port: [0x1800-0x181f]
[    0.793045] pci 0000:00:07.4: quirk: region 8100-810f claimed by vt82c686 SMB
[    0.793086] pci 0000:00:07.5: reg 10 io port: [0x1000-0x10ff]
[    0.793094] pci 0000:00:07.5: reg 14 io port: [0x1854-0x1857]
[    0.793102] pci 0000:00:07.5: reg 18 io port: [0x1850-0x1853]
[    0.793158] pci 0000:00:09.0: reg 10 32bit mmio: [0xe8000000-0xe800ffff]
[    0.793166] pci 0000:00:09.0: reg 14 io port: [0x1858-0x185f]
[    0.793194] pci 0000:00:09.0: PME# supported from D3hot
[    0.793200] pci 0000:00:09.0: PME# disabled
[    0.793233] pci 0000:00:0a.0: reg 10 32bit mmio: [0xffbfe000-0xffbfefff]
[    0.793244] pci 0000:00:0a.0: supports D1 D2
[    0.793247] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.793253] pci 0000:00:0a.0: PME# disabled
[    0.793285] pci 0000:00:0b.0: reg 10 io port: [0x1400-0x14ff]
[    0.793294] pci 0000:00:0b.0: reg 14 32bit mmio: [0xe8010000-0xe80100ff]
[    0.793322] pci 0000:00:0b.0: supports D1 D2
[    0.793326] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
[    0.793331] pci 0000:00:0b.0: PME# disabled
[    0.793393] pci 0000:01:00.0: reg 10 32bit mmio: [0xe8100000-0xe817ffff]
[    0.793402] pci 0000:01:00.0: reg 14 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.793424] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.793434] pci 0000:01:00.0: supports D1 D2
[    0.793474] pci 0000:00:01.0: bridge 32bit mmio: [0xe8100000-0xe81fffff]
[    0.793481] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.793509] bus 00 -> node 0
[    0.793519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.797738] ACPI: PCI Interrupt Link [LNKA] (IRQs *4)
[    0.797985] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[    0.798221] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[    0.798471] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
[    0.798694] ACPI: WMI: Mapper loaded
[    0.799229] SCSI subsystem initialized
[    0.799341] libata version 3.00 loaded.
[    0.799494] usbcore: registered new interface driver usbfs
[    0.799532] usbcore: registered new interface driver hub
[    0.799598] usbcore: registered new device driver usb
[    0.799855] PCI: Using ACPI for IRQ routing
[    0.800039] Bluetooth: Core ver 2.13
[    0.800139] NET: Registered protocol family 31
[    0.800143] Bluetooth: HCI device and connection manager initialized
[    0.800152] Bluetooth: HCI socket layer initialized
[    0.800157] NET: Registered protocol family 8
[    0.800160] NET: Registered protocol family 20
[    0.800181] NetLabel: Initializing
[    0.800185] NetLabel:  domain hash size = 128
[    0.800187] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.800223] NetLabel:  unlabeled traffic allowed by default
[    0.800448] AppArmor: AppArmor Filesystem Enabled
[    0.800467] pnp: PnP ACPI init
[    0.800467] ACPI: bus type pnp registered
[    0.805048] pnp: PnP ACPI: found 11 devices
[    0.805052] ACPI: ACPI bus type pnp unregistered
[    0.805060] PnPBIOS: Disabled by ACPI PNP
[    0.805083] system 00:05: iomem range 0x0-0x9ffff could not be reserved
[    0.805090] system 00:05: iomem range 0xdc000-0xdffff could not be reserved
[    0.805095] system 00:05: iomem range 0x7000000-0x7ffffff could not be reserved
[    0.805106] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.839984] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.839988] pci 0000:00:01.0:   IO window: disabled
[    0.839996] pci 0000:00:01.0:   MEM window: 0xe8100000-0xe81fffff
[    0.840015] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.840023] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.840028] pci 0000:00:0a.0:   IO window: 0x001c00-0x001cff
[    0.840034] pci 0000:00:0a.0:   IO window: 0x002000-0x0020ff
[    0.840040] pci 0000:00:0a.0:   PREFETCH window: 0x10000000-0x13ffffff
[    0.840046] pci 0000:00:0a.0:   MEM window: 0x14000000-0x17ffffff
[    0.840065] pci 0000:00:01.0: setting latency timer to 64
[    0.840142] pci 0000:00:0a.0: power state changed by ACPI to D0
[    0.840545] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    0.840550] PCI: setting IRQ 11 as level-triggered
[    0.840560] pci 0000:00:0a.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    0.840571] bus: 00 index 0 io port: [0x00-0xffff]
[    0.840574] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.840578] bus: 01 index 0 mmio: [0x0-0x0]
[    0.840582] bus: 01 index 1 mmio: [0xe8100000-0xe81fffff]
[    0.840585] bus: 01 index 2 mmio: [0xf0000000-0xf7ffffff]
[    0.840589] bus: 01 index 3 mmio: [0x0-0x0]
[    0.840592] bus: 02 index 0 io port: [0x1c00-0x1cff]
[    0.840596] bus: 02 index 1 io port: [0x2000-0x20ff]
[    0.840600] bus: 02 index 2 mmio: [0x10000000-0x13ffffff]
[    0.840603] bus: 02 index 3 mmio: [0x14000000-0x17ffffff]
[    0.840634] NET: Registered protocol family 2
[    0.840886] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.841393] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.841623] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.841832] TCP: Hash tables configured (established 8192 bind 8192)
[    0.841837] TCP reno registered
[    0.841980] NET: Registered protocol family 1
[    0.842282] checking if image is initramfs... it is
[    1.340149] Switched to high resolution mode on CPU 0
[    1.945135] Freeing initrd memory: 7371k freed
[    1.945406] cpufreq: No nForce2 chipset.
[    1.945723] audit: initializing netlink socket (disabled)
[    1.945783] type=2000 audit(1241770242.944:1): initialized
[    1.958992] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.961441] VFS: Disk quotas dquot_6.5.1
[    1.961550] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.962692] fuse init (API version 7.10)
[    1.962859] msgmni has been set to 425
[    1.963305] alg: No test for stdrng (krng)
[    1.963333] io scheduler noop registered
[    1.963337] io scheduler anticipatory registered
[    1.963340] io scheduler deadline registered
[    1.963370] io scheduler cfq registered (default)
[    1.963413] pci 0000:00:00.0: Applying VIA southbridge workaround
[    1.963421] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.963428] pci 0000:00:07.0: Disabling VIA external APIC routing
[    1.963469] pci 0000:01:00.0: Boot video device
[    1.968706] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.968725] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.969446] ACPI: AC Adapter [AC] (on-line)
[    1.983098] ACPI: Battery Slot [BAT0] (battery present)
[    1.983256] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.983262] ACPI: Power Button (FF) [PWRF]
[    1.983345] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.983355] ACPI: Sleep Button (CM) [SLPB]
[    1.983430] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.983436] ACPI: Power Button (CM) [PWRB]
[    1.983528] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.988830] ACPI: Lid Switch [LID]
[    1.989127] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.989177] processor ACPI_CPU:00: registered as cooling_device0
[    1.989184] ACPI: Processor [CPU0] (supports 16 throttling states)
[    1.992048] isapnp: Scanning for PnP cards...
[    2.346230] isapnp: No Plug & Play device found
[    2.348573] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.350463] brd: module loaded
[    2.351101] loop: module loaded
[    2.351341] Fixed MDIO Bus: probed
[    2.351356] PPP generic driver version 2.4.2
[    2.351493] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.351564] Driver 'sd' needs updating - please use bus_type methods
[    2.351584] Driver 'sr' needs updating - please use bus_type methods
[    2.352582] pata_via 0000:00:07.1: version 0.3.3
[    2.353109] scsi0 : pata_via
[    2.353781] scsi1 : pata_via
[    2.354874] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1840 irq 14
[    2.354880] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1848 irq 15
[    2.516515] ata1.00: ATA-5: HITACHI_DK23CA-20, 00H1A0J1, max UDMA/100
[    2.516521] ata1.00: 39070080 sectors, multi 16: LBA 
[    2.532505] ata1.00: configured for UDMA/100
[    2.696437] ata2.00: ATAPI: SD-R2102, 1A15, max MWDMA2
[    2.712455] ata2.00: configured for MWDMA2
[    2.713439] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23CA-2 00H1 PQ: 0 ANSI: 5
[    2.713661] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
[    2.713699] sd 0:0:0:0: [sda] Write Protect is off
[    2.713705] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.713759] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.713950] sd 0:0:0:0: [sda] 39070080 512-byte hardware sectors: (20.0 GB/18.6 GiB)
[    2.713981] sd 0:0:0:0: [sda] Write Protect is off
[    2.713986] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.714038] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.714047]  sda: sda1 sda2 < sda5 sda6 >
[    2.747079] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.747200] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.749753] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R2102 1A15 PQ: 0 ANSI: 5
[    2.756694] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.756701] Uniform CD-ROM driver Revision: 3.20
[    2.756896] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.756968] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.757256] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.757287] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.757309] uhci_hcd: USB Universal Host Controller Interface driver
[    2.757867] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[    2.757874] PCI: setting IRQ 9 as level-triggered
[    2.757884] uhci_hcd 0000:00:07.2: PCI INT D -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
[    2.757902] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    2.758053] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    2.758093] uhci_hcd 0000:00:07.2: irq 9, io base 0x00001800
[    2.758289] usb usb1: configuration #1 chosen from 1 choice
[    2.758343] hub 1-0:1.0: USB hub found
[    2.758368] hub 1-0:1.0: 2 ports detected
[    2.758606] usbcore: registered new interface driver libusual
[    2.758674] usbcore: registered new interface driver usbserial
[    2.758698] USB Serial support registered for generic
[    2.758722] usbcore: registered new interface driver usbserial_generic
[    2.758727] usbserial: USB Serial Driver core
[    2.758816] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.760766] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.760781] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.761034] mice: PS/2 mouse device common for all mice
[    2.761448] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.761482] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    2.761653] device-mapper: uevent: version 1.0.3
[    2.761906] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.762047] device-mapper: multipath: version 1.0.5 loaded
[    2.762053] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.762235] EISA: Probing bus 0 at eisa.0
[    2.762251] Cannot allocate resource for EISA slot 1
[    2.762256] Cannot allocate resource for EISA slot 2
[    2.762285] Cannot allocate resource for EISA slot 8
[    2.762288] EISA: Detected 0 cards.
[    2.762406] cpuidle: using governor ladder
[    2.762483] cpuidle: using governor menu
[    2.763451] TCP cubic registered
[    2.763624] NET: Registered protocol family 10
[    2.764461] lo: Disabled Privacy Extensions
[    2.765050] NET: Registered protocol family 17
[    2.765093] Bluetooth: L2CAP ver 2.11
[    2.765096] Bluetooth: L2CAP socket layer initialized
[    2.765102] Bluetooth: SCO (Voice Link) ver 0.6
[    2.765105] Bluetooth: SCO socket layer initialized
[    2.765193] Bluetooth: RFCOMM socket layer initialized
[    2.765215] Bluetooth: RFCOMM TTY layer initialized
[    2.765219] Bluetooth: RFCOMM ver 1.10
[    2.765263] powernow-k8: Processor cpuid 662 not supported
[    2.765382] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[    2.772857] powernow: No PST tables match this cpuid (0x762)
[    2.772861] powernow: This is indicative of a broken BIOS.
[    2.772864] powernow: Trying ACPI perflib
[    2.772902] powernow: Minimum speed 498 MHz. Maximum speed 1195 MHz.
[    2.773092] IO APIC resources could be not be allocated.
[    2.773153] Using IPI No-Shortcut mode
[    2.773366] registered taskstats version 1
[    2.773532]   Magic number: 9:57:169
[    2.773709] rtc_cmos 00:02: setting system clock to 2009-05-08 08:10:45 UTC (1241770245)
[    2.773715] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.773719] EDD information not available.
[    2.775061] Freeing unused kernel memory: 532k freed
[    2.775287] Write protecting the kernel text: 4128k
[    2.775357] Write protecting the kernel read-only data: 1532k
[    2.811005] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.840347] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[    3.402265] Floppy drive(s): fd0 is 1.44M
[    3.419916] FDC 0 is a post-1991 82077
[    3.634646] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.634725] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.640121] 8139too Fast Ethernet driver 0.9.28
[    3.640237] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    3.641587] eth0: RealTek RTL8139 at 0x1400, 00:08:02:04:d9:a1, IRQ 11
[    3.641592] eth0:  Identified 8139 chip type 'RTL-8139C'
[    4.336744] Marking TSC unstable due to TSC halts in idle
[    4.418477] PM: Starting manual resume from disk
[    4.418488] PM: Resume from partition 8:5
[    4.418491] PM: Checking hibernation image.
[    4.418887] PM: Resume from disk failed.
[    4.424435] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.424444] EXT3-fs: write access will be enabled during recovery.
[    5.783611] kjournald starting.  Commit interval 5 seconds
[    5.783662] EXT3-fs: recovery complete.
[    5.784923] EXT3-fs: mounted filesystem with ordered data mode.
[   15.157909] udev: starting version 141
[   15.406264] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input6
[   15.437985] Linux agpgart interface v0.103
[   15.444357] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.468902] parport_pc: VIA 686A/8231 detected
[   15.468911] parport_pc: probing current configuration
[   15.468932] parport_pc: Current parallel port base: 0x378
[   15.469014] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   15.489745] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   15.497135] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xec000000
[   15.560575] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.561738] parport_pc: VIA parallel port: io=0x378, irq=7
[   15.781423] vt596_smbus 0000:00:07.4: SMBUS: Error: Host SMBus controller not enabled! - upgrade BIOS or use force=1
[   15.967011] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   16.073409] yenta_cardbus 0000:00:0a.0: CardBus bridge found [0e11:b103]
[   16.073438] yenta_cardbus 0000:00:0a.0: Enabling burst memory read transactions
[   16.073445] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
[   16.073450] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
[   16.073457] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01001002, devctl 0x64
[   16.305126] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0018, PCI irq 11
[   16.305137] yenta_cardbus 0000:00:0a.0: Socket status: 30000010
[   16.460097] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[   16.544252] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   16.957225] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   16.958266] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   16.958273] PCI: setting IRQ 5 as level-triggered
[   16.958283] VIA 82xx Audio 0000:00:07.5: PCI INT C -> Link[LNKC] -> GSI 5 (level, low) -> IRQ 5
[   16.958437] VIA 82xx Audio 0000:00:07.5: setting latency timer to 64
[   17.007822] ppdev: user-space parallel port driver
[   17.425468] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   17.427904] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   17.428989] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   17.429859] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   17.431009] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   17.432000] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   17.439514] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   17.573835] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9d48b1, caps: 0x904713/0x4006
[   17.605253] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   17.613216] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   17.641136] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   17.933759] eth1: Hardware identity 800c:0000:0001:0000
[   17.933889] eth1: Station identity  001f:0009:0001:0004
[   17.933896] eth1: Firmware determined as Intersil 1.4.9
[   17.933901] eth1: Ad-hoc demo mode supported
[   17.933904] eth1: IEEE standard IBSS ad-hoc mode supported
[   17.933907] eth1: WEP supported, 104-bit key
[   18.058729] eth1: MAC address 00:0d:3a:23:1c:41
[   18.058827] eth1: Station name "Prism  I"
[   18.059459] eth1: ready
[   18.061358] eth1: orinoco_cs at 0.0, irq 3, io 0x0100-0x013f
[   18.158429] ieee80211_crypt: registered algorithm 'NULL'
[   18.703889] lp0: using parport0 (interrupt-driven).
[   19.067047] Adding 650592k swap on /dev/sda5.  Priority:-1 extents:1 across:650592k
[   19.798160] EXT3 FS on sda6, internal journal
[   21.300829] type=1505 audit(1241784664.026:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2028
[   21.422203] type=1505 audit(1241784664.146:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2032
[   21.422790] type=1505 audit(1241784664.146:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2032
[   21.422956] type=1505 audit(1241784664.146:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2032
[   21.423106] type=1505 audit(1241784664.146:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2032
[   21.763405] type=1505 audit(1241784664.486:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2037
[   21.764260] type=1505 audit(1241784664.490:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2037
[   21.838674] type=1505 audit(1241784664.562:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2041
[   25.481813] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.481821] Bluetooth: BNEP filters: protocol multicast
[   25.518332] Bridge firewalling registered
[   31.279370] eth0: link down
[   31.279486] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.321288] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.344967] eth1: New link status: Disconnected (0002)
[   32.682156] eth1: New link status: Connected (0001)
[   32.682233] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   43.212041] eth1: no IPv6 routers present
[   79.135625] eth1: New link status: Disconnected (0002)
[   80.246445] eth1: New link status: Connected (0001)
[   90.836071] Clocksource tsc unstable (delta = -105105713 ns)
[ 4573.619056] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 4573.619068] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 4573.619073] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 4715.440188] eth1: Information frame lost.
[ 4715.442246] eth1: Information frame lost.
[ 4715.447842] eth1: Information frame lost.
[ 4715.453845] eth1: Information frame lost.
[ 4715.461347] eth1: Information frame lost.
[ 4715.465165] eth1: Information frame lost.
[ 4715.468048] eth1: Information frame lost.
[ 4715.471717] eth1: Information frame lost.
[ 4715.477590] eth1: Information frame lost.
[ 4715.481293] eth1: Information frame lost.
[ 4720.442374] __ratelimit: 908 callbacks suppressed
[ 4720.442389] eth1: Information frame lost.
[ 4720.446095] eth1: Information frame lost.
[ 4720.447332] eth1: Information frame lost.
[ 4720.453291] eth1: Information frame lost.
[ 4720.458662] eth1: Information frame lost.
[ 4720.461317] eth1: Information frame lost.
[ 4720.464037] eth1: Information frame lost.
[ 4720.468221] eth1: Information frame lost.
[ 4720.471432] eth1: Information frame lost.
[ 4720.481948] eth1: Information frame lost.
[ 4755.459231] __ratelimit: 609 callbacks suppressed
[ 4755.459245] eth1: Information frame lost.
[ 4755.463114] eth1: Information frame lost.
[ 4755.493523] eth1: Information frame lost.
[ 4755.495567] eth1: Information frame lost.
[ 4755.502931] eth1: Information frame lost.
[ 4755.510936] eth1: Information frame lost.
[ 4755.516833] eth1: Information frame lost.
[ 4755.520507] eth1: Information frame lost.
[ 4755.524275] eth1: Information frame lost.
[ 4755.659569] eth1: Information frame lost.
[ 4760.464534] __ratelimit: 409 callbacks suppressed
[ 4760.464548] eth1: Information frame lost.
[ 4760.465751] eth1: Information frame lost.
[ 4760.467501] eth1: Information frame lost.
[ 4760.473469] eth1: Information frame lost.
[ 4760.475604] eth1: Information frame lost.
[ 4760.477648] eth1: Information frame lost.
[ 4760.486890] eth1: Information frame lost.
[ 4760.490891] eth1: Information frame lost.
[ 4760.495600] eth1: Information frame lost.
[ 4760.499087] eth1: Information frame lost.
[ 4766.334727] __ratelimit: 207 callbacks suppressed
[ 4766.334742] eth1: Information frame lost.
[ 4766.337582] eth1: Information frame lost.
[ 4766.338788] eth1: Information frame lost.
[ 4766.342865] eth1: Information frame lost.
[ 4766.347218] eth1: Information frame lost.
[ 4766.348452] eth1: Information frame lost.
[ 4766.353930] eth1: Information frame lost.
[ 4766.356537] eth1: Information frame lost.
[ 4766.361429] eth1: Information frame lost.
[ 4766.366754] eth1: Information frame lost.
[ 4771.343347] __ratelimit: 239 callbacks suppressed
[ 4771.343362] eth1: Information frame lost.
[ 4771.398273] eth1: Information frame lost.
[ 4771.402736] eth1: Information frame lost.
[ 4771.407016] eth1: Information frame lost.
[ 4771.410939] eth1: Information frame lost.
[ 4771.413989] eth1: Information frame lost.
[ 4771.413989] eth1: Information frame lost.
[ 4771.422578] eth1: Information frame lost.
[ 4771.426180] eth1: Information frame lost.
[ 4771.427393] eth1: Information frame lost.
[ 4776.421356] __ratelimit: 456 callbacks suppressed
[ 4776.421371] eth1: Information frame lost.
[ 4776.422970] eth1: Information frame lost.
[ 4776.426717] eth1: Information frame lost.
[ 4776.429405] eth1: Information frame lost.
[ 4776.434161] eth1: Information frame lost.
[ 4776.439064] eth1: Information frame lost.
[ 4776.442766] eth1: Information frame lost.
[ 4776.446154] eth1: Information frame lost.
[ 4776.461471] eth1: Information frame lost.
[ 4776.464501] eth1: Information frame lost.
[ 4800.025077] __ratelimit: 493 callbacks suppressed
[ 4800.025091] eth1: Information frame lost.
[ 4800.026263] eth1: Information frame lost.
[ 4800.032660] eth1: Information frame lost.
[ 4800.036997] eth1: Information frame lost.
[ 4800.059475] eth1: Information frame lost.
[ 4800.093496] eth1: Information frame lost.
[ 4800.094796] eth1: Information frame lost.
[ 4800.099513] eth1: Information frame lost.
[ 4800.168850] eth1: Information frame lost.
[ 4800.171738] eth1: Information frame lost.
[ 4805.037284] __ratelimit: 252 callbacks suppressed
[ 4805.037298] eth1: Information frame lost.
[ 4805.068073] eth1: Information frame lost.
[ 4805.097402] eth1: Information frame lost.
[ 4805.119304] eth1: Information frame lost.
[ 4805.171493] eth1: Information frame lost.
[ 4805.175878] eth1: Information frame lost.
[ 4805.178007] eth1: Information frame lost.
[ 4805.179153] eth1: Information frame lost.
[ 4805.183042] eth1: Information frame lost.
[ 4805.188049] eth1: Information frame lost.
[ 4811.069749] __ratelimit: 432 callbacks suppressed
[ 4811.069763] eth1: Information frame lost.
[ 4811.074531] eth1: Information frame lost.
[ 4811.075722] eth1: Information frame lost.
[ 4811.078687] eth1: Information frame lost.
[ 4811.084775] eth1: Information frame lost.
[ 4811.087472] eth1: Information frame lost.
[ 4811.093707] eth1: Information frame lost.
[ 4811.098537] eth1: Information frame lost.
[ 4811.100621] eth1: Information frame lost.
[ 4811.110391] eth1: Information frame lost.
[ 4834.890493] __ratelimit: 386 callbacks suppressed
[ 4834.890508] eth1: Information frame lost.
[ 4834.894047] eth1: Information frame lost.
[ 4834.895993] eth1: Information frame lost.
[ 4834.898700] eth1: Information frame lost.
[ 4834.901288] eth1: Information frame lost.
[ 4834.915545] eth1: Information frame lost.
[ 4834.918866] eth1: Information frame lost.
[ 4834.921319] eth1: Information frame lost.
[ 4834.922250] eth1: Information frame lost.
[ 4834.927088] eth1: Information frame lost.
[ 4839.903064] __ratelimit: 507 callbacks suppressed
[ 4839.903079] eth1: Information frame lost.
[ 4849.773285] eth1: Information frame lost.
[ 4849.779436] eth1: Information frame lost.
[ 4849.782134] eth1: Information frame lost.
[ 4849.785430] eth1: Information frame lost.
[ 4849.788124] eth1: Information frame lost.
[ 4849.793556] eth1: Information frame lost.
[ 4849.794685] eth1: Information frame lost.
[ 4849.797801] eth1: Information frame lost.
[ 4849.798947] eth1: Information frame lost.
[ 4854.778616] __ratelimit: 372 callbacks suppressed
[ 4854.778632] eth1: Information frame lost.
[ 4854.782005] eth1: Information frame lost.
[ 4854.784783] eth1: Information frame lost.
[ 4854.789847] eth1: Information frame lost.
[ 4854.795391] eth1: Information frame lost.
[ 4854.801942] eth1: Information frame lost.
[ 4854.804547] eth1: Information frame lost.
[ 4854.808358] eth1: Information frame lost.
[ 4854.812002] eth1: Information frame lost.
[ 4854.816530] eth1: Information frame lost.
[ 4859.788207] __ratelimit: 971 callbacks suppressed
[ 4859.788222] eth1: Information frame lost.
[ 4859.789437] eth1: Information frame lost.
[ 4859.792386] eth1: Information frame lost.
[ 4859.795800] eth1: Information frame lost.
[ 4859.799185] eth1: Information frame lost.
[ 4859.804224] eth1: Information frame lost.
[ 4859.812096] eth1: Information frame lost.
[ 4859.819299] eth1: Information frame lost.
[ 4859.825494] eth1: Information frame lost.
[ 4859.828919] eth1: Information frame lost.
[ 4864.797638] __ratelimit: 848 callbacks suppressed
[ 4864.797653] eth1: Information frame lost.
[ 4864.799458] eth1: Information frame lost.
[ 4864.804316] eth1: Information frame lost.
[ 4864.808358] eth1: Information frame lost.
[ 4864.813097] eth1: Information frame lost.
[ 4864.817070] eth1: Information frame lost.
[ 4864.822055] eth1: Information frame lost.
[ 4864.825384] eth1: Information frame lost.
[ 4864.834373] eth1: Information frame lost.
[ 4864.837472] eth1: Information frame lost.
[ 4870.834662] __ratelimit: 729 callbacks suppressed
[ 4870.834677] eth1: Information frame lost.
[ 4870.836542] eth1: Information frame lost.
[ 4870.840360] eth1: Information frame lost.
[ 4870.842119] eth1: Information frame lost.
[ 4870.844978] eth1: Information frame lost.
[ 4870.848178] eth1: Information frame lost.
[ 4870.850171] eth1: Information frame lost.
[ 4870.854043] eth1: Information frame lost.
[ 4870.856631] eth1: Information frame lost.
[ 4870.857859] eth1: Information frame lost.
[ 4875.856475] __ratelimit: 579 callbacks suppressed
[ 4875.856490] eth1: Information frame lost.
[ 4875.908328] eth1: Information frame lost.

```

And these are my configurations after the wireless stops

```

ryan@tashtego:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:04:d9:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x1400 

eth1      Link encap:Ethernet  HWaddr 00:0d:3a:23:1c:41  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:3aff:fe23:1c41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21281 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42176640 (42.1 MB)  TX bytes:3343744 (3.3 MB)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:159 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26254 (26.2 KB)  TX bytes:26254 (26.2 KB)

ryan@tashtego:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"docjp"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:BB:E2:E9   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=74/92  Signal level=-14 dBm  Noise level=-142 dBm
          Rx invalid nwid:0  Rx invalid crypt:2277  Rx invalid frag:3
          Tx excessive retries:21  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ryan@tashtego:~$ sudo lshw -C network
  *-network               
       description: Wireless Notebook Adapter MN-520
       vendor: Microsoft
       physical id: 0
       version: 1.0.3
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:08:02:04:d9:a1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0d:3a:23:1c:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.9 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:07:37:8f:b4:ec
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Now here is where the problem seems to lie (paraphrased from dmseg above)

```

[   90.836071] Clocksource tsc unstable (delta = -105105713 ns)
[ 4573.619056] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 4573.619068] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 4573.619073] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[ 4715.440188] eth1: Information frame lost.
[ 4715.442246] eth1: Information frame lost.

```

I went to the website it specified but what it recommended was pcmciautils which is already installed on my system.  I'm at a loss here.  It's great that my internet is working and fast and all but this burn out is getting very frustrating.  This has never been an issue and I've been on ubuntu since Breezy.  Any help is greatly appreciated.

---

### Post by superprash2003 on 2009-05-09
try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by Dr. Feelgood on 2009-05-09
Doesn't work... besides there is nothing wrong with my speed.  Well that's it folks, I've had enough of this crap.  That's 3 show stopping bugs now, not to mention the minor ones.  I'm reloading Hardy.  Jaunty is by far the worst, buggiest OS that Ubuntu has released in 5 years, at least for my setup.  Internet stops, video doesn't work at all and the damn computer can't even shut off anymore.  If anyone else is running older equipment just stick to 8.04.
</rant>

---

### Post by superprash2003 on 2009-05-10
well its just released , it would take time to fix the bugs.. that previous link was not only for slow speeds but for problems like yours.. you could also try looking for other drivers for your wifi card if you wish..

---

