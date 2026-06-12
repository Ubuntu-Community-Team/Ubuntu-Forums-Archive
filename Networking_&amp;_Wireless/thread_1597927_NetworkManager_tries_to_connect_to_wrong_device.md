---
title: "NetworkManager tries to connect to wrong device"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by fabiobh0 on 2010-10-15
I have a ZTE 3G USB modem (MF645).
When I plug it, 5 devices appear: /dev/ttyUSB[0-4]. The modem device is /dev/ttyUSB2, and I can successfully connect wvdial on it.
NetworkManager detects the modem, however, it tries to connect to /dev/ttyUSB1 instead, and fails.

How does NM decides which device to connect to?
Is it possible to instruct it to connect to a specific device?

---

### Post by inobe on 2010-10-15
i haven't used gnome in a wile but i remember in network settings i had a choice for preferred device, that was karmic, i don't know if its the same.

other than that you can simply unplug a cable so it won't obtain an ip from the other device till it's sorted.

---

