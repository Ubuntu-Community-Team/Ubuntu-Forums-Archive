---
title: "Jaunty 64-bit AMD.  Google OK but no further"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by folkmonster on 2009-10-17
I have recently done a clean install on an AMD 64 system.

Eth0 connects, Firefox brings up Google / News /Maps etc.
Clicking on a link results in 'waiting for ...' and then nothing.

I though this must be a DNS problem, so I changed the router settings to use 
open DNS 208.67.222, 208.67.220.220. I added these name servers to dhclient.conf, and
they appear in the resolv.conf file and network manager.

still no joy. The cable router router settings work fine in (32 bit) XP Home!

I can traceroute and ping  [www.bbc.co.uk]("http://www.bbc.co.uk") ok, but links don't work!

I'm Baffled, any ideas?

FM

---

