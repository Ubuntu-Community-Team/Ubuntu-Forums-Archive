---
title: "Realtek RTL8192CE driver : does not compile"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by mamboknave on 2011-11-18
System (laptop): HP Pavilion g6-1c77nr
Operating system: Ubuntu 10.04 64bit, kernel 2.6.32-35

The update from kernel -34 to -35 has disrupted the Wireless connection whose adapter is the Realtek RTL8188CE (and uses the driver RTL8192CE).

I downloaded and tried to install the newest driver: rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011

Here below is how the make command fails.

Any idea how I should resolve this?


> sudo make

make -C /lib/modules/2.6.32-35-generic/build M=/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-35-generic'
  CC [M]  /home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.o
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c: In function ‘_rtl_init_mac80211’:
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c:320: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c:320: error: (Each undeclared identifier is reported only once
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c:320: error: for each function it appears in.)
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c:1258: error: implicit declaration of function ‘ieee80211_connection_loss’
make[2]: *** [/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.o] Error 1
make[1]: *** [_module_/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-35-generic'
make: *** [all] Error 2

---

### Post by JoeFriday49 on 2011-11-30
> **mamboknave said:**
> System (laptop): HP Pavilion g6-1c77nr
Operating system: Ubuntu 10.04 64bit, kernel 2.6.32-35

The update from kernel -34 to -35 has disrupted the Wireless connection whose adapter is the Realtek RTL8188CE (and uses the driver RTL8192CE).

I downloaded and tried to install the newest driver: rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011

Here below is how the make command fails.

Any idea how I should resolve this?


> sudo make

make -C /lib/modules/2.6.32-35-generic/build M=/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-35-generic'
  CC [M]  /home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.o
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c: In function ‘_rtl_init_mac80211’:
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c:320: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c:320: error: (Each undeclared identifier is reported only once
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c:320: error: for each function it appears in.)
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.c:1258: error: implicit declaration of function ‘ieee80211_connection_loss’
make[2]: *** [/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011/base.o] Error 1
make[1]: *** [_module_/home/paolo/Downloads/rtl_92ce_92se_92de_linux_mac80211_0004.0816.2011] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-35-generic'
make: *** [all] Error 2


Did you ever find a solution?  I'm getting basically the same error code, just in different directory structure:
<snip>
[COLOR=Blue]root@ubuntu:/home/joefriday49/Downloads/RTL8188CE/work# make
make -C /lib/modules/2.6.32-35-generic/build M=/home/joefriday49/Downloads/RTL8188CE/work modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-35-generic'
  CC [M]  /home/joefriday49/Downloads/RTL8188CE/work/base.o
/home/joefriday49/Downloads/RTL8188CE/work/base.c: In function ‘_rtl_init_mac80211’:
/home/joefriday49/Downloads/RTL8188CE/work/base.c:320: error:  ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this  function)
/home/joefriday49/Downloads/RTL8188CE/work/base.c:320: error: (Each undeclared identifier is reported only once
/home/joefriday49/Downloads/RTL8188CE/work/base.c:320: error: for each function it appears in.)
/home/joefriday49/Downloads/RTL8188CE/work/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/joefriday49/Downloads/RTL8188CE/work/base.c:1258: error: implicit declaration of function ‘ieee80211_connection_loss’
make[2]: *** [/home/joefriday49/Downloads/RTL8188CE/work/base.o] Error 1
make[1]: *** [_module_/home/joefriday49/Downloads/RTL8188CE/work] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-35-generic'
make: *** [all] Error 2[/COLOR]

---

