---
title: "Port forwarding doesnt work"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by tobislv on 2009-07-03
I need to forward ssh from internet to my local network computer:
x.x.x.x - external IP
192.168.0.70 - Internal IP
eth0 external NIC
eth1 internal NIC
iptables rulles:
iptables -t nat -A PREROUTING -i eth0 -p tcp -d x.x.x.x --dport 22 -j DNAT --to 192.168.0.7:22
iptables -A FORWARD -p tcp -i eth0 -o eth1 -d 192.168.0.7 --dport 22 -j ACCEPT 
 
 
iptables -t nat -L -n -v:
 
Chain PREROUTING (policy ACCEPT 2469K packets, 179M bytes)
pkts bytes target prot opt in out source destination
123 5516 REDIRECT tcp -- eth1 * 0.0.0.0/0 0.0.0.0/0 tcp dpt:80 redir ports 3128
0 0 DNAT tcp -- eth0 * 0.0.0.0/0 x.x.x.x tcp dpt:22 to:192.168.0.70:22
Chain POSTROUTING (policy ACCEPT 15045 packets, 1279K bytes)
pkts bytes target prot opt in out source destination
837 50816 MASQUERADE all -- * eth0 0.0.0.0/0 0.0.0.0/0
 
iptables -L -n -v:
 
Chain INPUT (policy ACCEPT 1485K packets, 145M bytes)
pkts bytes target prot opt in out source destination
4748 2353K ACCEPT all -- * * 0.0.0.0/0 0.0.0.0/0 state RELATED,ESTABLISHED
 
Chain OUTPUT (policy ACCEPT 153K packets, 9582K bytes)
pkts bytes target prot opt in out source destination
 
0 0 ACCEPT tcp -- eth0 eth1 0.0.0.0/0 192.168.0.70 tcp dpt:22
Chain OUTPUT (policy ACCEPT 233K packets, 64M bytes)
pkts bytes target prot opt in out source destination
6182 2447K ACCEPT all -- * * 0.0.0.0/0 0.0.0.0/0 state RELATED,ESTABLISHED

---

### Post by computer13137 on 2009-07-03
I'm not that advanced in iptables admittedly, but when I want to forward a port in my Ubuntu router, I do it this way.

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 22 -j DNAT --to 10.1.1.55:22

I've never had to use that FORWARD statement... :S

In the above example, I am forwarding SSH (tcp port 22) to the internal IP of 10.1.1.55.
On my setup and that command, it is assumed that eth0 is the Internet.

-Kirk

---

### Post by superprash2003 on 2009-07-03
you could use something like gufw to handle that

---

