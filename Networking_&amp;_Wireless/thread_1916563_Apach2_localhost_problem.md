---
title: "Apach2 localhost problem"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by Phoneus on 2012-01-28
Hi, 

> Problem connecting to localhost; Apache2 Ubuntu 10.10, PHP, MySQL,   after intsalling a Wlancard and some Updates I fail to connect to my Website.  

Apache does not show any errors in the logs and seems to run normal. But I cannot connect to localhost, 127.xxxx or to my ip.   I bet it has something to do with the newly installed wirelesscard?

I hope someone can help me. If more informations needed just say what you need.

> netstat -nlp 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      3229/mysqld     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4100/apache2    
tcp        0      0 0.0.0.0:9876            0.0.0.0:*               LISTEN      4100/apache2    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      864/cupsd       
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      2039/master     
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      2056/tor        
tcp6       0      0 ::1:631                 :::*                    LISTEN      864/cupsd       
udp        0      0 0.0.0.0:59186           0.0.0.0:*                           819/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3906/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           819/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                819/avahi-daemon: r
udp6       0      0 :::55027                :::*                                819/avahi-daemon: r
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:22:d0:a0:67  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fed0:a067/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17835 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16039229 (16.0 MB)  TX bytes:2784277 (2.7 MB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30840 (30.8 KB)  TX bytes:30840 (30.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:30:bd:93:4e:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


errorlogs after restart... Just restarted sometimes and deactivated safe mode.... Nothing.

> [Sat Jan 28 14:39:12 2012] [notice] caught SIGTERM, shutting down
PHP Warning:  Directive 'safe_mode' is deprecated in PHP 5.3 and greater in Unknown on line 0
[Sat Jan 28 14:42:22 2012] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.7 with Suhosin-Patch configured -- resuming normal operations
[Sat Jan 28 14:46:15 2012] [notice] caught SIGTERM, shutting down
PHP Warning:  Directive 'safe_mode' is deprecated in PHP 5.3 and greater in Unknown on line 0
[Sat Jan 28 14:46:16 2012] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.7 with Suhosin-Patch configured -- resuming normal operations
[Sat Jan 28 14:54:44 2012] [notice] caught SIGTERM, shutting down
PHP Warning:  Directive 'safe_mode' is deprecated in PHP 5.3 and greater in Unknown on line 0
[Sat Jan 28 14:54:45 2012] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.7 with Suhosin-Patch configured -- resuming normal operations
[Sat Jan 28 15:03:16 2012] [notice] caught SIGTERM, shutting down
PHP Warning:  Directive 'safe_mode' is deprecated in PHP 5.3 and greater in Unknown on line 0
[Sat Jan 28 15:03:33 2012] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.7 with Suhosin-Patch configured -- resuming normal operations
[Sat Jan 28 15:22:15 2012] [notice] caught SIGTERM, shutting down
[Sat Jan 28 15:22:22 2012] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.7 with Suhosin-Patch configured -- resuming normal operations
[Sat Jan 28 15:47:56 2012] [notice] caught SIGTERM, shutting down
[Sat Jan 28 15:47:57 2012] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.7 with Suhosin-Patch configured -- resuming normal operations

---

