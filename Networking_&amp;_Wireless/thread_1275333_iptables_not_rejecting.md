---
title: "iptables not rejecting"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by supradave on 2009-09-25
I have a firewall device that has multiple interfaces.  On one interface, we have a wireless access point on the 192.168.129.0/24 network.  If you connect to the wireless, to access beyond the 129 network, you have to use OpenVPN to get in.  I have the following iptables rules in place:

```
-A INPUT -s 192.168.129.0/24 -d 192.168.129.1/32 -p udp -m udp --dport 6200 -m state --state NEW,ESTABLISHED -j ACCEPT 
-A INPUT -i eth1 -m iprange --dst-range 192.168.0.1-192.168.128.254 -j REJECT --reject-with icmp-port-unreachable 
-A INPUT -i eth1 -m iprange --dst-range 192.168.130.1-192.168.254.254 -j REJECT --reject-with icmp-port-unreachable
```

According to someone connecting on the 129 network, they are able to access all the networks beyond.

---

### Post by gombadi on 2009-09-25
The INPUT table is for packets arriving at an interface for the local machine.

The FORWARD table is for packets arriving, for example from the wireless interface, and leaving on some other interface.

Put your REJECT rules in the FORWARD table and try again.

---

### Post by supradave on 2009-09-29
Thanks for the assistance.

---

