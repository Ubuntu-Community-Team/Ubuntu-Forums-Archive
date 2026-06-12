---
title: "nmap can't use."
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by kmojo08 on 2012-11-19
Please help me on Ubuntu Desktop 10.04 : I use command ifconfig but now show IP address of eth because I need to check ip by nmap is error as below. 
Note : eth0 : IP 192.168.1.2
eth1 : IP 172.18.39.2
eth2 : IP 192.168.2.2
root@srvtest:~# ifconfig
eth0 Link encap:Ethernet HWaddr 44:1e:a1:3b:48:ea
inet6 addr: fe80::461e:a1ff:fe3b:48ea/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1648414 errors:0 dropped:0 overruns:0 frame:0
TX packets:1371934 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:921755168 (921.7 MB) TX bytes:220989068 (220.9 MB)
Memory:fbce0000-fbd00000
eth1 Link encap:Ethernet HWaddr 44:1e:a1:3b:48:eb
inet6 addr: fe80::461e:a1ff:fe3b:48eb/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1268297 errors:0 dropped:0 overruns:0 frame:0
TX packets:1519550 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:150440167 (150.4 MB) TX bytes:833127890 (833.1 MB)
Memory:fbde0000-fbe00000
eth2 Link encap:Ethernet HWaddr 2c:27:d7:14:10:8c
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Memory:fbfe0000-fc000000
root@srvtest:~# nmap -sP 172.18.39.0/24
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2012-11-19 21:43 ICT
Failed to lookup subnet/netmask for device (eth1): eth1: no IPv4 address assigned
QUITTING!
 
I had to try with other Server is srvthai2 as below and this server show ip address and I can use nmap normally So I need to know what is I mistake or can be solve on server srvtest please help and let me know for sovled.
root@srvthai2:~# ifconfig
eth0 Link encap:Ethernet HWaddr 00:25:b3:99:72:df
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::225:b3ff:fe99:72df/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:89018193 errors:0 dropped:0 overruns:0 frame:0
TX packets:72161729 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1842679283 (1.8 GB) TX bytes:3097831410 (3.0 GB)
Interrupt:17
eth1 Link encap:Ethernet HWaddr 00:23:7d:fd:95:07
inet addr:172.18.35.2 Bcast:172.18.255.255 Mask:255.255.0.0
inet6 addr: fe80::223:7dff:fefd:9507/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:178772056 errors:0 dropped:0 overruns:0 frame:0
TX packets:206021075 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:1716830687 (1.7 GB) TX bytes:877550671 (877.5 MB)
Memory:ec120000-ec140000
eth2 Link encap:Ethernet HWaddr 00:23:7d:fd:95:0a
inet addr:192.168.2.2 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::223:7dff:fefd:950a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5569847 errors:0 dropped:0 overruns:0 frame:0
TX packets:4977658 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:399104531 (399.1 MB) TX bytes:1086841521 (1.0 GB)
Memory:ec220000-ec240000
root@srvthai2:~# nmap -sP 172.18.35.0/24
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2012-11-19 22:12 ICT
Host 172.18.35.2 is up.
Host 172.18.35.4 is up (0.00073s latency).
MAC Address: 14:D6:4D:DF:AF:00 (Unknown)
Host 172.18.35.12 is up (0.0012s latency).
MAC Address: 00:04:F2:35:48:11 (Polycom)
Host 172.18.35.13 is up (0.0012s latency).
MAC Address: 1C:7E:E5:89:28:46 (Unknown)
Host 172.18.35.14 is up (0.0011s latency).
MAC Address: 00:15:65:32:89:AC (Xiamen Yealink Network Technology Co.)
Host 172.18.35.15 is up (0.0016s latency).
MAC Address: 00:15:65:32:94:E0 (Xiamen Yealink Network Technology Co.)
Host 172.18.35.16 is up (0.00061s latency).
MAC Address: 00:15:65:32:8C:AE (Xiamen Yealink Network Technology Co.)
Host 172.18.35.250 is up (0.00066s latency).
MAC Address: 00:17:61:10:93:4B (ZKSoftware)
Nmap done: 256 IP addresses (8 hosts up) scanned in 2.35 seconds
root@srvthai2:~#
 
Thank you for you help and support.
:Pkmojo:P

---

