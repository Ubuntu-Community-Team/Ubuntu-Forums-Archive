---
title: "Can't get Ethernet Lan to work"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by ACarib on 2006-04-14
Installed Ubuntu 5.10 Great...

However I can't get my ethernet Lan to work... any advice anyone.

---

### Post by ubernoob on 2006-04-14
try writing "ifconfig" and post the output here

---

### Post by ACarib on 2006-04-14
Here is the output from an ifconfig -a

gcj@GCJUbuntu:~$ ifconfig -a
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3337952 (3.1 MiB)  TX bytes:3337952 (3.1 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by mips on 2006-04-14
Your ethernet card is not listed in the above output and therefore probably not detected.

Follow this guide and let us know where youget stuck.
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

---

### Post by ACarib on 2006-04-18
Thanks for the link mips.... I will certainly check try it....

---

### Post by qw3rty on 2006-04-19
Is it an ISA card?

---

