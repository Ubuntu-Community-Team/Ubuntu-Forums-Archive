---
title: "Tried patching a driver and now hardware is unclaimed"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by andru183 on 2012-04-28
I followed ([http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless)) this guide to patch my wireless card. All was going fine till I got to

```
$ sudo make wlunload
```After that my wireless driver got unloaded and then I tried the next line with ath9k instead of driver name. Now my wireless card is now listed under ifconfig or iwconfig and if I check lshw -C Network, it finds the device but says it's unclaimed.

I have no idea how to bring it back from here or why modprobe will not work. Any one got any tips or help? Thanks

---

