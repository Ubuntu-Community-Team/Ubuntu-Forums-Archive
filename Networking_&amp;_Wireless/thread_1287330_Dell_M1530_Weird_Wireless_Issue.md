---
title: "Dell M1530 Weird Wireless Issue"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by warfy on 2009-10-10
Hello Ubuntu Community! I have an XPS M1530 laptop, and its having issues with connecting to wireless networks. The Broadcom STA driver is enabled, and when I put 
```
iwlist eth1 scan
``` 
it returns various local AP's, including my router, but the networking manager doesn't see any of them. Ive tried using the terminal to connect, with 
```
iwconfig eth1 essid "my network"
``` or ```
iwconfig eth1 ap any 
```
Neither of which seem to have any effect whatsoever.

For whatever reason, my wireless card is eth1 instead of wlan0. Any help would be sincerly appreciated.

Thanks, Tom

---

