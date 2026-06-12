---
title: "TVTime help"
date: 2010-05-08
forum: Multimedia Software
---

### Post by neslot35 on 2010-05-08
I'm a newb to Ubuntu, today is my first day exploring and configuring it.  I have a Hauppage WinTV tuner card to watch TV with so my son and I don't have to fight over the television remote.  Unfortunately I can't get the tv tuner to work with Ubuntu 10.  I've browsed a number of forums and threads but haven't found a solution yet. 

I installed TVtime from Applications > Ubuntu Software Center and when i click on the icon from the applications menu and run it, a window opens and then instantly closes.  I can't read anything in it or the window title.  Any ideas on how i can get this to work?

---

### Post by xc3RnbFO8P on 2010-05-09
In Terminal, show the output of:
> lspci -vnn
and
> dmesg

---

### Post by neslot35 on 2010-05-09
lscpi -vnn shows
```

00:00.0 Host bridge [0600]: Intel Corporation 82X38/X48 Express DRAM Controller [8086:29e0]
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: x38_edac
    Kernel modules: x38_edac

00:01.0 PCI bridge [0604]: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge [8086:29e1]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: dc000000-dfefffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge [0604]: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge [8086:29e9]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC-2 Gigabit Network Connection [8086:294c] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at dffe0000 (32-bit, non-prefetchable) [size=128K]
    Memory at dffdf000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at eca0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at ecc0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02) (prog-if 20)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at dffdec00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: dbf00000-dbffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at ff80 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at ff60 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at ff40 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02) (prog-if 20)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: d0000000-dbefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801IR (ICH9R) LPC Interface Controller [8086:2916] (rev 02)
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
    I/O ports at fe00 [size=8]
    I/O ports at fe10 [size=4]
    I/O ports at fe20 [size=8]
    I/O ports at fe30 [size=4]
    I/O ports at fec0 [size=32]
    Memory at ff970000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
    Subsystem: Dell Device [1028:0215]
    Flags: medium devsel, IRQ 10
    Memory at dffdeb00 (64-bit, non-prefetchable) [size=256]
    I/O ports at ece0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 [GeForce 9400 GT] [10de:0641] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:c945]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at dc80 [size=128]
    Expansion ROM at dfe00000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

04:00.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
    Subsystem: Creative Labs Device [1102:0031]
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at cce0 [size=32]
    Memory at dbc00000 (64-bit, non-prefetchable) [size=2M]
    Memory at d0000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: SB-XFi
    Kernel modules: snd-ctxfi

04:04.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder [14f1:5b7a]
    Subsystem: Hauppauge computer works Inc. Device [0070:7444]
    Flags: bus master, medium devsel, latency 64, IRQ 16
    Memory at d4000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel modules: cx18

04:05.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
    Subsystem: Pinnacle Systems Inc. Device [11bd:0051]
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at d8000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800

04:05.1 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] [14f1:8801] (rev 05)
    Subsystem: Pinnacle Systems Inc. Device [11bd:0051]
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at d9000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88_audio
    Kernel modules: cx88-alsa

04:05.2 Multimedia controller [0480]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
    Subsystem: Pinnacle Systems Inc. Device [11bd:0051]
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at da000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx88-mpeg driver manager
    Kernel modules: cx8802

04:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023] (prog-if 10)
    Subsystem: Dell Device [1028:0215]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at dbefb800 (32-bit, non-prefetchable) [size=2K]
    Memory at dbefc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

```dmesg shows
```

[    2.064323] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.064389] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.064406]   alloc irq_desc for 22 on node -1
[    2.064408]   alloc kstat_irqs on node -1
[    2.064412] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.064419] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.064422] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.064451] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.064475] ehci_hcd 0000:00:1a.7: debug port 1
[    2.068349] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.068361] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xdffdec00
[    2.084527] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.084604] usb usb1: configuration #1 chosen from 1 choice
[    2.084628] hub 1-0:1.0: USB hub found
[    2.084634] hub 1-0:1.0: 6 ports detected
[    2.084682]   alloc irq_desc for 23 on node -1
[    2.084684]   alloc kstat_irqs on node -1
[    2.084688] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.084695] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.084698] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.084722] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.084742] ehci_hcd 0000:00:1d.7: debug port 1
[    2.088618] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.088630] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff980800
[    2.104527] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.104584] usb usb2: configuration #1 chosen from 1 choice
[    2.104606] hub 2-0:1.0: USB hub found
[    2.104611] hub 2-0:1.0: 6 ports detected
[    2.104661] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.104674] uhci_hcd: USB Universal Host Controller Interface driver
[    2.104689] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.104695] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.104698] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.104722] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.104749] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[    2.104822] usb usb3: configuration #1 chosen from 1 choice
[    2.104843] hub 3-0:1.0: USB hub found
[    2.104848] hub 3-0:1.0: 2 ports detected
[    2.104883]   alloc irq_desc for 17 on node -1
[    2.104885]   alloc kstat_irqs on node -1
[    2.104889] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.104894] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.104897] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.104921] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.104947] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
[    2.105020] usb usb4: configuration #1 chosen from 1 choice
[    2.105042] hub 4-0:1.0: USB hub found
[    2.105047] hub 4-0:1.0: 2 ports detected
[    2.105083] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.105088] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.105090] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.105114] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    2.105134] uhci_hcd 0000:00:1a.2: irq 22, io base 0x0000ecc0
[    2.105204] usb usb5: configuration #1 chosen from 1 choice
[    2.105225] hub 5-0:1.0: USB hub found
[    2.105230] hub 5-0:1.0: 2 ports detected
[    2.105264] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.105270] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.105272] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.105297] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.105317] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff80
[    2.105388] usb usb6: configuration #1 chosen from 1 choice
[    2.105408] hub 6-0:1.0: USB hub found
[    2.105414] hub 6-0:1.0: 2 ports detected
[    2.105447] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.105452] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.105455] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.105479] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.105499] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[    2.105575] usb usb7: configuration #1 chosen from 1 choice
[    2.105595] hub 7-0:1.0: USB hub found
[    2.105600] hub 7-0:1.0: 2 ports detected
[    2.105635]   alloc irq_desc for 18 on node -1
[    2.105636]   alloc kstat_irqs on node -1
[    2.105640] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.105645] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.105648] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.105673] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.105699] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    2.105767] usb usb8: configuration #1 chosen from 1 choice
[    2.105787] hub 8-0:1.0: USB hub found
[    2.105793] hub 8-0:1.0: 2 ports detected
[    2.105868] PNP: No PS/2 controller found. Probing ports directly.
[    2.108547] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.108552] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.108613] mice: PS/2 mouse device common for all mice
[    2.108695] rtc_cmos 00:05: RTC can wake from S4
[    2.108725] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.108746] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    2.108822] device-mapper: uevent: version 1.0.3
[    2.108909] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.109077] device-mapper: multipath: version 1.1.0 loaded
[    2.109079] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.109186] EISA: Probing bus 0 at eisa.0
[    2.109190] Cannot allocate resource for EISA slot 1
[    2.109208] EISA: Detected 0 cards.
[    2.109464] cpuidle: using governor ladder
[    2.109466] cpuidle: using governor menu
[    2.109837] TCP cubic registered
[    2.109963] NET: Registered protocol family 10
[    2.110373] lo: Disabled Privacy Extensions
[    2.110653] NET: Registered protocol family 17
[    2.110702] Using IPI No-Shortcut mode
[    2.110757] PM: Resume from disk failed.
[    2.110766] registered taskstats version 1
[    2.111153]   Magic number: 10:768:181
[    2.111199] rtc_cmos 00:05: setting system clock to 2010-05-09 14:11:03 UTC (1273414263)
[    2.111202] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.111204] EDD information not available.
[    2.396020] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.414049] isapnp: No Plug & Play device found
[    2.414083] Freeing unused kernel memory: 656k freed
[    2.414397] Write protecting the kernel text: 4676k
[    2.414433] Write protecting the kernel read-only data: 1840k
[    2.429111] udev: starting version 151
[    2.470298] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    2.470301] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.470349]   alloc irq_desc for 21 on node -1
[    2.470351]   alloc kstat_irqs on node -1
[    2.470360] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.470371] e1000e 0000:00:19.0: setting latency timer to 64
[    2.470450]   alloc irq_desc for 27 on node -1
[    2.470451]   alloc kstat_irqs on node -1
[    2.470460] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[    2.475953] ohci1394 0000:04:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.528997] usb 1-1: configuration #1 chosen from 1 choice
[    2.532583] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dbefb800-dbefbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.702460] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1d:09:27:83:35
[    2.702463] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.702485] 0000:00:19.0: eth0: MAC: 7, PHY: 6, PBA No: 1031ff-0ff
[    2.702513] ahci 0000:00:1f.2: version 3.0
[    2.702524]   alloc irq_desc for 20 on node -1
[    2.702527]   alloc kstat_irqs on node -1
[    2.702533] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    2.702563]   alloc irq_desc for 28 on node -1
[    2.702565]   alloc kstat_irqs on node -1
[    2.702573] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    2.702581] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
[    2.702648] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    2.702651] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pmp pio slum part ccc ems sxs 
[    2.702655] ahci 0000:00:1f.2: setting latency timer to 64
[    2.740077] scsi0 : ahci
[    2.740214] scsi1 : ahci
[    2.740287] scsi2 : ahci
[    2.740375] scsi3 : ahci
[    2.740457] scsi4 : ahci
[    2.740547] scsi5 : ahci
[    2.740600] ata1: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970100 irq 28
[    2.740604] ata2: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970180 irq 28
[    2.740607] ata3: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970200 irq 28
[    2.740611] ata4: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970280 irq 28
[    2.740614] ata5: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970300 irq 28
[    2.740618] ata6: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970380 irq 28
[    2.752023] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    2.887098] usb 1-6: configuration #128 chosen from 1 choice
[    3.060029] ata6: SATA link down (SStatus 4 SControl 300)
[    3.060055] ata1: SATA link down (SStatus 4 SControl 300)
[    3.120019] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    3.224027] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.224044] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.224056] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.224067] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.224693] ata2.00: ATAPI: HP DVD Writer 1270d, GH24, max UDMA/100, ATAPI AN
[    3.225124] ata5.00: ATA-8: ST31000528AS, CC37, max UDMA/133
[    3.225127] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.225764] ata2.00: configured for UDMA/100
[    3.226380] ata5.00: configured for UDMA/133
[    3.240994] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 1270d GH24 PQ: 0 ANSI: 5
[    3.247647] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.247651] Uniform CD-ROM driver Revision: 3.20
[    3.247784] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.247854] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    3.252572] ata4.00: ATA-8: ST31000333AS, SD35, max UDMA/133
[    3.252576] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.257612] ata3.00: ATA-8: WDC WD5000AAKS-75YGA0, 12.01C02, max UDMA/133
[    3.257616] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.258571] ata3.00: configured for UDMA/133
[    3.276120] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-7 12.0 PQ: 0 ANSI: 5
[    3.276279] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    3.276303] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.276323] sd 2:0:0:0: [sda] Write Protect is off
[    3.276325] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.276353] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.276477]  sda: sda1 sda2
[    3.278860] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.294333] ata4.00: configured for UDMA/133
[    3.308618] scsi 3:0:0:0: Direct-Access     ATA      ST31000333AS     SD35 PQ: 0 ANSI: 5
[    3.308749] sd 3:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.308772] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    3.308794] sd 3:0:0:0: [sdb] Write Protect is off
[    3.308796] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.308820] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.308882] scsi 4:0:0:0: Direct-Access     ATA      ST31000528AS     CC37 PQ: 0 ANSI: 5
[    3.308945]  sdb:
[    3.309013] sd 4:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.309051] sd 4:0:0:0: [sdc] Write Protect is off
[    3.309053] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.309075] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.309177]  sdc:
[    3.309239] sd 4:0:0:0: Attached scsi generic sg3 type 0
[    3.310830] usb 2-2: configuration #1 chosen from 1 choice
[    3.316808] Initializing USB Mass Storage driver...
[    3.316939] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.317020] usb-storage: device found at 3
[    3.317022] usb-storage: waiting for device to settle before scanning
[    3.317032] usbcore: registered new interface driver usb-storage
[    3.317035] USB Mass Storage support registered.
[    3.318008]  sdc1 sdc2 < sdb1
[    3.321630] sd 3:0:0:0: [sdb] Attached SCSI disk
[    3.338359]  sdc5 >
[    3.338636] sd 4:0:0:0: [sdc] Attached SCSI disk
[    3.420029] usb 2-4: new high speed USB device using ehci_hcd and address 4
[    3.519115] EXT4-fs (sdc1): INFO: recovery required on readonly filesystem
[    3.519119] EXT4-fs (sdc1): write access will be enabled during recovery
[    3.562477] usb 2-4: configuration #1 chosen from 1 choice
[    3.562722] scsi7 : SCSI emulation for USB Mass Storage devices
[    3.562799] usb-storage: device found at 4
[    3.562801] usb-storage: waiting for device to settle before scanning
[    3.800555] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    3.804429] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[8000000a751df0bf]
[    3.969989] usb 4-2: configuration #1 chosen from 1 choice
[    3.981719] usbcore: registered new interface driver hiddev
[    3.985168] input: Microsoft Microsoft® 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input3
[    3.985233] generic-usb 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® 2.4GHz Transceiver v6.0] on usb-0000:00:1a.1-2/input0
[    3.992495] input: Microsoft Microsoft® 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input4
[    3.992603] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® 2.4GHz Transceiver v6.0] on usb-0000:00:1a.1-2/input1
[    4.018124] input: Microsoft Microsoft® 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.2/input/input5
[    4.018250] generic-usb 0003:045E:0745.0003: input,hiddev96,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® 2.4GHz Transceiver v6.0] on usb-0000:00:1a.1-2/input2
[    4.018277] usbcore: registered new interface driver usbhid
[    4.018279] usbhid: v2.6:USB HID core driver
[    4.212087] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    4.391378] usb 6-1: configuration #1 chosen from 1 choice
[    4.394303] hub 6-1:1.0: USB hub found
[    4.396259] hub 6-1:1.0: 3 ports detected
[    4.677244] usb 6-1.2: new full speed USB device using uhci_hcd and address 3
[    4.829363] usb 6-1.2: configuration #1 chosen from 1 choice
[    4.840480] input: Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.2/6-1.2:1.0/input/input6
[    4.840541] generic-usb 0003:046D:C718.0004: input,hidraw3: USB HID v1.11 Keyboard [Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.2/input0
[    4.913238] usb 6-1.3: new full speed USB device using uhci_hcd and address 4
[    5.061309] usb 6-1.3: configuration #1 chosen from 1 choice
[    5.075766] input: Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.3/6-1.3:1.0/input/input7
[    5.075872] generic-usb 0003:046D:C719.0005: input,hiddev97,hidraw4: USB HID v1.11 Mouse [Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.3/input0
[    5.597831] EXT4-fs (sdc1): recovery complete
[    5.598260] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[    8.323489] usb-storage: device scan complete
[    8.327587] scsi 6:0:0:0: Direct-Access     DELL     USB   HS-CF Card 7.08 PQ: 0 ANSI: 0
[    8.331214] scsi 6:0:0:1: Direct-Access     DELL     USB   HS-xD/SM   7.08 PQ: 0 ANSI: 0
[    8.334955] scsi 6:0:0:2: Direct-Access     DELL     USB   HS-MS Card 7.08 PQ: 0 ANSI: 0
[    8.338083] scsi 6:0:0:3: Direct-Access     DELL     USB   HS-SD Card 7.08 PQ: 0 ANSI: 0
[    8.338510] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    8.338635] sd 6:0:0:1: Attached scsi generic sg5 type 0
[    8.338748] sd 6:0:0:2: Attached scsi generic sg6 type 0
[    8.338875] sd 6:0:0:3: Attached scsi generic sg7 type 0
[    8.360436] sd 6:0:0:1: [sde] Attached SCSI removable disk
[    8.364938] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[    8.369065] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[    8.373434] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[    8.560457] usb-storage: device scan complete
[    8.676822] scsi 7:0:0:0: Direct-Access     Generic  USB  SD Reader   1.00 PQ: 0 ANSI: 0 CCS
[    8.677227] sd 7:0:0:0: Attached scsi generic sg8 type 0
[    8.677803] sd 7:0:0:0: [sdh] 7741440 512-byte logical blocks: (3.96 GB/3.69 GiB)
[    8.678298] sd 7:0:0:0: [sdh] Write Protect is off
[    8.678301] sd 7:0:0:0: [sdh] Mode Sense: 4b 00 00 08
[    8.678305] sd 7:0:0:0: [sdh] Assuming drive cache: write through
[    8.680296] sd 7:0:0:0: [sdh] Assuming drive cache: write through
[    8.680300]  sdh: sdh1
[    8.682295] sd 7:0:0:0: [sdh] Assuming drive cache: write through
[    8.682299] sd 7:0:0:0: [sdh] Attached SCSI removable disk
[   11.391312] udev: starting version 151
[   11.401209] lp: driver loaded but no devices found
[   11.411557] EDAC MC: Ver: 2.1.0 Apr 28 2010
[   11.430139] Linux agpgart interface v0.103
[   11.513186] [drm] Initialized drm 1.1.0 20060810
[   11.528869] Linux video capture interface: v2.00
[   11.534311] EDAC MC0: Giving out device to 'x38_edac' 'x38': DEV 0000:00:00.0
[   11.542543] Adding 97655800k swap on /dev/sdc5.  Priority:-1 extents:1 across:97655800k 
[   11.544972] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x7711
[   11.545003] usbcore: registered new interface driver usblp
[   11.545745] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.546316] dell-wmi: No known WMI GUID found
[   11.568230] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   11.568559] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected], frontend(s): 1
[   11.568562] cx88[0]: TV tuner type 76, Radio tuner type -1
[   11.589737] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.589744] nouveau 0000:01:00.0: setting latency timer to 64
[   11.597139] cx18:  Start initialization, version 1.2.0
[   11.598246] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x096080c1)
[   11.598807] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   11.619743] cx2388x alsa driver version 0.0.7 loaded
[   11.648461] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   11.651644] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   11.651648] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   11.651650] [drm] nouveau 0000:01:00.0: Bios version 62.94.29.00
[   11.651653] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
[   11.651656] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[   11.651659] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[   11.651662] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   11.651665] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[   11.651667] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   11.651670] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   11.651672] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   11.651674] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000028
[   11.651677] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00020030
[   11.651680] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
[   11.651682] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02011312 00020030
[   11.651684] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 010223f1 00c0c080
[   11.651692] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xD0BE
[   11.663381] type=1505 audit(1273435873.049:2):  operation="profile_load" pid=623 name="/sbin/dhclient3"
[   11.663955] type=1505 audit(1273435873.049:3):  operation="profile_load" pid=623 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.664270] type=1505 audit(1273435873.049:4):  operation="profile_load" pid=623 name="/usr/lib/connman/scripts/dhclient-script"
[   11.701633] tuner 0-0064: chip found @ 0xc8 (cx88[0])
[   11.704661] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD4D3
[   11.724528] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE4C4
[   11.724537] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE60D
[   11.732613] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE849
[   11.732615] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE8AE
[   11.747199] xc5000 0-0064: creating new instance
[   11.748180] xc5000: Successfully identified at address 0x64
[   11.748181] xc5000: Firmware has not been loaded previously
[   11.748185] cx88[0]: Calling XC5000 callback
[   11.748273] input: cx88 IR (Pinnacle PCTV HD 800i) as /devices/pci0000:00/0000:00:1e.0/0000:04:05.2/input/input8
[   11.748350] cx88[0]/2: cx2388x 8802 Driver Manager
[   11.748364] cx88-mpeg driver manager 0000:04:05.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.748372] cx88[0]/2: found at 0000:04:05.2, rev: 5, irq: 17, latency: 64, mmio: 0xda000000
[   11.748377] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.748431] cx18-0: Initializing card 0
[   11.748436] cx18-0: Autodetected Hauppauge card
[   11.749704] cx18 0000:04:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.750421] vmap allocation for size 67112960 failed: use vmalloc=<size> to increase size.
[   11.750916] cx18-0: ioremap failed, perhaps increasing __VMALLOC_RESERVE in page.h
[   11.750959] cx18-0: or disabling CONFIG_HIGHMEM4G into the kernel would help
[   11.753904] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   11.753906] cx88/2: registering cx8802 driver, type: dvb access: shared
[   11.753910] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   11.753912] cx88[0]/2: cx2388x based DVB/ATSC card
[   11.753914] cx8802_alloc_frontends() allocating 1 frontend(s)
[   11.754029] cx18-0: Error -12 on initialization
[   11.754076] cx18: probe of 0000:04:04.0 failed with error -12
[   11.754103] cx18:  End initialization
[   11.754214] cx88_audio 0000:04:05.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.754221] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.754242] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   11.754582] SB-XFi 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.756567] [drm] nouveau 0000:01:00.0: 0xE8AE: Condition still not met after 20ms, skipping following opcodes
[   11.756576] [drm] nouveau 0000:01:00.0: 0xC090: parsing output script 0
[   11.756582] [drm] nouveau 0000:01:00.0: 0xC090: parsing output script 0
[   11.756588] [drm] nouveau 0000:01:00.0: 0xAB1C: parsing output script 0
[   11.810035] xc5000 0-0064: attaching existing instance
[   11.811173] xc5000: Successfully identified at address 0x64
[   11.811175] xc5000: Firmware has not been loaded previously
[   11.812697] DVB: registering new adapter (cx88[0])
[   11.812700] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   11.874254] [TTM] Zone  kernel: Available graphics memory: 430106 kiB.
[   11.874257] [TTM] Zone highmem: Available graphics memory: 1547460 kiB.
[   11.874265] [drm] nouveau 0000:01:00.0: 1024 MiB VRAM
[   11.890700] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[   11.890724] mtrr: type mismatch for c0000000,10000000 old: write-back new: write-combining
[   11.890905] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   11.894902] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   11.895372] [drm] nouveau 0000:01:00.0: Detected a DAC output
[   11.895375] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[   11.895378] [drm] nouveau 0000:01:00.0: Detected a DAC output
[   11.895380] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[   11.895383] [drm] nouveau 0000:01:00.0: DCB encoder 1 unknown
[   11.895385] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   11.895435] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[   12.082202] cx8800 0000:04:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.082211] cx88[0]/0: found at 0000:04:05.0, rev: 5, irq: 17, latency: 64, mmio: 0xd8000000
[   12.082220] IRQ 17/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.082271] cx88[0]/0: registered device video0 [v4l2]
[   12.082299] cx88[0]/0: registered device vbi0
[   12.084988] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   12.084992] cx88-mpeg driver manager 0000:04:05.2: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[   12.106684] xc5000: firmware read 12401 bytes.
[   12.106686] xc5000: firmware uploading...
[   12.106688] cx88[0]: Calling XC5000 callback
[   12.119196] [drm] nouveau 0000:01:00.0: allocated 1360x1024 fb: 0x40250000, bo ef1b0000
[   12.119281] fb0: nouveaufb frame buffer device
[   12.119283] registered panic notifier
[   12.119288] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[   12.121101] vga16fb: initializing
[   12.121104] vga16fb: mapped to 0xc00a0000
[   12.121106] vga16fb: not registering due to another framebuffer present
[   12.130715] Console: switching to colour frame buffer device 160x48
[   12.136098] [drm] nouveau 0000:01:00.0: 0x11F1: parsing clock script 0
[   12.153454] [drm] nouveau 0000:01:00.0: 0x11F1: parsing clock script 0
[   12.275399] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   12.333962] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   12.334206] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.861897] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
[   12.867846] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
[   13.685657] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   13.685661] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   13.685850] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.120275] xc5000: firmware upload complete...
[   14.746564] cx88[0]: Calling XC5000 callback
[   16.903414] CPU0 attaching NULL sched-domain.
[   16.903420] CPU1 attaching NULL sched-domain.
[   16.903423] CPU2 attaching NULL sched-domain.
[   16.903425] CPU3 attaching NULL sched-domain.
[   16.920884] CPU0 attaching sched-domain:
[   16.920888]  domain 0: span 0-1 level MC
[   16.920890]   groups: 0 1
[   16.920894]   domain 1: span 0-3 level CPU
[   16.920896]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[   16.920904] CPU1 attaching sched-domain:
[   16.920905]  domain 0: span 0-1 level MC
[   16.920907]   groups: 1 0
[   16.920911]   domain 1: span 0-3 level CPU
[   16.920913]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[   16.920918] CPU2 attaching sched-domain:
[   16.920920]  domain 0: span 2-3 level MC
[   16.920922]   groups: 2 3
[   16.920925]   domain 1: span 0-3 level CPU
[   16.920927]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[   16.920932] CPU3 attaching sched-domain:
[   16.920934]  domain 0: span 2-3 level MC
[   16.920936]   groups: 3 2
[   16.920939]   domain 1: span 0-3 level CPU
[   16.920941]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[   21.890666] ISO 9660 Extensions: Microsoft Joliet Level 3
[   22.035596] ISO 9660 Extensions: RRIP_1991A
[   23.852136] eth0: no IPv6 routers present

```

---

### Post by xc3RnbFO8P on 2010-05-09
Can you remove the Haupauge card and do **dmesg** again and try TVtime?
You got a Pinnacle PCTV HD Card (800i) in your computer, no need for two TV cards.

---

### Post by WinterRain on 2010-05-09
Unless your tuner card is supported "out of the box", it can be an exercise in futility to get it to work.

[Here's]("http://www.linuxtv.org/wiki/index.php/Cx88_devices_(cx2388x)") some info if you want some info on getting it to work. But realize it will *not* be newb friendly. Good luck.

---

### Post by xc3RnbFO8P on 2010-05-09
Pinnacle PCTV HD Card (800i) is supported, analog and digital.
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29")

---

### Post by neslot35 on 2010-05-09
> **Ringi said:**
> Pinnacle PCTV HD Card (800i) is supported, analog and digital.
[http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

Thanks :)  Is there a way to disable the hauppage card in Ubuntu without removing it?  I use both in windows to record tv and watch a different channel.  Would be a real pain to have to keep installing and removing it.

---

### Post by xc3RnbFO8P on 2010-05-10
First try in Terminal:
> tvtime --device /dev/video0
> tvtime --device /dev/video1
show the output.

---

