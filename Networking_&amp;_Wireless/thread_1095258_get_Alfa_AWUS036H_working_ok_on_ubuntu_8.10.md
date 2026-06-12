---
title: "get Alfa AWUS036H working ok on ubuntu 8.10"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by vze57gc8 on 2009-03-13
rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl818x/rtl8187.ko
rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko




wget [http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip)
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/

wget [http://patches.aircrack-ng.org/rtl8187_2.6.27.patch](http://patches.aircrack-ng.org/rtl8187_2.6.27.patch)

tar xzf drv.tar.gz
tar xzf stack.tar.gz

sudo gedit ./beta-8187/r8187.h
and find the line:

#include <asm/semaphore.h>

and change it to:

#include <linux/semaphore.h>

sudo patch -Np1 -i rtl8187_2.6.27.patch

remove old drivers
rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl818x/rtl8187.ko
rm -rf /lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
rm -rf /lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko

Then I put rtl8187 to the blacklist:

sudo gedit /etc/modprobe.d/blacklist and add “blacklist rtl8187” as a new line.
Then remove the present driver:

sudo ifconfig wlan0 down
sudo rmmod rtl8187

make
sudo make install

reboot & enjoy

---

### Post by dark2bone on 2009-03-27
Really thank you !!
its working like a charm now :popcorn:

---

