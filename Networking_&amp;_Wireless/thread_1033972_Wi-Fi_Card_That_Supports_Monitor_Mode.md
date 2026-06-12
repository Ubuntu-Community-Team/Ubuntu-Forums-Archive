---
title: "Wi-Fi Card That Supports Monitor Mode?"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by Fireblazer on 2009-01-07
Hey,

I've been reading a little about Wi-Fi security and I would like to play with some tools like Wireshark, Kismet, Aircrack, etc. but it looks like they all require "Monitor Mode". I'm currently using Ndiswrapper for my Trendnet TEW-423PI Marvell Chipset, so I guess I need a new card. I need something that:

1. Is cheap, I'm only 13 and don't have a huge allowence
2. Works on a desktop
3. Supports all the tools listed above

What should I look for?

~ Fireblazer

---

### Post by damis648 on 2009-01-07
You may not need a new one. Can you try disassociating from you access point and issuing the following:
```
sudo iwconfig wlan0 mode monitor
```
and see if that works (replace wlan0 with your device). It might just respond with an error. To revert,
```
sudo iwconfig wlan0 mode managed
```

---

### Post by Fireblazer on 2009-01-07
Hey,

Thanks but I tried that, didn't work. After some reading I found that Ndiswrapper doesn't support monitor mode and there's no Linux driver for the Marvell chipset.

~ Fireblazer

---

