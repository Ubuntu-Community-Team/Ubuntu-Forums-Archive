---
title: "Trouble with Wireless Monitor Mode"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by Jackarow on 2010-11-22
I am attempting to put my wireless card into monitor mode on a specific channel via the airmon-ng tool. While my card does indeed go into monitor mode just fine, I cannot choose which channel to launch the mon0 interface on.

Some other user had this issue and found a fix be applying a couple of patches per this bug: [https://bugs.launchpad.net/ubuntu/+source/aircrack-ng/+bug/643788](https://bugs.launchpad.net/ubuntu/+source/aircrack-ng/+bug/643788)

The fix is as follows:
--------------------------------------
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
---------------------------------

When I first applied the fix it worked like a charm. However, at some point it has quit working for me. 

If the forum users would be so kind as to help me troubleshoot, I would be very grateful.

---

### Post by ~Middle on 2011-03-13
This worked for me, however my PC started freezing soon afterwards, the only thing that i can think was causing it was this!

So any ideas on how to remove it from the system?

P.S It worked fine on my laptop, just my PC freezes up now

---

