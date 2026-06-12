---
title: "2 NICs, 2 HW addr's, 2 IP's, but only 1 NIC responds to both IPs."
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by dhscaresme on 2010-08-23
I've got a recent install of Ubuntu Server 10.04. 
The machine has 2 onboard NICs, the mobo is an old Asus A8n-SLI deluxe. 

All I'm trying to do is get each NIC to have it's own IP address on the same subnet, because I would like to pass requests on a few ports from the outside internet to eth0's address. eth1 will be used by some other internal services.

The interesting thing is that when both NICs are configured like this (in /etc/network/interfaces):
```

auto eth1
iface eth1 inet static
	address 192.168.1.12
	network 192.168.1.0
	netmask 255.255.255.0
	gateway	192.168.1.1
	broadcast 192.168.1.255
	 


auto eth0
iface eth0 inet static
	address 192.168.1.13
	network 192.168.1.0
	netmask 255.255.255.0
	gateway 192.168.1.1
	broadcast 192.168.1.255

```
only eth1 responds to requests, for both 192.168.1.12 and 192.168.1.13.

Check out this "arp -a" output--from another machine on the same subnet--where both .12 and .13 have the same device:
```

[slambo@shineyblack64 ~]$ arp -a
infoserv2 (192.168.1.12) at 00:15:f2:66:7b:b2 [ether] on eth0
? (192.168.1.13) at 00:15:f2:66:7b:b2 [ether] on eth0

```


So my question: what is going on here? And, what is the correct way to define separate IPs for separate NICs, or even better, where should I look to find the info?

Thanks much!
dh

---------------------

Here is some dmesg output for each NIC, just to show drivers and hw addr.
```

root@infoserv2:~# dmesg | grep eth0
[    0.736703] skge eth0: addr 00:15:f2:66:8b:ed

root@infoserv2:~# dmesg | grep eth1
[    1.270740] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x5043 @ 9, addr 00:15:f2:66:7b:b2

```

And some of "ifconfig -a" (I removed only the lo interface).
```

root@infoserv2:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:f2:66:8b:ed  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe66:8bed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85122 (85.1 KB)  TX bytes:1708 (1.7 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:15:f2:66:7b:b2  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe66:7bb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1734898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:885015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2469525412 (2.4 GB)  TX bytes:248753644 (248.7 MB)
          Interrupt:23 Base address:0xa000 

```

---

### Post by Iowan on 2010-08-23
I could be off-base (again), but having two NIC's in the same subnet violates Spanning Tree Protocol. Multiple gateways probably doesn't help either (which interface is used to send traffic to 192.168.1.1?). I suspect (?) the routing table could be used to send traffic where desired...

---

### Post by dhscaresme on 2010-08-24
Yes you're right about having the same gateway defined for multiple interfaces. I've been reading through the threads in the Networking and Wireless section of the forums and there are plenty of other situations similar to this.

It makes sense that having the same gateway listed for two NICs on the same subnet would produce odd behavior. 

Thanks for your help Iowan, you've offered lots of advice here, and I'm sure many appreciate it. I do for sure! Plus I learned something new, and I'll read up on Spanning Tree Protocol.

I'll mark this solved, as I understand why that config wasn't working now. 

--dh

---

