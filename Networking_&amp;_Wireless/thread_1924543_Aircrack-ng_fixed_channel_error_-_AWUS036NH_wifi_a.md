---
title: "Aircrack-ng fixed channel error - AWUS036NH wifi adapter - Ubuntu 11.10"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by jed823 on 2012-02-12
Hello,

I am have been trying to get my AWUS036NH adapter to work correctly using aircrack-ng.

I get to the part where I run:
aireplay-ng -0 1 -a BSSID -c STATIONMAC mon0

At this point I get:

Waiting for beacon frame(BSSID: MAC) on channel -1
mon0 is on channel -1, but the AP uses channel 6.

When I started mon0 I ran:
airmon-ng start wlan1 6 (AP is on channel 6), but still get this issue.

I read through aircrack-ng's coverage of this issue, and found two possible solutions via patch.

V1:  [http://marc.info/?l=linux-wireless&m=127476407611861&w=4](http://marc.info/?l=linux-wireless&m=127476407611861&w=4) 

V2:  [http://marc.info/?l=linux-wireless&m=127541691302338&w=4](http://marc.info/?l=linux-wireless&m=127541691302338&w=4) 

Now my only question is what do I do with the script to perform the patch?

Any help is much appreciated.

---

