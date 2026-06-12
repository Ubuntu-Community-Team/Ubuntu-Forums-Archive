---
title: "patching ath5k driver"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by WobblyGuy on 2009-11-05
hey, i'm currently trying to get aircrack to work and according to the website, my wireless card is compatible but only with it being patched so, following all the instructions on patching the driver that I found from[http://ubuntuforums.org/showthread.php?t=1315396](http://ubuntuforums.org/showthread.php?t=1315396) work but when I use sudo make install, it does everything it probably should but then gives me loads of lines like this below:

```

garry@Henry:~/compat-wireless-2.6.30$ sudo make install
WARNING: -e needs -E or -F
Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

--- Below here is the part I don't get:

make -C /lib/modules/2.6.31-14-generic/build M=/home/garry/compat-wireless-2.6.30 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.o
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: In function &#8216;ath_rfkill_poll&#8217;:
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1201: error: storage size of &#8216;state&#8217; isn&#8217;t known
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1204: error: &#8216;RFKILL_STATE_SOFT_BLOCKED&#8217; undeclared (first use in this function)
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1204: error: (Each undeclared identifier is reported only once
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1204: error: for each function it appears in.)
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1205: error: &#8216;RFKILL_STATE_HARD_BLOCKED&#8217; undeclared (first use in this function)
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1208: error: &#8216;RFKILL_STATE_UNBLOCKED&#8217; undeclared (first use in this function)
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1219: error: implicit declaration of function &#8216;rfkill_force_state&#8217;
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1201: warning: unused variable &#8216;state&#8217;
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: At top level:
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1227: warning: &#8216;enum rfkill_state&#8217; declared inside parameter list
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1227: warning: its scope is only this definition or declaration, which is probably not what you want
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1227: error: parameter 2 (&#8216;state&#8217;) has incomplete type
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: In function &#8216;ath_sw_toggle_radio&#8217;:
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1232: error: &#8216;RFKILL_STATE_SOFT_BLOCKED&#8217; undeclared (first use in this function)
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1238: error: &#8216;RFKILL_STATE_UNBLOCKED&#8217; undeclared (first use in this function)
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: In function &#8216;ath_init_sw_rfkill&#8217;:
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1257: error: implicit declaration of function &#8216;rfkill_allocate&#8217;
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1258: warning: assignment makes pointer from integer without a cast
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1266: error: dereferencing pointer to incomplete type
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1267: error: dereferencing pointer to incomplete type
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1268: error: dereferencing pointer to incomplete type
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1269: error: dereferencing pointer to incomplete type
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1269: error: &#8216;RFKILL_STATE_UNBLOCKED&#8217; undeclared (first use in this function)
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1270: error: dereferencing pointer to incomplete type
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c: In function &#8216;ath_start_rfkill_poll&#8217;:
/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.c:1298: error: implicit declaration of function &#8216;rfkill_free&#8217;
make[4]: *** [/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k/main.o] Error 1
make[3]: *** [/home/garry/compat-wireless-2.6.30/drivers/net/wireless/ath9k] Error 2
make[2]: *** [/home/garry/compat-wireless-2.6.30/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/garry/compat-wireless-2.6.30] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2

```I just don't get what all the errors are about and if the patch was installed correctly and I was wondering if anybody could tell me this and if they did not install properly, a work-around?

Thanks.

---

