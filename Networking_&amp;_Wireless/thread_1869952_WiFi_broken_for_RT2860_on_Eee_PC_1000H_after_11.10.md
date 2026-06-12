---
title: "WiFi broken for RT2860 on Eee PC 1000H after 11.10 upgrade"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by T1Oracle on 2011-10-26
Hello all,

I have an Eee PC 1000H and my WiFi isn't working.

So after running dmesg and a number of other commands from the "HOWTO post a Wireless issue (ticket)" thread I got:
```
[    0.297144] system 00:08: [mem 0x8c000000-0x8c01ffff] has been reserved
[    0.297155] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.297166] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.297176] system 00:08: [mem 0xfed50000-0xfed8ffff] has been reserved
[    0.297187] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.297198] system 00:08: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.297211] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.297443] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.297548] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.297742] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.297753] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.297920] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.297932] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.297944] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.298077] pnp 00:0b: [mem 0xe0000000-0xe3ffffff]
[    0.298221] system 00:0b: [mem 0xe0000000-0xe3ffffff] has been reserved
[    0.298234] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.298899] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.298910] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.298918] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.298932] pnp 00:0c: [mem 0x00100000-0x3f7fffff]
[    0.298940] pnp 00:0c: [mem 0x00000000-0xffffffff disabled]
[    0.299137] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.299150] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.299160] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.299171] system 00:0c: [mem 0x00100000-0x3f7fffff] could not be reserved
[    0.299183] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.299723] pnp: PnP ACPI: found 13 devices
[    0.299732] ACPI: ACPI bus type pnp unregistered
[    0.299743] PnPBIOS: Disabled by ACPI PNP
[    0.341610] PCI: max bus depth: 1 pci_try_num: 2
[    0.341711] pci 0000:00:1c.3: BAR 13: assigned [io  0x1000-0x1fff]
[    0.341726] pci 0000:00:1c.2: BAR 14: assigned [mem 0x3f800000-0x3f9fffff]
[    0.341739] pci 0000:00:1c.2: BAR 15: assigned [mem 0x3fa00000-0x3fbfffff 64bit pref]
[    0.341752] pci 0000:00:1c.2: BAR 13: assigned [io  0x2000-0x2fff]
[    0.341765] pci 0000:00:1c.1: BAR 15: assigned [mem 0x3fc00000-0x3fdfffff 64bit pref]
[    0.341778] pci 0000:00:1c.0: BAR 14: assigned [mem 0x3fe00000-0x3fffffff]
[    0.341791] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40000000-0x401fffff 64bit pref]
[    0.341804] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.341814] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.341825] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.341839] pci 0000:00:1c.0:   bridge window [mem 0x3fe00000-0x3fffffff]
[    0.341852] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff 64bit pref]
[    0.341870] pci 0000:00:1c.1: PCI bridge to [bus 04-04]
[    0.341880] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.341894] pci 0000:00:1c.1:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.341907] pci 0000:00:1c.1:   bridge window [mem 0x3fc00000-0x3fdfffff 64bit pref]
[    0.341924] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    0.341934] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.341949] pci 0000:00:1c.2:   bridge window [mem 0x3f800000-0x3f9fffff]
[    0.341962] pci 0000:00:1c.2:   bridge window [mem 0x3fa00000-0x3fbfffff 64bit pref]
[    0.341981] pci 0000:00:1c.3: PCI bridge to [bus 01-02]
[    0.341993] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
[    0.342010] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xfbefffff]
[    0.342024] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.342041] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.342048] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.342061] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.342072] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.342100] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.342142] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.342156] pci 0000:00:1c.0: setting latency timer to 64
[    0.342189] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.342201] pci 0000:00:1c.1: setting latency timer to 64
[    0.342218] pci 0000:00:1c.2: enabling device (0104 -> 0107)
[    0.342242] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.342255] pci 0000:00:1c.2: setting latency timer to 64
[    0.342271] pci 0000:00:1c.3: enabling device (0106 -> 0107)
[    0.342295] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.342307] pci 0000:00:1c.3: setting latency timer to 64
[    0.342326] pci 0000:00:1e.0: setting latency timer to 64
[    0.342339] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.342348] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.342357] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.342366] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.342375] pci_bus 0000:00: resource 8 [mem 0x3f800000-0xffffffff]
[    0.342385] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.342394] pci_bus 0000:05: resource 1 [mem 0x3fe00000-0x3fffffff]
[    0.342403] pci_bus 0000:05: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
[    0.342413] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.342422] pci_bus 0000:04: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.342431] pci_bus 0000:04: resource 2 [mem 0x3fc00000-0x3fdfffff 64bit pref]
[    0.342441] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.342450] pci_bus 0000:03: resource 1 [mem 0x3f800000-0x3f9fffff]
[    0.342460] pci_bus 0000:03: resource 2 [mem 0x3fa00000-0x3fbfffff 64bit pref]
[    0.342469] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.342478] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbefffff]
[    0.342488] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf6ffffff 64bit pref]
[    0.342498] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.342506] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.342515] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.342524] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000dffff]
[    0.342534] pci_bus 0000:06: resource 8 [mem 0x3f800000-0xffffffff]
[    0.342661] NET: Registered protocol family 2
[    0.342864] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.343797] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.345018] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.345581] TCP: Hash tables configured (established 131072 bind 65536)
[    0.345594] TCP reno registered
[    0.345623] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.345659] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.346018] NET: Registered protocol family 1
[    0.346073] pci 0000:00:02.0: Boot video device
[    0.346274] PCI: CLS 32 bytes, default 64
[    0.347358] audit: initializing netlink socket (disabled)
[    0.347387] type=2000 audit(1319637924.340:1): initialized
[    0.407621] highmem bounce pool size: 64 pages
[    0.407640] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.414697] VFS: Disk quotas dquot_6.5.2
[    0.414940] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.417646] fuse init (API version 7.16)
[    0.418030] msgmni has been set to 1703
[    0.419356] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.419500] io scheduler noop registered
[    0.419509] io scheduler deadline registered
[    0.419584] io scheduler cfq registered (default)
[    0.419952] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.420093] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.420259] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.420347] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.420518] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.420611] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.420770] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.420858] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.421127] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.421231] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.421442] intel_idle: MWAIT substates: 0x20220
[    0.421461] intel_idle: v0.4 model 0x1C
[    0.421467] intel_idle: lapic_timer_reliable_states 0x2
[    0.421489] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.421675] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.421838] ACPI: AC Adapter [AC0] (on-line)
[    0.422220] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.427224] ACPI: Lid Switch [LID]
[    0.427420] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.427439] ACPI: Sleep Button [SLPB]
[    0.427599] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.427614] ACPI: Power Button [PWRB]
[    0.427779] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.427792] ACPI: Power Button [PWRF]
[    0.427896] ACPI: acpi_idle yielding to intel_idle
[    0.442741] thermal LNXTHERM:00: registered as thermal_zone0
[    0.442752] ACPI: Thermal Zone [TZ00] (39 C)
[    0.442864] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.442955] ERST: Table is not found!
[    0.443181] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.443702] isapnp: Scanning for PnP cards...
[    0.627165] ACPI: Battery Slot [BAT0] (battery present)
[    0.799445] isapnp: No Plug & Play device found
[    0.940653] Freeing initrd memory: 13308k freed
[    0.970844] Linux agpgart interface v0.103
[    0.971003] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    0.971171] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.971358] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.971577] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.974841] brd: module loaded
[    0.976457] loop: module loaded
[    0.976820] ata_piix 0000:00:1f.2: version 2.13
[    0.976853] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.976865] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.976940] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.977690] scsi0 : ata_piix
[    0.977942] scsi1 : ata_piix
[    0.980827] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.980835] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.982028] Fixed MDIO Bus: probed
[    0.982102] PPP generic driver version 2.4.2
[    0.982249] tun: Universal TUN/TAP device driver, 1.6
[    0.982254] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.982471] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.982540] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.982576] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.982584] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.982680] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.982723] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.982743] ehci_hcd 0000:00:1d.7: debug port 1
[    0.986650] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.986688] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    1.000036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.000331] hub 1-0:1.0: USB hub found
[    1.000344] hub 1-0:1.0: 8 ports detected
[    1.000521] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.000559] uhci_hcd: USB Universal Host Controller Interface driver
[    1.000638] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.000654] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.000662] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.000768] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.000814] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d480
[    1.001132] hub 2-0:1.0: USB hub found
[    1.001144] hub 2-0:1.0: 2 ports detected
[    1.001283] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.001297] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.001305] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.001409] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.001471] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    1.001773] hub 3-0:1.0: USB hub found
[    1.001785] hub 3-0:1.0: 2 ports detected
[    1.001915] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.001933] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.001941] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.002034] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.002096] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d880
[    1.002407] hub 4-0:1.0: USB hub found
[    1.002418] hub 4-0:1.0: 2 ports detected
[    1.002557] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.002572] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.002580] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.002673] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.002732] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000dc00
[    1.003047] hub 5-0:1.0: USB hub found
[    1.003058] hub 5-0:1.0: 2 ports detected
[    1.003325] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.029749] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.029771] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.030101] mousedev: PS/2 mouse device common for all mice
[    1.032206] rtc_cmos 00:03: RTC can wake from S4
[    1.032400] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.032447] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.032722] device-mapper: uevent: version 1.0.3
[    1.032932] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.033022] EISA: Probing bus 0 at eisa.0
[    1.033028] EISA: Cannot allocate resource for mainboard
[    1.033035] Cannot allocate resource for EISA slot 1
[    1.033040] Cannot allocate resource for EISA slot 2
[    1.033046] Cannot allocate resource for EISA slot 3
[    1.033051] Cannot allocate resource for EISA slot 4
[    1.033057] Cannot allocate resource for EISA slot 5
[    1.033062] Cannot allocate resource for EISA slot 6
[    1.033068] Cannot allocate resource for EISA slot 7
[    1.033073] Cannot allocate resource for EISA slot 8
[    1.033078] EISA: Detected 0 cards.
[    1.033097] cpufreq-nforce2: No nForce2 chipset.
[    1.033261] cpuidle: using governor ladder
[    1.033537] cpuidle: using governor menu
[    1.033542] EFI Variables Facility v0.08 2004-May-17
[    1.034227] TCP cubic registered
[    1.034611] NET: Registered protocol family 10
[    1.036056] NET: Registered protocol family 17
[    1.036108] Registering the dns_resolver key type
[    1.036158] Using IPI No-Shortcut mode
[    1.036406] PM: Hibernation image not present or could not be loaded.
[    1.036432] registered taskstats version 1
[    1.054186]   Magic number: 15:974:81
[    1.054348] rtc_cmos 00:03: setting system clock to 2011-10-26 14:05:25 UTC (1319637925)
[    1.055276] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.055282] EDD information not available.
[    1.056887] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.160582] ata2.00: CFA: ASUS-PHISON SSD, TST2.04U, max UDMA/66
[    1.160592] ata2.00: 15761088 sectors, multi 0: LBA 
[    1.160604] ata2.01: CFA: ASUS-PHISON SSD, TST2.04P, max UDMA/66
[    1.160611] ata2.01: 63045360 sectors, multi 0: LBA 
[    1.168445] ata2.00: configured for UDMA/66
[    1.176446] ata2.01: configured for UDMA/66
[    1.176792] scsi 1:0:0:0: Direct-Access     ATA      ASUS-PHISON SSD  TST2 PQ: 0 ANSI: 5
[    1.177150] sd 1:0:0:0: [sda] 15761088 512-byte logical blocks: (8.06 GB/7.51 GiB)
[    1.177250] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.177408] sd 1:0:0:0: [sda] Write Protect is off
[    1.177418] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.177524] sd 1:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.177650] scsi 1:0:1:0: Direct-Access     ATA      ASUS-PHISON SSD  TST2 PQ: 0 ANSI: 5
[    1.178131] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    1.179522] sd 1:0:1:0: [sdb] 63045360 512-byte logical blocks: (32.2 GB/30.0 GiB)
[    1.179832]  sda: sda1
[    1.179853] sd 1:0:1:0: [sdb] Write Protect is off
[    1.179863] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.179970] sd 1:0:1:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.180761] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.182829]  sdb: sdb1 < sdb5 >
[    1.183636] sd 1:0:1:0: [sdb] Attached SCSI disk
[    1.183718] Freeing unused kernel memory: 696k freed
[    1.184446] Write protecting the kernel text: 5332k
[    1.184534] Write protecting the kernel read-only data: 2188k
[    1.228112] udevd[83]: starting version 173
[    1.312098] usb 1-5: new high speed USB device number 2 using ehci_hcd
[    1.565253] ATL1E 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.565283] ATL1E 0000:04:00.0: setting latency timer to 64
[    1.627264] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.668242] usb 1-8: new high speed USB device number 4 using ehci_hcd
[    2.092076] usb 5-1: new full speed USB device number 2 using uhci_hcd
[    2.536092] udevd[278]: starting version 173
[    2.708091] lp: driver loaded but no devices found
[    2.910136] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    3.250799] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: user_xattr
[    3.297271] eeepc_laptop: Eee PC Hotkey Driver
[    3.297296] eeepc_laptop: Hotkey init flags 0x41
[    3.305979] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    3.306182] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    3.368670] [drm] Initialized drm 1.1.0 20060810
[    3.503066] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.503082] i915 0000:00:02.0: setting latency timer to 64
[    3.553899] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.553909] [drm] Driver supports precise vblank timestamp query.
[    3.597281] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.654872] composite sync not supported
[    3.673999] intel_rng: FWH not detected
[    3.711484] leds_ss4200: no LED devices found
[    3.861683] Bluetooth: Core ver 2.16
[    3.861755] NET: Registered protocol family 31
[    3.861761] Bluetooth: HCI device and connection manager initialized
[    3.861769] Bluetooth: HCI socket layer initialized
[    3.861775] Bluetooth: L2CAP socket layer initialized
[    3.873440] Linux video capture interface: v2.00
[    3.895214] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[    3.895737] Bluetooth: SCO socket layer initialized
[    3.896594] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    3.902200] usbcore: registered new interface driver btusb
[    3.914126] [drm] initialized overlay support
[    3.914201] composite sync not supported
[    3.926675] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
[    3.927243] usbcore: registered new interface driver uvcvideo
[    3.927252] USB Video Class driver (v1.1.0)
[    3.937106] usbcore: registered new interface driver uas
[    3.944543] fbcon: inteldrmfb (fb0) is primary device
[    3.947032] Console: switching to colour frame buffer device 128x37
[    3.947118] fb0: inteldrmfb frame buffer device
[    3.947125] drm: registered panic notifier
[    3.947188] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.981743] Initializing USB Mass Storage driver...
[    3.983467] scsi2 : usb-storage 1-5:1.0
[    3.984242] usbcore: registered new interface driver usb-storage
[    3.984252] USB Mass Storage support registered.
[    4.336905] type=1400 audit(1319637928.781:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=572 comm="apparmor_parser"
[    4.336932] type=1400 audit(1319637928.781:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=489 comm="apparmor_parser"
[    4.338609] type=1400 audit(1319637928.781:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=572 comm="apparmor_parser"
[    4.338673] type=1400 audit(1319637928.781:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=489 comm="apparmor_parser"
[    4.339675] type=1400 audit(1319637928.781:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=572 comm="apparmor_parser"
[    4.341101] type=1400 audit(1319637928.785:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=489 comm="apparmor_parser"
[    4.447067] psmouse serio1: ID: 10 00 64
[    4.645696] elantech: assuming hardware version 2, firmware version 2.0.48
[    4.651272] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[    4.661933] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[    4.661950] eeepc_laptop: Get control methods supported: 0x6101713
[    4.704944] input: Asus EeePC extra buttons as /devices/platform/eeepc/input/input7
[    4.727748] elantech: Synaptics capabilities query result 0x00, 0x02, 0x64.
[    4.937032] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
[    5.000018] scsi 2:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
[    5.085145] composite sync not supported
[    5.120911] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    5.658177] sd 2:0:0:0: [sdc] 8040448 512-byte logical blocks: (4.11 GB/3.83 GiB)
[    5.659341] sd 2:0:0:0: [sdc] Write Protect is off
[    5.659355] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    5.660624] sd 2:0:0:0: [sdc] No Caching mode page present
[    5.660638] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    5.668018] sd 2:0:0:0: [sdc] No Caching mode page present
[    5.668018] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    5.670285]  sdc: sdc1
[    5.673781] sd 2:0:0:0: [sdc] No Caching mode page present
[    5.673796] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[    5.673808] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[    5.787006] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.787139] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    5.787205] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    5.994596] eeepc_laptop: BIOS says wireless lan is unblocked, but the pci device is absent
[    5.994607] eeepc_laptop: skipped wireless hotplug as probably inappropriate for this model
[    6.109795] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    6.119675] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    6.173311] type=1400 audit(1319637930.617:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=763 comm="apparmor_parser"
[    6.176932] type=1400 audit(1319637930.621:9): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=762 comm="apparmor_parser"
[    6.213025] type=1400 audit(1319637930.657:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=767 comm="apparmor_parser"
[    6.215346] type=1400 audit(1319637930.657:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=767 comm="apparmor_parser"
[    6.234516] type=1400 audit(1319637930.677:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=767 comm="apparmor_parser"
[    6.431794] type=1400 audit(1319637930.873:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=768 comm="apparmor_parser"
[    6.446769] type=1400 audit(1319637930.889:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=768 comm="apparmor_parser"
[    6.457460] type=1400 audit(1319637930.901:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=768 comm="apparmor_parser"
[    6.533380] type=1400 audit(1319637930.977:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=778 comm="apparmor_parser"
[    6.535108] type=1400 audit(1319637930.977:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=778 comm="apparmor_parser"
[    7.075422] ATL1E 0000:04:00.0: irq 45 for MSI/MSI-X
[    7.076092] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.495293] ppdev: user-space parallel port driver
[    7.720553] init: failsafe main process (590) killed by TERM signal
[    7.752805] init: apport pre-start process (874) terminated with status 1
[    7.917957] init: apport post-stop process (928) terminated with status 1
[    7.972719] init: gdm main process (924) killed by TERM signal
[    8.068268] Bluetooth: RFCOMM TTY layer initialized
[    8.068285] Bluetooth: RFCOMM socket layer initialized
[    8.068292] Bluetooth: RFCOMM ver 1.11
[    8.539075] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.539084] Bluetooth: BNEP filters: protocol multicast
[    8.712639] composite sync not supported
[    8.744717] composite sync not supported
[   16.893204] composite sync not supported
[   19.797160] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   19.805898] EXT4-fs (sdb5): re-mounted. Opts: user_xattr,commit=0
[   20.947040] composite sync not supported
[   21.219661] init: plymouth-stop pre-start process (1290) terminated with status 1
[   24.452428] composite sync not supported
[  630.824293] composite sync not supported
[  631.552411] composite sync not supported
[  631.837091] composite sync not supported
[  633.252910] composite sync not supported
[ 2509.508800] composite sync not supported
[ 6748.954468] composite sync not supported
[ 8717.004528] composite sync not supported
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ sudo lshw -C network
[sudo] password for bernard: 
Sorry, try again.
[sudo] password for bernard: 
PCI (sysfs)  


  

ls
^Cbernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ iwlisscan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ lsb_release -d
Description:	Ubuntu 11.10
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ uname -mr
3.0.0-12-generic i686
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ sudo /etc/in
init/            initramfs-tools/ insserv.conf.d/  
init.d/          insserv/         
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ sudo /etc/in
init/            initramfs-tools/ insserv.conf.d/  
init.d/          insserv/         
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Ralink corp. RT2860
04:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 005 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. Broadcom Bluetooth 2.1
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:75:bf:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2037392 (2.0 MB)  TX bytes:2037392 (2.0 MB)

bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
joydev                 17393  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
psmouse                73673  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
usb_storage            44173  1 
uas                    17699  0 
btusb                  18160  2 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             148839  23 bnep,rfcomm,btusb
serio_raw              12990  0 
soundcore              12600  1 snd
i915                  505108  3 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
eeepc_laptop           19464  0 
sparse_keymap          13658  1 eeepc_laptop
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1e                  32809  0 
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$
```

