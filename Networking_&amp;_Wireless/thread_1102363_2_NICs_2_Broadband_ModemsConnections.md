---
title: "2 NICs 2 Broadband Modems/Connections"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by dimitriv on 2009-03-21
hi

My intrepid 8.10 is connected to a broadband modem via ethernet talking PPPOE. I'm just wondering if I was to add a second NIC and second broadband modem and using another connection to ISP, how would this effect my internet performance, would it double DL/UL speeds?? or would everything/or individual internet apps just only use one of the two connections? or would it work at all/any other pros or cons to the concept?!

thanks

---

### Post by dimitriv on 2009-03-26
Anybody any comments? thank you

---

### Post by BkkBonanza on 2009-03-26
Maybe. Depends. If your connections go to the same source and load is heavy already in that network (you know due to lots of kids downloading) then you may not see much improvement. But in a general sense, yes - having two connections should double your overall bandwidth. 

But to do it you need to set up some routing otherwise you only see one connection anyway. I used to have a couple connections like this and I'll give you my script here as a reference. Yours would be different but maybe you can get the idea from this one.

192.168.0.10 and 192.168.1.1 were my two gateways. 
One was wireless I picked up from "somewhere" and the other was my LAN.
It worked. Connections don't jump around though - they stay on the interface they were opened on. For torrents, no problem - you have heaps of connections and they tend to spread over both routes.
------------

#!/bin/bash

eth1=`ifconfig  | grep 'inet addr:192.168.1'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`;
echo 'Routing for '$eth1

sudo ifconfig eth0 192.168.0.103

sudo ip route replace 192.168.0.0/24 dev eth0 src 192.168.0.103 table T1
sudo ip route replace default via 192.168.0.10 table T1
sudo ip route replace 127.0.0.0/8 dev lo table T1

sudo ip route replace 192.168.1.0/24 dev eth1 src $eth1 table T2
sudo ip route replace default via 192.168.1.1 table T2
sudo ip route replace 127.0.0.0/8 dev lo table T2

sudo ip rule add from 192.168.0.103 table T1
sudo ip rule add from $eth1 table T2

sudo ip route replace 192.168.0.0/24 dev eth0 src 192.168.0.103
sudo ip route replace 192.168.1.0/24 dev eth1 src $eth1

sudo ip route replace default scope global nexthop via 192.168.0.10 dev eth0 weight 1 nexthop via 192.168.1.1 dev eth1 weight 1

---

### Post by dimitriv on 2009-03-26
Excellent! To hear it's feasible and get the script is a great help. Thank you very much BkkBonaza.

---

### Post by BkkBonanza on 2009-03-26
You're welcome. Note you will need to modify it to suit your network.

The weight values in the last command determine the load balance to some extent. It makes new connections get opened in a 1:1 ratio between interfaces. You could change that if one connection is faster than the other.

Cheers.

---

### Post by dimitriv on 2009-03-27
Great, thanks BkkBonaza.

---

