---
title: "Dv6-6c35dx wifi not working"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by Barcasoocer on 2012-05-14
Hi guys
Im running 10.04 on my new Hp dv6-6c35dx and i cant seems to get the wifi on and up and running. i have tired using ndiswrapper and downloading the drivers, but nothing seems to work. 

thanks

---

### Post by wildmanne39 on 2012-05-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

