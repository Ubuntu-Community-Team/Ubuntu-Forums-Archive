---
title: "Wireless not working after update to kernel 3.8.6"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by eternal70 on 2013-04-07
I have ubuntu 12.04 and before update kernel, the wifi is working. After update to kernel 3.8.6 the wifi is connected, but can't open the internet. Please help ! Which is the latest kernel that work with my wifi card. I have broadcom bcm 4313. I use the brcmsmac driver

---

### Post by chili555 on 2013-04-07
How and where did you upgrade the kernel and did you include linux-image-**extras**?

---

### Post by praseodym on 2013-04-07
BCM4313 needs the firmware for the respective module:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware
```

---

### Post by chili555 on 2013-04-07
> **praseodym said:**
> BCM4313 needs the firmware for the respective module:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware
```I wasn't aware that brcmsmac required firmware.

---

### Post by eternal70 on 2013-04-07
I update my kernel from upubuntu.com, do you know the latest linux kernel that works with b4313 ?

---

### Post by chili555 on 2013-04-07
> do you know the latest linux kernel that works with b4313 ? As far as i know, every kernel since 3.0.xx works fine. Let's identify your device first:```
lspci -nnd 14e4:
```And let's look at some diagnostics:```
dmesg | grep wlan
```

---

### Post by eternal70 on 2013-04-08
It's strange, i reinstalled my ubuntu, and do what i do before. And then, it's working with the old driver

---

### Post by chili555 on 2013-04-08
> **eternal70 said:**
> It's strange, i reinstalled my ubuntu, and do what i do before. And then, it's working with the old driverI'll take it! I'm glad it's working by whatever method. Have fun and post back if we can help you again.

---

### Post by eternal70 on 2013-04-09
Thanks

---

