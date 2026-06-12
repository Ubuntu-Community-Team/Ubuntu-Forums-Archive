---
title: "wlan0 is dropping packets after unpluging AC power MSI U100"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by bbrowaros on 2011-05-26
Hi, 

Just have upgraded the ubuntu from 10.10 to 11.04 on MSI Wind (U100). Just notice issue with wlan0 port. When the AC power is plugged in the wlan is working normally no delays on ECHO ICMP requests low packet lost: ```

PING 192.168.1.109 (192.168.1.109): 56 data bytes
64 bytes from 192.168.1.109: seq=0 ttl=64 time=5.881 ms
64 bytes from 192.168.1.109: seq=1 ttl=64 time=5.165 ms
64 bytes from 192.168.1.109: seq=2 ttl=64 time=2.097 ms
64 bytes from 192.168.1.109: seq=3 ttl=64 time=1.708 ms
64 bytes from 192.168.1.109: seq=4 ttl=64 time=1.717 ms
64 bytes from 192.168.1.109: seq=5 ttl=64 time=1.848 ms
64 bytes from 192.168.1.109: seq=6 ttl=64 time=1.795 ms
64 bytes from 192.168.1.109: seq=7 ttl=64 time=1.745 ms
64 bytes from 192.168.1.109: seq=8 ttl=64 time=2.078 ms
64 bytes from 192.168.1.109: seq=9 ttl=64 time=2.150 ms
64 bytes from 192.168.1.109: seq=10 ttl=64 time=2.053 ms
64 bytes from 192.168.1.109: seq=11 ttl=64 time=5.342 ms
64 bytes from 192.168.1.109: seq=13 ttl=64 time=1.589 ms
64 bytes from 192.168.1.109: seq=14 ttl=64 time=1.732 ms
64 bytes from 192.168.1.109: seq=15 ttl=64 time=1.974 ms
64 bytes from 192.168.1.109: seq=16 ttl=64 time=1.801 ms
64 bytes from 192.168.1.109: seq=17 ttl=64 time=2.401 ms
64 bytes from 192.168.1.109: seq=18 ttl=64 time=1.711 ms
64 bytes from 192.168.1.109: seq=19 ttl=64 time=1.710 ms
64 bytes from 192.168.1.109: seq=20 ttl=64 time=1.928 ms
64 bytes from 192.168.1.109: seq=21 ttl=64 time=2.036 ms
64 bytes from 192.168.1.109: seq=22 ttl=64 time=1.762 ms
64 bytes from 192.168.1.109: seq=23 ttl=64 time=1.933 ms
64 bytes from 192.168.1.109: seq=24 ttl=64 time=2.330 ms
64 bytes from 192.168.1.109: seq=26 ttl=64 time=2.016 ms
64 bytes from 192.168.1.109: seq=27 ttl=64 time=2.230 ms
64 bytes from 192.168.1.109: seq=28 ttl=64 time=1.594 ms
64 bytes from 192.168.1.109: seq=29 ttl=64 time=2.342 ms
64 bytes from 192.168.1.109: seq=30 ttl=64 time=1.681 ms
64 bytes from 192.168.1.109: seq=31 ttl=64 time=1.791 ms
64 bytes from 192.168.1.109: seq=32 ttl=64 time=3.188 ms
^C
--- 192.168.1.109 ping statistics ---
33 packets transmitted, 31 packets received, 6% packet loss
round-trip min/avg/max = 1.589/2.300/5.881 ms
```after unpluging the AC power the responce time and packet lost are increasing: 
```
PING 192.168.1.109 (192.168.1.109): 56 data bytes
64 bytes from 192.168.1.109: seq=2 ttl=64 time=75.573 ms
64 bytes from 192.168.1.109: seq=4 ttl=64 time=119.527 ms
64 bytes from 192.168.1.109: seq=6 ttl=64 time=1064.895 ms
64 bytes from 192.168.1.109: seq=7 ttl=64 time=64.502 ms
64 bytes from 192.168.1.109: seq=9 ttl=64 time=135.199 ms
64 bytes from 192.168.1.109: seq=11 ttl=64 time=78.182 ms
64 bytes from 192.168.1.109: seq=13 ttl=64 time=124.175 ms
64 bytes from 192.168.1.109: seq=15 ttl=64 time=70.201 ms
64 bytes from 192.168.1.109: seq=17 ttl=64 time=115.503 ms
64 bytes from 192.168.1.109: seq=19 ttl=64 time=157.417 ms
64 bytes from 192.168.1.109: seq=21 ttl=64 time=101.789 ms
64 bytes from 192.168.1.109: seq=23 ttl=64 time=148.583 ms
64 bytes from 192.168.1.109: seq=25 ttl=64 time=93.276 ms
64 bytes from 192.168.1.109: seq=27 ttl=64 time=140.335 ms
64 bytes from 192.168.1.109: seq=29 ttl=64 time=84.165 ms
64 bytes from 192.168.1.109: seq=31 ttl=64 time=131.039 ms
64 bytes from 192.168.1.109: seq=33 ttl=64 time=75.559 ms
64 bytes from 192.168.1.109: seq=35 ttl=64 time=127.801 ms
64 bytes from 192.168.1.109: seq=37 ttl=64 time=67.134 ms
64 bytes from 192.168.1.109: seq=41 ttl=64 time=57.773 ms
^C
--- 192.168.1.109 ping statistics ---
43 packets transmitted, 20 packets received, 53% packet loss
round-trip min/avg/max = 57.773/151.631/1064.895 ms


```ping outputs are from openwrt installed on my router. 

This was not visible on 10.10 or I did not notice that. 
Anyone notice the same or can help me with this problem? 

Thanks in advance. 
Peter

P.S. just to add stopping gnome-power-manager does not change the situation.

Just to add more This issue is visible only on kernel 2.6.38 when booting form 2.6.35 is ok. The wlan0 is working fine so maybe a new bug :). I will try to check the bugs on ubuntu for 2.6.38 :D

Filled a Bug #795273  for this. We will see what will be the result.

---

