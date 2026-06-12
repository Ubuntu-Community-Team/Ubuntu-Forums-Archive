---
title: "How do I enable Jumbo frames on a iface configured as manual?"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by mysteron on 2009-11-19
Hi.

I have an Ata-over-Ethernet system that run on Ubuntu server 9.10 and I need to set Jumbo frames to 5400 for the client. How do I go about doing that as a manual iface configuration does not accept setting the the mtu size according to the manual.

Current conf for the AoE nic is:

```
auto eth2
iface eth2 inet manual
        up ifconfig $IFACE 0.0.0.0 up
        down ifconfig $IFACE down
```

Help will be greatly appreciated :)


Thx,
/mysteron

---

### Post by Yoann Juet on 2009-11-19
Hi,

Just try "ifconfig eth2 mtu 5400" or add "mtu 5400" in your interfaces configuration file.

---

