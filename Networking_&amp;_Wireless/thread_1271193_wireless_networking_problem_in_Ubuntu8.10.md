---
title: "wireless networking problem in Ubuntu8.10"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by flylehe on 2009-09-20
Hi,

I must say I am really new to the networking stuff and Linux (Ubuntu8.10). I am unable to connect to my wireless network after running these commands to change the MAC address and run in monitor mode:
```

    airmon-ng stop wlan0 
    ifconfig wlan0 down
    macchanger --mac 00:11:22:33:44:55 wlan0
    airmon-ng start wlan0 

```
These are then followed by some call to aircrack-ng to test the security of my wireless network.

Here is what I have tried to connect to my wireless network:

(1) Firstly I think I should change wlan0 to where it was (especially the Mac address) with the following commands:
```

    ifconfig mon0 down
    ifconfig wlan0 down
    macchanger --mac 00:0e:9b:ab:56:19 # myoriginalMacAddress
    airmon-ng stop wlan0
    ifconfig wlan0 up

```
(2) secondly I tried to connect to my wireless network in my WICD but it failed at obtaining IP address after going through validating authentication. So I exited WICD and tried to do the same thing in terminal:
```

    $ sudo iwconfig wlan0 essid "mywireless"
    $ sudo dhclient wlan0
    There is already a pid file /var/run/dhclient.pid with pid 23682
    killed old client process, removed PID file
    Internet Systems Consortium DHCP Client V3.1.1
    Copyright 2004-2008 Internet Systems Consortium.
    All rights reserved.
    For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
    
    mon0: unknown hardware address type 803
    wmaster0: unknown hardware address type 801
    mon0: unknown hardware address type 803
    wmaster0: unknown hardware address type 801
    Listening on LPF/wlan0/00:0e:9b:ab:56:19
    Sending on   LPF/wlan0/00:0e:9b:ab:56:19
    Sending on   Socket/fallback
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
    DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
    No DHCPOFFERS received.
    No working leases in persistent database - sleeping.

```    
Anyone know what my problem is and how to solve it?

Thanks and regards!

---

