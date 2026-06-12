---
title: "command line / wicd"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by suvois on 2011-07-30
Connecting to the internet using Wicd and Networkmanager works just fine, but through the command line i get the next error:

```

# ifconfig eth1 down
# dhclient -r eth1
# ifconfig eth1 up
# iwconfig eth1 essid "[ESSID]"
# iwconfig eth1 key [KEY]
# dhclient eth1 -v
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth1/00:15:fa:31:b1:42
Sending on   LPF/eth1/00:15:fa:31:b1:42
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 10.0.0.8
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.

--- 10.0.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```What are Wicd and Networkmanager doing what i don't ?

Thanks

Btw: With open type connection just the same.

---

### Post by chili555 on 2011-07-30
Network Manager is so firmly in control that it's quite difficult to keep it from taking over management of the network interfaces. And, since people often roam from home to office to library to coffee shop, it is ever vigilant. I suspect that when you typed dhclient and pressed Enter, a few milliseconds later NM said, "I'm in control here, no thanks."

You might precede your commands with:```
sudo service network-manager stop
```In short, either use NM or remove it and use the command line; not both.

---

