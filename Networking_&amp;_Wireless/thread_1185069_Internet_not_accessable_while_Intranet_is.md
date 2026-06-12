---
title: "Internet not accessable while Intranet is"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Raptor354 on 2009-06-11
I just installed Ubuntu Server on a box I had sitting around.

After installing it, I configured the network interfaces and DNSs (both manually, of course).  There are 3 adapters in it: 2 onboard gigabit ones and an old Intel 10/100 card.  They all get recognized and they all can access the local network, as well as be accessed by computers on the local network.

The problem comes when I try and ping Google, for example.  It does resolve, but nothing comes back.  No errors.  No response.  Not even "destination unreachable"!

One symptom to note, it seems to like to reload Samba every few minutes.

Also, when I run "dhclient eth<some adapter number>", it works on that adapter, even after reboot.  I want it to be a static address, like all web servers should be.

Any thoughts?

Raptor354

Edit: Removed Samba.  No change.

---

### Post by gombadi on 2009-06-11
> 
The problem comes when I try and ping Google, for example. It does resolve, but nothing comes back. No errors. No response. Not even "destination unreachable"!


Sounds like a default gateway issue.
Are you able to ping the gateway?
Any firewall on the machine?

Can you show us the following
```

/sbin/ifconfig -a
cat /etc/network/interfaces
route -n
sudo iptables -vnL

```

---

### Post by Raptor354 on 2009-06-11
Yes, I can ping the gateway.  I don't think there's a firewall on it, but there should be.

Well, you asked for it.

```
root@ffsiwebsrv:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:db:f8:ba:14
          inet addr:192.168.11.114  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fef8:ba14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:293112 (293.1 KB)  TX bytes:125911 (125.9 KB)
          Interrupt:253 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:19:db:f7:30:5e
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5888 (5.8 KB)  TX bytes:468 (468.0 B)
          Interrupt:21 Base address:0x400

eth2      Link encap:Ethernet  HWaddr 00:a0:c9:e7:8e:70
          inet addr:192.168.11.128  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c9ff:fee7:8e70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:821 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1253964 (1.2 MB)  TX bytes:83652 (83.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:18240 (18.2 KB)  TX bytes:18240 (18.2 KB)

root@ffsiwebsrv:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#       address 192.168.11.5
#       netmask 255.255.255.0
#       network 192.168.11.0
#       broadcast 192.168.11.255
#       gateway 192.168.11.1

# The backup network interface
auto eth1
iface eth1 inet dhcp
#iface eth1 inet static
#       address 192.168.11.6
#       netmask 255.255.255.0
#       network 192.168.11.0
#       broadcast 192.168.11.255
#       gateway 192.168.11.1

# The last-ditch-effort network interface
auto eth2
iface eth2 inet dhcp
root@ffsiwebsrv:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.11.1    0.0.0.0         UG    100    0        0 eth2
0.0.0.0         192.168.11.1    0.0.0.0         UG    100    0        0 eth0
root@ffsiwebsrv:~# iptables -vnL
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 
root@ffsiwebsrv:~#
```

---

### Post by gombadi on 2009-06-12
```

root@ffsiwebsrv:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.11.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.11.1    0.0.0.0         UG    100    0        0 eth2
0.0.0.0         192.168.11.1    0.0.0.0         UG    100    0        0 eth0

```

You have two interfaces on the same network. Both have a route to the default gateway. In situations like this packets get lost quite easy - the kernel says do I send this pack on eth0 or eth2, why am I geting replies for on a different interface I sent the packet. Confusion all round.

Is there a reason you want to have two interfaces on the same network?
If you need both interfaces on the same network you will have to use bonding.

---

### Post by superprash2003 on 2009-06-12
what happens when you try to ping 208.67.222.222 ?

---

### Post by Raptor354 on 2009-06-12
I just wanted network redundancy.  As stated above, this will be a web server and I don't want a network card failure to kill my site for any length of time.

Eventually, I will have 2 different physical internet connections and one going to my local network.

It seems to work.  Thanks for the info.  Is there a way so that I can have two network interfaces on the same network?

---

### Post by Iowan on 2009-06-12
A few months ago, I'd have said "NO! Plays havoc with routing" (in fact, I did...), but I've seen a couple of threads that suggest it might be possible with some intricate iptable rules.

---

### Post by gombadi on 2009-06-12
> 
Is there a way so that I can have two network interfaces on the same network? 


Yes - bonding. Do a google or forum search. It is a way to get two interfaces working as one.

> 
but I've seen a couple of threads that suggest it might be possible with some intricate iptable rules


As Iowan says there may be other ways to do it but they seem to violate my KIS rule (Keep it simple).

---

