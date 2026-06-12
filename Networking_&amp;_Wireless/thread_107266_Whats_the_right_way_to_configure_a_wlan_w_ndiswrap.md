---
title: "Whats the right way to configure a wlan w/ ndiswrapper?"
date: 2005-12-22
forum: Networking &amp; Wireless
---

### Post by Mergulhao on 2005-12-22
I instaled ndiswrapper and the windows driver for the wlan card. I wrote an shell script to wakeup my card:

```
#!/bin/bash
/sbin/modprobe -r ndiswrapper
sleep 1
/sbin/modprobe ndiswrapper
sleep 2
/sbin/iwlist wlan0 scan
/sbin/iwconfig wlan0 essid "MY_WIFI_ESSID"
sleep 1
dhclient wlan0
```

This works fine, but i dont think its the more inteligent way to do this. I'm newbie in debian/kubuntu and I dont know how to configure /etc/network or something else.

---

### Post by towsonu2003 on 2005-12-24
I use the same stuff when I need my wireless up. People say: don't fix what ain't broken ;) It's fine as long as it works :) But you could also try inserting ndiswrapper for good (ndiswrapper -m, see man ndiswrapper) and try using the Networking tool (System>Administration>Networking then enable and configure your connection from there). But again, dont fix what aint broken :cool:

---

