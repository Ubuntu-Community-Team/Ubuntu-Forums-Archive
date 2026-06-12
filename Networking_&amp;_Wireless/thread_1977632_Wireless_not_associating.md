---
title: "Wireless not associating"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by Wipster on 2012-05-10
Hi all,

I am installing ubuntu 12.04 desktop on some machines at work ready to be imaged out to a few hundred but I am having real problems trying to get the wireless to work correctly.

The wireless card I am using is a Intel 4965 mini pcie card, which unfortunatly has its own issues with the release kernel [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929244](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929244)
But I have installed the 3.4-rc5 kernel which solves that problem, however the system fails to associate with the AP with this log

```
[ 3747.835187] wlan0: authenticate with 00:1a:4d:28:a7:bd
[ 3747.835338] wlan0: send auth to 00:1a:4d:28:a7:bd (try 1/3)
[ 3747.837143] wlan0: authenticated
[ 3747.844054] wlan0: associate with 00:1a:4d:28:a7:bd (try 1/3)
[ 3748.048032] wlan0: associate with 00:1a:4d:28:a7:bd (try 2/3)
[ 3748.252038] wlan0: associate with 00:1a:4d:28:a7:bd (try 3/3)
[ 3748.456063] wlan0: association with 00:1a:4d:28:a7:bd timed out
[ 3762.887215] wlan0: authenticate with 00:1a:4d:28:a7:bd
[ 3762.887381] wlan0: send auth to 00:1a:4d:28:a7:bd (try 1/3)
[ 3762.889215] wlan0: authenticated
[ 3762.900126] wlan0: associate with 00:1a:4d:28:a7:bd (try 1/3)
[ 3763.104040] wlan0: associate with 00:1a:4d:28:a7:bd (try 2/3)
[ 3763.308088] wlan0: associate with 00:1a:4d:28:a7:bd (try 3/3)
[ 3763.512046] wlan0: association with 00:1a:4d:28:a7:bd timed out

```

I have tried removing network-manager and using wicd instead, which results in a prompt that the network password maybe bad. This makes me suspect wpa_supplicant isn't quite doing its job correctly.

I have tried using 10.04 LTS but the problem is still apparent there.
The one solution I have found is removing the entries from network manager connecting to a different AP and back again, this seems to allow me to connect, here is the log for this.

