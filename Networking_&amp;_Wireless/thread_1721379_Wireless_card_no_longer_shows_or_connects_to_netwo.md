---
title: "Wireless card no longer shows or connects to network"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by Linkmaster. on 2011-04-04
I have Ubuntu netbook edition 10.10 installed on my friends box, and I have -buntu experience, but mainly with Kubuntu. I have tried several things to attempt to get the wireless card to recognize the network, which is hidden. I have the SSID of the network, and it has no password. First I attempted to simple connect with the default 'connect to hidden wireless network'. This didn't work, so I deleted the files for my network, and tried again. This did not work either. I then opened up a Terminal and tried the following:
```
sudo iwlist wlan0 scan essid "wireless name"
```
And this resulted in
```
wlan0: no scan results
```
So this is baffling me of course, since I've never had a problem with that code unless the wireless card is not supported. I thought it was, since it was working previously. I then tried an *iwconfig* to attempt and see what was wrong with the card, and this is the results:
```

IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
```

And I'm not sure what to do past this point. If any addition information is needed, please ask.

---

### Post by Linkmaster. on 2011-04-04
Attempting this is very difficult, and my friend needs his computer as soon as humanly possible. Its needed for school[printing, looking up information, etc.]

---

