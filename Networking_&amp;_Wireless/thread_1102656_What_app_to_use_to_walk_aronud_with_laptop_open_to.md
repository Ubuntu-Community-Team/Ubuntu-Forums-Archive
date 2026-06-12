---
title: "What app to use to walk aronud with laptop open to check wifi signal strength?"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by andresmh on 2009-03-21
I'm stuck at the airport and I want to find the best place to sit down that is also close to power outlet. I tried wifi-radar, gnome network applet and they don't seem to update very fast. I also tried SWScanner but it fails to open wlan0 even when running as root. Are there any CLI options or other apps? 

```
iwlist wlan0 scanning
``` only shows the signal strength of the network I am already connected to. I want to see all the available networks.

---

### Post by 03taxi on 2009-03-21
[http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html](http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html)

---

### Post by kevdog on 2009-03-21
sudo iwlist scan (refreshes cache)

or just put into monitor mode and use something like kismet!

---

