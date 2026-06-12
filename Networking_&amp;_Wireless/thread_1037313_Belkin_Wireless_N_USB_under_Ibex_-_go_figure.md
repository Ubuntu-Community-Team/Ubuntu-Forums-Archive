---
title: "Belkin Wireless N USB under Ibex - go figure"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by wjcunning on 2009-01-11
Truth is stranger than fiction - Bought a Belkin Wireless N USB FSD 8953 N device. After tooling through every google fix I could find, and every Ubuntu thread on the Belkin N USB device....and 3 days of effort, it still doesn't work under Ibex. Did the ndiswrapper thing...Got as far as lsusb yielding "Bus 006 Device 003: ID 050d:8053 Belkin Components" and System/Administration/Windows Wireless Drivers notes the rt2870 device present....but it fails to show up as a device in Network Tools.

Soooo....I installed Sun xVM Virtualbox and loaded XP and loaded the Belkin boxed software and whoa...the virtual XP side sees and can connect to my N wireless router using the Belkin Wireless N USB device.

OK, so why can Ibex not use the USB device, but the virtualboxXP not only see it but connect over it on the first try?

---

