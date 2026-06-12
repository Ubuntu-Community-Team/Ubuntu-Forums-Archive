---
title: "network nightmares"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by LordMerlin on 2006-06-05
Hi all
 
I wonder if anyone could help me. I'm trying to debug a network, which seems very very unstable. 
 
I have an iBurst modem, which connects via a cross-over cable to a D-Link (DI-624) router (IP: 192.168.0.1)
Then it connects to the Ubuntu 5.10 Server on IP 192.168.0.2. The server (which is the DNS, DHCP, PDC, File & Print server) for the LAN, has a second NIC, 192.168.10.2, which connects to a 24 port HUB, which in turn feeds the LAN. 
 
Once a client PC is logged onto the Domain, all seems well, untill the user logs off. After that, that particular PC can't see the PDC anymore, unless it's rebooted. Even then it sometimes doesn't see the PDC. At the same time if I ping (ping -t 192.168.10.2) the server from another PC, I get a constant reply. I'm also logged in with Putty (which disconnects if there was a network problem)
I also notice while surfing the internet, that it constantly kicks me off (If I'm on any site with logon options, I need to log back on. Sometimes it doesn't even go in. I have to try 10 - 15 times before it access the site. It's almost asif the IP addresses change the whole time, every few minutes. 
 
If I check the logs, I can see a lof of DHCP requests, the whole time, probably because there's 24 PC's on the LAN. Yet, each client keeps the same IP. 
 
Is there any way that I can debug this? Where do I start, what do I look for?

---

### Post by Iowan on 2006-06-05
What is the router doing for you? If all PC's go through the server to get to the router, it would *seem* that the server is (essentially) acting as a router, too.  (otherwise, how do the clients get to the router?) What is the lease-time?  Is the router also trying to act as DHCP server?

---

