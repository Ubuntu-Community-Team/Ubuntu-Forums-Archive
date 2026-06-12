---
title: "D-Link/RT2870 Wireless fix"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by brandon88tube on 2009-11-25
Getting it to work without the endless loop of asking for your wireless passphrase:

1. Open up /etc/modprobe.d/blacklist.conf in any text editor you prefer. Make sure you do it as a super user or root (sudo/su)

2. Make a new line at the bottom with this code in it. The first one is necessary, but the other two are just for good measure. You may not need them.
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```

3. Reboot and wait a few minutes as it may take a little bit for your wireless to come up.

---

### Post by brandon88tube on 2009-12-12
If you're getting the error "Error: Driver 'rt2870' is already registered, aborting..." then you probably want to also add this to your blacklist file.```
blacklist rt2870sta
```

---

