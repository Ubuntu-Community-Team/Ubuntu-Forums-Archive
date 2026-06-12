---
title: "Static IP with Wifi card"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by rollps on 2005-12-19
Hello everyone, :) 

I have trouble configuring my Wifi card with a static IP.

I run Xubuntu with an OvisLink Wifi PCI card (great linux card by the way) and a Wifi router.
When I put dhcp in /etc/network/interfaces :
```
...
auto ra0
iface ra0 inet dhcp
        wireless-essid xxxxxxxx
        wireless-key xxxxxxxxxxxxxxxxx
```
all goes well, the connection runs ok.

I am trying now to work with a static IP, here is /etc/network/interfaces :
```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map ra0

auto ra0
iface ra0 inet static
       adress 192.168.1.2
       netmask 255.255.255.0
       network 192.168.1.1
       gateway 192.168.1.1
       dns-nameservers 192.168.1.1
       wireless-essid ALICE-xxxx
       wireless-key xxxxxxxxxxxxxxxx

```
in fact I don't know exactly which fields to enter :???: 
I tried many different options but it won't work... 

Under WinXP, all I have to enter is :
IP adress 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
dns server 192.168.1.1

but with those in /etc/network/interfaces : nothing !
ra0 is not even listed with ifconfig command and ifup ra0 returns :

```
Don't seem to be have all the variables for ra0/inet.
Failed to bring up ra0.
```

Help please :-k

---

### Post by Lambert on 2005-12-19
1. address should have two d (address)
2. add an option dns-search with domain name of nameserver

dns-search name.of.domanin.net

---

### Post by rollps on 2005-12-19
Thank you so much ! I am French, that's why :mrgreen: ("adress" is "adresse")

works like a charm now :cool: 

keep up the good work with helping people guys !
thanks again

---

