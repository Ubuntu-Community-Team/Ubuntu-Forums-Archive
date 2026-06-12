---
title: "Cannot connect to ethernet"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by garmada on 2009-04-07
I install vmware server 2 and eth0 was destroy. Plz how to create eth0 network connection. This is my ifconfig:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1438796 (1.4 MB)  TX bytes:1438796 (1.4 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.21.1  Bcast:172.16.21.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.146.1  Bcast:192.168.146.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:61:b3:a8  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe61:b3a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:390966 errors:0 dropped:0 overruns:0 frame:0
          TX packets:383085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:585079553 (585.0 MB)  TX bytes:37858050 (37.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-61-B3-A8-33-61-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by superprash2003 on 2009-04-07
post output of cat /etc/network/interfaces

---

### Post by garmada on 2009-04-07
This is output from my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address         172.17.207.121
        netmask         255.255.255.0
        broadcast       172.17.207.255
        network         172.17.207.0
```

---

### Post by superprash2003 on 2009-04-08
in your terminal type **sudo /etc/init.d/networking restart** and post output

---

### Post by garmada on 2009-04-08
This is output:
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0.
eth1: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
```

---

### Post by GeeZor on 2009-04-08
is there an entry for eth in your dmesg
```

dmesg |grep eth

```

looks like you driver is not loaded..
dmesg will tell you what happend at startup

maybe that will help you.. 


Good luck!

---

### Post by garmada on 2009-04-08
This is output:
```
$ dmesg |grep eth
[    0.544192] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    4.111443] Driver 'sd' needs updating - please use bus_type methods
[    4.140809]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
```

---

