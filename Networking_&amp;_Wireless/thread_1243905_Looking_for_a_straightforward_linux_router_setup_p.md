---
title: "Looking for a straightforward linux router setup procedure."
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by michwill on 2009-08-18
Hi All,

I'm looking to replace a default DSL router/modem with a "dummy modem" + "linux-based router" combo.  I'm getting rid of the ZOOM ADSL modem because of its lack of capabilities.  For instance, I can't forward external ports to different internal ports (e.g. forward external port 2000 to internal port 80 -- I have to go 2000 to 2000, 80 to 80, etc.).  Although this can be done by logging into the router via telnet and manipulating the router's proprietary firewall, it's a huge pain.  Also, it, under no circumstances allows for loopback traffic, which I often need so that I may test as though I'm an external user.  So, I'm going linux.

I realize that it will take *some* time to get everything tweaked to my liking, however, I'm looking for the quickest means by which to get a quality, *safe* linux router up and running ASAP.  As stated, the setup will be to revert back to the dummy DSL modem for general ISP connectivity, then flow all traffic through the linux-box, and finally to a gigabit switch for the office:

	[INTERNET]  <--> ["DUMB" DSL MODEM] <--> [UBUNTU BOX (2 NICs) (w/Webmin?)] <--> [24-port gig switch] <--> [OFFICE COMPUTERS]

That said, can anyone provide some concise info on getting a decent (work-in-progress) linux router up and running?  I've seen too many documents and YouTube tutorials to count, but everyone seems to touch on cases I'd likely never even use.


I have the following NEEDS:

	GENERAL SAFETY (against general DOS, SMURFING, etc.), NAT, PORT FORWARDING
	

I have the following WANTS:
	
	WEB PRE-LOAD/CACHING, DNS, WIRELESS SERVING (future -- I can use an access point for now), VPN



FYI, I've currently got an Ubuntu Jaunty box running Webmin, but I'm willing to use whatever so long as it is, at least initially, straightforward.

Best.

---

### Post by timcredible on 2009-08-18
i would just buy a $40 modem with firewall services built-in.  they're easy to manage via browser.

---

### Post by dmizer on 2009-08-19
> **timcredible said:**
> i would just buy a $40 modem with firewall services built-in.  they're easy to manage via browser.

+1 for this.

Hardware firewalls are easier to manage, consume less energy, and are less apt to fail you.

If you MUST have a Linux gateway, I highly suggest something like [Clarkconnect](www.clarkconnect.com), [Untangle](www.untangle.com), or [Smoothwall](http://smoothwall.org). These gateway operating systems are tuned to do what you want, and offer simple solutions with minimal effort.

---

### Post by michwill on 2009-08-19
Thanks for the posts all, but yes, we've been through several hardware routers and none fit our needs.  For those interested, we ended up going with [pfSense]("http://pfsense.org/").  I'll update the thread when we have something interesting to report.  So far it works amazingly well, and, believe it or not, seems to route traffic much faster than the last couple of hardware routers we've had.

Thanks again!

---

### Post by Iowan on 2009-08-20
Until I got DSL, I used a single-floppy Firewall called [FREESCO]("http://www.freesco.org/") on a '486.

---

### Post by michwill on 2009-08-24
For those interested, I ended up going with pfSense.  So far it works amazingly well.  Although it is FreeBSD based, I will post future developments to this thread if anything interesting presents itself.

Feel free to keep the suggestions coming.  I'm sure there's always "something better".

Best.

---

