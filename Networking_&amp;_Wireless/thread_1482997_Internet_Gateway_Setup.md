---
title: "Internet Gateway Setup"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by eshwar_andhavarapu on 2010-05-14
Hi,
I am currently running a network with a file server that runs Ubuntu 10.04 Desktop at the moment. DHCP and samba are setup on it for now. Has multiple network cards but we only use the gigabit interface.
Here's what I want to do in the near future. I want to provide internet access to the network via ADSL (no better option currently) So what i'll have is one or more ADSL lines and their corresponding modems (most likely [D-link ones as they are cheap]("http://www.d-link.co.za/dslrouterwired.php")). As i understand it the server will be doing the job of a router.
anyway, point wise here's what i want to be able to do:
1. Have ability to increase capacity/bandwidth with more ADSL line & modem combinations
2. Have user accounts (probably web based setup or any other option) for internet access so that they can be billed per GB.
3. Still be able to share files that are on the local network using local DHCP if possible.

So to an existing network that has files i want to add internet access capability. but users will have to log on so that their usage can be monitored. I have been searching around but maybe the search terms are wrong for what i need accomplished. So could anybody suggest what kind of setup would work?

also, i don't mind upgrading the ubuntu version to the server edition so long as i can use X11 forwarding atleast so that i can do remote monitoring. VNC is too slow, and using nautilus forwarded via X11 to my desktop sorts out most of my needs.

The network provide has suggested maybe using pppoe but i am thinking if there was a welcome page based authentication system then it'd be more easy to monitor?

Please please help?

---

### Post by Iowan on 2010-05-14
Sourceforge.net has several "perfect server" articles - I've lost my shortcut, but there were some "ISP" setups as well. I recently saw an ISP Control Panel project, but didn't investigate.

---

### Post by eshwar_andhavarapu on 2010-05-20
Thank you! let me see. . .

---

### Post by eshwar_andhavarapu on 2010-05-31
something called amazingports seem to solve my needs almost entirely so this is for those that have the same problem!

but now... load balancing 4 ADSL connections. What are my options?

---

