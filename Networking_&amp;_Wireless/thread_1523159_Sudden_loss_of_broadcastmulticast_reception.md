---
title: "Sudden loss of broadcast/multicast reception"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by philwhineray on 2010-07-03
Having worked for the past 18 or 19 days solid my 10.04 laptop using ath9k wireless suddenly doesn't appear to be seeing broadcast or multicast packets any longer. Nothing obvious has changed - I went to bed with things working and when I got up this morning they weren't. Any idea what could be the cause? This is driving me crazy!

Symptoms are twofold:
 - ping to broadcast IPv4 address elicits no response from the machine
 - ipv6 stops working because the router gets no responses to Neighbor Solicitation mulitcasts

It may be that the two started at different times; I noticed the problem because of IPv6 connectivity loss. It happened once before and I have only ever checked IPv4 broadcast problems after noticing IPv6 was broken. I can re-instate IPv6 connectivity without fixing multicast by setting a permanent value in the neighbor table on the router and a static default route on the laptop.

On the laptop:

lspci | grep -i net
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 0c:60:76:3a:5d:eb  
          inet addr:81.187.93.67  Bcast:81.187.93.79  Mask:255.255.255.240
          inet6 addr: 2001:8b0:cafb::3/64 Scope:Global
          inet6 addr: fe80::e60:76ff:fe3a:5deb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10537698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8769889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10984450459 (10.9 GB)  TX bytes:3780282342 (3.7 GB)

On router:ping 81.187.93.67
PING 81.187.93.67 (81.187.93.67): 56 data bytes
64 bytes from 81.187.93.67: seq=0 ttl=64 time=1.775 ms
64 bytes from 81.187.93.67: seq=1 ttl=64 time=1.662 ms

Meantime on laptop: sudo tcpdump -n -iwlan0 icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
11:39:53.971798 IP 81.187.93.65 > 81.187.93.67: ICMP echo request, id 4735, seq 0, length 64
11:39:53.971841 IP 81.187.93.67 > 81.187.93.65: ICMP echo reply, id 4735, seq 0, length 64
11:39:54.972076 IP 81.187.93.65 > 81.187.93.67: ICMP echo request, id 4735, seq 1, length 64
11:39:54.972112 IP 81.187.93.67 > 81.187.93.65: ICMP echo reply, id 4735, seq 1, length 64

On router (note the other host responding to the packets): ping 81.187.93.79
PING 81.187.93.79 (81.187.93.79): 56 data bytes
64 bytes from 81.187.93.66: seq=0 ttl=64 time=0.512 ms
64 bytes from 81.187.93.66: seq=1 ttl=64 time=0.372 ms

tcpdump on the laptop sees no further packets.

Outgoing ARP requests seem OK:
sudo tcpdump -n -iwlan0 arp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
11:44:50.454385 ARP, Request who-has 81.187.93.65 tell 81.187.93.67, length 28
11:44:50.455835 ARP, Reply 81.187.93.65 is-at 00:23:cd:19:10:a8, length 28
11:45:13.263135 ARP, Request who-has 81.187.93.66 tell 81.187.93.67, length 28
11:45:13.264636 ARP, Reply 81.187.93.66 is-at 00:16:cb:a2:32:45, length 46

But the machine does not see ARP requests from any other source.

---

