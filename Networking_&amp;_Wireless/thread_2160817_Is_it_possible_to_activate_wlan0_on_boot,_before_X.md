---
title: "Is it possible to activate wlan0 on boot, before X11 loads?"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by sdgiffin on 2013-07-08
On my laptop, I have in /etc/rc0.d/ a little script (K06networking) that - in theory - load wlan0 and connect it before everything else loads, but it's not working.

The initial networking loader (K05networking) loads fine, but unless the laptop is connected to the LAN via CAT5, it adds 120 seconds to the boot time and I have to wait even longer while X11 authenticates the WIFI after a user logs in.

```
#!/bin/sh -e
ifconfig wlan0
iwconfig wlan0 essid (LAN_ESSID) key (WPA-KEY)
dhclient wlan0

```

What am I doing wrong?

Using Ringtail, 32-bit on a Toshiba Satellite A100. My goal was to have the WIFI connected before the user logs in so it's ready to go, just like it is when it's connected via CAT5.

---

### Post by steeldriver on 2013-07-08
Isn't /etc/network/interfaces the right place for this, rather than a separate init script? or am I missing something? 

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid *LAN_ESSID*
    wpa-psk *WPA_KEY*

```

Aside from that, I don't think 'ifconfig' on its own actually brings up the interface (that would be ifconfig wlan0 **up**) and also iirc 'iwconfig wlan0 *ssid *key *xxx*' maybe only works for WEP, not WPA?

---

