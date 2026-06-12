---
title: "No network connection with Lenovo Q150"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by teddytornado on 2011-02-18
Hi all,

I have a problem with my Lenovo Q150 and Ubuntu 10.10 Server edition.
The Q150 is not able to get the IP from the DHCP.
I tried a lot of things but without any results.

Below some information about my system.
I hope someone could help.


/etc/network/interfaces file:
```

auto eth0
iface eth0 inet dhcp

```
sudo lshw -class network
Network is disabled ! Possible to enable it ?
```

  *-network DISABLED
       description: Ethernet interface
       product: 82552 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 70:71:bc:4c:0a:39
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:fcfff000-fcffffff ioport:dc00(size=64)

```
ifconfig
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1664 (1.6 KB)  TX bytes:1664 (1.6 KB)

```
Many thanks in advance,
Kai

---

### Post by Hippytaff on 2011-02-18
Hi and welome You can try
```

sudo ifconfig eth0 up
``` to enable it, but ethernet connections should work without any problems. Does ethernet work with any other OS/PC?
 
You might need to manually configure your DHCP settings
 
What does you /etc/hosts file look like?

---

### Post by teddytornado on 2011-02-18
Many thanks !

The ethernet is working well with some other PC's and it worked also on the Q150 with Windows 7 before so it should be no hardware or network problem.

sudo ifconfig eth0 up
```

SIOCSIFFLAGS: Resource temporarily unavailable

```
/etc/hosts
```

127.0.0.1    localhost
127.0.1.1    the-root

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by nmstewart on 2011-02-18
Kai,

I just repaved mine the same way. search the forum for Q150 and you can see what worked.

Unfortunately when switching from windows to ubuntu I need to completely remove the power supply before switching to get it to load correctly.

Still trying to get the wireless working. I will post my results when I am successful.

Best of Luck,
Neil

---

### Post by Hippytaff on 2011-02-18
Odd...I know this is an obvious suggestion, but have you tried turning the router off and on again.
 
nmstewart seems to have found something more useful...I've only ever experinced SIOCSIFFLAGS when wireless firmware is missing

---

### Post by teddytornado on 2011-02-18
It is hard to believe but it is working now :D.

I have cutted the power supply for one minute and now it is working.
Unbelievable. I tried nearly everything before !

MANY THANKS Hippytaff & Neil

---

### Post by Hippytaff on 2011-02-18
your welcome - Glad you sorted it :-)
 
Remember to mark the thread as solved in the thread tools at the top of the page :-)

---

