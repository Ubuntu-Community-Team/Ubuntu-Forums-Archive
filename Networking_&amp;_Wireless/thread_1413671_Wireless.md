---
title: "Wireless?"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by shadowfax1 on 2010-02-22
Just installed 9.10 on a dell d620 laptop and unlike the last few times I successfully installed it on similar laptops the wireless icon on the top taskbar doesn't recognise any networks.

Could it be the driver on the wireless device is not recognised or maybe an error on the installation?

---

### Post by northd_tech on 2010-02-22
> **shadowfax1 said:**
> 
Could it be the driver on the wireless device is not recognised or maybe an error on the installation?
Absolutely!  (probably the first, esp. with 9.10). :) Can you run the following terminal commands and paste the results here so that we can see the status of your hardware?

```
lspci 

lsmod

lsusb

cat /etc/modules

cat /etc/modules.conf

sudo lshw -C network

ifconfig

iwconfig 
 
sudo iwlist scan 
 
nm-tool
```

---

