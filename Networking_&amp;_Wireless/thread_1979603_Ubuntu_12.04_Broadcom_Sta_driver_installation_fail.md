---
title: "Ubuntu 12.04 Broadcom Sta driver installation failed"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by stefan2140 on 2012-05-13
I have an HP Pavilion. When upgrading to Ubuntu 12.04, the Broadcom Wireless Card doesn't function properly.

I red the thread [http://ubuntuforums.org/showthread.php?t=1967805](http://ubuntuforums.org/showthread.php?t=1967805)

The first step in the solution is

> lspci -nn | grep 0280

which generates following result:

> 03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

What can be the solution in my case?

Thanks!

---

### Post by chili555 on 2012-05-13
Kwik-n-durty: open a terminal and do:```
sudo su
apt-get remove --purge bcmwl-kernel-source
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo brcmsmac >> /etc/modules
exit
```Reboot and let us have a report.

---

### Post by stefan2140 on 2012-05-14
Thank you for the quick response.
Bad news however... the proposed solution didn't work.

The last line in the /etc/modprobe.d/blacklist.conf is

> blacklist bcma

The last line in de /etc/modules is

> brcmsmac

Thanks for any further suggestions.

---

### Post by chili555 on 2012-05-14
Let's dig deeper. Please post:```
lsmod
rfkill list all
iwconfig
```Thanks.

---

