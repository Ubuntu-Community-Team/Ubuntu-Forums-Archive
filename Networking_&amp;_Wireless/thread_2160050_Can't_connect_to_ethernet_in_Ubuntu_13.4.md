---
title: "Can't connect to ethernet in Ubuntu 13.4"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by TheHimself on 2013-07-05
The LED at the ethernet socket is turned on but doesn't flash. Network manager doesn't do anything as if the cable is not connected.
The network is not to blame because my other computer connects without a problem. Here is the output of ifconfig (when the cable is connected)

eth0      Link encap:Ethernet  HWaddr 00:1d:72:8e:d2:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:329279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:273363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:296544501 (296.5 MB)  TX bytes:46697014 (46.6 MB)
          Interrupt:20 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1294903 (1.2 MB)  TX bytes:1294903 (1.2 MB)

---

### Post by DeathByDenim on 2013-07-05
It appears you didn't receive an IP address from the DNS server (your router). You can try looking in /var/log/syslog for the output regarding NetworkManager:
```
grep NetworkManager /var/log/syslog
```

You can also try running this command to fetch an IP address:
```
sudo dhclient eth0
```
If that fails, you can again look in /var/log/syslog to see if there are any error messages.

---

