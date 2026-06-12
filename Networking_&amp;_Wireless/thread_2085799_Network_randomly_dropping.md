---
title: "Network randomly dropping"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by tigerstripe40 on 2012-11-19
Ubuntu Desktop version 12.04.01 LTS

The computer is running a Linksys 802.11G wireless network card with an external hi gain antenna. While its got the desktop connection, I am using the machine to serve an apache web page, apache tomcat instance, MySql (local only), Samba (local, only) and a few other things. 

What is going on is that the machine will randomly become unavailable to the outside world. I can be working away in a terminal (via SSH) and then just get a 'connection lost' error. If I give it 5 minutes, it magically returns. 

If I log into the desktop locally, I can browse via Firefox to my hearts content, even when I am unable to remotely connect, or ping the computers private side IP Address. 

I have several other computers on this same network, running various OS's and none of them are having similar problems. 
I've checked the hardware -physically, its fine, no heatsinks full of dust bunnies. 

Is there any sort of network service panic log file located some place that I can grep for any problems? 

-James

---

### Post by ahallubuntu on 2012-11-19
How is your wireless connection set up?  With a router or access point?  How strong is your connection?

Is your computer getting an IP address automatically through DHCP from the router?  How long is the lease time before renewal?  Perhaps you could try using a static IP (choose an IP that is not in the DHCP range of the router, of course, so there will not be an IP address conflict on the network).

---

### Post by tigerstripe40 on 2012-11-19
> **ahallubuntu said:**
> How is your wireless connection set up? With a router or access point? How strong is your connection?
 
Is your computer getting an IP address automatically through DHCP from the router? How long is the lease time before renewal? Perhaps you could try using a static IP (choose an IP that is not in the DHCP range of the router, of course, so there will not be an IP address conflict on the network).
 
I am using a Dlink router. The High gain antenna is probably not warranted as the router is 12' away  (directly above, with a floor/ceiling in between). 
 
The IP is statically assigned as 10.0.0.75, which is outside the range of IP's the router would hand out (10.0.0.200 - 230).  I have a couple of port forarding rules set in the router. -forwarding port 80 to Apache2, port 8080 to Apache tomcat, port 22 for SSH.  I have other computers on the same network that I am forwarding specific ports for things such as remote desktop.

---

