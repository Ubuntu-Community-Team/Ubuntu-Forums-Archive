---
title: "Wifi attempts connection but aborts."
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by TehRainbowGuy on 2012-12-26
Laptop: HP Pavilion g6-2212sa on Ubuntu 12.10

lspci | grep Network
01:00.0 Network controller: Ralink corp. Device 539b
 
Ubuntu attempts connecting to my hub with wifi and seems to abort after ~10 seconds.

Any clues to what could be going on?

** Edit

dmesg | grep wlan0
[  222.700038] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  222.700689] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  225.112729] wlan0: authenticate with 00:8b:5d:b9:29:ca
[  225.128747] wlan0: send auth to 00:8b:5d:b9:29:ca (try 1/3)
[  225.130573] wlan0: authenticated
[  225.144008] wlan0: associate with 00:8b:5d:b9:29:ca (try 1/3)
[  225.146430] wlan0: RX AssocResp from 00:8b:5d:b9:29:ca (capab=0x431 status=0 aid=7)
[  225.146652] wlan0: associated
[  225.147204] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  270.984845] wlan0: deauthenticating from 00:8b:5d:b9:29:ca by local choice (reason=3)
[  274.888033] wlan0: authenticate with 00:8b:5d:b9:29:ca
[  274.904069] wlan0: send auth to 00:8b:5d:b9:29:ca (try 1/3)
[  274.905939] wlan0: authenticated
[  274.919648] wlan0: associate with 00:8b:5d:b9:29:ca (try 1/3)
[  274.922304] wlan0: RX AssocResp from 00:8b:5d:b9:29:ca (capab=0x431 status=0 aid=7)
[  274.922512] wlan0: associated
[  319.917190] wlan0: deauthenticating from 00:8b:5d:b9:29:ca by local choice (reason=3)
[  323.829370] wlan0: authenticate with 00:8b:5d:b9:29:ca
[  323.844815] wlan0: send auth to 00:8b:5d:b9:29:ca (try 1/3)
[  323.846574] wlan0: authenticated
[  323.860386] wlan0: associate with 00:8b:5d:b9:29:ca (try 1/3)
[  323.862886] wlan0: RX AssocResp from 00:8b:5d:b9:29:ca (capab=0x431 status=0 aid=7)
[  323.863092] wlan0: associated
[  368.841036] wlan0: deauthenticating from 00:8b:5d:b9:29:ca by local choice (reason=3)
[  372.748604] wlan0: authenticate with 00:8b:5d:b9:29:ca
[  372.764285] wlan0: send auth to 00:8b:5d:b9:29:ca (try 1/3)
[  372.766104] wlan0: authenticated
[  372.779841] wlan0: associate with 00:8b:5d:b9:29:ca (try 1/3)
[  372.782464] wlan0: RX AssocResp from 00:8b:5d:b9:29:ca (capab=0x431 status=0 aid=7)
[  372.782857] wlan0: associated
[  417.756614] wlan0: deauthenticating from 00:8b:5d:b9:29:ca by local choice (reason=3)
[  718.198965] wlan0: authenticate with 00:8b:5d:b9:29:ca
[  718.214840] wlan0: send auth to 00:8b:5d:b9:29:ca (try 1/3)
[  718.216686] wlan0: authenticated
[  718.230469] wlan0: associate with 00:8b:5d:b9:29:ca (try 1/3)
[  718.232985] wlan0: RX AssocResp from 00:8b:5d:b9:29:ca (capab=0x431 status=0 aid=7)
[  718.233319] wlan0: associated

---

### Post by TehRainbowGuy on 2012-12-26
Update...

Tested wicd, seems to get stuck at obtaining IP address.

Edit**

Installed driver from ralink, no luck.

---

### Post by TehRainbowGuy on 2012-12-26
Yet another update, it seems to work fine with static addressing. Dhcp will not work on any of the aps that I have tested.

---

