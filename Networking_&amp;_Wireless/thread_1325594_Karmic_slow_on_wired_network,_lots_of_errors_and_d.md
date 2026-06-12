---
title: "Karmic slow on wired network, lots of errors and dropped packets"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by Briga on 2009-11-13
Hi, 
my PC worked very well since 7.10 and all the releases after. Since doing a fresh install of 9.10 the network is very slow. First the DNS problem which I may have solved and now I have noticed that it is also very slow on the LAN and on the ping to direct local IPs. An ifconfig showed me lots of errors:

```
briga@ela-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:18:b2:70:02  
          indirizzo inet:192.168.1.2  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::2e0:18ff:feb2:7002/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1480  Metric:1
          RX packets:21422 errors:17693 dropped:8850 overruns:0 frame:2065
          TX packets:13820 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:22642773 (22.6 MB)  Byte TX:2112178 (2.1 MB)
          Interrupt:18 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:14729 (14.7 KB)  Byte TX:14729 (14.7 KB)

```

The metwork card is a Broadcomm and was working flawlessy in previous Ubuntu installs.

```
briga@ela-desktop:~$ sudo lspci
[sudo] password for briga: 
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

I don't spot ant major issue in dmesg
```
briga@ela-desktop:~$ dmesg | grep eth0
[    1.898848] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:e0:18:b2:70:02
[   19.817209] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.816173] b44: eth0: Link is up at 100 Mbps, full duplex.
[   22.816181] b44: eth0: Flow control is off for TX and off for RX.
[   22.816315] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   33.804060] eth0: no IPv6 routers present
```

I switch from DHCP to static IP and DNS seems fine. Bur even pinging my CAT6 connected router has packet loss:
```
briga@ela-desktop:~$ ping 192.168.1.1 
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=1.10 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.674 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.673 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.680 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.647 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.650 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.638 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.620 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.634 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=0.895 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=0.645 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=0.649 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=0.629 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=255 time=0.652 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=255 time=0.666 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=255 time=0.614 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=255 time=0.694 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=255 time=0.697 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=255 time=0.681 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=255 time=0.676 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=255 time=0.683 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=255 time=0.687 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=255 time=0.620 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=255 time=0.610 ms
^C
--- 192.168.1.1 ping statistics ---
26 packets transmitted, 24 received, 7% packet loss, time 25029ms
rtt min/avg/max/mdev = 0.610/0.684/1.103/0.103 ms

```

though the interface seems to be up and running at full speed. 

```
briga@ela-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 01
       serial: 00:e0:18:b2:70:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.2 latency=32 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:ed800000-ed801fff memory:efef0000-efef3fff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

Anyone can help me?

Thanks
Briga

---

### Post by Yoann Juet on 2009-11-14
>  RX packets:21422 errors:17693 dropped:8850 overruns:0 frame:2065

Have you tried to replace your cat6 cable ?

> Bur even pinging my CAT6 connected router has packet loss:

Has your router TX errors and dropped packets (if your PC is directly connected to your router, it should be symmetrical)?

---

### Post by Briga on 2009-11-14
Thanks for the reply Yoann.

Yes I did try a different port on the router and a different cable with no luck. 

Now there are some interesting facts. The router shows no errors:
```
Transmit 
Good Tx Frames 	                56612
Good Tx Broadcast Frames 	46
Good Tx Multicast Frames 	92
Tx Total Bytes 	                63100845
Collisions 	                0
	 
Error Frames 	                0
Carrier Sense Errors 	        0
	 
Receive
Good Rx Frames 	                34694
Good Rx Broadcast Frames 	529
Good Tx Multicast Frames 	367
Rx Total Bytes 	                4538162
	 
CRC Errors 	                0
Undersized Frames 	        0
Overruns 	                0

```

I tried to wire a laptop to the same network, different adapter BCM4401-B0 and it works much better but still has few errors. But the ration is way smaller than this PC. I.e. RX 2346 errors: 14 while this PC is much higher:
```
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5409 errors:3808 dropped:1905 overruns:0 frame:430
          TX packets:3918 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:5458447 (5.4 MB)  Byte TX:490307 (490.3 KB)
          Interrupt:18 

```

The MTU is the same for both at 1500. 

I tried also to go back to the .14 kernel but again nothing changed. it could be the router but then it's surprising that the two PC are experimenting different errors rates.....

---

### Post by Yoann Juet on 2009-11-15
> **Briga said:**
> 
I tried to wire a laptop to the same network, different adapter BCM4401-B0 and it works much better but still has few errors. But the ration is way smaller than this PC. I.e. RX 2346 errors: 14 while this PC is much higher:
```
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5409 errors:3808 dropped:1905 overruns:0 frame:430
          TX packets:3918 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:5458447 (5.4 MB)  Byte TX:490307 (490.3 KB)
          Interrupt:18 

```

The MTU is the same for both at 1500. 


looks weird ; two different computers experiencing TX packet errors on the same router. You have changed the cable, router port without observing improvement. Well, there should be something wrong on this router. Does-it have a 1500 Bytes MTU ? No vlan interfaces ?

---

### Post by Briga on 2009-11-16
Well, I should have sorted it out Yoann. 
It was a combination of different things. 

Partly software (9.10 idiosyncrasy with DNS and IPv6 (and lots of posts on this forums helped me there) and partly HW (I replaced the cabling and the physical errors went down). 

It's still not 100% OK but 98% I would say. Which is acceptable also because now I have other fish to fry (3d acc under wine slower than on 9.04). 

Thanks again Yoann. 
Briga

---

