---
title: "no wireless networks show up...drivers are installed"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by ParkerH19 on 2010-12-14
Hi, I just got the broadcom restricted drivers installed by using wired tether with my phone, but after installing and rebooting, I can't find an option to view wireless networks. In past experience it has popped up instantly.

Any help is greatly appreciated. 

PS: I am on a mac mini late 2009

---

### Post by Elaztic on 2010-12-14
Well....think you have to provide a bit more information but let's try the easy ones first.

Start Network Manager (either from applications menu or terminal with [FONT="Courier New"]nm-applet[/FONT]) and see if the icon shows in the tray.
If that works alright then just make sure it starts up (startup menu).
If not, then post the output of these commands:
[FONT="Courier New"]lspci
dmesg[/FONT]

and if you have it installed
[FONT="Courier New"]hwinfo[/FONT]

---

### Post by ParkerH19 on 2010-12-14
> **Elaztic said:**
> Well....think you have to provide a bit more information but let's try the easy ones first.

Start Network Manager (either from applications menu or terminal with [FONT=Courier New]nm-applet[/FONT]) and see if the icon shows in the tray.
If that works alright then just make sure it starts up (startup menu).
If not, then post the output of these commands:
[FONT=Courier New]lspci
dmesg[/FONT]

and if you have it installed
[FONT=Courier New]hwinfo[/FONT]


thanks for the quick response. I can't find Network Manager in the applications menu, and when I run nm-applet, I get the following error: ```
An instance of nm-applet is already running.

** (nm-applet:1820): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```

So I think I have network manager at the top, but it only shows wired connections. 

output of lspci: ```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400] (rev b1)
03:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05)
04:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)

