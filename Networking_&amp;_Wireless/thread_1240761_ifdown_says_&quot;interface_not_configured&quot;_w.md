---
title: "ifdown says &quot;interface not configured&quot; when configured"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by dmizer on 2009-08-15
This is probably a bug, but I thought I'd try here and see if anyone else had input.

Ifconfig shows this:
```
# ifconfig
eth3      Link encap:Ethernet  HWaddr 00:02:2d:ba:b6:ee  
          inet addr:192.168.3.6  Bcast:255.255.255.255  Mask:255.255.255.128
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11283339 (10.7 MB)  TX bytes:2590060 (2.4 MB)
          Interrupt:10 Base address:0xa080
```
The device is clearly connected, as I can ping and browse:
```
# ping www.google.com
PING www.l.google.com (66.249.89.147) 56(84) bytes of data.
64 bytes from jp-in-f147.google.com (66.249.89.147): icmp_seq=1 ttl=229 time=48.2 ms
64 bytes from jp-in-f147.google.com (66.249.89.147): icmp_seq=2 ttl=229 time=48.7 ms
64 bytes from jp-in-f147.google.com (66.249.89.147): icmp_seq=3 ttl=229 time=50.2 ms
```
But when I try to take the device down via CLI:
```
# ifdown eth3
ifdown: interface eth3 not configured
```

I have uninstalled network-manager, and no other GUI network configuration tool is currently installed but the problem persists.

---

### Post by MaindotC on 2009-08-15
ifdown or ifup has never worked for me so I've always used:
```

ifconfig up
or
ifconfig down

```
acheieves the same result imho

---

### Post by kerry_s on 2009-08-15
do you got your settings in /etc/network/interfaces ?

---

### Post by dmizer on 2009-08-15
> **kerry_s said:**
> do you got your settings in /etc/network/interfaces ?

Yes, I do.

```
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth3
iface eth3 inet dhcp
```

---

### Post by Iowan on 2009-08-15
Curious broadcast address (probably unrelated, since the interface seems to work).

---

### Post by unimous on 2013-01-04
> **Iowan said:**
> Curious broadcast address (probably unrelated, since the interface seems to work).

Why you say that broadcast address is "Curious"?

---

### Post by coffeecat on 2013-01-04
Old thread - closed.

---

