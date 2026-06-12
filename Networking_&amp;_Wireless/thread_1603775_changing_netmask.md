---
title: "changing netmask"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by k_umalakshmi on 2010-10-23
I tried changing my net mask...but it changes back to what it was as soon as i apply the changes.:confused:....i'm using ubuntu 9.04
the net mask it shows is 255.0.0.0
i guess tht is default

---

### Post by k_umalakshmi on 2010-11-09
no fair....no1 knows abt dis?
i seriously need help here

---

### Post by CharlesA on 2010-11-09
Why do you need to change the netmask?

---

### Post by puppywhacker on 2010-11-09
you have to tell us where you configured your network in the first place, if it comes from dhcp you have to change it in /etc/dhcp/dhclient.conf, or if you configured it in the network-manager and also different than configuring it in /etc/network/interfaces

---

### Post by SeijiSensei on 2010-11-09
255.0.0.0 is a "Class-A" netmask, one that would only make sense if you're on a 10.0.0.0/8 private network or work for Google.

If you're getting your network information from your router using DHCP, then you need to look at the router's settings to see what mask it sends.

---

