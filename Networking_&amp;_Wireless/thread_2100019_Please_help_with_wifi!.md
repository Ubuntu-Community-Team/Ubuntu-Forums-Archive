---
title: "Please help with wifi!"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by vikasagartha on 2012-12-31
Ive installed Ubuntu 12.10 on my Dell 1440, and I cant get the wireless to work. Any help? The hardware is BCM 4312. Thanks in advance!

---

### Post by Hadaka on 2012-12-31
Hi, try this...

```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
 
```

---

