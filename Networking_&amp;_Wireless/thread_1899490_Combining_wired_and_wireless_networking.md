---
title: "Combining wired and wireless networking"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by linuxhippy on 2011-12-23
I'm not sure this is possible, but I'm hoping it is.  I am running XUbuntu 11.10 on a 64 bit desktop along with a wired eth0 connection (DSL) and a wireless usb adaptor (Belkin G which picks up my 4G internet from a wireless cradlepoint router after converting it to 802.11).  All connections work alone...how can I combine them if they aren't already?

---

### Post by dandnsmith on 2011-12-24
If they both lead to the same connection to the internet/local network, then you have to think about what you'd like to handle on each route, and then set up routing rules to effect it.
Otherwise you're looking to do something a bit exotic, and I'm not sure what it is, but routing is going to be the basis for a solution (but may not be all of it).

---

### Post by linuxhippy on 2011-12-24
each one goes to a different ISP...dsl is verizon and wireless is clear.  I was told that bridging is what this is called but it may result in dropped connections.

---

### Post by dandnsmith on 2011-12-24
I don't think you're talking about bridging!
Never heard of a server called *clear*.
Sounds like you want to do, effectively, channel bonding, only over different services - as I say, you'll have to work out how you allocate the routes, and set the routing accordingly.

---

