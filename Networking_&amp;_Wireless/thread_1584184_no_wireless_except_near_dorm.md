---
title: "no wireless except near dorm"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by erjoalgo on 2010-09-28
I connect my laptop to my school's wireless network, which blankets the entire campus. The name of the connection is the same throughout campus, but there seem to be different access points (I dont know the details of this).

The first time I connected to the wireless network, it was near my dorm, so I must have connected to an access point near my dorm. 
My problem is that I cant connect to the network anywhere else except near my dorm!

I suspect that because the connection has the same name everywhere, Ubuntu tries to use the same exact settings (maybe the same IP, who knows), which vary from one access point to another.

I have tried several things including delete the connection information from "edit connections". Nothing has worked.

Additional Notes:
-Wireless works fine on Windows, from anywhere
-When connection is successful, sometimes a message pops up "~ your network uses a .local domain..."
-When attempting to use internet from outside dorm, sometimes network manager claims "connection established", but no browser can ever resolve any host. In this situation sometimes it "realizes" it is disconnected, and attempts to reconnect with no success.
-Here is the output from "sudo dhclient wlan0", according to the instructions on this official [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").
```

user@laptop:~$ sudo invoke-rc.d networking restart 
 * Reconfiguring network interfaces...                                                                                                                                                        [ OK ] 
user@laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 4023
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:24:d6:0c:f2:44
Sending on   LPF/wlan0/00:24:d6:0c:f2:44
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@laptop:~$ 

```

Any ideas are appreciated. It is immensely frustrating to have an internet capable device and not be able to connect to an open network.

---

### Post by blakep2 on 2010-09-28
The router located on the campus is not serving ip addresses.
Post the command ifconfig
If you are not using a static ip you might have to contact the IT team at your college.

I go to Clayton State and their dhcp get hammered all the time.  I don't think this would be a problem within the dorm where there are a limited number of clients

---

### Post by erjoalgo on 2010-09-29
Thanks for your response! Im glad someone else has/had a similar problem with these campus wide networks.
I dont think this is an issue on their side; no one that I know has the same issue, and my own computer doesnt have this issue when it is on Windows.
This is the output of ifconfig, though right now I am in my dorm so I dont think the problem will be evident from this. I will also post the output when I actually am having the problem. 

```
eth0      Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b  
          inet6 addr: fe80::224:e8ff:fed0:6f8b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1636193 (1.6 MB)  TX bytes:510839 (510.8 KB)
          Interrupt:31 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:0c:f2:44  
          inet addr:128.237.233.39  Bcast:128.237.255.255  Mask:255.255.224.0
          inet6 addr: fe80::224:d6ff:fe0c:f244/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117496 (117.4 KB)  TX bytes:9737 (9.7 KB)


```

Also I will keep searching the message:
"No DHCPOFFERS received"

---

### Post by erjoalgo on 2010-09-29
output of $ifconfig when outside of dorm
```


eth0      Link encap:Ethernet  HWaddr 00:24:e8:d0:6f:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1636193 (1.6 MB)  TX bytes:510839 (510.8 KB)
          Interrupt:31 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX paI dont think this can be very helpful at all. Any ideas??ckets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15376 (15.3 KB)  TX bytes:15376 (15.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:0c:f2:44  
          inet6 addr: fe80::224:d6ff:fe0c:f244/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:65392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19308882 (19.3 MB)  TX bytes:5011628 (5.0 MB)

```

It seems that I have no "inet addr". Any ideas please??

---

