---
title: "ralink wireless N usb adapter"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by inoh on 2010-03-07
I have a hornettek wireless N usb dongle that is really a ralink.  The device id is 148f:3071.

I am running off the drivers that came with karmic.  (Dongle has dropped four times in the first day of use)

I was unable to get the drivers that came with the cd to work, compile gave me Error 1 and Error 2 no matter what I did.  (Changed config.mk, used sudo make instead of make)

I also need to know how to enable and disable WWM feature, as it has to match the router(dir-655) in order setting in order to login as admin and change features.

Any help with getting the latest driver working correctly (cant get above 135MB, would like 300MB) and control of the WWM feature is greatly appriciated.

---

### Post by GeniusGeeko on 2010-03-07
I had the same problem, but I don't know the exacts. If you could post the exact error from the terminal.

You can do that by using: ```
sudo make 2> errors
```

Then look at the errors file in the gedit text editor. Copy paste that to here. 

You could also just copy straight from terminal.

---

### Post by inoh on 2010-03-10
sudo make
make -C tools
make[1]: Entering directory `/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools'
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.o
In file included from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rt_config.h:56,
                 from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/crypt_md5.h:35,
                 from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.c:27:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:654: error: ‘TX_RING_SIZE’ undeclared here (not in a function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:662: error: ‘RX_RING_SIZE’ undeclared here (not in a function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:670: error: ‘MGMT_RING_SIZE’ undeclared here (not in a function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:728: error: ‘NUM_OF_TX_RING’ undeclared here (not in a function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:2175: error: expected specifier-qualifier-list before ‘RTMP_INF_TYPE’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:2296: error: expected specifier-qualifier-list before ‘RTMP_INF_TYPE’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:2738: error: expected specifier-qualifier-list before ‘RT28XX_RXD_STRUC’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3521: error: expected declaration specifiers or ‘...’ before ‘INT_SOURCE_CSR_STRUC’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3612: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3632: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3638: error: expected declaration specifiers or ‘...’ before ‘PTXWI_STRUC’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:3677: error: expected declaration specifiers or ‘...’ before ‘PRT28XX_RXD_STRUC’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:5395: error: expected declaration specifiers or ‘...’ before ‘PRXWI_STRUC’
In file included from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rt_config.h:56,
                 from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/crypt_md5.h:35,
                 from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.c:27:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:6322: error: expected declaration specifiers or ‘...’ before ‘PRXWI_STRUC’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:6326: error: expected declaration specifiers or ‘...’ before ‘PRT28XX_RXD_STRUC’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rtmp.h:6534: error: expected declaration specifiers or ‘...’ before ‘RTMP_INF_TYPE’
In file included from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/rt_config.h:57,
                 from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/crypt_md5.h:35,
                 from /home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.c:27:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/include/ap.h:82: error: expected declaration specifiers or ‘...’ before ‘PRT28XX_RXD_STRUC’
make[2]: *** [/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/../../common/crypt_md5.o] Error 1
make[1]: *** [_module_/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make: *** [LINUX] Error 2

---

### Post by chili555 on 2010-03-10
Do you have *build-essential* installed? Is your card not working because conflicting drivers are loading?> $ modinfo rt3070sta | grep 3071
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Blue"]148F[/COLOR]p[COLOR="Blue"]3071[/COLOR]d*dc*dsc*dp*ic*isc*ip*
$ modinfo rt2800usb | grep 3071
alias:          usb:v[COLOR="Blue"]148F[/COLOR]p[COLOR="Blue"]3071[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*Find out with:```
lsmod | grep -e rt2 -e rt3
```Maybe we need to blacklist the conflicting modules.

---

### Post by inoh on 2010-03-12
i tried to blacklist the modules that came with karmic, but the card stopped recognizing all together and i still could not get the cd modules to configure.

lsmod | grep -e rt2 -e rt3
rt3070sta             503348  1 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211
crc_ccitt               1852  1 rt2800usb

a couple of postings i found said to blacklist rt2800 usb.  that however did nothing for me

---

### Post by chili555 on 2010-03-12
Please try blacklisting rt2800usb, rt2x00usb and rt2x00lib. Reboot and tell us if the device is now working.

You have a classic case of conflicting drivers. You, and many others, assume that because their card doesn't work correctly, they need another driver which also, sadly conflicts!

Please let us know your results so the searchers will learn.

---

### Post by inoh on 2010-03-12
i tried working on it again today.  i removed a folder that i noticed in make install, /etc/Wireless/RT3070STA.  then the wireless security wouldnt go through anymore.  blacklisted as you suggested.
not sure what all was in that directory
now im getting this.

/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:466: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:467: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:468: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘DuplicatePacket’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:494: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:495: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:498: warning: implicit declaration of function ‘skb_clone’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:498: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:498: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:501: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘duplicate_pkt’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:522: warning: implicit declaration of function ‘__dev_alloc_skb’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:522: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:522: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:524: warning: implicit declaration of function ‘skb_reserve’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:525: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:527: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:529: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘duplicate_pkt_with_TKIP_MIC’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:546: warning: implicit declaration of function ‘skb_tailroom’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:549: warning: implicit declaration of function ‘skb_copy_expand’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:549: warning: implicit declaration of function ‘skb_headroom’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:549: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:549: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘ClonePacket’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:576: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:576: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:580: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:580: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:585: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:585: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:586: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:587: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:588: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:588: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:588: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:589: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘update_os_packet_info’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:604: error: ‘RX_BLK’ has no member named ‘pRxPacket’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:604: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:604: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:605: error: ‘RX_BLK’ has no member named ‘pRxPacket’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:607: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:608: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:608: error: ‘RX_BLK’ has no member named ‘pData’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:609: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:609: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:610: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:610: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:610: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘wlan_802_11_to_802_3_packet’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:622: error: ‘RX_BLK’ has no member named ‘pRxPacket’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:622: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:622: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:623: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:625: error: ‘RX_BLK’ has no member named ‘pRxPacket’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:627: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:628: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:628: error: ‘RX_BLK’ has no member named ‘pData’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:629: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:629: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:630: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:630: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:630: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:639: warning: implicit declaration of function ‘skb_push’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:639: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/include/bits/string3.h:56: note: expected ‘void * __restrict__’ but argument is of type ‘int’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘announce_802_3_packet’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:652: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:652: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:663: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:663: warning: implicit declaration of function ‘eth_type_trans’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:663: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:670: warning: implicit declaration of function ‘netif_rx’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘rt_get_sg_list_from_packet’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:681: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:682: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RTMPSendWirelessEvent’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:771: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:771: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:779: warning: implicit declaration of function ‘sprintf’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:779: warning: incompatible implicit declaration of built-in function ‘sprintf’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:823: error: ‘u_int32_t’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:823: error: expected ‘;’ before ‘ralinkrate’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:828: error: ‘RX_BLK’ has no member named ‘pRxPacket’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:828: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:828: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:829: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:831: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:835: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:837: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:841: error: ‘RX_BLK’ has no member named ‘pRxPacket’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:842: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:843: error: ‘RX_BLK’ has no member named ‘pHeader’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:845: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:846: error: ‘RX_BLK’ has no member named ‘pHeader’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:847: error: ‘RX_BLK’ has no member named ‘pHeader’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:853: error: ‘RX_BLK’ has no member named ‘pHeader’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:857: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:861: error: ‘RX_BLK’ has no member named ‘pHeader’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:865: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:870: error: ‘RX_BLK’ has no member named ‘pData’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:873: error: ‘RX_BLK’ has no member named ‘RxD’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:874: error: ‘RX_BLK’ has no member named ‘pData’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:876: error: ‘RX_BLK’ has no member named ‘pData’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:880: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:880: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:881: warning: implicit declaration of function ‘skb_trim’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:881: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:883: error: ‘RX_BLK’ has no member named ‘DataSize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:883: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:886: error: ‘RX_BLK’ has no member named ‘pData’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:886: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:887: error: ‘RX_BLK’ has no member named ‘pData’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:887: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:888: warning: implicit declaration of function ‘skb_pull’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:888: error: ‘RX_BLK’ has no member named ‘pData’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:888: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:892: warning: implicit declaration of function ‘pskb_expand_head’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:892: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:899: warning: passing argument 1 of ‘memmove’ makes pointer from integer without a cast
/usr/include/bits/string3.h:56: note: expected ‘void * __restrict__’ but argument is of type ‘int’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:906: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:911: error: ‘jiffies’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:927: error: expected ‘;’ before ‘pAd’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:932: error: expected ‘;’ before ‘RTMPMaxRssi’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:945: error: ‘RX_BLK’ has no member named ‘pRxWI’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:947: error: ‘RX_BLK’ has no member named ‘pRxWI’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:947: error: ‘RX_BLK’ has no member named ‘pRxWI’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:947: error: ‘RX_BLK’ has no member named ‘pRxWI’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:951: error: ‘RX_BLK’ has no member named ‘pRxWI’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:952: error: ‘RX_BLK’ has no member named ‘pRxWI’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:954: error: ‘RX_BLK’ has no member named ‘pRxWI’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:963: error: ‘ralinkrate’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:968: error: expected ‘;’ before ‘pRxBlk’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:971: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:972: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:972: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:973: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:973: error: ‘CHECKSUM_NONE’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:979: error: ‘RX_BLK’ has no member named ‘pRxPacket’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSFileOpen’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:996: warning: implicit declaration of function ‘filp_open’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:996: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:997: warning: implicit declaration of function ‘IS_ERR’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:999: warning: implicit declaration of function ‘PTR_ERR’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSFileClose’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1007: warning: implicit declaration of function ‘filp_close’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSFileSeek’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1014: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSFileRead’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1021: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1021: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1023: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1023: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSFileWrite’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1035: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1035: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSFSInfoChange’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1050: warning: implicit declaration of function ‘current_fsuid’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1051: warning: implicit declaration of function ‘current_fsgid’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1053: error: ‘RTMP_OS_FS_INFO’ has no member named ‘fs’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1053: warning: implicit declaration of function ‘get_fs’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1054: warning: implicit declaration of function ‘set_fs’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1054: error: ‘KERNEL_DS’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1058: error: ‘RTMP_OS_FS_INFO’ has no member named ‘fs’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSTaskKill’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1088: warning: implicit declaration of function ‘pid_nr’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1091: warning: implicit declaration of function ‘mb’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1094: warning: implicit declaration of function ‘kill_pid’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1094: error: ‘SIGTERM’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1097: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1097: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1102: warning: implicit declaration of function ‘wait_for_completion’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSTaskNotifyToExit’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1120: warning: implicit declaration of function ‘complete_and_exit’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSTaskCustomize’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1134: warning: implicit declaration of function ‘daemonize’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1136: warning: implicit declaration of function ‘allow_signal’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1136: error: ‘SIGTERM’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1137: error: ‘SIGKILL’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1138: error: ‘current’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1138: error: ‘PF_NOFREEZE’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1159: warning: implicit declaration of function ‘complete’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSTaskAttach’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1171: error: ‘pid_t’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1171: error: expected ‘;’ before ‘pid_number’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1180: error: ‘pid_number’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1180: warning: implicit declaration of function ‘kernel_thread’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1180: error: ‘CLONE_VM’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1188: warning: implicit declaration of function ‘find_get_pid’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1188: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSTaskInit’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1206: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1206: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1218: warning: implicit declaration of function ‘sema_init’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1221: warning: implicit declaration of function ‘init_completion’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RTMP_IndicateMediaState’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1231: error: ‘struct _RTMP_ADAPTER’ has no member named ‘CommonCfg’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1233: error: ‘struct _RTMP_ADAPTER’ has no member named ‘IndicateMediaState’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1235: error: ‘struct _RTMP_ADAPTER’ has no member named ‘MacTab’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1239: error: ‘struct _RTMP_ADAPTER’ has no member named ‘MacTab’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSWrielessEventSend’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1301: warning: implicit declaration of function ‘wireless_send_event’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevAddrSet’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1315: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1321: error: ‘RTMP_ADAPTER’ has no member named ‘StaCfg’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1322: error: ‘RTMP_ADAPTER’ has no member named ‘StaCfg’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1322: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1322: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1326: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevRequestName’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1350: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1350: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1363: warning: incompatible implicit declaration of built-in function ‘sprintf’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1366: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1378: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevClose’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1395: warning: implicit declaration of function ‘dev_close’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevFree’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1401: error: ‘KERN_WARNING’ undeclared (first use in this function)
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1401: error: expected ‘)’ before string constant
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1404: warning: implicit declaration of function ‘free_netdev’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevAlloc’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1422: warning: implicit declaration of function ‘alloc_etherdev’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1422: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevGetByName’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1441: warning: implicit declaration of function ‘dev_get_by_name’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1441: warning: implicit declaration of function ‘dev_net’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1441: warning: assignment makes pointer from integer without a cast
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDeviceRefPut’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1476: warning: implicit declaration of function ‘dev_put’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1494: warning: implicit declaration of function ‘unregister_netdev’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1508: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1510: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1511: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1512: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1513: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1519: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1522: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1530: error: ‘struct _RTMP_ADAPTER’ has no member named ‘OpMode’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1532: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1547: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1553: error: dereferencing pointer to incomplete type
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1557: warning: implicit declaration of function ‘register_netdevice’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1559: warning: implicit declaration of function ‘register_netdev’
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c: In function ‘RtmpOSNetDevCreate’:
/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.c:1602: error: dereferencing pointer to incomplete type
make[1]: *** [/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux/rt_linux.o] Error 1
make[1]: Leaving directory `/home/craig/Desktop/2009_0525_RT3070_Linux_STA_v2.1.1.0/os/linux'
make: *** [LINUX] Error 2

