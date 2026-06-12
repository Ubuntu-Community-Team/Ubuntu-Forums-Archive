---
title: "wide-dhcp6-server init script"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by _saiko on 2012-05-07
Using Ubuntu 11.10 and wide-dhcpv6-server version 20080615-11.
I have a need for multiple dhcp6s instances on different interfaces.
Apparently the -p switch (ctlport) has to be configured in order for multiple instances to coexist.
The problem is with the init script that doesn't configure the -p ctlport.

I got the idea from here: [http://canonical.wordpress.com/2008/07/02/ipv6-enabled-home-network-with-openbsd/#comment-107](http://canonical.wordpress.com/2008/07/02/ipv6-enabled-home-network-with-openbsd/#comment-107)

Is there a fix or a suggestion how to modify the init script?


Thanks in advance!

---

### Post by _saiko on 2012-05-07
I modified the init script a bit and it seems to work fine.
Any suggestions are welcome...

Regards,
von Saiko

---

