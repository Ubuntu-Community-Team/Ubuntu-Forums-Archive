---
title: "VNC Home to Two Machines?"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-02-19
I know how to VNC, forward ports, etc. I use it currently on my main desktop at home.

But what if I want to have two systems VNC-able from home? Since I would have to forward each private IP to the port in the router, when I'm outside of the network and I hit my external IP, how do I ensure I hit Computer A instead of Computer B?

---

### Post by DGortze380 on 2010-02-19
> **Roasted said:**
> I know how to VNC, forward ports, etc. I use it currently on my main desktop at home.

But what if I want to have two systems VNC-able from home? Since I would have to forward each private IP to the port in the router, when I'm outside of the network and I hit my external IP, how do I ensure I hit Computer A instead of Computer B?

Use a non-default port on one machine.

or

configure a VPN Server.

---

### Post by Roasted on 2010-02-19
So I would just have to set up a different port on each machine and define it in the URL?

Machine 1 - Ex.Ter.Nal.IP:5900
Machine 2 - Ex.Ter.Nal.IP:5901

etc... ?

---

### Post by DGortze380 on 2010-02-19
> **Roasted said:**
> So I would just have to set up a different port on each machine and define it in the URL?

Machine 1 - Ex.Ter.Nal.IP:5900
Machine 2 - Ex.Ter.Nal.IP:5901

etc... ?

If you're using port forwarding, you can (typically) only forward one port to one machine.

If you want to access multiple machines at the same IP address, each will need to be accessed by a unique port.

---

### Post by ant2ne on 2010-02-19
incoming traffic on port 11122 on my home router is forwarded to 192.168.1.9:22 on my internal machine. I could also set incoming port 11123 to also come om pm port 22 but to 192.168.1.8:22. Get it? You just need to specify to you're VNC (or ssh in my case) client to use a different port than it is used to.

---

