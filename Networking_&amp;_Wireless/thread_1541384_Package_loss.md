---
title: "Package loss"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by albelix on 2010-07-29
Hi all,

I am rather new to Ubuntu, and struggle for a few month with slow internet connection in Ubuntu 10.04 (as well as in previous versions) with substantial (20-30%) packages loss:

 My traceroute  [v0.75]                            
albelix-vaio (0.0.0.0)                  Thu Jul 29 11:42:30 2010
Keys:  Help   Display mode   Restart statistics   Order of fields   quit       
                                      Packets               Pings             
 Host                  Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. 10.179.88.1        21.1%  3173    6.7  23.2   0.7 243.0  45.1
 2. 81.88.122.65       21.5%  3172    1.0   0.9   0.8  59.7   1.7
 3. 213.79.103.33      21.1%  3172    1.1   1.0   0.9   3.6   0.1
 4. 62.117.100.73      21.8%  3172    2.4   1.9   1.8  23.1   0.9
 5. 213.248.78.85      21.3%  3172   26.1  29.5  25.9 129.5  12.8
 6. 80.91.248.206      21.2%  3172   26.3  30.8  26.0 202.3  18.4
 7. 80.239.147.166     19.3%  3172   41.2  46.3  41.0 193.4  19.6
 8. 80.91.247.43       21.7%  3172   57.5  60.5  54.9 231.8  16.7
    80.91.254.217                                                        
    80.239.147.181                                                             
    80.91.250.221                                                              
    80.91.245.5                                                                
    80.91.250.149                                                              
    80.91.254.5                                                                
    80.91.249.10                                                               
 9. 80.91.252.206     20.5%  3172   57.6  58.7  54.9 164.1  11.5
    80.91.249.178                                                              
    80.91.247.90                                                               
    80.91.248.216                                                              
    80.91.252.198                                                              
10. 80.91.250.210     20.1%  3172   55.3  57.5  55.0 259.7  17.6
11. 213.248.74.42     20.9%  3172   58.0  92.7  57.7 368.7  57.4
12. 213.133.130.106   20.3%  3172   55.5  55.5  55.3 208.5   6.1
13. 91.189.88.10      21.4%  3172   61.6  61.1  58.0  64.5   0.4
14. 91.189.94.12      19.4%  3172   61.6  61.1  55.6  64.1   0.5
     
Package loss seems to begin somewhere between my provider's address, 10.179.88.1 (top table below), and my own IP, 10.179.88.33 (bottom table below):

