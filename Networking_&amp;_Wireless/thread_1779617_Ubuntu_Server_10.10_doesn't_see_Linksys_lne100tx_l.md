---
title: "Ubuntu Server 10.10 doesn't see Linksys lne100tx lan card"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by Wug on 2011-06-10
My integrated ethernet controller got fried during a thunderstorm.  I dug around in some older computers and salvaged an old Linksys lne100tx 10/100 network card (v. 5.1) and popped that in, but have been unable to get the machine to recognize it. 

With the machine running and the card installed and connected, the link and 100mb/s leds on the card are lit and the switch registers a connection, but no connection is registered from within ubuntu.

ifconfig shows only a loopback device.
attempting to ifup eth0 gives error messages about a missing network device.

the integrated controller (while nonfunctional) has been disabled from the bios.

windows 7 x64 doesn't recognize either the old integrated controller (which it used to work fine with) or the new one.  Searching the internet has yielded that the "new" card is not compatible with windows 7 at all.

That's all of the relevant information I can think of.  I have a feeling that it's a missing driver, but I'm not sure which driver to attempt to load/install and have no idea how to do that.

I'm running ubuntu server 10.10 x64.

---

### Post by Wug on 2011-06-10
I managed to find a solution based on the info in [THIS THREAD.]("http://ubuntuforums.org/showthread.php?t=242918")

When I installed the new network card, the network information on disk became out of date in a subtle way.

using ifconfig -a would indicate that there was an eth1, but attempts to ifup or ifdown it would fail.  That other thread points to making sure /etc/iftab was up to date.  /etc/iftab has been replaced with the somewhat more complicated /etc/udev/rules.d/70-persistent-net.rules , which was where I found my solution.  2 network devices were listed, the old one on eth0, and the new one on eth1.  Switching the names of the 2 and restarting networking did the trick.

---

