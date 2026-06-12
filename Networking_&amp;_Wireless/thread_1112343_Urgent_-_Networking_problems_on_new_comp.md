---
title: "Urgent - Networking problems on new comp"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by Glen Darby on 2009-03-31
I have just bought a new computer - 
[These are the specks]("http://h10010.www1.hp.com/wwpc/uk/en/ho/WF06b/12454-12454-3329740-64546-64546-3823602-3916212.html")

It has an on board network - Ethernet 10/100BT integrated network interface

I have installed ubuntu 8.10, but I am unable to connect to the network with ubuntu and wondered if there was any fix available.
The network is not even seeing the router, so im wondering if it is unsuported?

Im in pretty urgent need to get this up and running in order to get my accounts sorted for the end of tax year.

Any speedy help greatly appreciated.

Glen.

---

### Post by Iowan on 2009-03-31
Specs are a bit vague on NIC... What are results of **lshw -C network**?

---

### Post by Glen Darby on 2009-04-01
Hi, Thanks for the lightning reply, sorry I didn't respond quite as quick as im in UK and needed my sleep...... Didn't expect quite such a quick response.

The results of the lshw -C network are :

 *-network
          description: Ethernet interface
          product: MCP78S [GeForce 8200] Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:23:54:95:f9:d8
          size: 100MB/s
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:30:59:89:29:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Thanks for your help.

Glen.

---

### Post by coutts99 on 2009-04-01
Can you post output of dmesg and ifconfig

---

### Post by Glen Darby on 2009-04-01
Hi,

dmesg results :

