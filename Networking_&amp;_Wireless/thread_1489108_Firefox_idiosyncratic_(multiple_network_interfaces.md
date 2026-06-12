---
title: "Firefox idiosyncratic (multiple network interfaces)"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by Mick P. on 2010-05-20
This is probably not really an Ubuntu problem however I'm working with a server with Ubuntu installed. 

I have this X server, though normally connecting to the internet via it only happens for maintenance purposes / if no other computer is available. It has two network interfaces. I'm not positive they are configured ideally but they do what they are supposed to. 

One interface accesses the intranet and is permitted to be used for system maintenance and accessing other machines, the other interface is used for internet access whether being accessed from the outside (most common) or using the likes of Firefox to access the internet from the server.

The internet interface has a gateway defined, the intranet one does not. It's probably not secure to assign a gateway to the intranet interface but if you do the traffic gets confused in both directions.

This setup works fine for all programs that access the network/internet, except for poor Firefox. It seems like all other applications are intelligent enough to look for an interface with a gateway, but Firefox just gives up if the first interface (eth0) doesn't have a gateway.

It's possible I reckon since Firefox is desktop centric there is some Ubuntu desktop setting that might govern the preferred interface. Firefox however seems to offer no means of correcting for this behavior. Basically in order to use Firefox to access the net the interfaces have to be temporarily disabled. 

The internet interface can't be set as the first interface because any address it can't handle will end up going out to the internet which blocks the intranet traffic. 

Again I'm not sure the interfaces are setup as well as they could be. 

Thanks for listening,

PS: I think there might be some confusion in general perhaps because the two interfaces networks overlap. The internet interface is on a tiny subnet that overlaps with the intranet so it can access the router. Perhaps network interfaces are not supposed to ever be able to overlap and the gateways are tried as a last ditch, but it would be too much trouble to setup/maintain a second router and I'm not sure if that would work with the internet modem anyway.

---

