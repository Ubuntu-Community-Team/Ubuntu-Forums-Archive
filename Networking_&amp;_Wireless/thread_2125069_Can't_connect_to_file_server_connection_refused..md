---
title: "Can't connect to file server: connection refused."
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by oldpilsbury on 2013-03-12
Trying to connect my laptop to a home file server I set up. It's a desktop connected via eth0 to a linksys router, which I connect to wirelessly on my laptop. I had started setting up a static ip by reconfiguring /etc/network/interfaces, then gave up because it wasn't working and reset it to auto dhcp. It was working before the static ip setup. I'm running ubuntu server. I'm just going to give the important parts of the server's ifconfig because I don't have wireless on the server: 
[eth0]
HWaddr: 00:13:72:24:c2:88
inet addr:192.168.1.103
Bcast: 192.168.1.255
Mask: 255.255.255.0
 
This is my laptop's ifconfig:
eth0      Link encap:Ethernet  HWaddr e8:03:9a:9b:31:7a  
          inet6 addr: fe80::ea03:9aff:fe9b:317a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:695 errors:0 dropped:1 overruns:0 frame:0
          TX packets:935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:232740 (232.7 KB)  TX bytes:172306 (172.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:678043 (678.0 KB)  TX bytes:678043 (678.0 KB)

wlan0     Link encap:Ethernet  HWaddr e8:03:9a:84:a0:43  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea03:9aff:fe84:a043/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22451908 (22.4 MB)  TX bytes:4921122 (4.9 MB)

Both computers (server and laptop) can ping the router (192.168.1.1), but not the other computers' inet addr. Both computers have a default gateway of 192.168.1.1, as per "route" command. Laptop has an additional destination beneath default and localnet:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     *               255.255.255.0   U     9      0        0 wlan0

This is from the router setup page via web browser:
Network setup
Router IP
IP address: 192.168.1.1
Subnet mask: 255.255.255.0
DHCP enabled.
Start IP: 192.168.1.100
IP address range 192.168.1.100-150

:guitar:
Halp!

---

### Post by RoosterHam on 2013-03-12
I'm not familiar with the linksys so please forgive me if this question is irrelevant. Does the linksys router have a setting to allow/disallow ping on internal or external ports?

Without more information my first thought is this may be a config on the router. Do both have connectivity to the outside world?

What was the config you tried in /etc/network/interfaces? are you able to post it?

---

### Post by steeldriver on 2013-03-12
if you are getting 'connection refused' rather than 'no route to host' or 'destination host unreachable' then it sounds like either the service (are you trying ssh?) is not listening on the specified port, or your laptop IP is being actively blocked by a config or firewall rule - rather than a basic network layer issue

---

