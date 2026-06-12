---
title: "DHClient"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by Theredbaron1834 on 2011-07-11
I have been trying to connect to a wpa access point on my ibook g3, with the latest ubuntu, however, I keep failing. I can connect to the access point, but dhclient won't give me a ip lease. I also tried dhcpcd.

On dhclient I get  network is down error and  get no dhcpoffers. I am connected via wpa_supplicant on another term. Everything is good, till I start dhclient. Then I get errors on both, saying network is down. And after dhclient exits, I have to restart wpa_supplicant, as it never connects again till I do.

This is my first go at term network connecting, but I have had no luck with any gui connecting, so I thought I would try this. However, like I said, I have never done this before, so I have no idea what to do to try and fix this. Any idea's would be great.


EDIT
Well, I found out what was wrong. Seems that wpa_supplement doesn't do "wpa-psk tkip and wpa2-psk aes" Changed my router to just wpa-psk and all was good. :) Thanks for the help.

---

