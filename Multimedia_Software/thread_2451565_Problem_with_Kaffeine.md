---
title: "Problem with Kaffeine"
date: 2020-10-06
forum: Multimedia Software
---

### Post by nighthawk772 on 2020-10-06
I have a tbs5927 dvb-s2 usb tuner and I've been strugling to get it to work on linux based system. Have no problems on windows whatsoever, but since I'm transitioning to linux my lack of linux skills emerges...
I've installed Kaffeine but cannot scan for channels at all. When I run it from terminal I see a warning message Unsupported transmission type: 4. I've looked around but don't know what that means. When I start channel scan this is what I see in log:

06-10-20 22:20:24.712 [Warning ] QCommandLineParser: already having an option named "h"
06-10-20 22:20:24.712 [Warning ] QCommandLineParser: already having an option named "help-all"
06-10-20 22:20:24.712 [Warning ] QCommandLineParser: already having an option named "v"
06-10-20 22:20:24.973 [Info    ] kaffeine.dvb: Using built-in dvb device manager
06-10-20 22:20:25.250 [Warning ] kaffeine.dev: Unsupported transmission type: 4
06-10-20 22:20:25.267 [Info    ] kaffeine.dev: Found dvb device : TurboSight TBS 5927 DVB-S/S2
06-10-20 22:20:39.816 [Warning ] kaffeine.dvb: Timeout while reading section; type = 0, PID = 0
06-10-20 22:20:39.817 [Warning ] kaffeine.dvb: Timeout while reading section; type = 2, PID = 17

Any help would be appreciated!

---

### Post by tea for one on 2020-10-06
TBS have user guides and links to Linux drivers on their web pages.

[https://www.tbsdtv.com/products/tbs5927-dvb-s2-tv-tuner-usb.html](https://www.tbsdtv.com/products/tbs5927-dvb-s2-tv-tuner-usb.html)

I don't use that particular device so I can only offer the above web page to help you get started.

---

### Post by nighthawk772 on 2020-10-08
After some research I still wasn't able to figure out why I'm seeing  "Unsupported transmission type: 4" in Kaffeine log, but amazingly scan  works after I switthed to another usb port and problem solved. All ports  seems to work fine as I tried several sticks and it's ok.

---

### Post by tea for one on 2020-10-09
> **nighthawk772 said:**
> After some research I still wasn't able to figure out why I'm seeing  "Unsupported transmission type: 4" in Kaffeine log, but amazingly scan  works after I switthed to another usb port and problem solved. All ports  seems to work fine as I tried several sticks and it's ok.

Pleased to read that the problem is solved.

---

