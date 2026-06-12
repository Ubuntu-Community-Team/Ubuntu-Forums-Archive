---
title: "ralink3090/ubuntu11.04 can not install wireless driver"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by xinghu on 2011-06-16
hi,all 

my netbook wireless card is ralink3090,it works fine in ubuntu10.10 after I upgrade to 11.04 it down.

I downloaded a driver from [http://www.ralinktech.com/support.php?s=2,but](http://www.ralinktech.com/support.php?s=2,but) I can not install it.

```

hupengxing@hupengxing-netbook:~/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO$ make
make -C tools
make[1]: Entering directory `/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.o
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c: In function ‘RtmpAsicLoadFirmware’:
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:352:2: warning: ISO C90 forbids mixed declarations and code
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:355:2: warning: passing argument 1 of ‘writel’ makes integer from pointer without a cast
/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/io.h:66:1: note: expected ‘unsigned int’ but argument is of type ‘ULONG *’
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/rtmp_mcu.c:356:2: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘ULONG’
  CC [M]  /home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:679:2: warning: ‘enum tx_power_setting’ declared inside parameter list
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:679:2: warning: its scope is only this definition or declaration, which is probably not what you want
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:678:29: error: parameter 2 (‘Type’) has incomplete type
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:676:12: warning: function declaration isn’t a prototype
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1355:2: warning: initialization from incompatible pointer type
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1378:2: warning: initialization from incompatible pointer type
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1379:2: warning: initialization from incompatible pointer type
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1380:2: warning: initialization from incompatible pointer type
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1381:2: warning: initialization from incompatible pointer type
/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.c:1388:2: warning: initialization from incompatible pointer type
make[2]: *** [/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../os/linux/cfg80211.o] Error 1
make[1]: *** [_module_/home/hupengxing/Downloads/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2

```

please help me.

thanks!

---

### Post by manzdagratiano on 2011-06-17
Take a look at the following thread:

[http://ubuntuforums.org/showthread.php?t=1783881](http://ubuntuforums.org/showthread.php?t=1783881)

and the thread suggested in it.

---

### Post by xinghu on 2011-06-17
> **manzdagratiano said:**
> Take a look at the following thread:

[http://ubuntuforums.org/showthread.php?t=1783881](http://ubuntuforums.org/showthread.php?t=1783881)

and the thread suggested in it.

thank u!

but that does not work for me, I can not pass "make" and I don't have  "common/rt2870.bin" file

what should I do next ?

---

### Post by chili555 on 2011-06-17
I wonder if your wireless device is not working as expected because there is a conflict with the built-in driver, as often happens. Let's have a look at:```
lsmod | grep rt
lspci -nn
```Thanks.

---

