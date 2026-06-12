---
title: "vpnc and routing tables"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by patsissons on 2009-04-09
I finally got the vpnc-nortel branch ([http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/](http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel/)) to connect to my vpn the other day, but i had some trouble with the routing tables.

I know enough about routing tables to get things working, i.e. i was able to connect to servers through the vpn, but not enough to actually make things work properly. The main problem was that my DNS servers were acting pretty strange. By strange i mean i could resolve external domains (i.e. google.ca) but not internal vpn domains, even though all dns resolving was going through the vpn (i can only assume since name resolution latency was abnormally high).

I am hoping someone out there knows their routing tables inside and out and can either explain or point me to an explanation of how they actually work.  I would much rather know what i am changing than just adding a static route that kinda works.

What I want to achieve is connect to the VPN and then set up the routing tables such that all traffic going to a set of subnets is tunneled through the VPN (tun0), all other traffic defaults to the main internet device (eth0), which would then hit the local router.

Mostly i would like to know how the kernal actually decides where a packet goes based on the routing table.  If i can understand that, then it should no longer be difficult to write my own routing entries to match the behaviour that I desire.

Thanks.

---

