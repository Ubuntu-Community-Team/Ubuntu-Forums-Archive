---
title: "Wireless problem on Ubuntu 12.04 LTS (BCM 4313)"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by eternal70 on 2013-04-05
I have an Acer Aspire AOD270 netbook with Broadcom Bcm4313 wireless card. I already installed the broadcom STA driver. But, my wifi can't connect to my netbook. Please help !

---

### Post by praseodym on 2013-04-05
Hi,

please show the output of
```

uname -a
```
Can you connect via cable?

---

### Post by eternal70 on 2013-04-05
I just upgrade to 12.10 and my wifi working. But, it's very laggy.........

---

### Post by praseodym on 2013-04-06
Deactivate the Broadcom-STA driver, clean up the old config and install the missing firmware for the native driver:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware 
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Reboot.

---

### Post by eternal70 on 2013-04-07
Okay, i go back to ubuntu 12.04, but how to clean the old config ?

---

### Post by praseodym on 2013-04-07
There is no need to downgrade, can you connect via cable and use the commands named?

---

### Post by eternal70 on 2013-04-07
Thanks ! it's working ! by the way, ubuntu 12.10 is very laggy because it's netbook. So i re-installed my ubuntu 12.04

---

