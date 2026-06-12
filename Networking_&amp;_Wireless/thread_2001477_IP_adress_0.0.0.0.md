---
title: "IP adress 0.0.0.0"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by ecsk on 2012-06-10
I have a Acer Aspire One netbook and running dual boot 12.04 with windows 7.

So far the ubuntu experience is great except one annoying problem with ip address, occasionally when I boot up ubuntu I could not get ip address from my router, IPv4 ip address is 0.0.0.0 in connection information screen.

Reboot the router usually solve this but this has never happened in Windows.  

Has anyone had similar experience, where is the problem, router or ubuntu ?  I'd more tend to say it's ubuntu issue because whenever I boot into Windows it's perfectly fine.

---

### Post by papibe on 2012-06-10
Hi ecsk. Welcome to the forum! :D

Could you post the result of this command when you have the problem?
```
grep -i dhc  /var/log/syslog  /var/log/syslog.1 
```
BTW, you don't have to restart your computer. You can restart your network by open a terminal and running:
```
sudo service network-manager restart
```
Tell us how it goes.
Regards.

---

### Post by ecsk on 2012-06-11
Thanks,

I've tried your suggested command, and got
'grep : syslog: no such file or directory'

By the way, restart computer didn't help, but restart the router usually work.

---

### Post by papibe on 2012-06-11
:oops: Oops.. my fault.

I corrected my post above (the paths were missing).

Regards.

---

