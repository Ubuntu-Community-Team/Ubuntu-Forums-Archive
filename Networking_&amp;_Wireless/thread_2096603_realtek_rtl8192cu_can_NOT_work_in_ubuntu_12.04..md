---
title: "realtek rtl8192cu can NOT work in ubuntu 12.04."
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by waterloo2005 on 2012-12-20
The rtl8192cu module within ubuntu 12.04 can only link to wireless router, can not transfer date.
I down the newest driver of rtl8192cu from realtek site and install it. But every time I plug the rtl8192cu wireless card the system dies.
At that time I have blacklist the original module in /etc/modprobe.d/blacklist.conf.

I see the manul of the downloaded driver, it says it only support kernel 2.6.18~2.6.38 and Kernel 3.0.8 .
The kernel of ubuntu 12.04 is 3.2.0.
But someone said he(or she) had used the new driver successfully.

What is the matter ?
Thanks

---

### Post by ahallubuntu on 2012-12-20
Yes, I have built the Realtek driver from Realtek's website in 12.04 (and 12.10).  This is exactly what I did:

[http://ubuntuforums.org/showthread.php?p=12318056#poststop](http://ubuntuforums.org/showthread.php?p=12318056#poststop)

Don't forget the blacklisting.

---

### Post by waterloo2005 on 2012-12-20
> **ahallubuntu said:**
> Yes, I have built the Realtek driver from Realtek's website in 12.04 (and 12.10).  This is exactly what I did:

[http://ubuntuforums.org/showthread.php?p=12318056#poststop](http://ubuntuforums.org/showthread.php?p=12318056#poststop)

Don't forget the blacklisting.

Before I post this page, I had do like that .
But still every time I plug the rtl8192cu card , the system died.

---

### Post by waterloo2005 on 2012-12-21
rtl8192cu driver with kernel in mint14 is OK.(That is I do not install driver 8192cu from realtex site.)
Can I copy that rtl8192cu file to ubuntu12.04?
Thanks

PS. After I try some times, I find driver in mint14 is NOT stable, too.

---

