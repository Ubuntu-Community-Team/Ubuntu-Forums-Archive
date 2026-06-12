---
title: "USB Wireless N  adaptor driver issues"
date: 2010-04-13
forum: Networking &amp; Wireless
---

### Post by dezgo on 2010-04-13
Hey,

I'm very new to Ubuntu and Linux in general. I just bought a USB Wireless network adaptor hoping it would just work when I plugged it into my ubuntu box, but it didn't.

There were drivers on the disk for linux which I have tried to use but can't get them working. It appears I have to compile them, but when I do I get the following:

(from [http://paste.ubuntu.com/413635/](http://paste.ubuntu.com/413635/))

derek@backup-desktop:~/Downloads/rtl8192su_linux_2.6.0002.0708.2009$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.o
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c: In function ‘rtl819x_set_mcast_register’:
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c:4338: warning: unused variable ‘dev’
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c:11333: error: ‘struct net_device’ has no member named ‘open’
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c:11334: error: ‘struct net_device’ has no member named ‘stop’
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c:11335: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c:11336: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c:11337: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c:11338: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.c:11339: error: ‘struct net_device’ has no member named ‘get_stats’
make[2]: *** [/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/derek/Downloads/rtl8192su_linux_2.6.0002.0708.2009/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [all] Error 2

I'm hoping someone might be able to help me get this working.

Thanks heaps,
Derek.

---

### Post by chili555 on 2010-04-13
Do you have the package *build-essential* installed?```
sudo apt-get install build-essential
```

---

### Post by dezgo on 2010-04-13
I didn't actually, but now that I've installed that I tried again but am still getting the same error.

---

### Post by chili555 on 2010-04-13
Perhaps you will have better luck with the latest version:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=231&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=231&DownTypeID=3&GetDown=false&Downloads=true)

It makes perfectly for me with no errors or warnings.

---

### Post by dezgo on 2010-04-13
Awesome man, the updated driver worked! I'm now online typing this with the new wireless usb adapter. Thanks heaps.

---

