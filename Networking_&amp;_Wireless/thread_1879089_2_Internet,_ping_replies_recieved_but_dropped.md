---
title: "2 Internet, ping replies recieved but dropped?"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by ebolam on 2011-11-10
**Overview:**
I have a three network interfaces on my system PPP0 (Internet), PPP1 (Internet) and eth0 (local network). I have two routing tables setup, the main routing table with a default route through PPP0 and a secondary routing table with a default route through PPP1. I have ip tables setup to mark specific destinations/sources/mac addresses. Those marked packets go through the secondary routing table. 
 
When I ping a host from the local machine (that host is set to mark in ip tables), I see the traffic exit and return through PPP1 using tcpdump with the correct source and destinations for PPP1. However ping shows all of the packets are lost. If I remove the marking rules, I see the ping exiting and returning through PPP0 and get responses.
 
 
**A bit more detail:**
Here's a bit more information about my setup. The system is setup as my home network's router/firewall. I have two physical connections (eth0 and eth1). Eth0 servies the local network. Eth1 is connected to a dsl modem. PPP0 is the DSL connection to the internet. 
 
I recently moved to Australia from the USA, and am still enjoying netflix and hulu streaming thanks to a VPN service I subscribe to. I am trying to make some of the VPN stuff centralized on the router, so that I can use the wii and ps3 through the vpn and for other things. I am able to successfully connect to a PPTP VPN server (their PPTP is much faster than OpenVPN, and I don't really care about the encryption), creating PPP1. 
 
I am able to ping normally through PPP0. I can ping normally through PPP1 to the remote side of the tunnel. I can Ping through the PPP1 tunnel to a remote host and see proper responses through tcpdump, but the ping shows 100% losses.
 
**Nitty Gritty Logs and such:**
Ok, here's the setup in detail, including logs and what not.
 
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:25:22:83:1e:54  
          inet addr:172.16.0.11  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fe83:1e54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34411441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20477113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22719154084 (22.7 GB)  TX bytes:43714298169 (43.7 GB)
          Interrupt:41 Base address:0x6000 
 
eth1      Link encap:Ethernet  HWaddr 00:e0:4c:77:29:e3  
          inet6 addr: fe80::2e0:4cff:fe77:29e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2472126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1645140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2101869696 (2.1 GB)  TX bytes:247813504 (247.8 MB)
          Interrupt:19 Base address:0xac00 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6412201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6412201 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35199874669 (35.1 GB)  TX bytes:35199874669 (35.1 GB)
 
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:124.170.116.52  P-t-P:203.215.9.250  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:581247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:531276137 (531.2 MB)  TX bytes:74382850 (74.3 MB)
 
ppp1      Link encap:Point-to-Point Protocol  
          inet addr:174.140.161.121  P-t-P:174.140.161.66  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2807 (2.8 KB)  TX bytes:402 (402.0 B)
 
virbr0    Link encap:Ethernet  HWaddr 96:df:4b:4c:ae:80  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:455303 (455.3 KB)
 

```
 
Here's my IP Routes:
```
**> ip route show**
203.215.9.250 dev ppp0  proto kernel  scope link  src 124.170.116.52 
174.140.161.66 dev ppp1  proto kernel  scope link  src 174.140.161.121 
174.140.161.2 dev ppp0  scope link  src 124.170.116.52 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 
172.16.0.0/24 dev eth0  proto kernel  scope link  src 172.16.0.11 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default dev ppp0  scope link 
 
**> ip route show table HMA**
203.215.9.250 dev ppp0  proto kernel  scope link  src 124.170.116.52 
174.140.161.66 dev ppp1  proto kernel  scope link  src 174.140.161.121 
174.140.161.2 dev ppp0  scope link  src 124.170.116.52 
172.16.0.0/24 dev eth0  proto kernel  scope link  src 172.16.0.11 
192.168.122.0/24 dev virbr0  proto kernel  scope link  src 192.168.122.1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 174.140.161.66 dev ppp1 

```
 
Here's the ip rules:
```
**> ip rule show**
0:    from all lookup local 
32764:    from all iif ppp1 lookup HMA 
32765:    from all fwmark 0x1 lookup HMA 
32766:    from all lookup main 
32767:    from all lookup default 

```
 
Here's my IP Tables:
```
**> iptables -nvL**
Chain INPUT (policy DROP 100 packets, 7489 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 504K 2307M ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
32230 3149K ACCEPT     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
14282 3715K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8022 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:49160:49300 
   47  2240 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    3   180 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:1723 
    0     0 ACCEPT     47   --  ppp0   *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 
    0     0 ACCEPT     tcp  --  ppp0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8080 
 
Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 1626  209K ACCEPT     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
 1968  707K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 
Chain OUTPUT (policy ACCEPT 548K packets, 2328M bytes)
 pkts bytes target     prot opt in     out     source               destination         
 
**> iptables -t mangle -nvL**
Chain PREROUTING (policy ACCEPT 181K packets, 448M bytes)
 pkts bytes target     prot opt in     out     source               destination         
 550K 2315M CONNMARK   all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED CONNMARK restore 
    0     0 MARK       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MAC E0:B9:A5:2B:E1:7E MARK set 0x2 
   17  1428 HMA        all  --  *      *       203.206.129.11       0.0.0.0/0             
    0     0 HMA        all  --  *      *       0.0.0.0/0            203.206.129.11       
 
Chain INPUT (policy ACCEPT 178K packets, 448M bytes)
 pkts bytes target     prot opt in     out     source               destination         
 
Chain FORWARD (policy ACCEPT 2561 packets, 638K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 
Chain OUTPUT (policy ACCEPT 176K packets, 459M bytes)
 pkts bytes target     prot opt in     out     source               destination             
    4   336 HMA        all  --  *      *       0.0.0.0/0            203.206.129.11      
 
 
Chain POSTROUTING (policy ACCEPT 179K packets, 459M bytes)
 pkts bytes target     prot opt in     out     source               destination         
 
Chain HMA (37 references)
 pkts bytes target     prot opt in     out     source               destination         
   39  3180 MARK       all  --  *      *       0.0.0.0/0            0.0.0.0/0           MARK set 0x1 
   39  3180 CONNMARK   all  --  *      *       0.0.0.0/0            0.0.0.0/0           CONNMARK save 
 
**> iptables -t nat -nvL**
Chain PREROUTING (policy ACCEPT 520 packets, 41137 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 
Chain INPUT (policy ACCEPT 159 packets, 18208 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 
Chain OUTPUT (policy ACCEPT 5442 packets, 339K bytes)
 pkts bytes target     prot opt in     out     source               destination         
 
Chain POSTROUTING (policy ACCEPT 5397 packets, 336K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  206 16950 MASQUERADE  all  --  *      ppp0    0.0.0.0/0            0.0.0.0/0           
    7   492 MASQUERADE  all  --  *      ppp1    0.0.0.0/0            0.0.0.0/0           
  
```
 
I've also disabled rp_filter:
```
**> cat /proc/sys/net/ipv4/conf/ppp1/rp_filter**
0

```
 
 
Here's an example Ping (while running tcpdump):
```
**> ping -c 4 203.206.129.11**
PING 203.206.129.11 (203.206.129.11) 56(84) bytes of data.
 
--- 203.206.129.11 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3000ms

```
 
Here's the tcpdump run while pinging:
```
**>tcpdump -n host 203.206.129.11 -i ppp1**
14:06:24.185823 IP 174.140.161.121 > 203.206.129.11: ICMP echo request, id 23848
, seq 1, length 64                                                              
14:06:25.186518 IP 174.140.161.121 > 203.206.129.11: ICMP echo request, id 23848
, seq 2, length 64                                                              
14:06:26.186381 IP 174.140.161.121 > 203.206.129.11: ICMP echo request, id 23848
, seq 3, length 64                                                              
14:06:26.316401 IP 203.206.129.11 > 174.140.161.121: ICMP echo reply, id 23848, 
seq 1, length 64                                                                
14:06:26.316411 IP 203.206.129.11 > 174.140.161.121: ICMP echo reply, id 23848, 
seq 2, length 64                                                                
14:06:26.586383 IP 203.206.129.11 > 174.140.161.121: ICMP echo reply, id 23848, 
seq 3, length 64                                                                
14:06:27.186417 IP 174.140.161.121 > 203.206.129.11: ICMP echo request, id 23848
, seq 4, length 64                                                              
14:06:27.586395 IP 203.206.129.11 > 174.140.161.121: ICMP echo reply, id 23848, 
seq 4, length 64

```
 
If I have log_martians enabled, I do see martian packets (example from dmesg):
```
[528218.580153] martian source 124.170.116.52 from 203.206.129.11, on dev ppp1  
[528218.580159] ll header: 45:00:00:54                                          
[528219.101332] martian source 124.170.116.52 from 203.206.129.11, on dev ppp1  
[528219.101337] ll header: 45:00:00:54                                          
[528220.110155] martian source 124.170.116.52 from 203.206.129.11, on dev ppp1  
[528220.110160] ll header: 45:00:00:54                                          

```
 
I cannot for the life of me figure out why this doesn't work. Everything I've read says it should, and everything I'm seeing says it should (even the martian packet destination is the same as one of my interfaces).
 
Any help would be appreciated.

---

### Post by ebolam on 2011-11-14
bump.
 
No one has any suggestions on things to try? No one can give hints on what might cause a ping reply to be dropped?

---

