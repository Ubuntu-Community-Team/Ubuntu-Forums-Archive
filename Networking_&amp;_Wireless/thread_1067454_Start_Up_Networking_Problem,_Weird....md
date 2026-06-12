---
title: "Start Up Networking Problem, Weird..."
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by sjl127 on 2009-02-11
Say if I have to restart my system, the network manager says I'm connected, but i'm not because I can't ping my router or pull anything up, for that matter.  

In order for me to connect, I have to pull the wire out of the router, wait a few seconds, then plug it back in and the internet then works.

Any suggestions?

---

### Post by sjl127 on 2009-03-15
Solved, what I did to fix this was within my router.  

I had a static IP assigned through network manager.

Then, in the router, I had to, under DHCP Reservation, assign my machines MAC Address the specific IP address I wanted the machine to have.  

Problem solved.

---

