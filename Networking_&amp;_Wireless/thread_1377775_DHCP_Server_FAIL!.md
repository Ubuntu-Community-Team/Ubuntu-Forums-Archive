---
title: "DHCP Server FAIL!"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by jimmy.eric on 2010-01-10
I'm trying to configure a DHCP server but when I try to start it it just fails.  

```
log

Jan 10 16:25:52 SRV-LINUX00 dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jan 10 16:25:52 SRV-LINUX00 dhcpd: All rights reserved.
Jan 10 16:25:52 SRV-LINUX00 dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jan 10 16:25:52 SRV-LINUX00 dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jan 10 16:25:52 SRV-LINUX00 dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jan 10 16:25:52 SRV-LINUX00 dhcpd: All rights reserved.
Jan 10 16:25:52 SRV-LINUX00 dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Jan 10 16:25:52 SRV-LINUX00 dhcpd: Wrote 0 leases to leases file.
Jan 10 16:25:52 SRV-LINUX00 dhcpd:
```Doesn't tell me anything.

Also, my dhcpd.config
```
ddns-update-style ad-hoc;

option domain-name "207.local";

option domain-name-servers 10.30.50.5, 8.8.8.8, 8.8.4.4;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

#configuration for an internal subnet.
subnet 10.30.50.0 netmask 255.255.255.0 {
range 10.30.50.49 10.30.50.99;
option domain-name-servers 10.30.50.5, 8.8.8.8, 8.8.4.4;
option domain-name "207.local";
option routers 10.30.50.5;
option broadcast-address 10.30.50.255;
default-lease-time 600;
max-lease-time 7200;
}
```

---

### Post by adam814 on 2010-01-10
What exactly fails?  Does it say that dhcpcd cannot be started? Or it starts and you can't get an IP from it on another machine?

---

### Post by Iowan on 2010-01-10
A common problem is failing to have an interface configured for the DHCP range.

---

### Post by jimmy.eric on 2010-01-11
It just fails to start.

When I restart the dhcp server it says stop fails
and then start fails

then it says to look in the syslog for the reason.

and syslog doesn't tell me.

---

### Post by jimmy.eric on 2010-01-11
It seems like my problem is with my eth1 ethernet device.  When I type ifconfig it shows eth1 but doesn't have an ip address.  And when I type ifdown eth1 it says eth1 is not configured

likewise ifup eth1 ouputs 

#Don't seem to be have all the variables for eth1/inet.
Failed to bring up eth1.#

---

### Post by adam814 on 2010-01-11
When I've done that I've had to assign a static IP(since it wouldn't make sense to assign yourself one dynamically) in the same subnet as the DHCP pool.  You could try something like this to try it out before going through setting it up automatically at boot:
```
#ifconfig eth1 up 10.30.50.1 netmask 255.255.255.0
```
Then restart the DHCP server.

---

