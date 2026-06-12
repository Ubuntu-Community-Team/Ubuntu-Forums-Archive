---
title: "Wireless half of what it was in Intrepid."
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by missbliss on 2009-04-20
Ever since I installed Jaunty My connection has been about half of what it was in Intrepid, which was operating at 100%.

I know there are some easy ways to troubleshoot this, but I can't remember hwo and wasn't finding it on a search.

Suggestions?

*edit* I also have a really hard time connecting to youtube vids and am unable to connect to last.fm right now which I am assuming can be attributed to the low connection, but just thought I'd throw it out there.

---

### Post by kevdog on 2009-04-20
Um, yeah, beyond the rant we would actually need some networking information like card, driver, etc to provide some useful assistance.

---

### Post by missbliss on 2009-04-20
> **kevdog said:**
> Um, yeah, beyond the rant we would actually need some networking information like card, driver, etc to provide some useful assistance.

Uh, yeah.  That mighta been smart.  

HP G60 Laptop
Lynksys WRT54GS
AR242x 802.11abg Wireless PCI Express Adapter
RTL8101E/RTL8102E PCI Express Fast Ethernet controller


Is this helpful?

---

### Post by coffeecat on 2009-04-20
> **missbliss said:**
> HP G60 Laptop
Lynksys WRT54GS
AR242x 802.11abg Wireless PCI Express Adapter
RTL8101E/RTL8102E PCI Express Fast Ethernet controller


Is this helpful?

Well, it's a start. It's number 1 [on a list of 10]("http://ubuntuforums.org/showthread.php?p=6183681") helpfully linked to from [a sticky at the head of this subforum]("http://ubuntuforums.org/showthread.php?t=370108"). :wink:

---

### Post by kevdog on 2009-04-20
What driver are you using with the 242x module -- patched madwifi or ath5k or other?

---

### Post by missbliss on 2009-04-21
Sorry, was somewhat brain dead yesterday!!  Here goes:

Chipset - Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)

Ethernet controller - Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

ifconfig
```
sarah@skhill:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:57:2c:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:608 (608.0 B)  TX bytes:608 (608.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:76:9f:c7  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fe76:9fc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14494010 (14.4 MB)  TX bytes:1735407 (1.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4E-76-9F-C7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Network configuration
```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:57:2c:88
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4e:76:9f:c7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.100 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:be:a4:fb:45:78
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Ubuntu 9.04

2.6.28-11-generic x86_64

networking restart - ```
* Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

```

---

### Post by kevdog on 2009-04-21
Can you check dmesg for any errors when attempting to modprobe the ath5k_pci driver?  ath5k_pci is the driver you are using BTW.  I don't have a lot of Jaunty experience -- in fact none. ath5k_pci used to be called simply ath5k. Im not sure if this is part of the problem or not.  There is something definitely wrong however with the driver.

---

### Post by missbliss on 2009-04-21
Here is what I got when I ran 'dmesg'.  It's obviously pretty long, so I bolded the parts I thought might be important.

