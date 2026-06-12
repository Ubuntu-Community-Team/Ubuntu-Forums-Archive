---
title: "Intel 82576 constant flow issue"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by ubxyz on 2011-11-01
Hello,

I have just bought an Intel Gigabit ET2 Quad Port Svr adapter (known as Intel 82576(GB)).

In order to get the best out of my card, i've compiled and inserted the last version of the igb module provided by intel (igb-3.2.10) on ubuntu 10.04 LTS. Because the original module in ubuntu 10.04 (version 2.1.0-k2) does not recognized the card and therefore not all options are available !

Compilation and insertion of the module were done without any problem.
The different options for this card are recognized by the module (igb-3.2.10) which shows, opposed to the built-in module version (2.1.0-k2), that the card is correctly recognized.

My problem is the following:
When sending a constant flow using tcpreplay for example the card is not sending a constant flow but short burst of packets every half a second as if the card is not able to threat a constant flow. Problem has been identified by watching the output of /proc/net/dev.

I have to precise that I have tested the last driver version (igb-3.2.10) on ubuntu 11.10 too and that the result were the same as for ubuntu 10.04 LTS !
Moreover I have tested older version of the driver resulting always to the same issue.
I have also tested different packet rates that shows that it is not related to the packet rate (10pps, 100pps, ...) and different packet sizes.

The following elements are attached to this message:
* lspci -vvvv outputs (from ubuntu 11.10 and ubuntu 10.04)
* modinfo on igb 3.2.10 (ub 10.04)
* dmesg on inserting the igb 3.2.10 module (ub 10.04)

Some more precisions:

The card firmware as shown by ethtool -i <interface> is listed as 1.2.1.

The card is not recognized in lspci under ubuntu 10.04 as shown below:
03:00.0 Ethernet controller: Intel Corporation Device 1526 (rev 01)
03:00.1 Ethernet controller: Intel Corporation Device 1526 (rev 01)
04:00.0 Ethernet controller: Intel Corporation Device 1526 (rev 01)
04:00.1 Ethernet controller: Intel Corporation Device 1526 (rev 01)

Although it is recognized under ubuntu 11.10:
03:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
03:00.1 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
04:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
04:00.1 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)

I would be very grateful if anyone could give me any advice or direction on how to solve/identify the problem.
Thank you !

---

### Post by ubxyz on 2011-11-02
bug related to :
 
-> [http://sourceforge.net/tracker/index.php?func=detail&aid=3425859&group_id=42302&atid=447449](http://sourceforge.net/tracker/index.php?func=detail&aid=3425859&group_id=42302&atid=447449)
-> [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/829566](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/829566)
-> [http://sourceforge.net/tracker/index.php?func=detail&aid=1575590&group_id=42302&atid=447449](http://sourceforge.net/tracker/index.php?func=detail&aid=1575590&group_id=42302&atid=447449) (for e1000e driver)

---

