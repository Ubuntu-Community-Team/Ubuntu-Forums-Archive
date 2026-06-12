---
title: "Give each user their own NIC on server"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by cecure on 2009-11-03
Hi,

I have a server running Ubuntu that has 2 NICs.  My plan is to give each user (user1 and user2) control over one of these NICs.  Therefore, user1's traffic would pass on NIC1 and user2's on NIC2.  I have looked around on Google and on the forums but with no luck.  

I would appreciate any assistance,

Cecure

---

### Post by sedawk on 2009-11-04
Short: No - the users share system resources and you can
regard NICs as system resources, not user resources.

But:
* You can run virtual machines and assign NICs to virtual
  machines. If every User has his own virtual machine ...
* Without going into details about all the trouble getting
  the network setup right you might be able set different
  web proxies for the different users, so all "proxied"
  traffic for user1 uses NIC1, but for user2 it uses NIC2.
  This works at least for web browsing ...

---

