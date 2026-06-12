---
title: "is openvpn binding to a port?"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by pavel989 on 2010-10-12
```
Tue Oct 12 08:31:09 2010 UDPv4 link local (bound): [AF_INET]************:4605

Tue Oct 12 08:31:09 2010 Initialization Sequence Completed

```
...minus a few other things in between, it looks to me as though openvpn is binidng to the correct port. however, running netstat, reveals that port 4605 isnt used, running nmap on myself reveals the same.

at first i thought it was a firewall issue, but then why can i ssh to myself but not vpn? 

```
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4605
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```


For the record, im still thinking its got to do with iptables, because it was working prior to me messin with iptables



EDIT::
openvpn is definitely binding to the right port as netstat -a revealed.

but then why cant i connect to it?

---

