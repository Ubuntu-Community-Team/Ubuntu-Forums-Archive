---
title: "madwifi and compiled kernel"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by ephman on 2005-12-30
hi,

i had to compile a kernel and now madwifi doesn't work.  i know it's part of the restricted modules so i reinstalled them under the new kernel, but that didn't work.  i also tried installing the driver from source and got this error:

root@wintermute:/usr/src/madwifi# make
Checking requirements... ok.
Checking kernel configuration... ok.
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/usr/src/madwifi/ath_hal'
make -C /lib/modules/2.6.12-custom/build SUBDIRS=/usr/src/madwifi/ath_hal MODVERDIR=/usr/src/madwifi/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: Leaving directory `/usr/src/madwifi/ath_hal'
make[1]: Entering directory `/usr/src/madwifi/net80211'
make -C /lib/modules/2.6.12-custom/build SUBDIRS=/usr/src/madwifi/net80211 MODVERDIR=/usr/src/madwifi/net80211/../symbols modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
  CC [M]  /usr/src/madwifi/net80211/if_media.o
cc1: warnings being treated as errors
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi/net80211/if_media.c:60:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
make[3]: *** [/usr/src/madwifi/net80211/if_media.o] Error 1
make[2]: *** [_module_/usr/src/madwifi/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/madwifi/net80211'
make: *** [modules] Error 1
root@wintermute:/usr/src/madwifi#


any help would be great thanks,

ephman

---

### Post by Lambert on 2005-12-30
Ok, do this

find file Makefile.inc in the directory

open up Makefile.inc

```
sudo gedit Makefile.inc
```

towards the bottom you'll see a line COPT   -Werror

erase the -Werror part and save the file.

then sudo make again

You'll see a bunch of warnings in the output but these are ok, make should complete and you can go onto the make install step.

---

### Post by ephman on 2005-12-30
hello,

i took your advice i commented out the werror part and it didn't work :(  i have a pretty long output.  if anybody could help with this i'd appreciate it.

root@wintermute:/usr/src/madwifi# make
Checking requirements... ok.
Checking kernel configuration... ok.
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/usr/src/madwifi/ath_hal'
make -C /lib/modules/2.6.12-custom/build SUBDIRS=/usr/src/madwifi/ath_hal MODVERDIR=/usr/src/madwifi/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
  CC [M]  /usr/src/madwifi/ath_hal/ah_osdep.o
  LD [M]  /usr/src/madwifi/ath_hal/ath_hal.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
  LD [M]  /usr/src/madwifi/ath_hal/ath_hal.ko
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: Leaving directory `/usr/src/madwifi/ath_hal'
make[1]: Entering directory `/usr/src/madwifi/net80211'
make -C /lib/modules/2.6.12-custom/build SUBDIRS=/usr/src/madwifi/net80211 MODVERDIR=/usr/src/madwifi/net80211/../symbols modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
  CC [M]  /usr/src/madwifi/net80211/if_media.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi/net80211/if_media.c:60:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211.o
In file included from /usr/src/madwifi/net80211/ieee80211.c:44:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_beacon.o
In file included from /usr/src/madwifi/net80211/ieee80211_beacon.c:44:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/net80211/ieee80211_beacon.c: In function 'ieee80211_beacon_init':
/usr/src/madwifi/net80211/ieee80211_beacon.c:98: warning: pointer targets in assignment differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto.c:45:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto_none.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto_none.c:40:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_input.o
In file included from /usr/src/madwifi/net80211/ieee80211_input.c:44:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_node.o
In file included from /usr/src/madwifi/net80211/ieee80211_node.c:44:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_output.o
In file included from /usr/src/madwifi/net80211/ieee80211_output.c:44:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /usr/src/madwifi/net80211/ieee80211_output.c:48:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/net80211/ieee80211_output.c: In function 'ieee80211_add_rates':/usr/src/madwifi/net80211/ieee80211_output.c:1204: warning: pointer targets in return differ in signedness
/usr/src/madwifi/net80211/ieee80211_output.c: In function 'ieee80211_send_probereq':
/usr/src/madwifi/net80211/ieee80211_output.c:1706: warning: pointer targets in assignment differ in signedness
/usr/src/madwifi/net80211/ieee80211_output.c: In function 'ieee80211_send_mgmt':/usr/src/madwifi/net80211/ieee80211_output.c:1833: warning: pointer targets in assignment differ in signedness
/usr/src/madwifi/net80211/ieee80211_output.c:2015: warning: pointer targets in assignment differ in signedness
/usr/src/madwifi/net80211/ieee80211_output.c:2093: warning: pointer targets in assignment differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_power.o
In file included from /usr/src/madwifi/net80211/ieee80211_power.c:44:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_proto.o
In file included from /usr/src/madwifi/net80211/ieee80211_proto.c:45:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_scan.o
In file included from /usr/src/madwifi/net80211/ieee80211_scan.c:43:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/net80211/ieee80211_scan.c: In function 'scan_next':
/usr/src/madwifi/net80211/ieee80211_scan.c:692: warning: pointer targets in passing argument 5 of 'ieee80211_send_probereq' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_wireless.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi/net80211/ieee80211_wireless.c:47:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'encode_ie':
/usr/src/madwifi/net80211/ieee80211_wireless.c:1315: warning: pointer targets in passing argument 1 of 'sprintf' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'giwscan_cb':
/usr/src/madwifi/net80211/ieee80211_wireless.c:1364: warning: pointer targets in passing argument 4 of 'iwe_stream_add_point' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'ieee80211_ioctl_wdsmac':
/usr/src/madwifi/net80211/ieee80211_wireless.c:2839: warning: pointer targets in passing argument 1 of 'ether_sprintf' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'ieee80211_ioctl_wdsdelmac':
/usr/src/madwifi/net80211/ieee80211_wireless.c:2872: warning: pointer targets in passing argument 1 of 'ether_sprintf' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'ieee80211_ioctl_addmac':
/usr/src/madwifi/net80211/ieee80211_wireless.c:2891: warning: pointer targets in passing argument 2 of 'acl->iac_add' differ in signedness
/usr/src/madwifi/net80211/ieee80211_wireless.c: In function 'ieee80211_ioctl_delmac':
/usr/src/madwifi/net80211/ieee80211_wireless.c:2909: warning: pointer targets in passing argument 2 of 'acl->iac_remove' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_linux.o
In file included from /usr/src/madwifi/net80211/ieee80211_linux.c:39:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_monitor.o
In file included from /usr/src/madwifi/net80211/ieee80211_monitor.c:40:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/net80211/ieee80211_monitor.c: In function 'ieee80211_input_monitor':
/usr/src/madwifi/net80211/ieee80211_monitor.c:227: warning: pointer targets in passing argument 1 of 'strncpy' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_acl.o
In file included from /usr/src/madwifi/net80211/ieee80211_acl.c:51:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto_ccmp.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto_ccmp.c:42:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_scan_ap.o
In file included from /usr/src/madwifi/net80211/ieee80211_scan_ap.c:43:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_scan_sta.o
In file included from /usr/src/madwifi/net80211/ieee80211_scan_sta.c:43:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto_tkip.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto_tkip.c:42:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_crypto_wep.o
In file included from /usr/src/madwifi/net80211/ieee80211_crypto_wep.c:40:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /usr/src/madwifi/net80211/ieee80211_xauth.o
In file included from /usr/src/madwifi/net80211/ieee80211_xauth.c:53:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  LD [M]  /usr/src/madwifi/net80211/wlan.o
  LD [M]  /usr/src/madwifi/net80211/wlan_wep.o
  LD [M]  /usr/src/madwifi/net80211/wlan_tkip.o
  LD [M]  /usr/src/madwifi/net80211/wlan_ccmp.o
  LD [M]  /usr/src/madwifi/net80211/wlan_acl.o
  LD [M]  /usr/src/madwifi/net80211/wlan_xauth.o
  LD [M]  /usr/src/madwifi/net80211/wlan_scan_sta.o
  LD [M]  /usr/src/madwifi/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
  CC      /usr/src/madwifi/net80211/wlan.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan.ko
  CC      /usr/src/madwifi/net80211/wlan_acl.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_acl.ko
  CC      /usr/src/madwifi/net80211/wlan_ccmp.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_ccmp.ko
  CC      /usr/src/madwifi/net80211/wlan_scan_ap.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_scan_ap.ko
  CC      /usr/src/madwifi/net80211/wlan_scan_sta.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_scan_sta.ko
  CC      /usr/src/madwifi/net80211/wlan_tkip.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_tkip.ko
  CC      /usr/src/madwifi/net80211/wlan_wep.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_wep.ko
  CC      /usr/src/madwifi/net80211/wlan_xauth.mod.o
  LD [M]  /usr/src/madwifi/net80211/wlan_xauth.ko
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: Leaving directory `/usr/src/madwifi/net80211'
make[1]: Entering directory `/usr/src/madwifi/ath_rate/sample'
make -C /lib/modules/2.6.12-custom/build SUBDIRS=/usr/src/madwifi/ath_rate/sample MODVERDIR=/usr/src/madwifi/ath_rate/sample/../../symbols modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
  CC [M]  /usr/src/madwifi/ath_rate/sample/sample.o
In file included from /usr/src/madwifi/ath_rate/sample/sample.c:47:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  LD [M]  /usr/src/madwifi/ath_rate/sample/ath_rate_sample.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
  CC      /usr/src/madwifi/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /usr/src/madwifi/ath_rate/sample/ath_rate_sample.ko
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: Leaving directory `/usr/src/madwifi/ath_rate/sample'
make[1]: Entering directory `/usr/src/madwifi/ath'
make -C /lib/modules/2.6.12-custom/build SUBDIRS=/usr/src/madwifi/ath MODVERDIR=/usr/src/madwifi/ath/../symbols modules
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
  CC [M]  /usr/src/madwifi/ath/if_ath.o
In file included from /usr/src/madwifi/ath/if_ath.c:51:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/usr/src/madwifi/ath/if_ath.c: In function 'ath_attach':
/usr/src/madwifi/ath/if_ath.c:611: warning: pointer targets in passing argument 1 of 'strcpy' differ in signedness
/usr/src/madwifi/ath/if_ath.c: In function 'ath_grppoll_start':
/usr/src/madwifi/ath/if_ath.c:5718: warning: pointer targets in passing argument 1 of 'sscanf' differ in signedness
/usr/src/madwifi/ath/if_ath.c:5721: warning: pointer targets in passing argument 1 of 'strcmp' differ in signedness
/usr/src/madwifi/ath/if_ath.c:5721: warning: pointer targets in passing argument 2 of 'strcmp' differ in signedness
/usr/src/madwifi/ath/if_ath.c:5725: warning: pointer targets in passing argument 1 of 'sscanf' differ in signedness
/usr/src/madwifi/ath/if_ath.c:5726: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
/usr/src/madwifi/ath/if_ath.c:5726: warning: pointer targets in passing argument 1 of 'strlen' differ in signedness
/usr/src/madwifi/ath/if_ath.c: In function 'ath_getchannels':
/usr/src/madwifi/ath/if_ath.c:8284: warning: pointer targets in passing argument 4 of 'ath_hal_init_channels' differ in signedness
  CC [M]  /usr/src/madwifi/ath/if_ath_pci.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi/ath/if_ath_pci.c:50:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  LD [M]  /usr/src/madwifi/ath/ath_pci.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi/ath_hal/hal.o
  CC      /usr/src/madwifi/ath/ath_pci.mod.o
  LD [M]  /usr/src/madwifi/ath/ath_pci.ko
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: Leaving directory `/usr/src/madwifi/ath'
make -C ./tools  all || exit 1
make[1]: Entering directory `/usr/src/madwifi/tools'
gcc -o athstats -g -O2 -Wall -include ../include/compat.h -I. -I../hal -I.. -I../ath  athstats.c
athstats.c: In function 'main':
athstats.c:346: warning: 'sigblock' is deprecated (declared at /usr/include/signal.h:181)
athstats.c:348: warning: 'sigpause' is deprecated (declared at /usr/include/signal.h:158)
athstats.c:349: warning: 'sigsetmask' is deprecated (declared at /usr/include/signal.h:184)
gcc -o 80211stats -g -O2 -Wall -include ../include/compat.h -I. -I../hal -I..  80211stats.c
gcc -o athkey -g -O2 -Wall -include ../include/compat.h -I. -I../hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -include ../include/compat.h -I. -I../hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -include ../include/compat.h -I. -I../hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -include ../include/compat.h -I. -I../hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -include ../include/compat.h -I. -I../hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -include ../include/compat.h -I. -I../hal -I..  wlanconfig.c
make[1]: Leaving directory `/usr/src/madwifi/tools'
root@wintermute:/usr/src/madwifi# modprobe ath_pci
FATAL: Module ath_pci not found.
root@wintermute:/usr/src/madwifi#

thanks,
ephman

---

### Post by Lambert on 2005-12-30
It doesn't look like you did the final step. You just did make and then tried to insert module.

next step should be

```
sudo make install
```

---

### Post by ephman on 2005-12-30
duh!!  thanks.

---

