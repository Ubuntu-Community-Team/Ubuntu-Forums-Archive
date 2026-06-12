---
title: "DHCP and STATIC IP in 1 NIC?"
date: 2005-12-29
forum: Networking &amp; Wireless
---

### Post by kenweill on 2005-12-29
Is it possible to have both DHCP and STATIC ip address in 1 NIC?

The DHCP will be used for internet connection. The STATIC ip will be used to connect to the LAN.

Is that possible?

---

### Post by Koybe on 2005-12-29
You can set two IP to the same NIc using a virtual NIC. For example, if you're on eth0, using dhcp for your internet connexion you can set another IP to eth0.

```
sudo ifconfig eth0:1 192.168.1.10 
```

---

### Post by kenweill on 2005-12-29
Can I share the internet connection from DHCP to my LAN?
I mean using proxy.

---

### Post by Koybe on 2005-12-29
No you can't do this without have two NIC on your PC. Or just buy a little router, it's low cost material now and it's really the best way.

---