```

output of dmesg: ```
[    0.261995] PCI: Using ACPI for IRQ routing
[    0.261998] PCI: pci_cache_line_size set to 64 bytes
[    0.262489] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.262491] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.262493] reserve RAM buffer: 00000000ae64f000 - 00000000afffffff 
[    0.262577] NetLabel: Initializing
[    0.262579] NetLabel:  domain hash size = 128
[    0.262580] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.262591] NetLabel:  unlabeled traffic allowed by default
[    0.262617] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.262624] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
[    0.262629] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
[    0.272024] Switching to clocksource tsc
[    0.281335] AppArmor: AppArmor Filesystem Enabled
[    0.281351] pnp: PnP ACPI init
[    0.281369] ACPI: bus type pnp registered
[    0.284303] pnp: PnP ACPI: found 8 devices
[    0.284305] ACPI: ACPI bus type pnp unregistered
[    0.284309] PnPBIOS: Disabled by ACPI PNP
[    0.284320] system 00:01: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.284326] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.284331] system 00:06: [io  0x0400-0x047f] has been reserved
[    0.284334] system 00:06: [io  0x0480-0x04ff] has been reserved
[    0.284336] system 00:06: [io  0x0500-0x057f] has been reserved
[    0.284338] system 00:06: [io  0x0580-0x05ff] has been reserved
[    0.284340] system 00:06: [io  0x0800-0x087f] has been reserved
[    0.284342] system 00:06: [io  0x0880-0x08ff] has been reserved
[    0.284345] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.284348] system 00:06: [io  0x0295-0x0296] has been reserved
[    0.320165] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    0.320169] pci 0000:00:09.0:   bridge window [io  disabled]
[    0.320174] pci 0000:00:09.0:   bridge window [mem 0xd3300000-0xd33fffff]
[    0.320177] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    0.320182] pci 0000:00:10.0: PCI bridge to [bus 02-02]
[    0.320184] pci 0000:00:10.0:   bridge window [io  0x1000-0x1fff]
[    0.320188] pci 0000:00:10.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    0.320191] pci 0000:00:10.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.320195] pci 0000:00:15.0: PCI bridge to [bus 03-03]
[    0.320196] pci 0000:00:15.0:   bridge window [io  disabled]
[    0.320206] pci 0000:00:15.0:   bridge window [mem 0xd3200000-0xd32fffff]
[    0.320213] pci 0000:00:15.0:   bridge window [mem pref disabled]
[    0.320226] pci 0000:00:16.0: PCI bridge to [bus 04-04]
[    0.320228] pci 0000:00:16.0:   bridge window [io  disabled]
[    0.320238] pci 0000:00:16.0:   bridge window [mem 0xd3100000-0xd31fffff]
[    0.320245] pci 0000:00:16.0:   bridge window [mem pref disabled]
[    0.320260] pci 0000:00:09.0: enabling device (0000 -> 0002)
[    0.320266] pci 0000:00:09.0: setting latency timer to 64
[    0.320275] pci 0000:00:10.0: setting latency timer to 64
[    0.320649] ACPI: PCI Interrupt Link [Z00F] enabled at IRQ 23
[    0.320654]   alloc irq_desc for 23 on node -1
[    0.320656]   alloc kstat_irqs on node -1
[    0.320663] pci 0000:00:15.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[    0.320671] pci 0000:00:15.0: setting latency timer to 64
[    0.321001] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 22
[    0.321003]   alloc irq_desc for 22 on node -1
[    0.321005]   alloc kstat_irqs on node -1
[    0.321009] pci 0000:00:16.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[    0.321017] pci 0000:00:16.0: setting latency timer to 64
[    0.321024] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.321026] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.321028] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.321030] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.321032] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.321034] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.321036] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.321038] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.321039] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.321041] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.321043] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.321045] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.321047] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.321049] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.321051] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.321053] pci_bus 0000:00: resource 19 [mem 0xc0000000-0xfebfffff]
[    0.321055] pci_bus 0000:01: resource 1 [mem 0xd3300000-0xd33fffff]
[    0.321057] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.321059] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.321061] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.321063] pci_bus 0000:01: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.321065] pci_bus 0000:01: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.321067] pci_bus 0000:01: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.321069] pci_bus 0000:01: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.321071] pci_bus 0000:01: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.321073] pci_bus 0000:01: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.321075] pci_bus 0000:01: resource 13 [mem 0x000dc000-0x000dffff]
[    0.321077] pci_bus 0000:01: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.321079] pci_bus 0000:01: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.321080] pci_bus 0000:01: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.321082] pci_bus 0000:01: resource 17 [mem 0x000ec000-0x000effff]
[    0.321084] pci_bus 0000:01: resource 18 [mem 0x000f0000-0x000fffff]
[    0.321087] pci_bus 0000:01: resource 19 [mem 0xc0000000-0xfebfffff]
[    0.321089] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.321091] pci_bus 0000:02: resource 1 [mem 0xd2000000-0xd30fffff]
[    0.321093] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.321095] pci_bus 0000:03: resource 1 [mem 0xd3200000-0xd32fffff]
[    0.321097] pci_bus 0000:04: resource 1 [mem 0xd3100000-0xd31fffff]
[    0.321133] NET: Registered protocol family 2
[    0.321193] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.321419] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.321882] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.322090] TCP: Hash tables configured (established 131072 bind 65536)
[    0.322092] TCP reno registered
[    0.322095] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.322105] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.322175] NET: Registered protocol family 1
[    0.335944] pci 0000:02:00.0: Boot video device
[    0.336146] PCI: CLS 256 bytes, default 64
[    0.336325] cpufreq-nforce2: No nForce2 chipset.
[    0.336350] Scanning for low memory corruption every 60 seconds
[    0.336484] audit: initializing netlink socket (disabled)
[    0.336495] type=2000 audit(1292369903.332:1): initialized
[    0.345305] highmem bounce pool size: 64 pages
[    0.345310] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.346559] VFS: Disk quotas dquot_6.5.2
[    0.346618] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.347114] fuse init (API version 7.14)
[    0.347187] msgmni has been set to 1664
[    0.347570] modprobe[41]: segfault at 4 ip 00f637b6 sp bfd02878 error 4 in ld-linux.so.2[f54000+1c000]
[    0.347818] modprobe[43]: segfault at 4 ip 004a57b6 sp bffddcf8 error 4 in ld-linux.so.2[496000+1c000]
[    0.347894] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.347897] io scheduler noop registered
[    0.347899] io scheduler deadline registered
[    0.347910] io scheduler cfq registered (default)
[    0.348028] pcieport 0000:00:15.0: setting latency timer to 64
[    0.348141]   alloc irq_desc for 40 on node -1
[    0.348143]   alloc kstat_irqs on node -1
[    0.348162] pcieport 0000:00:15.0: irq 40 for MSI/MSI-X
[    0.348311] pcieport 0000:00:16.0: setting latency timer to 64
[    0.348421]   alloc irq_desc for 41 on node -1
[    0.348423]   alloc kstat_irqs on node -1
[    0.348439] pcieport 0000:00:16.0: irq 41 for MSI/MSI-X
[    0.348586] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.348604] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.348679] intel_idle: MWAIT substates: 0x3122220
[    0.348681] intel_idle: does not run on family 6 model 23
[    0.348770] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.348775] ACPI: Power Button [PWRB]
[    0.348814] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.348817] ACPI: Sleep Button [SLPB]
[    0.348870] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.348873] ACPI: Power Button [PWRF]
[    0.349280] ACPI: acpi_idle registered with cpuidle
[    0.349706] Monitor-Mwait will be used to enter C-1 state
[    0.351983] Monitor-Mwait will be used to enter C-2 state
[    0.352001] Monitor-Mwait will be used to enter C-3 state
[    0.352006] Marking TSC unstable due to TSC halts in idle
[    0.355994] ERST: Table is not found!
[    0.356239] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.357470] brd: module loaded
[    0.357922] loop: module loaded
[    0.358424] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 21
[    0.358429]   alloc irq_desc for 21 on node -1
[    0.358430]   alloc kstat_irqs on node -1
[    0.358436] pata_acpi 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 21 (level, low) -> IRQ 21
[    0.358462] pata_acpi 0000:00:0b.0: setting latency timer to 64
[    0.358470] pata_acpi 0000:00:0b.0: PCI INT A disabled
[    0.358727] Fixed MDIO Bus: probed
[    0.358755] PPP generic driver version 2.4.2
[    0.358784] tun: Universal TUN/TAP device driver, 1.6
[    0.358786] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.358855] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.359187] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[    0.359189]   alloc irq_desc for 20 on node -1
[    0.359191]   alloc kstat_irqs on node -1
[    0.359195] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 20 (level, low) -> IRQ 20
[    0.359205] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.359207] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.359236] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.359256] ehci_hcd 0000:00:04.1: debug port 1
[    0.359264] ehci_hcd 0000:00:04.1: cache line size of 256 is not supported
[    0.359280] ehci_hcd 0000:00:04.1: irq 20, io mem 0xd3489200
[    0.359300] Switching to clocksource hpet
[    0.359500] isapnp: Scanning for PnP cards...
[    0.374534] Freeing initrd memory: 10512k freed
[    0.408027] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.408208] hub 1-0:1.0: USB hub found
[    0.408212] hub 1-0:1.0: 7 ports detected
[    0.408654] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 19
[    0.408660]   alloc irq_desc for 19 on node -1
[    0.408661]   alloc kstat_irqs on node -1
[    0.408669] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 19 (level, low) -> IRQ 19
[    0.408689] ehci_hcd 0000:00:06.1: setting latency timer to 64
[    0.408692] ehci_hcd 0000:00:06.1: EHCI Host Controller
[    0.408725] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
[    0.408745] ehci_hcd 0000:00:06.1: debug port 1
[    0.408753] ehci_hcd 0000:00:06.1: cache line size of 256 is not supported
[    0.408772] ehci_hcd 0000:00:06.1: irq 19, io mem 0xd3489100
[    0.420013] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
[    0.420107] hub 2-0:1.0: USB hub found
[    0.420110] hub 2-0:1.0: 5 ports detected
[    0.420170] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.420502] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    0.420505]   alloc irq_desc for 18 on node -1
[    0.420506]   alloc kstat_irqs on node -1
[    0.420510] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    0.420519] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.420522] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.420551] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    0.420570] ohci_hcd 0000:00:04.0: irq 18, io mem 0xd3488000
[    0.478077] hub 3-0:1.0: USB hub found
[    0.478081] hub 3-0:1.0: 7 ports detected
[    0.478458] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 17
[    0.478460]   alloc irq_desc for 17 on node -1
[    0.478462]   alloc kstat_irqs on node -1
[    0.478466] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 17 (level, low) -> IRQ 17
[    0.478474] ohci_hcd 0000:00:06.0: setting latency timer to 64
[    0.478476] ohci_hcd 0000:00:06.0: OHCI Host Controller
[    0.478505] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
[    0.478523] ohci_hcd 0000:00:06.0: irq 17, io mem 0xd3487000
[    0.534076] hub 4-0:1.0: USB hub found
[    0.534081] hub 4-0:1.0: 5 ports detected
[    0.534136] uhci_hcd: USB Universal Host Controller Interface driver
[    0.534222] PNP: No PS/2 controller found. Probing ports directly.
[    0.535092] i8042.c: No controller found.
[    0.535146] mice: PS/2 mouse device common for all mice
[    0.535262] rtc_cmos 00:07: RTC can wake from S4
[    0.535295] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.535342] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.535431] device-mapper: uevent: version 1.0.3
[    0.535530] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.535589] device-mapper: multipath: version 1.1.1 loaded
[    0.535592] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.535687] EISA: Probing bus 0 at eisa.0
[    0.535689] EISA: Cannot allocate resource for mainboard
[    0.535691] Cannot allocate resource for EISA slot 1
[    0.535693] Cannot allocate resource for EISA slot 2
[    0.535695] Cannot allocate resource for EISA slot 3
[    0.535696] Cannot allocate resource for EISA slot 4
[    0.535698] Cannot allocate resource for EISA slot 5
[    0.535700] Cannot allocate resource for EISA slot 6
[    0.535701] Cannot allocate resource for EISA slot 7
[    0.535703] Cannot allocate resource for EISA slot 8
[    0.535704] EISA: Detected 0 cards.
[    0.535821] cpuidle: using governor ladder
[    0.535908] cpuidle: using governor menu
[    0.536194] TCP cubic registered
[    0.536304] NET: Registered protocol family 10
[    0.536614] lo: Disabled Privacy Extensions
[    0.536813] NET: Registered protocol family 17
[    0.537439] Using IPI No-Shortcut mode
[    0.537501] PM: Resume from disk failed.
[    0.537512] registered taskstats version 1
[    0.537982]   Magic number: 6:112:656
[    0.538101] rtc_cmos 00:07: setting system clock to 2010-12-14 23:38:24 UTC (1292369904)
[    0.538104] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.538105] EDD information not available.
[    0.712290] isapnp: No Plug & Play device found
[    0.712318] Freeing unused kernel memory: 684k freed
[    0.712698] Write protecting the kernel text: 4932k
[    0.712745] Write protecting the kernel read-only data: 1976k
[    0.724027] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.726610] udev[82]: starting version 163
[    0.789858] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.790235] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 16
[    0.790241]   alloc irq_desc for 16 on node -1
[    0.790243]   alloc kstat_irqs on node -1
[    0.790250] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 16 (level, low) -> IRQ 16
[    0.790254] forcedeth 0000:00:0a.0: setting latency timer to 64
[    0.809000] firewire_ohci 0000:04:00.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
[    0.809008] firewire_ohci 0000:04:00.0: setting latency timer to 64
[    0.820243] b43-pci-bridge 0000:03:00.0: power state changed by ACPI to D0
[    0.820514] b43-pci-bridge 0000:03:00.0: power state changed by ACPI to D0
[    0.820718] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
[    0.820726] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    0.837310] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x13, vendor 0x4243)
[    0.837318] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0C, vendor 0x4243)
[    0.837324] ssb: Core 2 found: PCI-E (cc 0x820, rev 0x08, vendor 0x4243)
[    0.837330] ssb: Core 3 found: PCI (cc 0x804, rev 0x0D, vendor 0x4243)
[    0.837336] ssb: Core 4 found: USB 1.1 Host (cc 0x817, rev 0x04, vendor 0x4243)
[    0.854390] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:26:b0:de:b6:8e
[    0.854394] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
[    0.854425] ahci 0000:00:0b.0: version 3.0
[    0.854439] ahci 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 21 (level, low) -> IRQ 21
[    0.854480]   alloc irq_desc for 42 on node -1
[    0.854482]   alloc kstat_irqs on node -1
[    0.854490] ahci 0000:00:0b.0: irq 42 for MSI/MSI-X
[    0.854496] ahci 0000:00:0b.0: controller can't do PMP, turning off CAP_PMP
[    0.854553] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl IDE mode
[    0.854556] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pio slum part boh 
[    0.854560] ahci 0000:00:0b.0: setting latency timer to 64
[    0.854719] scsi0 : ahci
[    0.854823] scsi1 : ahci
[    0.854987] scsi2 : ahci
[    0.855044] scsi3 : ahci
[    0.855103] scsi4 : ahci
[    0.855166] scsi5 : ahci
[    0.855336] ata1: SATA max UDMA/133 abar m8192@0xd3484000 port 0xd3484100 irq 42
[    0.855339] ata2: SATA max UDMA/133 abar m8192@0xd3484000 port 0xd3484180 irq 42
[    0.855341] ata3: DUMMY
[    0.855342] ata4: DUMMY
[    0.855344] ata5: DUMMY
[    0.855345] ata6: DUMMY
[    0.885333] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    0.948099] firewire_ohci: Added fw-ohci device 0000:04:00.0, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x0
[    0.988101] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.140893] Initializing USB Mass Storage driver...
[    1.140972] scsi6 : usb-storage 1-3:1.2
[    1.141042] usbcore: registered new interface driver usb-storage
[    1.141043] USB Mass Storage support registered.
[    1.172096] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.172112] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.173095] ata1.00: ATA-8: Hitachi HTS543232L9SA02, FB4AC52F, max UDMA/133
[    1.173100] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.174315] ata1.00: configured for UDMA/133
[    1.182605] ata2.00: ATAPI: PIONEER DVD-RW  DVRTS08, Q81F, max UDMA/33
[    1.188283] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 FB4A PQ: 0 ANSI: 5
[    1.188405] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.188476] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.188518] sd 0:0:0:0: [sda] Write Protect is off
[    1.188520] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.188538] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.188654]  sda:
[    1.195515] ata2.00: configured for UDMA/33
[    1.252103]  sda1 sda2 sda3 sda4
[    1.252431] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.264259] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVRTS08  Q81F PQ: 0 ANSI: 5
[    1.388214] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
[    1.388218] Uniform CD-ROM driver Revision: 3.20
[    1.388332] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.388383] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.440192] firewire_core: created device fw0: GUID 0026b0fffedeb68e, S800
[    1.720031] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    1.945073] hub 4-1:1.0: USB hub found
[    1.948051] hub 4-1:1.0: 3 ports detected
[    2.039282] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    2.143855] scsi 6:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[    2.144363] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.161210] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.264094] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    2.788095] usb 3-7: new full speed USB device using ohci_hcd and address 3
[    3.004077] hub 3-7:1.0: USB hub found
[    3.007033] hub 3-7:1.0: 4 ports detected
[    3.102104] usb 4-1.1: new full speed USB device using ohci_hcd and address 3
[    3.322048] usb 3-7.1: new low speed USB device using ohci_hcd and address 4
[    3.514038] usb 3-7.2: new full speed USB device using ohci_hcd and address 5
[    3.722035] usb 3-7.4: new full speed USB device using ohci_hcd and address 6
[   14.212067] udev[401]: starting version 163
[   14.288645] Adding 3999740k swap on /dev/sda4.  Priority:-1 extents:1 across:3999740k 
[   14.344021] WARNING! power/level is deprecated; use power/control instead
[   14.376850] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.377052] i2c i2c-0: nForce2 SMBus adapter at 0x2140
[   14.377076] i2c i2c-1: nForce2 SMBus adapter at 0x2100
[   14.378119] Linux agpgart interface v0.103
[   14.403894] applesmc: Apple Macmini detected:
[   14.403897] applesmc:  - Model without accelerometer
[   14.403899] applesmc:  - Model without light sensors and backlight
[   14.403901] applesmc:  - Model with 2 temperature sensors
[   14.403987] applesmc: device successfully initialized.
[   14.404522] applesmc: 1 fans found.
[   14.413370] applesmc: driver successfully loaded.
[   14.460105] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0847
[   14.460135] usbcore: registered new interface driver usblp
[   14.464630] lp: driver loaded but no devices found
[   14.472637] type=1400 audit(1292369918.429:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=604 comm="apparmor_parser"
[   14.473257] type=1400 audit(1292369918.433:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=604 comm="apparmor_parser"
[   14.473572] type=1400 audit(1292369918.433:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=604 comm="apparmor_parser"
[   14.480186] cfg80211: Calling CRDA to update world regulatory domain
[   14.507932] usbcore: registered new interface driver hiddev
[   14.508710] Bluetooth: Core ver 2.15
[   14.508747] NET: Registered protocol family 31
[   14.508749] Bluetooth: HCI device and connection manager initialized
[   14.508751] Bluetooth: HCI socket layer initialized
[   14.540979] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.1/3-7.1:1.0/input/input3
[   14.541088] generic-usb 0003:046D:C221.0002: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech Gaming Keyboard] on usb-0000:00:04.0-7.1/input0
[   14.541269] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   14.554085] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.1/3-7.1:1.1/input/input4
[   14.554193] generic-usb 0003:046D:C221.0003: input,hiddev96,hidraw1: USB HID v1.10 Device [Logitech Logitech Gaming Keyboard] on usb-0000:00:04.0-7.1/input1
[   14.561629] usbcore: registered new interface driver btusb
[   14.561641] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.2/3-7.2:1.0/input/input5
[   14.561736] generic-usb 0003:046D:C041.0004: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:04.0-7.2/input0
[   14.567476] apple 0003:05AC:8242.0001: hiddev97,hidraw3: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
[   14.570825] cfg80211: World regulatory domain updated:
[   14.570828]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.570831]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.570833]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.570835]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.570838]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.570840]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.573124] generic-usb 0003:046D:C041.0005: hiddev98,hidraw4: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:04.0-7.2/input1
[   14.582328] input: G15 Keyboard G15 Keyboard as /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.4/3-7.4:1.0/input/input6
[   14.582442] generic-usb 0003:046D:C222.0006: input,hiddev99,hidraw5: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:04.0-7.4/input0
[   14.582462] usbcore: registered new interface driver usbhid
[   14.582464] usbhid: USB HID core driver
[   14.599905] b43-phy0: Broadcom 4321 WLAN found (core revision 12)
[   14.644217] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 2)
[   14.644523] b43: probe of ssb0:0 failed with error -95
[   14.644543] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   14.660882] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[   14.660887] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 23 (level, low) -> IRQ 23
[   14.660890] hda_intel: Disable MSI for Nvidia chipset
[   14.660927] HDA Intel 0000:00:08.0: setting latency timer to 64
[   14.701570] usbcore: registered new interface driver cdc_ether
[   14.726227] rndis_host 1-1:1.0: usb0: register 'rndis_host' at usb-0000:00:04.1-1, RNDIS device, 26:7f:a7:3d:54:6c
[   14.726278] usbcore: registered new interface driver rndis_host
[   15.000062] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   15.272718] hda_codec: ALC889A: SKU not ready 0x400000f0
[   15.794881] nvidia: module license 'NVIDIA' taints kernel.
[   15.794888] Disabling lock debugging due to kernel taint
[   16.691317] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 22
[   16.691323] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 22 (level, low) -> IRQ 22
[   16.691330] nvidia: probe of 0000:00:03.5 failed with error -1
[   16.691662] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 21
[   16.691665] nvidia 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 21 (level, low) -> IRQ 21
[   16.691671] nvidia 0000:02:00.0: setting latency timer to 64
[   16.691675] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.691811] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   17.131454] ppdev: user-space parallel port driver
[   17.139512] type=1400 audit(1292369921.097:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=990 comm="apparmor_parser"
[   17.140091] type=1400 audit(1292369921.101:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=990 comm="apparmor_parser"
[   17.140119] type=1400 audit(1292369921.101:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=989 comm="apparmor_parser"
[   17.140406] type=1400 audit(1292369921.101:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=990 comm="apparmor_parser"
[   17.146128] type=1400 audit(1292369921.105:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1060 comm="apparmor_parser"
[   17.146490] type=1400 audit(1292369921.105:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1058 comm="apparmor_parser"
[   17.146839] type=1400 audit(1292369921.105:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1060 comm="apparmor_parser"
[   17.269786] Bluetooth: L2CAP ver 2.14
[   17.269788] Bluetooth: L2CAP socket layer initialized
[   17.275635] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.275638] Bluetooth: BNEP filters: protocol multicast
[   17.282096] Bluetooth: SCO (Voice Link) ver 0.6
[   17.282099] Bluetooth: SCO socket layer initialized
[   17.336666]   alloc irq_desc for 43 on node -1
[   17.336669]   alloc kstat_irqs on node -1
[   17.336678] forcedeth 0000:00:0a.0: irq 43 for MSI/MSI-X
[   17.336873] eth0: no link during initialization.
[   17.337439] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.396664] Bluetooth: RFCOMM TTY layer initialized
[   17.396669] Bluetooth: RFCOMM socket layer initialized
[   17.396671] Bluetooth: RFCOMM ver 1.11
[   18.736810] usb 1-3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   20.257606] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   23.665164] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   27.496046] usb0: no IPv6 routers present

```

hwinfo: ```
  Device Files: /dev/sda4, /dev/block/8:4, /dev/disk/by-id/ata-Hitachi_HTS543232L9SA02_090825FBE400CEHG5ASF-part4, /dev/disk/by-id/scsi-SATA_Hitachi_HTS5432090825FBE400CEHG5ASF-part4, /dev/disk/by-path/pci-0000:00:0b.0-scsi-0:0:0:0-part4, /dev/disk/by-uuid/f97deba3-fdaa-40d2-a57a-11b0bd7b4391, /dev/disk/by-id/wwn-0x5000cca5c3d488c5-part4
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #41 (Disk)

46: SCSI 100.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  Unique ID: KD9E.oquPvZNxql1
  Parent ID: gZD2.ZHZfVm+4gKA
  SysFS ID: /class/block/sr0
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:0b.0/host1/target1:0:0/1:0:0:0
  Hardware Class: cdrom
  Model: "PIONEER DVD-RW  DVRTS08"
  Vendor: "PIONEER"
  Device: "DVD-RW  DVRTS08"
  Revision: "Q81F"
  Driver: "ahci", "sr"
  Driver Modules: "ahci"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/block/11:0, /dev/scd0, /dev/disk/by-path/pci-0000:00:0b.0-scsi-1:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:1)
  Features: DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (IDE interface)
  Drive Speed: 24

47: SCSI 600.0: 10600 Disk
  [Created at block.254]
  Unique ID: yqzE.ugFg5rd_DmD
  Parent ID: +6Nb.SsnWKDZ4ks6
  SysFS ID: /class/block/sdb
  SysFS BusID: 6:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:04.1/usb1/1-3/1-3:1.2/host6/target6:0:0/6:0:0:0
  Hardware Class: disk
  Model: "EPSON Stylus Storage"
  Vendor: usb 0x04b8 "EPSON"
  Device: usb 0x0847 "Stylus Storage"
  Revision: "1.00"
  Serial ID: "4B584C593133393654"
  Driver: "usb-storage", "sd"
  Driver Modules: "usb_storage"
  Device File: /dev/sdb (/dev/sg2)
  Device Files: /dev/sdb, /dev/block/8:16, /dev/disk/by-id/usb-EPSON_Stylus_Storage_4B584C593133393654-0:0, /dev/disk/by-path/pci-0000:00:04.1-usb-0:3:1.2-scsi-0:0:0:0
  Device Number: block 8:16-8:31 (char 21:2)
  Speed: 480 Mbps
  Module Alias: "usb:v04B8p0847d0100dc00dsc00dp00ic08isc06ip50"
  Driver Info #0:
    Driver Status: usb_storage is active
    Driver Activation Cmd: "modprobe usb_storage"
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

48: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: k4bc.QtYiGM_hXFF
  Parent ID: +6Nb.SsnWKDZ4ks6
  SysFS ID: /devices/pci0000:00/0000:00:04.1/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-22-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-22-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:04.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)

