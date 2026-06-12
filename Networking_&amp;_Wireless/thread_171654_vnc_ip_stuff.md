---
title: "vnc ip stuff"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by iamsobored0056 on 2006-05-07
hi guys, its my first post here.  i am trying to set up a remote desktop by using vnc.  i don't really understand how all this port stuff works, and i was wondering if anyone could explain to me.  at my house, there there are two wireless routers.  there is one on one side of the house, and another router connected to the first one placed at the other side of the house.  my computer uses the second one.  can someone help me configure this?  im completely lost.  the router model is d-link 614.  thanks

---

### Post by joft on 2006-05-08
Hi,

I think you need to tell us what you really want to do, which means: more details.

The second AP is connected to the first one (by cable?), your computer connects to the second one. Is this all on the same IP subnet? So only one of them is acting as a DHCP server or do both have a DHCP server running (and providing IPs for two different subnets)?

The VNC server runs on your laptop (which is attached at the second AP). So, you want to connect to that server from a computer attached to the first AP, right?
If the PC in question is also attached to the second AP, you don't have problems starting a VNC client and connecting to it your VNC server (on your laptop), right?

---

