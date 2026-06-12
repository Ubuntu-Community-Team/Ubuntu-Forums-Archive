---
title: "Is My Wireless router dying"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by owise1 on 2012-04-11
Hi Guys - suspect that my wireless router is dying except that none of the other devices that connect to it have the same problem.

Regularly get disconnected for the last couple of weeks and a the wireless has to reconnect.  Occasionally I have a request to re-enter my wireless password (WPA) to get it going.  Wonder if there have been any updates to network manager / wireless drivers in the last few weeks?  Anyway of checking - I keep this machine up to date.

Dying router or wireless card??

Any ideas - cheers  Dave

From dmesg - get these message groups occurring regularly:


[1251933.492036] No probe response from AP 00:24:01:ae:a9:8b after 500ms, disconnecting.
[1251933.532541] cfg80211: All devices are disconnected, going to restore regulatory settings
[1251933.532552] cfg80211: Restoring regulatory settings
[1251933.532558] cfg80211: Calling CRDA to update world regulatory domain
[1251933.553505] cfg80211: World regulatory domain updated:
[1251933.553512]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[1251933.553518]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[1251933.553523]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[1251933.553528]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[1251933.553534]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[1251933.553539]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[1251934.868888] wlan0: authenticate with 00:24:01:ae:a9:8b (try 1)
[1251935.068035] wlan0: authenticate with 00:24:01:ae:a9:8b (try 2)
[1251935.070013] wlan0: authenticated
[1251935.070044] wlan0: associate with 00:24:01:ae:a9:8b (try 1)
[1251935.073625] wlan0: RX AssocResp from 00:24:01:ae:a9:8b (capab=0x431 status=0 aid=2)
[1251935.073630] wlan0: associated

---

### Post by Ms. Daisy on 2012-04-12
> none of the other devices that connect to it have the same problem
That part makes me suspect the wireless driver in Ubuntu. Perhaps there's a newer driver than the one you've got.

---

### Post by owise1 on 2012-04-12
Ms Daisy - I was wondering if the driver got updated and that caused the problem - is there a way of reviewing the last few months of updates??

---

### Post by Ms. Daisy on 2012-04-12
One way is to use synaptic package manager, go to "file" and choose "history."

Via terminal you would look at /var/log/apt/history.log

---

