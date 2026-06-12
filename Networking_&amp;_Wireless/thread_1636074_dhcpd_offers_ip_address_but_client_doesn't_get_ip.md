---
title: "dhcpd offers ip address but client doesn't get ip"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by kristof_v on 2010-12-02
I set up a dhcpd on my ubuntu server with this configuration:
please note that the ubuntu server which runs the dhcpd has a static ip
of 192.168.1.50

```

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.50;
option domain-name-servers 192.168.1.50;
option netbios-name-servers 192.168.1.50;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.150 192.168.1.200;
}

```

Now when I try to get an ip from the dhcpd server from my ubuntu client computer the server offers an ip from the pool of 192.168.1.150 but the client doesn't seem to pick it up, instead it fires new requests until a timeout occurs:

```

Listening on LPF/eth0/00:24:8c:1d:fb:40
Sending on   LPF/eth0/00:24:8c:1d:fb:40
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 195.130.132.102 port 67
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:24:8c:1d:fb:40
Sending on   LPF/eth0/00:24:8c:1d:fb:40
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.150 from 192.168.1.50
DHCPREQUEST of 192.168.1.150 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.150 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.150 from 192.168.1.50
DHCPREQUEST of 192.168.1.150 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.150 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.150 from 192.168.1.50
DHCPREQUEST of 192.168.1.150 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.150 on eth0 to 255.255.255.255 port 67
...

```

Any ideas??

---