```
[    0.546798] pci 0000:00:1c.0: bridge io port: [0x3000-0x4fff]
[    0.546802] pci 0000:00:1c.0: bridge 32bit mmio: [0xd3700000-0xd46fffff]
[    0.546810] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0400000-0xd14fffff]
[    0.546881] pci 0000:02:00.0: reg 10 64bit mmio: [0xd2600000-0xd260ffff]
[    0.547012] pci 0000:00:1c.1: bridge io port: [0x2000-0x2fff]
[    0.547016] pci 0000:00:1c.1: bridge 32bit mmio: [0xd2600000-0xd36fffff]
[    0.547024] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xd1500000-0xd24fffff]
[    0.547092] pci 0000:00:1e.0: transparent bridge
[    0.547124] bus 00 -> node 0
[    0.547135] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.547653] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.547720] ACPI Warning (nspredef-0357): \_SB_.PCI0.P32_._PRT: Return Package has no elements (empty) [20080926]
[    0.547835] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.548033] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.552011] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.552183] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.552350] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[    0.552515] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.552681] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.552847] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.553013] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.553178] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.553579] ACPI: WMI: Mapper loaded
[    0.553620] SCSI subsystem initialized
[    0.553620] libata version 3.00 loaded.
[    0.553620] usbcore: registered new interface driver usbfs
[    0.553620] usbcore: registered new interface driver hub
[    0.553620] usbcore: registered new device driver usb
[    0.553620] PCI: Using ACPI for IRQ routing
[    0.564009] Bluetooth: Core ver 2.13
[    0.564014] NET: Registered protocol family 31
[    0.564014] Bluetooth: HCI device and connection manager initialized
[    0.564017] Bluetooth: HCI socket layer initialized
[    0.564019] NET: Registered protocol family 8
[    0.564020] NET: Registered protocol family 20
[    0.564030] NetLabel: Initializing
[    0.564031] NetLabel:  domain hash size = 128
[    0.564032] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.564045] NetLabel:  unlabeled traffic allowed by default
[    0.564074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.564078] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.568074] AppArmor: AppArmor Filesystem Enabled
[    0.572008] Switched to high resolution mode on CPU 0
[    0.572402] Switched to high resolution mode on CPU 1
[    0.580508] pnp: PnP ACPI init
[    0.580518] ACPI: bus type pnp registered
[    0.582495] pnp: PnP ACPI: found 9 devices
[    0.582497] ACPI: ACPI bus type pnp unregistered
[    0.582506] system 00:01: ioport range 0x164e-0x164f has been reserved
[    0.582509] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.582511] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.582514] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.582516] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.582518] system 00:01: ioport range 0x820-0x823 has been reserved
[    0.582520] system 00:01: ioport range 0x830-0x83b has been reserved
[    0.582522] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.582524] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.582527] system 00:01: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.582529] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.582532] system 00:01: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.582534] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.582537] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.582539] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.582541] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.582544] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.582546] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.582548] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.582551] system 00:01: iomem range 0xff800000-0xff800fff has been reserved
[    0.587237] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.587240] pci 0000:00:1c.0:   IO window: 0x3000-0x4fff
[    0.587247] pci 0000:00:1c.0:   MEM window: 0xd3700000-0xd46fffff
[    0.587251] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0400000-0x000000d14fffff
[    0.587259] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.587262] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.587268] pci 0000:00:1c.1:   MEM window: 0xd2600000-0xd36fffff
[    0.587273] pci 0000:00:1c.1:   PREFETCH window: 0x000000d1500000-0x000000d24fffff
[    0.587281] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.587282] pci 0000:00:1e.0:   IO window: disabled
[    0.587288] pci 0000:00:1e.0:   MEM window: disabled
[    0.587292] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.587310] pci 0000:00:1c.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.587315] pci 0000:00:1c.0: setting latency timer to 64
[    0.587325] pci 0000:00:1c.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.587329] pci 0000:00:1c.1: setting latency timer to 64
[    0.587337] pci 0000:00:1e.0: setting latency timer to 64
[    0.587341] bus: 00 index 0 io port: [0x00-0xffff]
[    0.587343] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.587345] bus: 01 index 0 io port: [0x3000-0x4fff]
[    0.587347] bus: 01 index 1 mmio: [0xd3700000-0xd46fffff]
[    0.587349] bus: 01 index 2 mmio: [0xd0400000-0xd14fffff]
[    0.587351] bus: 01 index 3 mmio: [0x0-0x0]
[    0.587352] bus: 02 index 0 io port: [0x2000-0x2fff]
[    0.587354] bus: 02 index 1 mmio: [0xd2600000-0xd36fffff]
[    0.587356] bus: 02 index 2 mmio: [0xd1500000-0xd24fffff]
[    0.587357] bus: 02 index 3 mmio: [0x0-0x0]
[    0.587359] bus: 03 index 0 mmio: [0x0-0x0]
[    0.587360] bus: 03 index 1 mmio: [0x0-0x0]
[    0.587362] bus: 03 index 2 mmio: [0x0-0x0]
[    0.587363] bus: 03 index 3 io port: [0x00-0xffff]
[    0.587365] bus: 03 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.587375] NET: Registered protocol family 2
[    0.620557] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.621127] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.623480] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.624258] TCP: Hash tables configured (established 262144 bind 65536)
[    0.624261] TCP reno registered
[    0.632633] NET: Registered protocol family 1
[    0.632754] checking if image is initramfs... it is
[    1.302770] Freeing initrd memory: 7761k freed
[    **1.306564] Simple Boot Flag value 0x9 read from CMOS RAM was invalid**
[    1.306567] Simple Boot Flag at 0x44 set to 0x1
[    1.306877] audit: initializing netlink socket (disabled)
[    1.306892] type=2000 audit(1240314308.304:1): initialized
[    1.315124] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.316259] VFS: Disk quotas dquot_6.5.1
[    1.316309] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.316793] fuse init (API version 7.10)
[    1.316863] msgmni has been set to 5830
[    1.317013] alg: No test for stdrng (krng)
[    1.317022] io scheduler noop registered
[    1.317023] io scheduler anticipatory registered
[    1.317025] io scheduler deadline registered
[    1.317063] io scheduler cfq registered (default)
[    1.317074] pci 0000:00:02.0: Boot video device
[    1.319778] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.319827] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.319863] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.319878] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.319891] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.319901] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.319972] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.320020] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.320052] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.320068] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.320078] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.320090] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.320169] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.320903] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 2940 ss_vid 0 ss_did 0
[    1.320948] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
[    1.321518] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 2942 ss_vid 0 ss_did 0
[    1.321555] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
[    1.321563] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.323959] ACPI: AC Adapter [ADP1] (off-line)
[    1.500618] ACPI: Battery Slot [BAT0] (battery present)
[    1.500686] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.500688] ACPI: Power Button (FF) [PWRF]
[    1.500729] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.507448] ACPI: Lid Switch [LID0]
[    1.507490] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.507496] ACPI: Sleep Button (CM) [SLPB]
[    1.508256] ACPI: SSDT BBBB3C98, 0223 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    1.508847] ACPI: SSDT BBBB1598, 0537 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.509403] Monitor-Mwait will be used to enter C-1 state
[    1.509441] Monitor-Mwait will be used to enter C-2 state
[    1.509453] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.509476] processor ACPI_CPU:00: registered as cooling_device0
[    1.509479] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.510003] ACPI: SSDT BBBB2E18, 01CF (r1  PmRef    ApIst     3000 INTL 20051117)
[    1.510491] ACPI: SSDT BBBB3F18, 008D (r1  PmRef    ApCst     3000 INTL 20051117)
[    1.511112] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.511128] processor ACPI_CPU:01: registered as cooling_device1
[    1.511131] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.544790] thermal LNXTHERM:01: registered as thermal_zone0
[    1.558875] ACPI: Thermal Zone [TZS0] (27 C)
[    1.566081] thermal LNXTHERM:02: registered as thermal_zone1
[    1.570686] ACPI: Thermal Zone [TZS1] (27 C)
[    1.592269] Linux agpgart interface v0.103
[    1.592277] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.593138] brd: module loaded
[    1.593427] loop: module loaded
[    1.593503] Fixed MDIO Bus: probed
[    1.593507] PPP generic driver version 2.4.2
[    1.593560] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.593588] Driver 'sd' needs updating - please use bus_type methods
[    1.593596] Driver 'sr' needs updating - please use bus_type methods
[    1.593631] ahci 0000:00:1f.2: version 3.0
[    1.593649] ahci 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    1.593692] ahci 0000:00:1f.2: irq 2301 for MSI/MSI-X
[    1.593784] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.593787] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ems 
[    1.593792] ahci 0000:00:1f.2: setting latency timer to 64
[    1.594097] scsi0 : ahci
[    1.594199] scsi1 : ahci
[    1.594245] scsi2 : ahci
[    1.594294] scsi3 : ahci
[    1.594339] scsi4 : ahci
[    1.594386] scsi5 : ahci
[    1.594554] ata1: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705100 irq 2301
[    1.594557] ata2: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705180 irq 2301
[    1.594559] ata3: DUMMY
[    1.594560] ata4: DUMMY
[    1.594562] ata5: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705300 irq 2301
[    1.594565] ata6: SATA max UDMA/133 abar m2048@0xd4705000 port 0xd4705380 irq 2301
[    2.076015] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.076885] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.076890] ata1.00: ATA-8: TOSHIBA MK3252GSX, LV011C, max UDMA/100
[    2.076892] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.077780] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    2.077796] ata1.00: configured for UDMA/100
[    2.576014] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.591875] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    2.591878] ata2.00: ATAPI: Slimtype DVD A  DS8A2L-A, 7H63, max UDMA/100
[    2.607649] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[    2.607666] ata2.00: configured for UDMA/100
[    2.944016] ata5: SATA link down (SStatus 0 SControl 300)
[    3.280016] ata6: SATA link down (SStatus 0 SControl 300)
[    3.296107] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    3.296195] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.296211] sd 0:0:0:0: [sda] Write Protect is off
[    3.296213] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.296236] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.296303] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.296316] sd 0:0:0:0: [sda] Write Protect is off
[    3.296318] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.296340] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.296343]  sda: sda1 sda2 < sda5 >
[    3.415250] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.415294] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.418129] scsi 1:0:0:0: CD-ROM            Slimtype DVD A  DS8A2L-A  7H63 PQ: 0 ANSI: 5
[    3.427195] sr0: scsi3-mmc drive: 24x/6x writer dvd-ram cd/rw xa/form2 cdda pop-up
[    3.427198] Uniform CD-ROM driver Revision: 3.20
[    3.427285] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.427329] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.427862] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.427887] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 18 (level, low) -> IRQ 18
[    3.427906] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.427909] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.427962] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.431871] ehci_hcd 0000:00:1a.7: debug port 1
[    3.431878] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.431894] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xd4705c00
[    3.444009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.444066] usb usb1: configuration #1 chosen from 1 choice
[    3.444088] hub 1-0:1.0: USB hub found
[    3.444095] hub 1-0:1.0: 6 ports detected
[    3.444196] ehci_hcd 0000:00:1d.7: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.444208] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.444211] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.444248] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.448168] ehci_hcd 0000:00:1d.7: debug port 1
[    3.448174] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.448179] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd4705800
[    3.460008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.460051] usb usb2: configuration #1 chosen from 1 choice
[    3.460074] hub 2-0:1.0: USB hub found
[    3.460081] hub 2-0:1.0: 6 ports detected
[    3.460166] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.460179] uhci_hcd: USB Universal Host Controller Interface driver
[    3.460205] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.460212] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.460215] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.460259] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.460288] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000050e0
[    3.460356] usb usb3: configuration #1 chosen from 1 choice
[    3.460376] hub 3-0:1.0: USB hub found
[    3.460382] hub 3-0:1.0: 2 ports detected
[    3.460461] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.460467] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.460470] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.460521] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.460556] uhci_hcd 0000:00:1a.1: irq 19, io base 0x000050c0
[    3.460618] usb usb4: configuration #1 chosen from 1 choice
[    3.460639] hub 4-0:1.0: USB hub found
[    3.460644] hub 4-0:1.0: 2 ports detected
[    3.460723] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    3.460729] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.460732] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.460772] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.460805] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000050a0
[    3.460866] usb usb5: configuration #1 chosen from 1 choice
[    3.460888] hub 5-0:1.0: USB hub found
[    3.460893] hub 5-0:1.0: 2 ports detected
[    3.460969] uhci_hcd 0000:00:1d.0: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    3.460976] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.460979] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.461013] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.461039] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00005080
[    3.461107] usb usb6: configuration #1 chosen from 1 choice
[    3.461127] hub 6-0:1.0: USB hub found
[    3.461132] hub 6-0:1.0: 2 ports detected
[    3.461207] uhci_hcd 0000:00:1d.1: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    3.461213] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.461216] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.461251] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.461277] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005060
[    3.461341] usb usb7: configuration #1 chosen from 1 choice
[    3.461361] hub 7-0:1.0: USB hub found
[    3.461366] hub 7-0:1.0: 2 ports detected
[    3.461441] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 17 (level, low) -> IRQ 17
[    3.461447] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.461450] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.461499] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.461527] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00005040
[    3.461594] usb usb8: configuration #1 chosen from 1 choice
[    3.461616] hub 8-0:1.0: USB hub found
[    3.461621] hub 8-0:1.0: 2 ports detected
[    3.461739] usbcore: registered new interface driver libusual
[    3.461770] usbcore: registered new interface driver usbserial
[    3.461779] USB Serial support registered for generic
[    3.461791] usbcore: registered new interface driver usbserial_generic
[    3.461793] usbserial: USB Serial Driver core
[    3.461831] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.480754] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.493454] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.493460] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.493462] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.493464] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.493466] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.504532] mice: PS/2 mouse device common for all mice
[    3.552559] rtc_cmos 00:03: RTC can wake from S4
[    3.552589] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.552620] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.552686] device-mapper: uevent: version 1.0.3
[    3.552774] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.552839] device-mapper: multipath: version 1.0.5 loaded
[    3.552842] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.552965] cpuidle: using governor ladder
[    3.553037] cpuidle: using governor menu
[    3.553415] TCP cubic registered
[    3.553473] NET: Registered protocol family 10
[    3.553827] lo: Disabled Privacy Extensions
[    3.554075] NET: Registered protocol family 17
[    3.554095] Bluetooth: L2CAP ver 2.11
[    3.554096] Bluetooth: L2CAP socket layer initialized
[    3.554099] Bluetooth: SCO (Voice Link) ver 0.6
[    3.554100] Bluetooth: SCO socket layer initialized
[    3.554136] Bluetooth: RFCOMM socket layer initialized
[    3.554141] Bluetooth: RFCOMM TTY layer initialized
[    3.554143] Bluetooth: RFCOMM ver 1.10
[    3.554804] registered taskstats version 1
[    3.554933]   Magic number: 5:965:782
[    3.555034] Marking TSC unstable due to TSC halts in idle
[    3.555041] rtc_cmos 00:03: setting system clock to 2009-04-21 11:45:11 UTC (1240314311)
[    3.555044] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.555046] EDD information not available.
[    3.555107] Freeing unused kernel memory: 536k freed
[    3.555289] Write protecting the kernel read-only data: 6708k
[    3.574638] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.772049] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    3.951789] usb 1-3: configuration #1 chosen from 1 choice
[    3.957456] Initializing USB Mass Storage driver...
[    3.959197] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.959786] usbcore: registered new interface driver usb-storage
[    3.959789] USB Mass Storage support registered.
[    3.959889] usb-storage: device found at 2
[    3.959890] usb-storage: waiting for device to settle before scanning
[    4.050672] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.050704] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.050724] r8169 0000:01:00.0: setting latency timer to 64
[    4.050833] r8169 0000:01:00.0: irq 2300 for MSI/MSI-X
[    4.051390] eth0: RTL8102e at 0xffffc2000007a000, 00:1f:16:57:2c:88, XID 34a00000 IRQ 2300
[    4.068393] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    4.251300] usb 1-5: configuration #1 chosen from 1 choice
[    4.357750] PM: Starting manual resume from disk
[    4.357753] PM: Resume from partition 8:5
[    4.357755] PM: Checking hibernation image.
[    4.357948] PM: Resume from disk failed.
[    4.414716] kjournald starting.  Commit interval 5 seconds
[    4.414735] EXT3-fs: mounted filesystem with ordered data mode.
[    4.500049] Clocksource tsc unstable (delta = -145499623 ns)
[    8.956433] usb-storage: device scan complete
[    8.956468] isa bounce pool size: 16 pages
[    8.958368] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    8.960685] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    8.960738] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    9.256326] udev: starting version 141
[    9.556619] cfg80211: Calling CRDA to update world regulatory domain
[    9.632422] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.702216] iTCO_vendor_support: vendor-support=0
[    9.703728] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.703898] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[    9.704000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.728323] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    9.728814] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    9.731770] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    9.753378] Linux video capture interface: v2.00
[    9.912031] uvcvideo: Found UVC 1.00 device CNF7047 (04f2:b091)
[    9.913578] input: CNF7047 as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input6
[   [b] 9.920841] ath5k_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.920853] ath5k_pci 0000:02:00.0: setting latency timer to 64
[    9.921015] ath5k_pci 0000:02:00.0: registered as 'phy0'
[    9.932532] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.934660] acpi device:04: registered as cooling_device2
[    9.935152] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7
[    9.961368] phy0: Selected rate control algorithm 'pid'
[    9.968202] usbcore: registered new interface driver uvcvideo
[    9.968228] USB Video Class driver (v0.1.0)
[    9.996647] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   10.039438] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: [/b]0x70)
[   10.059689] cfg80211: World regulatory domain updated:
[   10.059693] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.059695] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.059697] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.059699] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.059701] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.059703] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.437177] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.437265] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.712715] lp: driver loaded but no devices found
[   10.796119] Adding 8747352k swap on /dev/sda5.  Priority:-1 extents:1 across:8747352k
[   10.909857] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1a0b1, caps: 0xd04711/0xa00000
[   10.975547] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input8
[   11.336669] EXT3 FS on sda1, internal journal
[   12.511053] type=1505 audit(1240314320.452:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2095
[   12.549526] type=1505 audit(1240314320.493:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2099
[   12.549659] type=1505 audit(1240314320.493:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2099
[   12.549698] type=1505 audit(1240314320.493:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2099
[   12.549732] type=1505 audit(1240314320.493:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2099
[   12.657015] type=1505 audit(1240314320.601:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2104
[   12.657197] type=1505 audit(1240314320.601:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2104
[   12.682235] type=1505 audit(1240314320.625:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2108
[   15.322451] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.322454] Bluetooth: BNEP filters: protocol multicast
[   15.330065] Bridge firewalling registered
[   17.351882] ppdev: user-space parallel port driver
[   19.150608] [drm] Initialized drm 1.1.0 20060810
[   19.155274] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.155279] pci 0000:00:02.0: setting latency timer to 64
[   19.155543] pci 0000:00:02.0: irq 2299 for MSI/MSI-X
[   19.155628] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   **19.158187] [drm:i915_setparam] *ERROR* unknown parameter 4**
[   21.056430] r8169: eth0: link down
[   21.057254] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.094203] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.031618] wlan0: authenticate with AP 00:1d:7e:2a:d1:18
[   23.033065] wlan0: authenticated
[   23.033068] wlan0: associate with AP 00:1d:7e:2a:d1:18
[   23.035212] wlan0: RX AssocResp from 00:1d:7e:2a:d1:18 (capab=0x401 status=0 aid=3)
[   23.035215] wlan0: associated
[   23.035640] wlan0: disassociating by local choice (reason=3)
[   36.964412] CPU0 attaching NULL sched-domain.
[   36.964418] CPU1 attaching NULL sched-domain.
[   36.980604] CPU0 attaching sched-domain:
[   36.980607]  domain 0: span 0-1 level MC
[   36.980609]   groups: 0 1
[   36.980614] CPU1 attaching sched-domain:
[   36.980615]  domain 0: span 0-1 level MC
[   36.980617]   groups: 1 0
[   52.572995] wlan0: authenticate with AP 00:14:bf:10:e3:4a
[   52.574493] wlan0: authenticated
[   52.574497] wlan0: associate with AP 00:14:bf:10:e3:4a
[   52.576539] wlan0: RX AssocResp from 00:14:bf:10:e3:4a (capab=0x411 status=0 aid=1)
[   52.576542] wlan0: associated
[   52.577409] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.604040] wlan0: no IPv6 routers present

```

