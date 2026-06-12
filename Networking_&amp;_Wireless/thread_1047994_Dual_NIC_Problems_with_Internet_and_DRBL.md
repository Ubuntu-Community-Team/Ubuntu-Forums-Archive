---
title: "Dual NIC Problems with Internet and DRBL"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by cniehoff on 2009-01-23
I have a 8.10 server that has 2 nic, eth0 is static set to 192.168.98.151 this is my internet connection network

eth1 is set up as my dhcp server and running DRBL as a PXE, also it is set to 192.168.0.1 and handing out address thru .60 This is were we are connecting machines that load images and also workstations that need to share the internet threw the eth0 

When both nic are up i get no internet but if i take down eth1 the internet comes back, any idea's?

Thanks,

Craig

---

### Post by Iowan on 2009-01-23
Post */etc/network/interfaces*

---

### Post by cniehoff on 2009-01-23
auto lo
 iface lo inet loopback

 auto eth0
 iface eth0 inet static
     address 192.168.98.151
     network 192.168.98.0
     netmask 255.255.254.0
     broadcast 192.168.0.255
     gateway 192.168.98.1

auto eth1
 iface eth1 inet static
     address 192.168.0.1
     network 192.168.0.0
     netmask 255.255.255.0
     broadcast 192.168.0.255
     gateway 192.168.0.1

And again eth0 is my wan side and eth1 is my dhcp & DRBL side

Thanks again ahead of time!!

---

### Post by Vesperatus on 2009-01-23
Post ( from server and a box on the network )

```
sudo /sbin/route -n 
```


I would'nt be surprised if you default gateway is the 192.168.0.1 for the server

---

### Post by Iowan on 2009-01-23
> **cniehoff said:**
> 
 auto eth0
 iface eth0 inet static
     address 192.168.98.151
     network 192.168.98.0
     netmask 255.255.254.0
     [COLOR="Red"]broadcast 192.168.0.255[/COLOR]
     gateway 192.168.98.1
Typo, my bad math, or is broadcast address outside subnet?
(Happens to be the same address that eth1 uses).

Also, something seems wrong using an interface as it's own gateway.> **cniehoff said:**
>   iface eth1 inet static
     [COLOR="Blue"]address 192.168.0.1[/COLOR]
     network 192.168.0.0
     netmask 255.255.255.0
     broadcast 192.168.0.255
     [COLOR="Blue"]gateway 192.168.0.1[/COLOR]

---

