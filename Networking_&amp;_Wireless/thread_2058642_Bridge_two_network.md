---
title: "Bridge two network"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by MC_Claus on 2012-09-16
Hello

I have a bit of a challenge, and seeing that I'm not quite familiar with network settings, I hope someone knows how to do it :)

I have an Ubuntu box sitting under my TV acting as a HTPC, and to this I have a HD Homerun box connected directly via eth0. 
The "homenetwork" which all my computers connect to is wlan0, and I would like to share the HDHR on eth0 with the computers on wlan0, so the rest of the computers can "see" the HDHR on the network too. 

Rough drawing of how it looks now:
[FONT="Courier New"]
+--------+............. +------+..........+------+
| Router | <--wlan0-->  | HTPC |<--eth0-->| HDHR |
+--------+............. +------+..........+------+
...^
...|
...|
+----------+   
| Internet |
| + rest of|
| network  |
+----------+ [/FONT]

IP on wlan0 is 10.0.0.29, and on eth0 is 10.42.0.1.

I have tried playing around with the brctl command, from the bridge-utils package, and tried the following:
brctl addbr mybr
brctl addif mybr eth0
brctl addif mybr wlan0
The last command outputs:
'can't add wlan0 to bridge mybr: Operation not supported'

I hope someone has a suggestion :)

---

