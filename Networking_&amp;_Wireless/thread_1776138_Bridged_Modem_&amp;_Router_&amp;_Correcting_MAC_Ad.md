---
title: "Bridged Modem &amp; Router &amp; Correcting MAC Addresses"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by FernandoTertiary on 2011-06-05
Hola,

Have Bridged a modem to a router & when running a "ifconfig" within the Terminal, it reflects HWaddr = MAC addr for Bridged Modem.

The problems within that the WAN is determined per the MAC for the Router & not certain how to configure that to enable WAN to be effectual. WAN is unreachable because either: 1) WAN was determined per the MAC from the router & that is not reflected locally via ifconfig, though can still access the internet because the router forwards connection via the modem; or 2) WAN was determined per the MAC from the modem & that is reflected via unseen modem configuration page & the router has proven good just for plugging in multiple machines & not much more because it is not correctly configured yet.

Question: "What is the way to configure the Router to utilize the MAC from the modem, or configure the modem to be totally moot and/or configure connection via the MAC from the router alone?"

Result should be: WAN is reachable per the WAN reflected & determined per the Router & Ports Forwarded via the Router & reachable via the WAN address.

Gracias.

---