---

### Post by missbliss on 2009-04-21
Bump for any other info!

---

### Post by soccerush10 on 2009-04-21
This isn't worth much, but I wish I was more experienced so that I could help.  I commend anyone that takes their time to help out on the forums.

---

### Post by kevdog on 2009-04-21
I guess Im more confused.  Your dmesg states you have an internet connection:

[   52.572995] wlan0: authenticate with AP 00:14:bf:10:e3:4a
[   52.574493] wlan0: authenticated
[   52.574497] wlan0: associate with AP 00:14:bf:10:e3:4a
[   52.576539] wlan0: RX AssocResp from 00:14:bf:10:e3:4a (capab=0x411 status=0 aid=1)
[   52.576542] wlan0: associated


I'm not sure what to suggest since some of the output you give us is conflicting.  In some cases you have a connection, in others you do not! Have you tried unloading and reloading the driver (modprobe statements) and then making a manual connection?  A helpful link may be found in my signature.  Its also possibly a driver problem.  I dont know a lot about the ath5k_pci driver -- Have you found more info on this driver on google or the linuxwireless.org website?

---

### Post by missbliss on 2009-04-21
Thanks for the help kevdog.  One more question:  Why would my wireless connection be fine in Intrepid but have a problem in Jaunty?  How could I have messed up a driver (or something else) just by doing an install?

