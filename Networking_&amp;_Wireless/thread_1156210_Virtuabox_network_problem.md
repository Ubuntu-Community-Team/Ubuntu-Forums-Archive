---
title: "Virtuabox network problem"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by qwerkus on 2009-05-11
Hello all,

I have the following problem: 

Guest winXP is running under host Ubuntu 8.10 with virtual box. The default installation of Vbox includes basic net access, but I couldn't see my LAN printer with the guest, so that I needed another system.
Thus I setup a tunnel (tap0) bridged to the hosts network interface (eth0) with bridge br0. Than I setup tap0 to be the default network interface in Virtualbox.
Works fine with xp showing up on the LAN, but I have no network access with hosts computer (Ubuntu) anymore. Sounds logic, since the interface is bridged, but what should I change to gain net access with BOTH host and guest machines ?

Thanks for your time,

qwerkus

---

### Post by qwerkus on 2009-05-24
EDIT: In case somebody cares, since 2.2, Virtualbox do not longer require to set up a tunneled bridge. Just open the configuration page of your virtual machine and chose "bridged connection" under "network adapter" - it does the trick...

---

