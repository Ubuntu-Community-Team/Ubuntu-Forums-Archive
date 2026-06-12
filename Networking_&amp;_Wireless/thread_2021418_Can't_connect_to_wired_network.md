---
title: "Can't connect to wired network"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by 0m3ns on 2012-07-09
Trying to set up my R3600 machine at work. Ubuntu 12.04. Plugged into LAN socket at desk.

System settings -> Network -> Wired 

The "save" box is always greyed out. I disabled the wireless connection and suddenly I can save. I tried to then configure it manually via IPv4 and used the same settings as my desktop computer except a different IP address. Again, the save box is greyed out.

Settings I tried:

IP address 10.217.237.82
subnet mask 255.255.255.192
default gateway 10.217.237.65
DNS 10.217.237.66

No idea what to put in "search domains", or whether to put anything in the "routes" section. The save button is always greyed out.

Any advice would be welcome.

---

### Post by nothingspecial on 2012-07-11
*Thread moved to **Networking & Wireless**.*

---

### Post by papibe on 2012-07-11
Hi 0m3ns. Welcome to the forums!

Besides the technical aspect of it...

I would not attempt to set an static IP address on a network that I don't manage myself.

The correct thing to do would be to ask the network manager for the correct values.

Just my thoughts.
Regards.

---

### Post by Kirk Schnable on 2012-07-11
Setting a static IP probably won't fix the problem anyway, as I'm guessing your hardware drivers aren't installed.  I'm curious what network card is in this laptop... can you supply us with the output of:

```
lspci
```

While you're at it, it wouldn't hurt to show us which kernel modules are loaded:

```
lsmod
```

Kirk

---

