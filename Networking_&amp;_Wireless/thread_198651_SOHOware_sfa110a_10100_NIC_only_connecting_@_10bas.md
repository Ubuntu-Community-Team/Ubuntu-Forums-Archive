---
title: "SOHOware sfa110a 10/100 NIC only connecting @ 10baseT"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by the7trumpets on 2006-06-17
I have a SOHOware sfa110a card which works at 10Mb/s, but does not connect at 100Mb/s (based on the 100mb/s light not coming on on the card, and transfers being limited to 10mb/s).

I have read quite a few threads talking about mii-tool and ethtool, hoping they could force my card into 100-baseTX:

[http://ubuntuforums.org/showthread.php?t=62821](http://ubuntuforums.org/showthread.php?t=62821)
[http://ubuntuforums.org/showthread.php?t=197931](http://ubuntuforums.org/showthread.php?t=197931)
[http://ubuntuforums.org/showthread.php?t=191653](http://ubuntuforums.org/showthread.php?t=191653)
[http://ubuntuforums.org/showthread.php?t=113629](http://ubuntuforums.org/showthread.php?t=113629)

But neither tool seems to have any knowledge or control over my NIC.


Running ifconfig I get the following:

eth0      Link encap:Ethernet  HWaddr 00:80:C6:F9:D9:87
          inet addr:192.168.2.201  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::280:c6ff:fef9:d987/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8151292 (7.7 MiB)  TX bytes:1324942 (1.2 MiB)
          Interrupt:185 Base address:0xd000

sudo ethtool eth0
Outputs:
No data available

sudo ethtool -s eth0 speed 100
Outputs:
Cannot get current device settings: Operation not supported

sudo mii-tool
Outputs:
no MII interfaces found

So, it seems that I have a network card which cannot talk to any existing linux tools... :( Next I went to SOHOware's site, and found the following page listing two linux drivers for the sfa110a:

[http://www.sohoware.com/span/new_sohoware/newfiles/consumerpages/downloadcenter.htm](http://www.sohoware.com/span/new_sohoware/newfiles/consumerpages/downloadcenter.htm)

BUT, those seem to be for kernel 2.0.x or 2.4.x. Not only do I not know how to build stuff, but I don't even know if these drivers are compatable with the 2.6.x kernel. There are fairly detailed install directions, but it references source directories (like /usr/source/linux/ and /usr/src/linux) which simply don't exist.

Do I need to install drivers? Do I need to use a tool other than mii-tool or ethtool? What do I do to get my card connected to the network at 100Mb/s?

---

