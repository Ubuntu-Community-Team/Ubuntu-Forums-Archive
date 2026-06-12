---
title: "router metering multiliple users"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by NZJohn on 2010-04-29
I have up to 4 homestay students with pcs and need to measure and charge each individually for the downloading or data used by their monthly net activity.
I use both wired and wireless. 
 
How can I do this without being too invasive or putting software in their pcs?
I have to give them 2 gigs per month free but they share my family adsl line and my 4 children also use up the limited broadband available. With 9 of us we use 40 gig plus monthly.
 
If I could measure their use at the router with each host assigned an ip address, bind their mac address and see stats on my pc it would be cool. 
Or could I set up a portal website that allocated and metered my students as they used the net so they could be charged as they used the resource?
 
ANY IDEAS -
ps I have CYBER 54m router that has VIRTUAL SERVER, PORT MAPPING, NAT , ALG, QOS, IP QOS, remote manage. The help files in the router are badly written by someone whose English is imperfect...

---

### Post by P4man on 2010-04-29
well, your router is not likely to provide this functionality. Although it might if  you flash it with dd-wrt or something like [http://www.gargoyle-router.com/](http://www.gargoyle-router.com/) (I think gargoyle does provide per IP bandwidth reports, but you need a router that can run it and with enough memory). You might ask on their forum.

Another approach is setting up a proxy server and doing the monitoring there. Squid should do this.

edit: hmm. proxy might be a problem actually, since you need wifi.

---

### Post by NZJohn on 2010-05-01
i have the students on wifi - do I need a separate computer to act as a server with squid installed?

---

### Post by P4man on 2010-05-01
well.. problem is your students will connect to the access point. From there you need to route them to the squid server, and back to the access point for internet. Assuming the adsl modem and wifi AP are one and the same. 

It should be doable it you let them connect to a wifi router that is not connected to the internet, but to your squid proxy, which then is connected to your adsl router on a second network card. Sounds like a fun project heh.

It doesnt have to be a dedicated pc, but it does need to run 24/7 so its probably best.

---

### Post by NZJohn on 2010-05-01
O:K, so say I use my old dell as a proxy,(transparent or?), it receives site requests from the students wifi pcs via the router, then, whilst it meters their individual use, it redirects their searches out again via the router back thru the modem to the web...
or do I need other equipment as well? Broadband is $100 for 40gig monthly, being the absolute max we can get here in NZ. The students have a free monthly allocation of up to 2 gig each but our 3 students regularly use the full 40gig and complain when the monthly cap is reached early> as some of them are so computer illiterate they dont know how to even run a meter, wont let me touch their pcs or some are too sneaky.
the modem is connected to the router which then shares out to 4 family wired pcs and 3 to 4 student wifi pcs.

---

### Post by P4man on 2010-05-01
> **NZJohn said:**
> O:K, so say I use my old dell as a proxy,(transparent or?), it receives site requests from the students wifi pcs via the router, then, whilst it meters their individual use, it redirects their searches out again via the router back thru the modem to the web...
or do I need other equipment as well?

I dont think so. Maybe a second network card if the modem has a ethernet connection. I wont be able to be much help setting it up though, im not exactly a squid expert, but I dont see why it wouldnt work.

---

