---
title: "how do I restart dhcp3 after changing dhcpd.conf?"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by intermentals on 2010-01-17
ver: 9.10

thanks

---

### Post by lloyd_b on 2010-01-17
In a terminal window:```
sudo /etc/init.d/networking restart
```will restart the networking subsystem, including fetching new DHCP settings.

Lloyd B.

---

### Post by Iowan on 2010-01-17
> **lloyd_b said:**
> sudo /etc/init.d/networking restart
That should do it - but you can see if there's an option in */etc/init.d* for something like **dhcp3-server**. (I'd check my server, but it uses **dnsmasq** instead.)

---

### Post by intermentals on 2010-01-17
thank you both that's really helped

---

