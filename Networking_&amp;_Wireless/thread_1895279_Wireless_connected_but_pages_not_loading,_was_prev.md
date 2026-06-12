---
title: "Wireless connected but pages not loading, was previously working"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by platypus42 on 2011-12-14
Hi,

I installed compat-wireless yesterday, according to the instructions here: [http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless)
After the 'sudo make unload' step, I tried 'sudo modprobe iwlagn', which I thought was the driver for my Intel WiFi Link 5100. There was an "Error inserting iwlagn", and I wasn't sure what driver I'm supposed to give, so I simply rebooted the system (I now think it should have been iwlwifi).

Since then, I haven't been able to access the Internet from my system. Ubuntu connects fine to the network, shows the "Connection established" message, but actually trying to load the pages or even pinging fails.

**But**, if I enable the monitor interface mon0 through airmon-ng, I'm able to monitor my own and the neighbouring networks without any problems. So, my WiFi card and driver seem to be working fine, but there's a problem with Internet connectivity alone. I'm able to connect to the Internet through the same router from other devices, no issues there.

I've gone through many threads on these and other forums, but nothing has helped so far. I've attached some possibly relevant outputs here, kindly tell me if there is some other command to try as well.

*ifconfig* and *iwconfig* output: [http://pastebin.com/KfjbzZ9A](http://pastebin.com/KfjbzZ9A)

*lshw* output: [http://pastebin.com/UJppqinC](http://pastebin.com/UJppqinC)

*route* *-n* and *ping*: [http://pastebin.com/0E8R0wdv](http://pastebin.com/0E8R0wdv)

---

