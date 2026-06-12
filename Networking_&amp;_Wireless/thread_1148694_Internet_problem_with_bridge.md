---
title: "Internet problem with bridge ?"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by mirmidon86 on 2009-05-04
Sorry for my Englisch! 
I use Ubuntu 9.04 Desktop and two network cards. I have maded two networks between my Ubuntu pc and my internet provider and my WiFi Router. I have created a neu /etc/network/interfaces file and now the two networks working good but i have internet only on Ubuntu pc. What can I do, to have a internet on the Router too. Need I bridge between this two networks ? If Ja can you tell me, how can I configurate it ?

eth0 -> external 
eth1 -> internal  

Thank you!

---

### Post by mirmidon86 on 2009-05-06
There is no one, who know, how to make it ?

---

### Post by iponeverything on 2009-05-06
add the following lines to your /etc/rc.local

```

iptables -t nat -A POSTROUTING -s  192.168.1.0/24 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

Where 192.168.1.0/24 is *your* internal network.

Then point your internal machines to the ip address of the internal interface as the gateway.

---

