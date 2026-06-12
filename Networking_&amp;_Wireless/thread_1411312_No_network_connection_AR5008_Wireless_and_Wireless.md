---
title: "No network connection: AR5008 Wireless and Wireless WiFi Link 5100"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by crash123 on 2010-02-19
Let me start by saying that yes, I have checked the wifi wiki, and though it doesn't say much about either of my two wireless adapters well...see below.

I've been using Xubuntu 9.10 for the past month on my Toshiba m305-4910 laptop. I then decided to switch to (first) Ubuntu 9.04 last week. Both of my wireless cards have worked without any problems at all. I haven't had to use madwifi or do anything at all; they just worked automatically after installation.

Today, I decided to upgrade 9.04 to Ubuntu 9.10. The upgrade went fine (at least I thought). I restarted the computer after installation, and my wireless was still working perfectly fine. I made **absolutely no changes** to any settings before shutting it down again; the only thing I did was use the software sources to download a few games, and this worked fine. However, when I restarted it again about an hour ago, the wifi was completely dead. Now the network manager icon has an "x" on it, and it says, "No Network Connection" when I put my cursor over it. When I click on the icon to see the menu, it doesn't even list my two wireless adapters, let alone show me networks in the area. 

These adapters definitely work with Ubuntu (at least the distros I've used)a, since I've been using them for over a month with **no problems** and without having to do anything special at all to get them to work. Do you all have ideas what's causing the issue? Thanks for any help here...this is frustrating. 


Here's the info it says to give you on the forum:


Toshiba M305-S4910

**lshw**

WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2863MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:f4000000-f43fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:f4400000-f44fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f4a04800-f4a04bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f4800000-f4803fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 memory:b8000000-b80fffff
           *-network
                description: Network controller
                product: AR5008 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ath9k latency=0
                resources: irq:16 memory:b8000000-b800ffff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:2000(size=4096) memory:b8100000-b81fffff
           *-network
                description: Ethernet interface
                product: 88E8040T PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 12
                serial: 00:23:8b:a1:fa:3e
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
                resources: irq:28 memory:b8100000-b8103fff ioport:2000(size=256)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:b8200000-b82fffff
           *-network
                description: Network controller
                product: Wireless WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=iwlagn latency=0
                resources: irq:30 memory:b8200000-b8201fff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f4a04c00-f4a04fff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:f4700000-f47fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:0a:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=32
                resources: irq:16 memory:ff501000-ff501fff memory:f4700000-f47007ff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 1.2
                bus info: pci@0000:0a:01.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:16 memory:f4700800-f47008ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 1.3
                bus info: pci@0000:0a:01.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage cap_list
                configuration: latency=32
                resources: memory:f4702000-f4702fff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:f4a04000-f4a047ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b8300000-b83000ff ioport:1c00(size=32)


**lspci**

02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

**lsmod**

ath9k                 258744  0 
iwlagn                109194  1 

ath                     8060  1 ath9k
iwlcore               112796  1 iwlagn

**dmesg**

[    9.995565] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    9.995569] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.995637] iwlagn 0000:08:00.0: enabling device (0000 -> 0002)
[    9.995647] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.995659] iwlagn 0000:08:00.0: setting latency timer to 64
[    9.995689] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   10.024412] ath9k 0000:02:00.0: enabling device (0000 -> 0002)
[   10.024425] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.024459] ath9k 0000:02:00.0: setting latency timer to 64
[   10.037263] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.037346]   alloc irq_desc for 30 on node -1
[   10.037349]   alloc kstat_irqs on node -1
[   10.037383] iwlagn 0000:08:00.0: irq 30 for MSI/MSI-X
[   10.169255] ath: EEPROM regdomain: 0x10
[   10.169258] ath: EEPROM indicates we should expect a direct regpair map
[   10.169261] ath: Country alpha2 being used: CO
[   10.169262] ath: Regpair used: 0x10


