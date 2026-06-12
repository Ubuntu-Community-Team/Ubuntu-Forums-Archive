---
title: "trouble compiling wireless driver"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by alcide nikopole on 2012-11-25
hi I am new to this forum but I have the same problem this is why I jump into the discussion. if this is not appropriate and I should be creating my own separate thread, please let me know.

I run ubuntu 12.04
I have a wifi pci board with chipset ACX 100
I have tried several driver downloads with no luck.
I tried using the  wl1251 driver but it did not work either.

today I tried to compile as per the method provided in the thread and I get error in the execution of the makefile that I cannot resolve.

```

claudie@casimir-claudie:/usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx$ sudo make
make -C /lib/modules/3.2.0-33-generic-pae/build SUBDIRS=`pwd` modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.2.0-33-generic-pae »
  CC [M]  /usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/wlan.o
In file included from include/linux/pci.h:55:0,
                 from /usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/acx_struct.h:1609,
                 from /usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/acx.h:5,
                 from /usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/wlan.c:49:
include/linux/irqreturn.h:11:12: erreur: expected identifier before &#8216;=&#8217; token
include/linux/irqreturn.h:16:24: erreur: conflicting types for &#8216;irqreturn_t&#8217;
/usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/wlan_compat.h:224:14: note: previous declaration of &#8216;irqreturn_t&#8217; was here
In file included from /usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/acx.h:6:0,
                 from /usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/wlan.c:49:
/usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/acx_func.h:109:0: attention : « printk_ratelimited » redéfini [enabled by default]
include/linux/printk.h:244:0: note: ceci est la localisation d'une précédente définition
make[2]: *** [/usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx/wlan.o] Erreur 1
make[1]: *** [_module_/usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.2.0-33-generic-pae »
make: *** [acx.o] Erreur 2
claudie@casimir-claudie:/usr/src/linux-headers-3.2.0-33/drivers/net/wireless/acx$ 

```


FYI the situation I get when loading other drivers using ndiswrapper is always the same:
 
using ndiswrapper -l I see that driver is installed OK
using iwconfig  the wireless interface board is not displayed under wlan0
using lsmod the ndiswrapper is indeed loaded in kernel
using sudo lshw -C network  I can see that the wireless board is 'not reclaimed / assigned ' ( i get this message in french)

if you can help or point me to compile this driver version I can try with this as well.

---

### Post by chili555 on 2012-11-25
> using ndiswrapper -l I see that driver is installed OKIf it says 'driver installed,' but not 'device present' I suspect the inf file is incorrect. Any interesting messages here?```
sudo modprobe ndiswrapper
dmesg | grep ndis
```> I tried using the wl1251 driver but it did not work either.Including the firmware installation?

---

### Post by varunendra on 2012-11-25
First of all, Welcome to the forums nikopole !
Onto your problem now-
> **alcide nikopole said:**
> today I tried to compile as per the method provided in the thread and I get error in the execution of the makefile that I cannot resolve.
Which method ? If you mean the [sourceforge link]("http://sourceforge.net/projects/acx100/") to acx driver, I couldn't compile it myself.

I also believe that ACX100 uses a different chip, and so wl1251 may not be correct driver for it. Accordingly, I would suggest to post a different thread of your own, post in it the results of wireless_script as suggested [here]("http://ubuntuforums.org/showpost.php?p=12350385"), [s]then post back here the link to your thread so we can follow.[/s][COLOR="DarkRed"]*(obsolete now)*[/COLOR]

---

### Post by wildmanne39 on 2012-11-25
Moved to own thread. Please do not jump in on someone else's thread while they are still being helped.
Thanks

---

