---
title: "Dual boot: windows connects, ubuntu cannot"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by Griff on 2009-02-17
I have a static ip set up for a dual-booting pc (windows xp and ubuntu).  Windows is able to connect to the internet, however, ubuntu cannot.  In fact, under ubuntu, I cannot even ping anything except for 127.0.0.1 and my local ip.  If I try to ping the gateway or anything else I receive an immediate 'connect: Network is unreachable' error message.  Any ideas?

Thanks,
Griff

---

### Post by superprash2003 on 2009-02-17
post output of **ifconfig** from the terminal..and also output of **sudo gedit /etc/network/interfaces**

---

### Post by Griff on 2009-02-18
Sorry for the late reply; the machine in question is in another lab.  Here's the output of ifconfig and /etc/network/infaces
```

from ifconfig:

eth0 Link 	encap:Ethernet HWaddr 00:40:ca:29:06:3e
		inet addr:10.227.237.37 Bcast:10.227.237.255 Mask:255.255.255.0
		inet6: addr: fe80::240::caff:fe29:63e/64 Scope:Link
		UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
		RX packets:86 errors:0 dropped:0 overruns:0 frame:0
		TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000
		RX bytes:13667 (13.3 KB) TX bytes:4297 (4.1 KB)
		Interrupt:11 Base address:0xc000

from /etc/network/interfaces:

auto lo
iface lo inet loopback


iface eth0 inet static
address 10.227.237.37
netmask 255.255.255.0
gateway 128.227.237.1

auto eth0

```
It's an odd local IP to have and not reachable from the outside.  It's something I hope to get changed.

---

### Post by smc18 on 2009-02-18
> address 10.227.237.37
netmask 255.255.255.0
gateway 128.227.237.1

Your host is on a different network. Either Your host should be 128.227.237.37 or your gateway should be 10.227.237.37

assuming you have a simple setup going on.

for example I have

> address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

192.168.1.100 is my host (laptop)
192.168.1.1 is my home router

My internal network address is 192.168.1.0/24 so anything on 192.168.1.x would be on the same network.

---

### Post by smc18 on 2009-02-18
When your in Windows, do you know off-hand what Ip your getting from your router?

Can you include the local IP address of your home router?

---

### Post by Griff on 2009-02-18
> **smc18 said:**
> Your host is on a different network. Either Your host should be 128.227.237.37 or your gateway should be 10.227.237.37


That is exactly what I thought, but the above connection information works on windows.  I didn't try changing the parameters around on the linux install since they worked under windows.  Your suggestion of changing my local ip to 128.227.237.37 worked.  The connecting information above was given to me by the IT dept at my school.  This is interesting.  Thanks a ton for the help.  I shall sing your praises.

Griff

---

### Post by smc18 on 2009-02-18
> I shall sing your praises.

haha thanks! Glad I could help.

---

