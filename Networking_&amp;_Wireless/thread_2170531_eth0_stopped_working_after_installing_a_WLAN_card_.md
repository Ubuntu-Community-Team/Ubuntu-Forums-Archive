---
title: "eth0 stopped working after installing a WLAN card (UBUNTU SERVER 12.04)"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by Niall_Dawson on 2013-08-26
Hi guys!

My first post here on the forums which turns out to be a thread where I require assistance

I have my server downstairs and up till now was currently (still kinda is) relying on a tether through the laptop to access the LAN, which is located upstairs. Since Ive install my WLAN card the ethernet eth0 has stopped working. 

NOTE: Ive installed the **HARDWARE** side of my WLAN card, i cant even install ubuntu-desktop with the apt-get command, therefore I cannot run the drivers from the CD. 

Please Help!

Thanks,
Niall

EDIT: requesting lock or delete please

---

### Post by chili555 on 2013-08-26
Let's see what the ethernet and wireless devices are. Please run and post:```
lspci -nn | grep -e 0200 -e 0280
```If the wireless card is USB, also post:```
lsusb
```

---

### Post by Niall_Dawson on 2013-08-27
Sorry for wasting your time chilli, it turns out it was a problem with the configuration on the laptop tether.

---

### Post by chili555 on 2013-08-27
Glad it's working by whatever means. No worries.

---

