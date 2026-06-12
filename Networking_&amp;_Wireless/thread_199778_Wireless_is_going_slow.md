---
title: "Wireless is going slow"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by Moldy Jello on 2006-06-19
Hi, i have the broadcom card in my computer, the bcm 4318, i got wireless working by following [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom) the thing is, when i use it, it is very slow, like it takes an additional 8 seconds to even start loading a page, its not my internet because i checked with all my other computers on the same websites to see if it was the site i was looking at or my internet, but they load instantly, i tried using swiftfox as well that i found on here, so any help or suggestions on getting my wireless working faster would be appreciated, oh and i tested my band width, still at the normal download speeds and everything, it just takes a long time to start loading the page

---

### Post by nickpaton on 2006-06-19
Hi

Try here:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")

---

### Post by iitywygms on 2006-06-19
same issue here, mine is a 4306.  I did not use ndiswrapper, i used bcmfwcutter ( i think that is how it is spelled)  check out my ping times.

First one was real slow, then i waited a minute and tried again and it got a little faster, then i plugged a network cable in. ( so i could connect ) it stops working after some time.
any ideas?  

kevin@kevin-laptop:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=23436 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=22550 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=21566 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=20571 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=19579 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=18580 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=17580 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=16589 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=15590 ms
64 bytes from 192.168.2.1: icmp_seq=10 ttl=64 time=14592 ms
64 bytes from 192.168.2.1: icmp_seq=11 ttl=64 time=13592 ms
64 bytes from 192.168.2.1: icmp_seq=12 ttl=64 time=12579 ms
64 bytes from 192.168.2.1: icmp_seq=13 ttl=64 time=11581 ms
64 bytes from 192.168.2.1: icmp_seq=14 ttl=64 time=10570 ms
64 bytes from 192.168.2.1: icmp_seq=15 ttl=64 time=9570 ms
64 bytes from 192.168.2.1: icmp_seq=16 ttl=64 time=8577 ms
64 bytes from 192.168.2.1: icmp_seq=17 ttl=64 time=7582 ms
64 bytes from 192.168.2.1: icmp_seq=18 ttl=64 time=6578 ms
64 bytes from 192.168.2.1: icmp_seq=19 ttl=64 time=5565 ms
64 bytes from 192.168.2.1: icmp_seq=20 ttl=64 time=4567 ms
64 bytes from 192.168.2.1: icmp_seq=21 ttl=64 time=3556 ms
64 bytes from 192.168.2.1: icmp_seq=22 ttl=64 time=2561 ms
64 bytes from 192.168.2.1: icmp_seq=23 ttl=64 time=1550 ms
64 bytes from 192.168.2.1: icmp_seq=24 ttl=64 time=551 ms
64 bytes from 192.168.2.1: icmp_seq=25 ttl=64 time=3.26 ms
64 bytes from 192.168.2.1: icmp_seq=26 ttl=64 time=1382 ms
64 bytes from 192.168.2.1: icmp_seq=27 ttl=64 time=4924 ms
64 bytes from 192.168.2.1: icmp_seq=28 ttl=64 time=3982 ms
64 bytes from 192.168.2.1: icmp_seq=29 ttl=64 time=3295 ms
64 bytes from 192.168.2.1: icmp_seq=30 ttl=64 time=2337 ms
64 bytes from 192.168.2.1: icmp_seq=31 ttl=64 time=4581 ms
64 bytes from 192.168.2.1: icmp_seq=32 ttl=64 time=3592 ms
64 bytes from 192.168.2.1: icmp_seq=33 ttl=64 time=2904 ms
64 bytes from 192.168.2.1: icmp_seq=34 ttl=64 time=2015 ms
64 bytes from 192.168.2.1: icmp_seq=35 ttl=64 time=3094 ms
64 bytes from 192.168.2.1: icmp_seq=36 ttl=64 time=3566 ms

--- 192.168.2.1 ping statistics ---
40 packets transmitted, 36 received, 10% packet loss, time 39211ms
rtt min/avg/max/mdev = 3.266/9036.300/23436.294/7131.824 ms, pipe 24
kevin@kevin-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:20:21:FE:37
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:90:4B:5E:C5:FB
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4919 errors:0 dropped:10 overruns:0 frame:0
          TX packets:4649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4990054 (4.7 MiB)  TX bytes:1694382 (1.6 MiB)
          Interrupt:9 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

kevin@kevin-laptop:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=312 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=17.0 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=3.49 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=42.7 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=95.4 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=90.6 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=29.1 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=24.6 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=155 ms
64 bytes from 192.168.2.1: icmp_seq=10 ttl=64 time=10.4 ms
64 bytes from 192.168.2.1: icmp_seq=11 ttl=64 time=41.5 ms
64 bytes from 192.168.2.1: icmp_seq=12 ttl=64 time=68.3 ms
64 bytes from 192.168.2.1: icmp_seq=13 ttl=64 time=1.69 ms
64 bytes from 192.168.2.1: icmp_seq=14 ttl=64 time=31.1 ms
64 bytes from 192.168.2.1: icmp_seq=15 ttl=64 time=239 ms
64 bytes from 192.168.2.1: icmp_seq=16 ttl=64 time=2.14 ms
64 bytes from 192.168.2.1: icmp_seq=17 ttl=64 time=144 ms
64 bytes from 192.168.2.1: icmp_seq=18 ttl=64 time=1.73 ms
64 bytes from 192.168.2.1: icmp_seq=19 ttl=64 time=211 ms
64 bytes from 192.168.2.1: icmp_seq=20 ttl=64 time=23.2 ms
64 bytes from 192.168.2.1: icmp_seq=21 ttl=64 time=184 ms

--- 192.168.2.1 ping statistics ---
22 packets transmitted, 21 received, 4% packet loss, time 21083ms
rtt min/avg/max/mdev = 1.698/82.489/312.745/88.698 ms
kevin@kevin-laptop:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=3.32 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=0.938 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=0.920 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=0.923 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=0.961 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=0.986 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=0.972 ms

---

### Post by Moldy Jello on 2006-06-19
ok, i did that and then when the file opened up, then there was nothing there, just and empty file, so what happened? how do i get stuff to show up there? or is it supposed to be empty like that?

---

### Post by iitywygms on 2006-06-20
reinstall ubuntu
used ndiswrapper
now i have this great connection

kevin@laptop:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=3.84 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=4.53 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=1.56 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=1.94 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=1.53 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=1.47 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=2.25 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=1.50 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=1.49 ms
64 bytes from 192.168.2.1: icmp_seq=10 ttl=64 time=1.48 ms

--- 192.168.2.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9037ms
rtt min/avg/max/mdev = 1.471/2.163/4.539/1.055 ms
kevin@laptop:~$

why?????????????????????

---

