---
title: "WIFI getting wlan0: deauthenticated (AT&amp;T)"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by whackco on 2009-05-10
[SIZE=2]I am using 9.04 on a Gateway T-1620 laptop.  Generally the WLAN works fine, but it does not seem to work well with AT&T and T-Mobile Hotspots.  When at these locations I authenticate, but the connections breaks off and is un-usable.  The log files show the following error: [/SIZE]


[INDENT]*[SIZE=1]May  6 16:21:04 EM-LNX kernel: [ 1061.368071] wlan0: direct probe to AP 00:0f:34:48:2b:80 try 1[/SIZE]*
*[SIZE=1]May  6 16:21:04 EM-LNX kernel: [ 1061.370257] wlan0 direct probe responded[/SIZE]*
*[SIZE=1]May  6 16:21:04 EM-LNX kernel: [ 1061.370269] wlan0: authenticate with AP 00:0f:34:48:2b:80[/SIZE]*
*[SIZE=1]May  6 16:21:04 EM-LNX kernel: [ 1061.372062] wlan0: authenticated[/SIZE]*
*[SIZE=1]May  6 16:21:04 EM-LNX kernel: [ 1061.372078] wlan0: associate with AP 00:0f:34:48:2b:80[/SIZE]*
*[SIZE=1]May  6 16:21:04 EM-LNX NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated  [/SIZE]*
*[SIZE=1]May  6 16:21:04 EM-LNX NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed  [/SIZE]*
*[SIZE=1]May  6 16:21:04 EM-LNX kernel: [ 1061.373883] wlan0: RX ReassocResp from 00:0f:34:48:2b:80 (capab=0x401 status=0 aid=205)[/SIZE]*
*[SIZE=1]May  6 16:21:04 EM-LNX kernel: [ 1061.373890] wlan0: associated[/SIZE]*
*[SIZE=1]May  6 16:21:08 EM-LNX NetworkManager: <debug> [1241652068.000833] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:34:48:2B:80 (attwifi)  [/SIZE]*
*[SIZE=1]May  6 16:21:08 EM-LNX NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected  [/SIZE]*
*[SIZE=1]May  6 16:21:08 EM-LNX kernel: [ 1065.225722] wlan0: deauthenticated[/SIZE]*
[SIZE=1]*May  6 16:21:08 EM-LNX NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning *
[/SIZE]
[/INDENT][SIZE=2]I assume this is caused by the driver, hardware, or NetworkManager error.   Can anyone help me? [/SIZE]

---

