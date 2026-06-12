---
title: "2 gateways ?"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by d0d0 on 2006-07-08
Hi everyone,
I've just installed dapper at work (I use it at home too :) ) and I need to configure my network card with 2 gateways. The 2nd gateway will be used to access another local network (so gateway + dns).

I've used the network configurator tool which is integrated in gnome to configure my network card. But with this tool, you can only insert 1 gateway. I know that under windows you can add 1 or more gateways but with ubuntu... not to sure.

Anway, can anyone help me on this ?

Cheers !

---

### Post by tturrisi on 2006-07-08
You should be able to do this by giving each connection a specific name in the Network Settings Location menu.

---

### Post by mgor on 2006-07-08
let say the second network is 192.168.0.0/32 and you're connected to it with eth1.
```
route add -net 192.168.0.0 netmask 255.255.255.0 dev eth1
```

all traffic to the 192.168.0.0 will then go through eth1.

---

### Post by bartbes on 2006-07-08
when you go to the network config tool (network-admin) you can make different locations, use 1 for the 1st and 1 for the 2nd, don't know if you can use those simultanously

---

### Post by d0d0 on 2006-07-08
> **tturrisi said:**
> You should be able to do this by giving each connection a specific name in the Network Settings Location menu.

I've tried giving profiles in the network manager. The thing is that the profiles only change stuff like dns, host... Everything like IP, netmask, gateway stays the same.

Edit : Sorry about that, the profiles work. But you have to choose between networks :(, no way to "merge" them.

---

### Post by mips on 2006-07-08
Do a search for dual homing or multi homing. i'm not to sure what you mean but I think that is it.

---

### Post by d0d0 on 2006-07-08
I tried searching dual/multi homing and I don't think that its what I'm looking for.

Anyway, to resume the situation : I'm looking to add a second gateway to my network configuration (in order to connect to a 2nd local network).

---

### Post by mips on 2006-07-08
ok, please post output of **ifconfig -a** & **route -n** here.

---

### Post by d0d0 on 2006-07-09
I will as soon as I can... the thing is I'll be back at work on tuesday ! I'll send in the results then (the output of "ifconfig -a" and "route -n").

Thankx for the help all of you !

---

### Post by mgor on 2006-07-09
default gateway is where all the packages that don't have any matching route will be sent. in other words, you can't have two default gateways...

you will have to add a route to the second network.

i'll give an example .. again.
```
route add -net 192.168.0.0 netmask 255.255.255.0 dev eth1
```
this will route all the traffic for 192.168.0.0/32 through the interface eth1.

add the DNS in /etc/resolv.conf,
```
nameserver 10.10.10.1 # primary net DNS
nameserver 192.168.0.1 # secondary net DNS
```

---

### Post by d0d0 on 2006-07-09
Thankx for your patience mgor ;). Will check-out on tuesday and post results.

Till tuesday...

---

### Post by gruepig on 2006-07-09
You don't actually need two "default gateways"; you need two "network routes".  In addition to posting the output of 'ifconfig -a' and 'route -n', post the contents of the file /etc/network/interfaces.

If you have one Ethernet card which will be on your network, you'll want something like:

```

auto eth0
iface eth0 inet static
  address <your.ipaddr.on.net1>
  network <your.nwaddr.on.net1>
  netmask <your.nmaddr.on.net1>
  gateway <default.gw.net1.only>

auto eth0:0
iface eth0:0 inet static
  address <your.ipaddr.on.net2>
  network <your.nwaddr.on.net2>
  netmask <your.nmaddr.on.net2>

```

(If you have two Ethernet cards, each physically connected to a separate network, the "eth0:0" would be, for example, "eth1".)

Also, I'm assuming you don't actually want to route traffic between the two networks, but just want your computer connected to both.

---

### Post by d0d0 on 2006-07-11
Back to work ;)

So, heres the ifconfig -a output : 

```
$ ifconfig -a
eth0      Lien encap:Ethernet  HWaddr 00:16:76:02:54:69
          inet adr:172.27.27.249  Bcast:172.27.27.255  Masque:255.255.255.0
          adr inet6: fe80::216:76ff:fe02:5469/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:25950 erreurs:0 :0 overruns:0 frame:0
          TX packets:16609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:30759785 (29.3 MiB) Octets transmis:1539786 (1.4 MiB)

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:21 erreurs:0 :0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:1072 (1.0 KiB) Octets transmis:1072 (1.0 KiB)

sit0      Lien encap:IPv6-dans-IPv4
          NOARP  MTU:1480  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)

vmnet1    Lien encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet adr:192.168.34.1  Bcast:192.168.34.255  Masque:255.255.255.0
          adr inet6: fe80::250:56ff:fec0:1/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)

vmnet8    Lien encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet adr:192.168.216.1  Bcast:192.168.216.255  Masque:255.255.255.0
          adr inet6: fe80::250:56ff:fec0:8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)

```

Heres the route -n:

```
$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.34.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.27.27.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.216.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
0.0.0.0         172.27.27.253   0.0.0.0         UG    0      0        0 eth0

```

And heres the /etc/network/interfaces :

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.27.27.249
netmask 255.255.255.0
gateway 172.27.27.253

auto eth0:0
iface eth0:0 inet static
  address 172.27.27.249
  network 172.27.27.1
  netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

and the resolv.conf

```

nameserver 213.203.124.147
nameserver 212.30.96.123
nameserver 10.1.13.11

```

...and it still doesn't work !

---

### Post by d0d0 on 2006-07-11
I finally got throught it at last !!!

So, heres a resumé of what I wanted to do :

I'm on a network with a 172.27.27.x addresse. Theres a gateway (172.27.27.1) to reach other networks (3 more) which are on 10.1.13.x, 10.9.141.x and 10.98.151.x

So, what I did is :

```
sudo route add -net 10.1.13.0 netmask 255.255.255.0 gw 172.27.27.1 dev eth0
```

```
sudo route add -net 10.9.141.0 netmask 255.255.255.0 gw 172.27.27.1 dev eth0
```

```
sudo route add -net 10.98.151.0 netmask 255.255.255.0 gw 172.27.27.1 dev eth0
```

I've only got one final problem now (don't worry, its only a small one ;)).

When I disconnect, I lose all my routes. anyway to hard-write all of that down ?

Cheers

---

### Post by mips on 2006-07-11
You could add them to your interfaces files or as a initiliasation script at startup.

---

### Post by d0d0 on 2006-07-11
Cheers dude, thats just what I did. I added these lines to my /etc/network/interfaces : 

```

up route add -net 10.1.13.0 netmask 255.255.255.0 gw 172.27.27.1
up route add -net 10.9.141.0 netmask 255.255.255.0 gw 172.27.27.1
up route add -net 10.98.151.0 netmask 255.255.255.0 gw 172.27.27.1
down route del -net 10.1.13.0 netmask 255.255.255.0 gw 172.27.27.1
down route del -net 10.9.141.0 netmask 255.255.255.0 gw 172.27.27.1
down route del -net 10.98.151.0 netmask 255.255.255.0 gw 172.27.27.1

```

Thankx all of you for your help :)

---

### Post by slo on 2006-07-18
this solution need manul input command after system up
also , you can add this command to rc.local
I want to konw how to save this to some config file to do this ?

---

