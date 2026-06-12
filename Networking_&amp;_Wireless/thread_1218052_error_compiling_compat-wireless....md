---
title: "error compiling compat-wireless..."
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by ichundu on 2009-07-20
hi,

i'm trying to patch my wireless driver zd1211rw-mac80211 (my device has a zydas chipset) to get injection and fragmentation attack to work in Aircrack-ng.
i'm following [[COLOR="Blue"]these instructions[/COLOR]]("http://www.aircrack-ng.org/doku.php?id=zd1211rw-mac80211"). it says to downloaded [[COLOR="Blue"]the compat-wireless package[/COLOR]]("http://wireless.kernel.org/download/compat-wireless-2.6/") from [http://www.wireless.kernel.org/]("http://www.wireless.kernel.org/") and patch the driver in it. [[COLOR="Blue"]the first patch[/COLOR]]("http://patches.aircrack-ng.org/zd1211rw_inject_2.6.26.patch") applied successfully, but the [[COLOR="Blue"]mac80211 patch[/COLOR]]("http://patches.aircrack-ng.org/mac80211_2.6.28-rc8-wl_frag+ack_radiotap.patch") succeeded partially. the output of this last patch is:
```
Hmm...  Looks like a unified diff to me...
(Stripping trailing CRs from patch.)
The text leading up to this was:
--------------------------
|diff --git a/include/net/ieee80211_radiotap.h b/include/net/ieee80211_radiotap.h
|index d364fd5..4e28c0c 100644
|--- a/include/net/ieee80211_radiotap.h
|+++ b/include/net/ieee80211_radiotap.h
--------------------------
Patching file include/net/ieee80211_radiotap.h using Plan A...
Hunk #1 succeeded at 240 (offset -7 lines).
Hmm...  The next patch looks like a unified diff to me...
(Stripping trailing CRs from patch.)
The text leading up to this was:
--------------------------
|diff --git a/net/mac80211/tx.c b/net/mac80211/tx.c
|index 22702e7..b397aed 100644
|--- a/net/mac80211/tx.c
|+++ b/net/mac80211/tx.c
--------------------------
Patching file net/mac80211/tx.c using Plan A...
Hunk #1 succeeded at 671 (offset 62 lines).
Hunk #2 FAILED at 933.
Hunk #3 succeeded at 973 (offset 55 lines).
Hunk #4 succeeded at 1030 with fuzz 1 (offset 54 lines).
Hunk #5 FAILED at 1059.
2 out of 5 hunks FAILED -- saving rejects to file net/mac80211/tx.c.rej
done

```

however, the main problem is i get errors when compiling "compat-wireless" (the same errors occur even if i compile it without applying the patches first). This is the output of "make":
```
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.28-13-generic/build M=/home/ichundu/src/compat-wireless-2009-07-19 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  LD      /home/ichundu/src/compat-wireless-2009-07-19/drivers/misc/eeprom/built-in.o
  CC [M]  /home/ichundu/src/compat-wireless-2009-07-19/drivers/misc/eeprom/eeprom_93cx6.o
  LD      /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/usb/built-in.o
  CC [M]  /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/usb/cdc_ether.o
  CC [M]  /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/usb/rndis_host.o
  CC [M]  /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/usb/usbnet.o
  LD      /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/built-in.o
  CC [M]  /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/main.o
  CC [M]  /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/regd.o
  LD [M]  /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/ath.o
  LD      /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/ar9170/built-in.o
  CC [M]  /home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/ar9170/usb.o
/home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/ar9170/usb.c: In function ‘ar9170_usb_open’:
/home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/ar9170/usb.c:706: error: implicit declaration of function ‘usb_unpoison_anchored_urbs’
make[5]: *** [/home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/ar9170/usb.o] Error 1
make[4]: *** [/home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath/ar9170] Error 2
make[3]: *** [/home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless/ath] Error 2
make[2]: *** [/home/ichundu/src/compat-wireless-2009-07-19/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/ichundu/src/compat-wireless-2009-07-19] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [modules] Error 2
```

i'm using a fresh-installed ubuntu 9.04 system.
when i had ubuntu 8.10, i managed to patch the zd1211rw driver directly to the kernel (with the zd1211rw_inject and mac80211 patches), not through the compat-wireless package, and aircrack-ng worked like a charm including injection and fragmentation attack.

thanks for any possible feedback  ;)

---

### Post by s0ysauce on 2011-05-16
I'm also getting this same exact error! How do I fix this? I have a feeling its because of the encryption I placed earlier on my home directory. Is this at all a possible cause?

---

