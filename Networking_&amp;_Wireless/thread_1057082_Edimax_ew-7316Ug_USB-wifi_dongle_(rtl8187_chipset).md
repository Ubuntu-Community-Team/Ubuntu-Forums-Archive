---
title: "Edimax ew-7316Ug USB-wifi dongle (rtl8187 chipset)"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by fb2007 on 2009-02-01
Hi!

I'm running xubuntu 8.10 on a laptop (clean install), and I recently bought Edimax EW-7316Ug USB-WIFI dongle, which is powered by realtek RTL8187 chipset (the card works on windows).

The output of **lsusb** is:
```
Bus 002 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

With NetworkManager I can see and also conect to my home wifi network. So if I do **ifconfig**:
```
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:d3:99:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2966 (2.9 KB)  TX bytes:2966 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:1f:02:01  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:1fff:fe1f:201/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7199 (7.1 KB)  TX bytes:12709 (12.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-1F-1F-02-01-32-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

And **iwconfig**:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:18 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=48/100  Signal level:-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

But I have a lot of problems with my connection (it's WPA encrypted, and it doesn't help if I turn the encryption off). If I do **ping**:
```
ursa@webshox:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.089 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.073 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.072 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.069 ms
64 bytes from localhost (127.0.0.1): icmp_seq=5 ttl=64 time=0.076 ms
64 bytes from localhost (127.0.0.1): icmp_seq=6 ttl=64 time=0.075 ms
^C
--- localhost ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4996ms
rtt min/avg/max/mdev = 0.069/0.075/0.089/0.011 ms
ursa@webshox:~$ ping 192.168.1.3
PING 192.168.1.3 (192.168.1.3) 56(84) bytes of data.
64 bytes from 192.168.1.3: icmp_seq=1 ttl=64 time=0.089 ms
64 bytes from 192.168.1.3: icmp_seq=2 ttl=64 time=0.076 ms
64 bytes from 192.168.1.3: icmp_seq=3 ttl=64 time=0.081 ms
^C
--- 192.168.1.3 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.076/0.082/0.089/0.005 ms
ursa@webshox:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=128 time=4.44 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=128 time=7.05 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=128 time=7.87 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=128 time=8.71 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=128 time=8.54 ms
^C
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 4.440/7.322/8.710/1.559 ms
ursa@webshox:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=18 Destination Host Unreachable
From 192.168.1.3 icmp_seq=19 Destination Host Unreachable
From 192.168.1.3 icmp_seq=20 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
21 packets transmitted, 0 received, +3 errors, 100% packet loss, time 20016ms
, pipe 3
ursa@webshox:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Host Unreachable
From 192.168.1.3 icmp_seq=2 Destination Host Unreachable
From 192.168.1.3 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3028ms
, pipe 3
```

EDIT:
I lose ping to my router, when I try to **ping [www.google.com](www.google.com)** or when I try open any page with firefox!


As far as I can tell the connection is very buggy! 192.168.1.1 is my routers address and 192.168.1.3 is my PC address. I newer got http protocol trough!

Does anybody know what else can I try?

Any help will be appreciated! Thanks in advance, fb2007!

---

### Post by roosh on 2010-07-03
You could try ndiswrapper if you have or can find windows XP drivers. 

Look here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