```
[ 4124.034211] wlan0: authenticate with 28:37:37:4b:6b:6f
[ 4124.040025] wlan0: send auth to 28:37:37:4b:6b:6f (try 1/3)
[ 4124.044545] wlan0: authenticated
[ 4124.052040] wlan0: associate with 28:37:37:4b:6b:6f (try 1/3)
[ 4124.256044] wlan0: associate with 28:37:37:4b:6b:6f (try 2/3)
[ 4124.263273] wlan0: RX AssocResp from 28:37:37:4b:6b:6f (capab=0x31 status=0 aid=1)
[ 4124.263281] wlan0: associated
[ 4124.292391] cfg80211: Calling CRDA for country: GB
[ 4124.311273] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311287] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311296] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311307] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311316] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311326] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311335] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311345] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311353] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311362] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311370] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311381] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311389] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311399] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311407] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311417] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311425] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311434] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311442] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311452] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311460] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311471] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311479] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311488] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311495] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311505] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311514] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311524] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311533] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311543] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311553] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311564] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311573] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311583] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311592] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311603] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311612] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311622] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311631] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311641] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311650] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311661] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4124.311670] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311680] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311689] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311699] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311708] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311718] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311726] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311735] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311744] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311754] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311762] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311771] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311779] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311790] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311798] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311808] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311817] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311827] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311836] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311846] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311855] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[ 4124.311865] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2700 mBm)
[ 4124.311878] cfg80211: Regulatory domain changed to country: GB
[ 4124.311884] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4124.311892] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4124.311900] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4124.311908] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4124.311916] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 4132.787143] wlan0: deauthenticating from 28:37:37:4b:6b:6f by local choice (reason=3)
[ 4132.815554] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4132.815568] cfg80211: Restoring regulatory settings while preserving user preference for: JP
[ 4132.815583] cfg80211: Calling CRDA to update world regulatory domain
[ 4132.830685] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 4132.830698] cfg80211: World regulatory domain updated:
[ 4132.830704] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4132.830714] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4132.830723] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4132.830731] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4132.830740] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4132.830749] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4132.830808] cfg80211: Calling CRDA for country: JP
[ 4132.848724] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848739] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848748] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848758] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848767] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848777] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848785] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848803] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848814] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848823] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848834] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848842] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848853] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848862] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848872] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848881] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848892] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848900] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848911] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848919] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848930] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848939] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848950] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848959] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848969] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848979] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.848990] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.848999] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849009] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.849018] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849028] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.849037] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849047] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.849056] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849066] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.849075] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849085] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.849094] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849104] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.849112] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849122] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4132.849130] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849141] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849150] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849160] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849170] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849180] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849189] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849200] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849209] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849219] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849228] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849239] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849248] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849259] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849268] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849279] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849288] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849299] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849307] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849317] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849326] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[ 4132.849336] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4132.849348] cfg80211: Regulatory domain changed to country: JP
[ 4132.849354] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4132.849363] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4132.849371] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[ 4132.849380] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[ 4132.849388] cfg80211:   (4910000 KHz - 4930000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[ 4132.849396] cfg80211:   (4910000 KHz - 4990000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[ 4132.849405] cfg80211:   (4930000 KHz - 4950000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[ 4132.849413] cfg80211:   (5030000 KHz - 5045000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[ 4132.849422] cfg80211:   (5030000 KHz - 5090000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[ 4132.849431] cfg80211:   (5050000 KHz - 5060000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[ 4132.849439] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4132.849447] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4132.849455] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[ 4134.368041] wlan0: no IPv6 routers present
[ 4146.719403] wlan0: authenticate with 00:1a:4d:28:a7:bd
[ 4146.728123] wlan0: send auth to 00:1a:4d:28:a7:bd (try 1/3)
[ 4146.729883] wlan0: authenticated
[ 4146.740124] wlan0: associate with 00:1a:4d:28:a7:bd (try 1/3)
[ 4146.944108] wlan0: associate with 00:1a:4d:28:a7:bd (try 2/3)
[ 4146.946720] wlan0: RX AssocResp from 00:1a:4d:28:a7:bd (capab=0x431 status=0 aid=1)
[ 4146.946732] wlan0: associated
[ 4146.970077] cfg80211: Calling CRDA for country: JP
[ 4146.983259] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983273] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983282] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983292] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983301] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983311] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983319] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983329] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983338] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983348] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983356] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983366] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983374] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983384] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983392] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983403] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983411] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983421] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983430] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983440] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983449] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983459] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983468] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983478] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983486] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983497] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983506] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983516] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983524] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983534] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983543] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983552] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983561] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983572] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983580] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983590] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983599] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983609] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983618] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983629] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983637] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983648] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 4146.983656] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983666] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983675] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983685] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983694] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983704] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983713] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983723] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983732] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983742] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983750] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983761] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983769] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983779] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983788] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983798] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983807] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983817] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983826] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983836] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983845] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[ 4146.983855] cfg80211: 5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A mBi, 2300 mBm)
[ 4146.983867] cfg80211: Regulatory domain changed to country: JP
[ 4146.983873] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4146.983882] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4146.983891] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[ 4146.983900] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[ 4146.983908] cfg80211:   (4910000 KHz - 4930000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[ 4146.983917] cfg80211:   (4910000 KHz - 4990000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[ 4146.983926] cfg80211:   (4930000 KHz - 4950000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[ 4146.983934] cfg80211:   (5030000 KHz - 5045000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[ 4146.983943] cfg80211:   (5030000 KHz - 5090000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[ 4146.983952] cfg80211:   (5050000 KHz - 5060000 KHz @ 10000 KHz), (N/A, 2300 mBm)
[ 4146.983960] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4146.983969] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 4146.983977] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2300 mBm)
[ 4157.240125] wlan0: no IPv6 routers present
chai-ers@CHAI-ERS-Tablet:~$ 
```

