---
title: "Wireless connection very sluggish"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by devind25 on 2010-01-17
I have a Dell Inspiron 9300 laptop with Ubuntu 9.10 installed and for some reason my wireless connection is slow at times. What's weird is when downloading it's super fast but when browsing it is very sluggish at times. I was using FF for the longest time but then switched over to Opera to see if that would help any, and it didn't really seem to make a difference. All other users in the house have no problems browsing. I am using the Network Manager and not the other one that I am spacing on the name at the moment. Any help or tips would be greatly appreciated. Thanks.

---

### Post by The Toxic Mite on 2010-01-18
Hey!

Open a terminal, and post the outputs of the following commands, please:

```

sudo lshw -c network
lspci (or lsusb if it's a USB dongle)
iwconfig
dmesg

```

Thanks :)

-TTM-

---

### Post by devind25 on 2010-01-19
Ok here is everything.
```
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:14:22:d6:45:92
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:18 memory:dfcfe000-dfcfffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth2
       version: 05
       serial: 00:13:ce:22:0b:f0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.207 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:dfcfd000-dfcfdfff
```
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11g  ESSID:"netgear"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:13:10:44:CD:A5   
          Bit Rate:36 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=85/100  Signal level=-45 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:8

```
```
[    0.123501] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.123507] pci 0000:00:1d.7: PME# disabled
[    0.123607] pci 0000:00:1e.2: reg 10 io port: [0xed00-0xedff]
[    0.123616] pci 0000:00:1e.2: reg 14 io port: [0xec40-0xec7f]
[    0.123624] pci 0000:00:1e.2: reg 18 32bit mmio: [0xdffffe00-0xdfffffff]
[    0.123632] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xdffffd00-0xdffffdff]
[    0.123670] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.123674] pci 0000:00:1e.2: PME# disabled
[    0.123712] pci 0000:00:1e.3: reg 10 io port: [0xee00-0xeeff]
[    0.123720] pci 0000:00:1e.3: reg 14 io port: [0xec80-0xecff]
[    0.123767] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.123772] pci 0000:00:1e.3: PME# disabled
[    0.123858] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.123867] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.123871] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.123876] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0900-097f
[    0.123919] pci 0000:00:1f.2: reg 10 io port: [0x1f0-0x1f7]
[    0.123927] pci 0000:00:1f.2: reg 14 io port: [0x3f4-0x3f7]
[    0.123935] pci 0000:00:1f.2: reg 18 io port: [0x170-0x177]
[    0.123943] pci 0000:00:1f.2: reg 1c io port: [0x374-0x377]
[    0.123951] pci 0000:00:1f.2: reg 20 io port: [0xbfa0-0xbfaf]
[    0.123984] pci 0000:00:1f.2: PME# supported from D3hot
[    0.123989] pci 0000:00:1f.2: PME# disabled
[    0.124058] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.124117] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.124123] pci 0000:01:00.0: reg 14 io port: [0xde00-0xdeff]
[    0.124129] pci 0000:01:00.0: reg 18 32bit mmio: [0xdfdf0000-0xdfdfffff]
[    0.124145] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfe00000-0xdfe1ffff]
[    0.124163] pci 0000:01:00.0: supports D1 D2
[    0.124215] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.124219] pci 0000:00:01.0: bridge 32bit mmio: [0xdfd00000-0xdfefffff]
[    0.124223] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.124264] pci 0000:03:00.0: reg 10 32bit mmio: [0xdfcfe000-0xdfcfffff]
[    0.124320] pci 0000:03:00.0: supports D1 D2
[    0.124323] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124328] pci 0000:03:00.0: PME# disabled
[    0.124371] pci 0000:03:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.124396] pci 0000:03:01.0: supports D1 D2
[    0.124398] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124403] pci 0000:03:01.0: PME# disabled
[    0.124447] pci 0000:03:01.1: reg 10 32bit mmio: [0xdfcfc800-0xdfcfcfff]
[    0.124507] pci 0000:03:01.1: supports D1 D2
[    0.124510] pci 0000:03:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124515] pci 0000:03:01.1: PME# disabled
[    0.124558] pci 0000:03:01.2: reg 10 32bit mmio: [0xdfcfc700-0xdfcfc7ff]
[    0.124619] pci 0000:03:01.2: supports D1 D2
[    0.124621] pci 0000:03:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.124626] pci 0000:03:01.2: PME# disabled
[    0.124684] pci 0000:03:03.0: reg 10 32bit mmio: [0xdfcfd000-0xdfcfdfff]
[    0.124751] pci 0000:03:03.0: PME# supported from D0 D3hot D3cold
[    0.124757] pci 0000:03:03.0: PME# disabled
[    0.124814] pci 0000:00:1e.0: transparent bridge
[    0.124822] pci 0000:00:1e.0: bridge 32bit mmio: [0xdfc00000-0xdfcfffff]
[    0.124857] pci_bus 0000:00: on NUMA node 0
[    0.124862] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.125136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.125192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.131331] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.131448] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.131562] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.131675] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    0.131773] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.131874] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.131976] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.132194] SCSI subsystem initialized
[    0.132244] libata version 3.00 loaded.
[    0.132319] usbcore: registered new interface driver usbfs
[    0.132336] usbcore: registered new interface driver hub
[    0.132361] usbcore: registered new device driver usb
[    0.132489] ACPI: WMI: Mapper loaded
[    0.132491] PCI: Using ACPI for IRQ routing
[    0.132653] Bluetooth: Core ver 2.15
[    0.132681] NET: Registered protocol family 31
[    0.132684] Bluetooth: HCI device and connection manager initialized
[    0.132687] Bluetooth: HCI socket layer initialized
[    0.132689] NetLabel: Initializing
[    0.132691] NetLabel:  domain hash size = 128
[    0.132692] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.132707] NetLabel:  unlabeled traffic allowed by default
[    0.132862] hpet clockevent registered
[    0.132866] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.132873] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.132878] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.137808] pnp: PnP ACPI init
[    0.137825] ACPI: bus type pnp registered
[    0.164495] pnp 00:02: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164500] pnp 00:02: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164574] pnp 00:03: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164578] pnp 00:03: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.164582] pnp 00:03: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.165337] pnp: PnP ACPI: found 11 devices
[    0.165339] ACPI: ACPI bus type pnp unregistered
[    0.165343] PnPBIOS: Disabled by ACPI PNP
[    0.165355] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.165359] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.165362] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.165366] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.165369] system 00:00: iomem range 0x100000-0x7ffd9fff could not be reserved
[    0.165372] system 00:00: iomem range 0x7ffda000-0x7fffffff has been reserved
[    0.165376] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.165379] system 00:00: iomem range 0xffb00000-0xffffffff has been reserved
[    0.165383] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.165386] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.165390] system 00:00: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.165393] system 00:00: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.165397] system 00:00: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.165400] system 00:00: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.165403] system 00:00: iomem range 0xf0006000-0xf0006fff has been reserved
[    0.165407] system 00:00: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.165410] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.165417] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.165423] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.165427] system 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.165430] system 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.165433] system 00:03: ioport range 0x10e0-0x10ff has been reserved
[    0.165440] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.165444] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.165447] system 00:08: ioport range 0x920-0x92f has been reserved
[    0.165450] system 00:08: ioport range 0x930-0x93f has been reserved
[    0.165453] system 00:08: ioport range 0x940-0x97f has been reserved
[    0.200132] AppArmor: AppArmor Filesystem Enabled
[    0.200166] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.200169] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.200174] pci 0000:00:01.0:   MEM window: 0xdfd00000-0xdfefffff
[    0.200178] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xd7ffffff
[    0.200188] pci 0000:03:01.0: CardBus bridge, secondary bus 0000:04
[    0.200191] pci 0000:03:01.0:   IO window: 0x002000-0x0020ff
[    0.200196] pci 0000:03:01.0:   IO window: 0x002400-0x0024ff
[    0.200202] pci 0000:03:01.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.200207] pci 0000:03:01.0:   MEM window: 0x84000000-0x87ffffff
[    0.200213] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.200217] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.200223] pci 0000:00:1e.0:   MEM window: 0xdfc00000-0xdfcfffff
[    0.200229] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.200241]   alloc irq_desc for 16 on node -1
[    0.200244]   alloc kstat_irqs on node -1
[    0.200250] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.200254] pci 0000:00:01.0: setting latency timer to 64
[    0.200262] pci 0000:00:1e.0: setting latency timer to 64
[    0.200271] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.200275]   alloc irq_desc for 19 on node -1
[    0.200277]   alloc kstat_irqs on node -1
[    0.200281] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.200290] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.200293] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.200296] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.200299] pci_bus 0000:01: resource 1 mem: [0xdfd00000-0xdfefffff]
[    0.200302] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]
[    0.200305] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
[    0.200308] pci_bus 0000:03: resource 1 mem: [0xdfc00000-0xdfcfffff]
[    0.200311] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.200314] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.200317] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.200320] pci_bus 0000:04: resource 0 io:  [0x2000-0x20ff]
[    0.200323] pci_bus 0000:04: resource 1 io:  [0x2400-0x24ff]
[    0.200326] pci_bus 0000:04: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.200329] pci_bus 0000:04: resource 3 mem: [0x84000000-0x87ffffff]
[    0.200365] NET: Registered protocol family 2
[    0.200464] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.200785] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.201722] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.202310] TCP: Hash tables configured (established 131072 bind 65536)
[    0.202314] TCP reno registered
[    0.202442] NET: Registered protocol family 1
[    0.202529] Trying to unpack rootfs image as initramfs...
[    0.426462] Freeing initrd memory: 7472k freed
[    0.432371] Simple Boot Flag at 0x79 set to 0x1
[    0.432465] cpufreq-nforce2: No nForce2 chipset.
[    0.432497] Scanning for low memory corruption every 60 seconds
[    0.432630] audit: initializing netlink socket (disabled)
[    0.432653] type=2000 audit(1263881228.431:1): initialized
[    0.442205] highmem bounce pool size: 64 pages
[    0.442212] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.443724] VFS: Disk quotas dquot_6.5.2
[    0.443783] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.444375] fuse init (API version 7.12)
[    0.444472] msgmni has been set to 1705
[    0.444671] alg: No test for stdrng (krng)
[    0.444683] io scheduler noop registered
[    0.444686] io scheduler anticipatory registered
[    0.444688] io scheduler deadline registered
[    0.444735] io scheduler cfq registered (default)
[    0.444844] pci 0000:01:00.0: Boot video device
[    0.444951]   alloc irq_desc for 24 on node -1
[    0.444954]   alloc kstat_irqs on node -1
[    0.444963] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.444970] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.445042] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.445068] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.445627] ACPI: AC Adapter [AC] (on-line)
[    0.445719] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.446205] ACPI: Lid Switch [LID]
[    0.446251] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.446258] ACPI: Power Button [PBTN]
[    0.446301] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.446304] ACPI: Sleep Button [SBTN]
[    0.446704] Marking TSC unstable due to TSC halts in idle
[    0.446736] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    0.446761] processor LNXCPU:00: registered as cooling_device0
[    0.446765] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.447985] thermal LNXTHERM:01: registered as thermal_zone0
[    0.447985] ACPI: Thermal Zone [THM] (46 C)
[    0.450752] Switched to high resolution mode on CPU 0
[    0.468218] isapnp: Scanning for PnP cards...
[    0.784595] ACPI: Battery Slot [BAT0] (battery present)
[    0.828225] isapnp: No Plug & Play device found
[    0.829310] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.829683]   alloc irq_desc for 17 on node -1
[    0.829685]   alloc kstat_irqs on node -1
[    0.829692] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.829698] serial 0000:00:1e.3: PCI INT B disabled
[    0.830644] brd: module loaded
[    0.831104] loop: module loaded
[    0.831190] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.831261] ahci 0000:00:1f.2: version 3.0
[    0.831272] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.831282] ahci 0000:00:1f.2: PCI INT B disabled
[    0.831287] ahci: probe of 0000:00:1f.2 failed with error -22
[    0.831326] ata_piix 0000:00:1f.2: version 2.13
[    0.831332] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.831338] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.984029] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.984172] scsi0 : ata_piix
[    0.984247] scsi1 : ata_piix
[    0.985017] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.985020] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.985864] Fixed MDIO Bus: probed
[    0.985900] PPP generic driver version 2.4.2
[    0.985980] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.985998] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.986012] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.986016] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.986068] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.989981] ehci_hcd 0000:00:1d.7: debug port 1
[    0.989987] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.990497] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    1.004017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.004100] usb usb1: configuration #1 chosen from 1 choice
[    1.004131] hub 1-0:1.0: USB hub found
[    1.004140] hub 1-0:1.0: 8 ports detected
[    1.004214] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.004231] uhci_hcd: USB Universal Host Controller Interface driver
[    1.004253] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.004260] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.004263] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.004295] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.004321] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    1.004399] usb usb2: configuration #1 chosen from 1 choice
[    1.004426] hub 2-0:1.0: USB hub found
[    1.004433] hub 2-0:1.0: 2 ports detected
[    1.004480] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.004486] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.004490] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.004521] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.004556] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    1.004632] usb usb3: configuration #1 chosen from 1 choice
[    1.004662] hub 3-0:1.0: USB hub found
[    1.004675] hub 3-0:1.0: 2 ports detected
[    1.004721]   alloc irq_desc for 18 on node -1
[    1.004723]   alloc kstat_irqs on node -1
[    1.004729] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.004735] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.004739] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.004770] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.004804] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    1.004879] usb usb4: configuration #1 chosen from 1 choice
[    1.004905] hub 4-0:1.0: USB hub found
[    1.004911] hub 4-0:1.0: 2 ports detected
[    1.004957] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.004964] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.004968] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.005006] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.005040] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    1.005115] usb usb5: configuration #1 chosen from 1 choice
[    1.005141] hub 5-0:1.0: USB hub found
[    1.005147] hub 5-0:1.0: 2 ports detected
[    1.005244] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.009890] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.009896] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.009949] mice: PS/2 mouse device common for all mice
[    1.010060] rtc_cmos 00:06: RTC can wake from S4
[    1.010090] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.010121] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.010221] device-mapper: uevent: version 1.0.3
[    1.010299] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.010372] device-mapper: multipath: version 1.1.0 loaded
[    1.010375] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.010488] EISA: Probing bus 0 at eisa.0
[    1.010495] Cannot allocate resource for EISA slot 1
[    1.010497] Cannot allocate resource for EISA slot 2
[    1.010521] EISA: Detected 0 cards.
[    1.010613] cpuidle: using governor ladder
[    1.010699] cpuidle: using governor menu
[    1.011173] TCP cubic registered
[    1.011340] NET: Registered protocol family 10
[    1.011778] lo: Disabled Privacy Extensions
[    1.012101] NET: Registered protocol family 17
[    1.012117] Bluetooth: L2CAP ver 2.13
[    1.012119] Bluetooth: L2CAP socket layer initialized
[    1.012121] Bluetooth: SCO (Voice Link) ver 0.6
[    1.012123] Bluetooth: SCO socket layer initialized
[    1.012153] Bluetooth: RFCOMM TTY layer initialized
[    1.012156] Bluetooth: RFCOMM socket layer initialized
[    1.012158] Bluetooth: RFCOMM ver 1.11
[    1.012386] Using IPI No-Shortcut mode
[    1.012446] PM: Resume from disk failed.
[    1.012458] registered taskstats version 1
[    1.012567]   Magic number: 10:95:115
[    1.012645] rtc_cmos 00:06: setting system clock to 2010-01-19 06:07:09 UTC (1263881229)
[    1.012649] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.012651] EDD information not available.
[    1.014894] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.132126] Clocksource tsc unstable (delta = -117120972 ns)
[    1.176480] ata2.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462C, DE07, max UDMA/33
[    1.208392] ata2.00: configured for UDMA/33
[    1.208948] ata1.00: ATA-7: WDC WD1600BEVE-00UYT0, 01.04A01, max UDMA/100
[    1.208951] ata1.00: 312581808 sectors, multi 8: LBA48 
[    1.208966] ata1.00: applying bridge limits
[    1.225471] ata1.00: configured for UDMA/100
[    1.225602] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVE-0 01.0 PQ: 0 ANSI: 5
[    1.225717] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.225755] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.225803] sd 0:0:0:0: [sda] Write Protect is off
[    1.225807] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.225831] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.225961]  sda:
[    1.226782] scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462C DE07 PQ: 0 ANSI: 5
[    1.229430] sr0: scsi3-mmc drive: 10x/24x writer cd/rw xa/form2 cdda tray
[    1.229433] Uniform CD-ROM driver Revision: 3.20
[    1.229504] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.229545] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.236196]  sda1 sda2 sda3
[    1.269715] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.269730] Freeing unused kernel memory: 540k freed
[    1.270041] Write protecting the kernel text: 4568k
[    1.270079] Write protecting the kernel read-only data: 1836k
[    1.441125] Linux agpgart interface v0.103
[    1.548844] [drm] Initialized drm 1.1.0 20060810
[    1.571639] [drm] radeon default to kernel modesetting DISABLED.
[    1.571783] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.571788] pci 0000:01:00.0: setting latency timer to 64
[    1.571921] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    1.577708] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/device:22/input/input5
[    1.577744] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.604483] ohci1394 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.662038] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfcfc800-dfcfcfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.669210] b44 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.728087] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.728111] b44.c:v2.0
[    1.748821] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:d6:45:92
[    2.690080] PM: Starting manual resume from disk
[    2.690084] PM: Resume from partition 8:2
[    2.690087] PM: Checking hibernation image.
[    2.690308] PM: Resume from disk failed.
[    2.752550] kjournald starting.  Commit interval 5 seconds
[    2.752560] EXT3-fs: mounted filesystem with writeback data mode.
[    2.940156] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[334fc000377b98e1]
[    3.621071] type=1505 audit(1263881232.107:2): operation="profile_load" pid=372 name=/usr/share/gdm/guest-session/Xsession
[    3.648154] type=1505 audit(1263881232.135:3): operation="profile_load" pid=373 name=/sbin/dhclient3
[    3.648828] type=1505 audit(1263881232.135:4): operation="profile_load" pid=373 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.649194] type=1505 audit(1263881232.135:5): operation="profile_load" pid=373 name=/usr/lib/connman/scripts/dhclient-script
[    3.681389] type=1505 audit(1263881232.167:6): operation="profile_load" pid=374 name=/usr/bin/evince
[    3.692388] type=1505 audit(1263881232.179:7): operation="profile_load" pid=374 name=/usr/bin/evince-previewer
[    3.698844] type=1505 audit(1263881232.183:8): operation="profile_load" pid=374 name=/usr/bin/evince-thumbnailer
[    3.731009] type=1505 audit(1263881232.215:9): operation="profile_load" pid=376 name=/usr/lib/cups/backend/cups-pdf
[    3.731810] type=1505 audit(1263881232.215:10): operation="profile_load" pid=376 name=/usr/sbin/cupsd
[   18.726574] udev: starting version 147
[   18.750949] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k 
[   19.203606] udev: renamed network interface eth0 to eth1
[   19.275187] lib80211: common routines for IEEE802.11 drivers
[   19.275191] lib80211_crypt: registered algorithm 'NULL'
[   19.660968] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   19.660972] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   19.662558] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.752609] EXT3 FS on sda1, internal journal
[   20.132726] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   20.132730] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   20.132810] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.132876] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   20.132915] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[   20.141151] sdhci: Secure Digital Host Controller Interface driver
[   20.141154] sdhci: Copyright(c) Pierre Ossman
[   20.153248] intel_rng: FWH not detected
[   20.325863] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   20.326841] sdhci-pci 0000:03:01.2: SDHCI controller found [1180:0822] (rev 17)
[   20.326860] sdhci-pci 0000:03:01.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[   20.328922] Registered led device: mmc0::
[   20.329948] mmc0: SDHCI controller on PCI [0000:03:01.2] using DMA
[   20.351204] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:0189]
[   20.477452] dell-wmi: No known WMI GUID found
[   20.480775] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   20.480780] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   20.480784] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   20.480792] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   20.480796] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   20.481004] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0xdfc00000 - 0xdfcfffff
[   20.481007] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   20.500249] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.530741] lp: driver loaded but no devices found
[   20.624192] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
[   20.643876] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[   20.740417] udev: renamed network interface eth0 to eth2
[   20.842020] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.842054] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   21.418786] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   21.420490] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   21.421203] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   21.421806] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   21.422559] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   21.427264] kjournald starting.  Commit interval 5 seconds
[   21.427707] EXT3 FS on sda3, internal journal
[   21.427712] EXT3-fs: mounted filesystem with writeback data mode.
[   21.668034] intel8x0_measure_ac97_clock: measured 55415 usecs (2670 samples)
[   21.668038] intel8x0: clocking to 48000
[   21.767067] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.882693] __ratelimit: 3 callbacks suppressed
[   21.882697] type=1505 audit(1263881250.367:12): operation="profile_replace" pid=894 name=/usr/share/gdm/guest-session/Xsession
[   21.884299] type=1505 audit(1263881250.371:13): operation="profile_replace" pid=895 name=/sbin/dhclient3
[   21.884976] type=1505 audit(1263881250.371:14): operation="profile_replace" pid=895 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   21.885347] type=1505 audit(1263881250.371:15): operation="profile_replace" pid=895 name=/usr/lib/connman/scripts/dhclient-script
[   21.890549] type=1505 audit(1263881250.375:16): operation="profile_replace" pid=896 name=/usr/bin/evince
[   21.905930] type=1505 audit(1263881250.391:17): operation="profile_replace" pid=896 name=/usr/bin/evince-previewer
[   21.912983] type=1505 audit(1263881250.399:18): operation="profile_replace" pid=896 name=/usr/bin/evince-thumbnailer
[   21.922962] type=1505 audit(1263881250.407:19): operation="profile_replace" pid=900 name=/usr/lib/cups/backend/cups-pdf
[   21.923762] type=1505 audit(1263881250.407:20): operation="profile_replace" pid=900 name=/usr/sbin/cupsd
[   21.926748] type=1505 audit(1263881250.411:21): operation="profile_replace" pid=901 name=/usr/sbin/tcpdump
[   22.771583] ppdev: user-space parallel port driver
[   22.923988] [drm] Setting GART location based on new memory map
[   22.925785] [drm] Loading R300 Microcode
[   22.925827] [drm] Num pipes: 1
[   22.925835] [drm] writeback test succeeded in 1 usecs
[   32.784013] eth2: no IPv6 routers present
[ 1295.897090] lib80211_crypt: registered algorithm 'CCMP'
[ 1295.993155] padlock: VIA PadLock not detected.
[ 1296.001245] lib80211_crypt: registered algorithm 'TKIP'
[ 1800.027749] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1800.027758] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1800.027765] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.

```
Not sure if that was all of it for that last one because I copied all that I could. Hope this helps. Thanks for the response.

---

### Post by devind25 on 2010-01-23
bump

---

### Post by devind25 on 2010-01-23
I have been doing some research and I am starting to wonder if it's because IPV6 is enabled. I tried to edit the GRUB using instructions from another site but when i do the command sudo gedit /etc/default/grub it opens up the text editor but nothing shows up so I can edit it. So not sure how to go about disabling it, any other tips would be greatly appreciated.

---

### Post by devind25 on 2010-01-29
bumping once again.

---

### Post by devind25 on 2010-02-02
Bump

---