In my attempt to fix this issue I attempted to get a driver for my RT2860 WiFi, but I cannot compile the driver that I downloaded from the Ralink website.

I keep getting the following error:
```
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ ls
common            Makefile                    os             sta
include           Makefile~                   README_STA     tools
iwpriv_usage.txt  Makefile.NonLoadableModule  RT2860STA.dat
[4]   Done                    sudo gedit README_STA
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ sudo make clean
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux'
rm -rf os/linux/Makefile
bernard@bernard-netbook:~/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0$ sudo make
make -C tools
make[1]: Entering directory `/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools'
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/Makefile
make  -C  /lib/modules/3.0.0-12-generic/build SUBDIRS=/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/md5.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/mlme.o
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/mlme.c:3589:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/mlme.c:3811:1: warning: the frame size of 1572 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/action.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/ba_action.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/eeprom.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_wpa.o
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_wpa.c: In function ‘AES_GTK_KEY_WRAP’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/cmm_wpa.c:669:1: warning: the frame size of 1088 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../common/dfs.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/assoc.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/aironet.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/auth.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sync.o
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sync.c:888:1: warning: the frame size of 1244 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sync.c:642:1: warning: the frame size of 1248 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sync.c:1447:1: warning: the frame size of 1300 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/sanity.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/connect.o
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/connect.c:311:1: warning: the frame size of 1596 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/wpa.o
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/wpa.c: In function ‘CCKMPRF’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../sta/wpa.c:1869:1: warning: the frame size of 1044 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.o
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c: In function ‘rtmp_os_thread_init’:
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:983:2: error: implicit declaration of function ‘daemonize’ [-Werror=implicit-function-declaration]
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:985:2: error: implicit declaration of function ‘allow_signal’ [-Werror=implicit-function-declaration]
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:985:15: error: ‘SIGTERM’ undeclared (first use in this function)
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:985:15: note: each undeclared identifier is reported only once for each function it appears in
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:986:15: error: ‘SIGKILL’ undeclared (first use in this function)
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:987:9: error: dereferencing pointer to incomplete type
/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.c:987:20: error: ‘PF_NOFREEZE’ undeclared (first use in this function)
cc1: some warnings being treated as errors

