---
title: "Unable to Access Certain Websites"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by siriain on 2009-11-27
Through a local network, all computers except one ubuntu machine can access 1. Adobe.com 2. Icann.org 3. Apache.org 4. Example.com.

The ubuntu machine returns (in firefox): "Though the site seems valid, 
the browser was unable to establish a connection."

Furthermore, when I traceroot those websites using the ubuntu machine, they all return ubuntu.local, and it ends there.
(traceroute to icann.org (192.0.32.7), 30 hops max, 40 byte packets
 1  ubuntu.local (192.168.1.105)  3000.791 ms !H  3000.808 ms !H  3000.814 ms !H).

I've checked the hosts file, and there isn't anything in there, and I have an apache server there so if it was redirected to localhost, I'd probably see the localhost webroot page.

Thanks in advance!

---

