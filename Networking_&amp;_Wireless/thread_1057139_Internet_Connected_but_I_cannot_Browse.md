---
title: "Internet Connected but I cannot Browse"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by Alessandra on 2009-02-01
Hello, 

I have a DELL XPS M1530 CORE 2 DUO T8100 2.10GHz, with Graphics Card 256MB NVIDIA GeForce Go 8600M GT, Wireless Dell 1395 (802.b/g) that I'm currently dual booting with Vista (Home Premium SP1, 32Bit OS) and Ubuntu 8.10.

I'm having trobles with the internet connection on Ubuntu 8.10...

I first connect this laptop in my office without any problems just plugging the cable or selecting the wireless.
I try to do the same at home but, even if the network manager says I am connected, I cannot browse, use skype and any other utilities with interent.
In fact, I plug ethernet cable (directly from the router) in , and I cannot use internet. 
From my lswh -C network output, it appears that my ethernet (eth0) port is enabled, and in my network manager the auto eth0 connected (ubuntu tells me it is connected and displays the signal strength etc.) but Firefox does not work! 
Pinging my network doesn't work...
Eventually, I just got the skype connection....but not the browser! (by the way, when I write in skype the emoticons and the words overlap! I downloaded the recomended Nvidia drivers but without any success!)

The same is with the wireless.

It is the first time I have setup wireless and wired connection on an ubuntu installation and I think I am missing something, since in a place it is working and in another place is not!

I copy here the results of my lswh -C network
(eth0 is my ethernet interface,  eth1 is my wireless interface)

*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:01:43:e9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.18 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4d:c5:5f:2e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.14 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:b6:9b:e5:f9:0c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

The ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:23:ae:01:43:e9  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe01:43e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:731 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:89692 (89.6 KB)  Byte TX:93528 (93.5 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:c5:5f:2e  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fec5:5f2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1630 errors:0 dropped:0 overruns:0 frame:15029
          TX packets:1458 errors:19 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:408038 (408.0 KB)  Byte TX:207455 (207.4 KB)
          Interrupt:17 Indirizzo base:0xc000 

lo        Link encap:Loopback locale  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132342 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:6673956 (6.6 MB)  Byte TX:6673956 (6.6 MB)


Any guidance appreciated!
Thanks!

---

### Post by Jahendo on 2009-02-01
I'm having the same problem, now.  I was connected to the internet just fine wirelessly, last night, then suddenly I couldn't browse, check email, or message on Pidgin.  I can connect to my router, but no internet usage is available.  No updates or anything are allowed to download.  Even when I plug in the wired connection, it says I'm connected, but Firefox can't open a website. 

Help!!

---

### Post by Iowan on 2009-02-01
Alessandra:
I suspect it'll be a problem having eth0 and eth1 in the same subnet. May need to disable the one you aren't using.

---

### Post by Alessandra on 2009-02-06
> **Iowan said:**
> Alessandra:
I suspect it'll be a problem having eth0 and eth1 in the same subnet. May need to disable the one you aren't using.


Thanks! But unfortunately that was the first thing that I tryed,
then i wrote both eth0 and eth1 just to print what I wanted to post here....:(

Every other suggestion would be welcome!:)

Cheers,
Alessandra

---

### Post by superprash2003 on 2009-02-06
post outpt of ping google.com

---

### Post by Alessandra on 2009-02-16
If I ping [www.google.it](www.google.it)
I have:
ping: unknown host google.it
It looks like is not finding the DNS.....
However, I have written all the correct numbers and parameters in the 
/ect/resolv.conf
The fact is that I connect my laptop without any problems when I'm at work (I work in a university and I know the net is different) whereas at home I have a Linksys WRT54GS Wireless Broadband Router.
Do you know any problem with this router?
If I ping the router at the IP address 192.168.1.1 that is the default for Linksys broadband routers i get:

ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.18 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.80 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=3.54 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2010ms
rtt min/avg/max/mdev = 2.808/3.178/3.547/0.305 ms

I tryed also 


iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.


route -n:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0


What do you think about?

---

