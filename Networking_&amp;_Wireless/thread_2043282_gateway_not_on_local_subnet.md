---
title: "gateway not on local subnet"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by stoneold on 2012-08-16
Hello,
I have the following setup:
Network A: 192.168.10.0/24 (internet gateway 192.168.10.1)
Network B: 10.10.10.0/24 (internet gateway 10.10.10.254)

Both networks are connected via routers on 192.168.10.250 and 10.10.10.250 respectively.

Now I want to use network B's gateway also from network A (1GB/s compared to 3Mbit/s) and that's where the trouble starts.

I considered it to be as simple as just
route add 10.10.10.0/24 gw 192.168.10.250
route add default gw 10.10.10.254
on a box in Network A.
WHile the first routing command works and I can ping 10.10.10.89 from node in A, I cannot set the default route to this external gateway.

While searching in this forum, I came accross [http://ubuntuforums.org/showthread.php?t=1510986&highlight=default+route+external+subnet](http://ubuntuforums.org/showthread.php?t=1510986&highlight=default+route+external+subnet)
At first I thought this would help me but it's a different story as in that post, the gateway is indeed on the same L2 network while I need to route the packets to the default gw before anything else.

Anyone got any clues?
br, so

---

### Post by bakegoodz on 2012-08-18
Sounds like both routers on the same Ethernet network. Right?
When you add a route it allows you to access the IPs in that network range, and points you to the other router to access its subnet. To change the gateway on the computer it needs to have a IP in that gateways subnet. You can put 2 IPs on an interface. I have seen 2 ip configured, but have not done it myself. I Googled 'ubuntu 2 ips same interface' and the first link was [http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html) 
Not sure how you would set which gateway it would connect to the Internet with.

---

