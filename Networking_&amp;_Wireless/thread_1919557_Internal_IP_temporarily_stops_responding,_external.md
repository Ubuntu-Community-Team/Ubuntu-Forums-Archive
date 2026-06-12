---
title: "Internal IP temporarily stops responding, external IP works fine"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by hvanzile on 2012-02-03
Hi there,

I have a strange problem and I can't seem to find anything about it.  My Ubuntu 11.10 install is connected via wireless, with a static IP to my router, and from time to time it stops responding to its internal IP.  This happens regularly, but is intermittent - it fixes itself.  

When this happens, I can't ping the IP or access the box via HTTP, SSH or samba.  Here's the odd part, though, while this is going on, I can still access it via HTTP using my external IP (Router is forwarding port 80 to the internal IP).  I haven't tried the other services, since I don't have them exposed through the router.

I don't know where to start with this one.  UFW?  Network Manager?  Any help would be greatly appreciated.

---

