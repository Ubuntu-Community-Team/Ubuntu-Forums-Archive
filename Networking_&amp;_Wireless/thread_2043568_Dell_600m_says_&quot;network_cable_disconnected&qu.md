---
title: "Dell 600m says &quot;network cable disconnected&quot;"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by bretsk2500 on 2012-08-16
Hi, I'm new here...

I recently revived my old Dell 600m Laptop with a new ebay HDD and Lubuntu 12.04LTS.  The OS keeps saying that the network cable is disconnected... it is a known good cable (i.e, I unplug it from the 600m and plug it into the win7 mini 10... and it works just fine).

I have no link light when plugged into the 600m (either directly or into the dock).  It worked fine when puppy 5 was installed on the old HDD (which sharted itself, and puppy sucks) so it's not a hardware problem.

ifconfig shows for eth0:

link endcap: Ethernet HWaddr 00:12:3f:f2:la:2f
UP BROADCAST MULTICAST MTU:1500 Metric 1
Rx packets all 0's
Tx Packets all 0's
RX/TX bytes 0
interrupt:11

I've got the DNS setup for 8.8.8.8 and 8.8.4.4

I'm currently forgetting the command to show what is on the pci bus.... but the broadcom BCM4401 does show up as eth0

HELP!

---

### Post by Hadaka on 2012-08-17
Hi, I have the same brcm as well and had the same problem once.
try this.
click the triangle network dohickey next to the envelope....upper right screen
then uncheck Enable Network
boot the machine
then repeat above and enable the network.

here is your lspci command.

```
lspci -nnk | grep -iA2 net 
```

this will show your network cards and their drivers.
hope this helps

---

### Post by bretsk2500 on 2012-08-19
I tried that... didn't work any other suggestions?

---

### Post by Iowan on 2012-08-19
**sudo lshw -C network** should provide some useful information.

---

### Post by dandnsmith on 2012-08-20
Just a thought - have you used this particular cable with your 600m previously (with success)?
I ask because some systems will work with straight patch cables, but not with X-over patch cables.

---

### Post by bretsk2500 on 2012-08-21
yes, it was the exact same cable it was plugged into before the win 98 HDD crashed...

sudo lshw -C network results

 *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:f2:1a:2f
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:11 memory:faffe000-faffffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:faffc000-faffdfff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:14:a5:38:83:3d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-23-generic firmware=666.2 ip=192.168.1.155 link=yes multicast=yes wireless=IEEE 802.11bg

---

