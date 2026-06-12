---
title: "Where is this second interface coming from?"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by carpat on 2013-02-21
I'm a programmer, not a network admin (and Windows is my platform may the gods forgive me), but am trying to pick some stuff up by playing around with a spare linux server at work.
 
My **/etc/network/interfaces**
 
```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 10.0.0.44
netmask 255.0.0.0
gateway 10.0.0.1
dns-nameservers 10.0.0.1

```
 
ifconfig after a boot:
 
```

eth0      Link encap:Ethernet  HWaddr 00:0b:cd:ef:8c:31
          inet addr:10.0.0.44  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20b:cdff:feef:8c31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18619 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2541071 (2.5 MB)  TX bytes:1931857 (1.9 MB)
          Interrupt:29
eth1      Link encap:Ethernet  HWaddr 00:0b:cd:ef:8c:30
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4334292 (4.3 MB)  TX bytes:4334292 (4.3 MB)

```
 
If I **/etc/init.d/networking** **restart** then eth1 disappears.
 
My questions:
1) Why is eth1 up after a boot? I thought only interfaces that are auto in **/etc/network/interfaces** are up after boot?
 
2) Does this mean that the server has two NIC's? Why is eth0 UP RUNNING and eth1 only UP ? If I assign it a static ip, it still only ever shows as UP without RUNNING.

---

### Post by chili555 on 2013-02-21
> Why is eth1 up after a boot? I thought only interfaces that are auto in /etc/network/interfaces are up after boot?Usually if the hardware and the driver join, the system will bring the interface up. It needn't necessarily be declared in interfaces since you could connect with ifconfig:```
sudo ifconfig eth1 10.0.0.45 up
```Or even:```
sudo dhclient eth1
```> Does this mean that the server has two NIC's?Most definitely; notice two distinct MAC addresses. Confirm:```
sudo lshw -C network
```To be RUNNING, I believe packets must be transmitted and received, that requires an attached ethernet cable.> and Windows is my platform may the gods forgive meRemember the first step to recovery is admitting you have a problem. Congratulations.

---

