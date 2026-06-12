---
title: "Wireless connected but no internet, ping 100% packet loss"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by Benic on 2009-02-21
I recently bought a Broadcom wireless card that works fine. I can connect to wireless network. I just set up a Trendnet TEW-432BRP router at home. I can connect to the router using a secure WEP connection. So far, no problem. But I just can't use internet. Here is some pertinent output:

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"MEBC"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:D1:40:30:0D   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=76/100  Signal level:-38 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:9a:6d:f5  
          inet adr:24.122.37.151  Bcast:24.122.37.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          Packets reçus:57430 erreurs:0 :0 overruns:1 frame:0
          TX packets:9272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:7707475 (7.7 MB) Octets transmis:1183002 (1.1 MB)
          Interruption:11 Adresse de base:0x2c00 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:218 erreurs:0 :0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:10752 (10.7 KB) Octets transmis:10752 (10.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:58:73:19  
          inet adr:192.168.1.100  Bcast:192.168.1.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1699 erreurs:0 :0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:531357 (531.3 KB) Octets transmis:9949 (9.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CE-58-73-19-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
```

If I ping loopback:
```
ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.097 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.084 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.081 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.077 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.077/0.084/0.097/0.013 ms
```

If I ping the router:
```
ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=127 time=6.91 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=127 time=1.36 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=127 time=1.09 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=127 time=1.08 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 1.086/2.616/6.917/2.485 ms
```

So far, so good. When Here comes trouble:
```

ping -c 4 216.239.57.99
PING 216.239.57.99 (216.239.57.99) 56(84) bytes of data.

--- 216.239.57.99 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3014ms
```

I have the right settings in /etc/resolv.conf so I don't think it's a DNS issue. 

I tried to look for some guides on the internet, but it's the first time I set up a home network. Maybe I didn't put the good router settings?

---

### Post by superprash2003 on 2009-02-21
what is eth0 connected to??

---

### Post by Benic on 2009-02-21
eth0 is directly connected to the modem. What I posted above is when eth0 is not connected.

---

### Post by superprash2003 on 2009-02-22
is this a DSL connection?? do you require a username and password and a dialer to connect to the internet or does the internet work as soon as you switch on your modem?

---

### Post by Benic on 2009-02-22
I found the problem! My internet provider changed its DNS addresses, but they still put the old ones on their website along the new ones. I didn't notice at first glance and put the wrong DNS settings. I changed DNS and now wireless and wired (through the router) internet work. 

I just don't understand why changing DNS would resolve the ping problem. If I try to ping again, I still have the same error message.

---

