---
title: "Intermittent wireless connectivity"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by susanw on 2010-04-16
Updating an old edition of ubuntu has been fantastic for my old computer but lack of consistent internet is getting too annoying now,
Sometimes when the pc turns on wireless networks show up but computer will not connect to them, it tries then the password window repeatedly comes up. All the settings look correct in network connections.

Other times when I turn on the computer it all works just fine with exactly the same settings. Then later on that login it ay randomly turn disconnect, or just be fine for ages.


Any ideas on how to reconnect network without restarting and hoping that this time it 'magically' works would be much appreciated. I wondered if it was some external thing like other computers being on the network but my other computer doesn't suffer anything like this so unlikely?

Thank you in advance,

---

### Post by susanw on 2010-04-16
Some possibly helpful output data

When it doesn't work:

susan@susan-desktop:~$ ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.058 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.039 ms
^C
--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.039/0.045/0.058/0.011 ms
susan@susan-desktop:~$ sudo ifconfig
[sudo] password for susan: 
eth0      Link encap:Ethernet  HWaddr 00:01:80:50:0c:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:09:5b:91:b3:e1  
          inet6 addr: fe80::209:5bff:fe91:b3e1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:276 (276.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2312 (2.3 KB)  TX bytes:2312 (2.3 KB)

---

### Post by susanw on 2010-04-16
When it does work:

susan@susan-desktop:~$ sudo ifconfig
[sudo] password for susan: 
eth0      Link encap:Ethernet  HWaddr 00:01:80:50:0c:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:09:5b:91:b3:e1  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe91:b3e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:2 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2434 (2.4 KB)  TX bytes:5192 (5.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

susan@susan-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"warrens wireless"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:C5:58:B3   
          Bit Rate:5.5 Mb/s   Sensitivity:1/0  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:2506-1979-25   Security mode:open
          Power Management:off
          Link Quality=32/70  Signal level=-54 dBm  Noise level=-134 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ignore the random smileys, supposed to be ":zero"

---

