---
title: "What does moblock really do?"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by Zilioum on 2009-11-19
I just installed moblock on my ubuntu server I use to download stuff with azureus. The server is connected to a router, as are a few other computers. 

Does moblock also act as a firewall for my other computers in the network as well? (if I started downloading from another pc, or to configure the whitelist)
I just dont really get where moblock (or a firewall in general) puts its "wall". Between the router and the pc the firewall is on, or in front of everything?

Thanks for your answers,
cheers

---

### Post by Wicked-Cricket on 2009-11-22
I'm sure Google would yield some thorough answers for you but here are the basics. Moblock simply blocks connections (incoming and/or outgoing) from specific IP addresses on the local machine only. Blocked connections are those that are blacklisted and whitelisted connections connect as they normally would. Unless you are routing traffic through the machine with MoBlock, other machines on your LAN are unaffected and will continue to connect to all IP addresses normally. You could configure your server to be your firewall/filter for all machines on the network by placing it between your router and modem. This, requires another NIC and some tweaking of the server to make this work. Hope this helps.

---

### Post by Zilioum on 2009-11-22
Helped a lot, thank you very much. Moblock is fine for the moment the way it is, but I'd like to put a real firewall/Ip-blocker in front of all of my computers. I'll try to figure out if theres a way to do this with my Lynksis router running on tomato. Using a pc as firewall would be better, but I would have to put it in my bedroom since my internet connection is there, and I dont really want that.

---

### Post by jre on 2009-11-25
The traffic traverses the iptables chains INPUT, OUTPUT and FORWARD. Check them with "sudo iptables -L -nv". INPUT and OUTPUT are for the machine itself, but FORWARD is for routed traffic.

We are working on pgl (in the git repository at [http://sourceforge.net/projects/peerguardian/](http://sourceforge.net/projects/peerguardian/)) as successor for MoBlock. pgl has support for low memory devices. So you might be able to run it on your linksys.

---

