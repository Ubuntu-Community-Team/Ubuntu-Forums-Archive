---
title: "Phantom ethernet and wireless interfaces getting created"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by cupabj on 2009-05-23
Hi,

I have a HP dv6000 series laptop with an external D-link USB wireless adapter. At times, it fails to connect to internet via wireless and via ethernet. I checked configuration using ifconfig and it shows extra ethernet and wireless interfaces titled, eth0:avahi, and wlan1:avahi, respectively getting created. If I plug out the ehternet cable and plug it back in, the extra avahi ethernet interface sometimes disappears and internet connection functions correctly. It does require a few cable remove/insert operations to get it to work. Likewise for wireless, it requires a few USB card removal and plugin operations to get it to work. When network connection functions, I notice that the extra, "avahi" interfaces have disappeared. Appreciate any help to get this to work correctly the first time as the number of retries to get it to work are random and obeys Murphy's laws :icon_frown: !. Data for my system:
$ uname -a
Linux aniruddha-laptop 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux

$ lspci|grep -i ethernet
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:21:91:83:90:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+dr71wu driverversion=1.52+D-Link,12/21/2006, 1.02.00. ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g


ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 00:16:36:ca:5a:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

**eth0:avahi** Link encap:Ethernet  HWaddr 00:16:36:ca:5a:e2  
          inet addr:169.254.8.179  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:185381 (181.0 KB)  TX bytes:185381 (181.0 KB)

wlan1     Link encap:Ethernet  HWaddr 00:21:91:83:90:bd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**wlan1:avahi** Link encap:Ethernet  HWaddr 00:21:91:83:90:bd  
          inet addr:169.254.8.190  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

---

### Post by cupabj on 2009-05-24
Hi,

I will greatly appreciate any help troubleshooting this problem. 

Thanks,
-Aniruddha

---

### Post by superprash2003 on 2009-05-24
in your terminal type the following 2 commands and post output
1)sudo dhclient eth0
2)sudo dhclient wlan1

---

### Post by cupabj on 2009-05-24
Hi,

Sorry for the delay in response, my ADSL connection was down. I tried the dhclient command on the ethernet interface and it removed the eth0:avahi interface while correctly negotiating DHCP on eth0 to assign IP address. Looks like this is a good workaround for the problem. I'll try it later for wireless interface too.

Thanks for your help,
-Aniruddha

---

### Post by Iowan on 2009-05-24
**avahi** is *supposed* to be a zero-conf network.  The appearance of avahi-addresses usually means DHCP is not working.  Although it is *supposed* to make networking easier, sometimes it seems to complicate things.

---

### Post by cupabj on 2009-05-25
I have observed that only an IPv6 address gets assigned to the main interface while avahi interface has a fixed IPv4 address assigned. Somehow, DHCP never gets negotiated on the main interface to assign an IPv4 address. Hope this helps in debugging. I'll be happy to volunteer my time to fix this problem if someone can give some direction. I'm an Ubentero but haven't yet attempted to fix any bug.

Thanks!
-Aniruddha

---

