---
title: "udp packets goes through old default route"
date: 2012-10-03
forum: Networking &amp; Wireless
---

### Post by swex on 2012-10-03
Hello everybody! The problem is:
I've got ubuntu server machine with 2 eth interfaces ex: eth0, eth1.
eth0-internet, eth1-lan.
And also I've got pptp connection to internet connection through eth0. 
In iptables I've got two nat rules for both eth1->ppp, eth1->eth0(reason: if ppp connection died). In eth1 network I've got audiocodes mp-201 VoIP to analog adapter. It uses external voip server, through nat with UDP packets. Point of problem: if my pptp connection drops for some reason packets from mp-201 starts to go through eth0 iface, and after pptp reconnects voip stop working because of changing routing rules.
PS: I used tcp dump to understand problem and I figured out that packets from mp-201 got src address of eth0 iface, instead of newly connections (used nc -u from lan machine to test) got right pptp iface address and works just fine. Where is that udp masquerade timeout settings. For now only solution to this problem is rebooting server or power off mp-201 for some "long" time about 3-5 min. Thanks.

---

