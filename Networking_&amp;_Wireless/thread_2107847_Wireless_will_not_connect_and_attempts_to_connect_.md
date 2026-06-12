---
title: "Wireless will not connect and attempts to connect while on wired connection"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by peperomia on 2013-01-22
Despite having a System76 laptop, my wireless has always been a bit fussy. (See [here]("http://ubuntuforums.org/showthread.php?t=1864882") and [here]("http://ubuntuforums.org/showthread.php?t=2034050") for gory and likely irrelevant details.) As described in the links, I developed some workarounds for the problems I was having before, but now they aren't working at all.

Problem 1: Now I cannot connect to any wireless networks (whether unsecured, WEP, or WPA). I can see networks, but when I attempt to connect, I am just repeatedly asked for my password. In the case of an unsecured network, it looks like it's trying to connect over and over (the little Network Manager radio waves keep "moving").

Problem 2: When I am connected to a wired connection and there is a "remembered" wireless connection available, my computer tries to connect to it, repeatedly asking for my password. 

I've attached all of the information described in [B][HOWTO post a Wireless issue]("http://ubuntuforums.org/showthread.php?p=6183681")

[/B]But I think this bit from ```
dmesg
``` is the clue to what's going wrong. 

```
[  108.113189] wlan0: authenticate with 5c:d9:98:6a:fe:78 (try 1)
[  108.115020] wlan0: authenticated
[  108.119412] wlan0: failed to insert Dummy STA entry for the AP (error -17)
[  172.685403] wlan0: deauthenticating from 5c:d9:98:6a:fe:78 by local choice (reason=2)
[  172.726388] wlan0: authenticate with 5c:d9:98:6a:fe:78 (try 1)
[  172.729685] wlan0: authenticated
[  172.730035] wlan0: failed to insert Dummy STA entry for the AP (error -17)
[  236.939900] jme 0000:04:00.5: eth0: Link is up at ANed: 100 Mbps, Full-Duplex, MDI
[  236.942745] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  543.037288] wlan0: deauthenticating from 5c:d9:98:6a:fe:78 by local choice (reason=2)
[  543.078831] wlan0: authenticate with 5c:d9:98:6a:fe:78 (try 1)
[  543.082216] wlan0: authenticated
[  543.082608] wlan0: failed to insert Dummy STA entry for the AP (error -17)
[  550.346419] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  550.346648] wlan0: deauthenticating from 5c:d9:98:6a:fe:78 by local choice (reason=3)
[  550.395991] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[  550.396001] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[  550.396006] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5)
[  919.916916] intel ips 0000:00:1f.6: MCP limit exceeded: Avg power 19703, limit 18000
[ 1889.876660] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 1889.878333] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 1889.885164] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[ 1890.041343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1897.757081] wlan0: authenticate with 5c:d9:98:6a:fe:78 (try 1)
[ 1897.758898] wlan0: authenticated
[ 1897.839296] wlan0: associate with 5c:d9:98:6a:fe:78 (try 1)
[ 1898.037683] wlan0: associate with 5c:d9:98:6a:fe:78 (try 2)
[ 1898.040131] wlan0: deauthenticated from 5c:d9:98:6a:fe:78 (Reason: 9)
[ 2262.054745] wlan0: authenticate with 5c:d9:98:6a:fe:78 (try 1)
[ 2262.056570] wlan0: authenticated
[ 2262.061954] wlan0: failed to insert Dummy STA entry for the AP (error -17)
[ 2625.788833] wlan0: deauthenticating from 5c:d9:98:6a:fe:78 by local choice (reason=2)
[ 2625.829363] wlan0: authenticate with 5c:d9:98:6a:fe:78 (try 1)
[ 2625.833584] wlan0: authenticated
[ 2625.834035] wlan0: failed to insert Dummy STA entry for the AP (error -17)

```

Unfortunately, I don't understand what it means and didn't have much luck googling for  "failed to insert Dummy STA entry for the AP." Help?

---

