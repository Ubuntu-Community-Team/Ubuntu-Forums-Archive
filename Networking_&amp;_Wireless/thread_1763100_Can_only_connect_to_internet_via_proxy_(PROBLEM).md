---
title: "Can only connect to internet via proxy (PROBLEM)"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by Knowsnothing on 2011-05-20
After attempting to use a VPN client (Astrill), I can no longer access the internet through my Ubuntu installation.

  Its not a network issue, as on the same Wifi and wired network both  my Windows install and other comps can connect and use the network.

  I can, however, connect to sites via a proxy client running through  WINE.  I've tried changing proxy settings, but to no avail.  I'm really  at a loss and have no idea what I should do.

  This is the output when I run route in the Terminal:
  Kernel IP routing table 
Destination     Gateway         Genmask                  Flags Metric Ref    Use Iface 
10.100.5.0             *                    255.255.255.0       U            2             0          0    wlan0 
link-local               *                  255.255.0.0                  U          1000       0           0    wlan0 
default            10.100.5.254    0.0.0.0                    UG           0            0            0 wlan0

This has been cross-posted here and on Ask Ubuntu:  [http://askubuntu.com/questions/43864/can-connect-to-internet-only-via-proxy](http://askubuntu.com/questions/43864/can-connect-to-internet-only-via-proxy)

---

