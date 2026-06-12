---
title: "problems with installing rltk8187 driver"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by EternalDream8 on 2010-10-27
```
$ wget http://dl.aircrackng.org/drivers/rtl8187_linux_26.1010.zip
$ wget http://dl.dropbox.com/u/1522424/rtl8187_2.6.34.patch
$ unzip rtl8187_linux_26.1010.zip
$ cd rtl8187_linux_26.1010.0622.2006
$ tar xzf drv.tar.gz
$ tar xzf stack.tar.gz
$ patch -Np1 -i ../rtl8187_2.6.34.patch
$ make
$ sudo make install
$ sudo rmmod r8187 rtl8187 mac80211 cfg80211
$ sudo modprobe r8187
```

when I try using ```
 sudo rmmod r8187 rtl8187 mac80211 cfg80211
```
it says that :
```
ERROR: Module r8187 does not exist in /proc/modules
ERROR: Module rtl8187 does not exist in /proc/modules
ERROR: Module mac80211 does not exist in /proc/modules
ERROR: Module cfg80211 does not exist in /proc/modules

```

---

### Post by chili555 on 2010-10-27
> ERROR: Module r8187 does not exist in /proc/modules
ERROR: Module rtl8187 does not exist in /proc/modules
ERROR: Module mac80211 does not exist in /proc/modules
ERROR: Module cfg80211 does not exist in /proc/modulesI think that means that the modules were not loaded in the first place. Your card did not grab the modules.

Are you very certain the driver rtl8187 is correct for your card?

---

### Post by EternalDream8 on 2010-10-27
rtl8187l

---

### Post by chili555 on 2010-10-27
So, did you go on to the last step?```
sudo modprobe r8187
```Did your card come to life? If so, you are all set!

---

### Post by alex19931 on 2011-04-22
men I've almost the same **** but mines says:


make
rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/home/aron/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/2.6.35-28-generic/build M=/home/aron/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/aron/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.o
/home/aron/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.c:48: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[3]: *** [/home/aron/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.o] Error 1
make[2]: *** [_module_/home/aron/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/aron/rtl8187_linux_26.1010.0622.2006/ieee80211'
make: *** [all] Error 2


please tell me what should i do?

---

### Post by chili555 on 2011-04-22
Please try:```
sudo touch /usr/src/linux-headers-`uname -r`/include/linux/autoconf.h
```Then make and sudo make install again. Post back any errors.

Those tick marks are on the left side of my US keyboard on the same key with ~.

---

