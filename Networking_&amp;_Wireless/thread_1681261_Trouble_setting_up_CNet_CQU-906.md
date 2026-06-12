---
title: "Trouble setting up CNet CQU-906"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by Haleck on 2011-02-03
First off, I am very new to Ubuntu, and to Open Source OS in general.  I think the term used around here is 'green'?  ;)

I was recently given an old PC that was barely chugging along in Windows XP, so I decided to try a less CPU intensive OS.  I installed Ubuntu 10.10, and have been trying to get it connected to my wireless connection ever since.

Before making the switch, I bought the CQU-906 USB Dongle; it worked flawlessly with XP, and since the packaging said that it had driver support for Linux, I assumed it would be a simple install--I was wrong.

After contacting CNet, I was given a link to a driver from Realtek which included an installation guide.  I've decompressed it and used the make command, which seems to work fine.  Next, I'm told to type './clean', which results in 6 errors:

ERROR: Module r8192s_usb does not exist in /proc/modules
ERROR: Module ieee80211_rsl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep does not exist in /proc/modules
ERROR: Module ieee80211_crypt does not exist in /proc/modules

The next command, 'insmod 8712u.ko', returns '-1 Operation not permitted'.

I realize that this cry for help is more than a little disjointed.  Feel free to ask any questions if you need more information!

---

### Post by Haleck on 2011-02-04
In case it helps, the chipset I was told to download is RTL8188SU.

---

### Post by volyrkr on 2011-03-19
Yep,
[FONT=Courier New]0bda:8176 Realtek Semiconductor Corp.[/FONT]
Had the same problem
I've found this among many other drivers on Realtek.
I've modified it to compile and work with 2.6.38 kernel (they removed the macro template for using semaphores as mutexes).
Works now for me.

---

### Post by volyrkr on 2011-03-19
I'm by the way on gentoo, not using buntu, but since this post is like in top 5 in google for "linux CQU-906" I decided to write here in case people like me in trouble.

---

### Post by EngineerBill on 2011-03-24
Yet another one having problems with the CQU-906 and Ubuntu. I have older desktops at non-profit organization running Ubuntu 8.04LTS desktop. Can't upgrade them any further. Kernal is 2.6.24-26-generic. Using your provided file gives error "linux/semiphore.h not file" and quits. I have a feeling it is something to do with the headers are different in the older kernal?

Here's the compile (2nd time so you don't see all of the original compile that was successful):

norcalems@Linux001:~/_my_rtl8192CU_linux_v2.0.1324.20110126$ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.24-26-generic/build M=/home/norcalems/_my_rtl8192CU_linux_v2.0.1324.20110126  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-26-generic'
  CC [M]  /home/norcalems/_my_rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.o
/home/norcalems/_my_rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.c:301:29: error: linux/semaphore.h: No such file or directory
make[2]: *** [/home/norcalems/_my_rtl8192CU_linux_v2.0.1324.20110126/os_dep/osdep_service.o] Error 1
make[1]: *** [_module_/home/norcalems/_my_rtl8192CU_linux_v2.0.1324.20110126] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-26-generic'
make: *** [modules] Error 2

If you happen to check back and know a quick fix, much appreciated. Thanks for posting.


> **volyrkr said:**
> Yep,
[FONT=Courier New]0bda:8176 Realtek Semiconductor Corp.[/FONT]
Had the same problem
I've found this among many other drivers on Realtek.
I've modified it to compile and work with 2.6.38 kernel (they removed the macro template for using semaphores as mutexes).
Works now for me.

---

### Post by volyrkr on 2011-03-24
This is the original (attached) that I've found of their ftp site among dozen of others.
Did you try it before?
Maybe it'll build&work with 2.6.24.

---

### Post by cverzyl on 2011-03-28
I tried several Realtek drivers with no success, but the CQU-906 works great using ndiswrapper (ndisgtk) which is listed in the Ubuntu software under "windows wireless drivers".  You just install that, then when you configure your connection, it asks for the ".inf" file which is on the CD that comes with the CQU-906.  There are drivers for XP, Vista, etc. on the CD and they all seem to work with Ubuntu.

---

### Post by Gabler on 2011-05-15
I've installed a driver onto my machine using ndisgtk and it recognizes that it is plugged in. However, I still can't access wireless internet at all. Is there something I'm missing? D:

---

### Post by nito2721 on 2012-02-25
Try this. Worked for me. 

[http://forums.linuxmint.com/viewtopic.php?f=53&t=94495&start=0](http://forums.linuxmint.com/viewtopic.php?f=53&t=94495&start=0)

---

