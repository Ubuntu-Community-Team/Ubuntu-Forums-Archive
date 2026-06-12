---
title: "What's up with network interfaces?"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by Thund3rstruck on 2011-04-02
Hi guys, 

Can someone please explain to me why none of the linux networking commands work for me on Linux Mint 9 (Ubuntu 10.04)?

```

$ sudo ifdown eth0
ifdown: interface eth0 not configured
$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0
$ sudo iwlist wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help')

```

All my usual networking commands fail but network is working fine.

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:2b:bf:c8  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe2b:bfc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6443883 (6.4 MB)  TX bytes:1319145 (1.3 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.174.1  Bcast:172.16.174.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.131.1  Bcast:172.16.131.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:0a:57:39  
          inet addr:192.168.2.109  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe0a:5739/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1286452 (1.2 MB)  TX bytes:5161 (5.1 KB)

```

I'm not understanding why my /etc/network/interfaces file doesn't define my interfaces but the network is working

```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

How the heck do I manage interfaces in Ubuntu based machines (from the command line)??

Thanks!

---

### Post by Thund3rstruck on 2011-04-02
Ugh... so apparently users have to manually configure /etc/network/interfaces (ref: ifdown man page)

This fixed it:

```

$ cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The wireless network interface
auto wlan0
iface wlan0 inet dhcp


```

---

### Post by Perfect Storm on 2011-04-02
Hi Thund3rstruck

There's a Linux Mint forum to get help with your distro.
You'll find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


regards
A.I. Dude
Ubuntu Forum Staff

---

