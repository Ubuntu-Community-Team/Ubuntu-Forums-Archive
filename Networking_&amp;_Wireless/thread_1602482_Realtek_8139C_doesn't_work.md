---
title: "Realtek 8139C doesn't work"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by rubiobarga on 2010-10-21
Hi!
My problem is I can't connect to internet by cable. The cable works because I tried it with another computer with Windows installed. Here 's more information:

# sudo dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 2244
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:05:1c:0e:6a:1a
Sending on   LPF/eth0/00:05:1c:0e:6a:1a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

# sudo ethtool eth0

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: no

# sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:05:1c:0e:6a:1a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:11 ioport:e400(size=256) memory:dfffff00-dfffffff
  *-network:1
       description: Wireless interface
       product: Wireless PCI Card - F5D6001
       vendor: Belkin
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 20
       serial: 00:30:bd:50:11:86
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.38 latency=32 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11b
       resources: irq:11 ioport:d800(size=256) memory:dffffd00-dffffdff

# lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT8753 [P4X266 AGP] (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
00:0b.0 Ethernet controller: Belkin Wireless PCI Card - F5D6001 (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

# ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:05:1c:0e:6a:1a  
          Dirección inet6: fe80::205:1cff:fe0e:6a1a/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:852 (852.0 B)
          Interrupción:11 Dirección base: 0xe400 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:30:bd:50:11:86  
          Direc. inet:192.168.1.38  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::230:bdff:fe50:1186/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:26870 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:22700 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:29120190 (29.1 MB)  TX bytes:3558614 (3.5 MB)

Thanks in advance

---

### Post by chili555 on 2010-10-21
First, with Network Manager running, it is very difficult to get a connection by manual methods; usually impossible. Second, you already have an IP address wirelessly; your system and Network Manager particularly, will not like two IP addresses. Third, what do you make of this?> *-network:0
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 9
bus info: pci@0000:00:09.0
logical name: eth0
--- snip ---
latency=32 [COLOR="Red"]link=no[/COLOR] maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
resources: irq:11 ioport:e400(size=256) memory:dfffff00-dfffffffWhat does this tell us?```
dmesg | grep -e eth -e 8139
```Thanks.

---

### Post by rubiobarga on 2010-10-21
Hi!
Thanks for answering so quickly. I've removed the wireless connection and executed **dmesg | grep -e eth -e 8139** but still not working:

[    1.326144] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.326188] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.364321] 8139too Fast Ethernet driver 0.9.28
[    1.364398] 8139too 0000:00:09.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.367335] eth0: RealTek RTL8139 at 0xe400, 00:05:1c:0e:6a:1a, IRQ 11
[   22.707844] eth0: link down
[   22.707978] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.606140] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   27.606322] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.634701] eth0: link down
[   29.336337] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   29.364761] eth0: link down
[   35.837719] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   35.867354] eth0: link down
[   37.968044] eth0: no IPv6 routers present
[   42.443964] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   42.467800] eth0: link down
[   44.069297] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   44.079743] eth0: link down
[   60.375170] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   60.430959] eth0: link down
[   66.824112] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   66.833616] eth0: link down
[   70.966121] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   70.996516] eth0: link down
[   99.121278] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   99.134520] eth0: link down
[  127.486159] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  127.529061] eth0: link down
[  160.307633] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  160.310602] eth0: link down
[  193.915593] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  193.939313] eth0: link down
[  200.469376] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  200.487468] eth0: link down
[  204.558949] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  204.597429] eth0: link down
[  216.041223] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  216.106153] eth0: link down
[  225.006827] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  225.006915] eth0: link down
[  253.214432] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  253.224183] eth0: link down
[  258.772059] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  258.779157] eth0: link down

Thanks again.

---

### Post by chili555 on 2010-10-21
> This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139tooThis is a common problem; two driver modules claim the device and fight. Let's blacklist the wrong one. Please do:```
sudo su
echo "blacklist 8139cp" >> /etc/modprobe.d/blacklist.conf
exit
```Now reboot and run and post:```
lsmod | grep 8139
dmesg | grep 8139
```Thanks.

---

### Post by rubiobarga on 2010-10-22
Hi! I did everything you told me to do:

**lsmod | grep 8139**
```
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
```**dmesg | grep 8139**
```
[    1.340842] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.341173] 8139cp 0000:00:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.716241] 8139too Fast Ethernet driver 0.9.28
[    1.716346] 8139too 0000:00:09.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.717880] eth0: RealTek RTL8139 at 0xe400, 00:05:1c:0e:6a:1a, IRQ 11
```Thanks!!

---

### Post by chili555 on 2010-10-23
No change! I suspect that, although 8139cp is blacklisted, the module *mii* drags it in anyway! We can work out a way to make it permanent if my next technique works.

Please do:```
sudo rmmod -f 8139cp
sudo mii-tool eth0 -F 10baseT-FD
sudo rmmod -f 8139too
sudo modprobe 8139too
```Now, when you click the Network Manager icon, can you connect? If so, we can amend a file or two and make this permanent.

---

### Post by rubiobarga on 2010-10-24
Hi!
It works!! I did a script:

```
#! /bin/bash
sudo rmmod -f 8139cp
sudo mii-tool eth0 -F 10baseT-FD
sudo rmmod -f 8139too
sudo modprobe 8139too
```

But I don't know how to run it at startup.

Thanks!!

---

### Post by chili555 on 2010-10-24
You could add all that to /etc/rc.local without the 'sudo' right above Exit 0. If you need assistance, please post back.

---

### Post by rubiobarga on 2010-10-26
Thanks a lot!! The last question: Is it normal for the network connection (20kb/s) is slower wireless connection (100kb/s)?[COLOR=#000000][/COLOR]

---

### Post by chili555 on 2010-10-26
Not at all. You might try massaging the line here:```
mii-tool eth0 -F 10baseT-FD
```You might try [COLOR="Red"]100[/COLOR]baseT-FD. I doubt your card is gigabit-capable, but you might try 1000 and see. I believe your router or switch must also be capable.

---

### Post by rubiobarga on 2010-10-26
Thanks!!
Now it works fine!!

Thanks again!!

---

