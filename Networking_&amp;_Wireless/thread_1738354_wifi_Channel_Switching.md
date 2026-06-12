---
title: "wifi Channel Switching"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by getafix28 on 2011-04-24
I try to run the command  aireplay-ng and get the next error:

    18:11:33  Waiting for beacon frame (BSSID: 00:21:63:9C:61:E3) on channel -1
    18:11:33  mon0 is on channel -1, but the AP uses channel 6

how can i Change the channel?

Thanks to all helpers

---

### Post by uncaspi on 2011-04-24
Open a terminal and type sudo iwconfig wlan0 channel 6
I assume your card is named wlan0.Perhaps its mon0

---

