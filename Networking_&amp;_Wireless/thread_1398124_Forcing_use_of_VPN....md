---
title: "Forcing use of VPN..."
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by bokopperud on 2010-02-04
I must admit I'm a bit green with networking, but here goes...

I some times use a VPN-connection to another computer, and uses 'pon' to set-up this connection (no GUI-wizard for me, thank you very much ;) ).   Then I (usually) must delete one of the routes listed in the routing table.

As I understand it; everything I send to eth0 (my network-card) is routed to ppp0 (the connection via VPN), except what's supposed to go to the remote VPN-server... that is routed to eth0 (from ppp0).

My problem is that occasionally I loose connection to the VPN-server ('pon' dies), and the ppp0 device disappears -- also from the routing-table.  This results in all network-traffic being routed directly to eth0 instead.  I don't loose my connection, and here lies the problem...

Is there a way to "lock" the routing-table or do something else that forces the use of ppp0, so that I actually "loose" my network connection when the VPN-link dies?  Of course it must be easy to manually reset it afterward, but I'd like for the connection to remain down until I do...

---

