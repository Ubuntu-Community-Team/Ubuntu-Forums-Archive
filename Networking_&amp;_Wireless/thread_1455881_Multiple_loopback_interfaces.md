---
title: "Multiple loopback interfaces"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by shikhar_sharma on 2010-04-16
Hi guys,
I wanted to know that is there any way in ubuntu that we can create multiple loopback adapters as in the case of windows.If yes please tell me how to do it.I know that ubuntu has by default one loopback lo.but my problem is due to some networking issue i want to create multiple loopback adapters and assign ip to them.Please tell me how to create them and how to assign ip address to them.

---

### Post by rvt on 2010-04-24
Hey,

You can use the following to create a new loopback interface

```

ifconfig lo:40 192.168.40.1 netmask 255.255.255.0 up

```Or add them permanently to /etc/network/interfaces


```

auto lo lo:10 lo:20
iface lo inet loopback

iface lo:10 inet static
        address 192.168.10.1
        netmask 255.255.255.0
        network 192.168.10.0

iface lo:20 inet static
        address 192.168.20.1
        netmask 255.255.255.0
        network 192.168.20.0

```Then use ifup to enable each lo interface after you've configured the file. You won't have to use ifup after reboot.
HTH

---

