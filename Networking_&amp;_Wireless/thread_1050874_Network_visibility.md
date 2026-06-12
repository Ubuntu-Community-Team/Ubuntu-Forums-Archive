---
title: "Network visibility"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by qwertymodo on 2009-01-26
I am having an issue with network visibility through a router.  I'm assuming it's just the router, not the OS, because it is the same in both Ubuntu and Vista.  I have a wireless router, and all computers that are connected DIRECTLY TO the router can see each other, and all computers elsewhere on the network can see each other, but the two groups can't see each other.  Basically, I am in a dorm setup, and my desktop is connected directly into the wall plug.  It is able to see all of the computers (practically) in the entire dorm.  I have my router plugged into a second wall plug.  I gave a few people access to my password-protected router so they had wireless access.  These people are the only people visible to my laptop connected to the wireless.  Also, my desktop cannot see my laptop and vice versa.  I CAN plug my desktop into the router and then my two computers can talk, but then I cannot access anybody else in my dorm.  I'm trying to set up a LAN party, and there will be people using both the wired and the wireless connections.  Any ideas how to allow visibility through the router?  It's a Netgear WPN824.

---

### Post by nixscripter on 2009-01-26
I bet your router has NAT separating the two networks -- intentionally hiding them from each other, because if you connect to the internet, that's what you want.

It depends upon exactly what kind of router you have, but what you should look for in the configuration (probably over HTTP) is something to turn it into a network bridge. Additionally, settings for "NAT" should be off, but "DHCP" should still be kept on.

---

