---
title: "No wifi on Ubuntu 12.04 - Dell Inspirion"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by msokola on 2012-06-16
Hi,

i just upgrade to 12.04 version and wifi connection doesn't work.
I've got Dell Inspirion 17R - N7010.

```

mateusz@mateusz-Inspiron:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
mateusz@mateusz-Inspiron:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

[http://ubuntuforums.org/showthread.php?t=1997880](http://ubuntuforums.org/showthread.php?t=1997880) - 
It doesn't work. 

Regards,
Matt

PS. Could you help me? Do need something else?

---

### Post by carl4926 on 2012-06-16
Look here
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by msokola on 2012-06-16
> **carl4926 said:**
> Look here
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Problem solved - I just reinstalled package and reboot PC again.

```

sudo apt-get install --reinstall linux-firmware-nonfree
sudo reboot

```

Thanks.

---

