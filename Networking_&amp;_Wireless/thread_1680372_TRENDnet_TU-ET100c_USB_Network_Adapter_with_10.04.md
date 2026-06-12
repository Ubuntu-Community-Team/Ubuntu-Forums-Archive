---
title: "TRENDnet TU-ET100c USB Network Adapter with 10.04"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by SupaRice on 2011-02-02
Help... :)

I've got 4 or 5 of these TRENDnet USB network adapters ( TU-ET100c ) that I use frequently when I'm configuring firewalls or IPS devices for customers.  I use them in combination with VirtualBox to test.

They've always worked great until my new laptop I just got, and I put 10.04 on it. Previously I was on 9.x

Sometimes they will give a link light, other times not. And when they do the interface shows that it's up, but I can't get any traffic across the interface.

```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:63:a7:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=172.20.227.236 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:38 memory:f6cfe000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761e Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: f0:4d:a2:61:48:99
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5761e-v3.71 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:39 memory:f69e0000-f69effff memory:f69f0000-f69fffff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: eth4
       serial: 00:14:d1:1b:e4:03
       size: 10MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=pegasus driverversion=v0.6.14 (2006/09/27) duplex=half link=no multicast=yes port=MII speed=10MB/s

```

```

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68a0
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
03:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:01.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)

```


```

dmesg
[  123.421177] usb 2-1.1: new full speed USB device using ehci_hcd and address 3
[  123.532066] usb 2-1.1: device descriptor read/all, error -32
[  123.611214] usb 2-1.1: new full speed USB device using ehci_hcd and address 4
[  123.724169] usb 2-1.1: unable to read config index 0 descriptor/all
[  123.724175] usb 2-1.1: can't read configurations, error -32
[  123.801067] usb 2-1.1: new full speed USB device using ehci_hcd and address 5
[  123.851863] usb 2-1.1: configuration #1 chosen from 1 choice
[  123.878526] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
[  123.879002] __ratelimit: 21 callbacks suppressed
[  123.880939] pegasus 2-1.1:1.0: setup Pegasus II specific registers
[  124.068829] pegasus 2-1.1:1.0: read_mii_word failed
[  124.164963] pegasus 2-1.1:1.0: read_mii_word failed
[  124.257470] pegasus 2-1.1:1.0: read_mii_word failed
[  124.349483] pegasus 2-1.1:1.0: read_mii_word failed
[  124.444987] pegasus 2-1.1:1.0: read_mii_word failed
[  124.533997] pegasus 2-1.1:1.0: read_mii_word failed
[  124.625255] pegasus 2-1.1:1.0: read_mii_word failed
[  124.713266] pegasus 2-1.1:1.0: read_mii_word failed
[  124.803401] pegasus 2-1.1:1.0: read_mii_word failed
[  124.891283] pegasus 2-1.1:1.0: read_mii_word failed
[  124.987045] pegasus 2-1.1:1.0: read_mii_word failed
[  125.078679] pegasus 2-1.1:1.0: read_mii_word failed
[  125.171187] pegasus 2-1.1:1.0: read_mii_word failed
[  125.261193] pegasus 2-1.1:1.0: read_mii_word failed
[  125.346830] pegasus 2-1.1:1.0: read_mii_word failed
[  125.431838] pegasus 2-1.1:1.0: read_mii_word failed
[  125.516096] pegasus 2-1.1:1.0: read_mii_word failed
[  125.601605] pegasus 2-1.1:1.0: read_mii_word failed
[  125.694488] pegasus 2-1.1:1.0: read_mii_word failed
[  125.777372] pegasus 2-1.1:1.0: read_mii_word failed
[  125.864755] pegasus 2-1.1:1.0: read_mii_word failed
[  125.948138] pegasus 2-1.1:1.0: read_mii_word failed
[  126.030144] pegasus 2-1.1:1.0: read_mii_word failed
[  126.115776] pegasus 2-1.1:1.0: read_mii_word failed
[  126.192160] pegasus 2-1.1:1.0: read_mii_word failed
[  126.281294] pegasus 2-1.1:1.0: read_mii_word failed
[  126.364301] pegasus 2-1.1:1.0: read_mii_word failed
[  126.448937] pegasus 2-1.1:1.0: read_mii_word failed
[  126.564827] pegasus 2-1.1:1.0: read_mii_word failed
[  126.649829] pegasus 2-1.1:1.0: read_mii_word failed
[  126.649833] pegasus 2-1.1:1.0: can't locate MII phy, using default
[  126.651087] pegasus 2-1.1:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:14:d1:1b:e4:03
[  126.651118] usbcore: registered new interface driver pegasus
[  126.661125] udev: renamed network interface eth1 to eth4
[  126.747713] pegasus 2-1.1:1.0: read_mii_word failed
[  126.836595] pegasus 2-1.1:1.0: read_mii_word failed
[  126.913882] pegasus 2-1.1:1.0: read_mii_word failed
[  126.979364] pegasus 2-1.1:1.0: read_mii_word failed
[  126.979391] pegasus 2-1.1:1.0: update_eth_regs_async, status -22
[  126.981755] ADDRCONF(NETDEV_UP): eth4: link is not ready
[  130.651159] __ratelimit: 3549 callbacks suppressed
[  130.654167] ADDRCONF(NETDEV_CHANGE): eth4: link becomes ready
[  136.723354] pegasus 2-1.1:1.0: read_mii_word failed
[  141.439919] eth4: no IPv6 routers present
[  142.720085] __ratelimit: 95 callbacks suppressed
[  158.786347] pegasus 2-1.1:1.0: read_mii_word failed

```

Any other output I should post up?  I know enough to be dangerous so help! :)

---

### Post by SupaRice on 2011-02-07
*bump* Anybody?

---

### Post by walt.smith1960 on 2011-02-07
I can't help with your problem but I have a couple adapters that don't work out of the box with 10.10, they both needed work.  Both adapter DO work out of the box with 11.04 alpha.  It might be worth burning a liveCD just to see if it works.  Have you tried enabling wireless backports?

---

### Post by SupaRice on 2011-02-08
> **walt.smith1960 said:**
> I can't help with your problem but I have a couple adapters that don't work out of the box with 10.10, they both needed work.  Both adapter DO work out of the box with 11.04 alpha.  It might be worth burning a liveCD just to see if it works.  Have you tried enabling wireless backports?


Thanks for the reply.  I'll try the 11.04 and report back.  I've not enabled backports, don't know what that is.  I'll look it up.  It's not a wireless adapter though, it's a USB 10/100 Ethernet adapter.

---

