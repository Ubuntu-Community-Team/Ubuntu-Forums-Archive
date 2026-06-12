---
title: "WiFi only works sometimes"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by ttcole1254 on 2010-08-05
I'm having an issue connecting my old pc running Ubuntu 10.04 LTS to the  Internet. It only connects sometimes, and sometimes sits for half an  hour before showing that it's connected. Also when it's trying to  connect I keep getting a pop-up telling me to enter the WiFi password,  even though the password is correct every time I push connect. I ran  "dmesg | grep -e ndis -e wlan" in terminal and this is what shows up:


[   63.316371] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.992551] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[   69.992655] wlan0: deauthenticating from 00:22:75:e6:d5:63 by local choice (reason=3)
[   69.992699] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[   70.010221] wlan0: direct probe responded
[   70.010234] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 1)
[   70.208061] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 2)
[   70.211896] wlan0: authenticated
[   70.211957] wlan0: associate with AP 00:22:75:e6:d5:63 (try 1)
[   70.412095] wlan0: associate with AP 00:22:75:e6:d5:63 (try 2)
[   70.416290] wlan0: RX AssocResp from 00:22:75:e6:d5:63 (capab=0x411 status=0 aid=2)
[   70.416298] wlan0: associated
[   70.429761] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   80.460129] wlan0: deauthenticating from 00:22:75:e6:d5:63 by local choice (reason=3)
[   80.652748] wlan0: deauthenticating from 00:22:75:e6:d5:63 by local choice (reason=3)
[   80.839787] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[   81.036069] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[   81.136018] wlan0: no IPv6 routers present
[   81.236529] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[   81.436074] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[   87.391994] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[   87.592138] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[   87.792083] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[   87.992748] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[   98.142322] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[   98.147476] wlan0: direct probe responded
[   98.147488] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 1)
[   98.344089] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 2)
[   98.544048] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 3)
[   98.744079] wlan0: authentication with AP 00:22:75:e6:d5:63 timed out
[  108.896662] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  108.901819] wlan0: direct probe responded
[  108.901832] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 1)
[  109.100103] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 2)
[  109.106943] wlan0: authenticated
[  109.106995] wlan0: associate with AP 00:22:75:e6:d5:63 (try 1)
[  109.111019] wlan0: RX AssocResp from 00:22:75:e6:d5:63 (capab=0x411 status=0 aid=2)
[  109.111028] wlan0: associated
[  109.856337] wlan0: deauthenticated from 00:22:75:e6:d5:63 (Reason: 2)
[  110.716146] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  110.916045] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  111.116039] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  111.316060] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  121.555039] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  121.752092] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  121.952058] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  121.957244] wlan0: direct probe responded
[  121.957257] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 1)
[  121.963798] wlan0: authenticated
[  121.963845] wlan0: associate with AP 00:22:75:e6:d5:63 (try 1)
[  121.967765] wlan0: RX AssocResp from 00:22:75:e6:d5:63 (capab=0x411 status=0 aid=2)
[  121.967775] wlan0: associated
[  125.963656] wlan0: deauthenticating from 00:22:75:e6:d5:63 by local choice (reason=3)
[  126.993594] wlan0: deauthenticating from 00:22:75:e6:d5:63 by local choice (reason=3)
[  127.188103] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  127.193292] wlan0: direct probe responded
[  127.193306] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 1)
[  127.392068] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 2)
[  127.394586] wlan0: authenticated
[  127.394632] wlan0: associate with AP 00:22:75:e6:d5:63 (try 1)
[  127.592088] wlan0: associate with AP 00:22:75:e6:d5:63 (try 2)
[  127.599742] wlan0: RX AssocResp from 00:22:75:e6:d5:63 (capab=0x411 status=0 aid=2)
[  127.599751] wlan0: associated
[  341.928163] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  342.128089] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  342.328072] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  342.528096] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  352.684225] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  352.884045] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  353.084092] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  353.284093] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  357.184080] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  357.384103] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  357.584107] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  357.784093] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  367.944631] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  368.144064] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  368.344066] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  368.544103] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  378.700648] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  378.900107] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  379.100086] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  379.300087] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  389.456320] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  389.657254] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  389.856086] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  390.056063] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  400.212307] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  400.412078] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  400.612065] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  400.812050] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  410.968609] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  411.168120] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  411.368077] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  411.568092] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  535.320711] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  535.520111] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  535.720051] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  535.920127] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  546.076384] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  546.276067] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  546.281230] wlan0: direct probe responded
[  546.281243] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 1)
[  546.480068] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 2)
[  546.491921] wlan0: authenticated
[  546.491984] wlan0: associate with AP 00:22:75:e6:d5:63 (try 1)
[  546.692112] wlan0: associate with AP 00:22:75:e6:d5:63 (try 2)
[  546.892069] wlan0: associate with AP 00:22:75:e6:d5:63 (try 3)
[  547.092072] wlan0: association with AP 00:22:75:e6:d5:63 timed out
[  556.832948] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  556.838111] wlan0: direct probe responded
[  556.838124] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 1)
[  556.842508] wlan0: authenticated
[  556.842560] wlan0: associate with AP 00:22:75:e6:d5:63 (try 1)
[  556.846743] wlan0: RX AssocResp from 00:22:75:e6:d5:63 (capab=0x411 status=0 aid=2)
[  556.846751] wlan0: associated
[  570.875668] wlan0: deauthenticating from 00:22:75:e6:d5:63 by local choice (reason=3)
[  571.065959] wlan0: deauthenticating from 00:22:75:e6:d5:63 by local choice (reason=3)
[  571.251823] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  571.448109] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  571.648090] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  571.848050] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  581.816219] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  582.016110] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  582.216075] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  582.416090] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[  592.568624] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[  592.768091] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 2)
[  592.968061] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 3)
[  593.168103] wlan0: direct probe to AP 00:22:75:e6:d5:63 timed out
[ 1199.628200] wlan0: direct probe to AP 00:22:75:e6:d5:63 (try 1)
[ 1199.634366] wlan0: direct probe responded
[ 1199.634379] wlan0: authenticate with AP 00:22:75:e6:d5:63 (try 1)
[ 1199.636593] wlan0: authenticated
[ 1199.636664] wlan0: associate with AP 00:22:75:e6:d5:63 (try 1)
[ 1199.643913] wlan0: RX AssocResp from 00:22:75:e6:d5:63 (capab=0x411 status=0 aid=2)
[ 1199.643921] wlan0: associated

