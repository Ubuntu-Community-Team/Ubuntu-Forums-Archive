---
title: "Two errors came out when making the wireless driver"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by ChipWolf on 2010-01-08
lspci -nn:
05:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
uname  -rm
2.6.31-17-generic i686

root@ubuntu:/home/ouyes/Desktop/compat-wireless-2.6.31-rc7# lsb_release -d
Description:    Ubuntu 9.10
root@ubuntu:/home/ouyes/Desktop/compat-wireless-2.6.31-rc7# uname  -rm
2.6.31-17-generic i686
root@ubuntu:/home/ouyes/Desktop/compat-wireless-2.6.31-rc7# make
make -C /lib/modules/2.6.31-17-generic/build M=/home/ouyes/Desktop/compat-wireless-2.6.31-rc7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
make[3]: *** No rule to make target `/home/ouyes/Desktop/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.c', needed by `/home/ouyes/Desktop/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.o'.  Stop.
make[2]: *** [/home/ouyes/Desktop/compat-wireless-2.6.31-rc7/drivers/misc/eeprom] Error 2
make[1]: *** [_module_/home/ouyes/Desktop/compat-wireless-2.6.31-rc7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [modules] Error 2
root@ubuntu:/home/ouyes/Desktop/compat-wireless-2.6.31-rc7# 
---------------------------------------------------------------------------------------------
root@ubuntu:/home/ouyes/Desktop/madwifi-0.9.4# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/ouyes/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.o
In file included from /home/ouyes/Desktop/madwifi-0.9.4/ath/../net80211/ieee80211_monitor.h:45,
                 from /home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c:71:
/home/ouyes/Desktop/madwifi-0.9.4/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_attach':
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c:402: error: 'struct net_device' has no member named 'priv'
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c:678: error: 'struct net_device' has no member named 'open'
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c:679: error: 'struct net_device' has no member named 'stop'
......there were a long list of this kind of line i deleted some
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_announce':
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c:9779: error: 'struct net_device' has no member named 'priv'
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rcv_dev_event':
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c:9926: error: 'struct net_device' has no member named 'priv'
/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.c:9928: error: 'struct net_device' has no member named 'open'
make[3]: *** [/home/ouyes/Desktop/madwifi-0.9.4/ath/if_ath.o] Error 1
make[2]: *** [/home/ouyes/Desktop/madwifi-0.9.4/ath] Error 2
make[1]: *** [_module_/home/ouyes/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [modules] Error 2
root@ubuntu:/home/ouyes/Desktop/madwifi-0.9.4# /ouyes
both come out errors why?Did i use the wrong driver?
any info you need please tell me.(sorry it's really long,waste the store space of the community .)

---

### Post by changingstate on 2010-01-08
The kernel devs have broken compatibility for older network drivers, which is why you're getting the build errors with madwifi. There's a snapshot on the main page of [http://madwifi-project.org/](http://madwifi-project.org/) for 2.6.25 and later kernels which claims to have resolved the compilation issues, I suggest you try that.

---

### Post by ChipWolf on 2010-01-08
> **changingstate said:**
> The kernel devs have broken compatibility for older network drivers, which is why you're getting the build errors with madwifi. There's a snapshot on the main page of [http://madwifi-project.org/](http://madwifi-project.org/) for 2.6.25 and later kernels which claims to have resolved the compilation issues, I suggest you try that.
  thanks  to chang
your suggestion works, the problem is my carefulness.

---

