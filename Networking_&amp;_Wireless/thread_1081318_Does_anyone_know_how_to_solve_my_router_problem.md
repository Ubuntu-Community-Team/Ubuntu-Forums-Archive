---
title: "Does anyone know how to solve my router problem?"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by mitc1425 on 2009-02-26
I have a desktop connected by wire to my linksys WRT54Gs router and cannot connect to it. I have tried using 192.168.1.1 to access it and that does not work...Since my ISP is DSL, I have set up my router to automatically connect through PPpOE...I used the sudo pppoeconf command and it found eth0...I selected yes...and got a not connected message...ifconfig gave me

eth0 Link encap:Ethernet HWaddr 0007:e9:b1:9a:52
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask 255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:25190 errors:0 dropped:0 overruns:0 frame:0
TX packets:25190 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1276172 (1.2 MB) TX bytes:1276172 (1.2 MB)

ping 192.168.1.1 says network unreachable


please help...I have no problems accessing my router with my windows boxes but since i am completely new to linux I have no diagnostic skills as of yet...thanks in advance

---

### Post by sanemanmad on 2009-02-26
```
sudo dhclient
``` ?

or 

```
sudo ifconfig eth0 up

sudo dhclient
```

---

### Post by mitc1425 on 2009-02-26
This is what I got

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:07:e9:b1:9a:52
Sending on   LPF/eth0/00:07:e9:b1:9a:52
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
hammer@the-bratz:~$ sudo ifconfig eth0 up
hammer@the-bratz:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 20938
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:07:e9:b1:9a:52
Sending on   LPF/eth0/00:07:e9:b1:9a:52
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by sanemanmad on 2009-02-26
hmm... what's your /etc/network/interfaces  look like?

---

### Post by mitc1425 on 2009-02-26
it said bash: /etc/network/interfaces: Permission denied...I probably did something wrong huh

---

### Post by sanemanmad on 2009-02-26
> **mitc1425 said:**
> it said bash: /etc/network/interfaces: Permission denied...I probably did something wrong huh

woops... gonna need to use ```
sudo cat /etc/network/interfaces 
```

---

### Post by darco on 2009-02-26
> **mitc1425 said:**
> I have a desktop connected by wire to my linksys WRT54Gs router and cannot connect to it. I have tried using 192.168.1.1 to access it and that does not work...Since my ISP is DSL, I have set up my router to automatically connect through PPpOE...I used the sudo pppoeconf command and it found eth0...I selected yes...and got a not connected message...ifconfig gave me

eth0 Link encap:Ethernet HWaddr 0007:e9:b1:9a:52
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 

Looks like you are not picking up an IP address...you configured for DHCP? Check the network icon on the desktop panel and right click and select connection info..then go from there by editing the connection.

darco

---

### Post by mitc1425 on 2009-02-26
auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1



iface ppp0 inet ppp
provider ppp0

auto ppp0

---

### Post by mitc1425 on 2009-02-26
> **darco said:**
> Looks like you are not picking up an IP address...you configured for DHCP? Check the network icon on the desktop panel and right click and select connection info..then go from there by editing the connection.

darco

I manually configured it to be DHCP and my router is set up for DHCP as well

---

### Post by darco on 2009-02-26
You can access the internet fine just not the router?

darco

---

### Post by stardash on 2009-02-26
> **mitc1425 said:**
> auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1



iface ppp0 inet ppp
provider ppp0

auto ppp0

It looks like you have a network connection now, in the prior posts that did not seem to be the case. Can you ping the gateway?

Also Is your router perhaps set to only accept secure connections? ([HTTPS://)](HTTPS://)) If so you need to make sure you type that before the ip of the router.

---

### Post by mitc1425 on 2009-02-26
I can access my router and the internet on my windows based pc's only...i haven't even been able to ping my router successfully with ubuntu

---

### Post by mitc1425 on 2009-02-26
I tried to ping 192.168.1.1 and it just kept repeating Destination Host Unreachable so I tried [HTTPS://192.168.1.1](HTTPS://192.168.1.1) and it said unknown host

---

### Post by stardash on 2009-02-26
> **mitc1425 said:**
> I can access my router and the internet on my windows based pc's only...i haven't even been able to ping my router successfully with ubuntu

What is the NIC info for one of your pcs. What you just posted looks quite correct as far as having a connection. Just currious to see if there is anything different.

---

### Post by sanemanmad on 2009-02-26
Can we see ```
route
``` ?

also, In my opinion, no good ever evolves from apparmor... look into removing that package.

---

### Post by mitc1425 on 2009-02-26
just a standard cat5 NIC...the pc I switched over to ubuntu is an old dell that I gave to my 12yr old...I mainly did it to keep her safe since i know she loves myspace and games which as we all know are loaded with bad stuff...plus I believe linux to be the FUTURE so she will be ahead of the game if we learn it together....sorry for ranting and thanks for helping all

---

### Post by mitc1425 on 2009-02-26
> **sanemanmad said:**
> Can we see ```
route
``` ?

also, In my opinion, no good ever evolves from apparmor... look into removing that package.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

---

### Post by sanemanmad on 2009-02-26
route add default gw 192.168.1.1

Look at this site... if it works.

[Routes in Ubuntu]("http://www.cyberciti.biz/faq/howto-debian-ubutnu-set-default-gateway-ipaddress/")

---

### Post by mitc1425 on 2009-02-26
response was: File exists...retried pinging and it still won't reach destination host

---

### Post by THEDARKNESSHASCOME on 2009-02-26
> **mitc1425 said:**
> response was: File exists...retried pinging and it still won't reach destination host

first of all why are you filtering your computer through your wireless router instead of just having a switch to handle both and you should easily beable to get internet onto your desktop after that. But if not you might have to check if you are going to need any drivers like black ports..etc if not check your black list incase it might be blocked

---

### Post by mitc1425 on 2009-02-26
> **THEDARKNESSHASCOME said:**
> first of all why are you filtering your computer through your wireless router instead of just having a switch to handle both and you should easily beable to get internet onto your desktop after that. But if not you might have to check if you are going to need any drivers like black ports..etc if not check your black list incase it might be blocked

I am using a router because there are 3 desktops and 2 laptops that get used here...they are all stand alone with one OS on them

---