---

### Post by kevdog on 2009-04-21
Here is what I suspect -- the ath5k open source driver contained within the newer Jaunty kernel is different than that contained in the Intrepid kernel.  The ath5k is an internal kernel module compiled into the kernel (if you ever compile your own kernel you have the option to include support for ath5k or not!).  My suspicion is that the ath5k driver was updated with the new kernel, possibly causing problems.  You can always recompile the ath5k from source and try this version if you need to.  I would definitely do a search for problems related to ath5k and your kernel version -- which can be found by typing
uname -r 
at the command line.  Hopefully with the mainline Jaunty release in a few days, this problem will be explored and a solution found.  Its difficult for me to support you on this problem since I don't own that chipset or a similar chipset supported by ath5k and Im not currently running Jaunty.  Ill upgrade after a week or two after the release when all the activity settles down.

---

### Post by missbliss on 2009-04-21
> **kevdog said:**
> Here is what I suspect -- the ath5k open source driver contained within the newer Jaunty kernel is different than that contained in the Intrepid kernel.  The ath5k is an internal kernel module compiled into the kernel (if you ever compile your own kernel you have the option to include support for ath5k or not!).  My suspicion is that the ath5k driver was updated with the new kernel, possibly causing problems.  You can always recompile the ath5k from source and try this version if you need to.  I would definitely do a search for problems related to ath5k and your kernel version -- which can be found by typing
uname -r 
at the command line.  Hopefully with the mainline Jaunty release in a few days, this problem will be explored and a solution found.  Its difficult for me to support you on this problem since I don't own that chipset or a similar chipset supported by ath5k and Im not currently running Jaunty.  Ill upgrade after a week or two after the release when all the activity settles down.

