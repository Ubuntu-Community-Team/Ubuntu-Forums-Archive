---
title: "eeepc 1000HE, cannot detect wireless networks"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by dmbjr on 2010-03-01
Hi,

I am running Ubuntu 9.10 on an ASUS eeepc 1000HE, and my wireless card, RaLink RT 2860, is failing to recognize any wireless networks. It was working fine this morning, until I accidentally hit Fn F2, disabling the wireless card. I hit Fn F2 again to reenable it, but it no longer will detect any wireless networks (and other computers in the household do recognize them).

Any help at all will be greatly appreciated!

I googled quite a bit and talked to a human about this but could not fix it. We tried dhclient ra0, which returned 

There is already a pid file /var/run/dhclient.pid with pid 2438
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:25:d3:13:f4:20
Sending on   LPF/ra0/00:25:d3:13:f4:20
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Other data:

iwconfig returns 

(other stuff here...)

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig returns

(other stuff here...)

ra0       Link encap:Ethernet  HWaddr 00:25:d3:13:f4:20  
          inet6 addr: fe80::225:d3ff:fe13:f420/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

ra0:avahi Link encap:Ethernet  HWaddr 00:25:d3:13:f4:20  
          inet addr:169.254.7.117  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19

---

### Post by booah on 2010-10-01
> **dmbjr said:**
> Hi,

I am running Ubuntu 9.10 on an ASUS eeepc 1000HE, and my wireless card, RaLink RT 2860, is failing to recognize any wireless networks. It was working fine this morning, until I accidentally hit Fn F2, disabling the wireless card. I hit Fn F2 again to reenable it, but it no longer will detect any wireless networks (and other computers in the household do recognize them).

Any help at all will be greatly appreciated!

I googled quite a bit and talked to a human about this but could not fix it. We tried dhclient ra0, which returned 

There is already a pid file /var/run/dhclient.pid with pid 2438
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:25:d3:13:f4:20
Sending on   LPF/ra0/00:25:d3:13:f4:20
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Other data:

iwconfig returns 

(other stuff here...)

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig returns

(other stuff here...)

ra0       Link encap:Ethernet  HWaddr 00:25:d3:13:f4:20  
          inet6 addr: fe80::225:d3ff:fe13:f420/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

ra0:avahi Link encap:Ethernet  HWaddr 00:25:d3:13:f4:20  
          inet addr:169.254.7.117  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19

I had the exact same issue today trying to get my wireless working from command line (xbmc live).

---

