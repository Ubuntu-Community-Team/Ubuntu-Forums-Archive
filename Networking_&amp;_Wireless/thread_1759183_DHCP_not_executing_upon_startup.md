---
title: "DHCP not executing upon startup"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by wgregori on 2011-05-15
I've been playing with xubuntu. I've changed the file interfaces to use DHCP.  I can bring up networking with the ifup eth0 command ... but upon boot networking is not working.

Any help would be much apprciated.

Thanks,
Wayne

---

### Post by wgregori on 2011-05-15
found the problem... 

need to add

auto eth0

in etc/network/interfaces

Hope this helps someone.

---

