---
title: "BCM4312 problems Ubuntu 13.04"
date: 2013-08-06
forum: Networking &amp; Wireless
---

### Post by suhelpc on 2013-08-06
I have a Dell Inspiron 1464 and installed Ubuntu 13.04 64 bit dual booted with Windows 8. Now the problem is that my wifi connects. I can open just one or two sites say google or so and then there is simple NO INTERNET. I have googled it there seems just no solutions. In the software and update window > additional drivers the hardware is detected and is running an alternate driver. I really love Ubuntu. This is really annoying. Please help me with it.

In windows it's working perfectly. Even in my phone. What is the problem?

Thanks in advance

---

### Post by praseodym on 2013-08-06
You need to install the missing firmware for the low-power chipset (LP-PHY)

```
sudo apt-get install firmware-b43-lpphy-installer 
```
Then uninstall the STA driver completely:
```

sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Reboot.

---

### Post by suhelpc on 2013-08-07
Thank you so much... Now its working perfectly... :d

---

