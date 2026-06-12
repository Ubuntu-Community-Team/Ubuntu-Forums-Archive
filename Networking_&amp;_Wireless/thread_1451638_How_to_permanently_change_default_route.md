---
title: "How to permanently change default route?"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by foxmajik on 2010-04-10
Hello,

I have a network setup like this:

1 network card is connected to the internal network to access my NAS and my other devices that I don't want exposed to the outside network.

1 network card is connected to the cable modem so I can browse the web without having to map ports through a router.

Every time I boot I have to execute two commands to set the default route, so that I'll be browsing through the interface connected to the cable modem:

```
gksudo route delete default eth2
gksudo route add default gw 173.164.188.110 eth1
```

**My question:**

How can I put this into a configuration file so I don't have to execute the script each time I boot to set the default gateway?

---

### Post by Xipher on 2010-04-11
Is either interface statically configured? If not I would suggest changing eth2 to be static and if you don't set a default route on it you should be fine. Just make sure you don't use an address inside the DHCP range so you don't end up with another host trying to use the same IP.

---

### Post by Iowan on 2010-04-11
Network Manager has the option to manually configure routes (dunno if it's for default route, though)

---

### Post by foxmajik on 2010-04-11
> **Iowan said:**
> Network Manager has the option to manually configure routes (dunno if it's for default route, though)

My roommate helped me figure it out.

You were right, we had to use Network Manager to configure the default route for each interface and check the box to only use resources available on each device's own network.

---

