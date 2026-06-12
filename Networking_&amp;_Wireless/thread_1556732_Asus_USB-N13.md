---
title: "Asus USB-N13"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by cdmike2k8 on 2010-08-19
I am trying to get this card working, and have tried everything I can find and think of.  Here is current status:
```


michael@michael-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 046d:c227 Logitech, Inc. 
Bus 004 Device 003: ID 046d:c226 Logitech, Inc. 
Bus 004 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bc2:3000 Seagate RSS LLC 
Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
michael@michael-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:10:09:0d  
          inet addr:192.168.1.130  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe10:90d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419650 (419.6 KB)  TX bytes:47070 (47.0 KB)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ra0       Link encap:Ethernet  HWaddr e0:cb:4e:bd:9e:24  
          inet6 addr: fe80::e2cb:4eff:febd:9e24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34669 (34.6 KB)  TX bytes:137272 (137.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:b6:71:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

michael@michael-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:18:F8:F4:9F:30
                    Protocol:802.11b/g
                    ESSID:"linksys"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-45 dBm  Noise level:-95 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 02 - Address: 68:7F:74:85:76:5B
                    Protocol:802.11b/g/n
                    ESSID:"linksys"
                    Mode:Managed
                    Channel:6
                    Quality:37/100  Signal level:-75 dBm  Noise level:-95 dBm
                    Encryption key:off
                    Bit Rates:18 Mb/s

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:F4:9F:30
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c2fdbb818b
                    Extra: Last beacon: 7040ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4

vboxnet0  Interface doesn't support scanning.

```
The network is seen, but unable to connect, saying unable to get IP address.  I am on 64 bit 10.04.  Any help would be appreciated.

---

