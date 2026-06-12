---
title: "Disabling Internet access on NFS server"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by reza81 on 2009-04-01
Hi ppl,

I have installed Ubuntu NFS system to mount on my VMWare ESX 3.5

Everything works fine & I am actualy pleased :KS

I have several netwoks interfaces. For now I have installed just one interface. Now I want to disable internet access to this interface. 

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth1
#iface eth1 inet dhcp

#auto eth0
#iface eth0 inet static
#address 10.37.30.130
#netmask 255.255.255.0
#gateway 0.0.0.0

auto eth1
iface eth1 inet static
address 10.37.0.130
netmask 255.255.0.0
gateway 127.0.0.1


```

I have changesd the real gateway address to the host loopback ip address & even tries 0.0.0.0

```
sudo /etc/init.d/networking restart

```

After restarting networking the still can access the internet!! Why & how can I configure this?


P.S.
Also any optimisation tips & trics regarding NFS server's are welcom.


Thanks in advanced,
Reza

---

### Post by coutts99 on 2009-04-01
What it the output of 'route'?

---

### Post by reza81 on 2009-04-01
> **coutts99 said:**
> What it the output of 'route'?

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.37.0.0       *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         10.37.0.1       0.0.0.0         UG    100    0        0 eth1

```

It seams interfaces is not the place to change my default gateway

---

### Post by coutts99 on 2009-04-01
Can you try -:

route del default gw 10.37.0.1

---

### Post by reza81 on 2009-04-01
offcourse!

Thanks a lot m8

---

