---
title: "interface not running, route still using it"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-04-08
This with the server edition.  On a machine with 2 ethernet ports, which only one is plugged in for the moment to install, but I have configured both interfaces in file "/etc/network/interfaces", I am finding that the routes are not "right".  The cable is pluged in to eth0.  There is a segment route for both eth0 and eth1, same metric (1).  But the eth1 is first.  It is the same subnet on both.  There is just one default route and it has eth1 specified.

No traffic goes through unless I manually change it (obviously only from the console), or switch the ethernet cable over to the eth1 port.

What I want is for there to be routes in effect for interfaces actually working (e.g. RUNNING state), and to not be in effect otherwise (but come back in effect for interfaces that change state to RUNNING).  It should let me have either port connected alone, or both.  I'm not trying to do port bonding ... just have a fallback for loose cables.

Let me add that the order of which way the two segments routes come in, and which interface is used for the default, is random.  Sometimes this way, sometimes the other way (so sometimes it works and sometimes not), after each reboot.

---

