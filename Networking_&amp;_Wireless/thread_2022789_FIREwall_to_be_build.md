---
title: "FIREwall to be build"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by sabarinath on 2012-07-11
Hai to all,
             my problem is ,I having the ubuntu 11.04 natty OS and installed virtual box inside on ubuntu& installed virtual OS as REDHAT LINUX 5.4 .
             The scenario i having,192.168.56.0 series ip addr for  virtual box and configured VB network as HOST-ONLY ADAPTER (vboxnet0).FROM ubuntu i connecting INTERNET using mobile blue-tooth modem.(in such case i got 10.0.66.2 ip addre and gw is 10.0.66.1 from ISP).
           this case in ubuntu OS itself the static routing entries makes automatically gw 10.0.66.1.so due to this any internet query from VB network is get connection to  internet.
You may clear by following route -n cmd on ubuntu.

[B]sabari@sabari-HCL-Notebook:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.66.0       0.0.0.0         255.255.255.240 U     5      0        0 bnep0
10.0.2.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.66.1       0.0.0.0         UG    0      0        0 bnep0

[/B]so that any query from 192.168.56.0 n/w get public access.

i need was, i want provide access  to Internet with some restrictions to access some site for VB networks using IPTABLES  in ubuntu.

So my requirement is :
       1.all packets from 192.168.56.0 to be examined by  physical  ubuntu OS using IPTABLES and forward to gw 10.0.66.1 if any packet access to Internet.

      2.during public access from 192.168.56.0 series ip through UBUNTU,i need some restriction to some particular web addr block through IPTABLE.

Please revert.........


Thank u

Regards
sabari

---

