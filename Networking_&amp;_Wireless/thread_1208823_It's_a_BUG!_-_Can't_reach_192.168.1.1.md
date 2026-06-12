---
title: "It's a BUG!? - Can't reach 192.168.1.1"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by N!coz on 2009-07-09
:popcorn: Hi, i'm italian, i don't write here often, but in italy, my problems don't seems to be resolvable, and i hope that in this community i can solve the busillis :p

When i try to configure my router ( DRAYTEK 2800 VG) on the broswer, writing 192.168.1.1 , the response is that the link is not existent...

Well, then i try to ping 192.168.1.1 in the console but the response is : Destination host unreachable..

On this machine i use ubuntu 9.04 amd64... I have many other pc's and, with the others ( installed 8.10) i can ping the router!

In the configuration /etc/network/interfaces i usually use the STATIC settings, but i have also tried to set DHCP mode, but with vary bad results...

I post my configuration of /network/interfaces 

```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.87
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```


my ifconfig: 

```
alessandro@ubunico:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:79:2e:4b  
          inet indirizzo:192.168.1.87  Bcast:192.168.1.255  Maschera:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:15:79:46:67  
          inet indirizzo:192.168.1.2  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::222:15ff:fe79:4667/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:413157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245074 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:540899246 (540.8 MB)  Byte TX:27688401 (27.6 MB)
          Interrupt:18 

lo        Link encap:Loopback locale  
          inet indirizzo:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1331 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:82924 (82.9 KB)  Byte TX:82924 (82.9 KB)
```

and my route

```
alessandro@ubunico:~$ route
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         my.router       0.0.0.0         UG    0      0        0 eth1
default         my.router       0.0.0.0         UG    100    0        0 eth0
alessandro@ubunico:~$ 
```

I wish someone can help me ! Byeee

---

### Post by jonobr on 2009-07-09
Hello

It looks as if you have two ethernet interfaces on the one machine connected to the same network segment which could be messing things up- Im thinking.

COuld you try to disable one of the interfaces , maybe eth1 and try your ping tests again?

---

### Post by wojox on 2009-07-09
On route try changing 

default    my.router   0.0.0.0    UG    100    0        0 eth0

to

default     192.168.1.1   0.0.0.0    UG    100    0      0 eth0

---

### Post by kerry_s on 2009-07-09
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.87
netmask 255.255.255.0
gateway 192.168.1.1

**auto eth0 <--remove**
```

---

### Post by N!coz on 2009-07-09
> **kerry_s said:**
> ```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.87
netmask 255.255.255.0
gateway 192.168.1.1

**auto eth0 <--remove**
```


I HAVE NO WORD :o   :popcorn::KS
 
I have only tried to remove auto eth0 , AND?

IT WORKS!!!! EUREKA!!

Router ping correctly... i don't try the other methods because now work correctly!!

I love this community ;)

---

### Post by N!coz on 2009-07-09
how i can write in the title  : SOLVED ?

---

