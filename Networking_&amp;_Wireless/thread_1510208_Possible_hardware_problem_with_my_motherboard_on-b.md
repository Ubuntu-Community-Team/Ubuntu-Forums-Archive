---
title: "Possible hardware problem with my motherboard on-board port"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by juanjo7 on 2010-06-15
Hello friends,

[COLOR=#000000]I have a problem with  the on-board ethernet port on my motherboard. [/COLOR]The  motherboard is new and still under warranty, so I would like to confirm  if this is a hardware problem to process the warranty.

A few  days ago it was working, but since a reboot of the computer stopped  working. I installed a pci nic card that was in home and it works perfect,  besides my wifi connection in a USB port.

I have  contacted Gigabyte support center (the motherboard is a Gigabyte  GA-H55M-UD2H) but they say thet can not help me because they do not provide  drivers for Linux ...

I tried  installing Ubuntu, Archlinux, Fedora ... and doesn't  work with any distribution. The ethernet port light is always orange, so if I connect the ethernet cable or not, and I never have connection. With the PCI nic card I plug in the cable and it works perfect, so I think it isn't router problem or  bad cable.

```
 ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:95:63:CB:43  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe63:cb43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:252417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:333040086 (317.6 MiB)  TX bytes:18698693 (17.8 MiB)
          Interrupt:19 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 6C:F0:49:0E:12:1B  
          inet6 addr: fe80::6ef0:49ff:fe0e:121b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:184 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:3221 (3.1 KiB)
          Interrupt:29 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1516 (1.4 KiB)  TX bytes:1516 (1.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:11:0A:0E:BC  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:fe0a:ebc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39139 (38.2 KiB)  TX bytes:7458 (7.2 KiB)
```The connection is eth1 (eth0 is the PCI nic card that works well)

```
dmesg |  grep eth1

eth1: RealTek RTL8139 at 0xffffc900050a2000, 00:11:95:63:cb:43, IRQ 19
udev: renamed network interface eth0 to eth1
udev: renamed network interface eth1_rename to eth0
r8169: eth1: link up
eth1: no IPv6 routers present
device eth1 entered promiscuous mode
device eth1 left promiscuous mode
device eth1 entered promiscuous mode
NETDEV WATCHDOG: eth1 (r8169): transmit queue 0 timed out
r8169: eth1: link up
device eth1 left promiscuous mode
r8169: eth1: link up
device eth1 entered promiscuous mode
r8169: eth1: link up
r8169: eth1: link up
device eth1 left promiscuous mode
device eth1 entered promiscuous mode
device eth1 left promiscuous mode
```Can  anyone help me? Can I be sure  it's a hardware problem without installing Windows?

Thank you very much [COLOR=#000000]and sorry for my  English[/COLOR],

Juanjo.

---

