---
title: "Multiple IP Addresses wont stick around after reboot"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by v0idnull on 2009-09-30
I have several IP addresses on eth0. Data center provider offered me:

```

64.15.74.64 	Network IP 		
64.15.74.65 	Useable IP 		
64.15.74.66 	Useable IP 		
64.15.74.67 	Useable IP 		
64.15.74.68 	Useable IP 		
64.15.74.69 	Useable IP 		
64.15.74.70 	Useable IP 		
64.15.74.71 	Broadcast IP

```

And there is one VLAN IP address. So I to setup my interfaces. I first start with 64.15.74.65

```
v0idnull@voidnull01:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 67.212.69.237
	netmask 255.255.255.224
	network 67.212.69.224
	broadcast 67.212.69.255
	gateway 67.212.69.225
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 64.15.64.91 64.15.64.92
	dns-search localdomain

auto eth0:1
iface eth0:1 inet static
	address 64.15.74.65
	netmask 255.255.255.248
	broadcast 64.15.74.71
	network 64.15.74.64
```

Should be fine? ifconfig -a shows everything properly. But then I reboot and I get this:

```
v0idnull@voidnull01:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:1f:aa:f4  
          inet addr:67.212.69.237  Bcast:67.212.69.255  Mask:255.255.255.224
          inet6 addr: fe80::21c:c0ff:fe1f:aaf4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:11667 (11.6 KB)  TX bytes:7428 (7.4 KB)
          Memory:50300000-50320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1176 (1.1 KB)  TX bytes:1176 (1.1 KB)
```

So my question is: wtf? I don't really know what's wrong here. I'd appreciate any help on the matter, thank you

---

### Post by kreggz on 2009-10-03
try removing network manager, it overwrites interfaces file

apt-get remove --purge network-manager

---

