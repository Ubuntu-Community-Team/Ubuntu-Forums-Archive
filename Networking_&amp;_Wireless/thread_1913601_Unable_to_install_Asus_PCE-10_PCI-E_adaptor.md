---
title: "Unable to install Asus PCE-10 PCI-E adaptor"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by Hill_guy on 2012-01-22
I have been struggling with firmware installation for this adaptor.
Here's the details:
Asus PCE-10 PCI-E , chip marked 'RTL8188CE'
Network Controller: Realtek Semiconductor Co, Ltd. Device 8176(rev 01)
Subsystem: AsusTek Computer Inc. Device 84b5
Ubuntu 10.04 (lucid), 2.6.32-37-generic-pae
I have tried processes spelled out in another post (**No wireless)**, but was not able to find the exact download called out, and downloaded 92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz
as it appeared to be correct for 2.6.32-37-generic-pae
Extraction, and running the terminal commands resulted in errors.
So, to start, am I going down the right path with the correct download?
Thank you in advance for your help!

---

### Post by chili555 on 2012-01-23
Compiling these packages requires two prerequisites: *build-essential* and *linux-headers-generic*. Please get a wired ethernet connection and install these packages. Then try the compile again:```
cd Downloads/92ce_se_de_linux_mac80211_0005.1230.2011
```^^^Or wherever it's downloaded.```
sudo su
make clean
make
make install
exit
```If there are still errors, post the exact error and we'll be glad to help you.

---

### Post by Hill_guy on 2012-01-23
OK, here's the result
william@william-desktop:~$ cd wireless_driver
william@william-desktop:~/wireless_driver$ ls
92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz  debug.h   rc.h
base.c                                           efuse.c   readme
base.h                                           efuse.h   regd.c
cam.c                                            firmware  regd.h
cam.h                                            Kconfig   release_note
compat                                           Makefile  rtl8192ce
compat.h                                         pci.c     rtl8192de
compat-wireless-3.0-2.tar.bz2                    pci.h     rtl8192se
core.c                                           ps.c      stats.c
core.h                                           ps.h      stats.h
debug.c                                          rc.c      wifi.h
william@william-desktop:~/wireless_driver$ sudo su
root@william-desktop:/home/william/wireless_driver# make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Entering directory `/home/william/wireless_driver/rtl8192ce'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/william/wireless_driver/rtl8192ce'
make[1]: Entering directory `/home/william/wireless_driver/rtl8192se'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/william/wireless_driver/rtl8192se'
make[1]: Entering directory `/home/william/wireless_driver/rtl8192de'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/william/wireless_driver/rtl8192de'
root@william-desktop:/home/william/wireless_driver# make
make -C /lib/modules/2.6.32-37-generic-pae/build M=/home/william/wireless_driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-37-generic-pae'
  CC [M]  /home/william/wireless_driver/base.o
