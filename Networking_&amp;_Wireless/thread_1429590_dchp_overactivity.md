---
title: "dchp overactivity"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by Kramtoad on 2010-03-14
Hi-

DHCP is driving me crazy! Even though I am happily plugged into the net and the connection is working fine DHCP keeps sending discover requests one after another. This is fine with me but the requests are logged to syslog which makes the hard drive chatter 24 hours a day. Very annoying. Any ideas on why this is happening and how to limit the requests? I could find no info via google on this problem so I'm kinda wondering if the DHCP behavior is actually normal.

> 
Mar 14 10:39:13 cougar dhclient: DHCPREQUEST of 74.70.4.0 on eth0 to 10.195.128.1 port 67
Mar 14 10:39:15 cougar dhclient: DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
Mar 14 10:39:21 cougar dhclient: DHCPREQUEST of 74.70.4.0 on eth0 to 10.195.128.1 port 67
Mar 14 10:39:28 cougar dhclient: DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 21
Mar 14 10:39:29 cougar dhclient: DHCPREQUEST of 74.70.4.0 on eth0 to 10.195.128.1 port 67
Mar 14 10:39:47 cougar last message repeated 4 times
Mar 14 10:39:49 cougar dhclient: DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 1
Mar 14 10:39:50 cougar dhclient: No DHCPOFFERS received.
Mar 14 10:39:50 cougar dhclient: No working leases in persistent database - sleeping.
Mar 14 10:39:54 cougar dhclient: DHCPREQUEST of 74.70.4.0 on eth0 to 10.195.128.1 port 67
Mar 14 10:39:54 cougar dhclient: DHCPREQUEST of 74.70.4.0 on eth0 to 10.195.128.1 port 67


---