make[2]: *** [/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/bernard/Downloads/2008_0522_RT2860_Linux_STA_v1.6.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [LINUX] Error 2
```

---

### Post by ratcheer on 2011-10-26
That seems to be a pretty old version of the driver. My rt2860 driver is version 2.4.1. Did you download it from the Ralink web site?

Tim

---

### Post by T1Oracle on 2011-10-26
> **ratcheer said:**
> That seems to be a pretty old version of the driver. My rt2860 driver is version 2.4.1. Did you download it from the Ralink web site?

Tim

Yes.

---

### Post by ratcheer on 2011-10-27
Ok, did you follow all the steps to install it?

1) Copy RTA2860STA.dat to /etc/Wireless/RT2860STA/

2) Made sure rt2860.bin is in /lib/firmware/ ? If not, download the firmware from Ralink, extract, and copy it there.

3) sudo make (run from the extracted driver directory, e.g., DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 on my system).

4) sudo make install (assuming step 3 works).

5) sudo modprobe rt3562sta

Also, there are some instructions in README_STA_pci about configuring a couple of SUPPLICANT parameters. And I always blacklist rt2800pci and add rt3562sta to /etc/initramfs-tools/modules

I hope this helps. But I still don't understand why your driver version seems to be so much older than the one I downloaded from Ralink.

Tim

---

### Post by T1Oracle on 2011-10-27
> **ratcheer said:**
> Ok, did you follow all the steps to install it?

1) Copy RTA2860STA.dat to /etc/Wireless/RT2860STA/

2) Made sure rt2860.bin is in /lib/firmware/ ? If not, download the firmware from Ralink, extract, and copy it there.

3) sudo make (run from the extracted driver directory, e.g., DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 on my system).

4) sudo make install (assuming step 3 works).

5) sudo modprobe rt3562sta

Also, there are some instructions in README_STA_pci about configuring a couple of SUPPLICANT parameters. And I always blacklist rt2800pci and add rt3562sta to /etc/initramfs-tools/modules

I hope this helps. But I still don't understand why your driver version seems to be so much older than the one I downloaded from Ralink.

Tim
1) This is the Ralink website: [http://web.ralinktech.com/ralink/Home/Support/Linux.html]("http://web.ralinktech.com/ralink/Home/Support/Linux.html")
2) I have an RT2860 not an RT3562
3) None of the instructions you presented are in the readme
4) RTA2860STA.dat and rt2860.bin are already in place.

I can't install the driver because it doesn't compile.  It doesn't compile due to what appears to be a syntax error.

Regardless, I found this for debian:
[http://wiki.debian.org/rt2860sta#Squeeze]("http://wiki.debian.org/rt2860sta#Squeeze")
But installing that didn't work either and now my Eee PC won't pair with my Droid X via Bluetooth using PDANet for tethering.  So now my computer is basically useless until I get a CAT5 cable.

To get the .deb package to install I had to use --force-overwite.

Thanks for trying.

---

### Post by ratcheer on 2011-10-27
Yes, I tried.

And, yes, my card is a Ralink 3062, but for some reason it uses the rt2860 driver.

```
Kernel driver in use: rt2860
```

So, I thought yours would be very similar to mine.

Good luck,
Tim

---

### Post by T1Oracle on 2011-10-27
Well I fixed the tethering by restarting my phone.  Silly Android :\

Anyway, I can't find the driver you have.  Where do I download it?

---

### Post by ratcheer on 2011-10-27
[http://web.ralinktech.com/ralink/Home/Support/Linux.html](http://web.ralinktech.com/ralink/Home/Support/Linux.html)

Tim

---

### Post by T1Oracle on 2011-10-28
That's the same link I gave you. It isn't there. Half the links on that page don't even work.

---

### Post by ratcheer on 2011-10-28
Sorry. That page is different from where I got mine. However, I can no longer find the page where I got it. It looks like Ralink was taken over by Mediatek earlier this year. Now, it seems Mediatek has put up faulty web pages for the previously good Ralink content.

I could try to email you my driver file, if you want to PM me your email address.

Tim

---

### Post by T1Oracle on 2011-10-28
So after much searching I found that rt2800pci replaced rt2860sta in the 3.0 kernel.  So I removed rt2800pci from the black list and ran sudo modprobe 2800pci and now it works!

Now I just need to make that change permanent so I don't have to do it every time I reboot.

---

### Post by T1Oracle on 2011-10-28
I added rt2800pci to the end of the /etc/modules file and it's perfect now :)

---

### Post by ratcheer on 2011-10-28
Hmmm. I will have to try that again, sometime.

Tim

---

### Post by T1Oracle on 2011-12-16
> **ratcheer said:**
> Hmmm. I will have to try that again, sometime.

Tim

Actually now it kernel panics randomly after a few minutes or hours of being on :\  This happens usually when on battery power.

---

### Post by Marky-boy on 2011-12-17
Just chiming in that I have the same issue - Ubuntu 11.10 broke the wifi on my wife's 1000H. I tried to DL the driver from RALink but the README only talks about kernel 2.6, not 3.0

I don't have the time to muck around with this anymore (and I'm frustrated beyond belief). I've plugged a Netgear USB adaptor into her eee and it works, so that'll do for now. Hopefully RAlink can update their driver and we'll get it with a future update.

---

### Post by ratcheer on 2011-12-18
The driver compiles and runs just fine for me on the 3.0 kernel. Also on the 3.1 kernel with Arch Linux.

Tim

---

### Post by TBABill on 2011-12-18
Oddly, that driver shouldn't need to be gotten from source. Ubuntu just sets it up wrong and enables more than one driver. Blacklisting the RT2800 and RT2x00 series drivers and keeping the RT2860STA driver enabled normally fixes issues with that chipset in ubuntu. Would be interesting to see if that holds true in 11.10 as it did in prior versions.

---

### Post by Marky-boy on 2011-12-18
> Blacklisting the RT2800 and RT2x00 series drivers and keeping the RT2860STA driver enabled

Apologies for the noobieness, but can you talk me through how to do this?

---

### Post by TBABill on 2011-12-18
Open a terminal and enter the code lsmod (that's LSMOD in lowercase). That lists all active drivers. If you have more than one that starts with RT2, then you may be dealing with the scenario I described. Basically, if you see RT2860STA in that list, the others should not be listed. 

In order to block them from starting, the process is called blacklisting and basically just stops the drivers (modules) from being enabled on every restart or login. 

To blacklist a driver, you must know what it is listed as in your lsmod output. So, assume you see RT2x00pci listed. That's just an example, but a possible one you may see. Now, if it was listed and you wanted to block it from loading ever, you would edit a file as follows:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```That just opens the file as root for editing. You just copy the following to the end of the list, save and restart: ```
blacklist rt2x00pci
``` 

Basically just blacklist any rt2 driver besides rt2860sta, but EACH ONE requires a blacklist entry. So, if you had 3 different ones conflicting, such as rt2x00pci, rt2800pci, rt2x00usb, you'd enter a separate blacklist line for each one just like I did above.

---

### Post by Marky-boy on 2011-12-19
Thanks so much, TBABill (and the rest of you) - it's folks like you that make it worth persevering when Ubuntu gets challenging.

Turns out that I had four drivers running - 
rt2800pci (used by 0),
rt2800lib (used by rt2800pci),
rt2x00pci (used by rt2800 pci) and
rt2x00lib (used by the previously listed three).

No STA in there - which backs up what T1Oracle said about pci replacing sta in kernel 3.0.

Interestingly, the blacklist had all four blacklisted! I just commented out rt2800pci and rt2800lib (i.e. unblacklisted them) and saved the file, and presto, wireless back up.

Will see if I get the same issues as T1Oracle, but for now, we're back in business.

Cheers again.

---

### Post by alfonso78 on 2012-01-30
> **ratcheer said:**
> The driver compiles and runs just fine for me on the 3.0 kernel. Also on the 3.1 kernel with Arch Linux.

Tim

sorry, just to understand, are you suggesting to compile RT2860STA also for kernel 3.0 / 3.1 and then blacklist rt2x00pci and rt2800pci? The latest RT2860STA I could find on [ralink website]("http://www.ralinktech.com/en/04_support/support.php?sn=501") is 2.4.0.0 from 16th July 2010!

Is this the one you are using?

---

### Post by itsjustarumour on 2012-01-30
> **Marky-boy said:**
> Just chiming in that I have the same issue - Ubuntu 11.10 broke the wifi on my wife's 1000H. I tried to DL the driver from RALink but the README only talks about kernel 2.6, not 3.0

I don't have the time to muck around with this anymore (and I'm frustrated beyond belief).  into her eee and it works, so that'll do for now. Hopefully RAlink can update their driver and we'll get it with a future update.

