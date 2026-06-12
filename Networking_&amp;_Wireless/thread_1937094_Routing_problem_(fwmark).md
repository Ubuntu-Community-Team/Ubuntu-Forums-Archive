---
title: "Routing problem (fwmark)"
date: 2012-03-07
forum: Networking &amp; Wireless
---

### Post by ruden on 2012-03-07
Hi! I'm trying to set up internet on my ubuntu 10.04 with 2 internet channels. I want to send all tcp packets through interface eth0 (isp1) and all udp packets through interface eth1 (isp2). I've read LARTC HOW-TO but still can't resolve this task.
What I've done:
iptables -t mangle -A OUTPUT -p tcp -j MARK --set-mark 1
iptables -t mangle -A OUTPUT -p udp -j MARK --set-mark 2
Then I'm adding rules:
ip rule add fwmark 1 lookup t1
ip rule add fwmark 2 lookup t2
And filling tables t1 & t2
ip ro add default via 192.168.0.1 table t1
ip ro add default via 192.168.1.1 table t2
And now if make any connections (ssh or via browser) I get: "Network is unreachable"
Looks like rule with fwmark doesn't work because iptables mark packets:
sudo iptables -t mangle -vnL OUTPUT
Chain OUTPUT (policy ACCEPT 1423 packets, 147K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1122  116K MARK       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK xset 0x1/0xffffffff

---

### Post by ruden on 2012-03-07
sorry for my english...
I wanted to say that iptables worked fine but ip rules with fwmark didn't

---

