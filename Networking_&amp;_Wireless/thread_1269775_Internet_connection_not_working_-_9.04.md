---
title: "Internet connection not working - 9.04"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by ntoko on 2009-09-18
Internet does not work on my computer with 9.04
I installed Ubuntu 9.04 an XP desktop which is connected to my home network via ethernet. My ADSL router is Motorola Netopia and configured not to use PPoE. On my Ubuntu, I have tried DHCP, Manual and other reasonable options. My client computer running Ubunto can see all other nodes on my local. My router sees the ubuntu computer LAN but NO INTERNET CONNECTION. I was rather excited to finally start my transition from Windows to Linux but ... I need my Internet to work. I need some help here!!

---

### Post by pdc124 on 2009-09-19
whats the output of 

sudo ifconfig
 
and 
sudo  route -n

---

### Post by ntoko on 2009-09-19
[SIZE=3][FONT=Times New Roman]root@ubuntu:~# sudo ifconfig[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr 00:50:bf:35:45:da  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: fe80::250:bfff:fe35:45da/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:60095 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:668 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:4685598 (4.6 MB)  TX bytes:42966 (42.9 KB)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Interrupt:11 Base address:0x7800 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:6 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:416 (416.0 B)  TX bytes:416 (416.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]wlan0     Link encap:Ethernet  HWaddr 00:13:d3:7a:ea:2f  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]wmaster0  Link encap:UNSPEC  HWaddr 00-13-D3-7A-EA-2F-00-00-00-00-00-00-00-00-00-00  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]root@ubuntu:~# sudo route -n[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Kernel IP routing table[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0[/FONT][/SIZE]

---

### Post by pdc124 on 2009-09-19
so its got an IP address from your router but doesnt know to send stuff back to it .

Whats the IP of your router ?

try ping -c4 192.168.1.1 and see if you get anything back 

you can set the route manually
[http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

tells you how 
route add default gw 192.168.1.1 eth0

and see what happens

go to0 [www.google.com](www.google.com) and see if it works
if it doesnt 
try 
[http://209.85.227.103](http://209.85.227.103)

---

### Post by Iowan on 2009-09-20
Is your interface configured with Network Manager, */etc/network/interfaces*, or something else (WICD)?

---

