---
title: "How to get ethernet working"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by ShirishAg75 on 2006-07-06
Hi all,
       I'm using Ubuntu 6.06. First up is the screenshot of the device mgr. :-

[CENTER][[IMG]http://img145.imageshack.us/img145/2918/devicemgr5uu.th.png[/IMG]]("http://img145.imageshack.us/img145/2918/devicemgr5uu.png")
[/CENTER]
   

 The second is the screenshot of the network settings 

  [CENTER][[IMG]http://img150.imageshack.us/img150/8791/networksettings2ly.th.png[/IMG]]("http://img150.imageshack.us/img150/8791/networksettings2ly.png")
[/CENTER]
   

 Please tell me what to do. The network card is the RTL-8139/8139C/8139C+

  On my windows side of things this is what I get when I give ipconfig/all :-

```
Windows IP Configuration

        Host Name . . . . . . . . . . . . : SHIRISH
        Primary Dns Suffix  . . . . . . . : 
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 3:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : SiS 900 PCI Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-07-95-44-10-DB

Ethernet adapter Local Area Connection 4:

        Connection-specific DNS Suffix  . : 
        Description . . . . . . . . . . . : D-Link DFE-538TX 10/100 Adapter
        Physical Address. . . . . . . . . : 00-08-A1-92-56-33
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.2
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 61.1.96.69
                                                    61.1.96.71

``` 

 Now from this the D-Link DFE-538TX 10/100 is the important one, now how should I deal with it. Thnx in advance.

---

### Post by Wyrm_1972 on 2006-07-06
It looks all good. What's not working?

You have two ethernet cards and they both look like everything is fine. What are you trying to achieve?

If you are connecting to the internet via a router then DHCP should dish out you IP adresses etc...

---

### Post by ShirishAg75 on 2006-07-06
[quote=Wyrm_1972]It looks all good. What's not working?

You have two ethernet cards and they both look like everything is fine. What are you trying to achieve?

If you are connecting to the internet via a router then DHCP should dish out you IP adresses etc...[/quote]

you're absolutely right, the Ethernet connection 4 which is seen on windows is the ethernet card which is connected to my D-Link Router. There has been a long gap in my ubuntu stuff so need some help.

1. What commands can I give to see tht the Ethernet card is working properly. 
    I remember vaguely that it has to do something with dmesg which kinda probes everything.

2. Then after that whole step is there, then the steps so tht I can ping the router & finally net.

         Thnx in advance.

---

### Post by araz on 2006-07-06
Have you noticed that you don't have any default gateway defined (Shown by 2nd pic)??

I suggest you to install the netwok-manager-gnome, it may help you(it simplified my problems).

---

### Post by ShirishAg75 on 2006-07-06
araz, I don't know what is to be put where. For e.g. how do I know which ethernet connection to work with. Also there are 3 tabs where things most probably would need to be filled. It's much better than what was in 5.10 though but still would like to know where to do what. I haven't messed around with anything yet. It's a default install.

 After getting all the things to do then would install the network-manager-gnome also to see if tht makes any difference.

---

### Post by araz on 2006-07-06
please, post your ifconfig result.

---

### Post by ShirishAg75 on 2006-07-06
These are the contents of ifconfig.txt


```

eth0      Link encap:Ethernet  HWaddr 00:08:A1:92:56:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0x4b00 

eth1      Link encap:Ethernet  HWaddr 00:07:95:44:10:DB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)
``` 
 And if u can make any sense out of this plz. lemme know. Thnx in advance.

---

### Post by araz on 2006-07-06
To configure connections like windows:
in network settings:
-click connection eth1->poperties->uncheck "activate connection"
->ok
-click connection eth0->poperties->check "activate connection"
                                                       ->choose static ip
                                                       ->fill ip adress 192.168.1.2
                                                       ->fill sub-net mask 255.255.255.0
                                                       ->fill gateway 192.168.1.1
                                                       ->ok
In default gateway-> choose eth0

I think thats what you need:) .

ps. To add DNS: in network settings go to DNS tab and add your dns servers (61.1.96.69 and 61.1.96.71)

---

### Post by ShirishAg75 on 2006-07-06
Thnx mate, will let u know how things work out :)

---

### Post by ShirishAg75 on 2006-07-07
Did the following things as u prescribed but still no show :-

