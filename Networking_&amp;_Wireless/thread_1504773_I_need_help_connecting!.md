---
title: "I need help connecting!"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by Hampton7c on 2010-06-08
I'm Hampton, I have never used Linux before, but looking forward to  this. I have only ever used Microsoft Windows platforms. 

Right now I am deployed in Iraq. I have never seen this before but to  connect to the internet either wired or wireless I have to connect to a  broadband connection as well. I am currently using wireless; I connect  to ISP with wireless but in order to access the internet I have connect  to the wireless connection through my broadband connection(This is where  I enter a user name and password.). I'm not sure why this is, I have  always just plugged an Ethernet cable in and the computer just knew I  guess.

I am using  ubuntu-10.04-netbook-i386.iso that I had put onto a USB  drive. It booted fine, but when I tried accessing the internet I  couldn't. I was able to connect to the ISP, but I couldn't find any  settings for a broadband connection.

My computer is a Acer Aspire One Netbook 250

Intel Atom
CPU N270 @ 1.60GHz
1.60 GHz 1.99 GB of RAM

Network Adapters
Atheros AR 5B95 Wireless Network Adapter
Atheros AR8132 PCI-E Fast Ethernet Controller

---

### Post by Iowan on 2010-06-08
While connected to wireless - before plugging in broadband, check (from a terminal) **route -n** - it's possible that the default route (usually last line - marked UG) is still defined to go through the wired interface. If so, you might check your wireless definition in Network Manager to see if that gateway got stuck in there.

---

### Post by Hampton7c on 2010-06-08
> **Iowan said:**
> While connected to wireless - before plugging in broadband, check (from a terminal) **route -n** - it's possible that the default route (usually last line - marked UG) is still defined to go through the wired interface. If so, you might check your wireless definition in Network Manager to see if that gateway got stuck in there.


Can you go a little more in depth on that? I am not sure what you mean.


Thank You

---

### Post by Iowan on 2010-06-08
Applications>Accessories>Terminal should open up a terminal. At the prompt, enter ```
route -n 
```Results should look something like:```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```The last line shows my gateway is 192.168.1.1 on eth0 (this machine has no wireless). If your gateway is eth0 while connected only to wireless...

---

