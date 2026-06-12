---
title: "/etc/network/interfaces: transition from jaunty to karmic"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by jbdurand on 2010-02-05
Hi,

   I installed ubuntu jaunty on an external USB drive (since I know more or less how to configure jaunty). I also installed karmic (kernel linux 2.6.31-17-generic) to test this karmic distribution. I have the following problem for configuring the network.
   On jaunty, my /etc/network/interfaces file was:
```

auto lo wlan0
iface lo inet loopback

iface wlan0 inet dhcp
        wireless-key ABCD-EFGH-IJ
        wireless-essid ABCDEF
        netmask 255.255.255.0
        channel 6
        mode Managed
        metric 10
        needhostname yes

auto lo wlan0
iface lo inet loopback

```and the network worked, before I even connected via gdm or console.


Keeping the same file does not work with karmic. At startup, I don't have wireless network. I can connect using the wireless tools in KDE and gnome, but I am not fully satisfied with this, because when I am connecting remotely, if the computer reboots I will not be able to be connected again. So I am trying to understand the new syntax in /etc/network/interfaces.
My interface is still wlan 0, since

```


sudo iwlist scan



```gives

```


 lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: aa:bb:cc:dd:ee:ff
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm
                    Encryption key:on
                    ESSID:"ABCDEF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c49b000e
                    Extra: Last beacon: 81308ms ago
                    IE: Unknown: 00065253464D4A42
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

vboxnet0  Interface doesn't support scanning.

```




I tried some variants below in  /etc/network/interfaces, inspired by posts on  [http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/) concerning karmic and networking, and in particular I tried to use the keywords  wireless-keymode, wireless-channel, etc. instead of keymode, channel... but nothing works, so I am stuck.

```
auto lo wlan0
iface lo inet loopback

iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid ABCDEF
wireless-keymode restricted
wireless-key ABCD-EFGH-IJ
wireless-channel 6
metric 10
needhostname yes
netmask 255.255.255.0

``````
ifconfig
```gives






```
eth0      Link encap:Ethernet  HWaddr 00:0c:76:f1:f2:44  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:19 Adresse de base:0xe800 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:8 erreurs:0 :0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:480 (480.0 B) Octets transmis:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:f8:a9:f7:84  
          adr inet6: fe80::218:f8ff:fea9:f784/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          Packets reçus:7 erreurs:0 :0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1100 (1.1 KB) Octets transmis:944 (944.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:f8:a9:f7:84  
          inet adr:169.254.11.116  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1492  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-18-F8-A9-F7-84-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)


```I also tried different network wifi cards, different wifi access points (netgear and linksys), and I cant make any of this work with /etc/netwkor/interfaces (unless I disable WEP).
Any idea please ? Thank you !

---

