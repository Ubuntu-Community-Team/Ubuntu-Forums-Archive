---
title: "Cannot connect to internet through DSL"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by Rezwan Mahbub on 2011-04-02
Hello,
I am unable to connect to the internet through DSL. I can use it in Windows 7 easily. I use a Broadband PPPoe with an user name and password along with a service name. I have set up a DSL in ubuntu and I have placed the required user name and password there and I have also entered the service name in the field between the username and password. But it shows to be disconnected every time i try to dial the connection.
 
I have also tried with the "sudo ppoeconf" command and "setpppoe 1.0 software" and failed.
 
Can somebody help me out

---

### Post by Sef on 2011-04-02
1) What version of Ubuntu are you using?

2) Here's some [documentation]("https://help.ubuntu.com/community/ADSLPPPoE").

---

### Post by Rezwan Mahbub on 2011-04-03
> **Sef said:**
> 1) What version of Ubuntu are you using?

2) Here's some [documentation]("https://help.ubuntu.com/community/ADSLPPPoE").


**[*Ubuntu* 10.04 *LTS*]("https://lists.ubuntu.com/archives/ubuntu-announce/2010-April/000133.html")**

---

### Post by Rezwan Mahbub on 2011-04-04
Was my answer so simple that nobody is there for help!

---

### Post by Rezwan Mahbub on 2011-04-04
Let the answer be more detailed:

My required service name is: smilebd

In the 'sudo pppoe-discovery' command, it says as:

[COLOR=DarkRed]prome@prome-desktop ~ $ sudo pppoe-discovery

[sudo] password for prome: [/COLOR] [COLOR=DarkRed]

Access-Concentrator: MikroTik[/COLOR] [COLOR=DarkRed]

Service-Name: cyberplanet[/COLOR]        [COLOR=DarkRed]
--------------------------------------------------

AC-Ethernet-Address: 1c:af:f7:7a:0e:60[/COLOR] [COLOR=DarkRed]

Access-Concentrator: Cyber[/COLOR] [COLOR=DarkRed]

Service-Name: smilebd[/COLOR]        [COLOR=DarkRed]
--------------------------------------------------

AC-Ethernet-Address: 00:0c:42:52:a6:59[/COLOR]

---

### Post by dineshs on 2011-04-05
> But it shows to be disconnected every time i try to dial the connection.
I think it will show auto eth disconnected then DSL connection established.
After connecting (using NM or pon command) see if ```
ifconfig -a
``` shows an IP for ppp0 (please post result) or see if you can ping open DNS```
ping 4.2.2.1 -c3
```

---

### Post by Rezwan Mahbub on 2011-04-05
> **dineshs said:**
> I think it will show auto eth disconnected then DSL connection established.
After connecting (using NM or pon command) see if ```
ifconfig -a
``` shows an IP for ppp0 (please post result) or see if you can ping open DNS```
ping 4.2.2.1 -c3
```
prome@prome-desktop ~ $ ifconfig -a

eth0      

Link encap:Ethernet  HWaddr 00:27:0e:0d:9d:5f  
          
inet6 addr: fe80::227:eff:fe0d:9d5f/64 Scope:Link
          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
RX packets:810 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000 
          
RX bytes:83948 (83.9 KB)  
TX bytes:2349 (2.3 KB)
          
Interrupt:43 Base address:0xa000 
lo        
Link encap:Local Loopback  
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0 
          
RX bytes:5856 (5.8 KB)  TX bytes:5856 (5.8 KB)


prome@prome-desktop ~ $ ping 4.2.2.1 -c3
connect: Network is unreachable

---

### Post by dineshs on 2011-04-06
Are you trying wired (ethernet) or wireless? Do you have a modem/router?
Please also post the results of```
sudo lshw -C network
```

---

### Post by Rezwan Mahbub on 2011-04-07
> **dineshs said:**
> Are you trying wired (ethernet) or wireless? Do you have a modem/router?
Please also post the results of```
sudo lshw -C network
```
I am using wired (ethernet) internet. My ethernet adapter is built in with the motherboard.

