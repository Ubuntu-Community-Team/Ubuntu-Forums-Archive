---
title: "Issues with USB to Ethernet adapter"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by jesin on 2013-03-28
I recently purchased a USB to Ethernet adapter, the chip of the adapter shows up as Davicom DM9601 in dmesg.

It is functioning properly without any additional drivers but the problem is it doesn't work at 100Mbps.

I found a similar issue in the thread - [http://ubuntuforums.org/showthread.php?t=869618](http://ubuntuforums.org/showthread.php?t=869618) but it is too old so the driver file provided there doesn't compile properly.

I even tried the drivers from [http://www.davicom.com.tw/page1.aspx?no=209814](http://www.davicom.com.tw/page1.aspx?no=209814) but they too show the following errors while compiling.

```
jesin@localhost:~/dm9601$ make
make -C /lib/modules/3.2.0-39-generic/build M=/home/jesin/dm9601  
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-39-generic'
  CC [M]  /home/jesin/dm9601/dm9601.o
/home/jesin/dm9601/dm9601.c: In function ‘ctrl_callback’:
/home/jesin/dm9601/dm9601.c:166:4: error: implicit declaration of function ‘warn’ [-Werror=implicit-function-declaration]
/home/jesin/dm9601/dm9601.c: In function ‘write_bulk_callback’:
/home/jesin/dm9601/dm9601.c:527:3: error: implicit declaration of function ‘info’ [-Werror=implicit-function-declaration]
/home/jesin/dm9601/dm9601.c: In function ‘dm9601_tx_timeout’:
/home/jesin/dm9601/dm9601.c:599:32: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c: In function ‘dm9601_start_xmit’:
/home/jesin/dm9601/dm9601.c:615:32: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c: In function ‘dm9601_netdev_stats’:
/home/jesin/dm9601/dm9601.c:656:37: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c: In function ‘init_dm9601’:
/home/jesin/dm9601/dm9601.c:784:55: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c: In function ‘dm9601_open’:
/home/jesin/dm9601/dm9601.c:824:55: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c: In function ‘dm9601_close’:
/home/jesin/dm9601/dm9601.c:864:32: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c: In function ‘dm9601_ioctl’:
/home/jesin/dm9601/dm9601.c:897:32: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c: In function ‘dm9601_set_multicast’:
/home/jesin/dm9601/dm9601.c:933:32: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c:934:33: error: ‘struct net_device’ has no member named ‘mc_list’
/home/jesin/dm9601/dm9601.c:935:17: error: ‘struct net_device’ has no member named ‘mc_count’
/home/jesin/dm9601/dm9601.c:954:44: error: dereferencing pointer to incomplete type
/home/jesin/dm9601/dm9601.c:955:36: error: dereferencing pointer to incomplete type
/home/jesin/dm9601/dm9601.c: In function ‘dm9601_probe’:
/home/jesin/dm9601/dm9601.c:1013:2: error: implicit declaration of function ‘init_MUTEX’ [-Werror=implicit-function-declaration]
/home/jesin/dm9601/dm9601.c:1017:5: error: ‘struct net_device’ has no member named ‘priv’
/home/jesin/dm9601/dm9601.c:1018:5: error: ‘struct net_device’ has no member named ‘open’
/home/jesin/dm9601/dm9601.c:1019:5: error: ‘struct net_device’ has no member named ‘stop’
/home/jesin/dm9601/dm9601.c:1021:5: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/jesin/dm9601/dm9601.c:1022:5: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/jesin/dm9601/dm9601.c:1023:5: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/jesin/dm9601/dm9601.c:1024:5: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/jesin/dm9601/dm9601.c:1025:5: error: ‘struct net_device’ has no member named ‘get_stats’
cc1: some warnings being treated as errors
make[2]: *** [/home/jesin/dm9601/dm9601.o] Error 1
make[1]: *** [_module_/home/jesin/dm9601] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-39-generic'
make: *** [default] Error 2
```

Moreover ethtool always shows "link detected: yes" even if I unplug the cable.

---

### Post by Linfreak on 2013-05-28
Have the same problem...

---

### Post by chili555 on 2013-05-28
> **Linfreak said:**
> Have the same problem...Do you suppose this is part of the answer?```
$ modinfo dm9601
filename:       /lib/modules/3.8.0-22-generic/kernel/drivers/net/usb/dm9601.ko
license:        GPL
description:    Davicom DM9601 [COLOR="#FF0000"]USB 1.1 ethernet devices[/COLOR]
author:         Peter Korsgaard <jacmet@sunsite.dk>
srcversion:     B7F159406EF8DD0D77BDF38
<snip>
```And then: [http://en.wikipedia.org/wiki/Universal_Serial_Bus#USB_1_.28Full_Speed.29](http://en.wikipedia.org/wiki/Universal_Serial_Bus#USB_1_.28Full_Speed.29)> 

Released in January 1996, USB 1 specified data rates of 1.5 Mb/s (Low-Bandwidth) and [COLOR="#FF0000"]12 Mb/s[/COLOR] (Full-Bandwidth).In other words, the device won't do 100 Mbps because it is incapable of transferring data that fast through USB 1.1??

---