Here is some info about the card
```
chai-ers@CHAI-ERS-Tablet:~$ dmesg | grep iwl
[   16.465925] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   16.465935] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   16.466077] iwl4965 0000:02:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   16.509423] iwl4965 0000:02:00.0: device EEPROM VER=0x36, CALIB=0x5
[   16.512252] iwl4965 0000:02:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[   16.512362] iwl4965 0000:02:00.0: irq 44 for MSI/MSI-X
[   17.074602] iwl4965 0000:02:00.0: loaded firmware version 228.61.2.24
[   17.231593] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
```

Thanks and best regards,
Ben

---

### Post by Wipster on 2012-05-15
After putting wpa_supplicant into debug logging I see a difference between a failed association and successfull one, I'm not recieving a second MLME event frame and it looks like it timesout and goes back to scanning.
This level of wireless authentication is a bit beyond me at the mo, could someone point me in a possible direction of the fault?

The way to make the AP associate is to attempt to connect, when it timesout connect to a different AP, then back again, here is the wpa_supplicant log from this test.

```
1337079933.838684: ssid - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079933.838935: PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
1337079933.894108: PSK (from passphrase) - hexdump(len=32): [REMOVED]
1337079933.896458: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079933.896648: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079933.896705: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337079935.978538: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079935.978707: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079935.978758: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337079935.979461:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079935.979525:   * IEs - hexdump(len=0): [NULL]
1337079941.613000: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079941.613251: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079941.613312: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337079943.812797: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079943.812978: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079943.813025: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337079943.813577:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079943.813644:   * IEs - hexdump(len=0): [NULL]
1337079943.815803: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd 80 63 00 00 02 00 00 00
1337079943.815908: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337079943.816174: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079943.816312:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079943.816366:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079949.519105: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079949.519349: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079949.519424: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337079951.645599: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079951.645777: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079951.645825: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337079951.646731:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079951.646783:   * IEs - hexdump(len=0): [NULL]
1337079952.056077: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd 40 69 00 00 02 00 00 00
1337079952.056203: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337079952.056459: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079952.056572:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079952.056608:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079957.716535: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079957.716793: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079957.716845: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337079959.912691: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079959.915123: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079959.915201: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337079959.916767:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079959.916828:   * IEs - hexdump(len=0): [NULL]
1337079959.921069: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd 90 6f 00 00 02 00 00 00
1337079959.921479: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337079959.922329: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079959.922750:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079959.922832:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079965.550475: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079965.550679: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079965.550735: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337079967.694371: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079967.694563: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079967.694614: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337079967.695343:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079967.695404:   * IEs - hexdump(len=0): [NULL]
1337079968.104174: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd 70 75 00 00 02 00 00 00
1337079968.104301: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337079968.104564: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079968.104683:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079968.104721:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079973.732332: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079973.732583: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079973.733517: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337079975.886768: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079975.887281: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079975.887356: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337079975.888824:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079975.888893:   * IEs - hexdump(len=0): [NULL]
1337079975.898507: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd 60 7b 00 00 02 00 00 00
1337079975.898636: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337079975.898965: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079975.899144:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079975.899245:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079981.526474: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079981.526701: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079981.526758: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337079983.571902: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079983.572069: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079983.572117: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337079983.574538:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079983.574606:   * IEs - hexdump(len=0): [NULL]
1337079983.984111: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd 30 81 00 00 02 00 00 00
1337079983.984236: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337079983.984494: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079983.984644:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079983.984744:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079989.610913: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079989.611112: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079989.611162: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337079991.784872: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079991.786301: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079991.786421: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337079991.787388:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079991.787524:   * IEs - hexdump(len=0): [NULL]
1337079991.790011: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd a0 87 00 00 02 00 00 00
1337079991.790128: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337079991.790472: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337079991.790665:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337079991.790724:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080056.848986: ssid - hexdump_ascii(len=7):
     53 65 71 75 6f 69 61                              Sequoia         
1337080056.849136: PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
1337080056.901050: PSK (from passphrase) - hexdump(len=32): [REMOVED]
1337080056.902991: Scan SSID - hexdump_ascii(len=7):
     53 65 71 75 6f 69 61                              Sequoia         
1337080056.903197: nl80211: Scan SSID - hexdump_ascii(len=7):
     53 65 71 75 6f 69 61                              Sequoia         
1337080056.903259: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337080059.133891: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080059.134062: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080059.134110: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337080059.134825:   * SSID - hexdump_ascii(len=7):
     53 65 71 75 6f 69 61                              Sequoia         
1337080059.134925:   * IEs - hexdump(len=0): [NULL]
1337080059.137067: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 d8 30 62 33 db 39 d8 30 62 33 db 39 20 ee 00 00 02 00 00 00
1337080059.137167: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337080059.137469: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080059.137627:   * SSID - hexdump_ascii(len=7):
     53 65 71 75 6f 69 61                              Sequoia         
1337080059.137673:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080059.397204: RX EAPOL - hexdump(len=99): 02 03 00 5f 02 00 8a 00 10 00 00 00 00 00 00 00 00 16 98 1a 44 f6 14 62 04 75 87 6a 9c e7 90 d2 f0 85 61 f8 d4 7d c5 9d f7 8a 32 c2 e6 7a 1b 1d 30 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080059.402074: nl80211: MLME event frame - hexdump(len=124): 10 00 3a 01 00 21 5c 85 25 d7 d8 30 62 33 db 39 d8 30 62 33 db 39 50 ee 31 04 00 00 01 c0 01 08 82 84 8b 0c 12 96 18 24 32 04 30 48 60 6c 2d 1a 2c 40 17 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 0b 00 15 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 18 00 50 f2 02 01 01 01 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
1337080059.402293: resp_ies - hexdump(len=94): 01 08 82 84 8b 0c 12 96 18 24 32 04 30 48 60 6c 2d 1a 2c 40 17 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 16 0b 00 15 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 dd 18 00 50 f2 02 01 01 01 00 03 a4 00 00 27 a4 00 00 42 43 5e 00 62 32 2f 00
1337080059.402434: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337080059.404186: RX EAPOL - hexdump(len=99): 02 03 00 5f 02 00 8a 00 10 00 00 00 00 00 00 00 00 16 98 1a 44 f6 14 62 04 75 87 6a 9c e7 90 d2 f0 85 61 f8 d4 7d c5 9d f7 8a 32 c2 e6 7a 1b 1d 30 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080059.404691:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 00
1337080059.404718:   key_nonce - hexdump(len=32): 16 98 1a 44 f6 14 62 04 75 87 6a 9c e7 90 d2 f0 85 61 f8 d4 7d c5 9d f7 8a 32 c2 e6 7a 1b 1d 30
1337080059.404763:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080059.404797:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1337080059.404825:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1337080059.404849:   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080059.404885: WPA: RX EAPOL-Key - hexdump(len=99): 02 03 00 5f 02 00 8a 00 10 00 00 00 00 00 00 00 00 16 98 1a 44 f6 14 62 04 75 87 6a 9c e7 90 d2 f0 85 61 f8 d4 7d c5 9d f7 8a 32 c2 e6 7a 1b 1d 30 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080059.405216: RSN: msg 1/4 key data - hexdump(len=0):
1337080059.407314: WPA: Renewed SNonce - hexdump(len=32): c1 78 5e 90 03 ed 86 33 0f cd d8 e6 a9 66 ba ff 0f 56 c4 d2 86 c1 65 f4 1c 3d 0b 76 bd 84 ae 6f
1337080059.407452: WPA: PMK - hexdump(len=32): [REMOVED]
1337080059.407477: WPA: PTK - hexdump(len=48): [REMOVED]
1337080059.407497: WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080059.407665: WPA: TX EAPOL-Key - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 00 c1 78 5e 90 03 ed 86 33 0f cd d8 e6 a9 66 ba ff 0f 56 c4 d2 86 c1 65 f4 1c 3d 0b 76 bd 84 ae 6f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e1 5b df 98 93 40 dc 43 66 27 72 cf 9b 18 3e 22 00 16 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080059.412510: RX EAPOL - hexdump(len=155): 02 03 00 97 02 13 ca 00 10 00 00 00 00 00 00 00 01 16 98 1a 44 f6 14 62 04 75 87 6a 9c e7 90 d2 f0 85 61 f8 d4 7d c5 9d f7 8a 32 c2 e6 7a 1b 1d 30 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6a 1a 2a ea 72 08 ea de 77 36 40 b6 58 b4 8a 0d 00 38 1f fb 79 80 09 cb b8 57 c7 67 ed bf 1e 29 f8 5c 35 cd b0 3a 25 97 85 b1 ba 82 9e 28 ed 66 d4 6a 8e 13 dd d1 5e 6e 52 1c 22 28 6d 6f 38 10 a1 1f 6b a0 42 a3 58 c9 54 2b
1337080059.412804:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
1337080059.412828:   key_nonce - hexdump(len=32): 16 98 1a 44 f6 14 62 04 75 87 6a 9c e7 90 d2 f0 85 61 f8 d4 7d c5 9d f7 8a 32 c2 e6 7a 1b 1d 30
1337080059.412859:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080059.412882:   key_rsc - hexdump(len=8): 3d 02 00 00 00 00 00 00
1337080059.412899:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1337080059.412916:   key_mic - hexdump(len=16): 6a 1a 2a ea 72 08 ea de 77 36 40 b6 58 b4 8a 0d
1337080059.412941: WPA: RX EAPOL-Key - hexdump(len=155): 02 03 00 97 02 13 ca 00 10 00 00 00 00 00 00 00 01 16 98 1a 44 f6 14 62 04 75 87 6a 9c e7 90 d2 f0 85 61 f8 d4 7d c5 9d f7 8a 32 c2 e6 7a 1b 1d 30 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 3d 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6a 1a 2a ea 72 08 ea de 77 36 40 b6 58 b4 8a 0d 00 38 1f fb 79 80 09 cb b8 57 c7 67 ed bf 1e 29 f8 5c 35 cd b0 3a 25 97 85 b1 ba 82 9e 28 ed 66 d4 6a 8e 13 dd d1 5e 6e 52 1c 22 28 6d 6f 38 10 a1 1f 6b a0 42 a3 58 c9 54 2b
1337080059.413063: RSN: encrypted key data - hexdump(len=56): 1f fb 79 80 09 cb b8 57 c7 67 ed bf 1e 29 f8 5c 35 cd b0 3a 25 97 85 b1 ba 82 9e 28 ed 66 d4 6a 8e 13 dd d1 5e 6e 52 1c 22 28 6d 6f 38 10 a1 1f 6b a0 42 a3 58 c9 54 2b
1337080059.413187: WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
1337080059.413242: WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 02 00 85 c1 28 44 8e 74 ed 37 39 23 80 cd 0f 00 b2 d8 dd 00
1337080059.413286: WPA: RSN IE in EAPOL-Key - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080059.413313: WPA: GTK in EAPOL-Key - hexdump(len=24): [REMOVED]
1337080059.413363: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f 02 03 0a 00 00 00 00 00 00 00 00 00 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 87 c2 13 c2 f8 d0 02 80 be f0 85 40 36 40 38 23 00 00
1337080059.417615: RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
1337080059.417678: WPA: Group Key - hexdump(len=16): [REMOVED]
1337080059.417738: WPA: RSC - hexdump(len=6): 3d 02 00 00 00 00
1337080110.003864: nl80211: MLME event frame - hexdump(len=26): c0 00 00 00 d8 30 62 33 db 39 00 21 5c 85 25 d7 d8 30 62 33 db 39 00 00 03 00
1337080144.167283: ssid - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337080144.167423: PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
1337080144.216552: PSK (from passphrase) - hexdump(len=32): [REMOVED]
1337080144.219450: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337080144.219730: nl80211: Scan SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337080144.219788: nl80211: Scan SSID - hexdump_ascii(len=0): [NULL]
1337080146.366377: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080146.366761: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080146.366806: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337080146.367851:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337080146.367908:   * IEs - hexdump(len=0): [NULL]
1337080146.776083: nl80211: MLME event frame - hexdump(len=30): b0 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd 90 2f 00 00 02 00 00 00
1337080146.776256: SME: Authentication response IEs - hexdump(len=0): [NULL]
1337080146.776502: WPA: set own WPA/RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080146.776611:   * SSID - hexdump_ascii(len=7):
     4b 34 62 2d 6e 65 77                              K4b-new         
1337080146.776647:   * IEs - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080147.016905: nl80211: MLME event frame - hexdump(len=60): 10 00 3a 01 00 21 5c 85 25 d7 00 1a 4d 28 a7 bd 00 1a 4d 28 a7 bd f0 2f 31 04 00 00 02 c0 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 0c 00 03 7f 02 01 01 00 00 02 a4 00 00
1337080147.017039: resp_ies - hexdump(len=30): 01 08 82 84 8b 96 0c 18 30 48 32 04 12 24 60 6c dd 0c 00 03 7f 02 01 01 00 00 02 a4 00 00
1337080147.017125: FT: Stored MDIE and FTIE from (Re)Association Response - hexdump(len=0):
1337080147.111082: RX EAPOL - hexdump(len=99): 01 03 00 5f 02 00 8a 00 10 00 00 00 00 00 00 00 01 46 6a 77 39 5a 62 9b 32 54 15 5a d3 bc b6 0b 22 a4 77 2c 48 b7 66 8c ed 3c 80 a5 dd 83 8b 61 97 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080147.111371:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
1337080147.111405:   key_nonce - hexdump(len=32): 46 6a 77 39 5a 62 9b 32 54 15 5a d3 bc b6 0b 22 a4 77 2c 48 b7 66 8c ed 3c 80 a5 dd 83 8b 61 97
1337080147.111453:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080147.111485:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1337080147.111510:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1337080147.111537:   key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080147.111576: WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f 02 00 8a 00 10 00 00 00 00 00 00 00 01 46 6a 77 39 5a 62 9b 32 54 15 5a d3 bc b6 0b 22 a4 77 2c 48 b7 66 8c ed 3c 80 a5 dd 83 8b 61 97 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080147.111919: RSN: msg 1/4 key data - hexdump(len=0):
1337080147.114051: WPA: Renewed SNonce - hexdump(len=32): b9 96 3f bb 89 67 5b 8f 95 e1 fe 56 99 ba 5e 40 b3 db d7 bd 91 a8 17 2f b3 92 79 3e bb 8c 15 9e
1337080147.114276: WPA: PMK - hexdump(len=32): [REMOVED]
1337080147.114315: WPA: PTK - hexdump(len=48): [REMOVED]
1337080147.114338: WPA: WPA IE for msg 2/4 - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080147.114455: WPA: TX EAPOL-Key - hexdump(len=121): 01 03 00 75 02 01 0a 00 00 00 00 00 00 00 00 00 01 b9 96 3f bb 89 67 5b 8f 95 e1 fe 56 99 ba 5e 40 b3 db d7 bd 91 a8 17 2f b3 92 79 3e bb 8c 15 9e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 94 7b 7d c1 dc 52 16 fa ec 80 1a 0e 7c 9e c6 b5 00 16 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080147.122069: RX EAPOL - hexdump(len=155): 01 03 00 97 02 13 ca 00 10 00 00 00 00 00 00 00 02 46 6a 77 39 5a 62 9b 32 54 15 5a d3 bc b6 0b 22 a4 77 2c 48 b7 66 8c ed 3c 80 a5 dd 83 8b 61 97 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c8 90 bd e7 4f 87 99 14 9c 85 3a 59 85 07 f6 bc 00 38 5d 98 e0 93 f1 31 42 32 75 a2 3c 8d b6 40 02 19 a0 98 4a 69 c2 3a 43 a7 b8 e6 3d 8d 8b 05 26 03 ca 47 66 93 97 3f 9d bc 29 05 cf 56 b4 d9 c0 31 fa d8 83 90 9e ec 1d 13
1337080147.122435:   replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
1337080147.122473:   key_nonce - hexdump(len=32): 46 6a 77 39 5a 62 9b 32 54 15 5a d3 bc b6 0b 22 a4 77 2c 48 b7 66 8c ed 3c 80 a5 dd 83 8b 61 97
1337080147.122519:   key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
1337080147.122553:   key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
1337080147.122581:   key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
1337080147.122677:   key_mic - hexdump(len=16): c8 90 bd e7 4f 87 99 14 9c 85 3a 59 85 07 f6 bc
1337080147.122727: WPA: RX EAPOL-Key - hexdump(len=155): 01 03 00 97 02 13 ca 00 10 00 00 00 00 00 00 00 02 46 6a 77 39 5a 62 9b 32 54 15 5a d3 bc b6 0b 22 a4 77 2c 48 b7 66 8c ed 3c 80 a5 dd 83 8b 61 97 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c8 90 bd e7 4f 87 99 14 9c 85 3a 59 85 07 f6 bc 00 38 5d 98 e0 93 f1 31 42 32 75 a2 3c 8d b6 40 02 19 a0 98 4a 69 c2 3a 43 a7 b8 e6 3d 8d 8b 05 26 03 ca 47 66 93 97 3f 9d bc 29 05 cf 56 b4 d9 c0 31 fa d8 83 90 9e ec 1d 13
1337080147.122924: RSN: encrypted key data - hexdump(len=56): 5d 98 e0 93 f1 31 42 32 75 a2 3c 8d b6 40 02 19 a0 98 4a 69 c2 3a 43 a7 b8 e6 3d 8d 8b 05 26 03 ca 47 66 93 97 3f 9d bc 29 05 cf 56 b4 d9 c0 31 fa d8 83 90 9e ec 1d 13
1337080147.123055: WPA: decrypted EAPOL-Key key data - hexdump(len=48): [REMOVED]
1337080147.123184: WPA: IE KeyData - hexdump(len=48): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00 dd 16 00 0f ac 01 05 00 a4 bd c0 c8 9d 4f 3b 1f c2 0d f9 eb 8e 7c c8 f6 dd 00
1337080147.123248: WPA: RSN IE in EAPOL-Key - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1337080147.123289: WPA: GTK in EAPOL-Key - hexdump(len=24): [REMOVED]
1337080147.123372: WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f 02 03 0a 00 00 00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 89 37 e3 53 05 1d 31 46 24 6d eb fc ea 9a d1 11 00 00
1337080147.127606: RSN: received GTK in pairwise handshake - hexdump(len=18): [REMOVED]
1337080147.127722: WPA: Group Key - hexdump(len=16): [REMOVED]
1337080147.127775: WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
```