The result shows as follows:

[sudo] password for prome: 
  
*-network               
       
description: Ethernet interface
       
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       
vendor: Realtek Semiconductor Co., Ltd.
       
physical id: 0
       
bus info: pci@0000:03:00.0
       
logical name: eth0
       
version: 03
       
serial: 00:27:0e:0d:9d:5f
       
size: 100MB/s
       
capacity: 1GB/s
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       
resources: irq:43 ioport:d000(size=256) memory:d3114000-d3114fff memory:d3110000-d3113fff memory:d3100000-d310ffff

---

### Post by dineshs on 2011-04-08
> Do you have a modem/router? ?
If yes what do you get for```
sudo dhclient eth0
```?
From the output of sudo lshw -C network your card is RTL8111/8168B and driver loaded is r8169.This may be a problem,Pl try [this ]("http://ubuntuforums.org/showpost.php?p=9293333&postcount=14")first then [this]("http://ubuntuforums.org/showthread.php?t=1022411") if nothing else work.

---

### Post by sandy0594 on 2011-04-08
Hey Rezwan,as Dinesh said..first u need to install the patch and driver of ur Ethernet,after that u will be able to connect to internet

```


sandy@ubuntu:~$ sudo dhclient eth0
[sudo] password for sandy: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/bc:ae:c5:50:83:1f
Sending on   LPF/eth0/bc:ae:c5:50:83:1f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12



```

```


sandy@ubuntu:~$ ping 4.2.2.1 -c3
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=244 time=267 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=244 time=266 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=244 time=277 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 266.235/270.336/277.625/5.167 ms



```

The links should resemble something like as above..i configured purely with the forum advice,initially i don't anything about linux

---

### Post by Rezwan Mahbub on 2011-04-08
> **dineshs said:**
> ?
```
sudo dhclient eth0
```?


sudo dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 2084

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.1.3

Copyright 2004-2009 Internet Systems Consortium.

All rights reserved.

For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)


Listening on LPF/eth0/00:27:0e:0d:9d:5f

Sending on   LPF/eth0/00:27:0e:0d:9d:5f

Sending on   Socket/fallback

DHCPREQUEST of 192.168.0.108 on eth0 to 255.255.255.255 port 67

DHCPACK of 192.168.0.108 from 192.168.0.1

bound to 192.168.0.108 -- renewal in 290 seconds.
__________________________________________________


Gone through successfully as per: [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411) but of no use.

---

### Post by dineshs on 2011-04-08
So the problem ,I think,is the service name.I do not know how to setup a DSL connection with service name.Though NM has a field for service name it may not be effective.

---

### Post by Rezwan Mahbub on 2011-04-10
> **dineshs said:**
> So the problem ,I think,is the service name.I do not know how to setup a DSL connection with service name.Though NM has a field for service name it may not be effective.
So I need someone to solve the problem by letting me know how to set up the SERVICE NAME in a DSl connection.

---

