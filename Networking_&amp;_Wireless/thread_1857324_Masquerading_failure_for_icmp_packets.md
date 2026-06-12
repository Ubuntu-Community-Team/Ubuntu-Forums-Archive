---
title: "Masquerading failure for icmp packets"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by codingfreak on 2011-10-10
Hi,

I am trying to perform NAPT operation using the MASQUERADE option of iptables.

Below is my nat rules

```
Chain POSTROUTING (policy ACCEPT 104 packets, 6628 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 MASQUERADE  tcp  --  *      eth1    192.168.1.0/24       0.0.0.0/0           masq ports: 63232-63359 
    0     0 MASQUERADE  udp  --  *      eth1    192.168.1.0/24       0.0.0.0/0           masq ports: 63232-63359 
    0     0 MASQUERADE  icmp --  *      eth1    192.168.1.0/24       0.0.0.0/0           masq ports: 63232-63359
```

In case of ICMP packets the MASQUERADE option sets the echo id attribute in ICMP packet since it doesnt have any field called SOURCE PORT.

But even after using the above rules echo id in my ICMP packet is not set with the value from port range.

Can anyone help me out to debug the same ?

---

