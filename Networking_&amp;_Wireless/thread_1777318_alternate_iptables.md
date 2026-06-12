---
title: "alternate iptables"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by daxbau on 2011-06-07
hi everyone!

usually i use the default configuration for my network interfaces.

but now i'm in a different situation:

1.)  I get my internet via wireless.
2.)  I am connected via ethernet to a private (for ftp sharing) network.
3.)  Ubuntu prior traffic via wired interfaces 

heres my routing tabel by default.

```
root@hp-compaq-8510w:~# route -n 
```> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.213.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
172.16.32.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.108.0   0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
root@HP-Compaq-8510w:~# 
as you can see:
1.)  all traffic to anywhere is routed to the ethernet,
2.)  but the internet gateway is 192.168.108.0 and not the gw of eth.


wich would be the best mehtod for me? I use default all day, but at home I need to exchange the last line and the wlan0 line.

can you help me to write a script to solve my issue?

thanks alot

thanks for your help

---

