---
title: "Internet PPPoe configuration problem RT2561/RT61"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by karol4722 on 2011-06-22
Hello
yesterday I've installed Ubuntu 11.04 on my computer. It's my first time with this OS. I'm connecting to internet by Air Live WT-2000PCI (RT2561 / RT61 802.11PCI) It's wifi by wlan0. I used PPPoe on windows too. Now on Linux I have strange problem... I've installed RT61 driver and ubuntu found my network and connected to whis but I cant copletelly browse internet. I have 2 OS now - windows xp and ubuntu, on windows internet works good. I repeat im beginner. What should I do?
here's my computer / network info. It may be useful for you i think. Help me configure my internet connection :(

ipconfig /all from windows
```
Microsoft Windows XP [Wersja 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Karol>ipconfig /all

Konfiguracja IP systemu Windows

        Nazwa hosta . . . . . . . . . . . : 231210f
        Sufiks podstawowej domeny DNS . . . . . . :
        Typ w&#281;z&#322;a . . . . . . . . . . . . : Hybrydowy
        Routing IP w&#322;&#261;czony . . . . . . . : Nie
        Serwer WINS Proxy w&#322;&#261;czony. . . . : Nie

Karta Ethernet Po&#322;&#261;czenie sieci bezprzewodowej:

        Sufiks DNS konkretnego po&#322;&#261;czenia :
        Opis . . . . . . . . . . . . . . :  AirLive WT-2000PCI
        Adres fizyczny. . . . . . . . . . : 00-4F-6A-04-FB-A2
        DHCP w&#322;&#261;czone . . . . . . . . . . : Tak
        Autokonfiguracja w&#322;&#261;czona . . . . : Tak
        Adres IP. . . . . . . . . . . . . : 192.168.100.104
        Maska podsieci. . . . . . . . . . : 255.255.255.0
        Brama domy&#347;lna. . . . . . . . . . : 192.168.100.252
        Serwer DHCP . . . . . . . . . . . : 192.168.100.252
        Serwery DNS . . . . . . . . . . . : 192.168.100.252
        Dzier&#380;awa uzyskana. . . . . . . . : 22 czerwca 2011 20:58:09
        Dzier&#380;awa wygasa. . . . . . . . . : 23 czerwca 2011 20:58:09

Karta PPP internet:

        Sufiks DNS konkretnego po&#322;&#261;czenia :
        Opis . . . . . . . . . . . . . . :  WAN (PPP/SLIP) Interface
        Adres fizyczny. . . . . . . . . . : 00-53-45-00-00-00
        DHCP w&#322;&#261;czone . . . . . . . . . . : Nie
        Adres IP. . . . . . . . . . . . . : 82.160.78.217
        Maska podsieci. . . . . . . . . . : 255.255.255.255
        Brama domy&#347;lna. . . . . . . . . . : 82.160.78.217
        Serwery DNS . . . . . . . . . . . : 10.0.0.2
        NetBIOS przez Tcpip . . . . . . . : Wy&#322;&#261;czony

C:\Documents and Settings\Karol>
```

ifconfig
```
karol@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:6a:4f:4a:0e            
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1        
RX packets:0 errors:0 dropped:0 overruns:0 frame:0          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)          
Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback            
inet addr:127.0.0.1  Mask:255.0.0.0         
inet6 addr: ::1/128 Scope:Host          
UP LOOPBACK RUNNING  MTU:16436  Metric:1         
RX packets:88 errors:0 dropped:0 overruns:0 frame:0         
TX packets:88 errors:0 dropped:0 overruns:0 carrier:0        
collisions:0 txqueuelen:0           
RX bytes:6200 (6.2 KB)  TX bytes:6200 (6.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:4f:6a:04:fb:a2       
inet addr:192.168.100.104  Bcast:192.168.100.255  Mask:255.255.255.0         
inet6 addr: fec0::b:24f:6aff:fe04:fba2/64 Scope:Site
inet6 addr: 2002:52a0:4e36:b:24f:6aff:fe04:fba2/64 Scope:Global         
inet6 addr: fe80::24f:6aff:fe04:fba2/64 Scope:Link          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1         
RX packets:1129 errors:0 dropped:0 overruns:0 frame:0         
TX packets:568 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000          
RX bytes:128879 (128.8 KB)  TX bytes:59754 (59.7 KB)         
Interrupt:18 Memory:cfff0000-cfff8000
```

iwconfig
```
karol@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"AK_ZG"       
Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0E:8E:1A:1B:7D            
Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm         
RTS thr=2347 B   Fragment thr=2346 B          
Power Management:off    
Link Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm       
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0          
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

my /etc/network/interfaces
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider

>>> interfaces sudo gedit /etc/network/interfaces

```

my etc/resolv.conf
```
# Generated by NetworkManager
nameserver 10.0.0.2
```

ping local and random site
```
karol@ubuntu:~$ ping localhost

PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.105 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.077 ms
64 bytes from localhost (127.0.0.1): icmp_req=3 ttl=64 time=0.070 ms
64 bytes from localhost (127.0.0.1): icmp_req=4 ttl=64 time=0.075 ms
^C

karol@ubuntu:~$ ping google.pl
ping: unknown host google.pl

```

---

### Post by dineshs on 2011-06-24
Please post the result of > ping 4.2.2.1 -c3after connecting internet using ```
pon dsl-provider
```

---

### Post by whatthefunk on 2011-06-24
You could try to connect through the command line

```
sudo pppoeconf
```

---

### Post by dineshs on 2011-06-24
> **whatthefunk said:**
> You could try to connect through the command line
```
sudo pppoeconf
```
From his /etc/network/interfaces I think he has already run ```
sudo pppoeconf wlan0
```

---

### Post by whatthefunk on 2011-06-24
> **dineshs said:**
> From his /etc/network/interfaces I think he has already run ```
sudo pppoeconf wlan0
```

Ah...you are correct.  I only saw the "# Generated by NetworkManager" in the etc/resolv.conf

You also might want to check your chap secrets file in (I think) etc/ppp to make sure your password info is in there correctly.

---

