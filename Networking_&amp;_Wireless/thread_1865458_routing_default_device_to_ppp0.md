---
title: "routing default device to ppp0"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by mahisura on 2011-10-20
Hi 
I am using ubuntu 10.10, I have ppp0 and eth0 network interfaces i want to setup ppp0 as my default route.
i have followed the thread [http://ubuntuforums.org/showthread.php?t=1313845](http://ubuntuforums.org/showthread.php?t=1313845). to do the setup.

here's what ihave done

```
route -e
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.29.145.65   *               255.255.255.255 UH        0 0          0 ppp0
10.5.116.0      *               255.255.255.224 U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         10.5.116.30     0.0.0.0         UG        0 0          0 eth0
```sudo route del default

route -e
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.29.145.65   *               255.255.255.255 UH        0 0          0 ppp0
10.5.116.0      *               255.255.255.224 U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0

sudo route add default gw 172.29.145.65 dev ppp0

route -e
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.29.145.65   *               255.255.255.255 UH        0 0          0 ppp0
10.5.116.0      *               255.255.255.224 U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         172.29.145.65   0.0.0.0         UG        0 0          0 ppp0

after i do the routing the default interface is changed to ppp0 but it doesnot work, do i need to modify some thing else?

Thanks

---

