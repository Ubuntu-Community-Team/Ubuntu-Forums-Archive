---
title: "Wireless not connecting to certain access points"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by ak123 on 2012-09-22
I've been having a rather strange problem the past few days. I recently downloaded some updates on my ubuntu 12.04 install, and since then, haven't been able to connect to a few networks. I can connect to the majority of networks. However, I CAN'T connect to a few very important ones, including the one in my room at home and the one at the office. 

With the the ones mentioned above, I can see them in the drop down list of networks in network manager and can even click on them. However, after this, it keeps trying to connect, but fails and asks me for the password repeatedly every minute or so before giving up. 

I have been through almost every post and solution I could find. None of these worked (a couple even broke my system). Another puzzling point is the fact that the same problem persists even when using my LiveUSB. Please help, it's driving me nuts.

Specs: Acer Aspire One D270
Network controller: Atheros Communications Inc. AR9485

please tell if you need any more specs.

---

### Post by ak123 on 2012-09-22
bump. I need this fixed very soon actually.

---

### Post by manadi on 2012-09-22
Have you tried WICD ?

---

### Post by ak123 on 2012-09-22
Yes I have. Doesn't make the slightest bit of difference.

---

### Post by manadi on 2012-09-22
Whats the difference between the APs you can connect to, and the ones you cannot ? Different security configurations? Which one ?

---

### Post by ak123 on 2012-09-22
None whatsoever other than names and passwords. They all use WPA encryption, which was supposed to fix this problem for others.

---

### Post by manadi on 2012-09-22
When using WICD, do you get an error message which points to a specific problem ?

---

### Post by ak123 on 2012-09-22
No. It just failed to connect and moved on to the next access point which DID connect.

---

### Post by manadi on 2012-09-22
Well its hard to say. Can you disable "Connect Automatically" option in WICD for all the networks except the one you want to connect(and are not able to) and try to check the dmesg log? Maybe paste the relevant part here too.

---

### Post by ak123 on 2012-09-22
Alright, I disabled the automatically connect option. Now, it goes through the standard steps, then gets stuck at the step "validating connection". When it fails, it says it failed due to bad password, but this is simply not true. I have checked the password three times. It has been entered correctly and the same password works on all my other devices.

---

### Post by manadi on 2012-09-22
Now you are at the same problem which I posted yesterday except that I am stuck with WEP key. I am yet to receive a reply. May the "network-manager deamon" be with you.

---

### Post by ak123 on 2012-09-22
I've looked in dmesg for two particular terms: wlan and ath9k. The latter is what I suspect might be the problem. Although all the results I hunted for on the web for fixing this particular issue haven't worked. I have found nothing out of the ordinary in the results either of the two commands 

Posting the results for each one:

