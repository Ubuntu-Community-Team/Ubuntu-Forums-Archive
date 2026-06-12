---
title: "Offline after updating the badger to dapper"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by AGS on 2006-06-16
Hi there!

I installed a working Breezy Badger some weeks ago and did the automatic update to Dapper Drake in the first week of june. Since the reset this installation of Ubuntu is offline. I did some asking in a german forum, but to no avail - still does not connect to the 'Net. Another Ubuntu I use, a updated former BetaFlight7 of the Drake, works just fine, so I think it has to be some file that has changed between Badger and Drake.

The rather strange thing is, pppoeconf works just fine - it detects my network card that directly connects to my DSL-Modem, asks for username and password for this connection and tries to start "a" connection - which fails with the comment " *Linux kernel does not support PPPoE -- are you running 2.4.x?* " Just the same happens when I try to do a *pon* manually. When I try to *poff* it tells me that there is no connection to be terminated.

*ifconfig -a* showed this:

```
andy@ubuntu:~$ ifconfig -a 
eth0      Protokoll:Ethernet  Hardware Adresse 00:0A:E6:49:96:E5 
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:11 Basisadresse:0xd400 
 
eth1      Protokoll:Ethernet  Hardware Adresse 00:02:2A:D7:D6:5E 
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:5 Basisadresse:0xc800 
 
eth2      Protokoll:Ethernet  Hardware Adresse 00:30:84:0B:22:18 
          inet6 Adresse: fe80::230:84ff:fe0b:2218/64 Gültigkeitsbereich:Verbindung 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b) 
          Interrupt:11 Basisadresse:0xc400 
 
lo        Protokoll:Lokale Schleife 
          inet Adresse:127.0.0.1  Maske:255.0.0.0 
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:460 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:460 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:34360 (33.5 KiB)  TX bytes:34360 (33.5 KiB) 
 
sit0      Protokoll:IPv6-nach-IPv4 
          NOARP  MTU:1480  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
 
andy@ubuntu:~$
``` 
The user from the german forum said it looked good and should work. BTW: I connected to the modem via eth2; eth0 is a non-used built-in chip I can't locate/use, and eth1 is for my homeLAN with my wifes computer.

We tried *lsmod* which showed that module pppoe was missing. We put it backin whith *sudo modprobe pppoe *but nothing changed - still says the kernel does not support pppoe.

I hope I put everything in the correct oder so anyone with the proper knowledge can really read it - and help! I really don't  want to erase that "old" installation to install a completely new Drake. It took me five tries to put the badger onto my harddisk!

So, can anyone help me and put my upgraded badger (is it a dapper badger, now? ;) )back into the internet?

---

