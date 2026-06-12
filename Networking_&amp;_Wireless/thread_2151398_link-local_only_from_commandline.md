---
title: "link-local only from commandline"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by jpflathead on 2013-06-04
How do I configure eth1 from the commandline as a IPv4 link-local only? I need that interface to be available for a virtual machine running a firewall.
The interface should not have an IP address, that is the way I have it on another linux box. But that one has X installed and this doesn't.
If the interface is not 'up' the firewall cannot use it.
This is the ifconfig from my working machine:

eth1      Link encap:Ethernet  HWaddr 00:04:76:8f:64:90 

          inet6 addr: fe80::204:76ff:fe8f:6490/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:12853125 errors:0 dropped:0 overruns:0 frame:0

          TX packets:13030472 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000

          RX bytes:1090211806 (1.0 GiB)  TX bytes:3661175688 (3.4 GiB)

          Interrupt:22 Base address:0x6c00

As you see it has no IPv4 address.

---

### Post by sanderj on 2013-06-04
I'm quite sure you can set it from SUPER-key -> "Network" -> Wired -> Options -> IPv4 Settings -> Method: Link-Local Only

---

### Post by jpflathead on 2013-06-05
I was not explicit enough: There is no GUI on the system I ask this for. Otherwise I would not have the problem.
The mobo is an Intel DN2800MT and the video chip on that board has (almost) no support under linux. 
And as it is a headless server I don't care that much although I will not buy the same board for a project like this again.

---

### Post by sanderj on 2013-06-05
> **jpflathead said:**
> I was not explicit enough: There is no GUI on the system I ask this for.


Ah, sorry. If you have a Ubuntu-with-GUI, you can do it the GUI-way ther, and then check what changed in the /etc-network-files.

HTH

---

### Post by steeldriver on 2013-06-05
Can't you just set the IPv4 address somewhere in the link-local reserved range (169.254.x.x)? I think that's all the network-manager GUI does for link-local (although no point looking in /etc/network/ for that, since network-manager uses its own config files in /etc/NetworkManager/)

---

