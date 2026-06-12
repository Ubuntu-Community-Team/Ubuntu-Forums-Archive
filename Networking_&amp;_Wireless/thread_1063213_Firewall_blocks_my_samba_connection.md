---
title: "Firewall blocks my samba connection"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by ingvald on 2009-02-07
I have just managed to remote control my ubuntu from my vista pc. I just also have installed firestarter in ubuntu.  I have shared a folder on my ubuntu laptop which I can access from my vista laptop when firestarter is off in ubuntu. When I open the shared folder in remote control from vista to ubuntu I can see in the firestarter active connections the following: Source: IP adress vista pc, Destination: ip adress ubuntu pc, Port 445 , Service Microsoft ds. When the firestarter is on I can not access the shared folder from my vista pc. 

I have tried adding the following INBOUND traffic policies: Allow connections from host: "IP adress vista laptop", and allow services for samba Port 137-139 445 For "ip adresss vista laptop"

My outbound policy is like default. I mean Permisse by default , blacklist traffic. I have not defined any connections or services that I have denied in that list. 

It seems like I have misunderstood something, but I don't know what. Appreciate some guidance on my firewall configure problem.

---

### Post by anthropop on 2009-06-04
I have the same problem and google-ing for an answer comes up with little.  I have enabled all ports available in Firestarter.  I also setup wireshark to sniff packets and found some interesting things.  If firestarter is on I do not get ARP packets and my Vista machine can't resolve my IP address.  As soon as I turn off Firestarter I get ARP packets and my Vista machine can browse my shares!

---

