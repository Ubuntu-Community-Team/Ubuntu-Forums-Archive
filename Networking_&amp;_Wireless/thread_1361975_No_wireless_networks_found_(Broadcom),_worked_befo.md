---
title: "No wireless networks found (Broadcom), worked before"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by yhrn on 2009-12-22
Hi,
I installed Karmic netbook remix on my Lenovo S10e about two months ago, enabled the "Broadcom STA wireless driver" in "Hardware Drivers" and after that wireless was working fine.

Then two days ago, I could no longer connect to any wireless networks - the NetwokManager applet didn't list any networks at all (another Ubuntu laptop next to it would find >20 networks) but there's still a section for wireless networks and it says that wireless networking is enabled. I haven't changed anything (might have installed some updates from the Ubuntu repos but that's all).

lshv gives:

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:19:5d:21
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:f0200000-f020ffff
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:7a:ca:85
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f0400000-f0403fff
```and iwlist scan gives:

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Failed to read scan data : Invalid argument
```I'm suspecting some kind of hardware failure but I'd like to be sure before I try to send it to Lenovo (their support for consumer products really sucks in Sweden).

I also tried to use the B43 driver as described [here]("http://ubuntuforums.org/showthread.php?t=1266620") but then I could not even bring the network interface up.

Any ideas on how to investigate this further?

---

### Post by yhrn on 2009-12-22
This is completely insane! Two minutes after I posted this the wireless networking started working again. Without me changing anything! I just started the netbook (posting this from another box) and everything was working again. Honest!

Well, I guess that I might as well mark this as solved since if it stops working again I guess it must be hardware failure.

---

