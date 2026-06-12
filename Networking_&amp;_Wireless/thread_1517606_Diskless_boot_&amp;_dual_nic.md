---
title: "Diskless boot &amp; dual nic"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by Valentin_X on 2010-06-25
Hello everyone,

i have a little issue here.

First my configuration:

i have a server with 4 nic's. those are bonded to bond0 (eth0 eth1) and bond1 (eth2 eth3) and i have some nodes (mini cluster installation), let me say 10, (all the same hardware, company etc). these nodes got 2 nic's and they are booting from 1 image on the server thru bond1 and there eth0 PXE boot (server holds the dhcp server). 

now my problem. i wanna ifup the second eth from each node but i do not know the registered name because in udev/rules.d/70-persistent-net.rules are 20 entries now. is there somehow a trick to find the corresponding one or do i have to know the mac's to find out?

cheers
dominik

---

