---
title: "Wired Working But Wireless =&gt; with connection no internet access"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by Mr.Gosh on 2012-06-11
Well I searched for some time and see many people who seem to have problems with networking in ubuntu, bat my problem wasn't there, so I try to discribe it:

I can access internet allways with the ethernet cable attached.
I can see all wireless networks around.
I can establish an connection to my network and i do get an ip adress

but i can' reach the internet through the wireless network
I can't even ping my router.

At first i thought that its a problem of my new thinkpad - and changed my wifi channel on my router - nothing changed.

The notebook works everywhere else, and all other machines work on the wifi.

I've got an [lenovo x220 tablet]("http://www.thinkwiki.org/wiki/Category:X220_Tablet")
the output if ifconfig in wireless mode is:
```
ifconfig 
eth0      Link encap:Ethernet  Hardware Adresse f0:de:f1:9b:fb:49  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:5817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4806 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:4710382 (4.7 MB)  TX-Bytes:655284 (655.2 KB)
          Interrupt:20 Speicher:f2500000-f2520000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:904 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:75387 (75.3 KB)  TX-Bytes:75387 (75.3 KB)

wlan0     Link encap:Ethernet  Hardware Adresse a0:88:b4:28:fc:f8  
          inet Adresse:192.168.1.40  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::a288:b4ff:fe28:fcf8/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:924 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:46241 (46.2 KB)  TX-Bytes:95394 (95.3 KB)
``` 

and the output of ```
mtr -n 8.8.8.8 --report -c4
``` is

```
mtr -n 8.8.8.8 --report -c4
HOST: goshbook                    Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  2.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  3.|-- 195.71.244.210             0.0%     4   20.3  20.4  20.1  20.7   0.3
  4.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
```


what to do? Thanks.

---

### Post by wildmanne39 on 2012-06-23
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by hoanghiepmd on 2012-06-24
> **Mr.Gosh said:**
> Well I searched for some time and see many people who seem to have problems with networking in ubuntu, bat my problem wasn't there, so I try to discribe it:

I can access internet allways with the ethernet cable attached.
I can see all wireless networks around.
I can establish an connection to my network and i do get an ip adress

but i can' reach the internet through the wireless network
I can't even ping my router.

At first i thought that its a problem of my new thinkpad - and changed my wifi channel on my router - nothing changed.

The notebook works everywhere else, and all other machines work on the wifi.

I've got an [lenovo x220 tablet]("http://www.thinkwiki.org/wiki/Category:X220_Tablet")
the output if ifconfig in wireless mode is:
```
ifconfig 
eth0      Link encap:Ethernet  Hardware Adresse f0:de:f1:9b:fb:49  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:5817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4806 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:4710382 (4.7 MB)  TX-Bytes:655284 (655.2 KB)
          Interrupt:20 Speicher:f2500000-f2520000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:904 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:75387 (75.3 KB)  TX-Bytes:75387 (75.3 KB)

wlan0     Link encap:Ethernet  Hardware Adresse a0:88:b4:28:fc:f8  
          inet Adresse:192.168.1.40  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::a288:b4ff:fe28:fcf8/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:924 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:46241 (46.2 KB)  TX-Bytes:95394 (95.3 KB)
``` 

and the output of ```
mtr -n 8.8.8.8 --report -c4
``` is

```
mtr -n 8.8.8.8 --report -c4
HOST: goshbook                    Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  2.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
  3.|-- 195.71.244.210             0.0%     4   20.3  20.4  20.1  20.7   0.3
  4.|-- ???                       100.0     4    0.0   0.0   0.0   0.0   0.0
```


what to do? Thanks.

Hi, I have the same problem like yours with Ubuntu 12.04
You should change the security configuration of your wireless modemn to WEP. Then it works.
Every thing ok. This is because... I Think Ubuntu 12.04 is not compatible with WPA or TKip or mixed,...
Good luck !

---

