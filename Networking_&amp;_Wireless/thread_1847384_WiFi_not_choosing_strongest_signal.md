---
title: "WiFi not choosing strongest signal"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by icevalley20 on 2011-09-20
I have a laptop here with a RALink rt2573 WiFi card installed.  Everything works fine with Ubuntu 11 right out of the box and the connection is strong.

The problem occurs when I move from floor to floor in my building.  I have three WiFi routers set up, all with the same security details and name but on different channels.

This setup works perfectly for Windows systems, when I move floor it picks up the stronger signal from that floors access point and seamlessly connects.

Ubuntu for some reason refuses to see the stronger signal.  It keeps trying to connect to the by now very weak signal from the floor below.  Even if I turn the laptop off and back on again it still trys to pick up the wrong access point.

Even stranger, if I leave the laptop off all night and then turn on in the morning, it correctly picks up the strongest signal.

Anyone any ideas what is happening?

---

### Post by praseodym on 2011-09-20
Hello,

please show the output of:

```
sudo iwlist scan
```

You can add the Hardware address of each network with the same [COLOR="Red"]E[/COLOR]SSID and key in a single connection in the networkmanager in the field [COLOR="Red"]B[/COLOR]SSID

---

