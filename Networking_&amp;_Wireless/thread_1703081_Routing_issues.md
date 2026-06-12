---
title: "Routing issues"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by bcdudley on 2011-03-08
I posted this in the Astaro forums, but I have not gotten any response yet, so I thought I would try here.

I just migrated to the Home version of Astaro. I am replacing my  Sonicwall TZ-170w, however I would like to keep it on as a WAP. I have  the Astaro configured on x.x.1.1 and the Sonicwall on x.x.1.3.

The Sonicwall uses a different subnet for wireless so it is x.x.2.1

I have enabled a route on the Astaro for a gateway route pointing to the x.x.2.0 network at x.x.1.3.

On the Sonicwall, I have created a default route of 0.0.0.0 with a gateway of x.x.1.1 on the Lan interface.

I am able to ping between the Lan and the wireless devices (ex:  192.168.1.5 can ping 192.168.2.205 and vice versa), but I am unable to  ping out to the internet from the wireless devices only (ex:  192.168.2.205 can ping 192.168.1.1, but not 4.2.2.2).  The sonicwall  itself is able to ping the internet.

I have attached a picture of my routes on the Sonicwall for those who are not familiar with them.

 My internal DNS server is 192.168.1.100. I  also use 4.2.2.2 as a backup. I am attaching log files from both the  Astaro and The Sonicwall when I try to ping google.com
 
I added a diagram of my network  for clarity.

I believe this to be something I missed in the routing, but I am unsure.  Could someone please give me some hints as to where I should be  looking.

Thank you,

---

