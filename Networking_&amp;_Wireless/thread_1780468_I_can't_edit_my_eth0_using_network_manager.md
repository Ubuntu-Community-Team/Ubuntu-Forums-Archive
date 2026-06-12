---
title: "I can't edit my eth0 using network manager"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by Cumatru on 2011-06-12
In network manager, at Wired, i don't have any connections listed.

For my connection to work, i have to setup ( manually ) the following:

- IP ADDRESS
- GATEWAY
- SUBNET MASK
- DNS SERVERS

How can i do this manually (without network manager ) ?
I remember there is a file somewhere.
I don't know the file nor the syntax.

Later edit:

I've edited /etc/network/interfaces, i have a stable internet connection, but it's SLOW.
I think it resolves the domain names slower than normal.

In my configuration file i have a line where i've specified a nameserver.
First, i've used my ISP DNS, then OPEN DNS, but it's still slow.

Much Later Edit:

I've edited /etc/resolv.conf - now it's working fast

---

### Post by superduperlinuxperson on 2011-06-12
so your problem is solved?

---

### Post by Cumatru on 2011-06-14
Yes. :D:popcorn:

---

