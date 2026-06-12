---
title: "Hp dm4 - Wired and wireless not working!"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by solrac418 on 2011-07-03
I got a new Hp Pavilion dm4 2015 dx. I installed Ubuntu 10.10 and my wired and wireless connections are not working.


My wireless card is an Intel Centrino Wireless-N + WiMax 6150 and my wired is an Atheros 

When I run lshw -c network it says that both networks are Unclaimed!

ANyone has any thoughts or suggestions???

---

### Post by chili555 on 2011-07-04
Which do you want to attack first? May I suggest wireless? I suspect you are lacking firmware. Let's see if there are any interesting kernel messages. Please open a terminal and run and post:```
dmesg | grep iwl
```You can copy and paste from the terminal to a text document and transfer it on a USB key or similar. If we find out firmware is the issue, we'll transfer a firmware file back to get wireless going.

The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

--------------------

Note to Chili:  [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz)

---

### Post by MaindotC on 2011-07-04
The proper place to start is the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  In order for your device to work properly you need the physical connectivity (plugged in all the way and/or turned on via your machine's BIOS), a driver to communicate between the device and the operating system, and then the proper configuration of the device which typically is via DHCP.  Please follow the guide and indicate at what point you are having difficulty.

---

### Post by solrac418 on 2011-07-05
When I type dmesg | grep iwl    Nothing happens

---

### Post by solrac418 on 2011-07-05
carlos@carlos-HP:~$ nm-tool

NetworkManager Tool

State: disconnected

carlos@carlos-HP:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c2500000-c2501fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c1400000-c143ffff ioport:2000(size=128)
carlos@carlos-HP:~$

---

### Post by chili555 on 2011-07-05
> **solrac418 said:**
> When I type dmesg | grep iwl    Nothing happensPerhaps that's the problem from the start; that the driver is not loading. Let's load it and then see if there are any informative messages:```
sudo modprobe iwlagn
dmesg | grep iwl
```If loading the driver starts your wireless, we can tweak one file to load it automatically on boot.

---

### Post by solrac418 on 2011-07-05
[    1.051600] _OSC request data:1 8 1f 
[    1.051605] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.052653] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.052656] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.052658] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.052662] pci_root PNP0A08:00: host bridge window [mem 0xafa00000-0xfeafffff]
[    1.052716] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    1.052722] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    1.052726] pci 0000:00:02.0: reg 20: [io  0x4000-0x403f]
[    1.052826] pci 0000:00:16.0: reg 10: [mem 0xc2604000-0xc260400f 64bit]
[    1.052896] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.052901] pci 0000:00:16.0: PME# disabled
[    1.052977] pci 0000:00:1a.0: reg 10: [mem 0xc2609000-0xc26093ff]
[    1.053060] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.053065] pci 0000:00:1a.0: PME# disabled
[    1.053121] pci 0000:00:1b.0: reg 10: [mem 0xc2600000-0xc2603fff 64bit]
[    1.053196] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.053201] pci 0000:00:1b.0: PME# disabled
[    1.053320] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.053325] pci 0000:00:1c.0: PME# disabled
[    1.053449] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.053454] pci 0000:00:1c.2: PME# disabled
[    1.053577] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.053582] pci 0000:00:1c.4: PME# disabled
[    1.053658] pci 0000:00:1d.0: reg 10: [mem 0xc2608000-0xc26083ff]
[    1.053741] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.053747] pci 0000:00:1d.0: PME# disabled
[    1.053934] pci 0000:00:1f.2: reg 10: [io  0x4088-0x408f]
[    1.053943] pci 0000:00:1f.2: reg 14: [io  0x4094-0x4097]
[    1.053952] pci 0000:00:1f.2: reg 18: [io  0x4080-0x4087]
[    1.053961] pci 0000:00:1f.2: reg 1c: [io  0x4090-0x4093]
[    1.053969] pci 0000:00:1f.2: reg 20: [io  0x4060-0x407f]
[    1.053978] pci 0000:00:1f.2: reg 24: [mem 0xc2607000-0xc26077ff]
[    1.054037] pci 0000:00:1f.2: PME# supported from D3hot
[    1.054042] pci 0000:00:1f.2: PME# disabled
[    1.054089] pci 0000:00:1f.3: reg 10: [mem 0xc2605000-0xc26050ff 64bit]
[    1.054113] pci 0000:00:1f.3: reg 20: [io  0x4040-0x405f]
[    1.054298] pci 0000:01:00.0: reg 10: [mem 0xc2500000-0xc2501fff 64bit]
[    1.054448] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    1.054457] pci 0000:01:00.0: PME# disabled
[    1.054506] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.054511] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.054517] pci 0000:00:1c.0:   bridge window [mem 0xc2500000-0xc25fffff]
[    1.054526] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.054644] pci 0000:02:00.0: reg 10: [mem 0xc1500000-0xc1500fff]
[    1.054757] pci 0000:02:00.0: supports D1 D2
[    1.054759] pci 0000:02:00.0: PME# supported from D1 D2 D3hot
[    1.054765] pci 0000:02:00.0: PME# disabled
[    1.054798] pci 0000:00:1c.2: PCI bridge to [bus 02-07]
[    1.054803] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    1.054809] pci 0000:00:1c.2:   bridge window [mem 0xc1500000-0xc24fffff]
[    1.054818] pci 0000:00:1c.2:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.055051] pci 0000:08:00.0: reg 10: [mem 0xc1400000-0xc143ffff 64bit]
[    1.055082] pci 0000:08:00.0: reg 18: [io  0x2000-0x207f]
[    1.055395] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.055410] pci 0000:08:00.0: PME# disabled
[    1.055516] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    1.055521] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    1.055526] pci 0000:00:1c.4:   bridge window [mem 0xc1400000-0xc14fffff]
[    1.055535] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.055560] pci_bus 0000:00: on NUMA node 0
[    1.055566] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.055845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.055949] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.056041] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    1.056275] \_SB_.PCI0:_OSC invalid UUID
[    1.056277] _OSC request data:1 19 1f 
[    1.063626] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.063782] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.063935] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    1.064086] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.064237] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.064390] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.064541] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.064692] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.064749] HEST: Table is not found!
[    1.064807] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.064815] vgaarb: loaded
[    1.064941] SCSI subsystem initialized
[    1.065033] libata version 3.00 loaded.
[    1.065077] usbcore: registered new interface driver usbfs
[    1.065088] usbcore: registered new interface driver hub
[    1.065110] usbcore: registered new device driver usb
[    1.065420] ACPI: WMI: Mapper loaded
[    1.065422] PCI: Using ACPI for IRQ routing
[    1.065424] PCI: pci_cache_line_size set to 64 bytes
[    1.065511] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    1.065514] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    1.065516] reserve RAM buffer: 00000000ace3f000 - 00000000afffffff 
[    1.065519] reserve RAM buffer: 00000000ad000000 - 00000000afffffff 
[    1.065590] NetLabel: Initializing
[    1.065592] NetLabel:  domain hash size = 128
[    1.065593] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.065603] NetLabel:  unlabeled traffic allowed by default
[    1.065638] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.065645] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.068658] Switching to clocksource tsc
[    1.077006] AppArmor: AppArmor Filesystem Enabled
[    1.077017] pnp: PnP ACPI init
[    1.077029] ACPI: bus type pnp registered
[    1.078350]   alloc irq_desc for 23 on node -1
[    1.078352]   alloc kstat_irqs on node -1
[    1.079433] pnp: PnP ACPI: found 13 devices
[    1.079435] ACPI: ACPI bus type pnp unregistered
[    1.079438] PnPBIOS: Disabled by ACPI PNP
[    1.079449] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.079451] system 00:05: [io  0x1000-0x100f] has been reserved
[    1.079453] system 00:05: [io  0x1010-0x1013] has been reserved
[    1.079456] system 00:05: [io  0xffff] has been reserved
[    1.079458] system 00:05: [io  0x0400-0x0453] has been reserved
[    1.079460] system 00:05: [io  0x0458-0x047f] has been reserved
[    1.079462] system 00:05: [io  0x0700-0x077f] has been reserved
[    1.079464] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.079469] system 00:07: [io  0x0454-0x0457] has been reserved
[    1.079475] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.079477] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.079479] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.079481] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.079484] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    1.079486] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.079488] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.079491] system 00:0b: [mem 0xff000000-0xffffffff] could not be reserved
[    1.079493] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.079495] system 00:0b: [mem 0xafa00000-0xafa00fff] has been reserved
[    1.079500] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
[    1.079502] system 00:0c: [mem 0x40000000-0x401fffff] could not be reserved
[    1.115070] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.115072] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.115079] pci 0000:00:1c.0:   bridge window [mem 0xc2500000-0xc25fffff]
[    1.115084] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.115093] pci 0000:00:1c.2: PCI bridge to [bus 02-07]
[    1.115097] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    1.115104] pci 0000:00:1c.2:   bridge window [mem 0xc1500000-0xc24fffff]
[    1.115110] pci 0000:00:1c.2:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.115119] pci 0000:00:1c.4: PCI bridge to [bus 08-08]
[    1.115122] pci 0000:00:1c.4:   bridge window [io  0x2000-0x2fff]
[    1.115129] pci 0000:00:1c.4:   bridge window [mem 0xc1400000-0xc14fffff]
[    1.115134] pci 0000:00:1c.4:   bridge window [mem pref disabled]
[    1.115154]   alloc irq_desc for 17 on node -1
[    1.115155]   alloc kstat_irqs on node -1
[    1.115160] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.115166] pci 0000:00:1c.0: setting latency timer to 64
[    1.115177]   alloc irq_desc for 18 on node -1
[    1.115179]   alloc kstat_irqs on node -1
[    1.115182] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.115187] pci 0000:00:1c.2: setting latency timer to 64
[    1.115199] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.115204] pci 0000:00:1c.4: setting latency timer to 64
[    1.115208] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.115210] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.115212] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.115214] pci_bus 0000:00: resource 7 [mem 0xafa00000-0xfeafffff]
[    1.115216] pci_bus 0000:01: resource 1 [mem 0xc2500000-0xc25fffff]
[    1.115218] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    1.115220] pci_bus 0000:02: resource 1 [mem 0xc1500000-0xc24fffff]
[    1.115222] pci_bus 0000:02: resource 2 [mem 0xc0400000-0xc13fffff 64bit pref]
[    1.115224] pci_bus 0000:08: resource 0 [io  0x2000-0x2fff]
[    1.115226] pci_bus 0000:08: resource 1 [mem 0xc1400000-0xc14fffff]
[    1.115253] NET: Registered protocol family 2
[    1.115297] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.115436] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.115675] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.115788] TCP: Hash tables configured (established 131072 bind 65536)
[    1.115790] TCP reno registered
[    1.115793] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.115798] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.115866] NET: Registered protocol family 1
[    1.115877] pci 0000:00:02.0: Boot video device
[    1.145567] PCI: CLS 64 bytes, default 64
[    1.145619] Simple Boot Flag at 0x44 set to 0x1
[    1.145850] cpufreq-nforce2: No nForce2 chipset.
[    1.145871] Scanning for low memory corruption every 60 seconds
[    1.145964] audit: initializing netlink socket (disabled)
[    1.145971] type=2000 audit(1309850172.956:1): initialized
[    1.154894] highmem bounce pool size: 64 pages
[    1.154898] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.156065] VFS: Disk quotas dquot_6.5.2
[    1.156115] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.156569] fuse init (API version 7.14)
[    1.156640] msgmni has been set to 1684
[    1.158766] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.158769] io scheduler noop registered
[    1.158771] io scheduler deadline registered
[    1.158781] io scheduler cfq registered (default)
[    1.158862] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.158920]   alloc irq_desc for 40 on node -1
[    1.158921]   alloc kstat_irqs on node -1
[    1.158934] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    1.159028] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.159084]   alloc irq_desc for 41 on node -1
[    1.159085]   alloc kstat_irqs on node -1
[    1.159094] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
[    1.159195] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.159250]   alloc irq_desc for 42 on node -1
[    1.159251]   alloc kstat_irqs on node -1
[    1.159261] pcieport 0000:00:1c.4: irq 42 for MSI/MSI-X
[    1.159357] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.159485] \_SB_.PCI0:_OSC invalid UUID
[    1.159486] _OSC request data:1 0 1f 
[    1.159609] \_SB_.PCI0:_OSC invalid UUID
[    1.159611] _OSC request data:1 0 1f 
[    1.159632] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.159703] intel_idle: MWAIT substates: 0x21120
[    1.159705] intel_idle: does not run on family 6 model 42
[    1.160776] ACPI: AC Adapter [AC] (on-line)
[    1.160836] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.161075] ACPI: Lid Switch [LID0]
[    1.161111] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.161115] ACPI: Power Button [PWRB]
[    1.161150] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.161153] ACPI: Power Button [PWRF]
[    1.161312] ACPI: Fan [FAN0] (on)
[    1.161752] ACPI: acpi_idle registered with cpuidle
[    1.162249] Monitor-Mwait will be used to enter C-1 state
[    1.162272] Monitor-Mwait will be used to enter C-2 state
[    1.168428] thermal LNXTHERM:01: registered as thermal_zone0
[    1.168435] ACPI: Thermal Zone [TZ00] (45 C)
[    1.168926] thermal LNXTHERM:02: registered as thermal_zone1
[    1.168932] ACPI: Thermal Zone [TZ01] (0 C)
[    1.168995] ERST: Table is not found!
[    1.169047] isapnp: Scanning for PnP cards...
[    1.169307] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.170957] brd: module loaded
[    1.171372] loop: module loaded
[    1.171733] Fixed MDIO Bus: probed
[    1.171760] PPP generic driver version 2.4.2
[    1.171789] tun: Universal TUN/TAP device driver, 1.6
[    1.171790] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.171845] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.171863]   alloc irq_desc for 16 on node -1
[    1.171865]   alloc kstat_irqs on node -1
[    1.171870] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.171882] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.171885] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.171914] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.171940] ehci_hcd 0000:00:1a.0: debug port 2
[    1.175818] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.175839] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc2609000
[    1.182561] ACPI: Battery Slot [BAT0] (battery present)
[    1.189448] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.189557] hub 1-0:1.0: USB hub found
[    1.189561] hub 1-0:1.0: 2 ports detected
[    1.189612]   alloc irq_desc for 20 on node -1
[    1.189613]   alloc kstat_irqs on node -1
[    1.189618] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.189629] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.189633] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.189660] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.189687] ehci_hcd 0000:00:1d.0: debug port 2
[    1.193583] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.193597] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xc2608000
[    1.212453] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.212534] hub 2-0:1.0: USB hub found
[    1.212537] hub 2-0:1.0: 2 ports detected
[    1.212583] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.212593] uhci_hcd: USB Universal Host Controller Interface driver
[    1.212669] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.214075] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.214900] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.214906] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.214910] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.214914] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.214917] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.214987] mice: PS/2 mouse device common for all mice
[    1.215110] rtc_cmos 00:06: RTC can wake from S4
[    1.215141] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.215181] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.215258] device-mapper: uevent: version 1.0.3
[    1.215348] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.215436] device-mapper: multipath: version 1.1.1 loaded
[    1.215439] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.215529] EISA: Probing bus 0 at eisa.0
[    1.215531] EISA: Cannot allocate resource for mainboard
[    1.215532] Cannot allocate resource for EISA slot 1
[    1.215534] Cannot allocate resource for EISA slot 2
[    1.215536] Cannot allocate resource for EISA slot 3
[    1.215537] Cannot allocate resource for EISA slot 4
[    1.215539] Cannot allocate resource for EISA slot 5
[    1.215540] Cannot allocate resource for EISA slot 6
[    1.215542] Cannot allocate resource for EISA slot 7
[    1.215543] Cannot allocate resource for EISA slot 8
[    1.215545] EISA: Detected 0 cards.
[    1.215741] cpuidle: using governor ladder
[    1.215860] cpuidle: using governor menu
[    1.216069] TCP cubic registered
[    1.216171] NET: Registered protocol family 10
[    1.216431] lo: Disabled Privacy Extensions
[    1.216589] NET: Registered protocol family 17
[    1.218086] Using IPI No-Shortcut mode
[    1.218145] PM: Resume from disk failed.
[    1.218153] registered taskstats version 1
[    1.218511]   Magic number: 3:839:267
[    1.218513] platform eisa.0: hash matches
[    1.218589] rtc_cmos 00:06: setting system clock to 2011-07-05 07:16:13 UTC (1309850173)
[    1.218593] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.218594] EDD information not available.
[    1.246830] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.504756] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.522426] isapnp: No Plug & Play device found
[    1.522509] Freeing unused kernel memory: 684k freed
[    1.522737] Write protecting the kernel text: 4932k
[    1.522793] Write protecting the kernel read-only data: 1976k
[    1.537402] udev[107]: starting version 163
[    1.575166] ahci 0000:00:1f.2: version 3.0
[    1.575188]   alloc irq_desc for 19 on node -1
[    1.575190]   alloc kstat_irqs on node -1
[    1.575199] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.575247]   alloc irq_desc for 43 on node -1
[    1.575250]   alloc kstat_irqs on node -1
[    1.575263] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.588440] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.588446] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.588453] ahci 0000:00:1f.2: setting latency timer to 64
[    1.603475] scsi0 : ahci
[    1.611563] scsi1 : ahci
[    1.613364] scsi2 : ahci
[    1.613460] scsi3 : ahci
[    1.613545] scsi4 : ahci
[    1.613633] scsi5 : ahci
[    1.613776] ata1: SATA max UDMA/133 abar m2048@0xc2607000 port 0xc2607100 irq 43
[    1.613779] ata2: DUMMY
[    1.613782] ata3: SATA max UDMA/133 abar m2048@0xc2607000 port 0xc2607200 irq 43
[    1.613784] ata4: DUMMY
[    1.613785] ata5: DUMMY
[    1.613786] ata6: DUMMY
[    1.640731] hub 1-1:1.0: USB hub found
[    1.640811] hub 1-1:1.0: 6 ports detected
[    1.751708] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.884154] hub 2-1:1.0: USB hub found
[    1.884330] hub 2-1:1.0: 6 ports detected
[    1.931424] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.932168] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.934822] ata3.00: ATAPI: hp       DVDRAM GU40N, QC04, max UDMA/100
[    1.937696] ata3.00: configured for UDMA/100
[    1.938397] ata1.00: ATA-8: WDC WD6400BPVT-60HXZT1, 01.01A01, max UDMA/133
[    1.938407] ata1.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.945697] ata1.00: configured for UDMA/133
[    1.959525] usb 1-1.1: new high speed USB device using ehci_hcd and address 3
[    1.959729] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400BPVT-6 01.0 PQ: 0 ANSI: 5
[    1.959874] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.959878] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.959881] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.959946] sd 0:0:0:0: [sda] Write Protect is off
[    1.959950] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.959973] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.960100]  sda:
[    1.961821] scsi 2:0:0:0: CD-ROM            hp       DVDRAM GU40N     QC04 PQ: 0 ANSI: 5
[    1.964219] sr0: scsi3-mmc drive: 62x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.964228] Uniform CD-ROM driver Revision: 3.20
[    1.964368] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.964429] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.996558]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.047401] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.123311] usb 1-1.4: new full speed USB device using ehci_hcd and address 4
[    2.299004] usb 2-1.6: new high speed USB device using ehci_hcd and address 3
[    2.832271] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   12.028288] udev[413]: starting version 163
[   12.054835] lp: driver loaded but no devices found
[   12.072176] Linux agpgart interface v0.103
[   12.110448] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[   12.111792] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   12.116717] Adding 12285948k swap on /dev/sda6.  Priority:-1 extents:1 across:12285948k 
[   12.200831] lis3lv02d: laptop model unknown, using default axes configuration
[   12.236610] type=1400 audit(1309864584.532:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=710 comm="apparmor_parser"
[   12.237377] type=1400 audit(1309864584.532:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=710 comm="apparmor_parser"
[   12.237783] type=1400 audit(1309864584.532:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=710 comm="apparmor_parser"
[   12.238540] lis3lv02d: unknown sensor type 0x33
[   12.238549] lis3lv02d: probe of HPQ0004:00 failed with error -22
[   12.238627] lis3lv02d driver loaded.
[   12.243091] [drm] Initialized drm 1.1.0 20060810
[   12.245183] Linux video capture interface: v2.00
[   12.251683] uvcvideo: Found UVC 1.00 device HP Truevision HD (10f1:1a2e)
[   12.259360] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[   12.266925] input: HP Truevision HD as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input4
[   12.267002] usbcore: registered new interface driver uvcvideo
[   12.267005] USB Video Class driver (v0.1.0)
[   12.285941] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.285951] i915 0000:00:02.0: setting latency timer to 64
[   12.308455] mtrr: type mismatch for b0000000,10000000 old: write-back new: write-combining
[   12.308459] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   12.308616]   alloc irq_desc for 44 on node -1
[   12.308619]   alloc kstat_irqs on node -1
[   12.308629] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   12.308639] [drm] set up 31M of stolen space
[   12.424510] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.440745] psmouse serio4: ID: 73 02 64
[   12.651258] input: HP WMI hotkeys as /devices/virtual/input/input5
[   12.713438] Skipping EDID probe due to cached edid
[   12.943074] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   13.019760] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/input/input6
[   13.159095] Console: switching to colour frame buffer device 170x48
[   13.162106] fb0: inteldrmfb frame buffer device
[   13.162107] drm: registered panic notifier
[   13.162111] Slow work thread pool: Starting up
[   13.162218] Slow work thread pool: Ready
[   13.166415] acpi device:35: registered as cooling_device5
[   13.167855] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   13.167911] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.167937] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.167980]   alloc irq_desc for 22 on node -1
[   13.167983]   alloc kstat_irqs on node -1
[   13.167992] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.168054]   alloc irq_desc for 45 on node -1
[   13.168057]   alloc kstat_irqs on node -1
[   13.168072] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   13.168115] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.186145] type=1400 audit(1309864585.484:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=952 comm="apparmor_parser"
[   13.186238] type=1400 audit(1309864585.484:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=953 comm="apparmor_parser"
[   13.187018] type=1400 audit(1309864585.484:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=953 comm="apparmor_parser"
[   13.187426] type=1400 audit(1309864585.484:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=953 comm="apparmor_parser"
[   13.187542] type=1400 audit(1309864585.484:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=956 comm="apparmor_parser"
[   13.188644] type=1400 audit(1309864585.484:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=956 comm="apparmor_parser"
[   13.188855] type=1400 audit(1309864585.484:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=954 comm="apparmor_parser"
[   13.208805] Skipping EDID probe due to cached edid
[   13.485905] Skipping EDID probe due to cached edid
[   13.517270] Skipping EDID probe due to cached edid
[   13.741951] input: HDA Intel PCH Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   13.742080] input: HDA Intel PCH HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.379183] Skipping EDID probe due to cached edid
[   14.411920] Skipping EDID probe due to cached edid
[   14.481465] Skipping EDID probe due to cached edid
[   14.513802] Skipping EDID probe due to cached edid
[   14.570824] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   15.661414] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   15.859118] ppdev: user-space parallel port driver
[   20.767342] HP WMI: Unknown key pressed - a
[   34.563382] Skipping EDID probe due to cached edid
[   34.596338] Skipping EDID probe due to cached edid
[   34.629947] Skipping EDID probe due to cached edid
[   34.662315] Skipping EDID probe due to cached edid
[   35.903659] ISO 9660 Extensions: Microsoft Joliet Level 3
[   35.970677] ISO 9660 Extensions: RRIP_1991A
[   39.945176] Skipping EDID probe due to cached edid
[   67.140673] psmouse.c: bad data from KBC - timeout
[   70.003238] psmouse.c: Mouse at isa0060/serio4/input0 lost synchronization, throwing 2 bytes away.
[   70.014555] psmouse.c: resync failed, issuing reconnect request
[   70.600136] psmouse serio4: ID: 73 02 64
[   90.728542] cfg80211: Calling CRDA to update world regulatory domain
[   90.875608] cfg80211: World regulatory domain updated:
[   90.875615]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   90.875623]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   90.875629]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   90.875635]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   90.875640]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   90.875645]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   90.918228] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   90.918232] iwlagn: Copyright(c) 2003-2010 Intel Corporation




carlos@carlos-HP:~$ dmesg | grep iwl
[   90.918228] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   90.918232] iwlagn: Copyright(c) 2003-2010 Intel Corporation
carlos@carlos-HP:~$ 


This is what came up, but there wireless is still not working.

---

### Post by chili555 on 2011-07-05
That's very weird! Let's also look at:```
lspci -nn | grep 0280
rfkill list all
dmesg | grep 01:00
```Thanks.

---

### Post by solrac418 on 2011-07-05
carlos@carlos-HP:~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Intel Corporation Device [8086:0886] (rev 67)
carlos@carlos-HP:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no 
carlos@carlos-HP:~$ dmesg | grep 01:00
[    1.054298] pci 0000:01:00.0: reg 10: [mem 0xc2500000-0xc2501fff 64bit]
[    1.054448] pci 0000:01:00.0: PME# supported from D0 D3hot D3cold
[    1.054457] pci 0000:01:00.0: PME# disabled
carlos@carlos-HP:~$ 


Still no wireless..


do you think the system needs an updated driver??... I read something online about linux-backports

Thanks,

---

### Post by chili555 on 2011-07-06
> Still no wireless..I'm sorry if I have not made my intentions clear. Most of the commands I asked you to run and post were not intended yet to get your wireless going. They were intended to gather information as to why the wireless isn't working as expected right from the start. Your wireless card is well known and well supported and the driver iwlagn generally performs quite well. Usually, either the wireless switch or, rarely, some electrical problem with the laptop stops the device and the driver from joining up and taking off.

Your device is claimed by the driver iwlagn:> Network controller [0280]: Intel Corporation Device [[COLOR="Red"]8086:0886[/COLOR]] (rev 67)> $ modinfo iwlagn 
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-5.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-3.ucode
srcversion:     786B9EF4588BA533C6D5E36
--- snip ---
alias:          pci:v0000[COLOR="Red"]8086[/COLOR]d0000[COLOR="Red"]0886[/COLOR]sv*sd00005025bc*sc*i*
---snip ---rfkill shows the wireless switch is not blocking the wireless. We loaded iwlagn manually and very little useful happened. dmesg has no complaints or problems to report.

Let's try a few things. First, we will cause iwlagn to load on boot. Please do:```
sudo su
echo iwlagn >> /etc/modules
exit
```Now reboot and check the computer's BIOS setup to be certain that wireless is activated. Next, start the computer and let's create a text document that we can examine for clues as to why the wireless won't start. Please do:```
dmesg > solrac.txt
ls /lib/firmware | grep iwl >> solrac.txt
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wlan >> solrac.txt
rfkill list all >> solrac.txt
zip solrac.zip solrac.txt
```You will find a zip file solrac.zip. Please attach it to your reply using the paperclip tool at the top of the reply box.> do you think the system needs an updated driver??Not yet. If iwlagn was not connecting or was unstable or wouldn't connect to WPA2, I'd suggest that. In your case, something else is keeping the driver from even starting.

---

### Post by solrac418 on 2011-07-06
Thank you for the clarification..  I went into the bios and didnt see anything out of the norm.

---

### Post by chili555 on 2011-07-06
You have this in dmesg:> MTRR allocation failed.  Graphics performance may suffer.You may want to Google it and ask on General Help. It probably doesn't affect wireless, but it's worth fixing. The same applies to this; there are *dozens* of instances in dmesg:> Skipping EDID probe due to cached edidIn your firmware file, you don't have all the files that I have. I am not sure that's the real issue, but let's try to fix it and see if the wireless improves. Please download this and transfer it on a USB key or similar to your desktop: [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz)

Right click the file and select Extract Here. In a terminal, do:```
cd Desktop/iwl
```Press Tab and the rest will fill in. Now do:```
sudo cp iwlwifi-6050-5.ucode /lib/firmware
sudo rmmod -f iwlagn
sudo modprobe iwlagn
dmesg | grep iwl
```We are trying to get the latest firmware file, x-5 to load. I am puzzled that there are no complaints in dmesg about firmware. There is also none of this from my machine:> dmesg | grep iwl
[   12.046310] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   12.046316] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   12.046390] iwl3945 0000:03:00.0: [COLOR="Red"]PCI INT A -> GSI 17 (level, low) -> IRQ 17[/COLOR]
[   12.046406] iwl3945 0000:03:00.0: setting latency timer to 64
[   12.102050] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.102055] iwl3945 0000:03:00.0: [COLOR="Red"]Detected Intel Wireless WiFi Link 3945ABG[/COLOR]
[   12.102211] iwl3945 0000:03:00.0: irq 46 for MSI/MSI-X
[   12.167682] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.788409] iwl3945 0000:03:00.0: [COLOR="Red"]loaded firmware version 15.32.2.9[/COLOR]
In other words, yours does not see a wireless device, grab an IRQ and load the firmware, but neither does it complain about missing or wrong firmware.

Any improvement?

---

### Post by solrac418 on 2011-07-06
> carlos@carlos-HP:~$ cd Desktop/iwlwifi-6050-ucode-41.28.5.1/
carlos@carlos-HP:~/Desktop/iwlwifi-6050-ucode-41.28.5.1$ sudo cp iwlwifi-6050-5.ucode /lib/firmware
[sudo] password for carlos: 
Sorry, try again.
[sudo] password for carlos: 
carlos@carlos-HP:~/Desktop/iwlwifi-6050-ucode-41.28.5.1$ sudo rmmod -f iwlagn
carlos@carlos-HP:~/Desktop/iwlwifi-6050-ucode-41.28.5.1$ sudo modprobe iwlagn
carlos@carlos-HP:~/Desktop/iwlwifi-6050-ucode-41.28.5.1$ dmesg | grep iwl
[   12.783866] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.783870] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[14673.187081] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[14673.187085] iwlagn: Copyright(c) 2003-2010 Intel Corporation
carlos@carlos-HP:~/Desktop/iwlwifi-6050-ucode-41.28.5.1$ 



Nothing has changed

---

### Post by chili555 on 2011-07-07
I am still quite troubled that your wireless card, the usually reliable Intel 6150 doesn't start. I have but a few 'grasping at straws' suggestions. Please look in the computer's BIOS. If you find a setting for plug and play operating system, whatever it's setting, reverse it. If you see a setting for Active State Power Management (ASPM), reverse it. In the settings for IRQs, make sure all are set to Auto Select. 

Are you able to try a live CD for Ubuntu 11.04 and get the device to work? Is it possible the device is electrically defective?

---

### Post by solrac418 on 2011-07-07
I'll check the bios settings when I get home, but I am dual-booting so when I log into windows 7 my connections work fine. I already ran a live cd with 11.4 on it and my connections worked fine on there as well. I just didnt want to use 11.04 yet, not sure if  I'm really a fan of Unity. I am aware that I have the option of running classic ubuntu/gnome on it. I figured I would give 10.10 a go on my system but its just been a headache... Before posting on here I tried using Keryx to update the system kernel and files, but I wasn't really sure what exactly I needed to install/update. I got it to the point where the drivers were loading but when I clicked on the network manager it said wirless disabled and just couldn't figure out how to enable. So wiped it out reinstalled 10.10 and decided to seek help on here.

---

### Post by chili555 on 2011-07-07
> a live cd with 11.4 on it and my connections worked fine on thereFrankly, I'd install 11.04 with a working wireless, select Classic Ubuntu and be happy. I've been using Unity for three months (I installed a beta of 11.04 before the final release) and I've gone from 'hate it' to 'don't mind it.' Unity and I have a long way to go before 'like' and then 'love,' if ever. Most of the reason I even use it is so I can tell posters where to find various system settings, etc., where to click and the ever-popular screenshots. Ditto Network Manager.

Nobody knows the troubles I've seen, as the man says.

---

### Post by solrac418 on 2011-07-08
Thank you for all of your help... I ended up installing 11.4  and everything is working under ubuntu classic.

---

