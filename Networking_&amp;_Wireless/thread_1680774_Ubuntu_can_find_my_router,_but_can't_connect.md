---
title: "Ubuntu can find my router, but can't connect"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by EvanEjk on 2011-02-03
It says my routor's name and signal strength but when I try to connect it tries for a while and then fails.

---

### Post by EvanEjk on 2011-02-03
I tryed uninstalling network manager and connecting in the terminal but I got this:

```
kevin@ubuntu:~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/ra0/88:9f:fa:22:84:a2
Sending on   LPF/ra0/88:9f:fa:22:84:a2
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

