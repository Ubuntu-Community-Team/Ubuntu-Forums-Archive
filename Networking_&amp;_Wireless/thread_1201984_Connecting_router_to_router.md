---
title: "Connecting router to router"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by jshaw22 on 2009-07-01
Hey guys,
So my roommate has a wireless router upstairs, but the signal is very weak and barely reaches my room downstairs. I have a spare wireless router lying around, and was just wondering if its possible to run an ethernet cable from the upstairs router into my old router, and have downstairs wireless? Supposedly there are some "DHCP?" issues that I have to get resolved first by connecting two routers together... can anybody clarify?
 
Thanks!

---

### Post by MartyBuntu on 2009-07-01
You'll need to shut off DHCP and possibly UPnP on the second router
and connect ethernet cable from a free LAN port on his router to a free LAN port on your router.

---

### Post by Boondoklife on 2009-07-01
This should be very simple, just make sure that the router next to you is giving out a different ip range than the main one and plug the wan port of the one next to you into a lan port on the other.

main router 192.168.0.1/24
your router 192.168.1.1/24

---

