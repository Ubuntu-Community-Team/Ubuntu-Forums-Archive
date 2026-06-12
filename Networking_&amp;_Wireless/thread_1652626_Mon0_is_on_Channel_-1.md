---
title: "Mon0 is on Channel -1"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by mak1991 on 2010-12-25
Hello,
i have a problem with using Aircrack. When i want do the regestration and typ, there come mon0 is on channel-1, but the AP uses channel1 

My Wireless card driver is rt2800pci

I use ubuntu since 3 days

---

### Post by mak1991 on 2010-12-26
no one know something ?

---

### Post by spiky001 on 2010-12-26
Hi is this to start airmon-ng?

---

### Post by bkratz on 2010-12-26
> **mak1991 said:**
> no one know something ?



There is probably something useful in this thread. I don't use Aircrack, so not really sure.

[http://ubuntuforums.org/showthread.php?t=1598930&highlight=channel](http://ubuntuforums.org/showthread.php?t=1598930&highlight=channel)

---

### Post by nova47 on 2011-03-21
I also had this problem. It seems to be a relatively recent issue. You can find solutions here. It's a problem with compat-wireless.

[http://trac.aircrack-ng.org/ticket/742](http://trac.aircrack-ng.org/ticket/742)

This solution worked for me.

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2)
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget [http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch](http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch)
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget [http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot

---

