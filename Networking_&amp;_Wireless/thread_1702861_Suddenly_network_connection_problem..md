---
title: "Suddenly network connection problem."
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by jack lefleur on 2011-03-08
Background-

installing, reinstalling different distros, flavors, on dual-boot (XP), for almost year & 1/2.
Never problems  with accessing internet. Ubuntu varients, Suse, mostly.

3 weeks ago, downloading new Mint ISO with bit-torrent. Did not complete the download.

Soon after this, abberrant behavior began - could no longer connect to internet. After exploring, appears that network is not enabled. Played with configuring / editing - seems to be correct - but still no more connection. 
Several times wiped disk, reinstalled. Same behavior.   AND Live CD works - always goes through (using it right now to access this site).

What condition could/would persist through various reinstallations, but not affect Live CD use?

Also in the network - Linksys router, vonnage phone. But no previous trouble.

I think the problem source is outside of Linux, but not sure.

Me - basically newbie - no shell experience/knowledge. Just enjoy playing / exploring Linux.

---

### Post by HermanAB on 2011-03-08
Howdy,

It sounds like a DHCP problem.  The live CD may be using different defaults, so it manages to work.

What I would try first, is to restart the Linksys router.  If that doesn't clear the problem, manually do a DHCP query on Ubuntu:
$ sudo dhclient eth0

If that doesn't work, see what is the problem with ifconfig and route:
$ sudo ifconfig eth0
$ sudo route

You must have an IP address, a network mask, a default route and a DNS server address, otherwise the network connection cannot work.

Re-installing ubuntu multiple times won't work - you will get the same result every time.

---

### Post by jack lefleur on 2011-03-09
HermanAB - thanks for your reply -

I restarted the router - no change in behavior.

did "sudo dhclient eth0"  

results were :

Listening on LPF/eth0/ MAC for router
Sending on LPF/eth0/ MAC for router
Sending on socket rollback.

DCHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
(same message for 6 more "intervals")

No DCHP offers received
No working leases in persistent data base - sleeping

That's it.

Did "sudo ifconfig" and "suddo route". Both return info to screen. I can type out here if you need the info.

The Ubuntu network config screen shows auto DCHP, with option to set up manual IPv4. I played with the manual option, but wasn't sure what the "Gateway" address was supposed to be.

Your comment about different defaults for the Live CD suggests copying those defaults to the permanent installation?

What do you  think?

---

### Post by jack lefleur on 2011-03-09
**Re: Suddenly network connection problem.** 			
 			 			 		   		 		 		HermanAB - thanks for your reply -

I restarted the router - no change in behavior.

did "sudo dhclient eth0"  

results were :

Listening on LPF/eth0/ MAC for router
Sending on LPF/eth0/ MAC for router
Sending on socket rollback.

DCHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
(same message for 6 more "intervals")

No DCHP offers received
No working leases in persistent data base - sleeping

That's it.

Did "sudo ifconfig" and "suddo route". Both return info to screen. I can type out here if you need the info.

The Ubuntu network config screen shows auto DCHP, with option to set up manual IPv4. I played with the manual option, but wasn't sure what the "Gateway" address was supposed to be.

Your comment about different defaults for the Live CD suggests copying those defaults to the permanent installation?

What do you  think?

---

