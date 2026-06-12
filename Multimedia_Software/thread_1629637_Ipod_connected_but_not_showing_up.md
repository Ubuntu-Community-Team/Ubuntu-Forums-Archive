---
title: "Ipod connected but not showing up"
date: 2010-11-24
forum: Multimedia Software
---

### Post by b3d3g1 on 2010-11-24
I am having a problem connecting my 30 gig ipod to ubuntu 10.10.  Can someone please help me.  Im new to linux and i really want to have some books on tape on my ipod for my thanksgiving drive home.

I plug in the ipod and it charges just fine.  It used to show up in rhythmbox music player and I tried to sync it and now it doesn't show up.  While syncing, it got to ~10% and stopped.  I have all my old music on it and I can still listen to it but I can't add more music or access it on the desktop.  

Please help.  I tried typing dmesg in the terminal and I can see the ipod is registering. See below:

[    0.356317] pnp 00:0a: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.356320] pnp 00:0a: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.356324] pnp 00:0a: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.378445] pnp: PnP ACPI: found 12 devices
[    0.378449] ACPI: ACPI bus type pnp unregistered
[    0.378453] PnPBIOS: Disabled by ACPI PNP
[    0.378469] system 00:05: [io  0x0c80-0x0cff] could not be reserved
[    0.378478] system 00:08: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.378485] system 00:09: [io  0x0900-0x097f] has been reserved
[    0.378488] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.378495] system 00:0a: [io  0xf400-0xf4fe] has been reserved
[    0.378498] system 00:0a: [io  0x1080-0x10bf] has been reserved
[    0.378501] system 00:0a: [io  0x10c0-0x10df] has been reserved
[    0.378504] system 00:0a: [io  0x0809] has been reserved
[    0.378510] system 00:0b: [mem 0x00000000-0x0009efff] could not be reserved
[    0.378514] system 00:0b: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.378517] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.378520] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.378523] system 00:0b: [mem 0x00100000-0x7fe6d7ff] could not be reserved
[    0.378527] system 00:0b: [mem 0x7fe6d800-0x7fefffff] has been reserved
[    0.378530] system 00:0b: [mem 0x7ff00000-0x7fffffff] has been reserved
[    0.378533] system 00:0b: [mem 0x7ff00000-0x806fffff] could not be reserved
[    0.378536] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.378540] system 00:0b: [mem 0xffa00000-0xffafffff] has been reserved
[    0.378543] system 00:0b: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.378546] system 00:0b: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.378549] system 00:0b: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.378552] system 00:0b: [mem 0xfeda0000-0xfeda3fff] has been reserved
[    0.378556] system 00:0b: [mem 0xfeda4000-0xfeda4fff] has been reserved
[    0.378559] system 00:0b: [mem 0xfeda5000-0xfeda5fff] has been reserved
[    0.378562] system 00:0b: [mem 0xfeda6000-0xfeda6fff] has been reserved
[    0.378565] system 00:0b: [mem 0xfed18000-0xfed1bfff] has been reserved
[    0.378568] system 00:0b: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.414812] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.414819] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.414823] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.414828] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.414831] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.414834] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.414837] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.414842] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfeafffff]
[    0.414846] pci 0000:00:01.0:   bridge window [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.414852] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.414856] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.414863] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.414869] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.414878] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.414882] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.414889] pci 0000:00:1c.1:   bridge window [mem 0xf9f00000-0xf9ffffff]
[    0.414894] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.414903] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.414907] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.414914] pci 0000:00:1c.3:   bridge window [mem 0xf9c00000-0xf9efffff]
[    0.414920] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf81fffff 64bit pref]
[    0.414929] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.414931] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.414938] pci 0000:00:1e.0:   bridge window [mem 0xf9b00000-0xf9bfffff]
[    0.414944] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.414965]   alloc irq_desc for 16 on node -1
[    0.414967]   alloc kstat_irqs on node -1
[    0.414975] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.414979] pci 0000:00:01.0: setting latency timer to 64
[    0.414992] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.414997] pci 0000:00:1c.0: setting latency timer to 64
[    0.415009]   alloc irq_desc for 17 on node -1
[    0.415011]   alloc kstat_irqs on node -1
[    0.415015] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.415021] pci 0000:00:1c.1: setting latency timer to 64
[    0.415033]   alloc irq_desc for 19 on node -1
[    0.415035]   alloc kstat_irqs on node -1
[    0.415039] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.415044] pci 0000:00:1c.3: setting latency timer to 64
[    0.415055] pci 0000:00:1e.0: setting latency timer to 64
[    0.415060] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.415063] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.415065] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.415068] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.415071] pci_bus 0000:00: resource 8 [mem 0x80000000-0xefffffff]
[    0.415073] pci_bus 0000:00: resource 9 [mem 0xf4000000-0xfebfffff]
[    0.415076] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.415079] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.415081] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.415084] pci_bus 0000:00: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.415086] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.415089] pci_bus 0000:00: resource 15 [mem 0xffb00000-0xffefffff]
[    0.415092] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.415094] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfeafffff]
[    0.415097] pci_bus 0000:01: resource 2 [mem 0xf4000000-0xf7ffffff 64bit pref]
[    0.415100] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.415102] pci_bus 0000:0b: resource 1 [mem 0x80000000-0x801fffff]
[    0.415105] pci_bus 0000:0b: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.415108] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.415110] pci_bus 0000:0c: resource 1 [mem 0xf9f00000-0xf9ffffff]
[    0.415113] pci_bus 0000:0c: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.415116] pci_bus 0000:0d: resource 0 [io  0xc000-0xcfff]
[    0.415118] pci_bus 0000:0d: resource 1 [mem 0xf9c00000-0xf9efffff]
[    0.415121] pci_bus 0000:0d: resource 2 [mem 0xf8000000-0xf81fffff 64bit pref]
[    0.415124] pci_bus 0000:03: resource 1 [mem 0xf9b00000-0xf9bfffff]
[    0.415126] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.415129] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.415132] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.415134] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.415137] pci_bus 0000:03: resource 8 [mem 0x80000000-0xefffffff]
[    0.415140] pci_bus 0000:03: resource 9 [mem 0xf4000000-0xfebfffff]
[    0.415142] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.415145] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.415148] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.415150] pci_bus 0000:03: resource 13 [mem 0xfeda7000-0xfedfffff]
[    0.415153] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xff9fffff]
[    0.415155] pci_bus 0000:03: resource 15 [mem 0xffb00000-0xffefffff]
[    0.415202] NET: Registered protocol family 2
[    0.415278] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.415565] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.416046] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.416252] TCP: Hash tables configured (established 131072 bind 65536)
[    0.416254] TCP reno registered
[    0.416258] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.416268] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.416366] NET: Registered protocol family 1
[    0.416580] pci 0000:01:00.0: Boot video device
[    0.416643] PCI: CLS 64 bytes, default 64
[    0.416678] Simple Boot Flag at 0x79 set to 0x1
[    0.416868] cpufreq-nforce2: No nForce2 chipset.
[    0.416902] Scanning for low memory corruption every 60 seconds
[    0.417050] audit: initializing netlink socket (disabled)
[    0.417064] type=2000 audit(1290574654.412:1): initialized
[    0.428198] highmem bounce pool size: 64 pages
[    0.428204] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.429815] VFS: Disk quotas dquot_6.5.2
[    0.429883] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.430522] fuse init (API version 7.14)
[    0.430618] msgmni has been set to 1683
[    0.430992] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.430996] io scheduler noop registered
[    0.430998] io scheduler deadline registered
[    0.431012] io scheduler cfq registered (default)
[    0.431146] pcieport 0000:00:01.0: setting latency timer to 64
[    0.431178]   alloc irq_desc for 40 on node -1
[    0.431180]   alloc kstat_irqs on node -1
[    0.431190] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.431272] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.431323]   alloc irq_desc for 41 on node -1
[    0.431325]   alloc kstat_irqs on node -1
[    0.431335] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.431449] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.431502]   alloc irq_desc for 42 on node -1
[    0.431504]   alloc kstat_irqs on node -1
[    0.431513] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.431623] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.431675]   alloc irq_desc for 43 on node -1
[    0.431677]   alloc kstat_irqs on node -1
[    0.431686] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.431829] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.431953] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.432050] intel_idle: MWAIT substates: 0x22220
[    0.432052] intel_idle: does not run on family 6 model 15
[    0.432188] ACPI: AC Adapter [AC] (on-line)
[    0.432273] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.432748] ACPI: Lid Switch [LID]
[    0.432797] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.432802] ACPI: Power Button [PBTN]
[    0.432849] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.432853] ACPI: Sleep Button [SBTN]
[    0.433161] ACPI: acpi_idle registered with cpuidle
[    0.433418] Monitor-Mwait will be used to enter C-1 state
[    0.435813] Monitor-Mwait will be used to enter C-2 state
[    0.435837] Monitor-Mwait will be used to enter C-3 state
[    0.435843] Marking TSC unstable due to TSC halts in idle
[    0.444027] thermal LNXTHERM:01: registered as thermal_zone0
[    0.444037] ACPI: Thermal Zone [THM] (27 C)
[    0.444089] Switching to clocksource hpet
[    0.444176] ERST: Table is not found!
[    0.444385] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.446057] brd: module loaded
[    0.446654] loop: module loaded
[    0.446850] ata_piix 0000:00:1f.1: version 2.13
[    0.446864] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.446908] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.447004] scsi0 : ata_piix
[    0.447091] scsi1 : ata_piix
[    0.447762] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.447765] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.447787] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.447793] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.460358] isapnp: Scanning for PnP cards...
[    0.477408] ACPI: Battery Slot [BAT0] (battery present)
[    0.477437] ata2: port disabled. ignoring.
[    0.507473] Freeing initrd memory: 10500k freed
[    0.605059] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.605164] scsi2 : ata_piix
[    0.605256] scsi3 : ata_piix
[    0.605943] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    0.605951] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    0.606338] Fixed MDIO Bus: probed
[    0.606381] PPP generic driver version 2.4.2
[    0.606453] tun: Universal TUN/TAP device driver, 1.6
[    0.606455] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.606556] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.606583]   alloc irq_desc for 22 on node -1
[    0.606585]   alloc kstat_irqs on node -1
[    0.606593] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.606614] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.606618] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.606659] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.606691] ehci_hcd 0000:00:1a.7: debug port 1
[    0.610576] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.610592] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.625014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.625141] hub 1-0:1.0: USB hub found
[    0.625147] hub 1-0:1.0: 4 ports detected
[    0.625234]   alloc irq_desc for 20 on node -1
[    0.625236]   alloc kstat_irqs on node -1
[    0.625241] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.625253] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.625257] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.625292] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.625324] ehci_hcd 0000:00:1d.7: debug port 1
[    0.629223] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.629241] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.645015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.645125] hub 2-0:1.0: USB hub found
[    0.645130] hub 2-0:1.0: 6 ports detected
[    0.645215] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.645232] uhci_hcd: USB Universal Host Controller Interface driver
[    0.645270] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.645277] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.645281] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.645316] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.645346] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.645473] hub 3-0:1.0: USB hub found
[    0.645478] hub 3-0:1.0: 2 ports detected
[    0.645549]   alloc irq_desc for 21 on node -1
[    0.645551]   alloc kstat_irqs on node -1
[    0.645556] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.645563] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.645567] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.645609] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.645649] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.645772] hub 4-0:1.0: USB hub found
[    0.645776] hub 4-0:1.0: 2 ports detected
[    0.645850] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.645857] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.645861] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.645897] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.645927] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.646057] hub 5-0:1.0: USB hub found
[    0.646061] hub 5-0:1.0: 2 ports detected
[    0.646134] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.646141] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.646145] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.646179] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.646208] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.646337] hub 6-0:1.0: USB hub found
[    0.646342] hub 6-0:1.0: 2 ports detected
[    0.646415] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.646422] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.646426] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.646460] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.646488] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.646620] hub 7-0:1.0: USB hub found
[    0.646624] hub 7-0:1.0: 2 ports detected
[    0.646769] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.649623] ata1.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
[    0.650234] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.650240] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.650356] mice: PS/2 mouse device common for all mice
[    0.650519] rtc_cmos 00:03: RTC can wake from S4
[    0.650560] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.650593] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.650710] device-mapper: uevent: version 1.0.3
[    0.650824] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.650893] device-mapper: multipath: version 1.1.1 loaded
[    0.650896] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.651015] EISA: Probing bus 0 at eisa.0
[    0.651018] EISA: Cannot allocate resource for mainboard
[    0.651020] Cannot allocate resource for EISA slot 1
[    0.651023] Cannot allocate resource for EISA slot 2
[    0.651025] Cannot allocate resource for EISA slot 3
[    0.651027] Cannot allocate resource for EISA slot 4
[    0.651029] Cannot allocate resource for EISA slot 5
[    0.651031] Cannot allocate resource for EISA slot 6
[    0.651033] Cannot allocate resource for EISA slot 7
[    0.651035] Cannot allocate resource for EISA slot 8
[    0.651037] EISA: Detected 0 cards.
[    0.651191] cpuidle: using governor ladder
[    0.651306] cpuidle: using governor menu
[    0.651650] TCP cubic registered
[    0.651788] NET: Registered protocol family 10
[    0.652191] lo: Disabled Privacy Extensions
[    0.652457] NET: Registered protocol family 17
[    0.653604] Using IPI No-Shortcut mode
[    0.653687] PM: Resume from disk failed.
[    0.653700] registered taskstats version 1
[    0.654144]   Magic number: 2:698:970
[    0.654239] rtc_cmos 00:03: setting system clock to 2010-11-24 04:57:34 UTC (1290574654)
[    0.654243] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.654244] EDD information not available.
[    0.655648] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.729616] ata1.00: configured for UDMA/33
[    0.816779] isapnp: No Plug & Play device found
[    0.819120] scsi 0:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
[    0.830272] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.830277] Uniform CD-ROM driver Revision: 3.20
[    0.830439] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.830525] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.408311] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.408334] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.416621] ata3.00: ATA-7: ST9160821AS, 3.CDE, max UDMA/133
[    1.416626] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.432670] ata3.00: configured for UDMA/133
[    1.432875] scsi 2:0:0:0: Direct-Access     ATA      ST9160821AS      3.CD PQ: 0 ANSI: 5
[    1.433080] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.433099] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.433180] sd 2:0:0:0: [sda] Write Protect is off
[    1.433183] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.433252] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.433582]  sda: sda1 sda2 < sda5 >
[    1.495737] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.960227] ata4.01: failed to resume link (SControl 0)
[    1.960285] ata4.00: SATA link down (SStatus 0 SControl 300)
[    1.960313] ata4.01: SATA link down (SStatus 0 SControl 0)
[    1.960411] Freeing unused kernel memory: 684k freed
[    1.960817] Write protecting the kernel text: 4932k
[    1.960881] Write protecting the kernel read-only data: 1976k
[    1.978977] udev[89]: starting version 163
[    2.157911] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.158678] sdhci: Secure Digital Host Controller Interface driver
[    2.158681] sdhci: Copyright(c) Pierre Ossman
[    2.304056] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
[    2.304108] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    2.304134]   alloc irq_desc for 18 on node -1
[    2.304139]   alloc kstat_irqs on node -1
[    2.304149] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.306234] Registered led device: mmc0::
[    2.307297] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    2.593628] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.796191] firewire_core: created device fw0: GUID 334fc0002ad6b1a1, S400
[   20.791575] udev[382]: starting version 163
[   20.911696] lp: driver loaded but no devices found
[   21.009270] Adding 6142972k swap on /dev/sda5.  Priority:-1 extents:1 across:6142972k 
[   21.024930] lib80211: common routines for IEEE802.11 drivers
[   21.024934] lib80211_crypt: registered algorithm 'NULL'
[   21.025178] Linux agpgart interface v0.103
[   21.069667] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.108394] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   21.175169] r852: driver loaded succesfully
[   21.199278] input: Dell WMI hotkeys as /devices/virtual/input/input4
[   21.225269] wl: module license 'MIXED/Proprietary' taints kernel.
[   21.225272] Disabling lock debugging due to kernel taint
[   21.236926] acpi device:30: registered as cooling_device2
[   21.245532] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.245552] wl 0000:0c:00.0: setting latency timer to 64
[   21.311870] type=1400 audit(1290574675.151:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=690 comm="apparmor_parser"
[   21.312606] type=1400 audit(1290574675.155:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=690 comm="apparmor_parser"
[   21.313019] type=1400 audit(1290574675.155:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=690 comm="apparmor_parser"
[   21.323482] lib80211_crypt: registered algorithm 'TKIP'
[   21.323628] eth0: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   21.349728] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.373041] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   21.373050] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   21.373058] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   21.421266] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   21.421291] b44: b44.c:v2.0
[   21.422299] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   21.422356]   alloc irq_desc for 44 on node -1
[   21.422359]   alloc kstat_irqs on node -1
[   21.422373] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   21.422411] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.441937] b44 ssb0:0: eth1: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:b8:27:87
[   21.541200] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:2d/LNXVIDEO:00/input/input5
[   21.541338] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   21.541398] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   21.553405] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   21.553489] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   21.772791] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000/0x0
[   21.772795] Synaptics: Clickpad mode enabled
[   21.772799] serio: Synaptics pass-through port at isa0060/serio1/input0
[   21.809265] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   22.289465] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.289476] nvidia 0000:01:00.0: setting latency timer to 64
[   22.289482] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   22.289642] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   22.301909] udev[390]: renamed network interface eth0 to eth0-eth1
[   22.317712] udev[389]: renamed network interface eth1 to eth0
[   22.368609] udev[390]: renamed network interface eth0-eth1 to eth1
[   23.004974] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   23.560912] type=1400 audit(1290574677.403:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1004 comm="apparmor_parser"
[   23.561181] type=1400 audit(1290574677.403:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1005 comm="apparmor_parser"
[   23.561932] type=1400 audit(1290574677.403:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1005 comm="apparmor_parser"
[   23.562341] type=1400 audit(1290574677.403:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1005 comm="apparmor_parser"
[   23.566918] type=1400 audit(1290574677.407:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1008 comm="apparmor_parser"
[   23.567827] type=1400 audit(1290574677.407:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1008 comm="apparmor_parser"
[   23.570387] type=1400 audit(1290574677.411:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1006 comm="apparmor_parser"
[   23.686684] ppdev: user-space parallel port driver
[   23.888540] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.641157] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   31.945995] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   34.849014] eth1: no IPv6 routers present
[ 1053.776192] usb 2-2: new high speed USB device using ehci_hcd and address 2
[ 1054.000293] Initializing USB Mass Storage driver...
[ 1054.000451] scsi4 : usb-storage 2-2:1.0
[ 1054.000556] usbcore: registered new interface driver usb-storage
[ 1054.000558] USB Mass Storage support registered.
[ 1055.001574] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1055.002989] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1057.454374] sd 4:0:0:0: [sdb] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 1057.455851] sd 4:0:0:0: [sdb] Write Protect is off
[ 1057.455860] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1057.455866] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1057.458862] sd 4:0:0:0: [sdb] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 1057.459966] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1057.459980]  sdb: sdb1 sdb2
[ 1057.471370] sd 4:0:0:0: [sdb] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 1057.472736] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1057.472749] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1058.231859] FAT: invalid media value (0x2f)
[ 1058.231867] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 1206.730444] usb 2-2: USB disconnect, address 2
[ 1348.880151] usb 2-2: new high speed USB device using ehci_hcd and address 3
[ 1349.016250] scsi5 : usb-storage 2-2:1.0
[ 1350.017518] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1350.021726] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 1352.524542] sd 5:0:0:0: [sdc] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 1352.525785] sd 5:0:0:0: [sdc] Write Protect is off
[ 1352.525789] sd 5:0:0:0: [sdc] Mode Sense: 68 00 00 08
[ 1352.525791] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1352.527807] sd 5:0:0:0: [sdc] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 1352.528924] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1352.528934]  sdc: sdc1 sdc2
[ 1352.544788] sd 5:0:0:0: [sdc] 14651280 2048-byte logical blocks: (30.0 GB/27.9 GiB)
[ 1352.546057] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1352.546063] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[ 1353.191684] FAT: invalid media value (0x2f)
[ 1353.191689] VFS: Can't find a valid FAT filesystem on dev sdc1.
b3d3g1@b3d3g1-Vostro-1500:~$

---

### Post by NoBugs! on 2010-11-24
Some of the newer ipods have the new database format that doesn't work with Linux...
You might find some useful info here:
[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

---

### Post by b3d3g1 on 2010-11-24
It is not even showing up in /mnt/ipod 
from what I can find, the ipod needs to show up there

---

