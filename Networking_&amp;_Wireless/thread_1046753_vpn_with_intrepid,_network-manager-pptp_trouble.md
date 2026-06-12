---
title: "vpn with intrepid, network-manager-pptp trouble"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by ptscott4 on 2009-01-21
I want to be able to VPN to my university's network using Intrepid. It works fine on my Windows partition.

It seems that many are having trouble with version 0.7 of the network manager, and I can't find the solution anywhere to what seems to be a simple problem.

My university requires that the MRU be set to 1500. This was easy to do with version 0.6 of the network manager, but I can't find an option in 0.7. Is there a way to do this manually?

Alternatively, how could I safely downgrade to the old network manager? I tried this by adding the Hardy repositories and forcing the old version, but that broke it: the nm applet did not show up after a restart, "sudo NetworkManager restart" did nothing noticeable, and "ifconfig" did not show my ethernet connection. I got it back to .7 with a USB drive and now I'm back to where I started.

---

### Post by ptscott4 on 2009-01-23
Does nobody know how to set an MRU in intrepid? It can't be that hard, right?

---

