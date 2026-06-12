---
title: "Belkin F5D8010"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by csevcik on 2006-03-04
I posted this somwhere else by mistake :oops: :oops: 

"I have been trying to get a Belkin Pre-N Card working on my HP Pavilion ZT3300. I have no problems usign a Belkin 801.11g F5D7010 with MS Windows drives and ndiswrapper 1.10 (Included in kubuntu 5.10). But when I switched to the Pre N the darn thing worked with the Belkin drives packed with the card for MS W XP, it was just grat 108Mb/s and I could almost work at the neighbours house. But after switching off the machine the system crashed. I removed the wlan0 settings in recue mode started the laptop again tried my old Belkin F5D7010 wich worked great as usual, after but reinstalling the Pre N it never worked again!!!    .

Reinstalling the MS W XP drives with ndiswrapper (Belkin F5D8010 or Netgear WPNT 511, makes no difference) results in the following mesage after ifup wlan0 with the Pre N:

wlanctl-ng: No such device
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:11:50:2d:07:96
Sending on LPF/wlan0/00:11:50:2d:07:96
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
bogus UDP packet length: 556
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
bogus UDP packet length: 556
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

It looks as it cannot communicate with my Belkin Pre N router (my son's F5D8010 works great in a desktop with MS W XP home edition, and my doughter's and wife's laptops wit 802.11g and b ineterfaces also work great with MS W XP home and pro respectively)."

I was using Belkin Pre-N drivers when I first posted this, I have Netgear's WPNT511 now but it makes no difference. The problem seems to be that the card does not get dhcp service (it did at first). I have no problems with Belkin F5D7010 in the same machine with the same router nor with the internal Intel IP2100 chipset (type b). I need the Pre-N for its speed and wider service area. 

Can anybody help?

Many thanks Carlos

---

