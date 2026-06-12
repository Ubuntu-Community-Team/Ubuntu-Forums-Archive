---
title: "IPTABLES - nat with multiple translated sources"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by perlkad on 2012-07-27
Hello,

For iptables, I have the following topology with 2 physical interfaces:  eth0(WAN) and eth1(LAN).  Also I added some virtual interfaces to support additional ip addresses.


WAN  ----  eth0   (110.120.130.140/24)  ----  eth1   (10.20.30.40/24)  ----  1.2.3.4/24
     ----  eth0:1 (110.120.130.141/24)  ----  eth1:1 (10.20.30.41/24)
     ----  eth0:2 (110.120.130.142/24)  ----  eth1:2 (10.20.30.42/24)



Currently I have the following iptables with the translation path taken. 

-A PREROUTING -d 110.120.130.140 -p tcp -m tcp --dport 80 -j DNAT --to-destination 1.2.3.4:80
-A PREROUTING -d 110.120.130.141 -p tcp -m tcp --dport 80 -j DNAT --to-destination 1.2.3.4:80
-A PREROUTING -d 110.120.130.142 -p tcp -m tcp --dport 80 -j DNAT --to-destination 1.2.3.4:80
-A POSTROUTING -d 1.2.3.4 -j MASQUERADE

110.120.130.140 -> 10.20.30.40 -> 1.2.3.4
110.120.130.141 -> 10.20.30.40 -> 1.2.3.4
110.120.130.142 -> 10.20.30.40 -> 1.2.3.4


I want to do the NAT based on the below paths instead, so that the device (1.2.3.4) will see packets coming from different source ip.

110.120.130.140 -> 10.20.30.40 -> 1.2.3.4
110.120.130.141 -> 10.20.30.41 -> 1.2.3.4
110.120.130.142 -> 10.20.30.42 -> 1.2.3.4


What else should be added to the iptables?

Thanks

---

