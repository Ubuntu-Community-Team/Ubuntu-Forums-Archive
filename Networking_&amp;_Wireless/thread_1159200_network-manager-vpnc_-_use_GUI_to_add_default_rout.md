---
title: "network-manager-vpnc - use GUI to add default route to tun0"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by rayjohnterrill@gmail.com on 2009-05-14
i've successfully configured a vpn connection using the network-manager-vpnc gui (on ubuntu 9.04 w/ latest updates), but am having to manually add a route to the newly established tun0 tunnel in order to route the traffic through the vpn.

the route statement is:
```
route add default dev tun0
```

is there a way to execute this route statement automatically, either through the network-manager-vpnc gui, or through a script that the script may be actually executing?

thanks,
-ray

---

