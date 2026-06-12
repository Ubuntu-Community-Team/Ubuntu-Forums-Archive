---
title: "Wired internet with proxy address not working"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by anirudh612 on 2009-05-20
Hi. I'm dual booting Kubuntu 9.04 with Windows vista. I'm using a wired internet and my settings for the same are
IP Adress: 10.148.0.142
Subnet Mask: 255.255.254.0
Default getaway: 10.148.1.1 

DNS: 10.10.1.2

Proxy settings

HTTP, HTTPS and FTP: 10.10.3.16
Port: 3128

These settings run perfectly fine on Windows vista and that is where I'm using internet from. For ubuntu, I made a new connection in Wired and filled these settings in the corresponding boxes and filled the MAC address as the one given by 'ifconfig eth0'. But still, the internet isn't working in kubuntu. 

ifconfig eth0 shows
Link encap:Ethernet  HWaddr 00:1a:80:7c:4b:63
          inet6 addr: fe80::21a:80ff:fe7c:4b63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31817 (31.8 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:251 Base address:0xa000

When I ping google, or any other address, it says 'Connect: Network Unreachable'

Please tell my how can I run internet on my Kubuntu


[IMG]http://kubuntuforums.net/forums/Themes/classic/images/icons/modify_inline.gif[/IMG]

---

