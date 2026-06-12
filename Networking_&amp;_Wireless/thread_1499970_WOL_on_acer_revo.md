---
title: "WOL on acer revo"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by rflores2323 on 2010-06-02
on an Acer revo 3610  (ubuntu 9.10) can someone possibly help me as I cannot get WOL to work.

Went into BIOS under power management and enabled WOL

I have used this guide to set up. [HOWTO: Set your system up for Wake On LAN (WOL]("http://ubuntuforums.org/showthread.php?t=234588&page=2")

my ipconfig is 

> xbmc@xbmc-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:2c:b2:1f  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92fb:a6ff:fe2c:b21f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1096890 (1.0 MB)  TX bytes:762787 (762.7 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33814 (33.8 KB)  TX bytes:33814 (33.8 KB)

wlan0     Link encap:Ethernet  HWaddr 90:4c:e5:4e:0d:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 90-4C-E5-4E-0D-CB-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)I put the script as
```
#!/bin/bash
ethtool -s eth0 wol g
exit
```I got to the last set where it says enter in the terminal 
```
/etc/init.d/wakeonlanconfig
``` and it does not show an error


Tried to suspend the system and then use [WAKEONLANEx2]("http://software.bootblock.co.uk/?id=wakeonlanex2") from a windows xp pc to wake it up (same network) and nothing happens.

Whats weird is that it will not take my MAC address (HWaddr 90:fb:a6:2c:b2:1f ) for eth0 as it says its invalid. It will however take the MAC Address wmaster0 address 90-4C-E5-4E-0D-CB and it shows that it sends out a packet however it does not wake up my htpc.

I tried to change the script from 

```
ethtool -s eth0 wol g 
```to 

```
ethtool -s wmaster0 wol g 
```and it gives me an error message saying 

> root@xbmc-desktop:/etc/init.d# /etc/init.d/wakeonlanconfig
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol
I then tried to follow this guide [HOW-TO set up Wake-On-Lan (Ubuntu)]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_Wake-On-Lan_%28Ubuntu%29") and followed those steps also still nothing. I deleted this script however as it did nothing and didnt want to have two scripts that might be interfering with each other.

How can I check that the magic packs are being received by the computer? **I think it has something to do with the MAC address but Im a linux noob and gettng kinda lost now, ANY help would be much appreciated**.

 I also have a another linux computer hooked up on the network to test however I want to WOL via the internet incase I am traveling and need to wake up my htpc.

Can anyone please help me as I think I have the scrips installed and Im just not doing something simple like configuring the magic packs correctly to send the information.

my output shows below

xbmc@xbmc-desktop:~$ ethtool eth0
Settings for eth0:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
Cannot get link status: Operation not permitted
No data available

have gone and enabled it as per below.

```
xbmc@xbmc-desktop:~$ sudo ethtool -s eth0 wol g
[sudo] password for xbmc: 
xbmc@xbmc-desktop:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes
xbmc@xbmc-desktop:~$ ethtool eth0
Settings for eth0:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
Cannot get link status: Operation not permitted
No data available
xbmc@xbmc-desktop:~$ 

```so what am I doing wrong?

---

### Post by rflores2323 on 2010-06-03
any help?

---

