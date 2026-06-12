---
title: "AutoEthernet connected - no internet connection"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by Skyo on 2012-01-02
Dear forum,

recently I restarted the ubuntu11.10-machine I use at work. The restart was necessary because of security-updates.

Now I do not have any internet access. The computer is connected via ethernetcable and has usually a static ip: 160.45.***.** 

Ifconfig shows now 10.0.1.3 as my ip - i have no clue where this comes from. 
 
```

skyo@host:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse aa:00:04:00:0a:04  
          inet Adresse:10.0.1.3  Bcast:10.0.255.255  Maske:255.255.0.0
          inet6-Adresse: fe80::a800:4ff:fe00:a04/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:434 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:59286 (59.2 KB)  TX bytes:57682 (57.6 KB)
          Interrupt:20 Speicher:d9b00000-d9b20000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:13214 (13.2 KB)  TX bytes:13214 (13.2 KB)

```

Here the output for route -n.

```

skyo@host:~$ route -n
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.0.0     U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```

NetworkManager says AutoEthernet connects succesfully. So there should be a DHCP error? DHCP is set to adjust automatically. 

I tried to un- and replug the cable, delete the AutoEthernet NetworkManager profile and ... simply as that: restart the machine. 

Shall I deliver more information?


PS: I hope the german output does not irritate you. :)

---

