---
title: "Ubuntu 10 cannot recognize  and connect to wired network"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by Laser Topalovic on 2010-12-23
I need help considering ubuntu 10 at asus notebook. Newly installed Ubuntu 10 network manager wan't recognize my wired network internet no matter what. It searches and finally says u r not connected. Thing is that I have 8.10 instalation where it also reports same problem. I recently came from other place where I had similar wired network and it worked. I tried to configure it manually but I failed. On the other notebook that I have it works normaly. Is there any way to configure connection manualy.  Thanks for any assistance!

---

### Post by Doruletz on 2010-12-28
Hi.

I have the same problem with any 64 bit Ubuntu 10.10 Maverick based distro that I tried. Please post here if you find a fix for this problem.

Cannot connect to wired network in:
Ubuntu 10.10 Maverick 64 bit
Ubuntu Ultimate Edition v2.8 64 bit
Linux Mint 10 Julia 64 bit

---

### Post by PatchesTheCaveman on 2010-12-29
Hey guys, what kind of connection do you have?  (cable/DSL/dorm room/whatever)

Also, go to Applications > Accessories > Terminal on your top bar and type the following into the black box and press Enter:
```
sudo dhclient eth0
```
Type in your password, press Enter, and copy and paste what follows into a post here.

---

### Post by mr-black on 2010-12-29
Also, if you could type

```
ifconfig -a
```

and paste the output of that in as well.

---

### Post by Dareth on 2011-01-09
I'm experiencing a similar problem on my Dell Inspiron E1505 running Ubuntu 10.10. My ethernet is labeled as eth1 instead of eth0, and the network manager isn't even displaying wired connections. I know it can't be a problem with the connection itself, because it works on my Windows partition.

When I type
```
sudo dhclient eth1
```

I get this:
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:16:ce:4a:3d:ed
Sending on   LPF/eth1/00:16:ce:4a:3d:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.109 from 192.168.1.1
DHCPREQUEST of 192.168.1.109 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.109 from 192.168.1.1
bound to 192.168.1.109 -- renewal in 40223 seconds.

And 
```
ifconfig -a
```

Yields this:
eth1      Link encap:Ethernet  HWaddr 00:16:ce:4a:3d:ed  
          inet addr:192.168.1.109  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe4a:3ded/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1229 errors:0 dropped:0 overruns:0 frame:48428
          TX packets:887 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:771338 (771.3 KB)  TX bytes:194342 (194.3 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15008 (15.0 KB)  TX bytes:15008 (15.0 KB)

---

### Post by PatchesTheCaveman on 2011-01-10
Dareth:  Even though NetworkManager isn't indicating you have a connection, that output indicates that you do.  If you try your Internet after running that first command, it should work just fine.

If you want, you can switch from NetworkManager to wicd, another program that drives the network icon.  It should show up properly then.  To do so, run the following commands:
```
sudo apt-get purge network-manager
sudo apt-get install wicd
```

---

