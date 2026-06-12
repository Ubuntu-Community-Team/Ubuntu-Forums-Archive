---
title: "[SOLVED] No wired connection"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by gryall on 2008-12-18
I am aware there a large number of posts of this form on the forum, however none seem to quite describe my problem.

I recently upgraded to Intrepid. After the upgrade I found that Wireless worked fine however The wired connection will not go beyond trying to acquire an address.

Ifconfig seems to suggest the MTU for eth0 (wired connection) is set to 64. Changing this in network manager to 1500 has no effect.

Does anyone know if the MTU setting is the problem, if it is ho do i fix it? If it isn't do you have any idea what is.

Thanks in advance

---

### Post by gryall on 2008-12-19
bump

---

### Post by gryall on 2008-12-19
rebump

---

### Post by superprash2003 on 2008-12-19
post output of ifconfig.. have you tried static ip?? what is the dhcp range of your router?

---

### Post by gryall on 2008-12-19
ifconfig (whilst connected to wireless)

eth0      Link encap:Ethernet  HWaddr 00:1c:23:b1:d3:ec  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1c:bf:37:09:75  
          inet addr:10.0.0.13  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21c:bfff:fe37:975/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49457984 (49.4 MB)  TX bytes:8331241 (8.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108160 (108.1 KB)  TX bytes:108160 (108.1 KB)

vbox0     Link encap:Ethernet  HWaddr ba:d2:9c:db:3a:86  
          inet6 addr: fe80::b8d2:9cff:fedb:3a86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-37-09-75-61-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I can't use a static IP as I Use a wired network at uni and they are reluctant to give us static IP's.

---

### Post by gryall on 2008-12-19
To clarify: I am currently at home using my wn router with dhcp range 10.0.0.4 - 10.0.0.15

Would you like me to post ifconfig whilst trying to connect to wired network (will it be differant?)

---

### Post by baAng on 2008-12-19
hello..i've tried this solution that i got from Ubuntu Documentation. I managed to enable *the wired connection and can surf the net*, but it seems like in the Network Manager the Wired Connection status don't pop up and also in the panel tray there is still X sign at the Network Manager icon.

This are the steps.

1) Open the terminal.

2) Type **sudo ifdown eth1** in the terminal and press **Enter**. 
*Replace eth1 with the name of your network interface if it is different. *

3) Enter the password if prompted.

4) Type **sudo ifup eth1** in the terminal and press **Enter**, again replacing _eth1_ with the name of your network interface.

5) If you have connected successfully, you should see a message similar to the following:

```
DHCPACK from 192.168.2.1
bound to 192.168.2.4 -- renewal in 536349522 seconds.
```

Now, you should be able to surf the net. I hope it helps.:p

---

### Post by gryall on 2008-12-19
Thanks. I take it there's no solution that actually involves getting network manager to work.

Does anyone know if there is a fix for this in the pipe line?

Also bellow is my ifconfig for when I am connected to wireless and I have plugged my network cable in.

[COLOR=DimGray]eth0      Link encap:Ethernet  HWaddr 00:1c:23:b1:d3:ec  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10290 (10.2 KB)  TX bytes:1006 (1.0 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1c:bf:37:09:75  
          inet addr:10.0.0.13  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21c:bfff:fe37:975/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1555363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2220984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:247758390 (247.7 MB)  TX bytes:368568935 (368.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:478889 (478.8 KB)  TX bytes:478889 (478.8 KB)

vbox0     Link encap:Ethernet  HWaddr ba:d2:9c:db:3a:86  
          inet6 addr: fe80::b8d2:9cff:fedb:3a86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-37-09-75-61-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR]


The vale given for the MTU seems low to me (although I really know nothing about these things). Could this be why network manager fails to connect. 

When I plug in the cable I Get the two filled green circles and if i Hover over them it says "requesting a network address from the wired network"

---

### Post by Iowan on 2008-12-19
> **gryall said:**
> The vale given for the MTU seems low to me (although I really know nothing about these things). Could this be why network manager fails to connect.  Thought I'd seen a bug mentioned about very low MTU...

---

### Post by gryall on 2008-12-20
so did I - But I can't find it anymore. I'll post If I find it.

---

### Post by ackattack on 2008-12-20
I had this problem and installing WICD or adding:

```
auto eth0
iface eth0 inet dhcp

```

to /etc/network/interfaces fixed the problem

It may be the return of this bug: [URL="https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/61989"]https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/61989
[/URL]
Really it's a bug in your router, which is reporting the incorrect MTU value.  However Network Manager *should* be smart enough to ignore any value below 576, but is not.

---

### Post by superprash2003 on 2008-12-21
eth1 seems to be the wired interface.. and its MTU seems correct..are you able to ping gateway?

---

### Post by gryall on 2008-12-21
[QUOTE=ackattack]It may be the return of this bug: [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/61989](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/61989)[/QUOTE]

This has fixed it.

I ran the command in the bug report

```
sudo ifconfig eth0 mtu 1500
```

Thank you so much for that suggestion. I never would have found it without you.

---

