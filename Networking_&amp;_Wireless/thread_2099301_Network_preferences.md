---
title: "Network preferences"
date: 2012-12-29
forum: Networking &amp; Wireless
---

### Post by c-m on 2012-12-29
Ubunutu's network manager is setup by default to use a lan connection first to access the internet. Then if there is no lan connection to look for wifi.

I need to change this default behaviour so that it searches first on wifi.

Any ideas on how to go about this?

---

### Post by praseodym on 2012-12-29
Uncheck "connect automatically" for the LAN connection and tick it for the wifi.

---

### Post by c-m on 2012-12-29
No the problem with that is that then I don't have any lan connectivity.

I want both wifi and lan connected, but I want Ubunutu to use the wifi connection for the Internet, and lan for my local network.

It's so that I can access BTOpenzone (WWAN) which is available in my area, but still have a local private network.

---

### Post by The Cog on 2012-12-29
You could try ignoring routes learned automatcally from the LAN. Then it should only use the default gateway from the wireless network.
See attached picture.

---

