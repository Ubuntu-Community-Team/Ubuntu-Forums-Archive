---
title: "Wireless connection problems"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by pizzipie on 2010-04-20
I am in an RV Park and I cannot get my computer to connect to the Park's wireless. I am using a Linksys WPC55AG v 1.2 Wireless A+G adapter.
The computer is Dell Latitude D800. 
I don't normally have any trouble with connections. I can't identify anything abnormal about the results of iwconfig, below.

My wife is sitting here happily on the internet. She has a Dell Inspiron 1525 with built-in adapter.

Both computers are using Ubuntu 9.04. Code and Results are below.

Please help!!!!

Thanks in advance,

Rick P

=============   Inspiron 1525 ... CODE: sudo  iwlist scan ... ======================

eth1      Scan completed :
          Cell 01 - Address: 00:1B:5B:52:AD:19
                    ESSID:"2WIRE779"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-73 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s

======================  Latitude D800  ... CODE: sudo iwlist scan ... ==============

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:5B:52:AD:19
                    ESSID:"2WIRE779"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/100  Signal level:-66 dBm  Noise level=-92 dBm
                    Encryption key:off
                    IE: Unknown: 00083257495245373739
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 320130
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                    Extra:tsf=0000000001ec3181
                    Extra: Last beacon: 8484ms ago
=================================================================================================                   

The "Auto Connector" thingee won't connect so I tried the following:
                  
The following is the result of CODE:

sudo iwconfig wlan0 freq 2.462G ( OR  iwconfig essid "2WIRE779"  OR  iwconfig ap 00:1B:5B:52:AD:19) 
sudo killall dhclient
sudo dhclient wlan0

 ..........The RESULTS are all generally the same I'm asleep .............

There is already a pid file /var/run/dhclient.pid with pid 8736
removed stale PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:63:2e:00
Sending on   LPF/wlan0/00:12:17:63:2e:00
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

