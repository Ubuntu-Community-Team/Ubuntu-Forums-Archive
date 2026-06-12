---
title: "Services inaccessible after sleep"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by Ranko Kohime on 2011-11-18
I'm having a sporadic issue with Xubuntu 11.04, wherein after putting my laptop to sleep, (which I believe to be the trigger, but not 100% sure), the open ports are no longer accessible from outside the laptop.

Ie., I can ssh into the laptop on a fresh boot, but not after putting it to sleep and waking.  Same goes for all services, web server, Rhythmbox library share, CrashPlan backup server, etc...

These services can be detected by running a port scan on the laptop from the laptop, to any valid address, loopback, LAN IP, WAN IP, etc.

The port scan results from any other computer report "filtered" on all scanned ports.

I'm not running any firewall that I'm aware of.

---

