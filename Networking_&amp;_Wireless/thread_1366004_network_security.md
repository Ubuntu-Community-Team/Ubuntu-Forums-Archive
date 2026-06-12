---
title: "network security"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by henhaus on 2009-12-27
Is there a program that will let me track the IP addresses different computers on my network are visiting?

---

### Post by clam2000 on 2009-12-28
If you are on a wireless network then you will be able to listen to the communications of other computers on that network.  You would use a program such as wireshark for this purpose.

If you are on a wired network, with a wire connecting the different computers to a router, then each computer will only be sent the packets that are directed to it, so the only location to monitor all of the network traffic is at the router.  Consumer routers typically don't have an easy way to log activity, so you would either place a computer between the router and the internet which could listen to all external traffic, or you would use a computer as a router which would then handle and be able to record all network traffic.

---

### Post by Lars Noodén on 2009-12-28
[snort](http://www.snort.org/) would be one such program.

---

