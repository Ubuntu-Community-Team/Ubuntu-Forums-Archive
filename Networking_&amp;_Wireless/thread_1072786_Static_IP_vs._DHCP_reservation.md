---
title: "Static IP vs. DHCP reservation"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by njschwartz on 2009-02-17
So I accidently fried my Buffallo Airstation by plugging in the wrong power adapter which sucked.  Sadly I cannot buy a replacement Buffallo router from a store and I needed a router now so I purchased the D-Link DIR-655 because it get such great reviews.  Anyway,  I am now having issues forwarding web server traffic to my Ubuntu server.  My server has a static ip address of 192.168.11.200.  On with my old Buffallo router, running DD-WRT by the way, I simply forwarded port 80 to 192.168.11.200 and all worked perfectly.  With the new router something doesn't seem to be working correctly.  I can ping the server, but web traffic seems to get lost somehow.  I am assuming it is a forwarding issue.  Would setting my server to use DHCP and then reserving the IP address in the router do anything for me?  I cannot test it at the moment because I am at work. I really don't understand what the point of DHCP reservations is or how it is any different than simply using a static ip.  Any advice or suggestions would be appreciated.

---

### Post by Iowan on 2009-02-17
> **njschwartz said:**
>  Would setting my server to use DHCP and then reserving the IP address in the router do anything for me?*Probably* not.  If one port-forward won't go through, another *probably* won't either.  DHCP reservations (AKA static leases) lets you manage your addresses from a single machine - instead of configuring each machine.  Static leases are outside the address pool - otherwise, the server might assign the address to another machine - nothing good happens then. One potential drawback is that if your DHCP server fails, the network fails with it.

I'm not familiar with D-Link routers, so I'm unable to advise what to change to make port-forwarding work (sorry).

---

### Post by njschwartz on 2009-02-17
Yea~I was thinking the same thing.  I just cannot figure out where the problem is.  From outside the network I can type in the web address or IP address and it connects but then times out I assume because the information is not being correctly forwarded to the webserver.  If I ping the external IP it just times out.  Internally I can ping the web server at it works as expected.  Everything is setup the way the old router was so I am at a loss what the difference is.

---

