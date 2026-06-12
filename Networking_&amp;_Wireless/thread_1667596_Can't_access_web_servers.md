---
title: "Can't access web servers"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by r5r4y on 2011-01-15
Hello, 
I've a very simple network setup [Dial-up connection, no router/switch]...

I'm using my ISP scripts to connect to the internet: [http://212.25.77.173/linux/files/cbezint.tar](http://212.25.77.173/linux/files/cbezint.tar)

Recently I've been trying to connect to L2TP through those scripts here: [http://stuff.pulkes.org/l2tp/](http://stuff.pulkes.org/l2tp/)

It didn't go so well so I tried to connect with my ISP script again, I'm getting good IP, ppp0 is created but I can't access web servers at all or sending pings when sending ping I'm getting the error: network is unreachable...

route -n:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
212.25.127.8    172.28.232.1    255.255.255.255 UGH   0      0        0 eth0
212.25.114.110  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.28.232.0    0.0.0.0         255.255.248.0   U     0      0        0 eth0

```


lspci:

```

00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV790 [Radeon HD 4800 Series]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

dmesg:

```

[    0.717769] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.718035] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.718038] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.718040] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.718042] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.718044] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
[    0.718046] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfed44fff]
[    0.718070] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.718131] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.718134] pci 0000:00:02.0: PME# disabled
[    0.718175] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.718178] pci 0000:00:06.0: PME# disabled
[    0.718223] pci 0000:00:12.0: reg 10: [io  0xc000-0xc007]
[    0.718230] pci 0000:00:12.0: reg 14: [io  0xb000-0xb003]
[    0.718237] pci 0000:00:12.0: reg 18: [io  0xa000-0xa007]
[    0.718243] pci 0000:00:12.0: reg 1c: [io  0x9000-0x9003]
[    0.718250] pci 0000:00:12.0: reg 20: [io  0x8000-0x800f]
[    0.718257] pci 0000:00:12.0: reg 24: [mem 0xfe9ff800-0xfe9ffbff]
[    0.718276] pci 0000:00:12.0: set SATA to AHCI mode
[    0.718314] pci 0000:00:13.0: reg 10: [mem 0xfe9fe000-0xfe9fefff]
[    0.718370] pci 0000:00:13.1: reg 10: [mem 0xfe9fd000-0xfe9fdfff]
[    0.718428] pci 0000:00:13.2: reg 10: [mem 0xfe9fc000-0xfe9fcfff]
[    0.718484] pci 0000:00:13.3: reg 10: [mem 0xfe9fb000-0xfe9fbfff]
[    0.718539] pci 0000:00:13.4: reg 10: [mem 0xfe9fa000-0xfe9fafff]
[    0.718608] pci 0000:00:13.5: reg 10: [mem 0xfe9ff000-0xfe9ff0ff]
[    0.718662] pci 0000:00:13.5: supports D1 D2
[    0.718664] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.718668] pci 0000:00:13.5: PME# disabled
[    0.718709] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
[    0.718778] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.718784] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.718791] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.718798] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.718804] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.718854] pci 0000:00:14.2: reg 10: [mem 0xfe9f4000-0xfe9f7fff 64bit]
[    0.718899] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.718903] pci 0000:00:14.2: PME# disabled
[    0.719137] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.719145] pci 0000:01:00.0: reg 18: [mem 0xfeaf0000-0xfeafffff 64bit]
[    0.719150] pci 0000:01:00.0: reg 20: [io  0xd000-0xd0ff]
[    0.719159] pci 0000:01:00.0: reg 30: [mem 0xfeac0000-0xfeadffff pref]
[    0.719177] pci 0000:01:00.0: supports D1 D2
[    0.719205] pci 0000:01:00.1: reg 10: [mem 0xfeaec000-0xfeaeffff 64bit]
[    0.719239] pci 0000:01:00.1: supports D1 D2
[    0.730014] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.730018] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.730021] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.730025] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.730081] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.730098] pci 0000:02:00.0: reg 18: [mem 0xfebff000-0xfebfffff 64bit]
[    0.730116] pci 0000:02:00.0: reg 30: [mem 0xfebc0000-0xfebdffff pref]
[    0.730153] pci 0000:02:00.0: supports D1 D2
[    0.730155] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.730159] pci 0000:02:00.0: PME# disabled
[    0.730177] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.730185] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.730188] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    0.730191] pci 0000:00:06.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.730195] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.730260] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.730265] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.730269] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.730274] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.730276] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.730278] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.730280] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.730283] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.730285] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.730287] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfed44fff] (subtractive decode)
[    0.730302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.730493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.730547] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.730628] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.734543] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.734634] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.734724] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.734811] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.734900] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.734986] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.735075] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.735161] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.735194] HEST: Table is not found!
[    0.735261] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.735264] vgaarb: loaded
[    0.735376] SCSI subsystem initialized
[    0.735391] libata version 3.00 loaded.
[    0.735391] usbcore: registered new interface driver usbfs
[    0.735391] usbcore: registered new interface driver hub
[    0.735391] usbcore: registered new device driver usb
[    0.735391] ACPI: WMI: Mapper loaded
[    0.735391] PCI: Using ACPI for IRQ routing
[    0.735391] PCI: pci_cache_line_size set to 64 bytes
[    0.735391] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.735391] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.735391] reserve RAM buffer: 00000000cffb0000 - 00000000cfffffff 
[    0.735391] NetLabel: Initializing
[    0.735391] NetLabel:  domain hash size = 128
[    0.735391] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.735391] NetLabel:  unlabeled traffic allowed by default
[    0.735391] Switching to clocksource tsc
[    0.736554] AppArmor: AppArmor Filesystem Enabled
[    0.736569] pnp: PnP ACPI init
[    0.736586] ACPI: bus type pnp registered
[    0.738741] pnp 00:0c: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.738744] pnp 00:0c: disabling [mem 0x000c0000-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.738748] pnp 00:0c: disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.738751] pnp 00:0c: disabling [mem 0x00100000-0xcfffffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.739008] pnp: PnP ACPI: found 13 devices
[    0.739009] ACPI: ACPI bus type pnp unregistered
[    0.739021] system 00:06: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.739023] system 00:06: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.739028] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.739030] system 00:07: [io  0x040b] has been reserved
[    0.739032] system 00:07: [io  0x04d6] has been reserved
[    0.739034] system 00:07: [io  0x0c00-0x0c01] has been reserved
[    0.739036] system 00:07: [io  0x0c14] has been reserved
[    0.739038] system 00:07: [io  0x0c50-0x0c51] has been reserved
[    0.739040] system 00:07: [io  0x0c52] has been reserved
[    0.739042] system 00:07: [io  0x0c6c] has been reserved
[    0.739044] system 00:07: [io  0x0c6f] has been reserved
[    0.739046] system 00:07: [io  0x0cd0-0x0cd1] has been reserved
[    0.739048] system 00:07: [io  0x0cd2-0x0cd3] has been reserved
[    0.739050] system 00:07: [io  0x0cd4-0x0cd5] has been reserved
[    0.739052] system 00:07: [io  0x0cd6-0x0cd7] has been reserved
[    0.739054] system 00:07: [io  0x0cd8-0x0cdf] has been reserved
[    0.739056] system 00:07: [io  0x0800-0x089f] has been reserved
[    0.739058] system 00:07: [io  0x0b10-0x0b1f] has been reserved
[    0.739061] system 00:07: [io  0x0900-0x090f] has been reserved
[    0.739063] system 00:07: [io  0x0910-0x091f] has been reserved
[    0.739065] system 00:07: [io  0xfe00-0xfefe] has been reserved
[    0.739067] system 00:07: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.739069] system 00:07: [mem 0xfff00000-0xffffffff] has been reserved
[    0.739074] system 00:0a: [io  0x0600-0x06df] has been reserved
[    0.739076] system 00:0a: [io  0x0ae0-0x0aef] has been reserved
[    0.739080] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.739084] system 00:0c: [mem 0xfed45000-0xffffffff] could not be reserved
[    0.744643] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.744646] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.744650] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.744653] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.744657] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.744659] pci 0000:00:06.0:   bridge window [io  0xe000-0xefff]
[    0.744662] pci 0000:00:06.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.744664] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.744668] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.744669] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.744674] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.744678] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.744692] pci 0000:00:02.0: setting latency timer to 64
[    0.744697] pci 0000:00:06.0: setting latency timer to 64
[    0.744705] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.744707] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.744709] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.744710] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.744712] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.744714] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.744716] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.744718] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.744720] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.744722] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.744723] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.744726] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.744727] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.744729] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.744731] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.744733] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.744735] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfed44fff]
[    0.744765] NET: Registered protocol family 2
[    0.744904] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.746005] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.748896] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.749250] TCP: Hash tables configured (established 524288 bind 65536)
[    0.749253] TCP reno registered
[    0.749265] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.749299] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.749407] NET: Registered protocol family 1
[    0.894108] pci 0000:01:00.0: Boot video device
[    0.894116] PCI: CLS 64 bytes, default 64
[    0.894844] PCI-DMA: Disabling AGP.
[    0.894944] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.894946] PCI-DMA: using GART IOMMU.
[    0.894949] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.898497] Scanning for low memory corruption every 60 seconds
[    0.898610] audit: initializing netlink socket (disabled)
[    0.898627] type=2000 audit(1295093810.890:1): initialized
[    0.909229] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.910345] VFS: Disk quotas dquot_6.5.2
[    0.910395] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.910851] fuse init (API version 7.14)
[    0.910910] msgmni has been set to 7897
[    0.911397] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.911400] io scheduler noop registered
[    0.911401] io scheduler deadline registered
[    0.911429] io scheduler cfq registered (default)
[    0.911529] pcieport 0000:00:02.0: setting latency timer to 64
[    0.911552]   alloc irq_desc for 40 on node 0
[    0.911554]   alloc kstat_irqs on node 0
[    0.911562] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.911639] pcieport 0000:00:06.0: setting latency timer to 64
[    0.911659]   alloc irq_desc for 41 on node 0
[    0.911660]   alloc kstat_irqs on node 0
[    0.911665] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    0.911740] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.911759] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.911904] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.911915] ACPI: Power Button [PWRB]
[    0.911946] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.911949] ACPI: Power Button [PWRF]
[    0.912199] ACPI: acpi_idle registered with cpuidle
[    0.912217] ACPI: duty_cycle spans bit 4
[    0.913715] ERST: Table is not found!
[    0.913810] Linux agpgart interface v0.103
[    0.913813] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.913922] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.914177] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.914972] brd: module loaded
[    0.915312] loop: module loaded
[    0.915501]   alloc irq_desc for 16 on node 0
[    0.915502]   alloc kstat_irqs on node 0
[    0.915507] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.915536] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.915809] Fixed MDIO Bus: probed
[    0.915836] PPP generic driver version 2.4.2
[    0.915884] tun: Universal TUN/TAP device driver, 1.6
[    0.915885] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.915948] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.915982]   alloc irq_desc for 19 on node 0
[    0.915984]   alloc kstat_irqs on node 0
[    0.915987] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.916006] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.916050] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.916077] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.916090] ehci_hcd 0000:00:13.5: debug port 1
[    0.916110] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe9ff000
[    0.933178] Freeing initrd memory: 10748k freed
[    0.934064] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.934171] hub 1-0:1.0: USB hub found
[    0.934177] hub 1-0:1.0: 10 ports detected
[    0.934264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.934305] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.934316] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.934346] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.934367] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe9fe000
[    0.998158] hub 2-0:1.0: USB hub found
[    0.998164] hub 2-0:1.0: 2 ports detected
[    0.998247]   alloc irq_desc for 17 on node 0
[    0.998248]   alloc kstat_irqs on node 0
[    0.998253] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.998262] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.998289] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.998307] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe9fd000
[    1.058166] hub 3-0:1.0: USB hub found
[    1.058171] hub 3-0:1.0: 2 ports detected
[    1.058257]   alloc irq_desc for 18 on node 0
[    1.058258]   alloc kstat_irqs on node 0
[    1.058261] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.058270] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    1.058295] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    1.058313] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe9fc000
[    1.118153] hub 4-0:1.0: USB hub found
[    1.118158] hub 4-0:1.0: 2 ports detected
[    1.118239] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.118247] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    1.118271] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    1.118282] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe9fb000
[    1.178158] hub 5-0:1.0: USB hub found
[    1.178163] hub 5-0:1.0: 2 ports detected
[    1.178249] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.178259] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    1.178285] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    1.178297] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe9fa000
[    1.238153] hub 6-0:1.0: USB hub found
[    1.238158] hub 6-0:1.0: 2 ports detected
[    1.238220] uhci_hcd: USB Universal Host Controller Interface driver
[    1.238309] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.240715] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.240719] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.240769] mice: PS/2 mouse device common for all mice
[    1.240847] rtc_cmos 00:02: RTC can wake from S4
[    1.240878] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.240899] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.240977] device-mapper: uevent: version 1.0.3
[    1.241032] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.241131] device-mapper: multipath: version 1.1.1 loaded
[    1.241133] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.241353] cpuidle: using governor ladder
[    1.241355] cpuidle: using governor menu
[    1.241625] TCP cubic registered
[    1.241739] NET: Registered protocol family 10
[    1.242056] lo: Disabled Privacy Extensions
[    1.242246] NET: Registered protocol family 17
[    1.242273] powernow-k8: Found 1 AMD Phenom(tm) 9950 Quad-Core Processor (4 cpu cores) (version 2.20.00)
[    1.242282] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.242283] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.242360] PM: Resume from disk failed.
[    1.242370] registered taskstats version 1
[    1.242577]   Magic number: 11:87:279
[    1.242604] tty tty16: hash matches
[    1.242654] rtc_cmos 00:02: setting system clock to 2011-01-15 12:16:52 UTC (1295093812)
[    1.242656] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.242658] EDD information not available.
[    1.242714] Freeing unused kernel memory: 908k freed
[    1.243003] Write protecting the kernel read-only data: 10240k
[    1.243145] Freeing unused kernel memory: 416k freed
[    1.243377] Freeing unused kernel memory: 1644k freed
[    1.256967] udev[131]: starting version 163
[    1.258015] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.281584] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.281798] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.281979] r8169 0000:02:00.0: setting latency timer to 64
[    1.282045]   alloc irq_desc for 42 on node 0
[    1.282047]   alloc kstat_irqs on node 0
[    1.282061] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.285437] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xffffc9000067e000, 00:1d:92:da:01:34, XID 18000000 IRQ 42
[    1.287716] scsi0 : pata_atiixp
[    1.291058] scsi1 : pata_atiixp
[    1.292189] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.292192] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.299377] ahci 0000:00:12.0: version 3.0
[    1.299401]   alloc irq_desc for 22 on node 0
[    1.299403]   alloc kstat_irqs on node 0
[    1.299412] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.299457] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.299544] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.299548] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.303177] scsi2 : ahci
[    1.303286] scsi3 : ahci
[    1.303347] scsi4 : ahci
[    1.303398] scsi5 : ahci
[    1.303488] ata3: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ff900 irq 22
[    1.303492] ata4: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ff980 irq 22
[    1.303495] ata5: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ffa00 irq 22
[    1.303498] ata6: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ffa80 irq 22
[    1.654197] ata6: SATA link down (SStatus 0 SControl 300)
[    1.654210] ata3: SATA link down (SStatus 0 SControl 300)
[    1.840023] ata4: softreset failed (device not ready)
[    1.840027] ata4: applying SB600 PMP SRST workaround and retrying
[    1.840041] ata5: softreset failed (device not ready)
[    1.840044] ata5: applying SB600 PMP SRST workaround and retrying
[    2.020034] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.020059] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.021675] ata4.00: ATA-8: ST3500320AS, SD1A, max UDMA/133
[    2.021678] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.021690] ata5.00: ATAPI: Optiarc DVD RW AD-7240S, 1.03, max UDMA/100
[    2.021692] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.021710] ata5.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.023700] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.023702] ata5.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.023705] ata5.00: configured for UDMA/100
[    2.023707] ata4.00: configured for UDMA/133
[    2.040194] scsi 3:0:0:0: Direct-Access     ATA      ST3500320AS      SD1A PQ: 0 ANSI: 5
[    2.040345] sd 3:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.040356] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    2.040378] sd 3:0:0:0: [sda] Write Protect is off
[    2.040381] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.040396] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.040520]  sda:
[    2.041547] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7240S  1.03 PQ: 0 ANSI: 5
[    2.045929] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.045931] Uniform CD-ROM driver Revision: 3.20
[    2.046015] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.046061] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.053527]  sda1 sda2 sda3 < sda5 sda6 >
[    2.081223] sd 3:0:0:0: [sda] Attached SCSI disk
[    2.497171] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   14.364027] udev[407]: starting version 163
[   14.398997] lp: driver loaded but no devices found
[   14.414557] k10temp 0000:00:18.3: unreliable CPU thermal sensor; monitoring disabled
[   14.416250] Adding 2555900k swap on /dev/sda6.  Priority:-1 extents:1 across:2555900k 
[   14.428063] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   14.428068] Disabling lock debugging due to kernel taint
[   14.431437] EDAC MC: Ver: 2.1.0 Oct 16 2010
[   14.440178] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io  0x0b00-0x0b0f 64bit window]
[   14.440182] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.478555] EDAC amd64_edac:  Ver: 3.3.0 Oct 16 2010
[   14.483238] type=1400 audit(1295086625.736:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=670 comm="apparmor_parser"
[   14.483235] type=1400 audit(1295086625.736:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=634 comm="apparmor_parser"
[   14.483465] type=1400 audit(1295086625.736:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=670 comm="apparmor_parser"
[   14.483466] type=1400 audit(1295086625.736:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=634 comm="apparmor_parser"
[   14.483592] type=1400 audit(1295086625.736:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=670 comm="apparmor_parser"
[   14.483608] type=1400 audit(1295086625.736:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=634 comm="apparmor_parser"
[   14.490937] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   14.490946] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   14.490948]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   14.490949]  (Note that use of the override may cause unknown side effects.)
[   14.490992] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   14.509363] [fglrx] Maximum main memory to use for locked dma buffers: 3800 MBytes.
[   14.509534] [fglrx]   vendor: 1002 device: 9460 count: 1
[   14.509858] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[   14.509873] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.509877] pci 0000:01:00.0: setting latency timer to 64
[   14.510069] [fglrx] Kernel PAT support is enabled
[   14.510091] [fglrx] module loaded - fglrx 8.80.5 [Nov 25 2010] with 1 minors
[   14.542624] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.620848] hda_codec: ALC888: BIOS auto-probing.
[   14.630560] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   14.630619]   alloc irq_desc for 43 on node 0
[   14.630621]   alloc kstat_irqs on node 0
[   14.630631] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[   14.630657] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.955384] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.251019] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   15.282504] type=1400 audit(1295086626.536:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=952 comm="apparmor_parser"
[   15.282799] type=1400 audit(1295086626.536:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=952 comm="apparmor_parser"
[   15.296720] r8169 0000:02:00.0: eth0: link up
[   15.296732] r8169 0000:02:00.0: eth0: link up
[   15.297169] ppdev: user-space parallel port driver
[   15.311393] type=1400 audit(1295086626.566:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1061 comm="apparmor_parser"
[   15.311980] type=1400 audit(1295086626.566:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1060 comm="apparmor_parser"
[   15.699526]   alloc irq_desc for 44 on node 0
[   15.699530]   alloc kstat_irqs on node 0
[   15.699542] fglrx_pci 0000:01:00.0: irq 44 for MSI/MSI-X
[   15.700126] [fglrx] Firegl kernel thread PID: 1163
[   15.700366] [fglrx] IRQ 44 Enabled
[   16.953927] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   17.272810] [fglrx] Gart USWC size:1240 M.
[   17.272813] [fglrx] Gart cacheable size:491 M.
[   17.272818] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   17.272820] [fglrx] Reserved FB block: Unshared offset:fc1f000, size:3e1000 
[   17.272822] [fglrx] Reserved FB block: Unshared offset:3fffb000, size:5000 
[   20.041356] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   20.543706] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[  100.262700] PPP BSD Compression module registered
[  100.292611] PPP Deflate Compression module registered

```

