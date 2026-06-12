---
title: "erroe with manual installation of realtek RTL 8188CE driver"
date: 2012-03-10
forum: Networking &amp; Wireless
---

### Post by dan0804smith on 2012-03-10
downloaded tar.gz from realtex for my linux distro
10.04.3 LTS  kernal 2.6.32-38

downloaded it to desktop

extracted to desktop

renames folder to 'x'

ran in the terminal:

sudo apt-get install build-essential

sudo apt-get install build-essential linux-headers-generic

successful 

ran: 

daniel@daniel-laptop:~$ cd Desktop/x
daniel@daniel-laptop:~/Desktop/x$ sudo su
[sudo] password for daniel: 
root@daniel-laptop:/home/daniel/Desktop/x# make
make -C /lib/modules/2.6.32-38-generic/build M=/home/daniel/Desktop/x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-38-generic'
  CC [M]  /home/daniel/Desktop/x/base.o
In file included from /home/daniel/Desktop/x/base.c:32:
/home/daniel/Desktop/x/wifi.h: In function ‘rtl_find_sta’:
/home/daniel/Desktop/x/wifi.h:2094: warning: passing argument 1 of ‘ieee80211_find_sta’ from incompatible pointer type
include/net/mac80211.h:2086: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
In file included from /home/daniel/Desktop/x/base.c:34:
/home/daniel/Desktop/x/base.h: At top level:
/home/daniel/Desktop/x/base.h:143: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/daniel/Desktop/x/base.h:143: warning: its scope is only this definition or declaration, which is probably not what you want
/home/daniel/Desktop/x/base.c: In function ‘_rtl_init_mac80211’:
/home/daniel/Desktop/x/base.c:322: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:322: error: (Each undeclared identifier is reported only once
/home/daniel/Desktop/x/base.c:322: error: for each function it appears in.)
/home/daniel/Desktop/x/base.c: In function ‘rtl_tx_agg_start’:
/home/daniel/Desktop/x/base.c:991: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2033: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/daniel/Desktop/x/base.c: In function ‘rtl_tx_agg_stop’:
/home/daniel/Desktop/x/base.c:1020: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2074: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/daniel/Desktop/x/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/daniel/Desktop/x/base.c:1274: error: implicit declaration of function ‘ieee80211_connection_loss’
/home/daniel/Desktop/x/base.c: At top level:
/home/daniel/Desktop/x/base.c:1332: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/daniel/Desktop/x/base.c:1332: error: parameter 2 (‘smps’) has incomplete type
/home/daniel/Desktop/x/base.c: In function ‘rtl_make_smps_action’:
/home/daniel/Desktop/x/base.c:1352: error: ‘WLAN_HT_ACTION_SMPS’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:1354: error: ‘IEEE80211_SMPS_AUTOMATIC’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:1355: error: ‘IEEE80211_SMPS_NUM_MODES’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:1357: error: ‘IEEE80211_SMPS_OFF’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:1359: error: ‘WLAN_HT_SMPS_CONTROL_DISABLED’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:1361: error: ‘IEEE80211_SMPS_STATIC’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:1363: error: ‘WLAN_HT_SMPS_CONTROL_STATIC’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:1365: error: ‘IEEE80211_SMPS_DYNAMIC’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c:1367: error: ‘WLAN_HT_SMPS_CONTROL_DYNAMIC’ undeclared (first use in this function)
/home/daniel/Desktop/x/base.c: At top level:
/home/daniel/Desktop/x/base.c:1376: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/daniel/Desktop/x/base.c:1376: error: parameter 3 (‘smps’) has incomplete type
/home/daniel/Desktop/x/base.c: In function ‘rtl_send_smps_action’:
/home/daniel/Desktop/x/base.c:1404: error: type of formal parameter 2 is incomplete
make[2]: *** [/home/daniel/Desktop/x/base.o] Error 1
make[1]: *** [_module_/home/daniel/Desktop/x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-38-generic'
make: *** [all] Error 2


what is this error?

---

### Post by chili555 on 2012-03-14
You forgot to PM me the link to this thread.

Which version did you download? I suspect you have the version for newer kernels and you have an older kernel.

---

