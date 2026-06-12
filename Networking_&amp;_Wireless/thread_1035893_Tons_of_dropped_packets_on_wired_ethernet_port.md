---
title: "Tons of dropped packets on wired ethernet port"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by courtarro on 2009-01-10
I just built a new machine running Hardy and I've got a strange network adapter problem. This is on a Gigabyte GA-G31M-ES2L micro ATX motherboard, which supposedly has a Realtek 8111C gigabit network chipset.

```

root@brock:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:1a:8d:86  
          inet addr:10.95.10.121  Bcast:10.95.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe1a:8d86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:291 errors:0 [COLOR="Red"]**dropped:15228110280**[/COLOR] overruns:0 frame:0
          TX packets:342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27669 (27.0 KB)  TX bytes:53974 (52.7 KB)
          Interrupt:253 Base address:0x8000

```

Note the "dropped" value in the RX area. This number grows by billions every few seconds. The network adapter is still functioning, but I worry that there's something wrong under the surface. I should also note that this happens even when the network port isn't connected to anything!

---

### Post by cdtech on 2009-01-10
Try blacklisting the ipv6:
```
sudo gedit /etc/modprobe.d/blacklist
```
and add:
```
blacklist ipv6
```
to the end.

---

### Post by courtarro on 2009-01-10
Thanks **cdtech**, but it turns out this is a driver problem. Shortly after posting, I discovered this great little tutorial and script:

[http://www.jamesonwilliams.com/hardy-r8168.html](http://www.jamesonwilliams.com/hardy-r8168.html)

Apparently the included kernel in Hardy incorrectly recognizes the port and uses the wrong driver. This fella's script replaces the existing kernel driver with a new one from Realtek that behaves properly.

Someone (Ubuntu? the kernel team?) needs to fix the existing driver!

---