Thanks a lot for the info.  I'll probably just go back to 8.10 if I can't figure it out after a few weeks.

---

### Post by 3rdalbum on 2009-04-21
I don't know for certain if that chipset is supported by the procedure, but a lot of people eschew the "ath5k" driver in favour of compiling the latest version of "madwifi".

---

### Post by kevdog on 2009-04-22
Compiling a patched version of madwifi (need the patch due to the particular chipset) is definitely an option.  There are instructions somewhere on this forums and also out in the wild on many internet sites how to do this.  Its not too hard, but if you have never compiled anything before, this method is slightly intimidating.

---

### Post by iponeverything on 2009-04-22
what does

```
iwconfig wlan0 
```

tell you about your connect speed? ie the "Bit Rate="

does the connection improve with:

```
sudo iwconfig wlan0 rate 54M
```

---

### Post by missbliss on 2009-04-22
> **3rdalbum said:**
> I don't know for certain if that chipset is supported by the procedure, but a lot of people eschew the "ath5k" driver in favour of compiling the latest version of "madwifi".

Oh, this post was really helpful.  I'm not too savvy on all this stuff!  I believe that's the problem.  In 8.10 I used madwifi.  In Jaunty I just let the OS pick up the wireless connection after plugging in the wep key and just assumed it did automatically what I had done manually before.  

Hope that makes sense!

I'm gonna give the madwifi thing a go.  I feel pretty confident that should help.

---

