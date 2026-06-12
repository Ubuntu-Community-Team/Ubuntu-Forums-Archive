---
title: "Cannot share network connection with Roku"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by DevilInPgh on 2010-06-24
I seem to be having quite a big problem with Internet sharing.  After doing a clean install of Lucid, I tried to set up a shared connection between my computer and my Roku set-top box.  I have noticed that I am only able to set up a connection profile in Network Connections under the Ethernet card with the active Internet connection.  That is, whenever I try to set up a connection, I am not given the option of using the second Ethernet card.  Thus I can't share the network connection.  Can someone PLEASE help me?  The IRC has been completely useless.

---

### Post by DevilInPgh on 2010-07-12
BTTT.  Was on vacation for a couple weeks. Can someone please help me?

---

### Post by DevilInPgh on 2010-07-13
BTTT again.  Now problem includes trying to share Internet connection with laptop.

---

### Post by Iowan on 2010-07-13
Do both interfaces show up in (from a terminal) **sudo lshw -C network**?

---

### Post by DevilInPgh on 2010-07-15
Yes, both interfaces appear in the command output.

```
  *-network:0             
       description: Ethernet interface
       product: Gigabit Network Adapter
       vendor: Linksys
       physical id: 5
       bus info: pci@0000:00:05.0
       logical name: eth0
       version: 10
       serial: 00:18:f8:0d:13:02
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:16 ioport:e800(size=256) memory:dfffff00-dfffffff memory:dffc0000-dffdffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 10
       serial: 00:e0:29:6e:76:3e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=130.49.36.40 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:d800(size=256) memory:dffffd00-dffffdff

```

---

### Post by Iowan on 2010-07-15
Which card is available for connection profile(s)? The info you posted looks like eth1 has an IP address. Is that the one with the active Internet connection?

---

### Post by DevilInPgh on 2010-07-15
Yes.  Eth1 (the Accton card) is the active one.

---

### Post by Iowan on 2010-07-16
Network Manager lists no **Auto eth0** option? 
Verify that */etc/network/interfaces* has only two lines defining "lo". Have you tried building a new connection for eth0?

---

### Post by DevilInPgh on 2010-07-20
Output of /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

Also, how do I build a new connection?  Network Manager does have an "Auto Eth0" entry, though.  I still can't get it to share with the Roku.

---

### Post by Iowan on 2010-07-20
I'm still a little curious how eth1 became the primary Internet connection - ordinarily, eth0 is (but there are no rules...). Have you tried reversing the connections - plugging the Linksys into the internet, and the Acctron into the LAN?

---

### Post by DevilInPgh on 2010-07-21
Yes, no difference.

---

### Post by DevilInPgh on 2010-08-11
Bumpity bump.  Same problem, same tune, same whining about nobody helping.

---

### Post by DevilInPgh on 2010-08-17
BUMP <snip>



As you can probably guess, I'm getting pissed off now.

---

### Post by cariboo on 2010-08-17
Have you tried following [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") howto?

---

### Post by DevilInPgh on 2010-08-17
Yes, and it doesn't work.  Why else would I be posting in here?

---

