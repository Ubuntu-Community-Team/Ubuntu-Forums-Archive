---
title: "Help installing drivers for WGUSB-ANT!"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by ad libitum on 2011-03-13
Hi,

I'm pretty much a noob, I just installed Ubuntu on my laptop and now I'm attempting to install drivers for WGUSB-ANT. I downloaded the drivers from here:

[http://www.connectionnc.com/n&c/gama_wireless.php?ID=5](http://www.connectionnc.com/n&c/gama_wireless.php?ID=5)

The readme says I don't need to untar the tarballs or anything, just run a couple of scripts and they will do all the work. I tried the first script, and it doesn't work... not sure if i'm doing something wrong. Anyways I opened the script to see what it does, and this is it:

```

#!/bin/sh

tar -zxvf stack.tar.gz
tar -zxvf drv.tar.gz
cd ieee80211
make clean
make
cd ../rtl8187
make clean
make
cd ..

```I went through the steps with the terminal, untarred the two tarballs, did "make clean", but while doing "make" I got a bunch of errors I don't understand:

```

user@user-HP-Pavilion-dv6000-GA456UA-ABA:~/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211$ make
make -C /lib/modules/2.6.35-27-generic/build M=/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-27-generic'
  CC [M]  /home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.o
In file included from /home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:17:
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211.h: In function ‘ieee80211_priv’:
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211.h:1212: warning: ‘netdev_priv’ is static but used in inline function ‘ieee80211_priv’ which is not static
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:421: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
include/linux/workqueue.h:219: note: expected ‘struct delayed_work *’ but argument is of type ‘struct work_struct *’
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_stop_scan’:
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:495: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
include/linux/workqueue.h:250: note: expected ‘struct delayed_work *’ but argument is of type ‘struct work_struct *’
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_abort’:
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:915: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
include/linux/workqueue.h:219: note: expected ‘struct delayed_work *’ but argument is of type ‘struct work_struct *’
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_stop_protocol_rtl’:
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2120: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
include/linux/workqueue.h:250: note: expected ‘struct delayed_work *’ but argument is of type ‘struct work_struct *’
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: (Each undeclared identifier is reported only once
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: for each function it appears in.)
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2230: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2231: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2232: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2233: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2234: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_free’:
/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2255: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
include/linux/workqueue.h:250: note: expected ‘struct delayed_work *’ but argument is of type ‘struct work_struct *’
make[2]: *** [/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/user/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-27-generic'
make: *** [modules] Error 2
user@user-HP-Pavilion-dv6000-GA456UA-ABA:~/Desktop/driver_wgusb-ant/rtl8187_linux_26.1025.0328.2007/ieee80211$

```Anyone have some advice?

---

### Post by ad libitum on 2011-03-14
bump

while looking for an answer, I found an old thread suggesting the following:

> **jdice said:**
> For those of you who have this same problem or any  other problem related to your wireless connection, make sure to download  file RTL8187L from realtek.com. This should solve any connection  problems you may have.

However, now I've downloaded RTL8187L and can't get the makefile in that to work either...

---

