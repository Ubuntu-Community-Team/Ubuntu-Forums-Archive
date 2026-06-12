---
title: "Network problem: dhcp works, static doesn't"
date: 2013-02-24
forum: Networking &amp; Wireless
---

### Post by gkuser on 2013-02-24
Hi members,
I have network issue, I don't know how to define static IP for my Ubuntu server 12.10, which run on OracleVM VirtualBox.
According to my notes, which I have wrote down, when I playing with Ubuntu Server 8.xx the file: /etc/network/interfaces should be like this

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.30
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

In this file I also add new line (before I have it in /etc/resolv.conf)
dns-nameservers xxx.xxx.xxx.xxx 192.168.1.1


So, what else I missed? If I use instead static dhcp, server works just fine.

Any ideas?
Thank you in advance for your time and help.

Cheers,
Gregor

---

### Post by chili555 on 2013-02-24
Please try this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.30
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers xxx.xxx.xxx.xxx 192.168.1.1
```Now reload:```
sudo ifdown eth0 && sudo ifup eth0
ifconfig
```Do you have the correct address? Are you connected?```
ping -c3 www.google.com
```I assume Network Manager is not installed or running on this server and I assume 192.168.1.30 is outside the range of the DHCP server in the router. I suspect it isn't outside.

---

### Post by gkuser on 2013-02-24
Hi,

Thank you for help, but it didn't solve my problem.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 80:00:00:e3:6b:d0  
          inet addr:192.168.1.101  Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fee3:6bd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1669345 (1.6 MB)  TX bytes:301602 (301.6 KB)
          Interrupt:20 Memory:f7f00000-f7f20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74443 (74.4 KB)  TX bytes:74443 (74.4 KB)
```


ping -c3 [www.google.com](www.google.com)
```
ping: unknown host www.google.com
```


Then I change back to dhcp.
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 80:00:00:e3:6b:d0  
          **inet addr:10.0.2.15  Bcast:10.0.2.255** Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fee3:6bd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1669345 (1.6 MB)  TX bytes:301602 (301.6 KB)
          Interrupt:20 Memory:f7f00000-f7f20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74443 (74.4 KB)  TX bytes:74443 (74.4 KB)
```

Where ubuntu get this IP, this is not in my range. Maybe I should check VirtualBox.

**********

I think IP is not a problem. The same IP I had in Ubuntu server 8.xx and it was fine. Just to be sure I changed to 192.168.1.101, but i get the same error.
In the same network I have another WIN server with IP 192.168.1.20 without problems.

Any other idea?

As I said, maybe is VM problem.


Cheers,
Gregor

---

### Post by chili555 on 2013-02-24
> As I said, maybe is VM problem.Indeed. Network interfaces in virtual machines are bridged to the host's actual interface. They are not themselves actual interfaces. [http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)> A virtual machine with NAT enabled acts much like a real computer that connects to the Internet through a router. The "router", in this case, is the VirtualBox networking engine, which maps traffic from and to the virtual machine transparently. In VirtualBox this router is placed between each virtual machine and the host. This separation maximizes security since by default virtual machines cannot talk to each other.I am not very experienced in VMs, so I may not be able to offer further real help.

---

### Post by steeldriver on 2013-02-24
You can't treat interfaces on a VM as just the same as any other interface on your LAN (unless you bridge them)

In particular, iirc Oracle's VirtualBox defaults to a NAT configuration which effectively means it runs a virtual router on the host, with a default network in the 10.0.2.xxx range

You can change that to bridged mode via the 'Devices --> Network adapters...' menu - otherwise afaik you *will* need to use an IP address within the virtual NAT range

See [http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

### Post by gkuser on 2013-02-24
Yes, you are right. How I didn't noticed that. I have like you said NAT.

I changed to Bridge and ta-ta :guitar:

Thank you both of you, for your time and help.

Cheers,
Gregor

---

