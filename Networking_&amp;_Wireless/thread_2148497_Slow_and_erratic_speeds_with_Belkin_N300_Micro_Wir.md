---
title: "Slow and erratic speeds with Belkin N300 Micro Wireless Adapter"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by MindZEye on 2013-05-25
I've just bought this device and while it has worked first time with no special effort required (Ubuntu 13.04), the speeds I'm seeing from it are a full magnitude slower than I'm seeing with other devices. For example using this speed test I get the following result:
```

wget -O/dev/null speedtest.pixelwolf.ch
--2013-05-25 17:41:17--  http://speedtest.pixelwolf.ch/
Resolving speedtest.pixelwolf.ch (speedtest.pixelwolf.ch)... 178.63.18.88, 2a02:41a:3204::134
Connecting to speedtest.pixelwolf.ch (speedtest.pixelwolf.ch)|178.63.18.88|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://speedtest.pixelwolf.ch/one.gigabyte [following]
--2013-05-25 17:41:17--  http://speedtest.pixelwolf.ch/one.gigabyte
Reusing existing connection to speedtest.pixelwolf.ch:80.
HTTP request sent, awaiting response... 200 OK
Length: 1048576000 (1000M) [text/plain]
Saving to: ‘/dev/null’

 0% [                                                                ] 6,900,746    439KB/s  eta 55m 19s

```

That speed of 439KB/s doesn't really compare to the 3.77M/s I see for the same request from another machine in the same room. On top of this that speed varies downwards by almost 50%, so it's not even very stable at that speed either. I've experimented with iwconfig even pretty much to the point of just changing things to random values, but nothing seems to make much difference.

Here's the output of iwconfig:
```

wlan1     IEEE 802.11bgn  ESSID:"XXXX"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

```

Also the pertinent line from lsusb to show the chipset it's using:
```

Bus 002 Device 006: ID 050d:2103 Belkin Components F7D2102 802.11n N300 Micro Wireless Adapter v3000 [Realtek RTL8192CU]

```

Does anyone have any suggestions for possible fixes or is anyone else even seeing this issue?

---

### Post by MindZEye on 2013-05-25
Interestingly hitting the speedtest download seems to cause the link quality and the signal level reported by iwconfig to plummet, which seems to indicate something a bit wonky is happening.

---

### Post by MindZEye on 2013-05-25
Now it appears switching the bandwidth option on my router from 20/40 to just plain 20 has caused a dramatic improvement. It's still really up and down and rarely gets near the speed my other laptop reaches however.

---

### Post by praseodym on 2013-05-25
Try to update the driver according to this:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

---

