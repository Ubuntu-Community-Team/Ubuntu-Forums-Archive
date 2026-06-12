---
title: "static I.P with wireless"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2009-09-02
Is there a way of having a static I.P when using the wireless interface?
If so how?
Thank you for your time

---

### Post by falconindy on 2009-09-02
Sure, a wireless connection is treated the same way as any other network connection as far as IP addressing goes. 

System > Preferences > Network Connections

Just edit the connection and assign an IP address and DNS servers. You should find these options until IPv4 settings.

Personally, I've always preferred to set a DHCP reservation rather than assigning a static IP on the client side.

---

### Post by methodtwo on 2009-09-02
Why do you prefer DHCP to static addressing?

---

### Post by falconindy on 2009-09-02
It's DHCP, but I get the same IP address every time because the router saves an IP address for my particular MAC address. This makes extra sense on something like a wireless laptop where you might find yourself connecting to other networks. Having the reservation for your home network means you don't have to worry about disabling the static IP and DNS settings when you need DHCP to get established somewhere else.

---

### Post by blackened on 2009-09-03
> **falconindy said:**
> ...This makes extra sense on something like a wireless laptop where you might find yourself connecting to other networks. Having the reservation for your home network means you don't have to worry about disabling the static IP and DNS settings when you need DHCP to get established somewhere else...

Not really necessary considering Network Manager saves settings on a per-network basis and defaults to DHCP for new connections. You could set a static address for your home network in Network Manager and it would still use DHCP for any previously-here-to-for unconnected-to networks.

If you plan on using a static address though, I suggest you use one that falls outside your router's DHCP range so as to avoid addressing conflicts.

---

