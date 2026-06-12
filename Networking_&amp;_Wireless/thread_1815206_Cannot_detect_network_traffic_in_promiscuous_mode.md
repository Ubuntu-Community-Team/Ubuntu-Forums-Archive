---
title: "Cannot detect network traffic in promiscuous mode"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by amolvaidya06 on 2011-07-30
Howdy,

I seem unable to be able to detect network traffic in promiscuous mode.  In searching for the traffic to and from another computer, all I get, no matter what I do on the other computer is something like the following:

```

sudo tcpdump -nnvvtei wlan0 | grep -i 192.168.1.112
tcpdump: listening on wlan0, link-type EN10MB (Ethernet), capture size 65535 bytes
00:1f:3c:95:d0:57 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.1 (ff:ff:ff:ff:ff:ff) tell 192.168.1.112, length 28
00:1f:3c:95:d0:57 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.106 (ff:ff:ff:ff:ff:ff) tell 192.168.1.112, length 28
00:1f:3c:95:d0:57 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.1 (ff:ff:ff:ff:ff:ff) tell 192.168.1.112, length 28
00:1f:3c:95:d0:57 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.68 (ff:ff:ff:ff:ff:ff) tell 192.168.1.112, length 28
00:1f:3c:95:d0:57 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.1 (ff:ff:ff:ff:ff:ff) tell 192.168.1.112, length 28
00:1f:3c:95:d0:57 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.109 (ff:ff:ff:ff:ff:ff) tell 192.168.1.112, length 28
00:1f:3c:95:d0:57 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.1 (ff:ff:ff:ff:ff:ff) tell 192.168.1.112, length 28
00:1f:3c:95:d0:57 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Ethernet (len 6), IPv4 (len 4), Request who-has 192.168.1.103 (ff:ff:ff:ff:ff:ff) tell 192.168.1.112, length 28

```Ad nauseum.  I don't know what other details you need, or what might be wrong, but I'd appreciate any help I can get.

---

