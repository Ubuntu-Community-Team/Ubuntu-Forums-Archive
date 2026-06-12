---
title: "multiple IPs single hostname in /etc/hosts"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by guvnr on 2009-12-18
Perhaps a silly q but, is it correct, please, to have hostname contradictions like this?  In /etc/hosts file ...

12.34.56.1   HOSTNAME
12.34.56.2   HOSTNAME

..There are the localhost and IPv6 entries in there too.

Would this have any consequences with, say, using the box as an openVPN svr (about to set that up).

Seems to me the only thing I couldn't do would be to do, say "ssh bloke@HOSTNAME" from somewhere else, but using the IP instead is no big deal.

Network tests fine.  So far.

One IP is for eth0, other for ra0.  Er, I guess I don't need both though.  Delete one maybe?

Machine is 9.10 64bit Desktop.

---

