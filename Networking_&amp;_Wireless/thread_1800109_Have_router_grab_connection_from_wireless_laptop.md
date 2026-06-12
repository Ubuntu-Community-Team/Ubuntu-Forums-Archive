---
title: "Have router grab connection from wireless laptop?"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by mschersten on 2011-07-08
Maybe this is crazy...

I'm setting up a test lab that has to be away from a wired connection.  The computers don't have wireless cards, but I'm using this laptop that does.  I have a DLink 524 wireless router.  So, since I can't run an ethernet connection into the router, can I have it pick up the connection that my laptop is getting wirelessly, and route it to the other computers via wired connections?

---

### Post by jmoorse on 2011-07-16
Sure, you can do that with internet connection sharing.  Not trivial, but here is the documentation:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I would use a switch hanging off the "server's" nic, then you can hook up all the lab machines.  

Performance will likely be pretty poor though.

---

