---
title: "Wifi connects to some, not to other networks"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by josvanr on 2010-03-17
I've been using wifi on my

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

with no trouble for some time. But today I tried to connect to a network in a bar and that didn't work. In dmesg I see

[13635.269833] wlan0: direct probe to AP 00:18:6e:34:28:c0 try 1
[13635.468065] wlan0: direct probe to AP 00:18:6e:34:28:c0 try 2
[13635.668089] wlan0: direct probe to AP 00:18:6e:34:28:c0 try 3
[13635.870675] wlan0: direct probe to AP 00:18:6e:34:28:c0 timed out
 
I could connect to another network there, then I see stuff like this:

[14724.056333] wlan0: no probe response from AP 00:1e:c2:a2:07:fe - disassociating
[14725.651022] wlan0: authenticate with AP 00:1e:c2:a2:07:fe
[14725.652552] wlan0: authenticated
[14725.652555] wlan0: associate with AP 00:1e:c2:a2:07:fe
[14725.654719] wlan0: RX ReassocResp from 00:1e:c2:a2:07:fe (capab=0x401 status=0 aid=4)
[14725.654723] wlan0: associated
[14749.652079] wlan0: no probe response from AP 00:1e:c2:a2:07:fe - disassociating
[14757.728558] wlan0: authenticate with AP 00:1e:c2:a2:07:fe
[14757.739844] wlan0: authenticated
[14757.739849] wlan0: associate with AP 00:1e:c2:a2:07:fe
[14757.744017] wlan0: RX ReassocResp from 00:1e:c2:a2:07:fe (capab=0x401 status=0 aid=4)
[14757.744021] wlan0: associated


so the card seems to be working.

How do I proceed to get this to work or at least see why it doesn't work?

josvanr

---

