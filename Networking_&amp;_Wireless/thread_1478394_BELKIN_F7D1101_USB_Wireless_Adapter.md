---
title: "BELKIN F7D1101 USB Wireless Adapter"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by mem16421 on 2010-05-09
Picked up BELKIN F7D1101 for Ubuntu 10.04 and it does not recognize it.  I tried NDISwrapper with no luck either.  Anyone have any luck with this one?  I don't have an option to put in a PC card, so I really trying to find a USB wireless N solution.  Works fine in Windows 7, but in Ubuntu I can't even see it using lspci.

Thanks!

---

### Post by dot_con_man on 2010-05-14
The BELKIN modal F7D1101 Will not work with Ubuntu what so ever. It's an operating dependent device. I have attempted to use wine to emulate windows 7 & windows XP. It ends in an epic fail. I'm just going to return this to target and get my $20.00 back. This thing was a bad buy & I don't recommend the product.  :mad:

---

### Post by Apv507 on 2010-05-28
Just bought this today. So there is NO hope? Belkin fails me again. Does anyone know of a good wireless adapter that runs on Ubuntu from the install and on Windoze 7? (both 64 bit)

---

### Post by flash63 on 2010-05-29
Hello,
build-in Chipset and Device-ID's?

For PCI-Cards:
```
lspci -nnk | grep -i net -A2
```
For USB-Devices
```
lsusb
```

---

### Post by linux.is.skynet on 2010-05-30
Same problem here. The belkin shows up with lsusb, but it doesn't light up or show any networks. Not even ndiswrapper seems to help. I've got my Ubuntu pc hooked up to my wife's Windows 7 pc via ethernet, and I need a fix for this. She'll skin me if no one ever finds the answer!

---

### Post by borkabrak on 2010-05-30
Funny.. it works for me, using ndiswrapper and the drivers that shipped with it.  Specifically, 'net8192su'.

I'm still running Ubuntu 8.04.  Maybe that matters somehow.

I actually came here hoping someone could help me get native drivers for it.  Guess not..

---

### Post by 1idcat on 2010-05-30
RTL8192U Linux driver version 0.03.. This driver supports RealTek rtl8192U USB Wireless LAN NIC for 2.6 kernel:
Fedora Core 2/3/4/5, Debian 3.1, Mandrake 10.2/Mandriva 2006, SUSE 9.3/10.1/10.2, Gentoo 3.1, Ubuntu 7.10/8.04, etc.

---

### Post by linux.is.skynet on 2010-05-31
Tried to make the driver for the RTL8192U Linux driver , but got this error message.


justin@AMD:~/Desktop/rtl8192u_linux_26.0003.0902.2008$ sudo sh  ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
rm -rf .tmp_versions
make -C /lib/modules/2.6.32-21-generic/build M=/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_rx.o
In file included from /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_rx.c:46:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211.h: In function ‘ieee80211_priv’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211.h:2191: warning: ‘netdev_priv’ is static but used in inline function ‘ieee80211_priv’ which is not static
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_rx.c: In function ‘RxReorderIndicatePacket’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_rx.c:792: warning: the frame size of 1072 bytes is larger than 1024 bytes
  CC [M]  /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_softmac.o
In file included from /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_softmac.c:17:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211.h: In function ‘ieee80211_priv’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211.h:2191: warning: ‘netdev_priv’ is static but used in inline function ‘ieee80211_priv’ which is not static
  CC [M]  /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_tx.o
In file included from /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_tx.c:56:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211.h: In function ‘ieee80211_priv’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211.h:2191: warning: ‘netdev_priv’ is static but used in inline function ‘ieee80211_priv’ which is not static
  CC [M]  /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.o
