---
title: "Ralink 802.11 n WLAN usb"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by cornflayke on 2010-12-27
Hello, 

I bought an USB-WLAN stick, which does not recognize any network.

A Ralink 802.11 **bg** WLAN Stick works fine, but
the Ralink 802.11 **n** WLAN Stick does not work unfortunately.

Both get recognized by the nm-applet of network manager
but only the first one recognizes my network and is able to connect to it.

My kernel version is:
Linux Vostro1500 2.6.32-27-generic[FONT=monospace]

[/FONT]```

$ lsusb | grep Ralink
Bus 002 Device 006: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

``````

$ lsmod | grep rt
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2870sta             461811  0 
rt2800usb              31531  0 
rt2x00usb               9703  3 rt73usb,rt2500usb,rt2800usb
rt2x00lib              27509  4 rt73usb,rt2500usb,rt2800usb,rt2x00usb
mac80211              205402  2 rt2x00usb,rt2x00lib
led_class               2864  2 rt2x00lib,sdhci
cfg80211              126528  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
agpgart                31724  2 nvidia,intel_agp
parport                32635  2 ppdev,lp

```Thank you very much in advance.

besten regards
cornflayke

---

### Post by cornflayke on 2010-12-28
Hey, 

after having followed every tiny instruction under:
[http://ubuntuforums.org/showthread.php?t=960642](http://ubuntuforums.org/showthread.php?t=960642)

I managed that, both cards recognize my wireless lan
but STILL only the Ralink 802.11 **bg** WLAN Stick is able to connect to this wlan.

My modules now look like:
$ lsmod | grep rt
```

rt2870sta             461811  1 
agpgart                31724  2 nvidia,intel_agp
parport                32635  2 ppdev,lp

```

lsusb has not changed.

Any suggestions?

---

### Post by cornflayke on 2011-01-03
Hey, my problem finally got solved.

For any searcher I may refer to:
[http://ubuntuforums.org/showthread.php?t=960642&page=24](http://ubuntuforums.org/showthread.php?t=960642&page=24)

Best regards
- cornflayke

---

