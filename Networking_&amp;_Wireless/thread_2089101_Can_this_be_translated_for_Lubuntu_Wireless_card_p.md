---
title: "Can this be translated for Lubuntu? Wireless card problem!"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by yamach on 2012-11-28
Hello dear ubuntu forum!

I have this classical problem with wireless intel ipw2200 that many people had few years ago that it did not inject packages and solved with a little patch, but the currenty problem is there are no more links that still works to have that patch, i searched over 10 hours, and only thing i found was that lovely security distro BackTrack has this but ofc it is explained to how to patch it for BackTrack distro.

My question is , is these commands that you see above, can they be translated to Lubuntu (as far as i know backtrack is pretty close to any ubuntu-debian in the bases), so i can solve this problem without being in need to use BackTrack? I have really limited internet download and my laptop does not support usb boot, so i kind of must do this without BackTrack.


ln -s /usr/src/linux /lib/modules/2.6.39.4/build
cd/usr/src/
wget [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2011-07-14.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2011-07-14.tar.bz2)
tar jxpf compat-wireless-2011-07-14.tar.bz2 
wget [http://www.backtrack-linux.org/2.6.39.patches.tar](http://www.backtrack-linux.org/2.6.39.patches.tar)
tar xpf 2.6.39.patches.tar
cd compat-wireless-2011-07-14
patch -p1 < ../patches/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
patch -p1 < ../patches/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < ../patches/zd1211rw-2.6.28.patch
patch -p1 < ../patches/ipw2200-inject.2.6.36.patch
make
make install
reboot


PS: i have driver 1.2.2, it works well, but does not support injection

---

