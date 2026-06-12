---
title: "Lubuntu: Wired connection stopped working, need help"
date: 2013-03-10
forum: Networking &amp; Wireless
---

### Post by Luca Borrione on 2013-03-10
Hello,

I recently installed Lubuntu 12.10 on my Asus S56C using the alternative iso.
Everything was working great until my modem-router blocked yesterday and I had to reset it to default.

After that my wi-fi connection is working, while my wired connection is unavailable under Lubuntu.
It's not a problem of my modem-router because I can access Internet through a wired connection
using another PC.
It's not a problem of my ethernet card in my Asus because I can access Internet through wired connection
under Windows 8 (I have a dual boot).

So it's just a problem of configure correctly the network in my Lubuntu, I guess.
I tried lots of things found on google without success, I need some expert help here, thanks.

```
$ sudo ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: p3p1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 50:46:5d:e9:29:b8 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether dc:85:de:70:c8:d1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.2/24 brd 192.168.1.255 scope global wlan0
    inet6 fe80::de85:deff:fe70:c8d1/64 scope link 
       valid_lft forever preferred_lft forever
4: vmnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:50:56:c0:00:01 brd ff:ff:ff:ff:ff:ff
    inet 172.16.141.1/24 brd 172.16.141.255 scope global vmnet1
    inet6 fe80::250:56ff:fec0:1/64 scope link 
       valid_lft forever preferred_lft forever
5: vmnet8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:50:56:c0:00:08 brd ff:ff:ff:ff:ff:ff
    inet 192.168.111.1/24 brd 192.168.111.255 scope global vmnet8
    inet6 fe80::250:56ff:fec0:8/64 scope link 
       valid_lft forever preferred_lft forever

```

```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: dc:85:de:70:c8:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-25-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: p3p1
       version: 0a
       serial: 50:46:5d:e9:29:b8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff

```

```
$ gksu leafpad /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
#NetworkManager#auto wlan0
#NetworkManager#iface wlan0 inet dhcp
#NetworkManager#    wpa-ssid xxxxxx
#NetworkManager#    wpa-psk  yyyyyy

```

```
$ ifconfig
lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:763 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:75271 (75.2 KB)  Byte TX:75271 (75.2 KB)


p3p1      Link encap:Ethernet  IndirizzoHW 50:46:5d:e9:29:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)


vmnet1    Link encap:Ethernet  IndirizzoHW 00:50:56:c0:00:01  
          indirizzo inet:172.16.141.1  Bcast:172.16.141.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)


vmnet8    Link encap:Ethernet  IndirizzoHW 00:50:56:c0:00:08  
          indirizzo inet:192.168.111.1  Bcast:192.168.111.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)


wlan0     Link encap:Ethernet  IndirizzoHW dc:85:de:70:c8:d1  
          indirizzo inet:192.168.1.2  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::de85:deff:fe70:c8d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3092 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:2777383 (2.7 MB)  Byte TX:512203 (512.2 KB)



```

```
$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: p3p1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        50:46:5D:E9:29:B8


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: wlan0  [xxxxxx] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        DC:85:DE:70:C8:D1


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *xxxxxx:    Infra, 00:24:01:4C:45:25, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2
    ......


  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1







```

---

### Post by Luca Borrione on 2013-03-10
@_@

It suddenly started to work by itself!
I was working on something and suddenly saw the toast message that the wired was connected!

I did nothing at all ...

Ok so please just ignore my previous post for now :)
How can I mark this thread as solved?

The site's style changed since my last solved thread ...

---

### Post by varunendra on 2013-03-10
> **Luca Borrione said:**
> 
How can I mark this thread as solved?

See [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

