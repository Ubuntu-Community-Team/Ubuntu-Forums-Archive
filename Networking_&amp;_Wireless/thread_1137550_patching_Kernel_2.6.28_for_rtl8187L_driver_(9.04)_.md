---
title: "patching Kernel 2.6.28 for rtl8187L driver (9.04) anyone?"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by marcon00 on 2009-04-25
Did anyone perform this ?
I did previously patch my kernel on 8.10, worked good. increased signal strength/display and no connection drops. but i'm still not sure how i did it. Anyone has already done it? which patches did you use ?

Thanks in advance.

---

### Post by marcon00 on 2009-04-26
*hickup*

---

### Post by marcon00 on 2009-04-26
okay . i did this :

mac80211_2.6.28-rc8-wl_frag+ack_radiotap_2.6.28_mod.patch
rtl8187_hw_signal_backport_2.6.28.patch
rtl8187-mac80211-injection-speed-2.6.28-wl.patch

on this :

rtl8187_linux_26.10100


with weird outcome as this :

```

Desktop/rtl8187_linux_26.1010.0622.2006$ ls
beta-8187						   ReadMe.txt~
drv.tar.gz						   rtl8187_hw_signal_backport_2.6.28.patch
ieee80211						   rtl8187-mac80211-injection-speed-2.6.28-wl.patch
ifcfg-wlan0						   stack.tar.gz
mac80211_2.6.28-rc8-wl_frag+ack_radiotap_2.6.28_mod.patch  wlan0dhcp
makedrv							   wlan0down
makedrv~						   wlan0rmv
makedrvbk						   wlan0up
ReadMe.txt						   wpa_supplicant-0.4.9
xxxxxxxxxx:~/Desktop/rtl8187_linux_26.1010.0622.2006$ patch -Np1 -i rtl8187_hw_signal_backport_2.6.28.patch 
can't find file to patch at input line 24
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|From: Larry Finger <Larry.Finger@lwfinger.net>
|Date: Thu, 4 Dec 2008 04:21:20 +0000 (-0600)
|Subject: rtl8187: Improve wireless statistics for RTL8187
|X-Git-Tag: master-2009-01-05~191
|X-Git-Url: http://git.kernel.org/?p=linux%2Fkernel%2Fgit%2Flinville%2Fwireless-testing.git;a=commitdiff_plain;h=cd2865552927d616be4a0da7c24$
|
|rtl8187: Improve wireless statistics for RTL8187
|
|The current wireless statistics for the RTL8187 poorly indicate the signal
|strength and quality. With testing, I found that the AGC value is inversely
|correlated with the strength as in the RTL8187B. By implementing a similar
|calculation, much more code becomes common to the two devices.
|
|Signed-off-by: Larry Finger <Larry.Finger@lwfinger.net>
|Tested by: MartÃ*n Ernesto Barreyro <barreyromartin@gmail.com>
|Acked-by: Hin-Tak Leung <htl10@users.sourceforge.net>
|Signed-off-by: John W. Linville <linville@tuxdriver.com>
|Crudely-backported-by: Zero_Chaos <zero_chaos@pentoo.ch>
|---
|
|diff -Naur linux-2.6.28-orig/drivers/net/wireless/rtl8187_dev.c linux-2.6.28/drivers/net/wireless/rtl8187_dev.c
|--- linux-2.6.28-orig/drivers/net/wireless/rtl8187_dev.c	2009-02-09 16:52:51.000000000 -0500
|+++ linux-2.6.28/drivers/net/wireless/rtl8187_dev.c	2009-02-09 17:22:50.000000000 -0500
--------------------------
File to patch: 

```

---

### Post by marcon00 on 2009-04-27
*fart*

---

### Post by Tom--d on 2009-04-27
Sound like you used the compact wireless package?
From here: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by marcon00 on 2009-04-27
> **Tom--d said:**
> Sound like you used the compact wireless package?
From here: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)



i got it from 
[http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip)

:)

---

