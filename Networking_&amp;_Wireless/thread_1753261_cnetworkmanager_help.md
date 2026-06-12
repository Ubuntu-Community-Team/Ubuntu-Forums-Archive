---
title: "cnetworkmanager help"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by l3ecl on 2011-05-08
I can't seem to connect wirelessly via cnetworkmanager. Although I can connect using the gui applet.

When I run:

```
cnetworkmanager -C myssid --wep-pass=1234567890
```

I get

```
Entering mainloop

Connecting
Disconnected
Connecting
Disconnected
```

my demsg output file is:

```
[  691.940610] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  691.940612] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  691.940614] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  691.940616] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  691.940617] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  691.940619] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  693.131898] wlan0: authenticate with 00:0d:72:04:74:89 (try 1)
[  693.133652] wlan0: authenticated
[  693.133667] wlan0: associate with 00:0d:72:04:74:89 (try 1)
[  693.135615] wlan0: RX AssocResp from 00:0d:72:04:74:89 (capab=0x51 status=0 aid=1)
[  693.135617] wlan0: associated
[  693.137107] wlan0: deauthenticating from 00:0d:72:04:74:89 by local choice (reason=3)
[  693.272930] cfg80211: All devices are disconnected, going to restore regulatory settings
[  693.272933] cfg80211: Restoring regulatory settings
[  693.272946] cfg80211: Calling CRDA to update world regulatory domain
[  693.275931] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  693.275937] cfg80211: World regulatory domain updated:
[  693.275938] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  693.275940] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  693.275942] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  693.275943] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  693.275945] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  693.275946] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  694.449261] wlan0: authenticate with 00:0d:72:04:74:89 (try 1)
[  694.451067] wlan0: authenticated
[  694.451083] wlan0: associate with 00:0d:72:04:74:89 (try 1)
[  694.466234] wlan0: RX AssocResp from 00:0d:72:04:74:89 (capab=0x51 status=0 aid=1)
[  694.466237] wlan0: associated
[  694.467543] wlan0: deauthenticating from 00:0d:72:04:74:89 by local choice (reason=3)
[  694.629540] cfg80211: All devices are disconnected, going to restore regulatory settings
[  694.629543] cfg80211: Restoring regulatory settings
[  694.629559] cfg80211: Calling CRDA to update world regulatory domain
[  694.633077] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 

```

please help, I've been trying to get internet via command line for more than 5 hours now. also wicd doesn't work for me.

---

