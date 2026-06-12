---
title: "Updating Network Driver"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by PostChache on 2009-09-08
I'm having trouble installing the newest driver for my Intel Corporation PRO/Wireless 4965, I got the .tgz but I have no idea how to install it...  Here's the readme [http://intellinuxwireless.org/tar.php?p=iwlwifi&f=README.iwlwifi-4965-ucode&a=iwlwifi-4965-ucode-228.61.2.24.tgz](http://intellinuxwireless.org/tar.php?p=iwlwifi&f=README.iwlwifi-4965-ucode&a=iwlwifi-4965-ucode-228.61.2.24.tgz)

---

### Post by chili555 on 2009-09-08
This appears to be a README to install the latest firmware only, not the entire driver. > cp iwlwifi-4965-2.ucode /lib/firmware
Furthermore, if you do:```
cd /lib/firmware
ls | grep 4965
```You will see that the needed firmware is probably already installed.

---

### Post by PostChache on 2009-09-08
> **chili555 said:**
> This appears to be a README to install the latest firmware only, not the entire driver. Furthermore, if you do:```
cd /lib/firmware
ls | grep 4965
```You will see that the needed firmware is probably already installed.

Oh x3 Silly me Thankyou

---

