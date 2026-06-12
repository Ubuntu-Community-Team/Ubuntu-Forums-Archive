---
title: "Strange problem with Transmission and Firewall"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by sanskaras on 2009-01-22
So started a torrent last night, downloaded/uploaded all night fine and all day.  Firewall was script up the entire time with port 51413 open for transmission, everything going good.

Left my computer for a while tonight and come back and transmission was stalled.  After a little messing around I noticed it would only work if I cleared the ip tables, even though I have the port opened and it was working before and iptables -L showed 51413 open.  Also transmission's preferences shows port 51413 closed with the firewall on and off.

I'm using the firewall script from one of the how to threads on here and have

iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 51413 -j ACCEPT
iptables -A TRUSTED -o eth1 -p tcp -m tcp --sport 51413 -j ACCEPT

in it.  

If I run a port scan in network tools it shows port 22, 139, 445, 631, and 51413 as always being open and then random ports such as 41888, 57615, etc opening randomly (Different every scan).

Not quite sure whats going on?

---

