---
title: "what is Chain ufw-user-input ?"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by chinye2020 on 2013-01-09
```

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination
  213 12676 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:80
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8080
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:8080
    4   168 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:3306
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:3306
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6901
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:6901
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6902
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:6902
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:6903
 2848  177K ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:6903
    4   196 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5900
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5900
    1    48 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:5902
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:5902


```
what is Chain ufw-user-input meaning? 
1)all the port received from incoming data? 
2)those data are bypass firewall?

---

### Post by Doug S on 2013-01-09
It is a chain created in the ufw iptabples rule set for the user defined rules to be added.
Packets incoming, on any interface, with the listed destination ports are accepted, yes.
I wouldn't call it by-passing the firewall, but rather not blocked by the iptables rule set at the users request.
 
Note: I do not actually use ufw. I only use iptables directly.

---

