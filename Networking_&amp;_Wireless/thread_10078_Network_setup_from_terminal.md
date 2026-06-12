---
title: "Network setup from terminal"
date: 2005-01-04
forum: Networking &amp; Wireless
---

### Post by labbe on 2005-01-04
how can I edit the network setup from the terminal?
I just wondering.......
I need to take it manuell...
My ip is: 192.168.0.11
Subnet mask: 255.255.255.0
gateway adress: 192.168.0.1
SSID/ESSID: Default
Wep key: 4020402040    (that isnt my really Wep key, but I need to have a example..

If you need it, this is the eth0 device and is a wireless intel 2200BG card.....

---

### Post by fng on 2005-01-04
you need to edit /etc/network/interfaces

```
# This is /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 123.123.123.123
    netmask 255.255.255.0
    gateway 123.123.123.1
    network 123.123.123.0
    broadcast 123.123.123.255
# Alternatively:
# iface eth0 inet dhcp
```

---

### Post by fng on 2005-01-04
Configuring the nameserver is in /etc/resolv.conf

```
fng@butters:~ $ cat /etc/resolv.conf
nameserver 10.0.0.1
fng@butters:~ $
```

---

### Post by labbe on 2005-01-04
Sounds Difficult...
Okay...What is Broadcast?
Where should I put the Wep key?
and what is the Nameserver..Is that the same as SSID/ESSID
And what is Network?
Is this right?:
```
This is /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.0.11
    netmask 255.255.255.0
    gateway 192.168.0.1
    network 123.123.123.0
    broadcast 123.123.123.255
# Alternatively:
# iface eth0 inet dhcp

```

---

### Post by fng on 2005-01-04
change 2 things in /etc/network/interfaces
network 192.168.0.0
broadcast 192.168.0.255

nameserver is the DNS-server of your internet provider.

Let's say your inet provider is telenet from belgium.
it has 2 DNS servers : 195.130.130.11 and 195.130.131.11
/etc/resolv.conf looks like this then :
```
nameserver 195.130.130.11
nameserver 195.130.131.11
```

---

### Post by labbe on 2005-01-05
Ok..So this is right?
```
This is /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.0.11
    netmask 255.255.255.0
    gateway 192.168.0.1
    network 192.168.0.0
    broadcast 192.168.0.255
# Alternatively:
# iface eth0 inet dhcp
```

But I have the Norwegian Alfanet...
So I don't know the DNS servers....
I haven't changed the DNS-servers when I did it from the GUI.
Do I have to do it when I do it from the terminal?

---

### Post by rolando on 2005-01-05
this works on my ubuntu at the root command prompt


[B]ifconfig eth0 192.168.0.11  netmask 255.255.255.0 broadcast 192.168.0.255

ifconfig eth0 up

route add default gw 192.168.0.1

iwconfig eth0 essid 'WIRELESS_LAN' 

iwconfig eth0 key 9f7h4j3jhe73o0f02002ws002s[/B]

change to suit your network

---

### Post by labbe on 2005-01-05
Thanks...
Should Work now.......
Thank you for the help :)

---

