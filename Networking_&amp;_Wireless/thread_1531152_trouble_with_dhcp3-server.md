---
title: "trouble with dhcp3-server"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by x0x on 2010-07-14
Hello, i am having trouble setting up dhcp3-server


ifconfig
```

k1ng@k1ng-desktop:~$ ifconfig
eth0 (auto)     Link encap:Ethernet  HWaddr 00:24:1d:ee:d2:4f  
          inet addr:192.168.3.11  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:feee:d24f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77446248 (77.4 MB)  TX bytes:5240763 (5.2 MB)
          Interrupt:26 

eth1  (static)    Link encap:Ethernet  HWaddr 00:e0:4c:ef:12:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5130 (5.1 KB)  TX bytes:5130 (5.1 KB)

```


dhcpd3 -f -d eth1
```

k1ng@k1ng-desktop:~$ sudo dhcpd3 -f -d eth1
[sudo] password for k1ng: 
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Not searching LDAP since ldap-server, ldap-port and ldap-base-dn were not specified in the config file
Wrote 0 leases to leases file.

No subnet declaration for eth1 (0.0.0.0).
** Ignoring requests on eth1.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth1 is attached. **


Not configured to listen on any interfaces!

```

dhcp.conf
```

    default-lease-time 600;
    max-lease-time 7200;

    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
    option routers 192.168.3.1;
    option domain-name-servers 8.8.8.8;
   # option domain-name &#8220;mydomain&#8221;;

    subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.200;
    }

```
any idea how to fix it?

thanks in advance

---

