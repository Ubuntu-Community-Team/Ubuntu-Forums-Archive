---
title: "Ethernet controller not functioning [VIA Technologies, Inc. VT6102 [Rhine-II)"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by fuwkej on 2009-05-03
Recently installed Xubuntu on an old computer (only 192mb of RAM). Systems works good, but the ethernet does not function. The internet connection is solid, but the Ethernet controller does not pick up the network.

from lspci:

Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78 )


Ubuntu website shows that a similiar card is supported, but doesn't list direct support for the exact model.

:confused:

---

### Post by chili555 on 2009-05-03
I think this is supposed to work with a module named, appropriately enough, *via-rhine*. If you do:```
sudo /etc/init.d/NetworkManager stop
sudo modprobe via-rhine
sudo ifconfig eth0 up
sudo dhclient eth0
```Do you get any errors? IP address?

---

### Post by fuwkej on 2009-05-03
Thanks for the quick reply, here are the results:

sudo /etc/init.d/NetworkManager stop
* Stopping network connection manager NetworkManager        [ OK ]

sudo modprobe via-rhine
WARNING: All config files need .conf /etc/modprobe.d/oss-compat, it will be ignored in a future release.

sudo ifconfig eth0 up

sudo dhclient eth0
Internet Systems Consortium DHCP Client C3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/eth0/00:11:d8:1f:1c:8f
Sending on   LPF/eth0/00:11:d8:1f:1c:8f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by chili555 on 2009-05-03
I don't think this will help or hurt your ability to connect, however it will just tidy things up:```
sudo mv /etc/modprobe.d/oss-compat /etc/modprobe.d/oss-compat.conf
```We at least know your ethernet is functioning! It seems to do everything except connect. Can you please post:```
dmesg | grep eth0
```Hopefully we can find and fix whatever is going wrong.

---

### Post by fuwkej on 2009-05-03
Modded the oss-compat.conf file.

The output from dmesg | grep eth0 is as follows:

[HTML]dmesg | grep eth0
[    3.382109] eth0: VIA Rhine II at 0xea003000, 00:11:d8:1f:1c:8f, IRQ 23.
[    3.382818] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   24.379921] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   34.888009] eth0: no IPv6 routers present[/HTML]

Thanks for helping

---

### Post by chili555 on 2009-05-04
I have been Googling quite a bit today and have determined that the Via is a troubling little chipset! At least, troubling to my ego!

I saw this: [http://ubuntuforums.org/showthread.php?t=897982&highlight=via-rhine](http://ubuntuforums.org/showthread.php?t=897982&highlight=via-rhine) Please try this:```
sudo ethtool -s speed 10 duplex half
sudo dhclient eth0
```Please report your success!

---

### Post by fuwkej on 2009-05-04
Unfortunately, no success.

Tried those commands, and gave me a syntax error, found in man file that eth0 has to be after -s. Changed that and it worked, but via dhclient test and still fails.

Just trying ethtool eth0, and everything appears to be working perfectly, just no internet.


You know if there is a way to diagnose it from my good computer? Like by networking the two together and running a network test on it.

---

### Post by chili555 on 2009-05-06
I'm sorry, my friend, but I'm stumped. Everything looks just perfect...except it doesn't work. I can't see a single thing to adjust or fix!!!

How would you feel about buying a new NIC card?

---

### Post by fuwkej on 2009-05-06
Ok, thanks for the help anyhow - maybe I'll just try another linux distribution since ubuntu isn't very good without a net connection (i know the card still works because it worked under windows). Know any good ones?

([http://www.creativesynthesis.net/blog/wp-content/uploads/feeds.feedburner.com/wp-content/uploads/2008/03/44218-linuxdistrotimeline-72.png](http://www.creativesynthesis.net/blog/wp-content/uploads/feeds.feedburner.com/wp-content/uploads/2008/03/44218-linuxdistrotimeline-72.png))

Still trying to figure out what I could use it for. I'd like to set it up to just do calculations, like for those scientific research programs, but it's not worth the extra dollar a month in utility bills.

Could always scrap it, and sell the parts on ebay.. might just be the best graveyard for it.

---

