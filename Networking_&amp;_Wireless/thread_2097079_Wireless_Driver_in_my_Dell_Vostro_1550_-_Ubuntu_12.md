---
title: "Wireless Driver in my Dell Vostro 1550 - Ubuntu 12.10 - Broadcom BCM43142"
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by kanishkdudeja on 2012-12-22
How do i install the wireless driver in my dell vostro 1550? i use Ubuntu 12.10.

---

### Post by kanishkdudeja on 2012-12-22
Can no one help?

---

### Post by mörgæs on 2012-12-22
Please don't bump a thread.

If you feel you get not enough response it might be because the thread is in the wrong forum. Moved to Networking and Wireless.

---

### Post by FerroPower on 2012-12-22
go to System Settings > then select Additional Drivers option you will be notified to activate the appropriate drivers for your wireless card.
 
After activation reboot. you will find the wireless option in Network Manager.

I hope it helps ...

---

### Post by Pjotr123 on 2012-12-22
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by macleapa on 2013-01-31
> **FerroPower said:**
> go to System Settings > then select Additional Drivers option you will be notified to activate the appropriate drivers for your wireless card.
 
After activation reboot. you will find the wireless option in Network Manager.

I hope it helps ...
Thanks for the info.

for Lubuntu: System Tools: Lubuntu Software Centre: look in the System category for Additional Drivers.

---

### Post by jsgrrc on 2013-02-07
I am also having dell-vostro1550 with ubuntu 12.10. I tried many ways and the road map too. But none of those working. Please assist me on this. One more additional info : Bluetooth is working fine. wifi only not working.

---

### Post by Hadaka on 2013-02-07
Hi, please post the output of..

```
lspci -nnk | grep 0280 
```
thanks.

---

### Post by jsgrrc on 2013-02-08
> **Hadaka said:**
> Hi, please post the output of..

```
lspci -nnk | grep 0280 
```thanks.

Please find the output below,

09:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)


Thanks in advance!!

---

### Post by jsgrrc on 2013-02-08
I saw: [URL="http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560"]dropbox driver
[/URL] 
 And had the same issue, that is not solved in that topic:
  I tried with Ubuntu 12.10, but got dpkg errors:

> 
DKMS make.log for wireless-bcm43142-oneiric-dkms-6.20.55.19~bdcom0602.0400.1000.0400 for kernel 3.5.0-17-generic (i686)
Fri Feb  8 22:08:52 IST 2013
make: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/built-in.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_linux.o
/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_linux.c:50:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[1]: *** [/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/wireless-bcm43142-oneiric-dkms/6.20.55.19~bdcom0602.0400.1000.0400/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'

  Am I missing anything?


  Is driver for i386 bad and i must install x64 ubuntu, or what?

---

### Post by Hadaka on 2013-02-08
Hi, it is doubtfull you will be able to load the correct
driver for your card...4365...becuse you currently are running
32 bit, this driver seems to only work with 64 bit systems, If
you computer is able, i would suggest reloading the Ubuntu
os choosing the 64 bit option.

[http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923](http://askubuntu.com/questions/215890/dell-inspiron-5720-wifi-broadcom-bcm43142-ubuntu-12-10/215923#215923)

---