Exactly the same scenario here - upgrade to 11.10 broke my wireless.  My system isn't even recognising the Ralink chipset.

Like you, I've plugged in a Netgear USB adapter (with Atheros chipset) to get up and running again. Like you, I've tried various solutions, and don't have the time to muck around with this anymore.

I had problems with wireless (various chipsets) on 11.04, and now with 11.10 it seems like Ubuntu/Canonical QA still leaves a lot to be desired. 

After 6 years of using Ubuntu as my primary OS, I'm writing this on what is my last Ubuntu-powered machine - everything else I've switched to Mint or Fedora, and the only reason this one's running 11.10 is because I haven't got the time right now to install all my software on a new box!

BTW, if I boot into Mint 11.10 or Fedora 16 on this same box, wireless on both other OS's works perfectly fine.  So come on Ubuntu/Canonical, what the he*l are you playing at?

[/RANT]

---

### Post by ratcheer on 2012-01-30
> **alfonso78 said:**
> sorry, just to understand, are you suggesting to compile RT2860STA also for kernel 3.0 / 3.1 and then blacklist rt2x00pci and rt2800pci? The latest RT2860STA I could find on [ralink website]("http://www.ralinktech.com/en/04_support/support.php?sn=501") is 2.4.0.0 from 16th July 2010!