In file included from /home/william/wireless_driver/base.c:32:
/home/william/wireless_driver/wifi.h: In function ‘rtl_find_sta’:
/home/william/wireless_driver/wifi.h:2094: warning: passing argument 1 of ‘ieee80211_find_sta’ from incompatible pointer type
include/net/mac80211.h:2086: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
In file included from /home/william/wireless_driver/base.c:34:
/home/william/wireless_driver/base.h: At top level:
/home/william/wireless_driver/base.h:143: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/william/wireless_driver/base.h:143: warning: its scope is only this definition or declaration, which is probably not what you want
/home/william/wireless_driver/base.c: In function ‘_rtl_init_mac80211’:
/home/william/wireless_driver/base.c:322: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:322: error: (Each undeclared identifier is reported only once
/home/william/wireless_driver/base.c:322: error: for each function it appears in.)
/home/william/wireless_driver/base.c: In function ‘rtl_tx_agg_start’:
/home/william/wireless_driver/base.c:991: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2033: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/william/wireless_driver/base.c: In function ‘rtl_tx_agg_stop’:
/home/william/wireless_driver/base.c:1020: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2074: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/william/wireless_driver/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/william/wireless_driver/base.c:1274: error: implicit declaration of function ‘ieee80211_connection_loss’
/home/william/wireless_driver/base.c: At top level:
/home/william/wireless_driver/base.c:1332: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/william/wireless_driver/base.c:1332: error: parameter 2 (‘smps’) has incomplete type
/home/william/wireless_driver/base.c: In function ‘rtl_make_smps_action’:
/home/william/wireless_driver/base.c:1352: error: ‘WLAN_HT_ACTION_SMPS’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1354: error: ‘IEEE80211_SMPS_AUTOMATIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1355: error: ‘IEEE80211_SMPS_NUM_MODES’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1357: error: ‘IEEE80211_SMPS_OFF’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1359: error: ‘WLAN_HT_SMPS_CONTROL_DISABLED’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1361: error: ‘IEEE80211_SMPS_STATIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1363: error: ‘WLAN_HT_SMPS_CONTROL_STATIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1365: error: ‘IEEE80211_SMPS_DYNAMIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1367: error: ‘WLAN_HT_SMPS_CONTROL_DYNAMIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c: At top level:
/home/william/wireless_driver/base.c:1376: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/william/wireless_driver/base.c:1376: error: parameter 3 (‘smps’) has incomplete type
/home/william/wireless_driver/base.c: In function ‘rtl_send_smps_action’:
/home/william/wireless_driver/base.c:1404: error: type of formal parameter 2 is incomplete
make[2]: *** [/home/william/wireless_driver/base.o] Error 1
make[1]: *** [_module_/home/william/wireless_driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-37-generic-pae'
make: *** [all] Error 2
root@william-desktop:/home/william/wireless_driver# make install
make -C /lib/modules/2.6.32-37-generic-pae/build M=/home/william/wireless_driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-37-generic-pae'
  CC [M]  /home/william/wireless_driver/base.o
In file included from /home/william/wireless_driver/base.c:32:
/home/william/wireless_driver/wifi.h: In function ‘rtl_find_sta’:
/home/william/wireless_driver/wifi.h:2094: warning: passing argument 1 of ‘ieee80211_find_sta’ from incompatible pointer type
include/net/mac80211.h:2086: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
In file included from /home/william/wireless_driver/base.c:34:
/home/william/wireless_driver/base.h: At top level:
/home/william/wireless_driver/base.h:143: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/william/wireless_driver/base.h:143: warning: its scope is only this definition or declaration, which is probably not what you want
/home/william/wireless_driver/base.c: In function ‘_rtl_init_mac80211’:
/home/william/wireless_driver/base.c:322: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:322: error: (Each undeclared identifier is reported only once
/home/william/wireless_driver/base.c:322: error: for each function it appears in.)
/home/william/wireless_driver/base.c: In function ‘rtl_tx_agg_start’:
/home/william/wireless_driver/base.c:991: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2033: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/william/wireless_driver/base.c: In function ‘rtl_tx_agg_stop’:
/home/william/wireless_driver/base.c:1020: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2074: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/william/wireless_driver/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/william/wireless_driver/base.c:1274: error: implicit declaration of function ‘ieee80211_connection_loss’
/home/william/wireless_driver/base.c: At top level:
/home/william/wireless_driver/base.c:1332: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/william/wireless_driver/base.c:1332: error: parameter 2 (‘smps’) has incomplete type
/home/william/wireless_driver/base.c: In function ‘rtl_make_smps_action’:
/home/william/wireless_driver/base.c:1352: error: ‘WLAN_HT_ACTION_SMPS’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1354: error: ‘IEEE80211_SMPS_AUTOMATIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1355: error: ‘IEEE80211_SMPS_NUM_MODES’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1357: error: ‘IEEE80211_SMPS_OFF’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1359: error: ‘WLAN_HT_SMPS_CONTROL_DISABLED’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1361: error: ‘IEEE80211_SMPS_STATIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1363: error: ‘WLAN_HT_SMPS_CONTROL_STATIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1365: error: ‘IEEE80211_SMPS_DYNAMIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c:1367: error: ‘WLAN_HT_SMPS_CONTROL_DYNAMIC’ undeclared (first use in this function)
/home/william/wireless_driver/base.c: At top level:
/home/william/wireless_driver/base.c:1376: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/william/wireless_driver/base.c:1376: error: parameter 3 (‘smps’) has incomplete type
/home/william/wireless_driver/base.c: In function ‘rtl_send_smps_action’:
/home/william/wireless_driver/base.c:1404: error: type of formal parameter 2 is incomplete
make[2]: *** [/home/william/wireless_driver/base.o] Error 1
make[1]: *** [_module_/home/william/wireless_driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-37-generic-pae'
make: *** [all] Error 2
root@william-desktop:/home/william/wireless_driver#

---

### Post by chili555 on 2012-01-24
Here is a quote from the README in the package you downloaded:> ========================================================================================
		III. Compile & Installation & uninstall [2.6.24, 2.6.34]
========================================================================================
We don't support kernel 2.6.24-2.6.34 directly, Because there are
lots of issues in mac80211 from kernel 2.6.24-2.6.34,
So we suggest you to use the latest kernel >= 2.6.35.

but if you want to use our driver in an old kernel,
you can use compat-wireless. this methord can support all kernel
versions higher than 2.6.24, and you can use all functions
of our driver like you use it in the latest kernel version.

You can get more informations of compat-wireless from:
[http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)

you should use the following commands to Compile, Installation, or uninstall the driver:

	1. Change to Super User
	   sudo su

	2. install compat-wireless driver
	   ./compat/script/compat-install.sh
		 
	3. reboot
	   reboot

	4. uninstall driver
	   ./compat/script/compat-uninstall.sh

	5. you can get more information form follwing webset for how to use compat-wireless:
	   [http://wireless.kernel.org/en/users/Download/stable](http://wireless.kernel.org/en/users/Download/stable)
	   Therefor, I suggest you try:```
cd wireless_driver
sudo su
./compat/script/compat-install.sh
reboot
```Any errors?

For the benefit of the searchers, if you run 'make' and see this, please stop. All further steps will be errors also:> make[2]: *** [/home/william/wireless_driver/base.o] Error 1
make[1]: *** [_module_/home/william/wireless_driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-37-generic-pae'
[COLOR="Red"]**make: *** [all] Error**[/COLOR] 2

---

### Post by Hill_guy on 2012-01-24
I did as you suggested. A lot of text was generated in the process.
The only place I saw errors was near the end as follows.
Also, I see a kernel update to Version 2.6.32-38.83: and wondering what effect it will have.

make -C /lib/modules/2.6.32-37-generic-pae/build M=/home/william/wireless_driver/compat-wireless-3.0-2 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-37-generic-pae' 
  CC [M]  /home/william/wireless_driver/compat-wireless-3.0-2/net/mac80211/rc80211_pid_algo.o 
/home/william/wireless_driver/compat-wireless-3.0-2/net/mac80211/rc80211_pid_algo.c:469: error: redefinition of ‘rc80211_pid_init’ 
/home/william/wireless_driver/compat-wireless-3.0-2/net/mac80211/rate.h:128: note: previous definition of ‘rc80211_pid_init’ was here 
/home/william/wireless_driver/compat-wireless-3.0-2/net/mac80211/rc80211_pid_algo.c:474: error: redefinition of ‘rc80211_pid_exit’ 
/home/william/wireless_driver/compat-wireless-3.0-2/net/mac80211/rate.h:132: note: previous definition of ‘rc80211_pid_exit’ was here 
make[3]: *** [/home/william/wireless_driver/compat-wireless-3.0-2/net/mac80211/rc80211_pid_algo.o] Error 1 
make[2]: *** [/home/william/wireless_driver/compat-wireless-3.0-2/net/mac80211] Error 2 
make[1]: *** [_module_/home/william/wireless_driver/compat-wireless-3.0-2] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-37-generic-pae' 
make: *** [modules] Error 2 
 
success install driver rtlwifi in compat-wireless, you can use driver after reboot 
 
/home/william/wireless_driver/compat/3.0-2 
root@william-desktop:/home/william/wireless_driver#

---

### Post by chili555 on 2012-01-25
I have fiddled with this thing for an hour; it makes little sense to me. There is a mechanism to use the 2.6.39 version included in the file but I am confounded as to how to make it work. Therefor, you have the same issue as before; a new driver on an old kernel and because there are improvements in the kernel and gcc, etc., the driver won't compile. I suggest one of two options; either install the latest Ubuntu version 11.10 where the device should work out of the box or else email Realtek, the developer of the package you downloaded and ask about your 'make' errors.

---

### Post by Hill_guy on 2012-01-25
Thank you very much for your time and effort. It is much appreciated.
I am very committed to Linux over the alternatives, and will continue to pursue a solution.
I will update this thread with what I find.****

---

### Post by chili555 on 2012-01-26
Excellent! We will await your findings and be happy to help.

---

