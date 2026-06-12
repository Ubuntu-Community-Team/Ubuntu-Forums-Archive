---
title: "NDAS issue on ubuntu 8.10"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by dir32jd on 2009-02-25
I am able to register and connect to my ndas devices separately (i have two of them). However, whenever I try to register and enable them both, I get an odd result. When I enter the "Blkid" command, both primary partitions of both devices get assigned the same UUID. So when I mount the two paritions, it's actually pointing to the first partition of the first device. The second device doesn't get mounted.
My workaround at the moment is I can only connect to one device at one time ... I have to deregister one device in order to connect to the other device ... really.

Other than that, the driver works great. Anybody have any ideas what I might be doing wrong?

---

