---
title: "WLAN with Atheros AR5001 finally working"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by karg on 2010-01-17
My 64-bit Karmic was having serious WLAN issues in Fujitsu Siemens PA 1538 laptop which has Atheros AR5001 WLAN card.

1. Default installation didn't find the WLAN card at all.
2. Wicd found the WLAN card, but the connection was stalling/disconnecting now and then. Also the signal level was quite bad even if the WLAN base station was near.
3. MadWIFI caused even more problems. More connection stalling/disconnecting and also quite bad signal level.

From this thread: [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072) I noticed from some page X that MadWIFI works only for 32-bit installations. (IMHO that should have been mentioned on page 1...)

Only after removing MadWIFI and installing compat-wireless all the WLAN issues were solved. Now the connection is really fast and stable including excellent signal level.

Before compat-wireless Tx-Power was only 16 dBm and no more was accepted.

After compat-wireless installation Tx-Power is 20 dBm.

---