ifconfig -a:

```

eth0  
          inet addr:172.28.233.12  Bcast:255.255.255.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:262369 (262.3 KB)  TX bytes:8724 (8.7 KB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:192 (192.0 B)  TX bytes:192 (192.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:84.110.57.146  P-t-P:212.25.114.110  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1410  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:64 (64.0 B)  TX bytes:97 (97.0 B)


```

Also I already deleted all the changes I did in the L2TP scripts but still I can't access the web...
Ohh... and I'm using ubuntu 10.10. 

Thanks.

---

### Post by ripat on 2011-01-15
Post result of:

```
$ cat /etc/resolv.conf
$ dig google.com
$ dig @8.8.8.8 google.com
```

---

### Post by r5r4y on 2011-01-15
cat /etc/resolv.conf

```
nameserver 62.219.186.7
nameserver 192.115.106.35
```

dig google.com

```

; <<>> DiG 9.7.1-P2 <<>> google.com
;; global options: +cmd
;; connection timed out; no servers could be reached

```

dig 8.8.8.8 google.com

```

; <<>> DiG 9.7.1-P2 <<>> 8.8.8.8 google.com
;; global options: +cmd
;; connection timed out; no servers could be reached
;; connection timed out; no servers could be reached

```

also here is the dhclient output:

