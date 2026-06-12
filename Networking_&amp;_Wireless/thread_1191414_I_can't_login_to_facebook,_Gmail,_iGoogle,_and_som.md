---
title: "I can't login to facebook, Gmail, iGoogle, and some forums"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by rboe3 on 2009-06-18
Hi, I just installed Ubuntu 9.04 for a few days.. Everything is working fine except that i can't log in to facebook, iGoogle and some forums. For Gmail, I can login and see my inbox only after i cleared cookies but i cant read the individual email (see attachments).Facebook and iGoogle still not loading after i cleared cookies and cached. I tried opera,ff3, shiretoko (ff 3.5), epiphany, all these browsers have the same problems. I reboot to my windows, everything works perfectly. I tried many solutions such as disabling ipv6, use openDNS, bla bla bla, none of them solve the problems. Are there any way to fix these problems? I liked ubuntu very much and these problems really disappoints me...

New Updates : I tried to login Gmail in basic html, it worked. I can read my email,  but i cant forward or delete my emails. Apparently, i'm having the same problem with yahoo mail. I can read but cant forward or delete my emails. Everything works fine with hotmail. One more thing, i cant log in to facebook!!!!

 

Thanks.. DESPERATELY need your help. GBU.

---

### Post by rboe3 on 2009-06-19
Hi everyone... the problems have been solved by running 
$ sudo ifconfig eth0 mtu 1360
$ sudo ifconfig wlan0 mtu 1360 (for wireless connection)

Source : [http://martinwebster.info/2009/06/18/problems-running-gmail-on-ubuntu/](http://martinwebster.info/2009/06/18/problems-running-gmail-on-ubuntu/)

---

### Post by matborda on 2009-06-19
Hi,

I can't enter Facebook

Following your solution:

```
matborda@matborda-laptop:~$ sudo ifconfig wlan0 mtu 1360
[sudo] password for matborda: 
SIOCSIFMTU: No such device

```

Thanks for the attention!

Mattia

---

### Post by matborda on 2009-06-19
allright

I just made a mistake by writing **wlan0** without knowing hat the real name of my wireless was **eth1** :-)

thanks!

Mattia

---

### Post by rboe3 on 2009-06-20
Dont forget to do it after each reboot or add it to startup apps..

---

### Post by matborda on 2009-06-20
Yeah, the solution is [http://monespaceperso.org/blog-en/2009/02/26/how-to-change-the-default-mtu-of-a-network-card-on-ubuntu/](http://monespaceperso.org/blog-en/2009/02/26/how-to-change-the-default-mtu-of-a-network-card-on-ubuntu/) like posted by alfplayer on this thread [http://ubuntuforums.org/showthread.php?p=6994000#post6994000](http://ubuntuforums.org/showthread.php?p=6994000#post6994000)

ciaooo

Mattia

---

### Post by MURATSPLAT on 2011-01-04
I have a same problem. Thank you  for this solution :) It is working on my ubuntu 10.10

---

### Post by Linicks on 2011-01-04
Fix reported by me too...

[http://ubuntuforums.org/showpost.php?p=10308321&postcount=1](http://ubuntuforums.org/showpost.php?p=10308321&postcount=1)

[http://ubuntuforums.org/showpost.php?p=10292683&postcount=4](http://ubuntuforums.org/showpost.php?p=10292683&postcount=4)

Nick

---

