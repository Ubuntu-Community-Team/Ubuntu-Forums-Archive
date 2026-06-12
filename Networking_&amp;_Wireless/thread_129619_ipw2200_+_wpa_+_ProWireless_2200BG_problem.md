---
title: "ipw2200 + wpa + Pro/Wireless 2200BG problem"
date: 2006-02-14
forum: Networking &amp; Wireless
---

### Post by donaldd on 2006-02-14
I believed I had followed the [http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+wpa](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+wpa) howto correctly but problems have arisen that I do not know how to resolve, appreciate if someone could point me in the right direction.

donald@home:/usr/src/ieee80211-1.1.11$ sudo make install
make -C /lib/modules/2.6.12-10-686/build M=/usr/src/ieee80211-1.1.11 MODVERDIR=/usr/src/ie ee80211-1.1.11 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  Building modules, stage 2.
  MODPOST
*** Warning: "ieee80211_wx_get_auth" [/usr/src/ieee80211-1.1.11/ieee80211.ko] undefined!
*** Warning: "ieee80211_wx_set_auth" [/usr/src/ieee80211-1.1.11/ieee80211.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
install -d /lib/modules/2.6.12-10-686/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_c cmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.12-10-686/net/ieee80211/
install -d `echo /lib/modules/2.6.12-10-686/include | grep "/net\$" || echo /lib/modules/2 .6.12-10-686/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /li b/modules/2.6.12-10-686/include | grep "/net\$" || echo /lib/modules/2.6.12-10-686/include /net`
mkdir -p /lib/modules/2.6.12-10-686/net/ieee80211//.tmp_versions
install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_cryp t_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.12-10-686/net/ieee80211//.tmp_version s
/sbin/depmod -a 2.6.12-10-686
WARNING: Loop detected: /lib/modules/2.6.12-10-686/net/ieee80211/ieee80211.ko which needs ieee80211.ko again!
WARNING: Module /lib/modules/2.6.12-10-686/net/ieee80211/ieee80211.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200.ko ignored,  due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2200/ipw2200.ko ignored, due to loop
WARNING: Module /lib/modules/2.6.12-10-686/kernel/drivers/net/wireless/ipw2100/ipw2100.ko ignored, due to loop

---

### Post by pnael on 2006-02-14
I am not sure if it was exactly the same problem but when I did this
HOWTO, the remove-old script did not remove everything.
I had errors when loading the modules.
So I removed manually all the ieee80211 and ipw2200 modules under /lib/modules and then everything worked fine.
Regards

---