[    0.580762] PCI: 0000:00:09.0 reg 18 io port: [d080, d087]
[    0.580766] PCI: 0000:00:09.0 reg 1c io port: [d000, d003]
[    0.580769] PCI: 0000:00:09.0 reg 20 io port: [cc00, cc0f]
[    0.580773] PCI: 0000:00:09.0 reg 24 32bit mmio: [f9e76000, f9e77fff]
[    0.580803] PCI: 0000:00:0a.0 reg 10 32bit mmio: [f9e7c000, f9e7cfff]
[    0.580807] PCI: 0000:00:0a.0 reg 14 io port: [c880, c887]
[    0.580811] PCI: 0000:00:0a.0 reg 18 32bit mmio: [f9e7e400, f9e7e4ff]
[    0.580815] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [f9e7e000, f9e7e00f]
[    0.580831] pci 0000:00:0a.0: supports D1
[    0.580833] pci 0000:00:0a.0: supports D2
[    0.580834] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.580839] pci 0000:00:0a.0: PME# disabled
[    0.581015] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.581022] pci 0000:00:10.0: PME# disabled
[    0.581194] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.581205] pci 0000:00:12.0: PME# disabled
[    0.581376] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.581388] pci 0000:00:13.0: PME# disabled
[    0.581559] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.581570] pci 0000:00:14.0: PME# disabled
[    0.581667] PCI: 0000:01:05.0 reg 10 32bit mmio: [f9fff000, f9ffffff]
[    0.581698] pci 0000:01:05.0: supports D1
[    0.581699] pci 0000:01:05.0: supports D2
[    0.581701] pci 0000:01:05.0: PME# supported from D0 D1 D2 D3hot
[    0.581708] pci 0000:01:05.0: PME# disabled
[    0.581733] pci 0000:00:08.0: transparent bridge
[    0.581737] PCI: bridge 0000:00:08.0 32bit mmio: [f9f00000, f9ffffff]
[    0.581768] PCI: 0000:02:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.581773] PCI: 0000:02:00.0 reg 14 32bit mmio: [e0000000, efffffff]
[    0.581784] PCI: 0000:02:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.581788] PCI: 0000:02:00.0 reg 24 io port: [ec00, ec7f]
[    0.581793] PCI: 0000:02:00.0 reg 30 32bit mmio: [febe0000, febfffff]
[    0.581845] PCI: bridge 0000:00:10.0 io port: [e000, efff]
[    0.581853] PCI: bridge 0000:00:10.0 32bit mmio: [fa000000, febfffff]
[    0.581866] PCI: bridge 0000:00:10.0 64bit mmio pref: [e0000000, efffffff]
[    0.582125] bus 00 -> node 0
[    0.582131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.584293] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.584537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
[    0.584708] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.584872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.585036] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.609063] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.609063] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.609143] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.609528] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *14
[    0.609911] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
[    0.612108] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.612493] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.612872] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.613252] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.613632] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.614012] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.614393] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.614778] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *11
[    0.615157] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.615538] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.615918] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.616304] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *15
[    0.616683] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.617063] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.617444] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.617828] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *14
[    0.618208] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.618588] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.618968] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.619348] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.619728] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.620114] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.620495] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.620876] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.621256] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.621635] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.622016] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.622395] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.622775] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.623156] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.623540] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.623922] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[    0.624312] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15
[    0.624694] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *15
[    0.625079] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.625453] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *0, disabled.
[    0.625838] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *7
[    0.626227] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[    0.626610] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.627061] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.627448] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *14
[    0.627833] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *10
[    0.628284] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.628294] pnp: PnP ACPI init
[    0.628294] ACPI: bus type pnp registered
[    0.637575] pnp: PnP ACPI: found 13 devices
[    0.637577] ACPI: ACPI bus type pnp unregistered
[    0.637580] PnPBIOS: Disabled by ACPI PNP
[    0.637593] PCI: Using ACPI for IRQ routing
[    0.644038] NET: Registered protocol family 8
[    0.644040] NET: Registered protocol family 20
[    0.644052] NetLabel: Initializing
[    0.644052] NetLabel:  domain hash size = 128
[    0.644052] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.644052] NetLabel:  unlabeled traffic allowed by default
[    0.644055] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.644059] hpet0: 3 32-bit timers, 25000000 Hz
[    0.646092] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.646095]    actual entries 65620
[    0.646164] AppArmor: AppArmor Filesystem Enabled
[    0.646189] ACPI: RTC can wake from S4
[    0.648044] Switched to high resolution mode on CPU 1
[    0.648047] Switched to high resolution mode on CPU 0
[    0.648058] Switched to high resolution mode on CPU 2
[    0.652195] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.652198] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.652201] system 00:04: ioport range 0x2000-0x207f has been reserved
[    0.652203] system 00:04: ioport range 0x2080-0x20ff has been reserved
[    0.652206] system 00:04: ioport range 0x2400-0x247f has been reserved
[    0.652208] system 00:04: ioport range 0x2480-0x24ff has been reserved
[    0.652211] system 00:04: ioport range 0x2800-0x287f has been reserved
[    0.652213] system 00:04: ioport range 0x2880-0x28ff has been reserved
[    0.652217] system 00:04: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.652220] system 00:04: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.652228] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.652231] system 00:07: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.652237] system 00:0a: ioport range 0xa00-0xadf has been reserved
[    0.652242] system 00:0b: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.652247] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.652254] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.652256] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.652259] system 00:0c: iomem range 0x100000-0xbfffffff could not be reserved
[    0.652262] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.687401] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.687403] pci 0000:00:08.0:   IO window: disabled
[    0.687407] pci 0000:00:08.0:   MEM window: 0xf9f00000-0xf9ffffff
[    0.687410] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.687415] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.687420] pci 0000:00:10.0:   IO window: 0xe000-0xefff
[    0.687430] pci 0000:00:10.0:   MEM window: 0xfa000000-0xfebfffff
[    0.687437] pci 0000:00:10.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.687450] pci 0000:00:12.0: PCI bridge, secondary bus 0000:03
[    0.687452] pci 0000:00:12.0:   IO window: disabled
[    0.687462] pci 0000:00:12.0:   MEM window: disabled
[    0.687468] pci 0000:00:12.0:   PREFETCH window: disabled
[    0.687481] pci 0000:00:13.0: PCI bridge, secondary bus 0000:04
[    0.687483] pci 0000:00:13.0:   IO window: disabled
[    0.687492] pci 0000:00:13.0:   MEM window: disabled
[    0.687499] pci 0000:00:13.0:   PREFETCH window: disabled
[    0.687511] pci 0000:00:14.0: PCI bridge, secondary bus 0000:05
[    0.687513] pci 0000:00:14.0:   IO window: disabled
[    0.687522] pci 0000:00:14.0:   MEM window: disabled
[    0.687529] pci 0000:00:14.0:   PREFETCH window: disabled
[    0.687546] pci 0000:00:08.0: setting latency timer to 64
[    0.688069] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.688080] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.688089] pci 0000:00:10.0: setting latency timer to 64
[    0.688595] ACPI: PCI Interrupt Link [LN2A] enabled at IRQ 18
[    0.688602] pci 0000:00:12.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    0.688610] pci 0000:00:12.0: setting latency timer to 64
[    0.689111] ACPI: PCI Interrupt Link [LN3A] enabled at IRQ 17
[    0.689118] pci 0000:00:13.0: PCI INT A -> Link[LN3A] -> GSI 17 (level, low) -> IRQ 17
[    0.689126] pci 0000:00:13.0: setting latency timer to 64
[    0.689626] ACPI: PCI Interrupt Link [LN4A] enabled at IRQ 16
[    0.689633] pci 0000:00:14.0: PCI INT A -> Link[LN4A] -> GSI 16 (level, low) -> IRQ 16
[    0.689641] pci 0000:00:14.0: setting latency timer to 64
[    0.689646] bus: 00 index 0 io port: [0, ffff]
[    0.689648] bus: 00 index 1 mmio: [0, ffffffff]
[    0.689650] bus: 01 index 0 mmio: [0, 0]
[    0.689652] bus: 01 index 1 mmio: [f9f00000, f9ffffff]
[    0.689654] bus: 01 index 2 mmio: [0, 0]
[    0.689656] bus: 01 index 3 io port: [0, ffff]
[    0.689657] bus: 01 index 4 mmio: [0, ffffffff]
[    0.689659] bus: 02 index 0 io port: [e000, efff]
[    0.689661] bus: 02 index 1 mmio: [fa000000, febfffff]
[    0.689663] bus: 02 index 2 mmio: [e0000000, efffffff]
[    0.689665] bus: 02 index 3 mmio: [0, 0]
[    0.689666] bus: 03 index 0 mmio: [0, 0]
[    0.689668] bus: 03 index 1 mmio: [0, 0]
[    0.689669] bus: 03 index 2 mmio: [0, 0]
[    0.689671] bus: 03 index 3 mmio: [0, 0]
[    0.689673] bus: 04 index 0 mmio: [0, 0]
[    0.689674] bus: 04 index 1 mmio: [0, 0]
[    0.689676] bus: 04 index 2 mmio: [0, 0]
[    0.689677] bus: 04 index 3 mmio: [0, 0]
[    0.689679] bus: 05 index 0 mmio: [0, 0]
[    0.689680] bus: 05 index 1 mmio: [0, 0]
[    0.689682] bus: 05 index 2 mmio: [0, 0]
[    0.689683] bus: 05 index 3 mmio: [0, 0]
[    0.689692] NET: Registered protocol family 2
[    0.704139] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.704351] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.704702] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.704912] TCP: Hash tables configured (established 131072 bind 65536)
[    0.704915] TCP reno registered
[    0.712304] NET: Registered protocol family 1
[    0.712406] checking if image is initramfs... it is
[    1.278071] Freeing initrd memory: 7991k freed
[    1.279336] audit: initializing netlink socket (disabled)
[    1.279354] type=2000 audit(1238581967.276:1): initialized
[    1.284085] highmem bounce pool size: 64 pages
[    1.284090] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.286069] VFS: Disk quotas dquot_6.5.1
[    1.286151] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.286235] msgmni has been set to 1725
[    1.286341] io scheduler noop registered
[    1.286343] io scheduler anticipatory registered
[    1.286345] io scheduler deadline registered
[    1.286356] io scheduler cfq registered (default)
[    1.352701] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.352731] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.352762] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.352793] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.352850] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.352918] pci 0000:00:12.0: Enabling HT MSI Mapping
[    1.352985] pci 0000:00:13.0: Enabling HT MSI Mapping
[    1.353061] pci 0000:00:14.0: Enabling HT MSI Mapping
[    1.353113] pci 0000:02:00.0: Boot video device
[    1.353257] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.353428] pcieport-driver 0000:00:10.0: found MSI capability
[    1.353544] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.353793] pcieport-driver 0000:00:12.0: setting latency timer to 64
[    1.353962] pcieport-driver 0000:00:12.0: found MSI capability
[    1.354077] pci_express 0000:00:12.0:pcie00: allocate port service
[    1.354327] pcieport-driver 0000:00:13.0: setting latency timer to 64
[    1.354496] pcieport-driver 0000:00:13.0: found MSI capability
[    1.354612] pci_express 0000:00:13.0:pcie00: allocate port service
[    1.354858] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    1.355027] pcieport-driver 0000:00:14.0: found MSI capability
[    1.355141] pci_express 0000:00:14.0:pcie00: allocate port service
[    1.355581] isapnp: Scanning for PnP cards...
[    1.708555] isapnp: No Plug & Play device found
[    1.742190] hpet_resources: 0xfed00000 is busy
[    1.742301] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.744214] brd: module loaded
[    1.744280] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.744393] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.746579] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.746585] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.748329] mice: PS/2 mouse device common for all mice
[    1.748454] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.748514] rtc0: alarms up to one year, y3k, hpet irqs
[    1.748638] EISA: Probing bus 0 at eisa.0
[    1.748646] Cannot allocate resource for EISA slot 2
[    1.748661] EISA: Detected 0 cards.
[    1.748664] cpuidle: using governor ladder
[    1.748666] cpuidle: using governor menu
[    1.749122] TCP cubic registered
[    1.749144] Using IPI No-Shortcut mode
[    1.749323] registered taskstats version 1
[    1.749440]   Magic number: 5:597:526
[    1.749561] rtc_cmos 00:06: setting system clock to 2009-04-01 10:32:48 UTC (1238581968)
[    1.749566] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.749568] EDD information not available.
[    1.749745] Freeing unused kernel memory: 424k freed
[    1.749799] Write protecting the kernel text: 2576k
[    1.749836] Write protecting the kernel read-only data: 936k
[    1.772263] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.849494] fuse init (API version 7.9)
[    1.866333] processor ACPI0007:00: registered as cooling_device0
[    1.866390] processor ACPI0007:01: registered as cooling_device1
[    1.866454] processor ACPI0007:02: registered as cooling_device2
[    2.181659] usbcore: registered new interface driver usbfs
[    2.181680] usbcore: registered new interface driver hub
[    2.181722] usbcore: registered new device driver usb
[    2.183180] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.183717] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    2.183728] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    2.183738] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.183741] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.183781] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.183804] ohci_hcd 0000:00:02.0: irq 23, io mem 0xf9e7f000
[    2.202497] No dock devices found.
[    2.221923] SCSI subsystem initialized
[    2.239164] usb usb1: configuration #1 chosen from 1 choice
[    2.239195] hub 1-0:1.0: USB hub found
[    2.239205] hub 1-0:1.0: 6 ports detected
[    2.253941] libata version 3.00 loaded.
[    2.449310] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
[    2.449329] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
[    2.449345] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    2.449350] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    2.449371] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    2.449408] ohci_hcd 0000:00:04.0: irq 22, io mem 0xf9e7d000
[    2.506186] usb usb2: configuration #1 chosen from 1 choice
[    2.506211] hub 2-0:1.0: USB hub found
[    2.506220] hub 2-0:1.0: 6 ports detected
[    2.620299] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    2.713420] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    2.713431] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    2.713443] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.713446] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.713475] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    2.713496] ehci_hcd 0000:00:02.1: debug port 1
[    2.713500] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.713516] ehci_hcd 0000:00:02.1: irq 21, io mem 0xf9e7ec00
[    2.808275] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.808371] usb usb3: configuration #1 chosen from 1 choice
[    2.808394] hub 3-0:1.0: USB hub found
[    2.808401] hub 3-0:1.0: 6 ports detected
[    3.017521] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 20
[    3.017529] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 20 (level, low) -> IRQ 20
[    3.017537] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    3.017540] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    3.017562] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[    3.017586] ehci_hcd 0000:00:04.1: debug port 1
[    3.017590] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    3.017601] ehci_hcd 0000:00:04.1: irq 20, io mem 0xf9e7e800
[    3.028790] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.028863] usb usb4: configuration #1 chosen from 1 choice
[    3.028886] hub 4-0:1.0: USB hub found
[    3.028891] hub 4-0:1.0: 6 ports detected
[    3.204254] usb 1-1: device not accepting address 2, error -62
[    3.236561] ahci 0000:00:09.0: version 3.0
[    3.237056] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    3.237060] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    3.237132] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[    3.237136] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    3.237139] ahci 0000:00:09.0: setting latency timer to 64
[    3.237354] scsi0 : ahci
[    3.237716] scsi1 : ahci
[    3.238024] scsi2 : ahci
[    3.238341] scsi3 : ahci
[    3.238421] ata1: SATA max UDMA/133 abar m8192@0xf9e76000 port 0xf9e76100 irq 219
[    3.238424] ata2: SATA max UDMA/133 abar m8192@0xf9e76000 port 0xf9e76180 irq 219
[    3.238427] ata3: SATA max UDMA/133 abar m8192@0xf9e76000 port 0xf9e76200 irq 219
[    3.238429] ata4: SATA max UDMA/133 abar m8192@0xf9e76000 port 0xf9e76280 irq 219
[    3.260034] hub 1-0:1.0: unable to enumerate USB device on port 1
[    3.628031] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    3.720099] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.726532] ata1.00: ATA-7: SAMSUNG HD642JJ, 1AA01114, max UDMA7
[    3.726535] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.733264] ata1.00: configured for UDMA/133
[    3.763063] usb 3-1: configuration #1 chosen from 1 choice
[    3.876203] usb 4-4: new high speed USB device using ehci_hcd and address 2
[    4.029065] usb 4-4: configuration #1 chosen from 1 choice
[    4.621098] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.626092] ata2.00: ATAPI: ATAPI   BD  B  DH6E2L, 6H1K, max UDMA/100
[    4.629616] ata2.00: configured for UDMA/100
[    4.948292] ata3: SATA link down (SStatus 0 SControl 300)
[    5.268209] ata4: SATA link down (SStatus 0 SControl 300)
[    5.268302] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD642JJ  1AA0 PQ: 0 ANSI: 5
[    5.272281] scsi 1:0:0:0: CD-ROM            ATAPI    BD  B  DH6E2L    6H1K PQ: 0 ANSI: 5
[    5.272400] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    5.272911] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    5.272915] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    5.272919] forcedeth 0000:00:0a.0: setting latency timer to 64
[    5.792889] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:23:54:95:f9:d8
[    5.792893] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq lnktim msi desc-v3
[    5.795296] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[    5.795301] ohci1394 0000:01:05.0: PCI INT A -> Link[LNKD] -> GSI 19 (level, low) -> IRQ 19
[    5.845038] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[f9fff000-f9fff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    5.857525] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.857563] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.874730] usbcore: registered new interface driver libusual
[    5.887566] Initializing USB Mass Storage driver...
[    5.887650] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.887734] usb-storage: device found at 2
[    5.887736] usb-storage: waiting for device to settle before scanning
[    5.887761] scsi5 : SCSI emulation for USB Mass Storage devices
[    5.887819] usbcore: registered new interface driver usb-storage
[    5.887822] USB Mass Storage support registered.
[    5.887826] usb-storage: device found at 2
[    5.887827] usb-storage: waiting for device to settle before scanning
[    5.890989] Driver 'sd' needs updating - please use bus_type methods
[    5.891077] sd 0:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
[    5.891090] sd 0:0:0:0: [sda] Write Protect is off
[    5.891092] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.891110] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.891167] sd 0:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
[    5.891178] sd 0:0:0:0: [sda] Write Protect is off
[    5.891180] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.891197] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.891200]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.907788]  sda1 sda2 < sda5 >
[    5.930650] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.940322] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.940326] Uniform CD-ROM driver Revision: 3.20
[    5.940396] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.055052] PM: Starting manual resume from disk
[    6.055056] PM: Resume from partition 8:5
[    6.055057] PM: Checking hibernation image.
[    6.055395] PM: Resume from disk failed.
[    6.126451] kjournald starting.  Commit interval 5 seconds
[    6.126459] EXT3-fs: mounted filesystem with ordered data mode.
[    7.116363] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001aed61e]
[   10.885394] usb-storage: device scan complete
[   10.885408] usb-storage: device scan complete
[   10.887266] scsi 4:0:0:0: Direct-Access     HP                        1.00 PQ: 0 ANSI: 5
[   10.892547] scsi 5:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[   10.899264] scsi 5:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[   10.899823] udevd version 124 started
[   10.906393] scsi 5:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[   10.913529] scsi 5:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[   10.915729] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   10.915855] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   10.916840] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[   10.919128] sd 5:0:0:1: Attached scsi generic sg3 type 0
[   10.920483] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[   10.921029] sd 5:0:0:2: Attached scsi generic sg4 type 0
[   10.921975] sd 5:0:0:3: [sde] Attached SCSI removable disk
[   10.923403] sd 5:0:0:3: Attached scsi generic sg5 type 0
[   10.925591] sd 4:0:0:0: [sdf] Attached SCSI removable disk
[   10.925717] sd 4:0:0:0: Attached scsi generic sg6 type 0
[   11.327237] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   11.341021] ACPI: Power Button (FF) [PWRF]
[   11.341118] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   11.373019] ACPI: Power Button (CM) [PWRB]
[   11.840490] ACPI: WMI: Mapper loaded
[   11.979232] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.034651] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.179181] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5D11
[   12.179199] usbcore: registered new interface driver usblp
[   12.285666] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   12.598571] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[   12.599065] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   12.599070] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   12.599086] HDA Intel 0000:00:07.0: setting latency timer to 64
[   12.631853] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.137827] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   13.913672] lp: driver loaded but no devices found
[   14.027860] Adding 9108812k swap on /dev/sda5.  Priority:-1 extents:1 across:9108812k
[   14.567313] EXT3 FS on sda1, internal journal
[   15.423477] type=1505 audit(1238581982.633:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4697
[   15.575548] type=1505 audit(1238581982.784:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4702
[   15.575715] type=1505 audit(1238581982.784:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4702
[   15.724587] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.416203] powernow-k8: Found 1 AMD Phenom(tm) 8650 Triple-Core Processor processors (3 cpu cores) (version 2.20.00)
[   16.416241] powernow-k8:    0 : pstate 0 (2300 MHz)
[   16.416244] powernow-k8:    1 : pstate 1 (1150 MHz)
[   16.950577] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   16.986684] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   16.986691] apm: disabled - APM is not SMP safe.
[   17.105252] ppdev: user-space parallel port driver
[   18.506139] Bluetooth: Core ver 2.13
[   18.506814] NET: Registered protocol family 31
[   18.506822] Bluetooth: HCI device and connection manager initialized
[   18.506828] Bluetooth: HCI socket layer initialized
[   18.534104] Bluetooth: L2CAP ver 2.11
[   18.534118] Bluetooth: L2CAP socket layer initialized
[   18.580892] Bluetooth: SCO (Voice Link) ver 0.6
[   18.580902] Bluetooth: SCO socket layer initialized
[   18.604971] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.604980] Bluetooth: BNEP filters: protocol multicast
[   18.665144] Bridge firewalling registered
[   18.665355] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   18.695618] Bluetooth: RFCOMM socket layer initialized
[   18.695643] Bluetooth: RFCOMM TTY layer initialized
[   18.695647] Bluetooth: RFCOMM ver 1.10
[   21.578332] mtrr: base(0xfb000000) is not aligned on a size(0xe00000) boundary
[   23.294172] NET: Registered protocol family 17

AND IFCONFIG RESULTS :

eth0      Link encap:Ethernet  HWaddr 00:23:54:95:f9:d8  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5845 (5.8 KB)  TX bytes:2976 (2.9 KB)
          Interrupt:218 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

And thanks again for the reply...

Glen.

---

### Post by coutts99 on 2009-04-01
Your MTU is being reported at 64, this is incorrect

Can remove the option 'interface-mtu' in /etc/dhcp3/dhclient.conf

This should fix the problem.

More info here - [http://propellerheadadmin.com/tutorials/ubuntu/6-wired-networking-problem-on-a-fresh-ubuntu-810-install]("http://propellerheadadmin.com/tutorials/ubuntu/6-wired-networking-problem-on-a-fresh-ubuntu-810-install")

---

### Post by Glen Darby on 2009-04-01
Hi,

Thanks for that.

I removed the the option 'interface-mtu' in /etc/dhcp3/dhclient.conf and it has connected fine....

Great stuff.

Really thankful, can now get on with my accounts :sad:

---