Is this the one you are using?

For the first part of your question, yes. For the second part, I am using 2.4.1.1 dated 17 Dec 2010.

Also, Arch recently went to the 3.2 kernel. This driver is working with it, too.

Tim

---

### Post by alfonso78 on 2012-01-31
> **ratcheer said:**
> For the first part of your question, yes. For the second part, I am using 2.4.1.1 dated 17 Dec 2010.

Also, Arch recently went to the 3.2 kernel. This driver is working with it, too.

Tim

Thank you! That sounds very promising!

Now I read again this thread and you have RT3562, not RT2860...

With RT2860, when I try to make, I get an error:

```
$ sudo make
make -C tools
make[1]: Entering directory `/home/alfonso/wifi/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/alfonso/wifi/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/alfonso/wifi/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/alfonso/wifi/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/3.2.0-interlaced2+/build SUBDIRS=/home/alfonso/wifi/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make: *** /lib/modules/3.2.0-interlaced2+/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

```

HOLD ON! :)

I realize the error is because I moved the folder where I compiled the last kernel! :)

now it's compiling!!!

Ok, I tried to follow [this post]("http://ubuntuforums.org/showpost.php?p=9255730&postcount=1"):

I download my driver [here]("http://www.ralinktech.com/en/04_support/support.php?sn=501").

then I edit config.mk and cmm_wpa.c as suggested, and I follow the commands:

```
sudo make
sudo make install
sudo ifconfig wlan0 down
sudo rmmod rt2860sta