### Post by rashwan on 2009-04-27
marcon00 , this card will never work properly in Manage Mode

dont wast your time :s 

Unless you use "Ndiswrapper"

---

### Post by marcon00 on 2009-04-27
i dont want it to work properly under managed mode,nevertheless it worked very good in 8.04.. but how come i cant patch it ?

---

### Post by Qfito on 2009-04-27
[http://foro.seguridadwireless.net/zona-linux/parche-para-8187l-en-ubuntu-con-kernel-2-6-28/](http://foro.seguridadwireless.net/zona-linux/parche-para-8187l-en-ubuntu-con-kernel-2-6-28/)

---

### Post by marcon00 on 2009-04-28
now im getting this :

```


sudo ./makedrv
ieee80211/
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_wx.c
ieee80211/license
ieee80211/Makefile
ieee80211/Modules.symvers
ieee80211/readme
beta-8187/
beta-8187/r8180_hw.h
beta-8187/r8187.h~
beta-8187/r8180_rtl8225.h
beta-8187/license
beta-8187/.tmp_versions/
beta-8187/.tmp_versions/r8187.mod
beta-8187/Makefile
beta-8187/r8180_93cx6.c
beta-8187/tags
beta-8187/authors
beta-8187/r8187_core.c~
beta-8187/r8180_pm.h
beta-8187/r8180_rtl8225.c
beta-8187/copying
beta-8187/r8180_wx.h
beta-8187/Modules.symvers
beta-8187/r8180_rtl8225z2.c
beta-8187/readme
beta-8187/r8187_core.c
beta-8187/ieee80211.h
beta-8187/r8180_93cx6.h
beta-8187/changes
beta-8187/r8187.h
beta-8187/r8180_pm.c
beta-8187/install
beta-8187/ieee80211_crypt.h
beta-8187/r8180_wx.c
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/tmp
make -C /lib/modules/2.6.28-11-generic/build M=/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
In file included from /home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:17:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h:1159: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_scan_wq&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:412: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_stop_scan&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:486: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_associate_abort&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:885: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1360:4: warning: #warning CHECK_LOCK_HERE
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1400:2: warning: #warning CHECK_LOCK_HERE
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_rx_frame_softmac&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1471: warning: ISO C90 forbids mixed declarations and code
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_stop_protocol&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2060: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: (Each undeclared identifier is reported only once
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2168: error: for each function it appears in.)
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2169:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2170:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2171:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2173:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_free&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2192: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
make[2]: *** [/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/tmp
make -C /lib/modules/2.6.28-11-generic/build M=/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o
In file included from /home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:64:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:29:26: error: linux/config.h: No such file or directory
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:48:27: error: asm/semaphore.h: No such file or directory
In file included from /home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:50,
                 from /home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:64:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/ieee80211.h: In function &#8216;ieee80211_priv&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/ieee80211.h:1159: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv&#8217; which is not static
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function &#8216;rtl8180_proc_module_init&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: error: (Each undeclared identifier is reported only once
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:421: error: for each function it appears in.)
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function &#8216;rtl8180_proc_module_remove&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:427: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function &#8216;rtl8187_rx_urbsubmit&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:700: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function &#8216;rtl8180_tx&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1428: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function &#8216;rtl8180_init&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:1625: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function &#8216;rtl8180_ioctl&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2298: warning: ISO C90 forbids mixed declarations and code
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c: In function &#8216;rtl8187_usb_probe&#8217;:
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2403: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:2421: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
make[2]: *** [/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/marcon/Desktop/rtl8187_linux_26.1010.0622.2006/beta-8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2


```

thanks for helping :)

---

### Post by Murdoc_of_puts on 2009-10-10
I'm having the same problem.....I tried grep / 'file' for both of the patches to se if I could find where the file was-sometimes it might be slightly out of place messing everything up.  Still I couldn't find wither of the files that it's looking for to patch.  If I could find out where I should be looking, I think I could thick the rest.  Thanks if you help.

---

