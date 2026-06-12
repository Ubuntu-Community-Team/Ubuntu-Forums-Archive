---
title: "ubuntu not using interfaces file"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by dread22 on 2009-11-11
Hi,

I have to assign a static address for my NIC on my ubuntu box so i edited the /etc/interfaces file to reflect this.

When I run /etc/init.d/networking restart it appears to start properly but no interfaces get created and all I see with the ifconfig command is the loopback device.

Any ideas?

---

### Post by sinurge on 2009-11-11
> **dread22 said:**
> Hi,

I have to assign a static address for my NIC on my ubuntu box so i edited the /etc/interfaces file to reflect this.

When I run /etc/init.d/networking restart it appears to start properly but no interfaces get created and all I see with the ifconfig command is the loopback device.

Any ideas?
hi,

Can you post a contents of the interfaces file. Also did you put your DNS entries in the resolv.conf file.

---

### Post by falconindy on 2009-11-11
You'll need to post your interfaces file as well as any output from dmesg when you try to restart networking.

---

### Post by Iowan on 2009-11-12
What version are you running?
 Network Manager's manual configuration won't work? 
Does **ifconfig -a** show any difference?
Does interface get IP address via DHCP (drivers are working)?

---

### Post by dread22 on 2009-11-16
My network is such that I have one interface which has 2 IP addresses on two separate subnets.

Here are my files and outputs


```

cat /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.8.2
netmask 255.255.255.0
gateway 192.168.8.1

iface eth0:0 inet static
address 192.168.7.1
netmask 255.255.255.0
network 192.168.7.0
broadcast 192.168.7.255
#gateway 192.168.7.1

```


```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:20:40:be:7f  
          inet addr:192.168.8.2  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe40:be7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10864245 (10.3 MB)  TX bytes:3632415 (3.4 MB)

eth0:0    Link encap:Ethernet  HWaddr 00:13:20:40:be:7f  
          inet addr:192.168.7.1  Bcast:192.168.7.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:199744 (195.0 KB)  TX bytes:199744 (195.0 KB)

```


```

cat /etc/resolv.conf

nameserver 192.168.8.1
nameserver 192.168.8.1

```

dmesg gives me nothing and neither does syslog

---

### Post by Iowan on 2009-11-16
> **dread22 said:**
> ... all I see with the ifconfig command is the loopback device.
What am I missing? It looks like both interfaces (as well as "lo") are showing in **ifconfig**.

---

### Post by dread22 on 2009-11-16
woops sorry

The ifconfig is what I require. I configured it manually via the command line using ifconfig. When I restart the machine the only thing that is created is the loopback device.

I'd prefer not having to go in each time and type the commands especially since there is a way to do it properly.

---

### Post by dread22 on 2009-11-17
figured it out

I forgot to put 

```
auto lo eth0 eth0:0
```

in the interfaces file.

---

### Post by Iowan on 2009-11-17
=D> Wow, right there for all to (not) see, but I missed it anyway. 
Glad you found it!

---

