---
title: "Kernel Panic when Avahi adds the wireless with Vmware"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by Carroarmato0 on 2009-02-04
This is a really hateful problem as it forces me to disable avahi in order t use my laptop.

I've already filled the bug here: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/317938]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/317938").

I've got Vmware Workstation installed. Basically what happens is that when my laptop bootsup... vmware's networking stuff loads.... then avahi loads... 

When I log in... Network Manager connects to my wireless network.  As soon as I'm connected, Avahi adds my wireless card (eth1) as an interesting mdns point. a that point my system freezes hard.

The only way to avoid this is disabling avahi totally.

However the weird part is that both alone work great... and once my wireless has connected and enabling avahi afterwards doesn't cause the problem.

Does anyone else have this problem or know a quick way to fix this?

---

