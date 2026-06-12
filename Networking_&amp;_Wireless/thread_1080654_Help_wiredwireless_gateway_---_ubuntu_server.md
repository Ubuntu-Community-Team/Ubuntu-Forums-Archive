---
title: "Help wired/wireless gateway --- ubuntu server"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by sanemanmad on 2009-02-25
Hi, Hopefully someone may be able to point me in the right direction here.

I have an 8.04 server running DyDNS (internally) + DHCP + SQUID + IPTABLES ... and now I have installed and configured a working AP, using Madwifi drivers. My problem is I cannot seem to get my routing tables correct or I simply do not understand how I can effectively route traffic between my eth1 and ath0.

SETUP:

eth0 = INTERNET
eth1 = LAN
ath0 = WLAN

Instead of explaining a bunch, here are output of what I believe to be relevent:

Here is my routing tables when it *doesn't* work
```
[SIZE="1"]root@server:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.51.0    *               255.255.255.0   U     0      0        0 ath0
192.168.51.0    *               255.255.255.0   U     0      0        0 eth1
**.***.***.*    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         ip**-***-***-*. 0.0.0.0         UG    100    0        0 eth0[/SIZE]
```

And routing table when it *does* [[SIZE="1"]after issuing ifdown eth1[/SIZE]]
```
[SIZE="1"]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.51.0    *               255.255.255.0   U     0      0        0 ath0
**.***.***.*    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         ip**-***-***-*. 0.0.0.0         UG    100    0        0 eth0[/SIZE]
```


A Portion of IPTABLES... I use a script ($INT) refers to eth0

```
[SIZE="1"][SIZE="1"]echo 1 > /proc/sys/net/ipv4/ip_forward
$IPT -A INPUT -i ath0 -d 192.168.51.0/24 -p all -j ACCEPT
$IPT -A INPUT -i eth1 -d 192.168.51.0/24 -p all -j ACCEPT
$IPT -A FORWARD -i $INT -m state --state NEW,INVALID -j DROP
$IPT -t nat -A PREROUTING -i ath0 -p tcp --dport 80 ! -d 192.168.51.10 -j DNAT --to 192.168.51.10:3128
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 80 -j REDIRECT --to-port 3128
$IPT -t nat -A POSTROUTING -o $INT -j MASQUERADE[/SIZE][/SIZE]
```

And my Interfaces file...

```
[SIZE="1"]root@server:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto ath0
iface ath0 inet static
address 192.168.51.10
netmask 255.255.255.0
network 192.168.51.0
broadcast 192.168.51.31
auto eth1 
iface eth1 inet static
address 192.168.51.1
netmask 255.255.255.0
[/SIZE]
```

Portion of dhcpd.conf just in case

```
[SIZE="1"]root@server:~# cat /etc/dhcp3/dhcpd.conf
subnet 192.168.51.0 netmask 255.255.255.0 {
  range 192.168.51.11 192.168.51.27;
  option routers 192.168.51.10;
  option broadcast-address 192.168.51.31;[/SIZE]
```

Internet works fine on the first device that comes up, So let's say ath0 is primary during boot then when I connect to WLAN I can browse fine, now if I disable my (client) wlan card and connect cat5e I can lease an IP via (server) DHCP but I cannot browse the internet nor can I access any of my network... Same goes for vice-versa.

**Let me know if more is needed. Thanks**

[COLOR="Red"]****UPDATE****[/COLOR] Now let's say I change my subnet information to the following:
```
[SIZE="1"]root@server:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto ath0
iface ath0 inet static
address 192.168.51.10
netmask 255.255.255.0
network 192.168.51.0
broadcast 192.168.51.31
auto eth1 
iface eth1 inet static
address 192.168.52.10
netmask 255.255.255.0
[/SIZE]
```

Then here is my route ... only I can ssh between hosts, but that is all, I cannot ping other hosts nor can browse the internet.

```
[SIZE="1"]root@server:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.51.0    *               255.255.255.0   U     0      0        0 ath0
192.168.52.0    *               255.255.255.0   U     0      0        0 eth1
**.***.***.*    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         ip**-***-***-*. 0.0.0.0         UG    100    0        0 eth0[/SIZE]
```

[SIZE="1"]> Internet - <eth0> gateway <eth1,ath0> - client PC's[/SIZE]

---

### Post by sanemanmad on 2009-02-26
Anybody have any ideas? I have tried using Bridge-Utils however I cannot achieve the end result of a Wired/Wireless routing server/gateway.

---

### Post by sanemanmad on 2009-03-01
**bump**

---

