---
title: "Internal routing broken after upgrade to 11.10"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by phlegm on 2012-02-07
AaaaGGGHHHHHH I'm borked.

Upgraded my gateway server yesterday from 11.04 to 11.10 and now things are broke. Need your help for ideas

Here is what works. I can get to the internet. I can get to my box from the internet. External is working fine. The problem is with my internal network. I can see systems trying to get DHCP requests. but they never get completed. Just keeps repeating over and over.

```
Feb  7 09:46:09 mythserver dhcpd: DHCPDISCOVER from a8:e3:ee:48:f3:f0 via eth1
Feb  7 09:46:09 mythserver dhcpd: DHCPOFFER on 10.0.0.100 to a8:e3:ee:48:f3:f0 via eth1
Feb  7 09:46:29 mythserver dhcpd: DHCPDISCOVER from 00:1d:fe:de:ad:da via eth1
Feb  7 09:46:29 mythserver dhcpd: DHCPOFFER on 10.0.0.77 to 00:1d:fe:de:ad:da via eth1
Feb  7 09:46:29 mythserver dhcpd: DHCPDISCOVER from 00:1d:fe:de:ad:da via eth1
Feb  7 09:46:29 mythserver dhcpd: DHCPOFFER on 10.0.0.77 to 00:1d:fe:de:ad:da via eth1
Feb  7 09:51:25 mythserver dhcpd: DHCPDISCOVER from 18:e7:f4:3e:ed:7d (iPod-Touch-2) via eth1

Feb 7 09:51:25 mythserver dhcpd: DHCPOFFER on 10.0.0.95 to 18:e7:f4:3e:ed:7d (iPod-Touch-2) via eth1

```
If I give my laptop a hardcoded IP on the 10 network I can't reach anything either.

I can't ping internal things form the inside interface on the server.
```

ping 10.0.0.22
PING 10.0.0.22 (10.0.0.22) 56(84) bytes of data.
From 10.0.0.1 icmp_seq=2 Destination Host Unreachable
From 10.0.0.1 icmp_seq=3 Destination Host Unreachable
traceroute 10.0.0.22
traceroute to 10.0.0.22 (10.0.0.22), 30 hops max, 60 byte packets
 1  10.0.0.1 (10.0.0.1)  3002.165 ms !H  3002.160 ms !H  3002.153 ms !H
```

Weird. Here is some info
```

root@mythserver:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:55:b9:a3 
          inet addr:xxx.53.xxx.27  Bcast:72.53.158.31  Mask:255.255.255.224
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3246551 (3.2 MB)  TX bytes:10586800 (10.5 MB)
          Interrupt:47 Base address:0x2000
eth1      Link encap:Ethernet  HWaddr 00:1b:21:ae:30:13 
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1099 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:230100 (230.1 KB)  TX bytes:305509 (305.5 KB)
```

```

root@mythserver:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         72-53-158-1.cpe 0.0.0.0         UG    0      0        0 eth0
10.0.0.0        *               255.255.255.0   U     1      0        0 eth1
xxx.53.158.0     *               255.255.255.224 U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1

```
No idea what to try next. Any ideas?

---

### Post by helgman on 2012-02-07
So you have to issues, no routing the in the router and DHCP clients that won't accept their offers. Since you can't ping the router I think that is the first thing to investigate.

Can you see any traffic coming back from the router? I remember a similar problem a while back ... we had two or three servers and one was unreachable from across the LAN. Nodes placed right next to it could communicate without a problem but clients "next door" (two switches away) was left unanswered.

We finally managed to solve the problem by changing the MAC address on the server ... but we was rebuilding the network so we didn't go any deeper than that. You could give that a try.

What happens if you bypass the network infrastructure and connect a client directly to the router?

Regards,
Helgman

---

### Post by phlegm on 2012-02-07
Just got home and tried a few things. Rebooted the router first. If I plug into it I can plug other things in the house but not the server/gateway. 

Seems like a routing problem but I'm not a networking guy. At my wits end with this one. It seems like traffic can come into the server as I see the DHCP requests. It's just that nothing leaves. I tried only having the internal interface plugged in and rebooting but no difference. Somebody help please before the family lynches me. lol

---

### Post by phlegm on 2012-02-07
Got it working. Never guess what it was. My layout is like this
Internet---> computer
Computer (in closet Under stereo)---> 4 port hub.
4 port hub ---> 8 port switch in back room
           ---> PS3
           ---> stereo
8 port switch ---> dlink wireless in kids room
              ---> upstairs to cisco wireless upstairs
              ---> upstairs to myth frontend


Soooooo...... I took out the 4 port switch and plugged the computer into the cable that goes to the 8 port in the back room. Bingo. Working. No more internet for the PS3 or Stereo for now but we are working.

Weird that the thing died the same time as my upgrade.

I am very happy now.

---

### Post by helgman on 2012-02-08
I'm glad it worked out!

Regards,
Helgman

---

