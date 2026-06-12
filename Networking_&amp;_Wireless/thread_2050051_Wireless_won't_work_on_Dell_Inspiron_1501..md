---
title: "Wireless won't work on Dell Inspiron 1501."
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by kbon on 2012-08-29
Hi, I am trying to configure this laptop for a friend using a lightweight distro, so it runs everything smoothly. Problem is, there;s no wireless Linux drivers for this pc, so I've beren trying to get a Windows wireless driver running using ndiswrapper. I've never done this before, so I'd appreciate some help with this if possible, or if there's an easier solution?

Edit: I need bed, so I'll respond in the morning.

---

### Post by kbon on 2012-08-30
Does anyone have any suggestions? :s

---

### Post by AndyOpie150 on 2012-08-30
I'm researching my own wireless woe's but have learned that more info is the best.
What is the output of: 
lsb_release -d
uname -mr
lspci
sudo lshw -C network
ifconfig
iwconfig
dmesg

---

### Post by kbon on 2012-08-30
Alright, here's the output of those commands:
```
wade@wade-Inspiron-1501:~$ lsb_release -d
Description:    Ubuntu 12.04 LTS
wade@wade-Inspiron-1501:~$ uname -mr
3.2.0-23-generic i686
wade@wade-Inspiron-1501:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
wade@wade-Inspiron-1501:~$ sudo lshw -C Network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:89:0e:aa
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1b:fc:d2:fe:13
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-23-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
wade@wade-Inspiron-1501:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:89:0e:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:117376 (117.3 KB)  TX bytes:117376 (117.3 KB)
wade@wade-Inspiron-1501:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

---------------

dmesg gave this huge output that filled up the entire terminal, so I couldn't get what was sent before:

[    0.028001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.028001] ..... (found apic 0 pin 0) ...
[    0.071613] ....... works.
[    0.071615] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 stepping 01
[    0.072003] Performance Events: AMD PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              48
[    0.072003] ... generic registers:      4
[    0.072003] ... value mask:             0000ffffffffffff
[    0.072003] ... max period:             00007fffffffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             000000000000000f
[    0.072003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.072003] CPU 1 irqstacks, hard=f44ca000 soft=f44cc000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.072003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.156153] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156139] System has AMD C1E enabled
[    0.156193] Brought up 2 CPUs
[    0.156197] Total of 2 processors activated (6783.43 BogoMIPS).
[    0.156189] Switch to broadcast mode on CPU1
[    0.156723] Switch to broadcast mode on CPU0
[    0.156723] devtmpfs: initialized
[    0.156723] EVM: security.selinux
[    0.156723] EVM: security.SMACK64
[    0.156723] EVM: security.capability
[    0.156723] PM: Registering ACPI NVS region at 77e80000 (524288 bytes)
[    0.157601] print_constraints: dummy: 
[    0.157641] RTC time: 13:56:21, date: 08/30/12
[    0.157701] NET: Registered protocol family 16
[    0.157762] Trying to unpack rootfs image as initramfs...
[    0.157924] EISA bus registered
[    0.157932] node 0 link 0: io port [1000, fffff]
[    0.157936] TOM: 0000000080000000 aka 2048M
[    0.157941] node 0 link 0: mmio [d0000000, dfffffff]
[    0.157945] node 0 link 0: mmio [c8000000, cfffffff]
[    0.157949] node 0 link 0: mmio [a0000, bffff]
[    0.157953] node 0 link 0: mmio [f0000000, ffffffff]
[    0.157957] node 0 link 0: mmio [e0000000, efffffff]
[    0.157960] node 0 link 0: mmio [80000000, c7ffffff]
[    0.157964] bus: [00, ff] on node 0 link 0
[    0.157969] bus: 00 index 0 [io  0x0000-0xffff]
[    0.157972] bus: 00 index 1 [mem 0x80000000-0xefffffff]
[    0.157975] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.157978] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.158020] ACPI: bus type pci registered
[    0.158107] PCI: MMCONFIG for domain 0000 [bus 00-09] at [mem 0xe0000000-0xe09fffff] (base 0xe0000000)
[    0.158112] PCI: MMCONFIG at [mem 0xe0000000-0xe09fffff] reserved in E820
[    0.158115] PCI: Using MMCONFIG for extended config space
[    0.158118] PCI: Using configuration type 1 for base access
[    0.158128] dmi type 0xB1 record - unknown flag
[    0.172192] bio: create slab <bio-0> at 0
[    0.172245] ACPI: Added _OSI(Module Device)
[    0.172249] ACPI: Added _OSI(Processor Device)
[    0.172252] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172255] ACPI: Added _OSI(Processor Aggregator Device)
[    0.173480] ACPI: EC: Look up EC in DSDT
[    0.173480] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.180093] ACPI: Interpreter enabled
[    0.180101] ACPI: (supports S0 S3 S4 S5)
[    0.180125] ACPI: Using IOAPIC for interrupt routing
[    0.210505] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.216305] ACPI: EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[    0.216486] ACPI: No dock devices found.
[    0.216490] HEST: Table not found.
[    0.216495] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.217288] ACPI Error: Needed type [Reference], found [Device] f441ff90 (20110623/exresop-104)
[    0.217297] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20110623/dswexec-460)
[    0.217305] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4428db0), AE_AML_OPERAND_TYPE (20110623/psparse-536)
[    0.217320] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d1fff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000d2000-0x000d3fff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d5fff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000d6000-0x000d7fff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000d9fff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000da000-0x000dbfff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000ddfff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e1fff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x000e2000-0x000e3fff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xffffffff] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.217320] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.217320] pci 0000:00:00.0: [1002:5950] type 0 class 0x000600
[    0.217320] pci 0000:00:01.0: [1002:5a3f] type 1 class 0x000604
[    0.217320] pci 0000:00:05.0: [1002:5a37] type 1 class 0x000604
[    0.217320] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.217320] pci 0000:00:05.0: PME# disabled
[    0.217320] pci 0000:00:06.0: [1002:5a38] type 1 class 0x000604
[    0.217320] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.217320] pci 0000:00:06.0: PME# disabled
[    0.217320] pci 0000:00:12.0: [1002:4380] type 0 class 0x000101
[    0.217320] pci 0000:00:12.0: reg 10: [io  0x8438-0x843f]
[    0.217320] pci 0000:00:12.0: reg 14: [io  0x8454-0x8457]
[    0.217320] pci 0000:00:12.0: reg 18: [io  0x8430-0x8437]
[    0.217320] pci 0000:00:12.0: reg 1c: [io  0x8450-0x8453]
[    0.217320] pci 0000:00:12.0: reg 20: [io  0x8400-0x840f]
[    0.217320] pci 0000:00:12.0: reg 24: [mem 0xc0004000-0xc00043ff]
[    0.217332] pci 0000:00:12.0: set SATA to AHCI mode
[    0.217381] pci 0000:00:13.0: [1002:4387] type 0 class 0x000c03
[    0.217399] pci 0000:00:13.0: reg 10: [mem 0xc0005000-0xc0005fff]
[    0.217485] pci 0000:00:13.1: [1002:4388] type 0 class 0x000c03
[    0.217503] pci 0000:00:13.1: reg 10: [mem 0xc0006000-0xc0006fff]
[    0.217589] pci 0000:00:13.2: [1002:4389] type 0 class 0x000c03
[    0.217608] pci 0000:00:13.2: reg 10: [mem 0xc0007000-0xc0007fff]
[    0.217695] pci 0000:00:13.3: [1002:438a] type 0 class 0x000c03
[    0.217713] pci 0000:00:13.3: reg 10: [mem 0xc0008000-0xc0008fff]
[    0.217799] pci 0000:00:13.4: [1002:438b] type 0 class 0x000c03
[    0.217817] pci 0000:00:13.4: reg 10: [mem 0xc0009000-0xc0009fff]
[    0.217910] pci 0000:00:13.5: [1002:4386] type 0 class 0x000c03
[    0.217936] pci 0000:00:13.5: reg 10: [mem 0xc0004400-0xc00044ff]
[    0.218044] pci 0000:00:13.5: supports D1 D2
[    0.218047] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.218053] pci 0000:00:13.5: PME# disabled
[    0.218082] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.218112] pci 0000:00:14.0: reg 10: [io  0x8410-0x841f]
[    0.218224] pci 0000:00:14.1: [1002:438c] type 0 class 0x000101
[    0.218242] pci 0000:00:14.1: reg 10: [io  0x01f0-0x01f7]
[    0.218255] pci 0000:00:14.1: reg 14: [io  0x03f4-0x03f7]
[    0.218269] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.218282] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.218295] pci 0000:00:14.1: reg 20: [io  0x8420-0x842f]
[    0.218351] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.218381] pci 0000:00:14.2: reg 10: [mem 0xc0000000-0xc0003fff 64bit]
[    0.218468] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.218474] pci 0000:00:14.2: PME# disabled
[    0.218493] pci 0000:00:14.3: [1002:438d] type 0 class 0x000601
[    0.218590] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.218653] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.218681] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.218704] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.218727] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.218763] PCI: peer root bus 00 res updated from pci conf
[    0.218794] pci 0000:01:05.0: [1002:5975] type 0 class 0x000300
[    0.218805] pci 0000:01:05.0: reg 10: [mem 0xc8000000-0xcfffffff pref]
[    0.218812] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.218819] pci 0000:01:05.0: reg 18: [mem 0xc0100000-0xc010ffff]
[    0.218836] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.218850] pci 0000:01:05.0: supports D1 D2
[    0.218870] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.218875] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.218879] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.218885] pci 0000:00:01.0:   bridge window [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.218915] pci 0000:00:05.0: PCI bridge to [bus 02-04]
[    0.218969] pci 0000:05:00.0: [14e4:4311] type 0 class 0x000280
[    0.218988] pci 0000:05:00.0: reg 10: [mem 0xc0200000-0xc0203fff]
[    0.219106] pci 0000:05:00.0: supports D1 D2
[    0.219128] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.219140] pci 0000:00:06.0: PCI bridge to [bus 05-07]
[    0.219147] pci 0000:00:06.0:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.219181] pci 0000:08:00.0: [14e4:170c] type 0 class 0x000200
[    0.219209] pci 0000:08:00.0: reg 10: [mem 0xc0300000-0xc0301fff]
[    0.219330] pci 0000:08:00.0: supports D1 D2
[    0.219333] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.219339] pci 0000:08:00.0: PME# disabled
[    0.219366] pci 0000:08:01.0: [1180:0822] type 0 class 0x000805
[    0.219394] pci 0000:08:01.0: reg 10: [mem 0xc0302000-0xc03020ff]
[    0.219514] pci 0000:08:01.0: supports D1 D2
[    0.219517] pci 0000:08:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.219524] pci 0000:08:01.0: PME# disabled
[    0.219550] pci 0000:08:01.1: [1180:0843] type 0 class 0x000880
[    0.219579] pci 0000:08:01.1: reg 10: [mem 0xc0302400-0xc03024ff]
[    0.219697] pci 0000:08:01.1: supports D1 D2
[    0.219700] pci 0000:08:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.219707] pci 0000:08:01.1: PME# disabled
[    0.219785] pci 0000:00:14.4: PCI bridge to [bus 08-0a] (subtractive decode)
[    0.219797] pci 0000:00:14.4:   bridge window [mem 0xc0300000-0xc03fffff]
[    0.219804] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.219808] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xefffffff] (subtractive decode)
[    0.219813] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.219817] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.219834] pci_bus 0000:00: on NUMA node 0
[    0.219839] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.219946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.220001] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.220115] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.220161] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.220258] ACPI Error: Needed type [Reference], found [Device] f441ff90 (20110623/exresop-104)
[    0.220265] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20110623/dswexec-460)
[    0.220272] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4428db0), AE_AML_OPERAND_TYPE (20110623/psparse-536)
[    0.220287]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.220331] ACPI Error: Needed type [Reference], found [Device] f441ff90 (20110623/exresop-104)
[    0.220338] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20110623/dswexec-460)
[    0.220345] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f4428db0), AE_AML_OPERAND_TYPE (20110623/psparse-536)
[    0.220359]  pci0000:00: ACPI _OSC request failed (AE_AML_OPERAND_TYPE), returned control mask: 0x1d
[    0.220362] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.225710] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.225768] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.225826] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.225881] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.225938] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.225994] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.226050] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.226105] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.226162] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.226342] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.226349] vgaarb: loaded
[    0.226351] vgaarb: bridge control possible 0000:01:05.0
[    0.226553] i2c-core: driver [aat2870] using legacy suspend method
[    0.226556] i2c-core: driver [aat2870] using legacy resume method
[    0.226682] SCSI subsystem initialized
[    0.228014] libata version 3.00 loaded.
[    0.228014] usbcore: registered new interface driver usbfs
[    0.228014] usbcore: registered new interface driver hub
[    0.228014] usbcore: registered new device driver usb
[    0.228014] PCI: Using ACPI for IRQ routing
[    0.228014] PCI: pci_cache_line_size set to 64 bytes
[    0.228014] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.228014] reserve RAM buffer: 0000000077e70000 - 0000000077ffffff 
[    0.228014] NetLabel: Initializing
[    0.228014] NetLabel:  domain hash size = 128
[    0.228014] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.228014] NetLabel:  unlabeled traffic allowed by default
[    0.238824] AppArmor: AppArmor Filesystem Enabled
[    0.238869] pnp: PnP ACPI init
[    0.238896] ACPI: bus type pnp registered
[    0.239661] pnp 00:00: [bus 00-ff]
[    0.239665] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.239669] pnp 00:00: [mem 0x000c0000-0x000c1fff window]
[    0.239673] pnp 00:00: [mem 0x000c2000-0x000c3fff window]
[    0.239676] pnp 00:00: [mem 0x000c4000-0x000c5fff window]
[    0.239680] pnp 00:00: [mem 0x000c6000-0x000c7fff window]
[    0.239684] pnp 00:00: [mem 0x000c8000-0x000c9fff window]
[    0.239687] pnp 00:00: [mem 0x000ca000-0x000cbfff window]
[    0.239691] pnp 00:00: [mem 0x000cc000-0x000cdfff window]
[    0.239694] pnp 00:00: [mem 0x000ce000-0x000cffff window]
[    0.239698] pnp 00:00: [mem 0x000d0000-0x000d1fff window]
[    0.239701] pnp 00:00: [mem 0x000d2000-0x000d3fff window]
[    0.239705] pnp 00:00: [mem 0x000d4000-0x000d5fff window]
[    0.239709] pnp 00:00: [mem 0x000d6000-0x000d7fff window]
[    0.239712] pnp 00:00: [mem 0x000d8000-0x000d9fff window]
[    0.239716] pnp 00:00: [mem 0x000da000-0x000dbfff window]
[    0.239719] pnp 00:00: [mem 0x000dc000-0x000ddfff window]
[    0.239723] pnp 00:00: [mem 0x000de000-0x000dffff window]
[    0.239726] pnp 00:00: [mem 0x000e0000-0x000e1fff window]
[    0.239730] pnp 00:00: [mem 0x000e2000-0x000e3fff window]
[    0.239734] pnp 00:00: [mem 0x000e4000-0x000e5fff window]
[    0.239737] pnp 00:00: [mem 0x000e6000-0x000e7fff window]
[    0.239741] pnp 00:00: [mem 0x000e8000-0x000e9fff window]
[    0.239748] pnp 00:00: [mem 0x000ea000-0x000ebfff window]
[    0.239752] pnp 00:00: [mem 0x000ec000-0x000edfff window]
[    0.239755] pnp 00:00: [mem 0x000ee000-0x000effff window]
[    0.239759] pnp 00:00: [mem 0x80000000-0xffffffff window]
[    0.239763] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.239766] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.239769] pnp 00:00: [io  0x0d00-0xffff window]
[    0.239852] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.239913] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.239917] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.239920] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.240001] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.240031] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.240036] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.240041] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.240476] pnp 00:02: [io  0x0000-0x001f]
[    0.240479] pnp 00:02: [io  0x0080-0x008f]
[    0.240482] pnp 00:02: [io  0x00c0-0x00df]
[    0.240486] pnp 00:02: [dma 4]
[    0.240532] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.240544] pnp 00:03: [io  0x00f0-0x00fe]
[    0.240559] pnp 00:03: [irq 13]
[    0.240602] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.240615] pnp 00:04: [io  0x0070-0x0071]
[    0.240623] pnp 00:04: [irq 8]
[    0.240670] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.240681] pnp 00:05: [io  0x0061]
[    0.240725] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.240739] pnp 00:06: [io  0x0060]
[    0.240742] pnp 00:06: [io  0x0064]
[    0.240748] pnp 00:06: [irq 1]
[    0.240793] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.240807] pnp 00:07: [irq 12]
[    0.240860] pnp 00:07: Plug and Play ACPI device, IDs SYN1015 SYN0100 SYN0002 PNP0f13 (active)
[    0.240881] pnp 00:08: [io  0x0022-0x0023]
[    0.240884] pnp 00:08: [io  0x002e-0x002f]
[    0.240887] pnp 00:08: [io  0x0072-0x0073]
[    0.240890] pnp 00:08: [io  0x0068-0x006f]
[    0.240893] pnp 00:08: [io  0x1080]
[    0.240896] pnp 00:08: [io  0x00b0-0x00b1]
[    0.240899] pnp 00:08: [io  0x0092]
[    0.240902] pnp 00:08: [io  0x0220-0x022f]
[    0.240905] pnp 00:08: [io  0x040b]
[    0.240907] pnp 00:08: [io  0x04d0-0x04d1]
[    0.240910] pnp 00:08: [io  0x04d6]
[    0.240913] pnp 00:08: [io  0x0530-0x0537]
[    0.240916] pnp 00:08: [io  0x0c00-0x0c01]
[    0.240919] pnp 00:08: [io  0x0c14]
[    0.240922] pnp 00:08: [io  0x0c50-0x0c52]
[    0.240925] pnp 00:08: [io  0x0c6c]
[    0.240928] pnp 00:08: [io  0x0c6f]
[    0.240931] pnp 00:08: [io  0x0cd0-0x0cd3]
[    0.240934] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.240937] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.240940] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.240943] pnp 00:08: [io  0x8000-0x805f]
[    0.240947] pnp 00:08: [io  0x8100-0x81ff window]
[    0.240950] pnp 00:08: [io  0x8200-0x82ff window]
[    0.240953] pnp 00:08: [io  0x0f40-0x0f47]
[    0.240956] pnp 00:08: [io  0x087f]
[    0.241056] system 00:08: [io  0x1080] has been reserved
[    0.241061] system 00:08: [io  0x0220-0x022f] has been reserved
[    0.241064] system 00:08: [io  0x040b] has been reserved
[    0.241068] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.241072] system 00:08: [io  0x04d6] has been reserved
[    0.241076] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.241080] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.241084] system 00:08: [io  0x0c14] has been reserved
[    0.241088] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.241092] system 00:08: [io  0x0c6c] has been reserved
[    0.241095] system 00:08: [io  0x0c6f] has been reserved
[    0.241099] system 00:08: [io  0x0cd0-0x0cd3] has been reserved
[    0.241104] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.241108] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.241112] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.241116] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.241120] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.241125] system 00:08: [io  0x8200-0x82ff window] has been reserved
[    0.241129] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.241133] system 00:08: [io  0x087f] has been reserved
[    0.241138] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.241216] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.241220] pnp 00:09: [mem 0xfff00000-0xffffffff]
[    0.241223] pnp 00:09: [mem 0xc0004800-0xc0004bff]
[    0.241227] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.241230] pnp 00:09: [mem 0x00000000-0x00000fff]
[    0.241258] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.241322] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.241326] system 00:09: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.241331] system 00:09: [mem 0xc0004800-0xc0004bff] has been reserved
[    0.241335] system 00:09: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.241340] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.260078] pnp: PnP ACPI: found 10 devices
[    0.260081] ACPI: ACPI bus type pnp unregistered
[    0.260086] PnPBIOS: Disabled by ACPI PNP
[    0.295341] Switching to clocksource acpi_pm
[    0.296018] PCI: max bus depth: 1 pci_try_num: 2
[    0.296018] pci 0000:00:06.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.296018] pci 0000:00:06.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.296018] pci 0000:00:05.0: BAR 14: assigned [mem 0x80200000-0x803fffff]
[    0.296018] pci 0000:00:05.0: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.296018] pci 0000:00:05.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.296018] pci 0000:01:05.0: BAR 6: assigned [mem 0xc0120000-0xc013ffff pref]
[    0.296018] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.296018] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.296018] pci 0000:00:01.0:   bridge window [mem 0xc0100000-0xc01fffff]
[    0.296018] pci 0000:00:01.0:   bridge window [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.296018] pci 0000:00:05.0: PCI bridge to [bus 02-04]
[    0.296018] pci 0000:00:05.0:   bridge window [io  0x3000-0x3fff]
[    0.296018] pci 0000:00:05.0:   bridge window [mem 0x80200000-0x803fffff]
[    0.296018] pci 0000:00:05.0:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.296018] pci 0000:00:06.0: PCI bridge to [bus 05-07]
[    0.296018] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.296018] pci 0000:00:06.0:   bridge window [mem 0xc0200000-0xc02fffff]
[    0.296018] pci 0000:00:06.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.296018] pci 0000:00:14.4: PCI bridge to [bus 08-0a]
[    0.296018] pci 0000:00:14.4:   bridge window [mem 0xc0300000-0xc03fffff]
[    0.296018] pci 0000:00:05.0: enabling device (0000 -> 0003)
[    0.296018] pci 0000:00:05.0: setting latency timer to 64
[    0.296018] pci 0000:00:06.0: setting latency timer to 64
[    0.296018] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.296018] pci_bus 0000:00: resource 5 [mem 0x80000000-0xefffffff]
[    0.296018] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.296018] pci_bus 0000:00: resource 7 [mem 0xf0000000-0xffffffff]
[    0.296018] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.296018] pci_bus 0000:01: resource 1 [mem 0xc0100000-0xc01fffff]
[    0.296018] pci_bus 0000:01: resource 2 [mem 0xc8000000-0xcfffffff 64bit pref]
[    0.296018] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.296018] pci_bus 0000:02: resource 1 [mem 0x80200000-0x803fffff]
[    0.296018] pci_bus 0000:02: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.296018] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.296018] pci_bus 0000:05: resource 1 [mem 0xc0200000-0xc02fffff]
[    0.296018] pci_bus 0000:05: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.296018] pci_bus 0000:08: resource 1 [mem 0xc0300000-0xc03fffff]
[    0.296018] pci_bus 0000:08: resource 4 [io  0x0000-0xffff]
[    0.296018] pci_bus 0000:08: resource 5 [mem 0x80000000-0xefffffff]
[    0.296018] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.296018] pci_bus 0000:08: resource 7 [mem 0xf0000000-0xffffffff]
[    0.296018] NET: Registered protocol family 2
[    0.296018] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.296848] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.297576] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.297929] TCP: Hash tables configured (established 131072 bind 65536)
[    0.297934] TCP reno registered
[    0.297939] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.297955] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.298078] NET: Registered protocol family 1
[    0.298094] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.298102] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.298138] pci 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.298174] pci 0000:00:13.0: PCI INT A disabled
[    0.298189] pci 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.298209] pci 0000:00:13.1: PCI INT B disabled
[    0.298223] pci 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.298240] pci 0000:00:13.2: PCI INT C disabled
[    0.298251] pci 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.298267] pci 0000:00:13.3: PCI INT B disabled
[    0.298278] pci 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.298296] pci 0000:00:13.4: PCI INT C disabled
[    0.298312] pci 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.298331] pci 0000:00:13.5: PCI INT D disabled
[    0.298362] pci 0000:01:05.0: Boot video device
[    0.298379] PCI: CLS 32 bytes, default 64
[    0.299360] audit: initializing netlink socket (disabled)
[    0.299360] type=2000 audit(1346334980.296:1): initialized
[    0.335791] highmem bounce pool size: 64 pages
[    0.335801] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.352084] VFS: Disk quotas dquot_6.5.2
[    0.352187] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.353022] fuse init (API version 7.17)
[    0.353158] msgmni has been set to 1681
[    0.353651] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.353692] io scheduler noop registered
[    0.353695] io scheduler deadline registered
[    0.353710] io scheduler cfq registered (default)
[    0.353995] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.354036] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.354657] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.355563] ACPI: AC Adapter [ACAD] (on-line)
[    0.355653] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.355661] ACPI: Power Button [PWRB]
[    0.355729] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.355735] ACPI: Sleep Button [SLPB]
[    0.355799] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.356450] ACPI: Lid Switch [LID]
[    0.356523] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.356528] ACPI: Power Button [PWRF]
[    0.356831] ACPI: processor limited to max C-state 1
[    0.360965] thermal LNXTHERM:00: registered as thermal_zone0
[    0.360969] ACPI: Thermal Zone [THRM] (62 C)
[    0.361002] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.361016] ACPI: Battery Slot [BAT1] (battery present)
[    0.361048] ERST: Table is not found!
[    0.361050] GHES: HEST is not enabled!
[    0.361228] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.361686] isapnp: Scanning for PnP cards...
[    0.608442] Freeing initrd memory: 13780k freed
[    0.716258] isapnp: No Plug & Play device found
[    0.748222] ACPI: Battery Slot [BAT1] (battery present)
[    0.776535] Linux agpgart interface v0.103
[    0.779514] brd: module loaded
[    0.780953] loop: module loaded
[    0.781144] ahci 0000:00:12.0: version 3.0
[    0.781176] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.781215] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    0.781336] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.781341] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.782628] scsi0 : ahci
[    0.782835] scsi1 : ahci
[    0.782996] scsi2 : ahci
[    0.783163] scsi3 : ahci
[    0.783349] ata1: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004100 irq 22
[    0.783355] ata2: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004180 irq 22
[    0.783360] ata3: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004200 irq 22
[    0.783365] ata4: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004280 irq 22
[    0.783603] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.783653] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.784284] Fixed MDIO Bus: probed
[    0.784325] tun: Universal TUN/TAP device driver, 1.6
[    0.784327] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.784447] PPP generic driver version 2.4.2
[    0.784641] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.784667] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.784694] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.784766] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.784801] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.784820] ehci_hcd 0000:00:13.5: debug port 1
[    0.784855] ehci_hcd 0000:00:13.5: irq 19, io mem 0xc0004400
[    0.796052] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.796313] hub 1-0:1.0: USB hub found
[    0.796320] hub 1-0:1.0: 10 ports detected
[    0.796463] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.796484] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.796504] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.796590] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.796626] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0005000
[    0.852280] hub 2-0:1.0: USB hub found
[    0.852290] hub 2-0:1.0: 2 ports detected
[    0.852380] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.852399] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.852496] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.852532] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000
[    0.908264] hub 3-0:1.0: USB hub found
[    0.908272] hub 3-0:1.0: 2 ports detected
[    0.908362] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.908379] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.908462] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.908495] ohci_hcd 0000:00:13.2: irq 18, io mem 0xc0007000
[    0.964269] hub 4-0:1.0: USB hub found
[    0.964277] hub 4-0:1.0: 2 ports detected
[    0.964371] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.964387] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.964467] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.964487] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0008000
[    1.020277] hub 5-0:1.0: USB hub found
[    1.020285] hub 5-0:1.0: 2 ports detected
[    1.020384] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.020401] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    1.020484] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    1.020506] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0009000
[    1.076281] hub 6-0:1.0: USB hub found
[    1.076290] hub 6-0:1.0: 2 ports detected
[    1.076394] uhci_hcd: USB Universal Host Controller Interface driver
[    1.076511] usbcore: registered new interface driver libusual
[    1.076576] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.079963] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.079974] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.080243] mousedev: PS/2 mouse device common for all mice
[    1.080650] rtc_cmos 00:04: RTC can wake from S4
[    1.080823] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.080855] rtc0: alarms up to one month, 114 bytes nvram
[    1.080971] device-mapper: uevent: version 1.0.3
[    1.081108] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.081166] EISA: Probing bus 0 at eisa.0
[    1.081169] EISA: Cannot allocate resource for mainboard
[    1.081173] Cannot allocate resource for EISA slot 1
[    1.081176] Cannot allocate resource for EISA slot 2
[    1.081179] Cannot allocate resource for EISA slot 3
[    1.081182] Cannot allocate resource for EISA slot 4
[    1.081185] Cannot allocate resource for EISA slot 5
[    1.081188] Cannot allocate resource for EISA slot 6
[    1.081191] Cannot allocate resource for EISA slot 7
[    1.081194] Cannot allocate resource for EISA slot 8
[    1.081197] EISA: Detected 0 cards.
[    1.081212] cpufreq-nforce2: No nForce2 chipset.
[    1.081216] cpuidle: using governor ladder
[    1.081219] cpuidle: using governor menu
[    1.081221] EFI Variables Facility v0.08 2004-May-17
[    1.081554] TCP cubic registered
[    1.081738] NET: Registered protocol family 10
[    1.082509] NET: Registered protocol family 17
[    1.082535] Registering the dns_resolver key type
[    1.082580] Using IPI No-Shortcut mode
[    1.082805] PM: Hibernation image not present or could not be loaded.
[    1.082821] registered taskstats version 1
[    1.100100] ata3: SATA link down (SStatus 0 SControl 300)
[    1.100157] ata4: SATA link down (SStatus 0 SControl 300)
[    1.100226] ata2: SATA link down (SStatus 0 SControl 300)
[    1.100325]   Magic number: 8:536:939
[    1.100462] rtc_cmos 00:04: setting system clock to 2012-08-30 13:56:22 UTC (1346334982)
[    1.100473] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 (2 cpu cores) (version 2.20.00)
[    1.100526] powernow-k8: fid 0x9 (1700 MHz), vid 0x13
[    1.100529] powernow-k8: fid 0x8 (1600 MHz), vid 0x14
[    1.100532] powernow-k8: fid 0x0 (800 MHz), vid 0x1a
[    1.100644] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.100647] EDD information not available.
[    1.112090] usb 1-7: new high-speed USB device number 2 using ehci_hcd
[    1.112303] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.247752] Initializing USB Mass Storage driver...
[    1.247979] scsi4 : usb-storage 1-7:1.0
[    1.248128] usbcore: registered new interface driver usb-storage
[    1.248131] USB Mass Storage support registered.
[    1.272055] ata1: softreset failed (device not ready)
[    1.272060] ata1: applying PMP SRST workaround and retrying
[    1.444061] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.445172] ata1.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC7KP, max UDMA/100
[    1.445178] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.445184] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.446449] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.446453] ata1.00: configured for UDMA/100
[    1.446692] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    1.446900] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.446953] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.446968] sd 0:0:0:0: [sda] Write Protect is off
[    1.446972] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.447001] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.499658]  sda: sda1 sda2 < sda5 >
[    1.500393] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.500418] Freeing unused kernel memory: 712k freed
[    1.500997] Write protecting the kernel text: 5628k
[    1.501057] Write protecting the kernel read-only data: 2324k
[    1.531387] udevd[99]: starting version 175
[    1.648638] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.648654] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[    1.668111] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.668127] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.668136] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.668145] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.686296] scsi5 : pata_atiixp
[    1.686516] scsi6 : pata_atiixp
[    1.687154] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    1.687158] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    1.689943] sdhci: Secure Digital Host Controller Interface driver
[    1.689948] sdhci: Copyright(c) Pierre Ossman
[    1.698135] sdhci-pci 0000:08:01.0: SDHCI controller found [1180:0822] (rev 19)
[    1.698174] sdhci-pci 0000:08:01.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.699214] sdhci-pci 0000:08:01.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.699664] mmc0: no vmmc regulator found
[    1.700731] Registered led device: mmc0::
[    1.702806] mmc0: SDHCI controller on PCI [0000:08:01.0] using DMA
[    1.702826] sdhci-pci 0000:08:01.1: SDHCI controller found [1180:0843] (rev 1)
[    1.702846] sdhci-pci 0000:08:01.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.702884] sdhci-pci 0000:08:01.1: setting latency timer to 64
[    1.702899] mmc1: no vmmc regulator found
[    1.702936] Registered led device: mmc1::
[    1.705757] mmc1: SDHCI controller on PCI [0000:08:01.1] using DMA
[    1.732224] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[    1.788823] mmc0: new SD card at address 8e24
[    1.793065] b44 0000:08:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.812138] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.812150] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.812160] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.852166] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[    1.852198] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.855597] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.864581] ata5.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D200, max UDMA/33
[    1.873172] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1c:23:89:0e:aa
[    1.896523] ata5.00: configured for UDMA/33
[    1.901189] scsi 5:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D200 PQ: 0 ANSI: 5
[    1.908608] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.908613] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.908836] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.909036] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    2.248887] scsi 4:0:0:0: Direct-Access     General  USB Flash Disk   1.0  PQ: 0 ANSI: 2
[    2.249997] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.250484] sd 4:0:0:0: [sdb] 15656960 512-byte logical blocks: (8.01 GB/7.46 GiB)
[    2.251229] sd 4:0:0:0: [sdb] Write Protect is off
[    2.251233] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    2.251976] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.251979] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.255234] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.255238] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.256172]  sdb: sdb1
[    2.258732] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.258736] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.258740] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   12.387619] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.068308] udevd[326]: starting version 175
[   13.136603] lp: driver loaded but no devices found
[   13.149203] Adding 1963004k swap on /dev/sda5.  Priority:-1 extents:1 across:1963004k 
[   13.233263] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   13.252272] acpi device:1d: registered as cooling_device2
[   13.252415] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input5
[   13.253200] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.342103] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.505436] wmi: Mapper loaded
[   13.524675] cfg80211: Calling CRDA to update world regulatory domain
[   13.573405] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   13.576462] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.604583] [drm] Initialized drm 1.1.0 20060810
[   13.640849] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.640856] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640860] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.640865] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640868] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.640872] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640876] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.640880] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640883] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.640887] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640890] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.640894] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640898] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.640902] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640905] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.640909] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640913] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.640917] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640920] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.640924] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640927] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.640932] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   13.640935] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.640939] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   13.640943] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.640947] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   13.640950] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   13.640954] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   13.672163] Bluetooth: Core ver 2.16
[   13.674221] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.674656] NET: Registered protocol family 31
[   13.674662] Bluetooth: HCI device and connection manager initialized
[   13.674668] Bluetooth: HCI socket layer initialized
[   13.674671] Bluetooth: L2CAP socket layer initialized
[   13.674687] Bluetooth: SCO socket layer initialized
[   13.681718] Registered led device: b43-phy0::tx
[   13.681752] Registered led device: b43-phy0::rx
[   13.681787] Registered led device: b43-phy0::radio
[   13.681814] Broadcom 43xx driver loaded [ Features: PNL ]
[   13.699313] Bluetooth: RFCOMM TTY layer initialized
[   13.699323] Bluetooth: RFCOMM socket layer initialized
[   13.699326] Bluetooth: RFCOMM ver 1.11
[   13.726128] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.726134] Bluetooth: BNEP filters: protocol multicast
[   13.731432] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   13.735296] ppdev: user-space parallel port driver
[   13.760196] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   13.760858] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   13.760986] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   13.766456] type=1400 audit(1346334995.162:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=487 comm="apparmor_parser"
[   13.767108] type=1400 audit(1346334995.162:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=487 comm="apparmor_parser"
[   13.767466] type=1400 audit(1346334995.162:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=487 comm="apparmor_parser"
[   13.771757] type=1400 audit(1346334995.166:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=535 comm="apparmor_parser"
[   13.790808] type=1400 audit(1346334995.186:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=537 comm="apparmor_parser"
[   13.804394] type=1400 audit(1346334995.202:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=537 comm="apparmor_parser"
[   13.824355] [drm] radeon defaulting to kernel modesetting.
[   13.824361] [drm] radeon kernel modesetting enabled.
[   13.824473] radeon 0000:01:05.0: power state changed by ACPI to D0
[   13.824480] radeon 0000:01:05.0: power state changed by ACPI to D0
[   13.824493] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.871481] [drm] initializing kernel modesetting (RS480 0x1002:0x5975 0x1028:0x01F5).
[   13.871517] [drm] register mmio base: 0xC0100000
[   13.871520] [drm] register mmio size: 65536
[   13.871700] [drm] Generation 2 PCI interface, using max accessible memory
[   13.871707] radeon 0000:01:05.0: VRAM: 128M 0x0000000078000000 - 0x000000007FFFFFFF (128M used)
[   13.871712] radeon 0000:01:05.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[   13.871728] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   13.871731] [drm] Driver supports precise vblank timestamp query.
[   13.871745] [drm] radeon: irq initialized.
[   13.872550] [drm] Detected VRAM RAM=128M, BAR=128M
[   13.872556] [drm] RAM width 128bits DDR
[   13.873504] [TTM] Zone  kernel: Available graphics memory: 437768 kiB.
[   13.873509] [TTM] Zone highmem: Available graphics memory: 965356 kiB.
[   13.873512] [TTM] Initializing pool allocator.
[   13.873554] [drm] radeon: 128M of VRAM memory ready
[   13.873556] [drm] radeon: 512M of GTT memory ready.
[   13.873588] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.886044] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   13.898310] [drm] PCIE GART of 512M enabled (table at 0x0000000032F80000).
[   13.899559] radeon 0000:01:05.0: WB enabled
[   13.902457] [drm] Loading R300 Microcode
[   13.950048] mmcblk0: mmc0:8e24 SD02G 1.84 GiB 
[   13.961333]  mmcblk0: p1
[   14.016843] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.103359] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[   14.111920] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   14.122238] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.353541] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   14.411437] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.411446] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411451] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   14.411455] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411459] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   14.411463] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411466] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   14.411470] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411474] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   14.411478] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411481] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   14.411485] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411489] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   14.411493] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411498] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   14.411502] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411506] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   14.411510] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411513] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   14.411517] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411520] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   14.411525] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411528] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   14.411532] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.411535] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   14.411540] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.411543] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   14.411547] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.411552] cfg80211: World regulatory domain updated:
[   14.411554] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.411558] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411562] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.411566] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.411570] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.411573] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.434364] [drm] radeon: ring at 0x0000000080001000
[   14.434385] [drm] ring test succeeded in 1 usecs
[   14.434615] [drm] radeon: ib pool ready.
[   14.434706] [drm] ib test succeeded in 0 usecs
[   14.435502] [drm] Panel ID String: AUO                     
[   14.435507] [drm] Panel Size 1280x800
[   14.446677] [drm] radeon legacy LVDS backlight initialized
[   14.446682] [drm] Radeon Display Connectors
[   14.446684] [drm] Connector 0:
[   14.446686] [drm]   VGA
[   14.446690] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   14.446692] [drm]   Encoders:
[   14.446695] [drm]     CRT1: INTERNAL_DAC2
[   14.446697] [drm] Connector 1:
[   14.446699] [drm]   LVDS
[   14.446702] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   14.446704] [drm]   Encoders:
[   14.446706] [drm]     LCD1: INTERNAL_LVDS
[   14.446804] [drm] radeon: power management initialized
[   14.504890] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   14.504897] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   14.504901] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   14.516364] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.524253] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.525705] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.558628] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   14.594238] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.607338] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.607349] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.611314] composite sync not supported
[   14.621570] [drm] fb mappable at 0xC8040000
[   14.621575] [drm] vram apper at 0xC8000000
[   14.621578] [drm] size 4096000
[   14.621581] [drm] fb depth is 24
[   14.621583] [drm]    pitch is 5120
[   14.621631] init: failsafe main process (721) killed by TERM signal
[   14.633701] fbcon: radeondrmfb (fb0) is primary device
[   14.634868] Console: switching to colour frame buffer device 160x50
[   14.634920] fb0: radeondrmfb frame buffer device
[   14.634924] drm: registered panic notifier
[   14.634938] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   14.697467] composite sync not supported
[   14.918774] type=1400 audit(1346334996.314:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=807 comm="apparmor_parser"
[   14.919449] type=1400 audit(1346334996.314:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=808 comm="apparmor_parser"
[   14.920205] type=1400 audit(1346334996.318:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=808 comm="apparmor_parser"
[   14.920568] type=1400 audit(1346334996.318:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=808 comm="apparmor_parser"
[   15.424898] composite sync not supported
[   15.452460] composite sync not supported
[  115.376441] composite sync not supported
[  115.414398] composite sync not supported
```Tell me if anything else is required.

---

