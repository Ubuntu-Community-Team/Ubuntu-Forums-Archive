---
title: "No Network connectivity after restore"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by john_d13 on 2009-05-03
Hey all, 

I recently had to perform a full system restore by untaring the backup i created to root.
Everything works well except for my network card settings.  I statically assigned my network here:

giancarlo@HOME-UBU-SV:~$ cat /etc/network/interfaces
#auto eth0
iface lo inet loopback
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

When I boot the IP is no longer configure on eth0:

eth0      Link encap:Ethernet  HWaddr 00:00:6c:1b:45:fd
           inet6 addr: fe80::200:6cff:fe1b:45fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:515988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:440605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:59940117 (59.9 MB)  TX bytes:145126369 (145.1 MB)
          Interrupt:20 Base address:0x8000

if I manually enter the ip using ifconfig 192.168.1.101 gateway 192.168.1.1 it works fine.  However if I run the init script on bootup or /etc/init.d/networking restart it reverts my settings back to nothing and changes my hostname to localhost.localdomain

Any way to fix this plesae will be greatly apprecitated

---

### Post by john_d13 on 2009-05-03
anyone ?

---

