---
title: "Trying to install Patch Drivers for Rtl8187"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by Stoowyguy on 2012-06-25
I know this probably isn't the right forum for this but it seams that the Aircrack-ng Forum is down.... 

I was hoping that maybe you guys could help me on my problem

I am trying to install a "patched" driver for my rtl8187... (the new patch driver being r8187)

I get as far as to when I need to compile everything (make)

Look at what it says when I type make 
root@Corys-Ubuntu:/home/cory/rtl8187_linux_26.1010.0622.2006# make
rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/3.2.0-25-generic/build M=/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic'
  CC [M]  /home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
In file included from /home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:17:0:
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h:986:24: error: field ‘ps_task’ has incomplete type
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac_rtl7’:
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1512:3: error: implicit declaration of function ‘tasklet_schedule’ [-Werror=implicit-function-declaration]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init_rtl7’:
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2229:2: error: implicit declaration of function ‘tasklet_init’ [-Werror=implicit-function-declaration]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_wpa_set_encryption_rtl7’:
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2474:3: error: implicit declaration of function ‘request_module’ [-Werror=implicit-function-declaration]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2503:3: error: implicit declaration of function ‘try_module_get’ [-Werror=implicit-function-declaration]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: At top level:
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2648:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2648:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2648:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2649:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2649:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2649:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2650:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2650:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2650:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2651:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2651:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2651:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2652:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2652:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2652:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2653:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2653:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2653:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2654:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2654:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2654:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2655:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2655:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2655:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2656:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2656:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2656:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2657:1: warning: data definition has no type or storage class [enabled by default]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2657:1: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’ [-Wimplicit-int]
/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2657:1: warning: parameter names (without types) in function declaration [enabled by default]
cc1: some warnings being treated as errors
make[3]: *** [/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o] Error 1
make[2]: *** [_module_/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/cory/rtl8187_linux_26.1010.0622.2006/ieee80211'
make: *** [all] Error 2

PLEASE HELP, I have been trying to fix this for a long time and can't seam to find out why it doesn't work.. 

By the Way I have done this before on previous kernels & versions of Ubuntu Linux..

If It helps I am running Kernel  3.2.0-25-generic and Ubuntu v. 12.04 LTS

---

### Post by chili555 on 2012-06-25
> rtl8187_linux_26.1010.0622.[COLOR="Red"]2006[/COLOR]We don't support aircrack on this forum, but I strongly suspect this oldy is never going to compile on your shiny 3.2.0-xx kernel. We no longer use wooden spoke wheels on our sleek new BMWs and Porsches.

---

