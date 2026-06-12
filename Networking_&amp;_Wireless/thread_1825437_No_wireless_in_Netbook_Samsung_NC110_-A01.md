---
title: "No wireless in Netbook Samsung NC110 -A01"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by Arggg on 2011-08-15
Hi. Recently purchased the netbook model Samsung NC110-A01. It seems to work fine in Windows but I decided to install Ubuntu as well an downloaded and installed Ubuntu 10.10 but it seems it does not recognize my wireless modem, there's an exclamation mark on the wireless sign and no network is found. How can I solve this problem? Thanks.

PCI Bridge: 
Intel Corporation N10/ICH Family Express

Network controller: 
Broadcom Corporation BCM4313 802.11b/g LP PHY

Ethernet Controller: 
Realtek Semiconductor RTL 810E/RTL8102E Espress fast ehternet controller

---

### Post by chili555 on 2011-08-15
We need just a bit more information. Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Arggg on 2011-08-15
Hi, after executing that command I get: 

05:00.0 Network controller [0280] : Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01) 

The [0280] shows up in red. 

Thanks!

---

### Post by chili555 on 2011-08-15
Please walk your netbook over to the router and get a wired ethernet connection. Open Synaptic Package Manager and go to Settings > Repositories. Add the repository *Restricted*. Press Reload. Then search for and install *bcmwl-kernel-source*. After it's done, detach the ethernet cable, reboot and enjoy your wireless!

---

### Post by Arggg on 2011-08-17
Thanks a lot chili555, problem solved! :-)

---

### Post by chili555 on 2011-08-17
Glad it's working. Have fun!

---