albelix@albelix-vaio:~$ ping 10.179.88.1
PING 10.179.88.1 (10.179.88.1) 56(84) bytes of data.
64 bytes from 10.179.88.1: icmp_seq=3 ttl=255 time=0.880 ms
64 bytes from 10.179.88.1: icmp_seq=4 ttl=255 time=1.05 ms
64 bytes from 10.179.88.1: icmp_seq=5 ttl=255 time=0.830 ms
64 bytes from 10.179.88.1: icmp_seq=11 ttl=255 time=0.837 ms
64 bytes from 10.179.88.1: icmp_seq=14 ttl=255 time=8.38 ms
64 bytes from 10.179.88.1: icmp_seq=16 ttl=255 time=6.51 ms
64 bytes from 10.179.88.1: icmp_seq=17 ttl=255 time=0.798 ms
64 bytes from 10.179.88.1: icmp_seq=18 ttl=255 time=0.827 ms
64 bytes from 10.179.88.1: icmp_seq=20 ttl=255 time=1.19 ms
64 bytes from 10.179.88.1: icmp_seq=23 ttl=255 time=0.889 ms
64 bytes from 10.179.88.1: icmp_seq=24 ttl=255 time=0.885 ms
64 bytes from 10.179.88.1: icmp_seq=26 ttl=255 time=0.878 ms
64 bytes from 10.179.88.1: icmp_seq=27 ttl=255 time=1.02 ms
64 bytes from 10.179.88.1: icmp_seq=28 ttl=255 time=0.839 ms
64 bytes from 10.179.88.1: icmp_seq=29 ttl=255 time=0.835 ms
64 bytes from 10.179.88.1: icmp_seq=30 ttl=255 time=0.826 ms
64 bytes from 10.179.88.1: icmp_seq=31 ttl=255 time=0.725 ms
64 bytes from 10.179.88.1: icmp_seq=33 ttl=255 time=0.792 ms
q64 bytes from 10.179.88.1: icmp_seq=34 ttl=255 time=0.806 ms
64 bytes from 10.179.88.1: icmp_seq=35 ttl=255 time=0.832 ms
^X64 bytes from 10.179.88.1: icmp_seq=36 ttl=255 time=0.827 ms
^Z
[1]+  Stopped                 ping 10.179.88.1
albelix@albelix-vaio:~$ ping 10.179.88.33
PING 10.179.88.33 (10.179.88.33) 56(84) bytes of data.
64 bytes from 10.179.88.33: icmp_seq=1 ttl=64 time=0.054 ms
64 bytes from 10.179.88.33: icmp_seq=2 ttl=64 time=0.043 ms
64 bytes from 10.179.88.33: icmp_seq=3 ttl=64 time=0.041 ms
64 bytes from 10.179.88.33: icmp_seq=4 ttl=64 time=0.044 ms
64 bytes from 10.179.88.33: icmp_seq=5 ttl=64 time=0.046 ms
64 bytes from 10.179.88.33: icmp_seq=6 ttl=64 time=0.046 ms
64 bytes from 10.179.88.33: icmp_seq=7 ttl=64 time=0.046 ms
64 bytes from 10.179.88.33: icmp_seq=8 ttl=64 time=0.046 ms
64 bytes from 10.179.88.33: icmp_seq=9 ttl=64 time=0.045 ms
64 bytes from 10.179.88.33: icmp_seq=10 ttl=64 time=0.046 ms
64 bytes from 10.179.88.33: icmp_seq=11 ttl=64 time=0.044 ms
64 bytes from 10.179.88.33: icmp_seq=12 ttl=64 time=0.044 ms
64 bytes from 10.179.88.33: icmp_seq=13 ttl=64 time=0.045 ms
64 bytes from 10.179.88.33: icmp_seq=14 ttl=64 time=0.042 ms
64 bytes from 10.179.88.33: icmp_seq=15 ttl=64 time=0.044 ms
64 bytes from 10.179.88.33: icmp_seq=16 ttl=64 time=0.045 ms
64 bytes from 10.179.88.33: icmp_seq=17 ttl=64 time=0.047 ms
64 bytes from 10.179.88.33: icmp_seq=18 ttl=64 time=0.049 ms
64 bytes from 10.179.88.33: icmp_seq=19 ttl=64 time=0.036 ms
64 bytes from 10.179.88.33: icmp_seq=20 ttl=64 time=0.046 ms
64 bytes from 10.179.88.33: icmp_seq=21 ttl=64 time=0.052 ms
64 bytes from 10.179.88.33: icmp_seq=22 ttl=64 time=0.046 ms
64 bytes from 10.179.88.33: icmp_seq=23 ttl=64 time=0.048 ms
64 bytes from 10.179.88.33: icmp_seq=24 ttl=64 time=0.046 ms
64 bytes from 10.179.88.33: icmp_seq=25 ttl=64 time=0.046 ms
64 bytes from 

but continues afterwards. Also, the route seems to me unduly long. Interestingly, this happens only in one notebook (Sony Vaio) and the same connection - direct, without proxy server. Using the same notebook at a different connection seems to work without problems, and using the same connection from another computer works OK as well. 

I tried to config firestarter by denying the addresses where packages are lost, and also by switching off ipv6 using "alias net-pf-10 off" in /etc/modprobe.conf - both without great success, and basically the same picture. It all looks like I caught some virus where I would not expect any, but my skills are not siffucient to get rid of it, and I failed to find anything direct in the forums. Below is my ifconfig (I use eth0 connection with wicd network manager) - any help is much appreciated.


eth0      Link encap:Ethernet  HWaddr 00:24:be:b4:9c:57  
          inet addr:10.179.88.33  Bcast:10.179.91.255  Mask:255.255.252.0
          inet6 addr: fe80::224:beff:feb4:9c57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3960907 (3.9 MB)  TX bytes:5009978 (5.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:340 (340.0 B)  TX bytes:340 (340.0 B)

---

