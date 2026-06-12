---
title: "WPA with Intel Centrino Ultimate-N 6300 not working (Thinkpad x201)"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by poschm on 2011-05-22
Hi,
I use natty (fresh install via wubi)  with the  64bit kernel 2.6.38-9-generic and cannot connect via wifi and wpa/wpa2. I use the network manager. Connections to an open network work fine. Under Windows the encrypted connection  works flawlessly. Here is the relevant line obtained by lspci 

02:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)

and the relevant output of dmesg

[ 1442.806864] wlan0: authenticate with xxxxxxxxx (try 1)
[ 1442.809558] wlan0: authenticated
[ 1442.809807] wlan0: associate with xxxxxxxxx (try 1)
[ 1442.813276] wlan0: RX AssocResp from xxxxxxxxxxxa (capab=0x431 status=0 aid=2)
[ 1442.813283] wlan0: associated
[ 1488.016798] wlan0: deauthenticating from xxxxxxxxxx by local choice (reason=3)

[ 1488.210495] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1488.210508] cfg80211: Restoring regulatory settings
[ 1488.210514] cfg80211: Calling CRDA to update world regulatory domain
[ 1488.215537] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 1488.215547] cfg80211: World regulatory domain updated:
[ 1488.215551] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1488.215556] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1488.215560] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1488.215564] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1488.215568] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1488.215572] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

Following googled advice II also tried wicd and several options in modprobe.conf (like disabling N, or disabling hardware encryption) but no success.  

Many thanks for any suggestions,

Martin

---

### Post by abaybas on 2011-06-07
Did you ever get this working? Thanks.

---