### Post by dineshs on 2011-04-11
If configuring network manager with service name fails you may try
Method-1  pppoeconf command . ie run ```
sudo pppoeconf
```and follow instructions.
run ```
sudo gedit /etc/network/interfaces
```and delete all lines except (You may save a copy before editing) ```
auto lo
iface lo inet loopback

```
Now run ```
sudo gedit /etc/ppp/peers/dsl-provider
``` and add this line at the begining (ref post #4 [here]("http://ubuntuforums.org/showthread.php?t=351686") )```
pty "/usr/sbin/pppoe -I eth0 -T 80 -S [COLOR="Red"]servicename[/COLOR] -C [COLOR="Red"]acname[/COLOR]"
``` replacing servicename with your service name and acname with your username
Restart PC and run ```
sudo pon dsl-provider 
``` to connect DSL.See if there is luck.Also see ```
plog
``` for details

Method-2 See if your router/modem can be configured in PPPoE mode with service name.
Method-3 See If the application rp-pppoe can solve your problem

---

### Post by Rezwan Mahbub on 2011-04-12
> **dineshs said:**
> If configuring network manager with service name fails you may try
Method-1  pppoeconf command . ie run ```
sudo pppoeconf
```and follow instructions.
run ```
sudo gedit /etc/network/interfaces
```and delete all lines except (You may save a copy before editing) ```
auto lo
iface lo inet loopback

```Now run ```
sudo gedit /etc/ppp/peers/dsl-provider
``` and add this line at the begining  ```
pty "/usr/sbin/pppoe -I eth0 -T 80 -S [COLOR=Red]servicename[/COLOR] -C [COLOR=Red]acname[/COLOR]"
``` replacing servicename with your service name and acname with your username
Restart PC and run ```
sudo pon dsl-provider 
``` to connect DSL.See if there is luck.Also see ```
plog
``` for details

Method-2 See if your router/modem can be configured in PPPoE mode with service name.
Method-3 See If the application rp-pppoe can solve your problem
Note : Ref [http://ubuntuforums.org/showthread.php?t=351686](http://ubuntuforums.org/showthread.php?t=351686)
[http://ubuntuforums.org/showthread.php?t=103522](http://ubuntuforums.org/showthread.php?t=103522)
prome@prome-desktop ~ $ sudo plog
Apr 12 14:07:59 
prome-desktop pppd[2118]: Remote message: Login ok
Apr 12 14:07:59 
prome-desktop pppd[2118]: PAP authentication succeeded
Apr 12 14:07:59 
prome-desktop pppd[2118]: peer from calling number 00:0C:42:52:A6:59 authorized
Apr 12 14:07:59 
prome-desktop pppd[2118]: not replacing existing default route via 192.168.0.1
Apr 12 14:07:59 
prome-desktop pppd[2118]: Cannot determine ethernet address for proxy ARP
Apr 12 14:07:59 
prome-desktop pppd[2118]: local  IP address 113.11.99.199
Apr 12 14:07:59 
prome-desktop pppd[2118]: remote IP address 113.11.99.1
Apr 12 14:07:59 
prome-desktop pppd[2118]: primary   DNS address 114.31.0.66
Apr 12 14:07:59 
prome-desktop pppd[2118]: secondary DNS address 8.8.8.8

It seems to be connected now but i am not being able to browse.

---

### Post by dineshs on 2011-04-12
Disconnect DSL using ```
sudo poff dsl-provider
```Now run ```
sudo gedit /etc/resolv.conf
``` save a copy of the file so opened  and edit it so that it reads only```
nameserver 8.8.8.8
nameserver 114.31.0.66
``` save and close the file.Connect DSL using ```
sudo pon dsl-provider
``` See if there is any progress .If there is no luck still,
 1)Can you ping 8.8.8.8 or any site by IP ?
eg:```
ping -c3 8.8.8.8
```
2)When you type [http://74.125.224.81](http://74.125.224.81)  on the address bar and enter do you get google?
3)Is there any proxy setting? open firefox-click edit-preferences-advanced-network-connection settings-set no proxy and try
4)What do you get for ```
route -n
```and```
cat /etc/ppp/peers/dsl-provider
```

---

### Post by Rezwan Mahbub on 2011-04-13
Did a fresh install of the whole operating system hoping for a luck, but found of no use. So just decided to stop using it and switch back to Windows till ubuntu itself rebuild its network strategy to cope up with servicename option without much hassle like Windows.

---

### Post by dineshs on 2011-04-14
From post #16 I understand that the connection was working fine except DNS issue which you could correct had you edited /etc/resolv.conf
I request you try this (post #15 and first portion of #17)because if you succeed others also get benefited.

---

### Post by Rezwan Mahbub on 2011-05-03
The problem successfully solved after installing Ubuntu 11.04 and now I can set "service name" directly in the DSL dialer in the default network manager, just as expected and mentioned earlier.

---

