---
title: "ip forwarding"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by hkc on 2010-06-02
Hi All,
   We have on Ubuntu 10.04 LTS installed on one m/c which is connected to office network using pptp vpn.Now i want to enable ip_forwarding on this m/c so that i can connect my RH9 m/c through this.
For enabling ip forwarding i did the basic thing 
 "echo "1">/proc/sys/net/ipv4/ip_forward"
And added route on the RH m/c as 
route add -net 10.254.254.0 netmask 255.255.255.0 gw  192.168.1.10 dev eth0"
(IP of Ubuntu m/c is "192.168.1.10 and RH m/c is 192.168.1.15)
But some how ipforwarding is not working properly.
Can any one help?

---

### Post by hkc on 2010-06-03
Hi All,
   I was able to resolve the issue by following the steps.
1.echo "1">/proc/sys/net/ipv4/ip_forward(For ipforwarding)
2.iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE(For masquerading)
--HKC

---

