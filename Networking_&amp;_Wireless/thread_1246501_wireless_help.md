---
title: "wireless help"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by guine on 2009-08-21
I just switched internet providers and with it I now am on a new network and router.  Now that I've switched I am unable to find any wireless networks with my linux computer after having internet working fine on the previous network.  Does anyone know what I need to do to find the new network.

The other question is I am still running an old install(fiesty I think)and I had just recently downloaded the live cd for 9.04 to see if wireless internet would work right off the bat with a new install.  After losing internet from changing routers I booted up the live cd to see if it could find the network and it was able to find the network but not log in.  When I looked through the settings it didn't have some things filled in such as the MAC address.  If I just went ahead and installed the newer version would it figure out the settings and information that it needed during the install and my wireless work once I pick the network and put in the password or would I likely still have to change a bunch of settings first?

---

### Post by Iowan on 2009-08-21
Seems like I had to manually enter some of the information when I installed Jaunty on a laptop. I can't remember if it was wired or wireless that needed MAC address, but the information is available via **lshw -C network**. Some of the other wireless information may also be required (I don't have wireless set up at home yet), so keeping a copy of that information would be a wise move.

---

