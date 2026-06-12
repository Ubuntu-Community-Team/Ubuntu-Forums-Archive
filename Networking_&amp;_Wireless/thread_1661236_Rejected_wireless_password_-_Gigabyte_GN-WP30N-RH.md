---
title: "Rejected wireless password - Gigabyte GN-WP30N-RH"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Artisten on 2011-01-06
Hi!

My new network card can't for some reason connect to the wireless router at my lodgings. It's a [[COLOR="Blue"]GN-WP30N-RH[/COLOR]]("http://www.wireless-driver.com/gigabyte-gn-wp30n-adapter-drivers-utility/") I bought just today. It connects flawlessly on my win7 partition, but apparently the same password is rejected in Ubuntu. The wireless network is visible from the list of available networks, but when trying to connect it asks for the "WPA & WPA2 Personal" password, I type in the same password that I used in windoze, but it rejects it and asks again.. ??

Here is the output from lspci:
```
05:00.0 Network controller: RaLink RT2860 Wireless 802.11n PCIe
```

And iwconfig:
```
wlan0     IEEE 802.11bgn  ESSID:"privat0572ham"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

uname -mr:
```
2.6.35-24-generic x86_64
```
(it's Ubuntu 10.10 64-bit)

Please help me :D

---

