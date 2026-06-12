---
title: "Wireless causes multicolored screen crash."
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by emnaki on 2009-10-18
Hello, I have installed ubuntu karmic UNR beta on my Sony Vaio P23G netbook. When I use wireless the system crashes. Here is what is shown before multicolored screen crash occurs: (last entries in the system and daemon log)
```

Oct 18 16:54:35 janice-laptop wpa_supplicant[942]: CTRL-EVENT-SCAN-RESULTS 
Oct 18 16:54:35 janice-laptop wpa_supplicant[942]: Trying to associate with 00:18:6e:31:56:42 (SSID='CC WLAN' freq=2412 MHz)
Oct 18 16:54:35 janice-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associating
Oct 18 16:54:35 janice-laptop wpa_supplicant[942]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct 18 16:54:35 janice-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Oct 18 16:54:36 janice-laptop wpa_supplicant[942]: Associated with 00:18:6e:31:56:42
Oct 18 16:54:36 janice-laptop wpa_supplicant[942]: CTRL-EVENT-CONNECTED - Connection to 00:18:6e:31:56:42 completed (reauth) [id=0 id_str=]
Oct 18 16:54:36 janice-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated
Oct 18 16:54:36 janice-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
**Oct 18 16:54:41 janice-laptop NetworkManager: <debug> [1255856081.003588] periodic_update(): Roamed from BSSID 00:18:6E:31:57:42 (CC WLAN) to 00:18:6E:31:56:42 (CC WLAN)**
```

The last line does not cause crash all the time, but still very often, like every 5-10 minutes. This is not a Karmic specific issue since I happens on Jaunty UNR as well. Although I have not found a fix for my particular system, from what I've read on the web, I gathered that the general approach is to either replace Network Manager or replace the driver (ath9k) with ndiswrapper (assuming it works). But before I try one of these approaches, I though I'd consult with the network knowledgeables of Ubuntu to see if there is a better way of solving this issue. Thanks in advance!

ps. it seems odd that a wireless problem will cause the whole system to crash, I'd have expected the worse that would happen would be a disconnect from the internet.

---

