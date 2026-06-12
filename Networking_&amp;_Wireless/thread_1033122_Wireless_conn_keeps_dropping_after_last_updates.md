---
title: "Wireless conn keeps dropping after last updates"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by neeldas on 2009-01-07
I am seeing my wireless connection drop off very often: within 1 minute of use, and I would greatly appreciate some help from the experts.


Here's one sequence of pings that I could see:
....
....
64 bytes from 192.168.31.10: icmp_seq=47 ttl=64 time=0.895 ms
64 bytes from 192.168.31.10: icmp_seq=48 ttl=64 time=0.738 ms
64 bytes from 192.168.31.10: icmp_seq=49 ttl=64 time=0.721 ms
64 bytes from 192.168.31.10: icmp_seq=50 ttl=64 time=0.716 ms
From 192.168.31.12 icmp_seq=84 Destination Host Unreachable
From 192.168.31.12 icmp_seq=85 Destination Host Unreachable
From 192.168.31.12 icmp_seq=86 Destination Host Unreachable
....
....
If I right-click -> UNCHECK enable_wireless on the wireless network connection icon, then CHECk the same box, the wireless connection comes alive again...until the next minute or so!
....
....
From 192.168.31.12 icmp_seq=267 Destination Host Unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
64 bytes from 192.168.31.10: icmp_seq=281 ttl=64 time=6.16 ms
64 bytes from 192.168.31.10: icmp_seq=282 ttl=64 time=0.663 ms
64 bytes from 192.168.31.10: icmp_seq=283 ttl=64 time=0.731 ms
....
....
Here's the config:
neel@omega:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:C9:1E:3C
                    ESSID:"tez tarrar"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/100  Signal level:-71 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000c484ca180
                    Extra: Last beacon: 104ms ago

Help please!!
-Neel

---

### Post by Yashiro on 2009-01-07
What hardware/manufacturer/model number is your wireless adapter?
Which version of Ubuntu?

---

### Post by Yashiro on 2009-01-07
What hardware/manufacturer/model number is your wireless adapter?
Which version of Ubuntu?

---

### Post by neeldas on 2009-01-15
hello,

the wireless adapter is Broadcom.

The linux version is:
neel@omega:~$ uname -a
Linux omega 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
neel@omega:~$ 


thanks.

---