dmesg | grep wlan
```
amol@amol-AOD270:~$ dmesg | grep wlan
[   37.057335] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.059559] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.564973] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[   40.566947] wlan0: authenticated
[   40.573683] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[   40.576179] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=3)
[   40.576190] wlan0: associated
[   40.576201] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[   40.576208] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[   40.582361] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   41.927438] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[   52.894699] wlan0: no IPv6 routers present
[   87.324325] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[   87.374258] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[   87.374266] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[   87.374272] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[   91.012151] wlan0: direct probe to 00:1e:40:1b:dd:9a (try 1/3)
[   91.014750] wlan0: direct probe responded
[   91.042765] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[   91.242560] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 2)
[   91.442379] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 3)
[   91.642186] wlan0: authentication with 00:1e:40:1b:dd:9a timed out
[  103.414943] wlan0: direct probe to 00:1e:40:1b:dd:9a (try 1/3)
[  103.417307] wlan0: direct probe responded
[  103.451041] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  103.650841] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 2)
[  103.850662] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 3)
[  104.050484] wlan0: authentication with 00:1e:40:1b:dd:9a timed out
[  109.951633] wlan0: direct probe to 00:1e:40:1b:dd:9a (try 1/3)
[  109.954192] wlan0: direct probe responded
[  109.992884] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  110.192667] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 2)
[  110.392506] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 3)
[  110.592311] wlan0: authentication with 00:1e:40:1b:dd:9a timed out
[  116.490047] wlan0: direct probe to 00:1e:40:1b:dd:9a (try 1/3)
[  116.492744] wlan0: direct probe responded
[  116.518724] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  116.718527] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 2)
[  116.918361] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 3)
[  117.118153] wlan0: authentication with 00:1e:40:1b:dd:9a timed out
[  134.755999] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[  134.757955] wlan0: authenticated
[  134.760460] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[  134.762925] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=3)
[  134.762936] wlan0: associated
[  134.762946] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[  134.762954] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[  135.480824] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[  145.703148] wlan0: no IPv6 routers present
[  181.248383] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[  181.285696] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[  181.285707] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[  181.285715] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[  184.946699] wlan0: direct probe to 00:1e:40:1b:dd:9a (try 1/3)
[  184.954231] wlan0: direct probe responded
[  184.990334] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  185.189988] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 2)
[  185.393715] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 3)
[  185.593546] wlan0: authentication with 00:1e:40:1b:dd:9a timed out
[  191.536864] wlan0: direct probe to 00:1e:40:1b:dd:9a (try 1/3)
[  191.539323] wlan0: direct probe responded
[  191.591882] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  191.791701] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 2)
[  191.991562] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 3)
[  192.191319] wlan0: authentication with 00:1e:40:1b:dd:9a timed out
[  198.160819] wlan0: direct probe to 00:1e:40:1b:dd:9a (try 1/3)
[  198.163700] wlan0: direct probe responded
[  198.205804] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  198.405496] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 2)
[  198.605257] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 3)
[  198.805076] wlan0: authentication with 00:1e:40:1b:dd:9a timed out
[  234.208708] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  234.210987] wlan0: authenticated
[  234.220810] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[  234.227216] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=1)
[  234.227224] wlan0: associated
[  234.227232] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[  234.227238] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[  234.228127] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[  244.633829] wlan0: no IPv6 routers present
[  317.931278] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[  317.931290] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[  317.931299] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[  319.245755] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  319.248265] wlan0: authenticated
[  319.248868] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[  319.447453] wlan0: associate with 00:1e:40:1b:dd:9a (try 2)
[  319.647348] wlan0: associate with 00:1e:40:1b:dd:9a (try 3)
[  319.847294] wlan0: association with 00:1e:40:1b:dd:9a timed out
[  321.516219] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  322.244673] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  322.316334] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  325.093169] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[  325.095263] wlan0: authenticated
[  325.102868] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[  325.105417] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=3)
[  325.105430] wlan0: associated
[  325.105442] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[  325.105450] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[  325.112613] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  325.478839] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[  336.367893] wlan0: no IPv6 routers present
[  371.126472] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[  371.168647] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[  371.168658] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[  371.168666] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[  374.531657] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  374.536587] wlan0: authenticated
[  374.545902] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[  374.553227] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=1)
[  374.553239] wlan0: associated
[  374.553250] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[  374.553258] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[  374.559428] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[  384.954368] wlan0: no IPv6 routers present
[  396.956401] wlan0: deauthenticated from 00:1e:40:1b:dd:9a (Reason: 7)
[  396.956497] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[  396.956506] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[  396.956513] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[  397.957847] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[  397.960071] wlan0: authenticated
[  397.960633] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[  397.965240] wlan0: RX ReassocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=1)
[  397.965252] wlan0: associated
[  397.965265] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[  397.965273] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[  397.966471] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 1515.018164] wlan0: deauthenticating from 00:1e:40:1b:dd:9a by local choice (reason=3)
[ 1515.052862] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 1515.052882] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 1515.052898] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[ 1515.228863] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1515.396960] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1515.492851] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1516.270642] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1518.970020] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 1518.972757] wlan0: authenticated
[ 1518.974846] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 1518.977647] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=1)
[ 1518.977659] wlan0: associated
[ 1518.977672] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 1518.977679] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 1518.978580] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1518.978883] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 1529.750532] wlan0: no IPv6 routers present
[ 1539.086544] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 1539.086572] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 1539.086594] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[ 1540.150380] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 1540.153014] wlan0: authenticated
[ 1540.154878] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 1540.352101] wlan0: deauthenticating from 00:1e:40:1b:dd:9a by local choice (reason=3)
[ 1540.434154] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1540.921739] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1540.986302] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1543.661852] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 1543.667674] wlan0: authenticated
[ 1543.668815] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 1543.671587] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=1)
[ 1543.671599] wlan0: associated
[ 1543.671610] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 1543.671618] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 1543.672685] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 1543.674692] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1543.684007] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1547.511189] wlan0: deauthenticating from 00:1e:40:1b:dd:9a by local choice (reason=3)
[ 1547.537823] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 1547.537835] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 1547.537843] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[ 1548.613488] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[ 1548.615473] wlan0: authenticated
[ 1548.625382] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[ 1548.627937] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=6)
[ 1548.627948] wlan0: associated
[ 1548.627959] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 1548.627968] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 1549.000716] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[ 1550.326408] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[ 1550.373892] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 1550.373910] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 1550.373917] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[ 1550.470384] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1550.917498] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1550.941684] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1553.683995] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[ 1553.687292] wlan0: authenticated
[ 1553.688203] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[ 1553.690672] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=3)
[ 1553.690684] wlan0: associated
[ 1553.690695] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 1553.690704] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 1553.691606] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1554.053457] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[ 1565.012370] wlan0: no IPv6 routers present
[ 1598.853032] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[ 1598.903597] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 1598.903609] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 1598.903617] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[ 1599.851335] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 1599.855739] wlan0: authenticated
[ 1599.863257] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 1599.870595] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=1)
[ 1599.870608] wlan0: associated
[ 1599.870619] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 1599.870627] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 1599.871513] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 1610.330926] wlan0: no IPv6 routers present
[ 5103.543903] wlan0: deauthenticating from 00:1e:40:1b:dd:9a by local choice (reason=3)
[ 5103.544273] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 5103.544286] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 5103.544295] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[ 5109.306089] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5109.434934] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5115.937262] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5116.514883] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5133.609224] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5134.187347] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5136.924036] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[ 5136.926151] wlan0: authenticated
[ 5136.933695] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[ 5136.937309] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=5)
[ 5136.937316] wlan0: associated
[ 5136.937323] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 5136.937329] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 5136.938122] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5137.351674] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[ 5138.560163] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 5138.560173] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 5138.560181] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[ 5139.883236] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[ 5139.885190] wlan0: authenticated
[ 5139.886817] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[ 5139.895471] wlan0: RX ReassocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=5)
[ 5139.895493] wlan0: associated
[ 5139.895513] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 5139.895520] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 5140.282307] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[ 5147.507584] wlan0: no IPv6 routers present
[ 5153.454426] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[ 5153.486294] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 5153.486306] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 5153.486314] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[ 5154.435534] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 5154.443690] wlan0: authenticated
[ 5154.450064] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 5154.454477] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=1)
[ 5154.454492] wlan0: associated
[ 5154.454508] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 5154.454518] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 5154.456661] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 5164.499574] wlan0: no IPv6 routers present
[ 5825.515773] wlan0: deauthenticating from 00:1e:40:1b:dd:9a by local choice (reason=3)
[ 5825.536470] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 5825.536481] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 5825.536488] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[ 5830.059950] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5830.187358] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5834.868146] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5836.590365] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5851.988314] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5852.568040] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5855.256427] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 5855.258631] wlan0: authenticated
[ 5855.259977] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 5855.262718] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=5)
[ 5855.262727] wlan0: associated
[ 5855.262735] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 5855.262741] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 5855.263725] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5855.267267] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 5865.700571] wlan0: no IPv6 routers present
[ 9320.971623] wlan0: deauthenticating from 00:1e:40:1b:dd:9a by local choice (reason=3)
[ 9321.036599] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 9321.036607] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 9321.036613] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[ 9321.174755] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9322.277710] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 9322.281015] wlan0: authenticated
[ 9322.281560] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 9322.284384] wlan0: RX ReassocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=5)
[ 9322.284393] wlan0: associated
[ 9322.284401] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 9322.284407] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 9322.285208] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9322.285956] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 9324.612937] wlan0: deauthenticating from 00:1e:40:1b:dd:9a by local choice (reason=3)
[ 9324.641197] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 9324.641206] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 9324.641212] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[ 9325.305986] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9325.399900] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9364.024242] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9364.116461] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9364.523047] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9365.660690] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[ 9365.662665] wlan0: authenticated
[ 9365.681011] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[ 9365.683511] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=1)
[ 9365.683522] wlan0: associated
[ 9365.683533] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 9365.683540] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 9365.684392] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9366.047569] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[ 9376.963621] wlan0: no IPv6 routers present
[ 9411.392184] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[ 9411.439229] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 9411.439240] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 9411.439248] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[ 9415.064636] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 9415.066844] wlan0: authenticated
[ 9415.067817] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 9415.070616] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=5)
[ 9415.070627] wlan0: associated
[ 9415.070639] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 9415.070646] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 9415.072021] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 9421.215428] wlan0: deauthenticating from 00:1e:40:1b:dd:9a by local choice (reason=3)
[ 9421.246037] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 9421.246048] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 9421.246056] wlan0: moving STA 00:1e:40:1b:dd:9a to state 0
[ 9421.334412] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9421.830356] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9421.874600] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9459.962475] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9460.035210] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9460.307038] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9461.447837] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[ 9461.449797] wlan0: authenticated
[ 9461.460993] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[ 9461.463467] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=1)
[ 9461.463478] wlan0: associated
[ 9461.463488] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 9461.463495] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 9461.474267] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9461.834644] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[ 9465.950315] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[ 9465.992233] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 9465.992244] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 9465.992252] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[ 9466.087198] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9466.480788] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9466.506343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9504.757037] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9504.839220] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9505.134027] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9506.255224] wlan0: authenticate with 00:25:5e:17:4a:78 (try 1)
[ 9506.257205] wlan0: authenticated
[ 9506.265341] wlan0: associate with 00:25:5e:17:4a:78 (try 1)
[ 9506.267807] wlan0: RX AssocResp from 00:25:5e:17:4a:78 (capab=0x411 status=0 aid=1)
[ 9506.267820] wlan0: associated
[ 9506.267833] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 9506.267841] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 9506.268801] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9506.633617] wlan0: moving STA 00:25:5e:17:4a:78 to state 3
[ 9516.918052] wlan0: no IPv6 routers present
[ 9521.036342] wlan0: deauthenticating from 00:25:5e:17:4a:78 by local choice (reason=3)
[ 9521.070301] wlan0: moving STA 00:25:5e:17:4a:78 to state 2
[ 9521.070314] wlan0: moving STA 00:25:5e:17:4a:78 to state 1
[ 9521.070322] wlan0: moving STA 00:25:5e:17:4a:78 to state 0
[ 9521.995507] wlan0: authenticate with 00:1e:40:1b:dd:9a (try 1)
[ 9521.999758] wlan0: authenticated
[ 9522.008545] wlan0: associate with 00:1e:40:1b:dd:9a (try 1)
[ 9522.012050] wlan0: RX AssocResp from 00:1e:40:1b:dd:9a (capab=0x411 status=0 aid=5)
[ 9522.012059] wlan0: associated
[ 9522.012068] wlan0: moving STA 00:1e:40:1b:dd:9a to state 1
[ 9522.012074] wlan0: moving STA 00:1e:40:1b:dd:9a to state 2
[ 9522.012955] wlan0: moving STA 00:1e:40:1b:dd:9a to state 3
[ 9532.759090] wlan0: no IPv6 routers present

```