---

### Post by chili555 on 2012-05-15
Before we delve into the depths of C code, let's get some easy stuff out of the way. First, either Network Manager or wpa_spplicant has difficulty with mixed mode WPA and WPA2 encryption. I suggest you try setting the router to WPA2-AES and forgo mixed mode. Next, let's try a driver module:```
sudo modprobe -r iwl4956
sudo modprobe iwl4965 11n_disable=1
```Does it connect now? If not, try this:```
sudo modprobe -r iwl4956
sudo modprobe iwl4965 swcrypto=1
```How about now? If either works, we can easily write a one line conf file and make it permanent.

---

### Post by Wipster on 2012-05-15
Hi chili555,
I can confirm that the router, a Vigor2800 with latest firmware, is running in WPA2 mode only.
I have tried both of those driver options with no effect unfortunatly.

---

### Post by chili555 on 2012-05-15
> cfg80211: Regulatory domain changed to country: [COLOR="Red"]JP[/COLOR]Is this correct?

---

### Post by Wipster on 2012-05-15
It does this automatically when connecting to the other wireless network.
It probably shouldn't as I am in the UK, but couldn't find how to make network manager lock to a region.

These machines are destined for Mozambique so that would require a change again.

---

### Post by chili555 on 2012-05-15
You might try:```
sudo modprobe -rv iwl4965
```It ought to also unload cfg80211, but if not:```
sudo modprobe -r cfg80211
sudo modprobe cfg80211 ieee80211_regdom=UK
sudo modprobe iwl4965
```In the last 15-20 lines of syslog, does UK stick? And does it connect?> These machines are destined for Mozambique so that would require a change again.Easy enough.

