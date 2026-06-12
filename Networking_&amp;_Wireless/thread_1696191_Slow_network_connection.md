---
title: "Slow network connection"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by scradock on 2011-02-27
I'm having trouble with one of three machines on a home network. It's an HP Pavilion Slimline s3100c desktop. Both my laptop (older HP) and my wife's laptop get reasonable download speeds (hundreds of kB/sec, sometimes over 1MB/s, from Time Warner cable, supposed to give up to 10Mb/s. No complaints.

The machine I mentioned first typically gets only 10 - 15 kB/sec download speeds, but occasionally shows bursts to acceptable levels of speed. It has a very poor Wifi board, so I usually run it wired - the other two use Wifi all the time with no trouble. The Connection Information from nmapplet in Ubuntu Maverick shows a connection speed of 100Mb/s over the eth0 interface.

System Monitor confirms the low transfer speeds, showing speeds around 15 kB/sec most of the time. My router is a dlink DIR-615, set up to connect to all three machines.

Any ideas about why it is so slow? How can I start checking the network traffic to see where the hold-up is happening? ifconfig shows no errors, dropped or overruns on RX or TX, for a start, so it's not missing packets and having to get them re-sent. Here's the ifconfig output for eth0:

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:7e:de:3e  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe7e:de3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19544 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28217911 (28.2 MB)  TX bytes:1581437 (1.5 MB)
          Interrupt:23 Base address:0x6000 

Any helpful ideas much appreciated!

---

