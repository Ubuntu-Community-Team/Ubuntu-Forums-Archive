---
title: "Share Wireless Connection Through Wired?"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by ShiftyEyes on 2009-08-29
I found some older solutions for this, but I'm not sure that they still work with newer Ubuntu versions.

Here's the situation: My friend lives in the apartment building across from me and I pay her a few bucks a month to share her wireless connection. This works for my laptop, but I also have a desktop computer (both are running Ubuntu 9.04) and I would very occasionally like to have internet access on that also. I know I could just get a wireless card, but I thought it would be cool to share the connection from my laptop to my desktop. I've looked at the NetworkManager settings and it certainly looks like there should be a way to do it, but I have no networking knowledge and I haven't been able to figure it out. Is this possible without setting up a full-blown proxy or doing some really complicated configuration?

Thanks!

---

### Post by w00ly on 2009-08-29
I have a similar setup as you but connecting to the laptop doesnt seem the most efficient way (and I dont know how to do it). Thankfully there's already another linux-based solution available: if you have a router handy that can support it, try installing DD WRT then setting it up in repeater mode. You can set it so that the network is bridged or even it's own separate connection (router behind a router, complete with it's own unique ESSID and security...the other router basically becomes your cable modem). I have mine set in repeater mode and it's fantastic...i'm able to connect to any device between the two networks and have them both online seemlessly.

make sure you get the proper version for your router as some routers have less RAM available to work with. Also make sure you get a more recent firmware version, NOT service pack 1 (see the peacock thread at their site)

---

