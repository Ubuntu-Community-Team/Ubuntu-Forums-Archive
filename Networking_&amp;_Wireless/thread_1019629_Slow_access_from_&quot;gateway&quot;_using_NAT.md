---
title: "Slow access from &quot;gateway&quot; using NAT"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by gibbsj on 2008-12-23
Hello, I setup a gateway using "NAT" with IPTABLES...  From any client computer, the internet is snappy and fast, but from the actual ubuntu server, its slow.  I have 8.10 server edition, everything is connected to a gig network.  If I just access the internet w/o the gateway setup and only one nic in the server, the internet is fast, but the second I setup the IPTABLES and try to update ubuntu or download a package, it downloads at 15 to 30 kb/s.

When the server is standalone not doing any NAT, it gets almost a meg a second.

But like I said, the other computers seam to be fine.

Any ideas?

Thanks

---

### Post by superprash2003 on 2008-12-23
well when connected to the other pcs , multiple machines are sharing the same internet.. so if 2 or more machines are downloading a file etc at that moment , then yes it would result in slow speeds on the gateway too..

---

### Post by gibbsj on 2008-12-23
Yeah, I know that.  I can turn all the other computers off, or whatnot.. makeinng sure we are using no other bandwith.  Cacti also shoes minimal bandwith usage.

---

### Post by gibbsj on 2008-12-23
any ideas?

---

