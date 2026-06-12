---
title: "Uh oh....what happened to my connection"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by Anduu on 2006-06-15
Not sure but all of a sudden I cannot connect to the internet.Not when logged in as root or in recovery mode.

Cable went out for a bit and since it is back on I can connect in Windows but not Ubuntu.

Is it possible for this to happen if an isp is having problems?

The only thing system wise I have done lately is messed around with the permissions of my /home/username folder but I am pretty sure it is back the way it is was...could this be the cause?

Oh and that boatload of updates that came down the pipe today...I tried booting to a previous kernel but no luck.

So where to start looking...I don't have a clue ](*,)

---

### Post by Anduu on 2006-06-15
A little update...

Tried Ubuntu and Knoppix live cd's and cant connect but Windows still can...

I am ready to scream :-&

---

### Post by Anduu on 2006-06-16
More info...

ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:13:D4:57:A9:87
          inet6 addr: fe80::213:d4ff:fe57:a987/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1778 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:107499 (104.9 KiB)  TX bytes:2862 (2.7 KiB)
          Interrupt:193 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:942 (942.0 b)  TX bytes:942 (942.0 b)
```

Tried a sudo /etc/init.d/networking restart and got this:

```
Listening on LPF/eth0/00:13:d4:57:a9:87
Sending on   LPF/eth0/00:13:d4:57:a9:87
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 64.59.135.150 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:13:d4:57:a9:87
Sending on   LPF/eth0/00:13:d4:57:a9:87
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
and so on.......
```

From everything I see the problem is not on my end...is it?
I didn't monkey with any network settings before it broke.

---

### Post by BaffledMollusc on 2006-06-16
My wireless connectivity also just broke after installing that latest set of updates. See the thread I just posted "Lost wireless internet after lastest set of updates." Rolling back to the previous kernel (2.6.15-23-amd64-k8 ) restored it though; so I guess the problem isn't quite the same as yours.

---

### Post by Anduu on 2006-06-16
Well that is the darnedest thing...It was/is my ISP's fault.I can now connect to the internet.The mail server is still down though :rolleyes: 

Anyone know how it was possible for Winblows to connect but not Linux.Is it because Linux' network error handling is too "picky" about connection quality.

Is there some tweaking that can be done to get a connection under less than ideal circumstances....I don't know...stayed up way too late...got up way too early :confused:

---

### Post by zxee on 2006-06-16
A thread here, at the networking forums,  mentioned this as a possible cause: "The 2.6 Kernal has had multiple issues with the Microsoft Point to Point Encryption and Microsoft Point to Point Compression (MPPE/MPPC).

[http://mppe-mppc.alphacron.de/](http://mppe-mppc.alphacron.de/) this site gives some insight into these issues." sic

I don't know for sure if this is just another sensationalized issue or if it's real.

---

