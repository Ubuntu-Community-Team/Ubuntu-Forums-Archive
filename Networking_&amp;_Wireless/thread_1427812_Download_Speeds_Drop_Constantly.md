---
title: "Download Speeds Drop Constantly"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by machavelli on 2010-03-12
Hello, I am running Ubuntu 9.10 on a Dell inspiron 1520 with intel 3945abg wireless card. I am fairly new to linux and just installed it earlier in the day. Everything so far has been easy to setup and get running as well as the networking or so i though... 

I can connect to my network and browse we pages just fine. However, when I download a file the speed starts high, drops down to around 50kbps and then works its way back up to around 1.3 mbps before dropping right back down. I tested a file on megaupload and it seems to bounce between 50kbps and 1.5mbps nonstop.

The driver i believe is the iwl3945 if that is the default driver. I have tried disabling ipv6 and that didnt seem to change anything. I've looked around on google and the forums and havent been able to find anything on how to fix this.

---

### Post by The Toxic Mite on 2010-03-12
Hey!
 
Go to Applications > Accessories > Terminal, and type in the following commands:
 
```

sudo lshw -c network
lspci -v
dmesg
iwconfig

```
 
Post the outputs when done :-)

---

### Post by machavelli on 2010-03-12
justin@justin-laptop:~$ sudo lshw -c network
[sudo] password for justin: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:9c:6a:90
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:f9fff000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:83:ef:13
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff







justin@justin-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Dell Device 01f1
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fa000000-feafffff
    Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f20 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f00 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
    Subsystem: Dell Device 01f1
    Flags: bus master, fast devsel, latency 0, IRQ 21
    Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    Memory behind bridge: f9f00000-f9ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f9c00000-f9efffff
    Prefetchable memory behind bridge: 00000000f8000000-00000000f81fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6f40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Memory behind bridge: f9b00000-f9bfffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 6fa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device 01f1
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 6eb0 [size=8]
    I/O ports at 6eb8 [size=4]
    I/O ports at 6ec0 [size=8]
    I/O ports at 6ec8 [size=4]
    I/O ports at 6ee0 [size=16]
    I/O ports at eff0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
    Subsystem: Dell Device 01f1
    Flags: medium devsel, IRQ 10
    Memory at febfbf00 (32-bit, non-prefetchable) [size=256]
    I/O ports at 10c0 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
    Subsystem: Dell Device 01f1
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at f4000000 (64-bit, prefetchable) [size=64M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at df00 [size=128]
    [virtual] Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
    Subsystem: Dell Device 01f1
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at f9bfe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at f9bfd800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at f9bfd500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 64, IRQ 4
    Memory at f9bfd600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
    Subsystem: Dell Device 01f1
    Flags: bus master, medium devsel, latency 64, IRQ 4
    Memory at f9bfd700 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1020
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945









DMESG

[    0.400463] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfeafffff
[    0.400468] pci 0000:00:01.0:   PREFETCH window: 0x000000f4000000-0x000000f7ffffff
[    0.400474] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.400477] pci 0000:00:1c.0:   IO window: disabled
[    0.400485] pci 0000:00:1c.0:   MEM window: disabled
[    0.400491] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.400497] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.400500] pci 0000:00:1c.1:   IO window: disabled
[    0.400508] pci 0000:00:1c.1:   MEM window: 0xf9f00000-0xf9ffffff
[    0.400514] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.400521] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.400525] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
[    0.400534] pci 0000:00:1c.3:   MEM window: 0xf9c00000-0xf9efffff
[    0.400540] pci 0000:00:1c.3:   PREFETCH window: 0x000000f8000000-0x000000f81fffff
[    0.400551] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.400554] pci 0000:00:1e.0:   IO window: disabled
[    0.400562] pci 0000:00:1e.0:   MEM window: 0xf9b00000-0xf9bfffff
[    0.400568] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.400582]   alloc irq_desc for 16 on node -1
[    0.400585]   alloc kstat_irqs on node -1
[    0.400591] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.400597] pci 0000:00:01.0: setting latency timer to 64
[    0.400608] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.400614] pci 0000:00:1c.0: setting latency timer to 64
[    0.400625]   alloc irq_desc for 17 on node -1
[    0.400627]   alloc kstat_irqs on node -1
[    0.400632] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.400639] pci 0000:00:1c.1: setting latency timer to 64
[    0.400652]   alloc irq_desc for 19 on node -1
[    0.400654]   alloc kstat_irqs on node -1
[    0.400659] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.400665] pci 0000:00:1c.3: setting latency timer to 64
[    0.400676] pci 0000:00:1e.0: setting latency timer to 64
[    0.400682] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.400685] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.400689] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.400692] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfeafffff]
[    0.400696] pci_bus 0000:01: resource 2 pref mem [0xf4000000-0xf7ffffff]
[    0.400700] pci_bus 0000:0c: resource 1 mem: [0xf9f00000-0xf9ffffff]
[    0.400703] pci_bus 0000:0d: resource 0 io:  [0xc000-0xcfff]
[    0.400707] pci_bus 0000:0d: resource 1 mem: [0xf9c00000-0xf9efffff]
[    0.400710] pci_bus 0000:0d: resource 2 pref mem [0xf8000000-0xf81fffff]
[    0.400714] pci_bus 0000:03: resource 1 mem: [0xf9b00000-0xf9bfffff]
[    0.400717] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.400720] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.400764] NET: Registered protocol family 2
[    0.400887] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.401292] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.401857] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.402104] TCP: Hash tables configured (established 131072 bind 65536)
[    0.402107] TCP reno registered
[    0.402195] NET: Registered protocol family 1
[    0.402266] Trying to unpack rootfs image as initramfs...
[    0.501772] Switched to high resolution mode on CPU 1
[    0.504019] Switched to high resolution mode on CPU 0
[    0.650136] Freeing initrd memory: 7466k freed
[    0.654663] Simple Boot Flag at 0x79 set to 0x1
[    0.654898] cpufreq-nforce2: No nForce2 chipset.
[    0.654934] Scanning for low memory corruption every 60 seconds
[    0.655063] audit: initializing netlink socket (disabled)
[    0.655083] type=2000 audit(1268366718.652:1): initialized
[    0.666570] highmem bounce pool size: 64 pages
[    0.666576] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.668568] VFS: Disk quotas dquot_6.5.2
[    0.668661] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.669377] fuse init (API version 7.12)
[    0.669487] msgmni has been set to 1705
[    0.669754] alg: No test for stdrng (krng)
[    0.669773] io scheduler noop registered
[    0.669775] io scheduler anticipatory registered
[    0.669778] io scheduler deadline registered
[    0.669834] io scheduler cfq registered (default)
[    0.670025] pci 0000:01:00.0: Boot video device
[    0.670191]   alloc irq_desc for 24 on node -1
[    0.670194]   alloc kstat_irqs on node -1
[    0.670205] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.670215] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.670388]   alloc irq_desc for 25 on node -1
[    0.670391]   alloc kstat_irqs on node -1
[    0.670402] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.670415] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.670610]   alloc irq_desc for 26 on node -1
[    0.670612]   alloc kstat_irqs on node -1
[    0.670626] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.670640] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.670829]   alloc irq_desc for 27 on node -1
[    0.670832]   alloc kstat_irqs on node -1
[    0.670843] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.670857] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.670991] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.671149] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.671351] ACPI: AC Adapter [AC] (on-line)
[    0.671449] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.672062] ACPI: Lid Switch [LID]
[    0.672122] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.672130] ACPI: Power Button [PBTN]
[    0.672188] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.672192] ACPI: Sleep Button [SBTN]
[    0.672996] ACPI: SSDT 7fe6e5b8 001C0 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.673622] ACPI: SSDT 7fe6df4e 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.674108] Monitor-Mwait will be used to enter C-1 state
[    0.674141] Monitor-Mwait will be used to enter C-2 state
[    0.674171] Monitor-Mwait will be used to enter C-3 state
[    0.674182] Marking TSC unstable due to TSC halts in idle
[    0.674205] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.674237] processor LNXCPU:00: registered as cooling_device0
[    0.674242] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.674663] ACPI: SSDT 7fe6e778 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.675082] ACPI: SSDT 7fe6e533 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.675708] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.675740] processor LNXCPU:01: registered as cooling_device1
[    0.675745] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.684231] thermal LNXTHERM:01: registered as thermal_zone0
[    0.684242] ACPI: Thermal Zone [THM] (60 C)
[    0.684328] isapnp: Scanning for PnP cards...
[    0.766838] ACPI: Battery Slot [BAT0] (battery present)
[    1.042471] isapnp: No Plug & Play device found
[    1.043934] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.045690] brd: module loaded
[    1.046284] loop: module loaded
[    1.046372] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.046514] ata_piix 0000:00:1f.1: version 2.13
[    1.046529] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.046578] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.046675] scsi0 : ata_piix
[    1.046774] scsi1 : ata_piix
[    1.047537] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    1.047541] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    1.047571] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.047582] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.047762] ata2: port disabled. ignoring.
[    1.200065] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.200277] scsi2 : ata_piix
[    1.200353] scsi3 : ata_piix
[    1.201103] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    1.201112] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    1.202311] Fixed MDIO Bus: probed
[    1.202362] PPP generic driver version 2.4.2
[    1.202470] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.202492]   alloc irq_desc for 22 on node -1
[    1.202495]   alloc kstat_irqs on node -1
[    1.202502] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.202516] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.202520] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.202558] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.206481] ehci_hcd 0000:00:1a.7: debug port 1
[    1.206490] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.206506] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.221017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.221114] usb usb1: configuration #1 chosen from 1 choice
[    1.221150] hub 1-0:1.0: USB hub found
[    1.221160] hub 1-0:1.0: 4 ports detected
[    1.221229]   alloc irq_desc for 20 on node -1
[    1.221231]   alloc kstat_irqs on node -1
[    1.221237] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.221250] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.221254] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.221291] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.224555] ata1.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE04, max UDMA/33
[    1.225190] ehci_hcd 0000:00:1d.7: debug port 1
[    1.225199] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.225215] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.240028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.240103] usb usb2: configuration #1 chosen from 1 choice
[    1.240140] hub 2-0:1.0: USB hub found
[    1.240148] hub 2-0:1.0: 6 ports detected
[    1.240225] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.240247] uhci_hcd: USB Universal Host Controller Interface driver
[    1.240275] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.240283] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.240287] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.240328] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.240360] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    1.240459] usb usb3: configuration #1 chosen from 1 choice
[    1.240492] hub 3-0:1.0: USB hub found
[    1.240501] hub 3-0:1.0: 2 ports detected
[    1.240558]   alloc irq_desc for 21 on node -1
[    1.240561]   alloc kstat_irqs on node -1
[    1.240567] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.240575] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.240579] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.240615] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.240655] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    1.240753] usb usb4: configuration #1 chosen from 1 choice
[    1.240787] hub 4-0:1.0: USB hub found
[    1.240795] hub 4-0:1.0: 2 ports detected
[    1.240854] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.240863] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.240867] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.240908] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.240939] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    1.241051] usb usb5: configuration #1 chosen from 1 choice
[    1.241085] hub 5-0:1.0: USB hub found
[    1.241093] hub 5-0:1.0: 2 ports detected
[    1.241149] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.241158] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.241162] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.241200] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.241232] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    1.241327] usb usb6: configuration #1 chosen from 1 choice
[    1.241361] hub 6-0:1.0: USB hub found
[    1.241372] hub 6-0:1.0: 2 ports detected
[    1.241432] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.241440] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.241445] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.241485] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.241516] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.241622] usb usb7: configuration #1 chosen from 1 choice
[    1.241655] hub 7-0:1.0: USB hub found
[    1.241663] hub 7-0:1.0: 2 ports detected
[    1.241789] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.245095] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.245102] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.245178] mice: PS/2 mouse device common for all mice
[    1.245321] rtc_cmos 00:03: RTC can wake from S4
[    1.245363] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.245398] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.245526] device-mapper: uevent: version 1.0.3
[    1.245625] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.245745] device-mapper: multipath: version 1.1.0 loaded
[    1.245748] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.245895] EISA: Probing bus 0 at eisa.0
[    1.245904] Cannot allocate resource for EISA slot 1
[    1.245938] EISA: Detected 0 cards.
[    1.246165] cpuidle: using governor ladder
[    1.248604] cpuidle: using governor menu
[    1.249256] TCP cubic registered
[    1.249459] NET: Registered protocol family 10
[    1.250057] lo: Disabled Privacy Extensions
[    1.250511] NET: Registered protocol family 17
[    1.250538] Bluetooth: L2CAP ver 2.13
[    1.250541] Bluetooth: L2CAP socket layer initialized
[    1.250545] Bluetooth: SCO (Voice Link) ver 0.6
[    1.250547] Bluetooth: SCO socket layer initialized
[    1.250589] Bluetooth: RFCOMM TTY layer initialized
[    1.250593] Bluetooth: RFCOMM socket layer initialized
[    1.250596] Bluetooth: RFCOMM ver 1.11
[    1.251183] Using IPI No-Shortcut mode
[    1.251257] PM: Resume from disk failed.
[    1.251272] registered taskstats version 1
[    1.251425]   Magic number: 2:815:59
[    1.251527] rtc_cmos 00:03: setting system clock to 2010-03-12 04:05:19 UTC (1268366719)
[    1.251531] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.251534] EDD information not available.
[    1.256462] ata1.00: configured for UDMA/33
[    1.258070] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.288801] scsi 0:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE04 PQ: 0 ANSI: 5
[    1.328849] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.328855] Uniform CD-ROM driver Revision: 3.20
[    1.329022] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.329093] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.500078] Clocksource tsc unstable (delta = -218341257 ns)
[    1.852135] ata4.00: SATA link down (SStatus 0 SControl 300)
[    1.852162] ata4.01: SATA link down (SStatus 0 SControl 0)
[    1.940057] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.004163] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.004187] ata3.01: SATA link down (SStatus 0 SControl 300)
[    2.012590] ata3.00: ATA-7: ST9160821AS, 3.CDD, max UDMA/133
[    2.012596] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    2.028622] ata3.00: configured for UDMA/133
[    2.028794] scsi 2:0:0:0: Direct-Access     ATA      ST9160821AS      3.CD PQ: 0 ANSI: 5
[    2.029018] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.029043] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.029100] sd 2:0:0:0: [sda] Write Protect is off
[    2.029104] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.029135] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.029290]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    2.074784] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.074819] Freeing unused kernel memory: 540k freed
[    2.075233] Write protecting the kernel text: 4580k
[    2.075308] Write protecting the kernel read-only data: 1840k
[    2.122549] usb 3-2: configuration #1 chosen from 1 choice
[    2.124480] hub 3-2:1.0: USB hub found
[    2.126447] hub 3-2:1.0: 3 ports detected
[    2.257842] Linux agpgart interface v0.103
[    2.271952] acpi device:32: registered as cooling_device2
[    2.273096] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input5
[    2.273141] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    2.321595] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.400056] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    2.400146] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    2.400179] b44.c:v2.0
[    2.400220] ohci1394 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.417095] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:83:ef:13
[    2.458202] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f9bfd800-f9bfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.585189] usb 5-2: configuration #1 chosen from 1 choice
[    2.595249] usbcore: registered new interface driver hiddev
[    2.609448] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input6
[    2.609530] generic-usb 0003:045E:0063.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:1d.0-2/input0
[    2.672181] input: Microsoft Microsoft Wireless Optical Desktop® 1.00 as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.1/input/input7
[    2.672304] generic-usb 0003:045E:0063.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 1.00] on usb-0000:00:1d.0-2/input1
[    2.672326] usbcore: registered new interface driver usbhid
[    2.672329] usbhid: v2.6:USB HID core driver
[    2.888060] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    3.162446] usb 6-1: configuration #1 chosen from 1 choice
[    3.171661] input: Logitech G9x Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input8
[    3.171759] generic-usb 0003:046D:C066.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech G9x Laser Mouse] on usb-0000:00:1d.1-1/input0
[    3.180514] input: Logitech G9x Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input9
[    3.180629] generic-usb 0003:046D:C066.0004: input,hiddev96,hidraw3: USB HID v1.11 Keyboard [Logitech G9x Laser Mouse] on usb-0000:00:1d.1-1/input1
[    3.261488] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    3.398636] usb 3-2.1: configuration #1 chosen from 1 choice
[    3.477511] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    3.696592] usb 3-2.2: configuration #1 chosen from 1 choice
[    3.703816] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input10
[    3.703893] generic-usb 0003:0A5C:4502.0005: input,hidraw4: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    3.781524] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    3.820634] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[464fc00037b6b981]
[    3.911601] usb 3-2.3: configuration #1 chosen from 1 choice
[    3.919975] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input11
[    3.920103] generic-usb 0003:0A5C:4503.0006: input,hidraw5: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    4.157490] PM: Starting manual resume from disk
[    4.157496] PM: Resume from partition 8:5
[    4.157499] PM: Checking hibernation image.
[    4.157675] PM: Resume from disk failed.
[    4.168097] EXT4-fs (sda6): barriers enabled
[    4.178994] kjournald2 starting: pid 433, dev sda6:8, commit interval 5 seconds
[    4.179162] EXT4-fs (sda6): delayed allocation enabled
[    4.179166] EXT4-fs: file extents enabled
[    4.181355] EXT4-fs: mballoc enabled
[    4.181374] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    4.856661] type=1505 audit(1268366723.104:2): operation="profile_load" pid=458 name=/usr/share/gdm/guest-session/Xsession
[    4.859984] type=1505 audit(1268366723.104:3): operation="profile_load" pid=459 name=/sbin/dhclient3
[    4.861083] type=1505 audit(1268366723.109:4): operation="profile_load" pid=459 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.861611] type=1505 audit(1268366723.109:5): operation="profile_load" pid=459 name=/usr/lib/connman/scripts/dhclient-script
[    4.911185] type=1505 audit(1268366723.156:6): operation="profile_load" pid=460 name=/usr/bin/evince
[    4.926943] type=1505 audit(1268366723.173:7): operation="profile_load" pid=460 name=/usr/bin/evince-previewer
[    4.936250] type=1505 audit(1268366723.181:8): operation="profile_load" pid=460 name=/usr/bin/evince-thumbnailer
[    4.959666] type=1505 audit(1268366723.205:9): operation="profile_load" pid=462 name=/usr/lib/cups/backend/cups-pdf
[    4.960811] type=1505 audit(1268366723.205:10): operation="profile_load" pid=462 name=/usr/sbin/cupsd
[    5.917229] Adding 6000236k swap on /dev/sda5.  Priority:-1 extents:1 across:6000236k 
[    6.588000] EXT4-fs (sda6): internal journal on sda6:8
[    7.041538] EXT4-fs (sda7): barriers enabled
[    7.056674] kjournald2 starting: pid 514, dev sda7:8, commit interval 5 seconds
[    7.099247] EXT4-fs (sda7): internal journal on sda7:8
[    7.099255] EXT4-fs (sda7): delayed allocation enabled
[    7.099261] EXT4-fs: file extents enabled
[    7.114298] EXT4-fs: mballoc enabled
[    7.114317] EXT4-fs (sda7): mounted filesystem with ordered data mode
[    7.174126] udev: starting version 147
[    8.982591] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.169137] cfg80211: Calling CRDA to update world regulatory domain
[    9.216336] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.273125] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    9.273279] usbcore: registered new interface driver btusb
[    9.289531] input: Dell WMI hotkeys as /devices/virtual/input/input12
[    9.394222] lp: driver loaded but no devices found
[    9.625151] sdhci: Secure Digital Host Controller Interface driver
[    9.625155] sdhci: Copyright(c) Pierre Ossman
[   10.024758] cfg80211: World regulatory domain updated:
[   10.024762]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.024766]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.024770]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.024773]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.024777]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.024780]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.515560] nvidia: module license 'NVIDIA' taints kernel.
[   10.515566] Disabling lock debugging due to kernel taint
[   10.770326] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.770337] nvidia 0000:01:00.0: setting latency timer to 64
[   10.770536] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   10.952503] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   10.952525]   alloc irq_desc for 18 on node -1
[   10.952527]   alloc kstat_irqs on node -1
[   10.952535] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   10.954601] Registered led device: mmc0::
[   10.955636] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   10.992202] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   10.992206] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   10.992329] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.992345] iwl3945 0000:0c:00.0: setting latency timer to 64
[   11.073692] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   11.073697] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.073833]   alloc irq_desc for 28 on node -1
[   11.073836]   alloc kstat_irqs on node -1
[   11.073874] iwl3945 0000:0c:00.0: irq 28 for MSI/MSI-X
[   11.471673] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   11.641551] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000
[   11.641560] serio: Synaptics pass-through port at isa0060/serio1/input0
[   11.679505] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[   12.349341] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.349374] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.461886] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input14
[   12.509484] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   12.509588] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   14.094355] __ratelimit: 3 callbacks suppressed
[   14.094359] type=1505 audit(1268366732.340:12): operation="profile_replace" pid=1010 name=/usr/share/gdm/guest-session/Xsession
[   14.096796] type=1505 audit(1268366732.344:13): operation="profile_replace" pid=1013 name=/sbin/dhclient3
[   14.097786] type=1505 audit(1268366732.344:14): operation="profile_replace" pid=1013 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.098318] type=1505 audit(1268366732.344:15): operation="profile_replace" pid=1013 name=/usr/lib/connman/scripts/dhclient-script
[   14.103395] type=1505 audit(1268366732.348:16): operation="profile_replace" pid=1014 name=/usr/bin/evince
[   14.119539] type=1505 audit(1268366732.364:17): operation="profile_replace" pid=1014 name=/usr/bin/evince-previewer
[   14.129285] type=1505 audit(1268366732.376:18): operation="profile_replace" pid=1014 name=/usr/bin/evince-thumbnailer
[   14.143038] type=1505 audit(1268366732.388:19): operation="profile_replace" pid=1018 name=/usr/lib/cups/backend/cups-pdf
[   14.144216] type=1505 audit(1268366732.392:20): operation="profile_replace" pid=1018 name=/usr/sbin/cupsd
[   14.148385] type=1505 audit(1268366732.396:21): operation="profile_replace" pid=1024 name=/usr/sbin/tcpdump
[   14.171395] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   14.444184] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   14.521692] Registered led device: iwl-phy0::radio
[   14.521733] Registered led device: iwl-phy0::assoc
[   14.521769] Registered led device: iwl-phy0::RX
[   14.521803] Registered led device: iwl-phy0::TX
[   14.541044] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.546407] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.022261] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.022265] Bluetooth: BNEP filters: protocol multicast
[   17.068019] Bridge firewalling registered
[   17.471574] ppdev: user-space parallel port driver
[   29.940012] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x00171701
[   49.209422] wlan0: authenticate with AP 00:23:69:1b:21:64
[   49.211226] wlan0: authenticated
[   49.211229] wlan0: associate with AP 00:23:69:1b:21:64
[   49.214136] wlan0: RX AssocResp from 00:23:69:1b:21:64 (capab=0x411 status=0 aid=1)
[   49.214141] wlan0: associated
[   49.219054] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.064245] wlan0: no IPv6 routers present
[  186.296070] CE: hpet increasing min_delta_ns to 15000 nsec
[  437.908161] CE: hpet increasing min_delta_ns to 22500 nsec
[ 3262.457366] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 3262.459225] SGI XFS Quota Management subsystem
[ 3262.467983] JFS: nTxBlock = 8192, nTxLock = 65536
[ 3262.497918] NTFS driver 2.1.29 [Flags: R/O MODULE].
[ 3262.532031] QNX4 filesystem 0.2.3 registered.
[ 5204.438805] CE: hpet increasing min_delta_ns to 33750 nsec
[ 7661.845078] CE: hpet increasing min_delta_ns to 50624 nsec
[14216.738621] wlan0: disassociating by local choice (reason=3)
[14233.706903] wlan0: authenticate with AP 00:23:69:1b:21:64
[14233.710132] wlan0: authenticated
[14233.710138] wlan0: associate with AP 00:23:69:1b:21:64
[14233.713452] wlan0: RX AssocResp from 00:23:69:1b:21:64 (capab=0x411 status=0 aid=1)
[14233.713456] wlan0: associated



IWCONFIG
justin@justin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"meade"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:1B:21:64   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by machavelli on 2010-03-12
Any ideas anybody? I've tried using openDNS and rebooting but nothing. The internet seems to load pages just as fast even when my file download speeds drops to around 50kbps. This is really an OS breaker if there is no fix as I will be downloading a lot of files.

---

### Post by machavelli on 2010-03-12
Edit: I tested the connection on a friend's network and the download speed stayed around a steady 695-699kbps and didnt vary more than 100kbps.

I am using an intel 3945abg wireless card and a linksys WRT54G2 router v1.5

---