49: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: pBe4.Sw8nI9PExT4
  Parent ID: 9LTX.+5dmmwvBJ08
  SysFS ID: /devices/pci0000:00/0000:00:06.1/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-22-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-22-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:06.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (USB Controller)

50: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: uIhY.moLwSePIflE
  Parent ID: 8otl.hR2hi8aDaK0
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-22-generic ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-22-generic ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:04.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (USB Controller)

51: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: zPk0.orx_URqq2_3
  Parent ID: H0_h.jGxAgHpdd51
  SysFS ID: /devices/pci0000:00/0000:00:06.0/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.35-22-generic ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.35-22-generic ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:06.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (USB Controller)

52: USB 00.0: 0291 USB Host-to-Host link
  [Created at usb.122]
  Unique ID: ADDn.lCek3gQAj_9
  Parent ID: k4bc.QtYiGM_hXFF
  SysFS ID: /devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1:1.0
  SysFS BusID: 1-1:1.0
  Hardware Class: network
  Model: "High Tech Android Phone"
  Hotplug: USB
  Vendor: usb 0x0bb4 "High Tech Computer Corp."
  Device: usb 0x0ffe "Android Phone"
  Revision: "2.26"
  Serial ID: "HT09NR223068"
  Driver: "rndis_host"
  Driver Modules: "rndis_host"
  Device File: usb0
  Speed: 480 Mbps
  HW Address: 26:7f:a7:3d:54:6c
  Link detected: yes
  Module Alias: "usb:v0BB4p0FFEd0226dc02dsc00dp00icE0isc01ip03"
  Driver Info #0:
    Driver Status: rndis_host is active
    Driver Activation Cmd: "modprobe rndis_host"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Hub)

