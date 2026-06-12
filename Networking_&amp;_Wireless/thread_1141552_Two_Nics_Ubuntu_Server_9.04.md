---
title: "Two Nics Ubuntu Server 9.04"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by gabriel2007 on 2009-04-28
Hi !

I have an EVGA dual NIC and I got one of the cards connected to my LAN and the other to my ISP, when both cards are plugged I cannot browse the internet, if I unplug one I can , both are set to dhcp I want to acccess my server from the outside world and I haven't been able to do it so far :-(, help me up please!

:popcorn:

---

### Post by cariboo on 2009-04-28
Are the two network interfaces on different subnets?

```
eth0     192.168.1.100
eth1     192.168.2.100
```

---

### Post by gabriel2007 on 2009-04-28
Yes , one has a a public ip

```
190.175.xxx.xxx
255.255.255.240 
```

the other has

```
192.168.0.109
255.255.255.0
```

:popcorn:

---

### Post by gabriel2007 on 2009-04-28
my /etc/network/interfaces file looks like

```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

---

### Post by Iowan on 2009-04-28
What are results of **route**? In particular, what is gateway.  Also, what is in */etc/resolv.conf*? I'm wondering if LAN information is overwriting ISP's info.

---

### Post by gabriel2007 on 2009-04-28
now I could see if I try to up the two interfaces it shows

inferfaces:11 unknown method
ifdown couldn't read interfaces file....

inferfaces:11 unknown method
ifup couldn't read interfaces file.......

if I use #s to comment out the eth1 interface it will load , while if uncommented won't work properly returning that error.

Thanks!

:popcorn:

---

