---
title: "cant connect to the internet"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by scuba117 on 2009-12-04
Hey guys, i just installed Linux Ubuntu but im having trouble connecting to the internet wiht my usb wireless adapter. it works fine when i boot in Windows but not in Ubuntu..

it says "connection established" and says connection 100% but it wont let me access the internet :/

whats up? ty :)

---

### Post by scuba117 on 2009-12-04
Hey guys, i just installed Linux Ubuntu but im having trouble connecting to the internet wiht my usb wireless adapter. it works fine when i boot in Windows but not in Ubuntu..

it says "connection established" and says connection 100% but it wont let me access the internet :/

whats up? ty :smile:

---

### Post by Iowan on 2009-12-04
Does it get IP address (check from terminal via **ifconfig -a**)? 
If it has IP address, does it know how to get to internet (Check via **route -n** - your router address should be on last line as UG (gateway)? 
If it knows how to get there, does it know where to go (check for nameservers in */etc/resolv.conf)?*

---

### Post by cariboo on 2009-12-04
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by scuba117 on 2009-12-04
**i tried ifconfig -a and heres what i got:**

root@ubuntu:/home/# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:54:9a:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:e3:a7:78  
          inet6 addr: fe80::21e:e5ff:fee3:a778/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126 (126.0 B)  TX bytes:2036 (2.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-E5-E3-A7-78-65-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@ubuntu:/home/#

---

### Post by uncaspi on 2009-12-04
Try to disable wmaster0  /sbin/ifconfig wmaster0 down or ifdown wmaster0
Run dhclient wlan0 and se if you get an ip address.
Btw what vesion do you have?

---

### Post by Iowan on 2009-12-04
Hmmm... no IP address. Wonder to what the machine thinks it connected? 
(Not a DHCP server...)

---

### Post by scuba117 on 2009-12-04
> **uncaspi said:**
> 
Btw what vesion do you have?

version 9.10

---

### Post by scuba117 on 2009-12-04
> **uncaspi said:**
> Try to disable wmaster0  /sbin/ifconfig wmaster0 down or ifdown wmaster0
Run dhclient wlan0 and se if you get an ip address.
Btw what vesion do you have?

**i tried your suggestion, heres what i got**

root@ubuntu:/home/sknight# ifdown wmaster0
ifdown: interface wmaster0 not configured
root@ubuntu:/home/sknight# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/wlan0/00:1e:e5:e3:a7:78
Sending on   LPF/wlan0/00:1e:e5:e3:a7:78
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by zaphod777 on 2009-12-04
Are you using any MAC address filtering on your router?

How about setting a static IP address does that work.

Also make sure you set the DNS settings.

---

### Post by uncaspi on 2009-12-04
Try to remove all lines except auto lo and iface lo inet loopback in /etc/network/interfaces
and reboot.
See if you have any network icon up to the right in the panel and click it and look for any available networks.

---

### Post by scuba117 on 2009-12-05
i have linux ubuntu and im trying to access the internet, it says the connection is established and running at 100% but when i try and use anything online it wont let me.. even though it says im connected.. (usb wireless receiver btw)
[U]
heres some stuff i've tried:[/U]

root@ubuntu:/home/# ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0d:9d:54:9a:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:e3:a7:78  
          inet6 addr: fe80::21e:e5ff:fee3:a778/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126 (126.0 B)  TX bytes:2036 (2.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-E5-E3-A7-78-65-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@ubuntu:/home/#

root@ubuntu:/home/sknight# ifdown wmaster0
ifdown: interface wmaster0 not configured
root@ubuntu:/home/sknight# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/wlan0/00:1e:e5:e3:a7:78
Sending on   LPF/wlan0/00:1e:e5:e3:a7:78
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

