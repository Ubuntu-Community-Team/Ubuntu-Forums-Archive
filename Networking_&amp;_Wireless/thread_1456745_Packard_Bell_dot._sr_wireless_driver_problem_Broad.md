---
title: "Packard Bell dot. sr wireless driver problem Broadcom BCM4312 801.11b/g"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by Staneslevski on 2010-04-17
Hi guys. 
I hate Microsoft so I'm trying to load Ubuntu Netbook Remix onto my computer but I'm having trouble getting the wireless internet to work. Wired internet connections find and work automatically but the wireless internet can't find any networks. For the time being I'm running windows as well on a different partition and it's finding the networks fine. I think it's a driver issue. Does anyone know of any fixes?

I've checked out some similar posts and typed 

lshw -c network 


This is what came up:

lshw -c network

WARNING: you should run this program as super-user.

*- network
[INDENT]description: network controller
product: BCM4312 801.11b/g
vendor: Broadcom corporation
physical id: 0
bus info:  pci@0000:01:00.0
version: 01
width: 64 bits
clock: 33MHZ
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:16 memory:5700000-57103fff

[/INDENT]does any of that help? If anyone requires more info just let me know. 

Thanks

---

### Post by bkratz on 2010-04-17
Just saw this today about your card.

[http://ubuntuforums.org/showpost.php?p=9134672&postcount=6](http://ubuntuforums.org/showpost.php?p=9134672&postcount=6)


Also, from this morning

[http://ubuntuforums.org/showthread.php?t=1456480](http://ubuntuforums.org/showthread.php?t=1456480)

---

### Post by Staneslevski on 2010-04-18
And it works! Thank you so much!

---

### Post by bkratz on 2010-04-18
> **Staneslevski said:**
> And it works! Thank you so much!

Could you go to the thread tools and mark the thread [solved] in case it helps someone else?

Also--congratulations!

---