54: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: 2UT6.Hh3ybuWiBQE
  Parent ID: k4bc.QtYiGM_hXFF
  SysFS ID: /devices/pci0000:00/0000:00:04.1/usb1/1-3/1-3:1.0
  SysFS BusID: 1-3:1.0
  Hardware Class: unknown
  Model: "Epson USB2.0 MFP(Hi-Speed)"
  Hotplug: USB
  Vendor: usb 0x04b8 "Epson"
  Device: usb 0x0847 "USB2.0 MFP(Hi-Speed)"
  Revision: "1.00"
  Serial ID: "4B584C593133393654"
  Speed: 480 Mbps
  Module Alias: "usb:v04B8p0847d0100dc00dsc00dp00icFFiscFFipFF"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Hub)

55: USB 00.1: 10900 Printer
  [Created at usb.122]
  Unique ID: VfjA.puwXZV0Gp29
  Parent ID: k4bc.QtYiGM_hXFF
  SysFS ID: /devices/pci0000:00/0000:00:04.1/usb1/1-3/1-3:1.1
  SysFS BusID: 1-3:1.1
  Hardware Class: printer
  Model: "Epson USB2.0 MFP(Hi-Speed)"
  Hotplug: USB
  Vendor: usb 0x04b8 "Epson"
  Device: usb 0x0847 "USB2.0 MFP(Hi-Speed)"
  Revision: "1.00"
  Serial ID: "4B584C593133393654"
  Driver: "usblp"
  Driver Modules: "usblp"
  Device File: /dev/usb/lp0
  Device Files: /dev/usb/lp0, /dev/char/180:0, /dev/usblp0
  Device Number: char 180:0
  Speed: 480 Mbps
  Module Alias: "usb:v04B8p0847d0100dc00dsc00dp00ic07isc01ip02"
  Driver Info #0:
    Driver Status: usblp is active
    Driver Activation Cmd: "modprobe usblp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #48 (Hub)

