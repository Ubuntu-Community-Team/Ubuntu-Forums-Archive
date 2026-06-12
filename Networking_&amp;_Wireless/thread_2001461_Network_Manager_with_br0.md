---
title: "Network Manager with br0"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by houstonbofh on 2012-06-10
For the record, this is on 10.04.

I just set up and started playing with KVM.  I have my network set up with a bridge using DHCP, and all my guests use DHCP as well, so everything just works automagically, and seems to be on the local LAN.

Other than vpns...  This was on my workstation, and I had a LOT of vpns configured in network manager.  Did not even realise that it was gone until I needed it...  So does anyone know a way to get network manager back for vpn control?  A search just brings up a lot of posts from 2008 and no answers...

/etc/network/interfaces

Note, eth1 due to replacement of faulty MB...  New MAC means new interface...

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet manual

# The bridge interface
auto br0
iface br0 inet dhcp
        bridge_ports eth1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
```

---

