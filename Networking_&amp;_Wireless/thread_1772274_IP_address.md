---
title: "IP address"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by manish411 on 2011-05-31
I am a newbie in computer networks and am starting network programming.
Now I have a doubt about IP addresses.
I have been reading that every machine on Internet is given an IP address,does that mean that at home I have an internet connection then I have a unique IP address and if that so how do I find it. 
Also in my hostel we all computers connected via LAN. does that also mean that all computers connected to the LAN also have different IP addresses.

---

### Post by matt_symes on 2011-05-31
Hi

> **manish411 said:**
> I am a newbie in computer networks and am starting network programming.
Now I have a doubt about IP addresses.
I have been reading that every machine on Internet is given an IP address,does that mean that at home I have an internet connection then I have a unique IP address and if that so how do I find it. 

Have a look at this site

[http://www.whatsmyip.org/](http://www.whatsmyip.org/)

The IP address shownat the top of the page is the external IP address of your router. You router will also have an internal ip address and all the computers on your LAN will share addresses on your routers internal subnet.

This uses a technique called NAT and allows many LAN's to share the same subnet so increasing the available IP address in the world. It's only your routers external IP address that needs to be unique.

> Also in my hostel we all computers connected via LAN. does that also mean that all computers connected to the LAN also have different IP addresses.

All the computers on you local LAN will get a different IP address otherwise you will get conflicts.

Kind regards

---

### Post by chili555 on 2011-05-31
> I have been reading that every machine on Internet is given an IP address,does that mean that at home I have an internet connection then I have a unique IP address and if that so how do I find it. You find your IP address with the terminal command:```
ifconfig
```Here is a sample from my computer:```
$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 99:19:d2:c2:99:88  
          [COLOR="Red"]inet addr:192.168.1.101[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fec2:1b8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10106983 (10.1 MB)  TX bytes:2443342 (2.4 MB)
```> does that also mean that all computers connected to the LAN also have different IP addresses.Yes. The router takes care of those details. For example, the first computer to connect may get 192.168.1.101; the second one gets x.102 and so forth. The internet service provider sees only the router and gives it its unique address. Most, but not all routers, give their clients 192.168.x.y addresses. When machine 101 request a web page from, say Google, it requests it from the internet service provider and routes the page back to 101. It may, within a few milliseconds, get a request from machine 102 for a page from Amazon; when it comes back, the page is routed to machine 102.

---

### Post by baarn on 2011-05-31
to make it a bit clearer. (edit: yeah ok, with chili's posting, mine is partly obsolete)
all the computers in your hostel have their own ip adress inside the LAN, but they all have the same external ip  adress.
the router will take care which incoming package from the internet is send to which computer on the lan.

btw there are some countries in which you have a relatively stable ip adress (i think in the US you dont change it often) and others, where you get another one every time your router disconnects or atleast after 24 hours (thats the case in germany for example).
this dynamic ip-adresses are ok for private purposes, servers on the internet need static ips.

you can find out your internal ip adress by typing in
```
ifconfig
```that lists all your network devices and their IP adress (eth0 would be you wired-ethernet-card, wlan0 your wireless card)

---

### Post by manish411 on 2011-05-31
> **baarn said:**
> to make it a bit clearer. (edit: yeah ok, with chili's posting, mine is partly obsolete)
all the computers in your hostel have their own ip adress inside the LAN, but they all have the same external ip  adress.
the router will take care which incoming package from the internet is send to which computer on the lan.


This means the router provides the different IP addresses to the computers connected to the LAN??

---

### Post by baarn on 2011-05-31
It depends on how the router is configured.
easiest way is to use dhcp, if a computer connects to the network it looks for the router, and the router assigns an IP address to that computer (there are some IP-patterns reserved for use in LAN, so that your computer wont get an IP address already given to a server on the Internet for example.
the other way is to give every computer a static address, but in this case you have to track, which computer has which address, that could be a problem in bigger networks and definitively leads to problems if there is a conflict. (two computers sharing one address)

the gentoo handbook has a good introduction to network terminology, forget the rest of the handbook about installing gentoo, but this might clear things up for you.
(understanding network terminology)
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=3#network_term](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=3#network_term)

it also explains what a netmask and a broadcast address is.

---

### Post by manish411 on 2011-05-31
Thanks a lot !! I am beginning to grasp roots of networking now!!

---

### Post by manish411 on 2011-06-01
1.When I type the address 192.168.1.1 I am directed to the settings of my modem which is of Siemens
and with ifconfig :wlan0 has inet addr is 192.168.1.2 .How are these two related.

2.
```

$ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36430 (36.4 KB)  TX bytes:36430 (36.4 KB)
```

eht0 refers to lan , wlan0 refers to wireless,what does this refer to and what is loclahost and the 
ip address 127.0.0.1?

3. Does the whole city gets a particular IP address ?

---

### Post by lisati on 2011-06-01
> **manish411 said:**
> 1.When I type the address 192.168.1.1 I am directed to the settings of my modem which is of Siemens
and with ifconfig :wlan0 has inet addr is 192.168.1.2 .How are these two related.

The "192.168.1" part is sometimes called a subnet or a netblock, and can be used to refer to a group of IP addresses. When used on its own, it can be written as 192.168.1.0/24.
> **manish411 said:**
> 
2.
```

$ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36430 (36.4 KB)  TX bytes:36430 (36.4 KB)
```

eht0 refers to lan , wlan0 refers to wireless,what does this refer to and what is loclahost and the 
ip address 127.0.0.1?

127.0.0.1, also known as "localhost", is a convenient way to refer to the machine you are currently using.
> **manish411 said:**
> 
3. Does the whole city gets a particular IP address ?

An IP address is a bit like a phone number: each phone line in a city usually gets its own phone number, and each network connection gets its own IP address.

---

### Post by I'mGeorge on 2011-06-01
> **manish411 said:**
> I am a newbie in computer networks and am starting network programming.
Now I have a doubt about IP addresses.
I have been reading that every machine on Internet is given an IP address,does that mean that at home I have an internet connection then I have a unique IP address and if that so how do I find it. 
Also in my hostel we all computers connected via LAN. does that also mean that all computers connected to the LAN also have different IP addresses.

Simple explanation

Your IP address it' an unique id, just like I'm George and you're Manish, so that computers could "socialize" through internet. An IP can be static or dynamic. A static IP remains always the same while a dynamic one changes once in a while. The nature of your IP addres depends of your ISP.

If your computer is linked in a LAN through a router  or other similar devices it means your computer has a local IP address. In this case your internet connection it's managed by your router, and your router is the one that connects directly to the internet and not your computer which is managed by the router.

To find out your local IP address given by the router simply do ifconfig, your local IP is after inet addr:

If you wanna see your general IP address, assigned to you by your ISP in a web broswer in its address box type [www.cmyip.com](www.cmyip.com) or just click on the link I've just provided.
    
That's all folks

---

### Post by manish411 on 2011-06-04
Some more questions 
1. how is a static IP address different , does that mean that our ip address can change over the time by isp??
2. when we ask for an internet connection from an ISP what is the password and username for and
   where is the ip address stored ??

---

### Post by JKyleOKC on 2011-06-04
1. A static address is one provided by your ISP that never changes. It's yours so long as you retain that specific account. For instance, I have a block of five static IPs from my ISP; it costs me almost five times as much per month as a usual account would, but allows me to run a file server used in my business which must be available from any location on the Internet. A dynamic address is subject to change each time you log on, or even more often in some cases. Since it changes so often, it becomes very difficult to provide it to folk elsewhere on the Internet. Services do exist that mitigate the difficulty, but again most of them have subscription fees.

2. The User Name and Password questions when you request an IP are asked only if you are on a "dynamic IP" account. They are how your ISP knows that you are a subscriber, and knows how to access your account for billing purposes. The IP is stored in the /proc/net directory, but since it's really a 32-bit number rather than the "dotted quad" translation that you see displayed elsewhere, and is displayed in decimal form rather than hexadecimal, you will have difficulty recognizing it if you search...

---

