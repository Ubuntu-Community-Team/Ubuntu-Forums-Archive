---
title: "Karmic / Realtek8139/810x: ethernet link seems established, but no Web pages display"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by hoonoze on 2010-02-12
Hi,

My Toshiba Satellite's Ethernet card is giving me grief. I have both an ethernet card and a wifi card in my laptop. The ISP's service is unreliable, and I'm living somewhere where they actually provide two connections - one via the ethernet and one via wifi. The wifi one keeps going down, so I need to get the ethernet one working.

At first, I could not get it to connect to the ethernet network at all. Ubuntu 9.10 seemed to recognize the card OK, and I would see an entry in the connections list in the top toolbar, but then it would silently disconnect. 

I have Windows Vista on a separate hard disk, and when I install that disk and boot, the ethernet works OK. My ISP is providing floating addresses, and on Vista you kind-of set everything to automatic (DHCP, etc) and it works OK.

I tried the same on Karmic Koala 9.10 and at first it did not work at all. Then, I tried to specify manual IP, DHCP server, DNS server, and gateway (using the same values as I discovered under Vista). No joy. I reset everything in the 'Edit connections...' dialog to automatic discovery. Then I ran lspci, ifconfig and dmesg.

Mysteriously, Ubuntu now seems to succeed in making the connection to the ethernet network. Everything is automatic discovery, but I entered the MAC address of the card.

BUT I CAN'T DISPLAY ANY WEB PAGES.

Below is the output from the ifconfig command, dmesg | grep etho command and lspci command.

Any help on this would be much appreciated, and big thanks in advance for any tips. :D

lspci:

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:79:38:64  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe79:3864/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:157 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10460 (10.4 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:242332 (242.3 KB)  TX bytes:242332 (242.3 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:17:4f:dc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-9E-17-4F-DC-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dmesg | grep eth0:

[    2.625503] eth0: RealTek RTL8139 at 0xa000, 00:a0:d1:79:38:64, IRQ 20
[   23.927110] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   34.364018] eth0: no IPv6 routers present

:guitar:

Thanks again in advance!

---

### Post by chili555 on 2010-02-12
> errors:157That can't be good.> they actually provide two connections - one via the ethernet and one via wifi.Is this some sort of modem or router or what? Let's take a peek at:```
route -n
sudo ethtool eth0
```Thanks.

---

### Post by hoonoze on 2010-02-12
Hi chili, thank for your help, :)

No, I'm staying in a place where they are running 2 internet subscriptions (to try and ensure that at least 1 is always up and running).  1 is available via an ethernet cable connection, and the other is on a Cisco WiFi router, so 2 sets of hardware...

route -n (when the ethernet-based connection is in use):

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0


route -n (when the wifi-based connection is in use, just for info):

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0


sudo ethtool eth0:

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: yes

Any ideas? Thanks again. :popcorn:

---

### Post by Iowan on 2010-02-12
> **hoonoze said:**
> 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0        [COLOR="Red"] UG [/COLOR]   0      0        0 wlan0

With the gateway defined for wlan0, your eth0 will allow you to connect to other 10.42.43.X machines, but no internet traffic. Is Ubuntu set for DHCP or static?

---

### Post by hoonoze on 2010-02-12
> **Iowan said:**
> With the gateway defined for wlan0, your eth0 will allow you to connect to other 10.42.43.X machines, but no internet traffic. Is Ubuntu set for DHCP or static?

In the 'Network connections' box I go to 'Wired' and then click on 'Edit' for the 'Globe via Ethernet' connection. I tried choosing 'Manual' in the IPv4 settings, and entering the same values as I discovered were used in the Windows Vista config. It connects, but no web pages. 

I also tried 'Automatic (DHCP)' in the IPv4 settings, but it does not manage to connect at all... (I also tried switching off the WiFi physically on the side of the laptop, to make sure that there was no kind-of conflict).

I attached 2 screenshots, if that helps.... and thanks for your help, Iowan ;)

:confused: Puzzled and stuck...

---

### Post by Iowan on 2010-02-12
When it works - DHCP has the advantage that gateway and nameservers are passed to the clients. Network Manager likes to pass the information to */etc/resolv.conf* - which can be a problem if you're trying to put the information there yourself. 
Does the ethernet connection have a router or modem that you connect to?

---

### Post by hoonoze on 2010-02-12
> **Iowan said:**
> When it works - DHCP has the advantage that gateway and nameservers are passed to the clients. Network Manager likes to pass the information to */etc/resolv.conf* - which can be a problem if you're trying to put the information there yourself.

Yes, I noticed Network Manager prefers you to let it do the editing and for you just to adjust settings in the dialog boxes. I guess that's the price of ease of use and convenience for inexperienced people... :)

> **Iowan said:**
> Does the ethernet connection have a router or modem that you connect to?

Yes, it does, but I don't have access to it yet. The Globe technicians are supposed to be coming to help me out, but... they don't know anything about networking and basically just follow a standard procedure that was written for Windows machines... :rolleyes: They just scratch their heads when faced with a Linux system... If no-one has any other clues, then I'll just wait 'til those guys come and then post back here once I managed to get my hands on the router...

Thanks for your suggestions guys. ):P

---