dmesg | grep ath9k
```
[   32.716408] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   32.716430] ath9k 0000:02:00.0: setting latency timer to 64
[   32.858390] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   32.859890] Registered led device: ath9k-phy0
[ 5122.101544] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 5122.101558] ath9k 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
[ 5841.021320] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 5841.021335] ath9k 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)

```

Then again, I'm not really an expert. Hopefully there's something useful in there.

---

### Post by ak123 on 2012-09-22
This seems to be a result of something that happened during the last update. I suspect they did something with the kernel that's messed it up for a few users. I saw a couple other posts like mine. But none of those had helpful replies either.

---

### Post by manadi on 2012-09-22
Well, your dmesg log says that the authentication is successful but for some funny reason, it "deauthenticates by local choice" (see log at timestamp:9465.950315). This authentication-deauthentication cycle keeps going on. A quick google pointed at some kernel level gibberish which I have no idea about. Sorry cant help further.

Btw, is this log for the case of only one network enabled for Connect Automatically in WICD?

And have you enabled the "Require IPV6" option ?

---

### Post by ak123 on 2012-09-23
Hmm. That's interesting. I didn't notice that before. Thanks. I think I can go try and debug it from there. Now I at least know what the problem is. 

The results I posted were with connect automatically disabled for all connections (from the preferences dialog). As far as making ipv6 required, I don't think I can do that because I'm fairly sure my router/ISP doesn't actually support ipv6.

---

### Post by ak123 on 2012-09-23
Interesting Update/Temporary fix: for anyone else with this issue, it would appear that the connection can be made after hibernating the computer (suspending however, doesn't seem to do the trick). Be warned though, the connection speed is quite bad if you do connect.  From  my research, it seems to be a fairly long standing bug. Somebody please fix this. It's a pretty big inconvenience.

---

