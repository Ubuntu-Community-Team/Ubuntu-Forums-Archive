---
title: "aircrack problems"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by acnyc2000 on 2008-12-12
hello all,
i have an acer aspire 4530 and i have my wireless card working properly (i hope, i can see different wireless connections) but when i am trying to search for open network with 
sudo -airodump ath1 (ath1 as being set as monitor) 

nothing shows up and its been 10 mins.

maybe i am missing some steps? with a fresh started ubuntu here is what i did

sudo iwconfig 

lo     no wireless extensions
eth0   no wireless extensions
wifi0  no wireless extensions
ath0   IEE 802.11g ESSID: "" Nickname:""
       Mode:Managed Frequency:2.437 GHz Access point: Not-ASsociated ..... (a few lines donno if they are important)

pan0   No wireless extensions.

then i would put wifi0 on monitor mode as
sudo airmon-ng start wifi0 

Interface    Chipset     Driver
Wifi0        Atheros     Madwifi-ng
ath0         Atheros     Madwifi-ng VAP (parent: wifi0)
ath1         Atheros     Madwifi-ng VAP (parent: Wifi0)(monitor mode enabled)

then i would airodump it...
sudo airodump-ng ath1 (is this the right one?)

i can see channel hopping, but there is nothing on my bssid or anything

and if i use airodump-ng wifi0 the sheet would go blank

any ideas?

aircrack forum is down for the moment :(

---

