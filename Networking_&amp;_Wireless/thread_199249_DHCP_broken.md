---
title: "DHCP broken"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by nekr0z on 2006-06-18
I gave a try to "whereami" package today, thinking that it could help me set up all these automatic lan/wlan travelling. After coming to conclusion that the thing doesn't work any good (at least fof my configuration), I removed it and installed network-manager back.

From this moment on, DHCP is not detected neither at startup, nor by network-manager, so the network is broken. Doing "sudo dhclient <interface>" helps until next reconnection or reboot.

Nothing of this sort ever happened before I installed whereami. Can there be any workaround for this?

---

### Post by nekr0z on 2006-06-19
bump

---

### Post by nekr0z on 2006-06-19
As I explored a little deeper, this is what I get from /var/log/syslog:

First, dhclient is querying the DHCP server, gets a reply and sets correct IP.
Then, kernel says that there's no IPv6 router present and spoils the complete setup.

Why would kernel ever think I need IPv6?

---

### Post by mips on 2006-06-19
IPv6 is built in to most modern OS's. The problem is not IPv6 but the el cheapo adsl routers on the market.

You can disable IPv6 globally if you like or try upgrading your routers firmware.

---

### Post by nekr0z on 2006-06-19
How would you explain everything working the day before? I didn't change router, nor any setup in it.

---

### Post by mips on 2006-06-19
[QUOTE=nekr0z]How would you explain everything working the day before? I didn't change router, nor any setup in it.[/QUOTE]

I can't as I dunno what depencies were installed or changes made. Might even be due to updates ?

---

### Post by nekr0z on 2006-06-19
I just scanned through all dependencies whereami has. All of them appear to be either already deleted, or components of ubuntu-minimal...

---