---

### Post by Wipster on 2012-05-15
Hi,

When it unloads iwl4965 it does take cfg80211 with it, my crda country code is GB so I used that but still unable to connect to the first AP.

Connected to the second AP fine and the region stuck, but when I tried to connect to the first AP again the connection succeded but with region switched to JP.

---

### Post by chili555 on 2012-05-15
> my crda country code is GB so I used thatQuite right! I'm gonna get the danged chart tattooed to my forearm! Sorry.> Connected to the second AP fine and the region stuck, but when I tried to connect to the first AP again the connection succeded but with region switched to JP. Weird. I'm studying this: [http://linuxwireless.org/en/developers/Regulatory/CRDA](http://linuxwireless.org/en/developers/Regulatory/CRDA)> **Changing regulatory domains**

Helping compliance by allowing to change regulatory domains

Linux allows changing regulatory domains in compliance with regulatory restrictions world wide, including the US FCC. In order to achieve this devices always respect their programmed regulatory domain and a country code selection will only enhance regulatory restrictions. This is in accordance with the FCC part 15 country code selection knowledge base publication number 594280. As an example if your device was programmed for operation in the US which allows operation on channels 1-11 on the 2.4 GHz band and you visit Japan which allows operation on channels 1-14 and you change your regulatory domain to JP you will not be able to use channel 12, 13 or 14 (CCK). But if you have a device programmed for operation in Japan and visit the US and you select US as your regulatory domain you will have channel 12-14 disabled. Weird. Was the second AP manufactured in Japan?

You are obviously not trying to connect to a disabled channel since it eventually connects. I wonder if it would succeed with cfg80211 hard-coded to JP. Of course, in Mozambique, all bets are off, but at least we have some clues.

---

### Post by Wipster on 2012-05-15
I'm afraid I'm not sure where the Vigor was produced, however its wireless area is set to Europe.
I have tried with another access point which can auto connect at startup but the CRDA is set to DE to get a connection. How do these drivers choose the domain because it seems to be a what ever works heh.

---

### Post by chili555 on 2012-05-15
I believe that the card starts with wherever it was made to be sold and then is updated by the AP, which may or may not be located in the country it was made to be sold, and discards any unavailable channels as above.

Whenever I start to answer a post involving a card or router purchased at that famous on-line auction site, I grit my teeth, take a tranquilizer and suspect cfg80211, since at least one piece of the puzzle may not be where it thinks it should be.

You might write a conf file, reboot and see what happens:```
sudo gedit (vim, nano, emacs, et al) /etc/modprobe.d/cfg80211.conf
```Add a single line:```
options cfg80211 ieee80211_regdom=DE
```Proofread, save and close gedit. Reboot. Does it work? If not, I'd change to JP and even GB and try again.

---

