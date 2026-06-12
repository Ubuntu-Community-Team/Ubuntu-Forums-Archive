---
title: "Manualy paching aircrack-ng?"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by messiah on 2011-08-13
Hi people, I was wondering if there is a way to manually patch Aircrack -ng with 'airodump-ng-channel-handling-broken-fix.patch' without installing compact wireless package, because I end up with nonfunctional network when I compile compact wireless package. If possible where to paste that patch?

sys info

11.04 natty

Linux 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux



Bus 008 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0cf3:1006 Atheros Communications, Inc. TP-Link **TL-WN422G v2 802.11g [Atheros AR9271]**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b083 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by realzippy on 2011-08-13
There are tons off stuff patching atheros drivers for aircrack ng out in the net...

---

### Post by messiah on 2011-08-13
I understand that injection might or might not work but main problem is -1 fixed chanel. As I said before I tried to solve problem by installing and patching compact wireless 'compat-wireless-3.1-rc1-1' and my network is down until I remove compact wireless package! Now I am looking a way apply channel-negative-one-maxim.patch without installing compact wireless. My USB wlan card is recognized properly as [B]Atheros Communications, Inc. TP-Link TL-WN422G v2 802.11g [Atheros AR9271]
[/B] even the aircrack-ng suite correctly recognize card.

I was  using this method when i installed compact wireless

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

One other thing that confused me is part when I need to replace line 

**#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build** with this one

**#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build** that was already there so I did not replace nothing.

---

### Post by messiah on 2011-08-14
I managed to solve my problem with non functional network (no adapter present in network manager) after installing compact wireless package. It was missing firmware all along! All I have to do download and paste **htc_9271.fw** firmware to /lib/firmware and my TL-WN422G v2 802.11g [Atheros AR9271] USB wlan adapter is functional again. Hope this will save some nerves and time to someone. :)

PS: -1 fixed channel fixed and injection seems to work:)

---

