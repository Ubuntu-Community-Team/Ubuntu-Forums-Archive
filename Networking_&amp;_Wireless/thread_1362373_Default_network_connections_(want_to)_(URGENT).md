---
title: "Default network connections (want to) (URGENT)"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by friendishan on 2009-12-23
I want to make my PC like it was tomorrow (running my connection)

Or i guess i will like to re-install network connections :P

or maybe put to to total default .

Thank YOU

PLEASE HELP ME :confused::confused::confused:

THE ACTUAL PROBLEM :-
i have 2 net connections (1 which i am using now) i have another cable connection which is not getting connected though it gets connected in win XP it says disconnected here please help! (it has to be automatic with DHCP)

um.. more information,

I use the Auto eth0 to connect to the net and it always worked!

but today it dosen't (i did not do anything funny yesterday)
for 3 days it wasn't working in windows XP but today when i talked to the ISP provider it worked but iit isn't working in ubuntu 

I am using ubuntu 9.04 jaunty jackalope!

---

### Post by garikaib on 2009-12-23
Run the command:
sudo netstat -r

You will get the current routing table information for example on mine i got:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

192.200.1.21    *               255.255.255.255 UH        0 0          0 ppp0
localnet        *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.200.1.21    0.0.0.0         UG        0 0          0 ppp0
default         claremontestate 0.0.0.0         UG        0 0          0 eth0

So on mine the default route is 192.200.1.21 if I wanted to change the default interface from ppp0 to eth0 I would use the command

sudo route add default eth0

Just substitute eth0 to the interface you want

---

### Post by friendishan on 2009-12-23
I uninstalled ubuntu 9.04 and freshly installed 9.10 (still no help)

i tried your method

all i get is
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

Any more help?

---

### Post by Iowan on 2009-12-23
> **friendishan said:**
> I uninstalled ubuntu 9.04 and freshly installed 9.10 (still no help)Probably need to start over with information. 
Post results of **lshw -C network** and **ifconfig -a**

---

### Post by friendishan on 2009-12-23
ishan@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: eth0
       version: 10
       serial: 4c:00:10:3a:82:5c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:19 ioport:b800(size=256) memory:ff8ffc00-ff8ffcff memory:40000000-4000ffff(prefetchable)


ishan@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 4c:00:10:3a:82:5c  
          inet6 addr: fe80::4e00:10ff:fe3a:825c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25371030 (25.3 MB)  TX bytes:5334954 (5.3 MB)
          Interrupt:19 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ishan@ubuntu:~$ 


These were the results :)

Thank you please reply ASAP!

---

