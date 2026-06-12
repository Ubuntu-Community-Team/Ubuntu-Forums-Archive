---
title: "Problems with Static IP"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2008-12-24
Hey All,

By no means a newbie to home networking, but I'm hitting a wall here, I must be overlooking something simple...

I have a cheap, older D-Link wireless G router, configured how I'd like. Some pertinent information below. I've reserved a range of IP Addresses for DHCP. I have an Ubuntu Desktop to which I would like to assign a static address outside the DHCP range.

I tried ifconfig and editing /etc/network/interfaces but each time is the same result, I end up with my self assigned address, but no internet access and can not ping my router (no route to host). The only network connection that is used on the desktop is a wireless pci card at wlan0.

```

Network Info for Ubuntu Desktop:

SSID: mySSID

address 192.168.0.2
netmask 255.255.255.240
broadcast 192.168.0.15
gateway 192.168.0.1

```
```

Working DHCP ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:40:F4:52:2C:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:91:B9:87  
          inet addr:192.168.0.8  Bcast:192.168.0.15  Mask:255.255.255.240
          inet6 addr: fe80::212:17ff:fe91:b987/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:206 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75662 (73.8 KB)  TX bytes:18781 (18.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-91-B9-87-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
```

Previously attempted interfaces configuration

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

# The primary wirless interface
auto wlan0
iface wlan0 inet static

address 192.168.0.2
netmask 255.255.255.240
broadcast 192.168.0.15
gateway 192.168.0.1


```

---

### Post by roelpeeters on 2008-12-24
Have you restart the networking script in /etc/init.d?

```

sudo /etc/init.d/network restart

```

---

### Post by DGortze380 on 2008-12-24
> **roelpeeters said:**
> Have you restart the networking script in /etc/init.d?

```

sudo /etc/init.d/network restart

```

yes I restarted networking after each change.

---

