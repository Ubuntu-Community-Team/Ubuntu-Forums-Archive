---
title: "Unable to Connect Wirelessly with Supported Card"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by scottmc9 on 2009-09-13
Recently installed XUbuntu 9.04 with a supported an known good wireless card (Netgear RangeMax Wireless PC Card WPN511). I cannot get wireless connectivity working. When I manually set up the WEP environment for the first time, I misspelled the name of the SSID.
I edited the properties of the wireless connections using the Netwroking applet at the top of the GUI interface, deleted the misspelled wireless connection and added/configured the correct connection information. It still cannot connect. As it is trying to connect, I view the connection attempt and it shows both the new and the old misspelled connections and it is still trying to connect using the old misspelled connection. Even when I manually select the radio button for the correct connection and again provide all the WEP info, it won't connect.
What do I need to do to connect?
Warning: Linux is not my native tongue. I know just enough to be dangerous. :)

---

### Post by atomizer on 2009-09-13
maybe you can set the correct essid with the command **iwconfig**.

you have to do in a terminal
```
sudo iwconfig *yourinterface* essid *"yournetworkname"*
```


for example:
```
sudo iwconfig wlan0 essid "homenetwork"
``` would set the essid "homenetwork" for the wireless adapter wlan0.

```
sudo iwconfig wlan0 essid any
``` would connect to any router in the neighbourhood.

see [man iwconfig]("http://linux.die.net/man/8/iwconfig") for more about iwconfig (you can type man iwconfig in the terminal also for the same information)

---

