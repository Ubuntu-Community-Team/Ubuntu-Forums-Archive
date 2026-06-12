---
title: "Trying to open two ports"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by mpn_1990 on 2010-04-12
I forwarded ports 28900(TCP/UDP) and 5029(UDP) to my linux box for a game. Testing my ports with a website now shows these ports as "connection refused" rather than "timeout" which means the connections are getting to my system but the iptables are blocking them.

But I added 28900 as a test and it still won't accept anything on this port. This is my output of iptables -L

> root@BPC3:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:28900 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:28900 

What do I need to do exactly to add exceptions for 28900 TCP/UDP and 5029 UDP?

---

### Post by gombadi on 2010-04-12
> 
I forwarded ports 28900(TCP/UDP) and 5029(UDP) to my linux box for a game. Testing my ports with a website now shows these ports as "connection refused" rather than "timeout" which means the connections are getting to my system but the iptables are blocking them.


Generally speaking a connection refused means that there is nothing listening on the port. Have you started the programs that listen on those ports?

Your firewall looks like it was already open - it had no reject or drop rules so it is not the firewall stopping the connections.

---

### Post by mpn_1990 on 2010-04-13
> **gombadi said:**
> Generally speaking a connection refused means that there is nothing listening on the port. Have you started the programs that listen on those ports?

Your firewall looks like it was already open - it had no reject or drop rules so it is not the firewall stopping the connections.

I tried testing the port with the game running, and it still says connection refused. No servers show up in my server list in the game.

I did some more iptables exceptions, this time for all the ports, but still no servers show up. Today, for some reason, iptables -L shows no exceptions at all. Is there any guide that shows me how exactly to open the ports? Is there a GUI tool that would make this easier? Is there a way to just get rid of the firewall?

---