[CENTER][[IMG]http://img106.imageshack.us/img106/3391/eth19oy.th.png[/IMG]]("http://img106.imageshack.us/my.php?image=eth19oy.png")
[/CENTER]
     
 The 1st image shows when I deactivated the eth0 as told by you.

[CENTER][[IMG]http://img106.imageshack.us/img106/8796/eth20vm.th.png[/IMG]]("http://img106.imageshack.us/my.php?image=eth20vm.png")
[/CENTER]
     
 The 2nd image is with the connection settings as given by you.

[CENTER][[IMG]http://img90.imageshack.us/img90/47/eth36cq.th.png[/IMG]]("http://img90.imageshack.us/my.php?image=eth36cq.png")
[/CENTER]
     
 3rd doesn't have anything, just for reference.

[CENTER][[IMG]http://img106.imageshack.us/img106/5347/eth44cs.th.png[/IMG]]("http://img106.imageshack.us/my.php?image=eth44cs.png")
[/CENTER]
     
 4th is the DNS servers as u have said

[CENTER][[IMG]http://img106.imageshack.us/img106/8290/eth51bd.th.png[/IMG]]("http://img106.imageshack.us/my.php?image=eth51bd.png")
[/CENTER]
 
5th is the hosts file

  These are the results of the ping packets which I've sent :-

> PING 61.1.96.69 (61.1.96.69) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable
From 192.168.1.2 icmp_seq=4 Destination Host Unreachable
From 192.168.1.2 icmp_seq=5 Destination Host Unreachable

--- 61.1.96.69 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3999ms
, pipe 3
PING 61.1.96.71 (61.1.96.71) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable
From 192.168.1.2 icmp_seq=4 Destination Host Unreachable
From 192.168.1.2 icmp_seq=5 Destination Host Unreachable

--- 61.1.96.71 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4000ms
, pipe 3         
     Although when I ping 192.168.1.2 then I get some results in positive. But not able to see 
the D-Link router webpage which is at 192.168.1.1/cgi-bin/webcm. Looking for advice & help. Any links for downloading the network-gnome.deb file would also be helpful. Thnx in advance.

---

### Post by araz on 2006-07-07
please, post your another ifconfig result. I'm getting out of ideas:-k . Try to create a location with this settings.

---

### Post by ShirishAg75 on 2006-07-07
> **araz said:**
> please, post your another ifconfig result. I'm getting out of ideas:-k . Try to create a location with this settings.

What do u mean a location with this settings ](*,)

---

### Post by araz on 2006-07-07
> What do u mean a location with this settings 
In location add a new location.The location select box is on top of network settings

---

### Post by ShirishAg75 on 2006-07-07
meanwhile here's the ping report. Will get the ifconfig file in a while.

> PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.053 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.052 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.050 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=0.046 ms
64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=0.051 ms

--- 192.168.1.2 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.046/0.050/0.053/0.006 ms

 Would send the ifconfig as well as try to do the location bit also.

---

### Post by araz on 2006-07-07
Ping your router or other lan ip (lan connection test) and ping one internet ip like 66.249.91.99(google) (internet connection test) ping [www.google.com](www.google.com) (DNS test).

---

### Post by ShirishAg75 on 2006-07-07
> **araz said:**
> Ping your router or other lan ip (lan connection test) and ping one internet ip like 66.249.91.99(google) (internet connection test) ping [www.google.com]("http://www.google.com") (DNS test).

araz, I'm not on a network. It's a single user home connection. I have an ethernet card, a modem card & a router, that's it although will be trying as u say. btw here's the ifconfig that u asked for 

> eth1      Link encap:Ethernet  HWaddr 00:07:95:44:10B  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xc400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6100 (5.9 KiB)  TX bytes:6100 (5.9 KiB) 
    Thnx for all the efforts :)

---

### Post by kagashe on 2006-07-07
Hi Shirish,

Most MTNL/BSNL routers work "out of the box" on Dapper Live CD without any settings. My router UTStarcom UT-300R2U is working and my friend who has DLink router reported that it is working on Kubuntu Dapper Live CD.

I have installed Dapper yesterday and started browsing after booting. Although, I had set up static IP address (like what you have in Windows set up) in Ubuntu 5.10 I did not go for it after installing Dapper since it is working well in DHCP.

No setting is required. Just click on Firefox browser and see whether you can surf or not.

kagashe

---

### Post by araz on 2006-07-07
> 
araz, I'm not on a network. It's a single user home connection. I have an ethernet card, a modem card & a router, that's it although will be trying as u say.

Are you connected to your router through a ethernet connection? If yes you are in a lan with 2 machines(pc and Router)

---

### Post by araz on 2006-07-07
Sorry:( man, I gave you the wrong connetion settings I switced the eth0 and eth1 names.

New settings:
in network settings:

-click connection eth1->poperties->uncheck "activate connection"
->ok
-click connection eth0->poperties->check "activate connection"
->choose static ip
->fill ip adress 192.168.1.2
->fill sub-net mask 255.255.255.0
->fill gateway 192.168.1.1
->ok
In default gateway-> choose eth0

---

### Post by ShirishAg75 on 2006-07-07
Got it, did it, browsing it, now got to do the real work :)

---

