---
title: "FATAL: Error inserting mac80211"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2009-05-08
I am trying to solve a problem with my intel wirless card that uses the iwl3945 driver.  At one point, I was encouraged to try 

>> sudo modprobe mac80211

and here is the result

FATAL: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/kernel/net/mac80211/mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)


And here is the output from dmesg:

[   79.597408] mac80211: Unknown symbol wiphy_register
[   79.597575] mac80211: Unknown symbol wiphy_new
[   79.599688] mac80211: Unknown symbol wiphy_unregister
[   79.600072] mac80211: Unknown symbol ieee80211_radiotap_iterator_init
[   79.600337] mac80211: Unknown symbol __ieee80211_get_channel
[   79.601464] mac80211: Unknown symbol ieee80211_radiotap_iterator_next
[   79.601663] mac80211: Unknown symbol ieee80211_channel_to_frequency
[   79.602804] mac80211: Unknown symbol ieee80211_frequency_to_channel
[   79.603603] mac80211: Unknown symbol wiphy_free


This seems bad.  How do I fix this?

Thanks,

Ryan

---

