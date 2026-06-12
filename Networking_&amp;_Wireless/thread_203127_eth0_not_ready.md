---
title: "eth0 not ready?"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by falkenberg_cph on 2006-06-24
What is going on with my internet. Right now i am writing from my xp partition.
I have been on the internet via cable since i got dapper, but suddenly its gone.

it says eth0 not ready. route -n gives me nothing.
Whats going on? the modem is not dead, since i can use it in xp.

:confused: 
Carsten

---

### Post by scxtt on 2006-06-24
when it's "not ready" what does the "ifconfig eth0" give you?
```
:> ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:D4:CB:7E:54
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fecb:7e54/64 Scope:Link
          **UP** BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:217974367 (207.8 MiB)  TX bytes:6801672 (6.4 MiB)
          Interrupt:217 Base address:0xe400
```is there a chance it's just going down for some reason? -- and if it is, what does "ifup eth0" give you?

---

### Post by falkenberg_cph on 2006-06-24
well, ifconfig doesnt report any errors. ifup says eth0 is already configured.
Id like to send you my terminal messages. i have saved them in a openoffice file, but i dont know how to reach my linux partition from the xp partition.

Carsten

---

### Post by scxtt on 2006-06-24
do you have any removable media (flash drive, maybe a CD-RW?) ...
how's your XP partitioned, NTFS?

---

### Post by falkenberg_cph on 2006-06-24
Doh :-? 
here we go:

carsten@carsten-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:2F:AC:D4:CD
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xee00

carsten@carsten-laptop:~$ sudo ifup eth0
Password:
ifup: interface eth0 already configured

carsten@carsten-laptop:~$ sudo ifup eth0
Password:
ifup: interface eth0 already configured

firestarter: failed to start the firewall
the device eth0 is not ready
please check your network device settings and make sure your internet connection is active.

---

### Post by scxtt on 2006-06-24
what do you see under "System --> Administration --> Networking" for your eth0?

does it show that it's active? (might just be a report on it being "UP") ...

can you down ("sudo ifdown eth0") it w/o error?

---

