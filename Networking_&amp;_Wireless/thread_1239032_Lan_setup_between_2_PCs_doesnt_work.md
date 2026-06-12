---
title: "Lan setup between 2 PCs doesnt work"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by ishant14 on 2009-08-13
Hello,
I am using 9.04 updated yesterday on 1 pc & 8.04 non updated on the other.

I have set them up as follows - 

PC1 - ubuntu 9.04

> ishan@ishan-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:09:6b:af:45:a4  
          inet addr:10.10.1.0  Bcast:10.10.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:feaf:45a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3438537 (3.4 MB)  TX bytes:564830 (564.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81800 (81.8 KB)  TX bytes:81800 (81.8 KB)

pan0      Link encap:Ethernet  HWaddr fe:77:ce:0e:b4:7b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



> ishan@ishan-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 10.10.1.0
netmask 255.255.255.0
gateway 10.10.1.1
broadcast 10.10.1.255

auto eth0

---------------------------

PC2 ubuntu 8.04

---------------------------

> ishan@ishan-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



iface eth0 inet static
address 10.10.1.20
netmask 255.255.255.0
gateway 10.10.1.1
broadcast 10.10.1.255

auto eth0

> ishan@ishan-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:09:6b:12:0f:5e  
          inet addr:10.10.1.20  Bcast:10.10.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:6bff:fe12:f5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25534 (24.9 KB)  TX bytes:27061 (26.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:30:f1:04:09:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:58362 (56.9 KB)  TX bytes:58362 (56.9 KB)


--------------------------------------------------

I cannot ping the other from the first.

Where am I going wrong ?

Thanks in advance,

Ishan

---

### Post by Adina on 2009-08-13
> shan@ishan-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 10.10.1.0
netmask 255.255.255.0
gateway 10.10.1.1
broadcast 10.10.1.255

auto eth0 

I think your problem is that the address 10.10.1.0 is supposed to be the network address and not the ip address for your computer.

try this:


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.10.1.10
netmask 255.255.255.0
network 10.10.1.0
gateway 10.10.1.1
broadcast 10.10.1.255


and also add network 10.10.1.0 to your /etc/network/interfaces file on the other machine.

---

### Post by Iowan on 2009-08-13
Are those the only two machines on the network? If so, you *might* need crossover cable, and the gateway address probably needs some adjustment. If there is a router, it's local address (10.10.1.1?) would (probably) be the gateway.

PC2 has 2 network cards?

---

