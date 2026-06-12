---
title: "Physical Ethernet Not Connecting"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by potatohamster on 2010-07-19
Bit of background first: I'm in a bit of a situation here, as I'm in China for the next 3 weeks on a summe research deal. I've been here for 5 weeks, and somewhere around the first week my ethernet port stopped working for some reason. The wireless is fine, but any connected ethernet cable doesn't work with the netbook, even if they work with other laptops or computers.
 
I referred to this thread first but the solutions offered there did not help:
[http://ubuntuforums.org/showthread.php?t=1460266](http://ubuntuforums.org/showthread.php?t=1460266)
 
Hardware: Gateway LT20 Netbook
Release: Ubuntu 9.1 (karmic)
 
I've tried to use "sudo ifdown eth0" and "sudo ifup eth0" to "reset" it, but that didn't really do anything.
 
I'm an Ubuntu newb and don't really know what else to try. I have automatic DHCP settings on, if that info helps.
 
Any help would be so unbelievably appreciated; it's very frustrating having limited internet connectivity here.

---

### Post by potatohamster on 2010-07-19
If I need to provide any more information tell me what and how to do it please, I really want to get this taken care of as soon as I can.

---

### Post by mickwombat on 2010-07-19
Are the lights on the ethernet port flickering or on?

Try doing in terminal

```
# sudo /etc/init.d/networking restart
```

Check in network manager as well to make sure it 'starts automatically' or whatever it is that needs to be checked.

---

### Post by Iowan on 2010-07-19
After restarting networking, check **ifconfig -a**. If the wired interface has no connection, try **sudo dhclient eth0** (assuming the wired interface is eth0). Probably you'll get several lines ending with something like "No DHCP offers received... sleeping"

---

### Post by potatohamster on 2010-07-20
The ethernet port lights are flickering.
I did ```
sudo /etc/init.d/networking restart
``` and nothing happened/changed.

The results of **ifconfig -a** yielded: ```
Link encap:Ethernet  HWaddr 00:26:22:89:a6:c3  
          inet6 addr: fe80::226:22ff:fe89:a6c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21018184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:575557 (575.5 KB)  TX bytes:11216 (11.2 KB)
          Interrupt:29 
```
for eth0.

After **sudo dhclient eth0**, I received: 
```
There is already a pid file /var/run/dhclient.pid with pid 11819
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:26:22:89:a6:c3
Sending on   LPF/eth0/00:26:22:89:a6:c3
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.76 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.76 from 192.168.0.1
resolvconf: Error: /etc/resolv.conf must be a symlink
bound to 192.168.0.76 -- renewal in 42160 seconds.
```

Still nothing....

---

### Post by Iowan on 2010-07-21
> **potatohamster said:**
> 
```
...
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.76 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.76 from 192.168.0.1
resolvconf: Error: /etc/resolv.conf must be a symlink
bound to 192.168.0.76 -- renewal in 42160 seconds.
```
Interesting error message...
*LOOKS* like the machine got IP address 192.168.0.76 - **ifconfig -a** reports otherwise?

---

### Post by potatohamster on 2010-07-23
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27230 (27.2 KB)  TX bytes:27230 (27.2 KB)

wlan0     Link encap:Ethernet  HWaddr 90:4c:e5:a0:a7:66  
          inet addr:192.168.1.128  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::924c:e5ff:fea0:a766/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129363968 (129.3 MB)  TX bytes:18309963 (18.3 MB)
          Interrupt:16 Memory:57100000-57110000 

```

---

### Post by Iowan on 2010-07-23
Wow, eth0 doesn't show at all - let alone having reported IP address...

I've never done this, but...
try **sudo dhclient -r** to release the current lease, then **sudo dhclient eth0** to get another one. 

**man dhclient ** has some other good info. You can check what is in */var/lib/dhcp3/dhclient.leases*.

---

