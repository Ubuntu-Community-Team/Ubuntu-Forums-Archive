---
title: "cfg80211 module installation"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by perudupinkop on 2012-05-21
Hello,

I am on Ubuntu 10.04 ARM with a Nvidia Tegra 2 tablet (Toshiba Folio 100) i'm trying to get wifi working so i follow this thread : [http://forum.xda-developers.com/archive/index.php/t-1032471.html](http://forum.xda-developers.com/archive/index.php/t-1032471.html)

I've build the ath6kl module with the 2.6.39-rc1-3 version of compat wireless driver, which give me :

```
updates/net/wireless/cfg80211.ko
updates/net/wireless/lib80211.ko
updates/drivers/staging/ath6kl/ath6kl.ko
updates/net/wireless/lib80211_crypt_ccmp.ko
updates/net/wireless/lib80211_crypt_tkip.ko
updates/net/wireless/lib80211_crypt_wep.ko
```I can modprobe lib80211.ko , lib80211_crypt_ccmp.ko, lib80211_crypt_ccmp.ko and lib80211_crypt_ccmp.ko but i can't modprobe ath6kl.ko :

```
#modprobe lib80211
#modprobe lib80211_crypt_ccmp
#modprobe lib80211_crypt_tkip
#modprobe lib80211_crypt_wep
#modprobe ath6kl
FATAL: Error inserting ath6kl (/lib/modules/2.6.32.9/updates/drivers/staging/
ath6kl.ko) : Unknown symbol in modules, or unknown parameter (see dmesg)

```So i dmesg to see what's going on :

```
#dmesg | tail 
...
...
...
...
[ xxx.xxxxx] cfg80211: Unknown symbol rfkill_resume_polling
```I think it's because i haven't the rfkill modules but i don't how to install it. 

I need help.
Thanks in advance.

---