In file included from /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:37:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211.h: In function ‘ieee80211_priv’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211.h:2191: warning: ‘netdev_priv’ is static but used in inline function ‘ieee80211_priv’ which is not static
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c: In function ‘ipw2100_translate_scan’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:93: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:93: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:93: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘long unsigned int’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:93: error: too few arguments to function ‘iwe_stream_add_event’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:102: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:102: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:102: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:102: error: too few arguments to function ‘iwe_stream_add_point’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:105: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:105: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:105: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘u8 *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:105: error: too few arguments to function ‘iwe_stream_add_point’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:117: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:117: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:117: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘long unsigned int’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:117: error: too few arguments to function ‘iwe_stream_add_event’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:127: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:127: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:127: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘long unsigned int’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:127: error: too few arguments to function ‘iwe_stream_add_event’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:137: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:137: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:137: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘long unsigned int’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:137: error: too few arguments to function ‘iwe_stream_add_event’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:146: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:146: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:146: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘u8 *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:146: error: too few arguments to function ‘iwe_stream_add_point’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:184: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:184: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:184: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘long unsigned int’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:184: error: too few arguments to function ‘iwe_stream_add_event’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:189: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:189: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:189: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:189: error: too few arguments to function ‘iwe_stream_add_point’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:205: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:205: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
include/net/iw_handler.h:517: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:205: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
include/net/iw_handler.h:517: note: expected ‘struct iw_event *’ but argument is of type ‘long unsigned int’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:205: error: too few arguments to function ‘iwe_stream_add_event’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:212: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:212: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:212: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:212: error: too few arguments to function ‘iwe_stream_add_point’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:251: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:251: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:251: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:251: error: too few arguments to function ‘iwe_stream_add_point’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:260: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:260: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:260: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:260: error: too few arguments to function ‘iwe_stream_add_point’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:273: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_request_info *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:273: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘char *’ but argument is of type ‘struct iw_event *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:273: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
include/net/iw_handler.h:542: note: expected ‘struct iw_event *’ but argument is of type ‘char *’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:273: error: too few arguments to function ‘iwe_stream_add_point’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.c:836: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
make[2]: *** [/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211/ieee80211_wx.o] Error 1
make[1]: *** [_module_/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf .tmp_versions
make -C /lib/modules/2.6.32-21-generic/build M=/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.o
In file included from /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:65:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U.h:42:27: error: asm/semaphore.h: No such file or directory
In file included from /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U.h:44,
                 from /home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:65:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/ieee80211.h: In function ‘ieee80211_priv’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/ieee80211.h:2184: warning: ‘netdev_priv’ is static but used in inline function ‘ieee80211_priv’ which is not static
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_rx_initiate’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:1158: warning: passing argument 4 of ‘usb_fill_bulk_urb’ makes pointer from integer without a cast
include/linux/usb.h:1277: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:1188: warning: passing argument 4 of ‘usb_fill_bulk_urb’ makes pointer from integer without a cast
include/linux/usb.h:1277: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_rx_isr’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:1567: warning: passing argument 4 of ‘usb_fill_bulk_urb’ makes pointer from integer without a cast
include/linux/usb.h:1277: note: expected ‘void *’ but argument is of type ‘sk_buff_data_t’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:1574: warning: assignment makes pointer from integer without a cast
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_initendpoints’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:2923: warning: cast from pointer to integer of different size
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:2933: warning: cast to pointer from integer of different size
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c: In function ‘rtl8192_usb_probe’:
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:6761: error: ‘struct net_device’ has no member named ‘open’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:6762: error: ‘struct net_device’ has no member named ‘stop’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:6764: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:6766: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:6767: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:6768: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.c:6769: error: ‘struct net_device’ has no member named ‘get_stats’
make[2]: *** [/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/justin/Desktop/rtl8192u_linux_26.0003.0902.2008/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] Error 2

---

### Post by linux.is.skynet on 2010-06-01
Still no luck...

---

### Post by linux.is.skynet on 2010-06-01
@borkabrak



I'm going to try to ndiswrapper in 8.04, hopefully it works for me too. I'll post later on what I find.

---

### Post by linux.is.skynet on 2010-06-01
Well, it goes farther, installs the Belkin, shows the router, but won't connect. It kicks out at the password when the password worked before with another adapter. I'm getting a headache...

---

### Post by mrwilky on 2010-06-03
Just installed ubuntu 10.04 lts. Bought a Belkin F7D1101 v1 usb n adapter and out of the box it didn't work. After reading the forums here and finding so many people can't make it work I began to wonder if I made a mistake buying the thing.  But after many more hours of reading I found that if I went to my package manager and type in "wifi" it brought up the file ndiswrapper in which many forums stated.   ndisgtk is the exact package This is for windows wireless drivers. After I installed the windows driver using this it worked like a charm.  Works great in 9.1 the same way Just to let you know

---

### Post by linux.is.skynet on 2010-06-06
Mine connects, but I can't use a WPA2 key... It won't connect with my router with that enabled...

---

### Post by twowheeler on 2010-06-09
Thanks to mrwilky for the tip about ndisgtk.  That is very easy and works perfectly with my Belkin F7D1101 USB wireless.

---

### Post by kreppnar on 2010-06-11
So far, i have noticed that the second you get a PCI D-Link wireless adapter, and throw it in your linux box..it just works. No questions asked. So D-Link is the best for Linux compatibility. They even provide Linux documentations with their software.

-Kreppnar-

---

### Post by mrwilky on 2010-06-12
for linux.is.skynet Go to your package manager and in the search type in wpa you may need this package " wpasuppcplicant " try that

---

### Post by fgsupport on 2010-06-19
Try the Trendnet wireless TEW-424UB. It works out of the box.

---

### Post by pwnjangles on 2010-08-05
> **mrwilky said:**
> Just installed ubuntu 10.04 lts. Bought a Belkin F7D1101 v1 usb n adapter and out of the box it didn't work. After reading the forums here and finding so many people can't make it work I began to wonder if I made a mistake buying the thing.  But after many more hours of reading I found that if I went to my package manager and type in "wifi" it brought up the file ndiswrapper in which many forums stated.   ndisgtk is the exact package This is for windows wireless drivers. After I installed the windows driver using this it worked like a charm.  Works great in 9.1 the same way Just to let you know

Tried it with 10.4 and it doesn't work sadly unless I chosing the wrong inf file to select when trying to install with ndis.

---

### Post by flash63 on 2010-08-06
Hello,
checkout the USB-ID:
```
lsusb
```
it looks like this
```
Bus 001 Device 001: ID 050d:945a Belkin Components
```
Very probably it is a device with Realtek Chipset. The manufacturer provides appropriate drivers.

---

### Post by Linux_Youth******* on 2010-08-06
Check another forum post: [http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101](http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101)

The instructions listed in that post are what I used to install this same device on my Mepis 8.5 installation, which is based on Debian much like Ubuntu. It should work well for you. If not then well, at least I tried. Good luck!

---

### Post by itsmilesdavis on 2010-08-12
I was going to try ndiswrapper (as mentioned by mrwilky, but I don't have the XP .inf file).  

Can anyone get this to me?  I don't have an XP machine.  Belkin only offers an .exe file, which I can't access with cabextract.

How can I get access to the WinXP inf.  Note, I have the Vista one.  It doesn't work (and I saw a different thread agreeing with this.

I'm running 10.04.

---

### Post by itsmilesdavis on 2010-08-13
I used the link provided by Linux_Youth for the Belkin adapter.  It worked perfectly in Lucid.

[http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101](http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101)

You can uninstall ndiswrapper.

Thanks!

---

### Post by MIJ-VI on 2010-08-19
A long-range, USB-based Wi-Fi adaptor which works plug 'n' play under recent Ubuntu releases:

"The Wi-Fire is the perfect WiFi adapter for Linux users, allowing  you to connect to your WiFi networks from up to three times as far away  as most other adapters can..."

[http://www.hfield.com/the-wi-fire/platform-compatibility/linux/](http://www.hfield.com/the-wi-fire/platform-compatibility/linux/)

Mine has worked well since I got it last Fall.

---

### Post by mrwilky on 2010-08-19
I read here some of you have made my way work and others have not. Please understand if you are running a 32bit sys. install the 32bit driver and the same for 64bit. The 32bit .inf just don't work on a 64bit sys...So I found out. the hard way... And sense this is a windows .inf please make sure you have installed "WINE" and wpa support.

---

### Post by socrates2718 on 2011-02-02
This helped me a lot. I couldn't get the mkdir command to work but someone suggested GKNautilus (a GUI for file structure) and I was able to move it to the directory manually. Restart and it found the wireless network perfectly.

Thanks to all

---

