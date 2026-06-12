---
title: "Network connections fail 50% of the time"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by skgu67 on 2006-07-12
[I'm actually running Debian Sarge, but haven't been able to get an answer there, so I'm cross-posting since I suspect the ultimate answer would be the same under Debian or Ubunutu]

I recently installed Debian (Sarge) on a refurbished IBM x300 machine that has dual ethernet ports.  I only use one of the connections so my /etc/network/interfaces reads:

> # The loopback network interface
> auto lo
> iface lo inet loopback
>
> # The primary network interface
> auto eth0
> iface eth0 inet static
>         address 192.168.0.155
>         netmask 255.255.255.0
>         network 192.168.0.0
>         broadcast 192.168.0.255
>         gateway 192.168.0.1
>         mtu 1492

[The mtu is set to 1492 to be compatible with my router and which in turn has the setting because of a finicky mail server of a family member]

For some reason that I completely fail to understand, when I reboot from a working status I always end up unable to connect to the network. I cannot even ping machines on my LAN.  But a subsequent reboot almost always re-establishes good network connections.  (Sometimes I have to reboot two or three times to get there).

Does anybody have any thoughts?

(I'm attaching the output of ifconfig in a working condition.  I haven't yet captured the output when the network connection is down).

> eth0      Link encap:Ethernet  HWaddr 00:02:55:FA:66:09
>           inet addr:192.168.0.155  Bcast:192.168.0.255 Mask:255.255.255.0
>           UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
>           RX packets:1495290 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:401768 errors:0 dropped:0 overruns:0 carrier:0
>           collisions:0 txqueuelen:1000
>           RX bytes:1973801104 (1.8 GiB)  TX bytes:225324078 (214.8 MiB)
>           Interrupt:10 Base address:0xbc00 Memory:df0c1000-df0c1038
>
> lo        Link encap:Local Loopback
>           inet addr:127.0.0.1  Mask:255.0.0.0
>           UP LOOPBACK RUNNING  MTU:16436  Metric:1
>           RX packets:655 errors:0 dropped:0 overruns:0 frame:0
>           TX packets:655 errors:0 dropped:0 overruns:0 carrier:0
>           collisions:0 txqueuelen:0
>           RX bytes:61300 (59.8 KiB)  TX bytes:61300 (59.8 KiB)

Thanks in advance,

Seth Green

---

### Post by mips on 2006-07-12
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

