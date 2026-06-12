---
title: "what to do, new to this and need wifi"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by morgue13 on 2009-11-24
need to know how to get my wifi working on my netbook its a Asus Eee pc 1000 it has the AzureWave AW-GE780 wireless mini PCI card

---

### Post by Some Penguin on 2009-11-24
It might help if you posted in what way it wasn't working.  There are multiple possible failure modes, such as 
1) kernel does not detect device,
2) device is detected but unusable, such as it's powered down
3) device is actually detected just fine, but you don't know how to associate it with any networks
4) association is configured properly but it's a router problem
5) device is actually not working (hardware failure?)

FWIW, some searching suggests to me that it may be using an Atheros AR2425, which apparently is supported by, say, madwifi.
[http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html](http://www.ubuntugeek.com/new-madwifi-now-supports-ar2425-in-madwifi-trunk-branch.html)
You might want to try WICD and see if that works for you -- if so, then it was mode 3.
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

