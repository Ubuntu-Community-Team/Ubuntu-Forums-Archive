---
title: "ip address configuration"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by usien on 2009-10-28
how to release and renew the ip address and flush the dns of my ethernet connection on jaunty/karmic (e.g ipconfig in windows)?

---

### Post by Iowan on 2009-10-28
Check the **man dhclient** page.
Dunno if it flushes DNS...

---

### Post by Baelus on 2009-10-28
Would this help?

```
sudo ifdown eth0
sudo ifup eth0
```

From what I can tell, that will restart the network interface.

Then you can get a dhcp address with this:

```
sudo dhclient eth0
```

Is that what you're looking for?

---

