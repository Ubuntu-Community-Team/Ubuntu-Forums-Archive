---
title: "Ralink/Ubuntu 10.04 64 bit/HP a6700f"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by roosh on 2010-06-23
I've been having trouble getting my ralink wireless adapter working for awhile now. It works fine when I boot to windows, and it seems that Vista uses a netr_7364 (which I think is the 64 bit version of netr_73) driver for it. Ubuntu uses the rt73usb driver, but I can never connect to any networks. I tried to use ndiswrapper with the netr_7364 driver, but I couldn't get it to work.

I can connect with a different USB adapter that I have tried; that's how I'm posting now.

The wireless adapter is integrated, but I have reason to believe that it connect via USB; Vista calls it something like Ralink 802.11 bg USB. 

lsusb:
```
Bus 002 Device 004: ID 0846:4110 NetGear, Inc. MA111(v1) 802.11b Wireless [Intersil Prism 3.0]
Bus 002 Device 003: ID 0d8c:0103 C-Media Electronics, Inc. Turtle Beach Audio Advantage Micro
Bus 002 Device 002: ID 050d:0002 Belkin Components 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 18e3:9102 Fitipower Integrated Technology Inc Multi car reader
Bus 001 Device 004: ID 15a9:0004  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I cannot find anything here relating to the adapter in question. The NetGear adapter is the one that already works, but I want to get my ralink one working.

Any help would greatly be appreciated.

---

