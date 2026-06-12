---
title: "Sapido AU-4622 ubuntu can't see."
date: 2012-04-07
forum: Networking &amp; Wireless
---

### Post by Matikx on 2012-04-07
Hello! 
I bought yesterday Sapido AU-4622 (chipset rtl8712 or rtl8192[When I installed on windows I see rtl8192su).
Ok I've problem with this network usb-card. uBuntu can't see this device(I want to see this card on wlan1. I can't see wlan1. I can see wlan0[standard network card in my laptop]) if I connected into usb.
I don't what happen. 
Information about my system, and other:

lsb_release -a
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

```uname -rm
```
3.0.0-19-generic i686
```lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0e0b:9063 Amigo Technology Inc. 
Bus 006 Device 002: ID 0af0:6901 Option 
Bus 007 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

```**ID: 0e0b:9063 Amigo Technology Inc. <---- This is Sapido.**

lsmod | grep r87
```
r8712u                163310  0 
```hwinfo --network
```
> hal.1: read hal dataprocess 3740: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
35: None 00.0: 10700 Loopback                                   
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

36: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.RK7x40KeMO6
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.3/0000:06:00.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  HW Address: 00:03:0d:7a:ec:6b
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #21 (Ethernet controller)

37: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: y9sn.voNJAxCYCzB
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:1c.2/0000:04:00.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "iwl3945"
  Driver Modules: "iwl3945"
  Device File: wlan0
  HW Address: 00:1c:bf:16:16:fd
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (WLAN controller)
```dmesg (link):
[http://pastebin.com/uLi7A7kP](http://pastebin.com/uLi7A7kP)

How does it run?

---

