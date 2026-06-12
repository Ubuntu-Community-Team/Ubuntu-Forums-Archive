---
title: "WiFi connection is lost very often"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by sonikmh on 2010-05-19
I was about to update my existing 8.10 instance of ubuntu with the fresh one, so I downloaded the latest ubuntu 10.04 and booted it up, but in a few minutes I came acros with this problem: wifi connection (with WPA personal encryption) is established correctly (using NetworkManager), but after a 30s or so the connection is lost and it's connecting again, connected, but then lost again and again.

My wifi card is Intel Pro Wireless 3945ABG

here is a part print of dmesg:

```
[ 24.324076] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[ 25.068287] lp: driver loaded but no devices found
[ 25.123909] ppdev: user-space parallel port driver
[ 82.934132] wlan0: deauthenticating from 00:c0:ca:1d:1b:d5 by local choice (reason=3)
[ 82.936540] wlan0: direct probe to AP 00:c0:ca:1d:1b:d5 (try 1)
[ 82.953468] wlan0: direct probe responded
[ 82.953479] wlan0: authenticate with AP 00:c0:ca:1d:1b:d5 (try 1)
[ 82.961821] wlan0: authenticated
[ 82.961863] wlan0: associate with AP 00:c0:ca:1d:1b:d5 (try 1)
[ 82.976325] wlan0: RX AssocResp from 00:c0:ca:1d:1b:d5 (capab=0x411 status=0 aid=193)
[ 82.976333] wlan0: invalid aid value 193; bits 15:14 not set
[ 82.976338] wlan0: associated
[ 82.978167] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 83.003686] wlan0: disassociated from 00:c0:ca:1d:1b:d5 (Reason: 14)
[ 83.020069] wlan0: deauthenticating from 00:c0:ca:1d:1b:d5 by local choice (reason=3)
```

I would like o know, if it's safe to do an install and then it will be ok, or what's the solution to this?

---

### Post by iponeverything on 2010-05-19
The issue will very likely be present in your initial install. There is a chance that might be resolved trough the first round of package updates, but I would not count on it.

This looks like it might be your bug:


[https://bugs.launchpad.net/network-manager/+bug/425455](https://bugs.launchpad.net/network-manager/+bug/425455)

---

### Post by anje on 2010-05-19
I suspect this is the same (or related to) the issue that I've been having.  I'm not losing my connection as frequently as described in the bug report, but it goes down annoyingly regularly.

I posted about it in [this thread](http://ubuntuforums.org/showthread.php?t=1482347), which has since died of obscurity.  Same Intel 3945ABG Wireless controller.

---

