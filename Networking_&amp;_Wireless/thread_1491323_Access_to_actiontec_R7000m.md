---
title: "Access to actiontec R7000m"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by pkmorrison on 2010-05-23
My release is 10.04, My internal net is 192.168.1.0.
I have an ActionTec R7000M which is essentially a networked
analog modem based with an IP of 192.168.0.1 - it provides a web
interface to set dial properties. Unfortunately, it will only allow changing its ip to 192.168.x.1 - ..1.1 is occupied.

My problem is finding some combination of route, ifconfig commands and parameters to access that ip 192.168.0.1 from
192.168.1.29.

I have tried various combinations of routes, netmasks etc.
First I tried to configure eth0 with netmask of 255.255.254.0
to no avail. Then "route add -net 192.168.0.0 netmask 255.255.255.0 dev eth0" no errors but no response from the actiontec.

Windows was simple - just added a second IP to the existing ethernet card. "properties - tcp/ipv4 - advanced - add ip - 192.168.0.21" No other settings were required.

I dont know how to get the equivalent results in Ubuntu

---

### Post by pkmorrison on 2010-05-23
Nevermind - apologize for the noise!
Just realized that the actiontec has no route back to the 192.168.1.0 network.

---

