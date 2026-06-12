---
title: "network connection outgoing not working on  11.10"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by spindler on 2011-11-11
I have recently installed ubuntu 11.10 and I am having some issues with the network connectivity.

The Problem:  Using the ubuntu computer I cannot access the internet using firefox.  I am using the machine as a webserver and the website software is unable to do automatic updates. 

TEST I have done......................... 

1.  Using a different computer on the network or from a coffee shop, I am able to access the websites on my Ubuntu machine so I know the inbound communication works.  

2   Using the webserver, I CAN ping other websites outside of my network and I can ping computers within my network.  So I know I have a basic level of communication from the Ubuntu webserver to other computers. 


3.  From my Ubuntu webserver, using firefox,  I am attempting to access several websites outside of my network. I cannot access google or any outside websites.   I also cannot get updates using my website automatic update tools. 

_I am not sure why I have limited connectivity.   It appears as if something might be wrong with the TCP/IP since outgoing requests for webpages does not appear to work._

I have a router setup with TCP and UDP port 80 open for my Ubuntu machine.
 

**Any Idea what might be happening here? **
......

.......
Here is some information on my network config.

Hardware:   NetXtreme BCM5721 Gigabit Ethernet PCI Express ( Broadcom)

IFCONFIG:

eth0      Link encap:Ethernet  HWaddr 00:15:c5:5e:ee:d8  
          inet addr:192.168.1.186  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe5e:eed8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4452349 (4.4 MB)  TX bytes:193891 (193.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5863 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34962503 (34.9 MB)  TX bytes:34962503 (34.9 MB)

INTERFACES:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.185
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.185
gateway 192.168.1.1

RESULTS:

domain yt.northwestel.net
search yt.northwestel.net
nameserver 192.168.1.1


DMESG | GREP ETH0    ( edited to show the last bit)


MAC=00:15:c5:5e:ee:d8:00:1e:58:f1:fb:11:08:00 SRC=192.168.1.1   DST=192.168.1.186 LEN=139 TOS=0x00 PREC=0x00 TTL=64 ID=30637 PROTO=UDP   SPT=53 DPT=32791 LEN=119

---

