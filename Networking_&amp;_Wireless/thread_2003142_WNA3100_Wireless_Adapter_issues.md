---
title: "WNA3100 Wireless Adapter issues"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by Relinies on 2012-06-13
So I installed a partition on my computer that has Ubuntu, but there's a big issue. My NetGear wireless internet adapter (WNA3100) doesn't work.
I was using this guide here: [http://matthew-4gl.wikispaces.com/wna3100_ubuntu_linux](http://matthew-4gl.wikispaces.com/wna3100_ubuntu_linux) and it worked up until I typed the command sudo make install. I don't know what went wrong, but it said Error twice, numbered respectively.
Please note this is using ndiswrapper 1.57, the most recent stable version. I looked through the guide, and one of the sections gave the version 1.56. So here's my question.
1. Would the different version make such a huge difference?
2. If not, how will I fix my problem?

---

### Post by Relinies on 2012-06-13
I have the full output of the Terminal now

relinies@Relinies-Ubuntu:~$ cd /home/relinies/Documents/ndis
relinies@Relinies-Ubuntu:~/Documents/ndis$ sudo make
[sudo] password for relinies: 
make -C driver
make[1]: Entering directory `/home/relinies/Documents/ndis/driver'
make -C /usr/src/linux-headers-3.2.0-23-generic M=/home/relinies/Documents/ndis/driver
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  LD      /home/relinies/Documents/ndis/driver/built-in.o
  MKEXPORT /home/relinies/Documents/ndis/driver/crt_exports.h
  MKEXPORT /home/relinies/Documents/ndis/driver/hal_exports.h
  MKEXPORT /home/relinies/Documents/ndis/driver/ndis_exports.h
  MKEXPORT /home/relinies/Documents/ndis/driver/ntoskernel_exports.h
  MKEXPORT /home/relinies/Documents/ndis/driver/ntoskernel_io_exports.h
  MKEXPORT /home/relinies/Documents/ndis/driver/rtl_exports.h
  MKEXPORT /home/relinies/Documents/ndis/driver/usb_exports.h
  MKSTUBS /home/relinies/Documents/ndis/driver/win2lin_stubs.h
  CC [M]  /home/relinies/Documents/ndis/driver/crt.o
  CC [M]  /home/relinies/Documents/ndis/driver/hal.o
  CC [M]  /home/relinies/Documents/ndis/driver/iw_ndis.o
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_essid’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:76:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_essid’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:110:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_infra_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:170:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_infra_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:198:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_network_type’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:241:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_freq’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:261:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_freq’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:295:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_tx_power’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:332:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_tx_power’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:351:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_bitrate’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:388:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_bitrate’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:406:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_rts_threshold’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:451:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_rts_threshold’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:469:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_frag_threshold’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:489:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_frag_threshold’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:507:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_ap_address’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:540:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_ap_address’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:554:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_encr’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:741:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_wep’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:906:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_nick’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:992:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_nick’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1004:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_scan’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1196:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_scan’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1203:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_power_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1265:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_power_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1288:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_sensitivity’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1320:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_sensitivity’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1339:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_ndis_stats’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1361:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_range’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1372:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_mlme’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1537:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_auth’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1571:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_get_auth’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1612:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_encodeext’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1643:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘iw_set_pmksa’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1749:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_reset’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1828:17: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_deauthenticate’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1842:23: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_power_profile’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1850:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_network_type’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1875:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_media_stream_mode’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1907:28: error: ‘struct net_device’ has no member named ‘priv’
/home/relinies/Documents/ndis/driver/iw_ndis.c: In function ‘priv_reload_defaults’:
/home/relinies/Documents/ndis/driver/iw_ndis.c:1928:28: error: ‘struct net_device’ has no member named ‘priv’
make[3]: *** [/home/relinies/Documents/ndis/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/relinies/Documents/ndis/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/relinies/Documents/ndis/driver'
make: *** [all] Error 2

Somebody tell me how I can put that in a spoiler tag or something, that would help some...

---

### Post by Relinies on 2012-06-13
Well, been a while now and gotten 0 helpful responses from either of my threads. I'm going to sleep. If anyone decides to be helpful while i'm asleep, go ahead and post.

---