this is what happens when a newb messes with files they dont understand

---

### Post by inoh on 2010-03-12
I found a newer module which configures but wont install

sudo make
make -C tools
make[1]: Entering directory `/home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/tools'
/home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/tools/bin2h
cp -f os/linux/Makefile.6 /home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/Makefile
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/rt3070sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/rt3070sta.o
see include/linux/module.h for more information
  LD [M]  /home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/rt3070sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
cp -f /home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/rt3070sta.ko /tftpboot
craig@craig-laptop:~/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208$ sudo make install
make -C /home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/RT3070STA.dat /etc/Wireless/RT3070STA/.
cp: cannot stat `/home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/RT3070STA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/craig/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux'
make: *** [install] Error 2

hope this helps

---

### Post by chili555 on 2010-03-12
As I explained:> You, and many others, assume that because their card doesn't work correctly, they need another driver which also, sadly conflicts!So you are trying valiantly to build a new driver, again.

The module rt3070sta is already installed on your system and loading:> lsmod | grep -e rt2 -e rt3
[COLOR="Blue"]rt3070sta[/COLOR] 503348 1
rt2800usb 37372 0
rt2x00usb 11548 1 rt2800usb
rt2x00lib 29756 2 rt2800usb,rt2x00usb
led_class 4096 1 rt2x00lib
input_polldev 3716 1 rt2x00lib
mac80211 181140 2 rt2x00usb,rt2x00lib
cfg80211 93052 2 rt2x00lib,mac80211
crc_ccitt 1852 1 rt2800usb
Please chack your blacklist file. Are these entries in there?```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Did you reboot? Afterwards, please post:```
iwconfig
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by inoh on 2010-03-13
ok.  i did everything you wanted me too.

but it wasnt working correctly from the start,  and similar posts said the solution was to blacklist and get the newest version of the 3070 module.

but as you pointed out, that caused conflicts and even more issues.

so i guess i should have been looking for help on removing all related modules that came with karmic, then installing the latest version of rt3070sta.ko.

i would still like to get the rate to 300MB.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"attempt2"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.427 GHz  Access Point: 00:26:5A:B5:EB:73   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-59 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod | grep -e rt2 -e rt3
rt3070sta             503348  1

does seem to be working better today!  dont know why the blacklisting didnt work yesterday, restarted twice.  it froze and never finished cutting the power, had to do a hard shutdown after waiting two minutes.

---

