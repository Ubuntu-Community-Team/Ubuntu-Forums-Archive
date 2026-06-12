---
title: "Attansic L1 Gigabit @9.04 AMD64 not working"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by petzler on 2009-06-15
Hi,

I've installed a new KUbuntu9.04 amd64 where the network doesn't work. The same Problem with ubuntu and mythbuntu (as aspected).

I've here an ASUS P5K-SE/EPU Board Rev. 1.00g.

```
 
$ lspci -n | grep 1969
02:00.0 0200: 1969:1048 (rev b0)

```

Which means following [this page](http://www.hogchain.net/attansic/attansic.html#variants) I have the L1 Chip.

```

$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:22:15:09:9c:4d  
          inet Adresse:192.168.1.3  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::222:15ff:fe09:9c4d/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1320  Metrik:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:1
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:3355 (3.3 KB)  TX bytes:5573 (5.5 KB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:2760 (2.7 KB)  TX bytes:2760 (2.7 KB)

```

```

$ lsmod | grep atl1
atl1                   45448  0 
mii                    14464  1 atl1

```

and

```

$ dmesg | grep atl1
[    3.052614] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.052624] atl1 0000:02:00.0: setting latency timer to 64
[    3.052648] atl1 0000:02:00.0: version 2.1.3
[   11.437815] atl1 0000:02:00.0: irq 2299 for MSI/MSI-X
[   11.437901] atl1 0000:02:00.0: eth0 link is up 1000 Mbps full duplex
[   16.672933] atl1 0000:02:00.0: irq 2299 for MSI/MSI-X
[   16.672989] atl1 0000:02:00.0: eth0 link is up 1000 Mbps full duplex

```

So all looks normal. I did try the 2.6.30 kernel mainstream as well with the same result:

```

$ uname -a
Linux tux64 2.6.30-999-generic #1244710815 SMP Thu Jun 11 09:07:08 UTC 2009 x86_64 GNU/Linux

```

The problem is weak: I can ping into the network, e.g. ping. [www.ubuntu.com](www.ubuntu.com) successfully, or can establish a ftp connection/login - but the dir command failed. HTTP failed also.
A dist upgrade doesn't work as well (apt-get can't establish the repositories).

On windows all is working! Therefore I don't believe that the problem is related to a network cable. RAM is 2GB; anyway, all the problems mentioned at [Attansic L1 Gigabit Ethernet driver for Linux](http://www.hogchain.net/attansic/attansic.html) page are gone with newer kernels.

What happens to me? How to solve it?

Thanks,
Olaf

---

### Post by petzler on 2009-06-16
setting MTU to 1492 or even 1200 doesn't solve the problem. Any ideas?

---

### Post by skibler on 2009-07-13
I have the same issue. It looks like it should be working, but it does not.

It worked fine in gentoo for the past 12+ months.

Please let me know what information could be provided to help solve this!

---

### Post by skibler on 2009-07-13
This is quite frustrating! The router sees the PC and assigns it an IP address.

---

