---
title: "WEP encription doesn't accept key"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by jorgose on 2009-05-20
Hello, in the of days I've been trying to get my wireless card to work(BCM4306 rev02; chipset 14e4:4320) without success. I first try it with Hardy and after installing the firmware with b43-fwcutter and compiling the newest broacom drivers it was working. but those drivers caused hangs and one day it didn't work anymore... so I've updated to Jaunty because I've read that with newer kernels it may work without any tweaking. I was able to scan routers but when I try to connect to my router and put my wep key the network manager tries to build a connection and after 30 sec or so I have to put my wep key again. Strange is that ** the field for the wep key returns with something I didn't wrote**. I recently tried changing MTU from 1500 to 1492 but it didn't help.
Do you have suggestions for me??

here some info:
```

nele@dell-laptop:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:0d:56:a8:98:51  
          inet Adresse:192.168.1.101  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::20d:56ff:fea8:9851/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:1890 (1.8 KB)
          Interrupt:11 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:7500 (7.5 KB)  TX bytes:7500 (7.5 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:90:4b:1b:a3:c9  
          UP BROADCAST MULTICAST  MTU:1492  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  Hardware Adresse 00-90-4B-1B-A3-C9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
iwlist scan:
```

nele@dell-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:E3:79:9B:E1
                    ESSID:"JorNel"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=83/100  Signal level:-48 dBm  Noise level=-59 dBm
                    Encryption key:on
                    IE: Unknown: 00064A6F724E656C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020100
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000125377a189
                    Extra: Last beacon: 40ms ago

pan0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.


```
uname -r:
2.6.28-11-generic

---

### Post by jorgose on 2009-05-20
I've just tried with a usb wireless adapter: Realtek 8187b and I have the same problem. I can see the networks but I can't join. 
I also have tried connecting with no encription at all on my router (Siemens SL2-141-I) but it also didn't work !? with any wireless adapter...

---

### Post by superprash2003 on 2009-05-20
have you tried using various combinations of security type? 64bit, 128bit etc..

---

### Post by jorgose on 2009-05-20
yes, i've also tried wpa and I've disable the security in my router too. I'm just not able to connect...
I'm using wicd instead of network manager, with the same results.

---

### Post by twntyonejay on 2009-05-20
I'm having the same problem with my new Linksys router but my comp will connect to other routers tho

---

