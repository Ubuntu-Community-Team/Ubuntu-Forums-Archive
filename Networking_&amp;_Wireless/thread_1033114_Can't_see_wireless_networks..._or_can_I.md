---
title: "Can't see wireless networks... or can I?"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by antonym on 2009-01-07
I've been having some problems with the wireless card on my laptop, an Acer Aspire One. After finally getting it working at one point, using madwifi drivers, I performed some of the customizations on the Ubuntu Community sites **[here]("https://help.ubuntu.com/community/AspireOne")** and **[here]("https://help.ubuntu.com/community/AspireOne110L")**... and it broke and I haven't been able to fix it again.

The weird thing, though, is that while my network manager (wicd) says "no wireless networks found", I followed some terminal instructions (below) found on the madwifi wiki, and found that the card could see nearby wireless networks.

executing these gives me a list of the nearby networks:
```
sudo ifconfig ath0 up
sudo modprobe wlan_scan_sta
sudo wlanconfig ath0 list scan
```


Now, why can't wicd see these too??

---

