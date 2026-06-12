---
title: "Disable on-board wireless at boot?"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by saddlesaur on 2011-05-16
My apologies if this has been posted somewhere else.

I have an issue with my on-board wireless card (powers down after about 5 minutes) so I'm stuck with a USB card. I don't use the on-board card and it causes the system to intermittently hang if it's powered on (once I run ifconfig wlan0 down, the system runs fine). Is there a way to power down the interface (or better yet prevent it from powering on) at boot?

Thanks for any help!

---

### Post by chili555 on 2011-05-16
You can blacklist its driver. For example, if its driver is ath5k, then do:```
sudo su
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
exit
```The interface will be disabled on reboot.

---

### Post by saddlesaur on 2011-05-16
Great, thanks for the help! That looks exactly like what I'm looking for. 

Pardon my ignorance, but any idea of how to determine my driver? When I drop down Network Manager, I see that it's labeled "Intel Centrino Advanced-N 6200".

---

### Post by chili555 on 2011-05-16
> **saddlesaur said:**
> Great, thanks for the help! That looks exactly like what I'm looking for. 

Pardon my ignorance, but any idea of how to determine my driver? When I drop down Network Manager, I see that it's labeled "Intel Centrino Advanced-N 6200".Then your driver is *iwlagn*.

---

### Post by saddlesaur on 2011-05-16
That worked great. Thanks for all your help!

---

