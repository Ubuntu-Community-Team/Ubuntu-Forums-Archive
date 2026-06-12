---
title: "need help ..."
date: 2006-04-29
forum: Networking &amp; Wireless
---

### Post by umai21 on 2006-04-29
i already search  thread about internet prob and try all method recommended ..but still no success... right now ....i need help from  ubuntu pro out there about my prob ...


i cant access internet ... 
i can access LAN but only 5 computer i can access (ping)
when i click network status ...received increase but sending almost no transmision

i already used DHCP and also static ip config still no changes...

this info i get when i use ifconfig

 Link encap:Ethernet  HWaddr 00:90:F5:00:86:3D
          inet addr:10.124.120.181  Bcast:10.255.255.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:443281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33411054 (31.8 MiB)  TX bytes:179858 (175.6 KiB)
          Interrupt:11 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3049460 (2.9 MiB)  TX bytes:3049460 (2.9 MiB)


and when i use  'sudo dhclient eth0'

Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:90:f5:00:86:3d
Sending on   LPF/eth0/00:90:f5:00:86:3d
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 10.124.120.2
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.124.120.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.124.120.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.124.120.2
SIOCADDRT: Network is unreachable
bound to 10.124.120.181 -- renewal in 326443 seconds.

network is unreachable !!

and 'netstat -nr'
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.124.120.0    0.0.0.0         255.255.248.0   U         0 0          0 eth0


no route detected..!!!
so, what should i do now??

---

### Post by souki on 2006-04-29
[quote=umai21]i already search  thread about internet prob and try all method recommended ..but still no success... right now ....i need help from  ubuntu pro out there about my prob ...[/quote] I'm not an ubuntu pro

> i cant access internet ... 
i can access LAN but only 5 computer i can access (ping) so you have more computers ? windows ? linux ?
can you access internet from there ?

> when i click network status ...received increase but sending almost no transmision what is that ? where did you click ?

could you post your /etc/resolv.conf ?
if you have a working machine on your lan, could you post its configuration ? or explain your network topology

---

### Post by sailor2001 on 2006-04-29
I have trouble also......My router is putting out a signal, but the ip is not sending info to it.....However, this problem is also in windows, it's not a linux problem......also the cut-out from the ip most of the time is very intermediate...... off and on again in a few seconds. almost like a bad telephone connection to the modem........

---

### Post by mips on 2006-05-02
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

At what point do you get stuck with the above guide ?

1. Please post output of **ifconfig eth0** (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please copy entire output of windows **ipconfig /all** command here
8. What router/modem/cable etc do you use ?
7. Who is your ISP and provide a web link.

---

