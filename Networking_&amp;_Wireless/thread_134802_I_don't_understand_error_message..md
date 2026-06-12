---
title: "I don't understand error message."
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by StormWatcher on 2006-02-22
I am a newb.

My wireless card was working flawlessly for a few weeks now.  All of a sudden it doesn't work and sometimes my dmesg fills up with...

[4295439.121000] ieee80211_crypt_tkip: disagrees about version of symbol ieee80211_register_crypto_ops
[4295439.121000] ieee80211_crypt_tkip: Unknown symbol ieee80211_register_crypto_ops
[4295439.121000] ieee80211_crypt_tkip: disagrees about version of symbol ieee80211_unregister_crypto_ops
[4295439.121000] ieee80211_crypt_tkip: Unknown symbol ieee80211_unregister_crypto_ops

and just fills with this info.  But it doesn't do this all the time.  I was using wpa_supplicant to handle connecting to my home network (WPA) and the built in network tool to connec to my college (WEP).

I am using the ipw2200 drivers from sourceforge for my intel wireless card.  Let me know any other information I can provide.

Any help would be great.

---

### Post by mpvano on 2006-02-22
Just a guess, but if you built your drivers from source, perhaps they are now out of sync with the kernel, since there have been at least two kernel updates in the past few weeks.

This normally shouldn't be a problem, but it would be an issue if you built  drivers that were already present in the kernel, but changed enough to have different communication between modules then the versions present in the kernel.

If this is what has happened, you may need to rebuild and reinstall the drivers from source again, and you may need to do this again in the future with later kernel revisions.

If this is what happened, you might want to avoid the automatic kernel updates unless they address problems you need fixed.....

hope this helps

Mario

---

### Post by StormWatcher on 2006-03-13
A few weeks later and a hell of a time I have it working again.  Tonight I was able to download each of the three pieces fresh from new builds, compiled them and install everything and my wireless is working again.  I want to thanks those from other threads that helped me out.

Stormwatcher

---

### Post by StormWatcher on 2006-03-14
Also thanks to MPVANO.  Did not mean to forget you.  You pointed me in the right direction.

---

