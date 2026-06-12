---
title: "Madwifi (Atheros) + NetworkManager: Working yet?"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by dyssident on 2006-06-12
from reading forums and mailing lists i can see that people have long had problems with the madwifi + NetworkManager combination. does anyone know for sure if this combination is supposed to be working yet?

For the record:

i am trying to establish an ad-hoc connection between a Toshiba M55-S1001 laptop with an Atheros card and and a dlink usb wifi card. im not entirely sure which exact model the Atheros card is because lspci returns "Unknown Device".

with the current Dapper madwifi package (linux-restricted-modules) i can establish a connection via iwconfig with `iwconfig ath0 essid "essid"; iwconfig ath0 mode Ad-Hoc; iwconfig ath0 key open`.

when i install network-manager and network-manager-gnome via apt-get it appears to run ok, but i cant establish a connection through it. ive done all the recomended steps 
([like so]("http://www.ubuntuforums.org/showpost.php?p=843432&postcount=30")) with no luck.

i began to think that the Dapper madwifi code, since it uses madwifi-old branch, just wouldnt work with NetworkManager. so ive tried compiling madiwifi-ng from source with [this process]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo"), but i cant establish an ad-hoc connnection via iwconfig, so theres no real point in trying NetworkManager.

---

### Post by dyssident on 2006-06-26
to wrap up this thread: i gave up on the whole ad-hoc idea in favor of a $20 (after rebate) access point from newegg; no brainer. whatever the current NetworkManager and madwifi wares are in Dapper, they work great for connecting to access points and wired.

---

