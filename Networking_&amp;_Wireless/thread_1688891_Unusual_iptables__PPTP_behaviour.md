---
title: "Unusual iptables / PPTP behaviour"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by wesg on 2011-02-15
My Ubuntu server currently handles DHCP duties for my network, and I want it to run a VPN server for accessing my LAN from the Internet. I have iptables handling NAT and filter, but right now I can connect to the VPN from inside the lan, however it does not route to the internet at large. 

I have NAT masquerading packets to eth1 (my internet facing interface) for the DHCP server, and recently added a masquerading rule for ppp0, but no joy. What other configurations do I need to add to iptables to make it work?

I added a log message to the forward chain in the hopes of learning more, and I discovered that things seem to be backwards. Ie. in the code below, 192.168.0.200 SHOULD be the incoming IP and eth1 should be outgoing (i was searching for Yahoo).

 ```
Feb 15 23:47:25 Nimitz kernel: [623031.850127] IN=eth1 OUT=ppp0 SRC=208.67.220.220 DST=192.168.0.200 LEN=72 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=UDP SPT=53 DPT=60426 LEN=52
```

---

