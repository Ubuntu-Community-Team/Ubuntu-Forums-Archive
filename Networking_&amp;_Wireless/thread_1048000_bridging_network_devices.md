---
title: "bridging network devices"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by macx979 on 2009-01-23
hey guys,

my ubuntu computer is connected to a netgear switch and this switch is connected to a external network where I don't have access to. (Gateway server, DNS, etc).
Of course I have internet access from my computer.

Now I plugged in a Linksys WRT54GC into the netgear router to use ist as a wireless access point. The Linksys has the IP 192.168.2.1 and I created a Virtualdevice eth0:1 on my ubuntu machine to communicate with devices within the 192.168.2.0 Network.
The address of eth0 is 140.253.x.x
So far I can access the clients connected to the wireless access point but I also want the wireless clients to have access to the internet. 
Due to the fact, that I don't have access to the external network behind the switch, I think the easiest way would be to bridge the two network devices on my ubuntu machine. 
I tried the bride-utils but it freezes my system everytime I add eth0:1.
Can somebody tell me how I can do the bridgeing or maybe another way how to solve it?

Greetings,
macx

---

