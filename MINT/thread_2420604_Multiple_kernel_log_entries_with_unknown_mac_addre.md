---
title: "Multiple kernel log entries with unknown mac address"
date: 2019-06-07
forum: MINT
---

### Post by arwdcs on 2019-06-07
Hi:

I have a Linix Mint installation, and my Kernel logs contain quite a few errors that I am trying to nail down.  One of them is very strange: I have multiple (thousands not hundreds) of log entries that read like this:

kernel: [328453.278549] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:cc:40:d0:ef:78:54:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=7348 DF
 PROTO=2

The entries are identical except for the ID= field, which always contains a unique number.  I have no idea what it means, but I have started to try to find the offending device in the hope that sheds some light.  I have scoured my network for devices that have that MAC address - and I am stumped.

Can anyone make any suggestions either was to what is causing the log entries and/or how I might fault-find and fix please?

V/R

Andreww

---

### Post by Doug S on 2019-06-07
Those type of packets are often from the router or modem, and are exploratory. The IP 224.0.0.1 is a [multicast address]("https://en.wikipedia.org/wiki/Multicast_address").  The source MAC address seems to be from some sort of NetGear device ( reference: [https://aruljohn.com/mac/CC40D0EF7854](https://aruljohn.com/mac/CC40D0EF7854) ), your router perhaps?

I get these packets also (2 per minute) from my ISP. The source IP is actually some internal address of my ISP, and nothing to do with my local LAN. To avoid my logs clogging I use an iptables rule to DROP them, without logging and early in the chain of rules. Packet examples:

```
2019-03-10 21:04:23.739743 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2019-03-10 21:04:53.737931 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2019-03-10 21:05:23.737627 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2019-03-10 21:05:53.735755 IP 10.197.248.13 > 224.0.0.1: igmp query v2
2019-03-10 21:06:23.734660 IP 10.197.248.13 > 224.0.0.1: igmp query v2
```

iptables rule example:

```
# Site Specific: ISP (Telus) annoying stuff
# This will prevent the further below generic 10.0.0.0/8 rule from logging stuff that is already known.
# V1.08: Change to generic 224.0.0.1 destination DROP for both internel and external source.
#$IPTABLES -A INPUT -i $EXTIF -s 10.197.248.13 -d $UNIVERSE -j DROP
$IPTABLES -A INPUT -d 224.0.0.1 -j DROP
```

Where:

```
IPTABLES=/sbin/iptables
EXTIF="enp4s0"
UNIVERSE="0.0.0.0/0"
```


EDIT: As for the MACs: They also don't otherwise appear anywhere else in my system. Not in the "arp" tables, not in any other packets to/from my system. Example with MACs:

```
2019-06-03 04:09:27.420403 00:90:d0:63:ff:00 > 01:00:5e:00:00:01, ethertype IPv4 (0x0800), length 60: 10.197.248.13 > 224.0.0.1: igmp query v2
```

---

### Post by oldfred on 2019-06-08
Moved to Mint sub-forum since not Ubuntu and Mint may be different.

That looks like a inet6 MAC address. Best not to post MAC addresses as someone can then spoof your address to do bad things that then are recorded as you.

Do you have IPv6 addressing, or is it saying it cannot connect to a IPv6 connection, and keeps trying?

---

### Post by Doug S on 2019-06-08
> **oldfred said:**
> That looks like a inet6 MAC address.
Do you have IPv6 addressing, or is it saying it cannot connect to a IPv6 connection, and keeps trying?

I believe this:

```
MAC=01:00:5e:00:00:01:cc:40:d0:ef:78:54:08:00
```
Is exactly the 14 bytes, in order, of the raw ethernet frame segment for [DST MAC, SRC MAC, ETHERTYPE], and breaks down as:
Source MAC: cc:40:d0:ef:78:54
Destination MAC (perhaps doesn't matter for a broadcast packet, I don't know): 01:00:5e:00:00:01
Ethernet type (2 bytes): 08:00

Reference: [https://en.wikipedia.org/wiki/Ethernet_frame]("https://en.wikipedia.org/wiki/Ethernet_frame")

> **oldfred said:**
> Best not to post MAC addresses as someone can then spoof your address to do bad things that then are recorded as you.
I am less worried about publicizing MACs than external IP addresses. MACs are dropped upon sub-net (LAN) boundaries, and only relevant within a local context.

---