```

sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1d:92:da:01:34
Sending on   LPF/eth0/00:1d:92:da:01:34
Sending on   Socket/fallback
DHCPREQUEST of 172.28.233.12 on eth0 to 255.255.255.255 port 67
DHCPACK of 172.28.233.12 from 10.181.192.1
bound to 172.28.233.12 -- renewal in 285040 seconds.

```

---

### Post by r5r4y on 2011-01-15
Bump

---

### Post by r5r4y on 2011-01-15
Bump

---

### Post by r5r4y on 2011-01-15
*bump*

---

### Post by ripat on 2011-01-15
Your gateway seems to be on another sub-net.

---

### Post by ripat on 2011-01-15
Your gateway seems to be on another subnet. Check your routing tables and netmask.

---

### Post by r5r4y on 2011-01-15
> **ripat said:**
> Your gateway seems to be on another sub-net.

OK, So how can I fix this?

---

### Post by ripat on 2011-01-16
I stand corrected. Subnet calculation is not my forte. After checking it seems that both your host's ip and your gateway _are_ on the same subnet. A netmask of 255.255.248.0 produces a subnet ip range of: 172.28.232.1 - 172.28.239.254

Can you ping your gateway (172.28.232.1)? Not sure about the genmask of your route to the gateway. Do you build the routing table using a script or you let the dhclient building it?

Try running:
```
$ sudo dhclient -v
```and check if your routing table changes.
```
$ sudo route -n
```
or
```
$ ip route show
```

---