57: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: PYMB.SAMIiYMCz2F
  Parent ID: zPk0.orx_URqq2_3
  SysFS ID: /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1:1.0
  SysFS BusID: 4-1:1.0
  Hardware Class: hub
  Model: "Broadcom BRCM2046 Hub"
  Hotplug: USB
  Vendor: usb 0x0a5c "Broadcom Corp."
  Device: usb 0x4500 "BRCM2046 Hub"
  Revision: "1.00"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v0A5Cp4500d0100dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #51 (Hub)

58: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: 4zpN.p1+OKuS+ID0
  Parent ID: uIhY.moLwSePIflE
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb3/3-5/3-5:1.0
  SysFS BusID: 3-5:1.0
  Hardware Class: unknown
  Model: "Apple IR Receiver"
  Hotplug: USB
  Vendor: usb 0x05ac "Apple Computer, Inc."
  Device: usb 0x8242 "IR Receiver"
  Revision: "0.16"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 1.5 Mbps
  Module Alias: "usb:v05ACp8242d0016dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Hub)

59: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: gLM6.+uCGtYnayJC
  Parent ID: uIhY.moLwSePIflE
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7:1.0
  SysFS BusID: 3-7:1.0
  Hardware Class: hub
  Model: "Logitech G15 Keyboard"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc223 "Logitech G15 Keyboard"
  Revision: "1.03"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC223d0103dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Hub)

