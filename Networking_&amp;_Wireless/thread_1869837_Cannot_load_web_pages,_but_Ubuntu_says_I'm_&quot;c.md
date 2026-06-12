---
title: "Cannot load web pages, but Ubuntu says I'm &quot;connected&quot;"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by liste on 2011-10-26
Hello!

I have had this problem on Ubuntu  11.04 on a laptop before, but when I did I just re-installed.  Now I'm having the same problem on Xubuntu 11.10 on a desktop computer.  I googled extensively both times, but have had no success.

I can "connect" to the router using the connection button at the top right, but I am not connected to the internet.  When I attempt to open my router's home page (192.168.0.1), I just get a connection error.  In fact, I cannot even ping it, despite Xubuntu saying that I have successfully connected to my router.

I'm not sure what information would be useful.  Here's the output from ifconfig, everything looks normal I think:

eth0      Link encap:Ethernet  HWaddr 08:00:27:49:b5:87  
          inet6 addr: fe80::a00:27ff:fe49:b587/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5369 (5.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5057 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:387647 (387.6 KB)  TX bytes:387647 (387.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:58:9b:f3:3e  
          inet addr:192.168.0.72  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:58ff:fe9b:f33e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1760 (1.7 KB)  TX bytes:8884 (8.8 KB)

And the output from iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:B0:CA:6E:C3   
          Bit Rate=104 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

Any help would be appreciated, because I don't want to re-install Xubuntu and all my programs.  Thank you!

---

### Post by jonobr on 2011-10-26
Can you ping 192.168.0.72

Can you set up another machine on the same network using dhcp and see if you can ping that also?

Did you try releasing and renewing IP addresses to see if it acquires an ip address correctly?


WAG.. which Im sure you checked but worth a mention.
You sure the ip address of the router is 192.168.0.1 and not something different?
Other devices use things like 192.168.1.1 (linksys Dlink)
192.168.1.254 (2 wire).
I get the feeling if your using dhcp the gate is 192.168.0 but the last octet, did you try 254?

---

### Post by liste on 2011-10-27
Thank you for the reply, and sorry for the delay in writing back.  By the time I got your reply, Xubuntu was connecting correctly.  It has stopped functioning again, so here are the answers:

Ping 192.168.0.72 from itself (xubuntu):

64 bytes from 192.168.0.72: icmp_req=1 ttl=64 time=0.120 ms
64 bytes from 192.168.0.72: icmp_req=2 ttl=64 time=0.039 ms
64 bytes from 192.168.0.72: icmp_req=3 ttl=64 time=0.035 ms
64 bytes from 192.168.0.72: icmp_req=4 ttl=64 time=0.033 ms
64 bytes from 192.168.0.72: icmp_req=5 ttl=64 time=0.044 ms
64 bytes from 192.168.0.72: icmp_req=6 ttl=64 time=0.067 ms
64 bytes from 192.168.0.72: icmp_req=7 ttl=64 time=0.040 ms
64 bytes from 192.168.0.72: icmp_req=8 ttl=64 time=0.126 ms
64 bytes from 192.168.0.72: icmp_req=9 ttl=64 time=0.047 ms
64 bytes from 192.168.0.72: icmp_req=10 ttl=64 time=0.095 ms
64 bytes from 192.168.0.72: icmp_req=11 ttl=64 time=0.055 ms
64 bytes from 192.168.0.72: icmp_req=12 ttl=64 time=0.058 ms
64 bytes from 192.168.0.72: icmp_req=13 ttl=64 time=0.041 ms
64 bytes from 192.168.0.72: icmp_req=14 ttl=64 time=0.061 ms
64 bytes from 192.168.0.72: icmp_req=15 ttl=64 time=0.033 ms
64 bytes from 192.168.0.72: icmp_req=16 ttl=64 time=0.039 ms
64 bytes from 192.168.0.72: icmp_req=17 ttl=64 time=0.078 ms
^C
--- 192.168.0.72 ping statistics ---
17 packets transmitted, 17 received, 0% packet loss, time 15997ms
rtt min/avg/max/mdev = 0.033/0.059/0.126/0.029 ms

*I pressed Ctrl+C (^C) because it seems to be in an infinite loop. Here's what happens when I ping from another machine in the same network:

ping 192.168.0.72
PING 192.168.0.72 (192.168.0.72) 56(84) bytes of data.
From 192.168.0.110 icmp_seq=9 Destination Host Unreachable
From 192.168.0.110 icmp_seq=10 Destination Host Unreachable
From 192.168.0.110 icmp_seq=11 Destination Host Unreachable
From 192.168.0.110 icmp_seq=12 Destination Host Unreachable
From 192.168.0.110 icmp_seq=13 Destination Host Unreachable
From 192.168.0.110 icmp_seq=14 Destination Host Unreachable
From 192.168.0.110 icmp_seq=15 Destination Host Unreachable
From 192.168.0.110 icmp_seq=16 Destination Host Unreachable
From 192.168.0.110 icmp_seq=17 Destination Host Unreachable
From 192.168.0.110 icmp_seq=18 Destination Host Unreachable
From 192.168.0.110 icmp_seq=19 Destination Host Unreachable
From 192.168.0.110 icmp_seq=20 Destination Host Unreachable
From 192.168.0.110 icmp_seq=21 Destination Host Unreachable
From 192.168.0.110 icmp_seq=22 Destination Host Unreachable
From 192.168.0.110 icmp_seq=23 Destination Host Unreachable
^C
--- 192.168.0.72 ping statistics ---
24 packets transmitted, 0 received, +15 errors, 100% packet loss, time 23155ms
pipe 3

Again, I pressed Ctrl+C to stop the apparent infinite loop.

Yes, I'm positive it's 192.168.0.1 (my router's IP address), but thanks for asking.  I could have missed something that simple by mistake.  I've actually assigned static IPs to the majority of the computers in the network.  My Xubuntu is at 192.168.0.72.  The router is set, though, to send dynamic IPs starting at 192.168.0.100.

---

### Post by jonobr on 2011-10-27
If you can ping itself locally and you cant ping from another machine, its sounds as if the ip address is on the interface and configured correctly but it just aint connected.
If this were a wired issue I would be looking at replacing your cat5 wire or the maybe have a faulty router port.

But given this is wireless.....
I would reckon if you set the machine to static, most likely its not working or getting an IP address.

Not sure where you can go here, but try doing a dmesg | grep wlan and see if that throughs up anything of interest

---

### Post by liste on 2011-10-28
Sorry for the delay again.  It keeps working and then stopping and then working, etc.  Here are the results from "dmesg | grep wlan" while it is not working:

dmesg | grep wlan
[   61.762648] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  138.296516] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  330.237500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  341.369229] wlan0: authenticate with 00:22:b0:ca:6e:c3 (try 1)
[  341.372499] wlan0: authenticated
[  341.373329] wlan0: associate with 00:22:b0:ca:6e:c3 (try 1)
[  341.378840] wlan0: RX AssocResp from 00:22:b0:ca:6e:c3 (capab=0x431 status=0 aid=2)
[  341.378844] wlan0: associated
[  341.997532] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  344.384284] wlan0: deauthenticated from 00:22:b0:ca:6e:c3 (Reason: 2)
[  350.180269] wlan0: authenticate with 00:22:b0:ca:6e:c3 (try 1)
[  350.206184] wlan0: authenticated
[  350.320349] wlan0: associate with 00:22:b0:ca:6e:c3 (try 1)
[  350.324581] wlan0: RX ReassocResp from 00:22:b0:ca:6e:c3 (capab=0x431 status=0 aid=2)
[  350.324585] wlan0: associated
[  355.578062] wlan0: deauthenticated from 00:22:b0:ca:6e:c3 (Reason: 6)
[  361.342159] wlan0: authenticate with 00:22:b0:ca:6e:c3 (try 1)
[  361.346229] wlan0: authenticated
[  361.462702] wlan0: associate with 00:22:b0:ca:6e:c3 (try 1)
[  361.468016] wlan0: RX ReassocResp from 00:22:b0:ca:6e:c3 (capab=0x431 status=0 aid=2)
[  361.468096] wlan0: associated
[  363.312114] wlan0: no IPv6 routers present

Is there anything of interest there?  I can see it's not normal, but I'm mostly lost at this point.

---

