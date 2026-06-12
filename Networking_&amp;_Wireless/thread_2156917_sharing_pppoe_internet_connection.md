---
title: "sharing pppoe internet connection"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by camper987 on 2013-06-23
Hi,

I'm trying to share my pppoe connection from ppp0.
Using ubuntu 12.04 x64, eth0 ip 10.10.5.1 mask 255.255.255.0

After clearing all rules and enabled ip forward with sudo echo 1 > /proc/sys/net/ipv4/ip_forward I used this linesudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

On a windows7 lan client, ip 10.10.5.2 mask 255.255.255.0 gw 10.10.5.1 dns 8.8.8.8
- only some websites get resolved, for example google.com, facebook and maybe a few more
- only skype connects, yahoo messenger or other software does not work

I'm not sure if I've done something wrong or if there's a problem on my linux machine.
I'll gladly provide more information if needed. Please help.

Thank you.

---

