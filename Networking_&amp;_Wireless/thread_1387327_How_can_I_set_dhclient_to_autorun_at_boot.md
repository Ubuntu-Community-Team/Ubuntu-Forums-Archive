---
title: "How can I set dhclient to autorun at boot?"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by Eirinjas on 2010-01-21
Had a problem getting my internet connection working with Ubuntu, but I resolved that issue.  Problem is I still have to manually run dhclient every time Ubuntu boots, because I have no network unless I do.  Is there a script or something that can do this automatically?

---

### Post by Iowan on 2010-01-21
Is your network configured through Network Manager? NM seems to configure network at login instead of boot. If you need the network at boot time, you can (manually) configure */etc/network/interfaces* - an example:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

---

### Post by seyfer on 2013-01-07
Thank's for answer!

---

