---
title: "Select sites stall with Jaunty router"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by cthomas975 on 2009-09-11
My company has decided to drop our current web hosting company, mostly because $80/hour to make changes to a site that looks like it should be advertising Rainbow Brite is a bit much.  We've got some excess bandwith, I'm fairly competent with HTML, and we're a pretty small company servicing a client base whose computer experience most involves a cop pecking away at the booking process...so we're not running a web store or anything and our requirements are pretty small.

So, we set up a static IP block through Qwest DSL, and I've split one of the IP's off through an old box with Jaunty server running as a router between the net and our internal network with NAT and a firewall.  I plan next week to install a second box on another static IP from Qwest to run the web site.  So far, everything's working wonderfully, except one thing...

...certain websites will stall before loading, both on the external boxes (71.xxx.xxx.xxx) and the internal network (192.xxx.xxx.xxx) that runs through the router with NAT.  But ONLY certain sites.  Newegg.com, the Iowa Department of Revenue, and Speedtest.net come to mind.

Checked our firewall, of course, but the problem persists even if I clear the iptables and start from scratch with a universal accept policy.  I'm starting to suspect there might be a problem with the way the destination firewalls are set up (ie. dropping packets from unknown IP's or IP's without an associated DNS record).  But, that might just be exhaustion and lack of beer...

Anyone have any random ideas?

---

### Post by cthomas975 on 2009-09-12
Nevermind.  Forgot to disable NAT on the modem, and it seems to have been interfering with certain sites.  Should have had that beer.

---

