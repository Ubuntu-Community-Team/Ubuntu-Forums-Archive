---
title: "problem with broadband connection"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by PROFE$$OR on 2010-04-28
hi guys 
i have problem with broadband connection when i connect to internet in every 5 minute and the internet make disconnect .
i connect to internet by using this commnad .
```
pppoeconf
```
and i type username and password .
and connect by using
```
pon dsl-provider
```
 
so can you slove this problem please :confused::confused:

---

### Post by PROFE$$OR on 2010-04-28
is there anyone can help me ????

can i make automatic broadband connection

---

### Post by dineshs on 2010-04-29
There are modems capable of storing username and password(PPPoE mode).Your ISP can tell you whether your modem can do this.If so you need not use pppoeconf or pon dsl-provider.The connection will always be on once you program your modem in PPPoE mode.

---

### Post by PROFE$$OR on 2010-04-29
but i was made in windows 7 broadband connection and type my username and password when i click connect he will connecto auto there is no way to connect in my ISP exept broadband connection could you help me ??

---

### Post by dineshs on 2010-04-29
I hope you are using a modem configured in bridge mode.In that case you need a PPPoE connection (Something similar to a dialup connection but without phone no.ie username and password alone).This is what you are doing now.But you can make your modem do this .For this  configure your modem in PPPoE mode,and store username and password there.If you do so you get an always on connection.Please open a terminal(applications-accessories-terminal)and post the results of
```
ifconfig -a
```
```
route -n
```
Please let us know what modem you are using.ie its model name

---

### Post by PROFE$$OR on 2010-04-29
this the output of first command
```
eth0      Link encap:Ethernet  HWaddr 00:26:9e:01:2d:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:568 (568.0 B)  TX bytes:568 (568.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.20.30.41  P-t-P:10.20.30.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1480  Metric:1
          RX packets:9514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9395683 (9.3 MB)  TX bytes:1437528 (1.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:1f:73:4f  
          inet addr:10.20.1.177  Bcast:10.20.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe1f:734f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12996978 (12.9 MB)  TX bytes:1822680 (1.8 MB)

wlan1     Link encap:Ethernet  HWaddr 00:22:5f:af:58:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-5F-AF-58-E2-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster1  Link encap:UNSPEC  HWaddr 00-C0-CA-1F-73-4F-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and this is the second command
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.20.30.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.20.1.0       0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

i use Realtek RTL8187 :confused::confused:

---

### Post by PROFE$$OR on 2010-04-30
bump

---

