---
title: "Connecting to ARRIS Router (WPA/WPA2-TKIP-AES)"
date: 2012-03-29
forum: Networking &amp; Wireless
---

### Post by consequent on 2012-03-29
I am attempting to connect my Debian Squeeze system to a wireless router provided by Comcast Xfinity. I called their "support service", however, they refused to speak to me when they discovered I was using Linux. My wireless drivers are properly installed and I have no trouble connecting to any other wireless networks. I am a competent programmer but have no experience manually configuring wireless networks. So please speak to me as if I were a small child.

* Router manufactured by ARRIS Group Inc.
    * Model:  TG862G/CT
    * P/N:  TG02DH7862CT
* Encryption Type:  WPA/WPA2-TKIP-AES
* Additional information available:
    * Network Name(SSID)
    * Network Key
    * WPS PIN
    * CM MAC, E-MTA MAC, WAN MAC
    * Network name/password pair used by my roommates to connect using Windows

The SSID is not broadcasted publicly. I am trying to use the "Connect to Hidden Wireless" option with NetworkManager Applet 0.8.1.

Any assistance with this matter will be greatly appreciated and payed forward at some point.

---

### Post by wildmanne39 on 2012-03-29
Hi, first unhide your network it is much harder for linux to connect to a hidden network and there it is really no more secure then a broadcasting network.

Also in your router set your encryption to just wpa2 if possible it will make it easier to connect too.

If it still does not connect please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

``` 
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

