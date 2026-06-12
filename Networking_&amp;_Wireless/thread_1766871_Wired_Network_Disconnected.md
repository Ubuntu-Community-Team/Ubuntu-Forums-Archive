---
title: "Wired Network: Disconnected"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by abal1221 on 2011-05-24
I installed Ubuntu 11.04 off a fresh install earlier today and have not had any network connectivity since.

It's been awhile since I've used Linux so my skills are rusty, I'll apologize for that in advance.

Installed on exact same hardware (plus hard drive and memory) as an XP system that had connectivity earlier today.  Connected to exact same network cable plugged into exact same router.  Tried different switch ports all with same result.  Link lights on both NIC and switch.  Motherboard has 2 NICs, moved cable between the two and both had link lights.

ifconfig recognizes that the system has two NICs (eth0 and eth1) as well as loopback.  At this moment in time, eth1 has the cable plugged in and eth0 is disconnected.  eth1 looks like it is pulling an IPv6 address but no IPv4 address.  I have an older Linksys router that I seriously doubt is IP6 compatible so I suspect eth1 is assigning itself it's own IP.  If the cable is moved from eth1 to eth0, eth0 exhibits the same behavior

I have tried to ifdown eth0 and eth1, regardless which has the cable plugged in both return "interface ethX not configured"
I have tried to ifup eth0 and eth1, regardless which has the cable plugged in both return "Ignoring unknown interface ethX=ethX"

I added line to **/etc/default/grub**[B]:
[/B]GRUB_CMDLINE="ipv6.disable=1" Did a sudo update-grub and rebooted.  eth1 still has an IPv6 address but no IPv4

/etc/networks/interfaces does not have an entry for either eth0 or eth1

Any suggestions?

---

### Post by dineshs on 2011-05-25
what about ```
sudo lshw -C network
``` ?

---

### Post by abal1221 on 2011-05-25
> **dineshs said:**
> what about ```
sudo lshw -C network
``` ?

That command does not return anything

If I leave off the "-C network" I get the following:

*-bridge:0
description: Ethernet Interface
product: MCP55 Ethernet
vendor: nVidia Corporation
physical id: 11
bus info: pcia@0000:00:11.0
logical name: eth0
version: a2
serial: looks like a MAC address
capacity: 1000000000
width: 32 bits
clock: 66MhZ
capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 lin=no maxlatency=20 mingnt=1 multicast=yes port=MII
resources: IRQ and memory stuff

*-bridge:1
Same as above, except for physical ID, serial number/MAC address, logical name
link is set to yes (2 NICs on Motherboard, this is the connected NIC), duplex=full, speed=100MBit/s

---