[   70.256391] Call Trace:
[   70.256395]  [<c02f19f5>] ? crypto_alg_mod_lookup+0x55/0x70
[   70.256399]  [<c02f1a62>] ? crypto_alloc_base+0x22/0x80
[   70.256412]  [<f90af2f0>] ? iwl_mac_hw_scan+0x0/0xf0 [iwlcore]
[   70.256426]  [<f8ff310a>] ? ieee80211_wep_init+0x2a/0x80 [mac80211]
[   70.256437]  [<f8ff11ff>] ? ieee80211_register_hw+0x1ff/0x4d0 [mac80211]
[   70.256442]  [<c048ea01>] ? pci_read+0x11/0x40
[   70.256455]  [<f90a3b34>] ? iwl_setup_mac+0x84/0xd0 [iwlcore]
[   70.256463]  [<f9212e1b>] ? iwl_pci_probe+0x4ab/0x5e0 [iwlagn]
[   70.256466] Registered led device: ath9k-phy1::radio
[   70.256471]  [<c032c31e>] ? local_pci_probe+0xe/0x10
[   70.256475]  [<c032d0a0>] ? pci_device_probe+0x60/0x80
[   70.256479]  [<c03a6ba0>] ? really_probe+0x50/0x140
[   70.256483]  [<c0573efa>] ? _spin_lock_irqsave+0x2a/0x40
[   70.256485] Registered led device: ath9k-phy1::assoc
[   70.256490]  [<c03a6ca9>] ? driver_probe_device+0x19/0x20
[   70.256493]  [<c03a6d29>] ? __driver_attach+0x79/0x80
[   70.256497]  [<c03a61f8>] ? bus_for_each_dev+0x48/0x70
[   70.256501]  [<c03a6a69>] ? driver_attach+0x19/0x20
[   70.256503] Registered led device: ath9k-phy1::tx
[   70.256506]  [<c03a6cb0>] ? __driver_attach+0x0/0x80
[   70.256510]  [<c03a644f>] ? bus_add_driver+0xbf/0x2a0
[   70.256513]  [<c032cfe0>] ? pci_device_remove+0x0/0x40
[   70.256516]  [<c03a6fb5>] ? driver_register+0x65/0x120
[   70.256519] Registered led device: ath9k-phy1::rx
[   70.256531]  [<f8ffd5b8>] ? ieee80211_rate_control_register+0xc8/0x120 [mac80211]
[   70.256536]  [<c032d2c0>] ? __pci_register_driver+0x40/0xb0
[   70.256543]  [<f90eb050>] ? iwl_init+0x50/0x6e [iwlagn]
[   70.256546] phy1: Atheros AR5418 MAC/BB Rev:2 AR2122 RF Rev:81: mem=0xf92c0000, irq=16
[   70.256551]  [<c010112c>] ? do_one_initcall+0x2c/0x190
[   70.256558]  [<f90eb000>] ? iwl_init+0x0/0x6e [iwlagn]
[   70.256563]  [<c0173761>] ? sys_init_module+0xb1/0x1f0
[   70.256566]  [<c01033ac>] ? syscall_call+0x7/0xb

**sudo lshw -C network**

*-network               
       description: Network controller
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ath9k latency=0
       resources: irq:16 memory:b8000000-b800ffff
  *-network
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:23:8b:a1:fa:3e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:b8100000-b8103fff ioport:2000(size=256)
  *-network
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwlagn latency=0
       resources: irq:30 memory:b8200000-b8201fff




**iwlist scan wlan**0
iwlist: unknown command `wlan0' (check 'iwlist --help').
iwlist scan iwlagn 
iwlist: unknown command `iwlagn' (check 'iwlist --help').

**lsb_release -d**
Description:	Ubuntu 9.10 (32-bit)

**uname -mr**
2.6.31-20-generic i686

**sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                         Ignoring unknown interface eth0=eth0.
                                                                        [ OK ]

---

### Post by crash123 on 2010-02-19
Okay, nevermind...for now. I just restarted again, and now the internet works fine. That would've been the smart thing to do the last time around.

But I still have no idea why it didn't work the last time at all. I'll post again if it becomes a problem again, I guess.

---

