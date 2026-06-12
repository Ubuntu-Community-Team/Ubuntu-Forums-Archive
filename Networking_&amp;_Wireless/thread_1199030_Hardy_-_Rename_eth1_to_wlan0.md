---
title: "Hardy - Rename eth1 to wlan0"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by frogotronic on 2009-06-28
Hello,

  I've been having a bear of a time trying to rename my wireless network interface.  I recently switched from ndiswrapper (ndiswrapper) to Broadcom STA Linux driver (wl).  During the upgrade, the *new* interface was labelled as eth1.  I don't like my wireless connections labelled as "ethx" because I always associated ethx as a wired connection.  Therefore, I wanted to rename my new wireless connection back to "wlan0"

I'm using Hardy Heron 8.04.3 LTS with all updates as of June 28th, 2009.

Here's how I did it.

```
$ sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

Find your wireless MAC address, in my case it was the second rule:

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1049 (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:38:c0:5d:62", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:73:e3:24:28", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

```

If you are unsure, run this command

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:c0:5d:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x5000 Memory:d8500000-d8520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:337420 (329.5 KB)  TX bytes:337420 (329.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.213.1  Bcast:172.16.213.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.247.1  Bcast:172.16.247.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:1a:73:e3:24:28  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fee3:2428/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1189 errors:0 dropped:0 overruns:0 frame:18
          TX packets:1214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1080601 (1.0 MB)  TX bytes:214347 (209.3 KB)
          Interrupt:17
``` 


Switch back to the gedit window and change the **eth1** to **wlan0**

It should now look like this...

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1049 (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:38:c0:5d:62", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4312 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:73:e3:24:28", ATTR{type}=="1", KERNEL=="eth*", NAME="wlan0"
```

Close & Save the file.

Reboot & re-run the **ifconfig** command - your output should now be:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:c0:5d:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x5000 Memory:d8500000-d8520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:337420 (329.5 KB)  TX bytes:337420 (329.5 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.213.1  Bcast:172.16.213.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.247.1  Bcast:172.16.247.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:e3:24:28  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fee3:2428/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1189 errors:0 dropped:0 overruns:0 frame:18
          TX packets:1214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1080601 (1.0 MB)  TX bytes:214347 (209.3 KB)
          Interrupt:17 

```


Good luck.


- CH

---

### Post by MaindotC on 2009-06-28
Thanks for the tip.  Interface names haven't really bothered me all that much that I have to change the interface name - I'd probably change the variable calling the interface before I change the actual interface name - but interesting.

---

### Post by Dirren on 2009-08-12
Thanks, good howto / hint.
This happens often if you move or copy a virtual machine with an ubuntu guest system. 
When the machine is started in the new location you'll have no network because your network interface has changed name. 
You can see that this happened if you type ```
dmesg | grep eth
```

udev throws a line saying something like ```
renamed network interface eth0 to eth1
```
And it is also kind enough to add a new rule to /etc/udev/rules.d/70-persistent-net.rules for this new interface.

To get the old name back just edit this file according to cement_head's suggestions above :)

---

