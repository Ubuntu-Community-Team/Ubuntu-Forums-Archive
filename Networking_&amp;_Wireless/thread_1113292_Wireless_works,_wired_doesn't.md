---
title: "Wireless works, wired doesn't"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by kravlin on 2009-04-01
Hello,

Sorry if this question's already been asked. I accidentally removed network-manager, and one of my friends reconnected my wireless to get me back online and i re-installed network manager off synaptic. However, now my wireless internet works better than ever but my wired internet doesn't work at all. When i connect a wired connection to it the computer continually connects to the network then disconnects. I'm not sure what's going on or how badly i screwed my system up but i'm hoping to learn what's going on. 

I ran sudo dhclient eth0 and was given this output:
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/MAC address (the actual mac address aka **:**: you get the idea)
Sending on   LPF/eth0/MAC address (same as above)
Sending on   Socket/fallback
DHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping

The network's working. i have a friend sitting playing left 4 dead on a switch connected to it right now next to me. and the computer's not blacklisted.

The final problem is that i'm at a college that doesn't let us have wireless access in our dorms. and i have class. this means i'll be around and able to post anything you want straight from the computer for the next two or so hours but i won't be able to try actually hooking it into anything for at least that. 

If anyone could help i'd be estatic. i've worked for a day with people on the irc channel but nobody seems to know anything to fix it anymore.

All i do know is that a reformat will fix it.

Thanks

---

