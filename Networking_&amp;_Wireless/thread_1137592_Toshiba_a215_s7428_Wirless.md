---
title: "Toshiba a215 s7428 Wirless"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by nicholas.alipaz on 2009-04-25
I am trying to get wireless to work on this laptop.  This is a new installation, but I previously had wireless working by following the guide here:
[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

I fixed it back in Ubuntu 8.04 in maybe August, but I installed 8.04.2 and tried to follow the guide but I receive errors when running the commands:

```
nicholas@alipaz:~$ cd /home/nicholas/Desktop/rtl8187b-modified
nicholas@alipaz:~/Desktop/rtl8187b-modified$ sudo chmod +x makedrv
[sudo] password for nicholas: 
nicholas@alipaz:~/Desktop/rtl8187b-modified$ sudo ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-23-generic/build M=/home/nicholas/Desktop/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.o
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:433: warning: initialization from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:432: warning: unused variable ‘dwork’
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_probe_resp’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:710: warning: ISO C90 forbids mixed declarations and code
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_retry_wq’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2253: warning: initialization from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2252: warning: unused variable ‘dwork’
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2475: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2476: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2477: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2478: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2479: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2480: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1666: warning: ‘chlen’ may be used uninitialized in this function
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_rx.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_tx.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_wx.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_module.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.o
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:87: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:109: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:125: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:141: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:423: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211-rtl.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211-rtl.ko
  CC      /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-23-generic/build M=/home/nicholas/Desktop/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.o
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:934: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_manage_urbsubmit’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:954: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_rtx_disable’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:1255: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2220: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2227: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2277: warning: ISO C90 forbids mixed declarations and code
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2280: warning: cast from pointer to integer of different size
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2281: warning: ISO C90 forbids mixed declarations and code
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2290: warning: cast to pointer from integer of different size
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2310: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2256: warning: unused variable ‘i’
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_deleteendpoints’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2328: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: At top level:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: ‘struct struct_work’ declared inside parameter list
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: its scope is only this definition or declaration, which is probably not what you want
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_wmm_param_update’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2437: warning: initialization from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2439: warning: initialization from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_init’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2654: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:2702: warning: assignment from incompatible pointer type
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_adapter_start’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3054: warning: unused variable ‘bInvalidWirelessMode’
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3053: warning: unused variable ‘SupportedWirelessMode’
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3052: warning: unused variable ‘InitWirelessMode’
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3051: warning: unused variable ‘ieee’
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_irq_rx_tasklet’:
/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187_core.c:3769: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8180_93cx6.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8180_wx.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8180_rtl8225.o
  CC [M]  /home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_wx_get_freq" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko] undefined!
  CC      /home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.mod.o
  LD [M]  /home/nicholas/Desktop/rtl8187b-modified/rtl8187/r8187.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
nicholas@alipaz:~/Desktop/rtl8187b-modified$ sudo chmod +x wlan0up
nicholas@alipaz:~/Desktop/rtl8187b-modified$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8187.ko': -1 File exists
```

Does anyone have any ideas on what I can do to get wireless to work here?

Thanks

---

### Post by nicholas.alipaz on 2009-04-26
wow, this forum moves really fast.  I am already on the 5th page within 19 hours.  No one has any ideas on why I get the errors?

---

