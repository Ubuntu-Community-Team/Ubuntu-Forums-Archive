---
title: "Reassociate access point"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by bsell on 2006-06-05
Is there a terminal command I can use to reassociate my wireless access point after the network drops?

---

### Post by rado_london on 2006-06-05
To get it down: sudo ifdown eth0 (depends what your interface is)
To get it up: sudo ifup eth0

Good luck

---

### Post by bsell on 2006-06-05
Cool. It works. 

> Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Nice to see this in my terminal.

---

