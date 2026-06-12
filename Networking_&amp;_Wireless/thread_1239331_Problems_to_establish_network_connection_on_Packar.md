---
title: "Problems to establish network connection on Packard Bell dot s netbook"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by eekie on 2009-08-13
The netbook is provided with  Atheros AR5B95 chip for wireless and Atheros Ar8132 chip for wired connection. Jaunty does not have the drivers but I downloaded the Mad wifi driver and the AR8132 driver and transferred these to my Jaunty home partition.
When I give the command make the mad wifi starts to install but then I get the following errors:
make[3]: *** [home/johan/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[3]: *** [home/johan/madwifi-0.9.4/net80211] Error 2
make[1]: *** [module_/home/johan/madwifi-0.9.4] Error 2
make: *** [modules] Error 2

The wired driver is zipped and does not even unzip properly. The archive manager states:

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors

Manual decompression of the tar.gz file does not work either

I hope there is no need for installing all kind of additional software for which I need internet connection, because that would mean the Baron of Munchhausen effect prevails again. ( pulls himself out of a swamp by his own hair )

---