60: USB 00.0: 11500 Bluetooth Device
  [Created at usb.122]
  Unique ID: o5i5.sBAeF2a55g0
  Parent ID: PYMB.SAMIiYMCz2F
  SysFS ID: /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.1/4-1.1:1.0
  SysFS BusID: 4-1.1:1.0
  Hardware Class: bluetooth
  Model: "Apple Bluetooth USB Host Controller"
  Hotplug: USB
  Vendor: usb 0x05ac "Apple Computer, Inc."
  Device: usb 0x8216 "Bluetooth USB Host Controller"
  Revision: "1.80"
  Serial ID: "0026B0F5BE8E"
  Driver: "btusb"
  Driver Modules: "btusb"
  Speed: 12 Mbps
  Module Alias: "usb:v05ACp8216d0180dcE0dsc01dp01icE0isc01ip01"
  Driver Info #0:
    Driver Status: btusb is active
    Driver Activation Cmd: "modprobe btusb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #57 (Hub)

64: USB 00.0: 10800 Keyboard
  [Created at usb.122]
  Unique ID: Z_6+.x5Dxtslg0A3
  Parent ID: gLM6.+uCGtYnayJC
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.1/3-7.1:1.0
  SysFS BusID: 3-7.1:1.0
  Hardware Class: keyboard
  Model: "Logitech Gaming Keyboard"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc221 "Logitech Gaming Keyboard"
  Revision: "1.70"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event3
  Device Files: /dev/input/event3, /dev/char/13:67, /dev/input/by-id/usb-Logitech_Logitech_Gaming_Keyboard-event-kbd, /dev/input/by-path/pci-0000:00:04.0-usb-0:7.1:1.0-event-kbd
  Device Number: char 13:67
  Speed: 1.5 Mbps
  Module Alias: "usb:v046DpC221d0170dc00dsc00dp00ic03isc01ip01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #59 (Hub)

