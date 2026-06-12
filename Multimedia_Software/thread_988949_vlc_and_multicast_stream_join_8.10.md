---
title: "vlc and multicast stream join 8.10"
date: 2008-11-21
forum: Multimedia Software
---

### Post by bogesman on 2008-11-21
Im having a hard time to make vlc join a multicast group and play multicasted stream. I achieved the same setup on windows with no problems.


This from VLC on start

```
main debug: creating demux: access='udp' demux='' path='@239.20.20.101:10135'
main debug: looking for access_demux module: 0 candidates
main warning: no access_demux module matched "udp"
main debug: TIMER module_Need() : 0.081 ms - Total 0.081 ms / 1 intvls (Avg 0.081 ms)
main debug: creating access 'udp' path='@239.20.20.101:10135'
main debug: looking for access module: 1 candidate
access_udp debug: opening server=:0 local=239.20.20.101:10135
main debug: net: opening 239.20.20.101 datagram port 10135
main debug: Multicast group join request
main debug: using access module "access_udp"
main debug: TIMER module_Need() : 0.525 ms - Total 0.525 ms / 1 intvls (Avg 0.525 ms)
main debug: Using AStream*Block
main debug: pre buffering
main debug: thread 2956172176 (input) created at priority 10 (input/input.c:370)
qt4 debug: Updating the stream status: 3
```

Thats from tcpdump on the interface.
sudo tcpdump -n -i eth0 -vv
```
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
08:51:09.572603 IP (tos 0xc0, ttl 1, id 0, offset 0, flags [DF], proto IGMP (2), length 40, options (RA)) 20.20.20.99 > 224.0.0.22: igmp v3 report, 1 group record(s) [gaddr 239.20.20.101 to_ex { }]
08:51:18.664073 IP (tos 0xc0, ttl 1, id 0, offset 0, flags [DF], proto IGMP (2), length 40, options (RA)) 20.20.20.99 > 224.0.0.22: igmp v3 report, 1 group record(s) [gaddr 239.20.20.101 to_ex { }]
```

Any knows issues about that ?
I really tried almost everything with no luck. Out of ideas.

---

### Post by bogesman on 2008-11-21
Finally i found where the problem lies after a day bumping my head. The problem is in the network driver r8168. It works I'm able to ping hosts from network, but i have the problem from the previous post. Tried with another ethernet adapter and problem solved. Now trying to change drivers so far no luck. I think that this is the latest driver i have. Any suggestions?

ethtool -i eth0```

driver: r8168
version: 8.009.00-NAPI
firmware-version:
bus-info: 0000:03:00.0
```

lspci |grep Ether
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by bogesman on 2008-11-29
Ignore previous post. That's not the reason :)
The real problem was caused by 

net.ipv4.conf.default.rp_filter
net.ipv4.conf.all.rp_filter

in /etc/sysctl.conf

After uncommenting them and changing them to

net.ipv4.conf.default.rp_filter=0
net.ipv4.conf.all.rp_filter=0

then sysctl -p problem solved. I hope it helps somebody else.

---

### Post by HorizonXP on 2010-03-09
This didn't help me. Mind you, I'm on Fedora 11 with vlc 1.0.4, so it could be something else entirely. Nevertheless, I have the same problem.

---

### Post by ayourk on 2011-07-10
What command line did you use or VLC options did you use to get this to work?

---

