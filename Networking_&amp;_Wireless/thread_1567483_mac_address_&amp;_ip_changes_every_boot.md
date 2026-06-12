---
title: "mac address &amp; ip changes every boot"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by rebrov on 2010-09-03
i had this issue at backtrack 4 ..even when i put static ip and mac in etc/network/interfaces

even with that it changes but when i put this commands on 

nano etc/init.d/rc.local 
/sbin/ifconfig eth0 hw ether "mac"

when i did that with backtrack 4 it worked and booted with the mac i want 

but with ubuntu 10.04 not working i want specific mac address when i boot it ...any script to make my ip and my mac work at startup ?

---