65: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: 0AN3.gCI5FPZGxCD
  Parent ID: gLM6.+uCGtYnayJC
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.1/3-7.1:1.1
  SysFS BusID: 3-7.1:1.1
  Hardware Class: unknown
  Model: "Logitech Gaming Keyboard"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc221 "Logitech Gaming Keyboard"
  Revision: "1.70"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/char/13:68, /dev/input/by-id/usb-Logitech_Logitech_Gaming_Keyboard-event-if01, /dev/input/by-path/pci-0000:00:04.0-usb-0:7.1:1.1-event
  Device Number: char 13:68
  Speed: 1.5 Mbps
  Module Alias: "usb:v046DpC221d0170dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #59 (Hub)

66: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: +6l9.xCkw_U0ZPy7
  Parent ID: gLM6.+uCGtYnayJC
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.2/3-7.2:1.0
  SysFS BusID: 3-7.2:1.0
  Hardware Class: mouse
  Model: "Logitech USB Gaming Mouse"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc041 "USB Gaming Mouse"
  Revision: "46.00"
  Compatible to: int 0x0210 0x0028
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event5, /dev/char/13:69, /dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-event-mouse, /dev/input/by-path/pci-0000:00:04.0-usb-0:7.2:1.0-event-mouse, /dev/char/13:32, /dev/input/by-id/usb-Logitech_USB_Gaming_Mouse-mouse, /dev/input/by-path/pci-0000:00:04.0-usb-0:7.2:1.0-mouse, /dev/char/13:63
  Device Number: char 13:63 (char 13:32)
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC041d4600dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    Buttons: 8
    Wheels: 2
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #59 (Hub)

