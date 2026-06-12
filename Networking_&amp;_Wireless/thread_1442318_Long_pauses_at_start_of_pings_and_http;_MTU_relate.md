---
title: "Long pauses at start of pings and http; MTU related?"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by SalishSea on 2010-03-29
Brand new network, just installed, all ubuntu 9.10 boxes connected to a Dell 2206 dumb gigabit switch, and from there to Dlink router to cable modem. Pretty simple. ISP confirms great link out and inbound, 

However, http requests can sit for 20-30 seconds (sometimes longer), before content returns, same for pings.

Some thought it might be MTU-related.  Any other suggestions?
What is best MTU setting 1500/1492/ ? 

Many thanks,

---

### Post by byStanderone on 2010-03-29
...some mtu defaults:
   Network             MTU (bytes)
   -------------------------------
   16 Mbps Token Ring        17914
   4 Mbps Token Ring          4464
   FDDI                       4352
   Ethernet                   1500
   IEEE 802.3/802.2           1492
   PPPoE (WAN Miniport)       1480
   X.25                        576

---

### Post by SalishSea on 2010-03-29
Gee, now I will seem stupid. I would have thought it was Ethernet (Cat -5 cable, etc.) but how would I distinguish Ethernet from 802.3/802.2...

Blush.

---

### Post by SalishSea on 2010-03-29
Yes, confirmed, ethernet ports on back of D-link router.


If there was a mismatch between the linux box,and the  router, would this give us the problem we are seeing?  Do dumb switches (e.g. Dell 2206) have MTU...

Hmm...

---

### Post by SalishSea on 2010-03-29
The 2216 does not appear to have an MTU, looks like it is set at the O/S.
So, switch is likely not the issue.

---

### Post by arvevans on 2010-03-30
May or may not be an MTU problem.  Dumb hubs (precursor to dumb Ethernet switches) didn't care about MTU settings.

To isolate the problem, start with a ping of your own "localhost" IP address and note the response time.  Then ping the entity closest to your PC and again note the response time.  Then ping the next hardware outward from your pc and also note the response time.  Do this all the way out to say maybe Google's DNS server at 8.8.8.8 to see where the slow-down might be occurring.  *_NOTE:_  Please use "ping -c 3 [entity]" to avoid loading down the network with lots of useless pings and ping responses.*

You may be able to find the IP addresses of network path hardware by doing a "traceroute" (requires sudo) to something far out on the net, like again maybe google.com at 8.8.8.8   Some intermediate entities will respond to a ping, and some will not.

If IP address number based pings show that things are relatively fast responding, then the problem may be related to DNS lookups.  If this is the case then "dig" is your friend because it will tell you how long it takes to do a DNS dip by URL versus how long by IP address number.

Have you set up your local router as a tertiary DNS server?  This places previously resolved DNS-to-IP numbers so they are available locally, but you then need to add that server to your Linux DNS server list.  Put the local DNS cache server first on your DNS server list so that it will try there first. 

Don't trust the ISP's advertised numbers for speed and bandwidth.  Cable modems are on shared bandwidth cables, so if 25 of your neighbors are 
simultaneously downloading videos, you may see slow response times.

---

### Post by SalishSea on 2010-03-30
The problem resolved with the removal of the IP6 entries in /etc/hosts.
MTU is set to 1500.

R

---

