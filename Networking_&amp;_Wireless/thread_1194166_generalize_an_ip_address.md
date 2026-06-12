---
title: "generalize an ip address"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by vielmaj on 2009-06-22
I have installed NIS and in hosts.allow i put in

portmap ypserv ypbind : (Here i put a bunch of ip address that start with 128.193.97. and the last digit ranges from 2 to 50.)

Will setting the IP address to 128.193.97.0/16 generalize all of them.

Jason

---

### Post by jhannah on 2009-06-24
You want to specify a network that encompasses all of the addresses you wish to permit. To permit anything from 128.193.97.1 through 128.193.97.255, you would want to use **128.193.97.0/24**. Of course, you could also use wildcards: **127.193.97.***. Check out the man page for hosts.allow for some more examples.

---

