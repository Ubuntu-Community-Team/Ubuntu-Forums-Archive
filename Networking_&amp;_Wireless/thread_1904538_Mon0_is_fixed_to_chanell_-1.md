---
title: "Mon0 is fixed to chanell -1"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by thig1002 on 2012-01-04
**Wifi card:** Intel Wifi Pro 5100
**Chip-set:** Intel Wifi 5100
**Drivers:** iwlagn

I set my card in monitor mode:

```

Mint-Ninja ninja # airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
825    NetworkManager
841    avahi-daemon
842    avahi-daemon
850    wpa_supplicant
19470    dhclient
Process with PID 19470 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Intel 4965/5xxx    iwlagn - [phy0]
                (monitor mode enabled on mon0)

```I then scan the air on the channel of my wireless network: 

```

airodump-ng -c 6 mon0

CH  6 ][ Elapsed: 32 s ][ 2012-01-04 22:09 ][ fixed channel mon0: -1                            

```The problem is that it is fixed to channel -1. I need it on channel 6 for aireplay-ng.

How do I fix this issue?

---

### Post by Basher101 on 2012-01-04
1. this forum supports no illegal activies at all (you should know reading the forum rules)

2. i know how to fix the "fixed channel" bug and would only help you if you would scan the air to **ONLY** check how secure **_your OWN_** wireless password is. Scanning for other access points [B][U][COLOR="Red"]other than your's is illegal.
[/COLOR][/U][/B]
regards

---

### Post by thig1002 on 2012-01-05
That's what I'm doing. My Wireless access point is Party Time, broadcasting on channel six. If you would like a screenshot, I'll post it.

Also, I have the go ahead to Pen-test our wireless access point at work. But I was testing the compatiblility of my hardware at home. 

I am an IT Assistant in charge of Internet Security. I work for The Center for Cancer Care, in north Alabama.
 
I hope this calms your nerves on helping me ;)

---

### Post by aesthetic.crazy on 2012-01-15
use this,

[http://ubuntuforums.org/showthread.php?p=11612383#post11612383](http://ubuntuforums.org/showthread.php?p=11612383#post11612383)

---