67: USB 00.1: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: SI+D.uhQYs3d0P+A
  Parent ID: gLM6.+uCGtYnayJC
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.2/3-7.2:1.1
  SysFS BusID: 3-7.2:1.1
  Hardware Class: unknown
  Model: "Logitech USB Gaming Mouse"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc041 "USB Gaming Mouse"
  Revision: "46.00"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC041d4600dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #59 (Hub)

68: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: tN+U.BdErjzgzSbD
  Parent ID: gLM6.+uCGtYnayJC
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb3/3-7/3-7.4/3-7.4:1.0
  SysFS BusID: 3-7.4:1.0
  Hardware Class: unknown
  Model: "Logitech G15 Keyboard"
  Hotplug: USB
  Vendor: usb 0x046d "Logitech, Inc."
  Device: usb 0xc222 "G15 Keyboard"
  Revision: "1.03"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event6
  Device Files: /dev/input/event6, /dev/char/13:70, /dev/input/by-id/usb-G15_Keyboard_G15_Keyboard-event-kbd, /dev/input/by-path/pci-0000:00:04.0-usb-0:7.4:1.0-event-kbd
  Device Number: char 13:70
  Speed: 12 Mbps
  Module Alias: "usb:v046DpC222d0103dc00dsc00dp00ic03isc00ip00"
  Driver Info #0:
    Driver Status: usbhid is active
    Driver Activation Cmd: "modprobe usbhid"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #59 (Hub)

69: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.23.10 "Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,lm,constant_tsc,arch_perfmon,pebs,bts,aperfmperf,pni,dtes64,monitor,ds_cpl,vmx,smx,est,tm2,ssse3,cx16,xtpr,pdcm,sse4_1,xsave,lahf_lm,tpr
  Clock: 2394 MHz
  BogoMips: 5041.92
  Cache: 3072 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

70: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.23.10 "Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,lm,constant_tsc,arch_perfmon,pebs,bts,aperfmperf,pni,dtes64,monitor,ds_cpl,vmx,smx,est,tm2,ssse3,cx16,xtpr,pdcm,sse4_1,xsave,lahf_lm,tpr
  Clock: 1596 MHz
  BogoMips: 5041.27
  Cache: 3072 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

71: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

72: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.PWmYQHojxY6
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:0a.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: eth0
  HW Address: 00:26:b0:de:b6:8e
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (Ethernet controller)

73: None 00.0: 1070c USB-Link
  [Created at net.124]
  Unique ID: IhCv.SyfSGg7YspF
  Parent ID: ADDn.lCek3gQAj_9
  SysFS ID: /class/net/usb0
  SysFS Device Link: /devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1:1.0
  Hardware Class: network interface
  Model: "USB-Link network interface"
  Driver: "rndis_host"
  Driver Modules: "rndis_host"
  Device File: usb0
  HW Address: 26:7f:a7:3d:54:6c
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #52 (USB Host-to-Host link)

```

---

### Post by ParkerH19 on 2010-12-14
Bump: Anyone has this problem?

I tried the live disc on 10.04 I believe and all drivers worked fine without me having to do anything. 

Is this something to do with 10.10?

---

### Post by Jack Kelly on 2010-12-22
Hi,

I have a related issue.  I have been running Ubuntu 10.10 on my laptop since it was released.  Connecting to my WiFi network has worked fine.

Since installing the last round of updates, I can still *connect* fine but the WiFi symbol has disappeared from my Panel.

I have tried:

```

~/$ nm-applet --sm-disable
An instance of nm-applet is already running.

** (nm-applet:2100): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```

---

### Post by Jack Kelly on 2010-12-22
Ah, I fixed my problem by resetting the Gnome Panel to its default settings by following [this guide]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html").  I can now see the WiFi connection in my gnome panel!

@ParkerH19, have you tried resetting your panel back to its default settings?  From your logs, it sounds like the Broadcom driver loads and than nm-applet is already running.  Is it possible that your problem is the same as mine: i.e. the applet is running but it isn't showing up in your panel?

However, looking at your dmesg output, it's not entirely clear to me that your Broadcom driver is loading correctly though.  Searching for "Broadcom" in your dmesg output reveals:

```

[   14.599905] b43-phy0: Broadcom 4321 WLAN found (core revision 12)
[   14.644217] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 2)
[   14.644523] b43: probe of ssb0:0 failed with error -95
[   14.644543] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]

```

---

### Post by Elaztic on 2011-01-14
Well....

Your Broadcom network card could be the cause.
In System -> Administration -> Third party drivers (just have the Danish name for it so hope this is what it is called): Check the Broadcom card is detected **and activated**.

If it is not in the list try to go to 'Ubuntu software center' and search for BC43 or BCM43 and install the driver from there.

Please post back with your findings.

---

### Post by idistech on 2011-01-16
Like Others , Ive stuggled with BCM 4321 on 10.10 ( HP Tx 2000 )

b43-PHY0 errors

In the end, I coundnt get any of the options or standard drivers working...

Tried the removal all and install packages... still didnt work..

End result, I downloaded and installed the latest Broadcom drivers from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

and followed the instructions...

The key to make this work was to ensure b43 wasnt already loaded ( which it was in my installation due to previous instructions/distros )...
Not sure if the new wl.ko was also a factor...but as soon as I had..

rmmod b43
rmmod ssb
rmmod wl  ( hadnt loaded anyway )

modprobe wl

... the device sprung into live.... Hooray

while I kept looking in blacklists* ... I was missing the 'b43' in /etc/modules ....doooh...


G

---

