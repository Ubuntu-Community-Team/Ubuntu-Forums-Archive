---
title: "Gateway with 2 red networks"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by ragrim on 2010-06-21
Hi, im need some help here. What i need to do is setup a gateway with 2 red networks, reason being 1 is my internet connection and the other is my bDSL connection for our IP phone system and i need an IP range of traffic routed to the bDSL rather than internet, i can do this on individual PC's but id like to do it at the firewall level so i dont have to configure each machine on the network.

basically i want all traffic to go to internet except for say 203.x.x.x which i want routed to the bDSL router and let it handle it.

Ive dome some reading and it seems ipcop and smoothwall cant do it so i was hoping with some tricky work maybe i can get ubuntu to do it for me.

Any help would be appreciated.

---

### Post by Iowan on 2010-06-21
To the uninitiated (that'd be me - for one), a "red" network doesn't mean much. **iptables** or **ufw** *might* be able to help...:confused:

---

### Post by Tpolich on 2010-06-21
This is actual really simple to do in linux. I have come across in it a couple of time doing research to make my own linux routing box. 

What you need to play with is the kernel routes. I believe from the command you need for your example is ```
sudo route add -net 203.0.0.0 netmask 255.0.0.0 dev eth0 
```

of course you need to replace eth0 with the name of whatever interface connects to your bDSL router.

This should tell the kernel to reach anything in 203.*.*.* that it need to go out via eth0.

---

