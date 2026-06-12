---
title: "Wireless network association"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by yang on 2010-04-15
I'm trying to associate with a wireless network ("StataCenter"), but for some reason it doesn't come up in `iwlist scan`, even though I can connect to the Internet through it just fine from my Windows laptops.

`iwlist scan` does show some networks with empty ESSIDs, but trying to associate with the strongest-signal such network with `iwconfig wlan0 ap <MAC addr>` doesn't work; iwconfig subsequently just says Not Associated.

Any hints? Let me know if any further information would be useful. FWIW, I've connected to the Internet successfully on other wireless networks from this box.

---

### Post by luthan on 2010-04-15
how about:

iwconfig wlan0 essid StataCenter
is it possible the ap you are trying to connect to is not broadcasting its ssid?

---

