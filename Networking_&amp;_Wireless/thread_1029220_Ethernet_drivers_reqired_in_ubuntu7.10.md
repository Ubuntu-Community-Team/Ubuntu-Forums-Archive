---
title: "Ethernet drivers reqired in ubuntu7.10"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by syamsajja@ubu on 2009-01-03
I have been installed ubuntu 7.10 in dell studio(1537)laptop.
But i cant get Ethernet drivers.If any one please help me.

---

### Post by albinootje on 2009-01-03
> **syamsajja@ubu said:**
> I have been installed ubuntu 7.10 in dell studio(1537)laptop.
Any specific reason you didn't install Ubuntu 8.04 or 8.10 ?
> 
But i cant get Ethernet drivers.If any one please help me.

Can you please post the output of the following :
```

lshw -c network
lspci
ifconfig -a
route -n
cat /etc/resolv.conf

```

---

### Post by syamsajja@ubu on 2009-01-03
Hi attached is the output can you tell me why it is not available with my laptop.

---

### Post by albinootje on 2009-01-03
Thanks.
Both network devices on your laptop are not recognized.
> 
04:00.0 Network controller: Intel Corporation Unknown device 4232
08:00.0 Ethernet controller: Broadcom Corporation Unknown device 1698 (rev 10)

Can you please try booting from an Ubuntu 8.10 or 8.04 installation cdrom (and use the "live session") and see whether that works better ?

Here's two pages where people mention that it works much better with 8.10 :
[http://www.uluga.ubuntuforums.org/showthread.php?t=1028154](http://www.uluga.ubuntuforums.org/showthread.php?t=1028154)
[http://www.facebook.com/topic.php?uid=2205498133&topic=7009](http://www.facebook.com/topic.php?uid=2205498133&topic=7009)

---

### Post by superprash2003 on 2009-01-03
strange.. it should work .. try reinstalling again

---

