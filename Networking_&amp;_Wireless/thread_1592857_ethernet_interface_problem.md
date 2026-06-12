---
title: "ethernet interface problem"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by michael_rodrigues on 2010-10-11
Hi,

I have a funny problem. Long ago the NIC of my desktop got damaged, so i am using a pci based LAN card.

Now, the thing is when i boot ubuntu (9.10), i used to get ethernet interface -> eth2. But now-a-days sometimes this same ethernet interface (after power up) swaps to eth0. Isn't this (eth2) supposed to be stable.:confused:

I have an external broadband connection that is connected to my LAN card, and to access this, i had to start pppoe. Now everytime this swapping occurs, i have to manually toggle between eth0 and eth2 in the dsl-provider file.

thanks

---

### Post by dineshs on 2010-10-11
what is in /etc/network/interfaces?```
gksudo gedit /etc/network/interfaces
```

---

