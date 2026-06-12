---
title: "Modifying routes in Ubuntu 9.04"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by ensnare on 2009-09-27
Hi -- What's the best way to add custom routes in Ubuntu 9.04 so they appear and re-appear after restarting the machine and/or networking?  I tried adding a line to /etc/init.d/networking that calls a custom script, and that works, but every few hours the routes just get deleted.  What's the proper way to do this ?

Thanks for your help.

---

### Post by nixscripter on 2009-10-03
Why do the routes get deleted? Is the underlying interface going up or down for some reason?

---

### Post by Iowan on 2009-10-04
Are you getting IP address via DHCP? Sounds like some of the network information is getting "updated".

---