I  have another PC running the same version of Ubuntu with the same WiFi  card (Linksys WMP110), but it has no issues connecting and sits right  next to the problem machine. However, the PC with problems is running  Ubuntu 10.04 32-bit, while the one that works is running 64-bit. I'm  wondering if it might be a driver issue and if I should try ndiswrapper  as the card worked out of the box with Ubuntu. Both machines run the  same card as in I take the card out of the one that works and put it in  the old PC, so it's not an issue with the card itself..

If anyone  has any ideas as to what's causing this please let me know and thanks  in advance. Also once in a while it'll just disconnect on it's own  sometimes if it's already connected. The PC is a Compaq Presario  SR1130NX. The one that works is a Dell Inspiron 530.

---

### Post by topet2k12001 on 2011-03-01
> **ttcole1254 said:**
> I'm having an issue connecting my old pc running Ubuntu 10.04 LTS to the Internet. It only connects sometimes, and sometimes sits for half an hour before showing that it's connected. Also when it's trying to connect I keep getting a pop-up telling me to enter the WiFi password, even though the password is correct every time I push connect. I ran "dmesg | grep -e ndis -e wlan" in terminal and this is what shows up:
 
I have another PC running the same version of Ubuntu with the same WiFi card (Linksys WMP110), but it has no issues connecting and sits right next to the problem machine. However, the PC with problems is running Ubuntu 10.04 32-bit, while the one that works is running 64-bit. I'm wondering if it might be a driver issue and if I should try ndiswrapper as the card worked out of the box with Ubuntu. Both machines run the same card as in I take the card out of the one that works and put it in the old PC, so it's not an issue with the card itself..
 
If anyone has any ideas as to what's causing this please let me know and thanks in advance. Also once in a while it'll just disconnect on it's own sometimes if it's already connected. The PC is a Compaq Presario SR1130NX. The one that works is a Dell Inspiron 530.
 
Hi Friend,
 
Hm, that's strange..I have the same wireless card (WMP110) and I multi-booted my computer with a lot of Operating Systems (Windows XP/7, Ubuntu 10.04, 10.10, Kubuntu 10.10, BackTrack 4 R2, Puppy Linux)...all of them seem to be working out-of-the-box for me with the WMP110 wireless card without any configuration done.

---

### Post by keithpeter on 2011-03-01
Hello Both

Is your router using WPA or WPA2 encryption?

I'm not clever enough to work it out from your log extract.

Does the issue recur if you use WEP or no encryption just as a test?

I'm having similar symptoms on a 32 bit 10.04 installation on a thinkpad laptop that has, similarly, always worked previously. See

[http://ubuntuforums.org/showpost.php?p=10509911&postcount=5](http://ubuntuforums.org/showpost.php?p=10509911&postcount=5)

---

