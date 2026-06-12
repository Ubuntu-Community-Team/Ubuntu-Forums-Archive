---
title: "Upgraded from 8.04 to 8,10 and lost Internet via Webmin"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by ions on 2008-12-10
I use a PC running Ubuntu and Webmin to act as my router.  I upgraded it from 8.04 to 8.10 last night and all clients on the network lost the ability to see the internet but can see the internal network fine.

Any thoughts as to what may have changed in my upgrade?  Need more info?

---

### Post by ions on 2008-12-10
The upgrade to 8.10 appears to have turned off ip_forwarding in 
/proc/sys/net/ipv4/ip_forward

Solved.

Thanks Pio!

---

