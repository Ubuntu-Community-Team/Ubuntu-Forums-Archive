---
title: "Wireless network continually dropping and reconnecting"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by askates on 2011-04-13
Within the last couple of days or so, my wireless has been on the fritz. It keeps disconnecting and reconnecting every minute or so, which is annoying to say the least. The information relating to my wireless network is:

Laptop model: Toshiba Satellite L350
Wireless interface: Atheros AR5001 Wireless Network Adapter
Interface:
ifconfig:```
wlan0     Link encap:Ethernet  HWaddr 00:21:63:d6:4c:e9  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fed6:4ce9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54970973 (54.9 MB)  TX bytes:4038074 (4.0 MB)

```iwconfig:```
wlan0     IEEE 802.11bg  ESSID:"Bebox435717"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:44:59:E4:91   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Modules:```
led_class               2633  1 ath5k
mac80211              231959  1 ath5k
ath                     8153  1 ath5k
cfg80211              144694  3 ath5k,mac80211,ath

```Kernel Boot Messages: ```
[ 4831.590552] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4831.590853] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4831.595563] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4831.595998] wlan0: authenticated
[ 4831.596024] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4831.600464] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4831.600469] wlan0: associated
[ 4832.516091] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4832.559092] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4832.559099] cfg80211: Restoring regulatory settings
[ 4832.559104] cfg80211: Calling CRDA to update world regulatory domain
[ 4832.567421] cfg80211: World regulatory domain updated:
[ 4832.567426]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4832.567430]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4832.567434]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4832.567438]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4832.567442]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4832.567445]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4832.583337] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4832.693828] r8169 0000:02:00.0: eth0: link down
[ 4832.694091] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4837.331303] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4838.330579] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4838.333002] wlan0: authenticated
[ 4838.333030] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4838.339627] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4838.339632] wlan0: associated
[ 4838.340739] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4838.980082] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4839.021053] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4839.021060] cfg80211: Restoring regulatory settings
[ 4839.021065] cfg80211: Calling CRDA to update world regulatory domain
[ 4839.026499] cfg80211: World regulatory domain updated:
[ 4839.026504]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4839.026508]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4839.026512]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4839.026516]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4839.026519]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4839.026523]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4839.043839] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4839.116774] r8169 0000:02:00.0: eth0: link down
[ 4839.117029] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4839.275805] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4841.734885] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4841.735299] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4841.739065] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4841.740804] wlan0: authenticated
[ 4841.740826] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4841.759880] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4841.759884] wlan0: associated
[ 4841.760651] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4842.384817] type=1400 audit(1302716006.093:40): apparmor="DENIED" operation="open" parent=10932 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=11000 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[ 4851.788595] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4851.812583] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4851.812591] cfg80211: Restoring regulatory settings
[ 4851.812596] cfg80211: Calling CRDA to update world regulatory domain
[ 4851.819162] cfg80211: World regulatory domain updated:
[ 4851.819167]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4851.819171]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4851.819175]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4851.819179]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4851.819182]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4851.819186]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4852.138087] wlan0: no IPv6 routers present
[ 4852.830933] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4852.836964] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4852.838687] wlan0: authenticated
[ 4852.838736] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4852.841193] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4852.841197] wlan0: associated
[ 4862.872087] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4862.896192] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4862.896200] cfg80211: Restoring regulatory settings
[ 4862.896204] cfg80211: Calling CRDA to update world regulatory domain
[ 4862.903123] cfg80211: World regulatory domain updated:
[ 4862.903128]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4862.903133]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4862.903137]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4862.903140]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4862.903144]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4862.903148]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4863.870888] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4863.871857] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4863.875819] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4863.877989] wlan0: authenticated
[ 4863.878015] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4863.881976] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4863.881982] wlan0: associated
[ 4869.516102] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4869.540097] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4869.540105] cfg80211: Restoring regulatory settings
[ 4869.540109] cfg80211: Calling CRDA to update world regulatory domain
[ 4869.562666] cfg80211: World regulatory domain updated:
[ 4869.562671]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4869.562676]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4869.562679]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4869.562683]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4869.562687]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4869.562691]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4870.547735] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4870.641392] r8169 0000:02:00.0: eth0: link down
[ 4870.641653] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4875.327380] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4876.326971] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4876.331177] wlan0: authenticated
[ 4876.331208] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4876.333698] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4876.333703] wlan0: associated
[ 4876.334465] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4876.712572] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4876.747043] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4876.747050] cfg80211: Restoring regulatory settings
[ 4876.747055] cfg80211: Calling CRDA to update world regulatory domain
[ 4876.756445] cfg80211: World regulatory domain updated:
[ 4876.756450]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4876.756454]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4876.756458]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4876.756462]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4876.756465]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4876.756469]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4876.767330] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4876.837595] r8169 0000:02:00.0: eth0: link down
[ 4876.837851] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4877.003831] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4879.467580] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4879.467721] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4879.471680] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4879.473457] wlan0: authenticated
[ 4879.473480] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4879.476898] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4879.476903] wlan0: associated
[ 4879.477656] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4880.116091] type=1400 audit(1302716043.818:41): apparmor="DENIED" operation="open" parent=11114 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=11181 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[ 4889.504578] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4889.528581] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4889.528588] cfg80211: Restoring regulatory settings
[ 4889.528593] cfg80211: Calling CRDA to update world regulatory domain
[ 4889.533871] cfg80211: World regulatory domain updated:
[ 4889.533876]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4889.533880]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4889.533884]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4889.533887]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4889.533891]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4889.533895]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4890.136028] wlan0: no IPv6 routers present
[ 4890.502754] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4890.506580] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4890.508694] wlan0: authenticated
[ 4890.508721] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4890.510916] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4890.510921] wlan0: associated
[ 4900.548091] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4900.572105] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4900.572113] cfg80211: Restoring regulatory settings
[ 4900.572118] cfg80211: Calling CRDA to update world regulatory domain
[ 4900.577212] cfg80211: World regulatory domain updated:
[ 4900.577216]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4900.577220]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4900.577224]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4900.577228]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4900.577232]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4900.577235]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4901.546055] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4901.546453] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4901.549878] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4901.551932] wlan0: authenticated
[ 4901.551958] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4901.554193] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4901.554198] wlan0: associated
[ 4911.592617] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4911.628592] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4911.628600] cfg80211: Restoring regulatory settings
[ 4911.628604] cfg80211: Calling CRDA to update world regulatory domain
[ 4911.633812] cfg80211: World regulatory domain updated:
[ 4911.633817]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4911.633821]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4911.633825]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4911.633829]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4911.633833]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4911.633837]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4912.594623] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4912.596671] wlan0: authenticated
[ 4912.596698] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4912.599212] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4912.599217] wlan0: associated
[ 4922.840178] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4922.868101] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4922.868108] cfg80211: Restoring regulatory settings
[ 4922.868113] cfg80211: Calling CRDA to update world regulatory domain
[ 4922.873753] cfg80211: World regulatory domain updated:
[ 4922.873757]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4922.873762]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4922.873766]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4922.873770]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4922.873773]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4922.873777]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4923.512035] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4923.597441] r8169 0000:02:00.0: eth0: link down
[ 4923.597698] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4928.331428] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4929.331113] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4929.333637] wlan0: authenticated
[ 4929.333666] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4929.335845] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4929.335849] wlan0: associated
[ 4929.337088] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4929.756074] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4929.797156] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4929.797164] cfg80211: Restoring regulatory settings
[ 4929.797168] cfg80211: Calling CRDA to update world regulatory domain
[ 4929.803217] cfg80211: World regulatory domain updated:
[ 4929.803222]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4929.803226]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4929.803230]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4929.803234]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4929.803238]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4929.803242]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4929.819805] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4929.893154] r8169 0000:02:00.0: eth0: link down
[ 4929.893414] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4930.075821] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4932.538783] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4932.542890] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4932.544604] wlan0: authenticated
[ 4932.544623] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4932.547114] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4932.547118] wlan0: associated
[ 4932.547855] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4942.551659] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4942.576092] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4942.576100] cfg80211: Restoring regulatory settings
[ 4942.576104] cfg80211: Calling CRDA to update world regulatory domain
[ 4942.581737] cfg80211: World regulatory domain updated:
[ 4942.581741]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4942.581746]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4942.581750]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4942.581753]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4942.581757]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4942.581760]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4943.544023] wlan0: no IPv6 routers present
[ 4943.550298] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4943.551359] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4943.555334] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4943.557515] wlan0: authenticated
[ 4943.557540] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4943.560725] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4943.560730] wlan0: associated
[ 4944.242225] type=1400 audit(1302716107.946:42): apparmor="DENIED" operation="open" parent=11296 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=11336 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[ 4953.588577] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4953.612587] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4953.612596] cfg80211: Restoring regulatory settings
[ 4953.612600] cfg80211: Calling CRDA to update world regulatory domain
[ 4953.618195] cfg80211: World regulatory domain updated:
[ 4953.618200]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4953.618204]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4953.618208]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4953.618212]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4953.618215]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4953.618219]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4954.591228] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4954.596351] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4954.603302] wlan0: authenticated
[ 4954.603336] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4954.605555] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4954.605561] wlan0: associated
[ 4958.516594] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4958.537697] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4958.537704] cfg80211: Restoring regulatory settings
[ 4958.537708] cfg80211: Calling CRDA to update world regulatory domain
[ 4958.571428] cfg80211: World regulatory domain updated:
[ 4958.571434]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4958.571438]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4958.571442]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4958.571446]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4958.571450]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4958.571454]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4959.582776] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4959.586605] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4959.596606] wlan0: authenticated
[ 4959.596637] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4959.600331] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4959.600336] wlan0: associated
[ 4961.480139] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4961.539553] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4961.539586] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4961.539591] cfg80211: Restoring regulatory settings
[ 4961.539595] cfg80211: Calling CRDA to update world regulatory domain
[ 4961.545434] cfg80211: World regulatory domain updated:
[ 4961.545440]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4961.545444]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4961.545448]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4961.545452]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4961.545456]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4961.545460]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4961.625216] r8169 0000:02:00.0: eth0: link down
[ 4961.625475] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4966.331794] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4967.334577] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4967.336352] wlan0: authenticated
[ 4967.336378] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4967.339258] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4967.339270] wlan0: associated
[ 4967.340691] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4967.740143] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4967.781029] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4967.781038] cfg80211: Restoring regulatory settings
[ 4967.781042] cfg80211: Calling CRDA to update world regulatory domain
[ 4967.787135] cfg80211: World regulatory domain updated:
[ 4967.787140]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4967.787144]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4967.787149]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4967.787152]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4967.787156]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4967.787159]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4967.803803] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4967.876810] r8169 0000:02:00.0: eth0: link down
[ 4967.877064] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4968.055807] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4970.514873] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4970.518773] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4970.520477] wlan0: authenticated
[ 4970.520497] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4970.523090] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4970.523094] wlan0: associated
[ 4970.523837] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4971.165297] type=1400 audit(1302716134.872:43): apparmor="DENIED" operation="open" parent=11449 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=11516 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[ 4980.526528] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4980.548615] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4980.548623] cfg80211: Restoring regulatory settings
[ 4980.548627] cfg80211: Calling CRDA to update world regulatory domain
[ 4980.554024] cfg80211: World regulatory domain updated:
[ 4980.554029]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4980.554033]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4980.554037]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4980.554041]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4980.554045]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4980.554048]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4980.656034] wlan0: no IPv6 routers present
[ 4981.523438] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4981.523938] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4981.528181] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4981.530257] wlan0: authenticated
[ 4981.530289] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4981.533818] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4981.533824] wlan0: associated
[ 4991.560570] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4991.584582] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4991.584591] cfg80211: Restoring regulatory settings
[ 4991.584595] cfg80211: Calling CRDA to update world regulatory domain
[ 4991.589969] cfg80211: World regulatory domain updated:
[ 4991.589974]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4991.589978]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4991.589982]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4991.589986]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4991.589990]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4991.589993]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4992.558277] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 4992.562106] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 4992.563854] wlan0: authenticated
[ 4992.563878] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 4992.566325] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 4992.566330] wlan0: associated
[ 5002.596598] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 5002.608860] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 5002.608869] cfg80211: Restoring regulatory settings
[ 5002.608873] cfg80211: Calling CRDA to update world regulatory domain
[ 5002.614267] cfg80211: World regulatory domain updated:
[ 5002.614272]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5002.614276]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5002.614281]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5002.614284]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5002.614288]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5002.614291]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5003.610248] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 5003.612291] wlan0: authenticated
[ 5003.612317] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 5003.614695] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 5003.614700] wlan0: associated
[ 5013.888087] wlan0: deauthenticating from 00:26:44:59:e4:91 by local choice (reason=3)
[ 5013.912097] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 5013.912105] cfg80211: Restoring regulatory settings
[ 5013.912110] cfg80211: Calling CRDA to update world regulatory domain
[ 5013.917612] cfg80211: World regulatory domain updated:
[ 5013.917617]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5013.917621]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5013.917625]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5013.917629]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5013.917632]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5013.917636]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5014.503805] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5014.609209] r8169 0000:02:00.0: eth0: link down
[ 5014.609470] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5018.516231] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5019.562940] wlan0: authenticate with 00:26:44:59:e4:91 (try 1)
[ 5019.564674] wlan0: authenticated
[ 5019.564701] wlan0: associate with 00:26:44:59:e4:91 (try 1)
[ 5019.567188] wlan0: RX AssocResp from 00:26:44:59:e4:91 (capab=0x411 status=0 aid=2)
[ 5019.567193] wlan0: associated
[ 5019.573333] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5030.320463] wlan0: no IPv6 routers present
[ 5606.888527] type=1400 audit(1302716770.592:44): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=12514 comm="apparmor_parser"
[ 5606.888695] type=1400 audit(1302716770.596:45): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=12514 comm="apparmor_parser"
[ 5606.888816] type=1400 audit(1302716770.596:46): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=12514 comm="apparmor_parser"

```Network Config: ```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:8e:30:12
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:3000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:63:d6:4c:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.1.67 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:94600000-9460ffff

```Scan for Networks: ```
wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:59:E4:91
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Bebox435717"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000258eac8e4
                    Extra: Last beacon: 42360ms ago
                    IE: Unknown: 000B4265626F78343335373137
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```Ubuntu Version 10.10
Kernel: 2.6.35-28-generic i686
Restarting Network: ```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                   
```

---

### Post by askates on 2011-04-13
If anyone could shed some light on this, it would be very much appreciated. My internet is all but unusable.

---

### Post by askates on 2011-04-21
A final bump...?

---

### Post by Kudo3035 on 2011-05-06
i have the same wireless card in a compaq f700, im still new to linux and cant post all the info but its very unstable sometimes ill get 5mins sometimes 30 b4 a disconnect then i have to reboot the comp to reconnect. no one has been able to post or help and i cant find anything else :(

---

