---
title: "Wireless rtl819x driver issues"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by GreigKM on 2010-01-10
I have recently installed Ubuntu on my new laptop. Everything works fine except for the wifi. I have a rtl8191se and am using the rtl819x driver. The problem is whenever I reboot it stops working, the driver is listed as active in Hardware Drivers but Ubuntu lists no wireless networks. After disabling and re-enabling the driver it works for a bit but cuts out after about one minuet, but never lists my signal as low. So what can I do? I am running Ubuntu 9.10 x86_64.

---

### Post by Crafty Kisses on 2010-01-10
What are the results of the following commands?
```
lspci -nn
dmesg
```

---

### Post by GreigKM on 2010-01-10
lspci -nn:
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a28] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0be2] (rev a1)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
04:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
04:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
04:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
04:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01)
```

dmesg:
```
[    1.080007] Switched to high resolution mode on CPU 0
[    1.081609] Switched to high resolution mode on CPU 1
[    1.100008] pnp: PnP ACPI init
[    1.100017] ACPI: bus type pnp registered
[    1.104120] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.4 BAR 13 (0x1000-0x1fff), disabling
[    1.104995] pnp: PnP ACPI: found 8 devices
[    1.104997] ACPI: ACPI bus type pnp unregistered
[    1.105007] system 00:01: ioport range 0x800-0x80f has been reserved
[    1.105010] system 00:01: ioport range 0x810-0x817 has been reserved
[    1.105013] system 00:01: ioport range 0x820-0x823 has been reserved
[    1.105015] system 00:01: ioport range 0x400-0x47f has been reserved
[    1.105018] system 00:01: ioport range 0x500-0x57f has been reserved
[    1.105021] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    1.105024] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.105026] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
[    1.105029] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.105032] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.105034] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    1.105037] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    1.105040] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    1.105043] system 00:01: iomem range 0xff800000-0xffffffff could not be reserved
[    1.109711] AppArmor: AppArmor Filesystem Enabled
[    1.109727] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfff80000-0xffffffff]
[    1.109731] pci 0000:02:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    1.109782] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.109785] pci 0000:00:01.0:   IO window: 0x7000-0x7fff
[    1.109788] pci 0000:00:01.0:   MEM window: 0xd2000000-0xd30fffff
[    1.109792] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000d1ffffff
[    1.109797] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.109800] pci 0000:00:1c.0:   IO window: 0x5000-0x6fff
[    1.109805] pci 0000:00:1c.0:   MEM window: 0xda400000-0xdb3fffff
[    1.109810] pci 0000:00:1c.0:   PREFETCH window: 0x000000d3100000-0x000000d41fffff
[    1.109818] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    1.109821] pci 0000:00:1c.1:   IO window: 0x3000-0x4fff
[    1.109826] pci 0000:00:1c.1:   MEM window: 0xd9300000-0xda3fffff
[    1.109830] pci 0000:00:1c.1:   PREFETCH window: 0x000000d4200000-0x000000d51fffff
[    1.109838] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    1.109842] pci 0000:00:1c.3:   IO window: 0x2000-0x2fff
[    1.109847] pci 0000:00:1c.3:   MEM window: 0xd8200000-0xd92fffff
[    1.109852] pci 0000:00:1c.3:   PREFETCH window: 0x000000d5200000-0x000000d61fffff
[    1.109859] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    1.109862] pci 0000:00:1c.4:   IO window: 0x1000-0x1fff
[    1.109868] pci 0000:00:1c.4:   MEM window: 0xd7200000-0xd81fffff
[    1.109872] pci 0000:00:1c.4:   PREFETCH window: 0x000000d6200000-0x000000d71fffff
[    1.109879] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    1.109880] pci 0000:00:1e.0:   IO window: disabled
[    1.109886] pci 0000:00:1e.0:   MEM window: disabled
[    1.109890] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.109898]   alloc irq_desc for 16 on node 0
[    1.109900]   alloc kstat_irqs on node 0
[    1.109905] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.109909] pci 0000:00:01.0: setting latency timer to 64
[    1.109915]   alloc irq_desc for 17 on node 0
[    1.109917]   alloc kstat_irqs on node 0
[    1.109920] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.109924] pci 0000:00:1c.0: setting latency timer to 64
[    1.109932] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.109936] pci 0000:00:1c.1: setting latency timer to 64
[    1.109944]   alloc irq_desc for 19 on node 0
[    1.109945]   alloc kstat_irqs on node 0
[    1.109948] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.109952] pci 0000:00:1c.3: setting latency timer to 64
[    1.109959] pci 0000:00:1c.4: enabling device (0000 -> 0003)
[    1.109963] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.109968] pci 0000:00:1c.4: setting latency timer to 64
[    1.109975] pci 0000:00:1e.0: setting latency timer to 64
[    1.109978] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.109981] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    1.109983] pci_bus 0000:01: resource 0 io:  [0x7000-0x7fff]
[    1.109985] pci_bus 0000:01: resource 1 mem: [0xd2000000-0xd30fffff]
[    1.109988] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xd1ffffff]
[    1.109990] pci_bus 0000:02: resource 0 io:  [0x5000-0x6fff]
[    1.109992] pci_bus 0000:02: resource 1 mem: [0xda400000-0xdb3fffff]
[    1.109994] pci_bus 0000:02: resource 2 pref mem [0xd3100000-0xd41fffff]
[    1.109996] pci_bus 0000:03: resource 0 io:  [0x3000-0x4fff]
[    1.110006] pci_bus 0000:03: resource 1 mem: [0xd9300000-0xda3fffff]
[    1.110008] pci_bus 0000:03: resource 2 pref mem [0xd4200000-0xd51fffff]
[    1.110010] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    1.110012] pci_bus 0000:04: resource 1 mem: [0xd8200000-0xd92fffff]
[    1.110014] pci_bus 0000:04: resource 2 pref mem [0xd5200000-0xd61fffff]
[    1.110016] pci_bus 0000:07: resource 0 io:  [0x1000-0x1fff]
[    1.110018] pci_bus 0000:07: resource 1 mem: [0xd7200000-0xd81fffff]
[    1.110021] pci_bus 0000:07: resource 2 pref mem [0xd6200000-0xd71fffff]
[    1.110023] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    1.110025] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    1.110053] NET: Registered protocol family 2
[    1.110291] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.111698] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.115684] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.116186] TCP: Hash tables configured (established 524288 bind 65536)
[    1.116189] TCP reno registered
[    1.116312] NET: Registered protocol family 1
[    1.116374] Trying to unpack rootfs image as initramfs...
[    1.288219] Freeing initrd memory: 7688k freed
[    1.291207] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.291210] Simple Boot Flag at 0x44 set to 0x1
[    1.291389] Scanning for low memory corruption every 60 seconds
[    1.291528] audit: initializing netlink socket (disabled)
[    1.291544] type=2000 audit(1263160347.290:1): initialized
[    1.301079] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.302417] VFS: Disk quotas dquot_6.5.2
[    1.302469] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.302994] fuse init (API version 7.12)
[    1.303068] msgmni has been set to 11965
[    1.303254] alg: No test for stdrng (krng)
[    1.303266] io scheduler noop registered
[    1.303268] io scheduler anticipatory registered
[    1.303270] io scheduler deadline registered
[    1.303309] io scheduler cfq registered (default)
[    3.300006] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    5.300005] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    5.300134] pci 0000:01:00.0: Boot video device
[    5.300271]   alloc irq_desc for 24 on node 0
[    5.300273]   alloc kstat_irqs on node 0
[    5.300281] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    5.300287] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    5.300428]   alloc irq_desc for 25 on node 0
[    5.300430]   alloc kstat_irqs on node 0
[    5.300439] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    5.300449] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    5.300619]   alloc irq_desc for 26 on node 0
[    5.300621]   alloc kstat_irqs on node 0
[    5.300629] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    5.300640] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    5.300801]   alloc irq_desc for 27 on node 0
[    5.300803]   alloc kstat_irqs on node 0
[    5.300811] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    5.300822] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    5.300986]   alloc irq_desc for 28 on node 0
[    5.300988]   alloc kstat_irqs on node 0
[    5.300996] pcieport-driver 0000:00:1c.4: irq 28 for MSI/MSI-X
[    5.301006] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    5.301109] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    5.301448] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    5.301629] ACPI: AC Adapter [ADP0] (on-line)
[    5.301704] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    5.301708] ACPI: Power Button [PWRF]
[    5.301754] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    5.301756] ACPI: Power Button [PWRB]
[    5.301795] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    5.304034] ACPI: Lid Switch [LID0]
[    5.304228] fan PNP0C0B:00: registered as cooling_device0
[    5.304233] ACPI: Fan [FAN] (on)
[    5.305384] ACPI: SSDT 00000000bfd77c98 00229 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    5.306009] ACPI: SSDT 00000000bfd75598 00537 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    5.306556] Monitor-Mwait will be used to enter C-1 state
[    5.306581] Monitor-Mwait will be used to enter C-2 state
[    5.306601] Monitor-Mwait will be used to enter C-3 state
[    5.306608] Marking TSC unstable due to TSC halts in idle
[    5.306625] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    5.306641] processor LNXCPU:00: registered as cooling_device1
[    5.306645] ACPI: Processor [CPU0] (supports 8 throttling states)
[    5.307196] ACPI: SSDT 00000000bfd76e18 001CF (v01  PmRef    ApIst 00003000 INTL 20051117)
[    5.307728] ACPI: SSDT 00000000bfd77f18 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    5.308433] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    5.308451] processor LNXCPU:01: registered as cooling_device2
[    5.308455] ACPI: Processor [CPU1] (supports 8 throttling states)
[    5.315071] thermal LNXTHERM:01: registered as thermal_zone0
[    5.315078] ACPI: Thermal Zone [THRM] (48 C)
[    5.316220] Linux agpgart interface v0.103
[    5.316227] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    5.317292] brd: module loaded
[    5.317691] loop: module loaded
[    5.317754] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    5.319026] ACPI: Battery Slot [BAT0] (battery present)
[    5.319072] ahci 0000:00:1f.2: version 3.0
[    5.319085] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.319122]   alloc irq_desc for 29 on node 0
[    5.319123]   alloc kstat_irqs on node 0
[    5.319133] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    5.319207] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    5.319210] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part 
[    5.319215] ahci 0000:00:1f.2: setting latency timer to 64
[    5.319443] scsi0 : ahci
[    5.319516] scsi1 : ahci
[    5.319564] scsi2 : ahci
[    5.319608] scsi3 : ahci
[    5.319653] scsi4 : ahci
[    5.319702] scsi5 : ahci
[    5.319990] ata1: SATA max UDMA/133 abar m2048@0xdb404000 port 0xdb404100 irq 29
[    5.319993] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 29
[    5.319995] ata3: DUMMY
[    5.319997] ata4: DUMMY
[    5.319999] ata5: SATA max UDMA/133 abar m2048@0xdb404000 port 0xdb404300 irq 29
[    5.320015] ata6: SATA max UDMA/133 irq_stat 0x00000040 irq 29, connection status changed
[    5.320865] Fixed MDIO Bus: probed
[    5.320894] PPP generic driver version 2.4.2
[    5.320971] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.321023] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    5.321035] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.321039] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.321084] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    5.325007] ehci_hcd 0000:00:1a.7: debug port 1
[    5.325013] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    5.325026] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xdb404c00
[    5.340020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.340089] usb usb1: configuration #1 chosen from 1 choice
[    5.340113] hub 1-0:1.0: USB hub found
[    5.340121] hub 1-0:1.0: 4 ports detected
[    5.340203]   alloc irq_desc for 23 on node 0
[    5.340205]   alloc kstat_irqs on node 0
[    5.340209] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.340219] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.340222] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.340250] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.344141] ehci_hcd 0000:00:1d.7: debug port 1
[    5.344147] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.344158] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xdb404800
[    5.360012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.360063] usb usb2: configuration #1 chosen from 1 choice
[    5.360086] hub 2-0:1.0: USB hub found
[    5.360091] hub 2-0:1.0: 8 ports detected
[    5.360159] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.360174] uhci_hcd: USB Universal Host Controller Interface driver
[    5.360241] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.360248] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.360251] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.360279] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    5.360312] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080e0
[    5.360382] usb usb3: configuration #1 chosen from 1 choice
[    5.360404] hub 3-0:1.0: USB hub found
[    5.360411] hub 3-0:1.0: 2 ports detected
[    5.360489]   alloc irq_desc for 21 on node 0
[    5.360491]   alloc kstat_irqs on node 0
[    5.360495] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.360501] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.360504] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.360533] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    5.360565] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000080c0
[    5.360630] usb usb4: configuration #1 chosen from 1 choice
[    5.360655] hub 4-0:1.0: USB hub found
[    5.360660] hub 4-0:1.0: 2 ports detected
[    5.360730] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.360737] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.360740] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.360769] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    5.360793] uhci_hcd 0000:00:1d.0: irq 23, io base 0x000080a0
[    5.360862] usb usb5: configuration #1 chosen from 1 choice
[    5.360884] hub 5-0:1.0: USB hub found
[    5.360890] hub 5-0:1.0: 2 ports detected
[    5.360960] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.360966] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.360969] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.361000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    5.361024] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00008080
[    5.361091] usb usb6: configuration #1 chosen from 1 choice
[    5.361113] hub 6-0:1.0: USB hub found
[    5.361119] hub 6-0:1.0: 2 ports detected
[    5.361191] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    5.361197] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.361201] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.361229] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.361254] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00008060
[    5.361322] usb usb7: configuration #1 chosen from 1 choice
[    5.361345] hub 7-0:1.0: USB hub found
[    5.361350] hub 7-0:1.0: 2 ports detected
[    5.361421]   alloc irq_desc for 18 on node 0
[    5.361422]   alloc kstat_irqs on node 0
[    5.361426] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.361432] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    5.361435] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.361465] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    5.361495] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00008040
[    5.361565] usb usb8: configuration #1 chosen from 1 choice
[    5.361589] hub 8-0:1.0: USB hub found
[    5.361597] hub 8-0:1.0: 2 ports detected
[    5.361683] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    5.391237] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.391242] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.391308] mice: PS/2 mouse device common for all mice
[    5.391403] rtc_cmos 00:03: RTC can wake from S4
[    5.391432] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    5.391462] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    5.391567] device-mapper: uevent: version 1.0.3
[    5.391633] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    5.391684] device-mapper: multipath: version 1.1.0 loaded
[    5.391687] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.391870] cpuidle: using governor ladder
[    5.393416] cpuidle: using governor menu
[    5.393773] TCP cubic registered
[    5.393885] NET: Registered protocol family 10
[    5.394290] lo: Disabled Privacy Extensions
[    5.394556] NET: Registered protocol family 17
[    5.394571] Bluetooth: L2CAP ver 2.13
[    5.394573] Bluetooth: L2CAP socket layer initialized
[    5.394576] Bluetooth: SCO (Voice Link) ver 0.6
[    5.394578] Bluetooth: SCO socket layer initialized
[    5.394598] Bluetooth: RFCOMM TTY layer initialized
[    5.394601] Bluetooth: RFCOMM socket layer initialized
[    5.394603] Bluetooth: RFCOMM ver 1.11
[    5.395193] PM: Resume from disk failed.
[    5.395204] registered taskstats version 1
[    5.395331]   Magic number: 10:287:904
[    5.395428] rtc_cmos 00:03: setting system clock to 2010-01-10 21:52:32 UTC (1263160352)
[    5.395431] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.395432] EDD information not available.
[    5.424721] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    5.660034] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    5.670046] ata5: SATA link down (SStatus 0 SControl 300)
[    5.670075] ata1: SATA link down (SStatus 0 SControl 300)
[    5.934264] usb 1-2: configuration #1 chosen from 1 choice
[    6.250056] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.255274] ata6.00: ATAPI: HL-DT-ST DVDRAM GA10F, TF11, max UDMA/133, ATAPI AN
[    6.260033] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.260742] ata6.00: configured for UDMA/133
[    6.319543] ata2.00: ATA-8: TOSHIBA MK5055GSX, FG001M, max UDMA/100
[    6.319546] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.320028] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    6.320309] ata2.00: configured for UDMA/100
[    6.320426] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MK5055GS FG00 PQ: 0 ANSI: 5
[    6.320530] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    6.320533] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    6.320576] sd 1:0:0:0: [sda] Write Protect is off
[    6.320578] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.320600] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.320717]  sda:
[    6.329071] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GA10F     TF11 PQ: 0 ANSI: 5
[    6.340382] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    6.340386] Uniform CD-ROM driver Revision: 3.20
[    6.340482] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    6.340517] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    6.373049]  sda1 sda2 sda3 < sda5 sda6 >
[    6.417130] sd 1:0:0:0: [sda] Attached SCSI disk
[    6.417144] Freeing unused kernel memory: 660k freed
[    6.417332] Write protecting the kernel read-only data: 7584k
[    6.525631] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.525668] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.525795] r8169 0000:02:00.0: setting latency timer to 64
[    6.525940]   alloc irq_desc for 30 on node 0
[    6.525942]   alloc kstat_irqs on node 0
[    6.525991] r8169 0000:02:00.0: irq 30 for MSI/MSI-X
[    6.526567] eth0: RTL8102e at 0xffffc90000c7a000, 00:26:6c:35:2f:cf, XID 24c00000 IRQ 30
[    6.547351] acpi device:3c: registered as cooling_device3
[    6.547624] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:39/device:3a/input/input5
[    6.547661] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    6.590588] ohci1394 0000:04:00.3: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    6.590596] ohci1394 0000:04:00.3: setting latency timer to 64
[    6.594167] usb 6-2: configuration #1 chosen from 1 choice
[    6.603199] usbcore: registered new interface driver hiddev
[    6.632644] input: 2.4GHZ RF ONLY  MOUSE as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input6
[    6.632747] generic-usb 0003:1BCF:0535.0001: input,hiddev96,hidraw0: USB HID v1.00 Mouse [2.4GHZ RF ONLY  MOUSE] on usb-0000:00:1d.1-2/input0
[    6.632761] usbcore: registered new interface driver usbhid
[    6.632764] usbhid: v2.6:USB HID core driver
[    6.652077] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[d8200000-d82007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    8.010520] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080d266c352fcf]
[    8.239232] PM: Starting manual resume from disk
[    8.239235] PM: Resume from partition 8:6
[    8.239237] PM: Checking hibernation image.
[    8.239331] PM: Resume from disk failed.
[    8.259824] EXT4-fs (sda5): barriers enabled
[    8.274657] kjournald2 starting: pid 434, dev sda5:8, commit interval 5 seconds
[    8.274670] EXT4-fs (sda5): delayed allocation enabled
[    8.274675] EXT4-fs: file extents enabled
[    8.283633] EXT4-fs: mballoc enabled
[    8.283645] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    8.875557] type=1505 audit(1263160355.975:2): operation="profile_load" pid=457 name=/usr/share/gdm/guest-session/Xsession
[    8.877310] type=1505 audit(1263160355.975:3): operation="profile_load" pid=458 name=/sbin/dhclient3
[    8.877998] type=1505 audit(1263160355.975:4): operation="profile_load" pid=458 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.878361] type=1505 audit(1263160355.975:5): operation="profile_load" pid=458 name=/usr/lib/connman/scripts/dhclient-script
[    8.917349] type=1505 audit(1263160356.014:6): operation="profile_load" pid=459 name=/usr/bin/evince
[    8.928020] type=1505 audit(1263160356.024:7): operation="profile_load" pid=459 name=/usr/bin/evince-previewer
[    8.934317] type=1505 audit(1263160356.034:8): operation="profile_load" pid=459 name=/usr/bin/evince-thumbnailer
[    8.957303] type=1505 audit(1263160356.054:9): operation="profile_load" pid=461 name=/usr/lib/cups/backend/cups-pdf
[    8.958091] type=1505 audit(1263160356.054:10): operation="profile_load" pid=461 name=/usr/sbin/cupsd
[    8.966708] type=1505 audit(1263160356.064:11): operation="profile_load" pid=462 name=/usr/sbin/tcpdump
[   20.884855] udev: starting version 147
[   20.906710] Adding 6273340k swap on /dev/sda6.  Priority:-1 extents:1 across:6273340k 
[   20.966575] Disabling lock debugging due to kernel taint
[   20.970225] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   21.023498] lp: driver loaded but no devices found
[   21.064473] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.066940] sdhci: Secure Digital Host Controller Interface driver
[   21.066942] sdhci: Copyright(c) Pierre Ossman
[   21.072865] Linux video capture interface: v2.00
[   21.075253] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (064e:d104)
[   21.087300] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input7
[   21.087345] usbcore: registered new interface driver uvcvideo
[   21.087350] USB Video Class driver (v0.1.0)
[   21.305791]   alloc irq_desc for 22 on node 0
[   21.305794]   alloc kstat_irqs on node 0
[   21.305801] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.305838] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.307840] sdhci-pci 0000:04:00.0: SDHCI controller found [1180:e822] (rev 1)
[   21.307859] sdhci-pci 0000:04:00.0: PCI INT D -> GSI 18 (level, low) -> IRQ 18
[   21.308887] sdhci-pci 0000:04:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[   21.308894] sdhci-pci 0000:04:00.0: setting latency timer to 64
[   21.309944] Registered led device: mmc0::
[   21.311004] mmc0: SDHCI controller on PCI [0000:04:00.0] using DMA
[   21.311697] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.311704] nvidia 0000:01:00.0: setting latency timer to 64
[   21.311856] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[   21.446876] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[   21.447779] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   21.464223] EXT4-fs (sda5): internal journal on sda5:8
[   21.506512] usbcore: registered new interface driver ndiswrapper
[   21.710429] type=1505 audit(1263178368.814:12): operation="profile_replace" pid=1004 name=/usr/share/gdm/guest-session/Xsession
[   21.711938] type=1505 audit(1263178368.814:13): operation="profile_replace" pid=1005 name=/sbin/dhclient3
[   21.712603] type=1505 audit(1263178368.814:14): operation="profile_replace" pid=1005 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   21.712965] type=1505 audit(1263178368.814:15): operation="profile_replace" pid=1005 name=/usr/lib/connman/scripts/dhclient-script
[   21.716239] type=1505 audit(1263178368.814:16): operation="profile_replace" pid=1006 name=/usr/bin/evince
[   21.727113] type=1505 audit(1263178368.824:17): operation="profile_replace" pid=1006 name=/usr/bin/evince-previewer
[   21.734204] type=1505 audit(1263178368.834:18): operation="profile_replace" pid=1006 name=/usr/bin/evince-thumbnailer
[   21.742932] type=1505 audit(1263178368.844:19): operation="profile_replace" pid=1010 name=/usr/lib/cups/backend/cups-pdf
[   21.743710] type=1505 audit(1263178368.844:20): operation="profile_replace" pid=1010 name=/usr/sbin/cupsd
[   21.745816] type=1505 audit(1263178368.844:21): operation="profile_replace" pid=1011 name=/usr/sbin/tcpdump
[   21.773902] r8169: eth0: link up
[   21.773917] r8169: eth0: link up
[   21.934924] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1e0b1, caps: 0xd04731/0xa40000
[   22.026651] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   22.197448] ppdev: user-space parallel port driver
[   22.289159] usplash:397 freeing invalid memtype ffffffffd1000000-ffffffffd1e00000
[   22.660206] CPU0 attaching NULL sched-domain.
[   22.660211] CPU1 attaching NULL sched-domain.
[   23.160208] CPU0 attaching sched-domain:
[   23.160212]  domain 0: span 0-1 level MC
[   23.160214]   groups: 0 1
[   23.160219] CPU1 attaching sched-domain:
[   23.160220]  domain 0: span 0-1 level MC
[   23.160222]   groups: 1 0
[   24.131259] CE: hpet increasing min_delta_ns to 15000 nsec
[   26.790041] CPU0 attaching NULL sched-domain.
[   26.790046] CPU1 attaching NULL sched-domain.
[   26.821348] CPU0 attaching sched-domain:
[   26.821353]  domain 0: span 0-1 level MC
[   26.821356]   groups: 0 1
[   26.821368] CPU1 attaching sched-domain:
[   26.821369]  domain 0: span 0-1 level MC
[   26.821371]   groups: 1 0
[   31.780016] eth0: no IPv6 routers present

```

---