```

but since there is no rt2860sta with kernel 3.0 or 3.2 I do: 

```
sudo rmmod rt2860pci rt2860lib rt2x00pci rt2x00lib mac80211 cfg80211
```

since they seem all inter-dependent.

then:

```
sudo depmod -a
sudo modprobe rt2860sta
```

and I can see with lsmod that the driver is loaded, but if I type ifconfig, I don't have any wlan0 or wlan1...

and obviously the network manager doesn't work.

any idea?

thank you!

---

### Post by ratcheer on 2012-01-31
@alfonso78, what a mess! I don't know. All I ever have to do is the make, make install, and modprobe. Then my wireless comes up without even rebooting.

When you run "sudo lspci -v", what shows as the "Kernel driver in use" in the wireless card section? Here is mine:

```
06:00.0 Network controller: Ralink corp. Device 3062
    Subsystem: Ralink corp. Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 19
    Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    [COLOR=Blue]Kernel driver in use: rt2860[/COLOR]
    Kernel modules: rt3562sta, rt2800pci
```

Tim

---

### Post by alfonso78 on 2012-01-31
> **ratcheer said:**
> @alfonso78, what a mess! I don't know. All I ever have to do is the make, make install, and modprobe. Then my wireless comes up without even rebooting.

When you run "sudo lspci -v", what shows as the "Kernel driver in use" in the wireless card section? Here is mine:

```
06:00.0 Network controller: Ralink corp. Device 3062
    Subsystem: Ralink corp. Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 19
    Memory at fbdf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    [COLOR=Blue]Kernel driver in use: rt2860[/COLOR]
    Kernel modules: rt3562sta, rt2800pci
```

Tim

Thank you!

I *almost* fixed the problem. I need just to be able to compile compat-wireless-3.3-rc1-2 under kernel 3.2.0

I will update the [main thread I created]("http://ubuntuforums.org/showthread.php?p=11654973") when I have results.

---

