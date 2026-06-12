---
title: "How to resolve using two nics ?"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by hanslammerts on 2011-06-23
Hello there,
 
I´m having trouble understanding how to fix my network that uses two NICs of which only one is supposed to go to the internet.
 
On my 10.04 x64 server I have two NICs. One is configured for the 192.168.2.x network, the other one for the 10.1.1.x network.
This is my interfaces file :
 
```

auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.30
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
auto eth1
iface eth1 inet static
        address 10.1.1.3
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.1

```
 
I am able to ping other machines in the 192.168.2.x network as well as machines in the 10.1.1.x network.
 
The intention is that ONLY the 192.168.2.x NIC can access the internet (for apt-get etc.), but this does not seem to work.
This is my resolv.conf file:
 
```

nameserver 62.179.104.196
nameserver 213.46.228.196
domain arnhem.chello.nl
search arnhem.chello.nl

```
 
Whenever I try to do a ping of [www.chello.nl]("http://www.chello.nl"), I get nothing back. If I try to do a ping of the IP address of [www.chello.nl]("http://www.chello.nl"), I see the following :
 
```

ping 213.46.242.72
PING 213.46.242.72 (213.46.242.72) 56(84) bytes of data.
From 10.1.1.1 icmp_seq=1 Destination Net Unreachable
From 10.1.1.1 icmp_seq=2 Destination Net Unreachable

```
 
It seems that the OS tries to resolve/ping over the 10.1.1.x network, which is not the network that is serviced by the router that does have an internet connection.
 
Question:
How can I force these kind of requests to go via the 192.168.2.x NIC on this machine ?
 
Thanks already,
 
Hans

---

### Post by alarme on 2011-06-23
check route -n

in my case:
$ route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.148.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0

you can see 4 adapter, wlan0, vmnet1, vmnet8 and eth0
wlan0 is the one I use to go to internet

maybe this help you

---

### Post by hanslammerts on 2011-06-23
Thanks for the reply, but it does not help me any further.
 
this is my route -n output :
 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.1.1.1        0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0

```
 
Anything wrong with this ?

---

### Post by i.r.id10t on 2011-06-23
Kill the gateway setting for the 10.x network

---

### Post by *nixgirl on 2011-06-23
Tried to route add default gw 192.168.2.1 ?
Although I think i.r.id10t's comment to remove the 10.x's gw should solve it.

Perhaps you will find this article + threads useful:
[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

---

### Post by hanslammerts on 2011-06-25
Thanks people,
 
It was indeed the gateway setting on the 10.x network that spoiled things.
Removed it, and things worked perfectly.
 
My mistake.....:p

---

