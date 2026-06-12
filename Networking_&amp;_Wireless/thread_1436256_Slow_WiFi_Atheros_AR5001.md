---
title: "Slow WiFi: Atheros AR5001"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by leoh on 2010-03-22
I have Ubuntu 9.10, and a few weeks ago the WiFi seems to be really, really slow.
However, this only happens at home (I tried at some other place and it works fine). It is not a hardware issue nor a router issue since it works fine on the same computer from Windows.

This is the WLAN:
```
08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

This is the "ping google.com" result from WiFi:

```
--- www.l.google.com ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 36215ms
rtt min/avg/max/mdev = 219.445/1829.849/7954.364/1980.087 ms, pipe 4
```

And the same, from Ethernet:
```
14 packets transmitted, 14 received, 0% packet loss, time 13016ms
rtt min/avg/max/mdev = 221.967/296.529/1225.903/257.769 ms, pipe 2
```

So, is there anything I can tweak or change?
This computer used to work fine until 2 or 3 weeks ago, so it must be something with an update.

---

### Post by leoh on 2010-03-22
I already replaced the router (both the old and new one are WRT54G with DD-WRT, last version). Same thing.

Anybody? Any hint at least?

---

### Post by kellenfreeman15 on 2010-03-24
I have the same exact problem! except it's with ubuntu 10.04...:(
I've tried several things but I can't figure it out...
If you make any progress please tell me!

---

### Post by kellenfreeman15 on 2010-03-24
I have the same exact problem and with the same wifi transmitter!

---

### Post by leoh on 2010-03-25
Ok problem solved...
Turns out that a neighbor had recently installed a router. It seems it was on the same frequency channel. I changed the frequency and now it works fine.

---

