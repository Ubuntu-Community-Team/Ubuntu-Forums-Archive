---
title: "[SOLVED] Cannot connect to wired network (out of a sudden)"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by anuragji on 2008-12-10
Hey there,

I have Ubuntu 8.04 installed on my laptop. Everything was going well - like it usually does in such situations ;) - and out of a sudden I am no longer able to connect to my wired network. Apart from some scheduled updates nothing has changed in my setup and the connection literally dropped in the middle of browsing.

Right now the network manager tries to connect to the router again and again and again with no avail.

Here is some more information.

dhclient eth0 :
```
anurag@anurag-laptop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:0f:b0:c8:3c:57
Sending on   LPF/eth0/00:0f:b0:c8:3c:57
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

```

ifconfig returns:
```
anurag@anurag-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:c8:3c:57  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:247042 (241.2 KB)  TX bytes:12848 (12.5 KB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93394 (91.2 KB)  TX bytes:93394 (91.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:9a:2b:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-9A-2B-18-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

anurag@anurag-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:c8:3c:57  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:313309 (305.9 KB)  TX bytes:12848 (12.5 KB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93423 (91.2 KB)  TX bytes:93423 (91.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:9a:2b:18  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-9A-2B-18-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

/etc/network/interfaces currently contains:
```

auto lo
iface lo inet loopback
```

And finally: 
lspci -vnn | grep Ethernet
```

05:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```

I have no clue why this is going on, and network setup is also no my forte AT ALL...

Any help is greatly appreciated!!!

Anurag

---

### Post by superprash2003 on 2008-12-10
well you arent getting an ip address.. try using static ip.. which interface is connected to wired network?

---

### Post by anuragji on 2008-12-10
> which interface is connected to wired network?

Do you mean the Router? That is a Linksys RTP300.

I can try the static IP address, but the strange thing is that is was actually working fine and out of a sudden it got screwed up.

---

### Post by anuragji on 2008-12-10
> which interface is connected to wired network?

Do you mean the Router? That is a Linksys RTP300.

I can try the static IP address, but the strange thing is that is was actually working fine and out of a sudden it got screwed up.

---

### Post by anuragji on 2008-12-10
I tried setting a static IP address by going to Network Manager > Wired connection and setting all values there, but no success.

Any other suggestions?

---

### Post by superprash2003 on 2008-12-11
post ifconfig outpt after setting static ip.. by interface i mean wlan0 or eth0 or .....

---

### Post by anuragji on 2008-12-11
I was trying to connect using eth0. I went out and got a wireless router, because I had to get online to finish a project.
I just tried the ethernet connection and it worked. Both with a static IP and with roaming mode enabled.

Maybe the problem was the other router?

Thank you for your input!!!!!

---

### Post by starcannon on 2008-12-11
I know this is solved, but I thought I'd put in 2cents anyway; I use Linksys routers regularly, and have noticed occasionally they crash; power cycling generally will do the trick, sometimes they do require being reset (you'll need a paperclip to get at the button.)

GL and have fun.

---

### Post by anuragji on 2008-12-11
Thanks Starcannon, I will keep that in mind...

I did unplug the router a few times, but I did reset it.

---

