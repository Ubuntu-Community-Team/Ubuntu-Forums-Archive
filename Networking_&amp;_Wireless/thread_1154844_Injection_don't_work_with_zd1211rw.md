---
title: "Injection don't work with zd1211rw"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by mendez on 2009-05-10
Hi

I would try to use aircrack-ng (1.0rc3) on my own wireless testing network.

I own a ZyXel G-202 usb stick with zd1211rw chipset on Ubuntu 8.10.


Monitor mode is working properly
```

# airmon-ng start wlan0 6
Interface       Chipset         Driver

eth1            Unknown                 wl
wlan0           ZyDAS 1211      zd1211rw - [phy0]
                                (monitor mode enabled on mon2)
mon0            ZyDAS 1211      zd1211rw - [phy0]

```

but the injection no...
```

# aireplay-ng --test mon0
13:17:39  Trying broadcast probe requests...
13:17:40  No Answer...
13:17:40  Found 1 AP

13:17:40  Trying directed probe requests...
13:17:40  00:02:CF:9D:ED:E7 - channel: 6 - 'WiFi-Test'
13:17:47   0/30:   0%

```

I have this different istruction to make running injection

[http://forum.aircrack-ng.org/index.php?topic=4134.msg23702#msg23702]("http://forum.aircrack-ng.org/index.php?topic=4134.msg23702#msg23702")

[http://forum.aircrack-ng.org/index.php?PHPSESSID=6324ac98f39cdb1d39418b4da2b98448&topic=4805.0]("http://forum.aircrack-ng.org/index.php?PHPSESSID=6324ac98f39cdb1d39418b4da2b98448&topic=4805.0")

but still don't work .-(


I have try BackTrac 4beta and monitor + injection work automagically!:-x

I am going to become crazy and I will not give peace until it works!:)

Please someone help me!

---

### Post by happy123world on 2009-05-23
try this tutorial, it should work:

[http://forum.aircrack-ng.org/index.php?topic=5334.msg28996#msg28996](http://forum.aircrack-ng.org/index.php?topic=5334.msg28996#msg28996)

I am getting the same dongle in a few days. Please tell me if it works or not.

---

### Post by mendez on 2009-05-23
> **happy123world said:**
> try this tutorial, it should work:

[http://forum.aircrack-ng.org/index.php?topic=5334.msg28996#msg28996](http://forum.aircrack-ng.org/index.php?topic=5334.msg28996#msg28996)

I am getting the same dongle in a few days. Please tell me if it works or not.

tomorrow i try this solution and I'll tell you if this time it worked ...

---

### Post by happy123world on 2009-05-24
What do you think of this card? how about its signal strength? unfortunately, the fragmentation attack will not be supported in the near future.

---

### Post by mendez on 2009-05-24
i have tryed and now the injection work...

i have problem with lose of association with ap, on closest distance (my ap)...

is not bad this card... i have a ZyXel G-202

---

