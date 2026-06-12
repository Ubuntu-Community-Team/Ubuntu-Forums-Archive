---
title: "Intel AGN4965 + aircrack/aireplay"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by ground21 on 2011-12-07
Hello

Could you provide me some working solution how can I force my Intel AGN4965 wireless card to work with aircrack (Ubuntu 10.04)? To be precise I want to use aireplay, but my card stuck on channel -1. 

```
mon0 is on channel -1, but the AP uses channel 6
```

What can recommend ? Which drivers to install and wchich patches to apply?
I can only say that I checked some workarounds but they didnt work, for example: [http://www.wardriving-forum.de/forum/f267/mon0-channel-1-but-ap-uses-channel-6-a-68603.html](http://www.wardriving-forum.de/forum/f267/mon0-channel-1-but-ap-uses-channel-6-a-68603.html)

Edit:
Also, when I try to load iwlagn module after compiling latest compat-wireless drivers I get an error:

```
user@laptop:~/compat-wireless-3.2-rc1-1$ sudo modprobe iwlagn
FATAL: Error inserting iwlagn (/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid argument
```

And something more on listing from 'dmesg':

```
user@laptop:~$ dmesg | grep iwl*
[   19.616502] iwlcore: disagrees about version of symbol ieee80211_chswitch_done
[   19.616507] iwlcore: Unknown symbol ieee80211_chswitch_done (err -22)
[   19.616800] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
[   19.616802] iwlcore: Unknown symbol ieee80211_alloc_hw (err -22)
[   19.616985] iwlcore: disagrees about version of symbol ieee80211_find_sta
[   19.616987] iwlcore: Unknown symbol ieee80211_find_sta (err -22)
[   19.617078] iwlcore: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   19.617080] iwlcore: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   19.617772] iwlcore: disagrees about version of symbol ieee80211_scan_completed
[   19.617774] iwlcore: Unknown symbol ieee80211_scan_completed (err -22)
[   19.617938] iwlcore: disagrees about version of symbol ieee80211_channel_to_frequency
[   19.617940] iwlcore: Unknown symbol ieee80211_channel_to_frequency (err -22)
[   19.618097] iwlcore: disagrees about version of symbol ieee80211_beacon_get_tim
[   19.618099] iwlcore: Unknown symbol ieee80211_beacon_get_tim (err -22)
```

---

