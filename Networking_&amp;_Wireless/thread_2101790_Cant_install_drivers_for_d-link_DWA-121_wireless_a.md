---
title: "Cant install drivers for d-link DWA-121 wireless adapter ubuntu 12.04 LTS"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by dg91 on 2013-01-05
I tryed this instructons on d-link.com :

support OS and kernel version : LINUX (kernel 2.6.18 ~ 2.6.37) 
install: 
1. tar zxvf rtl8192CU_linux_v2.0.1406.20110309.tar.gz 
2. cd rtl8192CU_linux_v2.0.1406.20110309
3. make
4. su 
5. make install 
6. reboot 

And I get errors on step 3  "3.make"...

---

### Post by 2F4U on 2013-01-05
> support OS and kernel version : LINUX (kernel 2.6.18 ~ 2.6.37) 

The problem may be that Ubuntu 12.04 has a much newer kernel.

---

### Post by dg91 on 2013-01-05
[http://askubuntu.com/questions/227683/errors-in-terminal-trying-to-install-wireless-drivers](http://askubuntu.com/questions/227683/errors-in-terminal-trying-to-install-wireless-drivers)

this guy here says he installed it on 12.4 :P....

if you still think it is a kernel problem what do I do then...beacuse this is relly frustrating....First I cant enable my build in atheros wireless card and now this doesnt work too ;(

Shoud I install some older ubuntu version that have older kernel??

---

### Post by 2F4U on 2013-01-05
Well, maybe, but there are no further details on how he got it working.

---

