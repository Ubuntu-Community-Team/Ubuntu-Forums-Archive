---
title: "Net sharing to windows xp pc"
date: 2006-05-14
forum: Networking &amp; Wireless
---

### Post by sawo on 2006-05-14
I have 2 pc's, a server running ubuntu x64 and and 2nd pc with windows xp. The server has 2 lan cards, eth0 is connected with internet (static ip) and i want to share the connection to the second pc with windows xp. I have configured the lan card settings (ip's, gateway and mask) but don't have internet on the 2nd PC, only lan. What should i type in terminal (iptables ?) to share the connection on the second PC ?

Here are the settings:
eth0 (lan, to share)
inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.252.0
eth1(internet in the server)
inet addr:85.187.137.178  Bcast:85.255.255.255  Mask:255.255.255.224
in windows :
lan
IP Address. . . . . . . . . . . . : 192.168.0.1
Subnet Mask . . . . . . . . . . . : 255.255.252.0
Default Gateway . . . . . . . . . : 192.168.0.2
Thanks.

---

### Post by louis_nichols on 2006-05-14
If I understand well, the IP's have to be the other way round. Your real IP has to belong to eth0, which you say has the internet connection. So eth1 will be the one to have 192.168.0.2. The windows machine is ok, but you'll have to put in the address of the dns server, the same one you have under Ubuntu.

After this, the first thing to do is see if the machines can ping each other. If that happens, it's only a matter of enabling the connection sharing.

As for the rest of the settings, what I did: I just installed firestarter, because you only have to check a box to enable connection sharing. Of course, there is the Linux way, of changing some configuration files, but I find all that pretty hard to remember...

---

