---
title: "using network manager and more than one wired network interface"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by piti-pablo on 2009-11-30
Hi everyone,

I'm experimenting a strange issue: I use network-manager, and have a classic ethernet connexion, to access the internet, and another wired connexion, usb witch is attached to a freerunner(openmoko)
The fact is, that from 9.10, I can't use both interfaces at the same time: it see and shows it, but I only can use one of them at a time. it shows eth0 and eth1 from the applet menu, but really configures only eth0 (that what is showed by ifconfig)
before, with 9.04, I had no trouble and could use the two interfaces.
It is really annoying, because I'd like to upgrade my phone from the usb connectivity

---

### Post by Iowan on 2009-11-30
I presume you've tried setting up "the other" interface in */etc/network/interfaces*...

---

### Post by piti-pablo on 2009-11-30
one part of the problem is that the usb interface doesn't appears as a standard interface when I use ethernet: both of them take the name of eth0

and I don't know how networkmanager does the stuff to 'up' and 'down' the interfaces:
when I use internet:
```
eth0      Link encap:Ethernet  HWaddr 00:19:66:99:31:12  
          inet adr:192.168.0.51  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: 2a01:e35:xxx:xxx:xxx:xxx:xxx:xxx/64 Scope:Global
          adr inet6: fe80::219:66ff:fe99:3112/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:11205271 erreurs:0 :0 overruns:0 frame:0
          TX packets:11179777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:4044101148 (4.0 GB) Octets transmis:2687293114 (2.6 GB)
          Interruption:27 Adresse de base:0xe000 

```and if I use the usb one:
```
eth0      Link encap:Ethernet  HWaddr 00:19:66:99:31:12  
          inet adr:192.168.0.200  Bcast:192.168.0.223  Masque:255.255.255.224
          adr inet6: 2a01:e35:2f6b:e8e0:219:66ff:fe99:3112/64 Scope:Global
          adr inet6: fe80::219:66ff:fe99:3112/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:11214353 erreurs:0 :0 overruns:0 frame:0
          TX packets:11187716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:4052155980 (4.0 GB) Octets transmis:2691498967 (2.6 GB)
          Interruption:27 Adresse de base:0xe000 

```but these are not the same physical interface!

---

### Post by Iowan on 2009-11-30
Post */etc/udev/rules.d/70-persistent-net.rules* and results of **lshw -C network**. You may be able to edit the udev rules to give the usb interface a different alias (or it might get put back...).

---

### Post by piti-pablo on 2009-12-01
I'm not at home at the moment, so can't plug in the usb interface. but I have a ssh access to the desktop and there is the file:
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x03ef (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:66:99:31:12", ATTR{type}=="1", KERNEL=
="eth*", NAME="eth0"

# USB device 0x0457:0x0163 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:03:2f:40:bc:fe", ATTR{type}=="1", KERNEL=
="wlan*", NAME="wlan0"

# USB device 0x:0x (cdc_ether)  
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:11:01:3d:97", ATTR{type}=="1", KERNEL=
="eth*", NAME="eth1"
```
I want to say that despite of this file, the usb interface is really showed as eth0 (with ifconfig), and network-manager-applet names it eth1

I have ran lshw on the box I'm on:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:19:66:13:f4:73
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.10 latency=0 module=r8169 multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:2c:86:d8:bd:bb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:2
       description: Ethernet interface
       physical id: 3
       logical name: eth1
       serial: 00:1f:11:01:3d:97
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.0.200 multicast=yes

```network2 is for the usb interface.

I also have run lshw on the distant desktop:
```
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0   
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```
So I am on the box, by ssh, on an invisible interface ?

---

