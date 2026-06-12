---
title: "Wired Internet connection gets disconnected when trying to upload"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by zkan on 2012-05-09
I have a problem with the wired Internet connection. Every time when I try to upload, I will be disconnected. I wonder if anyone is facing this problem? My current solution is to run the following commands: 
```

sudo ifconfig eth0 down
sudo ifconfig eth0 up

```I'm using Ubuntu 12.04 on Lenovo Y330. Below is my Ethernet card.
```

$ lspci | grep Ethernet
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

```Any help will be appreciated.

---

